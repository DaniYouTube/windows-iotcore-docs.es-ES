---
title: Configuración de una aplicación predeterminada
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/2017
ms.topic: article
description: Aprenda a configurar una aplicación predeterminada mediante el portal de dispositivos de Windows o el shell.
keywords: Windows IOT, aplicación predeterminada, PowerShell, IOT
ms.openlocfilehash: b7165331daba3b8bc953535ecc2d5b51cfda782c
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918204"
---
# <a name="setup-a-default-app"></a>Configuración de una aplicación predeterminada
Aquí aprenderá las maneras de configurar la aplicación como la aplicación predeterminada. La aplicación predeterminada es la que se inicia cuando se inicia el sistema.  

> [!NOTE]
> Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.

## <a name="runtime-options"></a>Opciones de tiempo de ejecución

Durante las fases de desarrollo o experimentales, puede cambiar la aplicación predeterminada de la manera siguiente:

### <a name="using-windows-device-portal"></a>Uso del portal de dispositivos de Windows

Puede hacer clic en la columna **Startup** correspondiente a la aplicación.
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>Usar el shell

Pasos para establecer la aplicación predeterminada mediante el shell 

1. Conexión al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md)

2. Enumerar las aplicaciones que se instalan mediante `iotstartup list`

3. Anote el valor de AppID de la aplicación que desea establecer como predeterminado y establézcalo mediante `iotstartup add headed <appid>`. En el caso de la aplicación sin periféricos, debe usar `iotstartup add headless <appid>`.


## <a name="build-time-option"></a>Opción de tiempo de compilación

Para implementaciones de gran tamaño, puede conseguirlo mediante el paquete de aprovisionamiento

Puede especificar el valor de StartupApp/default en el WCD durante la creación del paquete de aprovisionamiento.
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

Consulte [appx. IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) como ejemplo. Puede obtener el identificador de modelo de usuario de la aplicación (AUMID) de un appx mediante la [herramienta GetAppxInfo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).

## <a name="how-to-configure-home-key"></a>Cómo configurar la clave "principal"

Actualización de aniversario de IoT de Windows 10 (1607) proporciona compatibilidad con Shell para poner la ventana de la aplicación predeterminada en primer plano cuando otra aplicación se está ejecutando actualmente.

Para ver cómo habilitar la clave "Inicio", visite nuestra página de [Shell de IOT](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys) .
