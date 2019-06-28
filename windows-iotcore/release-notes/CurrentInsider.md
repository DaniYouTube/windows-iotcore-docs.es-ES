---
title: Notas de la versión de la compilación 17744
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/24/2018
ms.topic: article
description: Descubra las novedades del número de compilación 17744 de Windows Insider.
keywords: Windows IoT, Windows Insider, notas de la versión
ms.openlocfilehash: 3f78aa22f6edd4692d1e7956edc30856eeed2e7c
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "60170293"
---
# <a name="release-notes-for-build-17744"></a>Notas de la versión de la compilación 17744
_Número de compilación 17744. Agosto de 2018._

&copy; 2018 Microsoft Corporation. Todos los derechos reservados.

En este documento se proporciona la información más reciente y de otro tipo que complementa la documentación incluida con Windows 10 IoT Core.

Gracias por descargar Windows 10 IoT Core. Windows 10 IoT Core es la versión de Windows 10 destinada al desarrollo de dispositivos de uso insertado o dedicado, y es también la elección de la comunidad de fabricantes. Los paquetes de esta versión incluyen herramientas y contenido necesarios para instalar Windows 10 IoT Core en la plataforma MinnowBoard Max basada en procesadores Intel Atom, Raspberry Pi 2 o 3 basado en Broadcom 2836 o 2837 y DragonBoard 410c basado en procesadores de la serie Snapdragon 400 de Qualcomm.


## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar [aquí](http://go.microsoft.com/fwlink/?LinkId=506737).

Pegue el vínculo de redireccionamiento en la ventana del explorador para revisar los términos y condiciones vinculados.

## <a name="whats-new-in-this-build"></a>Novedades de esta compilación: 
* Correcciones de errores generales 


## <a name="additional-information"></a>Información adicional
* La versión 2118.0.0.0 de BSP es la usada para la imagen de DragonBoard. 


## <a name="known-issues-in-this-build"></a>Problemas conocidos de esta compilación:
* La implementación del controlador F5 de Visual Studio no funciona en IoT Core.
* Los dispositivos que se han instalado a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel. Esto se puede conseguir con la siguiente solución alternativa: ** Monte la tarjeta SD en el equipo. ** Busque el número de la partición de disco EFIESP con diskpart o Administración de discos (por ejemplo, "M:"). ** Ejecute el comando "bcdedit /store M:\EFI\Microsoft\boot\bcd /set {default} debug yes". ** Desmonte la tarjeta SD.
** Ya debería poder conectar el depurador de la forma habitual.
* En ocasiones, se interrumpirá la PSSession al enviar comandos a dispositivos IoT.
* RPi3 no empareja BT + BTLE con el Bluetooth incorporado.
* No se puede conectar a Internet a través de la conexión Wi-Fi con SoftAp de Up2.
* UWF produce errores de forma intermitente.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.


## <a name="iot-core-general-known-issues-and-work-arounds"></a>Problemas generales conocidos de IoT Core y soluciones

### <a name="for-raspberry-pi"></a>Para Raspberry Pi

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Resolución de pantalla de Raspberry Pi si se desconecta el monitor 
Puede que Raspberry Pi no mantenga la resolución de pantalla si se desconecta el monitor. El EDID del monitor se usa para establecer la resolución del sistema cuando hay uno conectado. Cuando se desconecta, el firmware de Raspberry Pi establece de forma predeterminada lo que está en config.txt en la raíz de la tarjeta SD. 

#### <a name="raspberry-pi-video-performance"></a>Rendimiento de vídeo de Raspberry Pi 
El rendimiento de la reproducción de vídeo en la plataforma de Raspberry Pi no está optimizado.  Es posible que el rendimiento que muestren los elementos animados del usuario, incluidos los menús desplegables basados en XAML, no sea el óptimo. 
 
#### <a name="raspberry-pi-camera-support"></a>Compatibilidad de Raspberry Pi con la cámara 
La compatibilidad con los dispositivos periféricos de cámara es limitada. El dispositivo PiCam conectado directamente al bus de la cámara incorporada no es compatible, ya que las limitaciones de la plataforma para admitir cámaras web USB modernas D3D generan flujos de datos muy exigentes en la controladora de host USB.  Incluso cuando se usa con cámaras web con valores de resolución bajos, se requerirá un ajuste preciso adicional y una lógica de control especializada del USB. 

#### <a name="raspberry-pi3-bluetooth-support"></a>Compatibilidad de Raspberry Pi3 con Bluetooth 
El controlador Bluetooth integrado de Raspberry Pi3 solo admite dispositivos con un ancho de banda bajo. 

#### <a name="serial-port-usage-and-access-on-rpi2"></a>Uso y acceso de los puertos serie en RPi2 
Raspberry Pi 2 es compatible con el transporte en serie para la comunicación a través de UART PL011.  Esto se establece de manera predeterminada en escenarios de depuración del kernel.  Un controlador de dispositivo o de aplicación puede usar UART PL011 para enviar y recibir datos con el controlador de dispositivo PL011 si se desactiva el depurador mediante el comando siguiente:

```
bcdedit /set debug off 
```

#### <a name="data-breakpoints-have-been-disabled-on-the-raspberry-pi2"></a>Se han deshabilitado los puntos de interrupción de datos en Raspberry Pi2
Por el momento no hay ninguna solución al respecto.

#### <a name="disabling-the-onboard-adapters-for-raspberry-pi-3"></a>Deshabilitación de los adaptadores incorporados para Raspberry Pi3
Raspberry Pi3 tiene Bluetooth incorporado, que se debe deshabilitar para usar una llave diferente. Para deshabilitar el Bluetooth incorporado, abra una sesión de telnet o ssh y ejecute lo siguiente: 
```
reg add hklm\system\controlset001\services\BtwSerialH5Bus /v Start /t REG_DWORD /d 4 
```

Puede deshabilitar la Wi-Fi con el siguiente comando: 
```
reg add hklm\system\controlset001\services\bcmsdh43xx /v Start /t REG_DWORD /d 4 
``` 

### <a name="for-dragonboard"></a>Para DragonBoard

#### <a name="dragonboard-410c-shutdown"></a>Apagado de DragonBoard 410c
En DragonBoard, la placa no se apagará con un comando de apagado. El sistema se reiniciará. Para apagar la placa, desconecte la alimentación.

#### <a name="dragonboard-and-windbg"></a>DragonBoard y windbg
Los controladores GPIO/I2C/SPI/UART se deshabilitarán al conectarse a DragonBoard con windbg.

#### <a name="dragonboard-headset--microphone-jack"></a>Conector de auriculares y micrófono de DragonBoard
El BSP de Dragonboard tiene controladores para el conector de auriculares y de micrófono, pero no tiene estos conectores en la placa.  

#### <a name="dragonboard-spi-runs-at-48mhz"></a>El SPI de DragonBoard se ejecuta a 4,8 Mhz
El SPI de DragonBoard omitirá la velocidad solicitada y siempre se ejecutará a 4,8 Mhz.  

#### <a name="dragonboard-connected-standby"></a>Modo de espera conectado de DragonBoard 
El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.  Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del Registro debe establecerse en "1":

```
HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1 
```

> [!NOTE]
> No todas las plataformas admiten el modo de espera conectado.  Esto podría no funcionar en todas las plataformas.    


### <a name="for-minnowboard"></a>Para MinnowBoard
#### <a name="minnowboard-max-boot-and-firmware-update"></a>Arranque de MinnowBoard Max y actualización de firmware 
MinnowBoard Max no arrancará a menos que la versión del firmware sea .092 o posterior. La versión mínima recomendada del firmware es "MinnowBoard Max 0.92 de 32 bits". Las actualizaciones de firmware pueden descargarse desde [aquí](http://go.microsoft.com/fwlink/?LinkId=708613).

#### <a name="minnow-board-peripheral-support"></a>Compatibilidad con los periféricos de MinnowBoard
La imagen de Windows 10 IoT Core incluida en esta lista es compatible con los periféricos que se exponen en la placa MinnowBoard Max. Posteriormente, Intel&reg; proporcionará soporte técnico del conjunto completo de características de los procesadores Baytrail, incluidos los procesadores Intel Celeron&trade; J1900/N2930/N2807 e Intel Atom&trade; E38XX.


### <a name="for-all-platforms"></a>Para todas las plataformas 

#### <a name="mouse-pointer-disappears-while-debugging"></a>El puntero del mouse desaparece durante la depuración 
En algunos casos, el puntero del mouse no es visible después de implementar o depurar aplicaciones con Visual Studio. El puntero del mouse debe reaparecer si cambia el foco con el teclado (Tabulador).


#### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP
Cuando se usa SoftAP, los clientes no podrán acceder al contenido que exponen las aplicaciones UAP.  
Para exponer las aplicaciones UAP a través de SoftAP, deben realizarse los cambios siguientes desde la consola en el dispositivo:  

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


#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Conflicto del controlador de sensor en FFU precompiladas 
Hay un conflicto del controlador de sensor en las FFU proporcionadas. El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio. Las API de UWP que proporcionan acceso a estos controladores desde una aplicación suponen que solo hay uno instalado. Si está desarrollando un controlador para un dispositivo adjuntado físicamente, el controlador remoto de las FFU que proporciona Microsoft entrará en conflicto.

Solución: se puede quitar el controlador que causa el conflicto mediante la conexión al dispositivo a través de SSH o Powershell, y mediante el uso de la herramienta devcon.exe para quitar el controlador de sensor remoto (escriba "devcon.exe remove @”ROOT\REMOTESENSORDRIVER*"). El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original.


#### <a name="default-administrator-user-name-and-password"></a>Nombre de usuario y contraseña predeterminados del administrador
El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña.

#### <a name="volume-controls"></a>Controles de volumen
Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core. 

#### <a name="usb-keyboards"></a>Teclados USB  
Es posible que algún teclado y mouse USB no funcionen en IoT Core. Use otro teclado o mouse. Encontrará una lista de dispositivos periféricos validados en [esta documentación](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/hardwarecompatlist).


#### <a name="screen-orientation"></a>Orientación de la pantalla
El establecimiento de la orientación en "Vertical" puede que no se respete en una aplicación universal.

#### <a name="referencing-adapters-with-alljoyn-templates"></a>Adaptadores de referencia con plantillas de AllJoyn
El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.  Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, luego, vuelva a cargar el proyecto.

#### <a name="wifi-direct-limitations-on-iotcore"></a>Limitaciones de Wi-Fi Direct en IoTCore
* El dispositivo IoTCore debe ser el dispositivo que se conecta. No funcionará como dispositivo de publicidad con otro dispositivo que inicie la conexión.   
* Debe usarse el emparejamiento avanzado.  La aplicación de ejemplo muestra cómo usar la API de emparejamiento avanzada para emparejar los dispositivos antes de conectar. 
* No todos los adaptadores inalámbricos son compatibles con Wi-Fi Direct. Hemos probado y validado el funcionamiento del "adaptador de red Realtek RTL8188EU Wireless Lan 802.11n USB 2.0", pero puede que otros adaptadores no sean compatibles. 


#### <a name="non-default-drive-mode"></a>Modo de unidad no predeterminado
En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO. Solución alternativa: establezca el modo de la unidad una vez al comienzo de la aplicación.

#### <a name="application-already-running"></a>Aplicación en ejecución
La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio. Solución alternativa: cambie la aplicación de inicio predeterminada a otra aplicación distinta de la que quiere implementar. 

#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>Puede que se bloquee la línea de código BackgroundMediaPlayer.MessageReceivedFromForeground
La línea de código siguiente podría bloquearse: "BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;". Para evitar el bloqueo, agregue este código para que se ejecute primero: "var player = BackgroundMediaPlayer.Current;". 

#### <a name="azure-active-directory-authentication-support"></a>Compatibilidad con la autenticación de Azure Active Directory
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  

#### <a name="shell-management-of-application-crashes"></a>Administración del shell de los bloqueos de la aplicación
La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.  Si los bloqueos continúan en las aplicaciones reiniciadas, el shell empleará un __failfast, es decir, un proceso crítico del sistema que provoca una comprobación de errores y un reinicio en un intento de recuperación.  Se usan una lógica y un control comparables para las tareas en segundo plano y las aplicaciones de primer plano en una configuración con cabezal.   A continuación se muestra la lógica de reintento y el control de bloqueo:

```
Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (or ForegroundAppConfig for headed) 
Qword:"FailureResetIntervalMs" – length of time app has to run successfully to reset failures seen to 0. – default is 0x00000000000493E0 == 5 minutes 
Qword:"BaseRetryDelayMs"  -- wait time coefficient.  Default is 0xa. 
Dword:"MaxFailureCount". Default is 10 
DWord:"FallbackExponentNumerator", default is 31. 
Dword:"FallbackExponentDenominator", default is 20 
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator; // default is 1.55 
```

Cuando se detecta un bloqueo de la aplicación: 

```
if time_since_last_crash > failureresetinterval then crashes_seen = 1 

else ++crashes_seen; 

if crashes_seen > MaxFailureCount then __failfast; 

else  

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent)) 
```

Espere el retraso y reinicie la aplicación. 


#### <a name="time-synchronization"></a>Sincronización de la hora  
Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales. 

1) Desde una línea de comandos en el dispositivo (por ejemplo, SSH, Powershell): w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 

2) También puede realizar estas adiciones en el Registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado, incluido como parte del proceso de creación de imagen, si es necesario. Para obtener más información, vea: 

* [Adición de un archivo y configuración del Registro en una imagen](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)


### <a name="starting-the-ftp-server"></a>Inicio del servidor FTP 
El servidor FTP ya no se ejecuta de manera predeterminada al inicio. 

Para ejecutarlo una vez: Inicie sesión con SSH o PS, y ejecute este comando para iniciar el FTP:  
```
start ftpd.exe 
```

Para ejecutarlo en todos los arranques, los usuarios deben crear una tarea de programador: Inicie sesión con SSH o PS, y cree una tarea de programador: 
```
schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
Schtasks /run /tn “IoTFTPD”
```
