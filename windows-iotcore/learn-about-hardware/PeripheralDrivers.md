---
title: Instalar a controladores periféricos de USB
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear un paquete de controladores e instalar a controladores de terceros en los dispositivos.
keywords: Windows iot, los controladores USB, los dispositivos periféricos USB
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514892"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="0c3a3-104">Instalar a controladores periféricos de USB</span><span class="sxs-lookup"><span data-stu-id="0c3a3-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="0c3a3-105">Siga estos pasos para agregar controladores de terceros (usb) para dispositivos periféricos, como los módems de banda ancha móvil USB, impresoras, escáneres, etcetera.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-105">Follow the steps below to add third-party drivers (usb) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span> 

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="0c3a3-106">Paso 1: Obtener los controladores de PC</span><span class="sxs-lookup"><span data-stu-id="0c3a3-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="0c3a3-107">El paso es obtener la x86 versión de los controladores de PC.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="0c3a3-108">ARM, póngase en contacto con el proveedor de los dispositivos periféricos para obtener los archivos inf/sys.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="0c3a3-109">Conecte el dispositivo en el equipo de windows</span><span class="sxs-lookup"><span data-stu-id="0c3a3-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="0c3a3-110">Instalar al controlador para el dispositivo en el equipo</span><span class="sxs-lookup"><span data-stu-id="0c3a3-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="0c3a3-111">Vaya al administrador de dispositivos, seleccione este dispositivo (se muestran en los controladores de Bus serie Universal) y haga clic y seleccione Propiedades.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="0c3a3-112">Vaya a la ficha controlador en la ventana Propiedades y haga clic en detalles del controlador.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="0c3a3-113">Tenga en cuenta los archivos sys en la lista.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="0c3a3-114">Copie los archivos sys de `C:\Windows\system32` y también el archivo inf relacionado desde `C:\Windows\Inf`.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="0c3a3-115">Puede encontrar el archivo inf por searcing para el sys de referencia del archivo en el `.inf` archivos.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-115">You can find the inf file by searcing for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="0c3a3-116">Es posible que deba copiar archivos adicionales que aparecen en el archivo Inf y se enumerarán en el archivo inf_filelist.txt creado al usar `inf2pkg.cmd` en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="0c3a3-117">Paso 2: Crear un paquete de controladores</span><span class="sxs-lookup"><span data-stu-id="0c3a3-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="0c3a3-118">El paquete de controladores contiene las referencias (InfSource) en el archivo Inf del controlador y también enumera todos los archivos que se hace referenciados en el archivo Inf.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="0c3a3-119">Puede crear el controlador. utilizando wm.xml [New IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span><span class="sxs-lookup"><span data-stu-id="0c3a3-119">You can author the driver .wm.xml using [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="0c3a3-120">[Nuevo IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) crea el archivo xml del paquete y también se basa directamente el archivo cab.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="0c3a3-121">Solo admite Windows IoT Core [INF Universal y controladores Universal](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span><span class="sxs-lookup"><span data-stu-id="0c3a3-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="0c3a3-122">Consulte también: [Paquete de controladores de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="0c3a3-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span> 

## <a name="step-3-install-on-device"></a><span data-ttu-id="0c3a3-123">Paso 3: Instalar en dispositivos</span><span class="sxs-lookup"><span data-stu-id="0c3a3-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="0c3a3-124">Conectarse al dispositivo ([mediante SSH](../connect-your-device/ssh.md) o [mediante Powershell](../connect-your-device/powershell.md))</span><span class="sxs-lookup"><span data-stu-id="0c3a3-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using Powershell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="0c3a3-125">Copia el <filename>archivo .cab en el dispositivo en un directorio, por ejemplo C:\OemInstall</span><span class="sxs-lookup"><span data-stu-id="0c3a3-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="0c3a3-126">Iniciar el almacenamiento provisional del paquete con `applyupdate -stage C:\OemInstall\<filename>.cab`.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="0c3a3-127">Tenga en cuenta que este paso es repetirse para cada paquete, cuando haya varios paquetes para instalar.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="0c3a3-128">Confirmar los paquetes mediante `applyupdate -commit`.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="0c3a3-129">El dispositivo se reiniciará en la actualización del sistema operativo (mostrando gears) para instalar los paquetes y se reiniciará al sistema operativo principal.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="0c3a3-130">Este proceso puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="0c3a3-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="0c3a3-131">Paso 4: Compruebe el estado del controlador</span><span class="sxs-lookup"><span data-stu-id="0c3a3-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="0c3a3-132">Iniciar el [Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="0c3a3-132">Launch the [Powershell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="0c3a3-133">Puede obtener el estado de los controladores instalados mediante los siguientes cmdlets de Powershell</span><span class="sxs-lookup"><span data-stu-id="0c3a3-133">You can get the status of the installed drivers using the following Powershell commandlets</span></span>

    * [<span data-ttu-id="0c3a3-134">Get-PnpDevice</span><span class="sxs-lookup"><span data-stu-id="0c3a3-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [<span data-ttu-id="0c3a3-135">Get-PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="0c3a3-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
