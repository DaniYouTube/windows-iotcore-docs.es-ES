---
title: AllJoyn Studio
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo crear una aplicación de UWP de AllJoyn con la plataforma Universal de Windows (UWP) AllJoyn APIs y Visual Studio 2017.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 5326873218c0126b918679308e3a8e08cdddf84c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514963"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="using-the-alljoyn-studio-extension"></a>Uso de la extensión de AllJoyn Studio

El [AllSeen Alliance](https://allseenalliance.org/) creado AllJoyn para permitir que el Internet de las cosas. Windows 10 tiene AllJoyn incorporada de forma nativa en su plataforma, lo que permite a los desarrolladores aprovechar fácilmente de AllJoyn a las aplicaciones "IoT-enable" Windows 10. En este artículo se describe los pasos necesarios para crear aplicaciones para Windows 10 con las APIs de AllJoyn de plataforma Universal de Windows (UWP) y Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extensión.

## <a name="understanding-alljoyn-uwp-app-development"></a>Descripción de desarrollo de aplicaciones UWP AllJoyn

Aplicaciones de UWP AllJoyn de formulario de tres componentes principales:

1. Diseño de la aplicación y diseño (XAML o HTML) y los componentes de la clase (C#, JavaScript, C++, o VB).
2. Las API de AllJoyn principales: AllJoyn Standard Client API (C) y Windows.Devices.AllJoyn API (WinRT) disponible en el SDK de Windows 10.
3. Uno o más componentes de tiempo de ejecución de Windows de UWP (la genera este código a partir de las interfaces de AllJoyn).

El siguiente diagrama muestra la arquitectura de un proyecto típico de AllJoyn UWP:

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

Las aplicaciones para UWP habilitados para AllJoyn pueden ser cualquiera de los productores (implementar y exponer interfaces, normalmente un dispositivo), los consumidores (usar interfaces, normalmente las aplicaciones), o ambos. Los consumidores y productores comparten los mismos pasos iniciales, solo divergentes en los detalles de implementación.

## <a name="creating-an-alljoyn-enabled-uwp-app"></a>Creación de una aplicación UWP habilitados para AllJoyn

Siga estos pasos para desarrollar aplicaciones para UWP habilitados para AllJoyn para Windows 10: (se explica en detalle más adelante en este documento)

1. Prepare el entorno de compilación.
2. Determine qué AllJoyn interfaces se usará y obtener o creación XML introspección necesario.
3. Crear un proyecto de AllJoyn App, a continuación, seleccione introspección XML e Interfaces deseadas para la generación de código.
4. Implementar el código de productor o ponsumer en su aplicación mediante las API expuestas desde los componentes de tiempo de ejecución de Windows de UWP generado.
5. Crear la interfaz de usuario.

## <a name="preparing-your-build-environment"></a>Preparar el entorno de compilación

La compilación de Windows 10 y herramientas relacionadas incluyen todos los recursos que necesitará para escribir aplicaciones para UWP habilitados para AllJoyn.

Aquí es lo que deberá hacer antes de empezar a escribir código:

* Instalar [Windows 10](https://www.microsoft.com/windows/) en un equipo
* Instalar [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (no utilice una edición Express)
* Descargue el [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extensión desde la Galería de Visual Studio. 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a>Obtención de introspección XML para las Interfaces de AllJoyn

Hay tres modos en que puede obtener las definiciones de interfaz de AllJoyn que necesitará para iniciar el proyecto:

1. Extraiga el XML de introspección AllJoyn productores presentes en la red en tiempo de ejecución.
2. Obtener el XML de introspección documentación; ejemplo: [Documentación del marco de trabajo de servicio (LSF) de iluminación](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) de AllSeen Alliance.
3. Crear su propio XML introspección que sea compatible con la AllJoyn /[introspección D Bus](http://dbus.freedesktop.org/doc/dbus-specification.html) formato.

Este artículo trata el primero de dos maneras: AllJoyn® Studio admite de forma nativa consultando la red para los productores AllJoyn y extraer su código XML, así como cargar archivos XML de introspección.  Aprenda a crear su propio [aquí](AllJoynProducer.md).

Un dispositivo habilitados para AllJoyn toaster servirá como el ejemplo de esta publicación. Este toaster expone controles para iniciar y detener la secuencia, configuración de la "oscuridad" y notificaciones toasting cuando está quemado el toast.

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

El toaster expone el siguiente código XML:

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

## <a name="creating-an-alljoyn-project"></a>Creación de un proyecto de AllJoyn

Cree un proyecto tal como lo haría normalmente: Haga clic en `File->New->New Project` para comenzar.

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

En lugar de navegar a una plantilla de Universal de Windows, seleccione la plantilla "Aplicación AllJoyn" para el idioma de destino que se instaló con la extensión.  Nombre del proyecto y elija una ubicación de archivo para empezar a desarrollar.

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

Inmediatamente después de seleccionar una AllJoyn App Template, Visual Studio le pedirá que seleccione las Interfaces de AllJoyn que le gustaría incluir en el proyecto. 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__Extraer las interfaces de un dispositivo en la red__

Si no se encuentra el dispositivo de AllJoyn o interfaz en la red, siga [esta guía](AllJoynTroubleshooting.md) para solucionar problemas. 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

Para consultar la red para las interfaces expuestas, seleccione los productores de"en la red" en el panel izquierdo. Este modo buscará a cualquier productor AllJoyn en la red y la lista de las interfaces que admiten.

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

Seleccione las interfaces que le gustaría incluir en el proyecto.  En este caso, sólo usamos la interfaz toaster, así que seleccionamos la interfaz "org.alljoyn.example.Toaster".

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

La columna "Acciones" describe los cambios pendientes al proyecto, mostrar "Agregar" para las Interfaces recién seleccionado. Aquí hemos incorporado la interfaz de un nombre descriptivo de "ToasterLibrary", lo que desencadena la acción "Rename" que se aplicará.

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__Cargar un archivo XML de un archivo__

Elija cualquier número de archivos XML de introspección a través del botón "Examinar" para ver sus interfaces independientes.

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

Vaya a y seleccione el código XML adecuado (en este caso, estamos usando toaster.xml).

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

Una vez AllJoyn® Studio carga el XML, analizará las diversas Interfaces y las descripciones que contiene, lo que le permite seleccionar qué Interfaces que le gustaría admitir.

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

La columna "Acciones" describe los cambios pendientes al proyecto, mostrar "Agregar" para las Interfaces recién seleccionado.

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

Aquí hemos elegido incluir la interfaz "org.alljoyn.example.Toaster" y ha dado un nombre descriptivo de "ToasterLibrary", desencadena la acción "Rename" que se aplicará.

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__Adición y eliminación de Interfaces__

Después de completar estos pasos, los archivos generados se agregan automáticamente a un C++ componente de Windows en tiempo de ejecución con el nombre descriptivo del anterior y se ha agregado como una referencia a la aplicación del proyecto.  Sin embargo, la raíz de Namespace sigue siendo el mismo "org.alljoyn.example.Toaster" como definidos por la interfaz.  Todas las clases que tienen acceso a estos componentes deben tener una cláusula "using" para el espacio de nombres del componente raíz.

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_PROPINA: Compilar los componentes generados ahora para beneficiarse de IntelliSense._

Después de haber creado la solución de AllJoyn App, siempre puede volver atrás y modificar las interfaces que está usando. En la barra de menú principal, haga clic en "AllJoyn -> Agregar o quitar Interfaces..." Para iniciar el Administrador de interfaz.

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

Desde aquí, puede hacer clic en "Examinar..." Para agregar más archivos XML, o anule la selección de las interfaces existentes. Anulando la selección de una interfaz de las actualizaciones su acción para "Quitar" y haga clic en el botón Aceptar quita el componente de tiempo de ejecución de Windows asociado de la solución.

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

Examinando el Explorador de soluciones, se ha quitado el componente de Windows en tiempo de ejecución.

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a>Pasos siguientes

Al implementar la funcionalidad de AllJoyn, siempre debe incluir el espacio de nombres "Windows.Devices.AllJoyn", así como el espacio de nombres de la interfaz que desea usar.

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__Implementación de un consumidor AllJoyn__

El código generado para las interfaces contiene una clase de monitor y el consumidor utilizada para buscar y, a continuación, controlar un productor. Implementa el monitor mediante la creación de un nuevo AllJoynBusAttachment, inicializar el monitor con ese AllJoynBusAttachment, registrarse para el Monitor de búsqueda de productores (el evento "Agregado") y luego iniciar el monitor.

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

Los desencadenadores de eventos ToasterWatcher_Added cada vez que el monitor busca un productor.  Use este evento para registrar un consumidor. Tenga en cuenta que Visual Studio generará el método de shell necesarias a través de las acciones rápidas.

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

Generar el método genera el siguiente código de shell:

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

Rellenar en el código de shell con la lógica correcto permite registrar el consumidor.

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

Tenga en cuenta que este evento se desencadena cada vez que el monitor detecta un productor.  Si se espera encontrar varios productores, mantenga una estructura de datos del consumidor ya habrá un consumidor para cada productor.

Registrar eventos de diversas señales que se emitirá el productor: cambiada de propiedad señales son miembros directos de la clase de consumidor, pero otras señales son miembros de la clase de las señales (igual que antes, use las acciones rápidas para generar el código de shell para estos eventos).

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

Utilice el objeto de consumidores para leer y escribir propiedades así como llamar a métodos.

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a>Implementar un productor AllJoyn

__Implementa el servicio__

Productores de implementan un servicio que exponen sus interfaces.  Para implementar un productor, cree primero una clase para su servicio.

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

Agregue el espacio de nombres para la interfaz para las instrucciones "using", a continuación, heredar la interfaz de shell que se generó para el servicio y use la acción rápida para implementar la clase.

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

Desde aquí, la acción rápida rellenará los componentes necesarios.

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

Todos los elementos pertinentes del código están listos para funcionar, pero debe implementar la lógica real para cada llamada de método y propiedad.

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

Llevar a cabo la SetDarknessLevelAsync como ejemplo, utilice una tarea para crear un resultado correcto.  En caso de error, devuelve ToasterSetDarknessLevelResult.CreateFailureResult().

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

Implementar el resto de las llamadas de método y propiedad a finalizar el servicio.

__Implementar el productor__

Crear el productor es sencillo: crear un nuevo AllJoynBusAttachment, inicialice un productor con ese AllJoynBusAttachment, inicializar el servicio recién creado para el productor y luego iniciará el productor.

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

Puesto que el servicio contiene la mayor parte de la lógica, la funcionalidad principal para implementar consiste en enviar señales discretas para eventos de estado no y las señales de los cambios de propiedad.  Implemente estas según sea necesario mediante llamadas a métodos.

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__Más información__

Si ha completado todas las instrucciones de este documento correctamente, está listo para empezar a escribir código AllJoyn en la aplicación.

Como referencia, consulte los ejemplos de aplicaciones universales de Windows de AllJoyn en GitHub de ejemplo de Microsoft para [AllJoyn productores](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) y [AllJoyn consumidores](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).

Para obtener un tutorial detallado de cómo crear una aplicación de AllJoyn, vea la sesión de AllJoyn 623:

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

Tenga en cuenta que AllJoyn la comunicación entre dos aplicaciones para UWP en la misma máquina está deshabilitada por directivas de Windows, a menos que ha habilitado una excepción de bucle invertido, por ejemplo, cuando se implementa directamente desde Visual Studio.  Para obtener instrucciones detalladas sobre cómo habilitar la exención de bucle invertido, consulte [aquí](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).



