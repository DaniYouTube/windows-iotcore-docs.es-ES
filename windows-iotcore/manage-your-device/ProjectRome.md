---
title: Usar Project Roma con Windows 10 IoT Core
ms.date: 11/14/2017
ms.topic: article
description: Conozca y comprenda los pasos necesarios para poner el dispositivo de Windows IoT en el mercado.
keywords: Windows 10 IoT Core, proyecto Roma, dispositivos remotos
ms.openlocfilehash: dcf1ba9bec776b2ebde0d374266bb4d7dba3baec
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917317"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="59f24-104">Usar Project Roma con Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="59f24-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="59f24-105">[Project Roma](https://developer.microsoft.com/en-us/windows/project-rome) le permite trabajar de forma remota con dispositivos que ejecutan Windows 10 IOT Core con las API de RemoteSystems y AppServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="59f24-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="59f24-106">En este artículo, veremos cómo detectar, controlar y conectar con dispositivos que ejecutan Windows 10 IoT Core con el proyecto Roma.</span><span class="sxs-lookup"><span data-stu-id="59f24-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="59f24-107">Detección de dispositivos IoT Core con las API de RemoteSystem</span><span class="sxs-lookup"><span data-stu-id="59f24-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
<span data-ttu-id="59f24-108">_Archivo_</span><span class="sxs-lookup"><span data-stu-id="59f24-108">_Setup:_</span></span>
* <span data-ttu-id="59f24-109">Ejecute el ejemplo RemoteSystems en un escritorio mientras está conectado a su cuenta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59f24-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="59f24-110">Sin ninguna aplicación que se ejecute en IoT Core, inicie sesión en su cuenta de Microsoft yendo a Cortana para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="59f24-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
<span data-ttu-id="59f24-111">_Pasos_</span><span class="sxs-lookup"><span data-stu-id="59f24-111">_Steps:_</span></span>
1. <span data-ttu-id="59f24-112">Ejecutar el ejemplo RemoteSystems en el escritorio</span><span class="sxs-lookup"><span data-stu-id="59f24-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="59f24-113">En "1" detección ", haga clic en" buscar sistemas ".</span><span class="sxs-lookup"><span data-stu-id="59f24-113">Under "1) Discovery," click "Search for systems"</span></span> 

![Buscar sistemas](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="59f24-115">Control de dispositivos IoT Core con RemoteSystems. LaunchUri</span><span class="sxs-lookup"><span data-stu-id="59f24-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
<span data-ttu-id="59f24-116">_Archivo_</span><span class="sxs-lookup"><span data-stu-id="59f24-116">_Setup:_</span></span>
* <span data-ttu-id="59f24-117">Ejecute el [ejemplo RemoteSystems](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras está [conectado a su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span><span class="sxs-lookup"><span data-stu-id="59f24-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="59f24-118">Sin ninguna aplicación que se ejecute en IoT Core, inicie sesión en su cuenta de Microsoft yendo a Cortana para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="59f24-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
<span data-ttu-id="59f24-119">_Pasos_</span><span class="sxs-lookup"><span data-stu-id="59f24-119">_Steps:_</span></span>
1. <span data-ttu-id="59f24-120">Encienda la máquina virtual de IoT Core con Cortana e inicie sesión en el cuenta de Microsoft de Cortana.</span><span class="sxs-lookup"><span data-stu-id="59f24-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="59f24-121">Ejecute el ejemplo RemoteSystems en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="59f24-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="59f24-122">En "1) detección", haga clic en "buscar sistemas".</span><span class="sxs-lookup"><span data-stu-id="59f24-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="59f24-123">En "2) URI de inicio", seleccione el dispositivo de IoT Core que ejecuta Cortana.</span><span class="sxs-lookup"><span data-stu-id="59f24-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="59f24-124">Escriba este URI e inicie.</span><span class="sxs-lookup"><span data-stu-id="59f24-124">Enter this URI and launch.</span></span> 

![Inicio del URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="59f24-126">Conexión al App Service remoto que se ejecuta en IoT Core</span><span class="sxs-lookup"><span data-stu-id="59f24-126">Connecting to the Remote App Service running on IoT Core</span></span> 
<span data-ttu-id="59f24-127">_Archivo_</span><span class="sxs-lookup"><span data-stu-id="59f24-127">_Setup:_</span></span>
* <span data-ttu-id="59f24-128">Ejecute el [ejemplo RemoteSystems](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras está [conectado a su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span><span class="sxs-lookup"><span data-stu-id="59f24-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="59f24-129">Asegúrese de que la [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) se ha implementado y se está ejecutando en al menos un dispositivo IOT Core.</span><span class="sxs-lookup"><span data-stu-id="59f24-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
<span data-ttu-id="59f24-130">_Pasos_</span><span class="sxs-lookup"><span data-stu-id="59f24-130">_Steps:_</span></span>
1. <span data-ttu-id="59f24-131">Encienda la máquina virtual de IoT Core con Cortana e inicie sesión en el cuenta de Microsoft de Cortana.</span><span class="sxs-lookup"><span data-stu-id="59f24-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="59f24-132">Implemente la aplicación AppServiceProvider, ejecútela una vez y ciérrela.</span><span class="sxs-lookup"><span data-stu-id="59f24-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="59f24-133">Ejecute el ejemplo RemoteSystems en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="59f24-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="59f24-134">En "1) detección", haga clic en "buscar sistemas".</span><span class="sxs-lookup"><span data-stu-id="59f24-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="59f24-135">En "3) iniciar App Services", seleccione el dispositivo de IoT Core que tiene implementada la aplicación AppServiceProvider y que se ejecutó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="59f24-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="59f24-136">Generar un número aleatorio.</span><span class="sxs-lookup"><span data-stu-id="59f24-136">Generate a random number.</span></span>  

![Iniciar App Services](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="59f24-138">Control de otros dispositivos y servicios de aplicaciones desde un dispositivo IoT Core</span><span class="sxs-lookup"><span data-stu-id="59f24-138">Controlling other devices and app services from an IoT Core device</span></span> 

<span data-ttu-id="59f24-139">_Archivo_</span><span class="sxs-lookup"><span data-stu-id="59f24-139">_Setup:_</span></span>
* <span data-ttu-id="59f24-140">Ejecute el [ejemplo RemoteSystems](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) implementado en un dispositivo de IOT Core mientras está [conectado a su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) desde la aplicación de Cortana.</span><span class="sxs-lookup"><span data-stu-id="59f24-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="59f24-141">Tener una máquina de escritorio con la [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) implementada y que se haya ejecutado al menos una vez.</span><span class="sxs-lookup"><span data-stu-id="59f24-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
<span data-ttu-id="59f24-142">_Pasos_</span><span class="sxs-lookup"><span data-stu-id="59f24-142">_Steps:_</span></span>
1. <span data-ttu-id="59f24-143">Ejecute el ejemplo RemoteSystems.</span><span class="sxs-lookup"><span data-stu-id="59f24-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="59f24-144">En "1) detección", haga clic en "buscar sistemas".</span><span class="sxs-lookup"><span data-stu-id="59f24-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="59f24-145">En "2) URI de inicio", seleccione la máquina de escritorio y el inicio.</span><span class="sxs-lookup"><span data-stu-id="59f24-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="59f24-146">En "3) iniciar App Services", seleccione la máquina de escritorio.</span><span class="sxs-lookup"><span data-stu-id="59f24-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="59f24-147">En el primer intento, esto puede tardar mucho tiempo.</span><span class="sxs-lookup"><span data-stu-id="59f24-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="59f24-148">Vuelva a intentarlo para obtener una respuesta mucho más rápida.</span><span class="sxs-lookup"><span data-stu-id="59f24-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="59f24-149">Vínculos útiles:</span><span class="sxs-lookup"><span data-stu-id="59f24-149">Helpful links:</span></span> 
* [<span data-ttu-id="59f24-150">Documentación de Project Roma en MSDN</span><span class="sxs-lookup"><span data-stu-id="59f24-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="59f24-151">Usar Project Roma para UWP</span><span class="sxs-lookup"><span data-stu-id="59f24-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
