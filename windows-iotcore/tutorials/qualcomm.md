---
title: Configuración de dispositivos de Qualcomm
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo de Qualcomm con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 949c5af00f48b4c2049e711d4e18385fe9f3c18e
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182207"
---
# <a name="setting-up-a-qualcomm-device"></a><span data-ttu-id="752c2-104">Cómo configurar un dispositivo de Qualcomm</span><span class="sxs-lookup"><span data-stu-id="752c2-104">Setting up a Qualcomm device</span></span>

<span data-ttu-id="752c2-105">Si busca para fabricar con un dispositivo de Qualcomm, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="752c2-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="752c2-106">No puede usar imágenes de creador de fabricación.</span><span class="sxs-lookup"><span data-stu-id="752c2-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="752c2-107">Asegúrese de que el dispositivo ahora consiste en arrancar desde la memoria eMMC volver a escribir la configuración del BIOS y cambiando el orden de la unidad de arranque cargar de la unidad en lugar de desde la unidad USB.</span><span class="sxs-lookup"><span data-stu-id="752c2-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="752c2-108">Uso de eMMC</span><span class="sxs-lookup"><span data-stu-id="752c2-108">Using eMMC</span></span>

1. <span data-ttu-id="752c2-109">Descargue e instale la herramienta de actualización DragonBoard para su [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) o [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) máquina.</span><span class="sxs-lookup"><span data-stu-id="752c2-109">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="752c2-110">Descargue el [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).</span><span class="sxs-lookup"><span data-stu-id="752c2-110">Download the [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).</span></span>
3. <span data-ttu-id="752c2-111">Haga doble clic en el archivo ISO descargado y busque la montado Virtual-unidad de CD.</span><span class="sxs-lookup"><span data-stu-id="752c2-111">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="752c2-112">Esta unidad contendrá un archivo de instalador (.msi); Haga doble clic en él.</span><span class="sxs-lookup"><span data-stu-id="752c2-112">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="752c2-113">Esto crea un nuevo directorio en su equipo bajo `C:\Program Files (x86)\Microsoft IoT\FFU\` en lo que debería ver un archivo de imagen, "flash.ffu".</span><span class="sxs-lookup"><span data-stu-id="752c2-113">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="752c2-114">Asegúrese de que su DragonBoard está en modo de descarga estableciendo el primer arranque cambie en el panel a USB de arranque, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="752c2-114">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="752c2-115">Conectar el equipo host a través de un cable microUSB DragonBoard, a continuación, conecte el DragonBoard a un 12V (> 1A) fuente de alimentación.</span><span class="sxs-lookup"><span data-stu-id="752c2-115">Then, connect DragonBoard the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="752c2-116">Inicie la herramienta de actualización DragonBoard, que debe detectar que el DragonBoard se conecte al equipo con un círculo verde.</span><span class="sxs-lookup"><span data-stu-id="752c2-116">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="752c2-117">"Examinar" para el DragonBoard FFU que ha descargado, a continuación, haga clic en el _programa_ botón.</span><span class="sxs-lookup"><span data-stu-id="752c2-117">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="752c2-118">Haga clic en "Examinar" nuevo y seleccione "rawprogram0.xml" que se generó en el paso 5.</span><span class="sxs-lookup"><span data-stu-id="752c2-118">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="752c2-119">A continuación, haga clic en el botón "Programa".</span><span class="sxs-lookup"><span data-stu-id="752c2-119">Then click the "Program" button.</span></span>
7. <span data-ttu-id="752c2-120">Una vez completada la descarga, desconecte el cable de alimentación de suministro y microUSB desde el panel y alternar el modificador de arranque USB al _OFF_.</span><span class="sxs-lookup"><span data-stu-id="752c2-120">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="752c2-121">Conectar una pantalla HDMI, un mouse y teclado al DragonBoard y rec-onectar la fuente de alimentación.</span><span class="sxs-lookup"><span data-stu-id="752c2-121">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and rec-onnect the power supply.</span></span> <span data-ttu-id="752c2-122">Después de unos minutos, debería ver la aplicación predeterminada de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="752c2-122">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![DragonBoard en modo de descarga](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="752c2-124">Conectarse a una red</span><span class="sxs-lookup"><span data-stu-id="752c2-124">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="752c2-125">Conexión con cable</span><span class="sxs-lookup"><span data-stu-id="752c2-125">Wired connection</span></span>
<span data-ttu-id="752c2-126">Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="752c2-126">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="752c2-127">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="752c2-127">Wireless connection</span></span>
<span data-ttu-id="752c2-128">Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:</span><span class="sxs-lookup"><span data-stu-id="752c2-128">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="752c2-129">Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="752c2-129">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="752c2-130">En la página de configuración, seleccione _red y Wi-Fi_.</span><span class="sxs-lookup"><span data-stu-id="752c2-130">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="752c2-131">El dispositivo realizará un examen para redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="752c2-131">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="752c2-132">Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.</span><span class="sxs-lookup"><span data-stu-id="752c2-132">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="752c2-133">Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:</span><span class="sxs-lookup"><span data-stu-id="752c2-133">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="752c2-134">Vaya al panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="752c2-134">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="752c2-135">Encuentre la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="752c2-135">Find your unconfigured board from the list.</span></span> <span data-ttu-id="752c2-136">Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="752c2-136">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="752c2-137">Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.</span><span class="sxs-lookup"><span data-stu-id="752c2-137">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="752c2-138">Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="752c2-138">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="752c2-139">La placa de esto conectará a la red.</span><span class="sxs-lookup"><span data-stu-id="752c2-139">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="752c2-140">Wi-Fi en el equipo debe estar activada para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="752c2-140">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="752c2-141">Conectarse a Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="752c2-141">Connect to Windows Device Portal</span></span>

<span data-ttu-id="752c2-142">Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="752c2-142">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="752c2-143">El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="752c2-143">The device portal makes valuable configuration and device management capabilities available.</span></span> 



