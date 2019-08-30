---
title: Guía de proyecto de cableado de Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la creación, la instalación y la implementación de un proyecto de cableado de Arduino con Windows IoT Core.
keywords: Windows IOT, Arduino, Arduino, rendimiento de relámpago, Visual Studio
ms.openlocfilehash: 7c5e51efd20de014af4533587fbe6f210140b793
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744810"
---
# <a name="arduino-wiring-project-guide"></a>Guía de proyecto de cableado de Arduino

> [!IMPORTANT]
> El equipo de IoT de Windows 10 ya no mantiene de forma activa Arduino.

Esta guía le guiará a través de la creación, configuración e implementación de un proyecto de cableado de Arduino con Windows IoT Core.

Los proyectos de cableado de Arduino usan la conocida API de cableado de Arduino fácil de usar con el controlador de Windows IoT Lightning DMAP: un controlador que usa la asignación de memoria directa para proporcionar [velocidades de rendimiento](../develop-your-app/LightningPerformance.md)significativas. Puede copiar & pegar bocetos y bibliotecas de Arduino en los proyectos de cableado de IoT Core Arduino y ejecutarlos en dispositivos IoT Core compatibles, incluidos Raspberry pi2, 3 y Minnowboard Max. Para obtener más información, consulte la sección desarrollo de esta página.

## <a name="install-the-microsoft-iot-templates"></a>Instalación de las plantillas de IoT de Microsoft

> [!NOTE]
> Descargar VS 2015 para acceder a las plantillas de cableado de Arduino: estas plantillas no admiten loner en VS 2017 y versiones posteriores.

Hemos proporcionado una extensión de Visual Studio que instalará automáticamente una plantilla de VS para los proyectos de cableado de Arduino, así como otros tipos de proyectos de IoT de Microsoft. 

- Vaya a la [Página de la extensión de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la galería de Visual Studio.
- Instale la extensión y reinicie Visual Studio si ya estaba abierto

## <a name="change-the-default-controller-driver"></a>Cambiar el controlador de controlador predeterminado

Tendrá que ejecutar el controlador asignado a memoria directa para escribir soluciones de cableado de Arduino. Consulte la [Guía de configuración de Lightning](../develop-your-app/LightningSetup.md) para obtener instrucciones.

## <a name="develop"></a>Desarrollo
Complete uno de los ejemplos de "conexión" en la [Página de ejemplos](https://developer.microsoft.com/en-us/windows/iot/samples)o cree su propio proyecto. Cualquiera de los ejemplos que se hayan creado con el cableado de Arduino se enumerará como se indica a continuación: [Parpadeo (cableado)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring). Parpadee, el proyecto de cononical "Hola mundo" para proyectos de IoT, es un buen lugar para empezar por su primer proyecto.

### <a name="create-a-new-project"></a>Crear un nuevo proyecto
1. Abra Visual Studio.

2. Seleccionar archivo-> Nuevo-> proyecto...

3. En el cuadro de diálogo que aparece, elija:  
Visual C++ -> windows-> Windows IOT core-> Arduino de la aplicación de cableado para Windows IOT Core  
(puede aparecer en su lugar como)  
Visual C++ -> aplicación de cableado de Windows IOT core-> Arduino para Windows IOT Core 


![Creación de aplicaciones](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a>Migración

La API de cableado de Arduino se ha implementado cuidadosamente para que sea posible copiar y pegar las bibliotecas y los bocetos en un proyecto de cableado de Arduino. No obstante, en algunas circunstancias, es posible que tenga que realizar pequeñas modificaciones en sus bocetos o bibliotecas. Hemos creado una guía de migración de [cables de Arduino](ArduinoWiringPortingGuide.md) fácil de seguir para cubrir estos posibles problemas.

## <a name="build-and-deploy"></a>Compilación e implementación

- En Visual Studio, asegúrese de que "equipo remoto" esté seleccionado como destino de implementación.
- Además, asegúrese de que la arquitectura está establecida para que coincida con la del panel en el que está ejecutando el proyecto. Para Raspberry pi 2 o 3, elija "ARM" y para Minnowboard Max, elija "x86".

![Equipo remoto](../media/ArduinoWiring/wiringapp_remotemachine.png)

- Abra las propiedades de la solución que se encuentran en el menú contextual de depuración en Visual Studio.

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties.png)

- Busque la dirección IP o el nombre de equipo del dispositivo. Use la aplicación Windows 10 IoT Core Dashboard o Conecte el dispositivo a un monitor.
- Escriba el nombre de la máquina (minwinpc de forma predeterminada) o la dirección IP del equipo remoto en el campo "nombre del equipo". Si ha cambiado el nombre del dispositivo a algo además de "minwinpc", use ese nombre en el cuadro de inicio de sesión.
- Asegúrese de que el tipo de Authentican es: Universal (protocolo sin cifrar)

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties2.png)

- Presione F5 para compilar e implementar el proyecto en el dispositivo.
