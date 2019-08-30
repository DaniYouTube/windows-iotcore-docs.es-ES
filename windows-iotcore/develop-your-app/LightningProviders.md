---
title: Proveedores de Rayo
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga más información sobre cómo puede usar la biblioteca Webstore Lightning Providers.
keywords: Windows IOT, proveedores de Lightning, pruebas de rendimiento de Lightning, buses
ms.openlocfilehash: 50cbf4f9940538da1570cebb6cc142e7fbe06588
ms.sourcegitcommit: fcc0c6add468040e2f676893b44b260e3ddc3c52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65779383"
---
# <a name="working-with-lightning-providers"></a><span data-ttu-id="e8495-104">Trabajar con los proveedores de Lightning</span><span class="sxs-lookup"><span data-stu-id="e8495-104">Working with lightning providers</span></span>
<span data-ttu-id="e8495-105">La biblioteca Microsoft. IoT. Lightning. Providers contiene un conjunto de proveedores para interactuar con los buses del controlador del panel a través del controlador asignado de memoria de Lightning Direct (DMAP).</span><span class="sxs-lookup"><span data-stu-id="e8495-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="e8495-106">Acerca del controlador asignado a memoria directa (DMAP)</span><span class="sxs-lookup"><span data-stu-id="e8495-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="e8495-107">El controlador DMAP es un controlador en desarrollo que proporciona mejoras de rendimiento de GPIO sobre el controlador de bandeja de entrada predeterminado.</span><span class="sxs-lookup"><span data-stu-id="e8495-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="e8495-108">Para obtener más información sobre estas mejoras de rendimiento, visite la página de [pruebas de rendimiento](../develop-your-app/LightningPerformance.md) .</span><span class="sxs-lookup"><span data-stu-id="e8495-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="e8495-109">Mientras que el controlador DMAP ofrece mejoras de rendimiento de GPIO sobre el controlador de bandeja de entrada, los comandos del controlador se envían al controlador DMAP a través de direcciones asignadas a memoria de modo de usuario para cada uno de los controladores.</span><span class="sxs-lookup"><span data-stu-id="e8495-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="e8495-110">Una aplicación que solo usa las API del proveedor de Lightning o Microsoft. IoT. Lightning. Providers.</span><span class="sxs-lookup"><span data-stu-id="e8495-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="e8495-111">Sin embargo, una aplicación malintencionada podría escribir directamente en esa memoria y causar problemas de hardware o seguridad.</span><span class="sxs-lookup"><span data-stu-id="e8495-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="e8495-112">En un equipo que solo tiene aplicaciones de confianza, DMAP suele ser seguro para su uso.</span><span class="sxs-lookup"><span data-stu-id="e8495-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="e8495-113">Obtención de la biblioteca</span><span class="sxs-lookup"><span data-stu-id="e8495-113">Obtaining the library</span></span>

<span data-ttu-id="e8495-114">La biblioteca se proporciona como parte del [paquete Nuget del SDK de Lightning](https://www.nuget.org/packages/Microsoft.IoT.Lightning) con el código fuente disponible en el repositorio de [GitHub MS-IOT/Lightning](https://github.com/ms-iot/lightning/).</span><span class="sxs-lookup"><span data-stu-id="e8495-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="e8495-115">Adicionalmente, ejemplos que muestran cómo usar los diferentes proveedores están disponibles en el [repositorio de github MS-IOT/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span><span class="sxs-lookup"><span data-stu-id="e8495-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="e8495-116">Adición de la biblioteca a la aplicación</span><span class="sxs-lookup"><span data-stu-id="e8495-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="e8495-117">Opción 1: A partir de un ejemplo existente</span><span class="sxs-lookup"><span data-stu-id="e8495-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="e8495-118">Una forma rápida de empezar a codificar con los proveedores de relámpago es empezar con uno de los ejemplos del [repositorio de github MS-IOT/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span><span class="sxs-lookup"><span data-stu-id="e8495-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="e8495-119">Cada uno de los ejemplos hace referencia al relámpago y está configurado correctamente para usar la biblioteca de los proveedores de Lightning.</span><span class="sxs-lookup"><span data-stu-id="e8495-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="e8495-120">**Tenga en cuenta**que, para ejecutar los ejemplos, el controlador DMAP debe estar habilitado mediante el portal web de dispositivos Windows.</span><span class="sxs-lookup"><span data-stu-id="e8495-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="e8495-121">Consulte la [Guía de configuración de Lightning](LightningSetup.md) para obtener información detallada sobre cómo habilitarlo.</span><span class="sxs-lookup"><span data-stu-id="e8495-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="e8495-122">Opción 2: Referencia a la biblioteca</span><span class="sxs-lookup"><span data-stu-id="e8495-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="e8495-123">Además, es sencillo agregar la referencia de Nuget de los proveedores de relámpago necesarios y la compatibilidad con una aplicación nueva o existente.</span><span class="sxs-lookup"><span data-stu-id="e8495-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="e8495-124">Sigue los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e8495-124">Follow the steps below:</span></span>

1. <span data-ttu-id="e8495-125">En su aplicación, haga clic con el botón derecho en el proyecto y haga clic en "administrar paquetes NuGet..." elemento de menú</span><span class="sxs-lookup"><span data-stu-id="e8495-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item</span></span>  
![Proyecto para UWP](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="e8495-127">Se abrirá el administrador de paquetes NuGet.</span><span class="sxs-lookup"><span data-stu-id="e8495-127">The NuGet Package Manager will open.</span></span> <span data-ttu-id="e8495-128">En la pestaña examinar, busque el "rayo SDK" y asegúrese de activar la casilla "incluir versión preliminar".</span><span class="sxs-lookup"><span data-stu-id="e8495-128">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="e8495-129">Seleccione la última versión y haga clic en "instalar" para agregar el SDK de Lightning a su proyecto.</span><span class="sxs-lookup"><span data-stu-id="e8495-129">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
<span data-ttu-id="e8495-130">![Administrador de paquetes NuGet](../media/LightningProviders/nuget-package-manager.png)</span><span class="sxs-lookup"><span data-stu-id="e8495-130">![NuGet Package Manager](../media/LightningProviders/nuget-package-manager.png)</span></span>

4. <span data-ttu-id="e8495-131">Siga las instrucciones que aparecen en pantalla, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="e8495-131">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="e8495-132">Una vez completada la instalación, se agregará al proyecto una referencia al SDK de Lightning.</span><span class="sxs-lookup"><span data-stu-id="e8495-132">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![Referencia del SDK de Lightning](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="e8495-134">Agregue el código siguiente al archivo de manifiesto, package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="e8495-134">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="e8495-135">La primera es una funcionalidad que permitirá a la aplicación tener acceso a los dispositivos personalizados.</span><span class="sxs-lookup"><span data-stu-id="e8495-135">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="e8495-136">El segundo es el identificador del GUID del dispositivo de la interfaz de relámpago</span><span class="sxs-lookup"><span data-stu-id="e8495-136">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="e8495-137">Ambas capacidades deben agregarse al manifiesto appx del proyecto en el `<Capabilities>` nodo.</span><span class="sxs-lookup"><span data-stu-id="e8495-137">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="e8495-138">Además, asegúrese de agregar los espacios de nombres necesarios al manifiesto, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="e8495-138">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![Manifiesto AppX Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="e8495-140">Actualización del código para usar los proveedores de Lightning</span><span class="sxs-lookup"><span data-stu-id="e8495-140">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="e8495-141">Comprobando el controlador Lightning (DMAP)</span><span class="sxs-lookup"><span data-stu-id="e8495-141">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="e8495-142">Para comprobar si el relámpago está habilitado `LightningProvider.IsLightningEnabled` , se debe usar la propiedad.</span><span class="sxs-lookup"><span data-stu-id="e8495-142">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="e8495-143">En general, siempre es recomendable comprobar si el controlador de Lightning está habilitado antes de usar las API del proveedor de Lightning.</span><span class="sxs-lookup"><span data-stu-id="e8495-143">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="e8495-144">Patrón de uso general</span><span class="sxs-lookup"><span data-stu-id="e8495-144">General usage pattern</span></span>

<span data-ttu-id="e8495-145">La manera más sencilla de usar los proveedores es establecer el proveedor de relámpago como el valor predeterminado dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e8495-145">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="e8495-146">El código siguiente mostrará, si el proveedor de relámpago está disponible, `Microsoft.IoT.Lightning.Providers.LightningProvider` establecido como el proveedor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="e8495-146">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="e8495-147">De lo contrario, si no se establece explícitamente ningún proveedor predeterminado, los distintos buses revertirán al valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="e8495-147">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
if (LightningProvider.IsLightningEnabled)
{
    LowLevelDevicesController.DefaultProvider = LightningProvider.GetAggregateProvider();
}

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
spiController = await SpiController.GetDefaultAsync();
```

<span data-ttu-id="e8495-148">Una vez que tenga un controlador para el bus deseado, puede usarlo como lo haría normalmente.</span><span class="sxs-lookup"><span data-stu-id="e8495-148">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="e8495-149">Uso de Lightning para buses individuales</span><span class="sxs-lookup"><span data-stu-id="e8495-149">Using Lightning for individual buses</span></span>

<span data-ttu-id="e8495-150">Si desea usar un proveedor predeterminado diferente, en las secciones siguientes se muestra cómo puede usar los proveedores de relámpagos para buses individuales.</span><span class="sxs-lookup"><span data-stu-id="e8495-150">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="e8495-151">Para controlador de bus GPIO:</span><span class="sxs-lookup"><span data-stu-id="e8495-151">For GPIO bus controller:</span></span>

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.Gpio;

if (LightningProvider.IsLightningEnabled)
{
    GpioController gpioController = (await GpioController.GetControllersAsync(LightningGpioProvider.GetGpioProvider()))[0];
    GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);
}
```

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="e8495-152">Para controlador de bus I2C:</span><span class="sxs-lookup"><span data-stu-id="e8495-152">For I2C bus controller:</span></span>

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.I2c;

if (LightningProvider.IsLightningEnabled)
{
    I2cController controller =  (await I2cController.GetControllersAsync(LightningI2cProvider.GetI2cProvider()))[0];
    I2cDevice sensor = controller.GetDevice(new I2cConnectionSettings(0x40));
}
```

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="e8495-153">Para controlador de bus SPI:</span><span class="sxs-lookup"><span data-stu-id="e8495-153">For SPI bus controller:</span></span>
<span data-ttu-id="e8495-154">usar Microsoft. IoT. Lightning. Providers; usar Windows. Devices; uso de Windows. Devices. SPI;</span><span class="sxs-lookup"><span data-stu-id="e8495-154">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="e8495-155">Ejemplos del proveedor de Lightning</span><span class="sxs-lookup"><span data-stu-id="e8495-155">Lightning Provider Samples</span></span>

<span data-ttu-id="e8495-156">Los ejemplos siguientes muestran cómo usar los proveedores de Lightning con tipos de bus compatibles:</span><span class="sxs-lookup"><span data-stu-id="e8495-156">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="e8495-157">[Parpadeo (UI) con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) muestra el GPIO con el proveedor de Lightning en una aplicación en primer plano</span><span class="sxs-lookup"><span data-stu-id="e8495-157">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="e8495-158">[BlinkyHeadless con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) muestra GPIO con el proveedor de Lightning en una aplicación sin periféricos</span><span class="sxs-lookup"><span data-stu-id="e8495-158">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="e8495-159">[SPIDisplay con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) muestra el uso de la API para controlar un dispositivo con SPI con el proveedor de Lightning</span><span class="sxs-lookup"><span data-stu-id="e8495-159">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="e8495-160">[WeatherStation con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) muestra la interacción con un dispositivo mediante I2C con el proveedor de Lightning</span><span class="sxs-lookup"><span data-stu-id="e8495-160">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="e8495-161">Requisitos de compilación</span><span class="sxs-lookup"><span data-stu-id="e8495-161">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="e8495-162">Windows SDK Update</span><span class="sxs-lookup"><span data-stu-id="e8495-162">Windows SDK Update</span></span>

<span data-ttu-id="e8495-163">Windows SDK necesario para compilar y usar la biblioteca es 10.0.10586.0 o posterior que se puede descargar desde [aquí](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="e8495-163">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="e8495-164">Para obtener más información sobre cómo configurar todo, consulte [nuestra guía](https://developer.microsoft.com/en-us/windows/iot/getstarted)de introducción.</span><span class="sxs-lookup"><span data-stu-id="e8495-164">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="e8495-165">Dependencias de paquetes Nuget</span><span class="sxs-lookup"><span data-stu-id="e8495-165">Nuget Package Dependencies</span></span>

<span data-ttu-id="e8495-166">La biblioteca del proveedor de Lightning depende del [paquete Nuget Microsoft. iot. Lightning](https://www.nuget.org/packages/Microsoft.IoT.Lightning)que, a su vez, depende del [paquete Nuget del SDK de Arduino](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span><span class="sxs-lookup"><span data-stu-id="e8495-166">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="e8495-167">En los proyectos de biblioteca se hace referencia a ambos paquetes Nuget y están disponibles en Nuget.org.</span><span class="sxs-lookup"><span data-stu-id="e8495-167">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="e8495-168">Si es necesario, el código fuente de cada uno de ellos también está disponible en GitHub en los repositorios del SDK de [Lightning](https://github.com/ms-iot/lightning) y [Arduino](https://github.com/ms-iot/arduino-sdk) .</span><span class="sxs-lookup"><span data-stu-id="e8495-168">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="e8495-169">Actualmente, Microsoft. IoT. Lightning Nuget todavía está en versión preliminar, por lo que debe actualizarse desde Nuget.org, cuando haya versiones más recientes disponibles.</span><span class="sxs-lookup"><span data-stu-id="e8495-169">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="e8495-170">Para instalar la versión preliminar (actual) del paquete de Nuget Microsoft. IoT. Lightning y recibir actualizaciones de la versión preliminar del paquete de relámpago, asegúrese de establecer la opción "incluir versión preliminar" en el administrador de paquetes Nuget.</span><span class="sxs-lookup"><span data-stu-id="e8495-170">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="e8495-171">Haga clic con el botón derecho en referencias en el proyecto</span><span class="sxs-lookup"><span data-stu-id="e8495-171">Right click References in your project</span></span>
1. <span data-ttu-id="e8495-172">Haga clic en "administrar paquetes Nuget..."</span><span class="sxs-lookup"><span data-stu-id="e8495-172">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="e8495-173">Selección de orígenes de paquetes para Lightning Nuget</span><span class="sxs-lookup"><span data-stu-id="e8495-173">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="e8495-174">Haga clic en "incluir versión preliminar".</span><span class="sxs-lookup"><span data-stu-id="e8495-174">Click "Include prerelease".</span></span>
1. <span data-ttu-id="e8495-175">Haga clic en "instalar" para instalar el paquete Nuget en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="e8495-175">Click "Install" to install the nuget package to your project</span></span>

![Configuración del administrador de paquetes](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="e8495-177">Requisitos de tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="e8495-177">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="e8495-178">Se requiere la actualización de Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="e8495-178">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="e8495-179">La compatibilidad con los proveedores de Lightning está incluida actualmente en las compilaciones de actualización para Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e8495-179">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="e8495-180">Puede descargar una imagen de Windows 10 IoT Core desde nuestra [Página de descargas](https://developer.microsoft.com/windows/iot/Downloads).</span><span class="sxs-lookup"><span data-stu-id="e8495-180">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="e8495-181">Haga clic en "descargar Insider Preview" para el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e8495-181">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="e8495-182">El controlador asignado a memoria directa debe estar habilitado</span><span class="sxs-lookup"><span data-stu-id="e8495-182">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="e8495-183">Las API de la biblioteca del proveedor de Lightning requieren que el controlador asignado de la memoria de Lightning Direct esté habilitado en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="e8495-183">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="e8495-184">Tanto Raspberry pi 2/3 como MinnowBoard Max tienen el controlador disponible, pero no está habilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="e8495-184">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="e8495-185">El controlador se puede habilitar mediante el portal web de dispositivos Windows.</span><span class="sxs-lookup"><span data-stu-id="e8495-185">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="e8495-186">Consulte la [Guía de configuración de Lightning](LightningSetup.md) para obtener información detallada acerca de cómo habilitar el controlador de Lightning.</span><span class="sxs-lookup"><span data-stu-id="e8495-186">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![Página dispositivos](../media/LightningProviders/dmap4.png)

<span data-ttu-id="e8495-188">El controlador también se puede habilitar con el comando DmapUtil:</span><span class="sxs-lookup"><span data-stu-id="e8495-188">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="e8495-189">DmapUtil: Para activar o desactivar el uso del controlador del asignador de memoria directo de DMAP: estado de dmaputil. exe | Enable | Disable status [-v] imprime si DMAP está habilitado actualmente.</span><span class="sxs-lookup"><span data-stu-id="e8495-189">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="e8495-190">Pase la marca-v para obtener información de configuración detallada.</span><span class="sxs-lookup"><span data-stu-id="e8495-190">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="e8495-191">Habilite habilitar DMAP en el siguiente arranque.</span><span class="sxs-lookup"><span data-stu-id="e8495-191">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="e8495-192">deshabilitar deshabilitar DMAP en el siguiente arranque.</span><span class="sxs-lookup"><span data-stu-id="e8495-192">disable       Disable dmap on next boot.</span></span>
