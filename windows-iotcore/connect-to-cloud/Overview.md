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
# <a name="overview-of-iot-on-the-cloud"></a>Información general de IoT en la nube

El Internet de las cosas se basa en la informática en la nube. La capacidad de comunicarse con la nube y obtener información de los datos es una parte esencial de cualquier proyecto de IoT.

## <a name="messaging"></a>Mensajes

Normalmente, los dispositivos de IoT se comunican con la nube o entre sí mediante el envío y la recepción de mensajes. La carga de un mensaje enviado desde el dispositivo a la nube puede ser tan pequeña como un valor de un sensor y tan grande como un archivo de vídeo. Un mensaje de nube a dispositivo suele ser un comando que indica al dispositivo que realice una acción.


Los patrones de comunicación de paso de mensajes varían en complejidad, desde mensajes unidireccionales simples hasta protocolos más complejos como los protocolos de solicitud-respuesta o transaccionales, como la confirmación en dos fases.

## <a name="security"></a>Seguridad

La seguridad es una parte esencial de IoT. Para cada mensaje, debemos asegurarnos de que procede de un dispositivo de confianza (o es recibido por él) y no se ha alterado. Los datos pueden contener información que se debe cifrar.

## <a name="azure-iot-hub"></a>Azure IoT Hub

[Azure IOT Hub](https://azure.microsoft.com/services/iot-hub/) es un servicio en la nube de Azure que ofrece mensajería de dispositivo a nube y de nube a dispositivo confiable y segura que se escala a millones de dispositivos. Ofrece un modelo de programación simplificado que le permite empezar a trabajar con el mínimo esfuerzo y escalar verticalmente la solución a medida que crezcan sus necesidades.

