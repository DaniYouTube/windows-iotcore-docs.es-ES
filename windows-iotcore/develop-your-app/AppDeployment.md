---
title: Implementar una aplicación con Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo implementar una aplicación mediante la característica de depuración remota de Visual Studio.
keywords: Windows iot, visual studio, la implementación de aplicaciones, la depuración remota
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514720"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="6f6b1-104">Implementar una aplicación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f6b1-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="6f6b1-105">Implementar y depurar la aplicación son sencilla con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="6f6b1-106">Vamos a usar el **depuración remota** característica para implementar la aplicación en su dispositivo Windows 10 IoT Core conectado localmente.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="6f6b1-107">Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="6f6b1-108">Para poder usar la depuración remota, el dispositivo de IoT Core en primer lugar debe estar conectado a la misma red local que el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-108">In order to use remote debugging, your IoT Core device must first be connected to same local network as your development PC.</span></span>  
><span data-ttu-id="6f6b1-109">Consulte la [conectarse a un dispositivo](../connect-your-device/SetupWiFi.md) instrucciones.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-109">See the [Connecting to a device](../connect-your-device/SetupWiFi.md) instructions.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="6f6b1-110">Implementar un C# aplicación en el dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="6f6b1-110">Deploy a C# app to your Windows 10 IoT Core device</span></span> 
___

1. <span data-ttu-id="6f6b1-111">Con la aplicación abierta en Visual Studio, establezca la arquitectura en la lista desplegable de la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-111">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="6f6b1-112">Si va a compilar para Minnowboard Max, seleccione `x86`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-112">If you're building for Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="6f6b1-113">Si va a compilar para Raspberry Pi 2, Raspberry Pi 3 o el Dragonboard, seleccione `ARM`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-113">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="6f6b1-114">A continuación, en la barra de herramientas de Visual Studio, haga clic en el `Local Machine` lista desplegable y seleccione `Remote Machine`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-114">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![Máquina remota en Visual Studio](../media/AppDeployment/cs-remote-machine-debugging.png)

3. <span data-ttu-id="6f6b1-116">En este punto, Visual Studio presentará la **conexiones remotas** cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-116">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="6f6b1-117">Si usó anteriormente [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirla aquí (en este ejemplo, estamos usando **mi dispositivo**).</span><span class="sxs-lookup"><span data-stu-id="6f6b1-117">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="6f6b1-118">En caso contrario, utilice la dirección IP del dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-118">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="6f6b1-119">Después de escribir el nombre de dispositivo o dirección IP, seleccione `Universal (Unencrypted Protocol)` modo de autenticación, a continuación, haga clic en **seleccione**.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-119">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![Modo de autenticación universal](../media/AppDeployment/cs-remote-connections.png)

<span data-ttu-id="6f6b1-121">Puede comprobar o modificar estos valores, vaya a las propiedades del proyecto (seleccione **propiedades** en el Explorador de soluciones) y eligiendo la `Debug` ficha a la izquierda:</span><span class="sxs-lookup"><span data-stu-id="6f6b1-121">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![Pestaña Depurar](../media/AppDeployment/cs-debug-project-properties.png)

5. <span data-ttu-id="6f6b1-123">Ahora ya estamos listos para implementar.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-123">Now we're ready to deploy.</span></span> <span data-ttu-id="6f6b1-124">Bastará que presione F5 (o seleccione Depurar \| Iniciar depuración) para iniciar la depuración de nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-124">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="6f6b1-125">Debería ver la aplicación y actuar en la pantalla del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-125">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="6f6b1-126">Una vez implementado, puede establecer puntos de interrupción, vea los valores de variable, etcetera. Para detener la aplicación de prensa en el botón 'Detener depuración' (o seleccione Depurar \| Detener depuración).</span><span class="sxs-lookup"><span data-stu-id="6f6b1-126">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="6f6b1-127">Después de implementar y depurar la aplicación para UWP, crear correctamente una versión de lanzamiento: cambiar la lista desplegable Configuración de barra de herramientas de Visual Studio desde `Debug` a `Release`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-127">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="6f6b1-128">Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando las compilación \| recompilar solución y compilación \| implementar solución.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-128">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a><span data-ttu-id="6f6b1-129">Implementar un C++ aplicación en el dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="6f6b1-129">Deploy a C++ app to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="6f6b1-130">Con la aplicación abierta en Visual Studio, establezca la arquitectura en la lista desplegable de la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-130">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="6f6b1-131">Si va a compilar para Minnowboard Max, seleccione `86`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-131">If you're building for Minnowboard Max, select `86`.</span></span> <span data-ttu-id="6f6b1-132">Si va a compilar para Raspberry Pi 2 o 3, seleccione `ARM`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-132">If you're building for Raspberry Pi 2 or 3, select `ARM`.</span></span>

2. <span data-ttu-id="6f6b1-133">A continuación, en la barra de herramientas de Visual Studio, haga clic en el `Local Machine` lista desplegable y seleccione</span><span class="sxs-lookup"><span data-stu-id="6f6b1-133">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select</span></span> `Remote Machine`

![Máquina local en Visual Studio](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. <span data-ttu-id="6f6b1-135">A continuación, haga clic en el proyecto en el **el Explorador de soluciones** panel.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-135">Next, right click on your project in the **Solution Explorer** pane.</span></span> <span data-ttu-id="6f6b1-136">Seleccione **Propiedades**.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-136">Select **Properties**.</span></span> 

![Propiedades en Visual Studio](../media/AppDeployment/cpp-project-properties.png)

4. <span data-ttu-id="6f6b1-138">En **propiedades de configuración -> depuración**, modifique los campos siguientes:</span><span class="sxs-lookup"><span data-stu-id="6f6b1-138">Under **Configuration Properties -> Debugging**, modify the following fields:</span></span>

    * <span data-ttu-id="6f6b1-139">**Nombre de equipo**: Si usó anteriormente [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirla aquí (en este ejemplo, estamos usando **mi dispositivo**).</span><span class="sxs-lookup"><span data-stu-id="6f6b1-139">**Machine Name**: If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my-device**).</span></span> <span data-ttu-id="6f6b1-140">En caso contrario, utilice la dirección IP del dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-140">Otherwise, use the IP address of your Windows IoT Core device.</span></span>
    * <span data-ttu-id="6f6b1-141">**Modo de autenticación**: Establecido en **Universal (protocolo sin cifrar)**</span><span class="sxs-lookup"><span data-stu-id="6f6b1-141">**Authentication Mode**: Set to **Universal (Unencrypted Protocol)**</span></span>
    
![Modo de autenticación universal](../media/AppDeployment/cpp-debug-project-properties.png)

5. <span data-ttu-id="6f6b1-143">Ahora ya estamos listos para implementar.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-143">Now we're ready to deploy.</span></span> <span data-ttu-id="6f6b1-144">Bastará que presione F5 (o seleccione Depurar \| Iniciar depuración) para iniciar la depuración de nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-144">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="6f6b1-145">Debería ver que la aplicación aparezca en la pantalla del dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-145">You should see the app come up in Windows IoT Core device screen.</span></span>

6. <span data-ttu-id="6f6b1-146">Una vez implementado, puede establecer puntos de interrupción, vea los valores de variable, etcetera. Para detener la aplicación, pulse en el botón 'Detener depuración' (o seleccione Depurar \| Detener depuración).</span><span class="sxs-lookup"><span data-stu-id="6f6b1-146">Once deployed, you can set breakpoints, see variable values, etc. To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

7. <span data-ttu-id="6f6b1-147">Tener correctamente implementado y depurar la aplicación para UWP, cree una versión de lanzamiento: cambiar la lista desplegable Configuración de barra de herramientas de Visual Studio desde `Debug` a `Release`.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-147">Having successfully deployed and debugged your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="6f6b1-148">Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando las compilación \| recompilar solución y compilación \| implementar solución.</span><span class="sxs-lookup"><span data-stu-id="6f6b1-148">You can now build and deploy your app to your device by selecting Build \| Rebuild Solution and Build \| Deploy Solution.</span></span>

