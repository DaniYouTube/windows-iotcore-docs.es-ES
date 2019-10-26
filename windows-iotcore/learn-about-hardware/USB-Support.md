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
# <a name="overview-of-usb-support-and-dual-role"></a>Información general sobre la compatibilidad con USB y el rol dual

Un bus serie universal (USB) proporciona una interfaz serie Plug and Play expansible y conectable en caliente que garantiza una conexión estándar de bajo costo para dispositivos periféricos como teclados, ratones, joysticks, impresoras, escáneres, dispositivos de almacenamiento, módems y vídeo. cámaras de conferencia.  
Cuando hablamos sobre dispositivos USB, la pila de funciones USB hace referencia a un grupo de controladores que el administrador de Plug and Play enumera y carga, y un dispositivo USB compuesto puede admitir varias interfaces en una sola configuración. Aunque la mayor parte de lo que hablamos en este artículo se refiere a la función dual de USB 2,0, más comúnmente conocida como USB a la vez o por el grupo OTG o OTG de USB, también resulta útil conocer USB 3,0 y cómo difiere de USB 2,0. El grupo OTG de USB define dos roles para dispositivos: OTG A-Device y OTG-Device, especificando qué lado suministra la alimentación al vínculo y cuál es el host inicialmente. Puesto que cada controlador OTG admite ambos roles, a menudo se denominan controladores de "doble rol" en lugar de "controladores OTG". USB 3,0, por otro lado, puede crear dispositivos en hosts o periféricos. Algunos dispositivos pueden tomar cualquier rol en función del tipo que se detecte en el otro extremo. Estos tipos de puertos se denominan datos de doble rol (DRD). Cuando dos dispositivos de este tipo están conectados, los roles se asignan aleatoriamente, pero se puede hacer un comando swap desde cualquier extremo. 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a>Arquitectura de la función USB en Windows 10 IoT Core

Cuando la plataforma de IoT de Windows 10 actúa como dispositivo USB, utilizará una de varias configuraciones. Cada configuración tiene una o más interfaces USB. Para admitir correctamente el OTG USB en Windows 10 IoT, es necesario tener en cuenta varios aspectos.  

## <a name="components-oems-have-to-supply"></a>Componentes que los OEM deben proporcionar

Los OEM deben proporcionar componentes en ambos lados: para el dispositivo USB y, posiblemente, para el host USB.  

![Componentes que proporciona un OEM](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a>Compatibilidad con OEM para ambos lados

Cada dispositivo USB tiene un VID y un PID únicos, que lo identifican. Un OEM, como fabricante de un dispositivo USB basado en Windows IoT, debe proporcionarlos.  Los fabricantes de equipos originales (OEM) pueden aplicarse al consorcio USB y obtener el VID de su empresa (si aún no tienen uno) y, a continuación, elegir un PID que sea único para ese producto. Cuando Windows 10 IoT con la funcionalidad de USBFN está conectado a un equipo, actuará como dispositivo USB (de cualquier funcionalidad que se elija como se establece en myUSBFN. sys), con los "VID_nnn" y "PID_NNN". El equipo host usa esta combinación de VID y PID para encontrar los controladores adecuados para cargar (myUSB. sys). 

![Cómo se unen las funciones USB](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a>Compatibilidad desde el lado del dispositivo

_Características que se van a incluir en FFU para la generación de imágenes con USBFN habilitado_
* La imagen de IoT debe tener los paquetes necesarios en ella, es decir, ufx01000. sys y usbfnclx. sys. Ambos se componen de la `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`de paquete siguiente. Los OEM deben usar una etiqueta "Feature" adecuada en su archivo XML, que enumera todas las características incluidas en FFU. Por ejemplo, en el archivo BoardTestOEMInput. XML se incluirá la siguiente entrada <Feature>IOT_USBFN_CLASS_EXTENSION</Feature> en la sección <Microsoft> características. 

_Controlador de conmutación de roles USB_
* Para el OTG USB, los OEM deben proporcionar la entrada de tabla ACPI (*myOTGacpi*) correcta para el controlador de conmutación de roles USB y el propio controlador (* myURS. sys).

_Controlador de controlador de función USB_
* Esto depende del hardware utilizado por los OEM. Microsoft proporciona controladores de controlador de función USB para dos conjuntos de chips de OTG de USB populares: Sinopsis y ChipIdea.
* Si un OEM decide usar otro conjunto de chips del OTG de USB, el OEM debe proporcionar su propio hardware de controlador de función USB (*myfunctioncontroller. sys*).

_Controladores de clase de función USB_
* Se debe proporcionar al menos un controlador de clase de función USB.
* Este controlador implementa la funcionalidad específica del dispositivo USB. Determina lo que el dispositivo mostrará como en el lado del host, así como lo que hará.
Por ejemplo, puede aparecer como un dispositivo de comunicaciones serie o como un dispositivo de almacenamiento masivo o un dispositivo de tipo completamente personalizado (*myUSBFN. sys*).

_Configuración de dispositivos de función USB_
* Cuando la plataforma de IoT está en modo de dispositivo USB, puede funcionar con una o más configuraciones. Cada configuración en uso debe agregarse y tener sus propiedades especificadas.

_Propiedades comunes_
* Hay propiedades comunes para todas las configuraciones de funciones USB de la plataforma de IoT. En última instancia, el OEM debe especificar entradas de descriptor USB estándar como VID, PID, DeviceClass, DeviceProtocol, cadena de fabricante, número de serie, etc.
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
> Los valores anteriores son solo para fines de demostración y no se pueden usar en ningún producto. El OEM debe reemplazar estos campos de marcador de posición por *los valores reales* de cada entrada anterior.

_Por propiedades de configuración_

Las configuraciones se almacenan en un registro con la siguiente clave: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

De forma predeterminada, hay una configuración de función USB predeterminada vacía incluida en FFU, como se establece en: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

Esta configuración predeterminada vacía hace que la plataforma de IoT aparezca como un dispositivo de Windows IoT para el que no hay ningún controlador en el lado del host instalado.

![Configuraciones para USBFN](../media/USB-Support/config-screenshot.png)

Cada configuración debe especificar ciertas propiedades, como la lista de interfaces. La plataforma de IoT puede funcionar como un dispositivo USB con distintas configuraciones, lo que Vidor define las interfaces USB que se exponen desde el dispositivo USB al host USB.

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

Actualmente, la configuración seleccionada es la que se aplicará cuando se conecte al dispositivo USB activo: `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_Ejemplos de configuraciones_

1. Configuración única
   1. Debe contener al menos una interfaz.
   2. Puede ser una configuración predeterminada
   3. Cuando se conecta a un equipo, la plataforma de IoT aparecerá como ese tipo de dispositivo USB (por ejemplo, módem o almacenamiento).
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`

2. Configuración compuesta
   1. Contiene una lista de interfaces con parámetros adicionales
   2. Cuando se conecta a un equipo, la plataforma de IoT aparecerá como un dispositivo USB compuesto con varias unidades (es decir, dispositivo MTP, dispositivo serie, dispositivo personalizado).
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`

Las interfaces USBFN se enumeran en el registro con la siguiente clave: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

Cada entrada de interfaz USB debe contener un valor de descriptor de interfaz y un GUID de interfaz.

### <a name="supporting-from-the-host-side"></a>Compatibilidad desde el lado del host

Si un OEM elige implementar cualquier interfaz USB estándar (por ejemplo,  almacenamiento masivo) en el lado del dispositivo, un equipo host puede usar controladores Windows incluidos para ese tipo de dispositivo USB. Si un OEM implementa una interfaz USB personalizada en el lado del dispositivo, es necesario que el OEM desarrolle un controlador de host de Windows para ese dispositivo de función USB personalizado. 
