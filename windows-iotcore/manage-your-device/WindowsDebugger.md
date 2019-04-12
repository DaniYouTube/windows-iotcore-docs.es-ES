---
title: Depurador de Windows
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar el depurador de Windows para depurar el dispositivo Windows IoT Core.
keywords: Windows iot, depurador, depurar, el depurador de Windows, dispositivos, herramientas
ms.openlocfilehash: e56f5ca837de79aaf0c36cf7d3c6ae6badf3fd16
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514752"
---
# <a name="windows-debugger-windbg"></a>Depurador de Windows (WinDbg)
Depurar el dispositivo de Windows 10 IoT Core mediante el potente depurador de Windows, WinDbg.

Las secciones siguientes describen cómo conectar correctamente con WinDbg para un dispositivo Windows 10 IoT Core para propósitos de depuración.  Esto incluye una descripción de la configuración del software necesario en el dispositivo, así como las conexiones de hardware físico.  

WinDbg es un depurador muy eficaz que está familiarizada con la mayoría de los desarrolladores de Windows.  Sin embargo, si acaba de empezar y desea obtener más información acerca de WinDbg, visite los vínculos siguientes:

* [Herramientas de depuración para Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx) 

* [Introducción a la depuración de Windows](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx) 

* [Usar WinDbg de análisis de volcado de bloqueos](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx) 


## <a name="minnowboard-max-mbm"></a>MinnowBoard Max (MBM) 

Puede conectar WinDbg al dispositivo MinnowBoard Max con una conexión de red.

### <a name="setup-network-connection"></a>Configurar conexión de red

Con el fin de habilitar la depuración del kernel con WinDbg a través de una red, asegúrese de que:

* Un cable Ethernet está conectado al dispositivo de MinnowBoard máxima a la red 

* El dispositivo MinnowBoard Max tiene una dirección IP válida en la red

* Una conexión activa con el dispositivo MinnowBoard Max a través de [PowerShell](../connect-your-device/PowerShell.md) 

Mediante la conexión activa de PowerShell, ejecute los comandos siguientes en el número máximo de MinnowBoard para habilitar la depuración a través de la red.

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * Este comando habilita la depuración a través de la red.  Además, especifica la dirección IP del equipo donde se ejecutará WinDbg (DEV_PC_IP_ADDRESS), el número de puerto de red que se usará para que la conexión (PORT_NUM) y una clave única que se utilizará para diferenciar varias conexiones (clave) 

    * Para PORT_NUM y la clave, puede usar los valores siguientes como ejemplos: 50045 y 1.2.3.4 respectivamente, aunque es gratis para cambiarlos como considere oportuno
    
* `bcdedit -debug on`

    * Este comando activa la depuración en el dispositivo 

* En el equipo del desarrollador, inicie WinDbg con la PORT_NUM y los valores de clave proporcionados en los pasos anteriores como sigue: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`

> [!NOTE]
> Si tiene alguno de los kits de Windows instalados, puede resultarle WinDbg bajo
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`

* Reiniciar el dispositivo IoTCore para volver a conectar al depurador

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a>Raspberry Pi 2 o 3 (RPi2 o RPi3) 

Puede conectar WinDbg en Raspberry Pi 2 o 3 mediante una conexión serie.

### <a name="setup-serial-connection"></a>Configuración de una conexión serie

Con el fin de habilitar la depuración del kernel con WinDbg a través de una conexión en serie, asegúrese de que:

* Tiene un cable de depuración, como el Cable USB para TTL de [Adafruit](https://www.adafruit.com/product/954) o [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105). 

* Un cable Ethernet o activa Wi-Fi conectar su Raspberry Pi 2 o 3 del dispositivo a la red (para conexiones IP, como SSH o PowerShell)

* Raspberry Pi 2 o 3 dispositivo tiene una dirección IP válida en la red

* Una conexión activa a Raspberry Pi 2 o 3 dispositivos a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md)

UART0 se usará en el Raspberry Pi 2 o 3 dispositivos para la conexión de depuración del kernel.  A continuación, las asignaciones de pin muestra para el dispositivo Raspberry Pi 2 o 3, así como los cables serie: 

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
            
La idea básica para realizar las conexiones serie correctas es recordar que, mientras que un dispositivo usa su TX para transmitir datos, el otro dispositivo usa su RX para recibir los datos.  Las conexiones recomendadas se enumeran a continuación:

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> La unión EFIESP ya no se crea. Debe montar usted mismo, puede usar el comando mountvol para obtener el GUID.
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

Mediante la conexión activa de PowerShell, ejecute los siguientes comandos en Raspberry Pi 2 o 3 del dispositivo para habilitar la depuración a través de la conexión serie.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * El comando anterior permite la conexión para la depuración serie
    * La velocidad en baudios para Raspberry Pi 2 o 3 está codificado de forma rígida para 921600, por lo que no tiene que especificarlo

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * Este comando activa la depuración en el dispositivo 

En el equipo del desarrollador, obtener el COM para el número de puerto asignado en el sistema para el cable USB para TTL. Esta opción estará disponible en el Administrador de dispositivos bajo "Puertos (COM y LPT)".

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * WinDbg de inicio con el número de puerto
    
> [!NOTE]
> Si tiene alguno de los kits de Windows instalados, puede resultarle WinDbg bajo
`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`

* Reiniciar el dispositivo IoTCore para volver a conectar al depurador


## <a name="dragonboard-db"></a>DragonBoard (DB) 
___

Puede conectar WinDbg para el DragonBoard mediante una serie o una conexión USB.

Con la conexión activa de PowerShell o SSH a su DragonBoard, ejecute los comandos siguientes para habilitar la depuración.

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * Permite al depurador

### <a name="setup-usb-connection"></a>Configuración de una conexión USB
De forma predeterminada, la configuración del depurador USB se configura en las imágenes de prueba. 

> [!NOTE]
> Una vez en el depurador del kernel USB, puertos USB en el dispositivo DragonBoard podrían no funcionar (es decir, el teclado, usb ethernet podría no funcionar).

### <a name="setup-serial-connection"></a>Configuración de una conexión serie

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * Configura el puerto serie

* Reiniciar el dispositivo IoTCore para volver a conectar al depurador
