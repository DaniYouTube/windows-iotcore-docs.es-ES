---
title: Capturas de paquetes de red
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar el analizador de mensajes de Microsoft para habilitar la captura de paquetes de red
keywords: Windows IOT, paquete de red, captura de paquetes de red, analizador de mensajes de Microsoft, PowerShell
ms.openlocfilehash: 1880b6502099c50653e9e60ebc3d4ff3cd926450
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60171022"
---
# <a name="network-packet-capture"></a><span data-ttu-id="157f8-104">Capturas de paquetes de red</span><span class="sxs-lookup"><span data-stu-id="157f8-104">Network packet capture</span></span>

<span data-ttu-id="157f8-105">Puede usar el [analizador de mensajes de Microsoft](http://www.microsoft.com/en-us/download/details.aspx?id=44226) para capturar, mostrar y analizar el tráfico de mensajes de protocolo en el dispositivo de Windows 10 IOT Core.</span><span class="sxs-lookup"><span data-stu-id="157f8-105">You can use [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="157f8-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="157f8-107">Prerequisites</span></span>

<span data-ttu-id="157f8-108">Conexión de PowerShell en funcionamiento (paso 1 a 8 descrito en [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="157f8-108">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="157f8-109">Configuración del dispositivo</span><span class="sxs-lookup"><span data-stu-id="157f8-109">Set up your device</span></span>

<span data-ttu-id="157f8-110">Para conectarse a su dispositivo con el analizador de mensajes, primero debe cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="157f8-110">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="157f8-111">Esto puede realizarse a través de [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) mediante el `setcomputername` comando.</span><span class="sxs-lookup"><span data-stu-id="157f8-111">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![Cambiar el nombre del dispositivo de PowerShell](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="157f8-113">Después de cambiar el nombre del dispositivo, reinicie el dispositivo para aplicar el cambio de nombre.</span><span class="sxs-lookup"><span data-stu-id="157f8-113">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="157f8-114">Desactivar el Firewall</span><span class="sxs-lookup"><span data-stu-id="157f8-114">Turn off the firewall</span></span>

<span data-ttu-id="157f8-115">Conéctese al dispositivo mediante PowerShell o SSH y ejecute el siguiente comando para deshabilitar el firewall.</span><span class="sxs-lookup"><span data-stu-id="157f8-115">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="157f8-116">Conectarse al dispositivo con el analizador de mensajes</span><span class="sxs-lookup"><span data-stu-id="157f8-116">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="157f8-117">Ahora que el dispositivo está configurado, vamos a conectarnos con el analizador de mensajes de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="157f8-117">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="157f8-118">Descargue el [analizador de mensajes de Microsoft](http://www.microsoft.com/en-us/download/details.aspx?id=44226).</span><span class="sxs-lookup"><span data-stu-id="157f8-118">Download the [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="157f8-119">Abra el analizador de mensajes.</span><span class="sxs-lookup"><span data-stu-id="157f8-119">Open Message Analyzer.</span></span>
3. <span data-ttu-id="157f8-120">Haga clic `New Session`en.</span><span class="sxs-lookup"><span data-stu-id="157f8-120">Click on `New Session`.</span></span>

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="157f8-122">En la ventana que se abre, haga clic `Live Trace` en el botón.</span><span class="sxs-lookup"><span data-stu-id="157f8-122">In the window that opens, click on the `Live Trace` button.</span></span>
    <span data-ttu-id="157f8-123">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span><span class="sxs-lookup"><span data-stu-id="157f8-123">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span></span>
5. <span data-ttu-id="157f8-124">Haga clic en `Edit...` el botón.</span><span class="sxs-lookup"><span data-stu-id="157f8-124">Click on the `Edit...` button.</span></span>
    <span data-ttu-id="157f8-125">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span><span class="sxs-lookup"><span data-stu-id="157f8-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span></span>
6. <span data-ttu-id="157f8-126">Reemplace localhost con el nombre del dispositivo de IoT y escriba el nombre de usuario y la contraseña del administrador.</span><span class="sxs-lookup"><span data-stu-id="157f8-126">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="157f8-127">A continuación `OK`, haga clic en.</span><span class="sxs-lookup"><span data-stu-id="157f8-127">Then click `OK`.</span></span>
    <span data-ttu-id="157f8-128">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span><span class="sxs-lookup"><span data-stu-id="157f8-128">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span></span>
7. <span data-ttu-id="157f8-129">Haga clic en `Select a trace scenario` la lista desplegable y seleccione. `Local Network Interfaces`</span><span class="sxs-lookup"><span data-stu-id="157f8-129">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    <span data-ttu-id="157f8-130">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span><span class="sxs-lookup"><span data-stu-id="157f8-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span></span>
8. <span data-ttu-id="157f8-131">Haga clic `Start` en el botón.</span><span class="sxs-lookup"><span data-stu-id="157f8-131">Click the `Start` button.</span></span>
9. <span data-ttu-id="157f8-132">Debería empezar a ver los mensajes que pasan a través de las interfaces de red del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="157f8-132">You should start to see the messages going through the network interfaces on your device.</span></span>
    <span data-ttu-id="157f8-133">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)</span><span class="sxs-lookup"><span data-stu-id="157f8-133">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span></span>
10. <span data-ttu-id="157f8-134">Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en la [interfaz web](DevicePortal.md)del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="157f8-134">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="157f8-135">Para ello, vaya a la pestaña ETW de la interfaz Web, seleccione `Microsoft-Windows-NDIS-PacketCapture` en el `Registered providers` menú desplegable y haga clic `Enable` en el botón.</span><span class="sxs-lookup"><span data-stu-id="157f8-135">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    <span data-ttu-id="157f8-136">![Analizador de mensajes](../media/NetworkPacketCapture/web-etw.png)</span><span class="sxs-lookup"><span data-stu-id="157f8-136">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span></span>    
