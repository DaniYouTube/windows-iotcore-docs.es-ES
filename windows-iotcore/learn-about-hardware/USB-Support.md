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
# <a name="overview-of-usb-support-and-dual-role"></a>Información general sobre la compatibilidad con USB y doble función

Un Bus serie Universal (USB) proporciona una interfaz serie Plug and Play conectable en caliente y ampliable que garantiza una conexión estándar y de bajo costo para los dispositivos periféricos, como teclados, mouse, joysticks, impresoras, escáneres, dispositivos de almacenamiento, módems y vídeo cámaras de conferencias.  
Cuando hablamos acerca de los dispositivos USB, la pila de la función USB hace referencia a un grupo de controladores que se enumeran y se cargan mediante el Administrador de Plug and Play y un dispositivo USB compuesto puede admitir varias interfaces en una sola configuración. Aunque la mayor parte de lo que hablamos en este artículo se relaciona con el rol dual para USB 2.0, más conocidos como USB en la oficina o USB OTG o OTG, también es útil saber acerca de USB 3.0 y cómo se diferencia de USB 2.0. El OTG USB define dos roles para los dispositivos: Especifica qué lado OTG un dispositivo y dispositivo OTG B, suministra la alimentación el vínculo y que es inicialmente el host. Puesto que todos los controladores de OTG admite ambos roles, a menudo se denominan controladores "Dual-Role" en lugar de "Controladores de OTG". USB 3.0, puede realizar por otro lado, los dispositivos en los hosts o dispositivos periféricos. Algunos dispositivos pueden tomar cualquiera de estos roles dependiendo de qué tipo se detecta en el otro extremo. Estos tipos de puertos se denominan datos del rol de doble (DRD). Cuando dos de estos dispositivos están conectados, los roles se asignan aleatoriamente, pero se puede ordenar un intercambio desde cualquiera de los extremos. 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>Arquitectura de la función USB en Windows 10 IoT Core

Cuando la plataforma de Windows 10 IoT actúa como dispositivo USB, usará una de varias configuraciones. Cada configuración tiene una o varias interfaces USB. Para admitir correctamente USB OTG en Windows 10 IoT, deben tenerse en cuenta varios aspectos.  

## <a name="components-oems-have-to-supply"></a>Los OEM componentes tengan que suministrar

Los OEM deben proporcionar los componentes en ambos lados: para el lado del dispositivo USB y, posiblemente, para el lado host USB.  

![Proporciona los componentes de un OEM](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>Compatibilidad con los fabricantes OEM para ambos lados

Todos los dispositivos USB tiene único VID y PID, que lo identifique. OEM, como el fabricante de un dispositivo USB basada en Windows IoT, debe proporcionarlos.  Los OEM pueden aplicar a USB Consortium y obtener su empresa VID (si no tienen uno ya) y, a continuación, elija un PID que sea único para ese producto. Cuando Windows 10 IoT con la funcionalidad USBFN está conectado a un equipo actuará como dispositivo USB (de cualquier funcionalidad para elegir como se establece en myUSBFN.sys), con esos "VID_nnn" y "PID_NNN". Esta combinación VID y el PID, a continuación, se usa por el equipo host para encontrar los controladores adecuados para cargar (myUSB.sys). 

![¿Cómo se reúnen las funciones USB](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>Compatibilidad con desde el lado del dispositivo

_Características para incluir en FFU para generación de imágenes con USBFN habilitado_
* La imagen de IoT debe tener los paquetes necesarios en ella, es decir, ufx01000.sys y usbfnclx.sys. Ambos programas acompañan con el siguiente paquete `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`. Los OEM deben usar una etiqueta adecuada "característica" en su propio archivo XML, que enumera todas las características incluidas en el FFU. Por ejemplo, en el archivo BoardTestOEMInput.xml habrá la siguiente entrada <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> incluyen bajo <Microsoft> sección de características. 

_Controlador USB conmutación de roles_
* Para el OTG USB, los OEM deben proporcionar la entrada de tabla ACPI correcta (*myOTGacpi*) para el controlador USB de conmutación de roles y el propio controlador (* myURS.sys).

_Controlador de la función controladora USB_
* Esto depende del hardware utilizado por los OEM. Microsoft proporciona controladores del controlador de función de USB para dos chipsets USB OTG populares: Synopsys y ChipIdea.
* Si elige utilizar otro conjunto de chips USB OTG un OEM, el OEM debe proporcionar su propio hardware del controlador de función USB (*myfunctioncontroller.sys*).

_Controladores de clase de función USB_
* Debe proporcionarse al menos un controlador de clase de función USB.
* Este controlador implementa funcionalidad específica de dispositivo USB. Determina qué va a aparecer el dispositivo como en el host de lado, así como lo que hará.
Por ejemplo, puede aparecer como un dispositivo de comunicaciones en serie o como un dispositivo de almacenamiento masivo o un dispositivo de tipo personalizado completamente (*myUSBFN.sys*).

_Configuración de dispositivo USB (función)_
* Cuando la plataforma de IoT está en modo de dispositivo USB, puede funcionar en una o varias configuraciones. Se debe agregar cada configuración en uso y que han especificado sus propiedades.

_Propiedades comunes_
* Hay propiedades comunes para todas las configuraciones de la función USB de la plataforma de IoT. Es en última instancia, hasta el OEM para especificar las entradas de descriptor USB estándares como VID, PID, DeviceClass, DeviceProtocol, cadena Manufacturerer, número de serie, etcetera.
* Estas propiedades comunes se establecen en el registro en la siguiente ubicación: `HKLM\System\ControlSet001\Control\USBFN\default`

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
> Los valores indicados anteriormente son solo con fines de demostración y no se puede usar en cualquier producto. El OEM debe reemplazar estos campos de marcador de posición con *valores reales* en cada entrada anterior.

_Por las propiedades de configuración_

Las configuraciones se almacenan en un registro en la siguiente clave: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

De forma predeterminada, hay una configuración de la función USB vacío predeterminado incluida en el FFU, como se establece en: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

Resultados de la configuración de este vacío predeterminado en la plataforma de IoT que aparecen como un dispositivo IoT de Windows para el que existe no es ningún controlador instalado en el host.

![Configuraciones para USBFN](../media/USB-Support/config-screenshot.png)

Cada configuración debe especificar ciertas propiedades, como la lista de interfaces. La plataforma de IoT puede funcionar como un dispositivo USB con distintas configuraciones, que liebre define las interfaces de USB que se exponen desde el dispositivo USB al host USB.

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

Actualmente, la configuración seleccionada es lo que estará en vigor cuando se conecta al puerto USB activa: `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_Ejemplos de configuraciones_

1. Configuración de inicio único
   1. Debe contener al menos una interfaz
   2. Puede ser una configuración predeterminada
   3. Cuando se conecta a un equipo, la plataforma IoT aparecerá como ese tipo de dispositivo USB (por ejemplo, un módem o almacenamiento).
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`

2. Configuración compuesta
   1. Contiene una lista de interfaces con parámetros adicionales
   2. Cuando se conecta a un equipo, la plataforma IoT aparecerá como un dispositivo USB compuesto con varias unidades en ella (es decir, estos dispositivos, dispositivo en serie, dispositivo personalizado).
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`

Interfaces USBFN se enumeran en la siguiente clave del registro:
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

Cada entrada de la interfaz USB debe contener un valor de descriptor de la interfaz y un GUID de la interfaz.

### <a name="supporting-from-the-host-side"></a>Compatibilidad con desde el lado del host

Si elige implementar ninguna interfaz USB estándar (por ejemplo, un OEM  almacenamiento masivo) en el dispositivo, a continuación, un equipo host puede usar controladores de Windows en el cuadro de ese tipo de dispositivo USB. Si un OEM implementa cualquier interfaz USB personalizada en el lado del dispositivo, es necesario para lo OEM desarrollar un controlador de host de Windows para ese dispositivo USB función personalizada. 
