---
title: Compatibilidad con Bluetooth
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo aprovechar Bluetooth para dispositivos que ejecutan Windows 10 IoT Core.
keywords: Windows IOT, Bluetooth, compatibilidad con Bluetooth, dispositivos, portal de dispositivos
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168982"
---
# <a name="bluetooth-support"></a><span data-ttu-id="d42d3-104">Compatibilidad con Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d42d3-104">Bluetooth Support</span></span>
<span data-ttu-id="d42d3-105">Windows 10 IoT Core admite Bluetooth 4,0.</span><span class="sxs-lookup"><span data-stu-id="d42d3-105">Windows 10 IoT Core supports Bluetooth 4.0.</span></span> <span data-ttu-id="d42d3-106">Puede encontrar una lista de los llaves Bluetooth compatibles en la [lista de compatibilidad de hardware](../learn-about-hardware/HardwareCompatList.md).</span><span class="sxs-lookup"><span data-stu-id="d42d3-106">A list of supported Bluetooth dongles can be found in the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span></span>

## <a name="about-bluetooth"></a><span data-ttu-id="d42d3-107">Acerca de Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d42d3-107">About Bluetooth</span></span>
<span data-ttu-id="d42d3-108">Hay dos tecnologías Bluetooth diferentes que puede elegir implementar en la aplicación:</span><span class="sxs-lookup"><span data-stu-id="d42d3-108">There are two different bluetooth technologies that you can choose to implement in your app:</span></span>

* <span data-ttu-id="d42d3-109">Bluetooth clásico (RFCOMM) antes de Bluetooth LE, los dispositivos suelen usar este protocolo para comunicarse con Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="d42d3-109">Classic Bluetooth (RFCOMM) Before Bluetooth LE, devices commonly used this protocol to communicate using Bluetooth.</span></span> <span data-ttu-id="d42d3-110">Este protocolo es simple y de utilidad para la comunicación entre dispositivos sin necesidad de ahorro de energía.</span><span class="sxs-lookup"><span data-stu-id="d42d3-110">This protocol is simple and useful for device-to-device communication without the need of energy savings.</span></span> <span data-ttu-id="d42d3-111">La conectividad requiere emparejamiento.</span><span class="sxs-lookup"><span data-stu-id="d42d3-111">Connectivity requires pairing.</span></span>

* <span data-ttu-id="d42d3-112">Bluetooth de baja energía (BLE/LE) Bluetooth de baja energía (LE) es una especificación que define los protocolos para la detección y la comunicación entre los dispositivos que tienen un requisito de uso de energía eficaz.</span><span class="sxs-lookup"><span data-stu-id="d42d3-112">Bluetooth Low-Energy (BLE/LE) Bluetooth Low Energy (LE) is a specification that defines protocols for discovery and communication between devices that have an efficient energy usage requirement.</span></span> <span data-ttu-id="d42d3-113">Para obtener más información, incluidos los ejemplos de código, como en el caso de las compilaciones recientes, un dispositivo puede conectarse a un dispositivo BLE sin necesidad de emparejamiento.</span><span class="sxs-lookup"><span data-stu-id="d42d3-113">For more information including code samples, As per recent builds, a device can connect to a BLE device without pairing.</span></span>

## <a name="supported-bluetooth-profiles"></a><span data-ttu-id="d42d3-114">Perfiles de Bluetooth compatibles</span><span class="sxs-lookup"><span data-stu-id="d42d3-114">Supported Bluetooth Profiles</span></span>
<span data-ttu-id="d42d3-115">Windows 10 IoT Core admite los siguientes perfiles de Bluetooth:</span><span class="sxs-lookup"><span data-stu-id="d42d3-115">Windows 10 IoT Core supports the following Bluetooth profiles:</span></span>

1.  <span data-ttu-id="d42d3-116">**Conceptos de perfiles de HID (HID)** Un dispositivo HID toma la entrada de un usuario y presenta una salida para el concárter humano.</span><span class="sxs-lookup"><span data-stu-id="d42d3-116">**Human Interface Device Profiles Concepts (HID)** An HID device takes input from a human and presents output for human consumpation.</span></span> <span data-ttu-id="d42d3-117">Algunos ejemplos son el teclado, el mouse, el dispositivo de juego, el lector de código de barras, el LED y la pantalla alfanumérica.</span><span class="sxs-lookup"><span data-stu-id="d42d3-117">Examples are keyboard, mouse, game controller, barcode reader, LED, and alphanumeric display.</span></span> <span data-ttu-id="d42d3-118">Un dispositivo de Windows 10 IoT Core puede conectarse a un dispositivo HID a través de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="d42d3-118">A Windows 10 IoT Core device can connect to an HID device over Bluetooth.</span></span> <span data-ttu-id="d42d3-119">Vea el tema general sobre HID en el contexto de Windows: [Introducción a los conceptos de HID](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span><span class="sxs-lookup"><span data-stu-id="d42d3-119">See the general topic about HID in the Windows context: [Introduction to HID Concepts](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span></span> 

2.  <span data-ttu-id="d42d3-120">**Comunicación por radiofrecuencia (RFCOMM)** RFCOMMM es la comunicación en serie subyacente para el Bluetooth clásico.</span><span class="sxs-lookup"><span data-stu-id="d42d3-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM is the underlying serial communications for Classic Bluetooth.</span></span> <span data-ttu-id="d42d3-121">Con las aplicaciones UWP, se admiten los siguientes servicios RFCOMM:</span><span class="sxs-lookup"><span data-stu-id="d42d3-121">With UWP apps, the following RFCOMM services are supported:</span></span>

* <span data-ttu-id="d42d3-122">serialPort</span><span class="sxs-lookup"><span data-stu-id="d42d3-122">serialPort</span></span>
* <span data-ttu-id="d42d3-123">obexObjectPush</span><span class="sxs-lookup"><span data-stu-id="d42d3-123">obexObjectPush</span></span>
* <span data-ttu-id="d42d3-124">obexFileTransfer</span><span class="sxs-lookup"><span data-stu-id="d42d3-124">obexFileTransfer</span></span>
* <span data-ttu-id="d42d3-125">phoneBookAccessPce</span><span class="sxs-lookup"><span data-stu-id="d42d3-125">phoneBookAccessPce</span></span>
* <span data-ttu-id="d42d3-126">phoneBookAccessPse</span><span class="sxs-lookup"><span data-stu-id="d42d3-126">phoneBookAccessPse</span></span>
* <span data-ttu-id="d42d3-127">genericFileTransfer</span><span class="sxs-lookup"><span data-stu-id="d42d3-127">genericFileTransfer</span></span>

3. <span data-ttu-id="d42d3-128">**Perfil de atributo genérico (GATT)** Consulte el tema [UWP-Bluetooth de baja energía](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) .</span><span class="sxs-lookup"><span data-stu-id="d42d3-128">**Generic Attribute Profile (GATT)** See the [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) topic.</span></span> 

> [!NOTE]
> <span data-ttu-id="d42d3-129">Tendrá que especificar manualmente los servicios RFCOMM en el archivo AppManifest.</span><span class="sxs-lookup"><span data-stu-id="d42d3-129">You will need to manually specify the RFCOMM services in the AppManifest.</span></span>  <span data-ttu-id="d42d3-130">Consulte el tema [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) .</span><span class="sxs-lookup"><span data-stu-id="d42d3-130">See the [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) topic.</span></span> <span data-ttu-id="d42d3-131">Consulte también el tema [de ejemplo UWP-Bluetooth RFCOMM chat](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) .</span><span class="sxs-lookup"><span data-stu-id="d42d3-131">Also see the [UWP-Bluetooth Rfcomm Chat Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) topic.</span></span>

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a><span data-ttu-id="d42d3-132">Conexión de dispositivos Bluetooth mediante el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="d42d3-132">Connecting Bluetooth devices using the device portal</span></span>
<span data-ttu-id="d42d3-133">Cuando se usa una de las imágenes de la [versión de Windows 10 IOT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) , los dispositivos Bluetooth se pueden emparejar con el dispositivo de Windows IOT Core mediante el portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d42d3-133">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth devices can be paired with the Windows IoT Core device using the device portal.</span></span> <span data-ttu-id="d42d3-134">Al ir a la pestaña Bluetooth, el dispositivo buscará dispositivos Bluetooth y también se podrá detectar en otros dispositivos Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="d42d3-134">When navigating to the Bluetooth tab the device will look for Bluetooth devices and will also be discoverable to other Bluetooth devices.</span></span> <span data-ttu-id="d42d3-135">En la imagen siguiente se muestra una solicitud de emparejamiento entrante.</span><span class="sxs-lookup"><span data-stu-id="d42d3-135">The picture below shows an incoming pairing request.</span></span> 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_2.png)

<span data-ttu-id="d42d3-137">Una vez que el dispositivo se empareja correctamente, se mostrará en la sección dispositivo emparejado.</span><span class="sxs-lookup"><span data-stu-id="d42d3-137">After the device is successfully paired it will be listed under the paired device section</span></span> 

![Emparejamiento de entrada de Bluetooth](../media/Bluetooth/Portal_BT_3.png)
