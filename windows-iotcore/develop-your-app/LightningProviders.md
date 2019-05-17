---
title: Proveedores de Rayo
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Más información acerca de cómo puede usar la biblioteca de proveedores de rayo de Microsoft.
keywords: Windows iot, proveedores de rayos, relámpago prueba de rendimiento, buses
ms.openlocfilehash: 50cbf4f9940538da1570cebb6cc142e7fbe06588
ms.sourcegitcommit: fcc0c6add468040e2f676893b44b260e3ddc3c52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65779383"
---
# <a name="working-with-lightning-providers"></a><span data-ttu-id="6fb58-104">Trabajar con proveedores de rayo</span><span class="sxs-lookup"><span data-stu-id="6fb58-104">Working with lightning providers</span></span>
<span data-ttu-id="6fb58-105">La biblioteca Microsoft.IoT.Lightning.Providers contiene un conjunto de proveedores para interactuar con el panel de buses de controlador a través de la luz controlador directo a memoria asignada (DMAP).</span><span class="sxs-lookup"><span data-stu-id="6fb58-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="6fb58-106">Acerca de la memoria directa asignado el controlador (DMAP)</span><span class="sxs-lookup"><span data-stu-id="6fb58-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="6fb58-107">El controlador DMAP es un controlador de desarrollo que proporciona mejoras de rendimiento de GPIO por el controlador predeterminado de la Bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="6fb58-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="6fb58-108">Para obtener información sobre estas mejoras de rendimiento, visite la [las pruebas de rendimiento increíblemente](../develop-your-app/LightningPerformance.md) página.</span><span class="sxs-lookup"><span data-stu-id="6fb58-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="6fb58-109">Mientras DMAP controlador oferta GPIO mejoras de rendimiento sobre el controlador de bandeja de entrada, los comandos del controlador se envían al controlador DMAP a través de direcciones de memoria asignada de modo de usuario para cada uno de los controladores.</span><span class="sxs-lookup"><span data-stu-id="6fb58-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="6fb58-110">Una aplicación que solo se usa la API del proveedor de rayo o Microsoft.IoT.Lightning.Providers.</span><span class="sxs-lookup"><span data-stu-id="6fb58-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="6fb58-111">Sin embargo, una aplicación malintencionada sería capaz de escribir directamente en el que la memoria y provocar problemas de hardware o de seguridad.</span><span class="sxs-lookup"><span data-stu-id="6fb58-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="6fb58-112">En un equipo con sólo las aplicaciones de confianza, el DMAP generalmente uso es seguro.</span><span class="sxs-lookup"><span data-stu-id="6fb58-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="6fb58-113">Obtención de la biblioteca</span><span class="sxs-lookup"><span data-stu-id="6fb58-113">Obtaining the library</span></span>

<span data-ttu-id="6fb58-114">La biblioteca se proporciona como parte de la [paquete Nuget del SDK relámpago](https://www.nuget.org/packages/Microsoft.IoT.Lightning) con código fuente disponible en [repositorio de GitHub de ms-iot/relámpago](https://github.com/ms-iot/lightning/).</span><span class="sxs-lookup"><span data-stu-id="6fb58-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="6fb58-115">Además, los ejemplos que muestran cómo usar los diferentes proveedores están disponibles en [repositorio de GitHub de ms-iot/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span><span class="sxs-lookup"><span data-stu-id="6fb58-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="6fb58-116">Agregar la biblioteca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="6fb58-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="6fb58-117">Opción 1: A partir de un ejemplo existente</span><span class="sxs-lookup"><span data-stu-id="6fb58-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="6fb58-118">Una forma rápida para comenzar a codificar con los proveedores de rayos es comenzar con uno de los ejemplos en los [repositorio de GitHub de ms-iot/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span><span class="sxs-lookup"><span data-stu-id="6fb58-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="6fb58-119">Cada uno de los ejemplos hace referencia al SDK de rayo y está configurado correctamente para usar la biblioteca de proveedores de rayo.</span><span class="sxs-lookup"><span data-stu-id="6fb58-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="6fb58-120">**Tenga en cuenta**, para ejecutar los ejemplos, la necesidad de controlador DMAP habilitarse mediante el Portal Web de los dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="6fb58-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="6fb58-121">Hacer referencia a la [Guía de instalación de rayo](LightningSetup.md) para obtener información detallada sobre cómo habilitarlo.</span><span class="sxs-lookup"><span data-stu-id="6fb58-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="6fb58-122">Opción 2: Hacer referencia a la biblioteca</span><span class="sxs-lookup"><span data-stu-id="6fb58-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="6fb58-123">Además, es fácil de agregar la referencia de Nuget de proveedores de rayo requerida y soporte técnico a una aplicación nueva o existente.</span><span class="sxs-lookup"><span data-stu-id="6fb58-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="6fb58-124">Sigue los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="6fb58-124">Follow the steps below:</span></span>

1. <span data-ttu-id="6fb58-125">En su aplicación, a la derecha, haga clic en el proyecto y haga clic en el "Administrar paquetes NuGet" elemento de menú</span><span class="sxs-lookup"><span data-stu-id="6fb58-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item</span></span>  
![Proyecto para UWP](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="6fb58-127">Se abrirá el Administrador de paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="6fb58-127">The NuGet Package Manager will open.</span></span> <span data-ttu-id="6fb58-128">En la pestaña Examinar, busque el "relámpago SDK", y asegúrese de activar la casilla "Incluir versión preliminar".</span><span class="sxs-lookup"><span data-stu-id="6fb58-128">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="6fb58-129">Seleccione la versión más reciente y haga clic en "Instalar" para agregar el SDK del rayo a su proyecto.</span><span class="sxs-lookup"><span data-stu-id="6fb58-129">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
<span data-ttu-id="6fb58-130">![Administrador de paquetes de NuGet](../media/LightningProviders/nuget-package-manager.png)</span><span class="sxs-lookup"><span data-stu-id="6fb58-130">![NuGet Package Manager](../media/LightningProviders/nuget-package-manager.png)</span></span>

4. <span data-ttu-id="6fb58-131">Siga cualquiera en pantalla instrucciones si es necesario.</span><span class="sxs-lookup"><span data-stu-id="6fb58-131">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="6fb58-132">Cuando se complete la instalación, se agregará una referencia al SDK del rayo a su proyecto.</span><span class="sxs-lookup"><span data-stu-id="6fb58-132">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![Referencia del SDK de rayo](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="6fb58-134">Agregue el código siguiente al archivo de manifiesto, Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="6fb58-134">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="6fb58-135">La primera es una funcionalidad que permita que la aplicación tener acceso a dispositivos personalizados.</span><span class="sxs-lookup"><span data-stu-id="6fb58-135">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="6fb58-136">El segundo es el identificador guid del dispositivo para la interfaz de rayo</span><span class="sxs-lookup"><span data-stu-id="6fb58-136">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="6fb58-137">Ambas capacidades deben agregarse a la AppX manifiesto del proyecto en el `<Capabilities>` nodo.</span><span class="sxs-lookup"><span data-stu-id="6fb58-137">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="6fb58-138">Además, asegúrese de agregar los espacios de nombres necesarios al manifiesto si es necesario.</span><span class="sxs-lookup"><span data-stu-id="6fb58-138">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![Manifiesto AppX Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="6fb58-140">Actualizar el código para usar los proveedores de rayo</span><span class="sxs-lookup"><span data-stu-id="6fb58-140">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="6fb58-141">Buscando el controlador de rayo (DMAP)</span><span class="sxs-lookup"><span data-stu-id="6fb58-141">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="6fb58-142">Para comprobar si está habilitada la luz, la `LightningProvider.IsLightningEnabled` propiedad debe utilizarse.</span><span class="sxs-lookup"><span data-stu-id="6fb58-142">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="6fb58-143">En general, siempre es una buena práctica para comprobar si está habilitado el controlador relámpago antes de usar las API del proveedor de rayo.</span><span class="sxs-lookup"><span data-stu-id="6fb58-143">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="6fb58-144">Patrón de uso general</span><span class="sxs-lookup"><span data-stu-id="6fb58-144">General usage pattern</span></span>

<span data-ttu-id="6fb58-145">Es la manera más sencilla de usar los proveedores establecer el proveedor de rayo como el valor predeterminado dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6fb58-145">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="6fb58-146">El código siguiente obtendrá, si está disponible, el proveedor de rayo establece `Microsoft.IoT.Lightning.Providers.LightningProvider` como el proveedor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6fb58-146">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="6fb58-147">En caso contrario, cuando no hay ningún proveedor predeterminado se establece explícitamente, lo buses distintos recurrirá a la predeterminada.</span><span class="sxs-lookup"><span data-stu-id="6fb58-147">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
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

<span data-ttu-id="6fb58-148">Una vez que un controlador para el bus deseado, puede usar como lo haría normalmente.</span><span class="sxs-lookup"><span data-stu-id="6fb58-148">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="6fb58-149">Uso de rayo para buses individuales</span><span class="sxs-lookup"><span data-stu-id="6fb58-149">Using Lightning for individual buses</span></span>

<span data-ttu-id="6fb58-150">Si desea usar un proveedor predeterminado distinto, en las secciones siguientes muestran cómo puede utilizar los proveedores de luz para los buses individuales.</span><span class="sxs-lookup"><span data-stu-id="6fb58-150">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="6fb58-151">Para el controlador de bus GPIO:</span><span class="sxs-lookup"><span data-stu-id="6fb58-151">For GPIO bus controller:</span></span>

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

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="6fb58-152">Para el controlador de bus I2C:</span><span class="sxs-lookup"><span data-stu-id="6fb58-152">For I2C bus controller:</span></span>

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

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="6fb58-153">Para el controlador de bus SPI:</span><span class="sxs-lookup"><span data-stu-id="6fb58-153">For SPI bus controller:</span></span>
<span data-ttu-id="6fb58-154">uso de Microsoft.IoT.Lightning.Providers; uso de Windows.Devices; uso de Windows.Devices.Spi;</span><span class="sxs-lookup"><span data-stu-id="6fb58-154">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="6fb58-155">Muestras de proveedor de rayo</span><span class="sxs-lookup"><span data-stu-id="6fb58-155">Lightning Provider Samples</span></span>

<span data-ttu-id="6fb58-156">Los ejemplos siguientes muestran cómo utilizar los proveedores de rayo con tipos de bus admitidas:</span><span class="sxs-lookup"><span data-stu-id="6fb58-156">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="6fb58-157">[Llamativa (UI) con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) muestra GPIO con el proveedor de luz en una aplicación de primer plano</span><span class="sxs-lookup"><span data-stu-id="6fb58-157">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="6fb58-158">[BlinkyHeadless con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) muestra GPIO con el proveedor de luz en una aplicación sin periféricos</span><span class="sxs-lookup"><span data-stu-id="6fb58-158">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="6fb58-159">[SPIDisplay con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) muestra el uso de la API para controlar un dispositivo con SPI relámpago proveedor</span><span class="sxs-lookup"><span data-stu-id="6fb58-159">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="6fb58-160">[WeatherStation con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) muestra la interacción con un dispositivo con I2C relámpago proveedor</span><span class="sxs-lookup"><span data-stu-id="6fb58-160">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="6fb58-161">Requisitos de compilación</span><span class="sxs-lookup"><span data-stu-id="6fb58-161">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="6fb58-162">Actualización del SDK de Windows</span><span class="sxs-lookup"><span data-stu-id="6fb58-162">Windows SDK Update</span></span>

<span data-ttu-id="6fb58-163">SDK de Windows necesarios para compilar y usar la biblioteca es 10.0.10586.0 o superior que puede descargarse desde [aquí](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="6fb58-163">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="6fb58-164">Para obtener más información sobre la configuración de todo el contenido, consulte [nuestra guía de introducción.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span><span class="sxs-lookup"><span data-stu-id="6fb58-164">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="6fb58-165">Dependencias de paquetes de NuGet</span><span class="sxs-lookup"><span data-stu-id="6fb58-165">Nuget Package Dependencies</span></span>

<span data-ttu-id="6fb58-166">Depende de la biblioteca del proveedor de rayo el [paquete Microsoft.IoT.Lightning Nuget](https://www.nuget.org/packages/Microsoft.IoT.Lightning), que a su vez depende del [paquete Nuget del SDK de Arduino](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span><span class="sxs-lookup"><span data-stu-id="6fb58-166">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="6fb58-167">Ambos paquetes de Nuget se hace referencia en los proyectos de biblioteca y están disponibles en Nuget.org.</span><span class="sxs-lookup"><span data-stu-id="6fb58-167">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="6fb58-168">Si es necesario, el código fuente para cada también está disponible en GitHub en el [relámpago](https://github.com/ms-iot/lightning) y [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositorios.</span><span class="sxs-lookup"><span data-stu-id="6fb58-168">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="6fb58-169">Actualmente, Microsoft.IoT.Lightning Nuget es aún una versión preliminar, por lo que debe actualizarse desde Nuget.org, cuando hay disponibles versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="6fb58-169">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="6fb58-170">Para instalar la versión preliminar de (actual) del paquete Microsoft.IoT.Lightning Nuget, así como recibir actualizaciones preliminares del paquete de rayos, asegúrese de que establecer la opción "Incluir versión preliminar" en el Administrador de paquetes de Nuget.</span><span class="sxs-lookup"><span data-stu-id="6fb58-170">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="6fb58-171">Haga clic en el proyecto de referencias</span><span class="sxs-lookup"><span data-stu-id="6fb58-171">Right click References in your project</span></span>
1. <span data-ttu-id="6fb58-172">Haga clic en "Administrar paquetes Nuget..."</span><span class="sxs-lookup"><span data-stu-id="6fb58-172">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="6fb58-173">Seleccione los orígenes de paquetes de nuget relámpago</span><span class="sxs-lookup"><span data-stu-id="6fb58-173">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="6fb58-174">Haga clic en "Incluir versión preliminar".</span><span class="sxs-lookup"><span data-stu-id="6fb58-174">Click "Include prerelease".</span></span>
1. <span data-ttu-id="6fb58-175">Haga clic en "Instalar" para instalar el paquete nuget al proyecto</span><span class="sxs-lookup"><span data-stu-id="6fb58-175">Click "Install" to install the nuget package to your project</span></span>

![Configuración del Administrador de paquetes](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="6fb58-177">Requisitos de tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="6fb58-177">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="6fb58-178">Requiere la actualización de otoño Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="6fb58-178">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="6fb58-179">Los proveedores de rayo soporte técnico se incluye actualmente en la actualización Fall compila para Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6fb58-179">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="6fb58-180">Puede descargar una imagen de Windows 10 IoT Core desde nuestro [página de descargas](https://developer.microsoft.com/windows/iot/Downloads).</span><span class="sxs-lookup"><span data-stu-id="6fb58-180">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="6fb58-181">Haga clic en "Descargar Insider Preview" el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6fb58-181">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="6fb58-182">Debe estar habilitado el controlador asignado en memoria directa</span><span class="sxs-lookup"><span data-stu-id="6fb58-182">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="6fb58-183">Las API en la biblioteca del proveedor de rayo requieren el controlador asignado en memoria directa relámpago esté habilitado en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="6fb58-183">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="6fb58-184">Raspberry Pi 2/3 y MinnowBoard Max tienen el controlador disponible, pero no están habilitadas de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="6fb58-184">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="6fb58-185">El controlador puede habilitarse mediante el Portal Web de los dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="6fb58-185">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="6fb58-186">Hacer referencia a la [Guía de instalación de rayo](LightningSetup.md) para obtener información detallada sobre cómo habilitar el controlador de rayo.</span><span class="sxs-lookup"><span data-stu-id="6fb58-186">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![Página de dispositivos](../media/LightningProviders/dmap4.png)

<span data-ttu-id="6fb58-188">También se puede habilitar el controlador con el comando DmapUtil:</span><span class="sxs-lookup"><span data-stu-id="6fb58-188">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="6fb58-189">DmapUtil: Utilidad para activar el controlador del asignador de memoria directa DMAP o desactivar el uso: estado dmaputil.exe | habilitar | deshabilitar estado [-v] si está habilitado actualmente dmap imprimir.</span><span class="sxs-lookup"><span data-stu-id="6fb58-189">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="6fb58-190">Pase la marca - v para obtener información detallada de configuración.</span><span class="sxs-lookup"><span data-stu-id="6fb58-190">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="6fb58-191">Habilitar dmap habilitar en el siguiente arranque.</span><span class="sxs-lookup"><span data-stu-id="6fb58-191">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="6fb58-192">deshabilitar dmap deshabilitar en el siguiente arranque.</span><span class="sxs-lookup"><span data-stu-id="6fb58-192">disable       Disable dmap on next boot.</span></span>
