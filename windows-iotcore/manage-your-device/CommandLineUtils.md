---
title: Utilidades de línea de comandos de Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las utilidades de línea de comandos para usar con PowreShell después de conectarse al dispositivo.
keywords: Windows iot, línea de comandos, utilidades de línea de comandos, PowerShell
ms.openlocfilehash: 4ba4ce1b77e14bb6cd8323ce44cb3a7b82ae8dbc
ms.sourcegitcommit: 3aaacf5e3ddbebb4a9324cfc8688110a2eb067ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132261"
---
# <a name="windows-10-iot-core-command-line-utils"></a>Utilidades de línea de comandos de Windows 10 IoT Core

¿Desea para configurar algunos de los valores en el dispositivo? Las siguientes herramientas están disponibles a su disposición. Use PowerShell para ejecutar estos comandos [conectarse al dispositivo](../connect-your-device/PowerShell.md).

> [!NOTE]
> Estas herramientas no se cargan previamente, deberá incluir identificadores de características correspondiente para obtener estas herramientas en la imagen.

## <a name="iot-core-specific-command-line-utils"></a>Utilidades de línea de comandos específicas de IoT Core

### <a name="setting-startup-app"></a>**Aplicación de inicio de configuración:**
Use el editor de inicio para configurar las aplicaciones de inicio en el dispositivo Windows IoT Core. Ejecute `IotStartup` con cualquiera de las siguientes opciones:

* `IotStartup list` las listas de las aplicaciones instaladas
* `IotStartup list headed` listas instaladas puntas de las aplicaciones
* `IotStartup list headless` aplicaciones sin periféricos listas instaladas
* `IotStartup list [MyApp]` lista de aplicaciones instaladas que coinciden con el patrón `MyApp`
* `IotStartup add` Agrega aplicaciones puntas y sin periféricos
* `IotStartup add headed [MyApp]` Agrega las puntas de las aplicaciones que coinciden con el patrón `MyApp`.  Patrón debe coincidir con sólo una aplicación.
* `IotStartup add headless [Task1]` Agrega aplicaciones sin periféricos que coinciden con el patrón `Task1`
* `IotStartup remove` Quita puntas y las aplicaciones sin periféricos
* `IotStartup remove headed [MyApp]` Quita las aplicaciones que coinciden con el patrón de puntas `MyApp`
* `IotStartup remove headless [Task1]` Quita las aplicaciones sin periféricos que coinciden con el patrón `Task1`
* `IotStartup startup` listas puntas y las aplicaciones sin periféricos registradas para el inicio
* `IotStartup startup [MyApp]` listas puntas y las aplicaciones sin periféricos registran para el inicio de ese patrón de coincidencia `MyApp`
* `IotStartup startup headed [MyApp]` listas puntas registradas para el inicio de aplicaciones que coinciden con `MyApp`
* `IotStartup startup headless [Task1]` Enumera las aplicaciones sin periféricos registradas para el inicio que coinciden con `Task1`
* `IotStartup run [MyApp]` Iniciar aplicación identificado por `MyApp`
* `IotStartup stop [MyApp]` detener aplicación identificado por `MyApp`
* Para obtener más ayuda, pruebe `IotStartup help`

### <a name="change-settings-for-region-and-user-or-speech-language"></a>**Cambiar la configuración de idioma de la región y de usuario o de voz:**

El `IoTSettings` herramienta cambia la región, el idioma del usuario o el idioma de voz. Esto es una herramienta de línea de comandos que se puede invocar desde una aplicación mediante la API ProcessLauncher. Estos comandos se deben ejecutar como cuenta predeterminada, no administrador.

* `IotSettings del account {all | username}` Elimina todas las MSA o AAD cuentas del sistema o una cuenta específica.  Cuentas específicas adoptan la forma username@provider.com
* `IotSettings del diagnostics` elimina la información de diagnóstico en la nube para el dispositivo actual.  Tenga en cuenta que esto quita el historial hasta el momento de invocación.  Nueva información de diagnóstico seguirán se ha iniciado.
* `IotSettings list account` Enumera todas las MSA o AAD cuentas que han sido firmadas en el dispositivo.
* `IotSettings list uilanguage` Enumera todos los idiomas de interfaz de usuario
* `IotSettings list speechlanguage` Enumera todos los idiomas de voz
* `IotSettings get uilanguage` Muestra el idioma de interfaz de usuario actual
* `IotSettings get speechlanguage` Muestra el idioma actual de voz
* `IotSettings get region` Muestra la región actual
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` establece el idioma predeterminado de la interfaz de usuario francés canadiense)
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` establece el idioma francés canadiense de voz)
* `IotSettings set region region\_code - (e.g. CA)` establece la región predeterminada para Canadá)
* `IotSettings set bluetoothpref {sink | source}` Especifica la preferencia de función Bluetooth para seleccionar cuando se conectan los dispositivos integrados con las características de IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK a otro dispositivo que también admite ambos roles.
* `IotSettings get bluetoothpref` Devuelve la preferencia de rol de Bluetooth actual para los dispositivos integrados con IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK.  El valor predeterminado es el origen.

> [!TIP]
> `IoTSettings -list uiLanguage` proporcionará volver la lista de idioma de interfaz de usuario compatible (en la versión de imagen de Windows IoT core con que se ha ejecutado)
    
### <a name="change-default-audio-device-and-volume"></a>**Cambiar el dispositivo de audio predeterminado y el volumen:**

El `IoTCoreAudioControlTool` herramienta controla las opciones relacionadas audio como valor predeterminado de los dispositivos de captura y reproducción y cambiar el volumen. Para obtener una lista completa de parámetros, ejecute `IoTCoreAudioControlTool h`.

### <a name="manually-installing-appx-files"></a>**Instalación manual. Archivos APPX:**
DeployAppx permite instalar y quitar en. Paquetes APPX en escenarios de desarrollo.  El método correcto para la instalación. Los paquetes APPX en imágenes de producción es usar un paquete de aprovisionamiento como se documenta en el [instalar la aplicación](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) asunto.  DeployAppx también admite las consultas. Información del paquete APPX.

*  `DeployAppx install MyApp.appx` instala el. APPX y el certificado del mismo nombre si se encuentra.
* `DeployAppx install force MyApp.appx` fuerza la desinstalación instalado actualmente. Nombre de Instalada con el mismo paquete si se encuentra antes de instalar el nuevo. APPX.  Esto es útil para instalar una. APPX con el número de versión igual o menor que la instalada actualmente. APPX.
* `DeployAppx install retry MyApp.appx` Vuelva a intentar instalar el. APPX 10 veces en caso de error con 2 segundo intervalo entre intentos.
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` Desinstale el archivo .appx con el nombre completo del paquete correspondiente.
*  `DeployAppx uninstall MyApp.appx` Desinstale cualquier instalado. APPX con un nombre de familia de paquete coincidente.
* `DeployAppx getpackages` Muestra los nombres completos de paquetes instalados.
* `DeployAppx getpackageid IotCoreDefaultApp.appx` Imprime el nombre del paquete, el nombre de familia de paquete y el paquete de nombre completo para el. APPX.
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` No compatible


## <a name="general-command-line-utils"></a>Utilidades de línea de comandos general

### <a name="update-account-password"></a>**Actualizar la contraseña de cuenta:**

Se recomienda encarecidamente que actualice la contraseña predeterminada para la cuenta de administrador. Para ello, puede emitir el comando siguiente: `net user Administrator [new password]` donde `[new password]` representa una contraseña segura de su elección.

### <a name="create-local-user-accounts"></a>**Crear cuentas de usuario local:**

Si desea asignar a otros usuarios acceso a su dispositivo Windows IoT Core, puede crear cuentas de usuario local adicional mediante PS escribiendo en `net user [username] [password] /add`. Si desea agregar este usuario a otros grupos, como el grupo de administradores, utilice `net localgroup Administrators [username] /add`.

### <a name="set-password"></a>**Establecer contraseña:**

Para cambiar la contraseña en una cuenta en el dispositivo, ejecute `net user [account-username] [new-password]` para cambiar la contraseña de cuenta.

### <a name="query-and-set-device-name"></a>**Consultar y establecer el nombre del dispositivo:**

Para identificar el nombre del dispositivo actual, simplemente escriba `hostname`. Para cambiar el nombre de su dispositivo Windows IoT Core, escriba `SetComputerName [new machinename]`. Es posible que deba reiniciar el dispositivo para que surta efecto el cambio de nombre.

### <a name="basic-network-configuration"></a>**Configuración de red básica:**

Muchas de las utilidades de configuración básica de la red, puede que ya esté familiarizado con están disponibles en Windows IoT Core, incluidos los comandos como `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, y `arp.exe`.

### <a name="copy-utilities"></a>**Utilidades de copia:**

Microsoft ofrece herramientas familiares, como `sfpcopy.exe` como `xcopy.exe`.

### <a name="process-management"></a>**Administración de procesos:**

Para ver los procesos que se está ejecutando, puede intentar `get-process` o bien puede `tlist.exe`. Para detener un proceso en ejecución, escriba `kill.exe [pid or process name]`.


### <a name="set-boot-option-headless-vs-headed-boot"></a>**Establezca la opción de arranque (sin periféricos frente a arranque con cabezal):**

Los dispositivos de Windows IoT Core pueden establecerse a puntas (cuando se requieren funciones de visualización) o sin periféricos (cuando una pantalla no es necesaria o está disponible) el modo de dispositivo. Para cambiar esta configuración, use `setbootoption.exe [headed | headless]`.

> [!NOTE]
> Si cambia esta configuración, se requerirá un reinicio en orden para que el cambio surta efecto.

### <a name="task-scheduler"></a>**Programador de tareas:**

Para ver la lista actual de las tareas programadas, use el `schtasks.exe` comando. Puede crear nuevas tareas con el `/create` cambiar o ejecutar tareas y a petición con la `/run` cambie. Para obtener una lista completa de parámetros admitidos, utilice `schtasks.exe /?`

### <a name="device-drivers"></a>**Controladores de dispositivos:**

La utilidad de la consola del dispositivo es útil para identificar y administrar los dispositivos instalados y los controladores. Para obtener una lista completa de parámetros, use `devcon.exe /?`

### <a name="registry-access"></a>**Acceso al registro:**

Si necesita tener acceso al registro para ver o modificar la configuración, utilice el `reg.exe /?` comando para obtener la lista completa de parámetros admitidos.

### <a name="services"></a>**Servicios:**

Administración de servicios de Windows se puede realizar mediante el `net.exe` comando. Para ver una lista de servicios en ejecución, escriba `net start`. Para iniciar o detener un servicio específico, escriba `net [start | stop] [service name]`. Como alternativa, también puede usar el Administrador de control de servicios a través de `sc.exe` comando.

### <a name="boot-configuration"></a>**Configuración de arranque:**

Puede realizar cambios a la configuración de arranque del dispositivo Windows IoT Core mediante `bcdedit.exe`. Por ejemplo, puede habilitar testsigning con `bcdedit –set testsigning on` comando.

### <a name="shutdownrestart-device"></a>**Cierre o reinicio del dispositivo:**

Para apagar el dispositivo, escriba `shutdown /s /t 0`. Para reiniciar el dispositivo, use el `/r` en su lugar cambiar con el comando `shutdown /r /t 0`.

### <a name="viewing-and-changing-display-settings"></a>**Ver y cambiar la configuración de pantalla**
La herramienta SetDisplayResolution puede utilizarse para enumerar la configuración de pantalla actual y para mostrar la lista de valores admitidos.  Además puede utilizarse para ajustar la resolución de la presentación, frecuencia de actualización u orientación a los valores admitidos por la plataforma.  La utilidad acepta los argumentos de línea de comandos siguientes:

* `SetDisplayResolution` Enumera lo resoltuion de presentación actual.
* `SetDisplayResolution -list` Las listas admiten resoluciones de pantalla.
* `SetDisplayResolution -orientation:[n]` Cambiar la orientación de pantalla, donde n = 0, 90, 180 o 270.
* `SetDisplayResolution [width] [height]` Cambiar el ancho y alto en píxeles 
* `SetDisplayResolution [width] [height] [refreshrate]` Cambiar ancho, alto y frecuencia de actualización donde son la anchura y altura en píxeles y refreshrate en Hz 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` Cambiar la orientación de ancho, alto, refreshrate y pantalla donde son de ancho y alto en píxeles, refreshrate en Hz y orientación es uno de 0, 90, 180 o 270.

### <a name="take-screenshot"></a>**Obtener captura de pantalla:**

Puede realizar la captura de pantalla del dispositivo Windows IoTCore mediante `ScreenCapture.exe`. Por ejemplo, ejecute `ScreenCapture c:\folder\screencap.jpg` tomará la captura de pantalla y guardarla en el archivo screencap.jpg.

### <a name="get-information-about-network-adapters"></a>**Obtenga información acerca de los adaptadores de red:**

Para ver la lista de todos los adaptadores de red disponible, ejecute `GetAdapterInfo` herramienta.

### <a name="set-folder-permissions-for-uwp-apps"></a>**Establecer permisos de carpeta para las aplicaciones para UWP:**

No todas las carpetas en el dispositivo están accesible mediante aplicaciones universales de Windows. Para hacer accesible a una carpeta en una aplicación para UWP, puede usar `FolderPermissions` herramienta. Por ejemplo ejecutar `FolderPermissions c:\test -e` para brindar acceso de aplicaciones para UWP a `c:\test` carpeta. Tenga en cuenta que esto funcionará sólo con las API de Win32 nativas para p. ej. CreateFile2 y no con las API de WinRT como StorageFolder, etcetera StorageFile.

### <a name="work-with-serial-ports"></a>**Trabajar con los puertos serie:**
[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) le permite trabajar con los puertos serie desde la línea de comandos. Se proporciona como un proyecto de ejemplo en el repositorio de ejemplos de iot de Microsoft. 

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


