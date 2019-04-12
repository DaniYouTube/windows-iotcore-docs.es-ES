---
title: Suma de las pruebas de rendimiento
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la frecuencia de funcionalidad y activar o desactivar Windows IoT relámpago para diferentes plataformas y lenguajes.
keywords: Windows iot, rendimiento increíblemente, funcionalidad relámpago GPIO
ms.openlocfilehash: 65f6732dd945b199902bb7eb4a9e0cc41aac2131
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514895"
---
# <a name="windows-iot-lightning-performance-testing"></a>Suma de las pruebas de rendimiento de IoT de Windows

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
> | Pila de Windows 10 IoT Core DMAP      | C++/CX          | **Representa el 3,78 MHz**  |
> | Pila de Windows 10 IoT Core DMAP      | WinJS           | 42 kHz        |

Las pruebas de Windows 10 IoT Core estaban ejecutar en un Raspberry Pi 3 con Windows 10 IoT Core Insider Preview compilar 15026 (nombre código piedra rojiza 2) y creadas con Microsoft IoT relámpago SDK 1.1.0.
