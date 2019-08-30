---
title: Información general sobre AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre AllJoyn, un protocolo común para dispositivos IoT y cómo habilita otras extensiones y características con Windows IoT.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 6b558680d479c71b6b8a22d34d03b04e5cbdbd76
ms.sourcegitcommit: 0f46b7b5c15906a6c82b847ffcd9f4d2674f9fd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226834"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Para preguntas, alternativas, el protocolo de IoT de nivel de aplicación que sirve para AllJoyn es [Open Connectivity Foundation](https://openconnectivity.org). La implementación estándar de la especificación de OCF es Iotivity. la compatibilidad con Windows para Iotivity se puede encontrar [aquí](https://wiki.iotivity.org/windows).

# <a name="alljoyn"></a>AllJoyn

AllJoyn permite el Internet de las cosas. AllJoyn define un protocolo común para que los dispositivos y las aplicaciones detecten y se comuniquen entre sí, independientemente de la tecnología de transporte, la plataforma o el fabricante.  AllJoyn es un estándar de código abierto controlado por [AllSeen Alliance](https://allseenalliance.org/), un consorcio multisector dedicado a habilitar la interoperabilidad de miles de millones de dispositivos, servicios y aplicaciones para el Internet de las cosas.

Microsoft ha unido a AllSeen Alliance en 2014 y ha agregado AllJoyn como componente principal en Windows 10. Con las [API de AllJoyn](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx)integradas, los desarrolladores pueden escribir aplicaciones compatibles con alljoyn que se ejecuten en cualquiera de los dispositivos Windows 10, incluidos equipos, tabletas, teléfonos, Xbox y dispositivos con Windows IOT Core. Además de la compatibilidad de la plataforma para AllJoyn, Microsoft publicó [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), una extensión de Visual Studio que acelera el desarrollo de alljoyn mediante la combinación de la generación de código con plantillas de aplicación preparadas. AllJoyn Studio permite a los desarrolladores aprovechar la eficacia de AllJoyn sin las molestias de la instalación y la configuración.

¿Está entusiasmado con AllJoyn? Vea [esta](AllJoynStudio.md) entrada de blog sobre cómo empezar a usar AllJoyn en Windows.


## <a name="developer-resources-and-tools"></a>Herramientas y recursos para desarrolladores

**Puente del sistema de dispositivos**

El [puente del sistema de dispositivos](AllJoynDSB.md) alljoyn permite a los dispositivos no AllJoyn interactuar con el ecosistema AllJoyn mediante alljoyn como su lenguaje común.

Características:
* Crea dispositivos virtuales para cada dispositivo no AllJoyn expuesto por el adaptador
* Generación automatizada de interfaz en tiempo de ejecución desde el dispositivo adaptador
* Admite LSF, servicios base del panel de control, extensible para agregar más servicios
* Plantillas de aplicacionesC#universales C++(,), para aplicaciones de interfaz de usuario de escritorio y tareas de inicio de Windows IOT
* Disponible como código abierto

Puede encontrar más detalles en la [Página puente de sistema del dispositivo](AllJoynDSB.md).


**Estudio de AllJoyn**

[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) es una extensión de Visual Studio desarrollada por Microsoft que acelera el desarrollo de® alljoyn mediante la combinación de generación de código y la API de WinRT con la administración automatizada de proyectos y plantillas de aplicación listas para usar. Permite a los desarrolladores aprovechar la eficacia de AllJoyn sin las molestias de la instalación y la configuración.

Características:
* Plantillas de aplicación universalC#(, JavaScript C++,, Visual Basic)
* Administración automatizada de referencias y configuración de proyectos
* Agregar o quitar interfaces en una solución
* Acceso sencillo a la administración de proyectos mediante el menú de® AllJoyn
* Cargando interfaces desde archivos XML introspección
* Detectando interfaces de productores en el network1

AllJoyn Studio se puede instalar a través de extensiones y actualizaciones de > de Visual Studio Tools... -> en línea-> en el campo "Buscar" tipo "AllJoyn"

Puede encontrar más información sobre cómo usar AllJoyn Studio [aquí](AllJoynStudio.md).

**Explorador de IoT para AllJoyn (explorador de AllJoyn)**

El explorador de IoT para AllJoyn (conocido anteriormente como explorador de AllJoyn) es una aplicación universal de Windows para interactuar con dispositivos AllJoyn en la red de proximidad local. Los desarrolladores pueden enumerar todos los dispositivos AllJoyn disponibles, inspeccionar su interfaz y estructura de objetos, así como recibir señales, establecer y obtener propiedades y llamar a métodos.

* [Explorador de IOT para la aplicación de la tienda AllJoyn](https://www.microsoft.com/store/apps/9nblggh6gpxl): Esta es la ubicación de la aplicación de almacenamiento oficial.
* [Explorador AllJoyn 1.0.1.11 (versión anterior)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): Este archivo comprimido contiene el paquete AppX del explorador AllJoyn que se va a cargar de lado en un equipo del desarrollador. Se trata de una versión publicada anteriormente de IoT Explorer para la aplicación AllJoyn.
* [Guía de configuración del explorador AllJoyn](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): Este pdf contiene la documentación sobre cómo implementar el explorador de AllJoyn.
* [Guía de usuario del explorador de AllJoyn](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): Este pdf contiene la documentación sobre cómo usar el explorador de AllJoyn.


### <a name="additional-resources"></a>Recursos adicionales

* [Usar la extensión de Studio AllJoyn](AllJoynStudio.md)
* [Introspección AllJoyn de creación y productor de AllJoyn](AllJoynProducer.md)
* [Solución de problemas de AllJoyn con Windows 10](AllJoynTroubleshooting.md)

**Vídeos**

* [Sesión técnica de la compilación 2015 AllJoyn](https://channel9.msdn.com/Events/Build/2015/2-623)
* [Sesión técnica de WinHEC 2015 AllJoyn](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**Ejemplos**

* [Productores de AllJoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [Consumidores de AllJoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [Ejemplos de UWP de AllJoyn (MSDN)](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**Referencia**

* [API de AllJoyn en Windows 10 (MSDN)](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [Detalles de la arquitectura AllJoyn (Allseen Alliance)](https://allseenalliance.org/developers/learn/)
* [Recursos para desarrolladores de AllJoyn (Allseen Alliance)](https://allseenalliance.org/developers/develop/)
* [Guía de referencia de la API de C de AllJoyn (Allseen Alliance)](https://allseenalliance.org/docs/api/c/index.html)

