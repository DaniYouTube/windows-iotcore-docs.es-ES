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
# <a name="setup-a-default-app"></a><span data-ttu-id="08c4d-104">Programa de instalación de una aplicación predeterminada</span><span class="sxs-lookup"><span data-stu-id="08c4d-104">Setup a default app</span></span>
<span data-ttu-id="08c4d-105">Aquí obtendrá información sobre las formas de configurar la aplicación como aplicación predeterminada.</span><span class="sxs-lookup"><span data-stu-id="08c4d-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="08c4d-106">La aplicación predeterminada es el que se inician cuando se inicia el sistema.</span><span class="sxs-lookup"><span data-stu-id="08c4d-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="08c4d-107">Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.</span><span class="sxs-lookup"><span data-stu-id="08c4d-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="08c4d-108">Opciones de tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="08c4d-108">Runtime options</span></span>

<span data-ttu-id="08c4d-109">Durante el desarrollo / experimental fases, puede cambiar la aplicación predeterminada por medios siguientes.</span><span class="sxs-lookup"><span data-stu-id="08c4d-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="08c4d-110">Uso de Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="08c4d-110">Using Windows Device Portal</span></span>

<span data-ttu-id="08c4d-111">Puede hacer clic en **inicio** columna correspondiente a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="08c4d-111">You can click on **Startup** column corresponding to the app.</span></span>
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a><span data-ttu-id="08c4d-113">Uso del shell</span><span class="sxs-lookup"><span data-stu-id="08c4d-113">Using the shell</span></span>

<span data-ttu-id="08c4d-114">Pasos para configurar la aplicación predeterminada mediante el shell</span><span class="sxs-lookup"><span data-stu-id="08c4d-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="08c4d-115">Conectarse al dispositivo a través de [Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="08c4d-115">Connect to the device via [Powershell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="08c4d-116">Lista de las aplicaciones instaladas con</span><span class="sxs-lookup"><span data-stu-id="08c4d-116">List the applications installed using</span></span> `iotstartup list`

3. <span data-ttu-id="08c4d-117">Tenga en cuenta el appid de la aplicación que desea realizar como valor predeterminado y establecerlo mediante `iotstartup add headed <appid>`.</span><span class="sxs-lookup"><span data-stu-id="08c4d-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="08c4d-118">Para la aplicación sin periféricos, debe usar `iotstartup add headless <appid>`.</span><span class="sxs-lookup"><span data-stu-id="08c4d-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="08c4d-119">Opción de tiempo de compilación</span><span class="sxs-lookup"><span data-stu-id="08c4d-119">Build time option</span></span>

<span data-ttu-id="08c4d-120">Para implementaciones grandes, puede conseguirlo mediante el paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="08c4d-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="08c4d-121">Puede especificar la configuración de StartupApp de forma predeterminada en el WCD durante la creación del paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="08c4d-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

<span data-ttu-id="08c4d-123">Consulte [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="08c4d-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="08c4d-124">Puede obtener la aplicación de usuario modelo ID (AUMID) de un appx con [GetAppxInfo herramienta](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span><span class="sxs-lookup"><span data-stu-id="08c4d-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="08c4d-125">Cómo configurar la clave "Hogar"</span><span class="sxs-lookup"><span data-stu-id="08c4d-125">How to configure "Home" key</span></span>

<span data-ttu-id="08c4d-126">Actualización de aniversario de Windows 10 IoT (1607) proporciona compatibilidad de shell para traer la ventana de la aplicación de forma predeterminada al primer plano cuando se está ejecutando otra aplicación.</span><span class="sxs-lookup"><span data-stu-id="08c4d-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="08c4d-127">Para ver cómo se habilita la clave "Home", visite nuestro [página IoT Shell](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span><span class="sxs-lookup"><span data-stu-id="08c4d-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
