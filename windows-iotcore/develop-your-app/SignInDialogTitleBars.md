---
title: Configurar el alto de la barra de título para el inicio de sesión en los cuadros de diálogo
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Obtenga información sobre cómo configurar el alto de la barra de título para el inicio de sesión en los cuadros de diálogo de Windows 10 IoT Core, versión 1809.
keywords: Windows 10 IoT Core, msa, aad, barra de título, cerrar, Cancelar, puntas, web, cuenta, WebAccountManagement, iniciar sesión, inicio de sesión
ms.custom: RS5
ms.openlocfilehash: 69f59b4416c5db39d119994139eba4907035598e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514759"
---
# <a name="title-bars-for-sign-in-dialogs"></a>Las barras de título para iniciar sesión en los cuadros de diálogo

Por diseño, no muestra un marco de aplicación en torno a la ventana de la aplicación de Windows 10 IoT Core \- obtener toda la pantalla. Sin embargo, en la versión 1809, varios cuadros de diálogo del sistema le ha dado un título de la barra que contiene el botón Cerrar para permitir al usuario Cancelar para salir de ellas, incluso cuando el contenido del cuadro de diálogo no proporciona ningún botón cancel.

## <a name="sign-in-dialog-boxes"></a>Inicie sesión en los cuadros de diálogo

Los cuadros de diálogo que tienen esta característica agrega son los cuadros de diálogo identidad - para iniciar sesión en cuentas de Microsoft (MSA) y Azure Active Directory (AAD). Se pueden usar en la aplicación como se muestra en el [ejemplo de administración de cuentas Web](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) en el [repositorio de ejemplos de la aplicación de UWP de Microsoft](https://github.com/Microsoft/Windows-universal-samples).

## <a name="configuring-the-title-bar-height"></a>Configuración de la altura de la barra de título

La barra de título tiene un alto predeterminado de 25 píxeles y se puede establecer en cualquier valor mayor de hasta 50 píxeles. Cualquier valor mayor que 50 se unirá a 50. El alto puede ser inferior a 25, pero tenga en cuenta el efecto negativo, posiblemente, en la experiencia del usuario al decidir el alto del botón Cerrar.

Por ejemplo, para establecer el alto de la barra de título en 32 píxeles en PowerShell puede hacer lo siguiente:
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> Para crear una imagen de OEM, el mecanismo preferido para establecer los valores del registro es con el `OEMInput.xml` archivo descritos en [personalizaciones en tiempo de ejecución](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)