---
title: Implementar una aplicación con Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo implementar una aplicación mediante la característica de depuración remota de Visual Studio.
keywords: Windows IOT, Visual Studio, implementación de aplicaciones, depuración remota
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533387"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="5c0e1-104">Implementar una aplicación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5c0e1-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="5c0e1-105">La implementación y depuración de la aplicación es sencilla con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="5c0e1-106">Usaremos la característica de depuración **remota** para implementar la aplicación en el dispositivo de Windows 10 IOT Core conectado localmente.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="5c0e1-107">Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="5c0e1-108">Para usar la depuración remota, el dispositivo de IoT Core primero debe estar conectado a la misma red local que el equipo de desarrollo y se deben permitir las comunicaciones UDP/TCP en la red.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="5c0e1-109">En caso de duda, consulte con su equipo en el tráfico de red permitido.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="5c0e1-110">Consulte [conexión a un dispositivo](../connect-your-device/SetupWiFi.md) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="5c0e1-111">Implementación de aplicaciones en el dispositivo de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="5c0e1-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="5c0e1-112">Con la aplicación abierta en Visual Studio, establezca la arquitectura en el menú desplegable de la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="5c0e1-113">Si va a compilar un máximo de Minnowboard `x86`, seleccione.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="5c0e1-114">Si va a compilar para Raspberry pi 2, Raspberry PI 3 o Dragonboard, seleccione `ARM`.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="5c0e1-115">Después, en la barra de herramientas de Visual Studio, `Local Machine` haga clic en `Remote Machine`la lista desplegable y seleccione.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![Equipo remoto en Visual Studio](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="5c0e1-117">En este momento, Visual Studio presentará el cuadro de diálogo **conexiones remotas** .</span><span class="sxs-lookup"><span data-stu-id="5c0e1-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="5c0e1-118">Si anteriormente usó [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirlo aquí (en este ejemplo, vamos a usar **el dispositivo**).</span><span class="sxs-lookup"><span data-stu-id="5c0e1-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="5c0e1-119">De lo contrario, use la dirección IP de su dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="5c0e1-120">Después de escribir el nombre del dispositivo/ `Universal (Unencrypted Protocol)` IP, seleccione el modo de autenticación y haga clic en **seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![Modo de autenticación universal](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="5c0e1-122">Puede comprobar o modificar estos valores Si navega a las propiedades del proyecto (seleccione **propiedades** en el explorador de soluciones) y elige la `Debug` pestaña de la izquierda:</span><span class="sxs-lookup"><span data-stu-id="5c0e1-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![Pestaña Depurar](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="5c0e1-124">Ahora estamos listos para implementar.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-124">Now we're ready to deploy.</span></span> <span data-ttu-id="5c0e1-125">Simplemente presione F5 (o seleccione Depurar | Inicie la depuración) para iniciar la depuración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="5c0e1-126">Debería ver que la aplicación aparece en la pantalla del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="5c0e1-127">Una vez implementado, puede establecer puntos de interrupción, ver valores de variables, etc. Para detener la aplicación, presione el botón "detener depuración" (o seleccione Depurar | Detener la depuración).</span><span class="sxs-lookup"><span data-stu-id="5c0e1-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="5c0e1-128">Después de implementar y depurar la aplicación de UWP correctamente, cree una versión de lanzamiento. cambie la lista desplegable `Debug` de `Release`configuración de la barra de herramientas de Visual Studio de a.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="5c0e1-129">Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando compilar | Recompilar solución y compilar | Implemente la solución.</span><span class="sxs-lookup"><span data-stu-id="5c0e1-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
