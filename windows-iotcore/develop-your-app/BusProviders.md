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
# <a name="bus-providers"></a>Proveedores de bus

A partir de Windows 10, Windows ha tenido incluido con las API de UWP que proporcionan acceso directo a Gpio, Spi, o buses de I2c ubicado en el Soc-. Esto proporciona muy fácil acceso a este hardware desde un API de alto nivel. Sin embargo, hay muchas veces que un fabricante de dispositivos que desea volver a usar un controlador de desactivar soc para tener acceso a un bus. Puede ser tan simple como un chip económico que agrega 16 pines GPIO, o tan enriquecido como una MCU completa (por ejemplo, Arduino) que no solo agrega anclajes I2C, SPI y Gpio, sino que también admite PWM y ADC. Con el modelo de "Proveedor de Bus", ofrecemos a los desarrolladores la capacidad de tener acceso a estos buses desactivar soc mediante las API de en el equipo, mediante un proveedor de modo de usuario que une la brecha. 

Alguien que está compilando un proveedor implementa un conjunto de interfaces en una biblioteca de clases UWP y, a continuación, los desarrolladores que quieran para comunicarse con que simplemente incluye el componente de hardware y le indica a las API en el cuadro acerca de él. Si observa el código de ejemplo desde el [Arduino remoto proveedor](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) puede ver lo fácil que es configurar el proveedor y, una vez establecido como el proveedor predeterminado para esa aplicación, el resto del código de la aplicación cliente es idéntico para el código necesario para un un bus en soc cceso.  

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

## <a name="available-providers"></a>Proveedores disponibles

Actualmente, tenemos un número de proveedores disponibles en el [Bus proveedores](https://github.com/ms-iot/BusProviders) repositorio de github. Además del código para el proveedor, cada proveedor tiene una solución de VS de ejemplo que muestra cómo un cliente podría usar ese proveedor. 

* ADC ** Ads1x15 ** Mcp3008 ** Remote Arduino
* PWM ** PCA9685 ** simula con Gpio ** Arduino remoto
* GPIO, SPI, I2c ** Arduino remoto

Además de los proveedores que proporcionan acceso a hardware real, hemos creado un [proveedor Simulated](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) que actuará como si fue un proveedor compatible con inifitely y está diseñado para que le permiten escribir y depurar sus aplicaciones sin tener que en primer lugar implementarlos en un dispositivo que funcione. Para una experiencia más enriquecida, puede personalizarlo para simular el hardware real. Por ejemplo: actualizando el proveedor I2c devuelva hacer una copia el resultado "75" al enviar el comando para una temperatura leer en un dispositivo con la dirección de esclavo designado. 
