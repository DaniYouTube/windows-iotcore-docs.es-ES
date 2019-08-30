---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo usar el portal de dispositivos de Windows para configurar y administrar el dispositivo de forma remota.
keywords: Windows IOT, Windows Device portal, Remote, portal de dispositivos
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412149"
---
# <a name="windows-device-portal"></a><span data-ttu-id="734ae-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="734ae-104">Windows Device Portal</span></span>
   <span data-ttu-id="734ae-105">Windows Device portal (WDP) le permite configurar y administrar el dispositivo de forma remota a través de la red local.</span><span class="sxs-lookup"><span data-stu-id="734ae-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="734ae-106">Las características principales se documentan en la [Página de información general del portal de dispositivos de Windows](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="734ae-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![Página principal del portal de dispositivos](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="734ae-108">No use las imágenes del creador con fines comerciales.</span><span class="sxs-lookup"><span data-stu-id="734ae-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="734ae-109">Si se comercializa un dispositivo, debe usar una FFU personalizada para una seguridad óptima.</span><span class="sxs-lookup"><span data-stu-id="734ae-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="734ae-110">Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="734ae-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="734ae-111">Actualmente no se puede realizar la depuración del kernel activo para dispositivos ARM.</span><span class="sxs-lookup"><span data-stu-id="734ae-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="734ae-112">Estamos trabajando para solucionar este problema.</span><span class="sxs-lookup"><span data-stu-id="734ae-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="734ae-113">Si va a crear un dispositivo minorista abierto para la implementación comercial en una "instalación específica/limitada" (es decir, en fábrica o en tienda) donde el usuario final realiza la configuración final y documenta a los clientes que deben [obtener un certificado para WDP y lo instala en WDP y los exploradores y las contraseñas se cambian en WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), y se acepta el uso de WDP en esta instancia comercial estrecha.</span><span class="sxs-lookup"><span data-stu-id="734ae-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="734ae-114">Las imágenes comerciales de este escenario *no* deben incluir IOT_TOOLKIT, pero deben usar el paquete IOT_WEBBEXTN para extraer de WDP.</span><span class="sxs-lookup"><span data-stu-id="734ae-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="734ae-115">Documentación compartida</span><span class="sxs-lookup"><span data-stu-id="734ae-115">Shared Documentation</span></span>
<span data-ttu-id="734ae-116">WDP es una herramienta de desarrollo compartida entre todos los dispositivos de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="734ae-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="734ae-117">Cada producto tiene sus propias características únicas, pero la funcionalidad básica es la misma.</span><span class="sxs-lookup"><span data-stu-id="734ae-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="734ae-118">La documentación de las principales características se encuentra en la [Página de información general del portal de dispositivos de Windows](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span><span class="sxs-lookup"><span data-stu-id="734ae-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="734ae-119">El resto de la documentación siguiente será específico de IoT.</span><span class="sxs-lookup"><span data-stu-id="734ae-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="734ae-120">Configuración</span><span class="sxs-lookup"><span data-stu-id="734ae-120">Set up</span></span>

<span data-ttu-id="734ae-121">Hay dos maneras de poner en marcha el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="734ae-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="734ae-122">1. Panel de Windows 10 IoT</span><span class="sxs-lookup"><span data-stu-id="734ae-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="734ae-123">En primer lugar, querrá descargar el [Panel de IOT de Windows 10](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), una herramienta de desarrollador que facilita la configuración de nuevos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="734ae-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="734ae-124">Una vez que haya usado el panel para crear una imagen de Windows 10 IoT Core en el dispositivo, compruebe que el dispositivo aparece en "mis dispositivos".</span><span class="sxs-lookup"><span data-stu-id="734ae-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="734ae-125">Desde allí, use los puntos suspensivos en "acciones" para seleccionar "abrir en el portal de dispositivos".</span><span class="sxs-lookup"><span data-stu-id="734ae-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="734ae-126">Desde allí, se le dirigirá a la página de autenticación del portal de dispositivos, donde, a menos que haya cambiado las credenciales inicialmente, las credenciales predeterminadas son:</span><span class="sxs-lookup"><span data-stu-id="734ae-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="734ae-127">2. Browser</span><span class="sxs-lookup"><span data-stu-id="734ae-127">2. Browser</span></span>
<span data-ttu-id="734ae-128">Si no puede encontrar el dispositivo en el panel o prefiere omitir el uso del panel, también puede abrir el portal de dispositivos escribiendo la dirección IP del dispositivo más `:8080` al final.</span><span class="sxs-lookup"><span data-stu-id="734ae-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="734ae-129">Cuando se realiza correctamente, debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="734ae-129">When done correctly, it should look something like this:</span></span>


   ![IoTDashboard ver dispositivos](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="734ae-131">Características específicas de IoT</span><span class="sxs-lookup"><span data-stu-id="734ae-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="734ae-132">Configuración del dispositivo</span><span class="sxs-lookup"><span data-stu-id="734ae-132">Device Settings</span></span>

<span data-ttu-id="734ae-133">IoT Core agrega una casilla para habilitar o deshabilitar el [teclado en pantalla](../develop-your-app/OnScreenKeyboard.md) .</span><span class="sxs-lookup"><span data-stu-id="734ae-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="734ae-134">Esta casilla tiene un error conocido en el que se desactivará "Flash" en no comprobada.</span><span class="sxs-lookup"><span data-stu-id="734ae-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="734ae-135">Actualice la página (F5) después de hacer clic para asegurarse de que la casilla muestra el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="734ae-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="734ae-136">Aplicaciones</span><span class="sxs-lookup"><span data-stu-id="734ae-136">Apps</span></span>
<span data-ttu-id="734ae-137">Proporciona la funcionalidad de instalación y desinstalación de paquetes AppX y agrupaciones en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="734ae-138">![Lista de aplicaciones](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="734ae-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="734ae-139">IoT Core es único, ya que solo permite ejecutar una aplicación en primer plano al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="734ae-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="734ae-140">La lista de aplicaciones se modifica para asegurarse de que este es el caso.</span><span class="sxs-lookup"><span data-stu-id="734ae-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="734ae-141">En la columna **Inicio** , puede seleccionar tantas aplicaciones en segundo plano como se inicien de forma predeterminada, pero solo puede establecer una aplicación en primer plano.</span><span class="sxs-lookup"><span data-stu-id="734ae-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="734ae-142">Explorador de archivos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="734ae-142">App File Explorer</span></span>

<span data-ttu-id="734ae-143">El explorador de archivos de aplicación muestra los directorios a los que pueden acceder las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="734ae-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="734ae-144">CameraRoll se comparte entre todas las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="734ae-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="734ae-145">Los documentos se comparten entre todas las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="734ae-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="734ae-146">LocalAppData contiene carpetas específicas de cada aplicación.</span><span class="sxs-lookup"><span data-stu-id="734ae-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="734ae-147">Esta carpeta tendrá el mismo nombre que la aplicación y otras aplicaciones no podrán acceder a ella.</span><span class="sxs-lookup"><span data-stu-id="734ae-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="734ae-148">Depuración</span><span class="sxs-lookup"><span data-stu-id="734ae-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="734ae-149">Volcados de kernel</span><span class="sxs-lookup"><span data-stu-id="734ae-149">Kernel dumps</span></span>
![Depuración con volcados de kernel](../media/DevicePortal/Debug1.png)

<span data-ttu-id="734ae-151">Los bloqueos del sistema se registrarán automáticamente y estarán disponibles para su visualización a través de la herramienta de administración web.</span><span class="sxs-lookup"><span data-stu-id="734ae-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="734ae-152">Después, puede descargar el volcado del kernel e intentar averiguar lo que está ocurriendo.</span><span class="sxs-lookup"><span data-stu-id="734ae-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="734ae-153">Procesos de volcado</span><span class="sxs-lookup"><span data-stu-id="734ae-153">Process dumps</span></span>
![Depuración con volcados de proceso](../media/DevicePortal/Debug2.png)

<span data-ttu-id="734ae-155">Esto es similar a los volcados de kernel en vivo, pero para los procesos de modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="734ae-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="734ae-156">Al hacer clic en el botón **Descargar** se producirá un "minivolcado" y se descargará todo el estado de ese proceso.</span><span class="sxs-lookup"><span data-stu-id="734ae-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="734ae-157">Esto es adecuado para depurar procesos de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="734ae-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="734ae-158">Configuración de bloqueo de kernel</span><span class="sxs-lookup"><span data-stu-id="734ae-158">Kernel crash settings</span></span>
![Configuración de bloqueo de kernel](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="734ae-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="734ae-160">Bluetooth</span></span>
<span data-ttu-id="734ae-161">En esta página se muestran todos los dispositivos emparejados con Bluetooth y todos los dispositivos que se pueden detectar.</span><span class="sxs-lookup"><span data-stu-id="734ae-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="734ae-162">Para emparejar con otro dispositivo Bluetooth, coloque el dispositivo en modo de emparejamiento y espere a que aparezca en la lista dispositivos disponibles.</span><span class="sxs-lookup"><span data-stu-id="734ae-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![Lista de dispositivos Bluetooth](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="734ae-164">Haga clic en el **vínculo emparejar** para emparejar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="734ae-165">Si el dispositivo requiere un PIN para el emparejamiento, aparecerá un cuadro de mensaje que muestra el PIN.</span><span class="sxs-lookup"><span data-stu-id="734ae-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="734ae-166">Una vez que el dispositivo se empareja, se mostrará en la lista de dispositivos emparejados.</span><span class="sxs-lookup"><span data-stu-id="734ae-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="734ae-167">Para desemparejar el dispositivo, haga clic en **quitar**.</span><span class="sxs-lookup"><span data-stu-id="734ae-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="734ae-168">Una vez que navegue a la página de Bluetooth, el dispositivo será reconocible para otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="734ae-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="734ae-169">También puede encontrarla desde su PC/teléfono y emparejarla desde allí.</span><span class="sxs-lookup"><span data-stu-id="734ae-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="734ae-170">Puede encontrar más información sobre Bluetooth en la [Página de Bluetooth](https://go.microsoft.com/fwlink/?linkid=823223).</span><span class="sxs-lookup"><span data-stu-id="734ae-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="734ae-171">Incorporación de IoT</span><span class="sxs-lookup"><span data-stu-id="734ae-171">IoT Onboarding</span></span>

<span data-ttu-id="734ae-172">La incorporación de IoT proporciona compatibilidad para configurar las opciones de conectividad Wi-Fi de un dispositivo IoT.</span><span class="sxs-lookup"><span data-stu-id="734ae-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="734ae-173">**Conexión compartida a Internet (ICS)** Conexión compartida a Internet permite compartir el acceso a Internet del dispositivo con otros dispositivos conectados al dispositivo a través de la SoftAP Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="734ae-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="734ae-174">Para usar esta característica, el dispositivo de IoT de Windows 10 debe tener acceso a Internet (por ejemplo, mediante una conexión LAN cableada).</span><span class="sxs-lookup"><span data-stu-id="734ae-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="734ae-175">En ' Conectividad-> incorporación: > configuración de SoftAP ' haga clic en ' habilitar ' y establezca el nombre y la contraseña del SSID.</span><span class="sxs-lookup"><span data-stu-id="734ae-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="734ae-176">A continuación, en ' Conectividad-> conexión compartida a Internet ' para ' adaptador de punto de acceso ' Seleccione ' adaptador virtual de Microsoft Wi-FI Direct #2 ' y para ' adaptador de red compartido ' Seleccione el adaptador Ethernet con cable.</span><span class="sxs-lookup"><span data-stu-id="734ae-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="734ae-177">Por último, haga clic en ' iniciar acceso compartido '.</span><span class="sxs-lookup"><span data-stu-id="734ae-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="734ae-178">Una vez que se haya iniciado, conecte un dispositivo Wi-Fi compatible con el SoftAP en el dispositivo de IoT de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="734ae-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="734ae-179">Una vez establecida una conexión, el dispositivo Wi-Fi compatible con Wi-Fi podrá conectarse a Internet a través del dispositivo de IoT de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="734ae-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="734ae-180">ICS se deshabilita cuando existe un perfil de Wi-Fi en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="734ae-181">Por ejemplo, ICS se deshabilitará si se conecta a un punto de acceso Wi-Fi y activa "crear perfil (volver a conectar automáticamente)".</span><span class="sxs-lookup"><span data-stu-id="734ae-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="734ae-182">**Configuración de SofTap** La configuración de SoftAP le permite controlar si el SoftAP de su dispositivo está habilitado o no.</span><span class="sxs-lookup"><span data-stu-id="734ae-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="734ae-183">También proporciona un medio para configurar el SSID de SoftAP y la clave WPA2-PSK necesaria para conectar el SoftAP desde otro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="734ae-184">**Configuración de incorporación de AllJoyn** La configuración de incorporación de AllJoyn le permite controlar si la conexión Wi-Fi de su dispositivo puede configurarse a través del productor de incorporación de AllJoyn de su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="734ae-185">Cuando un dispositivo independiente que ejecuta una aplicación de consumidor de incorporación AllJoyn se conecta a su SoftAP de IoT de Windows 10, la aplicación de consumidor de incorporación AllJoyn se puede usar para configurar el adaptador Wi-Fi del dispositivo IoT.</span><span class="sxs-lookup"><span data-stu-id="734ae-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="734ae-186">Cuando está habilitada, la aplicación de productor de incorporación de AllJoyn (IoTOnboarding) usa el método de autenticación de ECDHE_NULL.</span><span class="sxs-lookup"><span data-stu-id="734ae-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="734ae-187">Para usar la incorporación de AllJoyn con las compilaciones de IoT de Windows 10 10.0.14393 o anterior, se requiere una actualización del ejemplo <strong>IotOnboarding</strong> que se puede [Descargar aquí](https://github.com/ms-iot/samples).</span><span class="sxs-lookup"><span data-stu-id="734ae-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="734ae-188">![Incorporación a la incorporación de](../media/DevicePortal/OnboardingAllJoyn.png)
AllJoyn![en ICS](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="734ae-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="734ae-189">El adaptador de punto de acceso es el adaptador WiFi que actúa como punto de acceso WiFi (normalmente tiene una dirección IP como 192.168.137.1).</span><span class="sxs-lookup"><span data-stu-id="734ae-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="734ae-190">Adaptador de red compartido es el adaptador que se conecta a Internet (por ejemplo: Adaptador Ethernet).</span><span class="sxs-lookup"><span data-stu-id="734ae-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![Incorporación a AP blando](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="734ae-192">El prefijo "AJ_" de SoftAP SSID se prefijará automáticamente si la incorporación de AllJoyn está habilitada y se ha posfijado con la dirección MAC del adaptador WiFi.</span><span class="sxs-lookup"><span data-stu-id="734ae-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="734ae-193">La frase de contraseña de SoftAP debe tener entre 8 y 63 caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="734ae-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="734ae-194">Configuración de TPM</span><span class="sxs-lookup"><span data-stu-id="734ae-194">TPM configuration</span></span>
<span data-ttu-id="734ae-195">El Módulo de plataforma segura (TPM) es un coprocesador criptográfico que incluye funcionalidades para la generación de números aleatorios, la generación segura de claves criptográficas y la limitación de su uso.</span><span class="sxs-lookup"><span data-stu-id="734ae-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="734ae-196">También incluye funcionalidades como la atestación remota y el almacenamiento sellado.</span><span class="sxs-lookup"><span data-stu-id="734ae-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="734ae-197">Para obtener información sobre el TPM y la seguridad en IoT Core, visite la página [creación de dispositivos seguros](../secure-your-device/BuildingSecureDevices.md) y la página [TPM](../secure-your-device/TPM.md) .</span><span class="sxs-lookup"><span data-stu-id="734ae-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="734ae-198">Limpet. exe que se usa para formar parte de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="734ae-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="734ae-199">A partir del 2018 de octubre, ahora está disponible como Porject de código abierto [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client)en.</span><span class="sxs-lookup"><span data-stu-id="734ae-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="734ae-200">Para facilitar las pruebas, tenemos una versión pregenerada no firmada de limpet. exe disponible y se puede descargar directamente desde WDP.</span><span class="sxs-lookup"><span data-stu-id="734ae-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="734ae-201">Solo tiene que ir a la pestaña "configuración de TPM" y hacer clic en el botón "instalar latest".</span><span class="sxs-lookup"><span data-stu-id="734ae-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="734ae-202">Esta versión de limpet. exe no se debe enviar con el producto final.</span><span class="sxs-lookup"><span data-stu-id="734ae-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="734ae-203">En su lugar, debe compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.</span><span class="sxs-lookup"><span data-stu-id="734ae-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="734ae-204">Configuración de clientes de Azure</span><span class="sxs-lookup"><span data-stu-id="734ae-204">Azure Clients configuration</span></span>

<span data-ttu-id="734ae-205">Los dispositivos de IoT se pueden administrar de forma remota a través de Cloud Services.</span><span class="sxs-lookup"><span data-stu-id="734ae-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="734ae-206">Azure proporciona un conjunto muy completo de servicios para habilitar tales escenarios.</span><span class="sxs-lookup"><span data-stu-id="734ae-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="734ae-207">Hemos creado un cliente de administración de dispositivos que complementa el servicio de aprovisionamiento de dispositivos (DPS) de Azure y el servicio IoT Hub de Azure en la plataforma Windows y que también expone varias características de administración de Windows.</span><span class="sxs-lookup"><span data-stu-id="734ae-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="734ae-208">Los clientes se proporcionarán como proyectos de código abierto.</span><span class="sxs-lookup"><span data-stu-id="734ae-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="734ae-209">Para que sea más fácil probarla, se proporcionarán archivos binarios predefinidos.</span><span class="sxs-lookup"><span data-stu-id="734ae-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="734ae-210">Puede usar la pestaña "clientes de Azure" de WDP para instalar y ejecutar esos archivos binarios de prueba.</span><span class="sxs-lookup"><span data-stu-id="734ae-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="734ae-211">Esta versión de las herramientas no se debe enviar con el producto final.</span><span class="sxs-lookup"><span data-stu-id="734ae-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="734ae-212">En su lugar, debe compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.</span><span class="sxs-lookup"><span data-stu-id="734ae-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="734ae-213">Esta documentación se actualizará una vez que los proyectos de código abierto estén disponibles para su consumo.</span><span class="sxs-lookup"><span data-stu-id="734ae-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="734ae-214">Control remoto</span><span class="sxs-lookup"><span data-stu-id="734ae-214">Remote</span></span>
<span data-ttu-id="734ae-215">El servidor remoto de IoT de Windows permite a los usuarios ver lo que muestra su dispositivo sin necesidad de conectar un monitor físico al teclado.</span><span class="sxs-lookup"><span data-stu-id="734ae-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="734ae-216">Información adicional</span><span class="sxs-lookup"><span data-stu-id="734ae-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="734ae-217">Cambiar el puerto predeterminado</span><span class="sxs-lookup"><span data-stu-id="734ae-217">Changing the default port</span></span>
 
1. <span data-ttu-id="734ae-218">Inicie PowerShell y [Conéctese a su dispositivo.](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="734ae-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="734ae-219">Descargue la herramienta [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) , genérelo y cópiela en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="734ae-220">Tomar posesión de la clave del registro para el servicio ejecutando</span><span class="sxs-lookup"><span data-stu-id="734ae-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="734ae-221">Establecer el puerto deseado modificando la configuración del registro</span><span class="sxs-lookup"><span data-stu-id="734ae-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="734ae-222">Reinicie el servicio de administración de webmanagement ejecutando a continuación o reiniciando el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="734ae-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="734ae-223">Usar HTTPS</span><span class="sxs-lookup"><span data-stu-id="734ae-223">Using HTTPS</span></span> 

<span data-ttu-id="734ae-224">Si desea usar HTTPS, tome primero la propiedad de la clave del registro como se describe en la sección anterior y establezca las claves del registro HttpsPort y EncryptionMode como se indica a continuación y, a continuación, reinicie el servicio de administración de webmanagement.</span><span class="sxs-lookup"><span data-stu-id="734ae-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="734ae-225">Aprovisionamiento portal de dispositivos con un certificado SSL personalizado</span><span class="sxs-lookup"><span data-stu-id="734ae-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="734ae-226">En Windows 10 Creators Update, el portal de dispositivos de Windows agregó una manera de que los administradores de dispositivos instalaran un certificado personalizado para su uso en la comunicación HTTPS.</span><span class="sxs-lookup"><span data-stu-id="734ae-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="734ae-227">Para obtener más información, [Lea la documentación de los documentos de Windows Device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span><span class="sxs-lookup"><span data-stu-id="734ae-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="734ae-228">Configuración de volcado de memoria para capturar el volcado de memoria:</span><span class="sxs-lookup"><span data-stu-id="734ae-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="734ae-229">Para capturar un volcado de memoria completo, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="734ae-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="734ae-230">Conéctese a un dispositivo IoT a través de WDP.</span><span class="sxs-lookup"><span data-stu-id="734ae-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="734ae-231">En depurar-> configuración de depuración-> configuración de bloqueo del kernel-> tipo de volcado de memoria.</span><span class="sxs-lookup"><span data-stu-id="734ae-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span> 

3. <span data-ttu-id="734ae-232">No Volcado de memoria completo (en uso de memoria).</span><span class="sxs-lookup"><span data-stu-id="734ae-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="734ae-233">Asegúrese de que el dispositivo se reinicie para que la configuración surta efecto.</span><span class="sxs-lookup"><span data-stu-id="734ae-233">Make sure the device is rebooted for the setting to take effect.</span></span> 
    
4. <span data-ttu-id="734ae-234">Compruebe que `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` está establecido en 0x1.</span><span class="sxs-lookup"><span data-stu-id="734ae-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="734ae-235">Actualice `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` a 0X0.</span><span class="sxs-lookup"><span data-stu-id="734ae-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="734ae-236">Asegúrese de que tiene suficiente espacio en el dispositivo para que se genere este volcado.</span><span class="sxs-lookup"><span data-stu-id="734ae-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="734ae-237">Puede configurar el cambio de la ubicación del volcado de página desde aquí:`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="734ae-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="734ae-238">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="734ae-238">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="734ae-239">Página de información general del portal de dispositivos de Windows</span><span class="sxs-lookup"><span data-stu-id="734ae-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
