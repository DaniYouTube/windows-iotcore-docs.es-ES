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
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>Acceso UserMode GPIO, I2C y SPI

Windows 10 contiene nuevas API para acceder a GPIO, I2C, SPI y UART directamente desde el modo usuario. Los paneles de desarrollo como Raspberry Pi 2 exponen un subconjunto de estas conexiones que permiten a los usuarios ampliar un módulo de cálculo base con circuitos personalizados para dirigirte a una aplicación particular. Normalmente, estos buses de bajo nivel se comparten con otras funciones incorporadas críticas, con solo un subconjunto de las patillas y buses de GPIO expuestos en los encabezados. Para preservar la estabilidad del sistema, es necesario especificar qué patillas y buses son seguros para modificar las aplicaciones de modo de usuario.

El acceso de modo de usuario a buses de nivel bajo en Windows se asocia a través de los marcos `GpioClx` y `SpbCx` existentes. Expone un nuevo controlador denominado RhProxy, disponible en Windows IoT Core y Enterprise de Windows, `GpioClx` y `SpbCx` recursos a modo de usuario. Para habilitar las API, se debe declarar un nodo de dispositivo para rhproxy en las tablas ACPI con cada uno de los recursos GPIO y SPB que se deben exponer en modo de usuario.

Puede encontrar más documentación detallada en modo de usuario acceso a través de RhProxy [aquí](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access).

## <a name="bus-providers"></a>Proveedores de bus

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

- **ADC**
  - Ads1x15
  - Mcp3008
  - Arduino remoto

- **PWM**
  - PCA9685
  - Simular con Gpio
  - Arduino remoto
  
- **Gpio, SPI, I2C**
  - Arduino remoto

Además de los proveedores que proporcionan acceso a hardware real, hemos creado un [proveedor Simulated](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) que actuará como si fue un proveedor compatible con inifitely y está diseñado para que le permiten escribir y depurar sus aplicaciones sin tener que en primer lugar implementarlos en un dispositivo que funcione. Para una experiencia más enriquecida, puede personalizarlo para simular el hardware real. Por ejemplo: actualizando el proveedor I2c devuelva hacer una copia el resultado "75" al enviar el comando para una temperatura leer en un dispositivo con la dirección de esclavo designado.

## <a name="additional-resources"></a>Recursos adicionales

Herramientas de bus adicional, los códigos de ejemplo y compilación y pruebas en I2C, SPI, GPIO, pueden encontrarse MinComm/UART [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).

