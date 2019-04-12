---
title: Impresora de red 3D con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: Obtenga información sobre cómo activar el dispositivo Windows 10 IoT Core en un servidor de impresión y conectarse a la impresora en 3D.
keywords: Windows iot 3D, impresión en 3D, impresión, servidor de impresora de red 3D
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514288"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a><span data-ttu-id="02295-104">Impresora de red 3D con Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="02295-104">Network 3D Printer with Windows 10 IoT Core</span></span>

<span data-ttu-id="02295-105">Activar el dispositivo Windows 10 IoT Core en un servidor de impresión y conectarse a la impresora en 3D.</span><span class="sxs-lookup"><span data-stu-id="02295-105">Turn your Windows 10 IoT Core device into a print server and connect your 3D Printer to it.</span></span> <span data-ttu-id="02295-106">Podrá obtener acceso a la impresora de forma inalámbrica desde otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="02295-106">You will be able to access your printer wirelessly from other devices.</span></span>

## <a name="1-install-windows-10-iot-core-on-your-device"></a><span data-ttu-id="02295-107">1. Instalación de Windows 10 IoT Core en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="02295-107">1. Install Windows 10 IoT Core on your device</span></span>
___
<span data-ttu-id="02295-108">Antes de empezar, necesitará:</span><span class="sxs-lookup"><span data-stu-id="02295-108">Before you start, you will need:</span></span>

* <span data-ttu-id="02295-109">Un panel con la versión más reciente de Windows 10 IoT Core Insider Preview instalado.</span><span class="sxs-lookup"><span data-stu-id="02295-109">A board with the latest version of Windows 10 IoT Core Insider Preview installed.</span></span> <span data-ttu-id="02295-110">Siga el [Guía de introducción](https://developer.microsoft.com/en-us/windows/iot/getstarted) para obtener la aplicación de panel de IoT e instalar Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="02295-110">Follow the [Get Started guide](https://developer.microsoft.com/en-us/windows/iot/getstarted) to get the IoT Dashboard app and install Windows 10 IoT Core.</span></span>
* <span data-ttu-id="02295-111">Una impresora 3D compatible con nuestra aplicación impresora de red 3D:</span><span class="sxs-lookup"><span data-stu-id="02295-111">A 3D Printer compatible with our Network 3D Printer app:</span></span>

    * <span data-ttu-id="02295-112">Lulzbot Taz 6</span><span class="sxs-lookup"><span data-stu-id="02295-112">Lulzbot Taz 6</span></span>
    * <span data-ttu-id="02295-113">Makergear M2</span><span class="sxs-lookup"><span data-stu-id="02295-113">Makergear M2</span></span>
    * <span data-ttu-id="02295-114">Printrbot Play, además y Simple</span><span class="sxs-lookup"><span data-stu-id="02295-114">Printrbot Play, Plus and Simple</span></span>
    * <span data-ttu-id="02295-115">Prusa i3 Mk2</span><span class="sxs-lookup"><span data-stu-id="02295-115">Prusa i3 Mk2</span></span>
    * <span data-ttu-id="02295-116">Ultimaker Original y Original +</span><span class="sxs-lookup"><span data-stu-id="02295-116">Ultimaker Original and Original+</span></span>
    * <span data-ttu-id="02295-117">Ultimaker 2 y 2 +</span><span class="sxs-lookup"><span data-stu-id="02295-117">Ultimaker 2 and 2+</span></span>
    * <span data-ttu-id="02295-118">Ultimaker 2 extendido y extendidos +</span><span class="sxs-lookup"><span data-stu-id="02295-118">Ultimaker 2 Extended and Extended+</span></span>
    * <span data-ttu-id="02295-119">CraftBot 2</span><span class="sxs-lookup"><span data-stu-id="02295-119">CraftBot 2</span></span>
    * <span data-ttu-id="02295-120">CraftBot PLUS</span><span class="sxs-lookup"><span data-stu-id="02295-120">CraftBot PLUS</span></span>
    * <span data-ttu-id="02295-121">LulzBot Mini</span><span class="sxs-lookup"><span data-stu-id="02295-121">LulzBot Mini</span></span>
    * <span data-ttu-id="02295-122">Velleman K8200</span><span class="sxs-lookup"><span data-stu-id="02295-122">Velleman K8200</span></span>

## <a name="2-connect-your-3d-printer-to-your-device"></a><span data-ttu-id="02295-123">2. Conecte la impresora 3D al dispositivo</span><span class="sxs-lookup"><span data-stu-id="02295-123">2. Connect your 3D Printer to your device</span></span>
___
* <span data-ttu-id="02295-124">Complemento la impresora a la de Windows 10 IoT Core 3D del panel mediante el cable USB.</span><span class="sxs-lookup"><span data-stu-id="02295-124">Plug-in your 3D printer to your Windows 10 IoT Core board using the USB cable.</span></span>

    ![Conectar la impresora en 3D con el dispositivo](../media/3DPrintServer/connect-3d-printer.png)

* <span data-ttu-id="02295-126">Abra la aplicación de panel de IoT y compruebe que el dispositivo aparece en la **Mis dispositivos** ficha.</span><span class="sxs-lookup"><span data-stu-id="02295-126">Open the IoT Dashboard app and verify that your device shows up in the **My devices** tab.</span></span>

    ![Compruebe que el dispositivo aparece en el panel de IoT](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a><span data-ttu-id="02295-128">3. Implementar la red de la aplicación de impresión en 3D</span><span class="sxs-lookup"><span data-stu-id="02295-128">3. Deploy the Network 3D Printer app</span></span>
___
* <span data-ttu-id="02295-129">En el panel de IoT, haga clic en el **Pruebe algunos ejemplos** sección.</span><span class="sxs-lookup"><span data-stu-id="02295-129">In IoT Dashboard, click on the **Try some samples** section.</span></span>
* <span data-ttu-id="02295-130">Seleccione la aplicación de ejemplo de impresora 3D de red.</span><span class="sxs-lookup"><span data-stu-id="02295-130">Select the Network 3D Printer sample app.</span></span>

   ![Instalar la impresora de red 3D](../media/3dprintserver/dashboard-samples.png)

* <span data-ttu-id="02295-132">Seleccione el modelo de impresora y presione 3D el **implementar y ejecutar** botón para implementar la aplicación en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="02295-132">Select your 3D Printer model and press the **Deploy and run** button to deploy the app to your IoT Core device.</span></span> 

    ![Instalar la impresora de red 3D](../media/3dprintserver/dashboard-app.png)

    <span data-ttu-id="02295-134">[Imagen 6 de TAZ LulzBot](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) por [alef objetos, Inc.](https://www.alephobjects.com/) arreglo [CC BY SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="02295-134">[LulzBot TAZ 6 image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>
    
    <span data-ttu-id="02295-135">Si desea instalar una opción de seleccionar "personalizado" personalizados de impresora desde la lista de impresoras.</span><span class="sxs-lookup"><span data-stu-id="02295-135">If you wish to install a custom printer select the "Custom" option from the list of Printers.</span></span> <span data-ttu-id="02295-136">Custom impresoras 3d necesitan un archivo xml de configuración llamado archivo PrintDeviceCapabilities.xml proporcionarse correctamente conectarse e imprimir en la impresora en 3d.</span><span class="sxs-lookup"><span data-stu-id="02295-136">Custom 3d Printers need a configuration xml called the PrintDeviceCapabilities.xml file to be provided to correctly connect and print to the 3d printer.</span></span> <span data-ttu-id="02295-137">Un archivo de ejemplo PrintDeviceCapabilities.xml puede encontrarse aquí https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span><span class="sxs-lookup"><span data-stu-id="02295-137">A sample PrintDeviceCapabilities.xml file can be found here https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml</span></span>
   
   <span data-ttu-id="02295-138">Son los mínimos cambios que deba realizar en el archivo xml actualizar las secciones siguientes con los valores correctos específicos de la impresora compatible.</span><span class="sxs-lookup"><span data-stu-id="02295-138">The minimum changes you need to make in the xml file are to update the following sections with the correct values specific to your compatible printer.</span></span>

<span data-ttu-id="02295-139">Estos valores especifican las dimensiones de la cama impresión de la impresora 3d a la segmentación de datos al procesar el modelo 3d</span><span class="sxs-lookup"><span data-stu-id="02295-139">These values specify the print bed dimensions of your 3d printer to the slicer when processing the 3d model</span></span>

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


<span data-ttu-id="02295-140">El valor de la etiqueta xml de psk3dx:baudrate controla la velocidad en baudios específica para usar al comunicarse con la impresora de la raspberry pi3 3d.</span><span class="sxs-lookup"><span data-stu-id="02295-140">The value in the psk3dx:baudrate xml tag controls the specific baud rate to use while communicating with the 3d printer from the raspberry pi3.</span></span> <span data-ttu-id="02295-141">Establecer la velocidad en baudios adecuado específicas para su impresión en 3d.</span><span class="sxs-lookup"><span data-stu-id="02295-141">Set the appropriate baud rate specific to your 3d printer.</span></span> 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

<span data-ttu-id="02295-142">Los demás valores en el xml PrintDeviceCapabilities se usan para notificar a la segmentación de datos en el controlador de impresión en 3d para ajustar su funcionamiento con una determinada impresora compatible.</span><span class="sxs-lookup"><span data-stu-id="02295-142">The other values in the PrintDeviceCapabilities xml are used to notify the slicer in the 3d print driver to fine tune how it works with your specific compatible printer.</span></span>
<span data-ttu-id="02295-143">Más información sobre todos estos valores se proporcionan [aquí](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span><span class="sxs-lookup"><span data-stu-id="02295-143">More information on all these values are provided [here](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).</span></span>

    
    
## <a name="4-add-your-3d-printer"></a><span data-ttu-id="02295-144">4. Agregar la impresora en 3D</span><span class="sxs-lookup"><span data-stu-id="02295-144">4. Add your 3D Printer</span></span>
___
* <span data-ttu-id="02295-145">Vaya a su PC de Windows 10 y a **configuración** -> **dispositivos** -> **, impresoras y escáneres**.</span><span class="sxs-lookup"><span data-stu-id="02295-145">Go to your Windows 10 PC and go to **Settings** -> **Devices** -> **Printers & Scanners**.</span></span>
* <span data-ttu-id="02295-146">Presione **agregar una impresora o un escáner**.</span><span class="sxs-lookup"><span data-stu-id="02295-146">Press **Add a printer or scanner**.</span></span>

     ![Configuración de Windows agrega dispositivo](../media/3dprintserver/add-printer.png)

* <span data-ttu-id="02295-148">Seleccione la impresora y pulse 3D **Agregar dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="02295-148">Select your 3D Printer and press **Add device**.</span></span> <span data-ttu-id="02295-149">La impresora se instalará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="02295-149">The printer will install automatically.</span></span>

     ![Configuración de Windows agrega dispositivo](../media/3dprintserver/add-device.png)

<span data-ttu-id="02295-151">Enhorabuena, que ahora se ha instalado la impresora y se comportará exactamente como si se ha conectado con un cable USB.</span><span class="sxs-lookup"><span data-stu-id="02295-151">Congratulations your printer is now installed and will behave exactly as if it was connected with a USB cable.</span></span>
<span data-ttu-id="02295-152">Ahora puede imprimir utilizando [generador 3D](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span><span class="sxs-lookup"><span data-stu-id="02295-152">You can now print to it using [3D Builder](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).</span></span>
