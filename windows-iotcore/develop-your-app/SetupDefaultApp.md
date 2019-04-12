---
title: Programa de instalación de una aplicación predeterminada
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: Obtenga información sobre cómo configurar una aplicación de forma predeterminada con la de Windows Device Portal o el shell.
keywords: Windows iot, iot de aplicación, PowerShell, de forma predeterminada
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514763"
---
# <a name="setup-a-default-app"></a>Programa de instalación de una aplicación predeterminada
Aquí obtendrá información sobre las formas de configurar la aplicación como aplicación predeterminada. La aplicación predeterminada es el que se inician cuando se inicia el sistema.  

> [!NOTE]
> Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.

## <a name="runtime-options"></a>Opciones de tiempo de ejecución

Durante el desarrollo / experimental fases, puede cambiar la aplicación predeterminada por medios siguientes.

### <a name="using-windows-device-portal"></a>Uso de Windows Device Portal

Puede hacer clic en **inicio** columna correspondiente a la aplicación.
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>Uso del shell

Pasos para configurar la aplicación predeterminada mediante el shell 

1. Conectarse al dispositivo a través de [Powershell](../connect-your-device/PowerShell.md)

2. Lista de las aplicaciones instaladas con `iotstartup list`

3. Tenga en cuenta el appid de la aplicación que desea realizar como valor predeterminado y establecerlo mediante `iotstartup add headed <appid>`. Para la aplicación sin periféricos, debe usar `iotstartup add headless <appid>`.


## <a name="build-time-option"></a>Opción de tiempo de compilación

Para implementaciones grandes, puede conseguirlo mediante el paquete de aprovisionamiento

Puede especificar la configuración de StartupApp de forma predeterminada en el WCD durante la creación del paquete de aprovisionamiento.
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

Consulte [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) como ejemplo. Puede obtener la aplicación de usuario modelo ID (AUMID) de un appx con [GetAppxInfo herramienta](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).

## <a name="how-to-configure-home-key"></a>Cómo configurar la clave "Hogar"

Actualización de aniversario de Windows 10 IoT (1607) proporciona compatibilidad de shell para traer la ventana de la aplicación de forma predeterminada al primer plano cuando se está ejecutando otra aplicación.

Para ver cómo se habilita la clave "Home", visite nuestro [página IoT Shell](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)
