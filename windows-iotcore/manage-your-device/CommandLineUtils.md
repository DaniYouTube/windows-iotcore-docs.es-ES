---
title: Utilidades de la línea de comandos de IoT Core de Windows 10
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de las utilidades de línea de comandos que debe usar con PowreShell después de conectarse al dispositivo.
keywords: Windows IOT, línea de comandos, utilidades de línea de comandos, PowerShell
ms.openlocfilehash: 4ba4ce1b77e14bb6cd8323ce44cb3a7b82ae8dbc
ms.sourcegitcommit: 3aaacf5e3ddbebb4a9324cfc8688110a2eb067ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132261"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Utilidades de la línea de comandos de IoT Core de Windows 10

¿Desea configurar algunas opciones en el dispositivo? Las siguientes herramientas están disponibles a su disposición. Use PowerShell para ejecutar estos comandos después [de conectarse al dispositivo](../connect-your-device/PowerShell.md).

> [!NOTE]
> Estas herramientas no están precargadas; deberá incluir los identificadores de características correspondientes para obtener estas herramientas en la imagen.

## <a name="iot-core-specific-command-line-utils"></a>Utilidades de la línea de comandos específicas de IoT Core

### <a name="setting-startup-app"></a>**Configuración de la aplicación de Inicio:**
Use el editor de inicio para configurar aplicaciones de inicio en el dispositivo Windows IoT Core. Ejecute `IotStartup` con cualquiera de las siguientes opciones:

* `IotStartup list`enumera las aplicaciones instaladas
* `IotStartup list headed`enumera las aplicaciones instaladas
* `IotStartup list headless`enumera las aplicaciones desatendidas instaladas
* `IotStartup list [MyApp]`enumerar las aplicaciones instaladas que coinciden con el patrón`MyApp`
* `IotStartup add`agrega aplicaciones con cabeza y sin periféricos
* `IotStartup add headed [MyApp]`agrega aplicaciones con cabeza que coinciden con el patrón `MyApp`.  El patrón solo debe coincidir con una aplicación.
* `IotStartup add headless [Task1]`agrega aplicaciones desatendidas que coinciden con el patrón`Task1`
* `IotStartup remove`quita las aplicaciones de encabezado y sin periféricos
* `IotStartup remove headed [MyApp]`quita las aplicaciones de encabezado que coinciden con el patrón`MyApp`
* `IotStartup remove headless [Task1]`quita las aplicaciones sin encabezado que coinciden con el patrón`Task1`
* `IotStartup startup`enumera las aplicaciones con encabezado y sin periféricos registradas para el inicio
* `IotStartup startup [MyApp]`enumera las aplicaciones con encabezado y sin periféricos registradas para el inicio que coinciden con el patrón`MyApp`
* `IotStartup startup headed [MyApp]`enumera las aplicaciones registradas para el inicio que coinciden`MyApp`
* `IotStartup startup headless [Task1]`enumera las aplicaciones desatendidas registradas para el inicio que coinciden`Task1`
* `IotStartup run [MyApp]`iniciar la aplicación identificada por`MyApp`
* `IotStartup stop [MyApp]`detener la aplicación identificada por`MyApp`
* Para obtener más ayuda, pruebe`IotStartup help`

### <a name="change-settings-for-region-and-user-or-speech-language"></a>**Cambiar la configuración de la región y el idioma del usuario o de la voz:**

La `IoTSettings` herramienta cambia la región, el idioma del usuario o el idioma de la voz. Se trata de una herramienta de línea de comandos que se puede invocar desde una aplicación mediante la API de ProcessLauncher. Estos comandos se deben ejecutar como cuenta predeterminada, no como administrador.

* `IotSettings del account {all | username}`elimina todas las cuentas MSA o AAD en el sistema o en una cuenta específica.  Las cuentas específicas tienen el formatousername@provider.com
* `IotSettings del diagnostics`elimina la información de diagnóstico en la nube para el dispositivo actual.  Tenga en cuenta que esto quita el historial hasta el momento de la invocación.  Se seguirá registrando la nueva información de diagnóstico.
* `IotSettings list account`muestra todas las cuentas de MSA o AAD que han iniciado sesión en el dispositivo.
* `IotSettings list uilanguage`enumera todos los idiomas de interfaz de usuario
* `IotSettings list speechlanguage`enumera todos los lenguajes de voz
* `IotSettings get uilanguage`muestra el idioma actual de la interfaz de usuario
* `IotSettings get speechlanguage`muestra el idioma actual de la voz
* `IotSettings get region`muestra la región actual
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)`establece el idioma de interfaz de usuario predeterminado francés canadiense)
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)`establece el idioma de voz francés canadiense)
* `IotSettings set region region\_code - (e.g. CA)`establece la región predeterminada en Canadá)
* `IotSettings set bluetoothpref {sink | source}`Especifica la preferencia de rol de Bluetooth que se debe seleccionar cuando los dispositivos compilados con las características IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK se conectan a otro dispositivo que también admite ambos roles.
* `IotSettings get bluetoothpref`Devuelve la preferencia de rol de Bluetooth actual para dispositivos compilados con IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK.  El valor predeterminado es Source.

> [!TIP]
> `IoTSettings -list uiLanguage`devolverá la lista de idioma de interfaz de usuario admitido (en la versión de la imagen de Windows IoT Core con la que se ha ejecutado).
    
### <a name="change-default-audio-device-and-volume"></a>**Cambiar el dispositivo de audio y el volumen predeterminados:**

La `IoTCoreAudioControlTool` herramienta controla las opciones relacionadas con el audio, como establecer los dispositivos de captura y reproducción predeterminados y cambiar el volumen. Para obtener una lista completa de parámetros, `IoTCoreAudioControlTool h`ejecute.

### <a name="manually-installing-appx-files"></a>**Instalación manual. Archivos APPX:**
DeployAppx permite instalar y quitar en. Paquetes APPX en escenarios de desarrollo.  El método correcto para instalar. Los paquetes APPX en imágenes de producción usan un paquete de aprovisionamiento, tal como se documenta en el tema [instalación de la aplicación](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) .  DeployAppx también admite la consulta. Información del paquete APPX.

*  `DeployAppx install MyApp.appx`instala el. APPX y el certificado del mismo nombre si se encuentra.
* `DeployAppx install force MyApp.appx`fuerza la desinstalación de la instalada actualmente. APPX con el mismo nombre de paquete si se encuentra antes de instalar el nuevo. APPX.  Esto resulta útil para instalar un. APPX con el mismo número de versión o inferior que el instalado actualmente. APPX.
* `DeployAppx install retry MyApp.appx`Vuelva a intentar instalar el. APPX 10 veces en caso de error con un retraso de 2 segundos entre intentos.
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123`Desinstale el. appx con el nombre completo del paquete coincidente.
*  `DeployAppx uninstall MyApp.appx`Desinstale cualquier instalado. APPX con un nombre de familia de paquete coincidente.
* `DeployAppx getpackages`muestra los nombres completos de los paquetes instalados.
* `DeployAppx getpackageid IotCoreDefaultApp.appx`imprime el nombre del paquete, el nombre de la familia del paquete y el nombre completo del paquete para. APPX.
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml`no compatible


## <a name="general-command-line-utils"></a>Utilidades generales de la línea de comandos

### <a name="update-account-password"></a>**Actualizar contraseña de la cuenta:**

Se recomienda encarecidamente que actualice la contraseña predeterminada para la cuenta de administrador. Para ello, puede emitir el siguiente comando: `net user Administrator [new password]` , donde `[new password]` representa una contraseña segura de su elección.

### <a name="create-local-user-accounts"></a>**Crear cuentas de usuario locales:**

Si desea conceder a otros usuarios acceso a su dispositivo Windows IoT Core, puede crear cuentas de usuario locales adicionales mediante PS escribiendo en `net user [username] [password] /add`. Si desea agregar este usuario a otros grupos, como el grupo de administradores, use `net localgroup Administrators [username] /add`.

### <a name="set-password"></a>**Establecer contraseña:**

Para cambiar la contraseña en una cuenta de su dispositivo, ejecute `net user [account-username] [new-password]` para cambiar la contraseña de la cuenta.

### <a name="query-and-set-device-name"></a>**Consultar y establecer el nombre del dispositivo:**

Para identificar el nombre de dispositivo actual, simplemente `hostname`escriba. Para cambiar el nombre del dispositivo de Windows IoT Core, escriba `SetComputerName [new machinename]`. Es posible que tenga que reiniciar el dispositivo para que el cambio de nombre surta efecto.

### <a name="basic-network-configuration"></a>**Configuración de red básica:**

Muchas de las utilidades básicas de configuración de red con las que puede estar familiarizado están disponibles en Windows IOT Core, incluidos `ping.exe`comandos `netstat.exe`como `netsh.exe`, `ipconfig.exe`, `tracert.exe`,, `arp.exe`y.

### <a name="copy-utilities"></a>**Copiar Utilidades:**

Microsoft proporciona herramientas que ya conoce, `sfpcopy.exe` como, por `xcopy.exe`ejemplo,.

### <a name="process-management"></a>**Administración de procesos:**

Para ver los procesos que se están ejecutando actualmente, `get-process` puede intentar o `tlist.exe`bien. Para detener un proceso en ejecución, `kill.exe [pid or process name]`escriba.


### <a name="set-boot-option-headless-vs-headed-boot"></a>**Configuración de la opción de arranque (Inicio frente a Inicio de la cabeza):**

Los dispositivos Windows IoT Core pueden establecerse en la punta (cuando se requieren capacidades de visualización) o sin periféricos (cuando una pantalla no es necesaria o disponible) modo de dispositivo. Para cambiar esta configuración, use `setbootoption.exe [headed | headless]`.

> [!NOTE]
> El cambio de esta configuración requerirá un reinicio para que el cambio surta efecto.

### <a name="task-scheduler"></a>**Programador de tareas:**

Para ver la lista actual de tareas programadas, use `schtasks.exe` el comando. Puede crear nuevas tareas con el `/create` modificador o ejecutar tareas a petición con el `/run` modificador. Para obtener una lista completa de los parámetros admitidos, use`schtasks.exe /?`

### <a name="device-drivers"></a>**Controladores de dispositivos:**

La utilidad de la consola del dispositivo es útil para identificar y administrar los dispositivos y controladores instalados. Para obtener una lista completa de parámetros, use`devcon.exe /?`

### <a name="registry-access"></a>**Acceso al registro:**

Si necesita tener acceso al registro para ver o modificar la configuración, use el `reg.exe /?` comando para obtener la lista completa de parámetros admitidos.

### <a name="services"></a>**Server**

La administración de servicios de Windows se puede `net.exe` realizar mediante el comando. Para ver una lista de los servicios en ejecución `net start`, escriba. Para iniciar o detener un servicio específico, escriba `net [start | stop] [service name]`. Como alternativa, también puede usar el comando a través `sc.exe` del administrador de control de servicios.

### <a name="boot-configuration"></a>**Configuración de arranque:**

Puede realizar cambios en la configuración de arranque del dispositivo `bcdedit.exe`Windows IOT Core mediante. Por ejemplo, puede habilitar testsigning con `bcdedit –set testsigning on` el comando.

### <a name="shutdownrestart-device"></a>**Apagar o reiniciar el dispositivo:**

Para apagar el dispositivo, escriba `shutdown /s /t 0`. Para reiniciar el dispositivo, use el `/r` modificador en su lugar con `shutdown /r /t 0`el comando.

### <a name="viewing-and-changing-display-settings"></a>**Ver y cambiar la configuración de pantalla**
La herramienta SetDisplayResolution se puede usar para enumerar la configuración de pantalla actual y para mostrar la lista de valores admitidos.  Se puede usar para ajustar la resolución, la frecuencia de actualización y la orientación de la pantalla a los valores admitidos por la plataforma.  La utilidad acepta los siguientes argumentos de la línea de comandos:

* `SetDisplayResolution`Muestra el resoltuion de presentación actual.
* `SetDisplayResolution -list`Muestra las resoluciones de pantalla compatibles.
* `SetDisplayResolution -orientation:[n]`Cambiar la orientación de la pantalla, donde n = 0, 90180 o 270.
* `SetDisplayResolution [width] [height]`Cambiar el ancho y el alto en píxeles 
* `SetDisplayResolution [width] [height] [refreshrate]`Cambiar el ancho, el alto y la frecuencia de actualización, donde el ancho y el alto se encuentran en píxeles y en un máximo de Hz 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]`Cambiar el ancho, el alto, el valor de frecuencia y la orientación de la pantalla donde el ancho y el alto se encuentran en píxeles, el valor máximo en Hz y la orientación es uno de 0, 90, 180 o 270.

### <a name="take-screenshot"></a>**Captura de pantalla:**

Puede realizar la captura de pantalla de su dispositivo `ScreenCapture.exe`IoTCore de Windows mediante. Por ejemplo, ejecutar `ScreenCapture c:\folder\screencap.jpg` realizará la captura de pantalla y la guardará en el archivo captura. jpg.

### <a name="get-information-about-network-adapters"></a>**Obtener información acerca de los adaptadores de red:**

Para ver la lista de todos los adaptadores de red disponibles, ejecute `GetAdapterInfo` la herramienta.

### <a name="set-folder-permissions-for-uwp-apps"></a>**Establecer permisos de carpeta para aplicaciones UWP:**

No todas las carpetas de su dispositivo son accesible para aplicaciones universales de Windows. Para hacer que una carpeta sea accesible para una aplicación para UWP, puede `FolderPermissions` usar la herramienta. Por ejemplo, `FolderPermissions c:\test -e` ejecute para proporcionar a las aplicaciones `c:\test` para UWP acceso a la carpeta. Tenga en cuenta que esto solo funcionará con las API de Win32 nativas, por ejemplo. CreateFile2 y no con las API de WinRT como StorageFolder, StorageFile, etc.

### <a name="work-with-serial-ports"></a>**Trabajar con puertos serie:**
[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) permite trabajar con puertos serie desde la línea de comandos. Se proporciona como un proyecto de ejemplo en el repositorio de ejemplos de MS-iot. 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```


