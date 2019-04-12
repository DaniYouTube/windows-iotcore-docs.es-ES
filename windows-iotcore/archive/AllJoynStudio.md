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
> <span data-ttu-id="81240-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="81240-104">You are viewing archived documentation.</span></span> <span data-ttu-id="81240-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="81240-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="81240-106">Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.</span><span class="sxs-lookup"><span data-stu-id="81240-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="81240-107">Uso de la extensión de AllJoyn Studio</span><span class="sxs-lookup"><span data-stu-id="81240-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="81240-108">El [AllSeen Alliance](https://allseenalliance.org/) creado AllJoyn para permitir que el Internet de las cosas.</span><span class="sxs-lookup"><span data-stu-id="81240-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="81240-109">Windows 10 tiene AllJoyn incorporada de forma nativa en su plataforma, lo que permite a los desarrolladores aprovechar fácilmente de AllJoyn a las aplicaciones "IoT-enable" Windows 10.</span><span class="sxs-lookup"><span data-stu-id="81240-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="81240-110">En este artículo se describe los pasos necesarios para crear aplicaciones para Windows 10 con las APIs de AllJoyn de plataforma Universal de Windows (UWP) y Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extensión.</span><span class="sxs-lookup"><span data-stu-id="81240-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="81240-111">Descripción de desarrollo de aplicaciones UWP AllJoyn</span><span class="sxs-lookup"><span data-stu-id="81240-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="81240-112">Aplicaciones de UWP AllJoyn de formulario de tres componentes principales:</span><span class="sxs-lookup"><span data-stu-id="81240-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="81240-113">Diseño de la aplicación y diseño (XAML o HTML) y los componentes de la clase (C#, JavaScript, C++, o VB).</span><span class="sxs-lookup"><span data-stu-id="81240-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="81240-114">Las API de AllJoyn principales: AllJoyn Standard Client API (C) y Windows.Devices.AllJoyn API (WinRT) disponible en el SDK de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="81240-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="81240-115">Uno o más componentes de tiempo de ejecución de Windows de UWP (la genera este código a partir de las interfaces de AllJoyn).</span><span class="sxs-lookup"><span data-stu-id="81240-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="81240-116">El siguiente diagrama muestra la arquitectura de un proyecto típico de AllJoyn UWP:</span><span class="sxs-lookup"><span data-stu-id="81240-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="81240-118">Las aplicaciones para UWP habilitados para AllJoyn pueden ser cualquiera de los productores (implementar y exponer interfaces, normalmente un dispositivo), los consumidores (usar interfaces, normalmente las aplicaciones), o ambos.</span><span class="sxs-lookup"><span data-stu-id="81240-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="81240-119">Los consumidores y productores comparten los mismos pasos iniciales, solo divergentes en los detalles de implementación.</span><span class="sxs-lookup"><span data-stu-id="81240-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="81240-120">Creación de una aplicación UWP habilitados para AllJoyn</span><span class="sxs-lookup"><span data-stu-id="81240-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="81240-121">Siga estos pasos para desarrollar aplicaciones para UWP habilitados para AllJoyn para Windows 10: (se explica en detalle más adelante en este documento)</span><span class="sxs-lookup"><span data-stu-id="81240-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="81240-122">Prepare el entorno de compilación.</span><span class="sxs-lookup"><span data-stu-id="81240-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="81240-123">Determine qué AllJoyn interfaces se usará y obtener o creación XML introspección necesario.</span><span class="sxs-lookup"><span data-stu-id="81240-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="81240-124">Crear un proyecto de AllJoyn App, a continuación, seleccione introspección XML e Interfaces deseadas para la generación de código.</span><span class="sxs-lookup"><span data-stu-id="81240-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="81240-125">Implementar el código de productor o ponsumer en su aplicación mediante las API expuestas desde los componentes de tiempo de ejecución de Windows de UWP generado.</span><span class="sxs-lookup"><span data-stu-id="81240-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="81240-126">Crear la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="81240-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="81240-127">Preparar el entorno de compilación</span><span class="sxs-lookup"><span data-stu-id="81240-127">Preparing your Build Environment</span></span>

<span data-ttu-id="81240-128">La compilación de Windows 10 y herramientas relacionadas incluyen todos los recursos que necesitará para escribir aplicaciones para UWP habilitados para AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="81240-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="81240-129">Aquí es lo que deberá hacer antes de empezar a escribir código:</span><span class="sxs-lookup"><span data-stu-id="81240-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="81240-130">Instalar [Windows 10](https://www.microsoft.com/windows/) en un equipo</span><span class="sxs-lookup"><span data-stu-id="81240-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="81240-131">Instalar [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (no utilice una edición Express)</span><span class="sxs-lookup"><span data-stu-id="81240-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="81240-132">Descargue el [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extensión desde la Galería de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81240-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="81240-133">Obtención de introspección XML para las Interfaces de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="81240-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="81240-134">Hay tres modos en que puede obtener las definiciones de interfaz de AllJoyn que necesitará para iniciar el proyecto:</span><span class="sxs-lookup"><span data-stu-id="81240-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="81240-135">Extraiga el XML de introspección AllJoyn productores presentes en la red en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="81240-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="81240-136">Obtener el XML de introspección documentación; ejemplo: [Documentación del marco de trabajo de servicio (LSF) de iluminación](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) de AllSeen Alliance.</span><span class="sxs-lookup"><span data-stu-id="81240-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="81240-137">Crear su propio XML introspección que sea compatible con la AllJoyn /[introspección D Bus](http://dbus.freedesktop.org/doc/dbus-specification.html) formato.</span><span class="sxs-lookup"><span data-stu-id="81240-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="81240-138">Este artículo trata el primero de dos maneras: AllJoyn® Studio admite de forma nativa consultando la red para los productores AllJoyn y extraer su código XML, así como cargar archivos XML de introspección.</span><span class="sxs-lookup"><span data-stu-id="81240-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="81240-139">Aprenda a crear su propio [aquí](AllJoynProducer.md).</span><span class="sxs-lookup"><span data-stu-id="81240-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="81240-140">Un dispositivo habilitados para AllJoyn toaster servirá como el ejemplo de esta publicación.</span><span class="sxs-lookup"><span data-stu-id="81240-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="81240-141">Este toaster expone controles para iniciar y detener la secuencia, configuración de la "oscuridad" y notificaciones toasting cuando está quemado el toast.</span><span class="sxs-lookup"><span data-stu-id="81240-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="81240-143">El toaster expone el siguiente código XML:</span><span class="sxs-lookup"><span data-stu-id="81240-143">The toaster exposes the following XML:</span></span>

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

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="81240-144">Creación de un proyecto de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="81240-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="81240-145">Cree un proyecto tal como lo haría normalmente: Haga clic en `File->New->New Project` para comenzar.</span><span class="sxs-lookup"><span data-stu-id="81240-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="81240-147">En lugar de navegar a una plantilla de Universal de Windows, seleccione la plantilla "Aplicación AllJoyn" para el idioma de destino que se instaló con la extensión.</span><span class="sxs-lookup"><span data-stu-id="81240-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="81240-148">Nombre del proyecto y elija una ubicación de archivo para empezar a desarrollar.</span><span class="sxs-lookup"><span data-stu-id="81240-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="81240-150">Inmediatamente después de seleccionar una AllJoyn App Template, Visual Studio le pedirá que seleccione las Interfaces de AllJoyn que le gustaría incluir en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="81240-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

__<span data-ttu-id="81240-152">Extraer las interfaces de un dispositivo en la red</span><span class="sxs-lookup"><span data-stu-id="81240-152">Extracting interfaces from a device on the network</span></span>__

<span data-ttu-id="81240-153">Si no se encuentra el dispositivo de AllJoyn o interfaz en la red, siga [esta guía](AllJoynTroubleshooting.md) para solucionar problemas.</span><span class="sxs-lookup"><span data-stu-id="81240-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="81240-155">Para consultar la red para las interfaces expuestas, seleccione los productores de"en la red" en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="81240-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="81240-156">Este modo buscará a cualquier productor AllJoyn en la red y la lista de las interfaces que admiten.</span><span class="sxs-lookup"><span data-stu-id="81240-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="81240-158">Seleccione las interfaces que le gustaría incluir en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="81240-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="81240-159">En este caso, sólo usamos la interfaz toaster, así que seleccionamos la interfaz "org.alljoyn.example.Toaster".</span><span class="sxs-lookup"><span data-stu-id="81240-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="81240-161">La columna "Acciones" describe los cambios pendientes al proyecto, mostrar "Agregar" para las Interfaces recién seleccionado.</span><span class="sxs-lookup"><span data-stu-id="81240-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="81240-162">Aquí hemos incorporado la interfaz de un nombre descriptivo de "ToasterLibrary", lo que desencadena la acción "Rename" que se aplicará.</span><span class="sxs-lookup"><span data-stu-id="81240-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

__<span data-ttu-id="81240-164">Cargar un archivo XML de un archivo</span><span class="sxs-lookup"><span data-stu-id="81240-164">Loading an XML from a File</span></span>__

<span data-ttu-id="81240-165">Elija cualquier número de archivos XML de introspección a través del botón "Examinar" para ver sus interfaces independientes.</span><span class="sxs-lookup"><span data-stu-id="81240-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="81240-167">Vaya a y seleccione el código XML adecuado (en este caso, estamos usando toaster.xml).</span><span class="sxs-lookup"><span data-stu-id="81240-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="81240-169">Una vez AllJoyn® Studio carga el XML, analizará las diversas Interfaces y las descripciones que contiene, lo que le permite seleccionar qué Interfaces que le gustaría admitir.</span><span class="sxs-lookup"><span data-stu-id="81240-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="81240-171">La columna "Acciones" describe los cambios pendientes al proyecto, mostrar "Agregar" para las Interfaces recién seleccionado.</span><span class="sxs-lookup"><span data-stu-id="81240-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="81240-173">Aquí hemos elegido incluir la interfaz "org.alljoyn.example.Toaster" y ha dado un nombre descriptivo de "ToasterLibrary", desencadena la acción "Rename" que se aplicará.</span><span class="sxs-lookup"><span data-stu-id="81240-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

__<span data-ttu-id="81240-175">Adición y eliminación de Interfaces</span><span class="sxs-lookup"><span data-stu-id="81240-175">Adding and Removing Interfaces</span></span>__

<span data-ttu-id="81240-176">Después de completar estos pasos, los archivos generados se agregan automáticamente a un C++ componente de Windows en tiempo de ejecución con el nombre descriptivo del anterior y se ha agregado como una referencia a la aplicación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="81240-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="81240-177">Sin embargo, la raíz de Namespace sigue siendo el mismo "org.alljoyn.example.Toaster" como definidos por la interfaz.</span><span class="sxs-lookup"><span data-stu-id="81240-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="81240-178">Todas las clases que tienen acceso a estos componentes deben tener una cláusula "using" para el espacio de nombres del componente raíz.</span><span class="sxs-lookup"><span data-stu-id="81240-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

_<span data-ttu-id="81240-180">PROPINA: Compilar los componentes generados ahora para beneficiarse de IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="81240-180">TIP: Build the generated components now in order to benefit from IntelliSense.</span></span>_

<span data-ttu-id="81240-181">Después de haber creado la solución de AllJoyn App, siempre puede volver atrás y modificar las interfaces que está usando.</span><span class="sxs-lookup"><span data-stu-id="81240-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="81240-182">En la barra de menú principal, haga clic en "AllJoyn -> Agregar o quitar Interfaces..." Para iniciar el Administrador de interfaz.</span><span class="sxs-lookup"><span data-stu-id="81240-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="81240-184">Desde aquí, puede hacer clic en "Examinar..." Para agregar más archivos XML, o anule la selección de las interfaces existentes.</span><span class="sxs-lookup"><span data-stu-id="81240-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="81240-185">Anulando la selección de una interfaz de las actualizaciones su acción para "Quitar" y haga clic en el botón Aceptar quita el componente de tiempo de ejecución de Windows asociado de la solución.</span><span class="sxs-lookup"><span data-stu-id="81240-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="81240-187">Examinando el Explorador de soluciones, se ha quitado el componente de Windows en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="81240-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="81240-189">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="81240-189">Next Steps</span></span>

<span data-ttu-id="81240-190">Al implementar la funcionalidad de AllJoyn, siempre debe incluir el espacio de nombres "Windows.Devices.AllJoyn", así como el espacio de nombres de la interfaz que desea usar.</span><span class="sxs-lookup"><span data-stu-id="81240-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

__<span data-ttu-id="81240-192">Implementación de un consumidor AllJoyn</span><span class="sxs-lookup"><span data-stu-id="81240-192">Implementing an AllJoyn Consumer</span></span>__

<span data-ttu-id="81240-193">El código generado para las interfaces contiene una clase de monitor y el consumidor utilizada para buscar y, a continuación, controlar un productor.</span><span class="sxs-lookup"><span data-stu-id="81240-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="81240-194">Implementa el monitor mediante la creación de un nuevo AllJoynBusAttachment, inicializar el monitor con ese AllJoynBusAttachment, registrarse para el Monitor de búsqueda de productores (el evento "Agregado") y luego iniciar el monitor.</span><span class="sxs-lookup"><span data-stu-id="81240-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="81240-196">Los desencadenadores de eventos ToasterWatcher_Added cada vez que el monitor busca un productor.</span><span class="sxs-lookup"><span data-stu-id="81240-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="81240-197">Use este evento para registrar un consumidor.</span><span class="sxs-lookup"><span data-stu-id="81240-197">Use this event to register a consumer.</span></span> <span data-ttu-id="81240-198">Tenga en cuenta que Visual Studio generará el método de shell necesarias a través de las acciones rápidas.</span><span class="sxs-lookup"><span data-stu-id="81240-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="81240-200">Generar el método genera el siguiente código de shell:</span><span class="sxs-lookup"><span data-stu-id="81240-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="81240-202">Rellenar en el código de shell con la lógica correcto permite registrar el consumidor.</span><span class="sxs-lookup"><span data-stu-id="81240-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="81240-204">Tenga en cuenta que este evento se desencadena cada vez que el monitor detecta un productor.</span><span class="sxs-lookup"><span data-stu-id="81240-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="81240-205">Si se espera encontrar varios productores, mantenga una estructura de datos del consumidor ya habrá un consumidor para cada productor.</span><span class="sxs-lookup"><span data-stu-id="81240-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="81240-206">Registrar eventos de diversas señales que se emitirá el productor: cambiada de propiedad señales son miembros directos de la clase de consumidor, pero otras señales son miembros de la clase de las señales (igual que antes, use las acciones rápidas para generar el código de shell para estos eventos).</span><span class="sxs-lookup"><span data-stu-id="81240-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="81240-208">Utilice el objeto de consumidores para leer y escribir propiedades así como llamar a métodos.</span><span class="sxs-lookup"><span data-stu-id="81240-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="81240-210">Implementar un productor AllJoyn</span><span class="sxs-lookup"><span data-stu-id="81240-210">Implementing an AllJoyn Producer</span></span>

__<span data-ttu-id="81240-211">Implementa el servicio</span><span class="sxs-lookup"><span data-stu-id="81240-211">Implementing the Service</span></span>__

<span data-ttu-id="81240-212">Productores de implementan un servicio que exponen sus interfaces.</span><span class="sxs-lookup"><span data-stu-id="81240-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="81240-213">Para implementar un productor, cree primero una clase para su servicio.</span><span class="sxs-lookup"><span data-stu-id="81240-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="81240-215">Agregue el espacio de nombres para la interfaz para las instrucciones "using", a continuación, heredar la interfaz de shell que se generó para el servicio y use la acción rápida para implementar la clase.</span><span class="sxs-lookup"><span data-stu-id="81240-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="81240-217">Desde aquí, la acción rápida rellenará los componentes necesarios.</span><span class="sxs-lookup"><span data-stu-id="81240-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="81240-219">Todos los elementos pertinentes del código están listos para funcionar, pero debe implementar la lógica real para cada llamada de método y propiedad.</span><span class="sxs-lookup"><span data-stu-id="81240-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="81240-221">Llevar a cabo la SetDarknessLevelAsync como ejemplo, utilice una tarea para crear un resultado correcto.</span><span class="sxs-lookup"><span data-stu-id="81240-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="81240-222">En caso de error, devuelve ToasterSetDarknessLevelResult.CreateFailureResult().</span><span class="sxs-lookup"><span data-stu-id="81240-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="81240-224">Implementar el resto de las llamadas de método y propiedad a finalizar el servicio.</span><span class="sxs-lookup"><span data-stu-id="81240-224">Implement the rest of the method and property calls to finish the service.</span></span>

__<span data-ttu-id="81240-225">Implementar el productor</span><span class="sxs-lookup"><span data-stu-id="81240-225">Implementing the Producer</span></span>__

<span data-ttu-id="81240-226">Crear el productor es sencillo: crear un nuevo AllJoynBusAttachment, inicialice un productor con ese AllJoynBusAttachment, inicializar el servicio recién creado para el productor y luego iniciará el productor.</span><span class="sxs-lookup"><span data-stu-id="81240-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="81240-228">Puesto que el servicio contiene la mayor parte de la lógica, la funcionalidad principal para implementar consiste en enviar señales discretas para eventos de estado no y las señales de los cambios de propiedad.</span><span class="sxs-lookup"><span data-stu-id="81240-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="81240-229">Implemente estas según sea necesario mediante llamadas a métodos.</span><span class="sxs-lookup"><span data-stu-id="81240-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

__<span data-ttu-id="81240-231">Más información</span><span class="sxs-lookup"><span data-stu-id="81240-231">More Information</span></span>__

<span data-ttu-id="81240-232">Si ha completado todas las instrucciones de este documento correctamente, está listo para empezar a escribir código AllJoyn en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="81240-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="81240-233">Como referencia, consulte los ejemplos de aplicaciones universales de Windows de AllJoyn en GitHub de ejemplo de Microsoft para [AllJoyn productores](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) y [AllJoyn consumidores](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span><span class="sxs-lookup"><span data-stu-id="81240-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="81240-234">Para obtener un tutorial detallado de cómo crear una aplicación de AllJoyn, vea la sesión de AllJoyn 623:</span><span class="sxs-lookup"><span data-stu-id="81240-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="81240-235">Tenga en cuenta que AllJoyn la comunicación entre dos aplicaciones para UWP en la misma máquina está deshabilitada por directivas de Windows, a menos que ha habilitado una excepción de bucle invertido, por ejemplo, cuando se implementa directamente desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81240-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="81240-236">Para obtener instrucciones detalladas sobre cómo habilitar la exención de bucle invertido, consulte [aquí](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span><span class="sxs-lookup"><span data-stu-id="81240-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



