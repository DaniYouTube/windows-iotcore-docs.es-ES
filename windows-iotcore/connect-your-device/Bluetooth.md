---
title: Compatibilidad con Bluetooth
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo aprovechar Bluetooth para dispositivos que ejecutan Windows 10 IoT Core.
keywords: Windows IOT, Bluetooth, compatibilidad con Bluetooth, dispositivos, portal de dispositivos
ms.openlocfilehash: e9159e6488ddcd078f5d73b0dafd08082e295cde
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918367"
---
# <a name="bluetooth-support"></a>Compatibilidad con Bluetooth
Windows 10 IoT Core admite Bluetooth 4,0. Puede encontrar una lista de los llaves Bluetooth compatibles en la [lista de compatibilidad de hardware](../learn-about-hardware/HardwareCompatList.md).

## <a name="about-bluetooth"></a>Acerca de Bluetooth
Hay dos tecnologías Bluetooth diferentes que puede elegir implementar en la aplicación:

* Bluetooth clásico (RFCOMM) antes de Bluetooth LE, los dispositivos suelen usar este protocolo para comunicarse con Bluetooth. Este protocolo es simple y de utilidad para la comunicación entre dispositivos sin necesidad de ahorro de energía. La conectividad requiere emparejamiento.

* Bluetooth de baja energía (BLE/LE) Bluetooth de baja energía (LE) es una especificación que define los protocolos para la detección y la comunicación entre los dispositivos que tienen un requisito de uso de energía eficaz. Para obtener más información, incluidos los ejemplos de código, como en el caso de las compilaciones recientes, un dispositivo puede conectarse a un dispositivo BLE sin necesidad de emparejamiento.

## <a name="supported-bluetooth-profiles"></a>Perfiles de Bluetooth compatibles
Windows 10 IoT Core admite los siguientes perfiles de Bluetooth:

1.  **Conceptos de perfiles de HID (HID)** Un dispositivo HID toma la entrada de un usuario y presenta una salida para el concárter humano. Algunos ejemplos son el teclado, el mouse, el dispositivo de juego, el lector de código de barras, el LED y la pantalla alfanumérica. Un dispositivo de Windows 10 IoT Core puede conectarse a un dispositivo HID a través de Bluetooth. Vea el tema general sobre HID en el contexto de Windows: [Introducción a los conceptos de HID](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts). 

2.  **Comunicación por radiofrecuencia (RFCOMM)** RFCOMMM es la comunicación en serie subyacente para el Bluetooth clásico. Con las aplicaciones UWP, se admiten los siguientes servicios RFCOMM:

* serialPort
* obexObjectPush
* obexFileTransfer
* phoneBookAccessPce
* phoneBookAccessPse
* genericFileTransfer

3. **Perfil de atributo genérico (GATT)** Consulte el tema [UWP-Bluetooth de baja energía](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) . 

> [!NOTE]
> Tendrá que especificar manualmente los servicios RFCOMM en el archivo AppManifest.  Consulte el tema [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) . Consulte también el tema [de ejemplo UWP-Bluetooth RFCOMM chat](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) .

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a>Conexión de dispositivos Bluetooth mediante el portal de dispositivos
Cuando se usa una de las imágenes de la [versión de Windows 10 IOT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) , los dispositivos Bluetooth se pueden emparejar con el dispositivo de Windows IOT Core mediante el portal de dispositivos. Al ir a la pestaña Bluetooth, el dispositivo buscará dispositivos Bluetooth y también se podrá detectar en otros dispositivos Bluetooth. En la imagen siguiente se muestra una solicitud de emparejamiento entrante. 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_2.png)

Una vez que el dispositivo se empareja correctamente, se mostrará en la sección dispositivo emparejado. 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_3.png)
