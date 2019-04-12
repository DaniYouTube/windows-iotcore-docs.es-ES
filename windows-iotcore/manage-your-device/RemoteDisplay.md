---
title: Visualización remota
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo ver y controlar las aplicaciones de Windows 10 IoT Core UWP de forma remota.
keywords: aplicaciones Windows iot, UWP, visualización remota, remotas, UWP
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514787"
---
# <a name="remote-display"></a><span data-ttu-id="3e18d-104">Visualización remota</span><span class="sxs-lookup"><span data-stu-id="3e18d-104">Remote display</span></span>
<span data-ttu-id="3e18d-105">Ver y controlar las aplicaciones de Windows 10 IoT Core UWP de forma remota, desde un equipo de escritorio de Windows 10, tableta o teléfono</span><span class="sxs-lookup"><span data-stu-id="3e18d-105">View and control your Windows 10 IoT Core UWP applications remotely, from a Windows 10 desktop PC, tablet, or phone</span></span>

> [!WARNING]
> <span data-ttu-id="3e18d-106">Cliente de Windows IoT remoto es una característica única de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="3e18d-106">Windows IoT Remote Client is a developer only feature.</span></span> <span data-ttu-id="3e18d-107">No está diseñada ni compatible con dispositivos de producción.</span><span class="sxs-lookup"><span data-stu-id="3e18d-107">It is not intended or supported for production devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e18d-108">El cliente de Windows IoT remoto no funciona para Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="3e18d-108">The Windows IoT Remote client does not work for Raspberry Pi.</span></span> <span data-ttu-id="3e18d-109">Usar un panel con gráficos acelerados como Minnowboard Max o Dragonboard o adjuntar a un monitor para visualización local.</span><span class="sxs-lookup"><span data-stu-id="3e18d-109">Use a board with accelerated graphics such as Minnowboard Max or Dragonboard or attach a monitor for local display.</span></span>

## <a name="overview"></a><span data-ttu-id="3e18d-110">Información general</span><span class="sxs-lookup"><span data-stu-id="3e18d-110">Overview</span></span>
___
<span data-ttu-id="3e18d-111">La experiencia de pantalla remota es una herramienta de desarrollo que se usa para controlar de forma remota aplicaciones de UWP que se ejecutan en un dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="3e18d-111">The remote display experience is a developer tool used to remotely control UWP applications running on a Windows 10 IoT Core device.</span></span>   

## <a name="setup"></a><span data-ttu-id="3e18d-112">Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="3e18d-112">Setup</span></span>
___
<span data-ttu-id="3e18d-113">Para empezar, deberá configurar un dispositivo Windows 10 IoT Core con la compilación más reciente de Windows 10: visite el [comenzar](https://developer.microsoft.com/en-us/windows/iot/getstarted) página para configurar la placa.</span><span class="sxs-lookup"><span data-stu-id="3e18d-113">To get started, you'll need to set up a Windows 10 IoT Core device with the latest build of Windows 10 - visit the [Get Started](https://developer.microsoft.com/en-us/windows/iot/getstarted) page to set up your board.</span></span>

<span data-ttu-id="3e18d-114">El programa de instalación es rápido y sencillo, siga estos tres pasos para usar la tecnología de pantalla remota.</span><span class="sxs-lookup"><span data-stu-id="3e18d-114">Setup is quick and easy - follow the three steps below to use the remote display technology.</span></span>

1. <span data-ttu-id="3e18d-115">Asegúrese de que el equipo de desarrollo y el dispositivo de IoT Core están en la misma red y n un entorno seguro.</span><span class="sxs-lookup"><span data-stu-id="3e18d-115">Ensure that your IoT Core device and development computer are on the same network and n a secure environment.</span></span>

    <span data-ttu-id="3e18d-116">Es un método conectar el dispositivo directamente a su equipo portátil con un adaptador Ethernet USB que admite cruzado automática.</span><span class="sxs-lookup"><span data-stu-id="3e18d-116">One method is to connect your device directly to your laptop using a USB Ethernet adapter which supports automatic crossover.</span></span>

1. <span data-ttu-id="3e18d-117">Activar la funcionalidad de visualización remota en el dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="3e18d-117">Turn on the remote display functionality on your Windows 10 IoT Core device.</span></span>
  
    <span data-ttu-id="3e18d-118">Conecte el dispositivo a Internet y conectarse a Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="3e18d-118">Connect your device to the Internet and connect to Windows Device Portal.</span></span>
  
    <span data-ttu-id="3e18d-119">Elija la página "Remoto" en las opciones de la izquierda y marque la casilla "Habilitar ventana IoT Remote Server".</span><span class="sxs-lookup"><span data-stu-id="3e18d-119">Choose the page "Remote" from the options on the left, and mark the check box labeled "Enable Window IoT Remote Server".</span></span>  <span data-ttu-id="3e18d-120">El dispositivo ahora está habilitado para la experiencia de pantalla remota.</span><span class="sxs-lookup"><span data-stu-id="3e18d-120">Your device is now enabled for remote display experience.</span></span>
    ![Habilitar la experiencia de visualización remota](../media/RemoteDisplay/enable-remote.png)

1. <span data-ttu-id="3e18d-122">Instale al cliente remoto de Windows IoT en su dispositivo complementario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3e18d-122">Install the Windows IoT Remote Client on your companion Windows 10 device.</span></span>
  
    <span data-ttu-id="3e18d-123">Para habilitar un dispositivo Windows 10 para conectarse a su dispositivo Windows 10 IoT Core, deberá instalar la aplicación Store.</span><span class="sxs-lookup"><span data-stu-id="3e18d-123">To enable a Windows 10 device to connect to your Windows 10 IoT Core device, you need to install our Store application.</span></span>  <span data-ttu-id="3e18d-124">La aplicación cliente de Windows IoT remoto está disponible actualmente solo el vínculo y pueden encontrarse [aquí](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span><span class="sxs-lookup"><span data-stu-id="3e18d-124">The Windows IoT Remote Client app is currently available by link only and can be found [here](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).</span></span>
    
    ![Instalar la aplicación cliente](../media/RemoteDisplay/store-app.png)


1. <span data-ttu-id="3e18d-126">Conectarse al dispositivo de Windows 10 IoT Core a través de la aplicación instalada.</span><span class="sxs-lookup"><span data-stu-id="3e18d-126">Connect to your Windows 10 IoT Core device through the installed application.</span></span>
  
    <span data-ttu-id="3e18d-127">Ejecute la aplicación cliente remota de Windows IoT en el dispositivo complementario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3e18d-127">Run the Windows IoT Remote Client application on your Windows 10 companion device.</span></span>  <span data-ttu-id="3e18d-128">En la pantalla de conexión, escriba la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3e18d-128">At the Connect screen, enter the IP address of your device.</span></span> <span data-ttu-id="3e18d-129">Debe conectar los dos dispositivos, comunicación remota de la experiencia de interfaz de usuario del dispositivo Windows 10 IoT Core para el dispositivo complementario.</span><span class="sxs-lookup"><span data-stu-id="3e18d-129">The two devices should connect, remoting the UI experience of the Windows 10 IoT Core device to the companion device.</span></span>
    
    <span data-ttu-id="3e18d-130">Ahora está conectado.</span><span class="sxs-lookup"><span data-stu-id="3e18d-130">You're now connected!</span></span> <span data-ttu-id="3e18d-131">Desde este punto reenviar, táctil y haga clic en la entrada en el dispositivo puede usarse para controlar la aplicación de Windows 10 IoT Core UWP de Windows 10 complementario.</span><span class="sxs-lookup"><span data-stu-id="3e18d-131">From this point forward, touch and click input on the companion Windows 10 device can be used to control the Windows 10 IoT Core UWP application.</span></span>  
    ![Conexión de dispositivo](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a><span data-ttu-id="3e18d-133">Compatibilidad y ámbito</span><span class="sxs-lookup"><span data-stu-id="3e18d-133">Compatibility and scope</span></span>
___
<span data-ttu-id="3e18d-134">Para poder usar al cliente remoto de IoT, debe estar ejecutando la última compilación de Windows 10 IoT Core en el dispositivo de destino y la aplicación de cliente más reciente desde el almacén de.</span><span class="sxs-lookup"><span data-stu-id="3e18d-134">In order to use the IoT Remote Client, you must be running the latest build of Windows 10 IoT Core on the target device and the latest client application from the store.</span></span> 
    
  
## <a name="troubleshooting"></a><span data-ttu-id="3e18d-135">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="3e18d-135">Troubleshooting</span></span>
___
<span data-ttu-id="3e18d-136">Con la tecnología de pantalla remota es rápido y sencillo, pero todavía hay algunos problemas que pueden experimentar los usuarios.</span><span class="sxs-lookup"><span data-stu-id="3e18d-136">Using the remote display technology is quick and easy, but there are still some issues that users may experience.</span></span>  <span data-ttu-id="3e18d-137">Asegúrese de seguir la configuración de instrucciones anteriores estrechamente - si el problema persiste, consulte los siguientes.</span><span class="sxs-lookup"><span data-stu-id="3e18d-137">Make sure to follow the Setup instructions above closely - if problems persist, check below.</span></span>

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a><span data-ttu-id="3e18d-138">Al intentar conectarse, la aplicación cliente pasa a una pantalla en blanco.</span><span class="sxs-lookup"><span data-stu-id="3e18d-138">When I try to connect, the client app goes to a white screen.</span></span>
<span data-ttu-id="3e18d-139">Las conexiones con error pueden deberse a una serie de problemas, pero hemos ejecutado en un par problemas más comunes:</span><span class="sxs-lookup"><span data-stu-id="3e18d-139">Failed connections can be caused by a number of issues, but we've run into a couple more common problems:</span></span>

1. <span data-ttu-id="3e18d-140">Asegúrese de que se están ejecutando a la insider más reciente versión de Windows 10 IoT Core y la aplicación cliente remota de IoT.</span><span class="sxs-lookup"><span data-stu-id="3e18d-140">Ensure that you are running the latest insider version of Windows 10 IoT Core and the IoT Remote Client application.</span></span>
1. <span data-ttu-id="3e18d-141">En primer lugar, asegúrese de que el dispositivo de IoT se encuentra en la misma red que el dispositivo complementario.</span><span class="sxs-lookup"><span data-stu-id="3e18d-141">First, make sure your IoT device is on the same network as your companion device.</span></span>
    <span data-ttu-id="3e18d-142">Compruebe que está ejecutando la última compilación de Insider de Windows 10 IoT Core con el servidor remoto de Windows IoT habilitado.</span><span class="sxs-lookup"><span data-stu-id="3e18d-142">Check that you're running the latest Insider build of Windows 10 IoT Core with the Windows IoT Remote Server enabled.</span></span>
1. <span data-ttu-id="3e18d-143">Si esto no es el problema, pruebe a cambiar la resolución del dispositivo a algo estamos garantiza la compatibilidad siga las instrucciones que aparecen en el paso 1 de la sección de configuración anterior para desplazarse al servidor web de su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3e18d-143">If this isn't the issue, try changing the resolution of your device to something we're guaranteed to support Follow the instructions in step 1 of the Setup section above to navigate to your device's web server.</span></span>  <span data-ttu-id="3e18d-144">En lugar de seleccionar "Remoto" en el menú de la izquierda, permanecer en la página "Inicio" y desplácese hacia abajo para encontrar la resolución.</span><span class="sxs-lookup"><span data-stu-id="3e18d-144">Instead of selecting "Remote" from the menu on the left, stay on the "Home" page and scroll down to find resolution.</span></span>  <span data-ttu-id="3e18d-145">Pruebe a 800 x 600.</span><span class="sxs-lookup"><span data-stu-id="3e18d-145">Try 800x600.</span></span>
1. <span data-ttu-id="3e18d-146">Si todavía no se soluciona el problema, puede que tenga un problema que proviene de nunca conectar su dispositivo a una pantalla externa.</span><span class="sxs-lookup"><span data-stu-id="3e18d-146">If this still doesn't fix your issue, you may have an issue that stems from never connecting your device to an external display.</span></span>
    <span data-ttu-id="3e18d-147">Esto hará que el dispositivo a pensar en sí mismo como puramente sin periféricos.</span><span class="sxs-lookup"><span data-stu-id="3e18d-147">This will cause the device to think of itself as purely headless.</span></span>  <span data-ttu-id="3e18d-148">Para solucionar este error:</span><span class="sxs-lookup"><span data-stu-id="3e18d-148">To fix this:</span></span>
    * <span data-ttu-id="3e18d-149">Expulse la tarjeta MicroSD y colocan en el equipo</span><span class="sxs-lookup"><span data-stu-id="3e18d-149">Eject the MicroSD Card, and put into your computer</span></span>
    * <span data-ttu-id="3e18d-150">Editar el</span><span class="sxs-lookup"><span data-stu-id="3e18d-150">Edit the</span></span> `<MicroSD card drive>:\config.txt`
    * <span data-ttu-id="3e18d-151">Agregue las siguientes líneas:</span><span class="sxs-lookup"><span data-stu-id="3e18d-151">Add the following lines:</span></span>
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
