---
title: Configuración de un dispositivo MinnowBoard
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo MinnowBoard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, MinnowBoard
ms.custom: RS5
ms.openlocfilehash: abbc6548a9219b967ea379e238ed6a898830e798
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "75721920"
---
# <a name="setting-up-a-minnowboard"></a><span data-ttu-id="fbd2e-104">Configuración de un dispositivo MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="fbd2e-104">Setting up a MinnowBoard</span></span>

## <a name="overview"></a><span data-ttu-id="fbd2e-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="fbd2e-105">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbd2e-106">El firmware de 64 bits más reciente para MinnowBoard Turbot se puede encontrar en el [sitio web de MinnowBoard](https://minnowboard.org/tutorials/updating-the-firmware) (omita el paso 4 en las instrucciones del sitio de MinnowBoard).</span><span class="sxs-lookup"><span data-stu-id="fbd2e-106">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fbd2e-107">Cuando aparezca el mensaje emergente "formatear el disco", _no_ lo formatee.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-107">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="fbd2e-108">Estamos trabajando en una solución para este problema.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-108">We are working on a fix for this issue.</span></span>

<span data-ttu-id="fbd2e-109">Al configurar un dispositivo MinnowBoard para crear prototipos, se recomienda usar el Panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-109">When setting up a MinnowBoard for prototyping, we recommend using the Windows 10 IoT Core Dashboard.</span></span> <span data-ttu-id="fbd2e-110">Si lo que quiere es fabricar con un dispositivo MinnowBoard, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="fbd2e-110">However, if you're looking to manufacture with a MinnowBoard, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="fbd2e-111">No se pueden usar imágenes del creador para la fabricación.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-111">You cannot use maker images for manufacturing.</span></span>
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a><span data-ttu-id="fbd2e-112">Uso del panel</span><span class="sxs-lookup"><span data-stu-id="fbd2e-112">Using the Dashboard</span></span>

<span data-ttu-id="fbd2e-113">Para instalar una imagen de IoT Core o descargarlo en el dispositivo MinnowBoard, necesitará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="fbd2e-113">To flash, or download, IoT Core onto your MinnowBoard, you'll need:</span></span>
* <span data-ttu-id="fbd2e-114">Un equipo que ejecute Windows 10</span><span class="sxs-lookup"><span data-stu-id="fbd2e-114">A computer running Windows 10</span></span> 
* <span data-ttu-id="fbd2e-115">El [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)</span><span class="sxs-lookup"><span data-stu-id="fbd2e-115">[Windows 10 IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/downloads)</span></span>
* <span data-ttu-id="fbd2e-116">Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk</span><span class="sxs-lookup"><span data-stu-id="fbd2e-116">A high-performance SD card, such as a SanDisk SD card</span></span>
* <span data-ttu-id="fbd2e-117">Una pantalla externa</span><span class="sxs-lookup"><span data-stu-id="fbd2e-117">An external display</span></span>
* <span data-ttu-id="fbd2e-118">Otros periféricos (por ejemplo, mouse, teclado, etc.)</span><span class="sxs-lookup"><span data-stu-id="fbd2e-118">Any other peripherals (e.g. mouse, keyboard, etc.)</span></span>

### <a name="instructions"></a><span data-ttu-id="fbd2e-119">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="fbd2e-119">Instructions</span></span>

1. <span data-ttu-id="fbd2e-120">Ejecute el Panel de Windows 10 IoT Core, haga clic en *Set up a new device* (Configurar un nuevo dispositivo) e inserte una tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-120">Run the Windows 10 IoT Core Dashboard and click on *Set up a new device* and insert a SD card into your computer.</span></span>
2. <span data-ttu-id="fbd2e-121">Conecte el dispositivo MinnowBoard a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-121">Hook up your MinnowBoard to an external display.</span></span>
3. <span data-ttu-id="fbd2e-122">Rellene los campos.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-122">Fill out the fields.</span></span> <span data-ttu-id="fbd2e-123">Seleccione "Intel [MinnowBoard Turbox/MAX (x64)]" como el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-123">Select "Intel [MinnowBoard Turbox/MAX (x64)]" as the device type.</span></span> <span data-ttu-id="fbd2e-124">Asegúrese de asignar un nombre y una contraseña nuevos al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-124">Make sure to give your device a new name and password.</span></span> <span data-ttu-id="fbd2e-125">En caso contrario, las credenciales predeterminadas permanecerán como:</span><span class="sxs-lookup"><span data-stu-id="fbd2e-125">Otherwise the default credentials will remain as:</span></span>

```
Device: minwinpc
Password: p@ssw0rd
```

4. <span data-ttu-id="fbd2e-126">Acepte los términos de licencia de software y haga clic en *Descargar e instalar*.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-126">Accept the software license terms and click *Download and Install*.</span></span> <span data-ttu-id="fbd2e-127">Si todo es correcto, verá que Windows 10 IoT Core instala una imagen en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-127">If all goes well, you'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>

![Captura de pantalla del panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)

## <a name="connect-to-a-network"></a><span data-ttu-id="fbd2e-129">Conexión a una red</span><span class="sxs-lookup"><span data-stu-id="fbd2e-129">Connect to a network</span></span>
### <a name="wired-connection"></a><span data-ttu-id="fbd2e-130">Conexión por cable</span><span class="sxs-lookup"><span data-stu-id="fbd2e-130">Wired connection</span></span>
<span data-ttu-id="fbd2e-131">Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-131">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="fbd2e-132">Conexión inalámbrica</span><span class="sxs-lookup"><span data-stu-id="fbd2e-132">Wireless connection</span></span>
<span data-ttu-id="fbd2e-133">Si el dispositivo admite la conectividad Wi-Fi y le ha conectado una pantalla, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="fbd2e-133">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="fbd2e-134">Vaya a la aplicación predeterminada y haga clic en el botón de configuración situado junto al reloj.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-134">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="fbd2e-135">En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).</span><span class="sxs-lookup"><span data-stu-id="fbd2e-135">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="fbd2e-136">El dispositivo realizará una exploración de redes inalámbricas.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-136">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="fbd2e-137">Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-137">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="fbd2e-138">Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="fbd2e-138">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="fbd2e-139">Vaya al Panel de IoT y haga clic en _Mis dispositivos_.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-139">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="fbd2e-140">Busque la placa no configurada en la lista.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-140">Find your unconfigured board from the list.</span></span> <span data-ttu-id="fbd2e-141">El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68).</span><span class="sxs-lookup"><span data-stu-id="fbd2e-141">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="fbd2e-142">Si la placa no aparece después de unos minutos, intente reiniciarla.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-142">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="fbd2e-143">Haga clic en _Configurar dispositivo_ y escriba las credenciales de red.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-143">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="fbd2e-144">Esto conectará la placa a la red.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-144">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="fbd2e-145">En el equipo la Wi-Fi debe estar activada para poder buscar otras redes.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-145">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="fbd2e-146">Conexión al Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="fbd2e-146">Connect to Windows Device Portal</span></span>

<span data-ttu-id="fbd2e-147">Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-147">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="fbd2e-148">El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles.</span><span class="sxs-lookup"><span data-stu-id="fbd2e-148">The device portal makes valuable configuration and device management capabilities available.</span></span> 
