---
title: Creators Update - compilación 15063
author: zeeshanfurqan
ms.author: zeeshanf
ms.date: 08/28/2017
ms.topic: article
description: Lea y obtenga información acerca de cuáles son las novedades de Creators Update.
keywords: notas de la versión de Windows iot, Creators Update,
ms.openlocfilehash: 73be3f48ce1051d98aa9ebce06dbdc4682fff0fa
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514864"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Creadores de actualización las notas de la versión para Windows 10 IoT Core
15063 del número de compilación. Abril de 2017

Windows 10 IoT Core permite el desarrollo de dispositivos incrustados o dedicado de propósito y es la opción para los OEM y los desarrolladores que crean soluciones de Windows para los dispositivos pequeños.

Este documento proporciona información que complementa otros contenido y la documentación de esta versión de Windows 10 IoT Core.

Los paquetes dentro de esta versión contienen herramientas y componentes necesarios para instalar Windows 10 IoT Core en plataforma de Minnowboard Max basada en procesadores Intel Atom, basado en ARM Cortex A7 y Dragonboard c de 410 en función de la serie 400 de Qualcomm Snapdragon Raspberry Pi 2 procesadores.   

[Otras plataformas y procesadores](../../learn-about-hardware/SoCsAndCustomBoards.md) pueden estar disponibles de socios.

## <a name="privacy-statement"></a>Declaración de privacidad en línea

Se puede ver la declaración de privacidad para esta versión del sistema operativo Windows [aquí](http://go.microsoft.com/fwlink/?LinkId=506737).

## <a name="whats-new"></a>Novedades
* Versión pública de Windows 10 IoT Core. 
   * Compatibilidad de administración de dispositivos Azure - los OEM pueden usar la biblioteca de cliente de DM de Azure IoT de Windows para agregar capacidades de administración de dispositivos para sus dispositivos conectado del centro de IoT de Azure.
   * Soporte técnico de silicio adicionales
      * Comprobar la compatibilidad con Windows 10 IoT Core en julio de Intel, Intel Pentium N4200, Celeron N3350 de Intel, próximos Atom x5 E39xx los procesadores (anteriormente Lake Apollo) y SOM de Raspberry Pi 3.
      * Allwinner ha habilitado la compatibilidad para sus dispositivos de 64 pino y plátano Pi mediante el A64 de Allwinner Soc. 
   * Detectar los dispositivos remotos - ningún software especial es necesario para detectar los dispositivos que ha iniciado sesión con su Account de Microsoft.
   * Nuevos controles de las API de UWP y de vibración, brillo, modo de espera conectado moderna, administración de energía, batería y NFC (sin HCE). 
   * Buses nuevos y capacidades para ARM PCIe, modo de función USB, Wi-Fi Direct y API de recuento de interrupción GPIO. 
   * Nuevas características de incrustada en el restablecimiento y recuperación, en el SOC PWM y aprovisionamiento automático de USB 
   * Herramientas - VS Code, nuevo panel de IoT y Windows Device Portal características mejoradas, compatible con VS 2017.
   * Cortana en Windows IoT Core - Cortana ahora está disponible en Windows 10 IoT Core. Formule una pregunta de Cortana.
   * Mejoras de panel de IoT: nuevas características y correcciones de errores de estabilidad
      * Versiones de Windows Insider Preview para Raspberry Pi y Minnowboard 
      * Dispositivo que se conecta mediante el cliente remoto de Windows IoT 
      * Direcciones IPv6 de detección de dispositivos 
      * Cargar registros de dispositivo durante el envío de comentarios
   *  Interrupciones de alta precisión nuevas API GPIO: nuevas API (Windows.Devices.Gpio.GpioInterruptBuffer) para una medida precisa y eficiente de anchos de impulso mediante GPIO.  Proveedores GPIO incluyen la nueva interfaz del búfer de interrupción para permitir la interrupción de alta precisión para las aplicaciones, como los codificadores rotatorios y dispositivos de medición de distancia de control de tiempo
   * Device Guard para IoT - dispositivo generadores ahora pueden bloquear totalmente el detalle de los dispositivos de IoT y obtenga malware protección contra malware nuevos y desconocidos variantes avanzada.  Esto puede hacerse mediante la especificación de entidades de certificación de firmas de aplicaciones permitidas y los controladores que se ejecutan en el dispositivo al no permitir la ejecución de código desconocido o no.  Esto significa mejorar la seguridad frente a malware y cero ataques de día. 
   * Otras actualizaciones incluyen: 
      * Compatibilidad mejorada de actualización 
      * Compatibilidad con SDK de puerta de enlace de Azure 
      * Unidad USB en función de aprovisionamiento automático 
      * Rediseño del Portal de dispositivo 
      * imágenes de 64 bits ahora admite hasta 16 384 MB de memoria 
      * API de vibración de WinRT 
      * Compatibilidad de lenguaje mejorada 
   * Varios  
      * Se ha realizado un cambio a la configuración de BCD predeterminada para impedir que los dispositivos intenta arrancar en modo de recuperación cuando el modo de recuperación no existe. 
      * Característica IOT_POWER_SETTINGS ahora incluye powercfg.exe. Esto está disponible para todas las arquitecturas (ARM32, x86 y x64). 
      * Cambios realizados en Applyupdate.exe para agregar las marcas de blockrebooton/blockrebootoff 
      * Las extensiones de clase de notificación de Hardware (hwnclx) y la función de USB (usbfnclx) se han agregado en el valor predeterminado imágenes IoT Core

## <a name="known-issues"></a>Problemas conocidos

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Resolución de pantalla de raspberry Pi si se desconecta el monitor 
Raspberry Pi no puede mantener la resolución de pantalla si se desconecta el monitor. El EDID del monitor se usa para establecer la resolución del sistema cuando uno está conectado.  
Cuando se desconecta, el firmware del dispositivo Raspberry Pi predeterminado es lo que está en el config.txt en la raíz de la tarjeta SD. 

#### <a name="raspberry-pi-video-performance"></a>Rendimiento de vídeo de raspberry Pi 
No se ha optimizado el rendimiento de reproducción de vídeo en la plataforma de Raspberry Pi.  Anima el usuario pueden presentar elementos, como menús desplegables basada en XAML de menos de un rendimiento óptimo. 

#### <a name="raspberry-pi-camera-support"></a>Compatibilidad con la cámara raspberry Pi 
Compatibilidad con Windows 10 IoT Core dispositivos periféricos de cámara con dispositivos Raspberry Pi es limitada. El dispositivo PiCam directamente conectado al bus de cámara integrada no es compatible actualmente, ya que requiere servicios GPU que no están actualmente disponibles en Raspberry Pi, dado que no se implementa el controlador de DirectX. Cámaras Web USB modernos genera secuencias de datos que son muy exigentes en el controlador Host USB.  Incluso cuando se usa con cámaras Web de configuración de baja resolución requerirá adicionales USB ajustar y especializada la lógica de control.  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Soporte de raspberry Pi 3 Bluetooth 
El controlador Bluetooth de Raspberry Pi3 integrado solo es compatible con dispositivos de bajo ancho de banda  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Uso de los puertos serie y el acceso en Raspberry Pi 2 
Raspberry Pi 2 es compatible con el transporte de serie para la comunicación a través de UART PL011.  Esto se establece de forma predeterminada en escenarios de depuración del kernel.  Un controlador de dispositivo o aplicación puede usar el UART PL011 para enviar y recibir datos con el controlador de dispositivo PL011 si se desactiva el depurador mediante el siguiente comando:   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>Dragon Board 

#### <a name="dragonboard-410c-shutdown"></a>Apagado Dragonboard 410c 
En el DragonBoard, un comando de apagado no se apague la placa. El sistema se reiniciará. Inicie la alimentación del tablero al desconectar la alimentación. 

#### <a name="dragon-board-headset--microphone-jack"></a>Jack de auriculares & micrófono Dragon Board  
El BSP Dragonboard tiene controladores para el enchufe para auriculares y del micrófono, pero no tiene cualquiera de estos conectores a bordo.  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>Dragonboard SPI se ejecuta a la velocidad de bloqueo  
El SPI en el Dragonboard omitirá la velocidad solicitada y siempre se ejecutan con una velocidad preconfigurada.  

#### <a name="dragonboard-connected-standby"></a>Dragonboard conectado en espera 
Modo de espera conectado no está habilitado en el Qualcomm Dragonboard de forma predeterminada.  Para habilitar el modo de espera conectado en DragonBoard la siguiente clave del registro debe establecerse en "1" 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
Tenga en cuenta que no todas las plataformas tienen compatibilidad para CS, por lo que esto podría no funcionar en otras plataformas.    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>Vibración API podría no funcionar en algunas plataformas Qualcomm 
La solución recomendada consiste en agregar la clave del registro siguiente: 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
Confirmación / comprobación en una imagen existente conectarse con SSH o PowerShell y ejecute el siguiente comando: 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Actualización de Firmware Minnowboard máx. 
El número máximo de MinnowBoard no arrancará a menos que el firmware versión.092 o posterior.  
Puede haber errores de conectividad de red en MinnowBoard Max (MBM) versión de firmware 0,93.   El problema está corregido en la versión de firmware 0,94.)  La versión mínima recomendada del firmware es "MinnowBoard MAX 0,94 32 bits". Las actualizaciones de firmware pueden descargarse desde [aquí](http://go.microsoft.com/fwlink/?LinkId=708613).
  
 
### <a name="all-platforms"></a>Todas las plataformas 

#### <a name="mouse-pointer-disappears-while-debugging"></a>Puntero del mouse desaparece durante la depuración 
En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe reaparecer si cambia el foco mediante el teclado (ficha)  

#### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP  
Cuando se usa el SoftAP los clientes no podrán tener acceso al contenido expuesto por aplicaciones UAP.  
Para exponer las aplicaciones a través de SoftAP UAP se deben realizar los cambios siguientes desde la consola en el dispositivo:  
<br>
`reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1 `
<br>
`checknetisolation loopbackexempt -a -n=<AppID for SoftAP App>`
<br>
`checknetisolation loopbackexempt -a -n=<AppID for Additional App> `
<br>
`For example:  checknetisolation loopbackexempt -a -n=IoTOnboardingTask-uwp_1w720vyc4ccym`
<br>
`Reboot`

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Conflicto del controlador de sensor en FFUs precompiladas 
Hay un conflicto del controlador del Sensor en el FFUs proporcionados. El marco de Sensor remoto instala a controladores para Compass, Magnetómetro, acelerómetro y giro. Las API de UWP para tener acceso a ellos desde una aplicación supone simplemente 1 está instalado. Si está desarrollando un controlador para un dispositivo físicamente conectado, el controlador remoto de Microsoft proporciona que ffus entrará en conflicto.  
Solución: Se puede quitar el controlador en conflicto mediante la conexión al dispositivo a través de SSH o PowerShell y usar la herramienta devcon.exe para quitar el controlador de sensor remoto escribiendo "quitar devcon.exe @" ROOT\REMOTESENSORDRIVER *". El controlador de sensor remoto no afecta a los OEM creado FFUs. 
 
#### <a name="default-administrator-user-name-and-password"></a>Contraseña y nombre de usuario de administrador predeterminado 
El nombre de usuario de administrador predeterminado y la contraseña son difíciles de codificada en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a internet abierto hasta que se cambió la contraseña. 
 
#### <a name="volume-controls"></a>Controles de volumen 
Controles de volumen de hardware para micrófonos USB y altavoces que dependen del sistema de Windows para cambiar el volumen del sistema no se admiten en Windows 10 IoT Core. 
 
#### <a name="usb-keyboards"></a>Teclados USB  
Algunos teclados y ratones USB no funcionen en IoT Core. Usar un teclado o mouse. Puede encontrar una lista de dispositivos periféricos validados [aquí](../../learn-about-hardware/HardwareCompatList.md).  
 
#### <a name="screen-orientation"></a>Orientación de pantalla 
Establecer la orientación a "Vertical" no puede cumplirse en una aplicación Universal 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>Hacer referencia a los adaptadores con plantillas de AllJoyn 
Al intentar agregar referencias a proyectos de adaptador AllJoyn puede producirse errores al usar las versiones específicas del SDK.  Para resolver estos errores, cambiar la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y vuelva a cargar el proyecto. 

#### <a name="non-default-drive-mode"></a>Modo de unidad no predeterminada  
En Raspberry Pi y Dragonboard, al cambiar de un modo de unidad no predeterminada a un modo de unidad no predeterminada diferente, puede producir un problema en la clavija GPIO. Solución alternativa: Establecer el modo de la unidad una vez al principio de la aplicación. 
 
#### <a name="application-already-running"></a>Aplicación ya está ejecutando  
La aplicación de inicio predeterminada podría entrar en conflicto con sí mismo cuando también se implementa desde Visual Studio. Solución alternativa: Cambiar la aplicación de inicio predeterminada para una aplicación que distinta de la que desea implementar. 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>Se puede bloquear BackgroundMediaPlayer.MessageReceivedFromForeground  
La siguiente línea de código puede bloquearse: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.
<br>
Para evitar el bloqueo, agregue este código para que se ejecute en primer lugar `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Compatibilidad con la autenticación de Azure Active Directory  
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  
 
#### <a name="shell-management-of-application-crashes"></a>Shell de administración de bloqueos de la aplicación 
Infraestructura de IoT Core shell supervisa aplicaciones APPX-type que se ejecutan en el dispositivo de bloqueos y reinicia esas aplicaciones cuando se producen bloqueos.  Si las aplicaciones reiniciadas continúan se bloquee, el shell se emplean un __failfast: un proceso crítico de sistema que provoca una comprobación de errores y reinicie en un intento de recuperar.  Control y comparable lógica se utiliza para aplicaciones de primer plano en una configuración con cabezal y tareas en segundo plano.   

A continuación, se captura lógica de reintento y entrega de bloqueo: 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig (o ForegroundAppConfig para puntas) 
* QWORD: "FailureResetIntervalMs": longitud de la aplicación de tiempo debe ejecutarse correctamente para restablecer los errores que se ven en 0. : valor predeterminado es 0x00000000000493E0 == 5 minutos. 
* QWORD: "BaseRetryDelayMs"--coeficiente de tiempo de espera.  El valor predeterminado es 0xa.
* DWORD: "MaxFailureCount". Valor predeterminado es 10.
* DWord: "FallbackExponentNumerator", el valor predeterminado es 31.
* DWORD: "FallbackExponentDenominator", el valor predeterminado es 20.
 
```C#
Fallback_exponent = FallbackExponentNumerator / FallbackExponentDenominator;
// default is 1.55
When app crash is detected:
    if time_since_last_crash > failureresetinterval then crashes_seen = 1
    else ++crashes_seen;

if crashes_seen > MaxFailureCount then __failfast;

else

delay = (dword) ((float)BaseRetryDelayMs * (crashes_seen ** Fallback_exponent))
// wait for delay and relaunch app
```
 
#### <a name="time-synchronization"></a>Sincronización de hora  
Si se producen errores en sincronización de hora o tiempo de espera de esto puede deberse a inaccesible o un servidor distante del tiempo, la siguiente puede hacerse para agregar servidores de hora local o adicionales. 
 
* Desde una línea de comandos en el dispositivo (p ej. SSH, PowerShell)  w32tm /config/syncfromflags: manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2. otra cosa,..." 
* También puede hacer estas adiciones en el registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado incluido como parte del proceso de creación de imagen si es necesario. 
Para obtener más información, consulte: 
* [Agregar un archivo y una configuración del registro a una imagen](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Creación de imágenes de Windows 10 IoT Core](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>Iniciar el servidor FTP 
El servidor FTP ya no se ejecuta de forma predeterminada al inicio 
<br>
Para ejecutar una vez: 
`Login with SSH\PS` Ejecute este comando para iniciar FTP:  
`start ftpd.exe` 
  
Para ejecutar en cada arranque, los usuarios deben crear un programador de tareas. 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>Información de copyright 

© Microsoft. Todos los derechos reservados. 
 
Este documento se proporciona tal y como está.  Información y las opiniones expresadas en este documento, incluidas las direcciones URL y otras referencias a sitios Web de Internet pueden cambiar sin previo aviso. 

Algunos de los ejemplos mencionados aquí son solamente ejemplos ficticios.  No se pretende realizar ni debe interpretarse ninguna conexión o asociación reales.  

Este documento no proporciona ningún derecho legal sobre ninguna propiedad intelectual de ningún producto de Microsoft.  Este documento se puede usar para referencias internas, con fines. 
  
Microsoft no otorga garantías, expresas o implícitas.  

Consulte Trademarks Microsoft para obtener una lista de productos de marca registradas. 

Las demás marcas comerciales pertenecen a sus respectivos propietarios.  

UPnP ™ es una marca de certificación de lUPnP™ Implementers Corporation. 

Bluetooth® es una marca que pertenecen a Bluetooth SIG, Inc. Estados Unidos y autoriza el uso de Microsoft Corporation. 

Intel es una marca registrada de Intel Corporation. 

Itanium es una marca registrada de Intel Corporation.
 
Algunas partes de este software se según MCSA Mosaic, desarrolladas por el National Center for Supercomputing Applications de la Universidad de Illinois en Urbana-Champaign, distribuidas bajo un contrato de licencia con Spyglass, Inc. 

Este producto contiene software de seguridad bajo licencia de RSA Data Security, Inc. 
