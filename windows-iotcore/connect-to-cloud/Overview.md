---
title: Información general de IoT en la nube
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre mensajería, seguridad y administración de dispositivos con la nube mediante Azure IoT.
keywords: Windows IOT, nube, Azure, Azure IoT Hub, mensajería, UWP, Plataforma universal de Windows
ms.openlocfilehash: 14a8804025cea507574efef6a0512827333faff5
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918374"
---
# <a name="overview-of-iot-on-the-cloud"></a><span data-ttu-id="4f383-104">Información general de IoT en la nube</span><span class="sxs-lookup"><span data-stu-id="4f383-104">Overview of IoT on the Cloud</span></span>

<span data-ttu-id="4f383-105">El Internet de las cosas se basa en la informática en la nube.</span><span class="sxs-lookup"><span data-stu-id="4f383-105">The Internet of Things is built on cloud computing.</span></span> <span data-ttu-id="4f383-106">La capacidad de comunicarse con la nube y obtener información de los datos es una parte esencial de cualquier proyecto de IoT.</span><span class="sxs-lookup"><span data-stu-id="4f383-106">The ability to communicate with the cloud and derive insight from the data is an essential part of any IoT project.</span></span>

## <a name="messaging"></a><span data-ttu-id="4f383-107">Mensajes</span><span class="sxs-lookup"><span data-stu-id="4f383-107">Messaging</span></span>

<span data-ttu-id="4f383-108">Normalmente, los dispositivos de IoT se comunican con la nube o entre sí mediante el envío y la recepción de mensajes.</span><span class="sxs-lookup"><span data-stu-id="4f383-108">Usually, IoT devices communicate with the cloud or each other by sending and receiving messages.</span></span> <span data-ttu-id="4f383-109">La carga de un mensaje enviado desde el dispositivo a la nube puede ser tan pequeña como un valor de un sensor y tan grande como un archivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="4f383-109">The payload of a message sent from the device to cloud can be as small as a value from a sensor and as big as a video file.</span></span> <span data-ttu-id="4f383-110">Un mensaje de nube a dispositivo suele ser un comando que indica al dispositivo que realice una acción.</span><span class="sxs-lookup"><span data-stu-id="4f383-110">A cloud to device message is typically a command instructing the device to perform an action.</span></span>


<span data-ttu-id="4f383-111">Los patrones de comunicación de paso de mensajes varían en complejidad, desde mensajes unidireccionales simples hasta protocolos más complejos como los protocolos de solicitud-respuesta o transaccionales, como la confirmación en dos fases.</span><span class="sxs-lookup"><span data-stu-id="4f383-111">Message-passing communication patterns vary in complexity ranging from simple one-way messaging to more complex protocols such as request-response or transactional protocols such as the two-phase commit.</span></span>

## <a name="security"></a><span data-ttu-id="4f383-112">Seguridad</span><span class="sxs-lookup"><span data-stu-id="4f383-112">Security</span></span>

<span data-ttu-id="4f383-113">La seguridad es una parte esencial de IoT.</span><span class="sxs-lookup"><span data-stu-id="4f383-113">Security is an essential part of IoT.</span></span> <span data-ttu-id="4f383-114">Para cada mensaje, debemos asegurarnos de que procede de un dispositivo de confianza (o es recibido por él) y no se ha alterado.</span><span class="sxs-lookup"><span data-stu-id="4f383-114">For each message, we must ensure that it comes from (or is received by) a trusted device and is not tampered with.</span></span> <span data-ttu-id="4f383-115">Los datos pueden contener información que se debe cifrar.</span><span class="sxs-lookup"><span data-stu-id="4f383-115">The data can contain information that must be encrypted.</span></span>

## <a name="azure-iot-hub"></a><span data-ttu-id="4f383-116">Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="4f383-116">Azure IoT Hub</span></span>

<span data-ttu-id="4f383-117">[Azure IOT Hub](https://azure.microsoft.com/services/iot-hub/) es un servicio en la nube de Azure que ofrece mensajería de dispositivo a nube y de nube a dispositivo confiable y segura que se escala a millones de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4f383-117">[Azure IoT Hub](https://azure.microsoft.com/services/iot-hub/) is an Azure cloud service that offers reliable and secure device-to-cloud and cloud-to-device messaging that scales to millions of devices.</span></span> <span data-ttu-id="4f383-118">Ofrece un modelo de programación simplificado que le permite empezar a trabajar con el mínimo esfuerzo y escalar verticalmente la solución a medida que crezcan sus necesidades.</span><span class="sxs-lookup"><span data-stu-id="4f383-118">It offers a streamlined programming model that lets you get started with minimum effort and scale up your solution as its needs grow.</span></span>

