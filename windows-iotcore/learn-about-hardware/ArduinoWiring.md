---
title: Conexión de Arduino para dispositivos de Windows IoT Core
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: Aprenda a crear, implementar y depurar el cableado Arduino dibujos en los dispositivos compatibles de Windows IoT Core.
keywords: Windows iot, Arduino, Arduino cableado, plantilla, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744797"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a>Conexión de Arduino para dispositivos de Windows IoT Core

> [!IMPORTANT]
> El equipo de Windows 10 IoT activamente ya no es mantener Arduino.

Para habilitar el desarrollo y la reutilización de la conocida [Arduino cableado](https://www.arduino.cc/en/Reference/HomePage) dibujos en los dispositivos de IoT Core, una plantilla de proyecto de Visual Studio para la conexión de Arduino se proporciona como parte de la [plantillas de proyecto de Windows IoT Core extensión](https://go.microsoft.com/fwlink/?linkid=847472).

La plantilla de proyecto de cableado Arduino permite a los desarrolladores y responsables de crear, implementar y depurar bocetos de conexión de Arduino en dispositivos IoT Core compatibles con la misma semántica de lenguaje de conexión de Arduino y construye disponible en las plataformas de Arduino. No solo Esto puede ayudar bocetos de puerto existentes Arduino a IoT Core con un costo muy pequeño, pero bocetos de Arduino de cableado que se ejecutan en IoT Core son aplicaciones de Windows 10 completas que pueden hacer uso de la API de plataforma de Windows de universal (UWP). Por lo tanto, Arduino cableado bocetos tienen acceso total a las API, como la comunicación, acceso a datos, redes, gráficos, entre muchas otras cosas, que se puede usar para crear escenarios de extremo a extremo que se ejecutan en dispositivos Windows 10 IoT Core. Para obtener más información sobre el desarrollo de aplicaciones de Universal Windows Platform (UWP), consulte [compilar aplicaciones para Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).

Además, usar Arduino cableado hacer bocetos de controlador asignado memoria directa que ofrece un alto rendimiento en los dispositivos compatibles. Para obtener más detalles sobre los detalles de rendimiento, consulte el [pruebas de rendimiento de Windows IoT relámpago](../develop-your-app/LightningPerformance.md) informes.

Para empezar a crear proyectos de conexión de Arduino para Raspberry Pi2, Pi3 o Minnowboard Max, consulte el [Guía de proyecto de cableado Arduino](ArduinoWiringProjectGuide.md).

> [!NOTE]
> Conexión de Arduino es *no* admite actualmente en DragonBoard 410 c.
