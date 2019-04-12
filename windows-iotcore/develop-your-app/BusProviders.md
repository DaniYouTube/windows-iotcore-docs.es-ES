---
title: Proveedores de bus
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los diferentes proveedores disponibles a través de Windows 10 IoT Core.
keywords: Windows iot, proveedores, los proveedores de bus, UWP, Gpio, Spi
ms.openlocfilehash: 63e62e649aa6f54576e47419fe0be86ae5e5f096
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514680"
---
# <a name="bus-providers"></a><span data-ttu-id="69b20-104">Proveedores de bus</span><span class="sxs-lookup"><span data-stu-id="69b20-104">Bus Providers</span></span>

<span data-ttu-id="69b20-105">A partir de Windows 10, Windows ha tenido incluido con las API de UWP que proporcionan acceso directo a Gpio, Spi, o buses de I2c ubicado en el Soc-. Esto proporciona muy fácil acceso a este hardware desde un API de alto nivel.</span><span class="sxs-lookup"><span data-stu-id="69b20-105">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="69b20-106">Sin embargo, hay muchas veces que un fabricante de dispositivos que desea volver a usar un controlador de desactivar soc para tener acceso a un bus.</span><span class="sxs-lookup"><span data-stu-id="69b20-106">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="69b20-107">Puede ser tan simple como un chip económico que agrega 16 pines GPIO, o tan enriquecido como una MCU completa (por ejemplo, Arduino) que no solo agrega anclajes I2C, SPI y Gpio, sino que también admite PWM y ADC.</span><span class="sxs-lookup"><span data-stu-id="69b20-107">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="69b20-108">Con el modelo de "Proveedor de Bus", ofrecemos a los desarrolladores la capacidad de tener acceso a estos buses desactivar soc mediante las API de en el equipo, mediante un proveedor de modo de usuario que une la brecha.</span><span class="sxs-lookup"><span data-stu-id="69b20-108">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span> 

<span data-ttu-id="69b20-109">Alguien que está compilando un proveedor implementa un conjunto de interfaces en una biblioteca de clases UWP y, a continuación, los desarrolladores que quieran para comunicarse con que simplemente incluye el componente de hardware y le indica a las API en el cuadro acerca de él.</span><span class="sxs-lookup"><span data-stu-id="69b20-109">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="69b20-110">Si observa el código de ejemplo desde el [Arduino remoto proveedor](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) puede ver lo fácil que es configurar el proveedor y, una vez establecido como el proveedor predeterminado para esa aplicación, el resto del código de la aplicación cliente es idéntico para el código necesario para un un bus en soc cceso.</span><span class="sxs-lookup"><span data-stu-id="69b20-110">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>  

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

## <a name="available-providers"></a><span data-ttu-id="69b20-111">Proveedores disponibles</span><span class="sxs-lookup"><span data-stu-id="69b20-111">Available Providers</span></span>

<span data-ttu-id="69b20-112">Actualmente, tenemos un número de proveedores disponibles en el [Bus proveedores](https://github.com/ms-iot/BusProviders) repositorio de github.</span><span class="sxs-lookup"><span data-stu-id="69b20-112">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="69b20-113">Además del código para el proveedor, cada proveedor tiene una solución de VS de ejemplo que muestra cómo un cliente podría usar ese proveedor.</span><span class="sxs-lookup"><span data-stu-id="69b20-113">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

* <span data-ttu-id="69b20-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="69b20-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span></span>
* <span data-ttu-id="69b20-115">PWM \*\* PCA9685 \*\* simula con Gpio \*\* Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="69b20-115">PWM \*\* PCA9685 \*\* Simulated with Gpio \*\* Remote Arduino</span></span>
* <span data-ttu-id="69b20-116">GPIO, SPI, I2c \*\* Arduino remoto</span><span class="sxs-lookup"><span data-stu-id="69b20-116">Gpio, SPI, I2c \*\* Remote Arduino</span></span>

<span data-ttu-id="69b20-117">Además de los proveedores que proporcionan acceso a hardware real, hemos creado un [proveedor Simulated](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) que actuará como si fue un proveedor compatible con inifitely y está diseñado para que le permiten escribir y depurar sus aplicaciones sin tener que en primer lugar implementarlos en un dispositivo que funcione.</span><span class="sxs-lookup"><span data-stu-id="69b20-117">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="69b20-118">Para una experiencia más enriquecida, puede personalizarlo para simular el hardware real.</span><span class="sxs-lookup"><span data-stu-id="69b20-118">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="69b20-119">Por ejemplo: actualizando el proveedor I2c devuelva hacer una copia el resultado "75" al enviar el comando para una temperatura leer en un dispositivo con la dirección de esclavo designado.</span><span class="sxs-lookup"><span data-stu-id="69b20-119">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span> 
