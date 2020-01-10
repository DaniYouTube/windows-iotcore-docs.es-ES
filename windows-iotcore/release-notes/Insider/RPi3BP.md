---
title: Notas de la versión de Raspberry PI 3B +
ms.date: 05/16/2018
ms.topic: article
description: Lea y obtenga información sobre lo que hay en la compilación de Raspberry PI 3B +.
keywords: Windows IOT, Windows Insider, notas de la versión, Raspberry PI 3B +
ms.openlocfilehash: d321676758f7ff438540720098e6a6ecb1ba457f
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721020"
---
# <a name="release-notes-for-raspberry-pi-3b"></a>Notas de la versión de Raspberry PI 3B +

&copy; 2018 Microsoft Corporation. Todos los derechos reservados.

> [!NOTE]
> Esta versión para Raspberry Pi 3B+ es una versión preliminar técnica no admitida. Se ha completado la habilitación y la validación limitadas. La versión actual se puede encontrar [aquí](https://www.microsoft.com/en-us/software-download/windowsiot). Para obtener una mejor experiencia de evaluación y para cualquier producto comercial, use Raspberry Pi 3B u otros dispositivos con SoC de Intel, Qualcomm o NXP admitidos. Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B+, vea nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues). 

## <a name="whats-new-in-this-build"></a>Novedades de esta compilación: 
* Correcciones de errores generales

## <a name="known-issues-in-this-build"></a>Problemas conocidos de esta compilación:
* Esta imagen solo está pensada para RPi3B + y no arrancará en RPi2. 
* La implementación del controlador F5 de Visual Studio no funciona en IoT Core. 
* La incorporación de Wi-Fi y Bluetooth no funcionan en RPI3B +. 
* El controlador de pantalla táctil de Ft5406 está deshabilitado en RPi3B +. 
* El LED de actividad de tarjeta SD está deshabilitado. 


### <a name="display-resolution-is-monitor-is-disconnected"></a>La resolución de pantalla está desconectada
Es posible que Raspberry PI 3B + no mantenga la resolución de pantalla si el monitor está desconectado. El EDID del monitor se usa para establecer la resolución del sistema cuando hay uno conectado. Cuando está desconectada, el firmware tiene como valor predeterminado lo que se encuentra en el archivo config. txt en la raíz de la tarjeta SD. 


### <a name="video-performance"></a>Rendimiento de vídeo
El rendimiento de reproducción de vídeo en la plataforma no está optimizado.  Es posible que el rendimiento que muestren los elementos animados del usuario, incluidos los menús desplegables basados en XAML, no sea el óptimo.  

### <a name="camera-support"></a>Compatibilidad con cámaras
La compatibilidad con los dispositivos periféricos de cámara es limitada. El dispositivo PiCam conectado directamente al bus de la cámara incorporada no es compatible, ya que las limitaciones de la plataforma para admitir cámaras web USB modernas D3D generan flujos de datos muy exigentes en la controladora de host USB.  Incluso cuando se usa con cámaras web con valores de resolución bajos, se requerirá un ajuste preciso adicional y una lógica de control especializada del USB.  


### <a name="mouse-pointer-disappears-while-debugging"></a>El puntero del mouse desaparece durante la depuración
En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe volver a aparecer si cambia el foco con el teclado (tabulación) (8038595).

### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP
Cuando se usa SoftAP, los clientes no podrán acceder al contenido que exponen las aplicaciones UAP. Para exponer las aplicaciones UAP a través de SoftAP, se deben realizar los siguientes cambios desde la consola de en el dispositivo (8111807):  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym 
```

Reinicie el equipo.

### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Conflicto del controlador de sensor en FFU precompiladas 
Hay un conflicto del controlador de sensor en las FFU proporcionadas. El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio. Las API de UWP para acceder a ellas desde una aplicación suponen que solo hay una instalada. Si va a desarrollar un controlador para un dispositivo adjuntado físicamente, el controlador remoto de las FFU que proporciona Microsoft entrará en conflicto.  

Para solucionar este problema, se puede quitar el controlador conflictivo conectándose al dispositivo a través de SSH o PowerShell y usando la herramienta DEVCON. exe para quitar el controlador del sensor remoto; para ello, escriba: 

```
"devcon.exe remove @"ROOT\REMOTESENSORDRIVER*"
```

El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original. 


### <a name="default-administrator-user-name-and-password"></a>Nombre de usuario y contraseña de administrador predeterminados
El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña. 

### <a name="volume-controls"></a>Controles de volumen
Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core. 

### <a name="usb-keyboards"></a>Teclados USB
Es posible que algún teclado y mouse USB no funcionen en IoT Core. Use otro teclado o mouse. Puede encontrar una lista de dispositivos periféricos validados en la documentación [aquí](https://go.microsoft.com/fwlink/?LinkId=619428).
 
### <a name="screen-orientation"></a>Orientación de la pantalla
El establecimiento de la orientación en "Vertical" puede que no se respete en una aplicación universal.

### <a name="referencing-adapters-with-alljoyn-templates"></a>Referencia a adaptadores con plantillas AllJoyn
El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.  Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, luego, vuelva a cargar el proyecto.  

### <a name="wifi-direct-limitations-on-windows-10-iot-core"></a>Limitaciones de WiFi Direct en Windows 10 IoT Core
1. El dispositivo de Windows 10 IoT Core debe ser el dispositivo que se conecta: no funcionará como el dispositivo de publicidad con otro dispositivo que inicie la conexión.   
2. Se debe usar el emparejamiento avanzado.  La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de la conexión. 
3. No todos los adaptadores inalámbricos son compatibles con Wi-Fi Direct. Hemos probado y validado el funcionamiento del adaptador de red "Realtek RTL8188EU Wireless LAN 802.11 n USB 2,0", pero es posible que no se admitan otros adaptadores. 

### <a name="non-default-drive-mode-3890679"></a>Modo de unidad no predeterminada (3890679) 
En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO. Para solucionar este problema, establezca el modo de unidad una vez al principio de la aplicación. 

### <a name="application-already-running-1244550"></a>La aplicación ya se está ejecutando (1244550) 
La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio. SOLUCIÓN alternativa: cambie la aplicación de inicio predeterminada a una aplicación que no sea la que desea implementar. 

### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash-2199869"></a>BackgroundMediaPlayer. MessageReceivedFromForeground puede bloquearse (2199869) 
La línea de código siguiente podría bloquearse: 
```
BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground
```

Para evitar el bloqueo, agregue este código para que se ejecute primero:
```
var player = BackgroundMediaPlayer.Current;
```

### <a name="azure-active-directory-authentication-support-4266261"></a>Compatibilidad con la autenticación Azure Active Directory (4266261) 
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  

### <a name="shell-management-of-application-crashes"></a>Administración del shell de los bloqueos de la aplicación
La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.  Si las aplicaciones reiniciadas continúan bloqueándose, el shell empleará FailFast: un proceso crítico del sistema que provoca una comprobación de errores y un reinicio en un intento de recuperación.  Se usan una lógica y un control comparables para las tareas en segundo plano y las aplicaciones de primer plano en una configuración con cabezal.   La lógica de reintento y control de bloqueos se captura a continuación:

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

Espere el retraso y vuelva a iniciar la aplicación.

#### <a name="dragonboard-spi-runs-at-48mhz"></a>El SPI de DragonBoard se ejecuta a 4,8 Mhz
El SPI de DragonBoard omitirá la velocidad solicitada y siempre se ejecutará a 4,8 Mhz.  

#### <a name="dragonboard-connected-standby"></a>Modo de espera conectado de DragonBoard 
El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.  Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del registro debe establecerse en "1".


### <a name="time-synchronization"></a>Sincronización de hora
Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales. 
 
1. Desde una línea de comandos en el dispositivo (por ejemplo, SSH, PowerShell).
   ```
   w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..."
   ```
2. También puede realizar estas adiciones en el Registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado, incluido como parte del proceso de creación de imagen si es necesario. 

### <a name="starting-the-ftp-server"></a>Inicio del servidor FTP 
* Para ejecutarse una vez: inicie sesión con SSH\PS y ejecute este comando para iniciar FTP:  

```
start ftpd.exe 
```

* Para ejecutar en cada arranque, los usuarios deben crear un inicio de sesión de tarea de Scheduler con SSH\PS y crear una tarea de programador:

```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD” 
```

### <a name="partition-size-requirements-for-update"></a>Requisitos de tamaño de partición para Update 
Asegúrese de que la partición de datos mantiene suficiente espacio para la funcionalidad de actualización.  Se recomienda 1 GB de disponibilidad para la funcionalidad de actualización completa.  Si la partición de datos no tiene espacio suficiente, se producirá un error en las actualizaciones durante la fase de instalación. 

### <a name="powershell-log-generation-on-iot-core"></a>Generación de registros de PowerShell en IoT Core 
PowerShell en IOT Core puede generar archivos de registro de forma predeterminada ocupando espacio en el sistema de archivos. Aunque los tamaños de los archivos de registro están limitados, pueden ocupar espacio, lo que puede dar lugar a una situación de poco espacio en disco que, entre otras cosas, pueden producir errores en las actualizaciones. Los archivos de registro de eventos. evtx tienen un tamaño máximo predefinido de 20 MB cada uno. Puede limitar los archivos de forma individual para que tengan un tamaño máximo diferente a través del registro. Por ejemplo, para mantener Security. evtx en un tamaño máximo de 10 MB: 
```
regd add HKLM\SYSTEM\CurrentControlSet\Services\EventLog\Security /v MaxSize /t REG_DWORD /d 0xa00000 /f 
```

### <a name="schtasks-limitation"></a>Limitación de SchTasks  
Schtasks no admite el uso del modificador/XML. Por ejemplo: 
```
schtasks /create /xml <xmlfile> /TN <taskname>
```
Se producirá un error en IoT Core. Al ejecutar el comando se generará el error: ERROR: no se encontró el procedimiento especificado. 
