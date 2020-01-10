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
# <a name="network-packet-capture"></a>Capturas de paquetes de red

Puede usar el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226) para capturar, mostrar y analizar el tráfico de mensajes de protocolo en el dispositivo de Windows 10 IOT Core.

![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>Requisitos previos

Conexión de PowerShell en funcionamiento (paso 1 a 8 descrito en [PowerShell](../connect-your-device/PowerShell.md).

## <a name="set-up-your-device"></a>Configurar el dispositivo

Para conectarse a su dispositivo con el analizador de mensajes, primero debe cambiar el nombre del dispositivo.  Esto puede realizarse a través de [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) mediante el comando `setcomputername`.

![Cambiar el nombre del dispositivo de PowerShell](../media/NetworkPacketCapture/powershell-rename-device.png)

Después de cambiar el nombre del dispositivo, reinicie el dispositivo para aplicar el cambio de nombre.

## <a name="turn-off-the-firewall"></a>Desactivar el Firewall

Conéctese al dispositivo mediante PowerShell o SSH y ejecute el siguiente comando para deshabilitar el firewall.
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>Conectarse al dispositivo con el analizador de mensajes

Ahora que el dispositivo está configurado, vamos a conectarnos con el analizador de mensajes de Microsoft.

1. Descargue el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226).
2. Abra el analizador de mensajes.
3. Haga clic en `New Session`.

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. En la ventana que se abre, haga clic en el botón `Live Trace`.
    ](../media/NetworkPacketCapture/message-analyzer-live-trace.png) del analizador de mensajes de ![
5. Haga clic en el botón `Edit...`.
    ](../media/NetworkPacketCapture/message-analyzer-edit-button.png) del analizador de mensajes de ![
6. Reemplace localhost con el nombre del dispositivo de IoT y escriba el nombre de usuario y la contraseña del administrador.  A continuación, haga clic en `OK`.
    ](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png) del analizador de mensajes de ![
7. Haga clic en la lista desplegable `Select a trace scenario` y seleccione `Local Network Interfaces`.
    ](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png) del analizador de mensajes de ![
8. Haga clic en el botón `Start`.
9. Debería empezar a ver los mensajes que pasan a través de las interfaces de red del dispositivo.
    ](../media/NetworkPacketCapture/message-analyzer.png) del analizador de mensajes de ![
10. Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en la [interfaz web](DevicePortal.md)del dispositivo.  Para ello, vaya a la pestaña ETW de la interfaz Web, seleccione `Microsoft-Windows-NDIS-PacketCapture` en el menú desplegable `Registered providers` y haga clic en el botón `Enable`.
    ](../media/NetworkPacketCapture/web-etw.png) del analizador de mensajes de ![    
