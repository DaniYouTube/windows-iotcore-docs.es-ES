---
title: Captura de paquetes de red
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar Microsoft Message Analyzer para habilitar la captura de paquetes de red
keywords: Windows iot, el paquete de red, la captura de paquetes de red, Microsoft Message Analyzer, PowerShell
ms.openlocfilehash: 1880b6502099c50653e9e60ebc3d4ff3cd926450
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514435"
---
# <a name="network-packet-capture"></a>Captura de paquetes de red

Puede usar [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226) para capturar, mostrar y analizar el protocolo de mensajería de tráfico en el dispositivo Windows 10 IoT Core.

![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)

## <a name="prerequisites"></a>Requisitos previos

Trabajo PowerShell conexión (paso 1 a 8, se describe en [PowerShell](../connect-your-device/PowerShell.md).

## <a name="set-up-your-device"></a>Configurar el dispositivo

Para poder conectarse al dispositivo con el analizador de mensajes, deberá primero cambie el nombre del dispositivo.  Esto puede hacerse a través de [SSH](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) utilizando el `setcomputername` comando.

![Dispositivo de cambio de nombre de PowerShell](../media/NetworkPacketCapture/powershell-rename-device.png)

Después de cambiar el nombre de su dispositivo, reinicie el dispositivo para aplicar el cambio de nombre.

## <a name="turn-off-the-firewall"></a>Desactivar el firewall

Conectarse al dispositivo mediante PowerShell o SSH y ejecute el siguiente comando para deshabilitar el firewall.
    
    netsh advfirewall set allprofiles state off
    
## <a name="connect-to-your-device-using-message-analyzer"></a>Conectar el dispositivo con el analizador de mensajes

Ahora que el dispositivo se ha configurado, nos conectaremos a ella con el analizador de mensajes de Microsoft.

1. Descargue el [Microsoft Message Analyzer](http://www.microsoft.com/en-us/download/details.aspx?id=44226).
2. Abra el analizador de mensajes.
3. Haga clic en `New Session`.

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. En la ventana que se abre, haga clic en el `Live Trace` botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. Haga clic en el `Edit...` botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. Reemplace Localhost por el nombre del dispositivo de IoT y escriba el nombre de usuario administrador y la contraseña.  A continuación, haga clic en `OK`.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. Haga clic en el `Select a trace scenario` lista desplegable y seleccione `Local Network Interfaces`.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. Haga clic en el `Start` botón.
9. Debe iniciar ver los mensajes que pasen a través de las interfaces de red en el dispositivo.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)
10. Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en el dispositivo [interfaz web](DevicePortal.md).  Para ello, vaya a la pestaña ETW de la interfaz web, seleccione `Microsoft-Windows-NDIS-PacketCapture` desde el `Registered providers` menú desplegable y haga clic en el `Enable` botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/web-etw.png)    
