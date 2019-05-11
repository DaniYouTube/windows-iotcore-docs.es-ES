---
title: Proveedores de bus
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los diferentes proveedores disponibles a través de Windows 10 IoT Core.
keywords: Windows iot, proveedores, los proveedores de bus, UWP, Gpio, Spi
ms.openlocfilehash: 7e2a3bf45317cd11ca558db6f1b6845e0e0f7a67
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533280"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a><span data-ttu-id="6f4d2-104">Acceso UserMode GPIO, I2C y SPI</span><span class="sxs-lookup"><span data-stu-id="6f4d2-104">Usermode access to GPIO, I2C and SPI</span></span>

<span data-ttu-id="6f4d2-105">Windows 10 contiene nuevas API para acceder a GPIO, I2C, SPI y UART directamente desde el modo usuario.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-105">Windows 10 contains new APIs for accessing GPIO, I2C, SPI, and UART directly from usermode.</span></span> <span data-ttu-id="6f4d2-106">Los paneles de desarrollo como Raspberry Pi 2 exponen un subconjunto de estas conexiones que permiten a los usuarios ampliar un módulo de cálculo base con circuitos personalizados para dirigirte a una aplicación particular.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-106">Development boards like Raspberry Pi 2 expose a subset of these connections which enable users to extend a base compute module with custom circuitry to address a particular application.</span></span> <span data-ttu-id="6f4d2-107">Normalmente, estos buses de bajo nivel se comparten con otras funciones incorporadas críticas, con solo un subconjunto de las patillas y buses de GPIO expuestos en los encabezados.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-107">These low level buses are usually shared with other critical onboard functions, with only a subset of GPIO pins and buses exposed on headers.</span></span> <span data-ttu-id="6f4d2-108">Para preservar la estabilidad del sistema, es necesario especificar qué patillas y buses son seguros para modificar las aplicaciones de modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-108">To preserve system stability, it is necessary to specify which pins and buses are safe for modification by usermode applications.</span></span>

<span data-ttu-id="6f4d2-109">El acceso de modo de usuario a buses de nivel bajo en Windows se asocia a través de los marcos `GpioClx` y `SpbCx` existentes.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-109">Usermode access to low level buses on Windows is plumbed through the existing `GpioClx` and `SpbCx` frameworks.</span></span> <span data-ttu-id="6f4d2-110">Expone un nuevo controlador denominado RhProxy, disponible en Windows IoT Core y Enterprise de Windows, `GpioClx` y `SpbCx` recursos a modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-110">A new driver called RhProxy, available on Windows IoT Core and Windows Enterprise, exposes `GpioClx` and `SpbCx` resources to usermode.</span></span> <span data-ttu-id="6f4d2-111">Para habilitar las API, se debe declarar un nodo de dispositivo para rhproxy en las tablas ACPI con cada uno de los recursos GPIO y SPB que se deben exponer en modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-111">To enable the APIs, a device node for rhproxy must be declared in your ACPI tables with each of the GPIO and SPB resources that should be exposed to usermode.</span></span>

<span data-ttu-id="6f4d2-112">Puede encontrar más documentación detallada en modo de usuario acceso a través de RhProxy [aquí](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access).</span><span class="sxs-lookup"><span data-stu-id="6f4d2-112">Additional in-depth documentation on UserMode access via RhProxy can be found [here](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access).</span></span>

## <a name="bus-providers"></a><span data-ttu-id="6f4d2-113">Proveedores de bus</span><span class="sxs-lookup"><span data-stu-id="6f4d2-113">Bus Providers</span></span>

<span data-ttu-id="6f4d2-114">A partir de Windows 10, Windows ha tenido incluido con las API de UWP que proporcionan acceso directo a Gpio, Spi, o buses de I2c ubicado en el Soc-. Esto proporciona muy fácil acceso a este hardware desde un API de alto nivel.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-114">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="6f4d2-115">Sin embargo, hay muchas veces que un fabricante de dispositivos que desea volver a usar un controlador de desactivar soc para tener acceso a un bus.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-115">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="6f4d2-116">Puede ser tan simple como un chip económico que agrega 16 pines GPIO, o tan enriquecido como una MCU completa (por ejemplo, Arduino) que no solo agrega anclajes I2C, SPI y Gpio, sino que también admite PWM y ADC.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-116">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="6f4d2-117">Con el modelo de "Proveedor de Bus", ofrecemos a los desarrolladores la capacidad de tener acceso a estos buses desactivar soc mediante las API de en el equipo, mediante un proveedor de modo de usuario que une la brecha.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-117">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span>

<span data-ttu-id="6f4d2-118">Alguien que está compilando un proveedor implementa un conjunto de interfaces en una biblioteca de clases UWP y, a continuación, los desarrolladores que quieran para comunicarse con que simplemente incluye el componente de hardware y le indica a las API en el cuadro acerca de él.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-118">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="6f4d2-119">Si observa el código de ejemplo desde el [Arduino remoto proveedor](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) puede ver lo fácil que es configurar el proveedor y, una vez establecido como el proveedor predeterminado para esa aplicación, el resto del código de la aplicación cliente es idéntico para el código necesario para un un bus en soc cceso.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-119">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>


```
ArduinoProviders.ArduinoProvider.Configuration = 
    new ArduinoProviders.ArduinoConnectionConfiguration("VID_2341", "PID_0043", 57600);
Windows.Devices.LowLevelDevicesController.DefaultProvider =  new ArduinoProviders.ArduinoProvider();

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
adcController = await AdcController.GetDefaultAsync();
pwmController = await PwmController.GetDefaultAsync();

GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);`
```

## <a name="available-providers"></a><span data-ttu-id="6f4d2-120">Proveedores disponibles</span><span class="sxs-lookup"><span data-stu-id="6f4d2-120">Available Providers</span></span>

<span data-ttu-id="6f4d2-121">Actualmente, tenemos un número de proveedores disponibles en el [Bus proveedores](https://github.com/ms-iot/BusProviders) repositorio de github.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-121">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="6f4d2-122">Además del código para el proveedor, cada proveedor tiene una solución de VS de ejemplo que muestra cómo un cliente podría usar ese proveedor.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-122">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

- <span data-ttu-id="6f4d2-123">**ADC**</span><span class="sxs-lookup"><span data-stu-id="6f4d2-123">**ADC**</span></span>
  - <span data-ttu-id="6f4d2-124">Ads1x15</span><span class="sxs-lookup"><span data-stu-id="6f4d2-124">Ads1x15</span></span>
  - <span data-ttu-id="6f4d2-125">Mcp3008</span><span class="sxs-lookup"><span data-stu-id="6f4d2-125">Mcp3008</span></span>
  - <span data-ttu-id="6f4d2-126">Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="6f4d2-126">Remote Arduino</span></span>

- <span data-ttu-id="6f4d2-127">**PWM**</span><span class="sxs-lookup"><span data-stu-id="6f4d2-127">**PWM**</span></span>
  - <span data-ttu-id="6f4d2-128">PCA9685</span><span class="sxs-lookup"><span data-stu-id="6f4d2-128">PCA9685</span></span>
  - <span data-ttu-id="6f4d2-129">Simular con Gpio</span><span class="sxs-lookup"><span data-stu-id="6f4d2-129">Simulated with Gpio</span></span>
  - <span data-ttu-id="6f4d2-130">Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="6f4d2-130">Remote Arduino</span></span>
  
- <span data-ttu-id="6f4d2-131">**Gpio, SPI, I2C**</span><span class="sxs-lookup"><span data-stu-id="6f4d2-131">**Gpio, SPI, I2C**</span></span>
  - <span data-ttu-id="6f4d2-132">Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="6f4d2-132">Remote Arduino</span></span>

<span data-ttu-id="6f4d2-133">Además de los proveedores que proporcionan acceso a hardware real, hemos creado un [proveedor Simulated](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) que actuará como si fue un proveedor compatible con inifitely y está diseñado para que le permiten escribir y depurar sus aplicaciones sin tener que en primer lugar implementarlos en un dispositivo que funcione.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-133">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="6f4d2-134">Para una experiencia más enriquecida, puede personalizarlo para simular el hardware real.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-134">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="6f4d2-135">Por ejemplo: actualizando el proveedor I2c devuelva hacer una copia el resultado "75" al enviar el comando para una temperatura leer en un dispositivo con la dirección de esclavo designado.</span><span class="sxs-lookup"><span data-stu-id="6f4d2-135">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6f4d2-136">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="6f4d2-136">Additional Resources</span></span>

<span data-ttu-id="6f4d2-137">Herramientas de bus adicional, los códigos de ejemplo y compilación y pruebas en I2C, SPI, GPIO, pueden encontrarse MinComm/UART [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).</span><span class="sxs-lookup"><span data-stu-id="6f4d2-137">Additional bus tools, sample codes, and building and testing on I2C, SPI, GPIO, MinComm/UART can be found [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).</span></span>

