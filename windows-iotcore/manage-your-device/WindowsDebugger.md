---
title: Depurador de Windows
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar el depurador de Windows para depurar el dispositivo Windows IoT Core.
keywords: Windows IOT, depurador, depuración, depurador de Windows, dispositivos, herramientas
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170283"
---
# <a name="windows-debugger-windbg"></a>Depurador de Windows (WinDbg)
Depure el dispositivo de Windows 10 IoT Core mediante el potente depurador de Windows, WinDbg.

En las secciones siguientes se describe cómo conectarse correctamente a WinDbg a un dispositivo de Windows 10 IoT Core con fines de depuración.  Esto incluye una descripción de la configuración de software necesaria en el dispositivo, así como las conexiones de hardware físico.  

WinDbg es un depurador muy eficaz con el que están familiarizados la mayoría de los desarrolladores de Windows.  Sin embargo, si acaba de empezar y desea obtener más información sobre WinDbg, visite los vínculos siguientes:

* [Herramientas de depuración para Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [Introducción con depuración de Windows](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [Análisis de volcado de memoria mediante WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

Puede conectar WinDbg al dispositivo MinnowBoard Max mediante una conexión de red.

### <a name="setup-network-connection"></a>Configuración de la conexión de red

Para habilitar la depuración del kernel con WinDbg a través de una red, asegúrese de que:

* Un cable Ethernet está conectado al dispositivo MinnowBoard Max a la red 

* El dispositivo MinnowBoard Max tiene una dirección IP válida en la red

* Una conexión activa con el dispositivo MinnowBoard Max a través de [PowerShell](../connect-your-device/PowerShell.md) 

Con la conexión activa de PowerShell, ejecute los siguientes comandos en MinnowBoard Max para habilitar la depuración a través de la red.

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * Este comando habilita la depuración a través de la red.  Además, especifica la dirección IP del equipo en el que se ejecutará WinDbg (DEV_PC_IP_ADDRESS), el número de puerto de red que se usará para la conexión (PORT_NUM) y una clave única que se usará para diferenciar varias conexiones (clave). 

    * Para PORT_NUM y KEY, puede usar los siguientes valores como ejemplos: 50045 y 1.2.3.4, respectivamente, aunque es gratis cambiarlos como considere oportuno
    
* `bcdedit -debug on`

    * Este comando activa la depuración en el dispositivo 

* En el equipo del desarrollador, inicie WinDbg con el PORT_NUM y los valores de clave proporcionados en los pasos anteriores de la siguiente manera:`"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> Si tiene alguno de los kits de Windows instalados, puede encontrar WinDbg en`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* Reinicio del dispositivo IoTCore para volver a conectar con el depurador

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry pi 2 o 3 (RPi2 o RPi3) 

Puede conectar WinDbg a Raspberry pi 2 o 3 mediante una conexión serie.

### <a name="setup-serial-connection"></a>Configuración de la conexión serie

Para habilitar la depuración del kernel con WinDbg a través de una conexión serie, asegúrese de que:

* Tiene un cable de depuración como el cable serie de USB a TTL de [Adafruit](https://www.adafruit.com/product/954) o [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105). 

* Un cable Ethernet o Wi-Fi activo que conecta el dispositivo Raspberry pi 2 o 3 con la red (para conexiones IP como SSH o PowerShell)

* El dispositivo Raspberry pi 2 o 3 tiene una dirección IP válida en la red

* Una conexión activa al dispositivo Raspberry pi 2 ó 3 a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md)

UART0 se usará en el dispositivo Raspberry pi 2 o 3 para la conexión de depuración del kernel.  A continuación se muestran las asignaciones de PIN para Raspberry pi 2 o 3, así como los cables serie: 

        Raspberry Pi 2 or 3 pins:
            Pin #6 : GND
            Pin #8 : UART0 TX (3.3V)
            pin #10: UART0 RX (3.3V)

        Adafruit Cable:
            Black  : GND
            White  : RX  (3.3V)
            Green  : TX  (3.3V)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
        
        FTDI Cable:
            Black  : GND
            Brown  : CTS (NOT USED)
            Red    : PWR (5.0V NOT USED) <- DO NOT CONNECT!!
            Orange : TX  (3.3V)
            Yellow : RX  (3.3V)
            Green  : RTS (NOT USED)
            
La idea básica de establecer las conexiones serie correctas es recordar que mientras un dispositivo usa su TX para transmitir datos, el otro dispositivo usa su RX para recibir los datos.  A continuación se enumeran las conexiones recomendadas:

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> Ya no se crea la Unión EFIESP. Tendrá que montarla usted mismo, puede usar el comando mountvol para obtener el GUID.
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

Con la conexión activa de PowerShell, ejecute los siguientes comandos en el dispositivo Raspberry pi 2 o 3 para habilitar la depuración a través de la conexión serie.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * El comando anterior habilita la conexión serie para la depuración
    * La velocidad en baudios de Raspberry pi 2 o 3 está codificada de forma rígida en 921600, por lo que no tiene que especificarla

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * Este comando activa la depuración en el dispositivo 

En el equipo del desarrollador, obtenga el puerto del número de puerto COM asignado en el sistema para el cable USB a TTL. Estará disponible en Device Manager en "puertos (COM & LPT)".

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * Iniciar WinDbg con el número de Puerto
    
> [!NOTE]
> Si tiene alguno de los kits de Windows instalados, puede encontrar WinDbg en`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* Reinicio del dispositivo IoTCore para volver a conectar con el depurador


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

Puede conectar WinDbg a DragonBoard mediante una conexión USB o serie.

Mediante la conexión activa de PowerShell o SSH con el DragonBoard, ejecute los siguientes comandos para habilitar la depuración.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * Habilita el depurador

### <a name="setup-usb-connection"></a>Configuración de la conexión USB
De forma predeterminada, la configuración del depurador USB se configura en las imágenes de prueba. 

> [!NOTE]
> Una vez que el depurador de kernel USB está activado, es posible que los puertos USB en el dispositivo DragonBoard no funcionen (es decir, teclado, Ethernet USB podría no funcionar).

### <a name="setup-serial-connection"></a>Configuración de la conexión serie

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * Configura el puerto serie

* Reinicio del dispositivo IoTCore para volver a conectar con el depurador
