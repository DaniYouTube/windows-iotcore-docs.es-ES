---
title: Proveedores de bus
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los diferentes proveedores disponibles a través de Windows 10 IoT Core.
keywords: Windows IOT, proveedores, proveedores de bus, UWP, GPIO, SPI
ms.openlocfilehash: 9f9b13834565fd896fd63e6d09ce113ef5035202
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721430"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a><span data-ttu-id="127c7-104">Acceso de modo de solo acceso a GPIO, I2C y SPI</span><span class="sxs-lookup"><span data-stu-id="127c7-104">Usermode access to GPIO, I2C and SPI</span></span>

<span data-ttu-id="127c7-105">Windows 10 contiene nuevas API para acceder a GPIO, I2C, SPI y UART directamente desde el modo usuario.</span><span class="sxs-lookup"><span data-stu-id="127c7-105">Windows 10 contains new APIs for accessing GPIO, I2C, SPI, and UART directly from usermode.</span></span> <span data-ttu-id="127c7-106">Los paneles de desarrollo como Raspberry Pi 2 exponen un subconjunto de estas conexiones que permiten a los usuarios ampliar un módulo de cálculo base con circuitos personalizados para dirigirte a una aplicación particular.</span><span class="sxs-lookup"><span data-stu-id="127c7-106">Development boards like Raspberry Pi 2 expose a subset of these connections which enable users to extend a base compute module with custom circuitry to address a particular application.</span></span> <span data-ttu-id="127c7-107">Normalmente, estos buses de bajo nivel se comparten con otras funciones incorporadas críticas, con solo un subconjunto de las patillas y buses de GPIO expuestos en los encabezados.</span><span class="sxs-lookup"><span data-stu-id="127c7-107">These low level buses are usually shared with other critical onboard functions, with only a subset of GPIO pins and buses exposed on headers.</span></span> <span data-ttu-id="127c7-108">Para preservar la estabilidad del sistema, es necesario especificar qué patillas y buses son seguros para modificar las aplicaciones de modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="127c7-108">To preserve system stability, it is necessary to specify which pins and buses are safe for modification by usermode applications.</span></span>

<span data-ttu-id="127c7-109">El acceso de modo usuario a buses de nivel bajo en Windows se asocia a través de los marcos`GpioClx``SpbCx`existentes.</span><span class="sxs-lookup"><span data-stu-id="127c7-109">Usermode access to low level buses on Windows is plumbed through the existing `GpioClx` and `SpbCx` frameworks.</span></span> <span data-ttu-id="127c7-110">Un nuevo controlador denominado RhProxy, disponible en Windows IoT Core y Windows Enterprise, expone los recursos de `GpioClx` y `SpbCx` a un modo en modo de otro.</span><span class="sxs-lookup"><span data-stu-id="127c7-110">A new driver called RhProxy, available on Windows IoT Core and Windows Enterprise, exposes `GpioClx` and `SpbCx` resources to usermode.</span></span> <span data-ttu-id="127c7-111">Para habilitar las API, se debe declarar un nodo de dispositivo para rhproxy en las tablas ACPI con cada uno de los recursos GPIO y SPB que se deben exponer en modo de usuario.</span><span class="sxs-lookup"><span data-stu-id="127c7-111">To enable the APIs, a device node for rhproxy must be declared in your ACPI tables with each of the GPIO and SPB resources that should be exposed to usermode.</span></span>

<span data-ttu-id="127c7-112">Puede encontrar documentación más detallada sobre el acceso de modo de RhProxy [aquí](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).</span><span class="sxs-lookup"><span data-stu-id="127c7-112">Additional in-depth documentation on UserMode access via RhProxy can be found [here](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).</span></span>

## <a name="bus-providers"></a><span data-ttu-id="127c7-113">Proveedores de bus</span><span class="sxs-lookup"><span data-stu-id="127c7-113">Bus Providers</span></span>

<span data-ttu-id="127c7-114">A partir de Windows 10, Windows ha tenido API de UWP integradas que proporcionan acceso directo a los buses de GPIO, SPI o I2C ubicados en el SOC. Esto proporciona un acceso muy sencillo a este hardware desde una API de alto nivel.</span><span class="sxs-lookup"><span data-stu-id="127c7-114">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="127c7-115">Sin embargo, hay muchas ocasiones en las que un creador de dispositivos quiere usar un controlador fuera de la SOC para tener acceso a un bus.</span><span class="sxs-lookup"><span data-stu-id="127c7-115">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="127c7-116">Puede ser tan simple como un chip barato que agregue 16 clavijas de GPIO, o tan rico como una MCU completa (por ejemplo, un Arduino) que no solo agregue los pin GPIO, SPI y I2C, sino que también admita PWM y ADC.</span><span class="sxs-lookup"><span data-stu-id="127c7-116">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="127c7-117">Con el modelo de "proveedor de bus", ofrecemos a los desarrolladores la capacidad de acceder a estos buses fuera de la SOC mediante las API integradas, mediante un proveedor de modo de usuario que se asocia a la brecha.</span><span class="sxs-lookup"><span data-stu-id="127c7-117">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span>

<span data-ttu-id="127c7-118">Alguien que crea un proveedor implementa un conjunto de interfaces en una biblioteca de clases de UWP y, a continuación, cualquier desarrollador que quiera comunicarse con ese hardware simplemente incluye el componente e indica a las API integradas sobre él.</span><span class="sxs-lookup"><span data-stu-id="127c7-118">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="127c7-119">Si observa el código de ejemplo del proveedor de [Arduino remoto](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) , puede ver lo fácil que es configurar el proveedor y, una vez establecido como el proveedor predeterminado para esa aplicación, el resto del código de la aplicación cliente es idéntico al código necesario para acceder a un bus en SOC.</span><span class="sxs-lookup"><span data-stu-id="127c7-119">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>


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

## <a name="available-providers"></a><span data-ttu-id="127c7-120">Proveedores disponibles</span><span class="sxs-lookup"><span data-stu-id="127c7-120">Available Providers</span></span>

<span data-ttu-id="127c7-121">Actualmente tenemos varios proveedores disponibles en el repositorio de github de [proveedores de bus](https://github.com/ms-iot/BusProviders) .</span><span class="sxs-lookup"><span data-stu-id="127c7-121">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="127c7-122">Además del código del proveedor, cada proveedor tiene una solución de VS de ejemplo que muestra cómo un cliente usaría ese proveedor.</span><span class="sxs-lookup"><span data-stu-id="127c7-122">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

- <span data-ttu-id="127c7-123">**ADC**</span><span class="sxs-lookup"><span data-stu-id="127c7-123">**ADC**</span></span>
  - <span data-ttu-id="127c7-124">Ads1x15</span><span class="sxs-lookup"><span data-stu-id="127c7-124">Ads1x15</span></span>
  - <span data-ttu-id="127c7-125">Mcp3008</span><span class="sxs-lookup"><span data-stu-id="127c7-125">Mcp3008</span></span>
  - <span data-ttu-id="127c7-126">Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="127c7-126">Remote Arduino</span></span>

- <span data-ttu-id="127c7-127">**PWM**</span><span class="sxs-lookup"><span data-stu-id="127c7-127">**PWM**</span></span>
  - <span data-ttu-id="127c7-128">PCA9685</span><span class="sxs-lookup"><span data-stu-id="127c7-128">PCA9685</span></span>
  - <span data-ttu-id="127c7-129">Simulado con GPIO</span><span class="sxs-lookup"><span data-stu-id="127c7-129">Simulated with Gpio</span></span>
  - <span data-ttu-id="127c7-130">Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="127c7-130">Remote Arduino</span></span>
  
- <span data-ttu-id="127c7-131">**GPIO, SPI, I2C**</span><span class="sxs-lookup"><span data-stu-id="127c7-131">**Gpio, SPI, I2C**</span></span>
  - <span data-ttu-id="127c7-132">Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="127c7-132">Remote Arduino</span></span>

<span data-ttu-id="127c7-133">Además de los proveedores que proporcionan acceso al hardware real, hemos creado un [proveedor simulado](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) que actuará como si fuera un proveedor compatible con inifitely y está diseñado para permitirle escribir y depurar las aplicaciones sin tener que implementarlas primero en un dispositivo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="127c7-133">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="127c7-134">Para obtener una experiencia más completa, puede personalizarla para simular el hardware real.</span><span class="sxs-lookup"><span data-stu-id="127c7-134">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="127c7-135">Por ejemplo: actualizar el proveedor I2C para devolver el resultado "75" cuando lo envíe al comando para una lectura de temperatura en un dispositivo con la dirección subordinada designada.</span><span class="sxs-lookup"><span data-stu-id="127c7-135">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="127c7-136">Recursos adicionales</span><span class="sxs-lookup"><span data-stu-id="127c7-136">Additional Resources</span></span>

<span data-ttu-id="127c7-137">[Aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)encontrará herramientas adicionales de bus, códigos de ejemplo y compilaciones y pruebas en I2C, SPI, GPIO, MINCOMM/UART.</span><span class="sxs-lookup"><span data-stu-id="127c7-137">Additional bus tools, sample codes, and building and testing on I2C, SPI, GPIO, MinComm/UART can be found [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).</span></span>

