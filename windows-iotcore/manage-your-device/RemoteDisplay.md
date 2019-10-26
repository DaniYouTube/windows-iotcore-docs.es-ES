---
title: Visualización remota
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo ver y controlar las aplicaciones de UWP de Windows 10 IoT Core de forma remota.
keywords: Windows IOT, UWP, pantalla remota, aplicaciones de UWP remotas
ms.openlocfilehash: c0e082284e5bceb6f1a7a87723e883ad6e552c4e
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917395"
---
# <a name="remote-display"></a><span data-ttu-id="bf897-104">Visualización remota</span><span class="sxs-lookup"><span data-stu-id="bf897-104">Remote display</span></span>
<span data-ttu-id="bf897-105">Ver y controlar las aplicaciones de UWP de Windows 10 IoT Core de forma remota, desde un equipo de escritorio con Windows 10, tableta o teléfono</span><span class="sxs-lookup"><span data-stu-id="bf897-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="bf897-106">El cliente remoto de IoT de Windows es una característica solo para desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="bf897-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="bf897-107">No está prevista ni es compatible con dispositivos de producción.</span><span class="sxs-lookup"><span data-stu-id="bf897-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf897-108">El cliente remoto de Windows IoT no funciona para Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="bf897-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="bf897-109">Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.</span><span class="sxs-lookup"><span data-stu-id="bf897-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="bf897-110">Introducción</span><span class="sxs-lookup"><span data-stu-id="bf897-110">Overview</span></span>
___
<span data-ttu-id="bf897-111">La experiencia de pantalla remota es una herramienta de desarrollo que se usa para controlar de forma remota aplicaciones de UWP que se ejecutan en un dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="bf897-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="bf897-112">Configuración</span><span class="sxs-lookup"><span data-stu-id="bf897-112">Setup</span></span>
___
<span data-ttu-id="bf897-113">Para empezar, necesitará configurar un dispositivo de Windows 10 IoT Core con la compilación más reciente de Windows 10. [visite la página de introducción para](https://developer.microsoft.com/en-us/windows/iot/getstarted) configurar el panel.</span><span class="sxs-lookup"><span data-stu-id="bf897-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="bf897-114">La instalación es rápida y fácil: siga estos tres pasos para usar la tecnología de pantalla remota.</span><span class="sxs-lookup"><span data-stu-id="bf897-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="bf897-115">Asegúrese de que el dispositivo de IoT Core y el equipo de desarrollo se encuentran en la misma red y en un entorno seguro.</span><span class="sxs-lookup"><span data-stu-id="bf897-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="bf897-116">Un método consiste en conectar el dispositivo directamente al portátil mediante un adaptador Ethernet USB que admita la característica de cruce automático.</span><span class="sxs-lookup"><span data-stu-id="bf897-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter which supports automatic crossover.</span></span>

1. <span data-ttu-id="bf897-117">Active la funcionalidad de pantalla remota en el dispositivo de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="bf897-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="bf897-118">Conecte el dispositivo a Internet y conéctese al portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="bf897-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="bf897-119">Elija la página "remota" de las opciones de la izquierda y active la casilla "habilitar ventana de IoT Remote Server".</span><span class="sxs-lookup"><span data-stu-id="bf897-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="bf897-120">El dispositivo ya está habilitado para la experiencia de visualización remota.</span><span class="sxs-lookup"><span data-stu-id="bf897-120">Your device is now enabled for remote display experience.</span></span>
    <span data-ttu-id="bf897-121">![habilitar la experiencia de visualización remota](../media/RemoteDisplay/enable-remote.png)</span><span class="sxs-lookup"><span data-stu-id="bf897-121">![Enable remote display experience](../media/RemoteDisplay/enable-remote.png)</span></span>

1. <span data-ttu-id="bf897-122">Instale el cliente remoto de Windows IoT en el dispositivo de Windows 10 complementario.</span><span class="sxs-lookup"><span data-stu-id="bf897-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="bf897-123">Para permitir que un dispositivo de Windows 10 se conecte a su dispositivo de Windows 10 IoT Core, debe instalar la aplicación de la tienda.</span><span class="sxs-lookup"><span data-stu-id="bf897-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="bf897-124">Actualmente, la aplicación cliente remota de Windows IoT está disponible solo mediante vínculos y se puede encontrar [aquí](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span><span class="sxs-lookup"><span data-stu-id="bf897-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![Instalación de la aplicación cliente](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="bf897-126">Conéctese a su dispositivo Windows 10 IoT Core a través de la aplicación instalada.</span><span class="sxs-lookup"><span data-stu-id="bf897-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="bf897-127">Ejecute la aplicación cliente remoto de Windows IoT en el dispositivo complementario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bf897-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="bf897-128">En la pantalla conectar, escriba la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bf897-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="bf897-129">Los dos dispositivos deben conectarse, la experiencia de la interfaz de usuario del dispositivo Windows 10 IoT Core en el dispositivo complementario.</span><span class="sxs-lookup"><span data-stu-id="bf897-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="bf897-130">Ahora está conectado.</span><span class="sxs-lookup"><span data-stu-id="bf897-130">You're now connected!</span></span> <span data-ttu-id="bf897-131">A partir de este punto, se puede usar la función táctil y hacer clic en entrada en el dispositivo de Windows 10 complementario para controlar la aplicación Windows 10 IoT Core UWP.</span><span class="sxs-lookup"><span data-stu-id="bf897-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![Conectar dispositivo](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="bf897-133">Compatibilidad y ámbito</span><span class="sxs-lookup"><span data-stu-id="bf897-133">Compatibility and scope</span></span>
___
<span data-ttu-id="bf897-134">Para poder usar el cliente remoto de IoT, debe ejecutar la compilación más reciente de Windows 10 IoT Core en el dispositivo de destino y la aplicación cliente más reciente de la tienda.</span><span class="sxs-lookup"><span data-stu-id="bf897-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="bf897-135">de solución de problemas</span><span class="sxs-lookup"><span data-stu-id="bf897-135">Troubleshooting</span></span>
___
<span data-ttu-id="bf897-136">El uso de la tecnología de pantalla remota es rápido y sencillo, pero todavía hay algunos problemas que pueden experimentar los usuarios.</span><span class="sxs-lookup"><span data-stu-id="bf897-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="bf897-137">Asegúrese de seguir las instrucciones de configuración anteriores de cerca. Si el problema persiste, consulte a continuación.</span><span class="sxs-lookup"><span data-stu-id="bf897-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="bf897-138">Cuando intento conectar, la aplicación cliente se dirige a una pantalla en blanco.</span><span class="sxs-lookup"><span data-stu-id="bf897-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="bf897-139">Las conexiones erróneas pueden deberse a una serie de problemas, pero hemos surgido un par de problemas más comunes:</span><span class="sxs-lookup"><span data-stu-id="bf897-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="bf897-140">Asegúrese de que está ejecutando la versión más reciente de Insider de Windows 10 IoT Core y la aplicación cliente remota de IoT.</span><span class="sxs-lookup"><span data-stu-id="bf897-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="bf897-141">En primer lugar, asegúrese de que el dispositivo de IoT se encuentra en la misma red que el dispositivo complementario.</span><span class="sxs-lookup"><span data-stu-id="bf897-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="bf897-142">Compruebe que está ejecutando la última compilación Insider de Windows 10 IoT Core con el servidor remoto de Windows IoT habilitado.</span><span class="sxs-lookup"><span data-stu-id="bf897-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="bf897-143">Si este no es el problema, intente cambiar la resolución del dispositivo a algo que se garantiza que sea compatible, siga las instrucciones descritas en el paso 1 de la sección de configuración anterior para navegar al servidor Web del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bf897-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="bf897-144">En lugar de seleccionar "remoto" en el menú de la izquierda, permanezca en la página "Inicio" y desplácese hacia abajo hasta encontrar resolución.</span><span class="sxs-lookup"><span data-stu-id="bf897-144">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="bf897-145">Pruebe 800x600.</span><span class="sxs-lookup"><span data-stu-id="bf897-145">Try 800x600.</span></span>
1. <span data-ttu-id="bf897-146">Si esto sigue sin solucionar el problema, puede que tenga un problema que se debe a que nunca se conecta el dispositivo a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="bf897-146">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="bf897-147">Esto hará que el dispositivo se considere como sin periféricos.</span><span class="sxs-lookup"><span data-stu-id="bf897-147">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="bf897-148">Para solucionar este error:</span><span class="sxs-lookup"><span data-stu-id="bf897-148">To fix this:</span></span>
    * <span data-ttu-id="bf897-149">Expulse la tarjeta MicroSD y colóquela en el equipo</span><span class="sxs-lookup"><span data-stu-id="bf897-149">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="bf897-150">Editar el `<MicroSD card drive>:\config.txt`</span><span class="sxs-lookup"><span data-stu-id="bf897-150">Edit the `<MicroSD card drive>:\config.txt`</span></span>
    * <span data-ttu-id="bf897-151">Agregue las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="bf897-151">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
