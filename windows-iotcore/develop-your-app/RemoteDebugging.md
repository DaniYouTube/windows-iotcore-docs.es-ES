---
title: Depurar la aplicación con la depuración remota de aplicaciones de consola
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: Obtenga información sobre cómo depurar la aplicación de consola IoT Core remotamente en Visual Studio de forma remota.
keywords: Windows iot, visual studio, la implementación de aplicaciones, la depuración remota
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514547"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a><span data-ttu-id="85180-104">Depurar la aplicación con la depuración remota de aplicaciones de consola</span><span class="sxs-lookup"><span data-stu-id="85180-104">Debug your app using Remote Console App Debugging</span></span>

<span data-ttu-id="85180-105">Aquí le mostramos cómo depurar la aplicación de consola IoT Core remotamente en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="85180-105">Here's how to debug your IoT Core console application remotely in Visual Studio:</span></span>

* <span data-ttu-id="85180-106">En primer lugar, deberá configurar al depurador remoto en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="85180-106">You will first need to setup the Remote Debugger on your Windows IoT Core device.</span></span> <span data-ttu-id="85180-107">En primer lugar, siga los pasos [aquí](AppDeployment.md) para implementar cualquier otra aplicación Windows Universal en el dispositivo (pruebe el proyecto HelloWorld).</span><span class="sxs-lookup"><span data-stu-id="85180-107">First follow the steps [here](AppDeployment.md) to deploy any other Universal Windows Application on your device (try the HelloWorld project).</span></span> <span data-ttu-id="85180-108">Esto copiará todos los archivos binarios necesarios a su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="85180-108">This will copy all the required binaries to your device.</span></span> 

* <span data-ttu-id="85180-109">Para iniciar el depurador remoto en el dispositivo, abra un explorador Web en su PC y haga que señale a `http://<device name/IP address>:8080` para iniciar [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="85180-109">To start the remote debugger on your device, open a Web Browser on your PC and point it to `http://<device name/IP address>:8080` to launch [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="85180-110">En el cuadro de diálogo de credenciales, utilice el nombre de usuario predeterminado y la contraseña: `Administrator`, `p@ssw0rd`.</span><span class="sxs-lookup"><span data-stu-id="85180-110">In the credentials dialog, use the default username and password: `Administrator`, `p@ssw0rd`.</span></span> <span data-ttu-id="85180-111">Administración de dispositivos de Windows debe iniciar y mostrar la pantalla principal de administración de web.</span><span class="sxs-lookup"><span data-stu-id="85180-111">Windows Device Management should launch and display the web management home screen.</span></span>

* <span data-ttu-id="85180-112">Ahora, vaya a la sección de configuración de depuración de Windows Device Portal y haga clic en el botón Inicio en iniciar Visual Studio Remote Debugger.</span><span class="sxs-lookup"><span data-stu-id="85180-112">Now navigate to the Debug settings section of Windows Device Portal and click the Start button under Start Visual Studio Remote Debugger.</span></span> 

    ![Depurador remoto WindowsDevicePortalDebugSettings inicio](../media/Console/device_portal_start_debugger.png)

* <span data-ttu-id="85180-114">Esto mostrará emergente de un cuadro de mensaje y le proporcionarán la información de conexión.</span><span class="sxs-lookup"><span data-stu-id="85180-114">This will show pop-up a message box and give you the connection information.</span></span> 

*  <span data-ttu-id="85180-115">En Visual Studio, puede configurar el destino mediante la edición de las propiedades del proyecto (asegúrese de que todos los cambios resaltados según corresponda al nombre o dirección IP de la placa):</span><span class="sxs-lookup"><span data-stu-id="85180-115">In Visual Studio, you can configure your target by editing your project's properties (be sure to make all of the highlighted changes as appropriate to your board's name or IP address):</span></span>

    ![Configuración del proyecto de equipo remoto de la aplicación de consola](../media/Console/console_project_settings.png)
    
> [!NOTE]
> <span data-ttu-id="85180-117">Si no ve la imagen anterior, vaya a "Explorador de soluciones" en el menú contextual y vaya a "Propiedades del proyecto".</span><span class="sxs-lookup"><span data-stu-id="85180-117">If you're not seeing the image above, please go to the "Solution Explorer" in the context menu, and go to "Project Properties".</span></span> <span data-ttu-id="85180-118">Puede encontrar más información para las propiedades del proyecto [aquí](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span><span class="sxs-lookup"><span data-stu-id="85180-118">You can find more information for project properties [here](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).</span></span>

> [!TIP]
> <span data-ttu-id="85180-119">Puede usar la dirección IP en lugar del nombre de dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="85180-119">You can use the IP address instead of the Windows IoT Core device name.</span></span>

* <span data-ttu-id="85180-120">La configuración del proyecto debe modificarse para habilitar la implementación.</span><span class="sxs-lookup"><span data-stu-id="85180-120">The project configuration needs to be modified to enable deployment.</span></span>  <span data-ttu-id="85180-121">Para ello, abra el Administrador de configuración seleccionando el Administrador de configuración en el menú desplegable de configuración de soluciones en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="85180-121">To do this, open the Configuration Manager by selecting the Configuration manger from the Solution Configuration drop-down menu on the toolbar.</span></span>

    ![Aplicación de consola SolutionConfiguration](../media/Console/configuration_management.png)

    <span data-ttu-id="85180-123">Desde el Administrador de configuración, asegúrese de que esté seleccionada la casilla de verificación de implementación para la configuración del proyecto (si esta opción está deshabilitada, es probable que las opciones de implementación no se han escrito completamente en la pestaña de depuración de las propiedades del proyecto)</span><span class="sxs-lookup"><span data-stu-id="85180-123">From the Configuration Manager, ensure that the Deploy checkbox is selected for your project configuration (if this options is disabled, it is likely that the deployment options have not been fully entered into the Debugging tab of the project properties)</span></span>

    ![Configuración del proyecto de equipo remoto de la aplicación de consola](../media/Console/deploy_checkbox.png)

* <span data-ttu-id="85180-125">Ahora estamos listos para implementar en el dispositivo remoto de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="85180-125">Now we're ready to deploy to the remote Windows IoT Core device.</span></span> <span data-ttu-id="85180-126">Bastará que presione F5 (o seleccione Depurar \| Iniciar depuración) para iniciar la depuración de nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="85180-126">Simply press F5 (or select Debug \| Start Debugging) to start debugging our app.</span></span> <span data-ttu-id="85180-127">También puede usar la compilación \| implementar la solución para simplemente implementar la aplicación sin iniciar una sesión de depuración.</span><span class="sxs-lookup"><span data-stu-id="85180-127">You can also use Build \| Deploy Solution to simply deploy your application without starting a debug session.</span></span>

> [!NOTE]
> <span data-ttu-id="85180-128">Cuando se ejecuta desde Visual Studio, el resultado no se mostrará en cualquier lugar, pero podrá establecer puntos de interrupción, vea los valores de variable, etcetera.</span><span class="sxs-lookup"><span data-stu-id="85180-128">When run from Visual Studio, the output will not display anywhere, but you will be able to set breakpoints, see variable values, etc.</span></span>

* <span data-ttu-id="85180-129">Para detener la aplicación, pulse en el botón 'Detener depuración' (o seleccione Depurar \| Detener depuración).</span><span class="sxs-lookup"><span data-stu-id="85180-129">To stop the app, press on the 'Stop Debugging' button (or select Debug \| Stop Debugging).</span></span>

* <span data-ttu-id="85180-130">Ahora puede ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="85180-130">You can now run the application.</span></span>  <span data-ttu-id="85180-131">Solo tiene que abrir una conexión de PowerShell o SSH (puede encontrar instrucciones [aquí para PowerShell](../connect-your-device/PowerShell.md) y [aquí para SSH](../connect-your-device/SSH.md)) y escriba el comando remoto especificado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="85180-131">Simply open a PowerShell/SSH connection (instructions can be found [here for PowerShell](../connect-your-device/PowerShell.md) and [here for SSH](../connect-your-device/SSH.md)) and enter the Remote Command you specified above.</span></span>

    ![Salida de la aplicación de consola](../media/Console/console_output.png)

* <span data-ttu-id="85180-133">Una vez que termine de depurar la aplicación, no olvide detener el depurador remoto en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="85180-133">Once you are done debugging your application, remember to stop the remote debugger on the Windows IoT Core device.</span></span> <span data-ttu-id="85180-134">Puede hacerlo navegando para depurar la sección de configuración de Windows Device Portal y haga clic en el botón detener el depurador remoto.</span><span class="sxs-lookup"><span data-stu-id="85180-134">You can do this by navigating to Debug settings section of Windows Device Portal and clicking on the Stop Remote Debugger button.</span></span>

    ![Depurador remoto WindowsDevicePortalDebugSettings Stop](../media/Console/device_portal_stop_debugger.PNG)

