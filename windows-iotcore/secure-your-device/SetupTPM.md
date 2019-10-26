---
title: Configuración de TPM en las plataformas sugeridas
ms.date: 09/05/2017
ms.topic: article
description: Obtenga información acerca de cómo hacer que el dispositivo sea seguro siguiendo esta guía sobre cómo configurar TPM en las plataformas sugeridas.
keywords: Windows IOT, seguridad, configuración, Módulo de plataforma segura, TPM, criptografía, claves
ms.openlocfilehash: 905d6ea829d6920a1458dbc1a4bdd16f266f7be1
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918685"
---
# <a name="setting-up-tpm-on-suggested-platforms"></a><span data-ttu-id="9f89f-104">Configuración de TPM en las plataformas sugeridas</span><span class="sxs-lookup"><span data-stu-id="9f89f-104">Setting up TPM on Suggested Platforms</span></span>

## <a name="setup-firmware-tpm-ftpm"></a><span data-ttu-id="9f89f-105">Configuración del firmware TPM (fTPM)</span><span class="sxs-lookup"><span data-stu-id="9f89f-105">Setup firmware TPM (fTPM)</span></span>
<span data-ttu-id="9f89f-106">El TPM de firmware (fTPM) requiere compatibilidad especial con el procesador/SoC y el cofTPM no se implementa actualmente en Raspberry pi2.</span><span class="sxs-lookup"><span data-stu-id="9f89f-106">Firmware TPM (fTPM) requires special Processor/SoC support and whence fTPM is not currently implemented on Raspberry Pi2.</span></span>

1. <span data-ttu-id="9f89f-107">Debe tener MBM con la versión 0,80 o superior de UEFI.</span><span class="sxs-lookup"><span data-stu-id="9f89f-107">You must have MBM with UEFI version 0.80 or above.</span></span>
2. <span data-ttu-id="9f89f-108">Habilite fTPM cambiando la siguiente configuración de UEFI:</span><span class="sxs-lookup"><span data-stu-id="9f89f-108">Enable fTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> PTT = <Enable>

3. <span data-ttu-id="9f89f-109">Asegúrese de que no tiene C:\Windows\System32\ACPITABL.dat para sTPM/dTPM (resuelva el conflicto o elimine el archivo si no es necesario).</span><span class="sxs-lookup"><span data-stu-id="9f89f-109">Ensure you do not have C:\Windows\System32\ACPITABL.dat for sTPM/dTPM (resolve the conflict/delete the file if not needed).</span></span>
4. <span data-ttu-id="9f89f-110">Compruebe que tiene la versión correcta de TPM habilitada: ejecute la [herramienta tpm 2,0](https://github.com/ms-iot/security/tree/master/Urchin/T2T) en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="9f89f-110">Verify you have the right TPM version enabled - run the [TPM 2.0 Tool](https://github.com/ms-iot/security/tree/master/Urchin/T2T) on the Windows IoT Core device.</span></span>

        C:\>t2t.exe -cap

        TBS detected 2.0 firmware TPM (fTPM) using Intel TEE.
        Capabilities:
        PT_FIXED:
        TPM_PT_FAMILY_INDICATOR = '2.0'
        TPM_PT_LEVEL = 0 (0x00000000)
        TPM_PT_REVISION = 0.93
        TPM_PT_DAY_OF_YEAR = 283 (0x0000011b)
        TPM_PT_YEAR = 2012 (0x000007dc)
        TPM_PT_MANUFACTURER = 'INTC'
        TPM_PT_VENDOR_STRING = 'Intel'
        TPM_PT_VENDOR_TPM_TYPE = 3 (0x00000003)
        TPM_PT_FIRMWARE_VERSION_1 = 1.0 (0x1.0x0)
        TPM_PT_FIRMWARE_VERSION_2 = 2.1060 (0x2.0x424)
        TPM_PT_INPUT_BUFFER = 1024 (0x00000400)
        TPM_PT_HR_TRANSIENT_MIN = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_MIN = 2 (0x00000002)
        TPM_PT_HR_LOADED_MIN = 3 (0x00000003)
        TPM_PT_ACTIVE_SESSIONS_MAX = 64 (0x00000040)
        TPM_PT_PCR_COUNT = 24 (0x00000018)
        TPM_PT_PCR_SELECT_MIN = 3 (0x00000003)
        TPM_PT_CONTEXT_GAP_MAX = 65535 (0x0000ffff)
        TPM_PT_NV_COUNTERS_MAX = 16 (0x00000010)
        TPM_PT_NV_INDEX_MAX = 2048 (0x00000800)
        TPM_PT_MEMORY = sharedNV objectCopiedToRam
        TPM_PT_CLOCK_UPDATE = 4096ms
        TPM_PT_CONTEXT_HASH = TPM_ALG_SHA256
        TPM_PT_CONTEXT_SYM = TPM_ALG_AES
        TPM_PT_CONTEXT_SYM_SIZE = 128 (0x00000080)
        TPM_PT_ORDERLY_COUNT = 255 (0x000000ff)
        TPM_PT_MAX_COMMAND_SIZE = 3968 (0x00000f80)
        TPM_PT_MAX_RESPONSE_SIZE = 3968 (0x00000f80)
        TPM_PT_MAX_DIGEST = 32 (0x00000020)
        TPM_PT_MAX_OBJECT_CONTEXT = 924 (0x0000039c)
        TPM_PT_MAX_SESSION_CONTEXT = 244 (0x000000f4)
        TPM_PT_PS_FAMILY_INDICATOR = TPM_PS_MAIN
        TPM_PT_PS_LEVEL = 0 (0x00000000)
        TPM_PT_PS_REVISION = 0
        TPM_PT_PS_DAY_OF_YEAR = 0 (0x00000000)
        TPM_PT_PS_YEAR = 0 (0x00000000)
        TPM_PT_SPLIT_MAX = 0 (0x00000000)
        TPM_PT_TOTAL_COMMANDS = 70 (0x00000046)
        TPM_PT_LIBRARY_COMMANDS = 70 (0x00000046)
        TPM_PT_VENDOR_COMMANDS = 0 (0x00000000)

        PT_VAR:
        TPM_PT_PERMANENT = lockoutAuthSet tpmGeneratedEPS
        TPM_PT_STARTUP_CLEAR = phEnable shEnable ehEnable
        TPM_PT_HR_NV_INDEX = 2 (0x00000002)
        TPM_PT_HR_LOADED = 0 (0x00000000)
        TPM_PT_HR_LOADED_AVAIL = 3 (0x00000003)
        TPM_PT_HR_ACTIVE = 0 (0x00000000)
        TPM_PT_HR_ACTIVE_AVAIL = 64 (0x00000040)
        TPM_PT_HR_TRANSIENT_AVAIL = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_AVAIL = 18 (0x00000012)
        TPM_PT_NV_COUNTERS = 2 (0x00000002)
        TPM_PT_NV_COUNTERS_AVAIL = 14 (0x0000000e)
        TPM_PT_ALGORITHM_SET = 0 (0x00000000)
        TPM_PT_LOADED_CURVES = 0 (0x00000000)
        TPM_PT_LOCKOUT_COUNTER = 0 (0x00000000)
        TPM_PT_MAX_AUTH_FAIL = 10 (0x0000000a)
        TPM_PT_LOCKOUT_INTERVAL = 2h 0" 0'
        TPM_PT_LOCKOUT_RECOVERY = 2h 0" 0'
        TPM_PT_AUDIT_COUNTER = 0

        c:\>

5. <span data-ttu-id="9f89f-111">Comprobar que el fTPM está en funcionamiento: ejecute las [pruebas unitarias de Urchin](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="9f89f-111">Verify fTPM is functioning - run the [Urchin Unit Tests](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) on the Windows IoT Core device.</span></span>  
   <span data-ttu-id="9f89f-112">Debería ver varias pruebas de SUPERAción (tenga en cuenta que algunas de las funciones no son compatibles con fTPM, por lo que se esperan algunos códigos de error):</span><span class="sxs-lookup"><span data-stu-id="9f89f-112">You should see several PASS tests (note that some of the functionality is not supported by the fTPM, so a few error codes are expected):</span></span>

        C:\>urchintest.exe
        ---SETUP----------------------------------------
        PASS...........CreateAuthorities()
        PASS...........CreateEkObject()
        PASS...........CreateSrkObject()
        (0x80280400)...CreateAndLoadAikObject()
        PASS...........CreateAndLoadKeyObject()

        ---TESTS----------------------------------------
        PASS...........TestGetCapability()
        PASS...........TestGetEntropy()
        PASS...........TestPolicySession()
        PASS...........TestSignWithPW()
        PASS...........TestSignHMAC()
        PASS...........TestSignBound()
        PASS...........TestSignSalted()
        PASS...........TestSignSaltedAndBound()
        PASS...........TestSignParameterEncryption()
        PASS...........TestSignParameterDecryption()
        PASS...........TestReadPcrWithEkSeededSession()
        (0x80280400)...TestCreateHashAndHMAC()
        (0x80280400)...TestCreateHashAndHMACSequence()
        (0x80280400)...TestSymKeyImport()
        PASS...........TestRsaKeyImport()
        (0x00000184)...TestCredentialActivation()
        PASS...........TestKeyExport()
        (0x80280400)...TestSymEncryption()
        (0x80280400)...TestCertifiedMigration()
        (0x0000014b)...TestNVIndexReadWrite()
        (0x80280400)...TestVirtualization()
        PASS...........TestObjectChangeAuth()
        PASS...........TestUnseal()
        PASS...........TestDynamicPolicies()
        (0x80280400)...TestRSADecrypt()
        (0x000002ca)...TestECDSASign()
        (0x00000184)...TestKeyAttestation()
        (0x00000184)...TestPlatformAttestation()

        ---CLEANUP--------------------------------------
        (0x000001c4)...UnloadKeyObjects()

        C:\>

## <a name="setup-discrete-tpm-dtpm"></a><span data-ttu-id="9f89f-113">Configuración de TPM discreto (dTPM)</span><span class="sxs-lookup"><span data-stu-id="9f89f-113">Setup discrete TPM (dTPM)</span></span>
<span data-ttu-id="9f89f-114">Estas instrucciones se aplican a cualquier módulo dTPM admitido en MBM, RPi2 o RPi3.</span><span class="sxs-lookup"><span data-stu-id="9f89f-114">These instructions are applicable for any dTPM module supported on MBM, RPi2, or RPi3.</span></span>

1. <span data-ttu-id="9f89f-115">Obtenga un módulo de TPM discreto y asócielo a MBM/RPi2/RPi3.</span><span class="sxs-lookup"><span data-stu-id="9f89f-115">Get a discrete TPM module and attach it to the MBM/RPi2/RPi3.</span></span>
2. <span data-ttu-id="9f89f-116">(Se aplica a MBM) Deshabilite fTPM cambiando la siguiente configuración de UEFI:</span><span class="sxs-lookup"><span data-stu-id="9f89f-116">(Applies to MBM) Disable fTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> PTT = <Disable>

3. <span data-ttu-id="9f89f-117">(Se aplica a MBM) Habilite dTPM cambiando la siguiente configuración de UEFI:</span><span class="sxs-lookup"><span data-stu-id="9f89f-117">(Applies to MBM) Enable dTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> Discrete TPM = <Enable>

4. <span data-ttu-id="9f89f-118">En función del módulo de TPM discreto que elija, identifique [aquí](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL)su tabla ACPI coincidente.</span><span class="sxs-lookup"><span data-stu-id="9f89f-118">Based on your discrete TPM module of choice, identify its matching ACPI table [here](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL).</span></span>
5. <span data-ttu-id="9f89f-119">Copie esa tabla de ACPI a MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_.</span><span class="sxs-lookup"><span data-stu-id="9f89f-119">Copy that ACPI table to MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_.</span></span>
6. <span data-ttu-id="9f89f-120">Habilite testsigning en el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="9f89f-120">Enable testsigning on the device:</span></span>

        bcdedit /set {current} integrityservices disable
        bcdedit /set testsigning on

7. <span data-ttu-id="9f89f-121">Reinicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f89f-121">Reboot the device.</span></span>
8. <span data-ttu-id="9f89f-122">Compruebe que tiene la versión correcta de TPM habilitada: ejecute la [herramienta tpm 2,0](https://github.com/ms-iot/security/tree/master/Urchin/T2T) en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="9f89f-122">Verify you have the right TPM version enabled - run the [TPM 2.0 Tool](https://github.com/ms-iot/security/tree/master/Urchin/T2T) on the Windows IoT Core device.</span></span>

        C:\>t2t.exe -cap

        TBS detected 2.0 discrete TPM (dTPM) using TIS on SPB.
        Capabilities:
        PT_FIXED:
        TPM_PT_FAMILY_INDICATOR = '2.0'
        TPM_PT_LEVEL = 0 (0x00000000)
        TPM_PT_REVISION = 1.16
        TPM_PT_DAY_OF_YEAR = 303 (0x0000012f)
        TPM_PT_YEAR = 2014 (0x000007de)
        TPM_PT_MANUFACTURER = 'NTZ'
        TPM_PT_VENDOR_STRING = 'NTZ'
        TPM_PT_VENDOR_TPM_TYPE = 17 (0x00000011)
        TPM_PT_FIRMWARE_VERSION_1 = 4.31 (0x4.0x1f)
        TPM_PT_FIRMWARE_VERSION_2 = 5378.4617 (0x1502.0x1209)
        TPM_PT_INPUT_BUFFER = 2220 (0x000008ac)
        TPM_PT_HR_TRANSIENT_MIN = 4 (0x00000004)
        TPM_PT_HR_PERSISTENT_MIN = 7 (0x00000007)
        TPM_PT_HR_LOADED_MIN = 4 (0x00000004)
        TPM_PT_ACTIVE_SESSIONS_MAX = 64 (0x00000040)
        TPM_PT_PCR_COUNT = 24 (0x00000018)
        TPM_PT_PCR_SELECT_MIN = 3 (0x00000003)
        TPM_PT_CONTEXT_GAP_MAX = 65535 (0x0000ffff)
        TPM_PT_NV_COUNTERS_MAX = 0 (0x00000000)
        TPM_PT_NV_INDEX_MAX = 1639 (0x00000667)
        TPM_PT_MEMORY = objectCopiedToRam
        TPM_PT_CLOCK_UPDATE = 4096000ms
        TPM_PT_CONTEXT_HASH = TPM_ALG_SHA256
        TPM_PT_CONTEXT_SYM = TPM_ALG_AES
        TPM_PT_CONTEXT_SYM_SIZE = 128 (0x00000080)
        TPM_PT_ORDERLY_COUNT = 255 (0x000000ff)
        TPM_PT_MAX_COMMAND_SIZE = 2220 (0x000008ac)
        TPM_PT_MAX_RESPONSE_SIZE = 2220 (0x000008ac)
        TPM_PT_MAX_DIGEST = 32 (0x00000020)
        TPM_PT_MAX_SESSION_CONTEXT = 244 (0x000000f4)
        TPM_PT_PS_FAMILY_INDICATOR = TPM_PS_PDA
        TPM_PT_PS_LEVEL = 0 (0x00000000)
        TPM_PT_PS_REVISION = 25600
        TPM_PT_PS_DAY_OF_YEAR = 0 (0x00000000)
        TPM_PT_PS_YEAR = 0 (0x00000000)
        TPM_PT_SPLIT_MAX = 128 (0x00000080)
        TPM_PT_TOTAL_COMMANDS = 101 (0x00000065)
        TPM_PT_LIBRARY_COMMANDS = 99 (0x00000063)
        TPM_PT_VENDOR_COMMANDS = 2 (0x00000002)
        TPM_PT_NV_BUFFER_MAX = 1639 (0x00000667)

        PT_VAR:
        TPM_PT_STARTUP_CLEAR = phEnable shEnable ehEnable ehEnableNV
        TPM_PT_HR_NV_INDEX = 2 (0x00000002)
        TPM_PT_HR_LOADED = 0 (0x00000000)
        TPM_PT_HR_LOADED_AVAIL = 4 (0x00000004)
        TPM_PT_HR_ACTIVE = 0 (0x00000000)
        TPM_PT_HR_ACTIVE_AVAIL = 64 (0x00000040)
        TPM_PT_HR_TRANSIENT_AVAIL = 4 (0x00000004)
        TPM_PT_HR_PERSISTENT = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_AVAIL = 4 (0x00000004)
        TPM_PT_NV_COUNTERS = 2 (0x00000002)
        TPM_PT_NV_COUNTERS_AVAIL = 30 (0x0000001e)
        TPM_PT_ALGORITHM_SET = 0 (0x00000000)
        TPM_PT_LOADED_CURVES = 3 (0x00000003)
        TPM_PT_LOCKOUT_COUNTER = 0 (0x00000000)
        TPM_PT_MAX_AUTH_FAIL = 32 (0x00000020)
        TPM_PT_LOCKOUT_INTERVAL = 2h 0" 0'
        TPM_PT_LOCKOUT_RECOVERY = 24h 0" 0'
        TPM_PT_NV_WRITE_RECOVERY = 0ms
        TPM_PT_AUDIT_COUNTER = 0

        C:\>

9. <span data-ttu-id="9f89f-123">Comprobar que el dTPM está en funcionamiento: ejecute las [pruebas unitarias de Urchin](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="9f89f-123">Verify dTPM is functioning - run the [Urchin Unit Tests](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) on the Windows IoT Core device.</span></span>  
    <span data-ttu-id="9f89f-124">Debería ver varias pruebas de SUPERAción (tenga en cuenta que es posible que algunas de las funcionalidades no sean compatibles con dTPM, por lo que se esperan algunos códigos de error):</span><span class="sxs-lookup"><span data-stu-id="9f89f-124">You should see several PASS tests (note that some of the functionality may not be supported by the dTPM, so a few error codes are expected):</span></span>

        C:\>urchintest.exe

        ---SETUP----------------------------------------
        PASS...........CreateAuthorities()
        PASS...........CreateEkObject()
        PASS...........CreateSrkObject()
        PASS...........CreateAndLoadAikObject()
        PASS...........CreateAndLoadKeyObject()

        ---TESTS----------------------------------------
        PASS...........TestGetCapability()
        PASS...........TestGetEntropy()
        PASS...........TestPolicySession()
        PASS...........TestSignWithPW()
        PASS...........TestSignHMAC()
        PASS...........TestSignBound()
        PASS...........TestSignSalted()
        PASS...........TestSignSaltedAndBound()
        (0xc000000d)...TestSignParameterEncryption()
        PASS...........TestSignParameterDecryption()
        PASS...........TestReadPcrWithEkSeededSession()
        PASS...........TestCreateHashAndHMAC()
        PASS...........TestCreateHashAndHMACSequence()
        PASS...........TestSymKeyImport()
        (0xc000000d)...TestRsaKeyImport()
        PASS...........TestCredentialActivation()
        PASS...........TestKeyExport()
        (0x00000182)...TestSymEncryption()
        PASS...........TestCertifiedMigration()
        PASS...........TestNVIndexReadWrite()
        (0x80280400)...TestVirtualization()
        PASS...........TestObjectChangeAuth()
        PASS...........TestUnseal()
        PASS...........TestDynamicPolicies()
        PASS...........TestRSADecrypt()
        PASS...........TestECDSASign()
        (0xc000000d)...TestKeyAttestation()
        (0xc000000d)...TestPlatformAttestation()

        ---CLEANUP--------------------------------------
        PASS...........UnloadKeyObjects()

        C:\>

## <a name="enable-and-verify-software-tpm-stpm"></a><span data-ttu-id="9f89f-125">Habilitar y comprobar el TPM de software (sTPM)</span><span class="sxs-lookup"><span data-stu-id="9f89f-125">Enable and verify software TPM (sTPM)</span></span>  
<span data-ttu-id="9f89f-126">Tenga en cuenta que **sTPM está pensado únicamente para fines de desarrollo y no proporciona ninguna ventaja de seguridad real**.</span><span class="sxs-lookup"><span data-stu-id="9f89f-126">Note that **sTPM is intended for development purposes only and does not provide any real security benefits**.</span></span>

1. <span data-ttu-id="9f89f-127">(Se aplica a MBM) Deshabilite fTPM cambiando la siguiente configuración de UEFI:</span><span class="sxs-lookup"><span data-stu-id="9f89f-127">(Applies to MBM) Disable fTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> PTT = <Disable>

2. <span data-ttu-id="9f89f-128">(Se aplica a MBM) Habilite dTPM cambiando la siguiente configuración de UEFI:</span><span class="sxs-lookup"><span data-stu-id="9f89f-128">(Applies to MBM) Enable dTPM by changing the following UEFI settings:</span></span>

        Device Manager -> System Setup -> Security Configuration -> Discrete TPM = <Enable>

3. <span data-ttu-id="9f89f-129">Habilite testsigning en el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="9f89f-129">Enable testsigning on the device:</span></span>

        bcdedit /set {current} integrityservices disable
        bcdedit /set testsigning on

4. <span data-ttu-id="9f89f-130">Copie la tabla ACPI desde [aquí](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL/fTPMSim) a mbm/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_.</span><span class="sxs-lookup"><span data-stu-id="9f89f-130">Copy the ACPI table from [here](https://github.com/ms-iot/security/tree/master/TPM-ACPITABL/fTPMSim) to MBM/RPi2/RPi3 _C:\Windows\System32\ACPITABL.dat_.</span></span>
5. <span data-ttu-id="9f89f-131">Reinicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9f89f-131">Reboot the device.</span></span>
6. <span data-ttu-id="9f89f-132">Compruebe que tiene la versión correcta de TPM habilitada: ejecute la [herramienta tpm 2,0](https://github.com/ms-iot/security/tree/master/Urchin/T2T) en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="9f89f-132">Verify you have the right TPM version enabled - run the [TPM 2.0 Tool](https://github.com/ms-iot/security/tree/master/Urchin/T2T) on the Windows IoT Core device.</span></span>

        C:\>t2t.exe -cap
        TBS detected 2.0 simulated TPM (sTPM).
        Capabilities:
        PT_FIXED:
        TPM_PT_FAMILY_INDICATOR = '2.0'
        TPM_PT_LEVEL = 0 (0x00000000)  
        TPM_PT_REVISION = 1.15
        TPM_PT_DAY_OF_YEAR = 163 (0x000000a3)
        TPM_PT_YEAR = 2014 (0x000007de)
        TPM_PT_MANUFACTURER = 'MSFT'
        TPM_PT_VENDOR_STRING = 'IoT Software TPM'
        TPM_PT_VENDOR_TPM_TYPE = 1 (0x00000001)
        TPM_PT_FIRMWARE_VERSION_1 = 8213.275 (0x2015.0x113)
        TPM_PT_FIRMWARE_VERSION_2 = 21.18466 (0x15.0x4822)
        TPM_PT_INPUT_BUFFER = 1024 (0x00000400)
        TPM_PT_HR_TRANSIENT_MIN = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_MIN = 2 (0x00000002)
        TPM_PT_HR_LOADED_MIN = 3 (0x00000003)
        TPM_PT_ACTIVE_SESSIONS_MAX = 64 (0x00000040)
        TPM_PT_PCR_COUNT = 24 (0x00000018)
        TPM_PT_PCR_SELECT_MIN = 3 (0x00000003)
        TPM_PT_CONTEXT_GAP_MAX = 65535 (0x0000ffff)
        TPM_PT_NV_COUNTERS_MAX = 0 (0x00000000)
        TPM_PT_NV_INDEX_MAX = 2048 (0x00000800)
        TPM_PT_MEMORY = sharedNV objectCopiedToRam
        TPM_PT_CLOCK_UPDATE = 4096ms
        TPM_PT_CONTEXT_HASH = TPM_ALG_SHA256
        TPM_PT_CONTEXT_SYM = TPM_ALG_AES
        TPM_PT_CONTEXT_SYM_SIZE = 256 (0x00000100)
        TPM_PT_ORDERLY_COUNT = 255 (0x000000ff)
        TPM_PT_MAX_COMMAND_SIZE = 4096 (0x00001000)
        TPM_PT_MAX_RESPONSE_SIZE = 4096 (0x00001000)
        TPM_PT_MAX_DIGEST = 48 (0x00000030)
        TPM_PT_MAX_OBJECT_CONTEXT = 1520 (0x000005f0)
        TPM_PT_MAX_SESSION_CONTEXT = 308 (0x00000134)
        TPM_PT_PS_FAMILY_INDICATOR = TPM_PS_MAIN
        TPM_PT_PS_LEVEL = 0 (0x00000000)
        TPM_PT_PS_REVISION = 0
        TPM_PT_PS_DAY_OF_YEAR = 0 (0x00000000)
        TPM_PT_PS_YEAR = 0 (0x00000000)
        TPM_PT_SPLIT_MAX = 128 (0x00000080)
        TPM_PT_TOTAL_COMMANDS = 106 (0x0000006a)
        TPM_PT_LIBRARY_COMMANDS = 105 (0x00000069)
        TPM_PT_VENDOR_COMMANDS = 1 (0x00000001)

        PT_VAR:
        TPM_PT_PERMANENT = lockoutAuthSet tpmGeneratedEPS
        TPM_PT_STARTUP_CLEAR = phEnable shEnable ehEnable ehEnableNV
        TPM_PT_HR_NV_INDEX = 2 (0x00000002)
        TPM_PT_HR_LOADED = 0 (0x00000000)
        TPM_PT_HR_LOADED_AVAIL = 3 (0x00000003)
        TPM_PT_HR_ACTIVE = 0 (0x00000000)
        TPM_PT_HR_ACTIVE_AVAIL = 64 (0x00000040)
        TPM_PT_HR_TRANSIENT_AVAIL = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT = 3 (0x00000003)
        TPM_PT_HR_PERSISTENT_AVAIL = 5 (0x00000005)
        TPM_PT_NV_COUNTERS = 2 (0x00000002)
        TPM_PT_NV_COUNTERS_AVAIL = 31 (0x0000001f)
        TPM_PT_ALGORITHM_SET = 0 (0x00000000)
        TPM_PT_LOADED_CURVES = 3 (0x00000003)
        TPM_PT_LOCKOUT_COUNTER = 3 (0x00000003)
        TPM_PT_MAX_AUTH_FAIL = 32 (0x00000020)
        TPM_PT_LOCKOUT_INTERVAL = 2h 0" 0'
        TPM_PT_LOCKOUT_RECOVERY = 24h 0" 0'
        TPM_PT_AUDIT_COUNTER = 0

        C:\>

7. <span data-ttu-id="9f89f-133">Comprobar que el sTPM está en funcionamiento: ejecute las [pruebas unitarias de Urchin](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="9f89f-133">Verify sTPM is functioning - run the [Urchin Unit Tests](https://github.com/ms-iot/security/tree/master/Urchin/UrchinTest) on the Windows IoT Core device.</span></span>  
   <span data-ttu-id="9f89f-134">Debería ver varias pruebas de SUPERAción (tenga en cuenta que algunas de las funciones no son compatibles con sTPM, por lo que se esperan algunos códigos de error):</span><span class="sxs-lookup"><span data-stu-id="9f89f-134">You should see several PASS tests (note that some of the functionality is not supported by the sTPM, so a few error codes are expected):</span></span>

        C:\>urchintest.exe
        ---SETUP----------------------------------------
        PASS...........CreateAuthorities()
        PASS...........CreateEkObject()
        PASS...........CreateSrkObject()
        PASS...........CreateAndLoadAikObject()
        PASS...........CreateAndLoadKeyObject()

        ---TESTS----------------------------------------
        PASS...........TestGetCapability()
        PASS...........TestGetEntropy()
        PASS...........TestPolicySession()
        PASS...........TestSignWithPW()
        PASS...........TestSignHMAC()
        PASS...........TestSignBound()
        PASS...........TestSignSalted()
        PASS...........TestSignSaltedAndBound()
        (0xc000000d)...TestSignParameterEncryption()
        PASS...........TestSignParameterDecryption()
        PASS...........TestReadPcrWithEkSeededSession()
        PASS...........TestCreateHashAndHMAC()
        PASS...........TestCreateHashAndHMACSequence()
        PASS...........TestSymKeyImport()
        (0xc000000d)...TestRsaKeyImport()
        PASS...........TestCredentialActivation()
        PASS...........TestKeyExport()
        (0x00000182)...TestSymEncryption()
        PASS...........TestCertifiedMigration()
        PASS...........TestNVIndexReadWrite()
        (0x80280400)...TestVirtualization()
        PASS...........TestObjectChangeAuth()
        PASS...........TestUnseal()
        PASS...........TestDynamicPolicies()
        PASS...........TestECDSASign())
        PASS........
        (0xc000000d)...TestKeyAttestation()
        (0xc000000d)...TestPlatformAttestation()

        ---CLEANUP--------------------------------------
        PASS...........UnloadKeyObjects()

        C:\>
