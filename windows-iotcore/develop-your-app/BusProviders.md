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
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>Acceso de modo de solo acceso a GPIO, I2C y SPI

Windows 10 contiene nuevas API para acceder a GPIO, I2C, SPI y UART directamente desde el modo usuario. Los paneles de desarrollo como Raspberry Pi 2 exponen un subconjunto de estas conexiones que permiten a los usuarios ampliar un módulo de cálculo base con circuitos personalizados para dirigirte a una aplicación particular. Normalmente, estos buses de bajo nivel se comparten con otras funciones incorporadas críticas, con solo un subconjunto de las patillas y buses de GPIO expuestos en los encabezados. Para preservar la estabilidad del sistema, es necesario especificar qué patillas y buses son seguros para modificar las aplicaciones de modo de usuario.

El acceso de modo usuario a buses de nivel bajo en Windows se asocia a través de los marcos`GpioClx``SpbCx`existentes. Un nuevo controlador denominado RhProxy, disponible en Windows IoT Core y Windows Enterprise, expone los recursos de `GpioClx` y `SpbCx` a un modo en modo de otro. Para habilitar las API, se debe declarar un nodo de dispositivo para rhproxy en las tablas ACPI con cada uno de los recursos GPIO y SPB que se deben exponer en modo de usuario.

Puede encontrar documentación más detallada sobre el acceso de modo de RhProxy [aquí](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).

## <a name="bus-providers"></a>Proveedores de bus

A partir de Windows 10, Windows ha tenido API de UWP integradas que proporcionan acceso directo a los buses de GPIO, SPI o I2C ubicados en el SOC. Esto proporciona un acceso muy sencillo a este hardware desde una API de alto nivel. Sin embargo, hay muchas ocasiones en las que un creador de dispositivos quiere usar un controlador fuera de la SOC para tener acceso a un bus. Puede ser tan simple como un chip barato que agregue 16 clavijas de GPIO, o tan rico como una MCU completa (por ejemplo, un Arduino) que no solo agregue los pin GPIO, SPI y I2C, sino que también admita PWM y ADC. Con el modelo de "proveedor de bus", ofrecemos a los desarrolladores la capacidad de acceder a estos buses fuera de la SOC mediante las API integradas, mediante un proveedor de modo de usuario que se asocia a la brecha.

Alguien que crea un proveedor implementa un conjunto de interfaces en una biblioteca de clases de UWP y, a continuación, cualquier desarrollador que quiera comunicarse con ese hardware simplemente incluye el componente e indica a las API integradas sobre él. Si observa el código de ejemplo del proveedor de [Arduino remoto](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) , puede ver lo fácil que es configurar el proveedor y, una vez establecido como el proveedor predeterminado para esa aplicación, el resto del código de la aplicación cliente es idéntico al código necesario para acceder a un bus en SOC.


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

Actualmente tenemos varios proveedores disponibles en el repositorio de github de [proveedores de bus](https://github.com/ms-iot/BusProviders) . Además del código del proveedor, cada proveedor tiene una solución de VS de ejemplo que muestra cómo un cliente usaría ese proveedor. 

- **ADC**
  - Ads1x15
  - Mcp3008
  - Arduino remoto

- **PWM**
  - PCA9685
  - Simulado con GPIO
  - Arduino remoto
  
- **GPIO, SPI, I2C**
  - Arduino remoto

Además de los proveedores que proporcionan acceso al hardware real, hemos creado un [proveedor simulado](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) que actuará como si fuera un proveedor compatible con inifitely y está diseñado para permitirle escribir y depurar las aplicaciones sin tener que implementarlas primero en un dispositivo de trabajo. Para obtener una experiencia más completa, puede personalizarla para simular el hardware real. Por ejemplo: actualizar el proveedor I2C para devolver el resultado "75" cuando lo envíe al comando para una lectura de temperatura en un dispositivo con la dirección subordinada designada.

## <a name="additional-resources"></a>Recursos adicionales

[Aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)encontrará herramientas adicionales de bus, códigos de ejemplo y compilaciones y pruebas en I2C, SPI, GPIO, MINCOMM/UART.

