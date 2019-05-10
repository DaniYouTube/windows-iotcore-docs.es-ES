---
title: Información general de AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre AllJoyn, un protocolo común para los dispositivos de IoT y cómo permite que otras extensiones y características con Windows IoT.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 6b558680d479c71b6b8a22d34d03b04e5cbdbd76
ms.sourcegitcommit: 0f46b7b5c15906a6c82b847ffcd9f4d2674f9fd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226834"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, alternativas, el protocolo de IoT de capa de aplicación que sirve para AllJoyn es el [Open Foundation conectividad](https://openconnectivity.org). La implementación estándar de la especificación OCF es Iotivity: puede encontrar soporte técnico de Windows para Iotivity [aquí](https://wiki.iotivity.org/windows).

# <a name="alljoyn"></a>AllJoyn

AllJoyn mejora la capacidad de Internet de las cosas. AllJoyn define un protocolo común para los dispositivos y las aplicaciones detectar y comunicarse entre sí independientemente del fabricante, plataforma o tecnología de transporte.  AllJoyn es un estándar de código abierto controlado por la [AllSeen Alliance](https://allseenalliance.org/), un consorcio del sector entre dedicados a habilitar la interoperabilidad de miles de millones de dispositivos, servicios y aplicaciones para Internet de las cosas.

Microsoft incorporó a la alianza AllSeen en 2014 y agrega AllJoyn como un componente básico de Windows 10. Con la integrada [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), los desarrolladores son gratuitos escribir las aplicaciones compatibles con AllJoyn que se ejecutan en cualquiera de los dispositivos Windows 10, incluidos PCs, tabletas, teléfonos, Xbox, así como dispositivos con Windows IoT Core. Además de la compatibilidad de plataforma para AllJoyn, Microsoft lanzó [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), una extensión de Visual Studio que acelera el desarrollo de AllJoyn mediante la combinación de generación de código con plantillas de aplicaciones listas para usar. AllJoyn Studio permite a los desarrolladores para beneficiarse de la potencia de AllJoyn sin los problemas de instalación y configuración.

¿La idea de AllJoyn? Eche un vistazo a [esto](AllJoynStudio.md) entrada de blog sobre cómo empezar a trabajar con AllJoyn en Windows.


## <a name="developer-resources-and-tools"></a>Herramientas y recursos para desarrolladores

**Puente de dispositivo del sistema**

AllJoyn [puente de dispositivo del sistema](AllJoynDSB.md) permite a los dispositivos que no sean AllJoyn interactuar con el ecosistema de AllJoyn con AllJoyn como su lenguaje común.

Características:
* Crea los dispositivos virtuales para cada dispositivo que no sean AllJoyn expuestos por el adaptador
* Generación de la interfaz en tiempo de ejecución automática del dispositivo del adaptador
* Admite LSF, servicios básicos de Panel de Control, extensibles para agregar más servicios
* Las plantillas de aplicación universal (C#, C++), para las aplicaciones de interfaz de usuario de escritorio y las tareas de inicio de Windows IoT
* Disponible como código abierto

Pueden encontrar más detalles en el [página puente de dispositivo del sistema](AllJoynDSB.md).


**AllJoyn Studio**

[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) es una extensión de Visual Studio desarrollados por Microsoft que acelera el desarrollo de AllJoyn® mediante la combinación de generación de código y la API de WinRT con administración automatizada de proyectos y plantillas de aplicaciones listas para usar. Permite a los programadores beneficiarse de la potencia de AllJoyn sin los problemas de instalación y configuración.

Características:
* Las plantillas de aplicación universal (C#, JavaScript, C++, Visual Basic)
* Configuración de administración y el proyecto de referencia automatizadas
* Agregar o quitar interfaces de una solución
* Fácil acceso a la administración de proyectos a través del menú AllJoyn®
* Cargando las interfaces de los archivos XML de introspección
* Detección de las interfaces de productor, productores en el network1

AllJoyn Studio puede instalarse a través de Visual Studio Tools -> extensiones y actualizaciones... -> En línea -> en el tipo de campo "AllJoyn" de "Búsqueda"

Encontrará más detalles acerca de cómo usar AllJoyn Studio [aquí](AllJoynStudio.md).

**Explorador de IoT para AllJoyn (AllJoyn Explorer)**

El Explorador de IoT para AllJoyn (anteriormente conocido como el Explorador de AllJoyn) es una aplicación Universal de Windows para interactuar con dispositivos de AllJoyn de la red de proximidad local. Desarrolladores pueden enumerar todos los dispositivos de AllJoyn disponibles, inspeccione su estructura de la interfaz y un objeto, así como recibir señales, establecer y obtener propiedades y llamar a métodos.

* [Explorador de IoT para App Store de AllJoyn](https://www.microsoft.com/store/apps/9nblggh6gpxl): Esta es la ubicación de la aplicación de tienda oficial.
* [Explorador de AllJoyn 1.0.1.11 (versión anterior)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): Este archivo zip contiene la agrupación de AllJoyn Explorer AppX para que sea de carga lateral en una máquina de desarrollo. Se trata de una versión del explorador de IoT para AllJoyn aplicaciones publicada anteriormente.
* [Guía de configuración del explorador de AllJoyn](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): Este pdf contiene la documentación sobre cómo implementar el Explorador de AllJoyn.
* [Guía de usuario de explorador AllJoyn](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): Este pdf contiene la documentación sobre cómo usar el Explorador de AllJoyn.


### <a name="additional-resources"></a>Recursos adicionales

* [Uso de la extensión de AllJoyn Studio](AllJoynStudio.md)
* [Productor de AllJoyn y AllJoyn introspección de creación](AllJoynProducer.md)
* [Solución de problemas de AllJoyn con Windows 10](AllJoynTroubleshooting.md)

**Vídeos**

* [Crear sesión técnica AllJoyn de 2015](https://channel9.msdn.com/Events/Build/2015/2-623)
* [WinHEC 2015 AllJoyn Technical sesión](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**Ejemplos**

* [Productores AllJoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [Consumidores de AllJoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [Ejemplos de UWP de AllJoyn (MSDN)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**Referencia**

* [API de AllJoyn en Windows 10 (MSDN)](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [Detalles de la arquitectura de AllJoyn (Alliance Allseen)](https://allseenalliance.org/developers/learn/)
* [Recursos para desarrolladores de AllJoyn (Alliance Allseen)](https://allseenalliance.org/developers/develop/)
* [Manual de referencia de API de C de AllJoyn (Alliance Allseen)](https://allseenalliance.org/docs/api/c/index.html)

