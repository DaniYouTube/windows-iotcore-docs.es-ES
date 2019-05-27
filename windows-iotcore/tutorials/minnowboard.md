---
title: Configurar un Minnowboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar su Minnowboard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Minnowboard
ms.custom: RS5
ms.openlocfilehash: a8840272e0933ee4255661605a04441d542887f3
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182217"
---
# <a name="setting-up-a-minnowboard"></a><span data-ttu-id="192a9-104">Configurar un MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="192a9-104">Setting up a MinnowBoard</span></span>

## <a name="overview"></a><span data-ttu-id="192a9-105">Información general</span><span class="sxs-lookup"><span data-stu-id="192a9-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="192a9-106">El firmware más reciente de 64 bits para MinnowBoard Turbot puede encontrarse en el [sitio Web de MinnowBoard](https://minnowboard.org/tutorials/updating-the-firmware) (omita el paso 4 en las instrucciones de la carpeta del sitio MinnowBoard).</span><span class="sxs-lookup"><span data-stu-id="192a9-106">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="192a9-107">Cuando el "dar formato al disco" pop hasta, hacer _no_ formatear el disco.</span><span class="sxs-lookup"><span data-stu-id="192a9-107">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="192a9-108">Estamos trabajando en una solución para este problema.</span><span class="sxs-lookup"><span data-stu-id="192a9-108">We are working on a fix for this issue.</span></span>

<span data-ttu-id="192a9-109">Al configurar un MinnowBoard para crear prototipos, se recomienda usar el panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="192a9-109">When setting up a MinnowBoard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="192a9-110">Sin embargo, si busca para fabricar con un MinnowBoard, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="192a9-110">However, if you're looking to manufacture with a MinnowBoard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="192a9-111">No puede usar imágenes de creador de fabricación.</span><span class="sxs-lookup"><span data-stu-id="192a9-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="192a9-112">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="192a9-112">Using the Dashboard</span></span>

<span data-ttu-id="192a9-113">Para flash o descargar IoT Core en su MinnowBoard, necesitará:</span><span class="sxs-lookup"><span data-stu-id="192a9-113">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="192a9-114">Un equipo que ejecuta Windows 10</span><span class="sxs-lookup"><span data-stu-id="192a9-114">A computer running Windows 10</span></span> 
* [<span data-ttu-id="192a9-115">Panel de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="192a9-115">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="192a9-116">Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk</span><span class="sxs-lookup"><span data-stu-id="192a9-116">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="192a9-117">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="192a9-117">An external display</span></span>
* <span data-ttu-id="192a9-118">Cualquier otro periférico (por ejemplo, mouse, teclado, etcetera.)</span><span class="sxs-lookup"><span data-stu-id="192a9-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="192a9-119">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="192a9-119">Instructions</span></span>

1. <span data-ttu-id="192a9-120">Ejecutar el panel de Windows 10 IoT Core y haga clic en *configurar un nuevo dispositivo* e inserte una tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="192a9-120">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="192a9-121">Conecte su MinnowBoard a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="192a9-121">Hook up your MinnowBoard to an external display.</span></span>
3. <span data-ttu-id="192a9-122">Rellene los campos.</span><span class="sxs-lookup"><span data-stu-id="192a9-122">Fill out the fields.</span></span> <span data-ttu-id="192a9-123">Seleccione "Intel [MinnowBoard Turbox/máx. (x64)]" como el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="192a9-123">Select "Intel [MinnowBoard Turbox/MAX (x64)]" as the device type.</span></span> <span data-ttu-id="192a9-124">Asegúrese de dar a su dispositivo un nuevo nombre y una contraseña.</span><span class="sxs-lookup"><span data-stu-id="192a9-124">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="192a9-125">En caso contrario, las credenciales predeterminadas permanecerá como:</span><span class="sxs-lookup"><span data-stu-id="192a9-125">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="192a9-126">Acepte los términos de licencia de software y haga clic en *descargue e instale*.</span><span class="sxs-lookup"><span data-stu-id="192a9-126">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="192a9-127">Si todo va bien, verá que ahora es Windows 10 IoT Core intermitencia en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="192a9-127">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![Captura de pantalla de panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="192a9-129">Conectarse a una red</span><span class="sxs-lookup"><span data-stu-id="192a9-129">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="192a9-130">Conexión con cable</span><span class="sxs-lookup"><span data-stu-id="192a9-130">Wired connection</span></span>
<span data-ttu-id="192a9-131">Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="192a9-131">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="192a9-132">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="192a9-132">Wireless connection</span></span>
<span data-ttu-id="192a9-133">Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:</span><span class="sxs-lookup"><span data-stu-id="192a9-133">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="192a9-134">Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="192a9-134">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="192a9-135">En la página de configuración, seleccione _red y Wi-Fi_.</span><span class="sxs-lookup"><span data-stu-id="192a9-135">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="192a9-136">El dispositivo realizará un examen para redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="192a9-136">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="192a9-137">Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.</span><span class="sxs-lookup"><span data-stu-id="192a9-137">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="192a9-138">Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:</span><span class="sxs-lookup"><span data-stu-id="192a9-138">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="192a9-139">Vaya al panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="192a9-139">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="192a9-140">Encuentre la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="192a9-140">Find your unconfigured board from the list.</span></span> <span data-ttu-id="192a9-141">Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="192a9-141">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="192a9-142">Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.</span><span class="sxs-lookup"><span data-stu-id="192a9-142">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="192a9-143">Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="192a9-143">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="192a9-144">La placa de esto conectará a la red.</span><span class="sxs-lookup"><span data-stu-id="192a9-144">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="192a9-145">Wi-Fi en el equipo debe estar activada para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="192a9-145">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="192a9-146">Conectarse a Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="192a9-146">Connect to Windows Device Portal</span></span>

<span data-ttu-id="192a9-147">Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="192a9-147">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="192a9-148">El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="192a9-148">The device portal makes valuable configuration and device management capabilities available.</span></span> 
