---
title: Conectar la aplicación a la nube
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar la aplicación a la nube.
keywords: Windows IOT, Cloud, Azure, Azure IoT Hub
ms.openlocfilehash: 281befbbbe5b71dece9b2bc139be1564f5c24a98
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918405"
---
# <a name="connect-your-app-to-the-cloud"></a><span data-ttu-id="9c66d-104">Conectar la aplicación a la nube</span><span class="sxs-lookup"><span data-stu-id="9c66d-104">Connect your app to the cloud</span></span>

<span data-ttu-id="9c66d-105">Esta guía paso a paso le permitirá familiarizarse con Windows 10 IoT Core, configurar el dispositivo y crear la primera aplicación que se conecta a Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="9c66d-105">This step-by-step guide will allow you to familiarize yourself with Windows 10 IoT Core, set up your device and create your first application that connects to Azure IoT Hub.</span></span>

## <a name="step-1-prepare-your-device"></a><span data-ttu-id="9c66d-106">Paso 1: preparar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="9c66d-106">Step 1: Prepare your device</span></span>

<span data-ttu-id="9c66d-107">Puede encontrar instrucciones sobre cómo preparar el dispositivo en la [Página INTRODUCCIÓN](https://developer.microsoft.com/en-us/windows/iot/getstarted) y asegurarse de que [aprovisiona el TPM del dispositivo](../connect-to-cloud/ConnectDeviceToCloud.md)</span><span class="sxs-lookup"><span data-stu-id="9c66d-107">You can find instructions on how to prepare your device on the [Get Started Page](https://developer.microsoft.com/en-us/windows/iot/getstarted) Make sure you [provision the TPM of your device](../connect-to-cloud/ConnectDeviceToCloud.md)</span></span>

## <a name="step-2-install-visual-studio-2017-and-tools"></a><span data-ttu-id="9c66d-108">Paso 2: instalar Visual Studio 2017 y herramientas</span><span class="sxs-lookup"><span data-stu-id="9c66d-108">Step 2: Install Visual Studio 2017 and tools</span></span>

<span data-ttu-id="9c66d-109">Instale [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span><span class="sxs-lookup"><span data-stu-id="9c66d-109">Install [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271).</span></span> <span data-ttu-id="9c66d-110">Puede instalar cualquier edición de Visual Studio, incluida la edición gratuita Community.</span><span class="sxs-lookup"><span data-stu-id="9c66d-110">You can install any edition of Visual Studio, including the free Community edition.</span></span>

<span data-ttu-id="9c66d-111">Asegúrese de seleccionar las **herramientas de desarrollo de aplicaciones universales de Windows**, el componente necesario para escribir aplicaciones Windows 10:</span><span class="sxs-lookup"><span data-stu-id="9c66d-111">Make sure to select the **Universal Windows App Development Tools**, the component required for writing apps Windows 10:</span></span>

![Herramientas de desarrollo de aplicaciones universales de Windows](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a><span data-ttu-id="9c66d-113">Paso 3: instalar el Servicios conectados de Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="9c66d-113">Step 3: Install the Connected Services for Azure IoT Hub</span></span>

<span data-ttu-id="9c66d-114">La Servicios conectados de Azure IoT Hub extensión de Visual Studio le permite conectarse e iniciar la interacción con Azure IoT Hub en menos de un minuto.</span><span class="sxs-lookup"><span data-stu-id="9c66d-114">The Connected Services for Azure IoT Hub Visual Studio extension allows you to connect and start interacting with Azure IoT Hub in less than a minute.</span></span>

<span data-ttu-id="9c66d-115">Puede instalar la extensión desde la [Galería de vs](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span><span class="sxs-lookup"><span data-stu-id="9c66d-115">You can install the extension from the [VS Gallery](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).</span></span>

## <a name="step-4-create-a-visual-studio-uwp-solution"></a><span data-ttu-id="9c66d-116">Paso 4: creación de una solución de UWP de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c66d-116">Step 4: Create a Visual Studio UWP solution</span></span>

<span data-ttu-id="9c66d-117">Para crear una solución de UWP en Visual Studio, en el menú **archivo** , haga clic en **nuevo** y en **proyecto**:</span><span class="sxs-lookup"><span data-stu-id="9c66d-117">To create a UWP solution in Visual Studio, on the **File** menu, click **New** then **Project**:</span></span>

![Creación de nuevo proyecto](../media/ConnectAppToCloud/new_project_menu.png)

<span data-ttu-id="9c66d-119">En el cuadro de diálogo nuevo proyecto que aparece, seleccione **aplicación en blanco (Windows universal C#)** .</span><span class="sxs-lookup"><span data-stu-id="9c66d-119">In the New Project dialog that comes up, select **Blank App (Universal Windows) Visual C#**.</span></span> <span data-ttu-id="9c66d-120">Asigne un nombre al proyecto (e.x.</span><span class="sxs-lookup"><span data-stu-id="9c66d-120">Give your project a name (e.x.</span></span> <span data-ttu-id="9c66d-121">**MyFirstIoTCoreApp**):</span><span class="sxs-lookup"><span data-stu-id="9c66d-121">**MyFirstIoTCoreApp**):</span></span>

![Cuadro de diálogo Nueva solución](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a><span data-ttu-id="9c66d-123">Use el Servicios conectados para que Azure IoT Hub se conecte a Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="9c66d-123">Use the Connected Services for Azure IoT Hub to connect to Azure IoT Hub</span></span>

<span data-ttu-id="9c66d-124">Siga las instrucciones de la [herramienta servicios conectados](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) para conectar el proyecto a Azure IOT Hub.</span><span class="sxs-lookup"><span data-stu-id="9c66d-124">Follow the instructions from the [Connected Services tool](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) to connect your project to Azure IoT Hub.</span></span> <span data-ttu-id="9c66d-125">La herramienta generará dos funciones, `SendDeviceToCloudMessageAsync` y `ReceiveCloudToDeviceMessageAsync` que puede invocar en cualquier parte de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9c66d-125">The tool will generate two functions, `SendDeviceToCloudMessageAsync` and `ReceiveCloudToDeviceMessageAsync` that you can invoke anywhere in your app.</span></span> <span data-ttu-id="9c66d-126">Puede modificar estas funciones como considere oportuno.</span><span class="sxs-lookup"><span data-stu-id="9c66d-126">You can modify these functions as you see fit.</span></span>  

