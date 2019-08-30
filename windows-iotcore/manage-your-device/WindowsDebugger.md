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
# <a name="windows-debugger-windbg"></a><span data-ttu-id="4c7e8-104">Depurador de Windows (WinDbg)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-104">Windows Debugger (WinDbg)</span></span>
<span data-ttu-id="4c7e8-105">Depure el dispositivo de Windows 10 IoT Core mediante el potente depurador de Windows, WinDbg.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-105">Debug your Windows 10 IoT Core device using the powerful Windows debugger, WinDbg.</span></span>

<span data-ttu-id="4c7e8-106">En las secciones siguientes se describe cómo conectarse correctamente a WinDbg a un dispositivo de Windows 10 IoT Core con fines de depuración.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-106">The following sections describe how to successfully connect with WinDbg to a Windows 10 IoT Core device for debugging purposes.</span></span>  <span data-ttu-id="4c7e8-107">Esto incluye una descripción de la configuración de software necesaria en el dispositivo, así como las conexiones de hardware físico.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-107">This includes a description of the necessary software settings on the device as well as the physical hardware connections.</span></span>  

<span data-ttu-id="4c7e8-108">WinDbg es un depurador muy eficaz con el que están familiarizados la mayoría de los desarrolladores de Windows.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-108">WinDbg is a very powerful debugger that most Windows developers are familiar with.</span></span>  <span data-ttu-id="4c7e8-109">Sin embargo, si acaba de empezar y desea obtener más información sobre WinDbg, visite los vínculos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4c7e8-109">However, if you are just getting started and would like to learn more about WinDbg, please visit the following links:</span></span>

* <span data-ttu-id="4c7e8-110">[Herramientas de depuración para Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-110">[Debugging Tools for Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063(v=vs.85).aspx)</span></span> 

* <span data-ttu-id="4c7e8-111">[Introducción con depuración de Windows](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-111">[Getting Started with Windows Debugging](https://msdn.microsoft.com/library/windows/hardware/mt219729(v=vs.85).aspx)</span></span> 

* <span data-ttu-id="4c7e8-112">[Análisis de volcado de memoria mediante WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-112">[Crash Dump Analysis Using WinDbg](https://msdn.microsoft.com/library/windows/hardware/ff539316(v=vs.85).aspx)</span></span> 


## <a name="minnowboard-max-mbm"></a><span data-ttu-id="4c7e8-113">MinnowBoard Max (MBM)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-113">MinnowBoard Max (MBM)</span></span> 

<span data-ttu-id="4c7e8-114">Puede conectar WinDbg al dispositivo MinnowBoard Max mediante una conexión de red.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-114">You can connect WinDbg to the MinnowBoard Max device using a network connection.</span></span>

### <a name="setup-network-connection"></a><span data-ttu-id="4c7e8-115">Configuración de la conexión de red</span><span class="sxs-lookup"><span data-stu-id="4c7e8-115">Setup network connection</span></span>

<span data-ttu-id="4c7e8-116">Para habilitar la depuración del kernel con WinDbg a través de una red, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="4c7e8-116">In order to enable kernel debugging with WinDbg over a network, ensure that:</span></span>

* <span data-ttu-id="4c7e8-117">Un cable Ethernet está conectado al dispositivo MinnowBoard Max a la red</span><span class="sxs-lookup"><span data-stu-id="4c7e8-117">An Ethernet cable is connected to MinnowBoard Max device to your network</span></span> 

* <span data-ttu-id="4c7e8-118">El dispositivo MinnowBoard Max tiene una dirección IP válida en la red</span><span class="sxs-lookup"><span data-stu-id="4c7e8-118">The MinnowBoard Max device has a valid IP address in your network</span></span>

* <span data-ttu-id="4c7e8-119">Una conexión activa con el dispositivo MinnowBoard Max a través de [PowerShell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-119">An active connection to the MinnowBoard Max device via [PowerShell](../connect-your-device/PowerShell.md)</span></span> 

<span data-ttu-id="4c7e8-120">Con la conexión activa de PowerShell, ejecute los siguientes comandos en MinnowBoard Max para habilitar la depuración a través de la red.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-120">Using the active PowerShell connection, execute the following commands on the MinnowBoard Max to enable debugging over the network.</span></span>

* `bcdedit -dbgsettings net hostip:<DEV_PC_IP_ADDRESS> port:<PORT_NUM> key:<KEY>` 

    * <span data-ttu-id="4c7e8-121">Este comando habilita la depuración a través de la red.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-121">This command enables debugging over the network.</span></span>  <span data-ttu-id="4c7e8-122">Además, especifica la dirección IP del equipo en el que se ejecutará WinDbg (DEV_PC_IP_ADDRESS), el número de puerto de red que se usará para la conexión (PORT_NUM) y una clave única que se usará para diferenciar varias conexiones (clave).</span><span class="sxs-lookup"><span data-stu-id="4c7e8-122">Additionally, it specifies the IP address of the PC where WinDbg will be running (DEV_PC_IP_ADDRESS), the network port number to use for the connection (PORT_NUM), and a unique key to be used to differentiate multiple connections (KEY)</span></span> 

    * <span data-ttu-id="4c7e8-123">Para PORT_NUM y KEY, puede usar los siguientes valores como ejemplos: 50045 y 1.2.3.4, respectivamente, aunque es gratis cambiarlos como considere oportuno</span><span class="sxs-lookup"><span data-stu-id="4c7e8-123">For PORT_NUM and KEY, you can use the following values as examples: 50045 and 1.2.3.4 respectively, although you are free to change them as you see fit</span></span>
    
* `bcdedit -debug on`

    * <span data-ttu-id="4c7e8-124">Este comando activa la depuración en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="4c7e8-124">This command turns on debugging on the device</span></span> 

* <span data-ttu-id="4c7e8-125">En el equipo del desarrollador, inicie WinDbg con el PORT_NUM y los valores de clave proporcionados en los pasos anteriores de la siguiente manera:`"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span><span class="sxs-lookup"><span data-stu-id="4c7e8-125">On the developer PC, start WinDbg with the PORT_NUM and the KEY values provided in the previous steps as follows: `"c:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k net:port=<PORT_NUM>,key=<KEY>`</span></span>

> [!NOTE]
> <span data-ttu-id="4c7e8-126">Si tiene alguno de los kits de Windows instalados, puede encontrar WinDbg en`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span><span class="sxs-lookup"><span data-stu-id="4c7e8-126">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe</code>`</span></span>

* <span data-ttu-id="4c7e8-127">Reinicio del dispositivo IoTCore para volver a conectar con el depurador</span><span class="sxs-lookup"><span data-stu-id="4c7e8-127">Reboot the IoTCore device to reconnect to the debugger</span></span>

## <a name="raspberry-pi-2-or-3-rpi2-or-rpi3"></a><span data-ttu-id="4c7e8-128">Raspberry pi 2 o 3 (RPi2 o RPi3)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-128">Raspberry Pi 2 or 3 (RPi2 or RPi3)</span></span> 

<span data-ttu-id="4c7e8-129">Puede conectar WinDbg a Raspberry pi 2 o 3 mediante una conexión serie.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-129">You can connect WinDbg to the Raspberry Pi 2 or 3 using a serial connection.</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="4c7e8-130">Configuración de la conexión serie</span><span class="sxs-lookup"><span data-stu-id="4c7e8-130">Setup serial connection</span></span>

<span data-ttu-id="4c7e8-131">Para habilitar la depuración del kernel con WinDbg a través de una conexión serie, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="4c7e8-131">In order to enable kernel debugging with WinDbg over a serial connection, ensure that:</span></span>

* <span data-ttu-id="4c7e8-132">Tiene un cable de depuración como el cable serie de USB a TTL de [Adafruit](https://www.adafruit.com/product/954) o [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span><span class="sxs-lookup"><span data-stu-id="4c7e8-132">You have a debug cable such as the USB-to-TTL Serial Cable from [Adafruit](https://www.adafruit.com/product/954) or [FTDI](http://shop.clickandbuild.com/cnb/shop/ftdichip?productID=53&op=catalogue-product_info-null&prodCategoryID=105).</span></span> 

* <span data-ttu-id="4c7e8-133">Un cable Ethernet o Wi-Fi activo que conecta el dispositivo Raspberry pi 2 o 3 con la red (para conexiones IP como SSH o PowerShell)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-133">An Ethernet cable or active WiFi connecting your Raspberry Pi 2 or 3 device to your network (for IP connections like SSH or PowerShell)</span></span>

* <span data-ttu-id="4c7e8-134">El dispositivo Raspberry pi 2 o 3 tiene una dirección IP válida en la red</span><span class="sxs-lookup"><span data-stu-id="4c7e8-134">The Raspberry Pi 2 or 3 device has a valid IP address in your network</span></span>

* <span data-ttu-id="4c7e8-135">Una conexión activa al dispositivo Raspberry pi 2 ó 3 a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-135">An active connection to the Raspberry Pi 2 or 3 device via [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md)</span></span>

<span data-ttu-id="4c7e8-136">UART0 se usará en el dispositivo Raspberry pi 2 o 3 para la conexión de depuración del kernel.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-136">UART0 will be used on the Raspberry Pi 2 or 3 device for the kernel debugging connection.</span></span>  <span data-ttu-id="4c7e8-137">A continuación se muestran las asignaciones de PIN para Raspberry pi 2 o 3, así como los cables serie:</span><span class="sxs-lookup"><span data-stu-id="4c7e8-137">The following shows the pin mappings for the Raspberry Pi 2 or 3 as well as the serial cables:</span></span> 

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
            
<span data-ttu-id="4c7e8-138">La idea básica de establecer las conexiones serie correctas es recordar que mientras un dispositivo usa su TX para transmitir datos, el otro dispositivo usa su RX para recibir los datos.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-138">The basic idea for making the correct serial connections is to remember that while one device uses its TX to transmit data, the other device uses its RX to receive the data.</span></span>  <span data-ttu-id="4c7e8-139">A continuación se enumeran las conexiones recomendadas:</span><span class="sxs-lookup"><span data-stu-id="4c7e8-139">Recommended connections are listed below:</span></span>

        If using Adafruit's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [Adafruti] Black (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [Adafruit] White (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [Adafruit] Green (TX)
        
        If using FTDI's serial cable:
            [RPi2 or RPi3] Pin #6  (GND) <-> [FTDI] Black  (GND)
            [RPi2 or RPi3] Pin #8  (TX)  <-> [FTDI] Yellow (RX) 
            [RPi2 or RPi3] Pin #10 (RX)  <-> [FTDI] ORange (TX)

> [!NOTE] 
> <span data-ttu-id="4c7e8-140">Ya no se crea la Unión EFIESP.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-140">The EFIESP junction is no longer created.</span></span> <span data-ttu-id="4c7e8-141">Tendrá que montarla usted mismo, puede usar el comando mountvol para obtener el GUID.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-141">You'll have to mount it yourself,you can use mountvol command to get the GUID.</span></span>
`mkdir C:\EFIESP` 
`mountvol C:\EFIESP \?\Volume{ae420040-0000-0000-0000-200000000000}` 

<span data-ttu-id="4c7e8-142">Con la conexión activa de PowerShell, ejecute los siguientes comandos en el dispositivo Raspberry pi 2 o 3 para habilitar la depuración a través de la conexión serie.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-142">Using the active PowerShell connection, execute the following commands on the Raspberry Pi 2 or 3 device to enable debugging over the serial connection.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -dbgsettings serial` 

    * <span data-ttu-id="4c7e8-143">El comando anterior habilita la conexión serie para la depuración</span><span class="sxs-lookup"><span data-stu-id="4c7e8-143">The above command enables the serial connection for debugging</span></span>
    * <span data-ttu-id="4c7e8-144">La velocidad en baudios de Raspberry pi 2 o 3 está codificada de forma rígida en 921600, por lo que no tiene que especificarla</span><span class="sxs-lookup"><span data-stu-id="4c7e8-144">The baud-rate for the Raspberry Pi 2 or 3 is hard-coded to 921600, so you don't have to specify it</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD -debug on`

    * <span data-ttu-id="4c7e8-145">Este comando activa la depuración en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="4c7e8-145">This command turns on debugging on the device</span></span> 

<span data-ttu-id="4c7e8-146">En el equipo del desarrollador, obtenga el puerto del número de puerto COM asignado en el sistema para el cable USB a TTL.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-146">On the developer PC, get the COM port number PORT assigned in the system for the USB-to-TTL cable.</span></span> <span data-ttu-id="4c7e8-147">Estará disponible en Device Manager en "puertos (COM & LPT)".</span><span class="sxs-lookup"><span data-stu-id="4c7e8-147">This will be available in Device Manager under "Ports (COM & LPT)".</span></span>

* `"C:\Program Files (x86)\Debugging Tools for Windows (x86)\windbg.exe" -k com:port=<PORT>,baud=921600` 

    * <span data-ttu-id="4c7e8-148">Iniciar WinDbg con el número de Puerto</span><span class="sxs-lookup"><span data-stu-id="4c7e8-148">Start WinDbg with the PORT number</span></span>
    
> [!NOTE]
> <span data-ttu-id="4c7e8-149">Si tiene alguno de los kits de Windows instalados, puede encontrar WinDbg en`C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span><span class="sxs-lookup"><span data-stu-id="4c7e8-149">If you have any of the Windows kits installed, you may find WinDbg under `C:\Program Files (x86)\Windows Kits\10\Debuggers\x86\WinDbg.exe`</span></span>

* <span data-ttu-id="4c7e8-150">Reinicio del dispositivo IoTCore para volver a conectar con el depurador</span><span class="sxs-lookup"><span data-stu-id="4c7e8-150">Reboot the IoTCore device to reconnect to the debugger</span></span>


## <a name="dragonboard-db"></a><span data-ttu-id="4c7e8-151">DragonBoard (DB)</span><span class="sxs-lookup"><span data-stu-id="4c7e8-151">DragonBoard (DB)</span></span> 
___

<span data-ttu-id="4c7e8-152">Puede conectar WinDbg a DragonBoard mediante una conexión USB o serie.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-152">You can connect WinDbg to the DragonBoard using a serial or USB connection.</span></span>

<span data-ttu-id="4c7e8-153">Mediante la conexión activa de PowerShell o SSH con el DragonBoard, ejecute los siguientes comandos para habilitar la depuración.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-153">Using the active PowerShell or SSH connection to your DragonBoard, execute the following commands to enable debugging.</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /debug {default} ON`
    * <span data-ttu-id="4c7e8-154">Habilita el depurador</span><span class="sxs-lookup"><span data-stu-id="4c7e8-154">Enables the debugger</span></span>

### <a name="setup-usb-connection"></a><span data-ttu-id="4c7e8-155">Configuración de la conexión USB</span><span class="sxs-lookup"><span data-stu-id="4c7e8-155">Setup USB connection</span></span>
<span data-ttu-id="4c7e8-156">De forma predeterminada, la configuración del depurador USB se configura en las imágenes de prueba.</span><span class="sxs-lookup"><span data-stu-id="4c7e8-156">By default the USB debugger settings are configured in the test images.</span></span> 

> [!NOTE]
> <span data-ttu-id="4c7e8-157">Una vez que el depurador de kernel USB está activado, es posible que los puertos USB en el dispositivo DragonBoard no funcionen (es decir, teclado, Ethernet USB podría no funcionar).</span><span class="sxs-lookup"><span data-stu-id="4c7e8-157">Once USB kernel debugger is on, USB ports on the DragonBoard device might not work (i.e. keyboard, usb ethernet might not work).</span></span>

### <a name="setup-serial-connection"></a><span data-ttu-id="4c7e8-158">Configuración de la conexión serie</span><span class="sxs-lookup"><span data-stu-id="4c7e8-158">Setup serial connection</span></span>

* `bcdedit /store c:\EFIESP\EFI\Microsoft\Boot\BCD /dbgsettings  Serial debugport:1 baudrate:115200`
    * <span data-ttu-id="4c7e8-159">Configura el puerto serie</span><span class="sxs-lookup"><span data-stu-id="4c7e8-159">Configures the serial port</span></span>

* <span data-ttu-id="4c7e8-160">Reinicio del dispositivo IoTCore para volver a conectar con el depurador</span><span class="sxs-lookup"><span data-stu-id="4c7e8-160">Reboot the IoTCore device to reconnect to the debugger</span></span>
