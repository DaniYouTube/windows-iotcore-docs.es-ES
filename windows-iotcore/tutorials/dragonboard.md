---
title: Configurar un Dragonboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar su Dragonboard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 6488237a41f42c7acbe9e5e1c68466548577ab38
ms.sourcegitcommit: fa4a29fcd5af464924a0a5ab581f08f631a3ad72
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835609"
---
# <a name="setting-up-a-dragonboard"></a><span data-ttu-id="b2412-104">Configurar un Dragonboard</span><span class="sxs-lookup"><span data-stu-id="b2412-104">Setting up a Dragonboard</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2412-105">Cuando está trabajando con un nuevo Dragonboard, acompañada de Android instalado.</span><span class="sxs-lookup"><span data-stu-id="b2412-105">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="b2412-106">Deberá borrar y cargar el dispositivo mediante el eMMC intermitencia en el método, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm).</span><span class="sxs-lookup"><span data-stu-id="b2412-106">You will need to wipe and load the device using the eMMC flashing method, [here](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm).</span></span>

> [!NOTE]
> <span data-ttu-id="b2412-107">Si experimenta problemas relacionados con el audio con su DragonBoard, le recomendamos que lea manual de Qualcomm [aquí](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span><span class="sxs-lookup"><span data-stu-id="b2412-107">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

<span data-ttu-id="b2412-108">Al configurar un Dragonboard para crear prototipos, se recomienda usar el panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="b2412-108">When setting up a Dragonboard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="b2412-109">Sin embargo, si busca para fabricar con un Dragonboard, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="b2412-109">However, if you're looking to manufacture with a Dragonboard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="b2412-110">No puede usar imágenes de creador de fabricación.</span><span class="sxs-lookup"><span data-stu-id="b2412-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a><span data-ttu-id="b2412-111">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="b2412-111">Using the Dashboard</span></span>

<span data-ttu-id="b2412-112">Para flash o descargar IoT Core en su MinnowBoard, necesitará:</span><span class="sxs-lookup"><span data-stu-id="b2412-112">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="b2412-113">Un equipo que ejecuta Windows 10</span><span class="sxs-lookup"><span data-stu-id="b2412-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="b2412-114">Panel de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="b2412-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="b2412-115">Cable MicroUSB</span><span class="sxs-lookup"><span data-stu-id="b2412-115">MicroUSB cable</span></span>
* <span data-ttu-id="b2412-116">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="b2412-116">An external display</span></span>
* <span data-ttu-id="b2412-117">Cualquier otro periférico (por ejemplo, mouse, teclado, etcetera.)</span><span class="sxs-lookup"><span data-stu-id="b2412-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="b2412-118">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b2412-118">Instructions</span></span>

1. <span data-ttu-id="b2412-119">Ejecutar el panel de Windows 10 IoT Core y haga clic en *configurar un nuevo dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="b2412-119">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device*.</span></span>
2. <span data-ttu-id="b2412-120">Seleccione "Qualcomm [DragonBoard 410c]" como el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b2412-120">Select "Qualcomm [DragonBoard 410c]" as the device type.</span></span>
3. <span data-ttu-id="b2412-121">Conecte el DragonBoard a su compuetr mediante un cable microUSB.</span><span class="sxs-lookup"><span data-stu-id="b2412-121">Connect the DragonBoard to your compuetr using a microUSB cable.</span></span>
4. <span data-ttu-id="b2412-122">Conecte su DragongBoard a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="b2412-122">Hook up your DragongBoard to a external display.</span></span>
5. <span data-ttu-id="b2412-123">Encender su Dragonboard mediante un 12V (> 1A) alimentación mientras mantiene presionada (+) para Subir volumen botón.</span><span class="sxs-lookup"><span data-stu-id="b2412-123">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="b2412-124">El dispositivo - cuando se conecta a una pantalla - debe aparecer la imagen de un martillo, un rayo y un engranaje.</span><span class="sxs-lookup"><span data-stu-id="b2412-124">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span>
6. <span data-ttu-id="b2412-125">Ahora, el dispositivo debe estar visible en el panel, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="b2412-125">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="b2412-126">Seleccione el dispositivo adecuado.</span><span class="sxs-lookup"><span data-stu-id="b2412-126">Select the appropriate device.</span></span>
7. <span data-ttu-id="b2412-127">Acepte los términos de licencia de software y haga clic en **descargue e instale**.</span><span class="sxs-lookup"><span data-stu-id="b2412-127">Accept the software license terms and click **Download and install**.</span></span> <span data-ttu-id="b2412-128">Verá que ahora parpadea en su dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="b2412-128">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>

![DragonBoard en modo de flash](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="b2412-130">Conectarse a una red</span><span class="sxs-lookup"><span data-stu-id="b2412-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="b2412-131">Conexión con cable</span><span class="sxs-lookup"><span data-stu-id="b2412-131">Wired connection</span></span>
<span data-ttu-id="b2412-132">Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="b2412-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="b2412-133">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="b2412-133">Wireless connection</span></span>
<span data-ttu-id="b2412-134">Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:</span><span class="sxs-lookup"><span data-stu-id="b2412-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="b2412-135">Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="b2412-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="b2412-136">En la página de configuración, seleccione _red y Wi-Fi_.</span><span class="sxs-lookup"><span data-stu-id="b2412-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="b2412-137">El dispositivo realizará un examen para redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="b2412-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="b2412-138">Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.</span><span class="sxs-lookup"><span data-stu-id="b2412-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="b2412-139">Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:</span><span class="sxs-lookup"><span data-stu-id="b2412-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="b2412-140">Vaya al panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="b2412-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="b2412-141">Encuentre la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="b2412-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="b2412-142">Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="b2412-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="b2412-143">Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.</span><span class="sxs-lookup"><span data-stu-id="b2412-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="b2412-144">Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="b2412-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="b2412-145">La placa de esto conectará a la red.</span><span class="sxs-lookup"><span data-stu-id="b2412-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="b2412-146">Wi-Fi en el equipo debe estar activada para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="b2412-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="b2412-147">Conectarse a Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="b2412-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="b2412-148">Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="b2412-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="b2412-149">El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2412-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

