---
title: Obtener información general sobre la compatibilidad con USB y rol Dual para Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: Obtenga información sobre la compatibilidad con USB y doble función What ' s, así como cómo personalizarlo para sus dispositivos Windows 10 IoT Core.
keywords: Windows iot, compatibilidad con USB, doble función, USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514528"
---
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="5ddff-104">Información general sobre la compatibilidad con USB y doble función</span><span class="sxs-lookup"><span data-stu-id="5ddff-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="5ddff-105">Un Bus serie Universal (USB) proporciona una interfaz serie Plug and Play conectable en caliente y ampliable que garantiza una conexión estándar y de bajo costo para los dispositivos periféricos, como teclados, mouse, joysticks, impresoras, escáneres, dispositivos de almacenamiento, módems y vídeo cámaras de conferencias.</span><span class="sxs-lookup"><span data-stu-id="5ddff-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="5ddff-106">Cuando hablamos acerca de los dispositivos USB, la pila de la función USB hace referencia a un grupo de controladores que se enumeran y se cargan mediante el Administrador de Plug and Play y un dispositivo USB compuesto puede admitir varias interfaces en una sola configuración.</span><span class="sxs-lookup"><span data-stu-id="5ddff-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="5ddff-107">Aunque la mayor parte de lo que hablamos en este artículo se relaciona con el rol dual para USB 2.0, más conocidos como USB en la oficina o USB OTG o OTG, también es útil saber acerca de USB 3.0 y cómo se diferencia de USB 2.0.</span><span class="sxs-lookup"><span data-stu-id="5ddff-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="5ddff-108">El OTG USB define dos roles para los dispositivos: Especifica qué lado OTG un dispositivo y dispositivo OTG B, suministra la alimentación el vínculo y que es inicialmente el host.</span><span class="sxs-lookup"><span data-stu-id="5ddff-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="5ddff-109">Puesto que todos los controladores de OTG admite ambos roles, a menudo se denominan controladores "Dual-Role" en lugar de "Controladores de OTG".</span><span class="sxs-lookup"><span data-stu-id="5ddff-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="5ddff-110">USB 3.0, puede realizar por otro lado, los dispositivos en los hosts o dispositivos periféricos.</span><span class="sxs-lookup"><span data-stu-id="5ddff-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="5ddff-111">Algunos dispositivos pueden tomar cualquiera de estos roles dependiendo de qué tipo se detecta en el otro extremo.</span><span class="sxs-lookup"><span data-stu-id="5ddff-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="5ddff-112">Estos tipos de puertos se denominan datos del rol de doble (DRD).</span><span class="sxs-lookup"><span data-stu-id="5ddff-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="5ddff-113">Cuando dos de estos dispositivos están conectados, los roles se asignan aleatoriamente, pero se puede ordenar un intercambio desde cualquiera de los extremos.</span><span class="sxs-lookup"><span data-stu-id="5ddff-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="5ddff-114">Arquitectura de la función USB en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="5ddff-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="5ddff-115">Cuando la plataforma de Windows 10 IoT actúa como dispositivo USB, usará una de varias configuraciones.</span><span class="sxs-lookup"><span data-stu-id="5ddff-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="5ddff-116">Cada configuración tiene una o varias interfaces USB.</span><span class="sxs-lookup"><span data-stu-id="5ddff-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="5ddff-117">Para admitir correctamente USB OTG en Windows 10 IoT, deben tenerse en cuenta varios aspectos.</span><span class="sxs-lookup"><span data-stu-id="5ddff-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="5ddff-118">Los OEM componentes tengan que suministrar</span><span class="sxs-lookup"><span data-stu-id="5ddff-118">Components OEMs have to supply</span></span>

<span data-ttu-id="5ddff-119">Los OEM deben proporcionar los componentes en ambos lados: para el lado del dispositivo USB y, posiblemente, para el lado host USB.</span><span class="sxs-lookup"><span data-stu-id="5ddff-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![Proporciona los componentes de un OEM](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="5ddff-121">Compatibilidad con los fabricantes OEM para ambos lados</span><span class="sxs-lookup"><span data-stu-id="5ddff-121">OEMs support for both sides</span></span>

<span data-ttu-id="5ddff-122">Todos los dispositivos USB tiene único VID y PID, que lo identifique.</span><span class="sxs-lookup"><span data-stu-id="5ddff-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="5ddff-123">OEM, como el fabricante de un dispositivo USB basada en Windows IoT, debe proporcionarlos.</span><span class="sxs-lookup"><span data-stu-id="5ddff-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="5ddff-124">Los OEM pueden aplicar a USB Consortium y obtener su empresa VID (si no tienen uno ya) y, a continuación, elija un PID que sea único para ese producto.</span><span class="sxs-lookup"><span data-stu-id="5ddff-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="5ddff-125">Cuando Windows 10 IoT con la funcionalidad USBFN está conectado a un equipo actuará como dispositivo USB (de cualquier funcionalidad para elegir como se establece en myUSBFN.sys), con esos "VID_nnn" y "PID_NNN".</span><span class="sxs-lookup"><span data-stu-id="5ddff-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="5ddff-126">Esta combinación VID y el PID, a continuación, se usa por el equipo host para encontrar los controladores adecuados para cargar (myUSB.sys).</span><span class="sxs-lookup"><span data-stu-id="5ddff-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![¿Cómo se reúnen las funciones USB](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="5ddff-128">Compatibilidad con desde el lado del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddff-128">Supporting from the device side</span></span>

_<span data-ttu-id="5ddff-129">Características para incluir en FFU para generación de imágenes con USBFN habilitado</span><span class="sxs-lookup"><span data-stu-id="5ddff-129">Features to include in FFU for image generation with USBFN enabled</span></span>_
* <span data-ttu-id="5ddff-130">La imagen de IoT debe tener los paquetes necesarios en ella, es decir, ufx01000.sys y usbfnclx.sys.</span><span class="sxs-lookup"><span data-stu-id="5ddff-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="5ddff-131">Ambos programas acompañan con el siguiente paquete `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span><span class="sxs-lookup"><span data-stu-id="5ddff-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="5ddff-132">Los OEM deben usar una etiqueta adecuada "característica" en su propio archivo XML, que enumera todas las características incluidas en el FFU.</span><span class="sxs-lookup"><span data-stu-id="5ddff-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="5ddff-133">Por ejemplo, en el archivo BoardTestOEMInput.xml habrá la siguiente entrada <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> incluyen bajo <Microsoft> sección de características.</span><span class="sxs-lookup"><span data-stu-id="5ddff-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

_<span data-ttu-id="5ddff-134">Controlador USB conmutación de roles</span><span class="sxs-lookup"><span data-stu-id="5ddff-134">USB Role Switching driver</span></span>_
* <span data-ttu-id="5ddff-135">Para el OTG USB, los OEM deben proporcionar la entrada de tabla ACPI correcta (*myOTGacpi*) para el controlador USB de conmutación de roles y el propio controlador (\* myURS.sys).</span><span class="sxs-lookup"><span data-stu-id="5ddff-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

_<span data-ttu-id="5ddff-136">Controlador de la función controladora USB</span><span class="sxs-lookup"><span data-stu-id="5ddff-136">USB Function Controller Driver</span></span>_
* <span data-ttu-id="5ddff-137">Esto depende del hardware utilizado por los OEM.</span><span class="sxs-lookup"><span data-stu-id="5ddff-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="5ddff-138">Microsoft proporciona controladores del controlador de función de USB para dos chipsets USB OTG populares: Synopsys y ChipIdea.</span><span class="sxs-lookup"><span data-stu-id="5ddff-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="5ddff-139">Si elige utilizar otro conjunto de chips USB OTG un OEM, el OEM debe proporcionar su propio hardware del controlador de función USB (*myfunctioncontroller.sys*).</span><span class="sxs-lookup"><span data-stu-id="5ddff-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

_<span data-ttu-id="5ddff-140">Controladores de clase de función USB</span><span class="sxs-lookup"><span data-stu-id="5ddff-140">USB Function Class drivers</span></span>_
* <span data-ttu-id="5ddff-141">Debe proporcionarse al menos un controlador de clase de función USB.</span><span class="sxs-lookup"><span data-stu-id="5ddff-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="5ddff-142">Este controlador implementa funcionalidad específica de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="5ddff-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="5ddff-143">Determina qué va a aparecer el dispositivo como en el host de lado, así como lo que hará.</span><span class="sxs-lookup"><span data-stu-id="5ddff-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="5ddff-144">Por ejemplo, puede aparecer como un dispositivo de comunicaciones en serie o como un dispositivo de almacenamiento masivo o un dispositivo de tipo personalizado completamente (*myUSBFN.sys*).</span><span class="sxs-lookup"><span data-stu-id="5ddff-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

_<span data-ttu-id="5ddff-145">Configuración de dispositivo USB (función)</span><span class="sxs-lookup"><span data-stu-id="5ddff-145">Configuring USB Function Device</span></span>_
* <span data-ttu-id="5ddff-146">Cuando la plataforma de IoT está en modo de dispositivo USB, puede funcionar en una o varias configuraciones.</span><span class="sxs-lookup"><span data-stu-id="5ddff-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="5ddff-147">Se debe agregar cada configuración en uso y que han especificado sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="5ddff-147">Each configuration in use must be added and have its properties specified.</span></span>

_<span data-ttu-id="5ddff-148">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="5ddff-148">Common Properties</span></span>_
* <span data-ttu-id="5ddff-149">Hay propiedades comunes para todas las configuraciones de la función USB de la plataforma de IoT.</span><span class="sxs-lookup"><span data-stu-id="5ddff-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="5ddff-150">Es en última instancia, hasta el OEM para especificar las entradas de descriptor USB estándares como VID, PID, DeviceClass, DeviceProtocol, cadena Manufacturerer, número de serie, etcetera.</span><span class="sxs-lookup"><span data-stu-id="5ddff-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="5ddff-151">Estas propiedades comunes se establecen en el registro en la siguiente ubicación:</span><span class="sxs-lookup"><span data-stu-id="5ddff-151">These common properties are set in registry in the following location:</span></span> `HKLM\System\ControlSet001\Control\USBFN\default`

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
> <span data-ttu-id="5ddff-152">Los valores indicados anteriormente son solo con fines de demostración y no se puede usar en cualquier producto.</span><span class="sxs-lookup"><span data-stu-id="5ddff-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="5ddff-153">El OEM debe reemplazar estos campos de marcador de posición con *valores reales* en cada entrada anterior.</span><span class="sxs-lookup"><span data-stu-id="5ddff-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

_<span data-ttu-id="5ddff-154">Por las propiedades de configuración</span><span class="sxs-lookup"><span data-stu-id="5ddff-154">Per configuration properties</span></span>_

<span data-ttu-id="5ddff-155">Las configuraciones se almacenan en un registro en la siguiente clave:</span><span class="sxs-lookup"><span data-stu-id="5ddff-155">Configurations are stored in a registry under the following key:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

<span data-ttu-id="5ddff-156">De forma predeterminada, hay una configuración de la función USB vacío predeterminado incluida en el FFU, como se establece en:</span><span class="sxs-lookup"><span data-stu-id="5ddff-156">By default, there is an empty default USB function configuration included in the FFU, as set in:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

<span data-ttu-id="5ddff-157">Resultados de la configuración de este vacío predeterminado en la plataforma de IoT que aparecen como un dispositivo IoT de Windows para el que existe no es ningún controlador instalado en el host.</span><span class="sxs-lookup"><span data-stu-id="5ddff-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![Configuraciones para USBFN](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="5ddff-159">Cada configuración debe especificar ciertas propiedades, como la lista de interfaces.</span><span class="sxs-lookup"><span data-stu-id="5ddff-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="5ddff-160">La plataforma de IoT puede funcionar como un dispositivo USB con distintas configuraciones, que liebre define las interfaces de USB que se exponen desde el dispositivo USB al host USB.</span><span class="sxs-lookup"><span data-stu-id="5ddff-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="5ddff-161">Actualmente, la configuración seleccionada es lo que estará en vigor cuando se conecta al puerto USB activa:</span><span class="sxs-lookup"><span data-stu-id="5ddff-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_<span data-ttu-id="5ddff-162">Ejemplos de configuraciones</span><span class="sxs-lookup"><span data-stu-id="5ddff-162">Examples of configurations</span></span>_

1. <span data-ttu-id="5ddff-163">Configuración de inicio único</span><span class="sxs-lookup"><span data-stu-id="5ddff-163">Single configuration</span></span>
   1. <span data-ttu-id="5ddff-164">Debe contener al menos una interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddff-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="5ddff-165">Puede ser una configuración predeterminada</span><span class="sxs-lookup"><span data-stu-id="5ddff-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="5ddff-166">Cuando se conecta a un equipo, la plataforma IoT aparecerá como ese tipo de dispositivo USB (por ejemplo, un módem o almacenamiento).</span><span class="sxs-lookup"><span data-stu-id="5ddff-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`<span data-ttu-id="5ddff-167">,</span><span class="sxs-lookup"><span data-stu-id="5ddff-167">,</span></span> `InterfaceList = "MODEM\0MTP"`

2. <span data-ttu-id="5ddff-168">Configuración compuesta</span><span class="sxs-lookup"><span data-stu-id="5ddff-168">Composite configuration</span></span>
   1. <span data-ttu-id="5ddff-169">Contiene una lista de interfaces con parámetros adicionales</span><span class="sxs-lookup"><span data-stu-id="5ddff-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="5ddff-170">Cuando se conecta a un equipo, la plataforma IoT aparecerá como un dispositivo USB compuesto con varias unidades en ella (es decir, estos dispositivos, dispositivo en serie, dispositivo personalizado).</span><span class="sxs-lookup"><span data-stu-id="5ddff-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`<span data-ttu-id="5ddff-171">,</span><span class="sxs-lookup"><span data-stu-id="5ddff-171">,</span></span> `InterfaceList = "MODEM\0MTP"`

<span data-ttu-id="5ddff-172">Interfaces USBFN se enumeran en la siguiente clave del registro:</span><span class="sxs-lookup"><span data-stu-id="5ddff-172">USBFN Interfaces are enumerated in registry under the following key:</span></span>
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

<span data-ttu-id="5ddff-173">Cada entrada de la interfaz USB debe contener un valor de descriptor de la interfaz y un GUID de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="5ddff-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="5ddff-174">Compatibilidad con desde el lado del host</span><span class="sxs-lookup"><span data-stu-id="5ddff-174">Supporting from the host side</span></span>

<span data-ttu-id="5ddff-175">Si elige implementar ninguna interfaz USB estándar (por ejemplo, un OEM  almacenamiento masivo) en el dispositivo, a continuación, un equipo host puede usar controladores de Windows en el cuadro de ese tipo de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="5ddff-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="5ddff-176">Si un OEM implementa cualquier interfaz USB personalizada en el lado del dispositivo, es necesario para lo OEM desarrollar un controlador de host de Windows para ese dispositivo USB función personalizada.</span><span class="sxs-lookup"><span data-stu-id="5ddff-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
