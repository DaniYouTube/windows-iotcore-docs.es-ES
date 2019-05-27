---
title: Cómo configurar un dispositivo NXP
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo NXP con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, NXP
ms.custom: RS5
ms.openlocfilehash: 58bed6c49a5a05afe0852572051132f8731dfcb1
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182177"
---
# <a name="setting-up-a-nxp-device"></a><span data-ttu-id="83e4b-104">Cómo configurar un dispositivo NXP</span><span class="sxs-lookup"><span data-stu-id="83e4b-104">Setting up a NXP device</span></span>

## <a name="overview"></a><span data-ttu-id="83e4b-105">Información general</span><span class="sxs-lookup"><span data-stu-id="83e4b-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83e4b-106">Cuando el "dar formato al disco" pop hasta, hacer _no_ formatear el disco.</span><span class="sxs-lookup"><span data-stu-id="83e4b-106">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="83e4b-107">Estamos trabajando en una solución para este problema.</span><span class="sxs-lookup"><span data-stu-id="83e4b-107">We are working on a fix for this issue.</span></span>

<span data-ttu-id="83e4b-108">Al configurar un dispositivo NXP para crear prototipos, se recomienda usar el panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="83e4b-108">When setting up a NXP device for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="83e4b-109">Sin embargo, si busca para fabricar con un dispositivo NXP, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="83e4b-109">However, if you're looking to manufacture with a NXP device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="83e4b-110">No puede usar imágenes de creador de fabricación.</span><span class="sxs-lookup"><span data-stu-id="83e4b-110">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="83e4b-111">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="83e4b-111">Using the Dashboard</span></span>

<span data-ttu-id="83e4b-112">Para flash o descargar IoT Core en su dispositivo NXP, necesitará:</span><span class="sxs-lookup"><span data-stu-id="83e4b-112">To flash, or download, IoT Core onto your NXP device, you'll need:</span></span>
* <span data-ttu-id="83e4b-113">Un equipo que ejecuta Windows 10</span><span class="sxs-lookup"><span data-stu-id="83e4b-113">A computer running Windows 10</span></span> 
* [<span data-ttu-id="83e4b-114">Panel de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="83e4b-114">Windows 10 IoT Core Dashboard</span></span>](https://docs.microsoft.com/windows/iot-core/downloads)
* <span data-ttu-id="83e4b-115">Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk</span><span class="sxs-lookup"><span data-stu-id="83e4b-115">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="83e4b-116">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="83e4b-116">An external display</span></span>
* <span data-ttu-id="83e4b-117">Cualquier otro periférico (por ejemplo, mouse, teclado, etcetera.)</span><span class="sxs-lookup"><span data-stu-id="83e4b-117">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="83e4b-118">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="83e4b-118">Instructions</span></span>

1. <span data-ttu-id="83e4b-119">Ejecutar el panel de Windows 10 IOT Core y haga clic en *configurar un nuevo dispositivo* e inserte una tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="83e4b-119">Run the Windows 10 IOT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="83e4b-120">Conecte el dispositivo NXP a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="83e4b-120">Hook up your NXP device to an external display.</span></span>
3. <span data-ttu-id="83e4b-121">Rellene los campos.</span><span class="sxs-lookup"><span data-stu-id="83e4b-121">Fill out the fields.</span></span> <span data-ttu-id="83e4b-122">Seleccione "NXP [i.MX6/i.MX7]" como el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="83e4b-122">Select "NXP [i.MX6/i.MX7]" as the device type.</span></span> <span data-ttu-id="83e4b-123">Asegúrese de dar a su dispositivo un nuevo nombre y una contraseña.</span><span class="sxs-lookup"><span data-stu-id="83e4b-123">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="83e4b-124">En caso contrario, las credenciales predeterminadas permanecerá como:</span><span class="sxs-lookup"><span data-stu-id="83e4b-124">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="83e4b-125">Cargue el archivo de imagen descargada previamente mediante la función "Examinar".</span><span class="sxs-lookup"><span data-stu-id="83e4b-125">Upload your pre-downloaded image file using the "Browse" function.</span></span> <span data-ttu-id="83e4b-126">Para obtener más información, consulte nuestra [documentación NXP](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp).</span><span class="sxs-lookup"><span data-stu-id="83e4b-126">For more information, see our [NXP documentation](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp).</span></span>
5. <span data-ttu-id="83e4b-127">Acepte los términos de licencia de software y haga clic en *descargue e instale*.</span><span class="sxs-lookup"><span data-stu-id="83e4b-127">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="83e4b-128">Si todo va bien, verá que ahora es Windows 10 IoT Core intermitencia en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="83e4b-128">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![Captura de pantalla de panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)


## <a name="connect-to-a-network"></a><span data-ttu-id="83e4b-130">Conectarse a una red</span><span class="sxs-lookup"><span data-stu-id="83e4b-130">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="83e4b-131">Conexión con cable</span><span class="sxs-lookup"><span data-stu-id="83e4b-131">Wired connection</span></span>
<span data-ttu-id="83e4b-132">Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="83e4b-132">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="83e4b-133">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="83e4b-133">Wireless connection</span></span>
<span data-ttu-id="83e4b-134">Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:</span><span class="sxs-lookup"><span data-stu-id="83e4b-134">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="83e4b-135">Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="83e4b-135">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="83e4b-136">En la página de configuración, seleccione _red y Wi-Fi_.</span><span class="sxs-lookup"><span data-stu-id="83e4b-136">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="83e4b-137">El dispositivo realizará un examen para redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="83e4b-137">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="83e4b-138">Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.</span><span class="sxs-lookup"><span data-stu-id="83e4b-138">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="83e4b-139">Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:</span><span class="sxs-lookup"><span data-stu-id="83e4b-139">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="83e4b-140">Vaya al panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="83e4b-140">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="83e4b-141">Encuentre la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="83e4b-141">Find your unconfigured board from the list.</span></span> <span data-ttu-id="83e4b-142">Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="83e4b-142">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="83e4b-143">Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.</span><span class="sxs-lookup"><span data-stu-id="83e4b-143">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="83e4b-144">Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="83e4b-144">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="83e4b-145">La placa de esto conectará a la red.</span><span class="sxs-lookup"><span data-stu-id="83e4b-145">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="83e4b-146">Wi-Fi en el equipo debe estar activada para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="83e4b-146">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="83e4b-147">Conectarse a Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="83e4b-147">Connect to Windows Device Portal</span></span>

<span data-ttu-id="83e4b-148">Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="83e4b-148">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="83e4b-149">El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="83e4b-149">The device portal makes valuable configuration and device management capabilities available.</span></span> 

