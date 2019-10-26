---
title: Información general sobre la compatibilidad con USB y el doble rol para Windows 10 IoT Core
ms.date: 10/11/2017
ms.topic: article
description: Obtenga información sobre la compatibilidad con USB y el rol dual, así como sobre cómo personalizar esto para sus dispositivos Windows 10 IoT Core.
keywords: Windows IOT, compatibilidad con USB, doble función, USB
ms.openlocfilehash: 11b359d096aedf44e0dac8f87d343caa5db3f57f
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917332"
---
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="07439-104">Información general sobre la compatibilidad con USB y el rol dual</span><span class="sxs-lookup"><span data-stu-id="07439-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="07439-105">Un bus serie universal (USB) proporciona una interfaz serie Plug and Play expansible y conectable en caliente que garantiza una conexión estándar de bajo costo para dispositivos periféricos como teclados, ratones, joysticks, impresoras, escáneres, dispositivos de almacenamiento, módems y vídeo. cámaras de conferencia.</span><span class="sxs-lookup"><span data-stu-id="07439-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="07439-106">Cuando hablamos sobre dispositivos USB, la pila de funciones USB hace referencia a un grupo de controladores que el administrador de Plug and Play enumera y carga, y un dispositivo USB compuesto puede admitir varias interfaces en una sola configuración.</span><span class="sxs-lookup"><span data-stu-id="07439-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="07439-107">Aunque la mayor parte de lo que hablamos en este artículo se refiere a la función dual de USB 2,0, más comúnmente conocida como USB a la vez o por el grupo OTG o OTG de USB, también resulta útil conocer USB 3,0 y cómo difiere de USB 2,0.</span><span class="sxs-lookup"><span data-stu-id="07439-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="07439-108">El grupo OTG de USB define dos roles para dispositivos: OTG A-Device y OTG-Device, especificando qué lado suministra la alimentación al vínculo y cuál es el host inicialmente.</span><span class="sxs-lookup"><span data-stu-id="07439-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="07439-109">Puesto que cada controlador OTG admite ambos roles, a menudo se denominan controladores de "doble rol" en lugar de "controladores OTG".</span><span class="sxs-lookup"><span data-stu-id="07439-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="07439-110">USB 3,0, por otro lado, puede crear dispositivos en hosts o periféricos.</span><span class="sxs-lookup"><span data-stu-id="07439-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="07439-111">Algunos dispositivos pueden tomar cualquier rol en función del tipo que se detecte en el otro extremo.</span><span class="sxs-lookup"><span data-stu-id="07439-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="07439-112">Estos tipos de puertos se denominan datos de doble rol (DRD).</span><span class="sxs-lookup"><span data-stu-id="07439-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="07439-113">Cuando dos dispositivos de este tipo están conectados, los roles se asignan aleatoriamente, pero se puede hacer un comando swap desde cualquier extremo.</span><span class="sxs-lookup"><span data-stu-id="07439-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="07439-114">Arquitectura de la función USB en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="07439-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="07439-115">Cuando la plataforma de IoT de Windows 10 actúa como dispositivo USB, utilizará una de varias configuraciones.</span><span class="sxs-lookup"><span data-stu-id="07439-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="07439-116">Cada configuración tiene una o más interfaces USB.</span><span class="sxs-lookup"><span data-stu-id="07439-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="07439-117">Para admitir correctamente el OTG USB en Windows 10 IoT, es necesario tener en cuenta varios aspectos.</span><span class="sxs-lookup"><span data-stu-id="07439-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="07439-118">Componentes que los OEM deben proporcionar</span><span class="sxs-lookup"><span data-stu-id="07439-118">Components OEMs have to supply</span></span>

<span data-ttu-id="07439-119">Los OEM deben proporcionar componentes en ambos lados: para el dispositivo USB y, posiblemente, para el host USB.</span><span class="sxs-lookup"><span data-stu-id="07439-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![Componentes que proporciona un OEM](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="07439-121">Compatibilidad con OEM para ambos lados</span><span class="sxs-lookup"><span data-stu-id="07439-121">OEMs support for both sides</span></span>

<span data-ttu-id="07439-122">Cada dispositivo USB tiene un VID y un PID únicos, que lo identifican.</span><span class="sxs-lookup"><span data-stu-id="07439-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="07439-123">Un OEM, como fabricante de un dispositivo USB basado en Windows IoT, debe proporcionarlos.</span><span class="sxs-lookup"><span data-stu-id="07439-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="07439-124">Los fabricantes de equipos originales (OEM) pueden aplicarse al consorcio USB y obtener el VID de su empresa (si aún no tienen uno) y, a continuación, elegir un PID que sea único para ese producto.</span><span class="sxs-lookup"><span data-stu-id="07439-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="07439-125">Cuando Windows 10 IoT con la funcionalidad de USBFN está conectado a un equipo, actuará como dispositivo USB (de cualquier funcionalidad que se elija como se establece en myUSBFN. sys), con los "VID_nnn" y "PID_NNN".</span><span class="sxs-lookup"><span data-stu-id="07439-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="07439-126">El equipo host usa esta combinación de VID y PID para encontrar los controladores adecuados para cargar (myUSB. sys).</span><span class="sxs-lookup"><span data-stu-id="07439-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![Cómo se unen las funciones USB](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="07439-128">Compatibilidad desde el lado del dispositivo</span><span class="sxs-lookup"><span data-stu-id="07439-128">Supporting from the device side</span></span>

<span data-ttu-id="07439-129">_Características que se van a incluir en FFU para la generación de imágenes con USBFN habilitado_</span><span class="sxs-lookup"><span data-stu-id="07439-129">_Features to include in FFU for image generation with USBFN enabled_</span></span>
* <span data-ttu-id="07439-130">La imagen de IoT debe tener los paquetes necesarios en ella, es decir, ufx01000. sys y usbfnclx. sys.</span><span class="sxs-lookup"><span data-stu-id="07439-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="07439-131">Ambos se componen de la `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`de paquete siguiente.</span><span class="sxs-lookup"><span data-stu-id="07439-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="07439-132">Los OEM deben usar una etiqueta "Feature" adecuada en su archivo XML, que enumera todas las características incluidas en FFU.</span><span class="sxs-lookup"><span data-stu-id="07439-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="07439-133">Por ejemplo, en el archivo BoardTestOEMInput. XML se incluirá la siguiente entrada <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> en la sección <Microsoft> características.</span><span class="sxs-lookup"><span data-stu-id="07439-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

<span data-ttu-id="07439-134">_Controlador de conmutación de roles USB_</span><span class="sxs-lookup"><span data-stu-id="07439-134">_USB Role Switching driver_</span></span>
* <span data-ttu-id="07439-135">Para el OTG USB, los OEM deben proporcionar la entrada de tabla ACPI (*myOTGacpi*) correcta para el controlador de conmutación de roles USB y el propio controlador (\* myURS. sys).</span><span class="sxs-lookup"><span data-stu-id="07439-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

<span data-ttu-id="07439-136">_Controlador de controlador de función USB_</span><span class="sxs-lookup"><span data-stu-id="07439-136">_USB Function Controller Driver_</span></span>
* <span data-ttu-id="07439-137">Esto depende del hardware utilizado por los OEM.</span><span class="sxs-lookup"><span data-stu-id="07439-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="07439-138">Microsoft proporciona controladores de controlador de función USB para dos conjuntos de chips de OTG de USB populares: Sinopsis y ChipIdea.</span><span class="sxs-lookup"><span data-stu-id="07439-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="07439-139">Si un OEM decide usar otro conjunto de chips del OTG de USB, el OEM debe proporcionar su propio hardware de controlador de función USB (*myfunctioncontroller. sys*).</span><span class="sxs-lookup"><span data-stu-id="07439-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

<span data-ttu-id="07439-140">_Controladores de clase de función USB_</span><span class="sxs-lookup"><span data-stu-id="07439-140">_USB Function Class drivers_</span></span>
* <span data-ttu-id="07439-141">Se debe proporcionar al menos un controlador de clase de función USB.</span><span class="sxs-lookup"><span data-stu-id="07439-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="07439-142">Este controlador implementa la funcionalidad específica del dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="07439-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="07439-143">Determina lo que el dispositivo mostrará como en el lado del host, así como lo que hará.</span><span class="sxs-lookup"><span data-stu-id="07439-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="07439-144">Por ejemplo, puede aparecer como un dispositivo de comunicaciones serie o como un dispositivo de almacenamiento masivo o un dispositivo de tipo completamente personalizado (*myUSBFN. sys*).</span><span class="sxs-lookup"><span data-stu-id="07439-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

<span data-ttu-id="07439-145">_Configuración de dispositivos de función USB_</span><span class="sxs-lookup"><span data-stu-id="07439-145">_Configuring USB Function Device_</span></span>
* <span data-ttu-id="07439-146">Cuando la plataforma de IoT está en modo de dispositivo USB, puede funcionar con una o más configuraciones.</span><span class="sxs-lookup"><span data-stu-id="07439-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="07439-147">Cada configuración en uso debe agregarse y tener sus propiedades especificadas.</span><span class="sxs-lookup"><span data-stu-id="07439-147">Each configuration in use must be added and have its properties specified.</span></span>

<span data-ttu-id="07439-148">_Propiedades comunes_</span><span class="sxs-lookup"><span data-stu-id="07439-148">_Common Properties_</span></span>
* <span data-ttu-id="07439-149">Hay propiedades comunes para todas las configuraciones de funciones USB de la plataforma de IoT.</span><span class="sxs-lookup"><span data-stu-id="07439-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="07439-150">En última instancia, el OEM debe especificar entradas de descriptor USB estándar como VID, PID, DeviceClass, DeviceProtocol, cadena de fabricante, número de serie, etc.</span><span class="sxs-lookup"><span data-stu-id="07439-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="07439-151">Estas propiedades comunes se establecen en el registro en la siguiente ubicación: `HKLM\System\ControlSet001\Control\USBFN\default`</span><span class="sxs-lookup"><span data-stu-id="07439-151">These common properties are set in registry in the following location: `HKLM\System\ControlSet001\Control\USBFN\default`</span></span>

```
BcdDevice=0x1 
bDeviceClass=0x0 
bDeviceProtocol=0x0 
bDeviceSubClass= 0x0 
idProduct= 0xc0c0 
idVendor=0x045e 
iManufacturer=1 
iSerialNumber=3 
ManufacturerString=OEMname 
ProductString="Windows IOT" 
SerialNumberString=0x123 
```
> [!IMPORTANT]
> <span data-ttu-id="07439-152">Los valores anteriores son solo para fines de demostración y no se pueden usar en ningún producto.</span><span class="sxs-lookup"><span data-stu-id="07439-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="07439-153">El OEM debe reemplazar estos campos de marcador de posición por *los valores reales* de cada entrada anterior.</span><span class="sxs-lookup"><span data-stu-id="07439-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

<span data-ttu-id="07439-154">_Por propiedades de configuración_</span><span class="sxs-lookup"><span data-stu-id="07439-154">_Per configuration properties_</span></span>

<span data-ttu-id="07439-155">Las configuraciones se almacenan en un registro con la siguiente clave: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`</span><span class="sxs-lookup"><span data-stu-id="07439-155">Configurations are stored in a registry under the following key: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`</span></span>

<span data-ttu-id="07439-156">De forma predeterminada, hay una configuración de función USB predeterminada vacía incluida en FFU, como se establece en: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`</span><span class="sxs-lookup"><span data-stu-id="07439-156">By default, there is an empty default USB function configuration included in the FFU, as set in: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`</span></span>

<span data-ttu-id="07439-157">Esta configuración predeterminada vacía hace que la plataforma de IoT aparezca como un dispositivo de Windows IoT para el que no hay ningún controlador en el lado del host instalado.</span><span class="sxs-lookup"><span data-stu-id="07439-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![Configuraciones para USBFN](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="07439-159">Cada configuración debe especificar ciertas propiedades, como la lista de interfaces.</span><span class="sxs-lookup"><span data-stu-id="07439-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="07439-160">La plataforma de IoT puede funcionar como un dispositivo USB con distintas configuraciones, lo que Vidor define las interfaces USB que se exponen desde el dispositivo USB al host USB.</span><span class="sxs-lookup"><span data-stu-id="07439-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="07439-161">Actualmente, la configuración seleccionada es la que se aplicará cuando se conecte al dispositivo USB activo: `HKLM\SYSTEM\ControlSet001\Control\USBFN`</span><span class="sxs-lookup"><span data-stu-id="07439-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot: `HKLM\SYSTEM\ControlSet001\Control\USBFN`</span></span>

<span data-ttu-id="07439-162">_Ejemplos de configuraciones_</span><span class="sxs-lookup"><span data-stu-id="07439-162">_Examples of configurations_</span></span>

1. <span data-ttu-id="07439-163">Configuración única</span><span class="sxs-lookup"><span data-stu-id="07439-163">Single configuration</span></span>
   1. <span data-ttu-id="07439-164">Debe contener al menos una interfaz.</span><span class="sxs-lookup"><span data-stu-id="07439-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="07439-165">Puede ser una configuración predeterminada</span><span class="sxs-lookup"><span data-stu-id="07439-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="07439-166">Cuando se conecta a un equipo, la plataforma de IoT aparecerá como ese tipo de dispositivo USB (por ejemplo, módem o almacenamiento).</span><span class="sxs-lookup"><span data-stu-id="07439-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. <span data-ttu-id="07439-167">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`</span><span class="sxs-lookup"><span data-stu-id="07439-167">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`</span></span>

2. <span data-ttu-id="07439-168">Configuración compuesta</span><span class="sxs-lookup"><span data-stu-id="07439-168">Composite configuration</span></span>
   1. <span data-ttu-id="07439-169">Contiene una lista de interfaces con parámetros adicionales</span><span class="sxs-lookup"><span data-stu-id="07439-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="07439-170">Cuando se conecta a un equipo, la plataforma de IoT aparecerá como un dispositivo USB compuesto con varias unidades (es decir, dispositivo MTP, dispositivo serie, dispositivo personalizado).</span><span class="sxs-lookup"><span data-stu-id="07439-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. <span data-ttu-id="07439-171">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`</span><span class="sxs-lookup"><span data-stu-id="07439-171">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`</span></span>

<span data-ttu-id="07439-172">Las interfaces USBFN se enumeran en el registro con la siguiente clave: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`</span><span class="sxs-lookup"><span data-stu-id="07439-172">USBFN Interfaces are enumerated in registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`</span></span>

<span data-ttu-id="07439-173">Cada entrada de interfaz USB debe contener un valor de descriptor de interfaz y un GUID de interfaz.</span><span class="sxs-lookup"><span data-stu-id="07439-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="07439-174">Compatibilidad desde el lado del host</span><span class="sxs-lookup"><span data-stu-id="07439-174">Supporting from the host side</span></span>

<span data-ttu-id="07439-175">Si un OEM elige implementar cualquier interfaz USB estándar (por ejemplo,  almacenamiento masivo) en el lado del dispositivo, un equipo host puede usar controladores Windows incluidos para ese tipo de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="07439-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="07439-176">Si un OEM implementa una interfaz USB personalizada en el lado del dispositivo, es necesario que el OEM desarrolle un controlador de host de Windows para ese dispositivo de función USB personalizado.</span><span class="sxs-lookup"><span data-stu-id="07439-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
