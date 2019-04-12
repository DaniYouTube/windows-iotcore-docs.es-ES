---
title: Compatibilidad con Bluetooth
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar Bluetooth en dispositivos que ejecutan Windows 10 IoT Core.
keywords: Windows iot, bluetooth, compatibilidad con bluetooth, dispositivos, portal de dispositivos
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514731"
---
# <a name="bluetooth-support"></a>Compatibilidad con Bluetooth
Windows 10 IoT Core es compatible con Bluetooth 4.0. Encontrará una lista de dispositivos de protección admitidos de Bluetooth en el [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).

## <a name="about-bluetooth"></a>Acerca de Bluetooth
Existen dos tecnologías bluetooth diferentes que puede implementar en su aplicación:

* Clásico Bluetooth (RFCOMM) antes de Bluetooth LE, los dispositivos usan normalmente este protocolo para comunicarse con Bluetooth. Este protocolo es simple y de utilidad para la comunicación entre dispositivos sin necesidad de ahorro de energía. Conectividad requiere el emparejamiento.

* Bluetooth de baja energía (BLE/LE) Bluetooth baja energía (LE) es una especificación que define los protocolos para la detección y comunicación entre los dispositivos que tienen un requisito de uso de ahorro de energía. Para obtener más información, incluidos ejemplos de código, según las últimas compilaciones, un dispositivo puede conectarse a un dispositivo BLE sin emparejamiento.

## <a name="supported-bluetooth-profiles"></a>Perfiles de Bluetooth compatibles
Windows 10 IoT Core es compatible con los siguientes perfiles de Bluetooth:

1.  **Conceptos de perfiles de dispositivo de interfaz humana (HID)** HID de un dispositivo toma la entrada de una persona y presenta la salida para consumpation humano. Algunos ejemplos son el teclado, mouse, dispositivo de juego, lector de código de barras, LED y presentación alfanumérica. Un dispositivo Windows 10 IoT Core puede conectarse a un dispositivo HID a través de Bluetooth. Vea el tema acerca de HID general en el contexto de Windows: [Introducción a los conceptos HID](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts). 

2.  **Comunicación por radiofrecuencia (RFCOMM)** RFCOMMM es las comunicaciones en serie subyacentes Bluetooth clásico. Las aplicaciones para UWP, se admiten los siguientes servicios RFCOMM:

* serialPort
* obexObjectPush
* obexFileTransfer
* phoneBookAccessPce
* phoneBookAccessPse
* genericFileTransfer

3. **Perfil de atributo genéricos (GATT)** vea el [UWP Bluetooth baja energía](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) tema. 

> [!NOTE]
> Deberá especificar manualmente los servicios RFCOMM en el AppManifest.  Consulte la [UWP Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) tema. Consulte también el [ejemplo de Chat de UWP Bluetooth Rfcomm](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) tema.

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a>Conectar dispositivos Bluetooth mediante device portal
Al utilizar uno de los [imagen de lanzamiento de Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) dispositivos Bluetooth pueden emparejarse con el dispositivo Windows IoT Core mediante el portal de dispositivo. Al navegar a la pestaña de Bluetooth del dispositivo va a buscar dispositivos Bluetooth y también será reconocible para otros dispositivos Bluetooth. La siguiente imagen muestra una solicitud entrante de emparejamiento. 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_2.png)

Después de que el dispositivo se empareja correctamente, aparecerá en la sección de dispositivo emparejado 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_3.png)
