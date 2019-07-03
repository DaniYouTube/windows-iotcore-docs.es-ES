---
title: Configuración de dispositivos Qualcomm
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo Qualcomm con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 02f6c013c428a271d3b3956c88edc1ce8f4fdbf2
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "66835612"
---
# <a name="setting-up-a-qualcomm-device"></a><span data-ttu-id="9af0d-104">Configuración de un dispositivo Qualcomm</span><span class="sxs-lookup"><span data-stu-id="9af0d-104">Setting up a Qualcomm device</span></span>

<span data-ttu-id="9af0d-105">Si lo que quiere es fabricar con un dispositivo Qualcomm, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="9af0d-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="9af0d-106">No se pueden usar imágenes del creador para la fabricación.</span><span class="sxs-lookup"><span data-stu-id="9af0d-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="9af0d-107">Para asegurarse de que el dispositivo ahora arranca desde la memoria eMMC, escriba de nuevo la configuración del BIOS y cambie el orden de la unidad de arranque para que se cargue desde el disco duro en lugar de la unidad USB.</span><span class="sxs-lookup"><span data-stu-id="9af0d-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="9af0d-108">Uso de eMMC</span><span class="sxs-lookup"><span data-stu-id="9af0d-108">Using eMMC</span></span>

1. <span data-ttu-id="9af0d-109">Descargue e instale la herramienta de actualización de DragonBoard para el equipo [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) o [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip).</span><span class="sxs-lookup"><span data-stu-id="9af0d-109">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="9af0d-110">Descargue la [FFU de DragonBoard de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows/iot-core/downloads).</span><span class="sxs-lookup"><span data-stu-id="9af0d-110">Download the [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads).</span></span>
3. <span data-ttu-id="9af0d-111">Haga doble clic en el archivo ISO descargado y busque la unidad de Virtual CD montada.</span><span class="sxs-lookup"><span data-stu-id="9af0d-111">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="9af0d-112">Esta unidad contendrá un archivo de instalador (.msi); haga doble clic en él.</span><span class="sxs-lookup"><span data-stu-id="9af0d-112">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="9af0d-113">Esto crea un directorio en el equipo en  `C:\Program Files (x86)\Microsoft IoT\FFU\` donde debería ver un archivo de imagen, "flash.ffu".</span><span class="sxs-lookup"><span data-stu-id="9af0d-113">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="9af0d-114">Para asegurarse de que DragonBoard está en modo de descarga, establezca que el primer arranque cambie en la placa a arranque de USB, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="9af0d-114">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="9af0d-115">Después, conecte DragonBoard al equipo host a través de un cable microUSB y, luego, conecte DragonBoard a una fuente de alimentación de 12 V (> 1 A).</span><span class="sxs-lookup"><span data-stu-id="9af0d-115">Then, connect the DragonBoard to the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="9af0d-116">Inicie la herramienta de actualización de DragonBoard, que debe detectar que DragonBoard se conecta al equipo con un círculo verde.</span><span class="sxs-lookup"><span data-stu-id="9af0d-116">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="9af0d-117">Haga clic en "Examinar" en la FFU del DragonBoard que ha descargado y, después, haga clic en el botón _Programa_.</span><span class="sxs-lookup"><span data-stu-id="9af0d-117">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="9af0d-118">Haga clic otra vez en "Examinar" y seleccione "rawprogram0.xml", que se ha generado en el paso 5.</span><span class="sxs-lookup"><span data-stu-id="9af0d-118">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="9af0d-119">Luego haga clic en el botón "Programa".</span><span class="sxs-lookup"><span data-stu-id="9af0d-119">Then click the "Program" button.</span></span>
7. <span data-ttu-id="9af0d-120">Una vez completada la descarga, desconecte la fuente de alimentación y el cable microUSB de la placa y cambie el conmutador de arranque USB a _OFF_.</span><span class="sxs-lookup"><span data-stu-id="9af0d-120">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="9af0d-121">Conecte una pantalla HDMI, un ratón y un teclado a DragonBoard y vuelva a conectar la fuente de alimentación.</span><span class="sxs-lookup"><span data-stu-id="9af0d-121">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and reconnect the power supply.</span></span> <span data-ttu-id="9af0d-122">Pasados unos minutos, debería ver la aplicación predeterminada Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="9af0d-122">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![DragonBoard en modo de descarga](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="9af0d-124">Conexión a una red</span><span class="sxs-lookup"><span data-stu-id="9af0d-124">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="9af0d-125">Conexión por cable</span><span class="sxs-lookup"><span data-stu-id="9af0d-125">Wired connection</span></span>
<span data-ttu-id="9af0d-126">Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="9af0d-126">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="9af0d-127">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="9af0d-127">Wireless connection</span></span>
<span data-ttu-id="9af0d-128">Si el dispositivo admite la conectividad Wi-Fi y le ha conectado una pantalla, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9af0d-128">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="9af0d-129">Vaya a la aplicación predeterminada y haga clic en el botón de configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="9af0d-129">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="9af0d-130">En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).</span><span class="sxs-lookup"><span data-stu-id="9af0d-130">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="9af0d-131">El dispositivo realizará una exploración de redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="9af0d-131">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="9af0d-132">Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.</span><span class="sxs-lookup"><span data-stu-id="9af0d-132">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="9af0d-133">Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9af0d-133">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="9af0d-134">Vaya al Panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="9af0d-134">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="9af0d-135">Busque la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="9af0d-135">Find your unconfigured board from the list.</span></span> <span data-ttu-id="9af0d-136">El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="9af0d-136">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="9af0d-137">Si la placa no aparece después de unos minutos, intente reiniciarla.</span><span class="sxs-lookup"><span data-stu-id="9af0d-137">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="9af0d-138">Haga clic en _Configurar dispositivo_ y escriba las credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="9af0d-138">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="9af0d-139">Esto conectará la placa a la red.</span><span class="sxs-lookup"><span data-stu-id="9af0d-139">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="9af0d-140">La Wi-Fi debe estar activada en el equipo para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="9af0d-140">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="9af0d-141">Conexión al Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="9af0d-141">Connect to Windows Device Portal</span></span>

<span data-ttu-id="9af0d-142">Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="9af0d-142">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="9af0d-143">El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles.</span><span class="sxs-lookup"><span data-stu-id="9af0d-143">The device portal makes valuable configuration and device management capabilities available.</span></span> 



