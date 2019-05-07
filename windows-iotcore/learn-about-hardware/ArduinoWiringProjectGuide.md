---
title: Guía de proyectos de la conexión de Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la creación, el programa de instalación e implementación de un proyecto de cableado de Arduino con Windows IoT Core.
keywords: iot, Arduino, Arduino cableado de Windows, un rendimiento increíblemente, Visual Studio
ms.openlocfilehash: 7c5e51efd20de014af4533587fbe6f210140b793
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744810"
---
# <a name="arduino-wiring-project-guide"></a>Guía de proyectos de la conexión de Arduino

> [!IMPORTANT]
> El equipo de Windows 10 IoT activamente ya no es mantener Arduino.

Esta guía le guiará a través de la creación, el programa de instalación e implementación de un proyecto de cableado de Arduino con Windows IoT Core.

Proyectos de la conexión de Arduino usan la API de cableado de familiar y fácil de usar Arduino con controladores de Windows IoT relámpago DMAP: un controlador mediante la asignación de memoria directa para proporcionar importantes [velocidades de rendimiento](../develop-your-app/LightningPerformance.md). Puede copiar & Pegar Arduino Bocetos y las bibliotecas en sus proyectos de IoT Core Arduino cableado y ejecútelas en admitidos IoT Core dispositivos, incluidos Raspberry Pi2, 3 y Minnowboard máximo! Consulte la sección de desarrollo de esta página para obtener más información.

## <a name="install-the-microsoft-iot-templates"></a>Instalar las plantillas de IoT de Microsoft

> [!NOTE]
> Descarga de VS 2015 para acceder a las plantillas de cableado Arduino - estas plantillas no son ningún solitaria admitido en VS 2017 y versiones posteriores.

Hemos proporcionado una extensión de Visual Studio que se instalará automáticamente una plantilla de VS para los proyectos de la conexión de Arduino, así como otros tipos de proyecto de IoT de Microsoft. 

- Diríjase a [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la Galería de Visual Studio!
- Instalar la extensión y reinicie Visual Studio si estaba abierto

## <a name="change-the-default-controller-driver"></a>Cambiar el controlador del controlador predeterminado

Deberá ejecutar el controlador de asignar memoria directa para escribir soluciones de conexión de Arduino! Hacer referencia a la [relámpago Guía de instalación](../develop-your-app/LightningSetup.md) para obtener instrucciones.

## <a name="develop"></a>Desarrollo
Complete uno de los ejemplos de "Conexión" en el [página de ejemplos de](https://developer.microsoft.com/en-us/windows/iot/samples), o crear su propio proyecto. Cualquiera de los ejemplos que hemos creado que se escriben utilizando la conexión de Arduino, se mostrará la siguiente manera: [Llamativa (cableado)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring). El proyecto "Hello World" cononical para los proyectos de IoT, llamativa, es un excelente punto de partida para su primer proyecto.

### <a name="create-a-new-project"></a>Cree un nuevo proyecto
1. Abra Visual Studio.

2. Seleccione Archivo -> Nuevo -> proyecto...

3. En el cuadro de diálogo que aparece, elija:  
Visual C++ -> Windows -> Windows IoT Core -> Arduino cableado de la aplicación para Windows IoT Core  
(puede aparecer en su lugar como)  
Visual C++ -> Windows IoT Core -> Arduino cableado de la aplicación para Windows IoT Core 


![Crear aplicación](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>Migración

Se ha implementado la API de conexión de Arduino con cuidado para que sea posible copiar y pegar las bibliotecas y dibujos en un proyecto de cableado de Arduino. Sin embargo, hay, en algunas circunstancias, ligeras modificaciones, es posible que deba realizar en los esquemas o las bibliotecas. Hemos creado una fácil de seguir [Guía de migración de la conexión de Arduino](ArduinoWiringPortingGuide.md) para cubrir estos posibles problemas.

## <a name="build-and-deploy"></a>Compilación e implementación

- En Visual Studio, asegúrese de que "Máquina remota" está seleccionado como destino de implementación.
- Además, asegúrese de que la arquitectura se establece para que coincida con el panel que se ejecutan en el proyecto. Para Raspberry Pi 2 o 3 elija "ARM" y para Minnowboard Max, elija "x86".

![Equipo remoto](../media/ArduinoWiring/wiringapp_remotemachine.png)

- Abra las propiedades de la solución que se encuentra en el menú contextual de depuración en Visual Studio.

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties.png)

- Busque el nombre de máquina o la dirección IP del dispositivo. Usar la aplicación de panel de Windows 10 IoT Core o enlazar el dispositivo a un monitor.
- Escriba el nombre del equipo (minwinpc de forma predeterminada) o la dirección IP del equipo remoto en el campo 'nombre del equipo'. Si ha cambiado el nombre del dispositivo a algo además 'minwinpc' use ese nombre en el cuadro de inicio de sesión en su lugar.
- Asegúrese de que el tipo Authentican es: Universal (protocolo sin cifrar)

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties2.png)

- Presione F5 para compilar e implementar el proyecto en el dispositivo.
