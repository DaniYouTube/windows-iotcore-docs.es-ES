---
title: Instalación de controladores periféricos USB
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo crear un paquete de controladores e instalar controladores de terceros en los dispositivos.
keywords: Windows IOT, controladores USB, dispositivos periféricos, USB
ms.openlocfilehash: 4e3b77466e2bacb9bf8e06bc3a0dc081db2ee5f9
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721480"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="ace92-104">Instalación de controladores periféricos de USB</span><span class="sxs-lookup"><span data-stu-id="ace92-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="ace92-105">Siga los pasos que se indican a continuación para agregar controladores de terceros (USB) para dispositivos periféricos, como módems de banda ancha móvil USB, impresoras, escáneres, etc.</span><span class="sxs-lookup"><span data-stu-id="ace92-105">Follow the steps below to add third-party drivers (usb) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span> 

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="ace92-106">Paso 1: obtener controladores del equipo</span><span class="sxs-lookup"><span data-stu-id="ace92-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="ace92-107">El paso es obtener la versión x86 de los controladores del equipo.</span><span class="sxs-lookup"><span data-stu-id="ace92-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="ace92-108">Para ARM, póngase en contacto con el proveedor del periférico para obtener los archivos sys/INF.</span><span class="sxs-lookup"><span data-stu-id="ace92-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="ace92-109">Conectar el dispositivo al equipo Windows</span><span class="sxs-lookup"><span data-stu-id="ace92-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="ace92-110">Instalar el controlador del dispositivo en el equipo</span><span class="sxs-lookup"><span data-stu-id="ace92-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="ace92-111">Vaya a Device Manager, seleccione este dispositivo (que aparece en controladoras de bus serie universal), haga clic con el botón derecho y seleccione Propiedades.</span><span class="sxs-lookup"><span data-stu-id="ace92-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="ace92-112">Vaya a la pestaña controlador en el ventana Propiedades y haga clic en detalles del controlador.</span><span class="sxs-lookup"><span data-stu-id="ace92-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="ace92-113">Tenga en cuenta los archivos sys que aparecen en la lista.</span><span class="sxs-lookup"><span data-stu-id="ace92-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="ace92-114">Copie los archivos sys de `C:\Windows\system32` y también el archivo INF relacionado de `C:\Windows\Inf`.</span><span class="sxs-lookup"><span data-stu-id="ace92-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="ace92-115">Puede encontrar el archivo INF searcing para la referencia de archivo sys en los archivos de `.inf`.</span><span class="sxs-lookup"><span data-stu-id="ace92-115">You can find the inf file by searcing for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="ace92-116">Es posible que necesite copiar los archivos adicionales que se enumeran en el archivo INF y que se mostrarán en el archivo inf_filelist. txt creado al usar `inf2pkg.cmd` en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="ace92-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="ace92-117">Paso 2: crear un paquete de controladores</span><span class="sxs-lookup"><span data-stu-id="ace92-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="ace92-118">El paquete de controladores contiene las referencias (InfSource) del archivo INF para el controlador y también enumera todos los archivos a los que se hace referencia en el archivo INF.</span><span class="sxs-lookup"><span data-stu-id="ace92-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="ace92-119">Puede crear el archivo driver. WM. XML mediante [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span><span class="sxs-lookup"><span data-stu-id="ace92-119">You can author the driver .wm.xml using [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="ace92-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) crea el archivo XML del paquete y también genera el archivo CAB directamente.</span><span class="sxs-lookup"><span data-stu-id="ace92-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="ace92-121">Windows IoT Core solo admite [los controladores universal y universal INF](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span><span class="sxs-lookup"><span data-stu-id="ace92-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="ace92-122">Vea también: [paquete de controladores de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="ace92-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span> 

## <a name="step-3-install-on-device"></a><span data-ttu-id="ace92-123">Paso 3: instalar en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="ace92-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="ace92-124">Conexión al dispositivo ([mediante SSH](../connect-your-device/ssh.md) o [con PowerShell](../connect-your-device/powershell.md))</span><span class="sxs-lookup"><span data-stu-id="ace92-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using Powershell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="ace92-125">Copie el archivo <filename>. cab en el dispositivo a un directorio, por ejemplo, C:\OemInstall</span><span class="sxs-lookup"><span data-stu-id="ace92-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="ace92-126">Inicie el almacenamiento provisional del paquete mediante `applyupdate -stage C:\OemInstall\<filename>.cab`.</span><span class="sxs-lookup"><span data-stu-id="ace92-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="ace92-127">Tenga en cuenta que este paso se repite para cada paquete, cuando tiene varios paquetes para instalar.</span><span class="sxs-lookup"><span data-stu-id="ace92-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="ace92-128">Confirme los paquetes mediante `applyupdate -commit`.</span><span class="sxs-lookup"><span data-stu-id="ace92-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="ace92-129">El dispositivo se reiniciará en el sistema operativo de actualización (que muestra los engranajes) para instalar los paquetes y se reiniciará de nuevo en el sistema operativo principal.</span><span class="sxs-lookup"><span data-stu-id="ace92-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="ace92-130">Este proceso puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="ace92-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="ace92-131">Paso 4: comprobar el estado del controlador</span><span class="sxs-lookup"><span data-stu-id="ace92-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="ace92-132">Inicio de [PowerShell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="ace92-132">Launch the [Powershell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="ace92-133">Puede obtener el estado de los controladores instalados con el siguiente commandlets de PowerShell</span><span class="sxs-lookup"><span data-stu-id="ace92-133">You can get the status of the installed drivers using the following Powershell commandlets</span></span>

    * [<span data-ttu-id="ace92-134">Get-PnpDevice</span><span class="sxs-lookup"><span data-stu-id="ace92-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [<span data-ttu-id="ace92-135">Get-PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="ace92-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
