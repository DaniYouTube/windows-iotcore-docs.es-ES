---
title: Herramienta de migración de Windows 10 IoT Core API
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar la herramienta de migración de la API de IoT Core de Windows 10 para calcular los costos de portabilidad.
keywords: Windows IOT, herramienta de portabilidad de API, portabilidad de API, binarios
ms.openlocfilehash: 1a7acf4a027ef19a8920c7b10f6be61657d2d76a
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918087"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Herramienta de migración de Windows 10 IoT Core API

Windows 10 IoT Core solo admite un subconjunto del área expuesta de la API de Win32 y .net disponible en varias versiones anteriores de Windows. Esta herramienta examinará los archivos binarios y le proporcionará un informe de las API que usan estos archivos binarios que no están disponibles y ofrecen sugerencias para posibles reemplazos. Esto le ayudará a calcular el costo de un puerto a IoT Core, así como a ayudarle durante el proceso.


## <a name="usage"></a>Uso

La herramienta de portabilidad de la API de IoT Core de Windows 10 se puede encontrar en el repositorio de github [MS-IOT/IOT-Utilities](https://github.com/ms-iot/iot-utilities) .  Descargue el archivo [zip del repositorio](https://github.com/ms-iot/iot-utilities/archive/master.zip) y copie la carpeta IoTAPIPortingTool en el equipo local.  Abra **IoTAPIPortingTool. sln** en Visual Studio 2017 y compile el proyecto.  Se generará `IotAPIPortingTool.exe`.

Puede usar la herramienta ejecutando `IoTAPIPortingTool.exe <Application path> [-os]`.

*  `<Application path>` exe de la aplicación para la que se usa la herramienta de portabilidad

*  se debe especificar `-os` si no planea usar UWP.  De forma predeterminada, la herramienta valida los archivos binarios con la plataforma UWP de Windows.

> [!NOTE] 
> IoTAPIPortingTool. exe se debe ejecutar desde un Símbolo del sistema para desarrolladores de Visual Studio. Debe navegar hasta la carpeta que contiene IotAPIPortingTool. exe. 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>Salida

La herramienta generará un archivo de valores separados por comas (CSV) en la misma carpeta que contiene el `IotAPIPortingTool.exe`. El archivo se denomina `IoTAPIPortingTool.csv` (o, `IoTAPIPortingToolOS.csv` si se especifica-os) y se mostrará un resumen en la línea de comandos. Abra el archivo `.csv` en Excel para analizar la salida completa.
