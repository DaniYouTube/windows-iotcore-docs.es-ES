---
title: Requisitos de UEFI
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los requisitos de UEFI para Windows 10 IoT Core OS.
keywords: Windows iot, creación de imágenes, las personalizaciones de imagen, las personalizaciones de OEM, UEFI
ms.openlocfilehash: efd8f104d61667b443d48e1722e26789a490196b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514244"
---
# <a name="uefi-requirements"></a><span data-ttu-id="75654-104">Requisitos de UEFI</span><span class="sxs-lookup"><span data-stu-id="75654-104">UEFI Requirements</span></span>

<span data-ttu-id="75654-105">Los requisitos de UEFI para IoT Core son similares a otras ediciones de windows, como el escritorio.</span><span class="sxs-lookup"><span data-stu-id="75654-105">The UEFI requirements for IoT Core are similar to other windows editions like desktop.</span></span> <span data-ttu-id="75654-106">Consulte [UEFI en Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) para obtener detalles y vea específicamente [requisitos UEFI para las ediciones de Windows en las plataformas de SoC](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span><span class="sxs-lookup"><span data-stu-id="75654-106">See [UEFI in Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) for details and specifically see [UEFI requirements for Windows editions on SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms).</span></span> 

## <a name="acpi-design"></a><span data-ttu-id="75654-107">Diseño de ACPI</span><span class="sxs-lookup"><span data-stu-id="75654-107">ACPI Design</span></span>

<span data-ttu-id="75654-108">Consulte [Guía de diseño de ACPI de Windows para las plataformas de SoC](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) información detallada sobre los requisitos de ACPI de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="75654-108">See [Windows ACPI design guide for SoC platforms](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) for the details on the ACPI requirements for IoT Core.</span></span>

## <a name="replacing-windows-boot-logo"></a><span data-ttu-id="75654-109">Reemplazando logotipo de arranque de Windows</span><span class="sxs-lookup"><span data-stu-id="75654-109">Replacing Windows Boot Logo</span></span>

<span data-ttu-id="75654-110">Hay varias maneras de reemplazar el logotipo de arranque que se muestra en el BIOS o UEFI:</span><span class="sxs-lookup"><span data-stu-id="75654-110">There are multiple ways to replace the boot logo that is displayed by the BIOS or UEFI:</span></span>

* <span data-ttu-id="75654-111">Una consiste en UEFI, de licencia o pagar a un proveedor del fabricante board hacerlo y realizar cambios directamente en el código fuente UEFI.</span><span class="sxs-lookup"><span data-stu-id="75654-111">One way is to license the UEFI, or pay a board manufacturer vendor to do so, and make changes directly to the UEFI source code.</span></span>
* <span data-ttu-id="75654-112">Como alternativa, en los dispositivos cuya implementación UEFI admite controladores firmados de UEFI que se puede cargar hay un ejemplo [aquí](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) que muestra cómo compilar un controlador que reemplaza el logotipo de arranque y proporcionar una tabla BGRT a bootmgr para que arranque el Windows proceso deja su logotipo en su lugar durante el arranque en lugar de reemplazarlo con el logotipo de Windows.</span><span class="sxs-lookup"><span data-stu-id="75654-112">Alternatively, on devices whose UEFI implementation supports signed loadable UEFI drivers there is a sample [here](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) that shows how to build a driver that replaces the boot logo and supply a BGRT table to bootmgr so that the Windows boot process leaves your logo in place during boot instead of replacing it with the Windows logo.</span></span>

## <a name="smbios-settings"></a><span data-ttu-id="75654-113">Configuración de SMBIOS</span><span class="sxs-lookup"><span data-stu-id="75654-113">SMBIOS settings</span></span>

<span data-ttu-id="75654-114">Mínima requerida se describen en la configuración de SMBIOS [los requisitos de licencia OEM](OEMLicenseRequirements.md).</span><span class="sxs-lookup"><span data-stu-id="75654-114">Minimum required SMBIOS settings are described in [OEM License Requirements](OEMLicenseRequirements.md).</span></span>

## <a name="io-bus-access"></a><span data-ttu-id="75654-115">Acceso de Bus de E/S</span><span class="sxs-lookup"><span data-stu-id="75654-115">I/O Bus Access</span></span>

<span data-ttu-id="75654-116">Windows IoT Core y IoT Enterprise se permiten para las aplicaciones de usuario para interactuar con los PIN de E/S del sistema.</span><span class="sxs-lookup"><span data-stu-id="75654-116">Windows IoT Core and IoT Enterprise allow for user applications to interface with system I/O pins.</span></span> <span data-ttu-id="75654-117">Para habilitar esta opción, se requiere configuración específica de la tabla ASL.</span><span class="sxs-lookup"><span data-stu-id="75654-117">To enable this, specific configuration is required in the ASL table.</span></span> <span data-ttu-id="75654-118">Lectura [habilite el acceso de modo de usuario en Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="75654-118">Read [Enable user mode access on Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) for more information.</span></span>

## <a name="recovery-trigger"></a><span data-ttu-id="75654-119">Desencadenador de recuperación</span><span class="sxs-lookup"><span data-stu-id="75654-119">Recovery Trigger</span></span>

<span data-ttu-id="75654-120">Revisión [opciones de recuperación de Windows 10 IoT Core](Recovery.md) y si necesita que el desencadenador de hardware para entrar en modo de recuperación, es posible que necesite para implementar esto en las aplicaciones UEFI e invocar recuperación estableciendo el bootsequence necesario antes de windows se inicia .</span><span class="sxs-lookup"><span data-stu-id="75654-120">Review [Windows 10 IoT Core Recovery Options](Recovery.md) and if you require hardware trigger to get into recovery mode, you may require to implement this in the UEFI apps and invoke recovery by setting the required bootsequence before windows boots.</span></span>

<span data-ttu-id="75654-121">A continuación se muestra el bootsequence necesario para arrancar la recuperación del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="75654-121">The bootsequence required to boot into the recovery OS is given below</span></span>

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
