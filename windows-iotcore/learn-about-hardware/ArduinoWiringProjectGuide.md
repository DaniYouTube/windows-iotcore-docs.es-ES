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
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="78722-104">Guía de proyecto de cableado de Arduino</span><span class="sxs-lookup"><span data-stu-id="78722-104">Arduino Wiring Project Guide</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78722-105">El equipo de IoT de Windows 10 ya no mantiene de forma activa Arduino.</span><span class="sxs-lookup"><span data-stu-id="78722-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="78722-106">Esta guía le guiará a través de la creación, configuración e implementación de un proyecto de cableado de Arduino con Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="78722-106">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="78722-107">Los proyectos de cableado de Arduino usan la conocida API de cableado de Arduino fácil de usar con el controlador de Windows IoT Lightning DMAP: un controlador que usa la asignación de memoria directa para proporcionar [velocidades de rendimiento](../develop-your-app/LightningPerformance.md)significativas.</span><span class="sxs-lookup"><span data-stu-id="78722-107">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="78722-108">Puede copiar & pegar bocetos y bibliotecas de Arduino en los proyectos de cableado de IoT Core Arduino y ejecutarlos en dispositivos IoT Core compatibles, incluidos Raspberry pi2, 3 y Minnowboard Max.</span><span class="sxs-lookup"><span data-stu-id="78722-108">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="78722-109">Para obtener más información, consulte la sección desarrollo de esta página.</span><span class="sxs-lookup"><span data-stu-id="78722-109">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="78722-110">Instalación de las plantillas de IoT de Microsoft</span><span class="sxs-lookup"><span data-stu-id="78722-110">Install the Microsoft IoT Templates</span></span>

> [!NOTE]
> <span data-ttu-id="78722-111">Descargar VS 2015 para acceder a las plantillas de cableado de Arduino: estas plantillas no admiten loner en VS 2017 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="78722-111">Download VS 2015 to access Arduino Wiring templates - these templates are no loner supported on VS 2017 and beyond.</span></span>

<span data-ttu-id="78722-112">Hemos proporcionado una extensión de Visual Studio que instalará automáticamente una plantilla de VS para los proyectos de cableado de Arduino, así como otros tipos de proyectos de IoT de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78722-112">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="78722-113">Vaya a la [Página de la extensión de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la galería de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78722-113">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="78722-114">Instale la extensión y reinicie Visual Studio si ya estaba abierto</span><span class="sxs-lookup"><span data-stu-id="78722-114">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="78722-115">Cambiar el controlador de controlador predeterminado</span><span class="sxs-lookup"><span data-stu-id="78722-115">Change the Default Controller Driver</span></span>

<span data-ttu-id="78722-116">Tendrá que ejecutar el controlador asignado a memoria directa para escribir soluciones de cableado de Arduino.</span><span class="sxs-lookup"><span data-stu-id="78722-116">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="78722-117">Consulte la [Guía de configuración de Lightning](../develop-your-app/LightningSetup.md) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="78722-117">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="78722-118">Desarrollo</span><span class="sxs-lookup"><span data-stu-id="78722-118">Develop</span></span>
<span data-ttu-id="78722-119">Complete uno de los ejemplos de "conexión" en la [Página de ejemplos](https://developer.microsoft.com/en-us/windows/iot/samples)o cree su propio proyecto.</span><span class="sxs-lookup"><span data-stu-id="78722-119">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="78722-120">Cualquiera de los ejemplos que se hayan creado con el cableado de Arduino se enumerará como se indica a continuación: [Parpadeo (cableado)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span><span class="sxs-lookup"><span data-stu-id="78722-120">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="78722-121">Parpadee, el proyecto de cononical "Hola mundo" para proyectos de IoT, es un buen lugar para empezar por su primer proyecto.</span><span class="sxs-lookup"><span data-stu-id="78722-121">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="78722-122">Crear un nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="78722-122">Create a new Project</span></span>
1. <span data-ttu-id="78722-123">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78722-123">Open Visual Studio.</span></span>

2. <span data-ttu-id="78722-124">Seleccionar archivo-> Nuevo-> proyecto...</span><span class="sxs-lookup"><span data-stu-id="78722-124">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="78722-125">En el cuadro de diálogo que aparece, elija:</span><span class="sxs-lookup"><span data-stu-id="78722-125">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="78722-126">Visual C++ -> windows-> Windows IOT core-> Arduino de la aplicación de cableado para Windows IOT Core</span><span class="sxs-lookup"><span data-stu-id="78722-126">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="78722-127">(puede aparecer en su lugar como)</span><span class="sxs-lookup"><span data-stu-id="78722-127">(might appear instead as)</span></span>  
<span data-ttu-id="78722-128">Visual C++ -> aplicación de cableado de Windows IOT core-> Arduino para Windows IOT Core</span><span class="sxs-lookup"><span data-stu-id="78722-128">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![Creación de aplicaciones](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="78722-130">Migración</span><span class="sxs-lookup"><span data-stu-id="78722-130">Porting</span></span>

<span data-ttu-id="78722-131">La API de cableado de Arduino se ha implementado cuidadosamente para que sea posible copiar y pegar las bibliotecas y los bocetos en un proyecto de cableado de Arduino.</span><span class="sxs-lookup"><span data-stu-id="78722-131">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="78722-132">No obstante, en algunas circunstancias, es posible que tenga que realizar pequeñas modificaciones en sus bocetos o bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="78722-132">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="78722-133">Hemos creado una guía de migración de [cables de Arduino](ArduinoWiringPortingGuide.md) fácil de seguir para cubrir estos posibles problemas.</span><span class="sxs-lookup"><span data-stu-id="78722-133">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="78722-134">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="78722-134">Build and Deploy</span></span>

- <span data-ttu-id="78722-135">En Visual Studio, asegúrese de que "equipo remoto" esté seleccionado como destino de implementación.</span><span class="sxs-lookup"><span data-stu-id="78722-135">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="78722-136">Además, asegúrese de que la arquitectura está establecida para que coincida con la del panel en el que está ejecutando el proyecto.</span><span class="sxs-lookup"><span data-stu-id="78722-136">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="78722-137">Para Raspberry pi 2 o 3, elija "ARM" y para Minnowboard Max, elija "x86".</span><span class="sxs-lookup"><span data-stu-id="78722-137">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![Equipo remoto](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="78722-139">Abra las propiedades de la solución que se encuentran en el menú contextual de depuración en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78722-139">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="78722-141">Busque la dirección IP o el nombre de equipo del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="78722-141">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="78722-142">Use la aplicación Windows 10 IoT Core Dashboard o Conecte el dispositivo a un monitor.</span><span class="sxs-lookup"><span data-stu-id="78722-142">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="78722-143">Escriba el nombre de la máquina (minwinpc de forma predeterminada) o la dirección IP del equipo remoto en el campo "nombre del equipo".</span><span class="sxs-lookup"><span data-stu-id="78722-143">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="78722-144">Si ha cambiado el nombre del dispositivo a algo además de "minwinpc", use ese nombre en el cuadro de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="78722-144">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="78722-145">Asegúrese de que el tipo de Authentican es: Universal (protocolo sin cifrar)</span><span class="sxs-lookup"><span data-stu-id="78722-145">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="78722-147">Presione F5 para compilar e implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="78722-147">Press F5 to build and deploy your project on your device.</span></span>
