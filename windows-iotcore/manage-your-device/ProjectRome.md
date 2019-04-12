---
title: Uso de proyecto Roma con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: Obtenga información y conocer los pasos para aprovechar el dispositivo Windows IoT en el mercado.
keywords: dispositivos de Windows 10 IoT Core, proyecto Roma, remotos
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515053"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a><span data-ttu-id="1d7f2-104">Uso de proyecto Roma con Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="1d7f2-104">Using Project Rome with Windows 10 IoT Core</span></span> 
 
<span data-ttu-id="1d7f2-105">[Proyecto Roma](https://developer.microsoft.com/en-us/windows/project-rome) permite trabajar de forma remota con los dispositivos que ejecutan Windows 10 IoT Core utilizando el RemoteSystems y AppServiceProvider APIs.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-105">[Project Rome](https://developer.microsoft.com/en-us/windows/project-rome) allows you to work remotely with devices running Windows 10 IoT Core using the RemoteSystems and AppServiceProvider APIs.</span></span> 
 
<span data-ttu-id="1d7f2-106">En este artículo, analizaremos cómo detectar, control y conectarse a dispositivos que ejecutan Windows 10 IoT Core con Roma del proyecto.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-106">In this article, we'll go through how to discover, control, and connect to devices running Windows 10 IoT Core with Project Rome.</span></span>  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a><span data-ttu-id="1d7f2-107">Detección de dispositivos de IoT Core con las APIs RemoteSystem</span><span class="sxs-lookup"><span data-stu-id="1d7f2-107">Discovering IoT Core devices with the RemoteSystem APIs</span></span> 
 
_<span data-ttu-id="1d7f2-108">Programa de instalación:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-108">Setup:</span></span>_
* <span data-ttu-id="1d7f2-109">Ejecute el ejemplo RemoteSystems en un equipo de escritorio mientras ha iniciado sesión en su cuenta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-109">Run the RemoteSystems sample on a Desktop while signed into your Microsoft account.</span></span>  
* <span data-ttu-id="1d7f2-110">Con ninguna aplicación que se ejecutan en IoT Core, inicie sesión en su cuenta de Microsoft, vaya a Cortana al inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-110">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="1d7f2-111">Pasos a seguir:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-111">Steps:</span></span>_
1. <span data-ttu-id="1d7f2-112">Ejecutar el ejemplo de RemoteSystems en el escritorio</span><span class="sxs-lookup"><span data-stu-id="1d7f2-112">Run the RemoteSystems sample on your desktop</span></span> 
2. <span data-ttu-id="1d7f2-113">Detectando"(1)," haga clic en "Buscar sistemas"</span><span class="sxs-lookup"><span data-stu-id="1d7f2-113">Under "1) Discovery," click "Search for systems"</span></span> 

![Búsqueda de sistemas](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a><span data-ttu-id="1d7f2-115">Controlar los dispositivos de IoT Core con RemoteSystems.LaunchUri</span><span class="sxs-lookup"><span data-stu-id="1d7f2-115">Control IoT Core devices with RemoteSystems.LaunchUri</span></span> 
 
_<span data-ttu-id="1d7f2-116">Programa de instalación:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-116">Setup:</span></span>_
* <span data-ttu-id="1d7f2-117">Ejecute el [RemoteSystems ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras [ha iniciado sesión en su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span><span class="sxs-lookup"><span data-stu-id="1d7f2-117">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span>
* <span data-ttu-id="1d7f2-118">Con ninguna aplicación que se ejecutan en IoT Core, inicie sesión en su cuenta de Microsoft, vaya a Cortana al inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-118">With no app running on IoT Core, sign into your Microsoft account by going to Cortana to login.</span></span> 
 
_<span data-ttu-id="1d7f2-119">Pasos a seguir:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-119">Steps:</span></span>_
1. <span data-ttu-id="1d7f2-120">Encienda la máquina virtual de IoT Core con Cortana e inicie sesión en su cuenta de Microsoft de Cortana.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-120">Turn on the IoT Core virtual machine with Cortana and sign into your Microsoft account from Cortana.</span></span> 
2. <span data-ttu-id="1d7f2-121">Ejecute el ejemplo RemoteSystems en escritorio.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-121">Run the RemoteSystems sample on Desktop.</span></span> 
3. <span data-ttu-id="1d7f2-122">Detectando"(1)", haga clic en "Buscar sistemas".</span><span class="sxs-lookup"><span data-stu-id="1d7f2-122">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="1d7f2-123">En "(2) inicio URI", seleccione el dispositivo de IoT Core que se está ejecutando Cortana.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-123">Under "2) Launch URI", select the IoT Core device that is running Cortana.</span></span> 
5. <span data-ttu-id="1d7f2-124">Escriba este identificador URI y el lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-124">Enter this URI and launch.</span></span> 

![URI de inicio](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a><span data-ttu-id="1d7f2-126">Conectar con el servicio de aplicación remota que se ejecutan en IoT Core</span><span class="sxs-lookup"><span data-stu-id="1d7f2-126">Connecting to the Remote App Service running on IoT Core</span></span> 
_<span data-ttu-id="1d7f2-127">Programa de instalación:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-127">Setup:</span></span>_
* <span data-ttu-id="1d7f2-128">Ejecute el [RemoteSystems ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras [ha iniciado sesión en su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span><span class="sxs-lookup"><span data-stu-id="1d7f2-128">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) on a Desktop while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).</span></span> 
* <span data-ttu-id="1d7f2-129">Asegúrese de tener la [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) implementado y ejecutándose en al menos un dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-129">Make sure to have the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and running on at least one IoT Core device.</span></span> 
 
_<span data-ttu-id="1d7f2-130">Pasos a seguir:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-130">Steps:</span></span>_
1. <span data-ttu-id="1d7f2-131">Convertir en la máquina Virtual de IoT Core con Cortana e inicie sesión en su cuenta de Microsoft de Cortana.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-131">Turn on the IoT Core Virtual Machine with Cortana, and sign into your Microsoft account from Cortana.</span></span> <span data-ttu-id="1d7f2-132">Implementar la aplicación AppServiceProvider, ejecútelo una vez y cerrarlo.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-132">Deploy the AppServiceProvider app, run it once, then shut it down.</span></span> 
2. <span data-ttu-id="1d7f2-133">Ejecute el ejemplo RemoteSystems en escritorio.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-133">Run the RemoteSystems sample on desktop.</span></span> 
3. <span data-ttu-id="1d7f2-134">Detectando"(1)", haga clic en "Buscar sistemas".</span><span class="sxs-lookup"><span data-stu-id="1d7f2-134">Under "1) Discovery", click "Search for systems".</span></span> 
4. <span data-ttu-id="1d7f2-135">En"(3) inicio App Services," select IoT core dispositivo que tenga la aplicación AppServiceProvider implementada y se ha ejecutado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-135">Under "3) Launch App Services," select the IoT core device that has the AppServiceProvider app deployed and has been run previously.</span></span> 
5. <span data-ttu-id="1d7f2-136">Generar un número aleatorio.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-136">Generate a random number.</span></span>  

![Iniciar los servicios de aplicaciones](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a><span data-ttu-id="1d7f2-138">Controlar otros dispositivos y servicios de aplicaciones desde un dispositivo de IoT Core</span><span class="sxs-lookup"><span data-stu-id="1d7f2-138">Controlling other devices and app services from an IoT Core device</span></span> 

_<span data-ttu-id="1d7f2-139">Programa de instalación:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-139">Setup:</span></span>_
* <span data-ttu-id="1d7f2-140">Ejecute el [RemoteSystems ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) implementada en un dispositivo de IoT Core mientras [ha iniciado sesión en su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) desde la aplicación de Cortana.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-140">Run the [RemoteSystems sample](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) deployed on an IoT Core device while [signed into your Microsoft account](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) from the Cortana app.</span></span> 
* <span data-ttu-id="1d7f2-141">Tiene un equipo de escritorio con el [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) implementado y que se ha ejecutado al menos una vez.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-141">Have a desktop machine with the [AppServiceProvider app](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) deployed and having been run at least once.</span></span> 
 
_<span data-ttu-id="1d7f2-142">Pasos a seguir:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-142">Steps:</span></span>_
1. <span data-ttu-id="1d7f2-143">Ejecute el ejemplo RemoteSystems.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-143">Run the RemoteSystems sample.</span></span> 
2. <span data-ttu-id="1d7f2-144">Detectando"(1)", haga clic en "Buscar sistemas".</span><span class="sxs-lookup"><span data-stu-id="1d7f2-144">Under "1) Discovery", click on "Search for systems".</span></span> 
3. <span data-ttu-id="1d7f2-145">En "(2) inicio URI", seleccione el equipo de escritorio e inicie.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-145">Under "2) Launch URI", select the Desktop machine and launch.</span></span> 
4. <span data-ttu-id="1d7f2-146">En "(3) servicios de aplicación de inicio", seleccione la máquina de escritorio.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-146">Under "3) Launch App Services", select the desktop machine.</span></span>  
 
> [!NOTE] 
> <span data-ttu-id="1d7f2-147">En el primer intento, esto puede tardar mucho tiempo.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-147">On first attempt, this may take a long time.</span></span> <span data-ttu-id="1d7f2-148">Inténtelo de nuevo para una cantidad de respuesta más rápida.</span><span class="sxs-lookup"><span data-stu-id="1d7f2-148">Try this again for a much quicker response.</span></span> 
 
### <a name="helpful-links"></a><span data-ttu-id="1d7f2-149">Vínculos útiles:</span><span class="sxs-lookup"><span data-stu-id="1d7f2-149">Helpful links:</span></span> 
* [<span data-ttu-id="1d7f2-150">Documentación del proyecto Roma en MSDN</span><span class="sxs-lookup"><span data-stu-id="1d7f2-150">Project Rome documentation on MSDN</span></span>](https://developer.microsoft.com/en-us/windows/project-rome )
* [<span data-ttu-id="1d7f2-151">Uso de Roma de proyecto para UWP</span><span class="sxs-lookup"><span data-stu-id="1d7f2-151">Using Project Rome for UWP</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
