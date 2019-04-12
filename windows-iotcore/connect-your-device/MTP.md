---
title: Protocolo de transferencia multimedia
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
description: Obtenga información sobre cómo habilitar la característica opcional de protocolo de transferencia multimedia (MTP) transferir archivos a y desde los dispositivos a través de USB.
keywords: medios de Windows iot, MTP, transferencia de protocolo de transferencia de archivos, los dispositivos
ms.openlocfilehash: 72856617c8d49a1b06eadd13ab5fb085340d2ed4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514263"
---
# <a name="media-transfer-protocol"></a>Protocolo de transferencia multimedia
El protocolo de transferencia multimedia (MTP) le permite transferir archivos a y desde el dispositivo Windows 10 IoT Core a través de USB. Permite el acceso al almacenamiento interno del dispositivo y la tarjeta SD, si está presente.

La característica forma parte de los Kits de núcleo de IoT, que puede descargarse e instalarse desde el [los paquetes de Windows 10 IoT Core](https://www.microsoft.com/en-us/download/details.aspx?id=55031).

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>Cómo instalar la característica MTP en un dispositivo que ejecuta Windows 10 IoT Core

### <a name="provisioning-the-device-with-required-packages"></a>Aprovisionamiento del dispositivo con los paquetes necesarios

1. Iniciar [Powershell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md) y tener acceso a un dispositivo que ejecuta Windows 10 IoT Core.
2. Desde Powershell o SSH, realice lo siguiente:
    1. Cree una carpeta temporal del equipo de destino (por ejemplo, `C:\MTPTemp`).
    2. Según la arquitectura del dispositivo, copie los siguientes paquetes desde su PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`) a `C:\MTPTemp`:
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. Ejecute estos comandos desde `C:\MTPTemp` para instalar los paquetes a la imagen de sistema de su dispositivo de IoT:
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. El dispositivo arranque en el sistema operativo de la actualización, instale la característica MTP y para el MainOS reiniciar el equipo.

### <a name="enabling-the-mtp-usb-interface"></a>Habilitación de la interfaz de MTP USB

Una vez que el dispositivo vuelve a la MainOS, la configuración de USBFN debe actualizarse para incluir MTP. Para ello, deberá agregar MTP a las interfaces enumeradas por USBFN.
El [configuración del registro USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) artículo explica los detalles de configuración de USB.

Aunque puede modificar la configuración predeterminada de USBFN disponible bajo la `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` clave, se recomienda se definir las suyas propias, como no se sobrescriban por las actualizaciones del sistema.

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>Crear una nueva configuración de USBFN con la interfaz MTP

Siga estos pasos para agregar una nueva configuración con MTP:
1. Agregue una nueva clave en `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`. Ejemplo: `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`.
2. En la nueva clave cree una `REG_MULTI_SZ` valor `InterfaceList` igual a `MTP`.
3. En la misma clave, cree un `REG_BINARY` valor `MSOSCompatIdDescriptor` igual a `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`.
4. En `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` agregar un nuevo `REG_SZ` valor `CurrentConfiguration` igual al nombre de la clave recién creada. En este caso sería `MyConfiguration`.
5. [**Opcional**] bajo `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` agregar un nuevo `REG_DWORD` valor `IncludeDefaultCfg` igual a 1. Esto hará que el controlador USB para enumerar las interfaces de forma predeterminada junto con MTP.

> [!NOTE]
> Si ya está usando una configuración personalizada, que tendrá que modificarla en lugar de crear uno nuevo.

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>Adición de la interfaz MTP a una configuración existente

Siga estos pasos para agregar MTP a una configuración USBFN existente:
1. Busque la configuración actual mediante la comprobación de la `CurrentConfiguration` valor bajo `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`. Si el valor está presente, se puede encontrar la configuración actual en `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`. Si no se encuentra en `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`.
2. En la clave de configuración actual, agregue `\0MTP` al valor de `InterfaceList`. El ***\0*** parte se utiliza como el tipo de `InterfaceList` es `REG_MULTI_SZ` y requiere este separador entre los valores.
3. Modificar el `MSOSCompatIdDescriptor` valor para incluir el descriptor de MTP. Para crear un descriptor válido que contiene todas las interfaces actualmente en el `InterfaceList` valor, siga la documentación de instrucciones disponible en la parte inferior de [esta página](https://msdn.microsoft.com/windows/hardware/gg463179.aspx). *OS_Desc_CompatID.doc* ofrece una explicación del formato del descriptor y un ejemplo de inclusión de varias interfaces en el descriptor. Identificadores de Sub compatibles y compatibles de MTP también están disponibles en la misma página y se usan en uno de los ejemplos.

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>Cómo incluir MTP en su FFU personalizado

1. Agregar **IOT_MTP** Id. de característica en el archivo de entrada de OEM. Esto es equivalente a seguir los pasos de la "[**aprovisionar el dispositivo con los paquetes necesarios**](#provisioning-the-device-with-required-packages)" sección.
2. Asegúrese de aplicar los mismos cambios del registro como se mencionó en la "[**crear una nueva configuración de USBFN con la interfaz MTP**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)" sección. Siga [estas instrucciones](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) para obtener información sobre cómo aplicar los cambios del registro a un FFU.
3. Cree el image\FFU. Lectura [en este artículo](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para obtener instrucciones.

> [!WARNING]
> No se debe intentar modificar la configuración predeterminada mediante la personalización de FFU. Las entradas definidas por el sistema pueden actualizar o cambiar una actualización del sistema y se perderá cualquier configuración personalizada.

## <a name="how-to-setup-the-mtp-sd-card-filter"></a>Cómo configurar el filtro de la tarjeta SD MTP

De forma predeterminada MTP enumerará todo el contenido de una tarjeta SD, si está presente en el dispositivo. Sin embargo, es posible limitar esta enumeración en una subcarpeta específica. Para ello, debe agregar un valor del registro `MTPSDFolderFilter` bajo la clave del registro `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`.
El valor es de tipo `REG_SZ` y debe contener una ruta de acceso relativa a la carpeta que le gustaría MTP a enumerar. La carpeta obtener creará automáticamente si aún no existe.

Rutas de acceso de ejemplo:
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory.

> [!WARNING]
> No use una ruta de acceso absoluta que contiene la letra de unidad como `C:\Some\Folder\Path` -Esto podría impedir que la tarjeta SD está enumerando.

Consulte [este vínculo](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) para obtener más información acerca de cómo personalizar la imagen con las entradas del Registro específica.
