---
title: Tutorial de conexión compartida a Internet (versión 2015 de noviembre)
ms.date: 09/06/2017
ms.topic: article
description: Obtenga información acerca de cómo habilitar y configurar la conexión compartida a Internet para la versión de noviembre de 2015 de Windows.
keywords: Windows IOT, conexión compartida a Internet, ICS, portal de dispositivos
ms.openlocfilehash: fa53539128251fd45e47003979a72e5a588b2869
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918354"
---
# <a name="internet-connection-sharing-tutorial-november-2015-release"></a><span data-ttu-id="b4c5c-104">Tutorial de conexión compartida a Internet (versión 2015 de noviembre)</span><span class="sxs-lookup"><span data-stu-id="b4c5c-104">Internet Connection Sharing Tutorial (November 2015 Release)</span></span>

<span data-ttu-id="b4c5c-105">En este documento se describen los pasos para habilitar conexión compartida a Internet (ICS) en un dispositivo que ejecuta Windows 10 IoT Core, versión de noviembre de 2015.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-105">This document describes the steps to enable Internet Connection Sharing (ICS) on a device running Windows 10 IoT Core November 2015 Release.</span></span> <span data-ttu-id="b4c5c-106">El objetivo es compartir una conexión a Internet entre un punto de acceso Wi-Fi de software (SoftAP) y un adaptador Ethernet.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-106">The objective is to share an Internet connection between a software Wi-Fi access point (SoftAP) and an Ethernet adapter.</span></span> <span data-ttu-id="b4c5c-107">Si usa la versión de aniversario de Windows 10 IoT Core, consulte el [tutorial de conexión compartida a Internet](InternetConnectionSharing.md).</span><span class="sxs-lookup"><span data-stu-id="b4c5c-107">If you are using the Windows 10 IoT Core Anniversary Release please refer to the [Internet Connection Sharing Tutorial](InternetConnectionSharing.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4c5c-108">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b4c5c-108">Prerequisites</span></span>

* <span data-ttu-id="b4c5c-109">Dispositivo que ejecuta la versión de noviembre 2015 de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-109">Device running Windows 10 IoT Core November 2015 Release.</span></span>
* <span data-ttu-id="b4c5c-110">Dispositivo USB Wi-Fi capaz de iniciar un SoftAP.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-110">Wi-Fi USB device capable of starting a SoftAP.</span></span> <span data-ttu-id="b4c5c-111">Consulte la lista de [compatibilidad de hardware](../learn-about-hardware/HardwareCompatList.md) para dispositivos USB Wi-Fi compatibles.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-111">Please refer to the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md) for supported Wi-Fi USB devices.</span></span>
* <span data-ttu-id="b4c5c-112">Conexión Ethernet con acceso a Internet.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-112">Ethernet connection with Internet Access.</span></span>


## <a name="setup"></a><span data-ttu-id="b4c5c-113">Configuración</span><span class="sxs-lookup"><span data-stu-id="b4c5c-113">Setup</span></span>

### <a name="step-1-gathering-network-information"></a><span data-ttu-id="b4c5c-114">Paso 1: recopilar información de red</span><span class="sxs-lookup"><span data-stu-id="b4c5c-114">Step 1: Gathering Network Information</span></span>

1. <span data-ttu-id="b4c5c-115">Arranque del dispositivo con la llave Wi-Fi conectada, cable Ethernet enchufado.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-115">Boot up device with Wi-Fi dongle plugged in, Ethernet cable plugged in.</span></span>
2. <span data-ttu-id="b4c5c-116">Inicie SoftAP desde el dispositivo IoT Core.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-116">Start SoftAP from the IoT Core device.</span></span>

   <span data-ttu-id="b4c5c-117">De forma predeterminada, las imágenes proporcionadas por Microsoft inician una aplicación de incorporación de IoT que configurará un SoftAP si la radio Wi-Fi es compatible y no se ha agregado ningún perfil de WLAN.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-117">By default, the Microsoft provided images start an IoT Onboarding application that will setup a SoftAP if Wi-Fi radio is capable and no WLAN profile has been added.</span></span> <span data-ttu-id="b4c5c-118">Para iniciar SoftAP, las aplicaciones para UWP pueden usar la [API Windows. Devices. WiFiDirect. WiFiDirectAdvertisementPublisher](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span><span class="sxs-lookup"><span data-stu-id="b4c5c-118">To start SoftAP, UWP applications can use the [Windows.Devices.WiFiDirect.WiFiDirectAdvertisementPublisher API](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.wifidirectadvertisementpublisher.aspx).</span></span> <span data-ttu-id="b4c5c-119">El código fuente de la aplicación de incorporación de IoT puede estar en GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span><span class="sxs-lookup"><span data-stu-id="b4c5c-119">The source code for the IoT Onboarding application can be on GitHub [IoTOnboarding](https://github.com/ms-iot/samples/tree/develop/IotOnboarding).</span></span>

   <span data-ttu-id="b4c5c-120">Grabe el SSID de la red SoftAP.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-120">Record the SSID of the SoftAP network.</span></span> <span data-ttu-id="b4c5c-121">Lo necesitará más adelante para conectarse a su dispositivo de IoT Core a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-121">You will need it later to connect to your IoT Core device via Wi-Fi.</span></span> <span data-ttu-id="b4c5c-122">En el caso de la aplicación de incorporación de IoT, el SSID comenzará con "AJ\_SoftAPSsid\_" y se puede cambiar en el [archivo](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml)de configuración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-122">For IoT Onboarding application the SSID will start with "AJ\_SoftAPSsid\_" and can be changed in application's configuration [file](https://github.com/ms-iot/samples/blob/develop/IotOnboarding/IoTOnboardingTask/Config.xml).</span></span>

3. <span data-ttu-id="b4c5c-123">Conéctese de forma remota al dispositivo de IoT Core [mediante SSH](ssh.md).</span><span class="sxs-lookup"><span data-stu-id="b4c5c-123">Remotely connect to the IoT Core device [using ssh](ssh.md).</span></span>
4. <span data-ttu-id="b4c5c-124">Recopile información acerca de las redes de dispositivos buscando los índices y las descripciones de los dispositivos de red.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-124">Collect information about device networks by finding network device indexes and descriptions.</span></span> <span data-ttu-id="b4c5c-125">Esto es necesario para declarar las redes que se van a enlazar.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-125">This is needed to declare which networks to bridge.</span></span>

   <span data-ttu-id="b4c5c-126">En el dispositivo, ejecute **Route Print** y recopile los datos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b4c5c-126">On device, run **route print** and collect the following data:</span></span>

   * <span data-ttu-id="b4c5c-127">Registra el índice de red de la interfaz pública del Ethernet.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-127">Record PUBLIC Interface network index for the Ethernet.</span></span>
   * <span data-ttu-id="b4c5c-128">Registra el índice de red de la interfaz privada para SoftAP (por ejemplo, "adaptador virtual de Microsoft Wi-Fi Direct #2").</span><span class="sxs-lookup"><span data-stu-id="b4c5c-128">Record PRIVATE Interface network index for the SoftAP (e.g. “Microsoft Wi-Fi Direct Virtual Adapter #2”).</span></span>

   <span data-ttu-id="b4c5c-129">Por ejemplo, el SoftAP se expone a través del índice de la interfaz 5, la descripción del adaptador "adaptador virtual de Wi-Fi Direct de Microsoft #2".</span><span class="sxs-lookup"><span data-stu-id="b4c5c-129">For example, the SoftAP is exposed through interface index 5, adapter description “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span>

   ![imprimir ruta](../media/InternetConnectionSharing/internetconnectionsharing_route.png)

   <span data-ttu-id="b4c5c-131">En el dispositivo, ejecute **ipconfig/all** y recopile los datos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b4c5c-131">On device, run **ipconfig /all** and collect the following data:</span></span>
    
   * <span data-ttu-id="b4c5c-132">Registrar el nombre del adaptador de red de la interfaz privada para el SoftAP</span><span class="sxs-lookup"><span data-stu-id="b4c5c-132">Record PRIVATE Interface network adapter name for the SoftAP</span></span>

   <span data-ttu-id="b4c5c-133">Por ejemplo, si se ejecuta "ipconfig/all", se busca el adaptador específico denominado "conexión de área local \* 3" que tiene una descripción de "adaptador virtual de Microsoft Wi-Fi Direct #2".</span><span class="sxs-lookup"><span data-stu-id="b4c5c-133">For example, running "ipconfig /all" finds the specific adapter named “Local Area Connection\* 3” that has a description of “Microsoft Wi-Fi Direct Virtual Adapter #2”.</span></span> <span data-ttu-id="b4c5c-134">Use este método para buscar manualmente el nombre del adaptador de la descripción devuelta en "Route Print".</span><span class="sxs-lookup"><span data-stu-id="b4c5c-134">Use this method to manually find Adapter Name from the Description returned in “route print”.</span></span>

   ![ipconfig all](../media/InternetConnectionSharing/internetconnectionsharing_ipconfig.png)

### <a name="step-2-scripting-internet-connection-sharing-trigger"></a><span data-ttu-id="b4c5c-136">Paso 2: crear scripts para el desencadenador de conexión compartida a Internet</span><span class="sxs-lookup"><span data-stu-id="b4c5c-136">Step 2: Scripting Internet Connection Sharing trigger</span></span>

<span data-ttu-id="b4c5c-137">El inicio de conexión compartida a Internet entre dos redes requiere los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b4c5c-137">Starting Internet Connection Sharing between two networks requires the following steps:</span></span>

* <span data-ttu-id="b4c5c-138">Establezca las claves del registro para establecer las interfaces de red privadas (SoftAP) y públicas (Ethernet) en Bridge.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-138">Set registry keys to set private (SoftAP) and public (Ethernet) network interfaces to bridge.</span></span>
* <span data-ttu-id="b4c5c-139">Establezca las reglas de Firewall adecuadas.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-139">Set appropriate firewall rules.</span></span>
* <span data-ttu-id="b4c5c-140">Desactiva DHCP en la interfaz privada.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-140">Turns off DHCP on private interface.</span></span>
* <span data-ttu-id="b4c5c-141">Establece la dirección IP estática en la interfaz privada.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-141">Sets static IP address on private interface.</span></span>
* <span data-ttu-id="b4c5c-142">Inicia el servicio SharedAccess.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-142">Starts SharedAccess service.</span></span>
* <span data-ttu-id="b4c5c-143">Envía el código de comando "129" al servicio SharedAccess.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-143">Sends command code “129” to SharedAccess service.</span></span>


#### <a name="create-a-script-to-automate-the-ics-settings"></a><span data-ttu-id="b4c5c-144">Crear un script para automatizar la configuración de ICS</span><span class="sxs-lookup"><span data-stu-id="b4c5c-144">Create a script to automate the ICS settings</span></span>

<span data-ttu-id="b4c5c-145">A continuación se muestra un ejemplo de scripts y código para automatizar los pasos indicados anteriormente que se pueden integrar en la secuencia de inicio del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-145">Below is an example of a scripts and code to automate the steps listed above that can be integrated into the device startup sequence.</span></span> <span data-ttu-id="b4c5c-146">Cree un archivo de script (por ejemplo, **ConfigureICS. cmd**) con el siguiente contenido:</span><span class="sxs-lookup"><span data-stu-id="b4c5c-146">Create a script file (e.g. **ConfigureICS.cmd**) with the following content:</span></span>

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

<span data-ttu-id="b4c5c-147">Este script hará todo, excepto el servicio de inicio y detención de SharedAccess y no envía el comando de servicio.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-147">This script will do everything but start/stop SharedAccess service, and does not send service command.</span></span> <span data-ttu-id="b4c5c-148">Para las tareas a las que llama a SharedAccessUtility. exe, que debe crearse.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-148">For those tasks it calls to SharedAccessUtility.exe, which needs to be created.</span></span>

#### <a name="build-the-sharedaccessutility-application"></a><span data-ttu-id="b4c5c-149">Compilar la aplicación SharedAccessUtility</span><span class="sxs-lookup"><span data-stu-id="b4c5c-149">Build the SharedAccessUtility application</span></span>
<span data-ttu-id="b4c5c-150">En Visual Studio con [las extensiones de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) instaladas, cree un nuevo proyecto de Visual C++ aplicación de consola de Windows IOT Core en blanco denominado **SharedAccessUtility**.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-150">In Visual Studio with [Windows IoT Core Project Templates extensions](https://go.microsoft.com/fwlink/?linkid=847472) installed, create a new “Blank Windows IoT Core Console Application” Visual C++ project, named **SharedAccessUtility**.</span></span>

![VS nuevo proyecto](../media/InternetConnectionSharing/internetconnectionsharing_vs.png)

<span data-ttu-id="b4c5c-152">Reemplace el contenido de definimos. cpp por el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4c5c-152">Replace contents of ConsoleApplication.cpp with the following code:</span></span>

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

<span data-ttu-id="b4c5c-153">Compilación para la arquitectura de destino, por ejemplo, versión x86, y búsqueda de la salida **SharedAccessUtility. exe**</span><span class="sxs-lookup"><span data-stu-id="b4c5c-153">Build for target architecture, e.g. Release x86, and locate output **SharedAccessUtility.exe**</span></span>

### <a name="step-3-starting-internet-connection-sharing"></a><span data-ttu-id="b4c5c-154">Paso 3: iniciar la conexión compartida a Internet</span><span class="sxs-lookup"><span data-stu-id="b4c5c-154">Step 3: Starting Internet Connection Sharing</span></span>

1. <span data-ttu-id="b4c5c-155">Copie el script **ConfigICS. cmd** creado en el paso 2 en el dispositivo en alguna ubicación, por ejemplo, para `C:\test\`</span><span class="sxs-lookup"><span data-stu-id="b4c5c-155">Copy **ConfigICS.cmd** script created in Step 2 to the device in some location, e.g. to `C:\test\`</span></span>
2. <span data-ttu-id="b4c5c-156">Copie **SharedAccessUtility. exe** creado en el paso 2 en el dispositivo en la misma ubicación, por ejemplo, `C:\test`</span><span class="sxs-lookup"><span data-stu-id="b4c5c-156">Copy **SharedAccessUtility.exe** created in Step 2 to the device in the same location, e.g. `C:\test`</span></span>\
3. <span data-ttu-id="b4c5c-157">En el dispositivo, ejecute **C:\test\ConfigureICS.cmd Start [Public index] [Private index] [Private Adapter Name** ] en este ejemplo, lo que significa que <strong>C:\test\ConfigureICS.cmd start 4 5 "conexión de área local \* 3"</strong></span><span class="sxs-lookup"><span data-stu-id="b4c5c-157">On the device, run **C:\test\ConfigureICS.cmd start [public index] [private index] [private adapter name]** In this example, this would mean <strong>C:\test\ConfigureICS.cmd start 4 5 "Local Area Connection\* 3"</strong></span></span>

<span data-ttu-id="b4c5c-158">En este momento, el dispositivo ha habilitado el uso compartido de conexión a Internet para cualquier cliente conectado al SSID anunciado del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b4c5c-158">At this point the device has enabled Internet Connection Sharing for any client connected to the device’s advertised SSID.</span></span>
