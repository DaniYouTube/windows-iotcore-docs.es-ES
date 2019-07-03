---
title: Configuración de un dispositivo Raspberry Pi
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo Raspberry Pi con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "66182197"
---
# <a name="setting-up-a-raspberry-pi"></a><span data-ttu-id="aa7c5-104">Configuración de un dispositivo Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="aa7c5-104">Setting up a Raspberry Pi</span></span>

## <a name="overview"></a><span data-ttu-id="aa7c5-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="aa7c5-105">Overview</span></span>

> [!NOTE]
> <span data-ttu-id="aa7c5-106">El panel de información no se puede usar para configurar Raspberry Pi 3B+.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-106">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="aa7c5-107">Si tiene un dispositivo 3B+, debe usar la [versión preliminar técnica de 3B+](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="aa7c5-107">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="aa7c5-108">Vea las [limitaciones conocidas](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) de la versión preliminar técnica para determinar si esto es adecuado para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-108">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa7c5-109">Cuando aparezca el mensaje emergente "formatear el disco", _no_ lo formatee.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-109">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="aa7c5-110">Estamos trabajando en una solución para este problema.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-110">We are working on a fix for this issue.</span></span>

<span data-ttu-id="aa7c5-111">Al configurar un dispositivo Raspberry Pi para crear prototipos, se recomienda usar el Panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-111">When setting up a Raspberry Pi for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="aa7c5-112">Pero si lo que quiere es fabricar con un dispositivo Raspberry Pi, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="aa7c5-112">However, if you're looking to manufacture with a Raspberry Pi, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="aa7c5-113">No se pueden usar imágenes del creador para la fabricación.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-113">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="aa7c5-114">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="aa7c5-114">Using the Dashboard</span></span>

<span data-ttu-id="aa7c5-115">Para instalar una imagen de IoT Core o descargarlo en el dispositivo Raspberry Pi, necesitará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="aa7c5-115">To flash, or download, IoT Core onto your Raspberry Pi, you'll need:</span></span>
* <span data-ttu-id="aa7c5-116">Un equipo que ejecute Windows 10</span><span class="sxs-lookup"><span data-stu-id="aa7c5-116">A computer running Windows 10</span></span> 
* <span data-ttu-id="aa7c5-117">El [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)</span><span class="sxs-lookup"><span data-stu-id="aa7c5-117">[Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/downloads)</span></span>
* <span data-ttu-id="aa7c5-118">Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk</span><span class="sxs-lookup"><span data-stu-id="aa7c5-118">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="aa7c5-119">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="aa7c5-119">An external display</span></span>
* <span data-ttu-id="aa7c5-120">Otros periféricos (por ejemplo, mouse, teclado, etc.)</span><span class="sxs-lookup"><span data-stu-id="aa7c5-120">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="aa7c5-121">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="aa7c5-121">Instructions</span></span>

1. <span data-ttu-id="aa7c5-122">Ejecute el Panel de Windows 10 IoT Core, haga clic en *Set up a new device* (Configurar un nuevo dispositivo) e inserte una tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-122">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="aa7c5-123">Conecte el dispositivo Raspberry Pi a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-123">Hook up your Raspberry Pi to an external display.</span></span>
3. <span data-ttu-id="aa7c5-124">Rellene los campos.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-124">Fill out the fields.</span></span> <span data-ttu-id="aa7c5-125">Seleccione "Broadcomm [Raspberry Pi 2 & 3]" como el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-125">Select "Broadcomm [Raspberry Pi 2 & 3]" as the device type.</span></span> <span data-ttu-id="aa7c5-126">Asegúrese de asignar un nombre y una contraseña nuevos al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-126">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="aa7c5-127">En caso contrario, las credenciales predeterminadas permanecerán como:</span><span class="sxs-lookup"><span data-stu-id="aa7c5-127">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="aa7c5-128">Acepte los términos de licencia de software y haga clic en *Descargar e instalar*.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-128">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="aa7c5-129">Si todo es correcto, verá que Windows 10 IoT Core instala una imagen en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-129">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![Captura de pantalla del panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="aa7c5-131">Conexión a una red</span><span class="sxs-lookup"><span data-stu-id="aa7c5-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="aa7c5-132">Conexión por cable</span><span class="sxs-lookup"><span data-stu-id="aa7c5-132">Wired connection</span></span>
<span data-ttu-id="aa7c5-133">Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="aa7c5-134">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="aa7c5-134">Wireless connection</span></span>
<span data-ttu-id="aa7c5-135">Si el dispositivo admite la conectividad Wi-Fi y le ha conectado una pantalla, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="aa7c5-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="aa7c5-136">Vaya a la aplicación predeterminada y haga clic en el botón de configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="aa7c5-137">En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).</span><span class="sxs-lookup"><span data-stu-id="aa7c5-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="aa7c5-138">El dispositivo realizará una exploración de redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="aa7c5-139">Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="aa7c5-140">Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="aa7c5-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="aa7c5-141">Vaya al Panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="aa7c5-142">Busque la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="aa7c5-143">El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="aa7c5-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="aa7c5-144">Si la placa no aparece después de unos minutos, intente reiniciarla.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="aa7c5-145">Haga clic en _Configurar dispositivo_ y escriba las credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="aa7c5-146">Esto conectará la placa a la red.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="aa7c5-147">La Wi-Fi debe estar activada en el equipo para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="aa7c5-148">Conexión al Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="aa7c5-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="aa7c5-149">Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="aa7c5-150">El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 
