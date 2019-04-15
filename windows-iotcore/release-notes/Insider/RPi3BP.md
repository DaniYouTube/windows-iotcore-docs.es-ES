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
# <a name="release-notes-for-raspberry-pi-3b"></a>Notas de la versión de Raspberry Pi 3B +

&copy; 2018 Microsoft Corporation. Todos los derechos reservados.

> [!NOTE]
> Esta versión para el dispositivo Raspberry Pi 3B + es una versión preliminar técnica no admitida. Se ha completado la habilitación y la validación limitada. Puede encontrar la versión actual [aquí](https://www.microsoft.com/en-us/software-download/windowsiot). Para obtener una mejor evaluación experimentar y para los productos comerciales, use el 3B Raspberry Pi u otros dispositivos con Intel, Qualcomm o NXP Qualcomm admitidos. Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B +, consulte nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues). 

## <a name="whats-new-in-this-build"></a>Novedades en esta compilación: 
* Correcciones de errores generales

## <a name="known-issues-in-this-build"></a>Problemas conocidos de esta compilación:
* Esta imagen sólo está destinada para RPi3B + y no se iniciará en RPi2. 
* Implementación de controladores de F5 desde Visual Studio no funciona en IoT Core. 
* Incorporación de Wi-Fi y Bluetooth no funcionan en RPI3B +. 
* Controlador de pantalla táctil Ft5406 está deshabilitado en RPi3B +. 
* Está deshabilitado el LED de actividad de tarjeta SD. 


### <a name="display-resolution-is-monitor-is-disconnected"></a>Resolución de pantalla es el monitor está desconectado
El dispositivo Raspberry Pi 3B + no podrá mantener una resolución de pantalla si se desconecta el monitor. El EDID del monitor se usa para establecer la resolución del sistema cuando uno está conectado. Cuando se desconecta, el firmware del valor predeterminado es lo que está en el config.txt en la raíz de la tarjeta SD. 


### <a name="video-performance"></a>Rendimiento de vídeo
No se optimiza el rendimiento de reproducción de vídeo en la plataforma.  Anima el usuario pueden presentar elementos, como menús desplegables basada en XAML de menos de un rendimiento óptimo.  

### <a name="camera-support"></a>Compatibilidad con la cámara
Compatibilidad con dispositivos periféricos de cámara es limitada. No se admite el dispositivo PiCam directamente conectado al bus de cámara integrada debido a limitaciones en la plataforma para admitir USB modernas D3D cámaras Web generan los flujos de datos que son muy exigentes en el controlador Host USB.  Incluso cuando se usa con cámaras Web de configuración de baja resolución requerirá adicionales USB ajustar y especializada la lógica de control.  


### <a name="mouse-pointer-disappears-while-debugging"></a>Puntero del mouse desaparece durante la depuración
En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe reaparecer si cambia el foco mediante el teclado (pestaña) (8038595).

### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP
Cuando se usa el SoftAP los clientes no podrán tener acceso al contenido expuesto por aplicaciones UAP. Para exponer las aplicaciones a través de SoftAP UAP se deben realizar los cambios siguientes desde la consola en el dispositivo (8111807):  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

Reiniciar el equipo.

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Conflicto del controlador de sensor en FFUs precompiladas 
Hay un conflicto del controlador del Sensor en el FFUs proporcionados. El marco de Sensor remoto instala a controladores para Compass, Magnetómetro, acelerómetro y giro. Las API de UWP para tener acceso a ellos desde una aplicación se supone que solo uno está instalada. Si está desarrollando un controlador para un dispositivo físicamente conectado, el controlador remoto de Microsoft proporciona que ffus entrará en conflicto.  

Para resolver esto, se puede quitar el controlador en conflicto mediante la conexión al dispositivo a través de SSH o Powershell y usar la herramienta devcon.exe para quitar el controlador de sensor remoto escribiendo: 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

El controlador de sensor remoto no afecta a los OEM creado FFUs. 


### <a name="default-administrator-user-name-and-password"></a>Contraseña y nombre de usuario de administrador predeterminado
El nombre de usuario de administrador predeterminado y la contraseña son difíciles de codificada en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a internet abierto hasta que se cambió la contraseña. 

### <a name="volume-controls"></a>Controles de volumen
Controles de volumen de hardware para micrófonos USB y altavoces que dependen del sistema de Windows para cambiar el volumen del sistema no se admiten en Windows 10 IoT Core. 

### <a name="usb-keyboards"></a>Teclados USB
Algunos teclados y ratones USB no funcionen en IoT Core. Usar un teclado o mouse. Una lista de dispositivos periféricos validados puede encontrarse en la documentación de [aquí](http://go.microsoft.com/fwlink/?LinkId=619428).
 
### <a name="screen-orientation"></a>Orientación de pantalla
Establecer la orientación a "Vertical" no se respeta en una aplicación Universal.

### <a name="referencing-adapters-with-alljoyn-templates"></a>Hacer referencia a los adaptadores con plantillas de AllJoyn
Al intentar agregar referencias a proyectos de adaptador AllJoyn puede producirse errores al usar las versiones específicas del SDK.  Para resolver estos errores, cambiar la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y vuelva a cargar el proyecto.  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a>Limitaciones de Wi-Fi Direct en Windows 10 IoT Core
1. El de Windows 10 IoT Core dispositivo debe ser el dispositivo de conexión no funcionará como dispositivo de publicidad con otro dispositivo inicia la conexión.   
2. Debe usarse el emparejamiento avanzadas.  La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de conectar. 
3. No todos los adaptadores inalámbricos admiten Wi-Fi direct. Hemos probado y comprobado que la "red USB 2.0 de Realtek RTL8188EU Wireless Lan 802. 11n adaptador" funciona, pero otros adaptadores no se admite. 

### <a name="non-default-drive-mode-3890679"></a>Modo de unidad no predeterminada (3890679) 
En Raspberry Pi y Dragonboard, al cambiar de un modo de unidad no predeterminada a un modo de unidad no predeterminada diferente, puede producir un problema en la clavija GPIO. Para solucionar este problema, establecer el modo de unidad una vez al principio de la aplicación. 

### <a name="application-already-running-1244550"></a>Aplicación ya está ejecutando (1244550) 
La aplicación de inicio predeterminada podría entrar en conflicto con sí mismo cuando también se implementa desde Visual Studio. Solución alternativa: Cambiar la aplicación de inicio predeterminada para una aplicación que distinta de la que desea implementar. 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a>Se puede bloquear BackgroundMediaPlayer.MessageReceivedFromForeground (2199869) 
Se puede bloquear la siguiente línea de código: 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

Para evitar el bloqueo, agregue este código para que se ejecute en primer lugar:
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a>Compatibilidad con la autenticación de Azure Active Directory (4266261) 
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  

### <a name="shell-management-of-application-crashes"></a>Shell de administración de bloqueos de la aplicación
Infraestructura de IoT Core shell supervisa aplicaciones APPX-type que se ejecutan en el dispositivo de bloqueos y reinicia esas aplicaciones cuando se producen bloqueos.  Si las aplicaciones reiniciadas continúan se bloquee, el shell se emplean failfast: un proceso crítico de sistema que provoca una comprobación de errores y reinicie en un intento de recuperar.  Control y comparable lógica se utiliza para aplicaciones de primer plano en una configuración con cabezal y tareas en segundo plano.   A continuación, se captura lógica de reintento y control de bloqueo:

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

Espere a que el retraso y vuelva a iniciar la aplicación.

#### <a name="dragonboard-spi-runs-at-48mhz"></a>Dragonboard SPI se ejecuta en 4,8 Mhz
El SPI en el Dragonboard omitirá la velocidad solicitada y siempre se ejecutan con 4,8 Mhz.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard conectado en espera 
Modo de espera conectado no está habilitado en el Qualcomm Dragonboard de forma predeterminada.  Para habilitar el modo de espera conectado en DragonBoard la siguiente clave del registro debe establecerse en "1".


### <a name="time-synchronization"></a>Sincronización de hora
Si se producen errores en sincronización de hora o tiempo de espera de esto puede deberse a inaccesible o un servidor distante del tiempo, la siguiente puede hacerse para agregar servidores de hora local o adicionales. 
 
1. Desde una línea de comandos en el dispositivo (p ej. SSH, Powershell).
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. También puede hacer estas adiciones en el registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado incluido como parte del proceso de creación de imagen si es necesario. 

### <a name="starting-the-ftp-server"></a>Iniciar el servidor FTP 
* Para ejecutar una vez - inicio de sesión con SSH\PS y ejecute este comando para iniciar FTP:  

```
start ftpd.exe 
```

* Para ejecutar en cada arranque, los usuarios deben crear un programador de tareas - Inicio de sesión con SSH\PS y crear un programador de tareas:

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a>Requisitos de tamaño de partición para la actualización 
Asegúrese de partición de datos mantiene suficiente espacio para la funcionalidad de actualización.  Se recomienda 1GB de espacio libre para la funcionalidad de actualización completa.  Si la partición de datos no tiene suficiente espacio, las actualizaciones se producirá un error en la fase de instalación. 

### <a name="powershell-log-generation-on-iot-core"></a>Generación de registro de PowerShell en IoT Core 
PowerShell en Iot Core puede generar archivos de registro de forma predeterminada, ocupando espacio en el sistema de archivos. Aunque los tamaños de archivo de registro están limitados pueden ocupar espacio, lo que puede producir una situación de espacio insuficiente en disco que, entre otras cosas, puede dar lugar a actualizaciones con errores. Los archivos de registro de eventos de .evtx tienen un tamaño máximo predefinido de 20 MB cada uno. Individualmente puede limitar los archivos para que tengan un tamaño máximo diferentes a través del registro. Por ejemplo, para mantener security.evtx con tamaño máximo de 10 MB: 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a>SCHTASKS limitación  
Schtasks no admite el uso de modificador /xml. Por ejemplo: 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
Esto generará un error en IoT Core. Ejecute el comando generará el error: ERROR: No se encontró el procedimiento especificado. 
