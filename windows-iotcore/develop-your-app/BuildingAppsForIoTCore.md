---
title: Desarrollo de aplicaciones de primer plano
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los lenguajes y los tipos de aplicaciones compatibles con IoT Core.
keywords: Windows IOT, idiomas, tipos de aplicaciones, UWP, compatible
ms.openlocfilehash: e0eb046ba874e8433e7632d3f88a63a90b88fa2b
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627399"
---
# <a name="developing-foreground-applications"></a><span data-ttu-id="c93eb-104">Desarrollo de aplicaciones de primer plano</span><span class="sxs-lookup"><span data-stu-id="c93eb-104">Developing foreground applications</span></span>
<span data-ttu-id="c93eb-105">Obtenga información sobre los idiomas que se admiten en Windows 10 IoT Core, así como en los tipos de aplicaciones UWP y no UWP que se admiten en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c93eb-105">Learn about the languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported on IoT Core.</span></span>


> [!NOTE]
> <span data-ttu-id="c93eb-106">Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c93eb-106">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="application-types"></a><span data-ttu-id="c93eb-107">Tipos de aplicación</span><span class="sxs-lookup"><span data-stu-id="c93eb-107">Application Types</span></span>
___

### <a name="universal-windows-platform-uwp-apps"></a><span data-ttu-id="c93eb-108">Aplicaciones Plataforma universal de Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="c93eb-108">Universal Windows Platform (UWP) Apps</span></span>
<span data-ttu-id="c93eb-109">IoT Core es un sistema operativo centrado en UWP y las aplicaciones para UWP son el tipo de aplicación principal.</span><span class="sxs-lookup"><span data-stu-id="c93eb-109">IoT Core is a UWP centric OS and UWP apps are its primary app type.</span></span>

<span data-ttu-id="c93eb-110">Plataforma universal de Windows (UWP) es una plataforma de aplicaciones común en todas las versiones de Windows 10, incluida Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c93eb-110">Universal Windows Platform (UWP) is a common app platform across all version of Windows 10, including Windows 10 IoT Core.</span></span>  <span data-ttu-id="c93eb-111">UWP es una evolución de Windows Runtime (WinRT).</span><span class="sxs-lookup"><span data-stu-id="c93eb-111">UWP is an evolution of Windows Runtime (WinRT).</span></span> <span data-ttu-id="c93eb-112">Puede encontrar más información y una introducción a UWP [aquí](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span><span class="sxs-lookup"><span data-stu-id="c93eb-112">You can find more information and an overview to UWP [here](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).</span></span>

<span data-ttu-id="c93eb-113">Visual Studio es la herramienta principal para escribir aplicaciones para UWP para IoT Core y en general.</span><span class="sxs-lookup"><span data-stu-id="c93eb-113">Visual Studio is the primary tool for writing UWP apps for IoT Core and in general.</span></span> <span data-ttu-id="c93eb-114">Puede encontrar una lista detallada de los requisitos de compatibilidad de Visual Studio [aquí](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span><span class="sxs-lookup"><span data-stu-id="c93eb-114">You can find a detailed listing of the compatibility requirements for Visual Studio [here](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>


### <a name="traditional-uwp-apps"></a><span data-ttu-id="c93eb-115">Aplicaciones de UWP tradicionales</span><span class="sxs-lookup"><span data-stu-id="c93eb-115">Traditional UWP Apps</span></span>
<span data-ttu-id="c93eb-116">Las aplicaciones para UWP funcionan solo en IoT Core, al igual que en otras ediciones de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c93eb-116">UWP apps just work on IoT Core, just as they do on other Windows 10 editions.</span></span> <span data-ttu-id="c93eb-117">Una aplicación XAML sencilla y vacía en Visual Studio se implementará correctamente en el dispositivo IoT Core tal como lo haría en un teléfono o en un equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c93eb-117">A simple, blank Xaml app in Visual Studio will properly deploy to your IoT Core device just as it would on a phone or Windows 10 PC.</span></span> <span data-ttu-id="c93eb-118">Todos los lenguajes y plantillas de proyecto estándar de UWP son totalmente compatibles con IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c93eb-118">All of the standard UWP languages and project templates are fully supported on IoT Core.</span></span>

<span data-ttu-id="c93eb-119">Hay algunas adiciones al modelo de aplicación de UWP tradicional para admitir escenarios de IoT y cualquier aplicación para UWP que se beneficie de ellas necesitará la información correspondiente agregada a su manifiesto.</span><span class="sxs-lookup"><span data-stu-id="c93eb-119">There are a few additions to the traditional UWP app-model to support IoT scenarios and any UWP app that takes advantage of them will need the corresponding information added to their manifest.</span></span> <span data-ttu-id="c93eb-120">En particular, el espacio de nombres "IOT" debe agregarse al manifiesto de estas aplicaciones estándar de UWP.</span><span class="sxs-lookup"><span data-stu-id="c93eb-120">In particular the "iot" namespace needs to be added to the manifest of these standard UWP apps.</span></span> 

<span data-ttu-id="c93eb-121">Dentro del <Package> atributo del manifiesto, debe definir el xmlns de IOT y agregarlo a la lista IgnorableNamespaces.</span><span class="sxs-lookup"><span data-stu-id="c93eb-121">Inside the <Package> attribute of the manifest, you need to define the iot xmlns and add it to the IgnorableNamespaces list.</span></span> <span data-ttu-id="c93eb-122">El XML final debería ser similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="c93eb-122">The final xml should look like this:</span></span> 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a><span data-ttu-id="c93eb-123">Aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="c93eb-123">Background Apps</span></span>
<span data-ttu-id="c93eb-124">Además de las aplicaciones de interfaz de usuario tradicionales, IoT Core ha agregado un nuevo tipo de aplicación de UWP denominado "aplicaciones en segundo plano".</span><span class="sxs-lookup"><span data-stu-id="c93eb-124">In addition to the traditional UI apps, IoT Core has added a new UWP app type called "Background Applications".</span></span> <span data-ttu-id="c93eb-125">Estas aplicaciones no tienen un componente de interfaz de usuario, pero en su lugar tienen una clase que implementa la interfaz "IBackgroundTask".</span><span class="sxs-lookup"><span data-stu-id="c93eb-125">These applications do not have a UI component, but instead have a class that implements the "IBackgroundTask" interface.</span></span> <span data-ttu-id="c93eb-126">Después, registran esa clase como "StartupTask" para que se ejecute en el arranque del sistema.</span><span class="sxs-lookup"><span data-stu-id="c93eb-126">They then register that class as a "StartupTask" to run at system boot.</span></span> <span data-ttu-id="c93eb-127">Dado que todavía son aplicaciones para UWP, tienen acceso al mismo conjunto de API y son compatibles con el mismo lenguaje.</span><span class="sxs-lookup"><span data-stu-id="c93eb-127">Since they are still UWP apps, they have access to the same set of APIs and are supported from the same language.</span></span> <span data-ttu-id="c93eb-128">La única diferencia es que no hay ningún punto de entrada de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c93eb-128">The only difference is that there is no UI entry point.</span></span>

<span data-ttu-id="c93eb-129">Cada tipo de IBackgroundTask obtiene su propia Directiva de recursos.</span><span class="sxs-lookup"><span data-stu-id="c93eb-129">Each type of IBackgroundTask gets its own resource policy.</span></span> <span data-ttu-id="c93eb-130">Esto suele ser restrictivo para mejorar la duración de la batería y los recursos de la máquina en los dispositivos en los que estas aplicaciones en segundo plano son componentes secundarios de aplicaciones de interfaz de usuario de primer plano.</span><span class="sxs-lookup"><span data-stu-id="c93eb-130">This is usually restrictive to improve battery life and machine resources on devices where these background apps are secondary components of foreground UI apps.</span></span> <span data-ttu-id="c93eb-131">En los dispositivos IoT, las aplicaciones en segundo plano suelen ser la función principal del dispositivo, por lo que estas StartupTasks obtienen una directiva de recursos que refleja las aplicaciones de interfaz de usuario de primer plano en otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c93eb-131">On IoT devices, Background Apps are often the primary function of the device and so these StartupTasks get a resource policy that mirrors foreground UI apps on other devices.</span></span>

<span data-ttu-id="c93eb-132">En el ejemplo siguiente se muestra el código necesario para C# compilar una aplicación en segundo plano que parpadee un LED:</span><span class="sxs-lookup"><span data-stu-id="c93eb-132">The following sample shows the code necessary to build a C# Background App that blinks an LED:</span></span>

```C#
namespace BlinkyHeadlessCS
{
    public sealed class StartupTask : IBackgroundTask
    {
        BackgroundTaskDeferral deferral;
        private GpioPinValue value = GpioPinValue.High;
        private const int LED_PIN = 5;
        private GpioPin pin;
        private ThreadPoolTimer timer;

        public void Run(IBackgroundTaskInstance taskInstance)        {
            deferral = taskInstance.GetDeferral();
            InitGPIO();
            timer = ThreadPoolTimer.CreatePeriodicTimer(Timer_Tick, TimeSpan.FromMilliseconds(500));

        }
        private void InitGPIO()
        {
            pin = GpioController.GetDefault().OpenPin(LED_PIN);
            pin.Write(GpioPinValue.High);
            pin.SetDriveMode(GpioPinDriveMode.Output);
        }

        private void Timer_Tick(ThreadPoolTimer timer)
        {
            value = (value == GpioPinValue.High) ? GpioPinValue.Low : GpioPinValue.High;
            pin.Write(value);
        }
    }
}
```

<span data-ttu-id="c93eb-133">Puede encontrar información detallada sobre las aplicaciones en segundo plano [aquí](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span><span class="sxs-lookup"><span data-stu-id="c93eb-133">You can find in-depth information on Background apps [here](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

### <a name="non-uwp-apps"></a><span data-ttu-id="c93eb-134">Aplicaciones que no son de UWP</span><span class="sxs-lookup"><span data-stu-id="c93eb-134">Non-UWP Apps</span></span>
<span data-ttu-id="c93eb-135">IoT Core admite determinados tipos de aplicaciones Win32 tradicionales, como aplicaciones de consola Win32 y servicios NT.</span><span class="sxs-lookup"><span data-stu-id="c93eb-135">IoT Core supports certain traditional Win32 app types such as Win32 Console Apps and NT Services.</span></span> <span data-ttu-id="c93eb-136">Estas aplicaciones se compilan y ejecutan de la misma manera que en el escritorio de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="c93eb-136">These apps are built and run the same way as on Windows 10 Desktop.</span></span> <span data-ttu-id="c93eb-137">Además, hay una plantilla de proyecto C++ de consola de IOT Core que facilita la compilación de aplicaciones con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c93eb-137">Additionally, there is an IoT Core C++ Console project template to make it easy to build such apps using Visual Studio.</span></span>

<span data-ttu-id="c93eb-138">Existen dos limitaciones principales en estas aplicaciones que no son de UWP:</span><span class="sxs-lookup"><span data-stu-id="c93eb-138">There are two main limitations on these non-UWP applications:</span></span>
1. <span data-ttu-id="c93eb-139">*No compatible con la interfaz de usuario de Win32 heredada:* IoT Core no contiene las API para crear ventanas clásicas (HWND).</span><span class="sxs-lookup"><span data-stu-id="c93eb-139">*No legacy Win32 UI support:* IoT Core does not contain APIs to create classic (HWND) Windows.</span></span> <span data-ttu-id="c93eb-140">Los métodos heredados como CreateWindow () y CreateWindowEx () o cualquier otro método que trate con identificadores de Windows (HWND) no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="c93eb-140">Legacy methods such as CreateWindow() and CreateWindowEx() or any other methods that deal with Windows handles (HWNDs) are not available.</span></span> <span data-ttu-id="c93eb-141">Posteriormente, los marcos que dependen de estas API, como MFC, Windows Forms y WPF, no se admiten en IoT Core</span><span class="sxs-lookup"><span data-stu-id="c93eb-141">Subsequently, frameworks that depend on such APIs including MFC, Windows Forms and WPF, are not supported on IoT Core</span></span>
2. <span data-ttu-id="c93eb-142">*C++Solo aplicaciones:* Actualmente, solo C++ se admite para desarrollar aplicaciones Win32 en IOT Core.</span><span class="sxs-lookup"><span data-stu-id="c93eb-142">*C++ Apps Only:* Currently, only C++ is supported for developing Win32 apps on IoT Core.</span></span>

## <a name="programming-languages"></a><span data-ttu-id="c93eb-143">Lenguajes de programación</span><span class="sxs-lookup"><span data-stu-id="c93eb-143">Programming Languages</span></span>
___

<span data-ttu-id="c93eb-144">IoT Core admite una amplia variedad de lenguajes de programación.</span><span class="sxs-lookup"><span data-stu-id="c93eb-144">IoT Core supports a wide range of programming languages.</span></span>

### <a name="in-box-languages"></a><span data-ttu-id="c93eb-145">Idiomas en caja</span><span class="sxs-lookup"><span data-stu-id="c93eb-145">In-Box languages</span></span>
<span data-ttu-id="c93eb-146">Los lenguajes de UWP tradicionales se incluyen de forma predeterminada en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c93eb-146">Traditional UWP languages ship with support in Visual Studio by default.</span></span> <span data-ttu-id="c93eb-147">Todos los lenguajes integrados admiten las aplicaciones de interfaz de usuario y en segundo plano</span><span class="sxs-lookup"><span data-stu-id="c93eb-147">All of the In-Box languages support both UI and Background Applications</span></span>
 
* <span data-ttu-id="c93eb-148">Idiomas</span><span class="sxs-lookup"><span data-stu-id="c93eb-148">Languages</span></span>
  * <span data-ttu-id="c93eb-149">C#</span><span class="sxs-lookup"><span data-stu-id="c93eb-149">C#</span></span>
  * <span data-ttu-id="c93eb-150">C++</span><span class="sxs-lookup"><span data-stu-id="c93eb-150">C++</span></span>
  * <span data-ttu-id="c93eb-151">Código</span><span class="sxs-lookup"><span data-stu-id="c93eb-151">Javascript</span></span>
  * <span data-ttu-id="c93eb-152">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c93eb-152">Visual Basic</span></span>

### <a name="arduino-wiring"></a><span data-ttu-id="c93eb-153">Cableado de Arduino</span><span class="sxs-lookup"><span data-stu-id="c93eb-153">Arduino Wiring</span></span>
 <span data-ttu-id="c93eb-154">El cableado Arduino requiere la descarga de las "plantillas de proyecto de Windows IoT Core" desde las extensiones de Visual Studio **Tools-> y updates** Manager.</span><span class="sxs-lookup"><span data-stu-id="c93eb-154">Arduino Wiring requires the download of the "Windows IoT Core Project Templates" from the Visual Studio **Tools->Extensions and Updates** manager.</span></span>  <span data-ttu-id="c93eb-155">El cableado Arduino solo admite aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c93eb-155">Arduino Wiring supports only Background Applications.</span></span> <span data-ttu-id="c93eb-156">También puede compilar *componentes* de C#Windows Runtime C++mediante, o Visual Basic y, después, hacer referencia a esas bibliotecas desde cualquier otro lenguaje.</span><span class="sxs-lookup"><span data-stu-id="c93eb-156">You can also build *Windows Runtime Components* using C#, C++, or Visual Basic and then reference those libraries from any other language.</span></span>

### <a name="c-and-visual-basic-vb"></a><span data-ttu-id="c93eb-157">C#y Visual Basic (VB)</span><span class="sxs-lookup"><span data-stu-id="c93eb-157">C# and Visual Basic (VB)</span></span>
<span data-ttu-id="c93eb-158">C#y VB se admiten como aplicaciones UWP y tienen acceso a la parte de .NET Framework disponible para las aplicaciones de UWP.</span><span class="sxs-lookup"><span data-stu-id="c93eb-158">C# and VB are both supported as UWP apps and have access to the portion of the .Net Framework available to UWP applications.</span></span> <span data-ttu-id="c93eb-159">Admiten aplicaciones de interfaz de usuario compiladas con XAML y aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c93eb-159">They support UI apps built with Xaml as well as Background Apps.</span></span> <span data-ttu-id="c93eb-160">También puede compilar *componentes de Windows Runtime* que se pueden usar desde otros idiomas admitidos.</span><span class="sxs-lookup"><span data-stu-id="c93eb-160">You can also build *Windows Runtime Components* that can be used from other supported languages.</span></span>

<span data-ttu-id="c93eb-161">Assembl</span><span class="sxs-lookup"><span data-stu-id="c93eb-161">Samples:</span></span>


* [<span data-ttu-id="c93eb-162">C#Sin periféricos</span><span class="sxs-lookup"><span data-stu-id="c93eb-162">C# Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [<span data-ttu-id="c93eb-163">Parpadeo de VB sin periféricos</span><span class="sxs-lookup"><span data-stu-id="c93eb-163">VB Blinky Headless</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [<span data-ttu-id="c93eb-164">C#Aplicación de interfaz de usuario de parpadeo</span><span class="sxs-lookup"><span data-stu-id="c93eb-164">C# Blinky UI App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a><span data-ttu-id="c93eb-165">Código</span><span class="sxs-lookup"><span data-stu-id="c93eb-165">Javascript</span></span>
<span data-ttu-id="c93eb-166">Puede usar JavaScript para compilar aplicaciones en la interfaz de usuario y en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="c93eb-166">You can use Javascript to build both UI and Background Apps.</span></span> <span data-ttu-id="c93eb-167">Las aplicaciones de interfaz de usuario funcionan de la misma manera que en todas las ediciones de UWP.</span><span class="sxs-lookup"><span data-stu-id="c93eb-167">The UI apps work the same way they do on all UWP editions.</span></span> <span data-ttu-id="c93eb-168">Las aplicaciones en segundo plano son nuevas para IoT Core, pero son muy sencillas.</span><span class="sxs-lookup"><span data-stu-id="c93eb-168">The Background Apps are new for IoT Core but are very simple.</span></span> <span data-ttu-id="c93eb-169">En el código de ejemplo siguiente se muestra la salida de una *plantilla de proyecto New de JS*:</span><span class="sxs-lookup"><span data-stu-id="c93eb-169">The following sample code shows the output of a the *JS New Project Template*:</span></span>

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a><span data-ttu-id="c93eb-170">C++</span><span class="sxs-lookup"><span data-stu-id="c93eb-170">C++</span></span>
<span data-ttu-id="c93eb-171">Con C++ puede compilar aplicaciones de interfaz de usuario de DirectX o XAML, así como proyectos en segundo plano para UWP y aplicaciones *de Win32 que no son de interfaz de usuario* .</span><span class="sxs-lookup"><span data-stu-id="c93eb-171">With C++ you can build Xaml or DirectX UI apps, as well as UWP Background projects and *non-UI* Win32 apps.</span></span>

<span data-ttu-id="c93eb-172">Assembl</span><span class="sxs-lookup"><span data-stu-id="c93eb-172">Samples:</span></span>

* [<span data-ttu-id="c93eb-173">Sin periféricos</span><span class="sxs-lookup"><span data-stu-id="c93eb-173">Blinky Headless</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [<span data-ttu-id="c93eb-174">Punta de parpadeo</span><span class="sxs-lookup"><span data-stu-id="c93eb-174">Blinky Headed</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [<span data-ttu-id="c93eb-175">Aplicación de consola</span><span class="sxs-lookup"><span data-stu-id="c93eb-175">Console App</span></span>](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> <span data-ttu-id="c93eb-176">En el caso de aquellos que planean escribir su C++aplicación en, debe activar la casilla de C++ UWP al descargar.</span><span class="sxs-lookup"><span data-stu-id="c93eb-176">For those who are planning to write their app in C++, you'll need to check the UWP C++ checkbox upon downloading.</span></span>

![C++para Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a><span data-ttu-id="c93eb-178">Cableado de Arduino</span><span class="sxs-lookup"><span data-stu-id="c93eb-178">Arduino Wiring</span></span>
<span data-ttu-id="c93eb-179">Gracias a la compatibilidad con el cableado Arduino, puede crear aplicaciones en el cableado de Arduino para muchos componentes y periféricos populares en el ecosistema de IoT.</span><span class="sxs-lookup"><span data-stu-id="c93eb-179">With Arduino Wiring support you can build apps in Arduino Wiring for many popular components and peripherals in the IoT ecosystem.</span></span>

<span data-ttu-id="c93eb-180">Nuestra [Guía de proyecto de Arduino cables](../learn-about-hardware/ArduinoWiringProjectGuide.md) proporciona instrucciones completas sobre cómo configurar para compilar estas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c93eb-180">Our [Arduino Wiring Project Guide](../learn-about-hardware/ArduinoWiringProjectGuide.md) provides full instructions on how to get set up to build these apps.</span></span> <span data-ttu-id="c93eb-181">Los ejemplos copiados y vinculados a continuación le ayudarán a empezar a crear el suyo propio.</span><span class="sxs-lookup"><span data-stu-id="c93eb-181">The samples copied and linked below will help you get started building your own.</span></span>  <span data-ttu-id="c93eb-182">Incluso puede compilar [componentes de WinRT en Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) que luego se pueden usar desde otros idiomas.</span><span class="sxs-lookup"><span data-stu-id="c93eb-182">You can even [build WinRT components in Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) that can then be used from other languages.</span></span> 

<span data-ttu-id="c93eb-183">*Código de ejemplo de parpadeo* El [código de ejemplo completo y los documentos](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) están disponibles en nuestra página de ejemplos y puede encontrar el código completo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c93eb-183">*Blinky Sample Code* The full [sample code and docs](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) are available on our samples page and you can find the full code below:</span></span>

```C++
void setup()
{
    // put your setup code here, to run once:

    pinMode(GPIO5, OUTPUT);
}

void loop()
{
    // put your main code here, to run repeatedly:

    digitalWrite(GPIO5, LOW);
    delay(500);
    digitalWrite(GPIO5, HIGH);
    delay(500);
}
```
