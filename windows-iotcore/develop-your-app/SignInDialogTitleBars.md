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
# <a name="title-bars-for-sign-in-dialogs"></a><span data-ttu-id="8fcf3-104">Las barras de título para iniciar sesión en los cuadros de diálogo</span><span class="sxs-lookup"><span data-stu-id="8fcf3-104">Title bars for sign in dialogs</span></span>

<span data-ttu-id="8fcf3-105">Por diseño, no muestra un marco de aplicación en torno a la ventana de la aplicación de Windows 10 IoT Core \- obtener toda la pantalla.</span><span class="sxs-lookup"><span data-stu-id="8fcf3-105">By design, Windows 10 IoT Core does not display an application frame around your application's window \- you get the full screen.</span></span> <span data-ttu-id="8fcf3-106">Sin embargo, en la versión 1809, varios cuadros de diálogo del sistema le ha dado un título de la barra que contiene el botón Cerrar para permitir al usuario Cancelar para salir de ellas, incluso cuando el contenido del cuadro de diálogo no proporciona ningún botón cancel.</span><span class="sxs-lookup"><span data-stu-id="8fcf3-106">However, in version 1809, several system dialog boxes have been given a title bar containing close button to allow the user to cancel out of them, even when the content of the dialog box provides no cancel button.</span></span>

## <a name="sign-in-dialog-boxes"></a><span data-ttu-id="8fcf3-107">Inicie sesión en los cuadros de diálogo</span><span class="sxs-lookup"><span data-stu-id="8fcf3-107">Sign in dialog boxes</span></span>

<span data-ttu-id="8fcf3-108">Los cuadros de diálogo que tienen esta característica agrega son los cuadros de diálogo identidad - para iniciar sesión en cuentas de Microsoft (MSA) y Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="8fcf3-108">The dialogs that have this feature added are the identity dialogs - for signing in to Microsoft Accounts (MSA) and Azure Active Directory (AAD).</span></span> <span data-ttu-id="8fcf3-109">Se pueden usar en la aplicación como se muestra en el [ejemplo de administración de cuentas Web](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) en el [repositorio de ejemplos de la aplicación de UWP de Microsoft](https://github.com/Microsoft/Windows-universal-samples).</span><span class="sxs-lookup"><span data-stu-id="8fcf3-109">These can be used in your application as shown in the [Web Account Management sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in the [Microsoft UWP app samples repo](https://github.com/Microsoft/Windows-universal-samples).</span></span>

## <a name="configuring-the-title-bar-height"></a><span data-ttu-id="8fcf3-110">Configuración de la altura de la barra de título</span><span class="sxs-lookup"><span data-stu-id="8fcf3-110">Configuring the title bar height</span></span>

<span data-ttu-id="8fcf3-111">La barra de título tiene un alto predeterminado de 25 píxeles y se puede establecer en cualquier valor mayor de hasta 50 píxeles.</span><span class="sxs-lookup"><span data-stu-id="8fcf3-111">The title bar has a default height of 25 pixels, and can be set to any greater value up to 50 pixels.</span></span> <span data-ttu-id="8fcf3-112">Cualquier valor mayor que 50 se unirá a 50.</span><span class="sxs-lookup"><span data-stu-id="8fcf3-112">Any value greater than 50 will be clamped to 50.</span></span> <span data-ttu-id="8fcf3-113">El alto puede ser inferior a 25, pero tenga en cuenta el efecto negativo, posiblemente, en la experiencia del usuario al decidir el alto del botón Cerrar.</span><span class="sxs-lookup"><span data-stu-id="8fcf3-113">The height can be less than 25, but consider the possibly negative effect on the user's experience when deciding the height of the close button.</span></span>

<span data-ttu-id="8fcf3-114">Por ejemplo, para establecer el alto de la barra de título en 32 píxeles en PowerShell puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8fcf3-114">As an example, to set the title bar height to 32 pixels, in PowerShell you could do the following:</span></span>
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> <span data-ttu-id="8fcf3-115">Para crear una imagen de OEM, el mecanismo preferido para establecer los valores del registro es con el `OEMInput.xml` archivo descritos en [personalizaciones en tiempo de ejecución](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span><span class="sxs-lookup"><span data-stu-id="8fcf3-115">For creating an OEM image, the preferred mechanism for setting registry values is with the `OEMInput.xml` file discussed in [Runtime customizations](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span></span>
