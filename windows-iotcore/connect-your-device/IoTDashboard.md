---
title: Panel de Windows 10 IoT Core
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre lo que hace el panel de IoT Core de Windows 10 y cómo empezar.
keywords: Windows IOT, Windows 10 IOT Core Dashboard, panel de Windows IOT, dispositivos
ms.openlocfilehash: e244dd4705fa85707468f284b9a5d070c91720d8
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918617"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="03866-104">Panel de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="03866-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="03866-105">Panel de Windows 10 IoT Core es la mejor manera de descargar, configurar y conectar sus dispositivos Windows 10 IoT Core, todo desde su PC.</span><span class="sxs-lookup"><span data-stu-id="03866-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="03866-106">Puede descargar el [Panel de IOT Core aquí](http://go.microsoft.com/fwlink/?LinkID=708576).</span><span class="sxs-lookup"><span data-stu-id="03866-106">You can download the [IoT Core Dashboard here](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="03866-107">Si encuentra que está recibiendo una pantalla en blanco al abrir el panel de IoT después de la descarga, puede deberse a un problema con el controlador.</span><span class="sxs-lookup"><span data-stu-id="03866-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may be due to a driver issue.</span></span> <span data-ttu-id="03866-108">Para solucionar este problema, debe descargar el [formato zip](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) del controlador de gráficos Intel e instalar el controlador manualmente.</span><span class="sxs-lookup"><span data-stu-id="03866-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="03866-109">Configuración de un dispositivo nuevo</span><span class="sxs-lookup"><span data-stu-id="03866-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="03866-110">El panel de información no se puede usar para configurar Raspberry Pi 3B+.</span><span class="sxs-lookup"><span data-stu-id="03866-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="03866-111">Si tiene un dispositivo 3B+, debe usar la [versión preliminar técnica de 3B+](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="03866-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="03866-112">Vea las [limitaciones conocidas](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) de la versión preliminar técnica para determinar si esto es adecuado para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="03866-112">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="03866-113">Actualmente hay un problema conocido en el que el sistema operativo atraviesa las particiones de la tarjeta SD y solicita un "formato..."</span><span class="sxs-lookup"><span data-stu-id="03866-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="03866-114">mensaje para una partición de datos específica que no contiene ningún sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="03866-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="03866-115">Descartar este mensaje presionando cancelar.</span><span class="sxs-lookup"><span data-stu-id="03866-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="03866-116">Aunque trabajamos en una solución, se recomienda que, si hace clic en "formatear ahora", vuelva a crear la tarjeta SD con la imagen FFU cuando la acción de formato afecte al proceso de actualización y el dispositivo no se actualizará.</span><span class="sxs-lookup"><span data-stu-id="03866-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="03866-117">El panel de IoT facilita la configuración de un nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="03866-118">Para obtener instrucciones detalladas sobre cómo empezar, [consulte la página de introducción.](https://docs.microsoft.com/en-us/windows/iot-core/getstarted)</span><span class="sxs-lookup"><span data-stu-id="03866-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) page.</span></span>

![Página de configuración del panel de IoT](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="03866-120">Tarjeta SD</span><span class="sxs-lookup"><span data-stu-id="03866-120">SD card</span></span>
<span data-ttu-id="03866-121">El tipo, marca y modelo de la tarjeta SD afecta en gran medida al rendimiento y a la calidad de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="03866-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="03866-122">Una tarjeta lenta puede tardar hasta cinco veces más en arrancar que las [tarjetas recomendadas](../learn-about-hardware/hardwarecompatlist.md).</span><span class="sxs-lookup"><span data-stu-id="03866-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="03866-123">Una tarjeta SD más antigua y menos confiable podría no funcionar siquiera.</span><span class="sxs-lookup"><span data-stu-id="03866-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="03866-124">Si sigue teniendo problemas para instalar, considere la posibilidad de reemplazar la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="03866-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="03866-125">Nombre del dispositivo</span><span class="sxs-lookup"><span data-stu-id="03866-125">Device Name</span></span>
<span data-ttu-id="03866-126">El nombre de dispositivo predeterminado es minwinpc.</span><span class="sxs-lookup"><span data-stu-id="03866-126">The default device name is minwinpc.</span></span> <span data-ttu-id="03866-127">Se recomienda cambiarla a algo único, ya que esto facilita la búsqueda del dispositivo en la red.</span><span class="sxs-lookup"><span data-stu-id="03866-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="03866-128">El nombre del dispositivo puede tener una longitud de 15 caracteres como máximo y puede incluir letras, números y los siguientes símbolos: @ # $% ^ & ') (.</span><span class="sxs-lookup"><span data-stu-id="03866-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="03866-129">-_ {} ~ Si cambia el nombre del dispositivo en el panel de IoT al configurar el dispositivo, se producirá un reinicio automático la primera vez que encienda el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="03866-130">Contraseña</span><span class="sxs-lookup"><span data-stu-id="03866-130">Password</span></span>
<span data-ttu-id="03866-131">La contraseña es un campo obligatorio y debe establecerse.</span><span class="sxs-lookup"><span data-stu-id="03866-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="03866-132">Al establecer una contraseña en el panel de IoT, se modifica la contraseña del usuario administrador que, de forma predeterminada, es "p@ssw0rd".</span><span class="sxs-lookup"><span data-stu-id="03866-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="03866-133">Conexión de red Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="03866-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="03866-134">En el panel de IoT se muestran todas las redes disponibles a las que se ha conectado el equipo previamente.</span><span class="sxs-lookup"><span data-stu-id="03866-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="03866-135">Si no ve la red Wi-Fi deseada en la lista, asegúrese de que está conectado a ella en su PC.</span><span class="sxs-lookup"><span data-stu-id="03866-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="03866-136">Si desactiva la casilla, debe conectar un cable Ethernet a la placa después del parpadeo.</span><span class="sxs-lookup"><span data-stu-id="03866-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="03866-137">Primer arranque</span><span class="sxs-lookup"><span data-stu-id="03866-137">First boot</span></span>
<span data-ttu-id="03866-138">El primer arranque siempre tardará más que todos los arranques posteriores.</span><span class="sxs-lookup"><span data-stu-id="03866-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="03866-139">El sistema operativo tardará algún tiempo en instalarse y conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="03866-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="03866-140">El tiempo de arranque puede variar considerablemente en función de la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="03866-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="03866-141">Por ejemplo, un Raspberry PI 3 que se ejecuta en la tarjeta SD recomendada tarda 3-4 minutos en iniciarse por primera vez.</span><span class="sxs-lookup"><span data-stu-id="03866-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="03866-142">En el mismo PI con una tarjeta SD de baja calidad, hemos detectado tiempos de arranque de más de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="03866-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="03866-143">Conectarse a Internet</span><span class="sxs-lookup"><span data-stu-id="03866-143">Connecting to the internet</span></span>
<span data-ttu-id="03866-144">Es esencial tener el dispositivo IoT Core conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="03866-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="03866-145">Muchas de las placas más recientes incorporan adaptadores Wi-Fi integrados.</span><span class="sxs-lookup"><span data-stu-id="03866-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="03866-146">Si tiene problemas para conectarse a la red, intente lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="03866-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="03866-147">Reinicio del dispositivo</span><span class="sxs-lookup"><span data-stu-id="03866-147">Rebooting the device</span></span>
* <span data-ttu-id="03866-148">Conexión de un cable Ethernet</span><span class="sxs-lookup"><span data-stu-id="03866-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="03866-149">Conectando un monitor al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="03866-150">Esto le mostrará información de diagnóstico sobre el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="03866-151">El adaptador de Wi-Fi oficial de Raspberry pi 2 puede ser inestable al conectarse a Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="03866-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="03866-152">Mis dispositivos</span><span class="sxs-lookup"><span data-stu-id="03866-152">My Devices</span></span>
___
<span data-ttu-id="03866-153">Una vez que el dispositivo esté conectado a Internet, el panel de IoT detectará automáticamente el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="03866-154">Para encontrar el dispositivo, vaya a **mis dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="03866-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="03866-155">Si el dispositivo no aparece en la lista, intente reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="03866-156">Asegúrese de que, si hay más de un dispositivo en la red, cada uno tiene un nombre único.</span><span class="sxs-lookup"><span data-stu-id="03866-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="03866-157">Asegúrese también de que **windows10iotcoredashboard. exe** se puede comunicar a través de Firewall de Windows mediante los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="03866-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="03866-158">Abra el **centro de redes y recursos compartidos** y busque el tipo de red (dominio, privado o público) al que está conectado su equipo.</span><span class="sxs-lookup"><span data-stu-id="03866-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="03866-159">Abra el **Panel de control** y haga clic en **sistema y seguridad**.</span><span class="sxs-lookup"><span data-stu-id="03866-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="03866-160">Haga clic en **permitir una aplicación a través de Firewall de Windows** en **firewall de Windows**.</span><span class="sxs-lookup"><span data-stu-id="03866-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="03866-161">Haz clic en **Cambiar configuración**.</span><span class="sxs-lookup"><span data-stu-id="03866-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="03866-162">Busque **windows10iotcoredashboard. exe** en **aplicaciones y características permitidas** y, a continuación, habilite la casilla red adecuada (es decir, el tipo de red que encontró en el paso 1).</span><span class="sxs-lookup"><span data-stu-id="03866-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="03866-163">Conectarse al dispositivo</span><span class="sxs-lookup"><span data-stu-id="03866-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="03866-164">Si no puede encontrar el dispositivo en el panel, intente escribir su [dirección IP] y [: 8080] en el explorador para poner en marcha el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="03866-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="03866-165">Para que el dispositivo se muestre en el panel, intente reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="03866-166">Haga clic con el botón derecho y seleccione **abrir en el portal de dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="03866-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="03866-167">Esto iniciará la página del [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md) y es la mejor manera de interactuar y administrar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03866-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![IoTDashboard ver dispositivos](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="03866-169">También puede conectarse al dispositivo mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03866-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="03866-170">Conexión a Azure AD</span><span class="sxs-lookup"><span data-stu-id="03866-170">Connect to Azure</span></span>
___
<span data-ttu-id="03866-171">El panel de IoT le permite aprovisionar dispositivos IoT Core con Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="03866-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="03866-172">Puede obtener más información en esta entrada de [blog](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span><span class="sxs-lookup"><span data-stu-id="03866-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="03866-173">Aprenda a usar el panel de IoT con Azure</span><span class="sxs-lookup"><span data-stu-id="03866-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="03866-174">Ejemplos de ejecución rápida</span><span class="sxs-lookup"><span data-stu-id="03866-174">Quick Run Samples</span></span>
___

<span data-ttu-id="03866-175">Los ejemplos de ejecución rápida no requieren la compilación de código, la instalación de Visual Studio o la descarga del SDK.</span><span class="sxs-lookup"><span data-stu-id="03866-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="03866-176">Son ideales para comprobar rápidamente lo que puede hacer IoT Core.</span><span class="sxs-lookup"><span data-stu-id="03866-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="03866-177">Impresora de red 3D</span><span class="sxs-lookup"><span data-stu-id="03866-177">Network 3D Printer</span></span>
<span data-ttu-id="03866-178">Use el ejemplo de impresora de red 3D para conectar la impresora 3D a la placa, lo que puede hacer que se pueda detectar a través de la red doméstica.</span><span class="sxs-lookup"><span data-stu-id="03866-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![Impresora IoTDashboard Network 3D](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="03866-180">Radio por Internet</span><span class="sxs-lookup"><span data-stu-id="03866-180">Internet radio</span></span>
<span data-ttu-id="03866-181">Convierta el dispositivo de Windows 10 IoT Core en una radio de Internet que se pueda controlar desde cualquier lugar de su hogar.</span><span class="sxs-lookup"><span data-stu-id="03866-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard radio por Internet](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="03866-183">IoT Core sin bloqueos</span><span class="sxs-lookup"><span data-stu-id="03866-183">IoT Core Blockly</span></span>
<span data-ttu-id="03866-184">El ejemplo de IoT Core permite que el programa sea un pi2 o 3 de Raspberry y un sombrero de sentido de Raspberry PI mediante un editor de "bloque" desde el explorador.</span><span class="sxs-lookup"><span data-stu-id="03866-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard bloque](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
