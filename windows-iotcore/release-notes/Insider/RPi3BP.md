---
title: Notas de la versión de Raspberry Pi 3B+
ms.date: 05/16/2018
ms.topic: article
description: Lee y obtén información sobre las novedades de la compilación para Raspberry Pi 3B+.
keywords: windows iot, Windows Insider, notas de la versión, Raspberry Pi 3B+
ms.openlocfilehash: d321676758f7ff438540720098e6a6ecb1ba457f
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "75721020"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="7f964-104">Notas de la versión de Raspberry Pi 3B+</span><span class="sxs-lookup"><span data-stu-id="7f964-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="7f964-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="7f964-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="7f964-106">Todos los derechos reservados.</span><span class="sxs-lookup"><span data-stu-id="7f964-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="7f964-107">Esta versión para Raspberry Pi 3B+ es una versión preliminar técnica no admitida.</span><span class="sxs-lookup"><span data-stu-id="7f964-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="7f964-108">Se ha completado la habilitación y la validación limitadas.</span><span class="sxs-lookup"><span data-stu-id="7f964-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="7f964-109">La versión actual se puede encontrar [aquí](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="7f964-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="7f964-110">Para obtener una mejor experiencia de evaluación y para cualquier producto comercial, use Raspberry Pi 3B u otros dispositivos con SoC de Intel, Qualcomm o NXP admitidos.</span><span class="sxs-lookup"><span data-stu-id="7f964-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="7f964-111">Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B+, vea nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="7f964-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="7f964-112">Novedades de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="7f964-112">What's new in this build:</span></span> 
* <span data-ttu-id="7f964-113">Correcciones de errores generales</span><span class="sxs-lookup"><span data-stu-id="7f964-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="7f964-114">Problemas conocidos de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="7f964-114">Known issues in this build:</span></span>
* <span data-ttu-id="7f964-115">Esta imagen solo está pensada para RPi3B+ y no arrancará en RPi2.</span><span class="sxs-lookup"><span data-stu-id="7f964-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="7f964-116">La implementación del controlador F5 de Visual Studio no funciona en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7f964-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="7f964-117">La incorporación de Wi-Fi y Bluetooth no funcionan en RPi3B+.</span><span class="sxs-lookup"><span data-stu-id="7f964-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="7f964-118">El controlador de pantalla táctil Ft5406 está deshabilitado en RPi3B+.</span><span class="sxs-lookup"><span data-stu-id="7f964-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="7f964-119">El LED de actividad de tarjeta SD está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="7f964-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="7f964-120">La resolución de pantalla si se desconecta el monitor</span><span class="sxs-lookup"><span data-stu-id="7f964-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="7f964-121">Puede que Raspberry Pi 3B+ no mantenga la resolución de pantalla si se desconecta el monitor.</span><span class="sxs-lookup"><span data-stu-id="7f964-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="7f964-122">El EDID del monitor se usa para establecer la resolución del sistema cuando hay uno conectado.</span><span class="sxs-lookup"><span data-stu-id="7f964-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="7f964-123">Cuando se desconecta, el firmware establece de forma predeterminada lo que está en config.txt en la raíz de la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="7f964-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="7f964-124">Rendimiento de vídeo</span><span class="sxs-lookup"><span data-stu-id="7f964-124">Video performance</span></span>
<span data-ttu-id="7f964-125">El rendimiento de la reproducción de vídeo en la plataforma no está optimizado.</span><span class="sxs-lookup"><span data-stu-id="7f964-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="7f964-126">Es posible que el rendimiento que muestren los elementos animados del usuario, incluidos los menús desplegables basados en XAML, no sea el óptimo.</span><span class="sxs-lookup"><span data-stu-id="7f964-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="7f964-127">Compatibilidad con cámara</span><span class="sxs-lookup"><span data-stu-id="7f964-127">Camera support</span></span>
<span data-ttu-id="7f964-128">La compatibilidad con los dispositivos periféricos de cámara es limitada.</span><span class="sxs-lookup"><span data-stu-id="7f964-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="7f964-129">El dispositivo PiCam conectado directamente al bus de la cámara incorporada no es compatible, ya que las limitaciones de la plataforma para admitir cámaras web USB modernas D3D generan flujos de datos muy exigentes en la controladora de host USB.</span><span class="sxs-lookup"><span data-stu-id="7f964-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="7f964-130">Incluso cuando se usa con cámaras web con valores de resolución bajos, se requerirá un ajuste preciso adicional y una lógica de control especializada del USB.</span><span class="sxs-lookup"><span data-stu-id="7f964-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="7f964-131">El puntero del mouse desaparece durante la depuración</span><span class="sxs-lookup"><span data-stu-id="7f964-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="7f964-132">En algunos casos, el puntero del mouse no es visible después de implementar o depurar aplicaciones con Visual Studio. El puntero del mouse debe reaparecer si cambias el foco con el teclado (TAB) (8038595).</span><span class="sxs-lookup"><span data-stu-id="7f964-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="7f964-133">Aplicaciones de servidor con SoftAP</span><span class="sxs-lookup"><span data-stu-id="7f964-133">Server applications with SoftAP</span></span>
<span data-ttu-id="7f964-134">Cuando se usa SoftAP, los clientes no podrán acceder al contenido que exponen las aplicaciones UAP.</span><span class="sxs-lookup"><span data-stu-id="7f964-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="7f964-135">Para exponer las aplicaciones UAP a través de SoftAP, deben realizarse los cambios siguientes desde la consola en el dispositivo (8111807):</span><span class="sxs-lookup"><span data-stu-id="7f964-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="7f964-136">Reinicia.</span><span class="sxs-lookup"><span data-stu-id="7f964-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="7f964-137">Conflicto del controlador de sensor en FFU precompiladas</span><span class="sxs-lookup"><span data-stu-id="7f964-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="7f964-138">Hay un conflicto del controlador de sensor en las FFU proporcionadas.</span><span class="sxs-lookup"><span data-stu-id="7f964-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="7f964-139">El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio.</span><span class="sxs-lookup"><span data-stu-id="7f964-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="7f964-140">Las API de UWP que proporcionan acceso a estos controladores desde una aplicación suponen que solo hay uno instalado.</span><span class="sxs-lookup"><span data-stu-id="7f964-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="7f964-141">Si va a desarrollar un controlador para un dispositivo adjuntado físicamente, el controlador remoto de las FFU que proporciona Microsoft entrará en conflicto.</span><span class="sxs-lookup"><span data-stu-id="7f964-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="7f964-142">Para resolver esto, se puede quitar el controlador que causa el conflicto mediante la conexión al dispositivo a través de SSH o PowerShell, y mediante el uso de la herramienta devcon.exe para quitar el controlador de sensor remoto escribiendo:</span><span class="sxs-lookup"><span data-stu-id="7f964-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="7f964-143">El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original.</span><span class="sxs-lookup"><span data-stu-id="7f964-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="7f964-144">Nombre de usuario y contraseña predeterminados del administrador</span><span class="sxs-lookup"><span data-stu-id="7f964-144">Default administrator user name and password</span></span>
<span data-ttu-id="7f964-145">El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7f964-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="7f964-146">Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña.</span><span class="sxs-lookup"><span data-stu-id="7f964-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="7f964-147">Controles de volumen</span><span class="sxs-lookup"><span data-stu-id="7f964-147">Volume controls</span></span>
<span data-ttu-id="7f964-148">Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7f964-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="7f964-149">Teclados USB</span><span class="sxs-lookup"><span data-stu-id="7f964-149">USB keyboards</span></span>
<span data-ttu-id="7f964-150">Es posible que algún teclado y mouse USB no funcionen en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7f964-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="7f964-151">Use otro teclado o mouse.</span><span class="sxs-lookup"><span data-stu-id="7f964-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="7f964-152">Encontrarás una lista de dispositivos periféricos validados en esta [documentación](https://go.microsoft.com/fwlink/?LinkId=619428).</span><span class="sxs-lookup"><span data-stu-id="7f964-152">A list of validated peripheral devices can be found in the documentation [here](https://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="7f964-153">Orientación de la pantalla</span><span class="sxs-lookup"><span data-stu-id="7f964-153">Screen orientation</span></span>
<span data-ttu-id="7f964-154">El establecimiento de la orientación en "Vertical" puede que no se respete en una aplicación universal.</span><span class="sxs-lookup"><span data-stu-id="7f964-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="7f964-155">Referencia a adaptadores con plantillas de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="7f964-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="7f964-156">El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.</span><span class="sxs-lookup"><span data-stu-id="7f964-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="7f964-157">Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, luego, vuelva a cargar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="7f964-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="7f964-158">Limitaciones de Wi-Fi Direct en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7f964-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="7f964-159">El dispositivo con Windows 10 IoT Core debe ser el dispositivo que se conecta. No funcionará como dispositivo de publicidad con otro dispositivo que inicie la conexión.</span><span class="sxs-lookup"><span data-stu-id="7f964-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="7f964-160">Se debe usar el emparejamiento avanzado.</span><span class="sxs-lookup"><span data-stu-id="7f964-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="7f964-161">La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de la conexión.</span><span class="sxs-lookup"><span data-stu-id="7f964-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="7f964-162">No todos los adaptadores inalámbricos son compatibles con Wi-Fi Direct.</span><span class="sxs-lookup"><span data-stu-id="7f964-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="7f964-163">Hemos probado y validado el funcionamiento del "adaptador de red Realtek RTL8188EU Wireless Lan 802.11n USB 2.0", pero puede que otros adaptadores no sean compatibles.</span><span class="sxs-lookup"><span data-stu-id="7f964-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="7f964-164">Modo de unidad no predeterminado (3890679)</span><span class="sxs-lookup"><span data-stu-id="7f964-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="7f964-165">En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO.</span><span class="sxs-lookup"><span data-stu-id="7f964-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="7f964-166">Para solucionar este problema, establece el modo de la unidad una vez al comienzo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7f964-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="7f964-167">Aplicación en ejecución (1244550)</span><span class="sxs-lookup"><span data-stu-id="7f964-167">Application already running (1244550)</span></span> 
<span data-ttu-id="7f964-168">La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7f964-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="7f964-169">Solución alternativa: cambie la aplicación de inicio predeterminada a otra aplicación distinta de la que quiere implementar.</span><span class="sxs-lookup"><span data-stu-id="7f964-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="7f964-170">Puede que se bloquee la línea de código BackgroundMediaPlayer.MessageReceivedFromForeground (2199869)</span><span class="sxs-lookup"><span data-stu-id="7f964-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="7f964-171">La línea de código siguiente podría bloquearse:</span><span class="sxs-lookup"><span data-stu-id="7f964-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="7f964-172">Para evitar el bloqueo, agrega este código para que se ejecute primero:</span><span class="sxs-lookup"><span data-stu-id="7f964-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="7f964-173">Compatibilidad con la autenticación de Azure Active Directory (4266261)</span><span class="sxs-lookup"><span data-stu-id="7f964-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="7f964-174">La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7f964-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="7f964-175">Administración del shell de los bloqueos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="7f964-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="7f964-176">La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="7f964-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="7f964-177">Si los bloqueos continúan en las aplicaciones reiniciadas, el shell empleará un failfast, es decir, un proceso crítico del sistema que provoca una comprobación de errores y un reinicio en un intento de recuperación.</span><span class="sxs-lookup"><span data-stu-id="7f964-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="7f964-178">Se usan una lógica y un control comparables para las tareas en segundo plano y las aplicaciones de primer plano en una configuración con cabezal.</span><span class="sxs-lookup"><span data-stu-id="7f964-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="7f964-179">A continuación se muestra la lógica de reintento y el control de bloqueo:</span><span class="sxs-lookup"><span data-stu-id="7f964-179">Crash handling and retry logic is captured below:</span></span>

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
  Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
  Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
  Dword:"MaxFailureCount". Default is 10 
  DWord:"FallbackExponentNumerator", default is 31. 
  Dword:"FallbackExponentDenominator", default is 20 
  
  
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
When app crash is detected: 
    if time_since_last_crash > failureresetinterval then crashes_seen = 1 
    else ++crashes_seen; 
  
if crashes_seen > MaxFailureCount then __failfast; 
  
else  
  
delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

<span data-ttu-id="7f964-180">Espera el retraso y reinicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7f964-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="7f964-181">El SPI de DragonBoard se ejecuta a 4,8 Mhz</span><span class="sxs-lookup"><span data-stu-id="7f964-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="7f964-182">El SPI en DragonBoard omitirá la velocidad solicitada y siempre se ejecutará a 4,8 Mhz.</span><span class="sxs-lookup"><span data-stu-id="7f964-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="7f964-183">Modo de espera conectado de DragonBoard</span><span class="sxs-lookup"><span data-stu-id="7f964-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="7f964-184">El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="7f964-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="7f964-185">Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del Registro debe establecerse en "1".</span><span class="sxs-lookup"><span data-stu-id="7f964-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="7f964-186">Sincronización de la hora</span><span class="sxs-lookup"><span data-stu-id="7f964-186">Time synchronization</span></span>
<span data-ttu-id="7f964-187">Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales.</span><span class="sxs-lookup"><span data-stu-id="7f964-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="7f964-188">Desde una línea de comandos en el dispositivo (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="7f964-188">From a command line on the device (eg.</span></span> <span data-ttu-id="7f964-189">SSH, PowerShell).</span><span class="sxs-lookup"><span data-stu-id="7f964-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="7f964-190">También puede realizar estas adiciones en el Registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado, incluido como parte del proceso de creación de imagen si es necesario.</span><span class="sxs-lookup"><span data-stu-id="7f964-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="7f964-191">Inicio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="7f964-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="7f964-192">Para ejecutar una vez, inicia sesión con SSH\PS, y ejecuta este comando para iniciar el FTP:</span><span class="sxs-lookup"><span data-stu-id="7f964-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="7f964-193">Para ejecutar en cada arranque, los usuarios deben crear una tarea de programador: iniciar sesión con SSH\PS y crear una tarea de programador:</span><span class="sxs-lookup"><span data-stu-id="7f964-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="7f964-194">Requisitos de tamaño de partición para actualización</span><span class="sxs-lookup"><span data-stu-id="7f964-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="7f964-195">Asegúrate de que la partición de datos mantenga suficiente espacio para la funcionalidad de actualización.</span><span class="sxs-lookup"><span data-stu-id="7f964-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="7f964-196">  Se recomienda 1 GB libres para la funcionalidad de actualización completa.</span><span class="sxs-lookup"><span data-stu-id="7f964-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="7f964-197"> Si la partición de datos no tiene espacio suficiente, se producirá un error en las actualizaciones durante la fase de instalación.</span><span class="sxs-lookup"><span data-stu-id="7f964-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="7f964-198">Generación de registros de PowerShell en IoT Core</span><span class="sxs-lookup"><span data-stu-id="7f964-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="7f964-199">PowerShell en IoT Core puede generar archivos de registro de forma predeterminada, los que ocupan espacio en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="7f964-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="7f964-200">Aunque los tamaños de los archivos de registro están limitados, pueden ocupar espacio, lo que puede dar lugar a una situación de poco espacio en disco que, entre otras cosas, puede producir errores en las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="7f964-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="7f964-201">Los archivos de registro de eventos .evtx tienen un tamaño máximo predefinido de 20 MB cada uno.</span><span class="sxs-lookup"><span data-stu-id="7f964-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="7f964-202">Puedes limitar los archivos de forma individual para que tengan un tamaño máximo diferente mediante el registro.</span><span class="sxs-lookup"><span data-stu-id="7f964-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="7f964-203">Por ejemplo, para mantener security.evtx en un tamaño máximo de 10 MB:</span><span class="sxs-lookup"><span data-stu-id="7f964-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="7f964-204">Limitación de Schtasks</span><span class="sxs-lookup"><span data-stu-id="7f964-204">Schtasks limitation</span></span>  
<span data-ttu-id="7f964-205">Schtasks no admite el uso del modificador /xml.</span><span class="sxs-lookup"><span data-stu-id="7f964-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="7f964-206">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7f964-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="7f964-207">Se producirá un error en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="7f964-207">This will fail on IoT Core.</span></span> <span data-ttu-id="7f964-208">Al ejecutar el comando, se generará el error: ERROR: No se encontró el procedimiento especificado.</span><span class="sxs-lookup"><span data-stu-id="7f964-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
