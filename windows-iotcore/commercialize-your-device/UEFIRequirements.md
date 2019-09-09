---
title: Requisitos de UEFI
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Conozca los requisitos de UEFI para el sistema operativo Windows 10 IoT Core.
keywords: Windows IOT, creación de imágenes, personalizaciones de imágenes, personalizaciones de OEM, UEFI
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170413"
---
# <a name="uefi-requirements"></a><span data-ttu-id="7a30c-104">Requisitos de UEFI</span><span class="sxs-lookup"><span data-stu-id="7a30c-104">UEFI Requirements</span></span>

<span data-ttu-id="7a30c-105">Los requisitos de UEFI para IoT Core son similares a otras ediciones de Windows como Desktop.</span><span class="sxs-lookup"><span data-stu-id="7a30c-105">The UEFI requirements for IoT Core are similar to other windows editions like desktop.</span></span> <span data-ttu-id="7a30c-106">Consulte [UEFI en Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) para obtener más información y consulte específicamente [requisitos de UEFI para las ediciones de Windows en las plataformas de SOC](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span><span class="sxs-lookup"><span data-stu-id="7a30c-106">See [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) for details and specifically see [UEFI requirements for Windows editions on SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span></span> 

## <a name="acpi-design"></a><span data-ttu-id="7a30c-107">Diseño de ACPI</span><span class="sxs-lookup"><span data-stu-id="7a30c-107">ACPI Design</span></span>

<span data-ttu-id="7a30c-108">Consulte la [Guía de diseño de Windows ACPI para plataformas de SOC](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) para obtener información detallada sobre los requisitos de ACPI para IOT Core.</span><span class="sxs-lookup"><span data-stu-id="7a30c-108">See [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) for the details on the ACPI requirements for IoT Core.</span></span>

## <a name="replacing-windows-boot-logo"></a><span data-ttu-id="7a30c-109">Reemplazar el logotipo de arranque de Windows</span><span class="sxs-lookup"><span data-stu-id="7a30c-109">Replacing Windows Boot Logo</span></span>

<span data-ttu-id="7a30c-110">Hay varias maneras de reemplazar el logotipo de arranque que muestra el BIOS o UEFI:</span><span class="sxs-lookup"><span data-stu-id="7a30c-110">There are multiple ways to replace the boot logo that is displayed by the BIOS or UEFI:</span></span>

* <span data-ttu-id="7a30c-111">Una manera es conceder una licencia a la UEFI o pagar a un proveedor de fabricantes de paneles para hacerlo y realizar cambios directamente en el código fuente UEFI.</span><span class="sxs-lookup"><span data-stu-id="7a30c-111">One way is to license the UEFI, or pay a board manufacturer vendor to do so, and make changes directly to the UEFI source code.</span></span>
* <span data-ttu-id="7a30c-112">Como alternativa, en los dispositivos cuya implementación de UEFI admite controladores UEFI cargados con firma, hay un ejemplo que muestra cómo crear un [controlador que reemplaza](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) el logotipo de arranque y proporciona una tabla BGRT a BOOTMGR para que el proceso de arranque de Windows abandone el logotipo. en su lugar durante el arranque en lugar de reemplazarlo por el logotipo de Windows.</span><span class="sxs-lookup"><span data-stu-id="7a30c-112">Alternatively, on devices whose UEFI implementation supports signed loadable UEFI drivers there is a sample [here](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) that shows how to build a driver that replaces the boot logo and supply a BGRT table to bootmgr so that the Windows boot process leaves your logo in place during boot instead of replacing it with the Windows logo.</span></span>

## <a name="smbios-settings"></a><span data-ttu-id="7a30c-113">Configuración de SMBIOS</span><span class="sxs-lookup"><span data-stu-id="7a30c-113">SMBIOS settings</span></span>

<span data-ttu-id="7a30c-114">La configuración mínima requerida de SMBIOS se describe en [requisitos de licencia de OEM](OEMLicenseRequirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a30c-114">Minimum required SMBIOS settings are described in [OEM License Requirements](OEMLicenseRequirements.md).</span></span>

## <a name="io-bus-access"></a><span data-ttu-id="7a30c-115">Acceso a bus de e/s</span><span class="sxs-lookup"><span data-stu-id="7a30c-115">I/O Bus Access</span></span>

<span data-ttu-id="7a30c-116">Windows IoT Core y IoT Enterprise permiten a las aplicaciones de usuario interactuar con los pin de e/s del sistema.</span><span class="sxs-lookup"><span data-stu-id="7a30c-116">Windows IoT Core and IoT Enterprise allow for user applications to interface with system I/O pins.</span></span> <span data-ttu-id="7a30c-117">Para habilitar esto, se requiere una configuración específica en la tabla ASL.</span><span class="sxs-lookup"><span data-stu-id="7a30c-117">To enable this, specific configuration is required in the ASL table.</span></span> <span data-ttu-id="7a30c-118">Para obtener más información, consulte [Habilitar el acceso de modo de usuario en Windows 10 IOT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) .</span><span class="sxs-lookup"><span data-stu-id="7a30c-118">Read [Enable user mode access on Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) for more information.</span></span>

## <a name="recovery-trigger"></a><span data-ttu-id="7a30c-119">Desencadenador de recuperación</span><span class="sxs-lookup"><span data-stu-id="7a30c-119">Recovery Trigger</span></span>

<span data-ttu-id="7a30c-120">Revise [las opciones de recuperación de Windows 10 IOT Core](Recovery.md) y, si necesita desencadenador de hardware para entrar en el modo de recuperación, puede que necesite implementar esto en las aplicaciones UEFI e invocar la recuperación estableciendo el valor de BOOTSEQUENCE requerido antes de que arranque Windows.</span><span class="sxs-lookup"><span data-stu-id="7a30c-120">Review [Windows 10 IoT Core Recovery Options](Recovery.md) and if you require hardware trigger to get into recovery mode, you may require to implement this in the UEFI apps and invoke recovery by setting the required bootsequence before windows boots.</span></span>

<span data-ttu-id="7a30c-121">A continuación se proporciona el BOOTSEQUENCE necesario para arrancar en el sistema operativo de recuperación</span><span class="sxs-lookup"><span data-stu-id="7a30c-121">The bootsequence required to boot into the recovery OS is given below</span></span>

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
