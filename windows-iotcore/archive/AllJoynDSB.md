---
title: Introducción al puente del sistema de dispositivos AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre el puente del sistema de dispositivos AllJoyn, que adapta los dispositivos no AllJoyn al ecosistema AllJoyn para una interoperabilidad más amplia.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 305629867bb85600b314fc34de268c46d90ce6e7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167963"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="alljoyn-device-system-bridge"></a>Puente del sistema de dispositivos AllJoyn

AllJoyn proporciona a los desarrolladores la flexibilidad de usar una amplia gama de plataformas y tecnologías de conexión para crear dispositivos para el ecosistema AllJoyn.  Sin embargo, muchos de los responsables de dispositivos tienen soluciones de dispositivo existentes en sus carteras. En estas situaciones, Microsoft ha creado el puente de sistema del dispositivo (DSB). DSB adapta los dispositivos no AllJoyn al ecosistema AllJoyn para que los dispositivos adaptados puedan interoperar con AllJoyn como su lenguaje común. Los sistemas de automatización doméstica de soporte técnico de Microsoft DSB, como ZigBee y Z-Wave, e incluso pueden admitir sistemas de automatización de la creación industrial como BACnet.  Además, el código fuente está disponible para la personalización para admitir otras tecnologías

## <a name="how-dsb-works"></a>Cómo funciona DSB

La funcionalidad clave de una DSB es crear una representación virtual de dispositivos en el bus AllJoyn. Por lo tanto, estos dispositivos, sea cual sea su conectividad nativa o el ecosistema de dispositivos, aparecerán y serán accesibles como dispositivos AllJoyn. En la imagen que aparece debajo de dos DSBs, uno para la ola Z y otro para ZigBee crear una representación virtual de los dos dispositivos ZigBee en el bus AllJoyn. Con este, todos los dispositivos del sitio AllJoyn pueden comunicarse entre sí. Dado que los dispositivos ZigBee de Z y de onda están todos en el bus AllJoyn, ahora pueden comunicarse entre sí.

![AJ_Docu_DSB_Overview](../media/AllJoyn/AJ_Docu_DSB_Overview.png)

Otro elemento clave del diseño de DSB es que no requiere ningún cambio en el sistema de dispositivos no AllJoyn o AllJoyn. Todas las adoptaciones necesarias se realizan en el DSB.

Como también se muestra en la imagen, no hay ninguna asignación desde dispositivos AllJoyn al lado no AllJoyn. El objetivo de DSB es llevar los dispositivos al ecosistema de AllJoyn. Habilitar solo una manera simplifica el desarrollo. También reduce el riesgo de que las funcionalidades de seguridad de AllJoyn sean debilitadas por el sistema de dispositivos no AllJoyn potencialmente menos seguro.

## <a name="dsb-architecture"></a>Arquitectura de DSB

La arquitectura DSB propuesta de Microsoft consta de tres componentes principales: pila de acceso a la red, adaptador y puente. En la imagen siguiente se muestra la información general de alto nivel de esta arquitectura.

![AJ_Docu_DSB_Architecture](../media/AllJoyn/AJ_Docu_DSB_Architecture.png)

### <a name="bridge"></a>Superar
* Representa un objeto de dispositivo interno como dispositivo AllJoyn, datos adjuntos de bus independientes para cada dispositivo.
* Los dispositivos se agregan o quitan dinámicamente en el bus AllJoyn
* La configuración administra la visibilidad y la seguridad del dispositivo
* Crea datos adjuntos de bus para la interfaz de configuración de puente y adaptador
* El código de puente es independiente de los tipos de dispositivos internos y se puede volver a usar para cualquier tipo.

### <a name="adapter"></a>Adaptador
* Crea instancias y administra dispositivos virtuales en nombre de cada dispositivo desde la red no AllJoyn
* Traduce los esquemas de dispositivo en objetos de dispositivo internos.
* Administra los recursos de red, por ejemplo, las claves de acceso y las credenciales

### <a name="network-access-stack"></a>Pila de acceso a la red
* Acceso a una red no AllJoyn específica, por ejemplo, una pila de onda Z

## <a name="adapter-classes"></a>Clases de adaptadores

En el diagrama siguiente se muestran las clases que los desarrolladores usarán en la plantilla DSB de Microsoft para crear una abstracción de los dispositivos nativos que se deben enlazar a AllJoyn. El puente usará la instancia de la clase Adapter para crear los datos adjuntos de bus para cada dispositivo en la lista Adapter. Devices.
![AJ_Docu_DSB_Class_Diagram](../media/AllJoyn/AJ_Docu_DSB_Class_Diagram.png)

## <a name="special-handlers"></a>Controladores especiales

AllJoyn especifica varios servicios base y marcos de interfaces estándar, como LSF, HAE o panel de control. El DSB puede exponer a los usuarios con controladores especiales. La versión actual de la plantilla DSB contiene implementaciones de las interfaces de LSF y del panel de control. Los desarrolladores conectarán su código a las funciones de devolución de llamada para LSF e interfaces del panel de control en el puente.

![AJ_Docu_DSB_Special_Handlers](../media/AllJoyn/AJ_Docu_DSB_Special_Handlers.png)

## <a name="dsb-resources"></a>Recursos de DSB

### <a name="visual-studio-dsb-template"></a>Plantilla DSB de Visual Studio

La plantilla DSB de Visual Studio es una extensión de Visual Studio que le permite crear fácilmente nuevos proyectos de DSB. El proyecto creará todos los componentes necesarios, como el puente, un proyecto de Shell para el adaptador y todos los archivos de solución para compilar el DSB como dispositivo con o sin cabeza. Esta extensión de Visual Studio contiene las plantillas de puente de sistema de dispositivo AllJoyn nativo y administrado.

Descargar la plantilla de DSB desde estas ubicaciones:

* [Plantilla de DSB para Visual Studio 2015](https://visualstudiogallery.msdn.microsoft.com/aea0b437-ef07-42e3-bd88-8c7f906d5da8)
* [La plantilla DSB para Visual Studio 2017](https://marketplace.visualstudio.com/vsgallery/c5f52768-8df7-42ff-b84e-d66d3d22fb50)
_DSB plantilla también puede instalarse a través de extensiones y actualizaciones de Visual Studio Tools->...-> en línea > en el campo "Buscar", escriba "DSB"._

En el documento [asignación de objetos DSB a AllJoyn](AlljoynDsbApiGuide.md) se describen las interfaces y los métodos clave que se usan para compilar el puente del sistema AllJoyn.

### <a name="sample-dsbs"></a>DSBs de ejemplo

* [Tutorial y ejemplo de adaptador ficticio de AllJoyn DSB](https://developer.microsoft.com/en-us/windows/iot/samples/alljoynmockadapter)
  * En este tutorial se muestra cómo usar la aplicación de puente de sistema de dispositivos para conectar los dispositivos IoT Core a dispositivos BACnet ficticios.
* [Tutorial y ejemplo de adaptador de onda DSB de AllJoyn](https://developer.microsoft.com/en-us/windows/iot/samples/zwaveadapter)
  * En este tutorial se muestra cómo usar la aplicación de puente de sistema de dispositivos para conectar sus dispositivos IoT Core a dispositivos de onda Z.
* [Tutorial del adaptador de AllJoyn DSB GPIOC++](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsb)
  * En este tutorial se muestra cómo usar la plantilla de puente del sistema de dispositivos AllJoyn C++ para crear una aplicación de ejemplo que ejerza el dispositivo GPIO.
* [Tutorial del adaptador de AllJoyn DSB GPIOC#](https://developer.microsoft.com/en-us/windows/iot/samples/alljoyndsbcs)
  * En este tutorial se muestra cómo usar la plantilla de puente del sistema de dispositivos AllJoyn para crear una aplicación administrada de ejemplo que ejerza el dispositivo GPIO.
* [Tutorial y ejemplo de DSB de AllJoyn de ZigBee](https://developer.microsoft.com/en-us/windows/iot/samples/ZigBeeAdapter)
  * En este tutorial se muestra cómo usar la aplicación de puente de sistema de dispositivos para conectar los dispositivos IoT Core a dispositivos ZigBee.
* [Tutorial y ejemplo de DSB de AllJoyn de BACnet](https://developer.microsoft.com/en-us/windows/iot/samples/BACnetAdapter)
  * En este tutorial se muestra cómo usar la aplicación de puente de sistema de dispositivos para conectar los dispositivos IoT Core a dispositivos BACnet.
* [Tutorial de AllJoyn. JS](https://developer.microsoft.com/en-us/windows/iot/samples/AllJoynJS)
  * En este tutorial se muestra cómo ejecutar la aplicación AllJoyn. JS desarrollada por Allseen Alliance como una aplicación de Windows 10. AllJoyn. JS permite escribir JavaScript para crear, supervisar y controlar dispositivos AllJoyn.
* [Tutorial y ejemplo de DSB de AllJoyn de OIC](https://developer.microsoft.com/en-us/windows/iot/samples/OICAdapter)
  * En este tutorial se muestra cómo usar la aplicación de puente de sistema de dispositivos para conectar los dispositivos IoT Core a dispositivos IoTivity/OIC.
