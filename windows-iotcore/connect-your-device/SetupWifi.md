---
title: Usar Wi-Fi en el dispositivo de Windows 10 IoT Core
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar, configurar y configurar Wi-Fi en el dispositivo de Windows 10 IoT Core.
keywords: Windows IOT, Wi-Fi, instalación, dispositivos
ms.openlocfilehash: b8fa691da0560a741c0078d0030f10ae4ceb6c17
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918297"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="bddfa-104">Usar Wi-Fi en el dispositivo de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="bddfa-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="bddfa-105">Wi-Fi es compatible con dispositivos Windows 10 IoT Core mediante el uso de un adaptador de USB WiFi.</span><span class="sxs-lookup"><span data-stu-id="bddfa-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="bddfa-106">El uso de la red Wi-Fi proporciona toda la funcionalidad de una conexión cableada, como [ssh](../connect-your-device/SSH.md), [PowerShell](../connect-your-device/PowerShell.md), el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md)y la depuración e implementación de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="bddfa-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="bddfa-107">La conexión de un cable Ethernet cableado invalidará Wi-Fi como la interfaz de red predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bddfa-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="bddfa-108">Adaptadores admitidos</span><span class="sxs-lookup"><span data-stu-id="bddfa-108">Supported Adapters</span></span>
<span data-ttu-id="bddfa-109">Puede encontrar una lista de adaptadores de Wi-Fi que se han probado en Windows 10 IoT Core en nuestra página de [hardware compatible](../learn-about-hardware/HardwareCompatList.md) .</span><span class="sxs-lookup"><span data-stu-id="bddfa-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="bddfa-110">Configuración de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="bddfa-110">Configuring WiFi</span></span>
<span data-ttu-id="bddfa-111">Para usar Wi-Fi, debe proporcionar Windows 10 IoT Core con las credenciales de red WiFi.</span><span class="sxs-lookup"><span data-stu-id="bddfa-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="bddfa-112">Además de la documentación sobre cómo crear soluciones personalizadas de aplicación y WPS, hay varias opciones para hacerlo que se indican a continuación.</span><span class="sxs-lookup"><span data-stu-id="bddfa-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="bddfa-113">Ejemplos de incorporación de aplicaciones complementarias & WPS Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="bddfa-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="bddfa-114">Actualmente, ofrecemos varias maneras para que los desarrolladores creen una solución de incorporación Wi-Fi personalizada para su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bddfa-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="bddfa-115">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="bddfa-115">Samples</span></span> | <span data-ttu-id="bddfa-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="bddfa-116">Description</span></span> | <span data-ttu-id="bddfa-117">Ventajas</span><span class="sxs-lookup"><span data-stu-id="bddfa-117">Benefits</span></span>  |  <span data-ttu-id="bddfa-118">Desventajas</span><span class="sxs-lookup"><span data-stu-id="bddfa-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="bddfa-119">Aplicación complementaria</span><span class="sxs-lookup"><span data-stu-id="bddfa-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="bddfa-120">Cree una aplicación de Xamarin sencilla que pueda configurar la Wi-Fi del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bddfa-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="bddfa-121">Fácil de usar; Con cabeza o sin cabezal para IoT Core; Los clientes funcionan entre plataformas</span><span class="sxs-lookup"><span data-stu-id="bddfa-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="bddfa-122">El desarrollador está creando su propio protocolo; requiere que el desarrollador implemente la seguridad</span><span class="sxs-lookup"><span data-stu-id="bddfa-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="bddfa-123">Incorporación de IoT con Bluetooth RFCOMM</span><span class="sxs-lookup"><span data-stu-id="bddfa-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="bddfa-124">Cree una solución para configurar el dispositivo IoT sin periféricos con el fin de conectarse a la red Wi-Fi mediante Bluetooth RFCOMM.</span><span class="sxs-lookup"><span data-stu-id="bddfa-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="bddfa-125">Relevante en dispositivos con cabeza o sin periféricos; Utiliza tecnologías y conceptos conocidos; No requiere que el dispositivo IoT inicie un SoftAP; No es necesario ajustar la configuración del firewall</span><span class="sxs-lookup"><span data-stu-id="bddfa-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="bddfa-126">Requiere compatibilidad con Bluetooth para dispositivos cliente y servidor; El ejemplo solo proporciona la aplicación cliente para Windows 10; La aplicación de servidor define previamente o codifica los nombres del dispositivo cliente.</span><span class="sxs-lookup"><span data-stu-id="bddfa-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="bddfa-127">Incorporación de IoT con AllJoyn</span><span class="sxs-lookup"><span data-stu-id="bddfa-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="bddfa-128">Unir de forma remota el dispositivo de IoT sin periféricos con la red Wi-Fi doméstica.</span><span class="sxs-lookup"><span data-stu-id="bddfa-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="bddfa-129">Funciona con AllJoyn</span><span class="sxs-lookup"><span data-stu-id="bddfa-129">Works with AllJoyn</span></span> | <span data-ttu-id="bddfa-130">Parte de la compatibilidad con AllJoyn está en desuso.</span><span class="sxs-lookup"><span data-stu-id="bddfa-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="bddfa-131">API de instalación protegida Wi-Fi (WPS) para dispositivos</span><span class="sxs-lookup"><span data-stu-id="bddfa-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="bddfa-132">Realice la detección de WPS para consultar los métodos WPS admitidos por la red.</span><span class="sxs-lookup"><span data-stu-id="bddfa-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="bddfa-133">Simplemente aproveche los métodos [WiFiAdapter. GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) y [WiFiAdapter. ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) para conectar dispositivos Wi-Fi a redes específicas.</span><span class="sxs-lookup"><span data-stu-id="bddfa-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="bddfa-134">Deberá familiarizarse con estas API para aprovecharlas. solo compatible con enrutadores habilitados para WPS</span><span class="sxs-lookup"><span data-stu-id="bddfa-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="bddfa-135">Opciones de cabeza:</span><span class="sxs-lookup"><span data-stu-id="bddfa-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="bddfa-136">Opción 1: configuración de inicio</span><span class="sxs-lookup"><span data-stu-id="bddfa-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="bddfa-137">**Requisito previo:** El dispositivo Windows 10 IoT Core necesita un mouse, un teclado, una pantalla y un adaptador WiFi USB conectados</span><span class="sxs-lookup"><span data-stu-id="bddfa-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="bddfa-138">La primera vez que inicie Windows 10 IoT Core con un adaptador de USB WiFi compatible, aparecerá una pantalla de configuración.</span><span class="sxs-lookup"><span data-stu-id="bddfa-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="bddfa-139">En la pantalla Configuración, seleccione la red Wi-Fi a la que le gustaría conectarse y proporcione la contraseña.</span><span class="sxs-lookup"><span data-stu-id="bddfa-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="bddfa-140">Haga clic en **conectar** para iniciar la conexión.</span><span class="sxs-lookup"><span data-stu-id="bddfa-140">Click **connect** to initiate the connection.</span></span>

![Pantalla de configuración de Wi-Fi de inicio](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="bddfa-142">Opción 2: configuración de la aplicación predeterminada</span><span class="sxs-lookup"><span data-stu-id="bddfa-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="bddfa-143">**Requisito previo:** El dispositivo Windows 10 IoT Core necesita un mouse, un teclado, una pantalla y un adaptador WiFi USB conectados</span><span class="sxs-lookup"><span data-stu-id="bddfa-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="bddfa-144">Una manera alternativa de configurar Wi-Fi es usar la aplicación predeterminada.</span><span class="sxs-lookup"><span data-stu-id="bddfa-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="bddfa-145">Puede usar esta opción para configurar o modificar la configuración de Wi-Fi una vez arrancado el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bddfa-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="bddfa-146">Haga clic en el icono de configuración con forma de engranaje de la Página principal.</span><span class="sxs-lookup"><span data-stu-id="bddfa-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="bddfa-147">Seleccionar **red & Wi-Fi** en el panel izquierdo</span><span class="sxs-lookup"><span data-stu-id="bddfa-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="bddfa-148">Haga clic en la red Wi-Fi a la que desea conectarse.</span><span class="sxs-lookup"><span data-stu-id="bddfa-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="bddfa-149">Proporcione la contraseña si se le solicita y haga clic en **conectar** .</span><span class="sxs-lookup"><span data-stu-id="bddfa-149">Supply the password if prompted, and click **Connect**</span></span>

![Configuración de la aplicación Wi-Fi predeterminada](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="bddfa-151">Opciones sin periféricos:</span><span class="sxs-lookup"><span data-stu-id="bddfa-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="bddfa-152">Opción 1: configuración basada en Web</span><span class="sxs-lookup"><span data-stu-id="bddfa-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="bddfa-153">**Requisito previo:** El dispositivo ya tendrá que estar conectado a la red local a través de Ethernet y debe tener un adaptador de USB WiFi conectado</span><span class="sxs-lookup"><span data-stu-id="bddfa-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="bddfa-154">Si tiene el dispositivo a sin interfaz de usuario, pantalla o dispositivos de entrada, todavía puede configurarlo a través del [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="bddfa-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="bddfa-155">En el **Panel de Windows 10 IOT Core**, *haga clic* en el icono **abrir en el portal de dispositivos** del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bddfa-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="bddfa-156">Escriba **Administrador** para el nombre de usuario y proporcione la contraseña (p@ssw0rd de forma predeterminada)</span><span class="sxs-lookup"><span data-stu-id="bddfa-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="bddfa-157">Haga clic en **red** en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="bddfa-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="bddfa-158">En **redes disponibles**, seleccione la red a la que desea conectarse y proporcione las credenciales de conexión.</span><span class="sxs-lookup"><span data-stu-id="bddfa-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="bddfa-159">Haga clic en **conectar** para iniciar la conexión.</span><span class="sxs-lookup"><span data-stu-id="bddfa-159">Click **Connect** to initiate the connection</span></span>

![Configuración de Wi-Fi basada en Web](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="bddfa-161">Opción 2: conexión mediante perfiles de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="bddfa-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="bddfa-162">**Requisito previo:** El dispositivo ya tendrá que estar conectado a la red local a través de Ethernet y debe tener un adaptador de USB WiFi conectado.</span><span class="sxs-lookup"><span data-stu-id="bddfa-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="bddfa-163">También necesita un equipo Windows con capacidad WiFi.</span><span class="sxs-lookup"><span data-stu-id="bddfa-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="bddfa-164">La configuración de Wi-Fi mediante perfiles inalámbricos se admite en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="bddfa-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="bddfa-165">Consulte [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) para obtener más información y ejemplos.</span><span class="sxs-lookup"><span data-stu-id="bddfa-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="bddfa-166">Conecte el equipo Windows a la red inalámbrica deseada y cree el archivo XML del perfil de Wi-Fi con estos comandos:</span><span class="sxs-lookup"><span data-stu-id="bddfa-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * <span data-ttu-id="bddfa-167">`netsh wlan show profiles`-> Busque el nombre del perfil que acaba de agregar</span><span class="sxs-lookup"><span data-stu-id="bddfa-167">`netsh wlan show profiles` -> find the name of the profile you just added</span></span>

    * <span data-ttu-id="bddfa-168">`netsh wlan export profile name=<your profilename>`.</span><span class="sxs-lookup"><span data-stu-id="bddfa-168">`netsh wlan export profile name=<your profilename>`.</span></span> <span data-ttu-id="bddfa-169">Se exportará el perfil a un archivo XML.</span><span class="sxs-lookup"><span data-stu-id="bddfa-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="bddfa-170">Abra una ventana del **Explorador de archivos** y, en la barra de direcciones, escriba `\\<TARGET_DEVICE>\C$\` y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="bddfa-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="bddfa-171">En este caso concreto, `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo de Windows 10 IoT Core:</span><span class="sxs-lookup"><span data-stu-id="bddfa-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![SMB con el explorador de archivos](../media/SetupWifi/smb1.png)

    <span data-ttu-id="bddfa-173">Si se le pide un nombre de usuario y una contraseña, use las credenciales siguientes:</span><span class="sxs-lookup"><span data-stu-id="bddfa-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![SMB con el explorador de archivos](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="bddfa-175">Se **recomienda encarecidamente** que actualice la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="bddfa-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="bddfa-176">Siga las instrucciones que se encuentran [aquí](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="bddfa-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="bddfa-177">Copiar el archivo XML del perfil de Wi-Fi exportado del equipo de Windows en el dispositivo de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="bddfa-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="bddfa-178">Conéctese al dispositivo mediante [PowerShell](../connect-your-device/PowerShell.md) y agregue el nuevo perfil de Wi-Fi al dispositivo mediante la ejecución de los siguientes comandos.</span><span class="sxs-lookup"><span data-stu-id="bddfa-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="bddfa-179">Conexión del dispositivo Windows 10 IoT Core a la red inalámbrica a través de Netsh</span><span class="sxs-lookup"><span data-stu-id="bddfa-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="bddfa-180">Compruebe que el dispositivo está conectado a la red inalámbrica y puede conectarse a Internet.</span><span class="sxs-lookup"><span data-stu-id="bddfa-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="bddfa-181">Conexión a redes personales WPA2-PSK</span><span class="sxs-lookup"><span data-stu-id="bddfa-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="bddfa-182">Si necesita conectarse a una red Wi-Fi personal WiFi, siga primero las instrucciones anteriores, pero realice los cambios siguientes en el archivo XML.</span><span class="sxs-lookup"><span data-stu-id="bddfa-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="bddfa-183">La única diferencia es que cuando el equipo Windows exporta el XML, cifra la contraseña.</span><span class="sxs-lookup"><span data-stu-id="bddfa-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="bddfa-184">Esto hará que la conexión no sea segura.</span><span class="sxs-lookup"><span data-stu-id="bddfa-184">This will make your connection insecure.</span></span>

<span data-ttu-id="bddfa-185">Perfil XML exportado desde PC Windows:</span><span class="sxs-lookup"><span data-stu-id="bddfa-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="bddfa-186">Cambios necesarios para trabajar en Windows 10 IoT Core:</span><span class="sxs-lookup"><span data-stu-id="bddfa-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
