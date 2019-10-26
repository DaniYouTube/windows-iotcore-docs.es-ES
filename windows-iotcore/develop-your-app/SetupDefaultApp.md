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
# <a name="setup-a-default-app"></a><span data-ttu-id="5b86b-104">Configuración de una aplicación predeterminada</span><span class="sxs-lookup"><span data-stu-id="5b86b-104">Setup a default app</span></span>
<span data-ttu-id="5b86b-105">Aquí aprenderá las maneras de configurar la aplicación como la aplicación predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5b86b-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="5b86b-106">La aplicación predeterminada es la que se inicia cuando se inicia el sistema.</span><span class="sxs-lookup"><span data-stu-id="5b86b-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="5b86b-107">Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b86b-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="5b86b-108">Opciones de tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="5b86b-108">Runtime options</span></span>

<span data-ttu-id="5b86b-109">Durante las fases de desarrollo o experimentales, puede cambiar la aplicación predeterminada de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="5b86b-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="5b86b-110">Uso del portal de dispositivos de Windows</span><span class="sxs-lookup"><span data-stu-id="5b86b-110">Using Windows Device Portal</span></span>

<span data-ttu-id="5b86b-111">Puede hacer clic en la columna **Startup** correspondiente a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5b86b-111">You can click on **Startup** column corresponding to the app.</span></span>
<span data-ttu-id="5b86b-112">![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)</span><span class="sxs-lookup"><span data-stu-id="5b86b-112">![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)</span></span>

### <a name="using-the-shell"></a><span data-ttu-id="5b86b-113">Usar el shell</span><span class="sxs-lookup"><span data-stu-id="5b86b-113">Using the shell</span></span>

<span data-ttu-id="5b86b-114">Pasos para establecer la aplicación predeterminada mediante el shell</span><span class="sxs-lookup"><span data-stu-id="5b86b-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="5b86b-115">Conexión al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="5b86b-115">Connect to the device via [Powershell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="5b86b-116">Enumerar las aplicaciones que se instalan mediante `iotstartup list`</span><span class="sxs-lookup"><span data-stu-id="5b86b-116">List the applications installed using `iotstartup list`</span></span>

3. <span data-ttu-id="5b86b-117">Anote el valor de AppID de la aplicación que desea establecer como predeterminado y establézcalo mediante `iotstartup add headed <appid>`.</span><span class="sxs-lookup"><span data-stu-id="5b86b-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="5b86b-118">En el caso de la aplicación sin periféricos, debe usar `iotstartup add headless <appid>`.</span><span class="sxs-lookup"><span data-stu-id="5b86b-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="5b86b-119">Opción de tiempo de compilación</span><span class="sxs-lookup"><span data-stu-id="5b86b-119">Build time option</span></span>

<span data-ttu-id="5b86b-120">Para implementaciones de gran tamaño, puede conseguirlo mediante el paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="5b86b-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="5b86b-121">Puede especificar el valor de StartupApp/default en el WCD durante la creación del paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="5b86b-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
<span data-ttu-id="5b86b-122">![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)</span><span class="sxs-lookup"><span data-stu-id="5b86b-122">![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)</span></span>

<span data-ttu-id="5b86b-123">Consulte [appx. IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="5b86b-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="5b86b-124">Puede obtener el identificador de modelo de usuario de la aplicación (AUMID) de un appx mediante la [herramienta GetAppxInfo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span><span class="sxs-lookup"><span data-stu-id="5b86b-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="5b86b-125">Cómo configurar la clave "principal"</span><span class="sxs-lookup"><span data-stu-id="5b86b-125">How to configure "Home" key</span></span>

<span data-ttu-id="5b86b-126">Actualización de aniversario de IoT de Windows 10 (1607) proporciona compatibilidad con Shell para poner la ventana de la aplicación predeterminada en primer plano cuando otra aplicación se está ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="5b86b-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="5b86b-127">Para ver cómo habilitar la clave "Inicio", visite nuestra página de [Shell de IOT](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys) .</span><span class="sxs-lookup"><span data-stu-id="5b86b-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
