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
# <a name="uefi-requirements"></a>Requisitos de UEFI

Los requisitos de UEFI para IoT Core son similares a otras ediciones de Windows como Desktop. Consulte [UEFI en Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) para obtener más información y consulte específicamente [requisitos de UEFI para las ediciones de Windows en las plataformas de SOC](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms). 

## <a name="acpi-design"></a>Diseño de ACPI

Consulte la [Guía de diseño de Windows ACPI para plataformas de SOC](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) para obtener información detallada sobre los requisitos de ACPI para IOT Core.

## <a name="replacing-windows-boot-logo"></a>Reemplazar el logotipo de arranque de Windows

Hay varias maneras de reemplazar el logotipo de arranque que muestra el BIOS o UEFI:

* Una manera es conceder una licencia a la UEFI o pagar a un proveedor de fabricantes de paneles para hacerlo y realizar cambios directamente en el código fuente UEFI.
* Como alternativa, en los dispositivos cuya implementación de UEFI admite controladores UEFI cargados con firma, hay un ejemplo que muestra cómo crear un [controlador que reemplaza](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) el logotipo de arranque y proporciona una tabla BGRT a BOOTMGR para que el proceso de arranque de Windows abandone el logotipo. en su lugar durante el arranque en lugar de reemplazarlo por el logotipo de Windows.

## <a name="smbios-settings"></a>Configuración de SMBIOS

La configuración mínima requerida de SMBIOS se describe en [requisitos de licencia de OEM](OEMLicenseRequirements.md).

## <a name="io-bus-access"></a>Acceso a bus de e/s

Windows IoT Core y IoT Enterprise permiten a las aplicaciones de usuario interactuar con los pin de e/s del sistema. Para habilitar esto, se requiere una configuración específica en la tabla ASL. Para obtener más información, consulte [Habilitar el acceso de modo de usuario en Windows 10 IOT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) .

## <a name="recovery-trigger"></a>Desencadenador de recuperación

Revise [las opciones de recuperación de Windows 10 IOT Core](Recovery.md) y, si necesita desencadenador de hardware para entrar en el modo de recuperación, puede que necesite implementar esto en las aplicaciones UEFI e invocar la recuperación estableciendo el valor de BOOTSEQUENCE requerido antes de que arranque Windows.

A continuación se proporciona el BOOTSEQUENCE necesario para arrancar en el sistema operativo de recuperación

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
