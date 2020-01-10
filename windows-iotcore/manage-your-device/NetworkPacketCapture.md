---
title: Capturas de paquetes de red
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar el analizador de mensajes de Microsoft para habilitar la captura de paquetes de red
keywords: Windows IOT, paquete de red, captura de paquetes de red, analizador de mensajes de Microsoft, PowerShell
ms.openlocfilehash: 20f280623fc8919a5ebd3b015ece7d29dbe40cb5
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721662"
---
# <a name="network-packet-capture"></a><span data-ttu-id="b3e69-104">Capturas de paquetes de red</span><span class="sxs-lookup"><span data-stu-id="b3e69-104">Network packet capture</span></span>

<span data-ttu-id="b3e69-105">Puede usar el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226) para capturar, mostrar y analizar el tráfico de mensajes de protocolo en el dispositivo de Windows 10 IOT Core.</span><span class="sxs-lookup"><span data-stu-id="b3e69-105">You can use [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="b3e69-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b3e69-107">Prerequisites</span></span>

<span data-ttu-id="b3e69-108">Conexión de PowerShell en funcionamiento (paso 1 a 8 descrito en [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="b3e69-108">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="b3e69-109">Configurar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="b3e69-109">Set up your device</span></span>

<span data-ttu-id="b3e69-110">Para conectarse a su dispositivo con el analizador de mensajes, primero debe cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b3e69-110">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="b3e69-111">Esto puede realizarse a través de [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) mediante el comando `setcomputername`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-111">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![Cambiar el nombre del dispositivo de PowerShell](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="b3e69-113">Después de cambiar el nombre del dispositivo, reinicie el dispositivo para aplicar el cambio de nombre.</span><span class="sxs-lookup"><span data-stu-id="b3e69-113">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="b3e69-114">Desactivar el Firewall</span><span class="sxs-lookup"><span data-stu-id="b3e69-114">Turn off the firewall</span></span>

<span data-ttu-id="b3e69-115">Conéctese al dispositivo mediante PowerShell o SSH y ejecute el siguiente comando para deshabilitar el firewall.</span><span class="sxs-lookup"><span data-stu-id="b3e69-115">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="b3e69-116">Conectarse al dispositivo con el analizador de mensajes</span><span class="sxs-lookup"><span data-stu-id="b3e69-116">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="b3e69-117">Ahora que el dispositivo está configurado, vamos a conectarnos con el analizador de mensajes de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b3e69-117">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="b3e69-118">Descargue el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226).</span><span class="sxs-lookup"><span data-stu-id="b3e69-118">Download the [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="b3e69-119">Abra el analizador de mensajes.</span><span class="sxs-lookup"><span data-stu-id="b3e69-119">Open Message Analyzer.</span></span>
3. <span data-ttu-id="b3e69-120">Haga clic en `New Session`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-120">Click on `New Session`.</span></span>

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="b3e69-122">En la ventana que se abre, haga clic en el botón `Live Trace`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-122">In the window that opens, click on the `Live Trace` button.</span></span>
    <span data-ttu-id="b3e69-123">](../media/NetworkPacketCapture/message-analyzer-live-trace.png) del analizador de mensajes de ![</span><span class="sxs-lookup"><span data-stu-id="b3e69-123">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span></span>
5. <span data-ttu-id="b3e69-124">Haga clic en el botón `Edit...`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-124">Click on the `Edit...` button.</span></span>
    <span data-ttu-id="b3e69-125">](../media/NetworkPacketCapture/message-analyzer-edit-button.png) del analizador de mensajes de ![</span><span class="sxs-lookup"><span data-stu-id="b3e69-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span></span>
6. <span data-ttu-id="b3e69-126">Reemplace localhost con el nombre del dispositivo de IoT y escriba el nombre de usuario y la contraseña del administrador.</span><span class="sxs-lookup"><span data-stu-id="b3e69-126">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="b3e69-127">A continuación, haga clic en `OK`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-127">Then click `OK`.</span></span>
    <span data-ttu-id="b3e69-128">](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png) del analizador de mensajes de ![</span><span class="sxs-lookup"><span data-stu-id="b3e69-128">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span></span>
7. <span data-ttu-id="b3e69-129">Haga clic en la lista desplegable `Select a trace scenario` y seleccione `Local Network Interfaces`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-129">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    <span data-ttu-id="b3e69-130">](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png) del analizador de mensajes de ![</span><span class="sxs-lookup"><span data-stu-id="b3e69-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span></span>
8. <span data-ttu-id="b3e69-131">Haga clic en el botón `Start`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-131">Click the `Start` button.</span></span>
9. <span data-ttu-id="b3e69-132">Debería empezar a ver los mensajes que pasan a través de las interfaces de red del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b3e69-132">You should start to see the messages going through the network interfaces on your device.</span></span>
    <span data-ttu-id="b3e69-133">](../media/NetworkPacketCapture/message-analyzer.png) del analizador de mensajes de ![</span><span class="sxs-lookup"><span data-stu-id="b3e69-133">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span></span>
10. <span data-ttu-id="b3e69-134">Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en la [interfaz web](DevicePortal.md)del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b3e69-134">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="b3e69-135">Para ello, vaya a la pestaña ETW de la interfaz Web, seleccione `Microsoft-Windows-NDIS-PacketCapture` en el menú desplegable `Registered providers` y haga clic en el botón `Enable`.</span><span class="sxs-lookup"><span data-stu-id="b3e69-135">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    <span data-ttu-id="b3e69-136">](../media/NetworkPacketCapture/web-etw.png) del analizador de mensajes de ![</span><span class="sxs-lookup"><span data-stu-id="b3e69-136">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span></span>    
