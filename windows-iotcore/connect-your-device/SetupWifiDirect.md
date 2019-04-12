---
title: Uso de Wi-Fi Direct en su dispositivo con Windows 10 Iot Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a configurar, probar y usar direct de Wi-Fi en dispositivos con un adaptador de red Wi-Fi USB habilitado.
keywords: Windows iot, Wi-Fi direct, el programa de instalación, Wi-Fi, los dispositivos
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514803"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="60ab2-104">Uso de Wi-Fi Direct en su dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="60ab2-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="60ab2-105">Se admite la Wi-Fi Direct habilitan para el adaptador de USB Wi-Fi en Windows 10 IoT Core dispositivos mediante el uso directo de una red Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="60ab2-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="60ab2-106">Para asegurarse de que Wi-Fi Direct es dos cosas habilitadas debe ser true:</span><span class="sxs-lookup"><span data-stu-id="60ab2-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="60ab2-107">debe admitir Wi-Fi Direct, el hardware del adaptador de USB Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="60ab2-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="60ab2-108">el controlador del adaptador de USB Wi-Fi correspondiente debe admitir Wi-Fi Direct.</span><span class="sxs-lookup"><span data-stu-id="60ab2-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="60ab2-109">Wi-Fi Direct proporciona una solución para la conectividad de dispositivo a otro de Wi-Fi sin necesidad de ya sea un punto de acceso inalámbrico (AP inalámbrico) para configurar la conexión.</span><span class="sxs-lookup"><span data-stu-id="60ab2-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="60ab2-110">Eche un vistazo a las API de UWP disponibles en el [espacio de nombres Windows.Devices.WiFiDirect](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) para ver lo que puede hacer con WiFiDirect.</span><span class="sxs-lookup"><span data-stu-id="60ab2-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="60ab2-111">Adaptadores compatibles</span><span class="sxs-lookup"><span data-stu-id="60ab2-111">Supported Adapters</span></span>

<span data-ttu-id="60ab2-112">Una lista de adaptadores de red Wi-Fi que se han probado en Windows 10 IoT Core puede encontrarse en nuestra [Hardware admite](../learn-about-hardware/HardwareCompatList.md) página.</span><span class="sxs-lookup"><span data-stu-id="60ab2-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="60ab2-113">Ejemplo básico de Wi-Fi Direct</span><span class="sxs-lookup"><span data-stu-id="60ab2-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="60ab2-114">Puede probar fácilmente la funcionalidad de Wi-Fi Direct con Wi-Fi Direct UWP [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span><span class="sxs-lookup"><span data-stu-id="60ab2-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="60ab2-115">Usaremos el C# versión y ejecute el ejemplo de dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="60ab2-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="60ab2-116">Configurar los dos dispositivos</span><span class="sxs-lookup"><span data-stu-id="60ab2-116">Set up the two devices</span></span>
* <span data-ttu-id="60ab2-117">MinnowBoardMax (MBM) ejecuta Windows 10 IoT Core (consulte estas instrucciones), con una llave CanaKit WiFi</span><span class="sxs-lookup"><span data-stu-id="60ab2-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="60ab2-118">Conectar el monitor, teclado y mouse a la MBM</span><span class="sxs-lookup"><span data-stu-id="60ab2-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="60ab2-119">Un equipo de Windows 10 con la versión más reciente de Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="60ab2-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="60ab2-120">El PC (o equipo portátil) deberán tener Wi-Fi Direct admite (por ejemplo, un Microsoft Surface)</span><span class="sxs-lookup"><span data-stu-id="60ab2-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="60ab2-121">Instale Visual Studio 2017 en tu PC con Windows 10</span><span class="sxs-lookup"><span data-stu-id="60ab2-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="60ab2-122">Clone o descargue Wi-Fi Direct UWP [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(es la raíz del repositorio de GitHub [aquí](https://github.com/Microsoft/Windows-universal-samples)).</span><span class="sxs-lookup"><span data-stu-id="60ab2-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="60ab2-123">Carga el C# versión de la muestra de Wi-Fi Direct UWP en Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="60ab2-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="60ab2-124">Ejecutar el ejemplo en los dos dispositivos</span><span class="sxs-lookup"><span data-stu-id="60ab2-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="60ab2-125">Compile el ejemplo y la implementación y ejecución, en el MBM:</span><span class="sxs-lookup"><span data-stu-id="60ab2-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="60ab2-126">Establezca el cuadro combinado de "plataformas de solución" a "x86"</span><span class="sxs-lookup"><span data-stu-id="60ab2-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="60ab2-127">Seleccione "Máquina remota" en la lista desplegable "Run"</span><span class="sxs-lookup"><span data-stu-id="60ab2-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="60ab2-128">Iniciar el ejemplo en el MBM sin depuración (presionando Ctrl-F5 o seleccionando "Iniciar sin depurar" en el menú "Debug")</span><span class="sxs-lookup"><span data-stu-id="60ab2-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="60ab2-129">Debería ver el ejemplo de Wi-Fi Direct, que se ejecutan en el monitor conectado a la MBM</span><span class="sxs-lookup"><span data-stu-id="60ab2-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="60ab2-130">Compile el ejemplo y la implementación y ejecución, en el equipo de Windows 10:</span><span class="sxs-lookup"><span data-stu-id="60ab2-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="60ab2-131">Establezca el cuadro combinado de "plataformas de solución" a "x86"</span><span class="sxs-lookup"><span data-stu-id="60ab2-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="60ab2-132">Seleccione "Local" en la lista desplegable "Run"</span><span class="sxs-lookup"><span data-stu-id="60ab2-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="60ab2-133">Iniciar el ejemplo (F5 o CTRL+F5)</span><span class="sxs-lookup"><span data-stu-id="60ab2-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="60ab2-134">Debería ver el ejemplo de Wi-Fi Direct, que se ejecutan en los equipos Windows 10</span><span class="sxs-lookup"><span data-stu-id="60ab2-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="60ab2-135">Configurar el anunciante y el conector</span><span class="sxs-lookup"><span data-stu-id="60ab2-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="60ab2-136">En el MBM, seleccione "Anunciante" (1) y presione el botón "Iniciar anuncio"</span><span class="sxs-lookup"><span data-stu-id="60ab2-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="60ab2-137">Iniciará el MBM anuncia a sí mismo en el canal de Wi-Fi Direct</span><span class="sxs-lookup"><span data-stu-id="60ab2-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        ![Pantalla de configuración del anunciante](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="60ab2-139">Tenga en cuenta el banner "Advertisement Status" en la parte inferior de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="60ab2-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="60ab2-140">En el equipo con Windows 10, seleccione "Conector" (2) y presione el botón "Iniciar el monitor"</span><span class="sxs-lookup"><span data-stu-id="60ab2-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="60ab2-141">El equipo con Windows 10 iniciará la exploración para conexiones Wi-Fi Direct disponibles</span><span class="sxs-lookup"><span data-stu-id="60ab2-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="60ab2-142">Cuando se completa el análisis, debería ver el nombre de su MBM en la lista "Dispositivos detectados"</span><span class="sxs-lookup"><span data-stu-id="60ab2-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![Pantalla de configuración del conector](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="60ab2-144">Puede ver la lista aparecen dos dispositivos (estamos interesados en "ale-mbm01") y el mensaje "Se completó la enumeración DeviceWatcher".</span><span class="sxs-lookup"><span data-stu-id="60ab2-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="60ab2-145">Empareje los dispositivos</span><span class="sxs-lookup"><span data-stu-id="60ab2-145">Pair the devices</span></span>
* <span data-ttu-id="60ab2-146">En el equipo con Windows 10, seleccione el MBM ("ale-mbm01" en nuestro ejemplo) en la lista "Dispositivos detectados" y presione el botón "Conectar"</span><span class="sxs-lookup"><span data-stu-id="60ab2-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="60ab2-147">En el equipo con Windows 10, pulse "Sí" para iniciar el proceso de emparejamiento</span><span class="sxs-lookup"><span data-stu-id="60ab2-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![Emparejamiento de inicio de conector](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="60ab2-149">En el monitor MBM debería un mensaje con el PIN</span><span class="sxs-lookup"><span data-stu-id="60ab2-149">On the MBM monitor you should a message with the PIN</span></span>

    ![Cuadro de diálogo de NIP de anunciante](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="60ab2-151">En el equipo con Windows 10, debería ver un cuadro de diálogo donde debe escribir el PIN</span><span class="sxs-lookup"><span data-stu-id="60ab2-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![Cuadro de diálogo de NIP de conector](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="60ab2-153">Hablar en el canal</span><span class="sxs-lookup"><span data-stu-id="60ab2-153">Talk on the channel</span></span>
* <span data-ttu-id="60ab2-154">Los dos dispositivos deben estar conectados.</span><span class="sxs-lookup"><span data-stu-id="60ab2-154">The two devices should be connected.</span></span> <span data-ttu-id="60ab2-155">Debería ver un identificador de dispositivo generado al azar ("hqffpzhz.ggg" en nuestro ejemplo) en ambas pantallas en la lista "Dispositivos conectados"</span><span class="sxs-lookup"><span data-stu-id="60ab2-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![Dispositivo conectado de anunciante](../media/SetupWiFiDirect/Advertiser03.png)

    ![Dispositivo conectado de conector](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="60ab2-158">Ahora tiene un canal de dúplex completo (o socket) configurar</span><span class="sxs-lookup"><span data-stu-id="60ab2-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="60ab2-159">en el MBM, seleccione el dispositivo ("hqffpzhz.ggg") en la lista "Dispositivos conectados"</span><span class="sxs-lookup"><span data-stu-id="60ab2-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="60ab2-160">Escriba un mensaje en el cuadro de texto "Escriba un mensaje de"</span><span class="sxs-lookup"><span data-stu-id="60ab2-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="60ab2-161">Presione el botón "Enviar"</span><span class="sxs-lookup"><span data-stu-id="60ab2-161">press the "Send" button</span></span>
    * <span data-ttu-id="60ab2-162">debería ver el mensaje recibido desde el equipo con Windows 10</span><span class="sxs-lookup"><span data-stu-id="60ab2-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="60ab2-163">Intente enviar un mensaje desde el equipo con Windows 10 a la MBM</span><span class="sxs-lookup"><span data-stu-id="60ab2-163">try sending a message from the Windows 10 PC to the MBM</span></span>
