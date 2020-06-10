---
title: Capturas de paquetes de red
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar el analizador de mensajes de Microsoft para habilitar la captura de paquetes de red
keywords: Windows IOT, paquete de red, captura de paquetes de red, analizador de mensajes de Microsoft, PowerShell
ms.openlocfilehash: 2eaca4b71cb00f054ede9c8b159892b9f15c9296
ms.sourcegitcommit: b0ca7e5487469edf5bf199493be71604f3bd3fcd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84563392"
---
# <a name="network-packet-capture"></a><span data-ttu-id="12381-104">Capturas de paquetes de red</span><span class="sxs-lookup"><span data-stu-id="12381-104">Network packet capture</span></span>

## <a name="note---microsoft-message-analyzer-has-been-deprecated-information-contained-below-is-for-archival-reference-only"></a><span data-ttu-id="12381-105">Nota: el analizador de mensajes de Microsoft ha [quedado desusado](https://docs.microsoft.com/openspecs/blog/ms-winintbloglp/dd98b93c-0a75-4eb0-b92e-e760c502394f).</span><span class="sxs-lookup"><span data-stu-id="12381-105">NOTE - Microsoft Message Analyzer has been [deprecated](https://docs.microsoft.com/openspecs/blog/ms-winintbloglp/dd98b93c-0a75-4eb0-b92e-e760c502394f).</span></span> <span data-ttu-id="12381-106">La información que se incluye a continuación es solo para referencia de archivo.</span><span class="sxs-lookup"><span data-stu-id="12381-106">Information contained below is for archival reference only.</span></span>

<span data-ttu-id="12381-107">Puede usar el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226) para capturar, mostrar y analizar el tráfico de mensajes de protocolo en el dispositivo de Windows 10 IOT Core.</span><span class="sxs-lookup"><span data-stu-id="12381-107">You can use [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226) to capture, display, and analyze protocol messaging traffic on your Windows 10 IoT Core device.</span></span>

![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a><span data-ttu-id="12381-109">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="12381-109">Prerequisites</span></span>

<span data-ttu-id="12381-110">Conexión de PowerShell en funcionamiento (paso 1 a 8 descrito en [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="12381-110">Working PowerShell Connection (Step 1 to 8 described at [PowerShell](../connect-your-device/PowerShell.md).</span></span>

## <a name="set-up-your-device"></a><span data-ttu-id="12381-111">Configuración del dispositivo</span><span class="sxs-lookup"><span data-stu-id="12381-111">Set up your device</span></span>

<span data-ttu-id="12381-112">Para conectarse a su dispositivo con el analizador de mensajes, primero debe cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="12381-112">In order to connect to your device using Message Analyzer, you need to first rename your device.</span></span>  <span data-ttu-id="12381-113">Esto puede realizarse a través de [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) mediante el `setcomputername` comando.</span><span class="sxs-lookup"><span data-stu-id="12381-113">This can be done through [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/PowerShell.md) using the `setcomputername` command.</span></span>

![Cambiar el nombre del dispositivo de PowerShell](../media/NetworkPacketCapture/powershell-rename-device.png)

<span data-ttu-id="12381-115">Después de cambiar el nombre del dispositivo, reinicie el dispositivo para aplicar el cambio de nombre.</span><span class="sxs-lookup"><span data-stu-id="12381-115">After you rename your device, reboot the device to apply the name change.</span></span>

## <a name="turn-off-the-firewall"></a><span data-ttu-id="12381-116">Desactivar el Firewall</span><span class="sxs-lookup"><span data-stu-id="12381-116">Turn off the firewall</span></span>

<span data-ttu-id="12381-117">Conéctese al dispositivo mediante PowerShell o SSH y ejecute el siguiente comando para deshabilitar el firewall.</span><span class="sxs-lookup"><span data-stu-id="12381-117">Connect to your device using PowerShell or SSH and run the following command to disable the firewall.</span></span>
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a><span data-ttu-id="12381-118">Conectarse al dispositivo con el analizador de mensajes</span><span class="sxs-lookup"><span data-stu-id="12381-118">Connect to your device using Message Analyzer</span></span>

<span data-ttu-id="12381-119">Ahora que el dispositivo está configurado, vamos a conectarnos con el analizador de mensajes de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="12381-119">Now that your device is set up, let's connect to it using Microsoft Message Analyzer.</span></span>

1. <span data-ttu-id="12381-120">Descargue el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226).</span><span class="sxs-lookup"><span data-stu-id="12381-120">Download the [Microsoft Message Analyzer](https://www.microsoft.com/download/details.aspx?id=44226).</span></span>
2. <span data-ttu-id="12381-121">Abra el analizador de mensajes.</span><span class="sxs-lookup"><span data-stu-id="12381-121">Open Message Analyzer.</span></span>
3. <span data-ttu-id="12381-122">Haga clic en `New Session`.</span><span class="sxs-lookup"><span data-stu-id="12381-122">Click on `New Session`.</span></span>

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. <span data-ttu-id="12381-124">En la ventana que se abre, haga clic en el `Live Trace` botón.</span><span class="sxs-lookup"><span data-stu-id="12381-124">In the window that opens, click on the `Live Trace` button.</span></span>
    <span data-ttu-id="12381-125">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span><span class="sxs-lookup"><span data-stu-id="12381-125">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-live-trace.png)</span></span>
5. <span data-ttu-id="12381-126">Haga clic en el botón `Edit...`.</span><span class="sxs-lookup"><span data-stu-id="12381-126">Click on the `Edit...` button.</span></span>
    <span data-ttu-id="12381-127">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span><span class="sxs-lookup"><span data-stu-id="12381-127">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-button.png)</span></span>
6. <span data-ttu-id="12381-128">Reemplace localhost con el nombre del dispositivo de IoT y escriba el nombre de usuario y la contraseña del administrador.</span><span class="sxs-lookup"><span data-stu-id="12381-128">Replace Localhost with the name of your IoT device, and enter the administrator user name and password.</span></span>  <span data-ttu-id="12381-129">A continuación, haga clic en `OK` .</span><span class="sxs-lookup"><span data-stu-id="12381-129">Then click `OK`.</span></span>
    <span data-ttu-id="12381-130">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span><span class="sxs-lookup"><span data-stu-id="12381-130">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)</span></span>
7. <span data-ttu-id="12381-131">Haga clic en la `Select a trace scenario` lista desplegable y seleccione `Local Network Interfaces` .</span><span class="sxs-lookup"><span data-stu-id="12381-131">Click on the `Select a trace scenario` dropdown and select `Local Network Interfaces`.</span></span>
    <span data-ttu-id="12381-132">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span><span class="sxs-lookup"><span data-stu-id="12381-132">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)</span></span>
8. <span data-ttu-id="12381-133">Haga clic en el botón `Start`.</span><span class="sxs-lookup"><span data-stu-id="12381-133">Click the `Start` button.</span></span>
9. <span data-ttu-id="12381-134">Debería empezar a ver los mensajes que pasan a través de las interfaces de red del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="12381-134">You should start to see the messages going through the network interfaces on your device.</span></span>
    <span data-ttu-id="12381-135">![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)</span><span class="sxs-lookup"><span data-stu-id="12381-135">![Message Analyzer](../media/NetworkPacketCapture/message-analyzer.png)</span></span>
10. <span data-ttu-id="12381-136">Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en la [interfaz web](DevicePortal.md)del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="12381-136">After you start the trace through Message Analyzer, you can also view the ETW messages from the packet capture driver in your device's [web interface](DevicePortal.md).</span></span>  <span data-ttu-id="12381-137">Para ello, vaya a la pestaña ETW de la interfaz Web, seleccione `Microsoft-Windows-NDIS-PacketCapture` en el `Registered providers` menú desplegable y haga clic en el `Enable` botón.</span><span class="sxs-lookup"><span data-stu-id="12381-137">To do this, go to the ETW tab of the web interface, select `Microsoft-Windows-NDIS-PacketCapture` from the `Registered providers` dropdown menu and click the `Enable` button.</span></span>
    <span data-ttu-id="12381-138">![Analizador de mensajes](../media/NetworkPacketCapture/web-etw.png)</span><span class="sxs-lookup"><span data-stu-id="12381-138">![Message Analyzer](../media/NetworkPacketCapture/web-etw.png)</span></span>    
