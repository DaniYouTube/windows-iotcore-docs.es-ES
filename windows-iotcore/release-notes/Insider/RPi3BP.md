---
title: Notas de la versión de Raspberry Pi 3B +
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 05/16/2018
ms.topic: article
description: Lea y obtenga información sobre las novedades en la compilación para Raspberry Pi 3B +.
keywords: Windows iot, Windows Insider, notas de la versión, Raspberry Pi 3B +
ms.openlocfilehash: f9a1bf98e6ef53ff7f96d35cb34af9527f1c6de1
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514451"
---
# <a name="release-notes-for-raspberry-pi-3b"></a><span data-ttu-id="cf4c6-104">Notas de la versión de Raspberry Pi 3B +</span><span class="sxs-lookup"><span data-stu-id="cf4c6-104">Release Notes for Raspberry Pi 3B+</span></span>

<span data-ttu-id="cf4c6-105">&copy; 2018 Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-105">&copy; 2018 Microsoft Corporation.</span></span> <span data-ttu-id="cf4c6-106">Todos los derechos reservados.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-106">All rights reserved.</span></span>

> [!NOTE]
> <span data-ttu-id="cf4c6-107">Esta versión para el dispositivo Raspberry Pi 3B + es una versión preliminar técnica no admitida.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-107">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="cf4c6-108">Se ha completado la habilitación y la validación limitada.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-108">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="cf4c6-109">Puede encontrar la versión actual [aquí](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="cf4c6-109">The current release can be found [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="cf4c6-110">Para obtener una mejor evaluación experimentar y para los productos comerciales, use el 3B Raspberry Pi u otros dispositivos con Intel, Qualcomm o NXP Qualcomm admitidos.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-110">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="cf4c6-111">Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B +, consulte nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="cf4c6-111">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

## <a name="whats-new-in-this-build"></a><span data-ttu-id="cf4c6-112">Novedades en esta compilación:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-112">What's new in this build:</span></span> 
* <span data-ttu-id="cf4c6-113">Correcciones de errores generales</span><span class="sxs-lookup"><span data-stu-id="cf4c6-113">General bug fixes</span></span>

## <a name="known-issues-in-this-build"></a><span data-ttu-id="cf4c6-114">Problemas conocidos de esta compilación:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-114">Known issues in this build:</span></span>
* <span data-ttu-id="cf4c6-115">Esta imagen sólo está destinada para RPi3B + y no se iniciará en RPi2.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-115">This image is only meant for RPi3B+ and will not boot on RPi2.</span></span> 
* <span data-ttu-id="cf4c6-116">Implementación de controladores de F5 desde Visual Studio no funciona en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-116">F5 driver deployment from Visual Studio does not work on IoT Core.</span></span> 
* <span data-ttu-id="cf4c6-117">Incorporación de Wi-Fi y Bluetooth no funcionan en RPI3B +.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-117">Onboard WIFI and Bluetooth do not work on RPI3B+.</span></span> 
* <span data-ttu-id="cf4c6-118">Controlador de pantalla táctil Ft5406 está deshabilitado en RPi3B +.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-118">Ft5406 touch screen driver is disabled on RPi3B+.</span></span> 
* <span data-ttu-id="cf4c6-119">Está deshabilitado el LED de actividad de tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-119">SD card activity LED is disabled.</span></span> 


### <a name="display-resolution-is-monitor-is-disconnected"></a><span data-ttu-id="cf4c6-120">Resolución de pantalla es el monitor está desconectado</span><span class="sxs-lookup"><span data-stu-id="cf4c6-120">Display resolution is monitor is disconnected</span></span>
<span data-ttu-id="cf4c6-121">El dispositivo Raspberry Pi 3B + no podrá mantener una resolución de pantalla si se desconecta el monitor.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-121">The Raspberry Pi 3B+ may not maintain Display Resolution if monitor is disconnected.</span></span> <span data-ttu-id="cf4c6-122">El EDID del monitor se usa para establecer la resolución del sistema cuando uno está conectado.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-122">The EDID of the monitor is used to set the resolution of the system when one is connected.</span></span> <span data-ttu-id="cf4c6-123">Cuando se desconecta, el firmware del valor predeterminado es lo que está en el config.txt en la raíz de la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-123">When disconnected, the firmware defaults to what is in the config.txt in the root of the SD card.</span></span> 


### <a name="video-performance"></a><span data-ttu-id="cf4c6-124">Rendimiento de vídeo</span><span class="sxs-lookup"><span data-stu-id="cf4c6-124">Video performance</span></span>
<span data-ttu-id="cf4c6-125">No se optimiza el rendimiento de reproducción de vídeo en la plataforma.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-125">Video playback performance on the platform is not optimized.</span></span>  <span data-ttu-id="cf4c6-126">Anima el usuario pueden presentar elementos, como menús desplegables basada en XAML de menos de un rendimiento óptimo.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-126">Animated user elements including XAML-based dropdown menus may exhibit less than optimal performance.</span></span>  

### <a name="camera-support"></a><span data-ttu-id="cf4c6-127">Compatibilidad con la cámara</span><span class="sxs-lookup"><span data-stu-id="cf4c6-127">Camera support</span></span>
<span data-ttu-id="cf4c6-128">Compatibilidad con dispositivos periféricos de cámara es limitada.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-128">Support for camera peripheral devices is limited.</span></span> <span data-ttu-id="cf4c6-129">No se admite el dispositivo PiCam directamente conectado al bus de cámara integrada debido a limitaciones en la plataforma para admitir USB modernas D3D cámaras Web generan los flujos de datos que son muy exigentes en el controlador Host USB.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-129">The PiCam device directly connected to the onboard camera bus is not supported due to limitations in the platform to support D3D Modern USB webcams produce data streams that are very demanding on the USB Host controller.</span></span>  <span data-ttu-id="cf4c6-130">Incluso cuando se usa con cámaras Web de configuración de baja resolución requerirá adicionales USB ajustar y especializada la lógica de control.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-130">Even when used with low resolution settings webcams will require additional USB fine tuning and specialized control logic.</span></span>  


### <a name="mouse-pointer-disappears-while-debugging"></a><span data-ttu-id="cf4c6-131">Puntero del mouse desaparece durante la depuración</span><span class="sxs-lookup"><span data-stu-id="cf4c6-131">Mouse pointer disappears while debugging</span></span>
<span data-ttu-id="cf4c6-132">En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe reaparecer si cambia el foco mediante el teclado (pestaña) (8038595).</span><span class="sxs-lookup"><span data-stu-id="cf4c6-132">In some cases, the mouse pointer is not visible after deploying or debugging apps with Visual Studio, the mouse pointer should reappear if you change focus using the keyboard (Tab) (8038595).</span></span>

### <a name="server-applications-with-softap"></a><span data-ttu-id="cf4c6-133">Aplicaciones de servidor con SoftAP</span><span class="sxs-lookup"><span data-stu-id="cf4c6-133">Server applications with SoftAP</span></span>
<span data-ttu-id="cf4c6-134">Cuando se usa el SoftAP los clientes no podrán tener acceso al contenido expuesto por aplicaciones UAP.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-134">When using the SoftAP clients will not be able to access content exposed by UAP apps.</span></span> <span data-ttu-id="cf4c6-135">Para exponer las aplicaciones a través de SoftAP UAP se deben realizar los cambios siguientes desde la consola en el dispositivo (8111807):</span><span class="sxs-lookup"><span data-stu-id="cf4c6-135">To expose UAP applications via SoftAP the following changes must be made from the console on the device (8111807):</span></span>  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

<span data-ttu-id="cf4c6-136">Reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-136">Reboot.</span></span>

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a><span data-ttu-id="cf4c6-137">Conflicto del controlador de sensor en FFUs precompiladas</span><span class="sxs-lookup"><span data-stu-id="cf4c6-137">Sensor Driver conflict in pre-built FFUs</span></span> 
<span data-ttu-id="cf4c6-138">Hay un conflicto del controlador del Sensor en el FFUs proporcionados.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-138">There is a Sensor Driver Conflict in the provided FFUs.</span></span> <span data-ttu-id="cf4c6-139">El marco de Sensor remoto instala a controladores para Compass, Magnetómetro, acelerómetro y giro.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-139">The Remote Sensor Framework installs drivers for Compass, Magnetometer, Accelerometer and Gyro.</span></span> <span data-ttu-id="cf4c6-140">Las API de UWP para tener acceso a ellos desde una aplicación se supone que solo uno está instalada.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-140">The UWP APIs for accessing these from an application assume just one is installed.</span></span> <span data-ttu-id="cf4c6-141">Si está desarrollando un controlador para un dispositivo físicamente conectado, el controlador remoto de Microsoft proporciona que ffus entrará en conflicto.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-141">If you are developing a driver for a physically attached device, the remote driver on the Microsoft provided FFUs will conflict.</span></span>  

<span data-ttu-id="cf4c6-142">Para resolver esto, se puede quitar el controlador en conflicto mediante la conexión al dispositivo a través de SSH o Powershell y usar la herramienta devcon.exe para quitar el controlador de sensor remoto escribiendo:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-142">To solve for this, the conflicting driver can be removed by connecting to the device via SSH or Powershell and using the tool devcon.exe to remove the remote sensor driver by typing:</span></span> 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

<span data-ttu-id="cf4c6-143">El controlador de sensor remoto no afecta a los OEM creado FFUs.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-143">The remote sensor driver does not affect OEM created FFUs.</span></span> 


### <a name="default-administrator-user-name-and-password"></a><span data-ttu-id="cf4c6-144">Contraseña y nombre de usuario de administrador predeterminado</span><span class="sxs-lookup"><span data-stu-id="cf4c6-144">Default administrator user name and password</span></span>
<span data-ttu-id="cf4c6-145">El nombre de usuario de administrador predeterminado y la contraseña son difíciles de codificada en la imagen de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-145">The default administrator user name and password are hard coded in the Windows 10 IoT Core image.</span></span> <span data-ttu-id="cf4c6-146">Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a internet abierto hasta que se cambió la contraseña.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-146">This is a security risk for the device, and it should not be exposed to an open internet connection until the password has been changed.</span></span> 

### <a name="volume-controls"></a><span data-ttu-id="cf4c6-147">Controles de volumen</span><span class="sxs-lookup"><span data-stu-id="cf4c6-147">Volume controls</span></span>
<span data-ttu-id="cf4c6-148">Controles de volumen de hardware para micrófonos USB y altavoces que dependen del sistema de Windows para cambiar el volumen del sistema no se admiten en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-148">Hardware volume controls for USB microphones and speakers which depend on Windows system to change system volume are currently not supported on Windows 10 IoT Core.</span></span> 

### <a name="usb-keyboards"></a><span data-ttu-id="cf4c6-149">Teclados USB</span><span class="sxs-lookup"><span data-stu-id="cf4c6-149">USB keyboards</span></span>
<span data-ttu-id="cf4c6-150">Algunos teclados y ratones USB no funcionen en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-150">Some USB keyboards and mice may not work on IoT Core.</span></span> <span data-ttu-id="cf4c6-151">Usar un teclado o mouse.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-151">Use a different keyboard or mouse.</span></span> <span data-ttu-id="cf4c6-152">Una lista de dispositivos periféricos validados puede encontrarse en la documentación de [aquí](http://go.microsoft.com/fwlink/?LinkId=619428).</span><span class="sxs-lookup"><span data-stu-id="cf4c6-152">A list of validated peripheral devices can be found in the documentation [here](http://go.microsoft.com/fwlink/?LinkId=619428).</span></span>
 
### <a name="screen-orientation"></a><span data-ttu-id="cf4c6-153">Orientación de pantalla</span><span class="sxs-lookup"><span data-stu-id="cf4c6-153">Screen orientation</span></span>
<span data-ttu-id="cf4c6-154">Establecer la orientación a "Vertical" no se respeta en una aplicación Universal.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-154">Setting the orientation to “Portrait” may not be honored in a Universal App.</span></span>

### <a name="referencing-adapters-with-alljoyn-templates"></a><span data-ttu-id="cf4c6-155">Hacer referencia a los adaptadores con plantillas de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="cf4c6-155">Referencing adapters with AllJoyn templates</span></span>
<span data-ttu-id="cf4c6-156">Al intentar agregar referencias a proyectos de adaptador AllJoyn puede producirse errores al usar las versiones específicas del SDK.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-156">Attempting to add references to AllJoyn adapter projects may result in errors when using specific SDK versions.</span></span>  <span data-ttu-id="cf4c6-157">Para resolver estos errores, cambiar la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y vuelva a cargar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-157">To resolve these errors, change Visual Studio’s target platform to match the current SDK version, then reload the project.</span></span>  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a><span data-ttu-id="cf4c6-158">Limitaciones de Wi-Fi Direct en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="cf4c6-158">WiFi Direct limitations on Windows 10 IoT Core</span></span>
1. <span data-ttu-id="cf4c6-159">El de Windows 10 IoT Core dispositivo debe ser el dispositivo de conexión no funcionará como dispositivo de publicidad con otro dispositivo inicia la conexión.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-159">The Windows 10 IoT Core device has to be the connecting device – it will not work as the advertising device with another device initiating the connection.</span></span>   
2. <span data-ttu-id="cf4c6-160">Debe usarse el emparejamiento avanzadas.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-160">Advanced pairing must be used.</span></span>  <span data-ttu-id="cf4c6-161">La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de conectar.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-161">The sample app demonstrates how to use the advanced pairing API’s to pair the devices prior to connecting.</span></span> 
3. <span data-ttu-id="cf4c6-162">No todos los adaptadores inalámbricos admiten Wi-Fi direct.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-162">Not all wireless adapters support WiFi direct.</span></span> <span data-ttu-id="cf4c6-163">Hemos probado y comprobado que la "red USB 2.0 de Realtek RTL8188EU Wireless Lan 802. 11n adaptador" funciona, pero otros adaptadores no se admite.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-163">We have tested and validated that the "Realtek RTL8188EU Wireless Lan 802.11n USB 2.0 Network adapter" works, but other adapters may not be supported.</span></span> 

### <a name="non-default-drive-mode-3890679"></a><span data-ttu-id="cf4c6-164">Modo de unidad no predeterminada (3890679)</span><span class="sxs-lookup"><span data-stu-id="cf4c6-164">Non-default drive mode (3890679)</span></span> 
<span data-ttu-id="cf4c6-165">En Raspberry Pi y Dragonboard, al cambiar de un modo de unidad no predeterminada a un modo de unidad no predeterminada diferente, puede producir un problema en la clavija GPIO.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-165">On Raspberry Pi and Dragonboard, switching from a non-default drive mode to a different non-default drive mode may produce a glitch on the GPIO pin.</span></span> <span data-ttu-id="cf4c6-166">Para solucionar este problema, establecer el modo de unidad una vez al principio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-166">To workaround this issue, set drive mode once at the beginning of the application.</span></span> 

### <a name="application-already-running-1244550"></a><span data-ttu-id="cf4c6-167">Aplicación ya está ejecutando (1244550)</span><span class="sxs-lookup"><span data-stu-id="cf4c6-167">Application already running (1244550)</span></span> 
<span data-ttu-id="cf4c6-168">La aplicación de inicio predeterminada podría entrar en conflicto con sí mismo cuando también se implementa desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-168">The Default startup app may conflict with itself when it is also deployed from Visual Studio.</span></span> <span data-ttu-id="cf4c6-169">Solución alternativa: Cambiar la aplicación de inicio predeterminada para una aplicación que distinta de la que desea implementar.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-169">WORKAROUND: Change the default startup app to an application other than that you wish to deploy.</span></span> 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a><span data-ttu-id="cf4c6-170">Se puede bloquear BackgroundMediaPlayer.MessageReceivedFromForeground (2199869)</span><span class="sxs-lookup"><span data-stu-id="cf4c6-170">BackgroundMediaPlayer.MessageReceivedFromForeground may crash (2199869)</span></span> 
<span data-ttu-id="cf4c6-171">Se puede bloquear la siguiente línea de código:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-171">The following line of code may crash:</span></span> 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

<span data-ttu-id="cf4c6-172">Para evitar el bloqueo, agregue este código para que se ejecute en primer lugar:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-172">To prevent the crash, add this code so that it is executed first:</span></span>
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a><span data-ttu-id="cf4c6-173">Compatibilidad con la autenticación de Azure Active Directory (4266261)</span><span class="sxs-lookup"><span data-stu-id="cf4c6-173">Azure Active Directory Authentication Support (4266261)</span></span> 
<span data-ttu-id="cf4c6-174">La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-174">The Azure Active Directory Authentication Library does not work on Windows 10 IoT Core.</span></span>  

### <a name="shell-management-of-application-crashes"></a><span data-ttu-id="cf4c6-175">Shell de administración de bloqueos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="cf4c6-175">Shell Management of Application Crashes</span></span>
<span data-ttu-id="cf4c6-176">Infraestructura de IoT Core shell supervisa aplicaciones APPX-type que se ejecutan en el dispositivo de bloqueos y reinicia esas aplicaciones cuando se producen bloqueos.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-176">IoT Core’s shell infrastructure monitors APPX-type applications running on the device for crashes, and restarts those applications when crashes occur.</span></span>  <span data-ttu-id="cf4c6-177">Si las aplicaciones reiniciadas continúan se bloquee, el shell se emplean failfast: un proceso crítico de sistema que provoca una comprobación de errores y reinicie en un intento de recuperar.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-177">If the restarted applications continue to crash, the shell will employ a failfast – a system critical process that causes a bugcheck and reboot in an attempt to recover.</span></span>  <span data-ttu-id="cf4c6-178">Control y comparable lógica se utiliza para aplicaciones de primer plano en una configuración con cabezal y tareas en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-178">Comparable logic and handling is used to background tasks and foreground applications in a headed configuration.</span></span>   <span data-ttu-id="cf4c6-179">A continuación, se captura lógica de reintento y control de bloqueo:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-179">Crash handling and retry logic is captured below:</span></span>

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

<span data-ttu-id="cf4c6-180">Espere a que el retraso y vuelva a iniciar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-180">Wait for the delay and relaunch the app.</span></span>

#### <a name="dragonboard-spi-runs-at-48mhz"></a><span data-ttu-id="cf4c6-181">Dragonboard SPI se ejecuta en 4,8 Mhz</span><span class="sxs-lookup"><span data-stu-id="cf4c6-181">Dragonboard SPI runs at 4.8Mhz</span></span>
<span data-ttu-id="cf4c6-182">El SPI en el Dragonboard omitirá la velocidad solicitada y siempre se ejecutan con 4,8 Mhz.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-182">The SPI on the Dragonboard will ignore the requested speed and always run at 4.8 Mhz.</span></span>  

#### <a name="dragonboard-connected-standby"></a><span data-ttu-id="cf4c6-183">Dragonboard conectado en espera</span><span class="sxs-lookup"><span data-stu-id="cf4c6-183">Dragonboard Connected Standby</span></span> 
<span data-ttu-id="cf4c6-184">Modo de espera conectado no está habilitado en el Qualcomm Dragonboard de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-184">Connected Standby is not enabled on the Qualcomm Dragonboard by default.</span></span>  <span data-ttu-id="cf4c6-185">Para habilitar el modo de espera conectado en DragonBoard la siguiente clave del registro debe establecerse en "1".</span><span class="sxs-lookup"><span data-stu-id="cf4c6-185">To enable Connected Standby on DragonBoard the following registry key needs to be set to “1”.</span></span>


### <a name="time-synchronization"></a><span data-ttu-id="cf4c6-186">Sincronización de hora</span><span class="sxs-lookup"><span data-stu-id="cf4c6-186">Time synchronization</span></span>
<span data-ttu-id="cf4c6-187">Si se producen errores en sincronización de hora o tiempo de espera de esto puede deberse a inaccesible o un servidor distante del tiempo, la siguiente puede hacerse para agregar servidores de hora local o adicionales.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-187">If time sync is failing or timing out this may be due to unreachable or a distant time server, the following can be done to add additional or local time servers.</span></span> 
 
1. <span data-ttu-id="cf4c6-188">Desde una línea de comandos en el dispositivo (p ej.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-188">From a command line on the device (eg.</span></span> <span data-ttu-id="cf4c6-189">SSH, Powershell).</span><span class="sxs-lookup"><span data-stu-id="cf4c6-189">SSH, Powershell).</span></span>
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. <span data-ttu-id="cf4c6-190">También puede hacer estas adiciones en el registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado incluido como parte del proceso de creación de imagen si es necesario.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-190">You may also make these additions to the registry via a boot script or a custom runtime configuration package included as part of the image creation process if needed.</span></span> 

### <a name="starting-the-ftp-server"></a><span data-ttu-id="cf4c6-191">Iniciar el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="cf4c6-191">Starting the FTP Server</span></span> 
* <span data-ttu-id="cf4c6-192">Para ejecutar una vez - inicio de sesión con SSH\PS y ejecute este comando para iniciar FTP:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-192">To run once - Login with SSH\PS and run this command to start FTP:</span></span>  

```
start ftpd.exe 
```

* <span data-ttu-id="cf4c6-193">Para ejecutar en cada arranque, los usuarios deben crear un programador de tareas - Inicio de sesión con SSH\PS y crear un programador de tareas:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-193">To run on every boot, users should create a scheduler task - Login with SSH\PS and create a scheduler task:</span></span>

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a><span data-ttu-id="cf4c6-194">Requisitos de tamaño de partición para la actualización</span><span class="sxs-lookup"><span data-stu-id="cf4c6-194">Partition size requirements for Update</span></span> 
<span data-ttu-id="cf4c6-195">Asegúrese de partición de datos mantiene suficiente espacio para la funcionalidad de actualización.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-195">Ensure data partition maintains sufficient space for update functionality.</span></span><span data-ttu-id="cf4c6-196">  Se recomienda 1GB de espacio libre para la funcionalidad de actualización completa.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-196">  We recommend 1GB free for full update functionality.</span></span> <span data-ttu-id="cf4c6-197"> Si la partición de datos no tiene suficiente espacio, las actualizaciones se producirá un error en la fase de instalación.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-197"> If Data partition does not have enough space, updates will fail in the installation phase.</span></span> 

### <a name="powershell-log-generation-on-iot-core"></a><span data-ttu-id="cf4c6-198">Generación de registro de PowerShell en IoT Core</span><span class="sxs-lookup"><span data-stu-id="cf4c6-198">PowerShell log generation on IoT Core</span></span> 
<span data-ttu-id="cf4c6-199">PowerShell en Iot Core puede generar archivos de registro de forma predeterminada, ocupando espacio en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-199">PowerShell on Iot Core may generate log files by default taking up space on the filesystem.</span></span> <span data-ttu-id="cf4c6-200">Aunque los tamaños de archivo de registro están limitados pueden ocupar espacio, lo que puede producir una situación de espacio insuficiente en disco que, entre otras cosas, puede dar lugar a actualizaciones con errores.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-200">Although the log file sizes are limited they can take up space potentially resulting in a low disk space situation which, among other things, can result in updates failing.</span></span> <span data-ttu-id="cf4c6-201">Los archivos de registro de eventos de .evtx tienen un tamaño máximo predefinido de 20 MB cada uno.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-201">The .evtx event log files have a predefined maximum size of 20 MB each.</span></span> <span data-ttu-id="cf4c6-202">Individualmente puede limitar los archivos para que tengan un tamaño máximo diferentes a través del registro.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-202">You  can individually limit files to have a different max size via registry.</span></span> <span data-ttu-id="cf4c6-203">Por ejemplo, para mantener security.evtx con tamaño máximo de 10 MB:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-203">For example, To keep security.evtx at 10 MB max size:</span></span> 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a><span data-ttu-id="cf4c6-204">SCHTASKS limitación</span><span class="sxs-lookup"><span data-stu-id="cf4c6-204">Schtasks limitation</span></span>  
<span data-ttu-id="cf4c6-205">Schtasks no admite el uso de modificador /xml.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-205">Schtasks does not support using /xml switch.</span></span> <span data-ttu-id="cf4c6-206">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="cf4c6-206">For example:</span></span> 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
<span data-ttu-id="cf4c6-207">Esto generará un error en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-207">This will fail on IoT Core.</span></span> <span data-ttu-id="cf4c6-208">Ejecute el comando generará el error: ERROR: No se encontró el procedimiento especificado.</span><span class="sxs-lookup"><span data-stu-id="cf4c6-208">Running the command will generate the error: ERROR: The specified procedure could not be found.</span></span> 
