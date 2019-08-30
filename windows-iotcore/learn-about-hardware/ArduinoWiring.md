---
title: Cableado Arduino para dispositivos Windows IoT Core
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: Obtenga información sobre cómo crear, implementar y depurar bocetos de cableado de Arduino en dispositivos Windows IoT Core compatibles.
keywords: Windows IOT, Arduino, Arduino de conexión, plantilla, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744797"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>Cableado Arduino para dispositivos Windows IoT Core

> [!IMPORTANT]
> El equipo de IoT de Windows 10 ya no mantiene de forma activa Arduino.

Para permitir el desarrollo y reutilización de los bocetos de [cableado de Arduino](https://www.arduino.cc/en/Reference/HomePage) conocidos en los dispositivos IOT Core, se proporciona una plantilla de proyecto de Visual Studio para el cableado Arduino como parte de la extensión de plantillas de [proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472).

La plantilla de proyecto de cableado de Arduino permite a los desarrolladores y a los desarrolladores crear, implementar y depurar bocetos de cableado de Arduino en dispositivos IoT Core compatibles con la misma semántica de lenguaje de cableado Arduino y construcciones disponibles en plataformas Arduino. No solo esto puede ayudarle a migrar bocetos de Arduino existentes a IoT Core con muy poco costo, pero los bocetos de cableado de Arduino que se ejecutan en IoT Core son aplicaciones completas de Windows 10 que pueden hacer uso de la API de la plataforma universal de Windows (UWP). Por lo tanto, los bocetos de cableado de Arduino tienen acceso total a las API como la comunicación, el acceso a datos, las redes, los gráficos, entre muchos otros, que se pueden usar para crear escenarios de un extremo a otro que se ejecuten en dispositivos de IoT Core de Windows 10. Para obtener más información sobre el desarrollo de aplicaciones Plataforma universal de Windows (UWP), consulte [creación de aplicaciones para Windows 10 IOT Core](../develop-your-app/BuildingAppsForIoTCore.md).

Además, los bocetos de cableado de Arduino hacen uso de un controlador asignado a memoria directo que ofrece un alto rendimiento en los dispositivos compatibles. Para obtener más información sobre los detalles de rendimiento, consulte el informe de [pruebas de rendimiento de Windows IOT Lightning](../develop-your-app/LightningPerformance.md) .

Para empezar a crear proyectos de cableado de Arduino para Raspberry pi2, Pi3 o Minnowboard Max, consulte la [Guía de proyecto de cableado de Arduino](ArduinoWiringProjectGuide.md).

> [!NOTE]
> El cableado Arduino *no* se admite actualmente en DragonBoard 410C.
