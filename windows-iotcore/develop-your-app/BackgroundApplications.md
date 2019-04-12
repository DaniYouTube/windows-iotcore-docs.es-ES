---
title: Aplicaciones en segundo plano
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo desarrollar aplicaciones en segundo plano para el dispositivo de IoT.
keywords: Windows iot, aplicaciones en segundo plano
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514559"
---
# <a name="developing-background-applications"></a><span data-ttu-id="c97cd-104">Desarrollo de aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="c97cd-104">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="c97cd-105">Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.</span><span class="sxs-lookup"><span data-stu-id="c97cd-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="c97cd-106">Aplicaciones en segundo plano son aplicaciones que no tengan ninguna interfaz de usuario directa.</span><span class="sxs-lookup"><span data-stu-id="c97cd-106">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="c97cd-107">Una vez implementado y configurado, estas aplicaciones se ejecutan durante el inicio de la máquina y ejecutan continuamente sin recursos de administración de limitaciones de usar cualquier duración de proceso.</span><span class="sxs-lookup"><span data-stu-id="c97cd-107">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="c97cd-108">Si bloqueará o salir reiniciará automáticamente el sistema de ellos.</span><span class="sxs-lookup"><span data-stu-id="c97cd-108">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="c97cd-109">Estas aplicaciones en segundo plano tienen un modelo de ejecución muy sencilla.</span><span class="sxs-lookup"><span data-stu-id="c97cd-109">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="c97cd-110">Las plantillas de crean una clase que implementa la interfaz "IBackgroundTask" y genera el método vacío "Run".</span><span class="sxs-lookup"><span data-stu-id="c97cd-110">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="c97cd-111">Este método de "Run" es el punto de entrada a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c97cd-111">This "Run" method is the entry point to your application.</span></span>

![Tarea en segundo plano](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="c97cd-113">Hay un punto importante a tener en cuenta: de forma predeterminada, la aplicación se cerrará cuando finalice el método de ejecución.</span><span class="sxs-lookup"><span data-stu-id="c97cd-113">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="c97cd-114">Esto significa que las aplicaciones que siguen el patrón de IoT comunes de la ejecución de un servidor en espera para la entrada o en un temporizador encontrará prematuramente la salida de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c97cd-114">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="c97cd-115">Para evitar que esto suceda debe llamar al método "GetDeferral" para evitar que la aplicación sale.</span><span class="sxs-lookup"><span data-stu-id="c97cd-115">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="c97cd-116">Puede encontrar más información sobre el patrón de aplazamiento [aquí](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span><span class="sxs-lookup"><span data-stu-id="c97cd-116">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="c97cd-117">¿Dónde se puede instalar aplicaciones en segundo plano desde?</span><span class="sxs-lookup"><span data-stu-id="c97cd-117">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="c97cd-118">Puede descargar e instalar las plantillas de IoT para habilitar las aplicaciones en segundo plano desde la Galería de Visual Studio [aquí](https://go.microsoft.com/fwlink/?linkid=847472).</span><span class="sxs-lookup"><span data-stu-id="c97cd-118">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="c97cd-119">Como alternativa, pueden encontrarse las plantillas mediante la búsqueda de `Windows IoT Core Project Templates` en el [Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/) o directamente desde Visual Studio en el cuadro de diálogo Extensiones y actualizaciones (Herramientas > extensiones y actualizaciones > en línea).</span><span class="sxs-lookup"><span data-stu-id="c97cd-119">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="c97cd-120">¿En qué idiomas están disponibles?</span><span class="sxs-lookup"><span data-stu-id="c97cd-120">What languages are available?</span></span>

<span data-ttu-id="c97cd-121">**En segundo plano (IoT) de la aplicación** encontrará plantillas para:</span><span class="sxs-lookup"><span data-stu-id="c97cd-121">**Background Application (IoT)** templates can be found for:</span></span>

* **<span data-ttu-id="c97cd-122">C++</span><span class="sxs-lookup"><span data-stu-id="c97cd-122">C++</span></span>** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **<span data-ttu-id="c97cd-123">C#</span><span class="sxs-lookup"><span data-stu-id="c97cd-123">C#</span></span>** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **<span data-ttu-id="c97cd-124">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c97cd-124">Visual Basic</span></span>** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **<span data-ttu-id="c97cd-125">JavaScript</span><span class="sxs-lookup"><span data-stu-id="c97cd-125">JavaScript</span></span>** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a><span data-ttu-id="c97cd-126">¿Cómo se usan aplicaciones en segundo plano?</span><span class="sxs-lookup"><span data-stu-id="c97cd-126">How are background applications used?</span></span> 

<span data-ttu-id="c97cd-127">Creación de una aplicación en segundo plano es muy similar a la creación de una tarea en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c97cd-127">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="c97cd-128">Cuando se inicia la aplicación en segundo plano, se llama al método de ejecución:</span><span class="sxs-lookup"><span data-stu-id="c97cd-128">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="c97cd-129">Cuando finaliza el método Run, a menos que se crea un objeto aplazamiento, finaliza la aplicación en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c97cd-129">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="c97cd-130">La práctica común para la programación asincrónica es tomar un aplazamiento similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="c97cd-130">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

<span data-ttu-id="c97cd-131">Una vez que se toma un aplazamiento, la aplicación en segundo plano continuará hasta que se llama al método Complete del objeto aplazamiento.</span><span class="sxs-lookup"><span data-stu-id="c97cd-131">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="c97cd-132">¿Cómo iniciar aplicaciones en segundo plano?</span><span class="sxs-lookup"><span data-stu-id="c97cd-132">How do background applications start?</span></span>

<span data-ttu-id="c97cd-133">Esta pregunta puede dividirse en implementación y la invocación.</span><span class="sxs-lookup"><span data-stu-id="c97cd-133">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="c97cd-134">Para implementar una aplicación en segundo plano, puede:</span><span class="sxs-lookup"><span data-stu-id="c97cd-134">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="c97cd-135">Use F5 de Visual Studio (que compilar, implementar e invocar).</span><span class="sxs-lookup"><span data-stu-id="c97cd-135">Use Visual Studio's F5 (which will build, deploy and invoke).</span></span>  <span data-ttu-id="c97cd-136">Para obtener más información, consulte nuestra [ejemplo Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) donde se describe cómo implementar e iniciar desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c97cd-136">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="c97cd-137">No configurará la aplicación en segundo plano para iniciarse cuando arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c97cd-137">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="c97cd-138">Crear un elemento AppX en Visual Studio seleccionando el proyecto > Store > crear paquetes de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c97cd-138">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="c97cd-139">Una vez haya creado un AppX, puede usar [Windows Device Portal](../manage-your-device/DevicePortal.md) para implementarla en su dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c97cd-139">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="c97cd-140">Para invocar una aplicación en segundo plano, puede:</span><span class="sxs-lookup"><span data-stu-id="c97cd-140">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="c97cd-141">Como se mencionó anteriormente, F5 funcionalidad de Visual Studio implementará y comenzar inmediatamente la aplicación en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c97cd-141">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="c97cd-142">No configurará la aplicación en segundo plano para iniciarse cuando arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c97cd-142">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="c97cd-143">Para una aplicación en segundo plano que se ha implementado en un dispositivo de IoT, puede usar la utilidad iotstartup.exe para configurar la aplicación en segundo plano para iniciarse cuando arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c97cd-143">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="c97cd-144">Para especificar la aplicación en segundo plano como una aplicación de inicio, siga estas instrucciones (**sustituir el nombre de la aplicación** para `BackgroundApplication1` a continuación):</span><span class="sxs-lookup"><span data-stu-id="c97cd-144">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="c97cd-145">Inicie una sesión de PowerShell (PS) con el dispositivo Windows IoT Core, como se describe [aquí](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="c97cd-145">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="c97cd-146">En la sesión de PS, escriba:</span><span class="sxs-lookup"><span data-stu-id="c97cd-146">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="c97cd-147">Debería ver el nombre completo de la aplicación en segundo plano, es decir, algo como:</span><span class="sxs-lookup"><span data-stu-id="c97cd-147">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="c97cd-148">La utilidad es confirmar que la aplicación en segundo plano es una aplicación "sin periféricos" y se ha instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="c97cd-148">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="c97cd-149">Es probable que vea una entrada Headed también para las aplicaciones en segundo plano, pero pueden omitir.</span><span class="sxs-lookup"><span data-stu-id="c97cd-149">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="c97cd-150">Ahora, es fácil de configurar esta aplicación como una aplicación de' inicio'.</span><span class="sxs-lookup"><span data-stu-id="c97cd-150">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="c97cd-151">Basta con escribir el comando:</span><span class="sxs-lookup"><span data-stu-id="c97cd-151">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="c97cd-152">La utilidad se confirmará que la aplicación en segundo plano se ha agregado a la lista de equipos sin periféricos "aplicaciones de inicio":</span><span class="sxs-lookup"><span data-stu-id="c97cd-152">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="c97cd-153">Siga adelante y reinicie el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c97cd-153">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="c97cd-154">En la sesión de PS, puede emitir el comando de apagado:</span><span class="sxs-lookup"><span data-stu-id="c97cd-154">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="c97cd-155">Una vez que se haya reiniciado el dispositivo, la aplicación en segundo plano se iniciará automáticamente y Windows 10 IoT Core se asegurará de que se reinicia cada vez que se detiene.</span><span class="sxs-lookup"><span data-stu-id="c97cd-155">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="c97cd-156">Una vez que una aplicación en segundo plano se registra para ejecutarse automáticamente, si la aplicación se cierra o se bloquea se reiniciará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="c97cd-156">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="c97cd-157">La aplicación no se informará del motivo por el que se está iniciando o lo reinicia si desea hacer nada especial en un reinicio, deberá realizar un seguimiento del estado de la aplicación en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c97cd-157">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="c97cd-158">Puede quitar la aplicación en segundo plano de la lista de aplicaciones de inicio sin periféricos escribiendo el comando:</span><span class="sxs-lookup"><span data-stu-id="c97cd-158">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="c97cd-159">La utilidad se confirmará que la aplicación en segundo plano se ha quitado de la lista de equipos sin periféricos "aplicaciones de inicio":</span><span class="sxs-lookup"><span data-stu-id="c97cd-159">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a><span data-ttu-id="c97cd-160">Vea también</span><span class="sxs-lookup"><span data-stu-id="c97cd-160">See Also</span></span>
<span data-ttu-id="c97cd-161">Para agregar una aplicación en segundo plano cuando se crea una imagen personalizada, consulte [crear un paquete Appx](../build-your-image/createinstallpackage.md)</span><span class="sxs-lookup"><span data-stu-id="c97cd-161">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
