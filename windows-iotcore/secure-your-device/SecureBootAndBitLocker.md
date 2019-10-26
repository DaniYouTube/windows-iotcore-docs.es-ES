---
title: Habilitación del arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core
keywords: Windows IOT, arranque seguro, BitLocker, Device Guard, seguridad, seguridad llave en mano
ms.openlocfilehash: 00e2abf82a043dfebe956281995961692b45c3b9
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918539"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a>Habilitación del arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core

Windows 10 IoT Core incluye ofertas de características de seguridad como UEFI Secure boot, cifrado de dispositivos de BitLocker y Device Guard.  Estos ayudarán a los creadores de dispositivos en la creación de dispositivos IoT de Windows completamente bloqueados que son resistentes a muchos tipos diferentes de ataques.  Juntas, estas características proporcionan una protección óptima que garantiza que una plataforma se iniciará de una manera definida, al tiempo que se bloquean los binarios desconocidos y se protegen los datos de usuario mediante el cifrado del dispositivo.

## <a name="boot-order"></a>Orden de arranque

Se necesita una comprensión del orden de arranque en un dispositivo de Windows 10 IoT Core antes de que podamos profundizar en los componentes individuales que proporcionan una plataforma segura para el dispositivo de IoT.

Hay tres áreas principales que se producen desde el momento en que se enciende un dispositivo IoT, pasando por la carga y la ejecución del kernel de sistema operativo de la aplicación instalada.

* Arranque seguro de plataforma
* Arranque seguro de Unified Extensible Firmware Interface (UEFI)
* Integridad de código de Windows

![Orden de arranque](../media/SecureBootAndBitLocker/BootOrder.jpg)

[Aquí](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process)encontrará información adicional sobre el proceso de arranque de Windows 10.

## <a name="locking-down-iot-devices"></a>Bloqueo de dispositivos IoT

Para bloquear un dispositivo de Windows IoT, deben tenerse en cuenta las consideraciones siguientes.

### <a name="platform-secure-boot"></a>Arranque seguro de plataforma

Cuando el dispositivo se enciende por primera vez, el primer paso en el proceso de arranque total consiste en cargar y ejecutar los cargadores de arranque de firmware, que inicializan el hardware en los dispositivos y proporcionan funcionalidad intermitente de emergencia. A continuación, se carga el entorno UEFI y se entrega el control.

Estos cargadores de arranque de firmware son específicos del SoC, por lo que tendrá que trabajar con el fabricante del dispositivo adecuado para crear estos cargadores de arranque en el dispositivo.

### <a name="uefi-secure-boot"></a>Arranque seguro de la UEFI

El arranque seguro UEFI es el primer punto de cumplimiento de directiva y se encuentra en UEFI.  Restringe el sistema para permitir solo la ejecución de archivos binarios firmados por una entidad de certificación especificada, como controladores de firmware, opciones de ROM, controladores UEFI o aplicaciones y cargadores de arranque UEFI. Esta característica evita que el código desconocido se ejecute en la plataforma y pueda debilitar la posición de seguridad del mismo. El arranque seguro reduce el riesgo de ataques de malware de prearranque al dispositivo, como rootkits. 

Como OEM, debe almacenar las bases de datos de arranque seguro de UEFI en el dispositivo IoT en el momento de la fabricación. Estas bases de datos incluyen la base de datos de firmas (dB), la base de datos de firma revocada (dbx) y la base de datos de claves de inscripción de claves (KEK). Estas bases de datos se almacenan en la RAM no volátil de firmware (NV-RAM) del dispositivo.

* **Base de datos de firmas (BD):** Aquí se enumeran los firmantes o los hash de imagen de los cargadores de sistema operativo, las aplicaciones UEFI y los controladores UEFI que se pueden cargar en el dispositivo.

* **Base de datos de firma revocada (dbx):** Aquí se enumeran los firmantes o los hash de imagen de los cargadores de sistema operativo, las aplicaciones UEFI y los controladores UEFI que ya no son de confianza y *no* se les permite que se carguen en el dispositivo. 

* **Base de datos de clave de inscripción de claves (KEK):** Contiene una lista de claves de firma que se pueden utilizar para actualizar la firma y las bases de datos de firma revocadas.

Una vez que estas bases de datos se crean y se agregan al dispositivo, el OEM bloquea el firmware de la edición y genera una clave de firma de plataforma (PK). Esta clave se puede usar para firmar actualizaciones en KEK o para deshabilitar el arranque seguro UEFI.

Estos son los pasos que realiza el arranque seguro de UEFI:

1. Una vez encendido el dispositivo, las bases de datos de firmas se comprueban con la clave de firma de plataforma (PK).
2. Si el firmware no es de confianza, el firmware UEFI inicia la recuperación específica del OEM para restaurar el firmware de confianza.
3. Si no se puede cargar el administrador de arranque de Windows, el firmware intentará arrancar una copia de seguridad del administrador de arranque de Windows. Si también se produce un error, el firmware UEFI inicia la corrección específica del OEM.
4. El administrador de arranque de Windows ejecuta y comprueba la firma digital del kernel de Windows. Si es de confianza, el administrador de arranque de Windows pasa el control al kernel de Windows.

[Aquí](https://technet.microsoft.com/library/dn747883.aspx)encontrará más detalles sobre el arranque seguro, junto con la guía de creación y administración de claves.

### <a name="windows-code-integrity"></a>Integridad de código de Windows

La integridad de código de Windows (WCI) mejora la seguridad del sistema operativo al validar la integridad de un controlador o una aplicación cada vez que se carga en la memoria. CI contiene dos componentes principales: integridad de código en modo kernel (KMCI) e integridad de código de modo de usuario (UMCI).

La integridad de código configurable (CCI) es una característica de Windows 10 que permite a los creadores de dispositivos bloquear un dispositivo y permitirle ejecutar y ejecutar código firmado y de confianza.  Para ello, los generadores de dispositivos pueden crear una directiva de integridad de código en un dispositivo "Golden" (versión de lanzamiento final de hardware y software) y, a continuación, proteger y aplicar esta directiva en todos los dispositivos de la fábrica.

Para obtener más información sobre la implementación de directivas de integridad de código, auditorías y cumplimiento, consulte la documentación de TechNet más reciente [aquí](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).

Estos son los pasos que realiza la integridad de código de Windows:

1. El kernel de Windows comprobará todos los demás componentes en la base de datos de firmas antes de cargarlos. Esto incluye los controladores, los archivos de inicio y ELAM (antimalware de inicio temprano).
2. El kernel de Windows cargará los componentes de confianza en el proceso de inicio y prohibirá la carga de los componentes que no son de confianza.
3. Cargas del sistema operativo Windows 10 IoT Core, junto con las aplicaciones instaladas.

### <a name="bitlocker-device-encryption"></a>Cifrado de dispositivo de BitLocker

Windows 10 IoT Core también implementa una versión ligera del cifrado de dispositivos de BitLocker, protegiendo los dispositivos IoT contra ataques sin conexión. Esta funcionalidad tiene una dependencia fuerte en la presencia de un TPM en la plataforma, incluido el protocolo anterior al sistema operativo necesario en UEFI que realiza las medidas necesarias. Estas medidas previas al sistema operativo garantizan que el sistema operativo más adelante tenga un registro definitivo de cómo se inició el sistema operativo; sin embargo, no aplica ninguna restricción de ejecución.

> [!TIP]
> La funcionalidad de BitLocker en Windows 10 IoT Core permite el cifrado automático del volumen del sistema operativo basado en NTFS mientras enlaza todos los volúmenes de datos NTFS disponibles a él. Para ello, es necesario asegurarse de que el GUID del volumen EFIESP se establece en _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.

### <a name="device-guard-on-windows-iot-core"></a>Device Guard en Windows IoT Core

La mayoría de los dispositivos IoT se compilan como dispositivos de funciones fijas. Esto implica que los generadores de dispositivos saben exactamente qué firmware, sistema operativo, controladores y aplicaciones deben ejecutarse en un dispositivo determinado. A su vez, esta información se puede usar para el bloqueo completo de un dispositivo IoT, ya que solo se permite la ejecución de código conocido y de confianza. Device Guard en Windows 10 IoT Core puede ayudar a proteger los dispositivos IoT asegurándose de que no se pueda ejecutar código ejecutable desconocido o que no sea de confianza en dispositivos bloqueados.


## <a name="turnkey-security-on-iot-core"></a>Seguridad llave en mano en IoT Core

Para facilitar la habilitación de las principales características de seguridad en los dispositivos IoT Core, Microsoft proporciona un [paquete de seguridad Llave]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) en mano que permite a los creadores de dispositivos compilar dispositivos IOT totalmente bloqueados. Este paquete le ayudará con:

* Aprovisionamiento de claves de arranque seguras y habilitación de la característica en plataformas de IoT compatibles
* Instalación y configuración del cifrado de dispositivos con BitLocker
* Iniciar el bloqueo de dispositivo para permitir solo la ejecución de aplicaciones y controladores firmados

En los pasos siguientes se llevará a cabo el proceso de creación de una imagen de bloqueo mediante el [paquete de seguridad Llave]( https://github.com/ms-iot/security/tree/master/TurnkeySecurity) en mano.

![Crear imagen de bloqueo](../media/SecurityFlowAndCertificates/ImageLockDown.png)

### <a name="prerequisites"></a>Requisitos previos

* Un equipo que ejecuta Windows 10 Enterprise (los scripts proporcionados **no** admiten otras versiones de Windows) 
* [SDK de Windows 10](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) : necesario para la generación de certificados
* [Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) : necesario para la generación de CAB
* Plataforma de referencia: se necesitará hardware de versión con firmware de envío, sistema operativo, controladores y aplicaciones para el bloqueo final.

### <a name="development-iot-devices"></a>Desarrollo de dispositivos IoT

Windows 10 IoT Core funciona con varios silicios que se usan en cientos de dispositivos. De los [dispositivos de desarrollo de IOT sugeridos](../learn-about-hardware/SoCsAndCustomBoards.md), los siguientes proporcionan funcionalidad TPM de firmware, junto con el arranque seguro, el arranque medido, las funcionalidades de BitLocker y Device Guard:

* Qualcomm DragonBoard 410C

    Para habilitar el arranque seguro, puede que sea necesario aprovisionar RPMB. Una vez que el eMMC se ha deshabilitado con Windows 10 IoT Core (según las instrucciones que se indican [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), presione [POWER] + [VOL +] + [VOL-] simultáneamente en el dispositivo cuando se enciende y seleccione "aprovisionar RPMB" en el menú BDS. *Tenga en cuenta que se trata de un paso irreversible.*

* Intel MinnowBoardMax

    En el caso de MinnowBoard Max, la versión de firmware debe ser 0,82 o superior (obtener el [firmware más reciente](https://firmware.intel.com/projects/minnowboard-max)). Para habilitar las capacidades de TPM, encienda el panel con un teclado & Mostrar adjunta y presione F2 para especificar la configuración de UEFI. Vaya a _Device Manager-> configuración del sistema-> configuración de seguridad-> PTT_ y establézcalo en _&lt;habilitar&gt;_ . Presione F10 para guardar los cambios y continuar con un reinicio de la plataforma.

> [!NOTE]
> Raspberry pi 2 y 3 no admiten TPM y, por tanto, no se pueden configurar escenarios de bloqueo.

### <a name="generate-lockdown-packages"></a>Generar paquetes de bloqueo

1. Descargue el paquete de [scripts de DeviceLockDown](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) , que contiene todas las herramientas y los scripts adicionales necesarios para configurar y bloquear dispositivos.
2. Inicie una consola de administración de PowerShell (PS) en el equipo con Windows 10 y navegue hasta la ubicación del script descargado.
3. Monte la plataforma de hardware de referencia (que ejecuta la imagen desbloqueada) en el equipo a través de un recurso compartido de red con

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. Generar claves para el dispositivo mediante

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * Las claves y los certificados se generan en la carpeta de salida especificada con el sufijo adecuado.
    * **Proteja las claves generadas** , ya que el dispositivo confiará en los archivos binarios firmados con estas claves solo después del bloqueo.
    * Puede omitir este paso y usar las claves generadas previamente solo para realizar pruebas.

5. Configurar _Settings. XML_

    * Sección General: especificar los directorios del paquete
    * Sección herramientas: establecer la ruta de acceso de las herramientas
        * `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)` Windows10KitsRoot
        * `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)` WindowsSDKVersion
            * La versión del SDK instalada en la máquina está en `C:\Program Files (x86)\Windows Kits\10\`
    * Sección de SecureBoot: especificación de las claves que se van a usar para el arranque seguro (claves PK y SB)
    * Sección de BitLocker: especificar un certificado para la recuperación de datos de BitLocker (clave DRA)
    * Sección SIPolicy: especificar los certificados que deben ser de confianza
        * ScanPath: ruta de acceso del dispositivo para la exploración de archivos binarios, `\\a.b.c.d\C$`
        * Update: firmante de SIPolicy (PAUTH Keys)
        * Usuario: certificados de modo de usuario (claves UMCI) 
        * Kernel: certificados de modo kernel (claves KMCI)
    * Empaquetado: especifique la configuración de la generación de paquetes.

> [!IMPORTANT]
> Para ayudar a realizar las pruebas durante el ciclo de desarrollo inicial, Microsoft ha proporcionado claves y certificados generados previamente cuando corresponda.  Esto implica que los binarios de prueba, desarrollo y versión preliminar de Microsoft se consideran de confianza.  Durante la creación del producto final y la generación de la imagen, asegúrese de quitar estos dirija y usar sus propias claves para garantizar un dispositivo totalmente bloqueado.

6. Ejecute los siguientes comandos para generar los paquetes necesarios:

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a>Probar paquetes bloqueados
Puede probar los paquetes generados si los instala manualmente en un dispositivo desbloqueado mediante los pasos siguientes:

1. Desbloquee el dispositivo con la imagen desbloqueada (imagen usada para digitalizar en el paso anterior).
2. Conexión al dispositivo ([mediante SSH](../connect-your-device/SSH.md) o con [PowerShell](../connect-your-device/PowerShell.md))
3. Copie los siguientes archivos. cab en el dispositivo en un directorio, por ejemplo `c:\OemInstall`
    * OEM. Personalizado. cmd. cab
    * OEM. Security. BitLocker. cab
    * OEM. Security. SecureBoot. cab
    * OEM. Security. DeviceGuard. cab
4. Inicie el ensayo de los paquetes generados mediante el emisión de los siguientes comandos:

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    Si usa una imagen personalizada, tendrá que *omitir* este archivo y editar manualmente el `c:\windows\system32\oemcustomization.cmd` con el contenido disponible en `Output\OEMCustomization\OEMCustomization.cmd` archivo.

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. El dispositivo se reiniciará en Update OS (mostrando engranajes) para instalar los paquetes y se reiniciará de nuevo en el sistema operativo principal.  Una vez que el dispositivo se reinicia en los principales, se habilitará el arranque seguro y se debe usar SIPolicy.
7. Reinicie el dispositivo para activar el cifrado de BitLocker.
8. Probar las características de seguridad
    * SecureBoot: Pruebe `bcdedit /debug on`, obtendrá un error que indica que el valor está protegido por la Directiva de arranque seguro.
    * BitLocker: ejecute `start /wait sectask.exe -waitencryptcomplete:1`, si ERRORLEVEL es `-2147023436` (ERROR_TIMEOUT), el cifrado no se completa. Al ejecutar sectask. exe desde un archivo. cmd, omita el `start /wait`.
    * DeviceGuard: ejecute cualquier binario sin firmar o binario firmado con certificado que no esté en la lista SIPolicy y confirme que no se puede ejecutar.

### <a name="generate-lockdown-image"></a>Generar imagen de bloqueo

Después de validar que los paquetes de bloqueo funcionan según la configuración definida anteriormente, puede incluir estos paquetes en la imagen siguiendo los pasos indicados a continuación. Lea la [Guía de fabricación de IOT](https://aka.ms/iotcoreguide) para obtener instrucciones de creación de imágenes personalizadas.

1. En el directorio del área de trabajo, actualice los siguientes archivos desde el directorio de salida generado anterior
    * SecureBoot: `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * SetVariable_db. bin
      * SetVariable_kek. bin
      * SetVariable_pk. bin
    * BitLocker: `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * Destask. XML
      * Security. BitLocker. WM. XML
      * Setup. BitLocker. cmd
    * DeviceGuard: `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * SIPolicyOn. p7b
      * SIPolicyOff. p7b
  
2. Agregue RetailOEMInput. XML y TestOEMInput. XML en el directorio ProductName con el identificador de característica del paquete de bloqueo
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. Volver a generar la imagen
    * `buildpkg all` (esto genera nuevos paquetes de bloqueo basados en archivos de directivas anteriores)
    * `buildimage ProductName test(or)retail` (esto genera un nuevo flash. FFU)
4. Parpadee el dispositivo con este nuevo flash. FFU y valide las características de seguridad.

Vea [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) como ejemplo de configuración de la placa Dragon de bloqueo.

Como alternativa, puede generar los paquetes de seguridad en el propio Shell de IoTCore, consulte [agregar paquetes de seguridad](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) para los detalles.


### <a name="developing-with-codesigning-enforcement-enabled"></a>Desarrollo con la aplicación de codiseño habilitada

Una vez que se generan los paquetes y se activa el bloqueo, todos los archivos binarios introducidos en la imagen durante el desarrollo deberán firmarse de forma adecuada. Asegúrese de que los archivos binarios de modo de usuario están firmados con la clave _.\Keys\ * * *-UMCI. pfx_. En el caso de la firma en modo kernel, como en el caso de los controladores, deberá especificar sus propias claves de firma y asegurarse de que también se incluyen en el SIPolicy anterior.

### <a name="unlocking-encrypted-drives"></a>Desbloqueo de unidades cifradas

Durante el desarrollo y las pruebas, al intentar leer el contenido de un dispositivo cifrado sin conexión (por ejemplo, tarjeta SD para MinnowBoardMax o eMMC de DragonBoard a través del modo de almacenamiento masivo USB), se puede usar ' DiskPart ' para asignar una letra de unidad a los principales y al volumen de datos (vamos a Supongamos que es v: para los principales y w: para los datos).
Los volúmenes aparecerán bloqueados y deben desbloquearse manualmente. Esto puede realizarse en cualquier máquina que tenga instalado el certificado OEM-DRA. pfx (incluido en el [ejemplo DeviceLockDown](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)). Instale el archivo PFX y, a continuación, ejecute los siguientes comandos desde un símbolo del sistema de CMD administrativo:

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

Si es necesario tener acceso a los contenidos con frecuencia sin conexión, se puede configurar el desbloqueo automático de BitLocker para los volúmenes después del desbloqueo inicial mediante los siguientes comandos:

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a>Deshabilitar BitLocker

Si surge la necesidad de deshabilitar BitLocker temporalmente, iniciar una sesión remota de PowerShell con el dispositivo de IoT y ejecute el siguiente comando: `sectask.exe -disable`.  

> [!NOTE]
> El cifrado de dispositivo se volverá a habilitar en el siguiente arranque del dispositivo a menos que se deshabilite la tarea de cifrado programado.


