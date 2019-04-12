---
title: Seguimiento de eventos para Windows IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo utilizar el seguimiento de eventos para escribir los eventos y consumir eventos de Windows IoT Core.
keywords: Windows iot, seguimiento de eventos de seguimiento, ETW, event para dispositivos windows
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515192"
---
# <a name="event-tracing-for-windows-iot-core"></a>Seguimiento de eventos para Windows IoT Core

Seguimiento de eventos para Windows (ETW) proporciona a los desarrolladores la capacidad de iniciar y detener las sesiones de seguimiento de eventos, instrumentar una aplicación para proporcionar eventos de seguimiento y consumir eventos de seguimiento.
ETW en dispositivos de Windows IoT Core admite eventos basada en manifiestos y clásicos y no es diferente a otros dispositivos Windows 10.

Esta sección proporciona vínculos útiles sobre los conceptos básicos de escritura y consumo de eventos. Buscar la información más detallada de la [página seguimiento de eventos de Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).

## <a name="writing-events"></a>Eventos de escritura

Buscar una UWP de ejemplo que implementa los distintos métodos de escritura de eventos como parte de la [Github de Windows Universal Samples](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).
Esto se ejecutará en dispositivos de Windows IoT Core y también es una referencia de código de gran calidad.

Guía detallada sobre la escritura de eventos y obtener el GUID puede encontrarse [aquí](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).

## <a name="consuming-events"></a>Consumo de eventos

Los eventos se guardan en un archivo ETL o capturados en tiempo real.
Use [FTP](../connect-your-device/FTP.md) o [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md) para recuperar los archivos ETL de dispositivos de Windows IoT Core.

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>Usar herramientas en Windows Assessment and Deployment Kit

Windows Assessment and Deployment Kit incluye 3 herramientas para ayudar a capturar y analizar eventos. [Haga clic aquí para descargar](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. **Windows Performance Analyzer** visualiza los archivos ETL en escritorio, con una guía paso a paso [aquí](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).

2. **Herramienta de línea de comandos Xperf** captura los eventos en tiempo real y los escribe en un archivo ETL. Esta herramienta ya está instalada en los dispositivos de Windows IoT Core, simplemente ejecute los siguientes comandos en los dispositivos:

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Herramienta de línea de comandos tracerpt** convierte los archivos ETL en archivos xml.

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>Use el Portal de dispositivo

Portal de dispositivos puede capturar los eventos en tiempo real, con instrucciones [aquí](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).

> [!NOTE]
> Este método no genera un archivo ETL para su posterior análisis, pero requiere una configuración mínima.

## <a name="use-function-calls"></a>Usar llamadas de función

Habilita una aplicación para consumir eventos desde un archivo ETL o en tiempo real mediante llamadas a la función.
Aprenda a usar estas funciones [aquí](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).
