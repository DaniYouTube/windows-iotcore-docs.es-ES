---
title: Conexión a Internet compartida Tutorial (versión de noviembre de 2015)
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
description: Obtenga información sobre cómo habilitar y configurar la conexión a internet de uso compartido de la versión de noviembre de 2015 de Windows.
keywords: Windows iot, conexión compartida a Internet, ICS, Device Portal
ms.openlocfilehash: c8f27b48197a0ec881a66da5d3e81272b3076100
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514619"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a>Conexión a Internet compartida Tutorial (versión de noviembre de 2015)

Este documento describe los pasos para habilitar la conexión compartida a Internet (ICS) en un dispositivo que ejecuta Windows 10 IoT Core versión de noviembre de 2015. El objetivo es compartir una conexión a Internet entre un punto de acceso Wi-Fi de software (SoftAP) y un adaptador de Ethernet. Si está usando la versión de aniversario de Windows 10 IoT Core, consulte el [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).

## <a name="prerequisites"></a>Requisitos previos

* Los dispositivos que ejecutan Windows 10 IoT Core versión de noviembre de 2015.
* Dispositivo USB de Wi-Fi capaz de iniciar un SoftAP. Consulte la [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) admite dispositivos USB de Wi-Fi.
* Conexión Ethernet con acceso a Internet.


## <a name="setup"></a>Programa de instalación

### <a name="step-1-gathering-network-information"></a>Paso 1: Recopilando información de red

1. Arranque el dispositivo con Wi-Fi llave con corriente alterna, cable Ethernet conectado.
2. Iniciar SoftAP desde el dispositivo de IoT Core.

   De forma predeterminada, Microsoft proporciona una aplicación IoT Onboarding que configurará un SoftAP si es compatible con radio de Wi-Fi y no se ha agregado ningún perfil WLAN inicio imágenes. Para empezar a SoftAP, las aplicaciones de UWP pueden usar el [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx). El código fuente de la aplicación de IoT Onboarding puede estar en GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).

   Anote el SSID de la red SoftAP. Necesitará más adelante para conectarse al dispositivo de IoT Core a través de Wi-Fi. Para aplicaciones de IoT Onboarding se iniciará el SSID con "AJ\_SoftAPSsid\_" y se puede cambiar en la configuración de la aplicación [archivo](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).

3. Conectarse de forma remota al dispositivo de IoT Core [mediante ssh](ssh.md).
4. Recopilar información acerca de las redes de dispositivo mediante la búsqueda de descripciones y los índices de dispositivo de red. Esto es necesario declarar qué redes al puente.

   En el dispositivo, ejecute **enrutar impresión** y recopilar los datos siguientes:

   * Índice de red de interfaz pública de registro para la red Ethernet.
   * Interfaz privada de registro de red de índice para el SoftAP (p. ej. "Microsoft Wi-Fi Direct adaptador Virtual #2").

   Por ejemplo, el SoftAP se expone a través del índice de interfaz 5, descripción del adaptador "Adaptador Microsoft Wi-Fi Direct Virtual #2".

   ![ruta de impresión](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   En el dispositivo, ejecute **ipconfig/all** y recopilar los datos siguientes:
    
   * Nombre del adaptador de red de interfaz privada de registro para el SoftAP

   Por ejemplo, ejecutar "ipconfig /all" encuentra el adaptador específico denominado "conexión de área Local * 3" con una descripción de "Microsoft Wi-Fi Direct adaptador Virtual #2". Use este método para buscar manualmente el que nombre del adaptador de la descripción devuelta de "ruta de impresión".

   ![todos los ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a>Paso 2: Desencadenador de conexión compartida a Internet de secuencias de comandos

Iniciando la conexión compartida a Internet entre dos redes requiere los siguientes pasos:

* Establecer las claves del registro para establecer privado (SoftAP) y las interfaces de red (Ethernet) públicas al puente.
* Establecer reglas de firewall adecuados.
* Desactiva DHCP en la interfaz privada.
* Establece la dirección IP estática en la interfaz privada.
* Inicia el servicio de acceso compartido.
* Envía el código de comando "129" al servicio de acceso compartido.


#### <a name="create-a-script-to-automate-the-ics-settings"></a>Crear un script para automatizar la configuración de ICS

A continuación es un ejemplo de un scripts y código para automatizar los pasos indicados anteriormente se puede integrar en la secuencia de inicio del dispositivo. Crear un archivo de script (por ejemplo, **ConfigureICS.cmd**) con el siguiente contenido:

```
echo off

set START_OR_STOP=%1
set PUBLIC_INDEX=%2
set PRIVATE_INDEX=%3
set PRIVATE_INTERFACE_NAME=%4

if not defined PRIVATE_INTERFACE_NAME (
  goto usage
)

if "%START_OR_STOP%"=="start" (

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d %PRIVATE_INDEX%
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d %PUBLIC_INDEX%

  REM Set the firewall rules to allow DHCP to work
  netsh advfirewall firewall add rule name=\"AllowPort67In\" protocol=UDP dir=in localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68In\" protocol=UDP dir=in localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort67Out\" protocol=UDP dir=out localport=67 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort68Out\" protocol=UDP dir=out localport=68 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53Out\" protocol=UDP dir=out localport=53 action=allow
  netsh advfirewall firewall add rule name=\"AllowPort53In\" protocol=UDP dir=in localport=53 action=allow

  REM Turn off DHCP and set static IP for private interface
  netsh interface ip set address %4 static 192.168.137.1

  REM Start sharing
  call SharedAccessUtility.exe start

) else if "%START_OR_STOP%"=="stop" (

  REM Stop sharing
  call SharedAccessUtility.exe stop

  REM Set the public and private interface registry keys
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v private /t REG_DWORD /d 0
  reg add HKEY_LOCAL_MACHINE\System\SA /f /v public /t REG_DWORD /d 0

  REM Clear the firewall rules
  netsh advfirewall firewall delete rule name="AllowPort67In"
  netsh advfirewall firewall delete rule name="AllowPort68In"
  netsh advfirewall firewall delete rule name="AllowPort67Out"
  netsh advfirewall firewall delete rule name="AllowPort68Out"
  netsh advfirewall firewall delete rule name="AllowPort53Out"
  netsh advfirewall firewall delete rule name="AllowPort53In"

  REM Reenable DHCP for private interface
  netsh interface ip set address %4 dhcp

) else (
  goto usage
)

goto eof

:usage
ECHO USAGE: %0 [start ^| stop] [public interface index] [private interface index] [private interface name]
ECHO e.g. %0 start 1 2 "Ethernet"

:eof
```

Este script hará todo excepto iniciar o detener el servicio de acceso compartido y no envía el comando de servicio. Para las tareas que realiza una llamada a SharedAccessUtility.exe, que debe crearse.

#### <a name="build-the-sharedaccessutility-application"></a>Compile la aplicación SharedAccessUtility
En Visual Studio con [extensiones de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) instalado, cree un nuevo Visual "En blanco Windows IoT Core aplicación de consola" C++ proyecto, denominado **SharedAccessUtility**.

![Nuevo proyecto de VS](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

Reemplace el contenido de ConsoleApplication.cpp con el código siguiente:

```C++
#include "pch.h"
#include <ws2tcpip.h>
#include <iphlpapi.h>
#include <mstcpip.h>
#include <stdio.h>

#define SHARED_ACCESS_NAME L"SharedAccess"
#define START_SHARING_CONTROL 129

DWORD StartSharedAccessService(SC_HANDLE *phScm, SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    // open a handle to SCM
    *phScm = OpenSCManager(NULL, NULL, SC_MANAGER_CONNECT);
    if (*phScm == NULL)
    {
        dwError = GetLastError();
        printf("\nOpenSCManager failed; error = %d", dwError);
    }
    else
    {
        // open a handle to the service
        *phSvc = OpenService(*phScm, SHARED_ACCESS_NAME, SERVICE_START | SERVICE_QUERY_STATUS | SERVICE_QUERY_CONFIG | SERVICE_STOP | SERVICE_USER_DEFINED_CONTROL);
        if (*phSvc == NULL)
        {
            dwError = GetLastError();
            printf("\nOpenService failed; error = %d", dwError);
        }
        else
        {
            if (!StartService(*phSvc, 0, NULL))
            {
                dwError = GetLastError();
                if (dwError != ERROR_SERVICE_ALREADY_RUNNING)
                {
                    printf("\nStartService failed; error = %d", dwError);
                }
                else
                {
                    dwError = ERROR_SUCCESS;
                    printf("\nService already running.");
                }
            }

            if (dwError == ERROR_SUCCESS)
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_RUNNING)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to start.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_RUNNING)
                            {
                                printf("\nService is running.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                                {
                                    printf("\nService could not run.");
                                    // it is, so break out
                                    dwError = ERROR_SERVICE_NOT_ACTIVE;
                                    break;
                                }
                            }
                        }
                        else
                        {
                            printf("\nWaiting more time.");
                        }
                    }
                }
            }
        }
    }

    if (dwError == ERROR_SUCCESS) //service is running
    {
        if (!ControlService(*phSvc, START_SHARING_CONTROL, &svcStatus))
        {
            dwError = GetLastError();
            printf("\nControl service for start sharing failure, %d", dwError);
        }
        else
        {
            printf("\nSharing started");
        }
    }

    // Service cleanup done at the main.
    return dwError;
}


DWORD StopSharedAccessService(SC_HANDLE *phSvc)
{
    DWORD dwError = ERROR_SUCCESS;
    SERVICE_STATUS svcStatus = { 0 };

    if (!QueryServiceStatus(*phSvc, &svcStatus))
    {
        dwError = GetLastError();
        printf("\nFailed to query sharedaccess, %d", dwError);
    }
    else
    {
        if (svcStatus.dwCurrentState != SERVICE_STOPPED)
        {
            if (ControlService(*phSvc, SERVICE_CONTROL_STOP, &svcStatus))
            {
                if (QueryServiceStatus(*phSvc, &svcStatus) && svcStatus.dwCurrentState != SERVICE_STOPPED)
                {
                    for (int i = 0; i < 10; i++)
                    {
                        printf("\nWaiting 1 second for service to stop.");
                        Sleep(1000);
                        if (QueryServiceStatus(*phSvc, &svcStatus))
                        {
                            if (svcStatus.dwCurrentState == SERVICE_STOPPED)
                            {
                                printf("\nService stopped.");
                                // it is, so break out
                                dwError = ERROR_SUCCESS;
                                break;
                            }
                            else
                            {
                                printf("\nWaiting more time.");
                            }
                        }
                    }
                }
            }
        }
    }
    return dwError;
}

void ShowUsage()
{
    printf("Usage: SharedAccessUtility.exe start | stop\n"
        "Setup: Make sure the public and private interfaces are up and running and that the SharedAccess registry keys are set.");
}

int __cdecl
main(
    __in int argc,
    __in_ecount(argc) LPSTR argv[]
    )
{
    SC_HANDLE hScm = NULL;
    SC_HANDLE hSvc = NULL;
    DWORD dwError = NO_ERROR;
    bool startSharing = true;

    if (argc < 2)
    {
        ShowUsage();
        return -1;
    }
    else
    {
        if (strcmp(argv[1], "start") == 0 || strcmp(argv[1], "/start") == 0)
        {
            startSharing = true;
        }
        else if (strcmp(argv[1], "stop") == 0 || strcmp(argv[1], "/stop") == 0)
        {
            startSharing = false;
        }
        else
        {
            ShowUsage();
            return -1;
        }
    }

    dwError = startSharing ? StartSharedAccessService(&hScm, &hSvc) : StopSharedAccessService(&hSvc);

    // Cleanup
    if (hSvc != NULL)
    {
        CloseServiceHandle(hSvc);
        hSvc = NULL;
    }
    if (hScm != NULL)
    {
        CloseServiceHandle(hScm);
        hScm = NULL;
    }
    return 0;
}
```

Compilar para arquitectura de destino, por ejemplo, versión x86 y busque salida **SharedAccessUtility.exe**

### <a name="step-3-starting-internet-connection-sharing"></a>Paso 3: Iniciando Internet conexión compartida

1. Copia **ConfigICS.cmd** script creado en el paso 2 para el dispositivo en una ubicación, por ejemplo, para `C:\test\`
2. Copia **SharedAccessUtility.exe** creado en el paso 2 para el dispositivo en la misma ubicación, p. ej. `C:\test`\
3. En el dispositivo, ejecutar **C:\test\ConfigureICS.cmd inicio [índice pública] [índice privada] [nombre del adaptador privada]** en este ejemplo, esto significaría <strong>C:\test\ConfigureICS.cmd iniciar 4 5 "Local área conexión * 3"</strong>

En este momento, el dispositivo habilitó Conexión compartida a Internet para cualquier cliente conectado al SSID anunciados del dispositivo.
