---
title: 'Creators Update: compilación 15063'
ms.date: 08/28/2017
ms.topic: article
description: Lea y obtenga información sobre las novedades en Creators Update.
keywords: Windows IOT, Creators Update, notas de la versión
ms.openlocfilehash: 5946d97cd84992f62213d71c59374aa7f9a5779b
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721860"
---
# <a name="creators-update-release-notes-for-windows-10-iot-core"></a>Notas de la versión de Creators Update para Windows 10 IoT Core
Número de compilación 15063. Abril de 2017

Windows 10 IoT Core permite el desarrollo de dispositivos integrados o dedicados y es la opción para los OEM y desarrolladores que crean soluciones de Windows para dispositivos pequeños.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT Core.

Los paquetes de esta versión contienen las herramientas y los componentes necesarios para instalar Windows 10 IoT Core en Minnowboard Max Platform en función de los procesadores ATOM de Intel, Raspberry pi 2 basado en ARM Cortex A7 y Dragonboard 410C basados en la serie Qualcomm Snapdragon 400 incrustrados.   

Pueden estar disponibles [otras plataformas y procesadores](../../learn-about-hardware/SoCsAndCustomBoards.md) de asociados.

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar [aquí](https://go.microsoft.com/fwlink/?LinkId=506737).

## <a name="whats-new"></a>Novedades
* Versión pública de Windows 10 IoT Core. 
   * Compatibilidad con la administración de dispositivos de Azure: los OEM pueden usar la biblioteca de cliente de Azure DM para Windows IoT para agregar funcionalidades de administración de dispositivos a sus dispositivos conectados a Azure IoT Hub.
   * Compatibilidad adicional con silicio
      * Se ha comprobado la compatibilidad con Windows 10 IoT Core en Intel Joule (, Intel Pentium N4200, Intel Celeron N3350, el próximo Atom X5-E39xx processors (anteriormente Apollo Lake) y Raspberry PI 3 Som.
      * Allwinner ha habilitado la compatibilidad con sus dispositivos de pino 64 y banana PI mediante el SoC de Allwinner A64. 
   * Detección de dispositivos remotos: no se necesita software especial para detectar los dispositivos que han iniciado sesión con su cuenta de Microsoft.
   * Nuevas API y controles de UWP para vibraciones, brillo, el modo de espera conectado moderno, la administración de energía, la carga de la batería y NFC (w/o HCE). 
   * Nuevos buses y capacidades para ARM PCIe, el modo de función USB, la API de recuento de interrupciones de Wi-Fi Direct y GPIO. 
   * Nuevas características insertadas en el restablecimiento y la recuperación, en el SOC de SOC y el aprovisionamiento automático de USB 
   * Herramientas mejoradas: VS Code, nuevas características del portal de dispositivos de Windows y del panel de IoT, y compatibilidad con VS 2017.
   * Cortana en Windows IoT Core: Cortana ahora está disponible en Windows 10 IoT Core. Formule una pregunta a Cortana.
   * Mejoras en el panel de IoT: nuevas características y correcciones de errores de estabilidad
      * Compilaciones de Windows Insider Preview para Raspberry PI y Minnowboard 
      * Conexión de dispositivos con el cliente remoto de Windows IoT 
      * Direcciones IPv6 en la detección de dispositivos 
      * Carga de registros de dispositivo durante el envío de comentarios
   *  Nuevas API de GPIO de alta precisión: nuevas API (Windows. Devices. GPIO. GpioInterruptBuffer) para medir de forma precisa y eficiente el ancho de un pulso mediante interrupciones de GPIO.  Los proveedores de GPIO incluyen una nueva interfaz de búfer de interrupción para permitir la temporización de interrupción de alta precisión para aplicaciones como codificadores rotatorios y dispositivos de medición de distancia
   * Device Guard para ensambladores de dispositivos IoT ahora puede bloquear completamente los dispositivos IoT y obtener protección avanzada contra malware contra las variantes de malware nuevas y desconocidas.  Esto se puede hacer especificando las autoridades de firma para las aplicaciones y controladores permitidos que se ejecutan en el dispositivo, a la vez que se impide la ejecución de código desconocido o que no es de confianza.  Esto supone una mayor seguridad frente a ataques de malware y de cero días. 
   * Otras actualizaciones incluyen: 
      * Compatibilidad mejorada con las actualizaciones 
      * Compatibilidad con el SDK de puerta de enlace de Azure 
      * Aprovisionamiento automático basado en unidad USB 
      * Rediseño del portal de dispositivos 
      * Ahora, las imágenes de 64 bits admiten hasta 16.384 MB de memoria 
      * API de vibración de WinRT 
      * Compatibilidad con idiomas mejorada 
   * Varios  
      * Se ha realizado un cambio en la configuración de BCD predeterminada para evitar que los dispositivos intenten arrancar en modo de recuperación cuando no existe el modo de recuperación. 
      * IOT_POWER_SETTINGS característica ahora incluye powercfg. exe. Está disponible para todas las arquitecturas (ARM32, x86 y x64). 
      * Se realizaron cambios en Applyupdate. exe para agregar las marcas blockrebooton/blockrebootoff 
      * Se han agregado las extensiones de clase para la notificación de hardware (hwnclx) y la función USB (usbfnclx) a las imágenes de IoT Core predeterminadas.

## <a name="known-issues"></a>Problemas conocidos

### <a name="raspberry-pi"></a>Raspberry Pi  

#### <a name="raspberry-pi-display-resolution-if-monitor-is-disconnected"></a>Resolución de pantalla de Raspberry Pi si se desconecta el monitor 
Puede que Raspberry Pi no mantenga la resolución de pantalla si se desconecta el monitor. El EDID del monitor se usa para establecer la resolución del sistema cuando uno está conectado.  
Cuando se desconecta, el firmware de Raspberry Pi establece de forma predeterminada lo que está en config.txt en la raíz de la tarjeta SD. 

#### <a name="raspberry-pi-video-performance"></a>Rendimiento de vídeo de Raspberry Pi 
No se ha optimizado el rendimiento de reproducción de vídeo en la plataforma Raspberry PI.  Los elementos de usuario animados, incluidos los menús desplegables basados en XAML, pueden presentar un rendimiento inferior al óptimo. 

#### <a name="raspberry-pi-camera-support"></a>Compatibilidad de Raspberry Pi con la cámara 
La compatibilidad con Windows 10 IoT Core para dispositivos periféricos de cámara con dispositivos Raspberry PI es limitada. El dispositivo PiCam conectado directamente al bus de cámara incorporado no se admite actualmente, ya que requiere servicios de GPU que no están disponibles actualmente en Raspberry PI porque no se ha implementado el controlador de DirectX. Las webcams USB modernas producen flujos de datos muy exigentes en el controlador de host USB.  Incluso cuando se usa con configuraciones de baja resolución, las webcams requerirán una optimización de USB adicional y una lógica de control especializada.  

#### <a name="raspberry-pi-3-bluetooth-support"></a>Compatibilidad con Bluetooth de Raspberry PI 3 
El controlador Bluetooth integrado de Raspberry Pi3 solo admite dispositivos de ancho de banda bajo  

#### <a name="serial-port-usage-and-access-on-raspberry-pi-2"></a>Uso del puerto serie y acceso en Raspberry pi 2 
Raspberry Pi 2 es compatible con el transporte en serie para la comunicación a través de UART PL011.  Se establece de forma predeterminada en escenarios de depuración de kernel.  Un controlador de aplicación o dispositivo puede usar PL011 UART para enviar y recibir datos con el controlador de dispositivo PL011 desactivando el depurador con el siguiente comando:   
`bcedit /set debug off` 
 
### <a name="dragon-board"></a>Placa de dragón 

#### <a name="dragonboard-410c-shutdown"></a>Apagado de DragonBoard 410c 
En DragonBoard, la placa no se apagará con un comando de apagado. El sistema se reiniciará. Para apagar la placa, desconecte la alimentación. 

#### <a name="dragon-board-headset--microphone-jack"></a>Conector de auriculares y micrófono de DragonBoard  
El BSP de Dragonboard tiene controladores para el conector de auriculares y de micrófono, pero no tiene estos conectores en la placa.  

#### <a name="dragonboard-spi-runs-at-lock-speed"></a>Dragonboard SPI se ejecuta a la velocidad de bloqueo  
El SPI en el Dragonboard omitirá la velocidad solicitada y siempre se ejecutará a una velocidad preconfigurada.  

#### <a name="dragonboard-connected-standby"></a>Modo de espera conectado de DragonBoard 
El modo de espera conectado no está habilitado en Qualcomm DragonBoard de manera predeterminada.  Para habilitar el modo de espera conectado en DragonBoard, la siguiente clave del registro debe establecerse en "1" 
<br>
`HKLM\System\Controlset001\Control\Power\CsEnabled=DWORD:1`
<br>
Tenga en cuenta que no todas las plataformas admiten CS, por lo que es posible que esto no funcione en otras plataformas.    

#### <a name="vibration-api-may-not-function-on-some-qualcomm-platforms"></a>Es posible que la API de vibración no funcione en algunas plataformas Qualcomm 
La solución recomendada es agregar la siguiente clave del registro: 
<br>
`[HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics]` 
<br>
`"EnableOemSecurity"=dword:00000001 `
<br>
Para confirmación/comprobación en una imagen existente, conéctese con SSH o PowerShell y ejecute el siguiente comando: 
<br>
`reg add HKEY_LOCAL_MACHINE\SYSTEM\controlset001\services\hwnhaptics /t REG_DWORD /v EnableOemSecurity /d 1 `

### <a name="minnowboard"></a>MinnowBoard  

#### <a name="minnowboard-max-firmware-update"></a>Actualización de firmware de Minnowboard Max 
El número máximo de MinnowBoard no arrancará a menos que el firmware sea la versión. 092 o posterior.  
Puede haber errores de conectividad de red en el firmware MinnowBoard Max (MBM) versión 0,93.   El problema se corrigió en la versión de firmware 0,94).  la versión mínima recomendada del firmware es "MinnowBoard MAX 0,94 32-bit". Las actualizaciones de firmware se pueden descargar desde [aquí](https://go.microsoft.com/fwlink/?LinkId=708613).
  
 
### <a name="all-platforms"></a>Todas las plataformas 

#### <a name="mouse-pointer-disappears-while-debugging"></a>El puntero del mouse desaparece durante la depuración 
En algunos casos, el puntero del mouse no está visible después de implementar o depurar aplicaciones con Visual Studio, el puntero del mouse debe volver a aparecer si cambia el foco mediante el teclado (pestaña).  

#### <a name="server-applications-with-softap"></a>Aplicaciones de servidor con SoftAP  
Cuando se usa, los clientes de SoftAP no podrán acceder al contenido expuesto por las aplicaciones UAP.  
Para exponer las aplicaciones UAP a través de SoftAP, se deben realizar los siguientes cambios desde la consola del dispositivo:  
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
Hay un conflicto del controlador de sensor en las FFU proporcionadas. El marco del sensor remoto instala controladores para la brújula, el magnetómetro, el acelerómetro y el giroscopio. Las API de UWP que proporcionan acceso a estos controladores desde una aplicación suponen que solo hay uno instalado. Si está desarrollando un controlador para un dispositivo conectado físicamente, el controlador remoto en el FFUs proporcionado por Microsoft entrará en conflicto.  
Solución: el controlador conflictivo se puede quitar conectándose al dispositivo a través de SSH o PowerShell y usando la herramienta DEVCON. exe para quitar el controlador del sensor remoto escribiendo "DEVCON. exe Remove @" ROOT\REMOTESENSORDRIVER * ". El controlador de sensor remoto no afecta a las FFU que crea el fabricante de equipo original. 
 
#### <a name="default-administrator-user-name-and-password"></a>Nombre de usuario y contraseña predeterminados del administrador 
El nombre de usuario y la contraseña predeterminados del administrador están codificados de forma rígida en la imagen de Windows 10 IoT Core. Esto supone un riesgo de seguridad para el dispositivo y no debe exponerse a una conexión a Internet abierta hasta que se haya cambiado la contraseña. 
 
#### <a name="volume-controls"></a>Controles de volumen 
Los controles de volumen del hardware para micrófonos y altavoces USB que dependen del sistema de Windows para cambiar el volumen del sistema no son compatibles actualmente con Windows 10 IoT Core. 
 
#### <a name="usb-keyboards"></a>Teclados USB  
Es posible que algún teclado y mouse USB no funcionen en IoT Core. Use otro teclado o mouse. [Aquí](../../learn-about-hardware/HardwareCompatList.md)puede encontrar una lista de los dispositivos periféricos validados.  
 
#### <a name="screen-orientation"></a>Orientación de la pantalla 
No se puede establecer la orientación en "vertical" en una aplicación universal. 
 
#### <a name="referencing-adapters-with-alljoyn-templates"></a>Adaptadores de referencia con plantillas de AllJoyn 
El intento de agregar referencias a proyectos de adaptador AllJoyn puede producir errores al usar versiones específicas del SDK.  Para resolver estos errores, cambie la plataforma de destino de Visual Studio para que coincida con la versión actual del SDK y, a continuación, vuelva a cargar el proyecto. 

#### <a name="non-default-drive-mode"></a>Modo de unidad no predeterminado  
En Raspberry Pi y DragonBoard, el cambio de un modo de unidad no predeterminado a otro puede producir un problema en la patilla GPIO. SOLUCIÓN alternativa: establezca el modo de unidad una vez al principio de la aplicación. 
 
#### <a name="application-already-running"></a>Aplicación en ejecución  
La aplicación de inicio predeterminada podría entrar en conflicto consigo misma cuando también se implementa desde Visual Studio. SOLUCIÓN alternativa: cambie la aplicación de inicio predeterminada a una aplicación que no sea la que desea implementar. 
 
#### <a name="backgroundmediaplayermessagereceivedfromforeground-may-crash"></a>Puede que se bloquee la línea de código BackgroundMediaPlayer.MessageReceivedFromForeground  
La siguiente línea de código puede bloquearse: `BackgroundMediaPlayer.MessageReceivedFromForeground += OnMessageReceivedFromForeground;`.
<br>
Para evitar el bloqueo, agregue este código para que se ejecute en primer lugar `var player = BackgroundMediaPlayer.Current;` 
 
#### <a name="azure-active-directory-authentication-support"></a>Compatibilidad con la autenticación de Azure Active Directory  
La biblioteca de autenticación de Azure Active Directory no funciona en Windows 10 IoT Core.  
 
#### <a name="shell-management-of-application-crashes"></a>Administración del shell de los bloqueos de la aplicación 
La infraestructura del shell de IoT Core supervisa las aplicaciones de tipo APPX que se ejecutan en el dispositivo en busca de bloqueos y, cuando estos se producen, reinicia esas aplicaciones.  Si las aplicaciones reiniciadas continúan bloqueando, el shell empleará un __failfast: un proceso crítico del sistema que produce una comprobación de errores y se reinicia en un intento de recuperación.  La lógica comparable y el control se usan para las tareas en segundo plano y las aplicaciones de primer plano en una configuración.   

A continuación se muestra la lógica de reintento y el control de bloqueo: 

Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\CBTConfig (o ForegroundAppConfig para la cabeza) 
* QWord: "FailureResetIntervalMs": la duración de la aplicación debe ejecutarse correctamente para restablecer los errores detectados en 0. : el valor predeterminado es 0x00000000000493E0 = = 5 minutos. 
* QWord: "BaseRetryDelayMs"--coeficiente de tiempo de espera.  El valor predeterminado es 0xA.
* DWORD: "MaxFailureCount". El valor predeterminado es 10.
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
 
#### <a name="time-synchronization"></a>Sincronización de la hora  
Si se producen errores en la sincronización de la hora o se agota el tiempo de espera, puede deberse a un servidor horario lejano o inaccesible. Se puede hacer lo siguiente para agregar servidores de hora locales o adicionales. 
 
* Desde una línea de comandos en el dispositivo (por ejemplo, SSH, PowerShell)  W32tm/config/syncfromflags:/manualpeerlist manual: "0. Windows. Time. com 1.pool.ntp.org 2. otro elemento,..." 
* También puede realizar estas adiciones al registro a través de un script de arranque o un paquete de configuración de tiempo de ejecución personalizado incluido como parte del proceso de creación de la imagen, si es necesario. 
Para obtener más información, vea: 
* [Agregar un archivo y una configuración de registro a una imagen](https://msdn.microsoft.com/library/windows/hardware/mt670641(v=vs.85).aspx)
* [Creación de imágenes de Windows 10 IoT Core](https://blogs.msdn.microsoft.com/iot/2015/12/14/windows-10-iot-core-image-creation/)

#### <a name="starting-the-ftp-server"></a>Inicio del servidor FTP 
El servidor FTP ya no se ejecuta de forma predeterminada al iniciarse 
<br>
Para ejecutarse una vez: 
`Login with SSH\PS` ejecute este comando para iniciar FTP:  
`start ftpd.exe`    
Para ejecutar en todos los usuarios de arranque, debe crear una tarea de programador. 

    Login with SSH\PS and create a scheduler task:       
    schtasks /create /tn "IoTFTPD" /tr ftpd.exe /ru system /sc onstart 
    schtasks /run /tn “IoTFTPD” 

## <a name="copyright-information"></a>Información de copyright 

© Microsoft. Todos los derechos reservados. 
 
Este documento se proporciona tal y como está.  La información y las vistas expresadas en este documento, incluidas las direcciones URL y otras referencias a sitios web de Internet, pueden cambiar sin previo aviso. 

Algunos de los ejemplos mencionados aquí son solamente ejemplos ficticios.  No se pretende ni se debe inferir ninguna asociación o conexión real.  

Este documento no proporciona ningún derecho legal sobre ninguna propiedad intelectual de ningún producto de Microsoft.  Este documento se puede usar para fines de referencia internos. 
  
Microsoft no ofrece garantía alguna, ya sea expresa o implícita,  

Consulte las marcas comerciales de Microsoft para obtener una lista de productos marcados. 

Las demás marcas comerciales pertenecen a sus respectivos propietarios.  

UPnP ™ es una marca de certificación de lUPnP™ Implementers Corporation. 

Bluetooth® es una marca comercial propiedad de Bluetooth SIG, Inc. EE. UU. y con licencia para Microsoft Corporation. 

Intel es una marca registrada de Intel Corporation. 

Itanium es una marca registrada de Intel Corporation.
 
Algunas partes de este software se basan en MCSA Mosaic, desarrollada por National Center for Supercomputing Applications en la Universidad de Illinois en Urbana-Champaign, distribuida en virtud de un contrato de licencia con Spyglass, Inc. 

Este producto contiene software de seguridad con licencia de RSA Data Security, Inc. 
