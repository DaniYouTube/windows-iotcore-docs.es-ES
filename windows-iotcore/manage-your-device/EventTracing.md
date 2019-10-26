---
title: Seguimiento de eventos para Windows IoT Core
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar el seguimiento de eventos para escribir eventos y consumir eventos para Windows IoT Core.
keywords: Windows IOT, seguimiento de eventos, ETW, seguimiento de eventos para Windows, dispositivos
ms.openlocfilehash: ce031cd2bc7b94f01c970bec9e1ad4df0b9dbf06
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917260"
---
# <a name="event-tracing-for-windows-iot-core"></a>Seguimiento de eventos para Windows IoT Core

Seguimiento de eventos para Windows (ETW) proporciona a los desarrolladores la capacidad de iniciar y detener sesiones de seguimiento de eventos, instrumentar una aplicación para proporcionar eventos de seguimiento y consumir eventos de seguimiento.
ETW en dispositivos Windows IoT Core es compatible con eventos clásicos y basados en manifiestos, y no es diferente de otros dispositivos Windows 10.

En esta sección se proporcionan vínculos útiles sobre los aspectos básicos de la escritura y el consumo de eventos. Busque información más detallada en la [Página de seguimiento de eventos de Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).

## <a name="writing-events"></a>Escribir eventos

Busque un ejemplo de UWP que implemente los distintos métodos para escribir eventos como parte de los [ejemplos de Windows universal de github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).
Esto se ejecutará en dispositivos Windows IoT Core y también es una excelente referencia de código.

Puede encontrar una guía detallada sobre la escritura de eventos y la obtención de GUID [aquí](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).

## <a name="consuming-events"></a>Consumir eventos

Los eventos se guardan en un archivo ETL o se capturan en tiempo real.
Use [FTP](../connect-your-device/FTP.md) o el [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md) para recuperar archivos ETL desde dispositivos Windows IOT Core.

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a>Usar herramientas en Windows Assessment and Deployment Kit

Windows Assessment and Deployment Kit incluye 3 herramientas para ayudar a capturar y analizar eventos. [Haga clic aquí para descargar](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. El **analizador de rendimiento de Windows** visualiza archivos ETL en el escritorio, con una guía paso a paso [aquí](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).

2. La **herramienta de línea de comandos Xperf** captura eventos en tiempo real y los escribe en un archivo ETL. Esta herramienta ya está instalada en los dispositivos Windows IoT Core, solo tiene que ejecutar los siguientes comandos en los dispositivos:

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. **Tracerpt la herramienta de línea de comandos** convierte los archivos ETL en archivos XML.

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a>Uso del portal de dispositivos

El portal de dispositivos puede capturar eventos en tiempo real, con instrucciones [aquí](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).

> [!NOTE]
> Este método no genera un archivo ETL para su posterior análisis, pero requiere una configuración mínima.

## <a name="use-function-calls"></a>Usar llamadas a función

Permite que una aplicación consuma eventos de un archivo ETL o en tiempo real mediante llamadas a funciones.
Aprenda a usar estas funciones [aquí](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).
