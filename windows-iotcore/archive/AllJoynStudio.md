---
title: Estudio de AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo crear una aplicación para UWP de AllJoyn con las API AllJoyn de Plataforma universal de Windows (UWP) y Visual Studio 2017.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168503"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="using-the-alljoyn-studio-extension"></a>Usar la extensión de Studio AllJoyn

La [Alianza de AllSeen](https://allseenalliance.org/) creó AllJoyn para potenciar el Internet de las cosas. Windows 10 tiene AllJoyn compilado de forma nativa en su plataforma, lo que permite a los desarrolladores aprovechar con facilidad de AllJoyn para "habilitar IoT" las aplicaciones de Windows 10. En este artículo se describen los pasos necesarios para compilar aplicaciones para Windows 10 con las API AllJoyn de Plataforma universal de Windows (UWP) y la extensión Visual Studio 2017 [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) .

## <a name="understanding-alljoyn-uwp-app-development"></a>Descripción del desarrollo de aplicaciones para UWP de AllJoyn

Tres componentes principales forman aplicaciones de UWP de AllJoyn:

1. Diseño y diseño de aplicaciones (XAML o HTML) y componentes deC#clase (, C++JavaScript, o VB).
2. Las API principales de AllJoyn: La API de cliente estándar AllJoyn (C) y Windows. Devices. AllJoyn API (WinRT) están disponibles en el SDK de Windows 10.
3. Uno o varios componentes de Windows Runtime de UWP (el genera este código a partir de las interfaces AllJoyn).

En el diagrama siguiente se muestra la arquitectura de un proyecto de UWP de AllJoyn típico:

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

Las aplicaciones UWP habilitadas para AllJoyn pueden ser productores (implementar y exponer interfaces, normalmente un dispositivo), consumidores (usar interfaces, normalmente aplicaciones) o ambos. Los consumidores y productores comparten los mismos pasos de inicio, solo divergentes en los detalles de implementación.

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>Creación de una aplicación para UWP habilitada para AllJoyn

Siga estos pasos para desarrollar aplicaciones UWP habilitadas para AllJoyn para Windows 10: (se explica con más detalle más adelante en este documento)

1. Prepare el entorno de compilación.
2. Determine qué interfaces AllJoyn se usarán y obtenga o cree el XML de introspección necesario.
3. Cree un proyecto de aplicación AllJoyn y seleccione introspección XML e interfaces deseadas para la generación de código.
4. Implemente el código de productor o ponsumer en la aplicación mediante las API expuestas de los componentes de Windows Runtime de UWP generados.
5. Compilar la interfaz de usuario.

## <a name="preparing-your-build-environment"></a>Preparación del entorno de compilación

La compilación de Windows 10 y las herramientas relacionadas incluyen todos los recursos que necesitará para escribir aplicaciones UWP habilitadas para AllJoyn.

Esto es lo que debe hacer antes de empezar a escribir código:

* Instalación de [Windows 10](https://www.microsoft.com/windows/) en un equipo
* Instalación de [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (no use una edición Express)
* Descargue la extensión [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) de la galería de Visual Studio. 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>Obtención de XML de introspección para interfaces AllJoyn

Hay tres maneras de obtener las definiciones de la interfaz AllJoyn que necesitará para iniciar el proyecto:

1. Extraiga el XML introspección de los productores de AllJoyn presentes en la red en tiempo de ejecución.
2. Obtener el XML de introspección de la documentación; ejemplo [Documentación de iluminación de la plataforma de servicio (LSF)](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) de AllSeen Alliance.
3. Cree su propio archivo XML de introspección que sea compatible con el formato de[introspección del bus](http://dbus.freedesktop.org/doc/dbus-specification.html) AllJoyn/D.

En este artículo se tratan las dos primeras maneras: AllJoyn® Studio admite de forma nativa la consulta de la red para productores de AllJoyn y la extracción de su XML, así como la carga de archivos XML introspección.  Aprenda a crear su propio [aquí](AllJoynProducer.md).

Un dispositivo tostador habilitado para AllJoyn servirá como ejemplo para esta publicación. Este tostador expone los controles para iniciar y detener la secuencia de notificación, establecer la "oscuridad" y las notificaciones cuando se graba la notificación del sistema.

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

El sistema de notificaciones expone el siguiente código XML:

``` xml
<node name="/toaster">
  <interface name="org.alljoyn.example.Toaster">
    <annotation name="org.alljoyn.Bus.Secure" value="true"/>
    <description language="en">Example interface for controlling a toaster appliance</description>
    <description language="fr">Interface Exemple de commande d'un appareil de grille-pain</description>
    <property name="Version" type="q" access="read">
      <description>Interface version</description>
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="const"/>
    </property>
    <signal name="ToastBurnt" sessioncast="true">
      <description language="en">Toast is burnt</description>
      <description language="fr">Toast est brûlé</description>
    </signal>
    <method name="StartToasting">
      <description language="en">Start toasting</description>
      <description language="fr">Lancer grillage</description>
    </method>
    <method name="StopToasting">
      <description language="en">Stop toasting</description>
      <description language="fr">Arrêtez de grillage</description>
    </method>
    <property name="DarknessLevel" type="y" access="readwrite">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">Toasting darkness level</description>
      <description language="fr">Grillage niveau de l'obscurité</description>
    </property>
  </interface>
</node>
```

## <a name="creating-an-alljoyn-project"></a>Crear un proyecto AllJoyn

Cree un proyecto de la forma habitual: Haga `File->New->New Project` clic para comenzar.

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

En lugar de navegar a una plantilla universal de Windows, seleccione la plantilla "aplicación AllJoyn" para el idioma de destino que se instaló con la extensión.  Asigne un nombre al proyecto y elija una ubicación de archivo para empezar a desarrollar.

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

Inmediatamente después de seleccionar una plantilla de aplicación AllJoyn, Visual Studio le pedirá que seleccione las interfaces AllJoyn que desea incluir en el proyecto. 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__Extracción de interfaces de un dispositivo en la red__

Si no encuentra el dispositivo AllJoyn o la interfaz en la red, siga [esta guía](AllJoynTroubleshooting.md) para solucionar los problemas. 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

Para consultar las interfaces expuestas de la red, seleccione "productores en la red" en el panel izquierdo. Esto encontrará cualquier productor de AllJoyn en la red y mostrará las interfaces que admiten.

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

Seleccione las interfaces que le gustaría incluir en el proyecto.  En este caso, solo se usa la interfaz de tostador, por lo que seleccionamos solo la interfaz "org. alljoyn. example. tostador".

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

La columna "acciones" describe los cambios pendientes en el proyecto y muestra "agregar" para las interfaces recién seleccionadas. Aquí hemos proporcionado a la interfaz un nombre descriptivo de "ToasterLibrary", que desencadena la acción "rename" que se va a aplicar.

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__Cargar XML desde un archivo__

Elija cualquier número de archivos XML introspección a través del botón "examinar" para ver las interfaces contenidas.

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

Vaya a y seleccione el XML adecuado (aquí, vamos a usar tostador. xml).

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

Una vez que AllJoyn® Studio carga el XML, analizará las distintas interfaces y las descripciones que contiene, lo que le permitirá seleccionar las interfaces que le gustaría admitir.

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

La columna "acciones" describe los cambios pendientes en el proyecto y muestra "agregar" para las interfaces recién seleccionadas.

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

Aquí hemos optado por incluir la interfaz "org. alljoyn. example. tostador" y haber dado un nombre descriptivo de "ToasterLibrary", lo que desencadena la acción de "cambiar nombre" que se va a aplicar.

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__Adición y eliminación de interfaces__

Después de completar estos pasos, los archivos generados se agregan C++ automáticamente a un componente de Windows Runtime con el nombre descriptivo anterior y se agregan como una referencia al proyecto de aplicación.  Sin embargo, el espacio de nombres de la raíz sigue siendo el mismo "org. alljoyn. example. tostador", tal y como se define en la interfaz.  Todas las clases que tienen acceso a estos componentes deben tener una cláusula "Using" para el espacio de nombres raíz del componente.

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_TIP Cree los componentes generados ahora para beneficiarse de IntelliSense._

Después de crear la solución de la aplicación AllJoyn, siempre puede volver atrás y modificar las interfaces que está usando. En la barra de menús principal, haga clic en "AllJoyn-> Agregar o quitar interfaces..." para iniciar el administrador de la interfaz.

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

Desde aquí, puede hacer clic en "examinar..." para agregar más archivos XML o anular la selección de las interfaces existentes. La anulación de la selección de una interfaz actualiza su acción a "quitar" y, al hacer clic en el botón Aceptar, se quita el componente de Windows Runtime asociado de la solución.

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

Al examinar el Explorador de soluciones, se ha quitado el componente de Windows Runtime.

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>Pasos siguientes

Al implementar la funcionalidad AllJoyn, asegúrese siempre de incluir el espacio de nombres "Windows. Devices. AllJoyn" así como el espacio de nombres de la interfaz que desea usar.

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__Implementar un consumidor AllJoyn__

El código generado para las interfaces contiene un monitor y una clase de consumidor que se usa para buscar y después controlar un productor. Implemente el monitor mediante la creación de un nuevo AllJoynBusAttachment, inicialice el monitor con ese AllJoynBusAttachment, Regístrese para que el monitor busque un productor (el evento "agregado") y, a continuación, inicie el monitor.

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

El evento ToasterWatcher_Added se desencadena cuando el monitor encuentra un productor.  Utilice este evento para registrar un consumidor. Tenga en cuenta que Visual Studio generará el método de Shell necesario a través de las acciones rápidas.

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

Al generar el método, se genera el siguiente código de Shell:

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

Al rellenar el código de Shell con la lógica correcta se habilita el registro del consumidor.

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

Tenga en cuenta que este evento se desencadena cada vez que el monitor detecta un productor.  Si espera encontrar varios productores, mantenga una estructura de datos del consumidor, ya que habrá un consumidor para cada productor.

Registrar eventos para las distintas señales que emitirá el productor: las señales cambiadas de propiedad son miembros directos de la clase de consumidor, pero otras señales son miembros de la clase Signals (al igual que antes, use las acciones rápidas para generar el código de Shell para estos eventos).

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

Use el objeto de consumidor para leer y escribir propiedades, así como para llamar a métodos.

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>Implementar un productor de AllJoyn

__Implementar el servicio__

Los productores implementan un servicio que expone sus interfaces.  Para implementar un productor, cree primero una clase para su servicio.

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

Agregue el espacio de nombres de la interfaz a las instrucciones "Using" y, a continuación, herede la interfaz de Shell generada para el servicio y use la acción rápida para implementar la clase.

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

Desde aquí, la acción rápida rellenará los componentes necesarios.

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

Todas las partes necesarias del código están listas para funcionar, pero todavía necesita implementar la lógica real para cada llamada de método y propiedad.

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

Tomando el SetDarknessLevelAsync como ejemplo, usamos una tarea para crear un resultado correcto.  En caso de error, devuelva ToasterSetDarknessLevelResult. CreateFailureResult ().

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

Implemente el resto de las llamadas de método y propiedad para finalizar el servicio.

__Implementación del productor__

La creación del productor es sencilla: cree un nuevo AllJoynBusAttachment, inicialice un productor con ese AllJoynBusAttachment, inicialice el servicio recién creado para el productor y luego inicie el productor.

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

Dado que el servicio contiene la mayoría de la lógica, la funcionalidad principal que queda para implementar es enviar las señales de los cambios de propiedad y las señales discretas para los eventos sin estado.  Impleméntelo según sea necesario a través de llamadas a métodos.

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__Más información__

Si ha completado correctamente todas las instrucciones de este documento, está listo para empezar a escribir código AllJoyn en la aplicación.

Como referencia, consulte los ejemplos de aplicaciones universales de Windows de AllJoyn en el ejemplo de GitHub de Microsoft para [productores de alljoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) y [consumidores de alljoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).

Para obtener un tutorial detallado sobre cómo crear una aplicación AllJoyn, vea la sesión de AllJoyn 623:

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

Tenga en cuenta que la comunicación de AllJoyn entre dos aplicaciones UWP en el mismo equipo está deshabilitada por la Directiva de Windows a menos que haya habilitado una excepción de bucle invertido, por ejemplo, cuando se implementa directamente desde Visual Studio.  Para obtener instrucciones detalladas sobre cómo habilitar la exención de bucle invertido, consulte [aquí](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).



