---
title: Usar Wi-Fi Direct en el dispositivo de Windows 10 IOT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo configurar, probar y usar Wi-Fi Direct en dispositivos con un adaptador Wi-Fi USB habilitado.
keywords: Windows IOT, WiFi Direct, instalación, WiFi, dispositivos
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169412"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a><span data-ttu-id="043b6-104">Usar Wi-Fi Direct en el dispositivo de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="043b6-104">Using WiFi Direct on your Windows 10 IoT Core device</span></span>

<span data-ttu-id="043b6-105">WiFi Direct es compatible con dispositivos Windows 10 IoT Core mediante el uso de un adaptador Wi-Fi USB habilitado para Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="043b6-105">WiFi Direct is supported on Windows 10 IoT Core devices through the use of a WiFi Direct enabled USB WiFi adapter.</span></span> <span data-ttu-id="043b6-106">Para asegurarse de que Wi-Fi Direct está habilitado, deben cumplirse dos cosas:</span><span class="sxs-lookup"><span data-stu-id="043b6-106">To make sure that WiFi Direct is enabled two things need to be true:</span></span>
* <span data-ttu-id="043b6-107">el hardware del adaptador WiFi USB debe ser compatible con Wi-Fi Direct,</span><span class="sxs-lookup"><span data-stu-id="043b6-107">the hardware of the USB WiFi adapter needs to support WiFi Direct,</span></span>
* <span data-ttu-id="043b6-108">el controlador correspondiente del adaptador WiFi USB debe ser compatible con Wi-Fi Direct.</span><span class="sxs-lookup"><span data-stu-id="043b6-108">the corresponding driver of the USB WiFi adapter needs to support WiFi Direct.</span></span> 

<span data-ttu-id="043b6-109">Wi-Fi Direct proporciona una solución para la conectividad de dispositivo a dispositivo WiFi sin necesidad de que un punto de acceso inalámbrico (AP inalámbrico) Configure la conexión.</span><span class="sxs-lookup"><span data-stu-id="043b6-109">WiFi Direct provides a solution for WiFi device-to-device connectivity without the need for either a Wireless Access Point (wireless AP) to setup the connection.</span></span> <span data-ttu-id="043b6-110">Eche un vistazo a las API de UWP disponibles en el [espacio de nombres Windows. Devices. WiFiDirect](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) para ver lo que puede hacer con WiFiDirect.</span><span class="sxs-lookup"><span data-stu-id="043b6-110">Take a look at the UWP APIs available in the [Windows.Devices.WiFiDirect namespace](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) to see what you can do with WiFiDirect.</span></span>

## <a name="supported-adapters"></a><span data-ttu-id="043b6-111">Adaptadores admitidos</span><span class="sxs-lookup"><span data-stu-id="043b6-111">Supported Adapters</span></span>

<span data-ttu-id="043b6-112">Puede encontrar una lista de adaptadores de Wi-Fi que se han probado en Windows 10 IoT Core en nuestra página de [hardware compatible](../learn-about-hardware/HardwareCompatList.md) .</span><span class="sxs-lookup"><span data-stu-id="043b6-112">A list of WiFi adapters that have been tested on Windows 10 IoT Core can be found on our [Supported Hardware](../learn-about-hardware/HardwareCompatList.md) page.</span></span> 

## <a name="basic-sample-for-wifi-direct"></a><span data-ttu-id="043b6-113">Ejemplo básico para Wi-Fi Direct</span><span class="sxs-lookup"><span data-stu-id="043b6-113">Basic sample for WiFi Direct</span></span>

<span data-ttu-id="043b6-114">Puede probar fácilmente la funcionalidad de Wi-Fi Direct con el [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)de Wi-Fi Direct UWP.</span><span class="sxs-lookup"><span data-stu-id="043b6-114">You can easily test the WiFi Direct functionality with the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect).</span></span> <span data-ttu-id="043b6-115">Usaremos la C# versión y ejecutaremos el ejemplo de dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="043b6-115">We will use the C# version and run the sample of two devices.</span></span>

### <a name="set-up-the-two-devices"></a><span data-ttu-id="043b6-116">Configurar los dos dispositivos</span><span class="sxs-lookup"><span data-stu-id="043b6-116">Set up the two devices</span></span>
* <span data-ttu-id="043b6-117">MinnowBoardMax (MBM) con Windows 10 IoT Core (consulte las instrucciones aquí), con un dispositivo de protección WiFi de CanaKit</span><span class="sxs-lookup"><span data-stu-id="043b6-117">MinnowBoardMax (MBM) running Windows 10 IoT Core (see instructions here), with a CanaKit WiFi dongle</span></span>
* <span data-ttu-id="043b6-118">Conectar monitor, teclado y mouse al MBM</span><span class="sxs-lookup"><span data-stu-id="043b6-118">Connect monitor, keyboard and mouse to the MBM</span></span>
* <span data-ttu-id="043b6-119">Un equipo con Windows 10 que ejecute la última actualización de aniversario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="043b6-119">A Windows 10 PC running the latest Windows 10 Anniversary Update.</span></span> <span data-ttu-id="043b6-120">El equipo (o portátil) tendrá que tener compatibilidad con WiFi Direct (por ejemplo, una superficie de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="043b6-120">The PC (or laptop) will need to have WiFi Direct support (e.g. a Microsoft Surface)</span></span>
* <span data-ttu-id="043b6-121">Instalación de Visual Studio 2017 en el equipo con Windows 10</span><span class="sxs-lookup"><span data-stu-id="043b6-121">Install Visual Studio 2017 on your Windows 10 PC</span></span>
* <span data-ttu-id="043b6-122">Clone o descargue el [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)de Wi-Fi Direct UWP (la raíz del repositorio de github está [aquí](https://github.com/Microsoft/Windows-universal-samples)).</span><span class="sxs-lookup"><span data-stu-id="043b6-122">Clone or download the WiFi Direct UWP [sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(root of the GitHub repo is [here](https://github.com/Microsoft/Windows-universal-samples)).</span></span>
* <span data-ttu-id="043b6-123">Carga de C# la versión del ejemplo de Wi-Fi Direct UWP en Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="043b6-123">Load the C# version of the WiFi Direct UWP sample in Visual Studio 2017</span></span>

#### <a name="run-the-sample-on-the-two-devices"></a><span data-ttu-id="043b6-124">Ejecutar el ejemplo en los dos dispositivos</span><span class="sxs-lookup"><span data-stu-id="043b6-124">Run the sample on the two devices</span></span>
* <span data-ttu-id="043b6-125">Compile el ejemplo e impleméntelo/ejecútelo en MBM:</span><span class="sxs-lookup"><span data-stu-id="043b6-125">Compile the sample and deploy/run it on the MBM:</span></span>

    * <span data-ttu-id="043b6-126">Establecer el cuadro combinado "plataformas de solución" en "x86"</span><span class="sxs-lookup"><span data-stu-id="043b6-126">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="043b6-127">Seleccione "equipo remoto" en la lista desplegable "ejecutar".</span><span class="sxs-lookup"><span data-stu-id="043b6-127">Select "Remote Machine" from the "Run" dropdown</span></span>
    * <span data-ttu-id="043b6-128">Inicie el ejemplo en MBM sin depurar (presionando Ctrl-F5 o seleccionando "iniciar sin depurar" en el menú "depurar").</span><span class="sxs-lookup"><span data-stu-id="043b6-128">Start the sample on the MBM without debugging (either by pressing Ctrl-F5 or by selecting "Start Without Debugging" from the "Debug" menu)</span></span>
    * <span data-ttu-id="043b6-129">Debería ver el ejemplo de Wi-Fi Direct en ejecución en el monitor conectado a MBM</span><span class="sxs-lookup"><span data-stu-id="043b6-129">You should see the WiFi Direct sample running on the monitor connected to the MBM</span></span>
* <span data-ttu-id="043b6-130">Compile el ejemplo e impleméntelo y ejecútelo en el equipo con Windows 10:</span><span class="sxs-lookup"><span data-stu-id="043b6-130">Compile the sample and deploy/run it on the Windows 10 PC:</span></span>
    * <span data-ttu-id="043b6-131">Establecer el cuadro combinado "plataformas de solución" en "x86"</span><span class="sxs-lookup"><span data-stu-id="043b6-131">Set the "Solution Platforms" combobox to "x86"</span></span>
    * <span data-ttu-id="043b6-132">Seleccione "local" en la lista desplegable "ejecutar".</span><span class="sxs-lookup"><span data-stu-id="043b6-132">Select "Local" from the "Run" dropdown</span></span>
    * <span data-ttu-id="043b6-133">Inicie el ejemplo (F5 o Ctrl-F5).</span><span class="sxs-lookup"><span data-stu-id="043b6-133">Start the sample (either F5 or Ctrl-F5)</span></span>
    * <span data-ttu-id="043b6-134">Debería ver el ejemplo de Wi-Fi Direct en ejecución en su equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="043b6-134">You should see the WiFi Direct sample running on your Windows 10 PC</span></span>

### <a name="set-up-advertiser-and-connector"></a><span data-ttu-id="043b6-135">Configurar el anunciante y el conector</span><span class="sxs-lookup"><span data-stu-id="043b6-135">Set up Advertiser and Connector</span></span>
* <span data-ttu-id="043b6-136">En MBM, seleccione (1) "anunciador" y presione el botón "iniciar anuncio".</span><span class="sxs-lookup"><span data-stu-id="043b6-136">On the MBM, select (1) "Advertiser" and press the "Start Advertisement" button</span></span>

    * <span data-ttu-id="043b6-137">El MBM comenzará a anunciarse en el canal Wi-Fi Direct</span><span class="sxs-lookup"><span data-stu-id="043b6-137">The MBM will start advertising itself on the WiFi Direct channel</span></span>

        ![Pantalla de configuración del anunciante](../media/SetupWiFiDirect/Advertiser01.png)

        <span data-ttu-id="043b6-139">Observe el banner "Advertisement status" (estado de anuncio) en la parte inferior de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="043b6-139">Notice the "Advertisement Status" banner at the bottom of the app.</span></span>
    
* <span data-ttu-id="043b6-140">En el equipo con Windows 10, seleccione (2) "conector" y presione el botón "iniciar monitor".</span><span class="sxs-lookup"><span data-stu-id="043b6-140">On the Windows 10 PC, select (2) "Connector" and press the "Start Watcher" button</span></span> 

    * <span data-ttu-id="043b6-141">El equipo con Windows 10 iniciará el examen de las conexiones Wi-Fi Direct disponibles</span><span class="sxs-lookup"><span data-stu-id="043b6-141">The Windows 10 PC will start scanning for available WiFi Direct connections</span></span>
    * <span data-ttu-id="043b6-142">Una vez completado el análisis, debería ver el nombre de la MBM en la lista "dispositivos detectados"</span><span class="sxs-lookup"><span data-stu-id="043b6-142">When the scanning is complete, you should see the name of your MBM in the "Discovered Devices" list</span></span>

        ![Pantalla de configuración del conector](../media/SetupWiFiDirect/Connector01.png)

        <span data-ttu-id="043b6-144">Puede ver dos dispositivos en la lista (estamos interesados en "Ale-mbm01") y el mensaje "error de enumeración de DeviceWatcher completado".</span><span class="sxs-lookup"><span data-stu-id="043b6-144">You can see two devices listed (we're interested in "ale-mbm01"), and the "DeviceWatcher enumeration completed" message.</span></span>

### <a name="pair-the-devices"></a><span data-ttu-id="043b6-145">Emparejar los dispositivos</span><span class="sxs-lookup"><span data-stu-id="043b6-145">Pair the devices</span></span>
* <span data-ttu-id="043b6-146">En el equipo con Windows 10, seleccione MBM ("Ale-mbm01" en nuestro ejemplo) en la lista "dispositivos detectados" y presione el botón "conectar".</span><span class="sxs-lookup"><span data-stu-id="043b6-146">On the Windows 10 PC, select the MBM ("ale-mbm01" in our example) from the "Discovered Devices" list and press the "Connect" button</span></span>
* <span data-ttu-id="043b6-147">En el equipo con Windows 10, presione "sí" para iniciar el proceso de emparejamiento.</span><span class="sxs-lookup"><span data-stu-id="043b6-147">On the Windows 10 PC, press "Yes" to initiate the pairing process</span></span>

    ![Emparejamiento de inicio del conector](../media/SetupWiFiDirect/Connector02.png)

* <span data-ttu-id="043b6-149">En el monitor de MBM, debe un mensaje con el PIN</span><span class="sxs-lookup"><span data-stu-id="043b6-149">On the MBM monitor you should a message with the PIN</span></span>

    ![Cuadro de diálogo de anclaje del anunciante](../media/SetupWiFiDirect/Advertiser02.png)

* <span data-ttu-id="043b6-151">En el equipo con Windows 10, debería ver un cuadro de diálogo en el que debe escribir el PIN</span><span class="sxs-lookup"><span data-stu-id="043b6-151">On the Windows 10 PC, you should see a dialog where you need to enter the PIN</span></span>

    ![Cuadro de diálogo PIN del conector](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a><span data-ttu-id="043b6-153">Hable en el canal</span><span class="sxs-lookup"><span data-stu-id="043b6-153">Talk on the channel</span></span>
* <span data-ttu-id="043b6-154">Los dos dispositivos deben estar conectados.</span><span class="sxs-lookup"><span data-stu-id="043b6-154">The two devices should be connected.</span></span> <span data-ttu-id="043b6-155">Debería ver un identificador de dispositivo generado aleatoriamente ("hqffpzhz. GGG" en nuestro ejemplo) en ambas pantallas de la lista "dispositivos conectados".</span><span class="sxs-lookup"><span data-stu-id="043b6-155">You should see a randomly generated device id ("hqffpzhz.ggg" in our example) on both screens in the "Connected Devices" list</span></span>

    ![Dispositivo conectado al anunciante](../media/SetupWiFiDirect/Advertiser03.png)

    ![Dispositivo conectado al conector](../media/SetupWiFiDirect/Connector04.png)

* <span data-ttu-id="043b6-158">Ahora tiene una configuración de canal (o Socket) dúplex completo</span><span class="sxs-lookup"><span data-stu-id="043b6-158">You now have a full-duplex channel (or socket) set up</span></span>

    * <span data-ttu-id="043b6-159">en MBM, seleccione el dispositivo ("hqffpzhz. GGG") de la lista "dispositivos conectados".</span><span class="sxs-lookup"><span data-stu-id="043b6-159">on the MBM, select the device ("hqffpzhz.ggg") from the "Connected Devices" list</span></span>
    * <span data-ttu-id="043b6-160">Escriba un mensaje en el cuadro de texto "Escriba un mensaje"</span><span class="sxs-lookup"><span data-stu-id="043b6-160">type a message in the "Enter a message" textbox</span></span>
    * <span data-ttu-id="043b6-161">Presione el botón "enviar"</span><span class="sxs-lookup"><span data-stu-id="043b6-161">press the "Send" button</span></span>
    * <span data-ttu-id="043b6-162">debería ver el mensaje que se recibe desde el equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="043b6-162">you should see the message being received from the Windows 10 PC</span></span>
    * <span data-ttu-id="043b6-163">intente enviar un mensaje desde el equipo con Windows 10 a MBM</span><span class="sxs-lookup"><span data-stu-id="043b6-163">try sending a message from the Windows 10 PC to the MBM</span></span>
