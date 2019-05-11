---
title: Implementar una aplicación con Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo implementar una aplicación mediante la característica de depuración remota de Visual Studio.
keywords: Windows iot, visual studio, la implementación de aplicaciones, la depuración remota
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533387"
---
# <a name="deploying-an-app-with-visual-studio"></a><span data-ttu-id="e8de9-104">Implementar una aplicación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e8de9-104">Deploying an App with Visual Studio</span></span>

<span data-ttu-id="e8de9-105">Implementar y depurar la aplicación son sencilla con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e8de9-105">Deploying and debugging your application is straightforward with Visual Studio.</span></span> <span data-ttu-id="e8de9-106">Vamos a usar el **depuración remota** característica para implementar la aplicación en su dispositivo Windows 10 IoT Core conectado localmente.</span><span class="sxs-lookup"><span data-stu-id="e8de9-106">We'll use the **Remote Debugging** feature to deploy the app to your locally connected Windows 10 IoT Core device.</span></span> 

> [!NOTE]
> <span data-ttu-id="e8de9-107">Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.</span><span class="sxs-lookup"><span data-stu-id="e8de9-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

> [!NOTE]
> <span data-ttu-id="e8de9-108">Para poder usar la depuración remota, el dispositivo de IoT Core en primer lugar debe estar conectado a la misma red local que el equipo de desarrollo y las comunicaciones TCP/UDP deben permitirse en la red.</span><span class="sxs-lookup"><span data-stu-id="e8de9-108">In order to use remote debugging, your IoT Core device must first be connected to the same local network as your development PC and UDP/TCP communications should be allowed on the network.</span></span> <span data-ttu-id="e8de9-109">En caso de duda, póngase en contacto con el departamento de TI en el tráfico de red permitido.</span><span class="sxs-lookup"><span data-stu-id="e8de9-109">If in doubt, check with your IT on allowed network traffic.</span></span> <span data-ttu-id="e8de9-110">Consulte [conectarse a un dispositivo](../connect-your-device/SetupWiFi.md) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="e8de9-110">See [Connecting to a device](../connect-your-device/SetupWiFi.md) for instructions.</span></span>

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a><span data-ttu-id="e8de9-111">Implementar aplicaciones en su dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="e8de9-111">Deploy apps to your Windows 10 IoT Core device</span></span>

1. <span data-ttu-id="e8de9-112">Con la aplicación abierta en Visual Studio, establezca la arquitectura en la lista desplegable de la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="e8de9-112">With the application open in Visual Studio, set the architecture in the toolbar dropdown.</span></span> <span data-ttu-id="e8de9-113">Si va a compilar para un máximo Minnowboard, seleccione `x86`.</span><span class="sxs-lookup"><span data-stu-id="e8de9-113">If you're building for a Minnowboard Max, select `x86`.</span></span> <span data-ttu-id="e8de9-114">Si va a compilar para Raspberry Pi 2, Raspberry Pi 3 o el Dragonboard, seleccione `ARM`.</span><span class="sxs-lookup"><span data-stu-id="e8de9-114">If you're building for Raspberry Pi 2, Raspberry Pi 3 or the Dragonboard, select `ARM`.</span></span>

2. <span data-ttu-id="e8de9-115">A continuación, en la barra de herramientas de Visual Studio, haga clic en el `Local Machine` lista desplegable y seleccione `Remote Machine`.</span><span class="sxs-lookup"><span data-stu-id="e8de9-115">Next, in the Visual Studio toolbar, click on the `Local Machine` dropdown and select `Remote Machine`.</span></span>

![Máquina remota en Visual Studio](../media/AppDeployment/remote-vs.png)

3. <span data-ttu-id="e8de9-117">En este punto, Visual Studio presentará la **conexiones remotas** cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e8de9-117">At this point, Visual Studio will present the **Remote Connections** dialog.</span></span> <span data-ttu-id="e8de9-118">Si usó anteriormente [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirla aquí (en este ejemplo, estamos usando **mi dispositivo**).</span><span class="sxs-lookup"><span data-stu-id="e8de9-118">If you previously used [PowerShell](../connect-your-device/PowerShell.md) to set a unique name for your device, you can enter it here (in this example, we're using **my device**).</span></span> <span data-ttu-id="e8de9-119">En caso contrario, utilice la dirección IP del dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e8de9-119">Otherwise, use the IP address of your Windows IoT Core device.</span></span>

4. <span data-ttu-id="e8de9-120">Después de escribir el nombre de dispositivo o dirección IP, seleccione `Universal (Unencrypted Protocol)` modo de autenticación, a continuación, haga clic en **seleccione**.</span><span class="sxs-lookup"><span data-stu-id="e8de9-120">After entering the device name/IP select `Universal (Unencrypted Protocol)` Authentication Mode, then click **Select**.</span></span> 

![Modo de autenticación universal](../media/AppDeployment/remote-connections.png)

<span data-ttu-id="e8de9-122">Puede comprobar o modificar estos valores, vaya a las propiedades del proyecto (seleccione **propiedades** en el Explorador de soluciones) y eligiendo la `Debug` ficha a la izquierda:</span><span class="sxs-lookup"><span data-stu-id="e8de9-122">You can verify or modify these values by navigating to the project properties (select **Properties** in the Solution Explorer) and choosing the `Debug` tab on the left:</span></span>

![Pestaña Depurar](../media/AppDeployment/debug-tab.png)

5. <span data-ttu-id="e8de9-124">Ahora ya estamos listos para implementar.</span><span class="sxs-lookup"><span data-stu-id="e8de9-124">Now we're ready to deploy.</span></span> <span data-ttu-id="e8de9-125">Bastará que presione F5 (o seleccione Depurar | Iniciar depuración) para iniciar la depuración de nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="e8de9-125">Simply press F5 (or select Debug | Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="e8de9-126">Debería ver la aplicación y actuar en la pantalla del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e8de9-126">You should see the app come up on your device's screen.</span></span>

6. <span data-ttu-id="e8de9-127">Una vez implementado, puede establecer puntos de interrupción, vea los valores de variable, etcetera. Para detener la aplicación de prensa en el botón 'Detener depuración' (o seleccione Depurar | Detenga la depuración).</span><span class="sxs-lookup"><span data-stu-id="e8de9-127">Once deployed, you can set breakpoints, see variable values, etc. To stop the app press on the 'Stop Debugging' button (or select Debug | Stop Debugging).</span></span>

7. <span data-ttu-id="e8de9-128">Después de implementar y depurar la aplicación para UWP, crear correctamente una versión de lanzamiento: cambiar la lista desplegable Configuración de barra de herramientas de Visual Studio desde `Debug` a `Release`.</span><span class="sxs-lookup"><span data-stu-id="e8de9-128">After successfully deploying and debugging your UWP application, create a Release version - change the Visual Studio toolbar configuration dropdown from `Debug` to `Release`.</span></span>  <span data-ttu-id="e8de9-129">Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando las compilación | Solución de regeneración y compilación | Implementar la solución.</span><span class="sxs-lookup"><span data-stu-id="e8de9-129">You can now build and deploy your app to your device by selecting Build | Rebuild Solution and Build | Deploy Solution.</span></span>
