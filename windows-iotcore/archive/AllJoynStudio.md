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
> <span data-ttu-id="6bad7-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="6bad7-104">You are viewing archived documentation.</span></span> <span data-ttu-id="6bad7-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="6bad7-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="6bad7-106">Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.</span><span class="sxs-lookup"><span data-stu-id="6bad7-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="using-the-alljoyn-studio-extension"></a><span data-ttu-id="6bad7-107">Usar la extensión de Studio AllJoyn</span><span class="sxs-lookup"><span data-stu-id="6bad7-107">Using the AllJoyn Studio Extension</span></span>

<span data-ttu-id="6bad7-108">La [Alianza de AllSeen](https://allseenalliance.org/) creó AllJoyn para potenciar el Internet de las cosas.</span><span class="sxs-lookup"><span data-stu-id="6bad7-108">The [AllSeen Alliance](https://allseenalliance.org/) created AllJoyn to empower the Internet of Things.</span></span> <span data-ttu-id="6bad7-109">Windows 10 tiene AllJoyn compilado de forma nativa en su plataforma, lo que permite a los desarrolladores aprovechar con facilidad de AllJoyn para "habilitar IoT" las aplicaciones de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6bad7-109">Windows 10 has AllJoyn built natively into its platform, allowing developers to easily take advantage of AllJoyn to "IoT-enable" your Windows 10 apps.</span></span> <span data-ttu-id="6bad7-110">En este artículo se describen los pasos necesarios para compilar aplicaciones para Windows 10 con las API AllJoyn de Plataforma universal de Windows (UWP) y la extensión Visual Studio 2017 [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) .</span><span class="sxs-lookup"><span data-stu-id="6bad7-110">This article will outline the steps required to build apps for Windows 10 using the Universal Windows Platform (UWP) AllJoyn APIs and the Visual Studio 2017 [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension.</span></span>

## <a name="understanding-alljoyn-uwp-app-development"></a><span data-ttu-id="6bad7-111">Descripción del desarrollo de aplicaciones para UWP de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="6bad7-111">Understanding AllJoyn UWP App Development</span></span>

<span data-ttu-id="6bad7-112">Tres componentes principales forman aplicaciones de UWP de AllJoyn:</span><span class="sxs-lookup"><span data-stu-id="6bad7-112">Three major components form AllJoyn UWP apps:</span></span>

1. <span data-ttu-id="6bad7-113">Diseño y diseño de aplicaciones (XAML o HTML) y componentes deC#clase (, C++JavaScript, o VB).</span><span class="sxs-lookup"><span data-stu-id="6bad7-113">App layout and design (XAML or HTML) and class components (C#, JavaScript, C++, or VB).</span></span>
2. <span data-ttu-id="6bad7-114">Las API principales de AllJoyn: La API de cliente estándar AllJoyn (C) y Windows. Devices. AllJoyn API (WinRT) están disponibles en el SDK de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6bad7-114">The AllJoyn core APIs: AllJoyn Standard Client API (C) and Windows.Devices.AllJoyn API (WinRT)  available in the Windows 10 SDK.</span></span>
3. <span data-ttu-id="6bad7-115">Uno o varios componentes de Windows Runtime de UWP (el genera este código a partir de las interfaces AllJoyn).</span><span class="sxs-lookup"><span data-stu-id="6bad7-115">One or more UWP Windows Runtime Components (the  generates this code from AllJoyn interfaces).</span></span>

<span data-ttu-id="6bad7-116">En el diagrama siguiente se muestra la arquitectura de un proyecto de UWP de AllJoyn típico:</span><span class="sxs-lookup"><span data-stu-id="6bad7-116">The following diagram shows the architecture of a typical AllJoyn UWP project:</span></span>

![AJ_UWP_Architecture](../media/AllJoyn/AJ_UWP_Architecture.jpg)

<span data-ttu-id="6bad7-118">Las aplicaciones UWP habilitadas para AllJoyn pueden ser productores (implementar y exponer interfaces, normalmente un dispositivo), consumidores (usar interfaces, normalmente aplicaciones) o ambos.</span><span class="sxs-lookup"><span data-stu-id="6bad7-118">AllJoyn-enabled UWP apps can be either producers  (implement and expose interfaces, typically a device ), consumers (use interfaces, typically apps), or both.</span></span> <span data-ttu-id="6bad7-119">Los consumidores y productores comparten los mismos pasos de inicio, solo divergentes en los detalles de implementación.</span><span class="sxs-lookup"><span data-stu-id="6bad7-119">Consumers and producers share the same starting steps, only diverging in the implementation details.</span></span>

## <a name="creating-an-alljoyn-enabled-uwp-app"></a><span data-ttu-id="6bad7-120">Creación de una aplicación para UWP habilitada para AllJoyn</span><span class="sxs-lookup"><span data-stu-id="6bad7-120">Creating an AllJoyn-enabled UWP app</span></span>

<span data-ttu-id="6bad7-121">Siga estos pasos para desarrollar aplicaciones UWP habilitadas para AllJoyn para Windows 10: (se explica con más detalle más adelante en este documento)</span><span class="sxs-lookup"><span data-stu-id="6bad7-121">Follow these steps to develop AllJoyn-enabled UWP apps for Windows 10: (explained in detail later in this document)</span></span>

1. <span data-ttu-id="6bad7-122">Prepare el entorno de compilación.</span><span class="sxs-lookup"><span data-stu-id="6bad7-122">Prepare your build environment.</span></span>
2. <span data-ttu-id="6bad7-123">Determine qué interfaces AllJoyn se usarán y obtenga o cree el XML de introspección necesario.</span><span class="sxs-lookup"><span data-stu-id="6bad7-123">Determine which AllJoyn interfaces will be used, and obtain or create necessary Introspection XML.</span></span>
3. <span data-ttu-id="6bad7-124">Cree un proyecto de aplicación AllJoyn y seleccione introspección XML e interfaces deseadas para la generación de código.</span><span class="sxs-lookup"><span data-stu-id="6bad7-124">Create an AllJoyn App project then select Introspection XML and desired Interfaces for code generation.</span></span>
4. <span data-ttu-id="6bad7-125">Implemente el código de productor o ponsumer en la aplicación mediante las API expuestas de los componentes de Windows Runtime de UWP generados.</span><span class="sxs-lookup"><span data-stu-id="6bad7-125">Implement producer or ponsumer code in your app using APIs exposed from the generated UWP Windows Runtime Components.</span></span>
5. <span data-ttu-id="6bad7-126">Compilar la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6bad7-126">Build your UI.</span></span>

## <a name="preparing-your-build-environment"></a><span data-ttu-id="6bad7-127">Preparación del entorno de compilación</span><span class="sxs-lookup"><span data-stu-id="6bad7-127">Preparing your Build Environment</span></span>

<span data-ttu-id="6bad7-128">La compilación de Windows 10 y las herramientas relacionadas incluyen todos los recursos que necesitará para escribir aplicaciones UWP habilitadas para AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="6bad7-128">The Windows 10 build and related tools include all of the resources that you'll need to write AllJoyn-enabled UWP apps.</span></span>

<span data-ttu-id="6bad7-129">Esto es lo que debe hacer antes de empezar a escribir código:</span><span class="sxs-lookup"><span data-stu-id="6bad7-129">Here's what you'll need to do before you get started writing code:</span></span>

* <span data-ttu-id="6bad7-130">Instalación de [Windows 10](https://www.microsoft.com/windows/) en un equipo</span><span class="sxs-lookup"><span data-stu-id="6bad7-130">Install [Windows 10](https://www.microsoft.com/windows/) on a PC</span></span>
* <span data-ttu-id="6bad7-131">Instalación de [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (no use una edición Express)</span><span class="sxs-lookup"><span data-stu-id="6bad7-131">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/download-visual-studio-vs) (do NOT use an  Express edition)</span></span>
* <span data-ttu-id="6bad7-132">Descargue la extensión [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) de la galería de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bad7-132">Download the [AllJoyn® Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) Extension from the Visual Studio Gallery.</span></span> 


## <a name="obtaining-introspection-xml-for-alljoyn-interfaces"></a><span data-ttu-id="6bad7-133">Obtención de XML de introspección para interfaces AllJoyn</span><span class="sxs-lookup"><span data-stu-id="6bad7-133">Obtaining Introspection XML for AllJoyn Interfaces</span></span>

<span data-ttu-id="6bad7-134">Hay tres maneras de obtener las definiciones de la interfaz AllJoyn que necesitará para iniciar el proyecto:</span><span class="sxs-lookup"><span data-stu-id="6bad7-134">There are three ways that you can obtain the AllJoyn interface  definitions that you will need to start your project:</span></span>

1. <span data-ttu-id="6bad7-135">Extraiga el XML introspección de los productores de AllJoyn presentes en la red en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="6bad7-135">Extract the Introspection XML from AllJoyn Producers present on your network at runtime.</span></span>
2. <span data-ttu-id="6bad7-136">Obtener el XML de introspección de la documentación; ejemplo [Documentación de iluminación de la plataforma de servicio (LSF)](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) de AllSeen Alliance.</span><span class="sxs-lookup"><span data-stu-id="6bad7-136">Obtain the Introspection XML from documentation ; example: [Lighting Service Framework (LSF) documentation](https://wiki.allseenalliance.org/_media/compliance/alljoyn_lamp_service_14.06_interface_definition.pdf) from the AllSeen Alliance.</span></span>
3. <span data-ttu-id="6bad7-137">Cree su propio archivo XML de introspección que sea compatible con el formato de[introspección del bus](http://dbus.freedesktop.org/doc/dbus-specification.html) AllJoyn/D.</span><span class="sxs-lookup"><span data-stu-id="6bad7-137">Create your own Introspection XML that is compliant with the AllJoyn/[D-Bus introspection](http://dbus.freedesktop.org/doc/dbus-specification.html) format.</span></span>

<span data-ttu-id="6bad7-138">En este artículo se tratan las dos primeras maneras: AllJoyn® Studio admite de forma nativa la consulta de la red para productores de AllJoyn y la extracción de su XML, así como la carga de archivos XML introspección.</span><span class="sxs-lookup"><span data-stu-id="6bad7-138">This article covers the first two ways - AllJoyn® Studio natively supports querying the network for AllJoyn producers and extracting their XML as well as uploading Introspection XML files.</span></span>  <span data-ttu-id="6bad7-139">Aprenda a crear su propio [aquí](AllJoynProducer.md).</span><span class="sxs-lookup"><span data-stu-id="6bad7-139">Learn how to create your own [here](AllJoynProducer.md).</span></span>

<span data-ttu-id="6bad7-140">Un dispositivo tostador habilitado para AllJoyn servirá como ejemplo para esta publicación.</span><span class="sxs-lookup"><span data-stu-id="6bad7-140">An AllJoyn-enabled toaster device will serve as the example for this post.</span></span> <span data-ttu-id="6bad7-141">Este tostador expone los controles para iniciar y detener la secuencia de notificación, establecer la "oscuridad" y las notificaciones cuando se graba la notificación del sistema.</span><span class="sxs-lookup"><span data-stu-id="6bad7-141">This toaster exposes controls for starting and stopping the toasting sequence, setting the "darkness", and notifications when the toast is burnt.</span></span>

![AJ_toaster](../media/AllJoyn/AJ_toaster.jpg)

<span data-ttu-id="6bad7-143">El sistema de notificaciones expone el siguiente código XML:</span><span class="sxs-lookup"><span data-stu-id="6bad7-143">The toaster exposes the following XML:</span></span>

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

## <a name="creating-an-alljoyn-project"></a><span data-ttu-id="6bad7-144">Crear un proyecto AllJoyn</span><span class="sxs-lookup"><span data-stu-id="6bad7-144">Creating an AllJoyn Project</span></span>

<span data-ttu-id="6bad7-145">Cree un proyecto de la forma habitual: Haga `File->New->New Project` clic para comenzar.</span><span class="sxs-lookup"><span data-stu-id="6bad7-145">Create a Project the way you normally would: Click `File->New->New Project` to begin.</span></span>

![AJ_Studio_NewProject](../media/AllJoyn/AJ_Studio_NewProject.png)

<span data-ttu-id="6bad7-147">En lugar de navegar a una plantilla universal de Windows, seleccione la plantilla "aplicación AllJoyn" para el idioma de destino que se instaló con la extensión.</span><span class="sxs-lookup"><span data-stu-id="6bad7-147">Instead of navigating to a Windows Universal Template, select the "AllJoyn App" Template for your target language which was installed with the Extension.</span></span>  <span data-ttu-id="6bad7-148">Asigne un nombre al proyecto y elija una ubicación de archivo para empezar a desarrollar.</span><span class="sxs-lookup"><span data-stu-id="6bad7-148">Name your project and choose a file location to begin developing.</span></span>

![AJ_Studio_NameProj](../media/AllJoyn/AJ_Studio_NameProj.png)

<span data-ttu-id="6bad7-150">Inmediatamente después de seleccionar una plantilla de aplicación AllJoyn, Visual Studio le pedirá que seleccione las interfaces AllJoyn que desea incluir en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="6bad7-150">Immediately after selecting an AllJoyn App Template, Visual Studio will ask you to select the AllJoyn Interfaces you would like to include in your Project.</span></span> 

![AJ_Studio_Interfaces](../media/AllJoyn/AJ_Studio_Interfaces.png)

<span data-ttu-id="6bad7-152">__Extracción de interfaces de un dispositivo en la red__</span><span class="sxs-lookup"><span data-stu-id="6bad7-152">__Extracting interfaces from a device on the network__</span></span>

<span data-ttu-id="6bad7-153">Si no encuentra el dispositivo AllJoyn o la interfaz en la red, siga [esta guía](AllJoynTroubleshooting.md) para solucionar los problemas.</span><span class="sxs-lookup"><span data-stu-id="6bad7-153">If you cannot find your AllJoyn device or interface on the network, follow [this guide](AllJoynTroubleshooting.md) to troubleshoot.</span></span> 

![AJ_Studio_FindDevices](../media/AllJoyn/AJ_Studio_FindDevices.png)

<span data-ttu-id="6bad7-155">Para consultar las interfaces expuestas de la red, seleccione "productores en la red" en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="6bad7-155">To query your network for exposed interfaces, select the "Producers on the network" in the left-hand panel.</span></span> <span data-ttu-id="6bad7-156">Esto encontrará cualquier productor de AllJoyn en la red y mostrará las interfaces que admiten.</span><span class="sxs-lookup"><span data-stu-id="6bad7-156">This will find any AllJoyn producer on the network and list the interfaces they support.</span></span>

![AJ_Studio_ListDevices](../media/AllJoyn/AJ_Studio_ListDevices.png)

<span data-ttu-id="6bad7-158">Seleccione las interfaces que le gustaría incluir en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="6bad7-158">Select the interfaces you would like to inlude in your project.</span></span>  <span data-ttu-id="6bad7-159">En este caso, solo se usa la interfaz de tostador, por lo que seleccionamos solo la interfaz "org. alljoyn. example. tostador".</span><span class="sxs-lookup"><span data-stu-id="6bad7-159">In this case, we are only using the toaster interface, so we select just the "org.alljoyn.example.Toaster" interface.</span></span>

![AJ_Studio_SelectDevices](../media/AllJoyn/AJ_Studio_SelectDevices.png)

<span data-ttu-id="6bad7-161">La columna "acciones" describe los cambios pendientes en el proyecto y muestra "agregar" para las interfaces recién seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="6bad7-161">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span> <span data-ttu-id="6bad7-162">Aquí hemos proporcionado a la interfaz un nombre descriptivo de "ToasterLibrary", que desencadena la acción "rename" que se va a aplicar.</span><span class="sxs-lookup"><span data-stu-id="6bad7-162">Here we have given the interface a friendly name of "ToasterLibrary", which triggers the "Rename" action to be applied.</span></span>

![AJ_Studio_DeviceAction](../media/AllJoyn/AJ_Studio_DeviceAction.png)

<span data-ttu-id="6bad7-164">__Cargar XML desde un archivo__</span><span class="sxs-lookup"><span data-stu-id="6bad7-164">__Loading an XML from a File__</span></span>

<span data-ttu-id="6bad7-165">Elija cualquier número de archivos XML introspección a través del botón "examinar" para ver las interfaces contenidas.</span><span class="sxs-lookup"><span data-stu-id="6bad7-165">Choose any number of Introspection XML files via the "Browse" button to see their contained Interface(s).</span></span>

![AJ_Studio_BrowseXML](../media/AllJoyn/AJ_Studio_BrowseXML.png)

<span data-ttu-id="6bad7-167">Vaya a y seleccione el XML adecuado (aquí, vamos a usar tostador. xml).</span><span class="sxs-lookup"><span data-stu-id="6bad7-167">Navigate to and select the appropriate XML (here, we are using toaster.xml).</span></span>

![AJ_Studio_BrowseXML_2](../media/AllJoyn/AJ_Studio_BrowseXML_2.png)

<span data-ttu-id="6bad7-169">Una vez que AllJoyn® Studio carga el XML, analizará las distintas interfaces y las descripciones que contiene, lo que le permitirá seleccionar las interfaces que le gustaría admitir.</span><span class="sxs-lookup"><span data-stu-id="6bad7-169">Once AllJoyn® Studio loads the XML, it will parse the various Interfaces and the descriptions contained within, allowing you select which Interfaces you would like to support.</span></span>

![AJ_Studio_BrowseXML_3](../media/AllJoyn/AJ_Studio_BrowseXML_3.png)

<span data-ttu-id="6bad7-171">La columna "acciones" describe los cambios pendientes en el proyecto y muestra "agregar" para las interfaces recién seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="6bad7-171">The "Actions" column describes the pending changes to the Project, displaying "Add" for newly-selected Interfaces.</span></span>

![AJ_Studio_BrowseXML_4](../media/AllJoyn/AJ_Studio_BrowseXML_4.png)

<span data-ttu-id="6bad7-173">Aquí hemos optado por incluir la interfaz "org. alljoyn. example. tostador" y haber dado un nombre descriptivo de "ToasterLibrary", lo que desencadena la acción de "cambiar nombre" que se va a aplicar.</span><span class="sxs-lookup"><span data-stu-id="6bad7-173">Here we have chosen to include the "org.alljoyn.example.Toaster" Interface and have given it a friendly name of "ToasterLibrary", triggering the "Rename" action to be applied.</span></span>

![AJ_Studio_BrowseXML_5](../media/AllJoyn/AJ_Studio_BrowseXML_5.png)

<span data-ttu-id="6bad7-175">__Adición y eliminación de interfaces__</span><span class="sxs-lookup"><span data-stu-id="6bad7-175">__Adding and Removing Interfaces__</span></span>

<span data-ttu-id="6bad7-176">Después de completar estos pasos, los archivos generados se agregan C++ automáticamente a un componente de Windows Runtime con el nombre descriptivo anterior y se agregan como una referencia al proyecto de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6bad7-176">After completing these steps, the generated files are automatically added to a C++ Windows Runtime Component with the friendly name from above and added as a Reference to the application Project.</span></span>  <span data-ttu-id="6bad7-177">Sin embargo, el espacio de nombres de la raíz sigue siendo el mismo "org. alljoyn. example. tostador", tal y como se define en la interfaz.</span><span class="sxs-lookup"><span data-stu-id="6bad7-177">However, the Root Namespace is still the same "org.alljoyn.example.Toaster" as defined by the interface.</span></span>  <span data-ttu-id="6bad7-178">Todas las clases que tienen acceso a estos componentes deben tener una cláusula "Using" para el espacio de nombres raíz del componente.</span><span class="sxs-lookup"><span data-stu-id="6bad7-178">Any classes that access these components need to have a "using" clause for the component's root namespace.</span></span>

![AJ_Studio_SolutionExplorer](../media/AllJoyn/AJ_Studio_SolutionExplorer.png)

<span data-ttu-id="6bad7-180">_TIP Cree los componentes generados ahora para beneficiarse de IntelliSense._</span><span class="sxs-lookup"><span data-stu-id="6bad7-180">_TIP: Build the generated components now in order to benefit from IntelliSense._</span></span>

<span data-ttu-id="6bad7-181">Después de crear la solución de la aplicación AllJoyn, siempre puede volver atrás y modificar las interfaces que está usando.</span><span class="sxs-lookup"><span data-stu-id="6bad7-181">After you have created your AllJoyn App solution, you can always go back and modify the interfaces you are using.</span></span> <span data-ttu-id="6bad7-182">En la barra de menús principal, haga clic en "AllJoyn-> Agregar o quitar interfaces..." para iniciar el administrador de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="6bad7-182">From the main menu bar, click "AllJoyn->Add/Remove Interfaces..." to launch the Interface manager.</span></span>

![AJ_Studio_AddInterfaces](../media/AllJoyn/AJ_Studio_AddInterfaces.png)

<span data-ttu-id="6bad7-184">Desde aquí, puede hacer clic en "examinar..." para agregar más archivos XML o anular la selección de las interfaces existentes.</span><span class="sxs-lookup"><span data-stu-id="6bad7-184">From here, you may click "Browse..." to add more XML files, or de-select existing Interface(s).</span></span> <span data-ttu-id="6bad7-185">La anulación de la selección de una interfaz actualiza su acción a "quitar" y, al hacer clic en el botón Aceptar, se quita el componente de Windows Runtime asociado de la solución.</span><span class="sxs-lookup"><span data-stu-id="6bad7-185">De-selecting an Interface updates its Action to "Remove", and clicking the Ok button removes the associated Windows Runtime Component from your solution.</span></span>

![AJ_Studio_AddXML](../media/AllJoyn/AJ_Studio_AddXML.png)

<span data-ttu-id="6bad7-187">Al examinar el Explorador de soluciones, se ha quitado el componente de Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="6bad7-187">Looking at the Solution Explorer, the Windows Runtime Component has been removed.</span></span>

![AJ_Studio_SolutionExplorer_2](../media/AllJoyn/AJ_Studio_SolutionExplorer_2.png)

## <a name="next-steps"></a><span data-ttu-id="6bad7-189">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="6bad7-189">Next Steps</span></span>

<span data-ttu-id="6bad7-190">Al implementar la funcionalidad AllJoyn, asegúrese siempre de incluir el espacio de nombres "Windows. Devices. AllJoyn" así como el espacio de nombres de la interfaz que desea usar.</span><span class="sxs-lookup"><span data-stu-id="6bad7-190">When implementing AllJoyn functionality, always be sure to include the "Windows.Devices.AllJoyn" namespace as well as the namespace from the interface you want to use.</span></span>

![AJ_Studio_namespace](../media/AllJoyn/AJ_Studio_namespace.png)

<span data-ttu-id="6bad7-192">__Implementar un consumidor AllJoyn__</span><span class="sxs-lookup"><span data-stu-id="6bad7-192">__Implementing an AllJoyn Consumer__</span></span>

<span data-ttu-id="6bad7-193">El código generado para las interfaces contiene un monitor y una clase de consumidor que se usa para buscar y después controlar un productor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-193">The code generated for the interfaces contains a watcher and consumer class used to find and then control a producer.</span></span> <span data-ttu-id="6bad7-194">Implemente el monitor mediante la creación de un nuevo AllJoynBusAttachment, inicialice el monitor con ese AllJoynBusAttachment, Regístrese para que el monitor busque un productor (el evento "agregado") y, a continuación, inicie el monitor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-194">Implement the watcher by creating a new AllJoynBusAttachment, initialize the watcher with that AllJoynBusAttachment, register for the watcher finding a producer (the "Added" event), then start the watcher.</span></span>

![AJ_Studio_Code_1](../media/AllJoyn/AJ_Studio_Code_1.png)

<span data-ttu-id="6bad7-196">El evento ToasterWatcher_Added se desencadena cuando el monitor encuentra un productor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-196">The ToasterWatcher_Added event triggers whenever the watcher finds a producer.</span></span>  <span data-ttu-id="6bad7-197">Utilice este evento para registrar un consumidor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-197">Use this event to register a consumer.</span></span> <span data-ttu-id="6bad7-198">Tenga en cuenta que Visual Studio generará el método de Shell necesario a través de las acciones rápidas.</span><span class="sxs-lookup"><span data-stu-id="6bad7-198">Note that Visual Studio will generate the necessary shell method through the Quick Actions.</span></span>

![AJ_Studio_Code_2](../media/AllJoyn/AJ_Studio_Code_2.png)

<span data-ttu-id="6bad7-200">Al generar el método, se genera el siguiente código de Shell:</span><span class="sxs-lookup"><span data-stu-id="6bad7-200">Generating the method produces the following shell code:</span></span>

![AJ_Studio_Code_3](../media/AllJoyn/AJ_Studio_Code_3.png)

<span data-ttu-id="6bad7-202">Al rellenar el código de Shell con la lógica correcta se habilita el registro del consumidor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-202">Filling in the shell code with the correct logic enables registering the consumer.</span></span>

![AJ_Studio_Code_4](../media/AllJoyn/AJ_Studio_Code_4.png)

<span data-ttu-id="6bad7-204">Tenga en cuenta que este evento se desencadena cada vez que el monitor detecta un productor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-204">Note that this event triggers every time the watcher discovers a producer.</span></span>  <span data-ttu-id="6bad7-205">Si espera encontrar varios productores, mantenga una estructura de datos del consumidor, ya que habrá un consumidor para cada productor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-205">If you expect to find multiple producers, keep a data structure of the consumer as there will be one consumer for each producer.</span></span>

<span data-ttu-id="6bad7-206">Registrar eventos para las distintas señales que emitirá el productor: las señales cambiadas de propiedad son miembros directos de la clase de consumidor, pero otras señales son miembros de la clase Signals (al igual que antes, use las acciones rápidas para generar el código de Shell para estos eventos).</span><span class="sxs-lookup"><span data-stu-id="6bad7-206">Register events for the various signals the producer will emit – property changed signals are direct members of the consumer class, but other signals are members of the Signals class (just as before, use the Quick Actions to generate the shell code for these events).</span></span>

![AJ_Studio_Code_5](../media/AllJoyn/AJ_Studio_Code_5.png)

<span data-ttu-id="6bad7-208">Use el objeto de consumidor para leer y escribir propiedades, así como para llamar a métodos.</span><span class="sxs-lookup"><span data-stu-id="6bad7-208">Use the consumer object to read and write properties as well as call methods.</span></span>

![AJ_Studio_Code_6](../media/AllJoyn/AJ_Studio_Code_6.png)

### <a name="implementing-an-alljoyn-producer"></a><span data-ttu-id="6bad7-210">Implementar un productor de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="6bad7-210">Implementing an AllJoyn Producer</span></span>

<span data-ttu-id="6bad7-211">__Implementar el servicio__</span><span class="sxs-lookup"><span data-stu-id="6bad7-211">__Implementing the Service__</span></span>

<span data-ttu-id="6bad7-212">Los productores implementan un servicio que expone sus interfaces.</span><span class="sxs-lookup"><span data-stu-id="6bad7-212">Producers implement a service that expose their interfaces.</span></span>  <span data-ttu-id="6bad7-213">Para implementar un productor, cree primero una clase para su servicio.</span><span class="sxs-lookup"><span data-stu-id="6bad7-213">To implement a producer, first create a class for its service.</span></span>

![AJ_Studio_Code_7](../media/AllJoyn/AJ_Studio_Code_7.png)

<span data-ttu-id="6bad7-215">Agregue el espacio de nombres de la interfaz a las instrucciones "Using" y, a continuación, herede la interfaz de Shell generada para el servicio y use la acción rápida para implementar la clase.</span><span class="sxs-lookup"><span data-stu-id="6bad7-215">Add the namespace for the interface to the "using" statements, then inherit the shell interface generated for the service and use the Quick Action to implement the class.</span></span>

![AJ_Studio_Code_8](../media/AllJoyn/AJ_Studio_Code_8.png)

<span data-ttu-id="6bad7-217">Desde aquí, la acción rápida rellenará los componentes necesarios.</span><span class="sxs-lookup"><span data-stu-id="6bad7-217">From here, the Quick Action will fill in the necessary components.</span></span>

![AJ_Studio_Code_9](../media/AllJoyn/AJ_Studio_Code_9.png)

<span data-ttu-id="6bad7-219">Todas las partes necesarias del código están listas para funcionar, pero todavía necesita implementar la lógica real para cada llamada de método y propiedad.</span><span class="sxs-lookup"><span data-stu-id="6bad7-219">All the necessary parts of the code are ready to function, but you still need to implement the actual logic for each method and property call.</span></span>

![AJ_Studio_Code_10](../media/AllJoyn/AJ_Studio_Code_10.png)

<span data-ttu-id="6bad7-221">Tomando el SetDarknessLevelAsync como ejemplo, usamos una tarea para crear un resultado correcto.</span><span class="sxs-lookup"><span data-stu-id="6bad7-221">Taking the SetDarknessLevelAsync as an example, we use a task to create a success result.</span></span>  <span data-ttu-id="6bad7-222">En caso de error, devuelva ToasterSetDarknessLevelResult. CreateFailureResult ().</span><span class="sxs-lookup"><span data-stu-id="6bad7-222">In case of failure, return ToasterSetDarknessLevelResult.CreateFailureResult().</span></span>

![AJ_Studio_Code_11](../media/AllJoyn/AJ_Studio_Code_11.png)

<span data-ttu-id="6bad7-224">Implemente el resto de las llamadas de método y propiedad para finalizar el servicio.</span><span class="sxs-lookup"><span data-stu-id="6bad7-224">Implement the rest of the method and property calls to finish the service.</span></span>

<span data-ttu-id="6bad7-225">__Implementación del productor__</span><span class="sxs-lookup"><span data-stu-id="6bad7-225">__Implementing the Producer__</span></span>

<span data-ttu-id="6bad7-226">La creación del productor es sencilla: cree un nuevo AllJoynBusAttachment, inicialice un productor con ese AllJoynBusAttachment, inicialice el servicio recién creado para el productor y luego inicie el productor.</span><span class="sxs-lookup"><span data-stu-id="6bad7-226">Creating the producer is straightforward – create a new AllJoynBusAttachment, initialize a producer with that AllJoynBusAttachment, initialize the newly created service for the producer, then start the producer.</span></span>

![AJ_Studio_Code_12](../media/AllJoyn/AJ_Studio_Code_12.png)

<span data-ttu-id="6bad7-228">Dado que el servicio contiene la mayoría de la lógica, la funcionalidad principal que queda para implementar es enviar las señales de los cambios de propiedad y las señales discretas para los eventos sin estado.</span><span class="sxs-lookup"><span data-stu-id="6bad7-228">Since the service contains the majority of the logic, the main functionality left to implement is to send the signals for property changes and discrete signals for non-state events.</span></span>  <span data-ttu-id="6bad7-229">Impleméntelo según sea necesario a través de llamadas a métodos.</span><span class="sxs-lookup"><span data-stu-id="6bad7-229">Implement these as necessary through method calls.</span></span>

![AJ_Studio_Code_13](../media/AllJoyn/AJ_Studio_Code_13.png)

<span data-ttu-id="6bad7-231">__Más información__</span><span class="sxs-lookup"><span data-stu-id="6bad7-231">__More Information__</span></span>

<span data-ttu-id="6bad7-232">Si ha completado correctamente todas las instrucciones de este documento, está listo para empezar a escribir código AllJoyn en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6bad7-232">If you've completed all of the instructions in this document correctly, you are ready to start writing AllJoyn code in your app.</span></span>

<span data-ttu-id="6bad7-233">Como referencia, consulte los ejemplos de aplicaciones universales de Windows de AllJoyn en el ejemplo de GitHub de Microsoft para [productores de alljoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) y [consumidores de alljoyn](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span><span class="sxs-lookup"><span data-stu-id="6bad7-233">For reference, please look to the AllJoyn Universal Windows Apps samples on the Microsoft Sample GitHub for [AllJoyn Producers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences) and [AllJoyn Consumers](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences).</span></span>

<span data-ttu-id="6bad7-234">Para obtener un tutorial detallado sobre cómo crear una aplicación AllJoyn, vea la sesión de AllJoyn 623:</span><span class="sxs-lookup"><span data-stu-id="6bad7-234">For a detailed walkthrough of how to create an AllJoyn app, please watch the AllJoyn session 623:</span></span>

> [!VIDEO https://channel9.msdn.com/Events/Build/2015/2-623/player]

<span data-ttu-id="6bad7-235">Tenga en cuenta que la comunicación de AllJoyn entre dos aplicaciones UWP en el mismo equipo está deshabilitada por la Directiva de Windows a menos que haya habilitado una excepción de bucle invertido, por ejemplo, cuando se implementa directamente desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6bad7-235">Note that AllJoyn communication between two UWP apps on the same machine is disabled by Windows policy unless they have enabled a loopback exception, such as when being directly deployed from Visual Studio.</span></span>  <span data-ttu-id="6bad7-236">Para obtener instrucciones detalladas sobre cómo habilitar la exención de bucle invertido, consulte [aquí](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span><span class="sxs-lookup"><span data-stu-id="6bad7-236">For detailed instructions on enabling loopback exemption, see [here](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>



