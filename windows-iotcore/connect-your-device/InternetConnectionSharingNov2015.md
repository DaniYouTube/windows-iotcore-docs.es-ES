---
title: Tutorial de conexión compartida a Internet (versión 2015 de noviembre)
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
description: Obtenga información acerca de cómo habilitar y configurar la conexión compartida a Internet para la versión de noviembre de 2015 de Windows.
keywords: Windows IOT, conexión compartida a Internet, ICS, portal de dispositivos
ms.openlocfilehash: c8f27b48197a0ec881a66da5d3e81272b3076100
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169082"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a>Tutorial de conexión compartida a Internet (versión 2015 de noviembre)

En este documento se describen los pasos para habilitar conexión compartida a Internet (ICS) en un dispositivo que ejecuta Windows 10 IoT Core, versión de noviembre de 2015. El objetivo es compartir una conexión a Internet entre un punto de acceso Wi-Fi de software (SoftAP) y un adaptador Ethernet. Si usa la versión de aniversario de Windows 10 IoT Core, consulte el [tutorial de conexión compartida a Internet](InternetConnectionSharing.md).

## <a name="prerequisites"></a>Requisitos previos

* Dispositivo que ejecuta la versión de noviembre 2015 de Windows 10 IoT Core.
* Dispositivo USB Wi-Fi capaz de iniciar un SoftAP. Consulte la lista de [compatibilidad de hardware](../learn-about-hardware/HardwareCompatList.md) para dispositivos USB Wi-Fi compatibles.
* Conexión Ethernet con acceso a Internet.


## <a name="setup"></a>Programa de instalación

### <a name="step-1-gathering-network-information"></a>Paso 1: Recopilar información de red

1. Arranque del dispositivo con la llave Wi-Fi conectada, cable Ethernet enchufado.
2. Inicie SoftAP desde el dispositivo IoT Core.

   De forma predeterminada, las imágenes proporcionadas por Microsoft inician una aplicación de incorporación de IoT que configurará un SoftAP si la radio Wi-Fi es compatible y no se ha agregado ningún perfil de WLAN. Para iniciar SoftAP, las aplicaciones para UWP pueden usar la [API Windows. Devices. WiFiDirect. WiFiDirectAdvertisementPublisher](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx). El código fuente de la aplicación de incorporación de IoT puede estar en GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).

   Grabe el SSID de la red SoftAP. Lo necesitará más adelante para conectarse a su dispositivo de IoT Core a través de Wi-Fi. En el caso de la aplicación de incorporación de IoT, el SSID\_comenzará con "AJ SoftAPSsid\_" y se puede cambiar en el [archivo](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)de configuración de la aplicación.

3. Conéctese de forma remota al dispositivo de IoT Core [mediante SSH](ssh.md).
4. Recopile información acerca de las redes de dispositivos buscando los índices y las descripciones de los dispositivos de red. Esto es necesario para declarar las redes que se van a enlazar.

   En el dispositivo, ejecute **Route Print** y recopile los datos siguientes:

   * Registra el índice de red de la interfaz pública del Ethernet.
   * Registra el índice de red de la interfaz privada para SoftAP (por ejemplo, "Adaptador virtual de Microsoft Wi-Fi Direct #2").

   Por ejemplo, el SoftAP se expone a través del índice de la interfaz 5, la descripción del adaptador "adaptador virtual de Wi-Fi Direct de Microsoft #2".

   ![imprimir ruta](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   En el dispositivo, ejecute **ipconfig/all** y recopile los datos siguientes:
    
   * Registrar el nombre del adaptador de red de la interfaz privada para el SoftAP

   Por ejemplo, si se ejecuta "ipconfig/all", se busca el adaptador específico denominado "conexión de área local * 3" que tiene una descripción de "adaptador virtual de Microsoft Wi-Fi Direct #2". Use este método para buscar manualmente el nombre del adaptador de la descripción devuelta en "Route Print".

   ![ipconfig all](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a>Paso 2: Crear script para el desencadenador de conexión compartida a Internet

El inicio de conexión compartida a Internet entre dos redes requiere los pasos siguientes:

* Establezca las claves del registro para establecer las interfaces de red privadas (SoftAP) y públicas (Ethernet) en Bridge.
* Establezca las reglas de Firewall adecuadas.
* Desactiva DHCP en la interfaz privada.
* Establece la dirección IP estática en la interfaz privada.
* Inicia el servicio SharedAccess.
* Envía el código de comando "129" al servicio SharedAccess.


#### <a name="create-a-script-to-automate-the-ics-settings"></a>Crear un script para automatizar la configuración de ICS

A continuación se muestra un ejemplo de scripts y código para automatizar los pasos indicados anteriormente que se pueden integrar en la secuencia de inicio del dispositivo. Cree un archivo de script (por ejemplo, **ConfigureICS. cmd**) con el siguiente contenido:

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

Este script hará todo, excepto el servicio de inicio y detención de SharedAccess y no envía el comando de servicio. Para las tareas a las que llama a SharedAccessUtility. exe, que debe crearse.

#### <a name="build-the-sharedaccessutility-application"></a>Compilar la aplicación SharedAccessUtility
En Visual Studio con [las extensiones de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) instaladas, cree un nuevo proyecto de Visual C++ aplicación de consola de Windows IOT Core en blanco denominado **SharedAccessUtility**.

![VS nuevo proyecto](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

Reemplace el contenido de definimos. cpp por el código siguiente:

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

Compilación para la arquitectura de destino, por ejemplo, versión x86, y búsqueda de la salida **SharedAccessUtility. exe**

### <a name="step-3-starting-internet-connection-sharing"></a>Paso 3: Inicio de conexión compartida a Internet

1. Copie el script **ConfigICS. cmd** creado en el paso 2 en el dispositivo en alguna ubicación, por ejemplo, para`C:\test\`
2. Copie **SharedAccessUtility. exe** creado en el paso 2 en el dispositivo en la misma ubicación, por ejemplo,`C:\test`\
3. En el dispositivo, ejecute **C:\test\ConfigureICS.cmd Start [Public index] [Private index] [Private Adapter Name** ] en este ejemplo, lo que significa que <strong>C:\test\ConfigureICS.cmd start 4 5 "conexión de área local * 3"</strong>

En este momento, el dispositivo ha habilitado el uso compartido de conexión a Internet para cualquier cliente conectado al SSID anunciado del dispositivo.
