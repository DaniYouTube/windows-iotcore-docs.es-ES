---
title: Protocolo de transferencia de medios
author: PawelWMS
ms.author: pawelwi
ms.date: 12/06/2017
ms.topic: article
description: Obtenga información acerca de cómo habilitar la característica opcional de protocolo de transferencia multimedia (MTP) para transferir archivos desde y hacia los dispositivos a través de USB.
keywords: Windows IOT, MTP, protocolo de transferencia multimedia, transferencia de archivos, dispositivos
ms.openlocfilehash: 72856617c8d49a1b06eadd13ab5fb085340d2ed4
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168043"
---
# <a name="media-transfer-protocol"></a>Protocolo de transferencia de medios
El protocolo de transferencia multimedia (MTP) permite transferir archivos hacia y desde el dispositivo de Windows 10 IoT Core a través de USB. Permite el acceso al almacenamiento interno del dispositivo y a la tarjeta SD, si está presente.

La característica forma parte de los kits de IoT Core, que se pueden descargar e instalar desde los [paquetes de Windows 10 IOT Core](https://www.microsoft.com/en-us/download/details.aspx?id=55031).

## <a name="how-to-install-the-mtp-feature-on-a-device-running-windows-10-iot-core"></a>Cómo instalar la característica MTP en un dispositivo que ejecuta Windows 10 IoT Core

### <a name="provisioning-the-device-with-required-packages"></a>Aprovisionamiento del dispositivo con los paquetes necesarios

1. Inicie [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md) y acceda a su dispositivo con Windows 10 IOT Core.
2. En PowerShell o SSH, haga lo siguiente:
    1. Cree una carpeta temporal en el equipo de destino (por `C:\MTPTemp`ejemplo,).
    2. En función de la arquitectura del dispositivo, copie los siguientes paquetes desde su PC`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre`() `C:\MTPTemp`a:
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
    3. Ejecute estos comandos desde `C:\MTPTemp` para instalar los paquetes en la imagen del sistema de su dispositivo IOT:
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-OneCoreUAP-Mtp-UserService-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package.cab`
        * `ApplyUpdate.exe -stage Microsoft-WindowsStorSvc-API-Schema-Extension-Package_Lang_en-US.cab`
        * `ApplyUpdate.exe -commit`
3. El dispositivo arrancará en el sistema operativo de actualización, instalará la característica MTP y se reiniciará en el archivo principal.

### <a name="enabling-the-mtp-usb-interface"></a>Habilitación de la interfaz USB MTP

Una vez que el dispositivo vuelve a los principales, la configuración de USBFN todavía debe actualizarse para incluir MTP. Para ello, tendrá que agregar MTP a las interfaces enumeradas por USBFN.
En el artículo [configuración del registro USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-registry-settings-for-a-function-controller-driver) se explican los detalles de la configuración de USB.

Aunque puede modificar la configuración predeterminada de USBFN disponible en la `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default` clave, se recomienda definir la suya propia, ya que las actualizaciones del sistema no sobrescribirán.

#### <a name="creating-a-new-usbfn-configuration-with-the-mtp-interface"></a>Creación de una nueva configuración de USBFN con la interfaz MTP

Siga estos pasos para agregar una nueva configuración con MTP:
1. Agregue una nueva clave en `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations`. Ejemplo: `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\MyConfiguration`.
2. En la nueva clave, cree `REG_MULTI_SZ` un `InterfaceList` valor igual `MTP`a.
3. En la misma clave, cree `REG_BINARY` un `MSOSCompatIdDescriptor` valor igual `2800000000010400010000000000000000014D545000000000000000000000000000000000000000`a.
4. En `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` agregue un nuevo `REG_SZ` valor `CurrentConfiguration` igual al nombre de la clave recién creada. En este caso, sería `MyConfiguration`.
5. [**Opcional**] En `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN` , agregue un `REG_DWORD` nuevo `IncludeDefaultCfg` valor igual a 1. Esto hará que el controlador USB enumere las interfaces predeterminadas junto con MTP.

> [!NOTE]
> Si ya usa una configuración personalizada, tendrá que modificarla en lugar de crear una nueva.

#### <a name="adding-the-mtp-interface-to-an-existing-configuration"></a>Agregar la interfaz MTP a una configuración existente

Siga estos pasos para agregar MTP a una configuración de USBFN existente:
1. Busque la configuración actual comprobando el `CurrentConfiguration` valor en `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN`. Si el valor está presente, la configuración actual se puede encontrar en `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\[CurrentConfiguration]`. En caso contrario, `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\USBFN\Configurations\Default`está en.
2. En la clave de configuración actual `\0MTP` , agregue al valor `InterfaceList`de. La parte ***\ 0*** se usa como el tipo de `InterfaceList` is `REG_MULTI_SZ` y requiere este separador entre los valores.
3. Modifique el `MSOSCompatIdDescriptor` valor para incluir el descriptor de MTP. Para crear un descriptor válido que contenga todas las interfaces `InterfaceList` actualmente bajo el valor, siga la documentación de instrucciones disponible en la parte inferior de [esta página](https://msdn.microsoft.com/windows/hardware/gg463179.aspx). *OS_Desc_CompatID. doc* proporciona una explicación del formato del descriptor y un ejemplo de cómo incluir varias interfaces en el descriptor. Los identificadores compatibles y subcompatibles de MTP también están disponibles en la misma página y se usan en uno de los ejemplos.

## <a name="how-to-include-mtp-in-your-custom-ffu"></a>Cómo incluir MTP en el FFU personalizado

1. Agregue el identificador de la característica **IOT_MTP** al archivo de entrada OEM. Este es un equivalente a seguir los pasos de la sección "[**aprovisionar el dispositivo con los paquetes necesarios**](#provisioning-the-device-with-required-packages)".
2. Asegúrese de aplicar los mismos cambios del registro que se mencionan en la sección "[**creación de una nueva configuración de USBFN con la interfaz MTP**](#creating-a-new-usbfn-configuration-with-the-mtp-interface)". Siga [estas instrucciones](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) para obtener información sobre cómo aplicar cambios del registro a un FFU.
3. Crear image\FFU. Lea [este artículo](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para obtener instrucciones.

> [!WARNING]
> No se debe intentar modificar la configuración predeterminada mediante la personalización de FFU. Las entradas definidas por el sistema pueden ser actualizadas o modificadas por una actualización del sistema y se perderán todas las configuraciones personalizadas.

## <a name="how-to-setup-the-mtp-sd-card-filter"></a>Configuración del filtro de tarjeta SD MTP

De forma predeterminada, MTP enumerará todo el contenido de una tarjeta SD, si está presente en el dispositivo. Sin embargo, es posible limitar esta enumeración a una subcarpeta específica. Para ello, debe agregar un valor `MTPSDFolderFilter` del registro en la clave `HKEY_LOCAL_MACHINE\Software\Microsoft\MTP`del registro.
El valor es de tipo `REG_SZ` y debe contener una ruta de acceso relativa a la carpeta que desea que la Enumere MTP. La carpeta se creará automáticamente si aún no existe.

Rutas de acceso de ejemplo:
- \FirstLevelDirectory;
- FirstLevelDirectory;
- \FirstLevelDirectory\SecondLevelDirectory;
- Never\Before\Created\Directory.

> [!WARNING]
> No use una ruta de acceso absoluta que contenga la `C:\Some\Folder\Path` letra de la unidad, como-esto podría impedir que se Enumere la tarjeta SD.

Consulte [este vínculo](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-registry-setting-to-an-image) para obtener más información sobre cómo personalizar la imagen con entradas específicas del registro.
