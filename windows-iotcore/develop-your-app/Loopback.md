---
title: Comunicación con Localhost
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear una conexión TCP/IP con dos procesos al habilitar bucle invertido localhost.
keywords: Windows iot, localhost, bucle invertido, UWP, visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514247"
---
# <a name="communicating-with-localhost-loopback"></a>Comunicación con el host local (bucle invertido)

En Windows IoT Core, si desea crear una conexión TCP/IP entre 2 procesos que se ejecutan en el mismo dispositivo y una de ellas es una aplicación para UWP debe habilitar bucle invertido localhost.

## <a name="loopback-and-the-debugger"></a>El depurador y en bucle 
De forma predeterminada, que se ejecuta en el depurador de Visual Studio permite bucle invertido de salida automáticamente para esa sesión de depuración solo.  No debería tener que hacer nada, siempre y cuando se activa la casilla de bucle invertido en la configuración del depurador para su proyecto de inicio.  Si desea implementar un agente de escucha de socket se debe habilitar bucle invertido localhost para las conexiones entrantes (ver abajo).
 
## <a name="enabling-the-inbound-loopback-policy"></a>Habilitación de la directiva de bucle invertido de entrada
El host local de entrada directiva de bucle invertido para **Windows IoT Core** debe habilitarse para las que implementar servidores de aplicaciones para UWP.  Esta directiva se controla mediante la clave del registro siguiente:

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

Este valor de clave del registro IoTInboundLoopbackPolicy debe establecerse en DWORD: 00000001 para habilitar. Si cambia el valor del registro de IoTInboundLoopbackPolicy que debe reiniciarse para que el cambio surta efecto.  La directiva de bucle invertido localhost debe estar habilitada de forma predeterminada en **Windows IoT Core**

Para comprobar que el valor es el conjunto ejecute el siguiente comando en el **Windows IoT Core** dispositivo:

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

Para habilitar la directiva de ejecutar el comando siguiente en el **Windows IoT Core** dispositivo:

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a>Habilitación de bucle invertido para una aplicación de UWP
Antes de poder habilitar bucle invertido para una aplicación necesita el nombre de familia de paquete.  Puede encontrar el nombre de familia de paquete para una aplicación instalada mediante la ejecución de **iotstartup lista**.  Si el **iotstartup lista** entrada para la aplicación es IoTCoreDefaultApp\_1w720vyc4ccym! A continuación, el nombre de familia de paquete de aplicación es IoTCoreDefaultApp\_1w720vyc4ccym

Para permitir bucle invertido para su uso de conexiones de cliente `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.  CheckNetIsolation.exe configurará bucle invertido para la aplicación y salir. Esto permitirá que la aplicación realizar conexiones salientes a un servidor.

Por ejemplo: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

Para habilitar una aplicación de servidor recibir conexiones entrantes, use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`. A diferencia de la configuración de conexiones salientes, las conexiones entrantes requieren CheckNetIsolation.exe ejecutar continuamente mientras la aplicación de servidor está recibiendo las conexiones.  Esto requiere una compilación del sistema operativo más reciente que 10.0.14393.

Por ejemplo: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

La mejor manera de ejecutar CheckNetIsolation.exe automáticamente durante el inicio es usar schtasks.exe: `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

Tras reiniciar el sistema debe ser capaz de comprobar que se está ejecutando ese checknetisolation.exe utilizando tlist.exe o [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)
