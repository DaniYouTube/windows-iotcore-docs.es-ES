---
title: Depurar la aplicación mediante la depuración de aplicaciones de consola remota
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/2017
ms.topic: article
description: Obtenga información sobre cómo depurar de forma remota la aplicación de consola de IoT Core en Visual Studio.
keywords: Windows IOT, Visual Studio, implementación de aplicaciones, depuración remota
ms.openlocfilehash: b18af69009b43df5d5d6f3d64a45d9d468017642
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918215"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a><span data-ttu-id="20c00-104">Depurar la aplicación mediante la depuración de aplicaciones de consola remota</span><span class="sxs-lookup"><span data-stu-id="20c00-104">Debug your app using Remote Console App Debugging</span></span>

<span data-ttu-id="20c00-105">Aquí se muestra cómo depurar la aplicación de consola de IoT Core de forma remota en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="20c00-105">Here's how to debug your IoT Core console application remotely in Visual Studio:</span></span>

* <span data-ttu-id="20c00-106">En primer lugar, debe configurar el depurador remoto en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="20c00-106">You will first need to setup the Remote Debugger on your Windows IoT Core device.</span></span> <span data-ttu-id="20c00-107">En primer lugar, siga los pasos que se indican a [continuación](AppDeployment.md) para implementar cualquier otra aplicación universal de Windows en el dispositivo (Pruebe el proyecto HelloWorld).</span><span class="sxs-lookup"><span data-stu-id="20c00-107">First follow the steps [here](AppDeployment.md) to deploy any other Universal Windows Application on your device (try the HelloWorld project).</span></span> <span data-ttu-id="20c00-108">Se copiarán todos los archivos binarios necesarios en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="20c00-108">This will copy all the required binaries to your device.</span></span> 

* <span data-ttu-id="20c00-109">Para iniciar el depurador remoto en el dispositivo, abra un explorador Web en su PC y apunte a `http://<device name/IP address>:8080` para iniciar el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="20c00-109">To start the remote debugger on your device, open a Web Browser on your PC and point it to `http://<device name/IP address>:8080` to launch [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="20c00-110">En el cuadro de diálogo credenciales, use el nombre de usuario y la contraseña predeterminados: `Administrator``p@ssw0rd`.</span><span class="sxs-lookup"><span data-stu-id="20c00-110">In the credentials dialog, use the default username and password: `Administrator`, `p@ssw0rd`.</span></span> <span data-ttu-id="20c00-111">La administración de dispositivos Windows debe iniciar y mostrar la pantalla de inicio de administración web.</span><span class="sxs-lookup"><span data-stu-id="20c00-111">Windows Device Management should launch and display the web management home screen.</span></span>

* <span data-ttu-id="20c00-112">Ahora, vaya a la sección configuración de depuración del portal de dispositivos de Windows y haga clic en el botón Inicio en iniciar Visual Studio Remote Debugger.</span><span class="sxs-lookup"><span data-stu-id="20c00-112">Now navigate to the Debug settings section of Windows Device Portal and click the Start button under Start Visual Studio Remote Debugger.</span></span> 

    ![WindowsDevicePortalDebugSettings iniciar el depurador remoto](../media/Console/device_portal_start_debugger.png)

* <span data-ttu-id="20c00-114">Se mostrará un cuadro de mensaje emergente que le proporcionará la información de conexión.</span><span class="sxs-lookup"><span data-stu-id="20c00-114">This will show pop-up a message box and give you the connection information.</span></span> 

*  <span data-ttu-id="20c00-115">En Visual Studio, puede configurar el destino editando las propiedades del proyecto (Asegúrese de realizar todos los cambios resaltados según corresponda al nombre o la dirección IP del panel):</span><span class="sxs-lookup"><span data-stu-id="20c00-115">In Visual Studio, you can configure your target by editing your project's properties (be sure to make all of the highlighted changes as appropriate to your board's name or IP address):</span></span>

    ![Definimos configuración del proyecto de equipo remoto](../media/Console/console_project_settings.png)
    
> [!NOTE]
> <span data-ttu-id="20c00-117">Si no ve la imagen anterior, vaya al "Explorador de soluciones" en el menú contextual y vaya a "propiedades del proyecto".</span><span class="sxs-lookup"><span data-stu-id="20c00-117">If you're not seeing the image above, please go to the "Solution Explorer" in the context menu, and go to "Project Properties".</span></span> <span data-ttu-id="20c00-118">Puede encontrar más información sobre las propiedades del proyecto [aquí](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span><span class="sxs-lookup"><span data-stu-id="20c00-118">You can find more information for project properties [here](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span></span>

> [!TIP]
> <span data-ttu-id="20c00-119">Puede usar la dirección IP en lugar del nombre de dispositivo de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="20c00-119">You can use the IP address instead of the Windows IoT Core device name.</span></span>

* <span data-ttu-id="20c00-120">La configuración del proyecto debe modificarse para habilitar la implementación.</span><span class="sxs-lookup"><span data-stu-id="20c00-120">The project configuration needs to be modified to enable deployment.</span></span>  <span data-ttu-id="20c00-121">Para ello, abra el Configuration Manager seleccionando el administrador de configuración en el menú desplegable Configuración de soluciones de la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="20c00-121">To do this, open the Configuration Manager by selecting the Configuration manger from the Solution Configuration drop-down menu on the toolbar.</span></span>

    ![Definimos SolutionConfiguration](../media/Console/configuration_management.png)

    <span data-ttu-id="20c00-123">En el Configuration Manager, asegúrese de que la casilla implementar está seleccionada para la configuración del proyecto (si esta opción está deshabilitada, es probable que las opciones de implementación no se hayan introducido completamente en la pestaña depuración de las propiedades del proyecto)</span><span class="sxs-lookup"><span data-stu-id="20c00-123">From the Configuration Manager, ensure that the Deploy checkbox is selected for your project configuration (if this options is disabled, it is likely that the deployment options have not been fully entered into the Debugging tab of the project properties)</span></span>

    ![Definimos configuración del proyecto de equipo remoto](../media/Console/deploy_checkbox.png)

* <span data-ttu-id="20c00-125">Ahora estamos listos para implementar en el dispositivo Windows IoT Core remoto.</span><span class="sxs-lookup"><span data-stu-id="20c00-125">Now we're ready to deploy to the remote Windows IoT Core device.</span></span> <span data-ttu-id="20c00-126">Simplemente presione F5 (o seleccione Depurar \| iniciar depuración) para iniciar la depuración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="20c00-126">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="20c00-127">También puede usar compilar \| implementar solución para implementar simplemente la aplicación sin iniciar una sesión de depuración.</span><span class="sxs-lookup"><span data-stu-id="20c00-127">You can also use Build \| Deploy Solution to simply deploy your application without starting a debug session.</span></span>

> [!NOTE]
> <span data-ttu-id="20c00-128">Cuando se ejecuta desde Visual Studio, la salida no se mostrará en ningún lugar, pero podrá establecer puntos de interrupción, ver valores de variables, etc.</span><span class="sxs-lookup"><span data-stu-id="20c00-128">When run from Visual Studio, the output will not display anywhere, but you will be able to set breakpoints, see variable values, etc.</span></span>

* <span data-ttu-id="20c00-129">Para detener la aplicación, presione el botón "detener depuración" (o seleccione Depurar \| detener depuración).</span><span class="sxs-lookup"><span data-stu-id="20c00-129">To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

* <span data-ttu-id="20c00-130">Ahora puede ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="20c00-130">You can now run the application.</span></span>  <span data-ttu-id="20c00-131">Simplemente abra una conexión de PowerShell o SSH (las instrucciones se pueden encontrar [aquí para PowerShell](../connect-your-device/PowerShell.md) y [aquí para ssh](../connect-your-device/SSH.md)) y escriba el comando remoto que especificó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="20c00-131">Simply open a PowerShell/SSH connection (instructions can be found [here for PowerShell](../connect-your-device/PowerShell.md) and [here for SSH](../connect-your-device/SSH.md)) and enter the Remote Command you specified above.</span></span>

    ![Salida de definimos](../media/Console/console_output.png)

* <span data-ttu-id="20c00-133">Una vez que haya terminado de depurar la aplicación, recuerde detener el depurador remoto en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="20c00-133">Once you are done debugging your application, remember to stop the remote debugger on the Windows IoT Core device.</span></span> <span data-ttu-id="20c00-134">Para ello, vaya a la sección configuración de depuración del portal de dispositivos de Windows y haga clic en el botón detener el depurador remoto.</span><span class="sxs-lookup"><span data-stu-id="20c00-134">You can do this by navigating to Debug settings section of Windows Device Portal and clicking on the Stop Remote Debugger button.</span></span>

    ![WindowsDevicePortalDebugSettings detener el depurador remoto](../media/Console/device_portal_stop_debugger.PNG)

