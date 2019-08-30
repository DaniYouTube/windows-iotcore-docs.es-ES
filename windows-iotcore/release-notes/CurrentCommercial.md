---
title: Notas de la versión de la compilación 17763.253
ms.author: saclayt
author: saraclay
ms.date: 02/14/2019
ms.topic: article
description: Lea y obtenga información sobre las novedades en el número de compilación 17763.253 de Windows Insider
keywords: Windows IoT, Windows Insider, notas de la versión
ms.openlocfilehash: 476efb3edb5a260a6366e92927ebd24a4e648a19
ms.sourcegitcommit: 823a8f6967f74d71d5c61fe90f6b63ba79483479
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2019
ms.locfileid: "70159307"
---
# <a name="release-notes-for-build-17763253"></a><span data-ttu-id="c05e2-104">Notas de la versión de la compilación 17763.253</span><span class="sxs-lookup"><span data-stu-id="c05e2-104">Release Notes for Build 17763.253</span></span>
<span data-ttu-id="c05e2-105">_Número de compilación 17763.253. Febrero de 2019._</span><span class="sxs-lookup"><span data-stu-id="c05e2-105">_Build Number 17763.253. February 2019._</span></span>

<span data-ttu-id="c05e2-106">&copy; 2019 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="c05e2-106">&copy; 2019 Microsoft Corporation.</span></span> <span data-ttu-id="c05e2-107">Todos los derechos reservados.</span><span class="sxs-lookup"><span data-stu-id="c05e2-107">All rights reserved.</span></span>

<span data-ttu-id="c05e2-108">En este documento se proporciona la información más reciente y de otro tipo que complementa la documentación incluida con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-108">This document provides late-breaking or other information that supplements the documentation included with the Windows 10 IoT Core.</span></span>

<span data-ttu-id="c05e2-109">Gracias por descargar Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-109">Thank you for downloading Windows 10 IoT Core.</span></span> <span data-ttu-id="c05e2-110">Windows 10 IoT Core es la versión de Windows 10 destinada al desarrollo de dispositivos de uso insertado o dedicado, y es también la elección de la comunidad de fabricantes.</span><span class="sxs-lookup"><span data-stu-id="c05e2-110">Windows 10 IoT Core is the version of Windows 10 intended for development of embedded or dedicated purpose devices and the choice for the Maker community.</span></span> <span data-ttu-id="c05e2-111">Los paquetes de esta versión contienen herramientas y contenido necesarios para instalar Windows 10 IoT Core en la plataforma Minnowboard Max basada en procesadores Intel Atom, Raspberry Pi 2 o 3 basada en Broadcom 2836 o 2837, y DragonBoard 410c basada en procesadores de la serie Snapdragon 400 de Qualcomm.</span><span class="sxs-lookup"><span data-stu-id="c05e2-111">The packages within this release contain tools and content needed to install Windows 10 IoT Core on Minnowboard Max platform based on Intel Atom processers, Raspberry Pi 2/3 based on Broadcom 2836/2837, and Dragonboard 410c based on Qualcomm Snapdragon 400 series processors.</span></span>


## <a name="privacy-statement"></a><span data-ttu-id="c05e2-112">Declaración de privacidad en línea</span><span class="sxs-lookup"><span data-stu-id="c05e2-112">Privacy Statement</span></span>

<span data-ttu-id="c05e2-113">La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar [aquí](http://go.microsoft.com/fwlink/?LinkId=506737).</span><span class="sxs-lookup"><span data-stu-id="c05e2-113">The privacy statement for this version of the Windows operating system can be viewed [here](http://go.microsoft.com/fwlink/?LinkId=506737).</span></span>

<span data-ttu-id="c05e2-114">Pegue el vínculo de redireccionamiento en la ventana del explorador para revisar los términos y condiciones vinculados.</span><span class="sxs-lookup"><span data-stu-id="c05e2-114">You can review linked terms by pasting the forward link into your browser window.</span></span>

## <a name="whats-new-in-this-build"></a><span data-ttu-id="c05e2-115">Novedades de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="c05e2-115">What's new in this build:</span></span> 
* <span data-ttu-id="c05e2-116">Correcciones de errores generales</span><span class="sxs-lookup"><span data-stu-id="c05e2-116">General bug fixes</span></span> 


## <a name="additional-information"></a><span data-ttu-id="c05e2-117">Información adicional</span><span class="sxs-lookup"><span data-stu-id="c05e2-117">Additional Information</span></span>
* <span data-ttu-id="c05e2-118">La versión 2120.0.0.0 de BSP es la usada para la imagen en DragonBoard.</span><span class="sxs-lookup"><span data-stu-id="c05e2-118">The BSP version used for our Dragon Board image is 2120.0.0.0.</span></span> 

## <a name="known-issues-in-this-build"></a><span data-ttu-id="c05e2-119">Problemas conocidos de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="c05e2-119">Known issues in this build:</span></span>
* <span data-ttu-id="c05e2-120">La implementación del controlador F5 de Visual Studio no funciona en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-120">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span>
* <span data-ttu-id="c05e2-121">Los dispositivos que se han instalado a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.</span><span class="sxs-lookup"><span data-stu-id="c05e2-121">Devices that were installed via NOOBS cannot run the bcdedit tool to enable the kernel debugger.</span></span> <span data-ttu-id="c05e2-122">Esto se puede conseguir con la siguiente solución alternativa: \*\* Monte la tarjeta SD en el equipo. \*\* Busque el número de la partición de disco EFIESP con diskpart o Administración de discos (por ejemplo, "M:"). \*\* Ejecute el comando "bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug yes". \*\* Desmonte la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="c05e2-122">This can be achieved with the following workaround: \*\*  Mount the SD card on your PC \*\*  Find the EFIESP drive partition number with diskpart or Disk Management (say it’s “M:”) \*\*  Run the command “bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug yes” \*\*  Unmount the SD card.</span></span>
<span data-ttu-id="c05e2-123">\*\* Ya debería poder conectar el depurador de la forma habitual.</span><span class="sxs-lookup"><span data-stu-id="c05e2-123">\*\*  You should now be able to connect the debugger as usual</span></span>
* <span data-ttu-id="c05e2-124">En ocasiones, se interrumpirá la PSSession al enviar comandos a dispositivos IoT.</span><span class="sxs-lookup"><span data-stu-id="c05e2-124">On occasion, PSSession will break when sending commands to IoT devices.</span></span>
* <span data-ttu-id="c05e2-125">RPi3 no empareja BT + BTLE con el Bluetooth incorporado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-125">RPi3 will not pair BT + BTLE with onboard Bluetooth.</span></span>
* <span data-ttu-id="c05e2-126">No se puede conectar a Internet a través de la conexión Wi-Fi con SoftAp de Up2.</span><span class="sxs-lookup"><span data-stu-id="c05e2-126">Unable to connect to internet through WIFI connection with SoftAp of Up2.</span></span>
* <span data-ttu-id="c05e2-127">La configuración de control de brillo no se conserva en IoT durante la cancelación.</span><span class="sxs-lookup"><span data-stu-id="c05e2-127">Brightness control settings do not persist on IoT during Override.</span></span>


## <a name="iot-core-general-known-issues-and-work-arounds"></a><span data-ttu-id="c05e2-128">Problemas generales conocidos de IoT Core y soluciones</span><span class="sxs-lookup"><span data-stu-id="c05e2-128">IoT Core general known issues and work arounds</span></span>

### <a name="for-raspberry-pi"></a><span data-ttu-id="c05e2-129">Para Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="c05e2-129">For Raspberry Pi</span></span>

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a><span data-ttu-id="c05e2-130">Resolución de pantalla de Raspberry Pi si se desconecta el monitor</span><span class="sxs-lookup"><span data-stu-id="c05e2-130">Raspberry Pi Display Resolution if monitor is disconnected</span></span> 
<span data-ttu-id="c05e2-131">Puede que Raspberry Pi no mantenga la resolución de pantalla si se desconecta el monitor.</span><span class="sxs-lookup"><span data-stu-id="c05e2-131">The Raspberry Pi may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="c05e2-132">El EDID del monitor se usa para establecer la resolución del sistema cuando hay uno conectado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-132">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="c05e2-133">Cuando se desconecta, el firmware de Raspberry Pi establece de forma predeterminada lo que está en config.txt en la raíz de la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="c05e2-133">When disconnected, the Raspberry Pi firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 

#### <a name="raspberry-pi-video-performance"></a><span data-ttu-id="c05e2-134">Rendimiento de vídeo de Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="c05e2-134">Raspberry Pi Video Performance</span></span> 
<span data-ttu-id="c05e2-135">El rendimiento de la reproducción de vídeo en la plataforma de Raspberry Pi no está optimizado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-135">Video playback performance on the Raspberry Pi platform is not optimized.</span></span><span data-ttu-id="c05e2-136">  Es posible que el rendimiento que muestren los elementos animados del usuario, incluidos los menús desplegables basados en XAML, no sea el óptimo.</span><span class="sxs-lookup"><span data-stu-id="c05e2-136">  Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span> 
 
#### <a name="raspberry-pi-camera-support"></a><span data-ttu-id="c05e2-137">Compatibilidad de Raspberry Pi con la cámara</span><span class="sxs-lookup"><span data-stu-id="c05e2-137">Raspberry Pi Camera Support</span></span> 
<span data-ttu-id="c05e2-138">La compatibilidad con los dispositivos periféricos de cámara es limitada.</span><span class="sxs-lookup"><span data-stu-id="c05e2-138">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="c05e2-139">El dispositivo PiCam conectado directamente al bus de la cámara incorporada no es compatible, ya que las limitaciones de la plataforma para admitir cámaras web USB modernas D3D generan flujos de datos muy exigentes en la controladora de host USB.</span><span class="sxs-lookup"><span data-stu-id="c05e2-139">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span><span data-ttu-id="c05e2-140">  Incluso cuando se usa con cámaras web con valores de resolución bajos, se requerirá un ajuste preciso adicional y una lógica de control especializada del USB.</span><span class="sxs-lookup"><span data-stu-id="c05e2-140">  Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span> 

#### <a name="raspberry-pi3-bluetooth-support"></a><span data-ttu-id="c05e2-141">Compatibilidad de Raspberry Pi3 con Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c05e2-141">Raspberry Pi3 Bluetooth support</span></span> 
<span data-ttu-id="c05e2-142">El controlador Bluetooth integrado de Raspberry Pi3 solo admite dispositivos con un ancho de banda bajo.</span><span class="sxs-lookup"><span data-stu-id="c05e2-142">The Raspberry Pi3 built-in Bluetooth driver only supports low bandwidth devices.</span></span> 

#### <a name="serial-port-usage-and-access-on-rpi2"></a><span data-ttu-id="c05e2-143">Uso y acceso de los puertos serie en RPi2</span><span class="sxs-lookup"><span data-stu-id="c05e2-143">Serial Port Usage and Access on RPi2</span></span> 
<span data-ttu-id="c05e2-144">Raspberry Pi 2 es compatible con el transporte en serie para la comunicación a través de UART PL011.</span><span class="sxs-lookup"><span data-stu-id="c05e2-144">Raspberry Pi 2 supports the serial transport for communication through the PL011 UART.</span></span><span data-ttu-id="c05e2-145">  Esto se establece de manera predeterminada en escenarios de depuración del kernel.</span><span class="sxs-lookup"><span data-stu-id="c05e2-145">  This is set by default in kernel debugging scenarios.</span></span><span data-ttu-id="c05e2-146">  Un controlador de dispositivo o de aplicación puede usar UART PL011 para enviar y recibir datos con el controlador de dispositivo PL011 si se desactiva el depurador mediante el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="c05e2-146">  An application or device driver can use the PL011 UART to send and receive data with the PL011 device driver turning off the debugger using the following command:</span></span>
```
bcedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a><span data-ttu-id="c05e2-147">Se han deshabilitado los puntos de interrupción de datos en Raspberry Pi2</span><span class="sxs-lookup"><span data-stu-id="c05e2-147">Data breakpoints have been disabled on the Raspberry Pi2</span></span>
<span data-ttu-id="c05e2-148">Por el momento no hay ninguna solución al respecto.</span><span class="sxs-lookup"><span data-stu-id="c05e2-148">No workaround at this time.</span></span>

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a><span data-ttu-id="c05e2-149">Deshabilitación de los adaptadores incorporados para Raspberry Pi3</span><span class="sxs-lookup"><span data-stu-id="c05e2-149">Disabling the onboard adapters for Raspberry Pi 3</span></span>
<span data-ttu-id="c05e2-150">Raspberry Pi3 tiene Bluetooth incorporado, que se debe deshabilitar para usar una llave diferente. Para deshabilitar el Bluetooth incorporado, abra una sesión de telnet o ssh, y ejecute lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c05e2-150">The Raspberry Pi 3 has onboard Bluetooth which must be disabled to use a different dongle to disable to onboard Bluetooth, open a telnet/ssh session and run:</span></span> 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

<span data-ttu-id="c05e2-151">Puede deshabilitar la Wi-Fi con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c05e2-151">You may disable WiFi with the following command:</span></span> 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragon-board"></a><span data-ttu-id="c05e2-152">Para DragonBoard</span><span class="sxs-lookup"><span data-stu-id="c05e2-152">For Dragon Board</span></span>

#### <a name="dragonboard-410c-shutdown"></a><span data-ttu-id="c05e2-153">Apagado de DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="c05e2-153">Dragonboard 410c Shutdown</span></span>
<span data-ttu-id="c05e2-154">En DragonBoard, la placa no se apagará con un comando de apagado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-154">On the DragonBoard, a shutdown command will not power off the board.</span></span> <span data-ttu-id="c05e2-155">El sistema se reiniciará.</span><span class="sxs-lookup"><span data-stu-id="c05e2-155">The system will restart.</span></span> <span data-ttu-id="c05e2-156">Para apagar la placa, desconecte la alimentación.</span><span class="sxs-lookup"><span data-stu-id="c05e2-156">Please power off the board by disconnecting the power.</span></span>

#### <a name="dragon-board-and-windbg"></a><span data-ttu-id="c05e2-157">DragonBoard y windbg</span><span class="sxs-lookup"><span data-stu-id="c05e2-157">Dragon Board and windbg</span></span>
<span data-ttu-id="c05e2-158">Los controladores GPIO/I2C/SPI/UART se deshabilitarán cuando se conecta a DragonBoard con windbg.</span><span class="sxs-lookup"><span data-stu-id="c05e2-158">The GPIO/I2C/SPI/UART drivers will be disabled when connecting to the DragonBoard with windbg.</span></span>

#### <a name="dragon-board-headset--microphone-jack"></a><span data-ttu-id="c05e2-159">Conector de auriculares y micrófono de DragonBoard</span><span class="sxs-lookup"><span data-stu-id="c05e2-159">Dragon Board headset & microphone jack</span></span>
<span data-ttu-id="c05e2-160">El BSP de Dragonboard tiene controladores para el conector de auriculares y de micrófono, pero no tiene estos conectores en la placa.</span><span class="sxs-lookup"><span data-stu-id="c05e2-160">The Dragonboard BSP has drivers for the headset jack and microphone jack, but it doesn't have either of these jacks on board.</span></span>  

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="c05e2-161">El SPI de DragonBoard se ejecuta a 4,8 Mhz</span><span class="sxs-lookup"><span data-stu-id="c05e2-161">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="c05e2-162">El SPI en DragonBoard omitirá la velocidad solicitada y siempre se ejecutará a 4,8 Mhz.</span><span class="sxs-lookup"><span data-stu-id="c05e2-162">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="c05e2-163">Modo de espera conectado de DragonBoard</span><span class="sxs-lookup"><span data-stu-id="c05e2-163">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="c05e2-164">El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="c05e2-164">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="c05e2-165">Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del Registro debe establecerse en "1":</span><span class="sxs-lookup"><span data-stu-id="c05e2-165">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”:</span></span>

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> <span data-ttu-id="c05e2-166">No todas las plataformas admiten el modo de espera conectado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-166">Not all platforms have support for Connected Standby.</span></span>  <span data-ttu-id="c05e2-167">Esto podría no funcionar en todas las plataformas.</span><span class="sxs-lookup"><span data-stu-id="c05e2-167">This may not work on all platforms.</span></span>    


### <a name="for-minnowboard"></a><span data-ttu-id="c05e2-168">Para MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="c05e2-168">For MinnowBoard</span></span>
#### <a name="minnowboard-max-boot-and-firmware-update"></a><span data-ttu-id="c05e2-169">Arranque de MinnowBoard Max y actualización de firmware</span><span class="sxs-lookup"><span data-stu-id="c05e2-169">Minnowboard Max Boot and Firmware Update</span></span> 
<span data-ttu-id="c05e2-170">MinnowBoard Max no arrancará a menos que la versión del firmware sea .092 o posterior.</span><span class="sxs-lookup"><span data-stu-id="c05e2-170">The MinnowBoard Max will not boot unless the firmware is version .092 or later.</span></span> <span data-ttu-id="c05e2-171">La versión mínima recomendada del firmware es "MinnowBoard Max 0.92 de 32 bits".</span><span class="sxs-lookup"><span data-stu-id="c05e2-171">The minimum recommended version of the firmware is “MinnowBoard MAX 0.92 32-Bit”.</span></span> <span data-ttu-id="c05e2-172">Las actualizaciones de firmware pueden descargarse desde [aquí](http://go.microsoft.com/fwlink/?LinkId=708613).</span><span class="sxs-lookup"><span data-stu-id="c05e2-172">Firmware updates can be downloaded from [here](http://go.microsoft.com/fwlink/?LinkId=708613).</span></span>

#### <a name="minnow-board-peripheral-support"></a><span data-ttu-id="c05e2-173">Compatibilidad con los periféricos de MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="c05e2-173">Minnow Board Peripheral Support</span></span>
<span data-ttu-id="c05e2-174">La imagen de Windows 10 IoT Core incluida en esta lista es compatible con los periféricos que se exponen en la placa MinnowBoard Max.</span><span class="sxs-lookup"><span data-stu-id="c05e2-174">The Windows 10 IoT Core image included in this drop supports the peripherals that are exposed on the MinnowBoard MAX board.</span></span> <span data-ttu-id="c05e2-175">Posteriormente, Intel&reg; proporcionará soporte técnico del conjunto completo de características de los procesadores Baytrail, incluidos los procesadores Intel Celeron&trade; J1900/N2930/N2807 e Intel Atom&trade; E38XX.</span><span class="sxs-lookup"><span data-stu-id="c05e2-175">Subsequently, Intel&reg; will provide support of the full feature set of the Baytrail processors including the Intel Celeron&trade; Processors J1900/N2930/N2807 and Intel Atom&trade; Processors E38XX.</span></span>


### <a name="for-all-platforms"></a><span data-ttu-id="c05e2-176">Para todas las plataformas</span><span class="sxs-lookup"><span data-stu-id="c05e2-176">For All Platforms</span></span> 

#### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="c05e2-177">El puntero del mouse desaparece durante la depuración</span><span class="sxs-lookup"><span data-stu-id="c05e2-177">Mouse Pointer disappears while debugging</span></span> 
<span data-ttu-id="c05e2-178">En algunos casos, el puntero del mouse no es visible después de implementar o depurar aplicaciones con Visual Studio. El puntero del mouse debe reaparecer si cambia el foco con el teclado (Tabulador).</span><span class="sxs-lookup"><span data-stu-id="c05e2-178">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab).</span></span>

#### <a name="accessing-public-documents"></a><span data-ttu-id="c05e2-179">Acceso a documentos públicos</span><span class="sxs-lookup"><span data-stu-id="c05e2-179">Accessing public documents</span></span>
<span data-ttu-id="c05e2-180">Se ha realizado un cambio en las API subyacentes para el acceso a archivos que requiere que una aplicación especifique el acceso a broadFileSystem con el fin de acceder al directorio de documentos públicos.</span><span class="sxs-lookup"><span data-stu-id="c05e2-180">A change was made to the underlying APIs for file access which requires an application specify broadFileSystem access in order to access the public documents directory.</span></span>

<span data-ttu-id="c05e2-181">El fragmento de archivo .XML debe tener este aspecto:</span><span class="sxs-lookup"><span data-stu-id="c05e2-181">The .XML file snippet should look like this:</span></span>
```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
  IgnorableNamespaces="uap mp rescap">
--snip--
  <Capabilities>
    <uap:Capability Name="removableStorage" />
    <uap:Capability Name="picturesLibrary" />
    <rescap:Capability Name="broadFileSystemAccess" />
 </Capabilities>

</Package>
```

#### <a name="server-applications-with-softap"></a><span data-ttu-id="c05e2-182">Aplicaciones de servidor con SoftAP</span><span class="sxs-lookup"><span data-stu-id="c05e2-182">Server Applications with SoftAP</span></span>
<span data-ttu-id="c05e2-183">Cuando se usa SoftAP, los clientes no podrán acceder al contenido que exponen las aplicaciones UAP.</span><span class="sxs-lookup"><span data-stu-id="c05e2-183">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span>  
<span data-ttu-id="c05e2-184">Para exponer las aplicaciones UAP a través de SoftAP, deben realizarse los cambios siguientes desde la consola en el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="c05e2-184">To expose UAP applications via SoftAP the following changes must be made from the console on the device:</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
```

<span data-ttu-id="c05e2-185">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c05e2-185">For example:</span></span>  
```
checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym
```
<span data-ttu-id="c05e2-186">Reiniciar</span><span class="sxs-lookup"><span data-stu-id="c05e2-186">Reboot</span></span> 


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="c05e2-187">Conflicto del controlador de sensor en FFU precompiladas</span><span class="sxs-lookup"><span data-stu-id="c05e2-187">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="c05e2-188">Hay un conflicto del controlador de sensor en las FFU proporcionadas.</span><span class="sxs-lookup"><span data-stu-id="c05e2-188">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="c05e2-189">El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio.</span><span class="sxs-lookup"><span data-stu-id="c05e2-189">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="c05e2-190">Las API de UWP que proporcionan acceso a estos controladores desde una aplicación suponen que solo hay uno instalado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-190">The UWP APIs for accessing these from an application assume just 1 is installed.</span></span> <span data-ttu-id="c05e2-191">Si va a desarrollar un controlador para un dispositivo adjuntado físicamente, el controlador remoto de las FFU que proporciona Microsoft entrará en conflicto.</span><span class="sxs-lookup"><span data-stu-id="c05e2-191">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>

<span data-ttu-id="c05e2-192">Solución: se puede quitar el controlador que causa el conflicto mediante la conexión al dispositivo a través de SSH o Powershell, y mediante el uso de la herramienta devcon.exe para quitar el controlador de sensor remoto (escriba "devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*").</span><span class="sxs-lookup"><span data-stu-id="c05e2-192">Resolution: The conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing “devcon.exe remove @”ROOT\REMOTESENSORDRIVER\*”.</span></span> <span data-ttu-id="c05e2-193">El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original.</span><span class="sxs-lookup"><span data-stu-id="c05e2-193">The remote sensor driver does not affect OEM created FFUs.</span></span>


#### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="c05e2-194">Nombre de usuario y contraseña predeterminados del administrador</span><span class="sxs-lookup"><span data-stu-id="c05e2-194">Default Administrator User Name and Password</span></span>
<span data-ttu-id="c05e2-195">El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-195">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="c05e2-196">Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña.</span><span class="sxs-lookup"><span data-stu-id="c05e2-196">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span>

#### <a name="volume-controls"></a><span data-ttu-id="c05e2-197">Controles de volumen</span><span class="sxs-lookup"><span data-stu-id="c05e2-197">Volume Controls</span></span>
<span data-ttu-id="c05e2-198">Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-198">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

#### <a name="usb-keyboards"></a><span data-ttu-id="c05e2-199">Teclados USB</span><span class="sxs-lookup"><span data-stu-id="c05e2-199">USB Keyboards</span></span>  
<span data-ttu-id="c05e2-200">Es posible que algún teclado y mouse USB no funcionen en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-200">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="c05e2-201">Use otro teclado o mouse.</span><span class="sxs-lookup"><span data-stu-id="c05e2-201">Use a different keyboard or mouse.</span></span> <span data-ttu-id="c05e2-202">Encontrará una lista de dispositivos periféricos validados en [esta documentación](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/hardwarecompatlist).</span><span class="sxs-lookup"><span data-stu-id="c05e2-202">A list of validated peripheral devices can be found in the [documentation here](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/hardwarecompatlist).</span></span>


#### <a name="screen-orientation"></a><span data-ttu-id="c05e2-203">Orientación de la pantalla</span><span class="sxs-lookup"><span data-stu-id="c05e2-203">Screen Orientation</span></span>
<span data-ttu-id="c05e2-204">El establecimiento de la orientación en "Vertical" puede que no se respete en una aplicación universal.</span><span class="sxs-lookup"><span data-stu-id="c05e2-204">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

#### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="c05e2-205">Adaptadores de referencia con plantillas de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="c05e2-205">Referencing Adapters with AllJoyn Templates</span></span>
<span data-ttu-id="c05e2-206">El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.</span><span class="sxs-lookup"><span data-stu-id="c05e2-206">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="c05e2-207">Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, luego, vuelva a cargar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c05e2-207">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>

#### <a name="wifi-direct-limitations-on-iotcore"></a><span data-ttu-id="c05e2-208">Limitaciones de Wi-Fi Direct en IoTCore</span><span class="sxs-lookup"><span data-stu-id="c05e2-208">WiFi Direct limitations on IoTCore</span></span>
* <span data-ttu-id="c05e2-209">El dispositivo IoTCore debe ser el dispositivo que se conecta. No funcionará como dispositivo de publicidad con otro dispositivo que inicie la conexión.</span><span class="sxs-lookup"><span data-stu-id="c05e2-209">The IoTCore device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
* <span data-ttu-id="c05e2-210">Se debe usar el emparejamiento avanzado.</span><span class="sxs-lookup"><span data-stu-id="c05e2-210">Advanced pairing must be used.</span></span>  <span data-ttu-id="c05e2-211">La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de la conexión.</span><span class="sxs-lookup"><span data-stu-id="c05e2-211">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
* <span data-ttu-id="c05e2-212">No todos los adaptadores inalámbricos son compatibles con Wi-Fi Direct.</span><span class="sxs-lookup"><span data-stu-id="c05e2-212">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="c05e2-213">Hemos probado y validado el funcionamiento del "adaptador de red Realtek RTL8188EU Wireless Lan 802.11n USB 2.0", pero puede que otros adaptadores no sean compatibles.</span><span class="sxs-lookup"><span data-stu-id="c05e2-213">We have tested and validated that the “Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter” works, but other adapters may not be supported.</span></span> 


#### <a name="non-default-drive-mode"></a><span data-ttu-id="c05e2-214">Modo de unidad no predeterminado</span><span class="sxs-lookup"><span data-stu-id="c05e2-214">Non-default drive mode</span></span>
<span data-ttu-id="c05e2-215">En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO.</span><span class="sxs-lookup"><span data-stu-id="c05e2-215">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="c05e2-216">Solución alternativa: establezca el modo de la unidad una vez al comienzo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c05e2-216">WORKAROUND: Set drive mode once at the beginning of the application.</span></span>

#### <a name="application-already-running"></a><span data-ttu-id="c05e2-217">Aplicación en ejecución</span><span class="sxs-lookup"><span data-stu-id="c05e2-217">Application already running</span></span>
<span data-ttu-id="c05e2-218">La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c05e2-218">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="c05e2-219">Solución alternativa: cambie la aplicación de inicio predeterminada a otra aplicación distinta de la que quiere implementar.</span><span class="sxs-lookup"><span data-stu-id="c05e2-219">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a><span data-ttu-id="c05e2-220">Puede que se bloquee la línea de código BackgroundMediaPlayer.MessageReceivedFromForeground</span><span class="sxs-lookup"><span data-stu-id="c05e2-220">BackgroundMediaPlayer.MessageReceivedFromForeground may crash</span></span>
<span data-ttu-id="c05e2-221">La línea de código siguiente podría bloquearse: "BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;".</span><span class="sxs-lookup"><span data-stu-id="c05e2-221">The following line of code may crash: “BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;”.</span></span> <span data-ttu-id="c05e2-222">Para evitar el bloqueo, agregue este código para que se ejecute primero: "var player = BackgroundMediaPlayer.Current;".</span><span class="sxs-lookup"><span data-stu-id="c05e2-222">To prevent the crash, add this code so that it is executed first “var player = BackgroundMediaPlayer.Current;”</span></span> 

#### <a name="azure-active-directory-authentication-support"></a><span data-ttu-id="c05e2-223">Compatibilidad con la autenticación de Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c05e2-223">Azure Active Directory Authentication Support</span></span>
<span data-ttu-id="c05e2-224">La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c05e2-224">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

#### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="c05e2-225">Administración del shell de los bloqueos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c05e2-225">Shell Management of Application Crashes</span></span>
<span data-ttu-id="c05e2-226">La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c05e2-226">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="c05e2-227">Si los bloqueos continúan en las aplicaciones reiniciadas, el shell empleará un __failfast, es decir, un proceso crítico del sistema que provoca una comprobación de errores y un reinicio en un intento de recuperación.</span><span class="sxs-lookup"><span data-stu-id="c05e2-227">If the restarted applications continue to crash, the shell will employ a __failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="c05e2-228">Se usan una lógica y un control comparables para las tareas en segundo plano y las aplicaciones de primer plano en una configuración con cabezal.</span><span class="sxs-lookup"><span data-stu-id="c05e2-228">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="c05e2-229">A continuación se muestra la lógica de reintento y el control de bloqueo:</span><span class="sxs-lookup"><span data-stu-id="c05e2-229">Crash handing and retry logic is captured below:</span></span>

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

<span data-ttu-id="c05e2-230">Cuando se detecta un bloqueo de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="c05e2-230">When app crash is detected:</span></span> 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

<span data-ttu-id="c05e2-231">Espere el retraso y reinicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c05e2-231">Wait for delay and relaunch app</span></span> 


#### <a name="time-synchronization"></a><span data-ttu-id="c05e2-232">Sincronización de la hora</span><span class="sxs-lookup"><span data-stu-id="c05e2-232">Time Synchronization</span></span>  
<span data-ttu-id="c05e2-233">Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales.</span><span class="sxs-lookup"><span data-stu-id="c05e2-233">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 

1) <span data-ttu-id="c05e2-234">Desde una línea de comandos en el dispositivo (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="c05e2-234">From a command line on the device (eg.</span></span> <span data-ttu-id="c05e2-235">SSH, Powershell) w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span><span class="sxs-lookup"><span data-stu-id="c05e2-235">SSH, Powershell) w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."</span></span> 

2) <span data-ttu-id="c05e2-236">También puede realizar estas adiciones en el Registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado, incluido como parte del proceso de creación de imagen si es necesario.</span><span class="sxs-lookup"><span data-stu-id="c05e2-236">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> <span data-ttu-id="c05e2-237">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="c05e2-237">For more details, see:</span></span> 

* <span data-ttu-id="c05e2-238">[Adición de un archivo y configuración del Registro en una imagen](https://msdn.microsoft.com/en-us/library/windows/hardware/mt670641(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="c05e2-238">[Adding a file and registry setting to an image](https://msdn.microsoft.com/en-us/library/windows/hardware/mt670641(v=vs.85).aspx)</span></span>


### <a name="starting-the-ftp-server"></a><span data-ttu-id="c05e2-239">Inicio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c05e2-239">Starting the FTP Server</span></span> 
<span data-ttu-id="c05e2-240">El servidor FTP ya no se ejecuta de manera predeterminada al inicio.</span><span class="sxs-lookup"><span data-stu-id="c05e2-240">The FTP Server no longer runs by default at start-up</span></span> 

<span data-ttu-id="c05e2-241">Para ejecutarlo una vez: Inicie sesión con SSH o PS, y ejecute este comando para iniciar el FTP:</span><span class="sxs-lookup"><span data-stu-id="c05e2-241">To run once: Login with SSH\PS and run this command to start FTP:</span></span>  
```
start ftpd.exe 
```

<span data-ttu-id="c05e2-242">Para ejecutarlo en todos los arranques, los usuarios deben crear una tarea de programador: Inicie sesión con SSH o PS, y cree una tarea de programador:</span><span class="sxs-lookup"><span data-stu-id="c05e2-242">To run on every boot Users should create a scheduler task: Login with SSH\PS and create a scheduler task:</span></span> 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```
