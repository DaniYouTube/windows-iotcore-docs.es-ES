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
# <a name="working-with-lightning-providers"></a>Trabajar con los proveedores de Lightning
La biblioteca Microsoft. IoT. Lightning. Providers contiene un conjunto de proveedores para interactuar con los buses del controlador del panel a través del controlador asignado de memoria de Lightning Direct (DMAP).


## <a name="about-the-direct-memory-mapped-driver-dmap"></a>Acerca del controlador asignado a memoria directa (DMAP)

El controlador DMAP es un controlador en desarrollo que proporciona mejoras de rendimiento de GPIO sobre el controlador de bandeja de entrada predeterminado. Para obtener más información sobre estas mejoras de rendimiento, visite la página de [pruebas de rendimiento](../develop-your-app/LightningPerformance.md) .

Mientras que el controlador DMAP ofrece mejoras de rendimiento de GPIO sobre el controlador de bandeja de entrada, los comandos del controlador se envían al controlador DMAP a través de direcciones asignadas a memoria de modo de usuario para cada uno de los controladores. Una aplicación que solo usa las API del proveedor de Lightning o Microsoft. IoT. Lightning. Providers. Sin embargo, una aplicación malintencionada podría escribir directamente en esa memoria y causar problemas de hardware o seguridad. En un equipo que solo tiene aplicaciones de confianza, DMAP suele ser seguro para su uso.   

## <a name="obtaining-the-library"></a>Obtención de la biblioteca

La biblioteca se proporciona como parte del [paquete Nuget del SDK de Lightning](https://www.nuget.org/packages/Microsoft.IoT.Lightning) con el código fuente disponible en el repositorio de [GitHub MS-IOT/Lightning](https://github.com/ms-iot/lightning/).

Adicionalmente, ejemplos que muestran cómo usar los diferentes proveedores están disponibles en el [repositorio de github MS-IOT/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).

## <a name="adding-the-library-to-your-application"></a>Adición de la biblioteca a la aplicación

### <a name="option-1-starting-from-an-existing-sample"></a>Opción 1: A partir de un ejemplo existente
Una forma rápida de empezar a codificar con los proveedores de relámpago es empezar con uno de los ejemplos del [repositorio de github MS-IOT/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).

Cada uno de los ejemplos hace referencia al relámpago y está configurado correctamente para usar la biblioteca de los proveedores de Lightning.

**Tenga en cuenta**que, para ejecutar los ejemplos, el controlador DMAP debe estar habilitado mediante el portal web de dispositivos Windows. Consulte la [Guía de configuración de Lightning](LightningSetup.md) para obtener información detallada sobre cómo habilitarlo.

### <a name="option-2-referencing-the-library"></a>Opción 2: Referencia a la biblioteca

Además, es sencillo agregar la referencia de Nuget de los proveedores de relámpago necesarios y la compatibilidad con una aplicación nueva o existente. Sigue los pasos siguientes:

1. En su aplicación, haga clic con el botón derecho en el proyecto y haga clic en "administrar paquetes NuGet..." elemento de menú  
![Proyecto para UWP](../media/LightningProviders/manage-nuget-project.png)

2. Se abrirá el administrador de paquetes NuGet. En la pestaña examinar, busque el "rayo SDK" y asegúrese de activar la casilla "incluir versión preliminar".

3. Seleccione la última versión y haga clic en "instalar" para agregar el SDK de Lightning a su proyecto. 
![Administrador de paquetes NuGet](../media/LightningProviders/nuget-package-manager.png)

4. Siga las instrucciones que aparecen en pantalla, si es necesario. Una vez completada la instalación, se agregará al proyecto una referencia al SDK de Lightning.

![Referencia del SDK de Lightning](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. Agregue el código siguiente al archivo de manifiesto, package. appxmanifest.

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* La primera es una funcionalidad que permitirá a la aplicación tener acceso a los dispositivos personalizados.
* El segundo es el identificador del GUID del dispositivo de la interfaz de relámpago

Ambas capacidades deben agregarse al manifiesto appx del proyecto en el `<Capabilities>` nodo. Además, asegúrese de agregar los espacios de nombres necesarios al manifiesto, si es necesario.

![Manifiesto AppX Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a>Actualización del código para usar los proveedores de Lightning

### <a name="checking-for-the-lightning-dmap-driver"></a>Comprobando el controlador Lightning (DMAP)

Para comprobar si el relámpago está habilitado `LightningProvider.IsLightningEnabled` , se debe usar la propiedad. En general, siempre es recomendable comprobar si el controlador de Lightning está habilitado antes de usar las API del proveedor de Lightning. 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a>Patrón de uso general

La manera más sencilla de usar los proveedores es establecer el proveedor de relámpago como el valor predeterminado dentro de la aplicación. 

El código siguiente mostrará, si el proveedor de relámpago está disponible, `Microsoft.IoT.Lightning.Providers.LightningProvider` establecido como el proveedor predeterminado. De lo contrario, si no se establece explícitamente ningún proveedor predeterminado, los distintos buses revertirán al valor predeterminado.
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

Una vez que tenga un controlador para el bus deseado, puede usarlo como lo haría normalmente. 

### <a name="using-lightning-for-individual-buses"></a>Uso de Lightning para buses individuales

Si desea usar un proveedor predeterminado diferente, en las secciones siguientes se muestra cómo puede usar los proveedores de relámpagos para buses individuales. 

#### <a name="for-gpio-bus-controller"></a>Para controlador de bus GPIO:

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

#### <a name="for-i2c-bus-controller"></a>Para controlador de bus I2C:

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

#### <a name="for-spi-bus-controller"></a>Para controlador de bus SPI:
usar Microsoft. IoT. Lightning. Providers; usar Windows. Devices; uso de Windows. Devices. SPI;

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a>Ejemplos del proveedor de Lightning

Los ejemplos siguientes muestran cómo usar los proveedores de Lightning con tipos de bus compatibles:

* [Parpadeo (UI) con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) muestra el GPIO con el proveedor de Lightning en una aplicación en primer plano

* [BlinkyHeadless con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) muestra GPIO con el proveedor de Lightning en una aplicación sin periféricos

* [SPIDisplay con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) muestra el uso de la API para controlar un dispositivo con SPI con el proveedor de Lightning
 
* [WeatherStation con el proveedor de Lightning](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) muestra la interacción con un dispositivo mediante I2C con el proveedor de Lightning

## <a name="build-requirements"></a>Requisitos de compilación



### <a name="windows-sdk-update"></a>Windows SDK Update

Windows SDK necesario para compilar y usar la biblioteca es 10.0.10586.0 o posterior que se puede descargar desde [aquí](https://dev.windows.com/en-US/downloads/windows-10-sdk).

Para obtener más información sobre cómo configurar todo, consulte [nuestra guía](https://developer.microsoft.com/en-us/windows/iot/getstarted)de introducción.

### <a name="nuget-package-dependencies"></a>Dependencias de paquetes Nuget

La biblioteca del proveedor de Lightning depende del [paquete Nuget Microsoft. iot. Lightning](https://www.nuget.org/packages/Microsoft.IoT.Lightning)que, a su vez, depende del [paquete Nuget del SDK de Arduino](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino). En los proyectos de biblioteca se hace referencia a ambos paquetes Nuget y están disponibles en Nuget.org.

Si es necesario, el código fuente de cada uno de ellos también está disponible en GitHub en los repositorios del SDK de [Lightning](https://github.com/ms-iot/lightning) y [Arduino](https://github.com/ms-iot/arduino-sdk) .

Actualmente, Microsoft. IoT. Lightning Nuget todavía está en versión preliminar, por lo que debe actualizarse desde Nuget.org, cuando haya versiones más recientes disponibles.

Para instalar la versión preliminar (actual) del paquete de Nuget Microsoft. IoT. Lightning y recibir actualizaciones de la versión preliminar del paquete de relámpago, asegúrese de establecer la opción "incluir versión preliminar" en el administrador de paquetes Nuget.

1. Haga clic con el botón derecho en referencias en el proyecto
1. Haga clic en "administrar paquetes Nuget..."
1. Selección de orígenes de paquetes para Lightning Nuget
1. Haga clic en "incluir versión preliminar".
1. Haga clic en "instalar" para instalar el paquete Nuget en el proyecto.

![Configuración del administrador de paquetes](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a>Requisitos de tiempo de ejecución

### <a name="windows-iot-core-fall-update-required"></a>Se requiere la actualización de Windows IoT Core
La compatibilidad con los proveedores de Lightning está incluida actualmente en las compilaciones de actualización para Windows IoT Core.
Puede descargar una imagen de Windows 10 IoT Core desde nuestra [Página de descargas](https://developer.microsoft.com/windows/iot/Downloads). Haga clic en "descargar Insider Preview" para el tipo de dispositivo.

### <a name="direct-memory-mapped-driver-must-be-enabled"></a>El controlador asignado a memoria directa debe estar habilitado
 
Las API de la biblioteca del proveedor de Lightning requieren que el controlador asignado de la memoria de Lightning Direct esté habilitado en el dispositivo de destino. Tanto Raspberry pi 2/3 como MinnowBoard Max tienen el controlador disponible, pero no está habilitado de forma predeterminada.

El controlador se puede habilitar mediante el portal web de dispositivos Windows. Consulte la [Guía de configuración de Lightning](LightningSetup.md) para obtener información detallada acerca de cómo habilitar el controlador de Lightning.

![Página dispositivos](../media/LightningProviders/dmap4.png)

El controlador también se puede habilitar con el comando DmapUtil:

DmapUtil: Para activar o desactivar el uso del controlador del asignador de memoria directo de DMAP: estado de dmaputil. exe | Enable | Disable status [-v] imprime si DMAP está habilitado actualmente. Pase la marca-v para obtener información de configuración detallada.
Habilite habilitar DMAP en el siguiente arranque.
deshabilitar deshabilitar DMAP en el siguiente arranque.
