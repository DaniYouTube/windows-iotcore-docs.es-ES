---
title: Panel de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre lo que hace el panel de Windows 10 IoT Core y cómo empezar a trabajar.
keywords: Windows iot, panel de windows 10 iot core, panel de windows iot, los dispositivos
ms.openlocfilehash: af87ff8224cf77b567b1dd96e6de2297b4752530
ms.sourcegitcommit: f447681d9a73ebdec97a3da973bd798a02df975d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197677"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="6f57d-104">Panel de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="6f57d-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="6f57d-105">Panel de Windows 10 IoT Core es la mejor manera de descargar, configurar y conectar sus dispositivos Windows 10 IoT Core, todo ello desde su PC.</span><span class="sxs-lookup"><span data-stu-id="6f57d-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="6f57d-106">Puede descargar el [IoT Core aquí panel](http://go.microsoft.com/fwlink/?LinkID=708576).</span><span class="sxs-lookup"><span data-stu-id="6f57d-106">You can download the [IoT Core Dashboard here](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="6f57d-107">Si se detecta que está obteniendo una pantalla en blanco al abrir el panel de IoT después de descargar, puede deberse a un problema de controlador.</span><span class="sxs-lookup"><span data-stu-id="6f57d-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may be due to a driver issue.</span></span> <span data-ttu-id="6f57d-108">Para solucionar este problema, necesitará descargar el [formato zip](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) del controlador de gráficos Intel e instalar manualmente el controlador.</span><span class="sxs-lookup"><span data-stu-id="6f57d-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="6f57d-109">Configurar un dispositivo nuevo</span><span class="sxs-lookup"><span data-stu-id="6f57d-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="6f57d-110">No se puede utilizar el panel usado para configurar el dispositivo Raspberry Pi 3B +.</span><span class="sxs-lookup"><span data-stu-id="6f57d-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="6f57d-111">Si tiene un dispositivo 3B +, debe usar el [vista previa técnica de 3B +](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="6f57d-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="6f57d-112">Consulte la [limitaciones conocidas](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) de technical preview para determinar si esto es adecuado para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-112">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="6f57d-113">Actualmente no hay un problema conocido, donde el sistema operativo pasa por las particiones en la tarjeta SD y pide 'Format'...</span><span class="sxs-lookup"><span data-stu-id="6f57d-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="6f57d-114">mensaje para una partición de datos específicos que no contiene ningún sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="6f57d-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="6f57d-115">Haciendo clic en Cancelar para descartar este mensaje.</span><span class="sxs-lookup"><span data-stu-id="6f57d-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="6f57d-116">Mientras trabajamos en una solución, se recomienda que si hace clic en "Format ahora", programar la tarjeta SD, con la imagen FFU nuevo como los efectos de acción de formato que el proceso de actualización y el dispositivo no podrá actualizar.</span><span class="sxs-lookup"><span data-stu-id="6f57d-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="6f57d-117">El panel de IoT facilita la configuración de un dispositivo nuevo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="6f57d-118">Para obtener instrucciones detalladas sobre cómo empezar, vea el [comenzar](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) página.</span><span class="sxs-lookup"><span data-stu-id="6f57d-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) page.</span></span>

![Página de configuración del panel de IoT](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="6f57d-120">Tarjeta SD</span><span class="sxs-lookup"><span data-stu-id="6f57d-120">SD card</span></span>
<span data-ttu-id="6f57d-121">El tipo, la marca y el modelo de la tarjeta SD afecta en gran medida el rendimiento y la calidad de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6f57d-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="6f57d-122">Una tarjeta lenta puede tardar hasta cinco veces más en arrancar que nuestro [recomienda tarjetas](../learn-about-hardware/hardwarecompatlist.md).</span><span class="sxs-lookup"><span data-stu-id="6f57d-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="6f57d-123">No puede funcionar una tarjeta SD más antiguo y menos confiable.</span><span class="sxs-lookup"><span data-stu-id="6f57d-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="6f57d-124">Si sigues experimenta problemas al instalar, considere la posibilidad de reemplazar la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="6f57d-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="6f57d-125">Nombre del dispositivo</span><span class="sxs-lookup"><span data-stu-id="6f57d-125">Device Name</span></span>
<span data-ttu-id="6f57d-126">El nombre del dispositivo de forma predeterminada es minwinpc.</span><span class="sxs-lookup"><span data-stu-id="6f57d-126">The default device name is minwinpc.</span></span> <span data-ttu-id="6f57d-127">Se recomienda cambiar a un elemento único así resulta más fácil encontrar el dispositivo en la red.</span><span class="sxs-lookup"><span data-stu-id="6f57d-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="6f57d-128">El nombre del dispositivo puede tener como máximo 15 caracteres de longitud y puede incluir letras, números y los siguientes símbolos: @ # $ % ^ & ') (.</span><span class="sxs-lookup"><span data-stu-id="6f57d-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="6f57d-129">-_ {} ~ Si cambia el nombre del dispositivo en el panel de IoT al configurar el dispositivo, un reinicio automático se realizará la primera vez en cuando de energía en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="6f57d-130">Contraseña</span><span class="sxs-lookup"><span data-stu-id="6f57d-130">Password</span></span>
<span data-ttu-id="6f57d-131">Contraseña de un campo es obligatorio y debe establecerse.</span><span class="sxs-lookup"><span data-stu-id="6f57d-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="6f57d-132">Establecer una contraseña en el panel de IoT modifica la contraseña de usuario administrador cuyo valor predeterminado es "p@ssw0rd".</span><span class="sxs-lookup"><span data-stu-id="6f57d-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="6f57d-133">Conexión de red Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="6f57d-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="6f57d-134">Panel de IoT muestra todas las redes disponibles que se ha conectado anteriormente a su PC.</span><span class="sxs-lookup"><span data-stu-id="6f57d-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="6f57d-135">Si no ve la red Wi-Fi que desee en la lista, asegúrese de que está conectado a ella en su PC.</span><span class="sxs-lookup"><span data-stu-id="6f57d-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="6f57d-136">Si desactiva la casilla, debe conectarse mediante un cable Ethernet a la placa después de parpadear.</span><span class="sxs-lookup"><span data-stu-id="6f57d-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="6f57d-137">Primer arranque</span><span class="sxs-lookup"><span data-stu-id="6f57d-137">First boot</span></span>
<span data-ttu-id="6f57d-138">El primer arranque siempre tardará más que todos los arranques posteriores.</span><span class="sxs-lookup"><span data-stu-id="6f57d-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="6f57d-139">El sistema operativo tardará algún tiempo para instalar y conectar a la red.</span><span class="sxs-lookup"><span data-stu-id="6f57d-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="6f57d-140">Tiempo de arranque puede variar considerablemente en función de la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="6f57d-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="6f57d-141">Por ejemplo, un Raspberry Pi 3 que se ejecutan en la tarjeta SD recomendada tarda 3 a 4 minutos para el primer arranque.</span><span class="sxs-lookup"><span data-stu-id="6f57d-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="6f57d-142">En el mismo Pi con una tarjeta SD de baja calidad, hemos visto arranque veces más de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="6f57d-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="6f57d-143">Conexión a internet</span><span class="sxs-lookup"><span data-stu-id="6f57d-143">Connecting to the internet</span></span>
<span data-ttu-id="6f57d-144">Es esencial contar con el dispositivo de IoT Core se conecten a internet.</span><span class="sxs-lookup"><span data-stu-id="6f57d-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="6f57d-145">Muchos de los paneles más recientes vienen con integrado en adaptadores Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="6f57d-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="6f57d-146">Si tiene problemas para conectarse a la red, intente lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="6f57d-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="6f57d-147">Reiniciar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="6f57d-147">Rebooting the device</span></span>
* <span data-ttu-id="6f57d-148">Conectar un cable Ethernet</span><span class="sxs-lookup"><span data-stu-id="6f57d-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="6f57d-149">Conectar un monitor al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="6f57d-150">Esto mostrará información de diagnóstico sobre el dispositivo</span><span class="sxs-lookup"><span data-stu-id="6f57d-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="6f57d-151">El adaptador Wi-Fi de Raspberry Pi 2 oficial puede ser inestable al conectarse a Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="6f57d-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="6f57d-152">Mis dispositivos</span><span class="sxs-lookup"><span data-stu-id="6f57d-152">My Devices</span></span>
___
<span data-ttu-id="6f57d-153">Después de que el dispositivo está conectado a internet, el panel de IoT detectará automáticamente el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="6f57d-154">Para buscar el dispositivo, vaya a **Mis dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="6f57d-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="6f57d-155">Si el dispositivo no aparece, intente reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="6f57d-156">Asegúrese de que si hay varios dispositivos en la red, cada uno de ellos tiene un nombre único.</span><span class="sxs-lookup"><span data-stu-id="6f57d-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="6f57d-157">Además, asegúrese de que su **windows10iotcoredashboard.exe** puede comunicarse a través de Firewall de Windows siguiendo los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="6f57d-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="6f57d-158">Abra **centro de redes y recursos compartidos** y, a continuación, busque el tipo de red (dominio/privado/público) que está conectado su equipo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="6f57d-159">Abra **Panel de Control** y haga clic en **sistema y seguridad**.</span><span class="sxs-lookup"><span data-stu-id="6f57d-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="6f57d-160">Haga clic en **permitir que una aplicación a través de Firewall de Windows** en **Windows Firewall**.</span><span class="sxs-lookup"><span data-stu-id="6f57d-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="6f57d-161">Haga clic en **cambiar la configuración de**.</span><span class="sxs-lookup"><span data-stu-id="6f57d-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="6f57d-162">Buscar **windows10iotcoredashboard.exe** en **aplicaciones y características permitidas** y, a continuación, habilite la casilla de verificación de red adecuado (es decir, el tipo de red que se encuentra en el paso 1).</span><span class="sxs-lookup"><span data-stu-id="6f57d-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="6f57d-163">Conectarse al dispositivo</span><span class="sxs-lookup"><span data-stu-id="6f57d-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="6f57d-164">Si no puede encontrar el dispositivo en el panel, pruebe a escribir su [dirección IP] y [: 8080] en el explorador para obtener Windows Device Portal en marcha.</span><span class="sxs-lookup"><span data-stu-id="6f57d-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="6f57d-165">Para obtener el dispositivo para mostrar en el panel, pruebe a reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="6f57d-166">Haga clic y seleccione **abrir en el Portal de dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="6f57d-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="6f57d-167">Esto iniciará el [Windows Device Portal](../manage-your-device/DevicePortal.md) página y es la mejor manera de interactuar y administrar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f57d-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![IoTDashboard ver dispositivos](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="6f57d-169">También puede conectarse al dispositivo mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f57d-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="6f57d-170">Conectarse a Azure</span><span class="sxs-lookup"><span data-stu-id="6f57d-170">Connect to Azure</span></span>
___
<span data-ttu-id="6f57d-171">Panel de IoT le permite aprovisionar dispositivos de IoT Core con Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="6f57d-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="6f57d-172">Puede leer más información al respecto en esto [entrada de blog](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span><span class="sxs-lookup"><span data-stu-id="6f57d-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="6f57d-173">Obtenga información sobre cómo usar el panel de IoT con Azure</span><span class="sxs-lookup"><span data-stu-id="6f57d-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="6f57d-174">Ejemplos de ejecución rápidas</span><span class="sxs-lookup"><span data-stu-id="6f57d-174">Quick Run Samples</span></span>
___

<span data-ttu-id="6f57d-175">Ejecutar rápido ejemplos no requieren ninguna compilación de código, la instalación de Visual studio o descargar el SDK.</span><span class="sxs-lookup"><span data-stu-id="6f57d-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="6f57d-176">Son excelentes para comprobar rápidamente lo que puede hacer IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6f57d-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="6f57d-177">Impresora de red 3D</span><span class="sxs-lookup"><span data-stu-id="6f57d-177">Network 3D Printer</span></span>
<span data-ttu-id="6f57d-178">Use el ejemplo 3D de impresora de red para conectar la impresora 3D a la placa puede hacer que pueda detectar a través de la red doméstica.</span><span class="sxs-lookup"><span data-stu-id="6f57d-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![Impresora de red IoTDashboard 3D](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="6f57d-180">Internet radio</span><span class="sxs-lookup"><span data-stu-id="6f57d-180">Internet radio</span></span>
<span data-ttu-id="6f57d-181">Convierta el dispositivo Windows 10 IoT Core en una radio por internet que puede controlarse desde cualquier lugar del hogar.</span><span class="sxs-lookup"><span data-stu-id="6f57d-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![Radio por IoTDashboard Internet](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="6f57d-183">IoT Core Blockly</span><span class="sxs-lookup"><span data-stu-id="6f57d-183">IoT Core Blockly</span></span>
<span data-ttu-id="6f57d-184">Ejemplo de IoT Core Blockly permite su programa una Pi2 Raspberry o 3 y un "sombrero" sentido de Raspberry Pi mediante un editor de "bloque" desde el explorador.</span><span class="sxs-lookup"><span data-stu-id="6f57d-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
