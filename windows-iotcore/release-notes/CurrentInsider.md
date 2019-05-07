---
title: Notas de la versión de compilación 17744
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/24/2018
ms.topic: article
description: Lea y obtenga información acerca de cuáles son las novedades en 17744 de número de compilación de Insider de Windows.
keywords: notas de la versión de Windows iot, Windows Insider,
ms.openlocfilehash: 3f78aa22f6edd4692d1e7956edc30856eeed2e7c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514492"
---
# <a name="release-notes-for-build-17744"></a>Notas de la versión de compilación 17744
_17744 del número de compilación. Agosto de 2018._

&copy; 2018 Microsoft Corporation. Todos los derechos reservados.

Este documento proporciona información de última hora o de otro que complementa la documentación incluida con el de Windows 10 IoT Core.

Gracias por descargar Windows 10 IoT Core. Windows 10 IoT Core es la versión de Windows 10 dirigida al desarrollo de dispositivos incrustados o dedicado de propósito y la elección de la Comunidad de creadores de. Los paquetes dentro de esta versión contienen herramientas y el contenido necesario para instalar Windows 10 IoT Core en plataforma de Minnowboard Max basada en procesadores Intel Atom, Raspberry Pi 2 o 3 según Broadcom 2836/2837 y Dragonboard 410c en función de la serie 400 de Qualcomm Snapdragon procesadores.


## <a name="privacy-statement"></a>Declaración de privacidad en línea

Se puede ver la declaración de privacidad para esta versión del sistema operativo Windows [aquí](http://go.microsoft.com/fwlink/?LinkId=506737).

Puede revisar los términos vinculados si pega el vínculo hacia delante en la ventana del explorador.

## <a name="whats-new-in-this-build"></a>Novedades en esta compilación: 
* Correcciones de errores generales 


## <a name="additional-information"></a>Información adicional
* La versión BSP usada para nuestra imagen Dragon Board es 2118.0.0.0. 


## <a name="known-issues-in-this-build"></a>Problemas conocidos de esta compilación:
* Implementación de controladores de F5 desde Visual Studio no funciona en IoT Core.
* Los dispositivos que se instalaron a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel. Esto puede lograrse con la siguiente solución alternativa: ** montar la tarjeta SD en su PC ** encontrar la partición de disco EFIESP número con diskpart o administración de discos (por ejemplo, "M:") ** ejecute el comando "bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug Sí" **  Desmonte la tarjeta SD.
** Ya debería poder conectar el depurador como de costumbre
* En ocasiones, se interrumpirá la PSSession al enviar comandos a dispositivos IoT.
* RPi3 no asócielo BT + BTLE con Bluetooth incorporar.
* No se puede conectar a internet a través de la conexión Wi-Fi con SoftAp de Up2.
* Error intermitente UWF.
* El cliente de Windows IoT remoto no funciona para Raspberry Pi. Usar un panel con gráficos acelerados como Minnowboard Max o Dragonboard o adjuntar a un monitor para visualización local.


## <a name="iot-core-general-known-issues-and-work-arounds"></a>Problemas conocidos de IoT Core generales y soluciones

### <a name="for-raspberry-pi"></a>Para Raspberry Pi

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Resolución de pantalla de raspberry Pi si se desconecta el monitor 
Raspberry Pi no puede mantener la resolución de pantalla si se desconecta el monitor. El EDID del monitor se usa para establecer la resolución del sistema cuando uno está conectado. Cuando se desconecta, el firmware del dispositivo Raspberry Pi predeterminado es lo que está en el config.txt en la raíz de la tarjeta SD. 

#### <a name="raspberry-pi-video-performance"></a>Rendimiento de vídeo de raspberry Pi 
No se optimiza el rendimiento de reproducción de vídeo en la plataforma de Raspberry Pi.  Anima el usuario pueden presentar elementos, como menús desplegables basada en XAML de menos de un rendimiento óptimo. 
 
#### <a name="raspberry-pi-camera-support"></a>Compatibilidad con la cámara raspberry Pi 
Compatibilidad con dispositivos periféricos de cámara es limitada. No se admite el dispositivo PiCam directamente conectado al bus de cámara integrada debido a limitaciones en la plataforma para admitir USB modernas D3D cámaras Web generan los flujos de datos que son muy exigentes en el controlador Host USB.  Incluso cuando se usa con cámaras Web de configuración de baja resolución requerirá adicionales USB ajustar y especializada la lógica de control. 

#### <a name="raspberry-pi3-bluetooth-support"></a>Soporte de raspberry Pi3 Bluetooth 
El controlador Bluetooth integrado que Raspberry Pi3 solo admite dispositivos de bajo ancho de banda. 

#### <a name="serial-port-usage-and-access-on-rpi2"></a>Uso de los puertos serie y el acceso en RPi2 
Raspberry Pi 2 es compatible con el transporte de serie para la comunicación a través de UART PL011.  Esto se establece de forma predeterminada en escenarios de depuración del kernel.  Un controlador de dispositivo o aplicación puede usar el UART PL011 para enviar y recibir datos con el controlador de dispositivo PL011 si se desactiva el depurador mediante el siguiente comando:

```
bcdedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a>Se han deshabilitado los puntos de interrupción de datos en el Pi2 Raspberry
Ninguna solución alternativa en este momento.

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a>Deshabilitar a los adaptadores integrados para Raspberry Pi 3
Raspberry Pi 3 tiene incorporar Bluetooth que debe deshabilitarse para usar un dispositivo diferente para deshabilitar para incorporar Bluetooth, abra una sesión de telnet y ssh y ejecute: 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

Puede deshabilitar Wi-Fi con el siguiente comando: 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragonboard"></a>Para DragonBoard

#### <a name="dragonboard-410c-shutdown"></a>Apagado Dragonboard 410c
En el DragonBoard, un comando de apagado no se apague la placa. El sistema se reiniciará. Inicie la alimentación del tablero al desconectar la alimentación.

#### <a name="dragonboard-and-windbg"></a>DragonBoard y windbg
Los controladores GPIO/I2C/SPI/UART se deshabilitarán cuando se conecta a la DragonBoard con windbg.

#### <a name="dragonboard-headset--microphone-jack"></a>Jack de auriculares & micrófono DragonBoard
El BSP Dragonboard tiene controladores para el enchufe para auriculares y del micrófono, pero no tiene cualquiera de estos conectores a bordo.  

#### <a name="dragonboard-spi-runs-at-48mhz"></a>DragonBoard SPI se ejecuta en 4,8 Mhz
El SPI en el Dragonboard omitirá la velocidad solicitada y siempre se ejecutan con 4,8 Mhz.  

#### <a name="dragonboard-connected-standby"></a>DragonBoard conectado en espera 
Modo de espera conectado no está habilitado en el Qualcomm Dragonboard de forma predeterminada.  Para habilitar el modo de espera conectado en DragonBoard la siguiente clave del registro debe establecerse en "1":

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> No todas las plataformas tienen compatibilidad para el modo de espera conectado.  Esto podría no funcionar en todas las plataformas.    


### <a name="for-minnowboard"></a>Para MinnowBoard
#### <a name="minnowboard-max-boot-and-firmware-update"></a>Arranque de Max Minnowboard y actualización de Firmware 
El número máximo de MinnowBoard no arrancará a menos que el firmware versión.092 o posterior. La versión mínima recomendada del firmware es "MinnowBoard MAX 0,92 32 bits". Las actualizaciones de firmware pueden descargarse desde [aquí](http://go.microsoft.com/fwlink/?LinkId=708613).

#### <a name="minnow-board-peripheral-support"></a>Compatibilidad con periférico de la placa minnow
La imagen de Windows 10 IoT Core incluida en esta lista es compatible con los periféricos que se exponen en el panel MinnowBoard MAX. Posteriormente, Intel&reg; les ofrecerá soporte técnico del conjunto completo de características de los procesadores Baytrail incluyendo el Celeron de Intel&trade; procesadores J1900/N2930/N2807 y Intel Atom&trade; E38XX procesadores.


### <a name="for-all-platforms"></a>Para todas las plataformas 

#### <a name="mouse-pointer-disappears-while-debugging"></a>Puntero del mouse desaparece durante la depuración 
En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe reaparecer si cambia el foco mediante el teclado (pestaña).


#### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP
Cuando se usa el SoftAP los clientes no podrán tener acceso al contenido expuesto por aplicaciones UAP.  
Para exponer las aplicaciones a través de SoftAP UAP se deben realizar los cambios siguientes desde la consola en el dispositivo:  

```
reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 
checknetisolation loopbackexempt -a -n=<AppID for SoftAP App> 
checknetisolation loopbackexempt -a -n=<AppID for Additional App>  
```

Por ejemplo:  
```
checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym
```
Reiniciar 


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Conflicto del controlador de sensor en FFUs precompiladas 
Hay un conflicto del controlador del Sensor en el FFUs proporcionados. El marco de Sensor remoto instala a controladores para Compass, Magnetómetro, acelerómetro y giro. Las API de UWP para tener acceso a ellos desde una aplicación supone simplemente 1 está instalado. Si está desarrollando un controlador para un dispositivo físicamente conectado, el controlador remoto de Microsoft proporciona que ffus entrará en conflicto.

Solución: Se puede quitar el controlador en conflicto mediante la conexión al dispositivo a través de SSH o Powershell y usar la herramienta devcon.exe para quitar el controlador de sensor remoto escribiendo "quitar devcon.exe @" ROOT\REMOTESENSORDRIVER *". El controlador de sensor remoto no afecta a los OEM creado FFUs.


#### <a name="default-administrator-user-name-and-password"></a>Contraseña y nombre de usuario de administrador predeterminado
El nombre de usuario de administrador predeterminado y la contraseña son difíciles de codificada en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a internet abierto hasta que se cambió la contraseña.

#### <a name="volume-controls"></a>Controles de volumen
Controles de volumen de hardware para micrófonos USB y altavoces que dependen del sistema de Windows para cambiar el volumen del sistema no se admiten en Windows 10 IoT Core. 

#### <a name="usb-keyboards"></a>Teclados USB  
Algunos teclados y ratones USB no funcionen en IoT Core. Usar un teclado o mouse. Encontrará una lista de dispositivos periféricos validados en el [documentación aquí](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist).


#### <a name="screen-orientation"></a>Orientación de pantalla
Establecer la orientación a "Vertical" no se respeta en una aplicación Universal.

#### <a name="referencing-adapters-with-alljoyn-templates"></a>Hacer referencia a los adaptadores con plantillas de AllJoyn
Al intentar agregar referencias a proyectos de adaptador AllJoyn puede producirse errores al usar las versiones específicas del SDK.  Para resolver estos errores, cambiar la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y vuelva a cargar el proyecto.

#### <a name="wifi-direct-limitations-on-iotcore"></a>Limitaciones de Wi-Fi Direct en IoTCore
* El dispositivo IoTCore debe ser el dispositivo que se conecta, no funcionará como dispositivo de publicidad con otro dispositivo inicia la conexión.   
* Debe usarse el emparejamiento avanzadas.  La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de conectar. 
* No todos los adaptadores inalámbricos admiten Wi-Fi direct. Hemos probado y comprobado que la "red USB 2.0 de Realtek RTL8188EU Wireless Lan 802. 11n adaptador" funciona, pero otros adaptadores no se admite. 


#### <a name="non-default-drive-mode"></a>Modo de unidad no predeterminada
En Raspberry Pi y Dragonboard, al cambiar de un modo de unidad no predeterminada a un modo de unidad no predeterminada diferente, puede producir un problema en la clavija GPIO. Solución alternativa: Establecer el modo de la unidad una vez al principio de la aplicación.

#### <a name="application-already-running"></a>Aplicación ya está ejecutando
La aplicación de inicio predeterminada podría entrar en conflicto con sí mismo cuando también se implementa desde Visual Studio. Solución alternativa: Cambiar la aplicación de inicio predeterminada para una aplicación que distinta de la que desea implementar. 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>Se puede bloquear BackgroundMediaPlayer.MessageReceivedFromForeground
Se puede bloquear la siguiente línea de código: "BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;". Para evitar el bloqueo, agregue este código para que se ejecute primero "Reproductor de var = BackgroundMediaPlayer.Current;" 

#### <a name="azure-active-directory-authentication-support"></a>Compatibilidad con la autenticación de Azure Active Directory
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  

#### <a name="shell-management-of-application-crashes"></a>Shell de administración de bloqueos de la aplicación
Infraestructura de IoT Core shell supervisa aplicaciones APPX-type que se ejecutan en el dispositivo de bloqueos y reinicia esas aplicaciones cuando se producen bloqueos.  Si las aplicaciones reiniciadas continúan se bloquee, el shell se emplean un __failfast: un proceso crítico de sistema que provoca una comprobación de errores y reinicie en un intento de recuperar.  Control y comparable lógica se utiliza para aplicaciones de primer plano en una configuración con cabezal y tareas en segundo plano.   A continuación, se captura lógica de reintento y entrega de bloqueo:

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

Cuando se detecta el bloqueo de aplicación: 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

Espera para retraso y vuelva a iniciar la aplicación 


#### <a name="time-synchronization"></a>Sincronización de hora  
Si se producen errores en sincronización de hora o tiempo de espera de esto puede deberse a inaccesible o un servidor distante del tiempo, la siguiente puede hacerse para agregar servidores de hora local o adicionales. 

1) Desde una línea de comandos en el dispositivo (p ej. SSH, Powershell) w32tm /config/syncfromflags: manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2. otra cosa,..." 

2) También puede hacer estas adiciones en el registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado incluido como parte del proceso de creación de imagen si es necesario. Para obtener más información, consulte: 

* [Agregar un archivo y la configuración del registro a una imagen](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)


### <a name="starting-the-ftp-server"></a>Iniciar el servidor FTP 
El servidor FTP ya no se ejecuta de forma predeterminada al inicio 

Para ejecutar una vez: Inicio de sesión con SSH\PS y ejecute este comando para iniciar FTP:  
```
start ftpd.exe 
```

Para ejecutar en todos los usuarios de arranque, debe crear un programador de tareas: Inicio de sesión con SSH\PS y crear un programador de tareas: 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```