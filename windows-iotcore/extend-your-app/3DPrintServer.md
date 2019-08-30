---
title: Impresora de red 3D con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: Obtenga información sobre cómo convertir el dispositivo de Windows 10 IoT Core en un servidor de impresión y conectar su impresora 3D a él.
keywords: Windows IOT, 3D, impresora 3D, servidor de impresión, impresora 3D de red
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170492"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a><span data-ttu-id="c34c1-104">Impresora de red 3D con Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="c34c1-104">Network 3D Printer with Windows 10 IoT Core</span></span>

<span data-ttu-id="c34c1-105">Convierta el dispositivo de Windows 10 IoT Core en un servidor de impresión y conecte la impresora 3D a él.</span><span class="sxs-lookup"><span data-stu-id="c34c1-105">Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.</span></span> <span data-ttu-id="c34c1-106">Podrá acceder a la impresora de forma inalámbrica desde otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c34c1-106">You will be able to access your printer wirelessly from other devices.</span></span>

## <a name="1-install-windows-10-iot-core-on-your-device"></a><span data-ttu-id="c34c1-107">1. Instalación de Windows 10 IoT Core en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="c34c1-107">1. Install Windows 10 IoT Core on your device</span></span>
___
<span data-ttu-id="c34c1-108">Antes de empezar, necesitará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c34c1-108">Before you start, you will need:</span></span>

* <span data-ttu-id="c34c1-109">Un panel con la versión más reciente de Windows 10 IoT Core Insider instalada.</span><span class="sxs-lookup"><span data-stu-id="c34c1-109">A board with the latest version of Windows 10 IoT Core Insider Preview installed.</span></span> <span data-ttu-id="c34c1-110">Siga la [Guía de introducción](https://developer.microsoft.com/en-us/windows/iot/getstarted) para obtener la aplicación de panel de IOT e instalar Windows 10 IOT Core.</span><span class="sxs-lookup"><span data-stu-id="c34c1-110">Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.</span></span>
* <span data-ttu-id="c34c1-111">Una impresora 3D compatible con nuestra aplicación de impresora 3D de red:</span><span class="sxs-lookup"><span data-stu-id="c34c1-111">A 3D Printer compatible with our Network 3D Printer app:</span></span>

    * <span data-ttu-id="c34c1-112">Lulzbot taz 6</span><span class="sxs-lookup"><span data-stu-id="c34c1-112">Lulzbot Taz 6</span></span>
    * <span data-ttu-id="c34c1-113">Makergear m2</span><span class="sxs-lookup"><span data-stu-id="c34c1-113">Makergear M2</span></span>
    * <span data-ttu-id="c34c1-114">Printrbot Play, Plus y simple</span><span class="sxs-lookup"><span data-stu-id="c34c1-114">Printrbot Play, Plus and Simple</span></span>
    * <span data-ttu-id="c34c1-115">Prusa i3 MK2</span><span class="sxs-lookup"><span data-stu-id="c34c1-115">Prusa i3 Mk2</span></span>
    * <span data-ttu-id="c34c1-116">Ultimaker original y original +</span><span class="sxs-lookup"><span data-stu-id="c34c1-116">Ultimaker Original and Original+</span></span>
    * <span data-ttu-id="c34c1-117">Ultimaker 2 y 2 +</span><span class="sxs-lookup"><span data-stu-id="c34c1-117">Ultimaker 2 and 2+</span></span>
    * <span data-ttu-id="c34c1-118">Extendido y extendido de Ultimaker 2</span><span class="sxs-lookup"><span data-stu-id="c34c1-118">Ultimaker 2 Extended and Extended+</span></span>
    * <span data-ttu-id="c34c1-119">CraftBot 2</span><span class="sxs-lookup"><span data-stu-id="c34c1-119">CraftBot 2</span></span>
    * <span data-ttu-id="c34c1-120">CraftBot PLUS</span><span class="sxs-lookup"><span data-stu-id="c34c1-120">CraftBot PLUS</span></span>
    * <span data-ttu-id="c34c1-121">LulzBot</span><span class="sxs-lookup"><span data-stu-id="c34c1-121">LulzBot Mini</span></span>
    * <span data-ttu-id="c34c1-122">Velleman K8200</span><span class="sxs-lookup"><span data-stu-id="c34c1-122">Velleman K8200</span></span>

## <a name="2-connect-your-3d-printer-to-your-device"></a><span data-ttu-id="c34c1-123">2. Conectar la impresora 3D al dispositivo</span><span class="sxs-lookup"><span data-stu-id="c34c1-123">2. Connect your 3D Printer to your device</span></span>
___
* <span data-ttu-id="c34c1-124">Conecte la impresora 3D a la placa de Windows 10 IoT Core con el cable USB.</span><span class="sxs-lookup"><span data-stu-id="c34c1-124">Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.</span></span>

    ![Conectar la impresora 3D al dispositivo](../media/3DPrintServer/connect-3d-printer.png)

* <span data-ttu-id="c34c1-126">Abra la aplicación de panel de IoT y compruebe que el dispositivo aparece en la pestaña **mis dispositivos** .</span><span class="sxs-lookup"><span data-stu-id="c34c1-126">Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.</span></span>

    ![Comprobar que el dispositivo aparece en el panel de IoT](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a><span data-ttu-id="c34c1-128">3. Implementar la aplicación de impresora 3D de red</span><span class="sxs-lookup"><span data-stu-id="c34c1-128">3. Deploy the Network 3D Printer app</span></span>
___
* <span data-ttu-id="c34c1-129">En el panel de IoT, haga clic en la sección **probar algunos ejemplos** .</span><span class="sxs-lookup"><span data-stu-id="c34c1-129">In IoT Dashboard, click on the **Try some samples** section.</span></span>
* <span data-ttu-id="c34c1-130">Seleccione la aplicación de ejemplo de impresora Network 3D.</span><span class="sxs-lookup"><span data-stu-id="c34c1-130">Select the Network 3D Printer sample app.</span></span>

   ![Instalar impresora de red 3D](../media/3dprintserver/dashboard-samples.png)

* <span data-ttu-id="c34c1-132">Seleccione el modelo de impresora 3D y presione el botón **implementar y ejecutar** para implementar la aplicación en el dispositivo de IOT Core.</span><span class="sxs-lookup"><span data-stu-id="c34c1-132">Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.</span></span> 

    ![Instalar impresora de red 3D](../media/3dprintserver/dashboard-app.png)

    <span data-ttu-id="c34c1-134">[LULZBOT taz 6 Image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) tiene una licencia de [CC por-SA 4,0](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="c34c1-134">[LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>
    
    <span data-ttu-id="c34c1-135">Si desea instalar una impresora personalizada, seleccione la opción "personalizado" en la lista de impresoras.</span><span class="sxs-lookup"><span data-stu-id="c34c1-135">If you wish to install a custom printer select the "Custom" option from the list of Printers.</span></span> <span data-ttu-id="c34c1-136">Las impresoras 3D personalizadas necesitan un XML de configuración denominado archivo PrintDeviceCapabilities. XML que se va a proporcionar para conectarse e imprimir correctamente en la impresora 3D.</span><span class="sxs-lookup"><span data-stu-id="c34c1-136">Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer.</span></span> <span data-ttu-id="c34c1-137">Aquí puede encontrar un archivo PrintDeviceCapabilities. XML de ejemplo https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span><span class="sxs-lookup"><span data-stu-id="c34c1-137">A sample PrintDeviceCapabilities.xml file can be found here https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span></span>
   
   <span data-ttu-id="c34c1-138">Los cambios mínimos que debe realizar en el archivo XML son actualizar las secciones siguientes con los valores correctos específicos de la impresora compatible.</span><span class="sxs-lookup"><span data-stu-id="c34c1-138">The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.</span></span>

<span data-ttu-id="c34c1-139">Estos valores especifican las dimensiones de la cama de impresión de la impresora 3D en la segmentación al procesar el modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="c34c1-139">These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model</span></span>

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


<span data-ttu-id="c34c1-140">El valor de la etiqueta XML psk3dx: Baudrate controla la velocidad en baudios específica que se va a usar al comunicarse con la impresora 3D desde Raspberry PI3.</span><span class="sxs-lookup"><span data-stu-id="c34c1-140">The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3.</span></span> <span data-ttu-id="c34c1-141">Establezca la velocidad de baudios adecuada específica de la impresora 3D.</span><span class="sxs-lookup"><span data-stu-id="c34c1-141">Set the appropriate baud rate specific to your 3d printer.</span></span> 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

<span data-ttu-id="c34c1-142">Los demás valores en el XML de PrintDeviceCapabilities se usan para notificar a la segmentación de los controladores de impresión 3D para ajustar su funcionamiento con la impresora compatible específica.</span><span class="sxs-lookup"><span data-stu-id="c34c1-142">The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.</span></span>
<span data-ttu-id="c34c1-143">[Aquí](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)se proporciona más información sobre todos estos valores.</span><span class="sxs-lookup"><span data-stu-id="c34c1-143">More information on all these values are provided [here](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span></span>

    
    
## <a name="4-add-your-3d-printer"></a><span data-ttu-id="c34c1-144">4. Agregar la impresora 3D</span><span class="sxs-lookup"><span data-stu-id="c34c1-144">4. Add your 3D Printer</span></span>
___
* <span data-ttu-id="c34c1-145">Vaya a su equipo con Windows 10 y vaya a **configuración** -> **dispositivos** -> **impresoras impresoras & escáneres**.</span><span class="sxs-lookup"><span data-stu-id="c34c1-145">Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.</span></span>
* <span data-ttu-id="c34c1-146">Presione **Agregar una impresora o un escáner**.</span><span class="sxs-lookup"><span data-stu-id="c34c1-146">Press **Add a printer or scanner**.</span></span>

     ![Configuración de Windows Agregar dispositivo](../media/3dprintserver/add-printer.png)

* <span data-ttu-id="c34c1-148">Seleccione la impresora 3D y presione **Agregar dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="c34c1-148">Select your 3D Printer and press **Add device**.</span></span> <span data-ttu-id="c34c1-149">La impresora se instalará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="c34c1-149">The printer will install automatically.</span></span>

     ![Configuración de Windows Agregar dispositivo](../media/3dprintserver/add-device.png)

<span data-ttu-id="c34c1-151">Enhorabuena, la impresora ya está instalada y se comportará exactamente como si estuviera conectada con un cable USB.</span><span class="sxs-lookup"><span data-stu-id="c34c1-151">Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.</span></span>
<span data-ttu-id="c34c1-152">Ahora puede imprimir en él con el [generador 3D](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span><span class="sxs-lookup"><span data-stu-id="c34c1-152">You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span></span>
