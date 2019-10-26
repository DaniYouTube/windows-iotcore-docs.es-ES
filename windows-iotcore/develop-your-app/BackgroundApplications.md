---
title: Aplicaciones en segundo plano
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a desarrollar aplicaciones en segundo plano para su dispositivo IoT.
keywords: Windows IOT, aplicaciones en segundo plano
ms.openlocfilehash: ab9e4f66f3829c9758cbc40abfcde50df597a2d3
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918270"
---
# <a name="developing-background-applications"></a><span data-ttu-id="d33a6-104">Desarrollo de aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="d33a6-104">Developing Background Applications</span></span>

> [!NOTE]
> <span data-ttu-id="d33a6-105">Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d33a6-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="d33a6-106">Las aplicaciones en segundo plano son aplicaciones que no tienen interfaz de usuario directa.</span><span class="sxs-lookup"><span data-stu-id="d33a6-106">Background applications are applications that have no direct UI.</span></span> <span data-ttu-id="d33a6-107">Una vez implementadas y configuradas, estas aplicaciones se inician en el inicio del equipo y se ejecutan de forma continua sin limitaciones de uso de recursos de administración de la duración.</span><span class="sxs-lookup"><span data-stu-id="d33a6-107">Once deployed and configured, these applications launch at machine startup and run continuously without any process lifetime management resource use limitations.</span></span> <span data-ttu-id="d33a6-108">Si se bloquea o sale del sistema, se reiniciarán automáticamente.</span><span class="sxs-lookup"><span data-stu-id="d33a6-108">If they crash or exit the system will automatically restart them.</span></span>
<span data-ttu-id="d33a6-109">Estas aplicaciones en segundo plano tienen un modelo de ejecución muy simple.</span><span class="sxs-lookup"><span data-stu-id="d33a6-109">These Background Applications have a very simple execution model.</span></span> <span data-ttu-id="d33a6-110">Las plantillas crean una clase que implementa la interfaz "IBackgroundTask" y genera el método vacío "Run".</span><span class="sxs-lookup"><span data-stu-id="d33a6-110">The templates create a class that implements the "IBackgroundTask" interface and generates the empty "Run" method.</span></span> <span data-ttu-id="d33a6-111">Este método "ejecutar" es el punto de entrada a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d33a6-111">This "Run" method is the entry point to your application.</span></span>

![Tarea en segundo plano](../media/BackgroundApplications/backgroundTaskScreenshot.png)

<span data-ttu-id="d33a6-113">Hay un punto crítico a tener en cuenta: de forma predeterminada, la aplicación se cerrará cuando se complete el método Run.</span><span class="sxs-lookup"><span data-stu-id="d33a6-113">There is one critical point to note: by default, the application will shut down when the run method completes.</span></span> <span data-ttu-id="d33a6-114">Esto significa que las aplicaciones que siguen el patrón de IoT común de ejecutar un servidor que espera la entrada o en un temporizador encontrarán la salida prematura de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d33a6-114">This means that apps that follow the common IoT pattern of running a server waiting for input or on a timer will find the app exit prematurely.</span></span> <span data-ttu-id="d33a6-115">Para evitar que esto suceda, debe llamar al método "GetDeferral" para evitar que se salga de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d33a6-115">To prevent this from happening you must call the "GetDeferral" method to prevent the application from exiting.</span></span> <span data-ttu-id="d33a6-116">Puede encontrar más información sobre el patrón de aplazamiento [aquí](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span><span class="sxs-lookup"><span data-stu-id="d33a6-116">You can find more information on the deferral pattern [here](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).</span></span>

## <a name="where-can-background-applications-be-installed-from"></a><span data-ttu-id="d33a6-117">¿Dónde se pueden instalar las aplicaciones en segundo plano?</span><span class="sxs-lookup"><span data-stu-id="d33a6-117">Where can Background Applications be installed from?</span></span> 

<span data-ttu-id="d33a6-118">Puede descargar e instalar plantillas de IoT para habilitar las aplicaciones en segundo plano desde la galería de Visual Studio [aquí](https://go.microsoft.com/fwlink/?linkid=847472).</span><span class="sxs-lookup"><span data-stu-id="d33a6-118">You can download and install IoT templates to enable Background Applications from the Visual Studio Gallery [here](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>  <span data-ttu-id="d33a6-119">Como alternativa, puede encontrar las plantillas buscando `Windows IoT Core Project Templates` en la [Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/) o directamente desde Visual Studio en el cuadro de diálogo extensiones y actualizaciones (Herramientas > extensiones y actualizaciones > en línea).</span><span class="sxs-lookup"><span data-stu-id="d33a6-119">Alternatively, the templates can be found by searching for `Windows IoT Core Project Templates` in the [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/) or directly from Visual Studio in the Extension and Updates dialog (Tools > Extensions and Updates > Online).</span></span>

## <a name="what-languages-are-available"></a><span data-ttu-id="d33a6-120">¿Qué idiomas están disponibles?</span><span class="sxs-lookup"><span data-stu-id="d33a6-120">What languages are available?</span></span>

<span data-ttu-id="d33a6-121">Se pueden encontrar plantillas de **aplicación en segundo plano (IOT)** para:</span><span class="sxs-lookup"><span data-stu-id="d33a6-121">**Background Application (IoT)** templates can be found for:</span></span>

* <span data-ttu-id="d33a6-122">**C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="d33a6-122">**C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="d33a6-123">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="d33a6-123">**C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="d33a6-124">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span><span class="sxs-lookup"><span data-stu-id="d33a6-124">**Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`</span></span>
* <span data-ttu-id="d33a6-125">`File > New > Project > Installed > JavaScript > Windows > Windows IoT Core` de **JavaScript**</span><span class="sxs-lookup"><span data-stu-id="d33a6-125">**JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`</span></span>

## <a name="how-are-background-applications-used"></a><span data-ttu-id="d33a6-126">¿Cómo se usan las aplicaciones en segundo plano?</span><span class="sxs-lookup"><span data-stu-id="d33a6-126">How are background applications used?</span></span> 

<span data-ttu-id="d33a6-127">La creación de una aplicación en segundo plano es muy similar a la creación de una tarea en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d33a6-127">Creating a background application is very similar to creating a Background Task.</span></span>  <span data-ttu-id="d33a6-128">Cuando se inicia la aplicación en segundo plano, se llama al método Run:</span><span class="sxs-lookup"><span data-stu-id="d33a6-128">When the Background Application starts, the Run method is called:</span></span>

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

<span data-ttu-id="d33a6-129">Cuando finaliza el método Run, a menos que se cree un objeto de aplazamiento, finaliza la aplicación en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d33a6-129">When the Run method ends, unless a deferral object is created, the background application ends.</span></span> <span data-ttu-id="d33a6-130">La práctica habitual, para la programación asincrónica, es realizar un aplazamiento como este:</span><span class="sxs-lookup"><span data-stu-id="d33a6-130">The common practice, for asynchronous programming is to take a deferral like this:</span></span>

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

<span data-ttu-id="d33a6-131">Una vez que se toma un aplazamiento, la aplicación en segundo plano continuará hasta que se llame al método complete del objeto de aplazamiento.</span><span class="sxs-lookup"><span data-stu-id="d33a6-131">Once a deferral is taken, the background application will continue until the deferral object's Complete method is called.</span></span>

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a><span data-ttu-id="d33a6-132">¿Cómo se inician las aplicaciones en segundo plano?</span><span class="sxs-lookup"><span data-stu-id="d33a6-132">How do background applications start?</span></span>

<span data-ttu-id="d33a6-133">Esta pregunta puede dividirse en la implementación y la invocación.</span><span class="sxs-lookup"><span data-stu-id="d33a6-133">This question can be broken into deployment and invocation.</span></span>  

<span data-ttu-id="d33a6-134">Para implementar una aplicación en segundo plano, puede:</span><span class="sxs-lookup"><span data-stu-id="d33a6-134">To deploy a background application, you can either:</span></span>

* <span data-ttu-id="d33a6-135">Use F5 de Visual Studio (que se compilará, implementará e invocará).</span><span class="sxs-lookup"><span data-stu-id="d33a6-135">Use Visual Studio's F5 (which will build, deploy and invoke).</span></span>  <span data-ttu-id="d33a6-136">Para obtener más información, consulte nuestro [ejemplo de Hola mundo](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) en el que se describe cómo implementar e iniciar desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d33a6-136">For more details, see our [Hello World sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) where we describe how to deploy and launch from Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="d33a6-137">Esto no configurará la aplicación en segundo plano para que se inicie cuando se arranque el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d33a6-137">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="d33a6-138">Cree un AppX en Visual Studio seleccionando Project > Store > crear paquetes de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d33a6-138">Create an AppX in Visual Studio by selecting Project > Store > Create App Packages.</span></span>  <span data-ttu-id="d33a6-139">Una vez que haya creado un AppX, puede usar el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md) para implementarlo en el dispositivo de Windows 10 IOT Core.</span><span class="sxs-lookup"><span data-stu-id="d33a6-139">Once you have created an AppX, you can use [Windows Device Portal](../manage-your-device/DevicePortal.md) to deploy it to your Windows 10 IoT Core device.</span></span>

<span data-ttu-id="d33a6-140">Para invocar una aplicación en segundo plano, puede:</span><span class="sxs-lookup"><span data-stu-id="d33a6-140">To invoke a background application, you can either:</span></span>

* <span data-ttu-id="d33a6-141">Como se mencionó anteriormente, la funcionalidad F5 de Visual Studio se implementará e iniciará inmediatamente la aplicación en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d33a6-141">As mentioned above, Visual Studio's F5 functionality will deploy and immediately start your Background Application.</span></span>

> [!NOTE]
> <span data-ttu-id="d33a6-142">Esto no configurará la aplicación en segundo plano para que se inicie cuando se arranque el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d33a6-142">This will not configure your background application to start when the device boots.</span></span>

* <span data-ttu-id="d33a6-143">En el caso de una aplicación en segundo plano que se ha implementado en un dispositivo IoT, puede usar la utilidad iotstartup. exe para configurar la aplicación en segundo plano para que se inicie cuando se arranque el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d33a6-143">For a background application that has been deployed to an IoT device, you can use the iotstartup.exe utility to configure your background application to start when the device boots.</span></span>  <span data-ttu-id="d33a6-144">Para especificar la aplicación en segundo plano como una aplicación de inicio, siga estas instrucciones (**sustituya el nombre** de la aplicación por `BackgroundApplication1` a continuación):</span><span class="sxs-lookup"><span data-stu-id="d33a6-144">To specify your background application as a Startup App, follow these instructions (**substitute your app's name** for `BackgroundApplication1` below):</span></span>

1. <span data-ttu-id="d33a6-145">Inicie una sesión de PowerShell (PS) con el dispositivo Windows IoT Core tal como se describe [aquí](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="d33a6-145">Start a PowerShell (PS) session with your Windows IoT Core device as described [here](../connect-your-device/PowerShell.md).</span></span>

2. <span data-ttu-id="d33a6-146">En la sesión de PS, escriba:</span><span class="sxs-lookup"><span data-stu-id="d33a6-146">From the PS session, type:</span></span>
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. <span data-ttu-id="d33a6-147">Debería ver el nombre completo de la aplicación en segundo plano, es decir, algo parecido a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d33a6-147">You should see the full name of your background application, i.e. something like:</span></span>

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. <span data-ttu-id="d33a6-148">La utilidad confirma que la aplicación en segundo plano es una aplicación "sin periféricos" y se instala correctamente.</span><span class="sxs-lookup"><span data-stu-id="d33a6-148">The utility is confirming that your background application is an 'headless' application, and is installed correctly.</span></span>  <span data-ttu-id="d33a6-149">Probablemente verá una entrada para las aplicaciones en segundo plano, pero esto puede no tenerse en cuenta.</span><span class="sxs-lookup"><span data-stu-id="d33a6-149">You will likely see a Headed entry as well for your Background Applications, but this can be disregarded.</span></span>

5. <span data-ttu-id="d33a6-150">Ahora, es fácil establecer esta aplicación como una aplicación de inicio.</span><span class="sxs-lookup"><span data-stu-id="d33a6-150">Now, it's easy to set this app as a 'Startup App'.</span></span> <span data-ttu-id="d33a6-151">Simplemente escriba el comando:</span><span class="sxs-lookup"><span data-stu-id="d33a6-151">Just type the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. <span data-ttu-id="d33a6-152">La utilidad confirmará que la aplicación en segundo plano se ha agregado a la lista de aplicaciones de inicio sin periféricos:</span><span class="sxs-lookup"><span data-stu-id="d33a6-152">The utility will confirm that your background application has been added to the list of headless 'Startup Apps':</span></span>

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. <span data-ttu-id="d33a6-153">Continúe y reinicie el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d33a6-153">Go ahead and restart your Windows IoT Core device.</span></span> <span data-ttu-id="d33a6-154">Desde la sesión de PS, puede emitir el comando Shutdown:</span><span class="sxs-lookup"><span data-stu-id="d33a6-154">From the PS session, you can issue the shutdown command:</span></span>

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. <span data-ttu-id="d33a6-155">Una vez que el dispositivo se haya reiniciado, la aplicación en segundo plano se iniciará automáticamente y Windows 10 IoT Core se asegurará de que se reinicie cada vez que se detenga.</span><span class="sxs-lookup"><span data-stu-id="d33a6-155">Once the device has restarted, your background application will start automatically and Windows 10 IoT Core will make sure that it gets restarted anytime it stops.</span></span>  

> [!NOTE]
> <span data-ttu-id="d33a6-156">Una vez que se registra una aplicación en segundo plano para que se ejecute automáticamente, si la aplicación se cierra o se bloquea, se reiniciará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="d33a6-156">Once a background app is registered to run automatically, if the app exits or crashes it will be automatically restarted.</span></span>  <span data-ttu-id="d33a6-157">La aplicación no está informada de la razón por la que se inicia o se reinicia, por lo que si quiere realizar una acción especial en un reinicio, deberá realizar un seguimiento del estado de la aplicación en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d33a6-157">The app isn't informed of the reason that it's being started or restarted so if you want to take special action on a restart you will need to track the app state in your app.</span></span>

9. <span data-ttu-id="d33a6-158">Puede quitar la aplicación en segundo plano de la lista de aplicaciones de inicio sin periféricos. para ello, escriba el comando:</span><span class="sxs-lookup"><span data-stu-id="d33a6-158">You can remove your background application from the list of headless Startup Apps by typing the command:</span></span>

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. <span data-ttu-id="d33a6-159">La utilidad confirmará que se ha quitado la aplicación en segundo plano de la lista de aplicaciones de inicio sin periféricos:</span><span class="sxs-lookup"><span data-stu-id="d33a6-159">The utility will confirm that your background application has been removed from the list of headless 'Startup Apps':</span></span>

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a><span data-ttu-id="d33a6-160">Consulta también</span><span class="sxs-lookup"><span data-stu-id="d33a6-160">See Also</span></span>
<span data-ttu-id="d33a6-161">Para agregar una aplicación en segundo plano al compilar una imagen personalizada, consulte [crear un paquete appx](../build-your-image/createinstallpackage.md) .</span><span class="sxs-lookup"><span data-stu-id="d33a6-161">To add a background app when building a custom image see [Create an Appx package](../build-your-image/createinstallpackage.md)</span></span>
