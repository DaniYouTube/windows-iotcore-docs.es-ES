---
title: Habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core
keywords: Windows iot, arranque seguro, BitLocker, protección de dispositivos, seguridad, seguridad de llave en mano
ms.openlocfilehash: 957b81a0a5bc032c62fa75598418778862fdf76d
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533337"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>Habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core

Windows 10 IoT Core ahora incluye ofertas de características de seguridad como arranque seguro de UEFI, cifrado de dispositivo de BitLocker y Device Guard.  Estos le ayudará a los generadores de dispositivo crear totalmente bloqueado de los dispositivos de IoT de Windows que sean resistentes a muchos tipos diferentes de los ataques.  Juntas, estas características ofrecen la protección óptima que garantiza que se iniciará una plataforma de una forma definida, mientras el bloqueo de archivos binarios desconocidos y proteger los datos de usuario mediante el uso de cifrado de dispositivo.

## <a name="boot-order"></a>Orden de arranque

Antes de que podemos adentrarnos en los componentes individuales que proporcionan una plataforma segura para el dispositivo de IoT, es necesario comprender el orden de arranque en un dispositivo Windows 10 IoT Core.

Hay tres áreas principales que se producen cuando un dispositivo de IoT está encendido, todo el proceso para la carga de kernel del sistema operativo y la ejecución de la aplicación instalada.

* Arranque seguro de plataforma
* Arranque seguro (UEFI) de la interfaz de Firmware Extensible unificada
* Integridad de código de Windows

![Captura de pantalla de panel](../media/SecureBootAndBitLocker/BootOrder.jpg)

Puede encontrar información adicional sobre el proceso de arranque de Windows 10 [aquí](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process).

## <a name="locking-down-iot-devices"></a>Dispositivos IoT bloquear

En orden de bloqueo de un dispositivo Windows IoT, se deben realizar las siguientes consideraciones.

### <a name="platform-secure-boot"></a>Arranque seguro de plataforma

Cuando el dispositivo está encendido en primer lugar, es el primer paso del proceso general de arranque cargar y ejecutar firmware cargadores de arranque, que inicializan el hardware en los dispositivos y proporcionan funcionalidad de intermitencia de emergencia. El entorno de UEFI, a continuación, se cargan y se cede el control.

Estos cargadores de arranque de firmware son específicos de SoC, por lo que necesita trabajar con el fabricante del dispositivo adecuado para tener estos cargadores de arranque creados en el dispositivo.

### <a name="uefi-secure-boot"></a>Arranque seguro de la UEFI

Arranque seguro de UEFI es el primer punto de cumplimiento de directivas y se encuentra en UEFI.  Restringe el sistema para permitir solo la ejecución de archivos binarios firmados por una entidad determinada, como los controladores de firmware, ROM, controladores UEFI o aplicaciones y los cargadores de arranque UEFI. Esta característica evita que código desconocido se ejecuta en la plataforma y potencialmente debilitar su seguridad de ella. Arranque seguro reduce el riesgo de ataques de malware previo al arranque en el dispositivo, como los rootkits. 

OEM, deberá almacenar el arranque seguro de UEFI bases de datos en el dispositivo de IoT en tiempo de fabricación. Estas bases de datos incluyen la firma de base de datos (db), revocar la firma (dbx) y la base de datos de inscripción de clave (KEK). Estas bases de datos se almacenan en el firmware RAM no volátil (NV-RAM) del dispositivo.

* **Base de datos de la firma (db):** Esto enumera los firmantes o códigos hash de la imagen de cargadores del sistema operativo, aplicaciones UEFI y controladores UEFI que pueden cargarse en el dispositivo

* **Revocar la base de datos de firma (dbx):** Esto enumera los firmantes o códigos hash de la imagen de cargadores del sistema operativo, aplicaciones UEFI y controladores UEFI que ya no son de confianza y están *no* permite que se cargue en el dispositivo 

* **Base de datos de inscripción de clave (KEK):** Contiene una lista de claves que pueden usarse para actualizar la firma y revocar las bases de datos de la firma de firma.

Una vez que se crean estas bases de datos y se agrega al dispositivo, el OEM bloquea el firmware de la edición y genera una plataforma (PK) de la clave de firma. Esta clave se puede utilizar para firmar las actualizaciones a la KEK o para deshabilitar arranque seguro de UEFI.

Estos son los pasos realizados por el arranque seguro de UEFI:

1. Después de que el dispositivo está encendido, las bases de datos de la firma cada comprueban con la plataforma (PK) de la clave de firma.
2. Si el firmware no es de confianza, el firmware UEFI inicia recuperación específica del OEM para restaurar el firmware de confianza.
3. Si no se puede cargar el Administrador de arranque de Windows, el firmware intentará arrancar una copia de seguridad del Administrador de arranque de Windows. Si esto tampoco funciona, el firmware UEFI inicia corrección específica del OEM.
4. Administrador de arranque de Windows se ejecuta y comprueba la firma digital del Kernel de Windows. Si la confianza, el Administrador de arranque de Windows pasa el control al Kernel de Windows.


Obtener más detalles sobre el arranque seguro, junto con instrucciones para la administración y la creación de la clave está disponible [aquí](https://technet.microsoft.com/library/dn747883.aspx).

### <a name="windows-code-integrity"></a>Integridad de código de Windows

Integridad de código de Windows (WCI) mejora la seguridad del sistema operativo al validar la integridad de un controlador o una aplicación cada vez que se carga en la memoria. Elemento de configuración contiene dos componentes principales: integridad de código de modo Kernel (KMCI) y la integridad de código de modo de usuario (UMCI).

Integridad de código configurable (CCI) es una característica de Windows 10 que permite que los generadores de dispositivo para bloquear un dispositivo y solo le permiten ejecutar y ejecutar código que se firma y de confianza.  Para ello, los generadores de dispositivo pueden crear una directiva de integridad de código en un dispositivo "golden" (versión de lanzamiento final de hardware y software) y, a continuación, proteger y aplicar esta directiva en todos los dispositivos en la fábrica.

Para más información sobre la implementación de directivas de integridad de código, auditoría y cumplimiento, consulte la documentación más reciente de technet [aquí](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).

Estos son los pasos seguidos por integridad de código de Windows:

1. Kernel de Windows comprobará que todos los demás componentes en la base de datos de la firma antes de la carga. Esto incluye los controladores, los archivos de inicio y ELAM (temprana antimalware de inicio).
2. Kernel de Windows cargará los componentes de confianza en el proceso de inicio y prohibir la carga de los componentes de confianza.
3. Carga del sistema operativo de Windows 10 IoT Core, junto con las aplicaciones instaladas.

### <a name="bitlocker-device-encryption"></a>Cifrado de dispositivos de BitLocker

Windows 10 IoT Core también implementa una versión ligera de cifrado de dispositivo de BitLocker, protección de los dispositivos de IoT contra ataques sin conexión. Esta funcionalidad tiene una dependencia fuerte en la presencia de un TPM en la plataforma, incluido el protocolo previo necesario en UEFI que toma las medidas necesarias. Estas mediciones previo asegurarse de que el sistema operativo posterior tenga un registro definitivo de cómo se inició el sistema operativo; Sin embargo, no aplica las restricciones de ejecución.

> [!TIP]
> Funcionalidad de BitLocker en Windows 10 IoT Core permite para el cifrado automático de volumen del sistema operativo basado en NTFS al enlazar todos los volúmenes de datos NTFS disponibles en él. Para ello, es necesario para asegurarse de que el volumen EFIESP GUID se establece en _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.

### <a name="device-guard-on-windows-iot-core"></a>Device Guard en Windows IoT Core

La mayoría de los dispositivos de IoT se crean como dispositivos de funciones fijas. Esto implica que los generadores de dispositivo saben exactamente qué firmware, sistemas operativos, controladores y aplicaciones deben ejecutarse en un dispositivo determinado. A su vez, esta información puede ser utilizado totalmente bloquear un dispositivo IoT solo tiene que permitir la ejecución de código conocida y de confianza. Device Guard en Windows 10 IoT Core puede ayudar a proteger los dispositivos de IoT, lo que garantiza que no se puede ejecutar código ejecutable desconocido o que no se confía en los dispositivos bloqueados.


## <a name="turnkey-security-on-iot-core"></a>Seguridad de llave en mano en IoT Core

Para facilitar la fácil habilitación de características clave de seguridad en dispositivos de IoT Core, Microsoft ofrece una llave en mano "paquete de seguridad" que permite que los generadores de dispositivo crear completamente bloqueado de los dispositivos de IoT.  Le ayudará este paquete con:

* Aprovisionamiento de claves de arranque seguro y habilitar la característica en las plataformas admitidas de IoT
* Instalación y configuración de cifrado del dispositivo con BitLocker 
* Iniciando el bloqueo del dispositivo para solo permitir la ejecución de las aplicaciones firmadas y controladores

### <a name="prerequisites"></a>Requisitos previos

* Un equipo que ejecuta Windows 10 Enterprise
* [Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) : requerido para la generación de certificado
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) : requerido para la generación de CAB
* Plataforma de referencia: versión de hardware con el firmware de trasvase de registros, sistema operativo, controladores y aplicaciones será necesaria para bloqueo final

### <a name="development-iot-devices"></a>Dispositivos de IoT de desarrollo

Windows 10 IoT Core funciona con diversos silicons que se emplean en cientos de dispositivos. De la [sugiere los dispositivos de desarrollo de IoT](../learn-about-hardware/SoCsAndCustomBoards.md), los siguientes proporcionan funcionalidad TPM de firmware de fábrica, junto con las funcionalidades de arranque seguro, arranque medido, BitLocker y Device Guard:

* QUALCOMM DragonBoard 410c

    Con el fin de habilitar el arranque seguro, puede ser necesario para aprovisionar RPMB. Una vez que el eMMC ha sido se vacían con Windows 10 IoT Core (según las instrucciones [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), presione [Power] + [Vol +] + Vol-simultáneamente en el dispositivo cuando se inicia rápidamente y seleccione "RPMB aprovisionar" en el menú BDS. *Tenga en cuenta que esto es un paso irreversible.*

* Intel MinnowBoardMax

    Para Intel MinnowBoard Max, versión de firmware debe ser 0.82 o posterior (obtener el [firmware más reciente](https://firmware.intel.com/projects/minnowboard-max)). Para habilitar la funcionalidad de TPM, encender la placa con un teclado y pantalla adjunta y presione F2 para entrar en la configuración UEFI. Vaya a _el Administrador de dispositivos -> configuración del sistema -> configuración de seguridad -> PTT_ y establézcalo en  _&lt;habilitar&gt;_. Presione F10 para guardar los cambios y continuar con un reinicio de la plataforma.

> [!NOTE]
> Raspberry Pi 2 ni 3 no son compatibles con TPM y por lo que no podemos configuramos los escenarios de bloqueo.

### <a name="generate-lockdown-packages"></a>Generar paquetes de bloqueo

1. Descargue el [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) paquete, que contiene todas las herramientas adicionales y los scripts necesarios para configurar y bloqueo de dispositivos
2. Inicie una consola administrativa PowerShell (PS) en los equipos Windows 10 y navegue hasta la ubicación del script descargado.
3. Montaje de la plataforma de hardware de referencia (que se ejecuta la imagen desbloqueada) a su equipo a través de recurso compartido de red con

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. Generar claves para su dispositivo mediante

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * En la carpeta de salida especificado con el sufijo adecuado, se generan las claves y certificados.
    * **Proteger las claves generadas** como el dispositivo confiará en los archivos binarios firmados con estas claves solo después del bloqueo.
    * Puede omitir este paso y usar las claves generadas previamente solo para pruebas

5. Configure _settings.xml_

    * Sección general: Especifique los directorios de paquete
    * Sección de herramientas: Establecer la ruta de acceso para las herramientas
        * Windows10KitsRoot `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * WindowsSDKVersion `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * Versión del SDK instalado en el equipo está bajo `C:\Program Files (x86)\Windows Kits\10\`
    * Sección SecureBoot: Especifique qué claves que se usarán para el arranque seguro (PK y SB claves)
    * Sección de BitLocker: Especifique un certificado para la recuperación de datos de Bitlocker (clave DRA)
    * Sección SIPolicy: Especificar los certificados en los que deben ser de confianza
        * ScanPath : Ruta de acceso del dispositivo para el análisis de los archivos binarios, `\\a.b.c.d\C$`
        * actualizar: Firmante de la SIPolicy (claves PAUTH)
        * Usuario: Certificados de modo de usuario (claves UMCI) 
        * Kernel: Certificados de modo kernel (claves KMCI)
    * Empaquetado: Especifique la configuración para la generación de paquetes

> [!IMPORTANT]
> Con el fin de ayudar a probar durante el ciclo de desarrollo inicial, Microsoft ha proporcionado los certificados y claves generadas previamente en su caso.  Esto implica que los archivos binarios de Microsoft Test, desarrollo y versiones preliminares se consideran de confianza.  Durante la creación de un producto final y generación de imágenes, asegúrese de quitar estas dirija y usar sus propias claves para garantizar que un dispositivo totalmente bloqueado.

6. ejecutar los comandos siguientes para generar paquetes necesarios:

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a>Probar los paquetes de bloqueo
Puede probar los paquetes generados por instalarlos manualmente en un dispositivo desbloqueado mediante los pasos siguientes

1. Flash del dispositivo con la imagen desbloqueado (imagen utilizada para el análisis en el paso anterior).
2. Conectarse al dispositivo ([mediante SSH](../connect-your-device/SSH.md) o mediante [Powershell](../connect-your-device/PowerShell.md))
3. Copie los siguientes archivos .cab en el dispositivo en un directorio, p. ej. `c:\OemInstall`
    * OEM.Custom.Cmd.cab
    * OEM.Security.BitLocker.cab
    * OEM.Security.SecureBoot.cab
    * OEM.Security.DeviceGuard.cab
4. Iniciar el almacenamiento provisional de los paquetes generados por emitiendo los comandos siguientes

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    Si está utilizando la imagen personalizada y, después, tendrá que *omitir* este archivo y editar manualmente el `c:\windows\system32\oemcustomization.cmd` con el contenido disponible en `Output\OEMCustomization\OEMCustomization.cmd` archivo

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. El dispositivo se reiniciará en el sistema operativo (mostrando gears) para instalar los paquetes de actualización y se reiniciará al sistema operativo principal.  Una vez que el dispositivo se reinicia en MainOS, se habilitará el arranque seguro y debe exponerse a SIPolicy.
7. Reinicio del dispositivo para activar el cifrado de Bitlocker.
8. Probar las características de seguridad
    * SecureBoot: pruebe `bcdedit /debug on` , obtendrá un error que indica que el valor está protegido por la directiva de arranque seguro
    * BitLocker: Ejecute `fvecon -status c:`, obtendrá el estado mencionar *en Encrypted, tiene datos de recuperación (clave externa), tiene datos de TPM, seguro, partición de arranque, solo el espacio utilizado*
    * DeviceGuard: Ejecute cualquier binario sin signo o un archivo binario firmado con certificado no está en la lista SIPolicy y confirme que no puede ejecutar.

### <a name="generate-lockdown-image"></a>Generar imagen de bloqueo

Después de comprobar que los paquetes de bloqueo de seguridad funcionan según la configuración definida anteriormente, puede incluir estos paquetes en la imagen siguiendo el siguiente les indican los pasos. Leer el [IoT fabricación guía](https://aka.ms/iotcoreguide) para obtener instrucciones de creación de imagen personalizada.

1. En el directorio de área de trabajo, actualice los siguientes archivos desde el directorio de salida generado anterior
    * SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db.bin
      * SetVariable_kek.bin
      * SetVariable_pk.bin
    * BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * DETask.xml
      * Security.Bitlocker.wm.xml
      * setup.bitlocker.cmd
    * DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn.p7b
      * SIPolicyOff.p7b
  
2. Agregar RetailOEMInput.xml y TestOEMInput.xml bajo el directorio ProductName con Id. de característica de paquete de bloqueo
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. Volver a generar la imagen
    * `buildpkg all` (Esto genera nuevos paquetes de bloqueo según por encima de los archivos de directiva)
    * `buildimage ProductName test(or)retail`  (Esto genera Flash.ffu nueva)
4. El dispositivo con este nuevo Flash.ffu Flash y validar las características de seguridad.

Consulte [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) como un ejemplo de una configuración de la placa de bloqueo dragon.

Como alternativa, puede generar los paquetes de seguridad en el propio IoTCore Shell, consulte [agregar paquetes de seguridad](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) para obtener los detalles.


### <a name="developing-with-codesigning-enforcement-enabled"></a>Desarrollo con el cumplimiento de la firma de código habilitado

Una vez que se generan los paquetes y el bloqueo está activado, todos los archivos binarios que introdujo en la imagen durante el desarrollo deberá firmarse de forma adecuada. Asegúrese de que los archivos binarios de modo de usuario se firman con la clave _. \Keys\ ***-UMCI.pfx_. Para la firma de modo de kernel, como para los controladores, deberá especificar sus propias claves de firmas y asegúrese de se incluyen también en el SIPolicy anterior.

### <a name="unlocking-encrypted-drives"></a>Desbloquear unidades cifradas

Durante el desarrollo y pruebas, al intentar leer el contenido de un dispositivo cifrado sin conexión (por ejemplo, tarjeta SD para eMMC MinnowBoardMax o de DragonBoard con el modo de almacenamiento masivo USB), 'diskpart' puede usarse para asignar una letra de unidad al volumen de datos y MainOS (vamos a Suponga v: para MainOS y w: por datos).
Los volúmenes aparecerán bloqueados y necesita desbloquea manualmente. Esto puede realizarse en cualquier equipo que tenga instalado el certificado de OEM DRA.pfx (incluido en el [DeviceLockDown ejemplo](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)). Instale el archivo PFX y, a continuación, ejecute los siguientes comandos desde un símbolo del sistema administrativo:

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

Si necesita el contenido que se accede con frecuencia sin conexión, desbloqueo automático de BitLocker puede configurarse para los volúmenes después de la inicial desbloquear mediante los siguientes comandos:

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>Deshabilitar BitLocker

Surgiera existe una necesidad de deshabilitar temporalmente BitLocker, iniciar una sesión remota de PowerShell con el dispositivo de IoT y ejecute el siguiente comando: `sectask.exe -disable`.  

> [!NOTE]
> Cifrado del dispositivo se volverá a habilitar, en el arranque de dispositivos posterior a menos que la tarea programada de cifrado está deshabilitada.


