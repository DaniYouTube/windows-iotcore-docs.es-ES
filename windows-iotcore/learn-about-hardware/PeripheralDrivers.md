---
title: Instalación de controladores periféricos USB
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo crear un paquete de controladores e instalar controladores de terceros en los dispositivos.
keywords: Windows IOT, controladores USB, dispositivos periféricos, USB
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170933"
---
# <a name="install-usb-peripheral-drivers"></a>Instalación de controladores periféricos de USB
Siga los pasos que se indican a continuación para agregar controladores de terceros (USB) para dispositivos periféricos, como módems de banda ancha móvil USB, impresoras, escáneres, etc. 

## <a name="step-1-get-drivers-from-pc"></a>Paso 1: Obtener controladores del equipo
___
El paso es obtener la versión x86 de los controladores del equipo. Para ARM, póngase en contacto con el proveedor del periférico para obtener los archivos sys/INF.


1. Conectar el dispositivo al equipo Windows

2. Instalar el controlador del dispositivo en el equipo

3. Vaya a Device Manager, seleccione este dispositivo (que aparece en controladoras de bus serie universal), haga clic con el botón derecho y seleccione Propiedades.

4. Vaya a la pestaña controlador en el ventana Propiedades y haga clic en detalles del controlador. Tenga en cuenta los archivos sys que aparecen en la lista.

5. Copie los archivos sys desde `C:\Windows\system32` y también el archivo INF relacionado de `C:\Windows\Inf`. Puede encontrar el archivo INF searcing para la referencia de archivo sys en los `.inf` archivos. Es posible que necesite copiar los archivos adicionales que se enumeran en el archivo INF y que se mostrarán en el archivo inf_filelist `inf2pkg.cmd` . txt que se crea cuando se usa en el paso siguiente.


## <a name="step-2-create-a-driver-package"></a>Paso 2: Crear un paquete de controladores
___

El paquete de controladores contiene las referencias (InfSource) del archivo INF para el controlador y también enumera todos los archivos a los que se hace referencia en el archivo INF. Puede crear el archivo driver. WM. XML mediante [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).

[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) crea el archivo XML del paquete y también genera el archivo CAB directamente.

> [!NOTE]
> Windows IoT Core solo admite [los controladores universal y universal INF](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).


Consulte también: [Paquete de controladores de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO) 

## <a name="step-3-install-on-device"></a>Paso 3: Instalar en el dispositivo
___

* Conexión al dispositivo ([mediante SSH](../connect-your-device/ssh.md) o [con PowerShell](../connect-your-device/powershell.md))
* Copie el <filename>archivo. cab en el dispositivo a un directorio, por ejemplo, C:\OemInstall
* Inicie el almacenamiento provisional del paquete con `applyupdate -stage C:\OemInstall\<filename>.cab`. Tenga en cuenta que este paso se repite para cada paquete, cuando tiene varios paquetes para instalar.
* Confirme los paquetes mediante `applyupdate -commit`.

El dispositivo se reiniciará en el sistema operativo de actualización (que muestra los engranajes) para instalar los paquetes y se reiniciará de nuevo en el sistema operativo principal. Este proceso puede tardar unos minutos.

## <a name="step-4-check-status-of-driver"></a>Paso 4: Comprobar el estado del controlador
___

* Inicio de [PowerShell](../connect-your-device/PowerShell.md)
* Puede obtener el estado de los controladores instalados con el siguiente commandlets de PowerShell

    * [Get-PnpDevice](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [Get-PnpDeviceProperty](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
