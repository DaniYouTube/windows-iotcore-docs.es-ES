---
title: Información general de IoT en la nube
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de la mensajería, seguridad y administración de dispositivos con la nube con IoT de Azure.
keywords: Windows iot, en la nube, Azure, Azure IoT Hub, mensajería, UWP, plataforma Universal de Windows
ms.openlocfilehash: 4f38a45836e7c474655819988e447137249c2a7f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514883"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="70b00-104">Información general de IoT en la nube</span><span class="sxs-lookup"><span data-stu-id="70b00-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="70b00-105">Internet de las cosas se basa en la nube de informática.</span><span class="sxs-lookup"><span data-stu-id="70b00-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="70b00-106">La capacidad de comunicarse con la nube y entendimiento de los datos es una parte esencial de cualquier proyecto de IoT.</span><span class="sxs-lookup"><span data-stu-id="70b00-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="70b00-107">Mensajería</span><span class="sxs-lookup"><span data-stu-id="70b00-107">Messaging</span></span>

<span data-ttu-id="70b00-108">Por lo general, dispositivos de IoT se comunican con la nube o entre sí enviando y recibiendo mensajes.</span><span class="sxs-lookup"><span data-stu-id="70b00-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="70b00-109">La carga de un mensaje enviado desde el dispositivo a la nube puede ser tan pequeña como un valor de un sensor y tan grande como un archivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="70b00-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="70b00-110">Una nube para el mensaje de dispositivo suele ser un comando del dispositivo para realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="70b00-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="70b00-111">Patrones de comunicación de paso de mensajes varían en complejidad que abarcan desde mensajería unidireccional simple protocolos más complejas, como solicitud-respuesta o protocolos transaccionales como la confirmación en dos fases.</span><span class="sxs-lookup"><span data-stu-id="70b00-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="70b00-112">Seguridad</span><span class="sxs-lookup"><span data-stu-id="70b00-112">Security</span></span>

<span data-ttu-id="70b00-113">Seguridad es una parte esencial de IoT.</span><span class="sxs-lookup"><span data-stu-id="70b00-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="70b00-114">Para cada mensaje, debemos asegurarnos de que proviene de (o se recibe en) un dispositivo de confianza y no se haya alterado.</span><span class="sxs-lookup"><span data-stu-id="70b00-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="70b00-115">Los datos pueden contener información que se debe cifrar.</span><span class="sxs-lookup"><span data-stu-id="70b00-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="70b00-116">Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="70b00-116">Azure IoT Hub</span></span>

<span data-ttu-id="70b00-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) es un servicio de nube de Azure que ofrece confiable y segura dispositivo a nube y en la nube a dispositivo de mensajería que se puede escalar a millones de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="70b00-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="70b00-118">Ofrece un modelo de programación simplificado que le permite empezar a trabajar con un esfuerzo mínimo y escalar verticalmente la solución a medida que crecen sus necesidades.</span><span class="sxs-lookup"><span data-stu-id="70b00-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>

