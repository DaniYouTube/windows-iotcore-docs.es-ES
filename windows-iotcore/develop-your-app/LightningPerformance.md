---
title: Suma de las pruebas de rendimiento
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la frecuencia de funcionalidad y activar o desactivar Windows IoT relámpago para diferentes plataformas y lenguajes.
keywords: Windows iot, rendimiento increíblemente, funcionalidad relámpago GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744779"
---
# <a name="windows-iot-lightning-performance-testing"></a>Suma de las pruebas de rendimiento de IoT de Windows

> [!IMPORTANT]
> El equipo de Windows 10 IoT activamente ya no es compatible con Arduino.

Se ha probado el rendimiento de GPIO para la funcionalidad de Windows IoT relámpago mediante una aplicación sencilla de alternancia GPIO, [disponible aquí](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite). Las pruebas se realizaron alternando GPIO 5 entre 0 y 1 a la mayor velocidad posible. La frecuencia de alternancia para cada caso se midió mediante un osciloscopio de 2024 Tektronix TPS.

Los siguientes resultados obtenidos del análisis:

> | Plataforma de prueba                     | Lenguaje        | Frecuencia     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Boceto de Arduino  | 75.06 kHz     |
> | Pila nativa de Windows 10 IoT Core    | C#              | 239 KHz       |
> | Pila nativa de Windows 10 IoT Core    | C++/CX          | 278 kHz       |
> | Pila nativa de Windows 10 IoT Core    | WinJS           | 34 kHz        |
> | Conexión de Arduino de Windows 10 IoT Core  | Conexión de Arduino  | **7,36 MHz**  |
> | Pila de Windows 10 IoT Core DMAP      | C#              | **1.76 MHz**  |
> | Pila de Windows 10 IoT Core DMAP      | C++/CX          | **3.78 MHz**  |
> | Pila de Windows 10 IoT Core DMAP      | WinJS           | 42 kHz        |

Las pruebas de Windows 10 IoT Core estaban ejecutar en un Raspberry Pi 3 con Windows 10 IoT Core Insider Preview compilar 15026 (nombre código piedra rojiza 2) y creadas con Microsoft IoT relámpago SDK 1.1.0.
