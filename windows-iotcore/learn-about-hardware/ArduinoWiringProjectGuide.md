---
title: Guía de proyectos de la conexión de Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la creación, el programa de instalación e implementación de un proyecto de cableado de Arduino con Windows IoT Core.
keywords: iot, Arduino, Arduino cableado de Windows, un rendimiento increíblemente, Visual Studio
ms.openlocfilehash: baa904d1d5f23db15fd1dacd05c749449dc91213
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514536"
---
# <a name="arduino-wiring-project-guide"></a><span data-ttu-id="dbf58-104">Guía de proyectos de la conexión de Arduino</span><span class="sxs-lookup"><span data-stu-id="dbf58-104">Arduino Wiring Project Guide</span></span>

<span data-ttu-id="dbf58-105">Esta guía le guiará a través de la creación, el programa de instalación e implementación de un proyecto de cableado de Arduino con Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="dbf58-105">This guide will walk through the creation, setup, and deployment of an Arduino Wiring project using Windows IoT Core.</span></span>

<span data-ttu-id="dbf58-106">Proyectos de la conexión de Arduino usan la API de cableado de familiar y fácil de usar Arduino con controladores de Windows IoT relámpago DMAP: un controlador mediante la asignación de memoria directa para proporcionar importantes [velocidades de rendimiento](../develop-your-app/LightningPerformance.md).</span><span class="sxs-lookup"><span data-stu-id="dbf58-106">Arduino Wiring projects utilize the familiar, easy to use Arduino Wiring API with Windows IoT Lightning DMAP driver: a driver using direct memory mapping to provide significant [performance speeds](../develop-your-app/LightningPerformance.md).</span></span> <span data-ttu-id="dbf58-107">Puede copiar & Pegar Arduino Bocetos y las bibliotecas en sus proyectos de IoT Core Arduino cableado y ejecútelas en admitidos IoT Core dispositivos, incluidos Raspberry Pi2, 3 y Minnowboard máximo!</span><span class="sxs-lookup"><span data-stu-id="dbf58-107">You can copy & paste Arduino sketches and libraries into your IoT Core Arduino Wiring projects and run them on supported IoT Core devices, including Raspberry Pi2, 3 and Minnowboard Max!</span></span> <span data-ttu-id="dbf58-108">Consulte la sección de desarrollo de esta página para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="dbf58-108">See the develop section of this page for more information.</span></span>

## <a name="install-the-microsoft-iot-templates"></a><span data-ttu-id="dbf58-109">Instalar las plantillas de IoT de Microsoft</span><span class="sxs-lookup"><span data-stu-id="dbf58-109">Install the Microsoft IoT Templates</span></span>

<span data-ttu-id="dbf58-110">Hemos proporcionado una extensión de Visual Studio que se instalará automáticamente una plantilla de VS para los proyectos de la conexión de Arduino, así como otros tipos de proyecto de IoT de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dbf58-110">We've provided a Visual Studio extension which will automatically install a VS template for the Arduino Wiring projects as well as other Microsoft IoT project types.</span></span> 

- <span data-ttu-id="dbf58-111">Diríjase a [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la Galería de Visual Studio!</span><span class="sxs-lookup"><span data-stu-id="dbf58-111">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>
- <span data-ttu-id="dbf58-112">Instalar la extensión y reinicie Visual Studio si estaba abierto</span><span class="sxs-lookup"><span data-stu-id="dbf58-112">Install the extension and restart Visual Studio if it was already open</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="dbf58-113">Cambiar el controlador del controlador predeterminado</span><span class="sxs-lookup"><span data-stu-id="dbf58-113">Change the Default Controller Driver</span></span>

<span data-ttu-id="dbf58-114">Deberá ejecutar el controlador de asignar memoria directa para escribir soluciones de conexión de Arduino!</span><span class="sxs-lookup"><span data-stu-id="dbf58-114">You will need to be running the Direct Memory Mapped Driver to write Arduino Wiring solutions!</span></span> <span data-ttu-id="dbf58-115">Hacer referencia a la [relámpago Guía de instalación](../develop-your-app/LightningSetup.md) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="dbf58-115">Refer to the [Lightning Setup Guide](../develop-your-app/LightningSetup.md) for instructions!</span></span>

## <a name="develop"></a><span data-ttu-id="dbf58-116">Desarrollo</span><span class="sxs-lookup"><span data-stu-id="dbf58-116">Develop</span></span>
<span data-ttu-id="dbf58-117">Complete uno de los ejemplos de "Conexión" en el [página de ejemplos de](https://developer.microsoft.com/en-us/windows/iot/samples), o crear su propio proyecto.</span><span class="sxs-lookup"><span data-stu-id="dbf58-117">Complete one of the "Wiring" samples on the [Samples Page](https://developer.microsoft.com/en-us/windows/iot/samples), or build your own project!</span></span> <span data-ttu-id="dbf58-118">Cualquiera de los ejemplos que hemos creado que se escriben utilizando la conexión de Arduino, se mostrará la siguiente manera: [Llamativa (cableado)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span><span class="sxs-lookup"><span data-stu-id="dbf58-118">Any of the samples we've created that are written using Arduino Wiring will be listed like so: [Blinky (Wiring)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinkybackgroundwiring).</span></span> <span data-ttu-id="dbf58-119">El proyecto "Hello World" cononical para los proyectos de IoT, llamativa, es un excelente punto de partida para su primer proyecto.</span><span class="sxs-lookup"><span data-stu-id="dbf58-119">Blinky, the cononical "Hello World" project for IoT projects, is a great place to start for your first project!</span></span>

### <a name="create-a-new-project"></a><span data-ttu-id="dbf58-120">Cree un nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="dbf58-120">Create a new Project</span></span>
1. <span data-ttu-id="dbf58-121">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbf58-121">Open Visual Studio.</span></span>

2. <span data-ttu-id="dbf58-122">Seleccione Archivo -> Nuevo -> proyecto...</span><span class="sxs-lookup"><span data-stu-id="dbf58-122">Select File -> New -> Project...</span></span>

3. <span data-ttu-id="dbf58-123">En el cuadro de diálogo que aparece, elija:</span><span class="sxs-lookup"><span data-stu-id="dbf58-123">From the dialogue that appears, choose:</span></span>  
<span data-ttu-id="dbf58-124">Visual C++ -> Windows -> Windows IoT Core -> Arduino cableado de la aplicación para Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="dbf58-124">Visual C++ -> Windows -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span>  
<span data-ttu-id="dbf58-125">(puede aparecer en su lugar como)</span><span class="sxs-lookup"><span data-stu-id="dbf58-125">(might appear instead as)</span></span>  
<span data-ttu-id="dbf58-126">Visual C++ -> Windows IoT Core -> Arduino cableado de la aplicación para Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="dbf58-126">Visual C++ -> Windows IoT Core -> Arduino Wiring Application for Windows IoT Core</span></span> 


![Crear aplicación](../media/ArduinoWiring/appcreate.png)

### <a name="porting"></a><span data-ttu-id="dbf58-128">Migración</span><span class="sxs-lookup"><span data-stu-id="dbf58-128">Porting</span></span>

<span data-ttu-id="dbf58-129">Se ha implementado la API de conexión de Arduino con cuidado para que sea posible copiar y pegar las bibliotecas y dibujos en un proyecto de cableado de Arduino.</span><span class="sxs-lookup"><span data-stu-id="dbf58-129">The Arduino Wiring API has been carefully implemented to make it possible to copy/paste your libraries and sketches into an Arduino Wiring project.</span></span> <span data-ttu-id="dbf58-130">Sin embargo, hay, en algunas circunstancias, ligeras modificaciones, es posible que deba realizar en los esquemas o las bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="dbf58-130">Nevertheless there are, in some circumstances, slight modifications you may have to make to your sketches or libraries.</span></span> <span data-ttu-id="dbf58-131">Hemos creado una fácil de seguir [Guía de migración de la conexión de Arduino](ArduinoWiringPortingGuide.md) para cubrir estos posibles problemas.</span><span class="sxs-lookup"><span data-stu-id="dbf58-131">We've created an easy to follow [Arduino Wiring Porting Guide](ArduinoWiringPortingGuide.md) to cover these potential issues.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="dbf58-132">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="dbf58-132">Build and Deploy</span></span>

- <span data-ttu-id="dbf58-133">En Visual Studio, asegúrese de que "Máquina remota" está seleccionado como destino de implementación.</span><span class="sxs-lookup"><span data-stu-id="dbf58-133">In Visual Studio, make sure "Remote Machine" is selected as your deployment target.</span></span>
- <span data-ttu-id="dbf58-134">Además, asegúrese de que la arquitectura se establece para que coincida con el panel que se ejecutan en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="dbf58-134">Also, make sure the  architecture is set to match the board you're running your project on.</span></span> <span data-ttu-id="dbf58-135">Para Raspberry Pi 2 o 3 elija "ARM" y para Minnowboard Max, elija "x86".</span><span class="sxs-lookup"><span data-stu-id="dbf58-135">For Raspberry Pi 2 or 3 choose "ARM" and for Minnowboard Max, choose "x86".</span></span>

![Equipo remoto](../media/ArduinoWiring/wiringapp_remotemachine.png)

- <span data-ttu-id="dbf58-137">Abra las propiedades de la solución que se encuentra en el menú contextual de depuración en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbf58-137">Open the solution properties found on the Debug context menu in Visual Studio.</span></span>

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties.png)

- <span data-ttu-id="dbf58-139">Busque el nombre de máquina o la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dbf58-139">locate the IP address or machine name of your device.</span></span> <span data-ttu-id="dbf58-140">Usar la aplicación de panel de Windows 10 IoT Core o enlazar el dispositivo a un monitor.</span><span class="sxs-lookup"><span data-stu-id="dbf58-140">Either use the Windows 10 IoT Core Dashboard application or hook up your device to a monitor.</span></span>
- <span data-ttu-id="dbf58-141">Escriba el nombre del equipo (minwinpc de forma predeterminada) o la dirección IP del equipo remoto en el campo 'nombre del equipo'.</span><span class="sxs-lookup"><span data-stu-id="dbf58-141">Type the machine name (minwinpc by default) or the IP address of the remote machine into the 'machine name' field.</span></span> <span data-ttu-id="dbf58-142">Si ha cambiado el nombre del dispositivo a algo además 'minwinpc' use ese nombre en el cuadro de inicio de sesión en su lugar.</span><span class="sxs-lookup"><span data-stu-id="dbf58-142">If you have renamed your device to something besides 'minwinpc' use that name in the login box instead.</span></span>
- <span data-ttu-id="dbf58-143">Asegúrese de que el tipo Authentican es: Universal (protocolo sin cifrar)</span><span class="sxs-lookup"><span data-stu-id="dbf58-143">Ensure the Authentican Type is: Universal (Unencrypted Protocol)</span></span>

![Propiedades de la solución](../media/ArduinoWiring/wiringapp_properties2.png)

- <span data-ttu-id="dbf58-145">Presione F5 para compilar e implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dbf58-145">Press F5 to build and deploy your project on your device.</span></span>
