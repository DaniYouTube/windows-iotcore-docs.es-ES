---
title: Información general de puente de AllJoyn dispositivo del sistema
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre el puente de AllJoyn dispositivo del sistema, que se adapta a los dispositivos que no sean AllJoyn al ecosistema de AllJoyn para la interoperabilidad más amplia.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514335"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="alljoyn-device-system-bridge"></a>Puente de AllJoyn dispositivo del sistema

AllJoyn proporciona a los desarrolladores la flexibilidad necesaria para usar una amplia gama de plataformas y tecnologías de conexión para crear dispositivos para el ecosistema de AllJoyn.  Sin embargo, muchos fabricantes de dispositivos tienen soluciones de dispositivos existentes en sus carteras. Para estas situaciones, Microsoft creó el puente de dispositivo del sistema (OSD). El OSD adapta a los dispositivos que no sean AllJoyn al ecosistema de AllJoyn para que los dispositivos adaptados pueden interoperar con AllJoyn como su lenguaje común. Soporte técnico de Microsoft DSB principal de sistemas de automatización como Zigbee y Z-Wave y puede incluso la compatibilidad de industrial de creación de sistemas de automatización como BACnet.  Además, el código fuente está disponible para la personalización admitir otras tecnologías

## <a name="how-dsb-works"></a>Funcionamiento de OSD

La capacidad de clave de una OSD consiste en crear una representación virtual de dispositivos en el bus de AllJoyn. Por lo que estos dispositivos, lo que es su ecosistema de conectividad o dispositivo nativo, aparecerán y ser accesible como dispositivos AllJoyn. En la siguiente imagen se dos DSBs, uno para Z-Wave y otro para ZigBee crear una representación virtual de la Z-Wave dos y los dispositivos de ZigBee uno en el bus de AllJoyn. Con este todos los dispositivos en el AllJoyn sitio puede comunicarse entre sí. Dado que los dispositivos de Z-Wave y ZigBee todo en el bus AllJoyn ahora pueden comunicarse entre sí también.

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

Otro elemento clave del diseño OSD es que no requerirá cambios en el sistema de dispositivo AllJoyn o no AllJoyn. Todas las adopciones de escenarios necesarios se realizan en el OSD.

Como se muestra también en la imagen, no hay ninguna asignación de dispositivos de AllJoyn al lado no AllJoyn. El objetivo de la OSD es incluir dispositivos en el ecosistema de AllJoyn. Habilitar solo una manera simplifica el desarrollo. También reduce el riesgo que AllJoyn capacidades de seguridad se convierten en debilitada por el sistema del dispositivo no AllJoyn potencialmente menos seguro.

## <a name="dsb-architecture"></a>Arquitectura de OSD

Microsoft se propone arquitectura OSD consta de tres componentes principales, pila de acceso de red, el adaptador y el puente. La siguiente imagen muestra la descripción de esta arquitectura de alto nivel.

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>Puente
* Representa cada objeto de dispositivo interno como dispositivo de AllJoyn, datos adjuntos de bus independiente para cada dispositivo
* Los dispositivos se agregan o se quitó el bus AllJoyn dinámicamente
* Administra la configuración de seguridad y la visibilidad de dispositivo
* Crea datos adjuntos de bus de puente y el adaptador de interfaz de configuración
* Es independiente de los tipos de dispositivo interno y reutilizable para cualquier tipo de código de puente

### <a name="adapter"></a>Adaptador
* Crea y administra los dispositivos virtuales en nombre de cada dispositivo de la red no AllJoyn
* Esquemas de dispositivo se traduce en objetos de dispositivo interno
* Administra los recursos de red, por ejemplo, las claves de acceso, las credenciales

### <a name="network-access-stack"></a>Pila de acceso de red
* Acceso a fuera de la red AllJoyn específica, por ejemplo, la pila de Z-Wave

## <a name="adapter-classes"></a>Clases de adaptadores

El diagrama siguiente se muestran las clases que los desarrolladores usarán en la plantilla Microsoft DSB para crear una abstracción de los dispositivos nativos que deben estar vinculadas en AllJoyn. El puente usará la instancia de la clase de adaptador para crear los datos adjuntos de bus para cada dispositivo en la lista Adapter.devices.
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>Controladores especiales

AllJoyn especifica varios servicios bases y marcos de interfaces estándar como LSF, HAE o Panel de Control. El OSD puede expone a aquellos con controladores especiales. La versión actual de la plantilla de OSD contiene implementaciones de las interfaces LSF y Panel de Control. Los desarrolladores conectarán su código a las funciones de devolución de llamada para las interfaces LSF y Panel de Control en el puente.

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>Recursos de OSD

### <a name="visual-studio-dsb-template"></a>Plantilla de Visual Studio OSD

Plantilla de OSD de Visual Studio es una extensión de Visual Studio que le permite crear fácilmente nuevos proyectos de OSD. El proyecto creará todos los componentes necesarios, como el puente, un proyecto de shell para el adaptador y todos los archivos de solución compilar el OSD como dispositivo sin periféricos o puntas. Esta extensión de Visual Studio contiene plantillas nativos y administrados AllJoyn dispositivo sistema puente.

Descargar plantilla de OSD desde estas ubicaciones:

* [Plantilla de OSD para Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* [Plantilla de OSD para Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_OSD plantilla también puede instalarse a través de Visual Studio Tools -> extensiones y actualizaciones... -> en línea -> en el tipo de campo de "Búsqueda" "OSD"._

El [asignación de objetos de OSD para AllJoyn](AlljoynDsbApiGuide.md) documento describe las interfaces de clave y los métodos utilizados para generar el puente de Alljoyn del sistema.

### <a name="sample-dsbs"></a>Ejemplo DSBs

* [Ejemplo y el Tutorial de simulacro adaptador AllJoyn OSD](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * Este tutorial muestra cómo usar la aplicación de puente de dispositivo del sistema para conectar los dispositivos de IoT Core para simular dispositivos BACnet.
* [Ejemplo y el Tutorial de adaptador de Z-Wave AllJoyn OSD](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * Este tutorial muestra cómo usar la aplicación de puente de dispositivo del sistema para conectar los dispositivos de IoT Core a los dispositivos de Z-Wave.
* [Tutorial sobre el adaptador GPIO AllJoyn OSDC++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * Este tutorial muestra cómo usar la plantilla de puente de AllJoyn dispositivo del sistema para crear un ejemplo C++ app que ejerce el dispositivo GPIO.
* [Tutorial sobre el adaptador GPIO AllJoyn OSDC#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * Este tutorial muestra cómo usar la plantilla de puente de AllJoyn dispositivo del sistema para crear una aplicación administrada de ejemplo que ejerce el dispositivo GPIO.
* [Ejemplo y el Tutorial de adaptador ZigBee AllJoyn OSD](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * Este tutorial muestra cómo usar la aplicación de puente de dispositivo del sistema para conectar los dispositivos de IoT Core ZigBee dispositivos.
* [Ejemplo y el Tutorial de adaptador BACnet AllJoyn OSD](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * Este tutorial muestra cómo usar la aplicación de puente de dispositivo del sistema para conectar los dispositivos de IoT Core BACnet dispositivos.
* [Tutorial de AllJoyn.JS](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * Este tutorial muestra cómo ejecutar la aplicación AllJoyn.JS desarrollado por Allseen Alliance como una aplicación de Windows 10. AllJoyn.JS le permite escribir código JavaScript para crear, supervisar y controlar los dispositivos de AllJoyn.
* [Ejemplo y el Tutorial de adaptador OIC AllJoyn OSD](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * Este tutorial muestra cómo usar la aplicación de puente de dispositivo del sistema para conectar sus dispositivos de IoT Core a dispositivos IoTivity/OIC.
