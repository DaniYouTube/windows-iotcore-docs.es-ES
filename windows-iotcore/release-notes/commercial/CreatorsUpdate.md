---
title: 'Creators Update: compilación 15063'
ms.date: 08/28/2017
ms.topic: article
description: Lee y obtén información sobre las novedades en Creators Update.
keywords: windows iot, Creators Update, notas de la versión
ms.openlocfilehash: 09157cb634de971bfe57f549c3c87354f814f9e9
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080555"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Notas de la versión de Creators Update para Windows 10 IoT Core
Número de compilación 15063. Abril de 2017

Windows 10 IoT Core permite el desarrollo de dispositivos integrados o dedicados, y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para dispositivos pequeños.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT Core.

Los paquetes de esta versión contienen herramientas y componentes necesarios para instalar Windows 10 IoT Core en la plataforma Minnowboard Max basada en procesadores Intel Atom, Raspberry Pi 2 o 400 basada en ARM Cortex A7, y DragonBoard 410c basada en procesadores Qualcomm Snapdragon de la serie 400.   

Es posible que los partners tengan a disposición [otros procesadores y plataformas](../../learn-about-hardware/SoCsAndCustomBoards.md).

## <a name="privacy-statement"></a>Declaración de privacidad

La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar [aquí](https://go.microsoft.com/fwlink/?LinkId=506737).

## <a name="whats-new"></a>Novedades
* Versión pública de Windows 10 IoT Core. 
   * Compatibilidad con la administración de dispositivos de Azure: Los OEM pueden usar la biblioteca cliente de Windows Azure IoT DM para agregar funcionalidades de administración de dispositivos a sus dispositivos conectados a Azure IoT Hub.
   * Compatibilidad adicional con placas
      * Se ha verificado la compatibilidad con Windows 10 IoT Core en Intel Joule, Intel Pentium N4200, Intel Celeron N3350, los próximos procesadores Atom x5-E39xx (anteriormente Apollo Lake) y SoM Raspberry Pi 3.
      * Allwinner ha habilitado la compatibilidad con sus dispositivos Pine 64 y Banana Pi mediante el SoC Allwinner A64. 
   * Detección de dispositivos remotos: No se necesita software especial para detectar los dispositivos que han iniciado sesión con tu cuenta de Microsoft.
   * Nuevas API y controles de UWP para vibración, brillo, modo de espera conectado moderno, administración de energía, carga de la batería y NFC (sin HCE). 
   * Nuevos buses y funcionalidades para PCIe ARM, el modo de función USB, Wi-Fi Direct y la API de recuento de interrupciones de GPIO. 
   * Nuevas características insertadas en restablecimiento y recuperación, PWM en el SOC y aprovisionamiento automático de USB. 
   * Herramientas mejoradas: VS Code, nuevas características del Portal de dispositivos de Windows y del Panel de IoT, y compatibilidad con VS 2017.
   * Cortana en Windows IoT Core: Cortana ahora está disponible en Windows 10 IoT Core. Haz una pregunta a Cortana.
   * Mejoras en el Panel de IoT: Nuevas características y correcciones de errores de estabilidad.
      * Compilaciones de Windows Insider Preview para Raspberry Pi y Minnowboard. 
      * Conexión de dispositivos con el cliente remoto de Windows IoT. 
      * Direcciones IPv6 en la detección de dispositivos. 
      * Carga de registros de dispositivo durante el envío de comentarios.
   *  Nuevas API de GPIO de alta precisión: Nuevas API (Windows.Devices.Gpio.GpioInterruptBuffer) para medir de forma precisa y eficiente los anchos de pulso mediante interrupciones de GPIO.  Los proveedores de GPIO incluyen una nueva interfaz de búfer de interrupción para permitir tiempos de interrupción de alta precisión para aplicaciones como codificadores rotatorios y dispositivos de medición de distancia.
   * Device Guard para IoT: Los fabricantes de dispositivos ahora puede bloquear completamente los dispositivos IoT y obtener protección avanzada contra las variantes de malware nuevas y desconocidas.  Esto se puede hacer especificando las autoridades de firma para las aplicaciones y controladores permitidos que se ejecutan en el dispositivo, a la vez que se impide la ejecución de código desconocido o que no es de confianza.  Esto supone una mayor seguridad frente a ataques de malware y de día cero. 
   * Entre otras actualizaciones se incluyen: 
      * Compatibilidad mejorada con las actualizaciones. 
      * Compatibilidad con el SDK de Azure Gateway. 
      * Aprovisionamiento automático basado en unidad USB. 
      * Rediseño del Portal de dispositivos. 
      * Ahora, las imágenes de 64 bits admiten hasta 16 384 MB de memoria. 
      * API de vibración de WinRT. 
      * Compatibilidad mejorada con los idiomas. 
   * Varios  
      * Se ha hecho un cambio en la configuración de BCD predeterminada para evitar que los dispositivos intenten arrancar en modo de recuperación cuando no existe el modo de recuperación. 
      * La característica IOT_POWER_SETTINGS ahora incluye powercfg.exe. Está disponible para todas las arquitecturas (ARM32, x86 y x64). 
      * Se hicieron cambios en Applyupdate.exe para agregar las marcas blockrebooton/blockrebootoff. 
      * Se han agregado las extensiones de clase para la notificación de hardware (hwnclx) y la función USB (usbfnclx) a las imágenes de IoT Core predeterminadas.

## <a name="known-issues"></a>Problemas conocidos

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Resolución de pantalla de Raspberry Pi si se desconecta el monitor 
Puede que Raspberry Pi no mantenga la resolución de pantalla si se desconecta el monitor. El EDID del monitor se usa para establecer la resolución del sistema cuando hay uno conectado.  
Cuando se desconecta, el firmware de Raspberry Pi establece de forma predeterminada lo que está en config.txt en la raíz de la tarjeta SD. 

#### <a name="raspberry-pi-video-performance"></a>Rendimiento de vídeo de Raspberry Pi 
El rendimiento de la reproducción de vídeo en la plataforma de Raspberry Pi no se ha optimizado.  Es posible que el rendimiento que muestren los elementos animados del usuario, incluidos los menús desplegables basados en XAML, no sea el óptimo. 

#### <a name="raspberry-pi-camera-support"></a>Compatibilidad de Raspberry Pi con la cámara 
La compatibilidad con Windows 10 IoT Core para dispositivos periféricos de cámara con dispositivos Raspberry Pi es limitada. El dispositivo PiCam conectado directamente al bus de cámara incorporado no se admite actualmente, ya que requiere servicios de GPU que no están disponibles actualmente en Raspberry Pi porque no se ha implementado el controlador de DirectX. Las cámaras web USB modernas producen flujos de datos muy exigentes para el controlador de host USB.  Incluso cuando se usa con cámaras web con valores de resolución bajos, se requerirá un ajuste preciso adicional y una lógica de control especializada del USB.  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Compatibilidad de Raspberry Pi3 con Bluetooth 
El controlador Bluetooth integrado de Raspberry Pi3 solo admite dispositivos con un ancho de banda bajo.  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Uso y acceso de los puertos serie en Raspberry Pi 2 
Raspberry Pi 2 es compatible con el transporte en serie para la comunicación a través de UART PL011.  Esto se establece de manera predeterminada en escenarios de depuración del kernel.  Un controlador de dispositivo o de aplicación puede usar UART PL011 para enviar y recibir datos con el controlador de dispositivo PL011 si se desactiva el depurador mediante el comando siguiente:   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>DragonBoard 

#### <a name="dragonboard-410c-shutdown"></a>Apagado de DragonBoard 410c 
En DragonBoard, la placa no se apagará con un comando de apagado. El sistema se reiniciará. Para apagar la placa, desconecte la alimentación. 

#### <a name="dragon-board-headset--microphone-jack"></a>Conector de auriculares y micrófono de DragonBoard  
El BSP de Dragonboard tiene controladores para el conector de auriculares y de micrófono, pero no tiene estos conectores en la placa.  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>El SPI de DragonBoard se ejecuta a una velocidad fija.  
El SPI de DragonBoard omitirá la velocidad solicitada y siempre se ejecutará a la velocidad preconfigurada.  

#### <a name="dragonboard-connected-standby"></a>Modo de espera conectado de DragonBoard 
El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.  Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del Registro debe establecerse en "1" 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
Tenga en cuenta que no todas las plataformas admiten CS, así que puede que esto no funcione en otras plataformas.    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>Es posible que la API de vibración no funcione en algunas plataformas de Qualcomm. 
La solución recomendada es agregar la siguiente clave del Registro: 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
Para confirmar o verificar una imagen existente, conéctate con SSH o PowerShell y ejecuta el siguiente comando: 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Actualización del firmware de MinnowBoard Max 
MinnowBoard Max no arrancará a menos que la versión del firmware sea 0.92 o posterior.  
Puede haber errores de conectividad de red en el firmware de MinnowBoard Max (MBM) versión 0.93.   El problema se corrigió en la versión de firmware 0.94.  La versión mínima recomendada del firmware es MinnowBoard Max 0.94 de 32 bits. Las actualizaciones de firmware pueden descargarse desde  [aquí](https://go.microsoft.com/fwlink/?LinkId=708613).
  
 
### <a name="all-platforms"></a>Todas las plataformas 

#### <a name="mouse-pointer-disappears-while-debugging"></a>El puntero del mouse desaparece durante la depuración 
En algunos casos, el puntero del mouse no es visible después de implementar o depurar aplicaciones con Visual Studio. El puntero del mouse debe reaparecer si cambias el foco con el teclado (TAB).  

#### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP  
Cuando usen SoftAP, los clientes no podrán acceder al contenido que exponen las aplicaciones UAP.  
Para exponer las aplicaciones UAP a través de SoftAP, deben realizarse los cambios siguientes desde la consola en el dispositivo:  
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

#### <a name="sensor-driver-conflict-in-pre-built-ffus"></a>Conflicto del controlador de sensor en FFU precompiladas 
Hay un conflicto del controlador de sensor en las FFU proporcionadas. El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio. Las API de UWP que proporcionan acceso a estos controladores desde una aplicación suponen que solo hay uno instalado. Si vas a desarrollar un controlador para un dispositivo adjuntado físicamente, el controlador remoto de las FFU que proporciona Microsoft entrará en conflicto.  
Solución: Se puede quitar el controlador que causa el conflicto mediante la conexión al dispositivo a través de SSH o PowerShell, y mediante el uso de la herramienta devcon.exe para quitar el controlador de sensor remoto (escriba "devcon.exe remove @”ROOT\REMOTESENSORDRIVER*"). El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original. 
 
#### <a name="default-administrator-user-name-and-password"></a>Nombre de usuario y contraseña predeterminados del administrador 
El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña. 
 
#### <a name="volume-controls"></a>Controles de volumen 
Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core. 
 
#### <a name="usb-keyboards"></a>Teclados USB  
Es posible que algún teclado y mouse USB no funcionen en IoT Core. Use otro teclado o mouse. Encontrarás una lista de dispositivos periféricos validados [aquí](../../learn-about-hardware/HardwareCompatList.md).  
 
#### <a name="screen-orientation"></a>Orientación de la pantalla 
El establecimiento de la orientación en "Vertical" puede que no se respete en una aplicación universal. 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>Adaptadores de referencia con plantillas de AllJoyn 
El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.  Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, luego, vuelva a cargar el proyecto. 

#### <a name="non-default-drive-mode"></a>Modo de unidad no predeterminado  
En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO. Solución alternativa: establezca el modo de la unidad una vez al comienzo de la aplicación. 
 
#### <a name="application-already-running"></a>Aplicación en ejecución  
La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio. Solución alternativa: cambie la aplicación de inicio predeterminada a otra aplicación distinta de la que quiere implementar. 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>Puede que se bloquee la línea de código BackgroundMediaPlayer.MessageReceivedFromForeground  
La línea de código siguiente podría bloquearse: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.
<br>
Para evitar el bloqueo, agrega este código para que se ejecute primero `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Compatibilidad con la autenticación de Azure Active Directory  
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  
 
#### <a name="shell-management-of-application-crashes"></a>Administración del shell de los bloqueos de la aplicación 
La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.  Si los bloqueos continúan en las aplicaciones reiniciadas, el shell empleará un __failfast, es decir, un proceso crítico del sistema que provoca una comprobación de errores y un reinicio en un intento de recuperación.  Se usan una lógica y un control comparables para las tareas en segundo plano y las aplicaciones de primer plano en una configuración con cabezal.   

A continuación se muestra la lógica de reintento y el control de bloqueo: 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig  (o ForegroundAppConfig para con cabezal) 
* Qword: "FailureResetIntervalMs": Duración que la aplicación debe ejecutarse correctamente para restablecer los errores detectados en 0. El valor predeterminado es 0x00000000000493E0 == 5 minutos. 
* Qword: "BaseRetryDelayMs": Coeficiente de tiempo de espera.  El valor predeterminado es 0xa.
* Dword: "MaxFailureCount". El valor predeterminado es 10.
* Dword: "FallbackExponentNumerator", el valor predeterminado es 31.
* Dword: "FallbackExponentDenominator", el valor predeterminado es 20.
 
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
 
#### <a name="time-synchronization"></a>Sincronización de la hora  
Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales. 
 
* Desde una línea de comandos en el dispositivo (por ejemplo, SSH, PowerShell)  w32tm /config /syncfromflags:manual /manualpeerlist:"0.windows.time.com 1.pool.ntp.org 2.something else, ..." 
* También puedes realizar estas adiciones en el Registro mediante un script de arranque o un paquete de configuración de tiempo de ejecución personalizado, incluido como parte del proceso de creación de imagen si es necesario. 
Para obtener más información, vea: 
* [Adición de un archivo y configuración del Registro en una imagen](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Creación de imágenes de Windows 10 IoT Core](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>Inicio del servidor FTP 
El servidor FTP ya no se ejecuta de manera predeterminada al inicio. 
<br>
Para ejecutarlo una vez: 
`Login with SSH\PS` Ejecuta este comando para iniciar FTP:  
`start ftpd.exe`    
Para ejecutarlo en todos los arranques, los usuarios deben crear una tarea de programador. 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>Información de copyright 

© Microsoft. Todos los derechos reservados. 
 
Este documento se proporciona tal y como está.  La información y las vistas expresadas en este documento, incluidas las direcciones URL y otras referencias a sitios web de Internet, pueden cambiar sin previo aviso. 

Algunos de los ejemplos mencionados aquí son solamente ejemplos ficticios.  No se pretende ni debe inferirse una asociación o relación real.  

Este documento no proporciona derechos legales sobre ninguna propiedad intelectual en ningún producto de Microsoft.  Este documento se puede usar con fines de referencia internos. 
  
Microsoft no otorga ninguna garantía, ni expresa ni implícita.  

Consulta las Marcas comerciales de Microsoft para obtener una lista de productos de marca registrada. 

Las demás marcas comerciales pertenecen a sus respectivos propietarios.  

UPnP ™ es una marca de certificación de lUPnP™ Implementers Corporation. 

Bluetooth® es una marca comercial propiedad de Bluetooth SIG, Inc. Estados Unidos, y se otorga bajo licencia a Microsoft Corporation. 

Intel es una marca comercial registrada de Intel Corporation. 

Itanium es una marca comercial registrada de Intel Corporation.
 
Algunas partes de este software se basan en MCSA Mosaic, desarrollada por National Center for Supercomputing Applications en la Universidad de Illinois, en Urbana-Champaign, distribuido en virtud de un contrato de licencia con Spyglass, Inc. 

Este producto contiene software de seguridad bajo licencia de RSA Data Security, Inc. 
