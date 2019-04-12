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
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a><span data-ttu-id="f2c50-104">Conexión a Internet compartida Tutorial (versión de noviembre de 2015)</span><span class="sxs-lookup"><span data-stu-id="f2c50-104">Internet Connection Sharing Tutorial (November 2015 Release)</span></span>

<span data-ttu-id="f2c50-105">Este documento describe los pasos para habilitar la conexión compartida a Internet (ICS) en un dispositivo que ejecuta Windows 10 IoT Core versión de noviembre de 2015.</span><span class="sxs-lookup"><span data-stu-id="f2c50-105">This document describes the steps to enable Internet Connection Sharing (ICS) on a device running Windows 10 IoT Core November 2015 Release.</span></span> <span data-ttu-id="f2c50-106">El objetivo es compartir una conexión a Internet entre un punto de acceso Wi-Fi de software (SoftAP) y un adaptador de Ethernet.</span><span class="sxs-lookup"><span data-stu-id="f2c50-106">The objective is to share an Internet connection between a software Wi-Fi access point (SoftAP) and an Ethernet adapter.</span></span> <span data-ttu-id="f2c50-107">Si está usando la versión de aniversario de Windows 10 IoT Core, consulte el [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span><span class="sxs-lookup"><span data-stu-id="f2c50-107">If you are using the Windows 10 IoT Core Anniversary Release please refer to the [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2c50-108">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f2c50-108">Prerequisites</span></span>

* <span data-ttu-id="f2c50-109">Los dispositivos que ejecutan Windows 10 IoT Core versión de noviembre de 2015.</span><span class="sxs-lookup"><span data-stu-id="f2c50-109">Device running Windows 10 IoT Core November 2015 Release.</span></span>
* <span data-ttu-id="f2c50-110">Dispositivo USB de Wi-Fi capaz de iniciar un SoftAP.</span><span class="sxs-lookup"><span data-stu-id="f2c50-110">Wi-Fi USB device capable of starting a SoftAP.</span></span> <span data-ttu-id="f2c50-111">Consulte la [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) admite dispositivos USB de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="f2c50-111">Please refer to the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) for supported Wi-Fi USB devices.</span></span>
* <span data-ttu-id="f2c50-112">Conexión Ethernet con acceso a Internet.</span><span class="sxs-lookup"><span data-stu-id="f2c50-112">Ethernet connection with Internet Access.</span></span>


## <a name="setup"></a><span data-ttu-id="f2c50-113">Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="f2c50-113">Setup</span></span>

### <a name="step-1-gathering-network-information"></a><span data-ttu-id="f2c50-114">Paso 1: Recopilando información de red</span><span class="sxs-lookup"><span data-stu-id="f2c50-114">Step 1: Gathering Network Information</span></span>

1. <span data-ttu-id="f2c50-115">Arranque el dispositivo con Wi-Fi llave con corriente alterna, cable Ethernet conectado.</span><span class="sxs-lookup"><span data-stu-id="f2c50-115">Boot up device with Wi-Fi dongle plugged in, Ethernet cable plugged in.</span></span>
2. <span data-ttu-id="f2c50-116">Iniciar SoftAP desde el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f2c50-116">Start SoftAP from the IoT Core device.</span></span>

   <span data-ttu-id="f2c50-117">De forma predeterminada, Microsoft proporciona una aplicación IoT Onboarding que configurará un SoftAP si es compatible con radio de Wi-Fi y no se ha agregado ningún perfil WLAN inicio imágenes.</span><span class="sxs-lookup"><span data-stu-id="f2c50-117">By default, the Microsoft provided images start an IoT Onboarding application that will setup a SoftAP if Wi-Fi radio is capable and no WLAN profile has been added.</span></span> <span data-ttu-id="f2c50-118">Para empezar a SoftAP, las aplicaciones de UWP pueden usar el [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span><span class="sxs-lookup"><span data-stu-id="f2c50-118">To start SoftAP, UWP applications can use the [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span></span> <span data-ttu-id="f2c50-119">El código fuente de la aplicación de IoT Onboarding puede estar en GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span><span class="sxs-lookup"><span data-stu-id="f2c50-119">The source code for the IoT Onboarding application can be on GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span></span>

   <span data-ttu-id="f2c50-120">Anote el SSID de la red SoftAP.</span><span class="sxs-lookup"><span data-stu-id="f2c50-120">Record the SSID of the SoftAP network.</span></span> <span data-ttu-id="f2c50-121">Necesitará más adelante para conectarse al dispositivo de IoT Core a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="f2c50-121">You will need it later to connect to your IoT Core device via Wi-Fi.</span></span> <span data-ttu-id="f2c50-122">Para aplicaciones de IoT Onboarding se iniciará el SSID con "AJ\_SoftAPSsid\_" y se puede cambiar en la configuración de la aplicación [archivo](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span><span class="sxs-lookup"><span data-stu-id="f2c50-122">For IoT Onboarding application the SSID will start with "AJ\_SoftAPSsid\_" and can be changed in application's configuration [file](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span></span>

3. <span data-ttu-id="f2c50-123">Conectarse de forma remota al dispositivo de IoT Core [mediante ssh](ssh.md).</span><span class="sxs-lookup"><span data-stu-id="f2c50-123">Remotely connect to the IoT Core device [using ssh](ssh.md).</span></span>
4. <span data-ttu-id="f2c50-124">Recopilar información acerca de las redes de dispositivo mediante la búsqueda de descripciones y los índices de dispositivo de red.</span><span class="sxs-lookup"><span data-stu-id="f2c50-124">Collect information about device networks by finding network device indexes and descriptions.</span></span> <span data-ttu-id="f2c50-125">Esto es necesario declarar qué redes al puente.</span><span class="sxs-lookup"><span data-stu-id="f2c50-125">This is needed to declare which networks to bridge.</span></span>

   <span data-ttu-id="f2c50-126">En el dispositivo, ejecute **enrutar impresión** y recopilar los datos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f2c50-126">On device, run **route print** and collect the following data:</span></span>

   * <span data-ttu-id="f2c50-127">Índice de red de interfaz pública de registro para la red Ethernet.</span><span class="sxs-lookup"><span data-stu-id="f2c50-127">Record PUBLIC Interface network index for the Ethernet.</span></span>
   * <span data-ttu-id="f2c50-128">Interfaz privada de registro de red de índice para el SoftAP (p. ej. "Microsoft Wi-Fi Direct adaptador Virtual #2").</span><span class="sxs-lookup"><span data-stu-id="f2c50-128">Record PRIVATE Interface network index for the SoftAP (e.g. “Microsoft Wi-Fi Direct Virtual Adapter #2”).</span></span>

   <span data-ttu-id="f2c50-129">Por ejemplo, el SoftAP se expone a través del índice de interfaz 5, descripción del adaptador "Adaptador Microsoft Wi-Fi Direct Virtual #2".</span><span class="sxs-lookup"><span data-stu-id="f2c50-129">For example, the SoftAP is exposed through interface index 5, adapter description “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span>

   ![ruta de impresión](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   <span data-ttu-id="f2c50-131">En el dispositivo, ejecute **ipconfig/all** y recopilar los datos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f2c50-131">On device, run **ipconfig /all** and collect the following data:</span></span>
    
   * <span data-ttu-id="f2c50-132">Nombre del adaptador de red de interfaz privada de registro para el SoftAP</span><span class="sxs-lookup"><span data-stu-id="f2c50-132">Record PRIVATE Interface network adapter name for the SoftAP</span></span>

   <span data-ttu-id="f2c50-133">Por ejemplo, ejecutar "ipconfig /all" encuentra el adaptador específico denominado "conexión de área Local \* 3" con una descripción de "Microsoft Wi-Fi Direct adaptador Virtual #2".</span><span class="sxs-lookup"><span data-stu-id="f2c50-133">For example, running "ipconfig /all" finds the specific adapter named “Local Area Connection\* 3” that has a description of “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span> <span data-ttu-id="f2c50-134">Use este método para buscar manualmente el que nombre del adaptador de la descripción devuelta de "ruta de impresión".</span><span class="sxs-lookup"><span data-stu-id="f2c50-134">Use this method to manually find Adapter Name from the Description returned in “route print”.</span></span>

   ![todos los ipconfig](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a><span data-ttu-id="f2c50-136">Paso 2: Desencadenador de conexión compartida a Internet de secuencias de comandos</span><span class="sxs-lookup"><span data-stu-id="f2c50-136">Step 2: Scripting Internet Connection Sharing trigger</span></span>

<span data-ttu-id="f2c50-137">Iniciando la conexión compartida a Internet entre dos redes requiere los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="f2c50-137">Starting Internet Connection Sharing between two networks requires the following steps:</span></span>

* <span data-ttu-id="f2c50-138">Establecer las claves del registro para establecer privado (SoftAP) y las interfaces de red (Ethernet) públicas al puente.</span><span class="sxs-lookup"><span data-stu-id="f2c50-138">Set registry keys to set private (SoftAP) and public (Ethernet) network interfaces to bridge.</span></span>
* <span data-ttu-id="f2c50-139">Establecer reglas de firewall adecuados.</span><span class="sxs-lookup"><span data-stu-id="f2c50-139">Set appropriate firewall rules.</span></span>
* <span data-ttu-id="f2c50-140">Desactiva DHCP en la interfaz privada.</span><span class="sxs-lookup"><span data-stu-id="f2c50-140">Turns off DHCP on private interface.</span></span>
* <span data-ttu-id="f2c50-141">Establece la dirección IP estática en la interfaz privada.</span><span class="sxs-lookup"><span data-stu-id="f2c50-141">Sets static IP address on private interface.</span></span>
* <span data-ttu-id="f2c50-142">Inicia el servicio de acceso compartido.</span><span class="sxs-lookup"><span data-stu-id="f2c50-142">Starts SharedAccess service.</span></span>
* <span data-ttu-id="f2c50-143">Envía el código de comando "129" al servicio de acceso compartido.</span><span class="sxs-lookup"><span data-stu-id="f2c50-143">Sends command code “129” to SharedAccess service.</span></span>


#### <a name="create-a-script-to-automate-the-ics-settings"></a><span data-ttu-id="f2c50-144">Crear un script para automatizar la configuración de ICS</span><span class="sxs-lookup"><span data-stu-id="f2c50-144">Create a script to automate the ICS settings</span></span>

<span data-ttu-id="f2c50-145">A continuación es un ejemplo de un scripts y código para automatizar los pasos indicados anteriormente se puede integrar en la secuencia de inicio del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f2c50-145">Below is an example of a scripts and code to automate the steps listed above that can be integrated into the device startup sequence.</span></span> <span data-ttu-id="f2c50-146">Crear un archivo de script (por ejemplo, **ConfigureICS.cmd**) con el siguiente contenido:</span><span class="sxs-lookup"><span data-stu-id="f2c50-146">Create a script file (e.g. **ConfigureICS.cmd**) with the following content:</span></span>

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

<span data-ttu-id="f2c50-147">Este script hará todo excepto iniciar o detener el servicio de acceso compartido y no envía el comando de servicio.</span><span class="sxs-lookup"><span data-stu-id="f2c50-147">This script will do everything but start/stop SharedAccess service, and does not send service command.</span></span> <span data-ttu-id="f2c50-148">Para las tareas que realiza una llamada a SharedAccessUtility.exe, que debe crearse.</span><span class="sxs-lookup"><span data-stu-id="f2c50-148">For those tasks it calls to SharedAccessUtility.exe, which needs to be created.</span></span>

#### <a name="build-the-sharedaccessutility-application"></a><span data-ttu-id="f2c50-149">Compile la aplicación SharedAccessUtility</span><span class="sxs-lookup"><span data-stu-id="f2c50-149">Build the SharedAccessUtility application</span></span>
<span data-ttu-id="f2c50-150">En Visual Studio con [extensiones de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) instalado, cree un nuevo Visual "En blanco Windows IoT Core aplicación de consola" C++ proyecto, denominado **SharedAccessUtility**.</span><span class="sxs-lookup"><span data-stu-id="f2c50-150">In Visual Studio with [Windows IoT Core Project Templates extensions](https://go.microsoft.com/fwlink/?linkid=847472) installed, create a new “Blank Windows IoT Core Console Application” Visual C++ project, named **SharedAccessUtility**.</span></span>

![Nuevo proyecto de VS](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

<span data-ttu-id="f2c50-152">Reemplace el contenido de ConsoleApplication.cpp con el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="f2c50-152">Replace contents of ConsoleApplication.cpp with the following code:</span></span>

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

<span data-ttu-id="f2c50-153">Compilar para arquitectura de destino, por ejemplo, versión x86 y busque salida **SharedAccessUtility.exe**</span><span class="sxs-lookup"><span data-stu-id="f2c50-153">Build for target architecture, e.g. Release x86, and locate output **SharedAccessUtility.exe**</span></span>

### <a name="step-3-starting-internet-connection-sharing"></a><span data-ttu-id="f2c50-154">Paso 3: Iniciando Internet conexión compartida</span><span class="sxs-lookup"><span data-stu-id="f2c50-154">Step 3: Starting Internet Connection Sharing</span></span>

1. <span data-ttu-id="f2c50-155">Copia **ConfigICS.cmd** script creado en el paso 2 para el dispositivo en una ubicación, por ejemplo, para</span><span class="sxs-lookup"><span data-stu-id="f2c50-155">Copy **ConfigICS.cmd** script created in Step 2 to the device in some location, e.g. to</span></span> `C:\test\`
2. <span data-ttu-id="f2c50-156">Copia **SharedAccessUtility.exe** creado en el paso 2 para el dispositivo en la misma ubicación, p. ej. `C:\test`\\</span><span class="sxs-lookup"><span data-stu-id="f2c50-156">Copy **SharedAccessUtility.exe** created in Step 2 to the device in the same location, e.g. `C:\test`\\</span></span>
3. <span data-ttu-id="f2c50-157">En el dispositivo, ejecutar **C:\test\ConfigureICS.cmd inicio [índice pública] [índice privada] [nombre del adaptador privada]** en este ejemplo, esto significaría <strong>C:\test\ConfigureICS.cmd iniciar 4 5 "Local área conexión \* 3"</strong></span><span class="sxs-lookup"><span data-stu-id="f2c50-157">On the device, run **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** In this example, this would mean <strong>C:\test\ConfigureICS.cmd start 4 5 "Local Area Connection\* 3"</strong></span></span>

<span data-ttu-id="f2c50-158">En este momento, el dispositivo habilitó Conexión compartida a Internet para cualquier cliente conectado al SSID anunciados del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f2c50-158">At this point the device has enabled Internet Connection Sharing for any client connected to the device’s advertised SSID.</span></span>
