---
title: Uso de Wi-Fi en el dispositivo Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar, de instalación y configuración de Wi-Fi en el dispositivo Windows 10 IoT Core.
keywords: Windows iot, Wi-Fi, el programa de instalación, los dispositivos
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514800"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a><span data-ttu-id="fc4bc-104">Uso de Wi-Fi en el dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="fc4bc-104">Using WiFi on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="fc4bc-105">Wi-Fi se admite en dispositivos Windows 10 IoT Core mediante el uso de un adaptador USB Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-105">WiFi is supported on Windows 10 IoT Core devices through the use of a USB WiFi adapter.</span></span> <span data-ttu-id="fc4bc-106">Uso de Wi-Fi proporciona toda la funcionalidad de una conexión con cable, incluidos [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md)y depurar la aplicación e implementación.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-106">Using WiFi provides all the functionality of a wired connection, including [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md), and application debugging and deployment.</span></span>

> [!NOTE]
> <span data-ttu-id="fc4bc-107">Conexión de un cable Ethernet con cable invalidará Wi-Fi como la interfaz de red predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-107">Plugging in a wired Ethernet cable will override WiFi as the default network interface.</span></span>

### <a name="supported-adapters"></a><span data-ttu-id="fc4bc-108">Adaptadores compatibles</span><span class="sxs-lookup"><span data-stu-id="fc4bc-108">Supported Adapters</span></span>
<span data-ttu-id="fc4bc-109">Una lista de adaptadores de red Wi-Fi que se han probado en Windows 10 IoT Core puede encontrarse en nuestra [Hardware admite](../learn-about-hardware/HardwareCompatList.md) página.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-109">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span>

### <a name="configuring-wifi"></a><span data-ttu-id="fc4bc-110">Configuración de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="fc4bc-110">Configuring WiFi</span></span>
<span data-ttu-id="fc4bc-111">Para utilizar Wi-Fi, deberá proporcionar las credenciales de red Wi-Fi a Windows 10 IoT core.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-111">To use WiFi, you'll need to provide Windows 10 IoT core with the WiFi network credentials.</span></span> <span data-ttu-id="fc4bc-112">Además de la documentación sobre cómo compilar la aplicación complementaria y soluciones personalizadas de WPS, hay varias opciones diferentes para hacerlo, por lo que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-112">In addition to documentation on how to build companion app and WPS custom solutions, there are a few different options for doing so listed below.</span></span>

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a><span data-ttu-id="fc4bc-113">Aplicación personalizada complementaria y ejemplos de incorporación de Wi-Fi WPS</span><span class="sxs-lookup"><span data-stu-id="fc4bc-113">Custom Companion App & WPS Wi-Fi Onboarding Samples</span></span>

<span data-ttu-id="fc4bc-114">Actualmente, se ofrecen una serie de formas para que los desarrolladores crear una solución de incorporación de red Wi-Fi personalizado para su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-114">Currently, we offer a number of ways for developers to build a custom wifi onboarding solution for their device.</span></span> 

> | <span data-ttu-id="fc4bc-115">Muestras</span><span class="sxs-lookup"><span data-stu-id="fc4bc-115">Samples</span></span> | <span data-ttu-id="fc4bc-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="fc4bc-116">Description</span></span> | <span data-ttu-id="fc4bc-117">Ventajas</span><span class="sxs-lookup"><span data-stu-id="fc4bc-117">Benefits</span></span>  |  <span data-ttu-id="fc4bc-118">Inconvenientes</span><span class="sxs-lookup"><span data-stu-id="fc4bc-118">Drawbacks</span></span>  |
> |-------------|----------|---------|---------|
> | [<span data-ttu-id="fc4bc-119">Aplicación complementaria</span><span class="sxs-lookup"><span data-stu-id="fc4bc-119">Companion App</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | <span data-ttu-id="fc4bc-120">Creación de una aplicación simple que puede configurar Wi-Fi su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-120">Create a simple Xamarin app that can configure your device's Wi-Fi.</span></span> |  <span data-ttu-id="fc4bc-121">Fácil de usar; Puntas o sin periféricos de IoT Core; Los clientes funcionan en varias plataformas</span><span class="sxs-lookup"><span data-stu-id="fc4bc-121">Simple to use; Headed or headless for IoT Core; Clients work cross-platform</span></span> | <span data-ttu-id="fc4bc-122">Programador crea su propio protocolo; requiere que el desarrollador implementar la seguridad</span><span class="sxs-lookup"><span data-stu-id="fc4bc-122">Developer is creating his or her own protocol; requires developer to implement security</span></span> |
> | [<span data-ttu-id="fc4bc-123">Incorporación de IoT con RFCOMM de Bluetooth</span><span class="sxs-lookup"><span data-stu-id="fc4bc-123">IoT Onboarding with Bluetooth RFCOMM</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | <span data-ttu-id="fc4bc-124">Crear soluciones para configurar el dispositivo sin periféricos de IoT para conectar con su red Wi-Fi mediante RFCOMM de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-124">Create solution to configure your headless IoT device to connect with your Wi-Fi using Bluetooth RFCOMM.</span></span>  | <span data-ttu-id="fc4bc-125">Relevantes en dispositivos con cabezal o sin periféricos; Usa tecnologías conocidas y conceptos: No requiere de dispositivo IoT para iniciar un SoftAP; No es necesario ajustar la configuración de firewall</span><span class="sxs-lookup"><span data-stu-id="fc4bc-125">Relevant in headed or headless devices; Uses familiar technologies and concepts; Does not require IoT device to start a SoftAP; Does not need to adjust firewall settings</span></span> | <span data-ttu-id="fc4bc-126">Requiere compatibilidad con Bluetooth para dispositivos de cliente y servidor; Ejemplo proporciona sólo la aplicación cliente para Windows 10; Servidor aplicación pre-defines/codifica los nombres de los dispositivos cliente.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-126">Requires Bluetooth support for client and server devices; Sample only provides client app for Windows 10; Server app pre-defines/hard-codes the names of the client device.</span></span> |
> | [<span data-ttu-id="fc4bc-127">Incorporación de IoT con AllJoyn</span><span class="sxs-lookup"><span data-stu-id="fc4bc-127">IoT Onboarding with AllJoyn</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | <span data-ttu-id="fc4bc-128">Unirse de forma remota el dispositivo de IoT sin periféricos con la red Wi-Fi doméstica.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-128">Remotely join your headless IoT device with your home Wi-Fi network.</span></span> | <span data-ttu-id="fc4bc-129">Funciona con AllJoyn</span><span class="sxs-lookup"><span data-stu-id="fc4bc-129">Works with AllJoyn</span></span> | <span data-ttu-id="fc4bc-130">Compatibilidad para AllJoyn está en desuso</span><span class="sxs-lookup"><span data-stu-id="fc4bc-130">Some support for AllJoyn is deprecated</span></span> |
> | <span data-ttu-id="fc4bc-131">Wi-Fi Protected Setup (WPS) API para los dispositivos</span><span class="sxs-lookup"><span data-stu-id="fc4bc-131">Wi-Fi Protected Setup (WPS) APIs for devices</span></span> | <span data-ttu-id="fc4bc-132">Ejecutar la detección WPS para consultar los métodos WPS admitidos por la red.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-132">Perform WPS discovery to query the WPS methods supported by the network.</span></span> | <span data-ttu-id="fc4bc-133">Simplemente Aproveche el [WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) y [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) métodos para conectar dispositivos de wi-fi a redes específicas.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-133">Simply leverage the [WiFiAdapter.GetWpsConfigurationAsync(WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) and [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) methods to connect wi-fi devices to specific networks.</span></span> | <span data-ttu-id="fc4bc-134">Deberá familiarizarse con estas API aprovecharlas.; solo es compatible con enrutadores compatibles con WPS</span><span class="sxs-lookup"><span data-stu-id="fc4bc-134">You will need to become familiar with these APIs to leverage them.; only compatible with WPS-enabled routers</span></span>|

## <a name="headed-options"></a><span data-ttu-id="fc4bc-135">Opciones de punta:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-135">Headed Options:</span></span>

### <a name="option-1-startup-configuration"></a><span data-ttu-id="fc4bc-136">Opción 1: Configuración de inicio</span><span class="sxs-lookup"><span data-stu-id="fc4bc-136">Option 1: Startup Configuration</span></span>
<span data-ttu-id="fc4bc-137">**Requisito previo:** El dispositivo de Windows 10 IoT core necesita un mouse, teclado, mostrar y adaptador de Wi-Fi USB conectado</span><span class="sxs-lookup"><span data-stu-id="fc4bc-137">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="fc4bc-138">La primera vez que arranque Windows 10 IoT Core con un adaptador USB Wi-Fi compatible, se le mostrará una pantalla de configuración.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-138">The first time you boot Windows 10 IoT Core with a supported USB WiFi adapter, you will be presented with a configuration screen.</span></span>
<span data-ttu-id="fc4bc-139">En la pantalla de configuración, seleccione la red Wi-Fi que le gustaría conectar a y proporcionar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-139">On the configuration screen, select the WiFi network you would like to connect to and supply the password.</span></span> <span data-ttu-id="fc4bc-140">Haga clic en **conectar** para iniciar la conexión.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-140">Click **connect** to initiate the connection.</span></span>

![Pantalla de inicio de configuración de Wi-Fi](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a><span data-ttu-id="fc4bc-142">Opción 2: Configuración de la aplicación predeterminada</span><span class="sxs-lookup"><span data-stu-id="fc4bc-142">Option 2: Default App Configuration</span></span>
<span data-ttu-id="fc4bc-143">**Requisito previo:** El dispositivo de Windows 10 IoT core necesita un mouse, teclado, mostrar y adaptador de Wi-Fi USB conectado</span><span class="sxs-lookup"><span data-stu-id="fc4bc-143">**Prerequisite:** The Windows 10 IoT core device needs a mouse, keyboard, display, and USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="fc4bc-144">Configuración de Wi-Fi de forma alternativa es usar la aplicación predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-144">An alternative way to configure WiFi is to use the default app.</span></span> <span data-ttu-id="fc4bc-145">Puede utilizarlo para configurar o modificar la configuración de Wi-Fi después de que el dispositivo se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-145">You can use this to configure or modify WiFi settings after the device has booted.</span></span>

1. <span data-ttu-id="fc4bc-146">Haga clic en el icono de configuración en forma de engranaje en la página principal</span><span class="sxs-lookup"><span data-stu-id="fc4bc-146">Click on the gear-shaped settings icon on the homepage</span></span>
2. <span data-ttu-id="fc4bc-147">Seleccione **Wi-Fi & red** en el panel izquierdo</span><span class="sxs-lookup"><span data-stu-id="fc4bc-147">Select **Network & Wi-Fi** in the left pane</span></span>
3. <span data-ttu-id="fc4bc-148">Haga clic en la red Wi-Fi que desea conectarse.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-148">Click on the WiFi network you want to connect to.</span></span> <span data-ttu-id="fc4bc-149">Escriba la contraseña si se le solicita y haga clic en **Connect**</span><span class="sxs-lookup"><span data-stu-id="fc4bc-149">Supply the password if prompted, and click **Connect**</span></span>

![Configuración de Wi-Fi de aplicación predeterminada](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a><span data-ttu-id="fc4bc-151">Opciones sin periféricos:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-151">Headless Options:</span></span>




### <a name="option-1-web-based-configuration"></a><span data-ttu-id="fc4bc-152">Opción 1: Configuración basada en Web</span><span class="sxs-lookup"><span data-stu-id="fc4bc-152">Option 1: Web-Based Configuration</span></span>
<span data-ttu-id="fc4bc-153">**Requisito previo:** El dispositivo ya debe estar conectado a la red local a través de Ethernet y debe conectado un adaptador de USB Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="fc4bc-153">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in</span></span>

<span data-ttu-id="fc4bc-154">Si tiene dispositivos un con ninguna interfaz de usuario, mostrar o dispositivos de entrada, puede configurar a través de la [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="fc4bc-154">If you have device a with no UI, display, or input devices, you can still configure it through the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>
<span data-ttu-id="fc4bc-155">En **panel de Windows 10 IoT Core**, *haga clic en* en el **abrir en el Portal de dispositivo** icono para el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-155">In **Windows 10 IoT Core Dashboard**, *Click* on the **Open in Device Portal** icon for your device.</span></span>

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. <span data-ttu-id="fc4bc-156">Escriba **administrador** para el nombre de usuario y proporcione la contraseña (p@ssw0rd de forma predeterminada)</span><span class="sxs-lookup"><span data-stu-id="fc4bc-156">Enter **Administrator** for the username, and supply your password (p@ssw0rd by default)</span></span>
2. <span data-ttu-id="fc4bc-157">Haga clic en **red** en el panel izquierdo</span><span class="sxs-lookup"><span data-stu-id="fc4bc-157">Click on **Network** in the left-hand pane</span></span>
3. <span data-ttu-id="fc4bc-158">En **redes disponibles**, seleccione que le gustaría conectar a y proporcionar las credenciales de conexión de red.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-158">Under **Available networks**, select network you would like to connect to and supply the connection credentials.</span></span> <span data-ttu-id="fc4bc-159">Haga clic en **Connect** para iniciar la conexión</span><span class="sxs-lookup"><span data-stu-id="fc4bc-159">Click **Connect** to initiate the connection</span></span>

![Configuración de Wi-Fi basado en Web](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a><span data-ttu-id="fc4bc-161">Opción 2: Conectarse mediante perfiles de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="fc4bc-161">Option 2: Connect using WiFi Profiles</span></span>

<span data-ttu-id="fc4bc-162">**Requisito previo:** El dispositivo ya debe estar conectado a la red local a través de Ethernet y debe conectado un adaptador de USB Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-162">**Prerequisite:** Your device will already need to be connected to your local network through Ethernet and should have a USB WiFi Adapter plugged in.</span></span> <span data-ttu-id="fc4bc-163">También necesita un equipo Windows con la funcionalidad de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-163">You also need a Windows PC with WiFi capability.</span></span>

<span data-ttu-id="fc4bc-164">Se admite la configuración de Wi-Fi mediante perfiles inalámbricos en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-164">Setting up WiFi using wireless profiles is supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="fc4bc-165">Consulte [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) para obtener información detallada y ejemplos.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-165">See [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) for details and examples.</span></span>

1. <span data-ttu-id="fc4bc-166">Conectar el equipo de Windows a la red inalámbrica deseada y cree el archivo XML de perfil de Wi-Fi con estos comandos:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-166">Connect your Windows PC to the desired wireless network and create WiFi profile XML file with these commands:</span></span>

    * `netsh wlan show profiles` <span data-ttu-id="fc4bc-167">-> Buscar el nombre del perfil que acaba de agregar</span><span class="sxs-lookup"><span data-stu-id="fc4bc-167">-> find the name of the profile you just added</span></span>

    * `netsh wlan export profile name=<your profilename>`<span data-ttu-id="fc4bc-168">.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-168">.</span></span> <span data-ttu-id="fc4bc-169">El perfil se exportarán a un archivo XML</span><span class="sxs-lookup"><span data-stu-id="fc4bc-169">This will export the profile to an XML file</span></span>

2. <span data-ttu-id="fc4bc-170">Abra un **Explorador de archivos** ventana y en el tipo de la barra de dirección `\\<TARGET_DEVICE>\C$\` y, a continuación, presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-170">Open up a **File Explorer** window, and in the address bar type `\\<TARGET_DEVICE>\C$\` and then hit enter.</span></span>  <span data-ttu-id="fc4bc-171">En este caso concreto, `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo Windows 10 IoT Core:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-171">In this particular case, `<TARGET_DEVICE>` is either the name or the IP address of your Windows 10 IoT Core device:</span></span>

    ![SMB con el Explorador de archivos](../media/SetupWifi/smb1.png)

    <span data-ttu-id="fc4bc-173">Si se le pide un nombre de usuario y contraseña, utilice las credenciales siguientes:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-173">If you are prompted for a user name and password, use the following credentials:</span></span>

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![SMB con el Explorador de archivos](../media/SetupWifi/cred1.png)

> [!NOTE]
> <span data-ttu-id="fc4bc-175">Es **recomienda** que actualizar la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-175">It is **highly recommended** that you update the default password for the Administrator account.</span></span>  <span data-ttu-id="fc4bc-176">Siga las instrucciones que encontrará [aquí](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="fc4bc-176">Please follow the instructions found [here](../connect-your-device/PowerShell.md).</span></span>

3. <span data-ttu-id="fc4bc-177">Copie el archivo XML de perfil de Wi-Fi exportado desde el equipo de Windows para el dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="fc4bc-177">Copy the exported WiFi profile XML file from the Windows PC to your Windows 10 IoT Core device</span></span>

4. <span data-ttu-id="fc4bc-178">Conéctese a su dispositivo con [PowerShell](../connect-your-device/PowerShell.md) y agregue el nuevo perfil de Wi-Fi a su dispositivo mediante la ejecución de los siguientes comandos</span><span class="sxs-lookup"><span data-stu-id="fc4bc-178">Connect to your device using [PowerShell](../connect-your-device/PowerShell.md) and add the new WiFi profile to your device by executing the following commands</span></span>

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. <span data-ttu-id="fc4bc-179">Conecte el dispositivo de Windows 10 IoT Core a una red inalámbrica a través de netsh</span><span class="sxs-lookup"><span data-stu-id="fc4bc-179">Connect the Windows 10 IoT Core device to wireless network via netsh</span></span>

    * `netsh wlan connect name=<profile name>`

6. <span data-ttu-id="fc4bc-180">Compruebe que el dispositivo está conectado a la red inalámbrica y puede conectarse a internet</span><span class="sxs-lookup"><span data-stu-id="fc4bc-180">Verify that your device is connected to the wireless network and can reach the internet</span></span>

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a><span data-ttu-id="fc4bc-181">Conexión a redes WPA2-PSK Personal</span><span class="sxs-lookup"><span data-stu-id="fc4bc-181">Connecting to WPA2-PSK Personal networks</span></span>

<span data-ttu-id="fc4bc-182">Si necesita conectarse a una red Wi-Fi de WPA2-PSK Personal, siga las instrucciones anteriores en primer lugar, pero realizar los cambios siguientes en el archivo XML.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-182">If you need to connect to a WPA2-PSK Personal WiFi network, follow the instructions above first, but make the following changes to the XML file.</span></span> <span data-ttu-id="fc4bc-183">La única diferencia es que, cuando su PC de Windows se exporta el código XML cifra la contraseña.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-183">The only difference is that when your Windows PC exports the XML it encrypts the password.</span></span>

> [!WARNING] 
> <span data-ttu-id="fc4bc-184">Esto hará que la conexión no segura.</span><span class="sxs-lookup"><span data-stu-id="fc4bc-184">This will make your connection insecure.</span></span>

<span data-ttu-id="fc4bc-185">Perfil XML exportado desde PC Windows:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-185">Profile XML exported from Windows PC:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


<span data-ttu-id="fc4bc-186">Los cambios necesitan para trabajar en Windows 10 IoT Core:</span><span class="sxs-lookup"><span data-stu-id="fc4bc-186">Changes needed to work on Windows 10 IoT Core:</span></span>

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
