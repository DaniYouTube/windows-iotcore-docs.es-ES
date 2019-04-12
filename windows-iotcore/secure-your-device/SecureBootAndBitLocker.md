---
title: Habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core
keywords: Windows iot, arranque seguro, BitLocker, protección de dispositivos, seguridad, seguridad de llave en mano
ms.openlocfilehash: 68698a1b440b297eb9bfa9223bd324ce330386b9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514900"
---
# <a name="enabling-secure-boot-bitlocker-and-device-guard-on-windows-10-iot-core"></a><span data-ttu-id="a1977-104">Habilitar el arranque seguro, BitLocker y Device Guard en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="a1977-104">Enabling Secure Boot, BitLocker, and Device Guard on Windows 10 IoT Core</span></span>

## <a name="introduction"></a><span data-ttu-id="a1977-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="a1977-105">Introduction</span></span>

<span data-ttu-id="a1977-106">Con el lanzamiento de Creators Update, Windows 10 IoT Core mejora sus ofertas de características de seguridad para incluir el arranque seguro de UEFI, dispositivo de cifrado de BitLocker y Device Guard.</span><span class="sxs-lookup"><span data-stu-id="a1977-106">With the release of Creators Update, Windows 10 IoT Core improves its security feature offerings to include UEFI Secure Boot, BitLocker Device Encryption and Device Guard.</span></span>  <span data-ttu-id="a1977-107">Esto permite a los generadores de dispositivo en la creación de bloqueado completamente los dispositivos de IoT de Windows que sean resistentes a muchos tipos diferentes de los ataques.</span><span class="sxs-lookup"><span data-stu-id="a1977-107">These will allow device builders in creating fully locked down Windows IoT devices that are resilient to many different types of attacks.</span></span>  <span data-ttu-id="a1977-108">Juntas, estas características ofrecen la protección óptima que garantiza que se iniciará una plataforma de una forma definida, mientras el bloqueo de archivos binarios desconocidos y proteger los datos de usuario mediante el uso de cifrado de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a1977-108">Together, these features provide the optimal protection that ensures that a platform will launch in a defined way, while locking out unknown binaries and protecting user data through the use of device encryption.</span></span>

### <a name="secure-boot"></a><span data-ttu-id="a1977-109">Arranque seguro</span><span class="sxs-lookup"><span data-stu-id="a1977-109">Secure Boot</span></span>

<span data-ttu-id="a1977-110">Arranque seguro de UEFI es el primer punto de cumplimiento de directiva, ubicado en UEFI.</span><span class="sxs-lookup"><span data-stu-id="a1977-110">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="a1977-111">Restringe el sistema para permitir solo la ejecución de archivos binarios firmados por una entidad determinada.</span><span class="sxs-lookup"><span data-stu-id="a1977-111">It restricts the system to only allow execution of binaries signed by a specified authority.</span></span> <span data-ttu-id="a1977-112">Esta característica evita que código desconocido se ejecuta en la plataforma y potencialmente debilitar su seguridad de ella.</span><span class="sxs-lookup"><span data-stu-id="a1977-112">This feature prevents unknown code from being executed on the platform and potentially weakening the security posture of it.</span></span>

### <a name="bitlocker-device-encryption"></a><span data-ttu-id="a1977-113">Cifrado de dispositivos de BitLocker</span><span class="sxs-lookup"><span data-stu-id="a1977-113">BitLocker Device Encryption</span></span>

<span data-ttu-id="a1977-114">Windows 10 IoT Core también implementa una versión ligera de cifrado de dispositivo de BitLocker, protección de los dispositivos de IoT contra ataques sin conexión.</span><span class="sxs-lookup"><span data-stu-id="a1977-114">Windows 10 IoT Core also implements a lightweight version of BitLocker Device Encryption, protecting IoT devices against offline attacks.</span></span>  <span data-ttu-id="a1977-115">Esta funcionalidad tiene una dependencia fuerte en la presencia de un TPM en la plataforma, incluido el protocolo preOS necesarios en UEFI que toma las medidas necesarias.</span><span class="sxs-lookup"><span data-stu-id="a1977-115">This capability has a strong dependency on the presence of a TPM on the platform, including the necessary preOS protocol in UEFI that conducts the necessary measurements.</span></span> <span data-ttu-id="a1977-116">Estas medidas de preOS asegurarse de que el sistema operativo posterior tenga un registro definitivo de cómo se inició el sistema operativo; Sin embargo, no aplica las restricciones de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a1977-116">These preOS measurements ensure that the OS later has a definitive record of how the OS was launched; however, it does not enforce any execution restrictions.</span></span>

> [!TIP]
> <span data-ttu-id="a1977-117">Funcionalidad de BitLocker en Windows 10 IoT Core permite para el cifrado automático de volumen del sistema operativo basado en NTFS al enlazar todos los volúmenes de datos NTFS disponibles en él.</span><span class="sxs-lookup"><span data-stu-id="a1977-117">BitLocker functionality on Windows 10 IoT Core allows for automatic encryption of NTFS-based OS volume while binding all available NTFS data volumes to it.</span></span>  <span data-ttu-id="a1977-118">Para ello, es necesario para asegurarse de que el volumen EFIESP GUID se establece en _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span><span class="sxs-lookup"><span data-stu-id="a1977-118">For this, it’s necessary to ensure that the EFIESP volume GUID is set to _C12A7328-F81F-11D2-BA4B-00A0C93EC93B_.</span></span>

### <a name="device-guard-on-windows-iot-core"></a><span data-ttu-id="a1977-119">Device Guard en Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="a1977-119">Device Guard on Windows IoT Core</span></span>

<span data-ttu-id="a1977-120">La mayoría de los dispositivos de IoT se crean como dispositivos de funciones fijas.</span><span class="sxs-lookup"><span data-stu-id="a1977-120">Most IoT devices are built as fixed-function devices.</span></span>  <span data-ttu-id="a1977-121">Esto implica que los generadores de dispositivo saben exactamente qué firmware, sistemas operativos, controladores y aplicaciones deben ejecutarse en un dispositivo determinado.</span><span class="sxs-lookup"><span data-stu-id="a1977-121">This implies that device builders know exactly which firmware, operating system, drivers and applications should be running on a given device.</span></span>  <span data-ttu-id="a1977-122">A su vez, esta información puede ser utilizado totalmente bloquear un dispositivo IoT solo tiene que permitir la ejecución de código conocida y de confianza.</span><span class="sxs-lookup"><span data-stu-id="a1977-122">In turn, this information can be used to fully lockdown an IoT device by only allowing execution of known and trusted code.</span></span>  <span data-ttu-id="a1977-123">Device Guard en Windows 10 IoT Core puede ayudar a proteger los dispositivos de IoT, lo que garantiza que no se puede ejecutar código ejecutable desconocido o que no se confía en los dispositivos bloqueados.</span><span class="sxs-lookup"><span data-stu-id="a1977-123">Device Guard on Windows 10 IoT Core can help protect IoT devices by ensuring that unknown or untrusted executable code cannot be run on locked-down devices.</span></span>

## <a name="locking-down-iot-devices"></a><span data-ttu-id="a1977-124">Dispositivos IoT bloquear</span><span class="sxs-lookup"><span data-stu-id="a1977-124">Locking-down IoT Devices</span></span>

<span data-ttu-id="a1977-125">Con el fin de bloquear un dispositivo Windows IoT, se deben realizar las siguientes consideraciones...</span><span class="sxs-lookup"><span data-stu-id="a1977-125">In order to lockdown a Windows IoT device, the following considerations must be made...</span></span>

### <a name="uefi-platform--secure-boot"></a><span data-ttu-id="a1977-126">Plataforma UEFI y arranque seguro</span><span class="sxs-lookup"><span data-stu-id="a1977-126">UEFI Platform & Secure Boot</span></span>

<span data-ttu-id="a1977-127">Para poder aprovechar las capacidades de Device Guard, es necesario garantizar que los archivos binarios de arranque y el firmware UEFI están firmados y no se puedan alterar.</span><span class="sxs-lookup"><span data-stu-id="a1977-127">In order to leverage Device Guard capabilities, it is necessary to ensure that the boot binaries and UEFI firmware are signed and cannot be tampered with.</span></span>  <span data-ttu-id="a1977-128">Arranque seguro de UEFI es el primer punto de cumplimiento de directiva, ubicado en UEFI.</span><span class="sxs-lookup"><span data-stu-id="a1977-128">UEFI Secure Boot is the first policy enforcement point, located in UEFI.</span></span>  <span data-ttu-id="a1977-129">Evita la alteración mediante la restricción del sistema para solo permitir la ejecución de los archivos binarios de arranque firmado por una entidad especificada.</span><span class="sxs-lookup"><span data-stu-id="a1977-129">It prevents tampering by restricting the system to only allow execution of boot binaries signed by a specified authority.</span></span> <span data-ttu-id="a1977-130">Obtener más detalles sobre el arranque seguro, junto con instrucciones para la administración y la creación de la clave está disponible [aquí](https://technet.microsoft.com/library/dn747883.aspx).</span><span class="sxs-lookup"><span data-stu-id="a1977-130">Additional details on Secure Boot, along with key creation and management guidance, is available [here](https://technet.microsoft.com/library/dn747883.aspx).</span></span>

### <a name="configurable-code-integrity-cci"></a><span data-ttu-id="a1977-131">Integridad de código configurable (CCI)</span><span class="sxs-lookup"><span data-stu-id="a1977-131">Configurable Code Integrity (CCI)</span></span>

<span data-ttu-id="a1977-132">Integridad de código (CI) mejora la seguridad del sistema operativo al validar la integridad de un controlador o una aplicación cada vez que se carga en la memoria.</span><span class="sxs-lookup"><span data-stu-id="a1977-132">Code Integrity (CI) improves the security of the operating system by validating the integrity of a driver or application each time it is loaded into memory.</span></span> <span data-ttu-id="a1977-133">Elemento de configuración contiene dos componentes principales: integridad de código de modo Kernel (KMCI) y la integridad de código de modo de usuario (UMCI).</span><span class="sxs-lookup"><span data-stu-id="a1977-133">CI contains two main components - Kernel Mode Code Integrity (KMCI) and User Mode Code Integrity (UMCI).</span></span>

<span data-ttu-id="a1977-134">Integridad de código configurable (CCI) es una característica de Windows 10 que permite que los generadores de dispositivo para bloquear un dispositivo y solo le permiten ejecutar y ejecutar código que se firma y de confianza.</span><span class="sxs-lookup"><span data-stu-id="a1977-134">Configurable Code Integrity (CCI) is a feature in Windows 10 that allows device builders to lockdown a device and only allow it to run and execute code that is signed and trusted.</span></span>  <span data-ttu-id="a1977-135">Para ello, los generadores de dispositivo pueden crear una directiva de integridad de código en un dispositivo "golden" (versión de lanzamiento final de hardware y software) y, a continuación, proteger y aplicar esta directiva en todos los dispositivos en la fábrica.</span><span class="sxs-lookup"><span data-stu-id="a1977-135">To do so, device builders can create a code integrity policy on a 'golden' device (final release version of hardware and software) and then secure and apply this policy on all devices on the factory floor.</span></span>

<span data-ttu-id="a1977-136">Para más información sobre la implementación de directivas de integridad de código, auditoría y cumplimiento, consulte la documentación más reciente de technet [aquí](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span><span class="sxs-lookup"><span data-stu-id="a1977-136">To learn more about deploying code integrity policies, auditing and enforcement, check out the latest technet documentation [here](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-code-integrity-policies-steps).</span></span>

## <a name="turnkey-security-on-iot-core"></a><span data-ttu-id="a1977-137">Seguridad de llave en mano en IoT Core</span><span class="sxs-lookup"><span data-stu-id="a1977-137">Turnkey Security on IoT Core</span></span>

<span data-ttu-id="a1977-138">Para facilitar la fácil habilitación de características clave de seguridad en dispositivos de IoT Core, Microsoft ofrece una llave en mano "paquete de seguridad" que permite que los generadores de dispositivo crear completamente bloqueado de los dispositivos de IoT.</span><span class="sxs-lookup"><span data-stu-id="a1977-138">To facilitate easy enablement of key security features on IoT Core devices, Microsoft is providing a turnkey 'Security Package' that allows device builders to build fully locked down IoT devices.</span></span>  <span data-ttu-id="a1977-139">Le ayudará este paquete con:</span><span class="sxs-lookup"><span data-stu-id="a1977-139">This package will help with:</span></span>

* <span data-ttu-id="a1977-140">Aprovisionamiento de claves de arranque seguro y habilitar la característica en las plataformas admitidas de IoT</span><span class="sxs-lookup"><span data-stu-id="a1977-140">Provisioning Secure Boot keys and enabling the feature on supported IoT platforms</span></span>
* <span data-ttu-id="a1977-141">Instalación y configuración de cifrado del dispositivo con BitLocker</span><span class="sxs-lookup"><span data-stu-id="a1977-141">Setup and configuration of device encryption using BitLocker</span></span> 
* <span data-ttu-id="a1977-142">Iniciando el bloqueo del dispositivo para solo permitir la ejecución de las aplicaciones firmadas y controladores</span><span class="sxs-lookup"><span data-stu-id="a1977-142">Initiating device lockdown to only allow execution of signed applications and drivers</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="a1977-143">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a1977-143">Pre-requisites</span></span>

* <span data-ttu-id="a1977-144">Un equipo que ejecuta Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="a1977-144">A PC running Windows 10 Enterprise</span></span>
* <span data-ttu-id="a1977-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) : requerido para la generación de certificado</span><span class="sxs-lookup"><span data-stu-id="a1977-145">[Windows 10 SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk) - Required for Certificate Generation</span></span>
* <span data-ttu-id="a1977-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) : requerido para la generación de CAB</span><span class="sxs-lookup"><span data-stu-id="a1977-146">[Windows 10 ADK](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) - Required for CAB generation</span></span>
* <span data-ttu-id="a1977-147">Plataforma de referencia: versión de hardware con el firmware de trasvase de registros, sistema operativo, controladores y aplicaciones será necesaria para bloqueo final</span><span class="sxs-lookup"><span data-stu-id="a1977-147">Reference platform - release hardware with shipping firmware, OS, drivers and applications will be required for final lockdown</span></span>

### <a name="development-iot-devices"></a><span data-ttu-id="a1977-148">Dispositivos de IoT de desarrollo</span><span class="sxs-lookup"><span data-stu-id="a1977-148">Development IoT Devices</span></span>

<span data-ttu-id="a1977-149">Windows 10 IoT Core funciona con diversos silicons que se emplean en cientos de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a1977-149">Windows 10 IoT Core works with various silicons that are utilized in hundreds of devices.</span></span> <span data-ttu-id="a1977-150">De la [sugiere los dispositivos de desarrollo de IoT](../learn-about-hardware/SoCsAndCustomBoards.md), los siguientes proporcionan funcionalidad TPM de firmware de fábrica, junto con las funcionalidades de arranque seguro, arranque medido, BitLocker y Device Guard:</span><span class="sxs-lookup"><span data-stu-id="a1977-150">Of the [suggested IoT development devices](../learn-about-hardware/SoCsAndCustomBoards.md), the following provide firmware TPM functionality out of the box, along with Secure Boot, Measured Boot, BitLocker and Device Guard capabilities:</span></span>

* <span data-ttu-id="a1977-151">QUALCOMM DragonBoard 410c</span><span class="sxs-lookup"><span data-stu-id="a1977-151">Qualcomm DragonBoard 410c</span></span>

    <span data-ttu-id="a1977-152">Con el fin de habilitar el arranque seguro, puede ser necesario para aprovisionar RPMB.</span><span class="sxs-lookup"><span data-stu-id="a1977-152">In order to enable Secure Boot, it may be necessary to provision RPMB.</span></span> <span data-ttu-id="a1977-153">Una vez que el eMMC ha sido se vacían con Windows 10 IoT Core (según las instrucciones [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), presione [Power] + [Vol +] + Vol-simultáneamente en el dispositivo cuando se inicia rápidamente y seleccione "RPMB aprovisionar" en el menú BDS.</span><span class="sxs-lookup"><span data-stu-id="a1977-153">Once the eMMC has been flashed with Windows 10 IoT Core (as per instructions [here](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-dragonboard-410c), press [Power] + [Vol+] + [Vol-] simultaneously on the device when powering up and select "Provision RPMB" from the BDS menu.</span></span> *<span data-ttu-id="a1977-154">Tenga en cuenta que esto es un paso irreversible.</span><span class="sxs-lookup"><span data-stu-id="a1977-154">Please note that this is an irreversible step.</span></span>*

* <span data-ttu-id="a1977-155">Intel MinnowBoardMax</span><span class="sxs-lookup"><span data-stu-id="a1977-155">Intel MinnowBoardMax</span></span>

    <span data-ttu-id="a1977-156">Para Intel MinnowBoard Max, versión de firmware debe ser 0.82 o posterior (obtener el [firmware más reciente](https://firmware.intel.com/projects/minnowboard-max)).</span><span class="sxs-lookup"><span data-stu-id="a1977-156">For Intel's MinnowBoard Max, firmware version must be 0.82 or higher (get the [latest firmware](https://firmware.intel.com/projects/minnowboard-max)).</span></span> <span data-ttu-id="a1977-157">Para habilitar la funcionalidad de TPM, encender la placa con un teclado y pantalla adjunta y presione F2 para entrar en la configuración UEFI.</span><span class="sxs-lookup"><span data-stu-id="a1977-157">To enable TPM capabilities, power up board with a keyboard & display attached and press F2 to enter UEFI setup.</span></span> <span data-ttu-id="a1977-158">Vaya a _el Administrador de dispositivos -> configuración del sistema -> configuración de seguridad -> PTT_ y establézcalo en  _&lt;habilitar&gt;_.</span><span class="sxs-lookup"><span data-stu-id="a1977-158">Go to _Device Manager -> System Setup -> Security Configuration -> PTT_ and set it to _&lt;Enable&gt;_.</span></span> <span data-ttu-id="a1977-159">Presione F10 para guardar los cambios y continuar con un reinicio de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="a1977-159">Press F10 to save changes and proceed with a reboot of the platform.</span></span>

> [!NOTE]
> <span data-ttu-id="a1977-160">Raspberry Pi 2 ni 3 no son compatibles con TPM y por lo que no podemos configuramos los escenarios de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="a1977-160">Raspberry Pi 2 nor 3 do not support TPM and so we cannot configure Lockdown scenarios.</span></span>

### <a name="generate-lockdown-packages"></a><span data-ttu-id="a1977-161">Generar paquetes de bloqueo</span><span class="sxs-lookup"><span data-stu-id="a1977-161">Generate Lockdown Packages</span></span>

1. <span data-ttu-id="a1977-162">Descargue el [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) paquete, que contiene todas las herramientas adicionales y los scripts necesarios para configurar y bloqueo de dispositivos</span><span class="sxs-lookup"><span data-stu-id="a1977-162">Download the [DeviceLockDown Script](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) package, which contains all of the additional tools and scripts required for configuring and locking down devices</span></span>
2. <span data-ttu-id="a1977-163">Inicie una consola administrativa PowerShell (PS) en los equipos Windows 10 y navegue hasta la ubicación del script descargado.</span><span class="sxs-lookup"><span data-stu-id="a1977-163">Start an Administrative PowerShell (PS) console on your Windows 10 PC and navigate to the location of the downloaded script.</span></span>
3. <span data-ttu-id="a1977-164">Montaje de la plataforma de hardware de referencia (que se ejecuta la imagen desbloqueada) a su equipo a través de recurso compartido de red con</span><span class="sxs-lookup"><span data-stu-id="a1977-164">Mount your reference hardware platform (running the unlocked image) to your PC via network share using</span></span>

    ```powershell
    net use \\a.b.c.d\c$ /user:username password
    ```

4. <span data-ttu-id="a1977-165">Generar claves para su dispositivo mediante</span><span class="sxs-lookup"><span data-stu-id="a1977-165">Generate keys for your device using</span></span>

    ```powershell
    .\GenerateKeys.ps1 -OemName '<your oem name>' -outputPath '<output directory>'
    ```

    * <span data-ttu-id="a1977-166">En la carpeta de salida especificado con el sufijo adecuado, se generan las claves y certificados.</span><span class="sxs-lookup"><span data-stu-id="a1977-166">The keys and certificates are generated in the specified output folder with appropriate suffix.</span></span>
    * <span data-ttu-id="a1977-167">**Proteger las claves generadas** como el dispositivo confiará en los archivos binarios firmados con estas claves solo después del bloqueo.</span><span class="sxs-lookup"><span data-stu-id="a1977-167">**Secure your generated keys** as the device will trust binaries signed with these keys only after lockdown.</span></span>
    * <span data-ttu-id="a1977-168">Puede omitir este paso y usar las claves generadas previamente solo para pruebas</span><span class="sxs-lookup"><span data-stu-id="a1977-168">You may skip this step and use the pre-generated keys for testing only</span></span>

5. <span data-ttu-id="a1977-169">Instalar los certificados PFX generado al hacer clic en los archivos pfx directamente o mediante el siguiente comando de powershell</span><span class="sxs-lookup"><span data-stu-id="a1977-169">Install the generated .pfx certificates by clicking on the pfx files directly or using the below powershell command</span></span>

    ```powershell
    Import-PfxCertificate -FilePath $pfxfile -CertStoreLocation Cert:\CurrentUser\My
    ```

6. <span data-ttu-id="a1977-170">Configure _settings.xml_</span><span class="sxs-lookup"><span data-stu-id="a1977-170">Configure _settings.xml_</span></span>

    * <span data-ttu-id="a1977-171">Sección general: Especifique los directorios de paquete</span><span class="sxs-lookup"><span data-stu-id="a1977-171">General section : Specify the package directories</span></span>
    * <span data-ttu-id="a1977-172">Sección de herramientas: Establecer la ruta de acceso para las herramientas</span><span class="sxs-lookup"><span data-stu-id="a1977-172">Tools section : Set the path for the tools</span></span>
        * <span data-ttu-id="a1977-173">Windows10KitsRoot</span><span class="sxs-lookup"><span data-stu-id="a1977-173">Windows10KitsRoot</span></span> `(e.g. <Windows10KitsRoot>C:\Program Files (x86)\Windows Kits\10\</Windows10KitsRoot>)`
        * <span data-ttu-id="a1977-174">WindowsSDKVersion</span><span class="sxs-lookup"><span data-stu-id="a1977-174">WindowsSDKVersion</span></span> `(e.g. <WindowsSDKVersion>10.0.15063.0</WindowsSDKVersion>)`
            * <span data-ttu-id="a1977-175">Versión del SDK instalado en el equipo está bajo</span><span class="sxs-lookup"><span data-stu-id="a1977-175">SDK version installed on your machine is under</span></span> `C:\Program Files (x86)\Windows Kits\10\`
    * <span data-ttu-id="a1977-176">Sección SecureBoot: Especifique qué claves que se usarán para el arranque seguro (PK y SB claves)</span><span class="sxs-lookup"><span data-stu-id="a1977-176">SecureBoot section : Specify which keys to use for secure boot (PK and SB keys)</span></span>
    * <span data-ttu-id="a1977-177">Sección de BitLocker: Especifique un certificado para la recuperación de datos de Bitlocker (clave DRA)</span><span class="sxs-lookup"><span data-stu-id="a1977-177">BitLocker section : Specify a certificate for Bitlocker data recovery (DRA key)</span></span>
    * <span data-ttu-id="a1977-178">Sección SIPolicy: Especificar los certificados en los que deben ser de confianza</span><span class="sxs-lookup"><span data-stu-id="a1977-178">SIPolicy section : Specify certs that should be trusted</span></span>
        * <span data-ttu-id="a1977-179">ScanPath : Ruta de acceso del dispositivo para el análisis de los archivos binarios,</span><span class="sxs-lookup"><span data-stu-id="a1977-179">ScanPath : Path of the device for scanning binaries ,</span></span> `\\a.b.c.d\C$`
        * <span data-ttu-id="a1977-180">actualizar: Firmante de la SIPolicy (claves PAUTH)</span><span class="sxs-lookup"><span data-stu-id="a1977-180">Update   : Signer of the SIPolicy (PAUTH keys)</span></span>
        * <span data-ttu-id="a1977-181">Usuario: Certificados de modo de usuario (claves UMCI)</span><span class="sxs-lookup"><span data-stu-id="a1977-181">User     : User mode certificates (UMCI keys)</span></span> 
        * <span data-ttu-id="a1977-182">Kernel: Certificados de modo kernel (claves KMCI)</span><span class="sxs-lookup"><span data-stu-id="a1977-182">Kernel   : Kernel mode certificates (KMCI keys)</span></span>
    * <span data-ttu-id="a1977-183">Empaquetado: Especifique la configuración para la generación de paquetes</span><span class="sxs-lookup"><span data-stu-id="a1977-183">Packaging : Specify the settings for the package generation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1977-184">Con el fin de ayudar a probar durante el ciclo de desarrollo inicial, Microsoft ha proporcionado los certificados y claves generadas previamente en su caso.</span><span class="sxs-lookup"><span data-stu-id="a1977-184">In order to assist with testing during the initial development cycle, Microsoft has provided pre-generated keys and certificates where appropriate.</span></span>  <span data-ttu-id="a1977-185">Esto implica que los archivos binarios de Microsoft Test, desarrollo y versiones preliminares se consideran de confianza.</span><span class="sxs-lookup"><span data-stu-id="a1977-185">This implies that Microsoft Test, Development and Pre-Release binaries are considered trusted.</span></span>  <span data-ttu-id="a1977-186">Durante la creación de un producto final y generación de imágenes, asegúrese de quitar estas dirija y usar sus propias claves para garantizar que un dispositivo totalmente bloqueado.</span><span class="sxs-lookup"><span data-stu-id="a1977-186">During final product creation and image generation, be sure to remove these certifcates and use your own keys to ensure a fully locked down device.</span></span>

> [!TIP]
> <span data-ttu-id="a1977-187">Pueden permitir al incluir el certificado de Microsoft Marketplace PCA 2011 en la configuración de las aplicaciones de Microsoft App Store _settings.xml_:</span><span class="sxs-lookup"><span data-stu-id="a1977-187">The apps from Microsoft App Store can be allowed by including the Microsoft Marketplace PCA 2011 certificate in the configuration _settings.xml_:</span></span> 
    ```xml
    <Cert>db\MicrosoftMarketPlacePCA2011.cer</Cert>              <!-- Microsoft MarketPlace PCA 2011 -->
    ```

<span data-ttu-id="a1977-188">6. ejecutar los comandos siguientes para generar paquetes necesarios:</span><span class="sxs-lookup"><span data-stu-id="a1977-188">6.Execute the following commands to generate required packages:</span></span>

    ```powershell
    Import-Module .\IoTTurnkeySecurity.psm1
    # Generate the security packages for retail
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml
    (or)
    # Generate the security packages for test
    New-IoTTurnkeySecurity -ConfigFileName .\settings.xml -Test
    ```

### <a name="test-lockdown-packages"></a><span data-ttu-id="a1977-189">Probar los paquetes de bloqueo</span><span class="sxs-lookup"><span data-stu-id="a1977-189">Test Lockdown packages</span></span>
<span data-ttu-id="a1977-190">Puede probar los paquetes generados por instalarlos manualmente en un dispositivo desbloqueado mediante los pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="a1977-190">You can test the generated packages by manually installing them on a unlocked device by the following steps</span></span>

1. <span data-ttu-id="a1977-191">Flash del dispositivo con la imagen desbloqueado (imagen utilizada para el análisis en el paso anterior).</span><span class="sxs-lookup"><span data-stu-id="a1977-191">Flash the device with the unlocked image (image used for scanning in earlier step).</span></span>
2. <span data-ttu-id="a1977-192">Conectarse al dispositivo ([mediante SSH](../connect-your-device/SSH.md) o mediante [Powershell](../connect-your-device/PowerShell.md))</span><span class="sxs-lookup"><span data-stu-id="a1977-192">Connect to the device ([using SSH](../connect-your-device/SSH.md) or using [Powershell](../connect-your-device/PowerShell.md))</span></span>
3. <span data-ttu-id="a1977-193">Copie los siguientes archivos .cab en el dispositivo en un directorio, p. ej.</span><span class="sxs-lookup"><span data-stu-id="a1977-193">Copy the following .cab files to the device under a directory e.g.</span></span> `c:\OemInstall`
    * <span data-ttu-id="a1977-194">OEM.Custom.Cmd.cab</span><span class="sxs-lookup"><span data-stu-id="a1977-194">OEM.Custom.Cmd.cab</span></span>
    * <span data-ttu-id="a1977-195">OEM.Security.BitLocker.cab</span><span class="sxs-lookup"><span data-stu-id="a1977-195">OEM.Security.BitLocker.cab</span></span>
    * <span data-ttu-id="a1977-196">OEM.Security.SecureBoot.cab</span><span class="sxs-lookup"><span data-stu-id="a1977-196">OEM.Security.SecureBoot.cab</span></span>
    * <span data-ttu-id="a1977-197">OEM.Security.DeviceGuard.cab</span><span class="sxs-lookup"><span data-stu-id="a1977-197">OEM.Security.DeviceGuard.cab</span></span>
4. <span data-ttu-id="a1977-198">Iniciar el almacenamiento provisional de los paquetes generados por emitiendo los comandos siguientes</span><span class="sxs-lookup"><span data-stu-id="a1977-198">Initiate staging of the generated packages by issueing the following commands</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Custom.Cmd.cab
    ```
    <span data-ttu-id="a1977-199">Si está utilizando la imagen personalizada y, después, tendrá que *omitir* este archivo y editar manualmente el `c:\windows\system32\oemcustomization.cmd` con el contenido disponible en `Output\OEMCustomization\OEMCustomization.cmd` archivo</span><span class="sxs-lookup"><span data-stu-id="a1977-199">If you are using custom image, then you will have to *skip* this file and manually edit the `c:\windows\system32\oemcustomization.cmd` with the contents available in `Output\OEMCustomization\OEMCustomization.cmd` file</span></span>

    ```C
    applyupdate -stage c:\OemInstall\OEM.Security.BitLocker.cab
    applyupdate -stage c:\OemInstall\OEM.Security.SecureBoot.cab
    applyupdate -stage c:\OemInstall\OEM.Security.DeviceGuard.cab

5. Finally, commit the packages via

    ```C
    applyupdate -commit
    ```

6. <span data-ttu-id="a1977-200">El dispositivo se reiniciará en el sistema operativo (mostrando gears) para instalar los paquetes de actualización y se reiniciará al sistema operativo principal.</span><span class="sxs-lookup"><span data-stu-id="a1977-200">The device will reboot into update OS (showing gears) to install the packages and will reboot again to main OS.</span></span>  <span data-ttu-id="a1977-201">Una vez que el dispositivo se reinicia en MainOS, se habilitará el arranque seguro y debe exponerse a SIPolicy.</span><span class="sxs-lookup"><span data-stu-id="a1977-201">Once the device reboots back into MainOS, Secure Boot will be enabled and SIPolicy should be engaged.</span></span>
7. <span data-ttu-id="a1977-202">Reinicio del dispositivo para activar el cifrado de Bitlocker.</span><span class="sxs-lookup"><span data-stu-id="a1977-202">Reboot the device again to activate the Bitlocker encryption.</span></span>
8. <span data-ttu-id="a1977-203">Probar las características de seguridad</span><span class="sxs-lookup"><span data-stu-id="a1977-203">Test the security features</span></span>
    * <span data-ttu-id="a1977-204">**SecureBoot** : pruebe `bcdedit /debug on` , obtendrá un error que indica que el valor está protegido por la directiva de arranque seguro.</span><span class="sxs-lookup"><span data-stu-id="a1977-204">**SecureBoot** : try `bcdedit /debug on` , you will get an error stating that the value is protected by secure boot policy.</span></span>
   * <span data-ttu-id="a1977-205">**BitLocker** : Para validar que bitlocker se ha completado el cifrado, ejecute</span><span class="sxs-lookup"><span data-stu-id="a1977-205">**BitLocker** : To validate that bitlocker encryption has been completed, run</span></span><p>
        `sectask.exe -waitenableforcompletion 1`<p>
        <span data-ttu-id="a1977-206">Si se devuelve 0, significa que todas las unidades en el sistema han sido bitlockered correctamente.</span><span class="sxs-lookup"><span data-stu-id="a1977-206">If it returns 0, that means all drives on the system have been bitlockered successfully.</span></span>  <span data-ttu-id="a1977-207">Cualquier otro código de retorno es error.</span><span class="sxs-lookup"><span data-stu-id="a1977-207">Any other return code is failure.</span></span><p>
        *<span data-ttu-id="a1977-208">Sintaxis adicional</span><span class="sxs-lookup"><span data-stu-id="a1977-208">Additional Syntax</span></span>*<p>
         `-waitenableforcompletion [timeout]` <p>
        <span data-ttu-id="a1977-209">= > Espera hasta que se complete el cifrado de BitLocker en todos los volúmenes NTFS.</span><span class="sxs-lookup"><span data-stu-id="a1977-209">=> Wait until BitLocker encryption is completed on all NTFS volumes.</span></span><p>
        <span data-ttu-id="a1977-210">= > Tiempo de espera en segundos de espera para que habilitar en completarse.</span><span class="sxs-lookup"><span data-stu-id="a1977-210">=> Timeout in seconds to wait for enable to complete.</span></span><p>
        <span data-ttu-id="a1977-211">= > Si tiempo de espera no se especifica, esperará indefinidamente o hasta que se complete la habilite.</span><span class="sxs-lookup"><span data-stu-id="a1977-211">=> If timeout not specified, it will wait indefinitely or until enable completes.</span></span><p>
        <span data-ttu-id="a1977-212">Devuelve:</span><span class="sxs-lookup"><span data-stu-id="a1977-212">Returns:</span></span> <p>
        <span data-ttu-id="a1977-213">0 : El cifrado de BitLocker que se completó correctamente, el volumen está cifrada con Bitlocker.</span><span class="sxs-lookup"><span data-stu-id="a1977-213">0 : BitLocker encryption successfully completed, volume is Bitlocker encrypted.</span></span><p>
        <span data-ttu-id="a1977-214">ERROR_TIMEOUT: Tiempo de espera para la finalización, cifrado en curso.</span><span class="sxs-lookup"><span data-stu-id="a1977-214">ERROR_TIMEOUT: Timeout waiting for completion, encryption still in progress.</span></span><p>
        <span data-ttu-id="a1977-215">Error / otro código: devuelve el código de error devuelto por el servicio de la caja de seguridad de bits.</span><span class="sxs-lookup"><span data-stu-id="a1977-215">Failure/Other code: returns the failure error code returned by the bit locker service.</span></span>

    * <span data-ttu-id="a1977-216">**DeviceGuard** : Ejecute cualquier binario sin signo o un archivo binario firmado con certificado no está en la lista SIPolicy y confirme que no puede ejecutar.</span><span class="sxs-lookup"><span data-stu-id="a1977-216">**DeviceGuard** : Run any unsigned binary or a binary signed with certificate not in the SIPolicy list and confirm that it fails to run.</span></span>

### <a name="generate-lockdown-image"></a><span data-ttu-id="a1977-217">Generar imagen de bloqueo</span><span class="sxs-lookup"><span data-stu-id="a1977-217">Generate Lockdown image</span></span>

<span data-ttu-id="a1977-218">Después de comprobar que los paquetes de bloqueo de seguridad funcionan según la configuración definida anteriormente, puede incluir estos paquetes en la imagen siguiendo el siguiente les indican los pasos.</span><span class="sxs-lookup"><span data-stu-id="a1977-218">After validating that the lockdown packages are working as per the settings defined earlier, you can then include these packages into the image by following the below given steps.</span></span> <span data-ttu-id="a1977-219">Lectura [IoT fabricación guía](https://aka.ms/iotcoreguide) para obtener instrucciones de creación de imagen personalizada.</span><span class="sxs-lookup"><span data-stu-id="a1977-219">Read [IoT manufacturing guide](https://aka.ms/iotcoreguide) for custom image creation instructions.</span></span>

1. <span data-ttu-id="a1977-220">En el directorio de área de trabajo, actualice los siguientes archivos desde el directorio de salida generado anterior</span><span class="sxs-lookup"><span data-stu-id="a1977-220">In the workspace directory, update the following files from the generated output directory above</span></span>
    * <span data-ttu-id="a1977-221">SecureBoot:</span><span class="sxs-lookup"><span data-stu-id="a1977-221">SecureBoot :</span></span> `Copy ..\Output\SecureBoot\*.bin  ..\Workspace\Common\Packages\Security.SecureBoot`
      * <span data-ttu-id="a1977-222">SetVariable_db.bin</span><span class="sxs-lookup"><span data-stu-id="a1977-222">SetVariable_db.bin</span></span>
      * <span data-ttu-id="a1977-223">SetVariable_kek.bin</span><span class="sxs-lookup"><span data-stu-id="a1977-223">SetVariable_kek.bin</span></span>
      * <span data-ttu-id="a1977-224">SetVariable_pk.bin</span><span class="sxs-lookup"><span data-stu-id="a1977-224">SetVariable_pk.bin</span></span>
    * <span data-ttu-id="a1977-225">BitLocker :</span><span class="sxs-lookup"><span data-stu-id="a1977-225">BitLocker :</span></span> `Copy ..\Output\Bitlocker\*.* ..\Workspace\Common\Packages\Security.Bitlocker`
      * <span data-ttu-id="a1977-226">DETask.xml</span><span class="sxs-lookup"><span data-stu-id="a1977-226">DETask.xml</span></span>
      * <span data-ttu-id="a1977-227">Security.Bitlocker.wm.xml</span><span class="sxs-lookup"><span data-stu-id="a1977-227">Security.Bitlocker.wm.xml</span></span>
      * <span data-ttu-id="a1977-228">setup.bitlocker.cmd</span><span class="sxs-lookup"><span data-stu-id="a1977-228">setup.bitlocker.cmd</span></span>
    * <span data-ttu-id="a1977-229">DeviceGuard:</span><span class="sxs-lookup"><span data-stu-id="a1977-229">DeviceGuard :</span></span> `Copy ..\Output\DeviceGuard\*.*  ..\Workspace\Common\Packages\Security.DeviceGuard`
      * <span data-ttu-id="a1977-230">SIPolicyOn.p7b</span><span class="sxs-lookup"><span data-stu-id="a1977-230">SIPolicyOn.p7b</span></span>
      * <span data-ttu-id="a1977-231">SIPolicyOff.p7b</span><span class="sxs-lookup"><span data-stu-id="a1977-231">SIPolicyOff.p7b</span></span>
  
2. <span data-ttu-id="a1977-232">Agregar RetailOEMInput.xml y TestOEMInput.xml bajo el directorio ProductName con Id. de característica de paquete de bloqueo</span><span class="sxs-lookup"><span data-stu-id="a1977-232">Add RetailOEMInput.xml and TestOEMInput.xml under the ProductName directory with lockdown package feature ID</span></span>
    * `<Feature>SEC_BITLOCKER</Feature>`
    * `<Feature>SEC_SECUREBOOT</Feature>`
    * `<Feature>SEC_DEVICEGUARD</Feature>`
3. <span data-ttu-id="a1977-233">Volver a generar la imagen</span><span class="sxs-lookup"><span data-stu-id="a1977-233">Re-generate Image</span></span>
    * `buildpkg all` <span data-ttu-id="a1977-234">(Esto genera nuevos paquetes de bloqueo según por encima de los archivos de directiva)</span><span class="sxs-lookup"><span data-stu-id="a1977-234">(this generates new lockdown packages based on above policy files)</span></span>
    * `buildimage ProductName test(or)retail`  <span data-ttu-id="a1977-235">(Esto genera Flash.ffu nueva)</span><span class="sxs-lookup"><span data-stu-id="a1977-235">(this generates new Flash.ffu)</span></span>
4. <span data-ttu-id="a1977-236">El dispositivo con este nuevo Flash.ffu Flash y validar las características de seguridad.</span><span class="sxs-lookup"><span data-stu-id="a1977-236">Flash the device with this new Flash.ffu and validate the security features.</span></span>

<span data-ttu-id="a1977-237">Consulte [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) como un ejemplo de una configuración de la placa de bloqueo dragon.</span><span class="sxs-lookup"><span data-stu-id="a1977-237">See [SecureSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SecureSample) as an example of a lockdown dragon board configuration.</span></span>

<span data-ttu-id="a1977-238">Como alternativa, puede generar los paquetes de seguridad en el propio IoTCore Shell, consulte [agregar paquetes de seguridad](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) para obtener los detalles.</span><span class="sxs-lookup"><span data-stu-id="a1977-238">Alternatively, you can generate the security packages in the IoTCore Shell itself, see [adding security packages](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools#adding-security-packages) for the details.</span></span>


### <a name="developing-with-codesigning-enforcement-enabled"></a><span data-ttu-id="a1977-239">Desarrollo con el cumplimiento de la firma de código habilitado</span><span class="sxs-lookup"><span data-stu-id="a1977-239">Developing with CodeSigning Enforcement Enabled</span></span>

<span data-ttu-id="a1977-240">Una vez que se generan los paquetes y el bloqueo está activado, todos los archivos binarios que introdujo en la imagen durante el desarrollo deberá firmarse de forma adecuada.</span><span class="sxs-lookup"><span data-stu-id="a1977-240">Once the packages are generated and lockdown is activated, any binaries introduced into the image during development will need to be signed appropriately.</span></span> <span data-ttu-id="a1977-241">Asegúrese de que los archivos binarios de modo de usuario se firman con la clave _. \Keys\ \*\*\*-UMCI.pfx_.</span><span class="sxs-lookup"><span data-stu-id="a1977-241">Ensure that your user-mode binaries are signed with the key  _.\Keys\ \*\*\*-UMCI.pfx_.</span></span> <span data-ttu-id="a1977-242">Para la firma de modo de kernel, como para los controladores, deberá especificar sus propias claves de firmas y asegúrese de se incluyen también en el SIPolicy anterior.</span><span class="sxs-lookup"><span data-stu-id="a1977-242">For kernel-mode signing, such as for drivers, you’ll need to specify your own signing keys and make sure that they are also included in the SIPolicy above.</span></span>

### <a name="unlocking-encrypted-drives"></a><span data-ttu-id="a1977-243">Desbloquear unidades cifradas</span><span class="sxs-lookup"><span data-stu-id="a1977-243">Unlocking Encrypted Drives</span></span>

<span data-ttu-id="a1977-244">Durante el desarrollo y pruebas, al intentar leer el contenido de un dispositivo cifrado sin conexión (por ejemplo, tarjeta SD para eMMC MinnowBoardMax o de DragonBoard con el modo de almacenamiento masivo USB), 'diskpart' puede usarse para asignar una letra de unidad al volumen de datos y MainOS (vamos a Suponga v: para MainOS y w: por datos).</span><span class="sxs-lookup"><span data-stu-id="a1977-244">During development and testing, when attempting to read contents from an encrypted device offline (e.g. SD card for MinnowBoardMax or DragonBoard's eMMC through USB mass storage mode), 'diskpart' may be used to assign a drive letter to MainOS and Data volume (let's assume v: for MainOS and w: for Data).</span></span>
<span data-ttu-id="a1977-245">Los volúmenes aparecerán bloqueados y necesita desbloquea manualmente.</span><span class="sxs-lookup"><span data-stu-id="a1977-245">The volumes will appear locked and need to be manually unlocked.</span></span> <span data-ttu-id="a1977-246">Esto puede realizarse en cualquier equipo que tenga instalado el certificado de OEM DRA.pfx (incluido en el [DeviceLockDown ejemplo](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span><span class="sxs-lookup"><span data-stu-id="a1977-246">This can be done on any machine that has the OEM-DRA.pfx certificate installed (included in the [DeviceLockDown sample](https://github.com/ms-iot/security/tree/master/TurnkeySecurity)).</span></span> <span data-ttu-id="a1977-247">Instale el archivo PFX y, a continuación, ejecute los siguientes comandos desde un símbolo del sistema administrativo:</span><span class="sxs-lookup"><span data-stu-id="a1977-247">Install the PFX and then run the following commands from an administrative CMD prompt:</span></span>

* `manage-bde -unlock v: -cert -cf OEM-DRA.cer`
* `manage-bde -unlock w: -cert -cf OEM-DRA.cer`

<span data-ttu-id="a1977-248">Si necesita el contenido que se accede con frecuencia sin conexión, desbloqueo automático de BitLocker puede configurarse para los volúmenes después de la inicial desbloquear mediante los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="a1977-248">If the contents need to be frequently accessed offline, BitLocker autounlock can be set up for the volumes after the initial unlock using the following commands:</span></span>

* `manage-bde -autounlock v: -enable`
* `manage-bde -autounlock w: -enable`

### <a name="disabling-bitlocker"></a><span data-ttu-id="a1977-249">Deshabilitar BitLocker</span><span class="sxs-lookup"><span data-stu-id="a1977-249">Disabling BitLocker</span></span>

<span data-ttu-id="a1977-250">Surgiera existe una necesidad de deshabilitar temporalmente BitLocker, iniciar una sesión remota de PowerShell con el dispositivo de IoT y ejecute el siguiente comando: `sectask.exe -disable`.</span><span class="sxs-lookup"><span data-stu-id="a1977-250">Should there arise a need to temporarily disable BitLocker, initate a remote PowerShell session with your IoT device and run the following command: `sectask.exe -disable`.</span></span>  
<span data-ttu-id="a1977-251">**Nota:** Cifrado del dispositivo se volverá a habilitar, en el arranque de dispositivos posterior a menos que la tarea programada de cifrado está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="a1977-251">**Note:** Device encryption will be re-enabled on subsequent device boot unless the scheduled encryption task is disabled.</span></span>

### <a name="disabling-device-guard"></a><span data-ttu-id="a1977-252">Deshabilitación de Device Guard</span><span class="sxs-lookup"><span data-stu-id="a1977-252">Disabling Device Guard</span></span>

<span data-ttu-id="a1977-253">La secuencia de comandos de seguridad inmediata genera archivos SIPolicyOn.p7b y SIPolicyOff.p7b en la carpeta.</span><span class="sxs-lookup"><span data-stu-id="a1977-253">The turnkey security script generates SIPolicyOn.p7b and SIPolicyOff.p7b files in the folder.</span></span>
<span data-ttu-id="a1977-254">El wm.xml empaqueta el SIPolicyOn.p7b y lo coloca en el sistema que SIPolicy.p7b.</span><span class="sxs-lookup"><span data-stu-id="a1977-254">The wm.xml packages the SIPolicyOn.p7b and places it on the system as SIPolicy.p7b.</span></span>

<span data-ttu-id="a1977-255">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a1977-255">For example:</span></span>

```
C:\src\iot-adk-addonkit.db410c\TurnkeySecurity\QCDB\Output\DeviceGuard\Security.DeviceGuard.wm.xml
…
    <files>
        <file
            destinationDir="$(runtime.bootDrive)\efi\microsoft\boot"
            source="SIPolicyOn.p7b"
            name="SIPolicy.p7b" />
    </files>
..

```

<span data-ttu-id="a1977-256">Si crea un paquete que usa el archivo SIPolicyOff.p7b y lo coloca como un SIPolicy.p7b, aplicará este paquete y se desactivará la protección del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a1977-256">If you create a package that takes the SIPolicyOff.p7b file and places it as a SIPolicy.p7b, it will apply this package and the Device Guard will be turned off.</span></span>



