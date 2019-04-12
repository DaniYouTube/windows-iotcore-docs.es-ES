---
title: Instalar a controladores periféricos de USB
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear un paquete de controladores e instalar a controladores de terceros en los dispositivos.
keywords: Windows iot, los controladores USB, los dispositivos periféricos USB
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514892"
---
# <a name="install-usb-peripheral-drivers"></a>Instalar a controladores periféricos de USB
Siga estos pasos para agregar controladores de terceros (usb) para dispositivos periféricos, como los módems de banda ancha móvil USB, impresoras, escáneres, etcetera. 

## <a name="step-1-get-drivers-from-pc"></a>Paso 1: Obtener los controladores de PC
___
El paso es obtener la x86 versión de los controladores de PC. ARM, póngase en contacto con el proveedor de los dispositivos periféricos para obtener los archivos inf/sys.


1. Conecte el dispositivo en el equipo de windows

2. Instalar al controlador para el dispositivo en el equipo

3. Vaya al administrador de dispositivos, seleccione este dispositivo (se muestran en los controladores de Bus serie Universal) y haga clic y seleccione Propiedades.

4. Vaya a la ficha controlador en la ventana Propiedades y haga clic en detalles del controlador. Tenga en cuenta los archivos sys en la lista.

5. Copie los archivos sys de `C:\Windows\system32` y también el archivo inf relacionado desde `C:\Windows\Inf`. Puede encontrar el archivo inf por searcing para el sys de referencia del archivo en el `.inf` archivos. Es posible que deba copiar archivos adicionales que aparecen en el archivo Inf y se enumerarán en el archivo inf_filelist.txt creado al usar `inf2pkg.cmd` en el paso siguiente.


## <a name="step-2-create-a-driver-package"></a>Paso 2: Crear un paquete de controladores
___

El paquete de controladores contiene las referencias (InfSource) en el archivo Inf del controlador y también enumera todos los archivos que se hace referenciados en el archivo Inf. Puede crear el controlador. utilizando wm.xml [New IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).

[Nuevo IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) crea el archivo xml del paquete y también se basa directamente el archivo cab.

> [!NOTE]
> Solo admite Windows IoT Core [INF Universal y controladores Universal](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).


Consulte también: [Paquete de controladores de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>Paso 3: Instalar en dispositivos
___

* Conectarse al dispositivo ([mediante SSH](../connect-your-device/ssh.md) o [mediante Powershell](../connect-your-device/powershell.md))
* Copia el <filename>archivo .cab en el dispositivo en un directorio, por ejemplo C:\OemInstall
* Iniciar el almacenamiento provisional del paquete con `applyupdate -stage C:\OemInstall\<filename>.cab`. Tenga en cuenta que este paso es repetirse para cada paquete, cuando haya varios paquetes para instalar.
* Confirmar los paquetes mediante `applyupdate -commit`.

El dispositivo se reiniciará en la actualización del sistema operativo (mostrando gears) para instalar los paquetes y se reiniciará al sistema operativo principal. Este proceso puede tardar unos minutos.

## <a name="step-4-check-status-of-driver"></a>Paso 4: Compruebe el estado del controlador
___

* Iniciar el [Powershell](../connect-your-device/PowerShell.md)
* Puede obtener el estado de los controladores instalados mediante los siguientes cmdlets de Powershell

    * [Get-PnpDevice](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [Get-PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
