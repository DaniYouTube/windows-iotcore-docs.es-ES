---
title: Configurar el alto de la barra de título para los cuadros de diálogo de inicio de sesión
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Aprenda a configurar el alto de la barra de título para los cuadros de diálogo de inicio de sesión en Windows 10 IoT Core, versión 1809.
keywords: Windows 10 IoT Core, MSA, AAD, TitleBar, Close, CANCEL, puntas, Web, Account, WebAccountManagement, Inicio de sesión, Sign
ms.custom: RS5
ms.openlocfilehash: 69f59b4416c5db39d119994139eba4907035598e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169113"
---
# <a name="title-bars-for-sign-in-dialogs"></a>Barras de título de los cuadros de diálogo de inicio de sesión

Por diseño, Windows 10 IOT Core no muestra un marco de aplicación en torno a la ventana \- de la aplicación y obtiene la pantalla completa. Sin embargo, en la versión 1809, a varios cuadros de diálogo del sistema se les ha asignado una barra de título con el botón Cerrar para que el usuario pueda cancelarla, incluso cuando el contenido del cuadro de diálogo no proporciona ningún botón Cancelar.

## <a name="sign-in-dialog-boxes"></a>Cuadros de diálogo de inicio de sesión

Los cuadros de diálogo que tienen esta característica se agregan son los cuadros de diálogo de identidad: para iniciar sesión en cuentas de Microsoft (MSA) y Azure Active Directory (AAD). Se pueden usar en la aplicación como se muestra en el [ejemplo de administración de cuentas web](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) en el [repositorio de ejemplos de aplicaciones para UWP de Microsoft](https://github.com/Microsoft/Windows-universal-samples).

## <a name="configuring-the-title-bar-height"></a>Configurar el alto de la barra de título

La barra de título tiene un alto predeterminado de 25 píxeles y se puede establecer en cualquier valor mayor hasta 50 píxeles. Cualquier valor mayor que 50 se fijará en 50. El alto puede ser inferior a 25, pero tenga en cuenta el efecto posiblemente negativo en la experiencia del usuario al decidir el alto del botón Cerrar.

Por ejemplo, para establecer el alto de la barra de título en 32 píxeles, puede hacer lo siguiente en PowerShell:
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> Para crear una imagen de OEM, el mecanismo preferido para establecer los valores del registro `OEMInput.xml` es con el archivo que se describe en las personalizaciones en [tiempo de ejecución](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations) .
