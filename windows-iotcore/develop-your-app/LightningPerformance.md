---
title: Pruebas de rendimiento de Lightning
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de la funcionalidad de Windows IoT Lightning y la frecuencia de alternancia para diferentes plataformas y lenguajes.
keywords: Windows IOT, Lightning rendimiento, funcionalidad de Lightning, GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744779"
---
# <a name="windows-iot-lightning-performance-testing"></a>Pruebas de rendimiento de Windows IoT Lightning

> [!IMPORTANT]
> El equipo de IoT de Windows 10 ya no admite activamente Arduino.

El rendimiento de GPIO se probó para la funcionalidad de Windows IoT Lightning mediante una sencilla aplicación de alternancia de GPIO, [disponible aquí](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite). Las pruebas se realizaron alternando el GPIO 5 entre 0 y 1 a la velocidad más rápida posible. La frecuencia de alternancia para cada caso se midió con un osciloscopio de Tektronix TPS 2024.

Los siguientes resultados se obtuvieron del análisis:

> | Plataforma probada                     | Lenguaje        | Frecuencia     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino uno                         | Boceto de Arduino  | 75,06 kHz     |
> | Pila nativa de Windows 10 IoT Core    | C#              | 239 KHz       |
> | Pila nativa de Windows 10 IoT Core    | C++/CX          | 278 kHz       |
> | Pila nativa de Windows 10 IoT Core    | WinJS           | 34 kHz        |
> | Cableado de Windows 10 IoT Core Arduino  | Cableado de Arduino  | **7,36 MHz**  |
> | Pila DMAP de Windows 10 IoT Core      | C#              | **1,76 MHz**  |
> | Pila DMAP de Windows 10 IoT Core      | C++/CX          | **3,78 MHz**  |
> | Pila DMAP de Windows 10 IoT Core      | WinJS           | 42 kHz        |

Las pruebas de Windows 10 IoT Core se ejecutaban en un Raspberry PI 3 con Windows 10 IoT Core Insider versión preliminar 15026 (nombre del código Redstone 2) y se crearon con Microsoft IoT Lightning SDK 1.1.0.
