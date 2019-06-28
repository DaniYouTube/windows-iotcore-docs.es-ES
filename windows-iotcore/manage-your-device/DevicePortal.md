---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo usar el Windows Device Portal para configurar y administrar de forma remota el dispositivo.
keywords: portal de dispositivo remoto, de Windows iot, Windows Device Portal,
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412149"
---
# <a name="windows-device-portal"></a><span data-ttu-id="0e98a-104">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="0e98a-104">Windows Device Portal</span></span>
   <span data-ttu-id="0e98a-105">La herramienta Windows Device Portal (WDP) le permite configurar y administrar el dispositivo de forma remota a través de la red local.</span><span class="sxs-lookup"><span data-stu-id="0e98a-105">The Windows Device Portal (WDP) lets you configure and manage your device remotely over your local network.</span></span>
<span data-ttu-id="0e98a-106">Las características principales se documentan en el [página de información general de Windows Device Portal](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span><span class="sxs-lookup"><span data-stu-id="0e98a-106">The main features are documented on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)</span></span>

![Dispositivo principal del Portal](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> <span data-ttu-id="0e98a-108">No use maker imágenes para la comercialización.</span><span class="sxs-lookup"><span data-stu-id="0e98a-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="0e98a-109">Si se commercializing un dispositivo, debe usar un FFU personalizado para una seguridad óptima.</span><span class="sxs-lookup"><span data-stu-id="0e98a-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="0e98a-110">Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="0e98a-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!WARNING]
> <span data-ttu-id="0e98a-111">Depuración de kernel en vivo actualmente se producen errores para dispositivos ARM.</span><span class="sxs-lookup"><span data-stu-id="0e98a-111">Live kernel debug is currently failing for ARM devices.</span></span> <span data-ttu-id="0e98a-112">Estamos trabajando para conseguir que esto se ha corregido.</span><span class="sxs-lookup"><span data-stu-id="0e98a-112">We are working to get this fixed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e98a-113">Si está creando un dispositivo comercial abierto para la implementación comercial en una "instalación específico o limitado" (es decir, almacén de fábrica o comercial) donde el usuario final realiza la configuración final y documentar los clientes que deben [obtener una certificado de WDP e instalar en tanto WDP y conecta los exploradores y las contraseñas se cambian en WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), a continuación, uso de WDP en esta instancia comercial estrecha es aceptable.</span><span class="sxs-lookup"><span data-stu-id="0e98a-113">If you are building an open retail device for commercial deployment to a "specific/limited installation" (i.e. factory or retail store) where the end-user does the final configuration and you document your customers that they must [obtain a certificate for WDP and install it on both WDP and connecting browsers and passwords are changed on WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), then using WDP in this narrow commercial instance is acceptable.</span></span> <span data-ttu-id="0e98a-114">Imágenes de venta directa en este escenario deben seguir *no* incluyen IOT_TOOLKIT, pero debe usar el paquete IOT_WEBBEXTN para extraer WDP.</span><span class="sxs-lookup"><span data-stu-id="0e98a-114">Retail images in this scenario should still *not* include IOT_TOOLKIT, but should use the IOT_WEBBEXTN package to pull in WDP.</span></span> 

## <a name="shared-documentation"></a><span data-ttu-id="0e98a-115">Documentación compartida</span><span class="sxs-lookup"><span data-stu-id="0e98a-115">Shared Documentation</span></span>
<span data-ttu-id="0e98a-116">WDP es una herramienta de desarrollador que se comparte entre todos los dispositivos Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0e98a-116">WDP is a developer tool shared among all Windows 10 devices.</span></span> <span data-ttu-id="0e98a-117">Cada producto tiene sus propias características únicas, pero la funcionalidad básica es la misma.</span><span class="sxs-lookup"><span data-stu-id="0e98a-117">Each product has its own unique features, but the core functionality is the same.</span></span>
<span data-ttu-id="0e98a-118">Documentación de las características principales se encuentran en el [página de información general de Windows Device Portal](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span><span class="sxs-lookup"><span data-stu-id="0e98a-118">Documentation for the main features are found on the [Windows Device Portal overview page](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span> <span data-ttu-id="0e98a-119">El resto de la documentación siguiente será IoT específico.</span><span class="sxs-lookup"><span data-stu-id="0e98a-119">The rest of the documentation below will be IoT specific.</span></span>

## <a name="set-up"></a><span data-ttu-id="0e98a-120">Configuración</span><span class="sxs-lookup"><span data-stu-id="0e98a-120">Set up</span></span>

<span data-ttu-id="0e98a-121">Hay dos maneras de obtener el Windows Device Portal en marcha.</span><span class="sxs-lookup"><span data-stu-id="0e98a-121">There are two ways to go get the Windows Device Portal up and running.</span></span>

### <a name="1-windows-10-iot-dashboard"></a><span data-ttu-id="0e98a-122">1. Panel de Windows 10 IoT</span><span class="sxs-lookup"><span data-stu-id="0e98a-122">1. Windows 10 IoT Dashboard</span></span>

<span data-ttu-id="0e98a-123">En primer lugar, es conveniente que descargue el [panel de Windows 10 IoT](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), una herramienta para desarrolladores que facilita la configuración de nuevos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="0e98a-123">First, you'll want to download the [Windows 10 IoT Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), a developer tool that makes it easy to set up new devices.</span></span> <span data-ttu-id="0e98a-124">Una vez que ha usado el panel que se instalará una imagen de Windows 10 IoT Core en el dispositivo, compruebe que el dispositivo aparece en "Mis dispositivos".</span><span class="sxs-lookup"><span data-stu-id="0e98a-124">Once you've used the Dashboard to flash a Windows 10 IoT Core image onto your device, check that your device shows up under "My devices".</span></span> 

<span data-ttu-id="0e98a-125">Desde allí, use el botón de puntos suspensivos en "Acciones" para seleccionar "Abrir en Portal de dispositivos".</span><span class="sxs-lookup"><span data-stu-id="0e98a-125">From there, use the ellipses under "Actions" to select "Open in Device Portal".</span></span> <span data-ttu-id="0e98a-126">Desde allí, se le dirigirá a la página de autenticación de dispositivo Portal donde, a menos que cambie las credenciales inicialmente, las credenciales predeterminadas son:</span><span class="sxs-lookup"><span data-stu-id="0e98a-126">From there, you'll be taken to the Device Portal authentication page where, unless you changed the credentials initially, the default credentials are:</span></span> 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a><span data-ttu-id="0e98a-127">2. Browser</span><span class="sxs-lookup"><span data-stu-id="0e98a-127">2. Browser</span></span>
<span data-ttu-id="0e98a-128">Si no se puede encontrar el dispositivo en el panel o prefiere omitir el uso del panel, también puede abrir Device Portal escribiendo la dirección IP del dispositivo más `:8080` al final.</span><span class="sxs-lookup"><span data-stu-id="0e98a-128">If you cannot find your device in the dashboard or prefer to skip using the dashboard, you can also open the Device Portal by entering the IP address of your device plus `:8080` onto the end.</span></span> <span data-ttu-id="0e98a-129">Cuando se realiza correctamente, debe tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="0e98a-129">When done correctly, it should look something like this:</span></span>


   ![IoTDashboard ver dispositivos](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a><span data-ttu-id="0e98a-131">Características específicas de IoT</span><span class="sxs-lookup"><span data-stu-id="0e98a-131">IoT specific features</span></span>

### <a name="device-settings"></a><span data-ttu-id="0e98a-132">Configuración del dispositivo</span><span class="sxs-lookup"><span data-stu-id="0e98a-132">Device Settings</span></span>

<span data-ttu-id="0e98a-133">IoT Core agrega una casilla de verificación para habilitar o deshabilitar la [teclado en pantalla](../develop-your-app/OnScreenKeyboard.md)</span><span class="sxs-lookup"><span data-stu-id="0e98a-133">IoT Core adds a checkbox to enable or disable the [on-screen keyboard](../develop-your-app/OnScreenKeyboard.md)</span></span>
> [!NOTE]
> <span data-ttu-id="0e98a-134">Esta casilla de verificación tiene un problema conocido, donde "parpadeará" desde comprueba para que no es activado.</span><span class="sxs-lookup"><span data-stu-id="0e98a-134">This checkbox has a known bug where it will "flash" from checked to non-checked.</span></span> <span data-ttu-id="0e98a-135">Actualice la página (F5) después de hacer clic para asegurarse de que la casilla muestre el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="0e98a-135">Please refresh the page (F5) after clicking to ensure that the checkbox is showing your desired state.</span></span>

### <a name="apps"></a><span data-ttu-id="0e98a-136">Aplicaciones</span><span class="sxs-lookup"><span data-stu-id="0e98a-136">Apps</span></span>
<span data-ttu-id="0e98a-137">Proporciona funcionalidad de instalación o desinstalación de paquetes AppX y agrupaciones en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-137">Provides install/uninstall functionality for AppX packages and bundles on your device.</span></span>
<span data-ttu-id="0e98a-138">![Lista de aplicaciones](../media/DevicePortal/AppList.png)</span><span class="sxs-lookup"><span data-stu-id="0e98a-138">![App list](../media/DevicePortal/AppList.png)</span></span>

<span data-ttu-id="0e98a-139">IoT Core es único, que solo permite que una aplicación en primer plano ejecutar al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-139">IoT Core is unique in that it only allows one foreground app to run at one time.</span></span> <span data-ttu-id="0e98a-140">Para asegurarse de que este es el caso, se modifica la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="0e98a-140">The app list is modified to ensure that this is the case.</span></span> <span data-ttu-id="0e98a-141">En el **inicio** columna, puede seleccionar tantas aplicaciones en segundo plano para iniciarse de forma predeterminada, pero solo se puede establecer una aplicación en primer plano.</span><span class="sxs-lookup"><span data-stu-id="0e98a-141">Under the **STARTUP** column, you can select as many background applications to start by default, but can only set one foreground application.</span></span>  

### <a name="app-file-explorer"></a><span data-ttu-id="0e98a-142">Explorador de archivos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="0e98a-142">App File Explorer</span></span>

<span data-ttu-id="0e98a-143">El Explorador de archivos de la aplicación muestra los directorios que se pueden tener acceso sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="0e98a-143">The app file explorer shows the directories that your apps can access.</span></span>

* <span data-ttu-id="0e98a-144">CameraRoll se comparte entre todas las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="0e98a-144">CameraRoll is shared among all apps</span></span>
* <span data-ttu-id="0e98a-145">Documentos se comparte entre todas las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="0e98a-145">Documents is shared among all apps</span></span>
* <span data-ttu-id="0e98a-146">LocalAppData contiene carpetas específicas de cada aplicación.</span><span class="sxs-lookup"><span data-stu-id="0e98a-146">LocalAppData contains folders specific to each app.</span></span> <span data-ttu-id="0e98a-147">Esta carpeta será el mismo nombre que la aplicación y otras aplicaciones no pueden acceder a él.</span><span class="sxs-lookup"><span data-stu-id="0e98a-147">This folder will be the same name as your app and other apps cannot access it.</span></span>

### <a name="debugging"></a><span data-ttu-id="0e98a-148">Depuración</span><span class="sxs-lookup"><span data-stu-id="0e98a-148">Debugging</span></span>

#### <a name="kernel-dumps"></a><span data-ttu-id="0e98a-149">Volcados de memoria del núcleo</span><span class="sxs-lookup"><span data-stu-id="0e98a-149">Kernel dumps</span></span>
![Depuración de volcados de memoria del núcleo](../media/DevicePortal/Debug1.png)

<span data-ttu-id="0e98a-151">Los bloqueos del sistema será automáticamente registran y están disponibles para ver a través de la herramienta de administración web.</span><span class="sxs-lookup"><span data-stu-id="0e98a-151">Any system crashes will automatically be logged and available to view through the web management tool.</span></span>  <span data-ttu-id="0e98a-152">A continuación, puede descargar el volcado de memoria del núcleo e intentar averiguar qué está sucediendo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-152">You can then download the kernel dump and try to figure out what's going on.</span></span>

#### <a name="process-dumps"></a><span data-ttu-id="0e98a-153">Volcados de proceso</span><span class="sxs-lookup"><span data-stu-id="0e98a-153">Process dumps</span></span>
![Depuración de volcados de memoria de proceso](../media/DevicePortal/Debug2.png)

<span data-ttu-id="0e98a-155">Esto es similar a volcados de memoria del kernel en vivo, pero para los procesos de modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="0e98a-155">This is similar to Live kernel dumps, but for the user mode processes.</span></span> <span data-ttu-id="0e98a-156">Al hacer clic en el **descargar** botón provocarán un minivolcado' ', y se descargará todo el estado de ese proceso.</span><span class="sxs-lookup"><span data-stu-id="0e98a-156">Clicking the **download** button will cause a 'minidump', and the entire state of that process will be downloaded.</span></span> <span data-ttu-id="0e98a-157">Esto es útil para depurar procesos francesa.</span><span class="sxs-lookup"><span data-stu-id="0e98a-157">This is good for debugging hanging processes.</span></span>

#### <a name="kernel-crash-settings"></a><span data-ttu-id="0e98a-158">Configuración de bloqueo de kernel</span><span class="sxs-lookup"><span data-stu-id="0e98a-158">Kernel crash settings</span></span>
![Configuración de bloqueo de kernel](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a><span data-ttu-id="0e98a-160">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="0e98a-160">Bluetooth</span></span>
<span data-ttu-id="0e98a-161">Esta página muestra todos los dispositivos bluetooth emparejado y todos los dispositivos que son reconocibles.</span><span class="sxs-lookup"><span data-stu-id="0e98a-161">This page shows you all the bluetooth paired devices and all the devices which are discoverable.</span></span> <span data-ttu-id="0e98a-162">Para emparejar con otro dispositivo Bluetooth, el dispositivo entrará en modo de emparejamiento y espere a que aparezca en la lista dispositivos disponibles.</span><span class="sxs-lookup"><span data-stu-id="0e98a-162">To pair with another Bluetooth device, put the device in pairing mode and wait for it to appear in the available devices list.</span></span>  
![Lista de dispositivos Bluetooth](../media/DevicePortal/Bluetooth.png)

<span data-ttu-id="0e98a-164">Haga clic en **vínculo par** para emparejar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-164">Click on **Pair link** to pair the device.</span></span> <span data-ttu-id="0e98a-165">Si el dispositivo requiere un PIN para emparejamiento, aparecerá un cuadro de mensaje muestra el PIN.</span><span class="sxs-lookup"><span data-stu-id="0e98a-165">If the device requires a PIN for pairing, it will pop-up a message box displaying the PIN.</span></span> <span data-ttu-id="0e98a-166">Una vez que se corresponde el dispositivo, se mostrará en la lista de dispositivos emparejada.</span><span class="sxs-lookup"><span data-stu-id="0e98a-166">Once the device is paired, it will show up in the Paired devices list.</span></span> <span data-ttu-id="0e98a-167">Puede anular par haciendo clic en el dispositivo **quitar**.</span><span class="sxs-lookup"><span data-stu-id="0e98a-167">You can un-pair the device by clicking on **Remove**.</span></span> 

<span data-ttu-id="0e98a-168">Una vez que navegue a la página de Bluetooth, el dispositivo podrán detectar otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="0e98a-168">Once you navigate to the Bluetooth page, your device will be discoverable by other devices.</span></span> <span data-ttu-id="0e98a-169">También puede encontrarlo en su PC o teléfono y emparéjelo desde allí.</span><span class="sxs-lookup"><span data-stu-id="0e98a-169">You can also find it from your PC/Phone and pair it from there.</span></span>

<span data-ttu-id="0e98a-170">Encontrará más información sobre el bluetooth en el [bluetooth página](https://go.microsoft.com/fwlink/?linkid=823223).</span><span class="sxs-lookup"><span data-stu-id="0e98a-170">More information on bluetooth can be found on the [bluetooth page](https://go.microsoft.com/fwlink/?linkid=823223).</span></span>

### <a name="iot-onboarding"></a><span data-ttu-id="0e98a-171">Incorporación de IoT</span><span class="sxs-lookup"><span data-stu-id="0e98a-171">IoT Onboarding</span></span>

<span data-ttu-id="0e98a-172">IoT Onboarding proporciona compatibilidad para configurar las opciones de conectividad de Wi-Fi de un dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="0e98a-172">IoT Onboarding provides support for configuring an IoT device's Wi-Fi connectivity options.</span></span>

<span data-ttu-id="0e98a-173">**Conexión compartida a Internet (ICS)** conexión compartida a Internet le permite compartir el acceso a Internet del dispositivo con otros dispositivos conectados al dispositivo a través de la SoftAP Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="0e98a-173">**Internet Connection Sharing (ICS)** Internet Connection Sharing allows you to share the Internet access of your device with other devices connected to your device over the Wi-Fi SoftAP.</span></span>
<span data-ttu-id="0e98a-174">Para usar esta característica, debe tener acceso a internet (por ejemplo, mediante una conexión LAN con cable) el dispositivo de Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="0e98a-174">To use this feature, your Windows 10 IoT Device needs to have access to the internet (e.g. through a wired LAN connection).</span></span>  <span data-ttu-id="0e98a-175">En ' conectividad -> incorporación -> clic SoftAP configuración 'enable' y establezca el nombre SSID y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="0e98a-175">In 'Connectivity->Onboarding->SoftAP settings' click 'enable' and set SSID name and password.</span></span>  <span data-ttu-id="0e98a-176">A continuación, en "Conectividad -> conexión compartida a Internet" de "Adaptador Wi-FI de Microsoft directo Virtual #2", seleccione 'adaptador de punto de acceso' y 'adaptador de red compartida' Seleccione el adaptador ethernet con cable.</span><span class="sxs-lookup"><span data-stu-id="0e98a-176">Then in 'Connectivity->Internet connection sharing' for 'access point adapter' select "Microsoft Wi-FI Direct Virtual Adapter #2" and for 'shared network adapter' select your wired ethernet adapter.</span></span>  <span data-ttu-id="0e98a-177">Por último, haga clic en "start acceso compartido".</span><span class="sxs-lookup"><span data-stu-id="0e98a-177">Finally, click 'start shared access.'</span></span>  <span data-ttu-id="0e98a-178">Una vez iniciado, conecte un dispositivo de Wi-Fi habilitada independiente para el SoftAP en el dispositivo Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="0e98a-178">Once started, connect a separate Wi-Fi enabled device to the SoftAP on your Windows 10 IoT device.</span></span>  <span data-ttu-id="0e98a-179">Una vez establecida una conexión de su dispositivo Wi-Fi habilitada independiente será capaz de conectarse a internet a través de su dispositivo Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="0e98a-179">After a connection is established your separate Wi-Fi enabled device will be able to connect to the internet through your Windows 10 IoT device.</span></span>

> [!NOTE]
> <span data-ttu-id="0e98a-180">ICS está deshabilitado cuando existe un perfil de Wi-Fi en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-180">ICS is disabled when a Wi-Fi profile exists on the device.</span></span> <span data-ttu-id="0e98a-181">Por ejemplo, se deshabilitará ICS si se conecta a un punto de acceso Wi-Fi y compruebe "Crear perfil (automáticamente volver a conectar)".</span><span class="sxs-lookup"><span data-stu-id="0e98a-181">For example, ICS will be disabled if you connect to a Wi-Fi access point and check “Create profile (auto re-connect)”.</span></span>

<span data-ttu-id="0e98a-182">**Configuración de SoftAP** The SoftAP configuración le permite controlar si SoftAP su dispositivo está habilitada.</span><span class="sxs-lookup"><span data-stu-id="0e98a-182">**SoftAP Settings** The SoftAP Settings allow you to control whether or not your device's SoftAP is enabled.</span></span>  <span data-ttu-id="0e98a-183">También proporciona un medio para configurar su SoftAP SSID y la WPA2-PSK clave que son necesarios para conectar el SoftAP desde otro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-183">It also provides a means for configuring your SoftAP's SSID and the WPA2-PSK key which are necessary to connect the SoftAP from another device.</span></span>

<span data-ttu-id="0e98a-184">**Configuración de incorporación de AllJoyn** la configuración de incorporación de AllJoyn le permiten controlar o no conexión de Wi-Fi del dispositivo se puede configurar a través AllJoyn incorporación productor de su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-184">**AllJoyn Onboarding Settings** The AllJoyn Onboarding Settings allow you to control whether or not your device's Wi-Fi connection can configured through your device's AllJoyn Onboarding Producer.</span></span>  <span data-ttu-id="0e98a-185">Cuando un dispositivo independiente que se ejecuta un consumidor de incorporación de AllJoyn aplicación se conecta a su SoftAP de Windows 10 IoT, la aplicación de consumidor de incorporación de AllJoyn puede usarse para configurar el adaptador de Wi-Fi del dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="0e98a-185">When a separate device running an AllJoyn Onboarding Consumer application connects to your Windows 10 IoT SoftAP, the AllJoyn Onboarding Consumer application can be used to configure your IoT device's Wi-Fi adapter.</span></span>  <span data-ttu-id="0e98a-186">Cuando se habilita, la aplicación de productor de incorporación de AllJoyn (IoTOnboarding) usa el método de autenticación ECDHE_NULL.</span><span class="sxs-lookup"><span data-stu-id="0e98a-186">When enabled, the AllJoyn Onboarding Producer app (IoTOnboarding) uses the ECDHE_NULL authentication method.</span></span> 

> [!NOTE]
> <span data-ttu-id="0e98a-187">Para usar AllJoyn incorporación con Windows 10 IoT compilaciones 10.0.14393 o versiones anteriores requiere una actualización para el <strong>IotOnboarding</strong> ejemplo que puede ser [descargar aquí](https://github.com/ms-iot/samples).</span><span class="sxs-lookup"><span data-stu-id="0e98a-187">To use AllJoyn Onboarding with Windows 10 IoT builds 10.0.14393 or earlier requires an update to the <strong>IotOnboarding</strong> sample which may be [downloaded here](https://github.com/ms-iot/samples).</span></span>

<span data-ttu-id="0e98a-188">![Incorporación a AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![incorporación en ICS](../media/DevicePortal/OnboardingICS.png)</span><span class="sxs-lookup"><span data-stu-id="0e98a-188">![Onboarding onto AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![Onboarding onto ICS](../media/DevicePortal/OnboardingICS.png)</span></span>

> [!NOTE]
> <span data-ttu-id="0e98a-189">Adaptador de punto de acceso es el adaptador de Wi-Fi que actúan como un punto de acceso Wi-Fi (normalmente tiene una dirección IP como 192.168.137.1).</span><span class="sxs-lookup"><span data-stu-id="0e98a-189">Access point adapter is the WiFi adapter that act as a WiFi access point (it usually has an IP address like 192.168.137.1).</span></span>
> <span data-ttu-id="0e98a-190">Adaptador de red compartida es el adaptador que se conecta a Internet (p. ej.: Adaptador Ethernet).</span><span class="sxs-lookup"><span data-stu-id="0e98a-190">Shared network adapter is the adapter that connects to Internet (e.g.: Ethernet adapter).</span></span>

![Incorporar en el punto de acceso temporal](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> <span data-ttu-id="0e98a-192">SoftAP SSID tendrá automáticamente el prefijo por "AJ_" si AllJoyn incorporación está habilitado y postfija con la dirección MAC del adaptador Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="0e98a-192">SoftAP SSID will be automatically prefixed by "AJ_" if AllJoyn onboarding is enabled and postfixed with the MAC address of the Wifi adapter.</span></span> <span data-ttu-id="0e98a-193">La frase de contraseña SoftAP debe tener entre 8 y 63 caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="0e98a-193">The SoftAP passphrase must be between 8 and 63 ASCII characters.</span></span>


### <a name="tpm-configuration"></a><span data-ttu-id="0e98a-194">Configuración de TPM</span><span class="sxs-lookup"><span data-stu-id="0e98a-194">TPM configuration</span></span>
<span data-ttu-id="0e98a-195">El módulo de plataforma segura (TPM) es un coprocesador criptográfico que incluye capacidades de generación de números aleatorios, generación segura de claves criptográficas y la limitación de su uso.</span><span class="sxs-lookup"><span data-stu-id="0e98a-195">The Trusted Platform Module (TPM) is a cryptographic coprocessor including capabilities for random number generation, secure generation of cryptographic keys and limitation of their use.</span></span> <span data-ttu-id="0e98a-196">También incluye capacidades como la autorización remota y almacenamiento sealed.</span><span class="sxs-lookup"><span data-stu-id="0e98a-196">It also includes capabilities such as remote attestation and sealed storage.</span></span> <span data-ttu-id="0e98a-197">Para obtener información sobre el TPM y la seguridad en IoT Core, visite la [crear dispositivos seguros](../secure-your-device/BuildingSecureDevices.md) página y el [TPM](../secure-your-device/TPM.md) página.</span><span class="sxs-lookup"><span data-stu-id="0e98a-197">To learn about the TPM and security on IoT Core, visit the [Building secure devices](../secure-your-device/BuildingSecureDevices.md) page and the [TPM](../secure-your-device/TPM.md) page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e98a-198">Limpet.exe usa para formar parte de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="0e98a-198">Limpet.exe used to be part of Windows IoT Core.</span></span> <span data-ttu-id="0e98a-199">A partir de octubre de 2018, está ahora disponible como un porject de código abierto en [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client).</span><span class="sxs-lookup"><span data-stu-id="0e98a-199">Starting with October 2018, it is now available as an open source porject at [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client).</span></span>

<span data-ttu-id="0e98a-200">Para facilitar las pruebas, se tiene una versión pregenerada de Limpet.exe disponible sin firmar y puede descargarse desde WDP.</span><span class="sxs-lookup"><span data-stu-id="0e98a-200">To make testing easier, we have a non-signed pre-built version of Limpet.exe available and can be downloaded right from WDP.</span></span> <span data-ttu-id="0e98a-201">Simplemente deberá ir a la pestaña "Configuración de TPM" y haga clic en el botón "Instalar Latest".</span><span class="sxs-lookup"><span data-stu-id="0e98a-201">You just need to go the 'TPM Configuration' tab and click the 'Install Latest' button.</span></span> 

> [!NOTE]
> <span data-ttu-id="0e98a-202">Esta versión de Limpet.exe no debe enviarse con el producto final.</span><span class="sxs-lookup"><span data-stu-id="0e98a-202">This version of Limpet.exe should not be shipped with your final product.</span></span> <span data-ttu-id="0e98a-203">En su lugar, deberá compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.</span><span class="sxs-lookup"><span data-stu-id="0e98a-203">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

### <a name="azure-clients-configuration"></a><span data-ttu-id="0e98a-204">Configuración de clientes de Azure</span><span class="sxs-lookup"><span data-stu-id="0e98a-204">Azure Clients configuration</span></span>

<span data-ttu-id="0e98a-205">Dispositivos de IoT pueden administrarse de forma remota a través de servicios en la nube.</span><span class="sxs-lookup"><span data-stu-id="0e98a-205">IoT devices can be remotely managed through cloud services.</span></span> <span data-ttu-id="0e98a-206">Azure proporciona un conjunto muy rico de servicios para habilitar estos escenarios.</span><span class="sxs-lookup"><span data-stu-id="0e98a-206">Azure provides a very rich set of services to enable such scenarios.</span></span> <span data-ttu-id="0e98a-207">Hemos creado a un cliente de administración de dispositivos que complementa el servicio IoT Hub de Azure y de servicio de aprovisionamiento de dispositivos (DPS de Azure) de la plataforma de Windows y que también expone varias características de capacidad de administración de Windows.</span><span class="sxs-lookup"><span data-stu-id="0e98a-207">We have created a device management client that complements Azure's Device Provisioning Service (DPS) and Azure's IoT Hub service on the Windows platform and which also exposes several Windows manageability features.</span></span>

<span data-ttu-id="0e98a-208">Los clientes se proporcionará como proyectos de código abierto.</span><span class="sxs-lookup"><span data-stu-id="0e98a-208">The clients will be provided as open source projects.</span></span> <span data-ttu-id="0e98a-209">Para facilitar la fase de pruebas, proporcionaremos archivos binarios compilados previamente.</span><span class="sxs-lookup"><span data-stu-id="0e98a-209">To make testing them easier, we will be providing pre-built binaries.</span></span> <span data-ttu-id="0e98a-210">Puede usar la ficha 'Azure clientes' en WDP para instalar y ejecutar los archivos binarios de prueba.</span><span class="sxs-lookup"><span data-stu-id="0e98a-210">You can use the 'Azure Clients' tab in WDP to install and run those test binaries.</span></span>

> [!NOTE]
> <span data-ttu-id="0e98a-211">Esta versión de las herramientas no debe enviarse con el producto final.</span><span class="sxs-lookup"><span data-stu-id="0e98a-211">This version of the tools should not be shipped with your final product.</span></span> <span data-ttu-id="0e98a-212">En su lugar, deberá compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.</span><span class="sxs-lookup"><span data-stu-id="0e98a-212">Instead, you need to build the open source project, sign it, and package it with your image.</span></span>

<span data-ttu-id="0e98a-213">Una vez que los proyectos de código abierto están disponibles para su uso, actualizaremos esta documentación.</span><span class="sxs-lookup"><span data-stu-id="0e98a-213">We will update this documentation once the open source projects are available for consumption.</span></span>

### <a name="remote"></a><span data-ttu-id="0e98a-214">Control remoto</span><span class="sxs-lookup"><span data-stu-id="0e98a-214">Remote</span></span>
<span data-ttu-id="0e98a-215">El servidor remoto de Windows IoT permite a los usuarios ver lo que se muestra su dispositivo sin necesidad de conectarse a un monitor físico para el teclado.</span><span class="sxs-lookup"><span data-stu-id="0e98a-215">The Windows IoT Remote Server allows users to see what their device is displaying without connecting a physical monitor to the keyboard.</span></span>


## <a name="additional-information"></a><span data-ttu-id="0e98a-216">Información adicional</span><span class="sxs-lookup"><span data-stu-id="0e98a-216">Additional Information</span></span> 

### <a name="changing-the-default-port"></a><span data-ttu-id="0e98a-217">Cambiar el puerto predeterminado</span><span class="sxs-lookup"><span data-stu-id="0e98a-217">Changing the default port</span></span>
 
1. <span data-ttu-id="0e98a-218">Inicie powershell y [conectarse al dispositivo.](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="0e98a-218">Launch powershell and [connect to your device.](../connect-your-device/PowerShell.md)</span></span>
2. <span data-ttu-id="0e98a-219">Descargar [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) herramienta, compílelo y cópielo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0e98a-219">Download [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) tool, build it, and copy it to your device.</span></span> 
3. <span data-ttu-id="0e98a-220">Tomar posesión de la clave del registro para el servicio mediante la ejecución</span><span class="sxs-lookup"><span data-stu-id="0e98a-220">Take ownership of the registry key for the service by running</span></span>

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. <span data-ttu-id="0e98a-221">Establezca el puerto deseado al modificar la configuración del registro</span><span class="sxs-lookup"><span data-stu-id="0e98a-221">Set the desired port by modifying the registry settings</span></span> 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. <span data-ttu-id="0e98a-222">Reinicie el servicio WebManagement mediante la ejecución siguiente o reiniciando el dispositivo</span><span class="sxs-lookup"><span data-stu-id="0e98a-222">Restart the WebManagement service by running following or by restarting the device</span></span>

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a><span data-ttu-id="0e98a-223">Uso de HTTPS</span><span class="sxs-lookup"><span data-stu-id="0e98a-223">Using HTTPS</span></span> 

<span data-ttu-id="0e98a-224">Si desea usar HTTPS, en primer lugar tomar la posesión de la clave del registro como se describe en la sección anterior y establecer las claves del registro HttpsPort y EncryptionMode como la siguiente y, a continuación, reinicie el servicio de webmanagement</span><span class="sxs-lookup"><span data-stu-id="0e98a-224">If you want to use HTTPS, first take the ownership of the registry key as described in previous section and set the HttpsPort and EncryptionMode registry keys as below and then restart the webmanagement service</span></span>

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a><span data-ttu-id="0e98a-225">Portal de aprovisionamiento de dispositivos con un certificado SSL personalizado</span><span class="sxs-lookup"><span data-stu-id="0e98a-225">Provisoning Device Portal with a custom SSL certificate</span></span>

<span data-ttu-id="0e98a-226">En Windows 10 Creators Update, el de Windows Device Portal agregado a los administradores de dispositivos instalar un certificado personalizado para su uso en la comunicación HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0e98a-226">In the Windows 10 Creators Update, the Windows Device Portal added a way for device administrators to install a custom certificate for use in HTTPS communication.</span></span>

<span data-ttu-id="0e98a-227">Para obtener más información, [lea la documentación en los documentos de Windows Device Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span><span class="sxs-lookup"><span data-stu-id="0e98a-227">To learn more, [read the documentation under the Windows Device Portal docs](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl).</span></span> 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a><span data-ttu-id="0e98a-228">Bloquear la configuración de volcado de memoria para la captura de volcado de memoria:</span><span class="sxs-lookup"><span data-stu-id="0e98a-228">Crash Dump Settings for Capturing Memory Dump:</span></span>

<span data-ttu-id="0e98a-229">Para capturar un volcado de memoria completo, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0e98a-229">To capture a Full Memory Dump, do the following:</span></span>

1. <span data-ttu-id="0e98a-230">Conectarse a un dispositivo de IoT a través de WDP.</span><span class="sxs-lookup"><span data-stu-id="0e98a-230">Connect to a IoT device through WDP.</span></span>

2. <span data-ttu-id="0e98a-231">En depuración -> depuración -> configuración de configuración de bloqueo de Kernel -> tipo de volcado.</span><span class="sxs-lookup"><span data-stu-id="0e98a-231">From Debug -> Debug settings -> Kernel crash settings -> Crash dump type.</span></span> 

3. <span data-ttu-id="0e98a-232">Seleccione: Volcado de memoria completo (en uso de memoria).</span><span class="sxs-lookup"><span data-stu-id="0e98a-232">Select: Complete memory dump (in use memory).</span></span>
    <span data-ttu-id="0e98a-233">Asegúrese de que el dispositivo se reinicia para que la configuración surta efecto.</span><span class="sxs-lookup"><span data-stu-id="0e98a-233">Make sure the device is rebooted for the setting to take effect.</span></span> 
    
4. <span data-ttu-id="0e98a-234">Compruebe que `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` se establece en 0 x 1.</span><span class="sxs-lookup"><span data-stu-id="0e98a-234">Verify  that `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` is set to 0x1.</span></span>

5. <span data-ttu-id="0e98a-235">Actualización `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` en 0 x 0.</span><span class="sxs-lookup"><span data-stu-id="0e98a-235">Update `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` to 0x0.</span></span>

6. <span data-ttu-id="0e98a-236">Asegúrese de que tiene suficiente espacio en el dispositivo para que se genere este volcado de memoria.</span><span class="sxs-lookup"><span data-stu-id="0e98a-236">Make sure you have enough space on the device for this Dump to be generated.</span></span> <span data-ttu-id="0e98a-237">Puede configurar el cambio de la ubicación del archivo de volcado desde aquí: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span><span class="sxs-lookup"><span data-stu-id="0e98a-237">You can configure the changing the DumpFile location from here: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`</span></span>


## <a name="additional-resources"></a><span data-ttu-id="0e98a-238">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="0e98a-238">Additional Resources</span></span>
___ 

1. [<span data-ttu-id="0e98a-239">Página de información general de Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="0e98a-239">Windows Device Portal overview page</span></span>](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
