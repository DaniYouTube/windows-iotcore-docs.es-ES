---
title: Notas de la versión de Raspberry PI 3B +
ms.date: 05/16/2018
ms.topic: article
description: Lea y obtenga información sobre lo que hay en la compilación de Raspberry PI 3B +.
keywords: Windows IOT, Windows Insider, notas de la versión, Raspberry PI 3B +
ms.openlocfilehash: e0cf0afb98440034d8384e5d44ce98bb14a0fe71
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918746"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="2c319-104">Notas de la versión de Raspberry PI 3B +</span><span class="sxs-lookup"><span data-stu-id="2c319-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="2c319-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="2c319-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="2c319-106">Todos los derechos reservados.</span><span class="sxs-lookup"><span data-stu-id="2c319-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="2c319-107">Esta versión para Raspberry Pi 3B+ es una versión preliminar técnica no admitida.</span><span class="sxs-lookup"><span data-stu-id="2c319-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="2c319-108">Se ha completado la habilitación y la validación limitadas.</span><span class="sxs-lookup"><span data-stu-id="2c319-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="2c319-109">La versión actual se puede encontrar [aquí](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="2c319-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="2c319-110">Para obtener una mejor experiencia de evaluación y para cualquier producto comercial, use Raspberry Pi 3B u otros dispositivos con SoC de Intel, Qualcomm o NXP admitidos.</span><span class="sxs-lookup"><span data-stu-id="2c319-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="2c319-111">Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B+, vea nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="2c319-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="2c319-112">Novedades de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="2c319-112">What's new in this build:</span></span> 
* <span data-ttu-id="2c319-113">Correcciones de errores generales</span><span class="sxs-lookup"><span data-stu-id="2c319-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="2c319-114">Problemas conocidos de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="2c319-114">Known issues in this build:</span></span>
* <span data-ttu-id="2c319-115">Esta imagen solo está pensada para RPi3B + y no arrancará en RPi2.</span><span class="sxs-lookup"><span data-stu-id="2c319-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="2c319-116">La implementación del controlador F5 de Visual Studio no funciona en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2c319-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="2c319-117">La incorporación de Wi-Fi y Bluetooth no funcionan en RPI3B +.</span><span class="sxs-lookup"><span data-stu-id="2c319-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="2c319-118">El controlador de pantalla táctil de Ft5406 está deshabilitado en RPi3B +.</span><span class="sxs-lookup"><span data-stu-id="2c319-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="2c319-119">El LED de actividad de tarjeta SD está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="2c319-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="2c319-120">La resolución de pantalla está desconectada</span><span class="sxs-lookup"><span data-stu-id="2c319-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="2c319-121">Es posible que Raspberry PI 3B + no mantenga la resolución de pantalla si el monitor está desconectado.</span><span class="sxs-lookup"><span data-stu-id="2c319-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="2c319-122">El EDID del monitor se usa para establecer la resolución del sistema cuando hay uno conectado.</span><span class="sxs-lookup"><span data-stu-id="2c319-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="2c319-123">Cuando está desconectada, el firmware tiene como valor predeterminado lo que se encuentra en el archivo config. txt en la raíz de la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="2c319-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="2c319-124">Rendimiento de vídeo</span><span class="sxs-lookup"><span data-stu-id="2c319-124">Video performance</span></span>
<span data-ttu-id="2c319-125">El rendimiento de reproducción de vídeo en la plataforma no está optimizado.</span><span class="sxs-lookup"><span data-stu-id="2c319-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="2c319-126">Es posible que el rendimiento que muestren los elementos animados del usuario, incluidos los menús desplegables basados en XAML, no sea el óptimo.</span><span class="sxs-lookup"><span data-stu-id="2c319-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="2c319-127">Compatibilidad con cámaras</span><span class="sxs-lookup"><span data-stu-id="2c319-127">Camera support</span></span>
<span data-ttu-id="2c319-128">La compatibilidad con los dispositivos periféricos de cámara es limitada.</span><span class="sxs-lookup"><span data-stu-id="2c319-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="2c319-129">El dispositivo PiCam conectado directamente al bus de la cámara incorporada no es compatible, ya que las limitaciones de la plataforma para admitir cámaras web USB modernas D3D generan flujos de datos muy exigentes en la controladora de host USB.</span><span class="sxs-lookup"><span data-stu-id="2c319-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="2c319-130">Incluso cuando se usa con cámaras web con valores de resolución bajos, se requerirá un ajuste preciso adicional y una lógica de control especializada del USB.</span><span class="sxs-lookup"><span data-stu-id="2c319-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="2c319-131">El puntero del mouse desaparece durante la depuración</span><span class="sxs-lookup"><span data-stu-id="2c319-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="2c319-132">En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe volver a aparecer si cambia el foco con el teclado (tabulación) (8038595).</span><span class="sxs-lookup"><span data-stu-id="2c319-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="2c319-133">Aplicaciones de servidor con SoftAP</span><span class="sxs-lookup"><span data-stu-id="2c319-133">Server applications with SoftAP</span></span>
<span data-ttu-id="2c319-134">Cuando se usa SoftAP, los clientes no podrán acceder al contenido que exponen las aplicaciones UAP.</span><span class="sxs-lookup"><span data-stu-id="2c319-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="2c319-135">Para exponer las aplicaciones UAP a través de SoftAP, se deben realizar los siguientes cambios desde la consola de en el dispositivo (8111807):</span><span class="sxs-lookup"><span data-stu-id="2c319-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="2c319-136">Reinicio.</span><span class="sxs-lookup"><span data-stu-id="2c319-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="2c319-137">Conflicto del controlador de sensor en FFU precompiladas</span><span class="sxs-lookup"><span data-stu-id="2c319-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="2c319-138">Hay un conflicto del controlador de sensor en las FFU proporcionadas.</span><span class="sxs-lookup"><span data-stu-id="2c319-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="2c319-139">El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio.</span><span class="sxs-lookup"><span data-stu-id="2c319-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="2c319-140">Las API de UWP para acceder a ellas desde una aplicación suponen que solo hay una instalada.</span><span class="sxs-lookup"><span data-stu-id="2c319-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="2c319-141">Si va a desarrollar un controlador para un dispositivo adjuntado físicamente, el controlador remoto de las FFU que proporciona Microsoft entrará en conflicto.</span><span class="sxs-lookup"><span data-stu-id="2c319-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="2c319-142">Para solucionar este problema, se puede quitar el controlador conflictivo conectándose al dispositivo a través de SSH o PowerShell y usando la herramienta DEVCON. exe para quitar el controlador del sensor remoto; para ello, escriba:</span><span class="sxs-lookup"><span data-stu-id="2c319-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="2c319-143">El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original.</span><span class="sxs-lookup"><span data-stu-id="2c319-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="2c319-144">Nombre de usuario y contraseña de administrador predeterminados</span><span class="sxs-lookup"><span data-stu-id="2c319-144">Default administrator user name and password</span></span>
<span data-ttu-id="2c319-145">El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2c319-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="2c319-146">Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña.</span><span class="sxs-lookup"><span data-stu-id="2c319-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="2c319-147">Controles de volumen</span><span class="sxs-lookup"><span data-stu-id="2c319-147">Volume controls</span></span>
<span data-ttu-id="2c319-148">Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2c319-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="2c319-149">Teclados USB</span><span class="sxs-lookup"><span data-stu-id="2c319-149">USB keyboards</span></span>
<span data-ttu-id="2c319-150">Es posible que algún teclado y mouse USB no funcionen en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2c319-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="2c319-151">Use otro teclado o mouse.</span><span class="sxs-lookup"><span data-stu-id="2c319-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="2c319-152">Puede encontrar una lista de dispositivos periféricos validados en la documentación [aquí](http://go.microsoft.com/fwlink/?LinkId=619428).</span><span class="sxs-lookup"><span data-stu-id="2c319-152">A list of validated peripheral devices can be found in the documentation [here](http://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="2c319-153">Orientación de la pantalla</span><span class="sxs-lookup"><span data-stu-id="2c319-153">Screen orientation</span></span>
<span data-ttu-id="2c319-154">El establecimiento de la orientación en "Vertical" puede que no se respete en una aplicación universal.</span><span class="sxs-lookup"><span data-stu-id="2c319-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="2c319-155">Referencia a adaptadores con plantillas AllJoyn</span><span class="sxs-lookup"><span data-stu-id="2c319-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="2c319-156">El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.</span><span class="sxs-lookup"><span data-stu-id="2c319-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="2c319-157">Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, luego, vuelva a cargar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="2c319-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="2c319-158">Limitaciones de WiFi Direct en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="2c319-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="2c319-159">El dispositivo de Windows 10 IoT Core debe ser el dispositivo que se conecta: no funcionará como el dispositivo de publicidad con otro dispositivo que inicie la conexión.</span><span class="sxs-lookup"><span data-stu-id="2c319-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="2c319-160">Se debe usar el emparejamiento avanzado.</span><span class="sxs-lookup"><span data-stu-id="2c319-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="2c319-161">La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de la conexión.</span><span class="sxs-lookup"><span data-stu-id="2c319-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="2c319-162">No todos los adaptadores inalámbricos son compatibles con Wi-Fi Direct.</span><span class="sxs-lookup"><span data-stu-id="2c319-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="2c319-163">Hemos probado y validado el funcionamiento del adaptador de red "Realtek RTL8188EU Wireless LAN 802.11 n USB 2,0", pero es posible que no se admitan otros adaptadores.</span><span class="sxs-lookup"><span data-stu-id="2c319-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="2c319-164">Modo de unidad no predeterminada (3890679)</span><span class="sxs-lookup"><span data-stu-id="2c319-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="2c319-165">En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO.</span><span class="sxs-lookup"><span data-stu-id="2c319-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="2c319-166">Para solucionar este problema, establezca el modo de unidad una vez al principio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2c319-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="2c319-167">La aplicación ya se está ejecutando (1244550)</span><span class="sxs-lookup"><span data-stu-id="2c319-167">Application already running (1244550)</span></span> 
<span data-ttu-id="2c319-168">La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c319-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="2c319-169">SOLUCIÓN alternativa: cambie la aplicación de inicio predeterminada a una aplicación que no sea la que desea implementar.</span><span class="sxs-lookup"><span data-stu-id="2c319-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="2c319-170">BackgroundMediaPlayer. MessageReceivedFromForeground puede bloquearse (2199869)</span><span class="sxs-lookup"><span data-stu-id="2c319-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="2c319-171">La línea de código siguiente podría bloquearse:</span><span class="sxs-lookup"><span data-stu-id="2c319-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="2c319-172">Para evitar el bloqueo, agregue este código para que se ejecute primero:</span><span class="sxs-lookup"><span data-stu-id="2c319-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="2c319-173">Compatibilidad con la autenticación Azure Active Directory (4266261)</span><span class="sxs-lookup"><span data-stu-id="2c319-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="2c319-174">La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2c319-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="2c319-175">Administración del shell de los bloqueos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="2c319-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="2c319-176">La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="2c319-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="2c319-177">Si las aplicaciones reiniciadas continúan bloqueándose, el shell empleará FailFast: un proceso crítico del sistema que provoca una comprobación de errores y un reinicio en un intento de recuperación.</span><span class="sxs-lookup"><span data-stu-id="2c319-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="2c319-178">Se usan una lógica y un control comparables para las tareas en segundo plano y las aplicaciones de primer plano en una configuración con cabezal.</span><span class="sxs-lookup"><span data-stu-id="2c319-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="2c319-179">La lógica de reintento y control de bloqueos se captura a continuación:</span><span class="sxs-lookup"><span data-stu-id="2c319-179">Crash handling and retry logic is captured below:</span></span>

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

<span data-ttu-id="2c319-180">Espere el retraso y vuelva a iniciar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2c319-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="2c319-181">El SPI de DragonBoard se ejecuta a 4,8 Mhz</span><span class="sxs-lookup"><span data-stu-id="2c319-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="2c319-182">El SPI en DragonBoard omitirá la velocidad solicitada y siempre se ejecutará a 4,8 Mhz.</span><span class="sxs-lookup"><span data-stu-id="2c319-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="2c319-183">Modo de espera conectado de DragonBoard</span><span class="sxs-lookup"><span data-stu-id="2c319-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="2c319-184">El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="2c319-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="2c319-185">Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del registro debe establecerse en "1".</span><span class="sxs-lookup"><span data-stu-id="2c319-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="2c319-186">Sincronización de hora</span><span class="sxs-lookup"><span data-stu-id="2c319-186">Time synchronization</span></span>
<span data-ttu-id="2c319-187">Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales.</span><span class="sxs-lookup"><span data-stu-id="2c319-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="2c319-188">Desde una línea de comandos en el dispositivo (por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="2c319-188">From a command line on the device (eg.</span></span> <span data-ttu-id="2c319-189">SSH, PowerShell).</span><span class="sxs-lookup"><span data-stu-id="2c319-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="2c319-190">También puede realizar estas adiciones en el Registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado, incluido como parte del proceso de creación de imagen si es necesario.</span><span class="sxs-lookup"><span data-stu-id="2c319-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="2c319-191">Inicio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="2c319-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="2c319-192">Para ejecutarse una vez: inicie sesión con SSH\PS y ejecute este comando para iniciar FTP:</span><span class="sxs-lookup"><span data-stu-id="2c319-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="2c319-193">Para ejecutar en cada arranque, los usuarios deben crear un inicio de sesión de tarea de Scheduler con SSH\PS y crear una tarea de programador:</span><span class="sxs-lookup"><span data-stu-id="2c319-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="2c319-194">Requisitos de tamaño de partición para Update</span><span class="sxs-lookup"><span data-stu-id="2c319-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="2c319-195">Asegúrese de que la partición de datos mantiene suficiente espacio para la funcionalidad de actualización.</span><span class="sxs-lookup"><span data-stu-id="2c319-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="2c319-196">  Se recomienda 1 GB de disponibilidad para la funcionalidad de actualización completa.</span><span class="sxs-lookup"><span data-stu-id="2c319-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="2c319-197"> Si la partición de datos no tiene espacio suficiente, se producirá un error en las actualizaciones durante la fase de instalación.</span><span class="sxs-lookup"><span data-stu-id="2c319-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="2c319-198">Generación de registros de PowerShell en IoT Core</span><span class="sxs-lookup"><span data-stu-id="2c319-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="2c319-199">PowerShell en IOT Core puede generar archivos de registro de forma predeterminada ocupando espacio en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="2c319-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="2c319-200">Aunque los tamaños de los archivos de registro están limitados, pueden ocupar espacio, lo que puede dar lugar a una situación de poco espacio en disco que, entre otras cosas, pueden producir errores en las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="2c319-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="2c319-201">Los archivos de registro de eventos. evtx tienen un tamaño máximo predefinido de 20 MB cada uno.</span><span class="sxs-lookup"><span data-stu-id="2c319-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="2c319-202">Puede limitar los archivos de forma individual para que tengan un tamaño máximo diferente a través del registro.</span><span class="sxs-lookup"><span data-stu-id="2c319-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="2c319-203">Por ejemplo, para mantener Security. evtx en un tamaño máximo de 10 MB:</span><span class="sxs-lookup"><span data-stu-id="2c319-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="2c319-204">Limitación de SchTasks</span><span class="sxs-lookup"><span data-stu-id="2c319-204">Schtasks limitation</span></span>  
<span data-ttu-id="2c319-205">Schtasks no admite el uso del modificador/XML.</span><span class="sxs-lookup"><span data-stu-id="2c319-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="2c319-206">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2c319-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="2c319-207">Se producirá un error en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2c319-207">This will fail on IoT Core.</span></span> <span data-ttu-id="2c319-208">Al ejecutar el comando se generará el error: ERROR: no se encontró el procedimiento especificado.</span><span class="sxs-lookup"><span data-stu-id="2c319-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
