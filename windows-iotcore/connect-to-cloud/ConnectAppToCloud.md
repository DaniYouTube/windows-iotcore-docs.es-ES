---
title: Conectar su aplicación a la nube
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar su aplicación a la nube.
keywords: Windows iot, en la nube, Azure, Azure IoT Hub
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514776"
---
# <a name="connect-your-app-to-the-cloud"></a><span data-ttu-id="b994f-104">Conectar su aplicación a la nube</span><span class="sxs-lookup"><span data-stu-id="b994f-104">Connect your app to the cloud</span></span>

<span data-ttu-id="b994f-105">Esta guía paso a paso le permitirá familiarizarse con Windows 10 IoT Core, configurar el dispositivo y crear su primera aplicación que se conecta a Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="b994f-105">This step-by-step guide will allow you to familiarize yourself with Windows 10 IoT Core, set up your device and create your first application that connects to Azure IoT Hub.</span></span>

## <a name="step-1-prepare-your-device"></a><span data-ttu-id="b994f-106">Paso 1: Preparar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="b994f-106">Step 1: Prepare your device</span></span>

<span data-ttu-id="b994f-107">Puede encontrar instrucciones sobre cómo preparar el dispositivo en el [obtener la página de introducción de](https://developer.microsoft.com/en-us/windows/iot/getstarted) asegurarse de que se [aprovisione el TPM del dispositivo](../connect-to-cloud/ConnectDeviceToCloud.md)</span><span class="sxs-lookup"><span data-stu-id="b994f-107">You can find instructions on how to prepare your device on the [Get Started Page](https://developer.microsoft.com/en-us/windows/iot/getstarted) Make sure you [provision the TPM of your device](../connect-to-cloud/ConnectDeviceToCloud.md)</span></span>

## <a name="step-2-install-visual-studio-2017-and-tools"></a><span data-ttu-id="b994f-108">Paso 2: Instalar Visual Studio 2017 y herramientas</span><span class="sxs-lookup"><span data-stu-id="b994f-108">Step 2: Install Visual Studio 2017 and tools</span></span>

<span data-ttu-id="b994f-109">Instalar [de Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span><span class="sxs-lookup"><span data-stu-id="b994f-109">Install [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span></span> <span data-ttu-id="b994f-110">Puede instalar cualquier edición de Visual Studio, incluida la edición Community gratis.</span><span class="sxs-lookup"><span data-stu-id="b994f-110">You can install any edition of Visual Studio, including the free Community edition.</span></span>

<span data-ttu-id="b994f-111">Asegúrese de seleccionar el **herramientas de desarrollo de aplicaciones universales de Windows**, el componente necesario para escribir aplicaciones de Windows 10:</span><span class="sxs-lookup"><span data-stu-id="b994f-111">Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:</span></span>

![Herramientas de desarrollo de aplicaciones de Windows universal](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a><span data-ttu-id="b994f-113">Paso 3: Instalar los servicios conectados para Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="b994f-113">Step 3: Install the Connected Services for Azure IoT Hub</span></span>

<span data-ttu-id="b994f-114">Los servicios conectados de la extensión de Visual Studio de Azure IoT Hub le permite conectarse y empezar a interactuar con Azure IoT Hub en menos de un minuto.</span><span class="sxs-lookup"><span data-stu-id="b994f-114">The Connected Services for Azure IoT Hub Visual Studio extension allows you to connect and start interacting with Azure IoT Hub in less than a minute.</span></span>

<span data-ttu-id="b994f-115">Puede instalar la extensión desde el [VS galería](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span><span class="sxs-lookup"><span data-stu-id="b994f-115">You can install the extension from the [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span></span>

## <a name="step-4-create-a-visual-studio-uwp-solution"></a><span data-ttu-id="b994f-116">Paso 4: Crear una solución de UWP de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b994f-116">Step 4: Create a Visual Studio UWP solution</span></span>

<span data-ttu-id="b994f-117">Para crear una solución UWP en Visual Studio, en el **archivo** menú, haga clic en **New** , a continuación, **proyecto**:</span><span class="sxs-lookup"><span data-stu-id="b994f-117">To create a UWP solution in Visual Studio, on the **File** menu, click **New** then **Project**:</span></span>

![Crear un proyecto](../media/ConnectAppToCloud/new_project_menu.png)

<span data-ttu-id="b994f-119">En el cuadro de diálogo nuevo proyecto que aparece, seleccione **Visual de la aplicación vacía (Windows Universal) C#** .</span><span class="sxs-lookup"><span data-stu-id="b994f-119">In the New Project dialog that comes up, select **Blank App (Universal Windows) Visual C#**.</span></span> <span data-ttu-id="b994f-120">Asigne al proyecto un nombre (e.x.</span><span class="sxs-lookup"><span data-stu-id="b994f-120">Give your project a name (e.x.</span></span> <span data-ttu-id="b994f-121">**MyFirstIoTCoreApp**):</span><span class="sxs-lookup"><span data-stu-id="b994f-121">**MyFirstIoTCoreApp**):</span></span>

![Cuadro de diálogo nueva solución](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a><span data-ttu-id="b994f-123">Usar los servicios conectados para Azure IoT Hub para conectarse a Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="b994f-123">Use the Connected Services for Azure IoT Hub to connect to Azure IoT Hub</span></span>

<span data-ttu-id="b994f-124">Siga las instrucciones de la [herramienta Connected Services](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) para conectar el proyecto a Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="b994f-124">Follow the instructions from the [Connected Services tool](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) to connect your project to Azure IoT Hub.</span></span> <span data-ttu-id="b994f-125">La herramienta generará dos funciones `SendDeviceToCloudMessageAsync` y `ReceiveCloudToDeviceMessageAsync` que se puede invocar en cualquier lugar en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b994f-125">The tool will generate two functions, `SendDeviceToCloudMessageAsync` and `ReceiveCloudToDeviceMessageAsync` that you can invoke anywhere in your app.</span></span> <span data-ttu-id="b994f-126">Puede modificar estas funciones como considere oportuno.</span><span class="sxs-lookup"><span data-stu-id="b994f-126">You can modify these functions as you see fit.</span></span>  

