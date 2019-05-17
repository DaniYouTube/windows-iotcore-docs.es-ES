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
# <a name="working-with-lightning-providers"></a>Trabajar con proveedores de rayo
La biblioteca Microsoft.IoT.Lightning.Providers contiene un conjunto de proveedores para interactuar con el panel de buses de controlador a través de la luz controlador directo a memoria asignada (DMAP).


## <a name="about-the-direct-memory-mapped-driver-dmap"></a>Acerca de la memoria directa asignado el controlador (DMAP)

El controlador DMAP es un controlador de desarrollo que proporciona mejoras de rendimiento de GPIO por el controlador predeterminado de la Bandeja de entrada. Para obtener información sobre estas mejoras de rendimiento, visite la [las pruebas de rendimiento increíblemente](../develop-your-app/LightningPerformance.md) página.

Mientras DMAP controlador oferta GPIO mejoras de rendimiento sobre el controlador de bandeja de entrada, los comandos del controlador se envían al controlador DMAP a través de direcciones de memoria asignada de modo de usuario para cada uno de los controladores. Una aplicación que solo se usa la API del proveedor de rayo o Microsoft.IoT.Lightning.Providers. Sin embargo, una aplicación malintencionada sería capaz de escribir directamente en el que la memoria y provocar problemas de hardware o de seguridad. En un equipo con sólo las aplicaciones de confianza, el DMAP generalmente uso es seguro.   

## <a name="obtaining-the-library"></a>Obtención de la biblioteca

La biblioteca se proporciona como parte de la [paquete Nuget del SDK relámpago](https://www.nuget.org/packages/Microsoft.IoT.Lightning) con código fuente disponible en [repositorio de GitHub de ms-iot/relámpago](https://github.com/ms-iot/lightning/).

Además, los ejemplos que muestran cómo usar los diferentes proveedores están disponibles en [repositorio de GitHub de ms-iot/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).

## <a name="adding-the-library-to-your-application"></a>Agregar la biblioteca de la aplicación

### <a name="option-1-starting-from-an-existing-sample"></a>Opción 1: A partir de un ejemplo existente
Una forma rápida para comenzar a codificar con los proveedores de rayos es comenzar con uno de los ejemplos en los [repositorio de GitHub de ms-iot/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).

Cada uno de los ejemplos hace referencia al SDK de rayo y está configurado correctamente para usar la biblioteca de proveedores de rayo.

**Tenga en cuenta**, para ejecutar los ejemplos, la necesidad de controlador DMAP habilitarse mediante el Portal Web de los dispositivos de Windows. Hacer referencia a la [Guía de instalación de rayo](LightningSetup.md) para obtener información detallada sobre cómo habilitarlo.

### <a name="option-2-referencing-the-library"></a>Opción 2: Hacer referencia a la biblioteca

Además, es fácil de agregar la referencia de Nuget de proveedores de rayo requerida y soporte técnico a una aplicación nueva o existente. Sigue los pasos siguientes:

1. En su aplicación, a la derecha, haga clic en el proyecto y haga clic en el "Administrar paquetes NuGet" elemento de menú  
![Proyecto para UWP](../media/LightningProviders/manage-nuget-project.png)

2. Se abrirá el Administrador de paquetes de NuGet. En la pestaña Examinar, busque el "relámpago SDK", y asegúrese de activar la casilla "Incluir versión preliminar".

3. Seleccione la versión más reciente y haga clic en "Instalar" para agregar el SDK del rayo a su proyecto. 
![Administrador de paquetes de NuGet](../media/LightningProviders/nuget-package-manager.png)

4. Siga cualquiera en pantalla instrucciones si es necesario. Cuando se complete la instalación, se agregará una referencia al SDK del rayo a su proyecto.

![Referencia del SDK de rayo](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. Agregue el código siguiente al archivo de manifiesto, Package.appxmanifest.

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* La primera es una funcionalidad que permita que la aplicación tener acceso a dispositivos personalizados.
* El segundo es el identificador guid del dispositivo para la interfaz de rayo

Ambas capacidades deben agregarse a la AppX manifiesto del proyecto en el `<Capabilities>` nodo. Además, asegúrese de agregar los espacios de nombres necesarios al manifiesto si es necesario.

![Manifiesto AppX Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a>Actualizar el código para usar los proveedores de rayo

### <a name="checking-for-the-lightning-dmap-driver"></a>Buscando el controlador de rayo (DMAP)

Para comprobar si está habilitada la luz, la `LightningProvider.IsLightningEnabled` propiedad debe utilizarse. En general, siempre es una buena práctica para comprobar si está habilitado el controlador relámpago antes de usar las API del proveedor de rayo. 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a>Patrón de uso general

Es la manera más sencilla de usar los proveedores establecer el proveedor de rayo como el valor predeterminado dentro de la aplicación. 

El código siguiente obtendrá, si está disponible, el proveedor de rayo establece `Microsoft.IoT.Lightning.Providers.LightningProvider` como el proveedor predeterminado. En caso contrario, cuando no hay ningún proveedor predeterminado se establece explícitamente, lo buses distintos recurrirá a la predeterminada.
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

Una vez que un controlador para el bus deseado, puede usar como lo haría normalmente. 

### <a name="using-lightning-for-individual-buses"></a>Uso de rayo para buses individuales

Si desea usar un proveedor predeterminado distinto, en las secciones siguientes muestran cómo puede utilizar los proveedores de luz para los buses individuales. 

#### <a name="for-gpio-bus-controller"></a>Para el controlador de bus GPIO:

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

#### <a name="for-i2c-bus-controller"></a>Para el controlador de bus I2C:

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

#### <a name="for-spi-bus-controller"></a>Para el controlador de bus SPI:
uso de Microsoft.IoT.Lightning.Providers; uso de Windows.Devices; uso de Windows.Devices.Spi;

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a>Muestras de proveedor de rayo

Los ejemplos siguientes muestran cómo utilizar los proveedores de rayo con tipos de bus admitidas:

* [Llamativa (UI) con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) muestra GPIO con el proveedor de luz en una aplicación de primer plano

* [BlinkyHeadless con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) muestra GPIO con el proveedor de luz en una aplicación sin periféricos

* [SPIDisplay con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) muestra el uso de la API para controlar un dispositivo con SPI relámpago proveedor
 
* [WeatherStation con el proveedor de rayo](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) muestra la interacción con un dispositivo con I2C relámpago proveedor

## <a name="build-requirements"></a>Requisitos de compilación



### <a name="windows-sdk-update"></a>Actualización del SDK de Windows

SDK de Windows necesarios para compilar y usar la biblioteca es 10.0.10586.0 o superior que puede descargarse desde [aquí](https://dev.windows.com/en-US/downloads/windows-10-sdk).

Para obtener más información sobre la configuración de todo el contenido, consulte [nuestra guía de introducción.](https://developer.microsoft.com/en-us/windows/iot/getstarted).

### <a name="nuget-package-dependencies"></a>Dependencias de paquetes de NuGet

Depende de la biblioteca del proveedor de rayo el [paquete Microsoft.IoT.Lightning Nuget](https://www.nuget.org/packages/Microsoft.IoT.Lightning), que a su vez depende del [paquete Nuget del SDK de Arduino](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino). Ambos paquetes de Nuget se hace referencia en los proyectos de biblioteca y están disponibles en Nuget.org.

Si es necesario, el código fuente para cada también está disponible en GitHub en el [relámpago](https://github.com/ms-iot/lightning) y [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositorios.

Actualmente, Microsoft.IoT.Lightning Nuget es aún una versión preliminar, por lo que debe actualizarse desde Nuget.org, cuando hay disponibles versiones más recientes.

Para instalar la versión preliminar de (actual) del paquete Microsoft.IoT.Lightning Nuget, así como recibir actualizaciones preliminares del paquete de rayos, asegúrese de que establecer la opción "Incluir versión preliminar" en el Administrador de paquetes de Nuget.

1. Haga clic en el proyecto de referencias
1. Haga clic en "Administrar paquetes Nuget..."
1. Seleccione los orígenes de paquetes de nuget relámpago
1. Haga clic en "Incluir versión preliminar".
1. Haga clic en "Instalar" para instalar el paquete nuget al proyecto

![Configuración del Administrador de paquetes](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a>Requisitos de tiempo de ejecución

### <a name="windows-iot-core-fall-update-required"></a>Requiere la actualización de otoño Windows IoT Core
Los proveedores de rayo soporte técnico se incluye actualmente en la actualización Fall compila para Windows IoT Core.
Puede descargar una imagen de Windows 10 IoT Core desde nuestro [página de descargas](https://developer.microsoft.com/windows/iot/Downloads). Haga clic en "Descargar Insider Preview" el tipo de dispositivo.

### <a name="direct-memory-mapped-driver-must-be-enabled"></a>Debe estar habilitado el controlador asignado en memoria directa
 
Las API en la biblioteca del proveedor de rayo requieren el controlador asignado en memoria directa relámpago esté habilitado en el dispositivo de destino. Raspberry Pi 2/3 y MinnowBoard Max tienen el controlador disponible, pero no están habilitadas de forma predeterminada.

El controlador puede habilitarse mediante el Portal Web de los dispositivos de Windows. Hacer referencia a la [Guía de instalación de rayo](LightningSetup.md) para obtener información detallada sobre cómo habilitar el controlador de rayo.

![Página de dispositivos](../media/LightningProviders/dmap4.png)

También se puede habilitar el controlador con el comando DmapUtil:

DmapUtil: Utilidad para activar el controlador del asignador de memoria directa DMAP o desactivar el uso: estado dmaputil.exe | habilitar | deshabilitar estado [-v] si está habilitado actualmente dmap imprimir. Pase la marca - v para obtener información detallada de configuración.
Habilitar dmap habilitar en el siguiente arranque.
deshabilitar dmap deshabilitar en el siguiente arranque.
