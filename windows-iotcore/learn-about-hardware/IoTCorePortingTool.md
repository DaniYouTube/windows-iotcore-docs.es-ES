---
title: Herramienta de migración de Windows 10 IoT Core API
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar la herramienta de migración de Windows 10 IoT Core API para calcular los costos de migración.
keywords: Windows iot, API de migración de la herramienta, la portabilidad de API, los archivos binarios
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514604"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Herramienta de migración de Windows 10 IoT Core API

Windows 10 IoT Core solo admite un subconjunto de la de Win32 y .net área expuesta de API disponible en diferentes versiones anteriores de Windows. Esta herramienta examinará los archivos binarios y le entregará un informe de las API que use estos archivos binarios que no están disponibles y se ofrecen sugerencias para los reemplazos posibles. Esto se ambos ayudar a estimar el costo de un puerto de IoT Core así como ayudarle a lo largo de la forma.


## <a name="usage"></a>Uso

La herramienta de migración de Windows 10 IoT Core API puede encontrarse en el [ms: iot/iot-utilidades](https://github.com/ms-iot/iot-utilities) repositorio de github.  Descargue el [zip del repositorio](https://github.com/ms-iot/iot-utilities/archive/master.zip) y copie la carpeta IoTAPIPortingTool en el equipo local.  Abra **IoTAPIPortingTool.sln** en Visual Studio 2017 y compile el proyecto.  Esto generará `IotAPIPortingTool.exe`.

Puede usar la herramienta mediante la ejecución de `IoTAPIPortingTool.exe <Application path> [-os]`.

*  `<Application path>` exe de la aplicación que se usa la herramienta de migración para

*  `-os` debe especificarse si no planea usar UWP.  De forma predeterminada, la herramienta valida los archivos binarios en la plataforma UWP de Windows.

> [!NOTE] 
> IoTAPIPortingTool.exe se debe ejecutar desde un símbolo del sistema de Visual Studio para desarrolladores. Necesita navegar hasta la carpeta que contiene el IotAPIPortingTool.exe. 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>Salida

La herramienta generará un archivo de archivo (csv) de valores separados por comas en la misma carpeta que contiene el `IotAPIPortingTool.exe`. El archivo se denomina `IoTAPIPortingTool.csv` (o bien, `IoTAPIPortingToolOS.csv` si se especifica - sistema operativo) y será un resumen en la línea de comandos. Abra el `.csv` archivo en Excel para analizar la salida completa.
