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
# <a name="network-packet-capture"></a>Capturas de paquetes de red

## <a name="note---microsoft-message-analyzer-has-been-deprecated-information-contained-below-is-for-archival-reference-only"></a>Nota: el analizador de mensajes de Microsoft ha [quedado desusado](https://docs.microsoft.com/openspecs/blog/ms-winintbloglp/dd98b93c-0a75-4eb0-b92e-e760c502394f). La información que se incluye a continuación es solo para referencia de archivo.

Puede usar el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226) para capturar, mostrar y analizar el tráfico de mensajes de protocolo en el dispositivo de Windows 10 IOT Core.

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

1. Descargue el [analizador de mensajes de Microsoft](https://www.microsoft.com/download/details.aspx?id=44226).
2. Abra el analizador de mensajes.
3. Haga clic en `New Session`.

    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-new-session.png)
4. En la ventana que se abre, haga clic en el `Live Trace` botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-live-trace.png)
5. Haga clic en el botón `Edit...`.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-button.png)
6. Reemplace localhost con el nombre del dispositivo de IoT y escriba el nombre de usuario y la contraseña del administrador.  A continuación, haga clic en `OK` .
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-edit-target-computers.png)
7. Haga clic en la `Select a trace scenario` lista desplegable y seleccione `Local Network Interfaces` .
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer-trace-scenario.png)
8. Haga clic en el botón `Start`.
9. Debería empezar a ver los mensajes que pasan a través de las interfaces de red del dispositivo.
    ![Analizador de mensajes](../media/NetworkPacketCapture/message-analyzer.png)
10. Después de iniciar el seguimiento a través del analizador de mensajes, también puede ver los mensajes ETW desde el controlador de captura de paquetes en la [interfaz web](DevicePortal.md)del dispositivo.  Para ello, vaya a la pestaña ETW de la interfaz Web, seleccione `Microsoft-Windows-NDIS-PacketCapture` en el `Registered providers` menú desplegable y haga clic en el `Enable` botón.
    ![Analizador de mensajes](../media/NetworkPacketCapture/web-etw.png)    
