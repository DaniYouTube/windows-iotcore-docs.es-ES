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
# <a name="title-bars-for-sign-in-dialogs"></a><span data-ttu-id="81f91-104">Barras de título de los cuadros de diálogo de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="81f91-104">Title bars for sign in dialogs</span></span>

<span data-ttu-id="81f91-105">Por diseño, Windows 10 IOT Core no muestra un marco de aplicación en torno a la ventana \- de la aplicación y obtiene la pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="81f91-105">By design, Windows 10 IoT Core does not display an application frame around your application's window \- you get the full screen.</span></span> <span data-ttu-id="81f91-106">Sin embargo, en la versión 1809, a varios cuadros de diálogo del sistema se les ha asignado una barra de título con el botón Cerrar para que el usuario pueda cancelarla, incluso cuando el contenido del cuadro de diálogo no proporciona ningún botón Cancelar.</span><span class="sxs-lookup"><span data-stu-id="81f91-106">However, in version 1809, several system dialog boxes have been given a title bar containing close button to allow the user to cancel out of them, even when the content of the dialog box provides no cancel button.</span></span>

## <a name="sign-in-dialog-boxes"></a><span data-ttu-id="81f91-107">Cuadros de diálogo de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="81f91-107">Sign in dialog boxes</span></span>

<span data-ttu-id="81f91-108">Los cuadros de diálogo que tienen esta característica se agregan son los cuadros de diálogo de identidad: para iniciar sesión en cuentas de Microsoft (MSA) y Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="81f91-108">The dialogs that have this feature added are the identity dialogs - for signing in to Microsoft Accounts (MSA) and Azure Active Directory (AAD).</span></span> <span data-ttu-id="81f91-109">Se pueden usar en la aplicación como se muestra en el [ejemplo de administración de cuentas web](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) en el [repositorio de ejemplos de aplicaciones para UWP de Microsoft](https://github.com/Microsoft/Windows-universal-samples).</span><span class="sxs-lookup"><span data-stu-id="81f91-109">These can be used in your application as shown in the [Web Account Management sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in the [Microsoft UWP app samples repo](https://github.com/Microsoft/Windows-universal-samples).</span></span>

## <a name="configuring-the-title-bar-height"></a><span data-ttu-id="81f91-110">Configurar el alto de la barra de título</span><span class="sxs-lookup"><span data-stu-id="81f91-110">Configuring the title bar height</span></span>

<span data-ttu-id="81f91-111">La barra de título tiene un alto predeterminado de 25 píxeles y se puede establecer en cualquier valor mayor hasta 50 píxeles.</span><span class="sxs-lookup"><span data-stu-id="81f91-111">The title bar has a default height of 25 pixels, and can be set to any greater value up to 50 pixels.</span></span> <span data-ttu-id="81f91-112">Cualquier valor mayor que 50 se fijará en 50.</span><span class="sxs-lookup"><span data-stu-id="81f91-112">Any value greater than 50 will be clamped to 50.</span></span> <span data-ttu-id="81f91-113">El alto puede ser inferior a 25, pero tenga en cuenta el efecto posiblemente negativo en la experiencia del usuario al decidir el alto del botón Cerrar.</span><span class="sxs-lookup"><span data-stu-id="81f91-113">The height can be less than 25, but consider the possibly negative effect on the user's experience when deciding the height of the close button.</span></span>

<span data-ttu-id="81f91-114">Por ejemplo, para establecer el alto de la barra de título en 32 píxeles, puede hacer lo siguiente en PowerShell:</span><span class="sxs-lookup"><span data-stu-id="81f91-114">As an example, to set the title bar height to 32 pixels, in PowerShell you could do the following:</span></span>
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> <span data-ttu-id="81f91-115">Para crear una imagen de OEM, el mecanismo preferido para establecer los valores del registro `OEMInput.xml` es con el archivo que se describe en las personalizaciones en [tiempo de ejecución](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations) .</span><span class="sxs-lookup"><span data-stu-id="81f91-115">For creating an OEM image, the preferred mechanism for setting registry values is with the `OEMInput.xml` file discussed in [Runtime customizations](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span></span>
