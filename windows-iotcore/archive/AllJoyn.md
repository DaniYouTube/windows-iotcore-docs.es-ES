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
ms.openlocfilehash: 6655cf5e8584a9c7046301cda24b10348a704d6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514291"
---
> [!NOTE]
> <span data-ttu-id="f6e69-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="f6e69-104">You are viewing archived documentation.</span></span> <span data-ttu-id="f6e69-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="f6e69-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="f6e69-106">Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.</span><span class="sxs-lookup"><span data-stu-id="f6e69-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn"></a><span data-ttu-id="f6e69-107">AllJoyn</span><span class="sxs-lookup"><span data-stu-id="f6e69-107">AllJoyn</span></span>

<span data-ttu-id="f6e69-108">AllJoyn mejora la capacidad de Internet de las cosas.</span><span class="sxs-lookup"><span data-stu-id="f6e69-108">AllJoyn empowers the Internet of Things.</span></span> <span data-ttu-id="f6e69-109">AllJoyn define un protocolo común para los dispositivos y las aplicaciones detectar y comunicarse entre sí independientemente del fabricante, plataforma o tecnología de transporte.</span><span class="sxs-lookup"><span data-stu-id="f6e69-109">AllJoyn defines a common protocol for devices and applications to discover and communicate with each other regardless of transport technology, platform or manufacturer.</span></span>  <span data-ttu-id="f6e69-110">AllJoyn es un estándar de código abierto controlado por la [AllSeen Alliance](https://allseenalliance.org/), un consorcio del sector entre dedicados a habilitar la interoperabilidad de miles de millones de dispositivos, servicios y aplicaciones para Internet de las cosas.</span><span class="sxs-lookup"><span data-stu-id="f6e69-110">AllJoyn is an open source standard driven by the [AllSeen Alliance](https://allseenalliance.org/), a cross-industry consortium dedicated to enabling the interoperability of billions of devices, services and applications for the Internet of Things.</span></span>

<span data-ttu-id="f6e69-111">Microsoft incorporó a la alianza AllSeen en 2014 y agrega AllJoyn como un componente básico de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f6e69-111">Microsoft joined the AllSeen Alliance in 2014 and added AllJoyn as a core component in Windows 10.</span></span> <span data-ttu-id="f6e69-112">Con la integrada [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), los desarrolladores son gratuitos escribir las aplicaciones compatibles con AllJoyn que se ejecutan en cualquiera de los dispositivos Windows 10, incluidos PCs, tabletas, teléfonos, Xbox, así como dispositivos con Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f6e69-112">With the built-in [AllJoyn APIs](https://msdn.microsoft.com/library/windows/apps/windows.devices.alljoyn.aspx), developers are free to write AllJoyn capable applications that run on any of the Windows 10 devices including PCs, tablets, phones, Xbox as well as devices using Windows IoT Core.</span></span> <span data-ttu-id="f6e69-113">Además de la compatibilidad de plataforma para AllJoyn, Microsoft lanzó [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), una extensión de Visual Studio que acelera el desarrollo de AllJoyn mediante la combinación de generación de código con plantillas de aplicaciones listas para usar.</span><span class="sxs-lookup"><span data-stu-id="f6e69-113">In addition to the platform support for AllJoyn, Microsoft released [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286), a Visual Studio extension that accelerates AllJoyn development by combining code generation with ready-made application templates.</span></span> <span data-ttu-id="f6e69-114">AllJoyn Studio permite a los desarrolladores para beneficiarse de la potencia de AllJoyn sin los problemas de instalación y configuración.</span><span class="sxs-lookup"><span data-stu-id="f6e69-114">AllJoyn Studio allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="f6e69-115">¿La idea de AllJoyn?</span><span class="sxs-lookup"><span data-stu-id="f6e69-115">Excited about AllJoyn?</span></span> <span data-ttu-id="f6e69-116">Eche un vistazo a [esto](AllJoynStudio.md) entrada de blog sobre cómo empezar a trabajar con AllJoyn en Windows.</span><span class="sxs-lookup"><span data-stu-id="f6e69-116">Have a look at [this](AllJoynStudio.md) blog post on how to get started with AllJoyn on Windows.</span></span>


## <a name="developer-resources-and-tools"></a><span data-ttu-id="f6e69-117">Herramientas y recursos para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="f6e69-117">Developer Resources and Tools</span></span>

**<span data-ttu-id="f6e69-118">Puente de dispositivo del sistema</span><span class="sxs-lookup"><span data-stu-id="f6e69-118">Device System Bridge</span></span>**

<span data-ttu-id="f6e69-119">AllJoyn [puente de dispositivo del sistema](AllJoynDSB.md) permite a los dispositivos que no sean AllJoyn interactuar con el ecosistema de AllJoyn con AllJoyn como su lenguaje común.</span><span class="sxs-lookup"><span data-stu-id="f6e69-119">AllJoyn [Device System Bridge](AllJoynDSB.md) enables non-AllJoyn devices to interact with the AllJoyn ecosystem using AllJoyn as their common language.</span></span>

<span data-ttu-id="f6e69-120">Características:</span><span class="sxs-lookup"><span data-stu-id="f6e69-120">Features:</span></span>
* <span data-ttu-id="f6e69-121">Crea los dispositivos virtuales para cada dispositivo que no sean AllJoyn expuestos por el adaptador</span><span class="sxs-lookup"><span data-stu-id="f6e69-121">Creates virtual devices for each non-AllJoyn device exposed by Adapter</span></span>
* <span data-ttu-id="f6e69-122">Generación de la interfaz en tiempo de ejecución automática del dispositivo del adaptador</span><span class="sxs-lookup"><span data-stu-id="f6e69-122">Automated runtime interface generation from Adapter device</span></span>
* <span data-ttu-id="f6e69-123">Admite LSF, servicios básicos de Panel de Control, extensibles para agregar más servicios</span><span class="sxs-lookup"><span data-stu-id="f6e69-123">Supports LSF, Control Panel base services, extensible to add more services</span></span>
* <span data-ttu-id="f6e69-124">Las plantillas de aplicación universal (C#, C++), para las aplicaciones de interfaz de usuario de escritorio y las tareas de inicio de Windows IoT</span><span class="sxs-lookup"><span data-stu-id="f6e69-124">Universal app templates (C#, C++), for Desktop UI applications and Windows IoT startup tasks</span></span>
* <span data-ttu-id="f6e69-125">Disponible como código abierto</span><span class="sxs-lookup"><span data-stu-id="f6e69-125">Available as open source</span></span>

<span data-ttu-id="f6e69-126">Pueden encontrar más detalles en el [página puente de dispositivo del sistema](AllJoynDSB.md).</span><span class="sxs-lookup"><span data-stu-id="f6e69-126">More details can be found on the [Device System Bridge page](AllJoynDSB.md).</span></span>


**<span data-ttu-id="f6e69-127">AllJoyn Studio</span><span class="sxs-lookup"><span data-stu-id="f6e69-127">AllJoyn Studio</span></span>**

<span data-ttu-id="f6e69-128">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) es una extensión de Visual Studio desarrollados por Microsoft que acelera el desarrollo de AllJoyn® mediante la combinación de generación de código y la API de WinRT con administración automatizada de proyectos y plantillas de aplicaciones listas para usar.</span><span class="sxs-lookup"><span data-stu-id="f6e69-128">[AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) is an extension to Visual Studio developed by Microsoft that accelerates AllJoyn® development by combining code generation and the WinRT API with automated project management and ready-made application templates.</span></span> <span data-ttu-id="f6e69-129">Permite a los programadores beneficiarse de la potencia de AllJoyn sin los problemas de instalación y configuración.</span><span class="sxs-lookup"><span data-stu-id="f6e69-129">It allows developers to benefit from the power of AllJoyn without the hassle of set-up and configuration.</span></span>

<span data-ttu-id="f6e69-130">Características:</span><span class="sxs-lookup"><span data-stu-id="f6e69-130">Features:</span></span>
* <span data-ttu-id="f6e69-131">Las plantillas de aplicación universal (C#, JavaScript, C++, Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6e69-131">Universal app templates (C#, JavaScript, C++, Visual Basic)</span></span>
* <span data-ttu-id="f6e69-132">Configuración de administración y el proyecto de referencia automatizadas</span><span class="sxs-lookup"><span data-stu-id="f6e69-132">Automated reference management and project configuration</span></span>
* <span data-ttu-id="f6e69-133">Agregar o quitar interfaces de una solución</span><span class="sxs-lookup"><span data-stu-id="f6e69-133">Adding/removing interfaces to/from a solution</span></span>
* <span data-ttu-id="f6e69-134">Fácil acceso a la administración de proyectos a través del menú AllJoyn®</span><span class="sxs-lookup"><span data-stu-id="f6e69-134">Easy access to project management via the AllJoyn® menu</span></span>
* <span data-ttu-id="f6e69-135">Cargando las interfaces de los archivos XML de introspección</span><span class="sxs-lookup"><span data-stu-id="f6e69-135">Loading interfaces from introspection XML file(s)</span></span>
* <span data-ttu-id="f6e69-136">Detección de las interfaces de productor, productores en el network1</span><span class="sxs-lookup"><span data-stu-id="f6e69-136">Discovering interfaces from producer(s) on the network1</span></span>

<span data-ttu-id="f6e69-137">AllJoyn Studio puede instalarse a través de Visual Studio Tools -> extensiones y actualizaciones...</span><span class="sxs-lookup"><span data-stu-id="f6e69-137">AllJoyn Studio can be installed through Visual Studio Tools -> Extensions and Updates …</span></span> <span data-ttu-id="f6e69-138">-> En línea -> en el tipo de campo "AllJoyn" de "Búsqueda"</span><span class="sxs-lookup"><span data-stu-id="f6e69-138">-> Online -> In the "Search" field type "AllJoyn"</span></span>

<span data-ttu-id="f6e69-139">Encontrará más detalles acerca de cómo usar AllJoyn Studio [aquí](AllJoynStudio.md).</span><span class="sxs-lookup"><span data-stu-id="f6e69-139">More detail about how to use AllJoyn Studio are available [here](AllJoynStudio.md).</span></span>

**<span data-ttu-id="f6e69-140">Explorador de IoT para AllJoyn (AllJoyn Explorer)</span><span class="sxs-lookup"><span data-stu-id="f6e69-140">IoT Explorer for AllJoyn (AllJoyn Explorer)</span></span>**

<span data-ttu-id="f6e69-141">El Explorador de IoT para AllJoyn (anteriormente conocido como el Explorador de AllJoyn) es una aplicación Universal de Windows para interactuar con dispositivos de AllJoyn de la red de proximidad local.</span><span class="sxs-lookup"><span data-stu-id="f6e69-141">The IoT Explorer for AllJoyn (previously known as AllJoyn Explorer) is a Windows Universal Application for interacting with AllJoyn devices on the local proximity network.</span></span> <span data-ttu-id="f6e69-142">Desarrolladores pueden enumerar todos los dispositivos de AllJoyn disponibles, inspeccione su estructura de la interfaz y un objeto, así como recibir señales, establecer y obtener propiedades y llamar a métodos.</span><span class="sxs-lookup"><span data-stu-id="f6e69-142">Developers can list all available AllJoyn devices, inspect their interface and object structure, as well as receive signals, set and get properties, and call methods.</span></span>

* <span data-ttu-id="f6e69-143">[Explorador de IoT para App Store de AllJoyn](https://www.microsoft.com/store/apps/9nblggh6gpxl): Esta es la ubicación de la aplicación de tienda oficial.</span><span class="sxs-lookup"><span data-stu-id="f6e69-143">[IoT Explorer for AllJoyn Store App](https://www.microsoft.com/store/apps/9nblggh6gpxl): This is the official store app location.</span></span>
* <span data-ttu-id="f6e69-144">[Explorador de AllJoyn 1.0.1.11 (versión anterior)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): Este archivo zip contiene la agrupación de AllJoyn Explorer AppX para que sea de carga lateral en una máquina de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f6e69-144">[AllJoyn Explorer 1.0.1.11 (previous release)](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoynExplorer_1.0.1.11.zip): This zip contains the AllJoyn Explorer AppX bundle to be side-loaded on a developer machine.</span></span> <span data-ttu-id="f6e69-145">Se trata de una versión del explorador de IoT para AllJoyn aplicaciones publicada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f6e69-145">This is a previously released version of the IoT Explorer for AllJoyn application.</span></span>
* <span data-ttu-id="f6e69-146">[Guía de configuración del explorador de AllJoyn](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): Este pdf contiene la documentación sobre cómo implementar el Explorador de AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="f6e69-146">[AllJoyn Explorer Setup Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_Setup_Guide_v1.0.pdf): This pdf contains the documentation for how to deploy the AllJoyn Explorer.</span></span>
* <span data-ttu-id="f6e69-147">[Guía de usuario de explorador AllJoyn](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): Este pdf contiene la documentación sobre cómo usar el Explorador de AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="f6e69-147">[AllJoyn Explorer User Guide](https://github.com/ms-iot/samples/releases/download/AllJoynExplorer_1.0.11/AllJoyn_Explorer_User_Guide_v1.0.pdf): This pdf contains the documentation for how to use the AllJoyn Explorer.</span></span>


### <a name="additional-resources"></a><span data-ttu-id="f6e69-148">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="f6e69-148">Additional Resources</span></span>

* [<span data-ttu-id="f6e69-149">Uso de la extensión de AllJoyn Studio</span><span class="sxs-lookup"><span data-stu-id="f6e69-149">Using the AllJoyn Studio extension</span></span>](AllJoynStudio.md)
* [<span data-ttu-id="f6e69-150">Productor de AllJoyn y AllJoyn introspección de creación</span><span class="sxs-lookup"><span data-stu-id="f6e69-150">AllJoyn Producer and Authoring AllJoyn Introspection</span></span>](AllJoynProducer.md)
* [<span data-ttu-id="f6e69-151">Solución de problemas de AllJoyn con Windows 10</span><span class="sxs-lookup"><span data-stu-id="f6e69-151">Troubleshooting AllJoyn with Windows 10</span></span>](AllJoynTroubleshooting.md)

**<span data-ttu-id="f6e69-152">Vídeos</span><span class="sxs-lookup"><span data-stu-id="f6e69-152">Videos</span></span>**

* [<span data-ttu-id="f6e69-153">Crear sesión técnica AllJoyn de 2015</span><span class="sxs-lookup"><span data-stu-id="f6e69-153">//build 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/Build/2015/2-623)
* [<span data-ttu-id="f6e69-154">WinHEC 2015 AllJoyn Technical sesión</span><span class="sxs-lookup"><span data-stu-id="f6e69-154">WinHEC 2015 AllJoyn Technical Session</span></span>](https://channel9.msdn.com/Events/WinHEC/2015/IOT200)

**<span data-ttu-id="f6e69-155">Muestras</span><span class="sxs-lookup"><span data-stu-id="f6e69-155">Samples</span></span>**

* [<span data-ttu-id="f6e69-156">Productores AllJoyn</span><span class="sxs-lookup"><span data-stu-id="f6e69-156">AllJoyn Producers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ProducerExperiences)
* [<span data-ttu-id="f6e69-157">Consumidores de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="f6e69-157">AllJoyn Consumers</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)
* [<span data-ttu-id="f6e69-158">Ejemplos de UWP de AllJoyn (MSDN)</span><span class="sxs-lookup"><span data-stu-id="f6e69-158">AllJoyn UWP Samples (MSDN)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AllJoyn/ConsumerExperiences)

**<span data-ttu-id="f6e69-159">Referencia</span><span class="sxs-lookup"><span data-stu-id="f6e69-159">Reference</span></span>**

* [<span data-ttu-id="f6e69-160">API de AllJoyn en Windows 10 (MSDN)</span><span class="sxs-lookup"><span data-stu-id="f6e69-160">AllJoyn APIs in Windows 10 (MSDN)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx)
* [<span data-ttu-id="f6e69-161">Detalles de la arquitectura de AllJoyn (Alliance Allseen)</span><span class="sxs-lookup"><span data-stu-id="f6e69-161">AllJoyn Architecture Details (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/learn/)
* [<span data-ttu-id="f6e69-162">Recursos para desarrolladores de AllJoyn (Alliance Allseen)</span><span class="sxs-lookup"><span data-stu-id="f6e69-162">AllJoyn Developer Resources (Allseen Alliance)</span></span>](https://allseenalliance.org/developers/develop/)
* [<span data-ttu-id="f6e69-163">Manual de referencia de API de C de AllJoyn (Alliance Allseen)</span><span class="sxs-lookup"><span data-stu-id="f6e69-163">AllJoyn C API Reference Manual (Allseen Alliance)</span></span>](https://allseenalliance.org/docs/api/c/index.html)

