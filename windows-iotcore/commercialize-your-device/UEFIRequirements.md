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
# <a name="uefi-requirements"></a>Requisitos de UEFI

Los requisitos de UEFI para IoT Core son similares a otras ediciones de windows, como el escritorio. Consulte [UEFI en Windows](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-in-windows) para obtener detalles y vea específicamente [requisitos UEFI para las ediciones de Windows en las plataformas de SoC](https://docs.microsoft.com/windows-hardware/drivers/bringup/uefi-requirements-that-apply-to-all-windows-platforms). 

## <a name="acpi-design"></a>Diseño de ACPI

Consulte [Guía de diseño de ACPI de Windows para las plataformas de SoC](https://docs.microsoft.com/windows-hardware/drivers/bringup/windows-acpi-design-guide-for-soc-platforms) información detallada sobre los requisitos de ACPI de IoT Core.

## <a name="replacing-windows-boot-logo"></a>Reemplazando logotipo de arranque de Windows

Hay varias maneras de reemplazar el logotipo de arranque que se muestra en el BIOS o UEFI:

* Una consiste en UEFI, de licencia o pagar a un proveedor del fabricante board hacerlo y realizar cambios directamente en el código fuente UEFI.
* Como alternativa, en los dispositivos cuya implementación UEFI admite controladores firmados de UEFI que se puede cargar hay un ejemplo [aquí](https://github.com/Microsoft/MS_UEFI/tree/share/MsIoTSamples) que muestra cómo compilar un controlador que reemplaza el logotipo de arranque y proporcionar una tabla BGRT a bootmgr para que arranque el Windows proceso deja su logotipo en su lugar durante el arranque en lugar de reemplazarlo con el logotipo de Windows.

## <a name="smbios-settings"></a>Configuración de SMBIOS

Mínima requerida se describen en la configuración de SMBIOS [los requisitos de licencia OEM](OEMLicenseRequirements.md).

## <a name="io-bus-access"></a>Acceso de Bus de E/S

Windows IoT Core y IoT Enterprise se permiten para las aplicaciones de usuario para interactuar con los PIN de E/S del sistema. Para habilitar esta opción, se requiere configuración específica de la tabla ASL. Lectura [habilite el acceso de modo de usuario en Windows 10 IoT Core](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) para obtener más información.

## <a name="recovery-trigger"></a>Desencadenador de recuperación

Revisión [opciones de recuperación de Windows 10 IoT Core](Recovery.md) y si necesita que el desencadenador de hardware para entrar en modo de recuperación, es posible que necesite para implementar esto en las aplicaciones UEFI e invocar recuperación estableciendo el bootsequence necesario antes de windows se inicia .

A continuación se muestra el bootsequence necesario para arrancar la recuperación del sistema operativo

```
bcdedit /set {bootmgr} bootsequence {a5935ff2-32ba-4617-bf36-5ac314b3f9bf}
```
