---
title: Configuración de un dispositivo DragonBoard
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo DragonBoard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, DragonBoard
ms.custom: RS5
ms.openlocfilehash: 49de9a3007dac12a13a42a334d33dc79c96f96af
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721748"
---
# <a name="setting-up-a-dragonboard"></a><span data-ttu-id="46a99-104">Configuración de un dispositivo DragonBoard</span><span class="sxs-lookup"><span data-stu-id="46a99-104">Setting up a Dragonboard</span></span>

> [!IMPORTANT]
> <span data-ttu-id="46a99-105">Cuando trabaja con un nuevo dispositivo DragonBoard, viene con Android instalado.</span><span class="sxs-lookup"><span data-stu-id="46a99-105">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="46a99-106">Deberá borrar y cargar el dispositivo mediante el método de instalación de imagen eMMC, como se indica [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/qualcomm).</span><span class="sxs-lookup"><span data-stu-id="46a99-106">You will need to wipe and load the device using the eMMC flashing method, [here](https://docs.microsoft.com/windows/iot-core/tutorials/qualcomm).</span></span>

> [!NOTE]
> <span data-ttu-id="46a99-107">Si experimenta problemas relacionados con el audio con DragonBoard, le recomendamos que consulte el manual de Qualcomm [aquí](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span><span class="sxs-lookup"><span data-stu-id="46a99-107">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

<span data-ttu-id="46a99-108">Al configurar un dispositivo DragonBoard para crear prototipos, se recomienda usar el Panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="46a99-108">When setting up a Dragonboard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="46a99-109">Si lo que quiere es fabricar con un dispositivo DragonBoard, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="46a99-109">However, if you're looking to manufacture with a Dragonboard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="46a99-110">No se pueden usar imágenes del creador para la fabricación.</span><span class="sxs-lookup"><span data-stu-id="46a99-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a><span data-ttu-id="46a99-111">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="46a99-111">Using the Dashboard</span></span>

<span data-ttu-id="46a99-112">Para instalar una imagen de IoT Core o descargarlo en el dispositivo MinnowBoard, necesitará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="46a99-112">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="46a99-113">Un equipo que ejecute Windows 10</span><span class="sxs-lookup"><span data-stu-id="46a99-113">A computer running Windows 10</span></span> 
* <span data-ttu-id="46a99-114">El [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)</span><span class="sxs-lookup"><span data-stu-id="46a99-114">[Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/downloads)</span></span>
* <span data-ttu-id="46a99-115">Un cable microUSB</span><span class="sxs-lookup"><span data-stu-id="46a99-115">MicroUSB cable</span></span>
* <span data-ttu-id="46a99-116">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="46a99-116">An external display</span></span>
* <span data-ttu-id="46a99-117">Otros periféricos (por ejemplo, mouse, teclado, etc.)</span><span class="sxs-lookup"><span data-stu-id="46a99-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="46a99-118">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="46a99-118">Instructions</span></span>

1. <span data-ttu-id="46a99-119">Ejecute el Panel de Windows 10 IoT Core y haga clic en *Set up a new device* (Configurar un nuevo dispositivo).</span><span class="sxs-lookup"><span data-stu-id="46a99-119">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device*.</span></span>
2. <span data-ttu-id="46a99-120">Seleccione "Qualcomm [DragonBoard 410c]" como tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="46a99-120">Select "Qualcomm [DragonBoard 410c]" as the device type.</span></span>
3. <span data-ttu-id="46a99-121">Conecte el dispositivo DragonBoard a su equipo con un cable microUSB.</span><span class="sxs-lookup"><span data-stu-id="46a99-121">Connect the DragonBoard to your compuetr using a microUSB cable.</span></span>
4. <span data-ttu-id="46a99-122">Conecte el dispositivo DragongBoard a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="46a99-122">Hook up your DragongBoard to a external display.</span></span>
5. <span data-ttu-id="46a99-123">Encienda el dispositivo DragonBoard con una fuente de alimentación de 12 V (> 1 A) mientras mantiene presionado el botón de subir volumen (+).</span><span class="sxs-lookup"><span data-stu-id="46a99-123">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="46a99-124">El dispositivo, cuando se conecta a una pantalla, debe mostrar la imagen de un martillo, un rayo y un engranaje.</span><span class="sxs-lookup"><span data-stu-id="46a99-124">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span>
6. <span data-ttu-id="46a99-125">Ahora, el dispositivo debe estar visible en el panel, como se muestra debajo.</span><span class="sxs-lookup"><span data-stu-id="46a99-125">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="46a99-126">Seleccione el dispositivo correspondiente.</span><span class="sxs-lookup"><span data-stu-id="46a99-126">Select the appropriate device.</span></span>
7. <span data-ttu-id="46a99-127">Acepte los términos de licencia de software y, después, haga clic en **Descargar e instalar**.</span><span class="sxs-lookup"><span data-stu-id="46a99-127">Accept the software license terms and click **Download and install**.</span></span> <span data-ttu-id="46a99-128">Verá que Windows 10 IoT Core instala una imagen en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="46a99-128">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>

![DragonBoard en modo sobrescribir](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a><span data-ttu-id="46a99-130">Conexión a una red</span><span class="sxs-lookup"><span data-stu-id="46a99-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="46a99-131">Conexión por cable</span><span class="sxs-lookup"><span data-stu-id="46a99-131">Wired connection</span></span>
<span data-ttu-id="46a99-132">Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="46a99-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="46a99-133">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="46a99-133">Wireless connection</span></span>
<span data-ttu-id="46a99-134">Si el dispositivo admite la conectividad Wi-Fi y le ha conectado una pantalla, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="46a99-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="46a99-135">Vaya a la aplicación predeterminada y haga clic en el botón de configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="46a99-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="46a99-136">En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).</span><span class="sxs-lookup"><span data-stu-id="46a99-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="46a99-137">El dispositivo realizará una exploración de redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="46a99-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="46a99-138">Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.</span><span class="sxs-lookup"><span data-stu-id="46a99-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="46a99-139">Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="46a99-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="46a99-140">Vaya al Panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="46a99-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="46a99-141">Busque la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="46a99-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="46a99-142">El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="46a99-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="46a99-143">Si la placa no aparece después de unos minutos, intente reiniciarla.</span><span class="sxs-lookup"><span data-stu-id="46a99-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="46a99-144">Haga clic en _Configurar dispositivo_ y escriba las credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="46a99-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="46a99-145">Esto conectará la placa a la red.</span><span class="sxs-lookup"><span data-stu-id="46a99-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="46a99-146">La Wi-Fi debe estar activada en el equipo para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="46a99-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="46a99-147">Conexión al Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="46a99-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="46a99-148">Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="46a99-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="46a99-149">El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles.</span><span class="sxs-lookup"><span data-stu-id="46a99-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

