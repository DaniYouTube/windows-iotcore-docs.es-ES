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
# <a name="network-packet-capture"></a>Capturas de paquetes de red

Puede usar el [analizador de mensajes de Microsoft](http://www.microsoft.com/en-us/download/details.aspx?id=44226) para capturar, mostrar y analizar el tráfico de mensajes de protocolo en el dispositivo de Windows 10 IOT Core.

![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>Requisitos previos

Conexión de PowerShell en funcionamiento (paso 1 a 8 descrito en [PowerShell](../connect-your-device/PowerShell.md).

## <a name="set-up-your-device"></a>Configuración del dispositivo

Para conectarse a su dispositivo con el analizador de mensajes, primero debe cambiar el nombre del dispositivo.  Esto puede realizarse a través de [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) mediante el `setcomputername` comando.

![Cambiar el nombre del dispositivo de PowerShell](../media/NetworkPacketCapture/powershell-rename-device.png)

Después de cambiar el nombre del dispositivo, reinicie el dispositivo para aplicar el cambio de nombre.

## <a name="turn-off-the-firewall"></a>Desactivar el Firewall

Conéctese al dispositivo mediante PowerShell o SSH y ejecute el siguiente comando para deshabilitar el firewall.
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>Conectarse al dispositivo con el analizador de mensajes

Ahora que el dispositivo está configurado, vamos a conectarnos con el analizador de mensajes de Microsoft.

1. Descargue el [analizador de mensajes de Microsoft](http://www.microsoft.com/en-us/download/details.aspx?id=44226).
2. Abra el analizador de mensajes.
3. Haga clic `New Session`en.

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. En la ventana que se abre, haga clic `Live Trace` en el botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. Haga clic en `Edit...` el botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. Reemplace localhost con el nombre del dispositivo de IoT y escriba el nombre de usuario y la contraseña del administrador.  A continuación `OK`, haga clic en.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. Haga clic en `Select a trace scenario` la lista desplegable y seleccione. `Local Network Interfaces`
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. Haga clic `Start` en el botón.
9. Debería empezar a ver los mensajes que pasan a través de las interfaces de red del dispositivo.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)
10. Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en la [interfaz web](DevicePortal.md)del dispositivo.  Para ello, vaya a la pestaña ETW de la interfaz Web, seleccione `Microsoft-Windows-NDIS-PacketCapture` en el `Registered providers` menú desplegable y haga clic `Enable` en el botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/web-etw.png)    
