---
title: Comunicación con localhost
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear una conexión TCP/IP con dos procesos habilitando el bucle invertido localhost.
keywords: Windows IOT, localhost, loopback, UWP, Visual Studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170673"
---
# <a name="communicating-with-localhost-loopback"></a>Comunicación con localhost (bucle invertido)

En Windows IoT Core, si desea crear una conexión TCP/IP entre 2 procesos que se ejecutan en el mismo dispositivo y uno de ellos es una aplicación para UWP, debe habilitar el bucle invertido localhost.

## <a name="loopback-and-the-debugger"></a>Bucle invertido y el depurador 
De forma predeterminada, la ejecución en el depurador de Visual Studio solo habilita el bucle invertido de salida automáticamente para esa sesión de depuración.  No debe hacer nada, siempre y cuando la casilla de bucle invertido esté activada en la configuración del depurador del proyecto de inicio.  Si desea implementar un agente de escucha de socket, debe habilitar el bucle invertido localhost para las conexiones entrantes (consulte a continuación).
 
## <a name="enabling-the-inbound-loopback-policy"></a>Habilitar la Directiva de bucle invertido entrante
La Directiva de bucle invertido de entrada localhost para **Windows IOT Core** debe estar habilitada para las aplicaciones UWP que implementan servidores.  Esta directiva está controlada por la siguiente clave del registro:

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

Este valor de clave del registro IoTInboundLoopbackPolicy debe establecerse en DWORD: 00000001 para habilitar. Si cambia el valor del registro IoTInboundLoopbackPolicy, debe reiniciar para que el cambio surta efecto.  La directiva de bucle invertido localhost debe estar habilitada de forma predeterminada en **Windows IoT Core**

Para comprobar que el valor está establecido, ejecute el siguiente comando en el dispositivo **Windows IOT Core** :

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

Para habilitar la Directiva, ejecute el siguiente comando en el dispositivo **Windows IOT Core** :

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a>Habilitación de bucle invertido para una aplicación de UWP
Antes de poder habilitar el bucle invertido para una aplicación, necesitará el nombre de familia del paquete.  Para encontrar el nombre de familia de paquete de una aplicación instalada, ejecute la **lista iotstartup**.  Si la entrada de la **lista de iotstartup** para la\_aplicación es IoTCoreDefaultApp 1w720vyc4ccym! Aplicación, el nombre de familia del paquete\_es IoTCoreDefaultApp 1w720vyc4ccym

Para habilitar el bucle invertido para las `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`conexiones de cliente, use.  CheckNetIsolation. exe configurará el bucle invertido para la aplicación y se cerrará. Esto permitirá que la aplicación realice conexiones salientes a un servidor.

Ejemplo: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

Para permitir que una aplicación de servidor reciba conexiones de entrada `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`, use. A diferencia de la configuración de la conexión de salida, las conexiones entrantes requieren que CheckNetIsolation. exe se ejecute continuamente mientras la aplicación de servidor recibe conexiones.  Esto requiere una compilación de sistema operativo más reciente que 10.0.14393.

Ejemplo: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

La mejor manera de ejecutar CheckNetIsolation. exe automáticamente al iniciar es usar SchTasks. exe:`schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

Tras el reinicio, debería poder comprobar que checknetisolation. exe se está ejecutando mediante Tlist. exe o el [portal de dispositivos de Windows](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal) .
