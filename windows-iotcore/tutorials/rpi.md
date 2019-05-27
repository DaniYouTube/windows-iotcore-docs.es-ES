---
title: Configurar un dispositivo Raspberry Pi
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar Raspberry Pi con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182197"
---
# <a name="setting-up-a-raspberry-pi"></a><span data-ttu-id="d27c8-104">Configurar un dispositivo Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="d27c8-104">Setting up a Raspberry Pi</span></span>

## <a name="overview"></a><span data-ttu-id="d27c8-105">Información general</span><span class="sxs-lookup"><span data-stu-id="d27c8-105">Overview</span></span>

> [!NOTE]
> <span data-ttu-id="d27c8-106">No se puede utilizar el panel usado para configurar el dispositivo Raspberry Pi 3B +.</span><span class="sxs-lookup"><span data-stu-id="d27c8-106">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="d27c8-107">Si tiene un dispositivo 3B +, debe usar el [vista previa técnica de 3B +](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="d27c8-107">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="d27c8-108">Consulte la [limitaciones conocidas](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) de technical preview para determinar si esto es adecuado para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="d27c8-108">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d27c8-109">Cuando el "dar formato al disco" pop hasta, hacer _no_ formatear el disco.</span><span class="sxs-lookup"><span data-stu-id="d27c8-109">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="d27c8-110">Estamos trabajando en una solución para este problema.</span><span class="sxs-lookup"><span data-stu-id="d27c8-110">We are working on a fix for this issue.</span></span>

<span data-ttu-id="d27c8-111">Al configurar un dispositivo Raspberry Pi para la creación de prototipos, se recomienda usar el panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d27c8-111">When setting up a Raspberry Pi for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="d27c8-112">Sin embargo, si busca para fabricar con Raspberry Pi, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="d27c8-112">However, if you're looking to manufacture with a Raspberry Pi, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="d27c8-113">No puede usar imágenes de creador de fabricación.</span><span class="sxs-lookup"><span data-stu-id="d27c8-113">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="d27c8-114">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="d27c8-114">Using the Dashboard</span></span>

<span data-ttu-id="d27c8-115">Para flash o descargar IoT Core en su Raspberry Pi, necesitará:</span><span class="sxs-lookup"><span data-stu-id="d27c8-115">To flash, or download, IoT Core onto your Raspberry Pi, you'll need:</span></span>
* <span data-ttu-id="d27c8-116">Un equipo que ejecuta Windows 10</span><span class="sxs-lookup"><span data-stu-id="d27c8-116">A computer running Windows 10</span></span> 
* [<span data-ttu-id="d27c8-117">Panel de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="d27c8-117">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="d27c8-118">Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk</span><span class="sxs-lookup"><span data-stu-id="d27c8-118">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="d27c8-119">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="d27c8-119">An external display</span></span>
* <span data-ttu-id="d27c8-120">Cualquier otro periférico (por ejemplo, mouse, teclado, etcetera.)</span><span class="sxs-lookup"><span data-stu-id="d27c8-120">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="d27c8-121">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d27c8-121">Instructions</span></span>

1. <span data-ttu-id="d27c8-122">Ejecutar el panel de Windows 10 IoT Core y haga clic en *configurar un nuevo dispositivo* e inserte una tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="d27c8-122">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="d27c8-123">Conecte Raspberry Pi a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="d27c8-123">Hook up your Raspberry Pi to an external display.</span></span>
3. <span data-ttu-id="d27c8-124">Rellene los campos.</span><span class="sxs-lookup"><span data-stu-id="d27c8-124">Fill out the fields.</span></span> <span data-ttu-id="d27c8-125">Seleccione "Broadcomm [Raspberry Pi 2 & 3]" como el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d27c8-125">Select "Broadcomm [Raspberry Pi 2 & 3]" as the device type.</span></span> <span data-ttu-id="d27c8-126">Asegúrese de dar a su dispositivo un nuevo nombre y una contraseña.</span><span class="sxs-lookup"><span data-stu-id="d27c8-126">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="d27c8-127">En caso contrario, las credenciales predeterminadas permanecerá como:</span><span class="sxs-lookup"><span data-stu-id="d27c8-127">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="d27c8-128">Acepte los términos de licencia de software y haga clic en *descargue e instale*.</span><span class="sxs-lookup"><span data-stu-id="d27c8-128">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="d27c8-129">Si todo va bien, verá que ahora es Windows 10 IoT Core intermitencia en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="d27c8-129">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![Captura de pantalla de panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="d27c8-131">Conectarse a una red</span><span class="sxs-lookup"><span data-stu-id="d27c8-131">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="d27c8-132">Conexión con cable</span><span class="sxs-lookup"><span data-stu-id="d27c8-132">Wired connection</span></span>
<span data-ttu-id="d27c8-133">Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="d27c8-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="d27c8-134">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="d27c8-134">Wireless connection</span></span>
<span data-ttu-id="d27c8-135">Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:</span><span class="sxs-lookup"><span data-stu-id="d27c8-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="d27c8-136">Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="d27c8-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="d27c8-137">En la página de configuración, seleccione _red y Wi-Fi_.</span><span class="sxs-lookup"><span data-stu-id="d27c8-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="d27c8-138">El dispositivo realizará un examen para redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="d27c8-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="d27c8-139">Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.</span><span class="sxs-lookup"><span data-stu-id="d27c8-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="d27c8-140">Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:</span><span class="sxs-lookup"><span data-stu-id="d27c8-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="d27c8-141">Vaya al panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="d27c8-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="d27c8-142">Encuentre la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="d27c8-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="d27c8-143">Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="d27c8-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="d27c8-144">Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.</span><span class="sxs-lookup"><span data-stu-id="d27c8-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="d27c8-145">Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="d27c8-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="d27c8-146">La placa de esto conectará a la red.</span><span class="sxs-lookup"><span data-stu-id="d27c8-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="d27c8-147">Wi-Fi en el equipo debe estar activada para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="d27c8-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="d27c8-148">Conectarse a Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="d27c8-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="d27c8-149">Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="d27c8-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="d27c8-150">El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d27c8-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 
