---
title: Guía de proyectos de la conexión de Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la creación, el programa de instalación e implementación de un proyecto de cableado de Arduino con Windows IoT Core.
keywords: iot, Arduino, Arduino cableado de Windows, un rendimiento increíblemente, Visual Studio
ms.openlocfilehash: 7c5e51efd20de014af4533587fbe6f210140b793
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744810"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="23c9e-104">Guía de proyectos de la conexión de Arduino</span><span class="sxs-lookup"><span data-stu-id="23c9e-104">Arduino Wiring Project Guide</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23c9e-105">El equipo de Windows 10 IoT activamente ya no es mantener Arduino.</span><span class="sxs-lookup"><span data-stu-id="23c9e-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="23c9e-106">Esta guía le guiará a través de la creación, el programa de instalación e implementación de un proyecto de cableado de Arduino con Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="23c9e-106">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="23c9e-107">Proyectos de la conexión de Arduino usan la API de cableado de familiar y fácil de usar Arduino con controladores de Windows IoT relámpago DMAP: un controlador mediante la asignación de memoria directa para proporcionar importantes [velocidades de rendimiento](../develop-your-app/LightningPerformance.md).</span><span class="sxs-lookup"><span data-stu-id="23c9e-107">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="23c9e-108">Puede copiar & Pegar Arduino Bocetos y las bibliotecas en sus proyectos de IoT Core Arduino cableado y ejecútelas en admitidos IoT Core dispositivos, incluidos Raspberry Pi2, 3 y Minnowboard máximo!</span><span class="sxs-lookup"><span data-stu-id="23c9e-108">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="23c9e-109">Consulte la sección de desarrollo de esta página para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="23c9e-109">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="23c9e-110">Instalar las plantillas de IoT de Microsoft</span><span class="sxs-lookup"><span data-stu-id="23c9e-110">Install the Microsoft IoT Templates</span></span>

> [!NOTE]
> <span data-ttu-id="23c9e-111">Descarga de VS 2015 para acceder a las plantillas de cableado Arduino - estas plantillas no son ningún solitaria admitido en VS 2017 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="23c9e-111">Download VS 2015 to access Arduino Wiring templates - these templates are no loner supported on VS 2017 and beyond.</span></span>

<span data-ttu-id="23c9e-112">Hemos proporcionado una extensión de Visual Studio que se instalará automáticamente una plantilla de VS para los proyectos de la conexión de Arduino, así como otros tipos de proyecto de IoT de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="23c9e-112">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="23c9e-113">Diríjase a [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la Galería de Visual Studio!</span><span class="sxs-lookup"><span data-stu-id="23c9e-113">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="23c9e-114">Instalar la extensión y reinicie Visual Studio si estaba abierto</span><span class="sxs-lookup"><span data-stu-id="23c9e-114">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="23c9e-115">Cambiar el controlador del controlador predeterminado</span><span class="sxs-lookup"><span data-stu-id="23c9e-115">Change the Default Controller Driver</span></span>

<span data-ttu-id="23c9e-116">Deberá ejecutar el controlador de asignar memoria directa para escribir soluciones de conexión de Arduino!</span><span class="sxs-lookup"><span data-stu-id="23c9e-116">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="23c9e-117">Hacer referencia a la [relámpago Guía de instalación](../develop-your-app/LightningSetup.md) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="23c9e-117">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="23c9e-118">Desarrollo</span><span class="sxs-lookup"><span data-stu-id="23c9e-118">Develop</span></span>
<span data-ttu-id="23c9e-119">Complete uno de los ejemplos de "Conexión" en el [página de ejemplos de](https://developer.microsoft.com/en-us/windows/iot/samples), o crear su propio proyecto.</span><span class="sxs-lookup"><span data-stu-id="23c9e-119">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="23c9e-120">Cualquiera de los ejemplos que hemos creado que se escriben utilizando la conexión de Arduino, se mostrará la siguiente manera: [Llamativa (cableado)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span><span class="sxs-lookup"><span data-stu-id="23c9e-120">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="23c9e-121">El proyecto "Hello World" cononical para los proyectos de IoT, llamativa, es un excelente punto de partida para su primer proyecto.</span><span class="sxs-lookup"><span data-stu-id="23c9e-121">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="23c9e-122">Cree un nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="23c9e-122">Create a new Project</span></span>
1. <span data-ttu-id="23c9e-123">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="23c9e-123">Open Visual Studio.</span></span>

2. <span data-ttu-id="23c9e-124">Seleccione Archivo -> Nuevo -> proyecto...</span><span class="sxs-lookup"><span data-stu-id="23c9e-124">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="23c9e-125">En el cuadro de diálogo que aparece, elija:</span><span class="sxs-lookup"><span data-stu-id="23c9e-125">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="23c9e-126">Visual C++ -> Windows -> Windows IoT Core -> Arduino cableado de la aplicación para Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="23c9e-126">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="23c9e-127">(puede aparecer en su lugar como)</span><span class="sxs-lookup"><span data-stu-id="23c9e-127">(might appear instead as)</span></span>  
<span data-ttu-id="23c9e-128">Visual C++ -> Windows IoT Core -> Arduino cableado de la aplicación para Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="23c9e-128">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![Crear aplicación](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="23c9e-130">Migración</span><span class="sxs-lookup"><span data-stu-id="23c9e-130">Porting</span></span>

<span data-ttu-id="23c9e-131">Se ha implementado la API de conexión de Arduino con cuidado para que sea posible copiar y pegar las bibliotecas y dibujos en un proyecto de cableado de Arduino.</span><span class="sxs-lookup"><span data-stu-id="23c9e-131">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="23c9e-132">Sin embargo, hay, en algunas circunstancias, ligeras modificaciones, es posible que deba realizar en los esquemas o las bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="23c9e-132">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="23c9e-133">Hemos creado una fácil de seguir [Guía de migración de la conexión de Arduino](ArduinoWiringPortingGuide.md) para cubrir estos posibles problemas.</span><span class="sxs-lookup"><span data-stu-id="23c9e-133">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="23c9e-134">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="23c9e-134">Build and Deploy</span></span>

- <span data-ttu-id="23c9e-135">En Visual Studio, asegúrese de que "Máquina remota" está seleccionado como destino de implementación.</span><span class="sxs-lookup"><span data-stu-id="23c9e-135">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="23c9e-136">Además, asegúrese de que la arquitectura se establece para que coincida con el panel que se ejecutan en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="23c9e-136">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="23c9e-137">Para Raspberry Pi 2 o 3 elija "ARM" y para Minnowboard Max, elija "x86".</span><span class="sxs-lookup"><span data-stu-id="23c9e-137">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![Equipo remoto](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="23c9e-139">Abra las propiedades de la solución que se encuentra en el menú contextual de depuración en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="23c9e-139">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="23c9e-141">Busque el nombre de máquina o la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="23c9e-141">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="23c9e-142">Usar la aplicación de panel de Windows 10 IoT Core o enlazar el dispositivo a un monitor.</span><span class="sxs-lookup"><span data-stu-id="23c9e-142">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="23c9e-143">Escriba el nombre del equipo (minwinpc de forma predeterminada) o la dirección IP del equipo remoto en el campo 'nombre del equipo'.</span><span class="sxs-lookup"><span data-stu-id="23c9e-143">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="23c9e-144">Si ha cambiado el nombre del dispositivo a algo además 'minwinpc' use ese nombre en el cuadro de inicio de sesión en su lugar.</span><span class="sxs-lookup"><span data-stu-id="23c9e-144">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="23c9e-145">Asegúrese de que el tipo Authentican es: Universal (protocolo sin cifrar)</span><span class="sxs-lookup"><span data-stu-id="23c9e-145">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="23c9e-147">Presione F5 para compilar e implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="23c9e-147">Press F5 to build and deploy your project on your device.</span></span>
