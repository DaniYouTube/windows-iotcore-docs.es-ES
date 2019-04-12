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
# <a name="bluetooth-support"></a><span data-ttu-id="7f192-104">Compatibilidad con Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7f192-104">Bluetooth Support</span></span>
<span data-ttu-id="7f192-105">Windows 10 IoT Core es compatible con Bluetooth 4.0.</span><span class="sxs-lookup"><span data-stu-id="7f192-105">Windows 10 IoT Core supports Bluetooth 4.0.</span></span> <span data-ttu-id="7f192-106">Encontrará una lista de dispositivos de protección admitidos de Bluetooth en el [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span><span class="sxs-lookup"><span data-stu-id="7f192-106">A list of supported Bluetooth dongles can be found in the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span></span>

## <a name="about-bluetooth"></a><span data-ttu-id="7f192-107">Acerca de Bluetooth</span><span class="sxs-lookup"><span data-stu-id="7f192-107">About Bluetooth</span></span>
<span data-ttu-id="7f192-108">Existen dos tecnologías bluetooth diferentes que puede implementar en su aplicación:</span><span class="sxs-lookup"><span data-stu-id="7f192-108">There are two different bluetooth technologies that you can choose to implement in your app:</span></span>

* <span data-ttu-id="7f192-109">Clásico Bluetooth (RFCOMM) antes de Bluetooth LE, los dispositivos usan normalmente este protocolo para comunicarse con Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="7f192-109">Classic Bluetooth (RFCOMM) Before Bluetooth LE, devices commonly used this protocol to communicate using Bluetooth.</span></span> <span data-ttu-id="7f192-110">Este protocolo es simple y de utilidad para la comunicación entre dispositivos sin necesidad de ahorro de energía.</span><span class="sxs-lookup"><span data-stu-id="7f192-110">This protocol is simple and useful for device-to-device communication without the need of energy savings.</span></span> <span data-ttu-id="7f192-111">Conectividad requiere el emparejamiento.</span><span class="sxs-lookup"><span data-stu-id="7f192-111">Connectivity requires pairing.</span></span>

* <span data-ttu-id="7f192-112">Bluetooth de baja energía (BLE/LE) Bluetooth baja energía (LE) es una especificación que define los protocolos para la detección y comunicación entre los dispositivos que tienen un requisito de uso de ahorro de energía.</span><span class="sxs-lookup"><span data-stu-id="7f192-112">Bluetooth Low-Energy (BLE/LE) Bluetooth Low Energy (LE) is a specification that defines protocols for discovery and communication between devices that have an efficient energy usage requirement.</span></span> <span data-ttu-id="7f192-113">Para obtener más información, incluidos ejemplos de código, según las últimas compilaciones, un dispositivo puede conectarse a un dispositivo BLE sin emparejamiento.</span><span class="sxs-lookup"><span data-stu-id="7f192-113">For more information including code samples, As per recent builds, a device can connect to a BLE device without pairing.</span></span>

## <a name="supported-bluetooth-profiles"></a><span data-ttu-id="7f192-114">Perfiles de Bluetooth compatibles</span><span class="sxs-lookup"><span data-stu-id="7f192-114">Supported Bluetooth Profiles</span></span>
<span data-ttu-id="7f192-115">Windows 10 IoT Core es compatible con los siguientes perfiles de Bluetooth:</span><span class="sxs-lookup"><span data-stu-id="7f192-115">Windows 10 IoT Core supports the following Bluetooth profiles:</span></span>

1.  <span data-ttu-id="7f192-116">**Conceptos de perfiles de dispositivo de interfaz humana (HID)** HID de un dispositivo toma la entrada de una persona y presenta la salida para consumpation humano.</span><span class="sxs-lookup"><span data-stu-id="7f192-116">**Human Interface Device Profiles Concepts (HID)** An HID device takes input from a human and presents output for human consumpation.</span></span> <span data-ttu-id="7f192-117">Algunos ejemplos son el teclado, mouse, dispositivo de juego, lector de código de barras, LED y presentación alfanumérica.</span><span class="sxs-lookup"><span data-stu-id="7f192-117">Examples are keyboard, mouse, game controller, barcode reader, LED, and alphanumeric display.</span></span> <span data-ttu-id="7f192-118">Un dispositivo Windows 10 IoT Core puede conectarse a un dispositivo HID a través de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="7f192-118">A Windows 10 IoT Core device can connect to an HID device over Bluetooth.</span></span> <span data-ttu-id="7f192-119">Vea el tema acerca de HID general en el contexto de Windows: [Introducción a los conceptos HID](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span><span class="sxs-lookup"><span data-stu-id="7f192-119">See the general topic about HID in the Windows context: [Introduction to HID Concepts](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span></span> 

2.  <span data-ttu-id="7f192-120">**Comunicación por radiofrecuencia (RFCOMM)** RFCOMMM es las comunicaciones en serie subyacentes Bluetooth clásico.</span><span class="sxs-lookup"><span data-stu-id="7f192-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM is the underlying serial communications for Classic Bluetooth.</span></span> <span data-ttu-id="7f192-121">Las aplicaciones para UWP, se admiten los siguientes servicios RFCOMM:</span><span class="sxs-lookup"><span data-stu-id="7f192-121">With UWP apps, the following RFCOMM services are supported:</span></span>

* <span data-ttu-id="7f192-122">serialPort</span><span class="sxs-lookup"><span data-stu-id="7f192-122">serialPort</span></span>
* <span data-ttu-id="7f192-123">obexObjectPush</span><span class="sxs-lookup"><span data-stu-id="7f192-123">obexObjectPush</span></span>
* <span data-ttu-id="7f192-124">obexFileTransfer</span><span class="sxs-lookup"><span data-stu-id="7f192-124">obexFileTransfer</span></span>
* <span data-ttu-id="7f192-125">phoneBookAccessPce</span><span class="sxs-lookup"><span data-stu-id="7f192-125">phoneBookAccessPce</span></span>
* <span data-ttu-id="7f192-126">phoneBookAccessPse</span><span class="sxs-lookup"><span data-stu-id="7f192-126">phoneBookAccessPse</span></span>
* <span data-ttu-id="7f192-127">genericFileTransfer</span><span class="sxs-lookup"><span data-stu-id="7f192-127">genericFileTransfer</span></span>

3. <span data-ttu-id="7f192-128">**Perfil de atributo genéricos (GATT)** vea el [UWP Bluetooth baja energía](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) tema.</span><span class="sxs-lookup"><span data-stu-id="7f192-128">**Generic Attribute Profile (GATT)** See the [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) topic.</span></span> 

> [!NOTE]
> <span data-ttu-id="7f192-129">Deberá especificar manualmente los servicios RFCOMM en el AppManifest.</span><span class="sxs-lookup"><span data-stu-id="7f192-129">You will need to manually specify the RFCOMM services in the AppManifest.</span></span>  <span data-ttu-id="7f192-130">Consulte la [UWP Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) tema.</span><span class="sxs-lookup"><span data-stu-id="7f192-130">See the [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) topic.</span></span> <span data-ttu-id="7f192-131">Consulte también el [ejemplo de Chat de UWP Bluetooth Rfcomm](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) tema.</span><span class="sxs-lookup"><span data-stu-id="7f192-131">Also see the [UWP-Bluetooth Rfcomm Chat Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) topic.</span></span>

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a><span data-ttu-id="7f192-132">Conectar dispositivos Bluetooth mediante device portal</span><span class="sxs-lookup"><span data-stu-id="7f192-132">Connecting Bluetooth devices using the device portal</span></span>
<span data-ttu-id="7f192-133">Al utilizar uno de los [imagen de lanzamiento de Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) dispositivos Bluetooth pueden emparejarse con el dispositivo Windows IoT Core mediante el portal de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7f192-133">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth devices can be paired with the Windows IoT Core device using the device portal.</span></span> <span data-ttu-id="7f192-134">Al navegar a la pestaña de Bluetooth del dispositivo va a buscar dispositivos Bluetooth y también será reconocible para otros dispositivos Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="7f192-134">When navigating to the Bluetooth tab the device will look for Bluetooth devices and will also be discoverable to other Bluetooth devices.</span></span> <span data-ttu-id="7f192-135">La siguiente imagen muestra una solicitud entrante de emparejamiento.</span><span class="sxs-lookup"><span data-stu-id="7f192-135">The picture below shows an incoming pairing request.</span></span> 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_2.png)

<span data-ttu-id="7f192-137">Después de que el dispositivo se empareja correctamente, aparecerá en la sección de dispositivo emparejado</span><span class="sxs-lookup"><span data-stu-id="7f192-137">After the device is successfully paired it will be listed under the paired device section</span></span> 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_3.png)
