---
title: Asignaciones de raspberry Pi 2 & 3 Pin
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de la funcionalidad de las asignaciones de pin para Raspberry Pi 2 y 3.
keywords: Windows iot, 2 de Rasperry Pi, Raspberry Pi 3, anclar asignaciones, GPIO
ms.openlocfilehash: 86e641bdcc6b4895161c6509ca7529b0dd55fad9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514539"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Asignaciones de raspberry Pi 2 & 3 Pin

![Encabezado de raspberry Pi 2 & 3 Pin](../../media/PinMappingsRPI/RP2_Pinout.png)

Interfaces de hardware para el dispositivo Raspberry Pi 2 y Raspberry Pi 3 se exponen a través del encabezado de 40-pin **celda J8** en el panel. La funcionalidad incluye:

* **24 x** -pines GPIO
* **1 x** -UARTs serie (RPi3 sólo incluye mini UART)
* **2 x** -bus SPI
* **1 x** -bus I2C
* **2 x** -PIN de alimentación de 5 v
* **2 x** : 3,3 v power PIN
* **8 x** -masa PIN

## <a name="gpio-pins"></a>Pines GPIO

Echemos un vistazo a la GPIO disponible en este dispositivo.

### <a name="gpio-pin-overview"></a>Información general sobre el Pin GPIO

Las clavijas GPIO siguientes son accesibles a través de API:

> | GPIO # | Incorporación de cambios de encendido | Funciones alternativas | Pin de encabezado         |
> |-------|---------------|---------------------|--------------------|
> | 2     | Subida        | I2C1 SDA            | 3                  |
> | 3     | Subida        | I2C1 SCL            | 5                  |
> | 4     | Subida        |                     | 7                  |
> | 5     | Subida        |                     | 29                 |
> | 6     | Subida        |                     | 31                 |
> | 7     | Subida        | SPI0 CS1            | 26                 |
> | 8     | Subida        | SPI0 CS0            | 24                 |
> | 9     | PullDown      | SPI0 MISO           | 21                 |
> | 10    | PullDown      | SPI0 MOSI           | 19                 |
> | 11    | PullDown      | SPI0 SCLK           | 23                 |
> | 12    | PullDown      |                     | 32                 |
> | 13    | PullDown      |                     | 33                 |
> | 16    | PullDown      | SPI1 CS0            | 36                 |
> | 17    | PullDown      |                     | 11                 |
> | 18    | PullDown      |                     | 12                 |
> | 19    | PullDown      | SPI1 MISO           | 35                 |
> | 20    | PullDown      | SPI1 MOSI           | 38                 |
> | 21    | PullDown      | SPI1 SCLK           | 40                 |
> | 22    | PullDown      |                     | 15                 |
> | 23    | PullDown      |                     | 16                 |
> | 24    | PullDown      |                     | 18                 |
> | 25    | PullDown      |                     | 22                 |
> | 26    | PullDown      |                     | 37                 |
> | 27    | PullDown      |                     | 13                 |
> | 35*   | Subida        |                     | LED de alimentación rojo      |
> | 47*   | Subida        |                     | LED verde de la actividad |

\* = Raspberry Pi 2 solo. GPIO 35 & 47 no están disponibles en Raspberry Pi 3.

### <a name="gpio-sample"></a>Ejemplo GPIO

Por ejemplo, el siguiente código se abre **GPIO 5** como salida y escribe un digitales '**1**' out en el pin:

```csharp
using Windows.Devices.Gpio;

public void GPIO()
{
    // Get the default GPIO controller on the system
    GpioController gpio = GpioController.GetDefault();
    if (gpio == null)
        return; // GPIO not available on this system

    // Open GPIO 5
    using (GpioPin pin = gpio.OpenPin(5))
    {
        // Latch HIGH value first. This ensures a default value when the pin is set as output
        pin.Write(GpioPinValue.High);

        // Set the IO direction as output
        pin.SetDriveMode(GpioPinDriveMode.Output);

    } // Close pin - will revert to its power-on state
}
```

Al abrir un pin, estará en su estado de encendido, que puede incluir una resistencia de incorporación de cambios. Para desconectar las resistencias de incorporación de cambios y obtener una entrada de impedancia de alta, establezca el modo de unidad en GpioPinDriveMode.Input:

    pin.SetDriveMode(GpioPinDriveMode.Input);

Cuando se cierra un pin, revierte a su estado de encendido.

### <a name="pin-muxing"></a>PIN Muxing

Algunos pines GPIO pueden realizar varias funciones. De forma predeterminada, el PIN se configuran como entradas GPIO. Cuando abre una función alternativa mediante una llamada a `I2cDevice.FromIdAsync()` o `SpiDevice.FromIdAsync()` , el PIN requeridos por la función son automáticamente conmutada ("MUX") a la función correcta. Cuando se cierra el dispositivo mediante una llamada a `I2cDevice.Dispose()` o `SpiDevice.Dispose()`, el PIN se restablecerá a su función de forma predeterminada. Si intenta usar un pin para dos funciones diferentes a la vez, se producirá una excepción al intentar abrir la función en conflicto. Por ejemplo,

```csharp
var controller = GpioController.GetDefault();
var gpio2 = controller.OpenPin(2);      // open GPIO2, shared with I2C1 SDA

var dis = await DeviceInformation.FindAllAsync(I2cDevice.GetDeviceSelector());
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // exception thrown because GPIO2 is open

gpio2.Dispose(); // close GPIO2
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // succeeds because gpio2 is now available

var gpio2 = controller.OpenPin(2); // throws exception because GPIO2 is in use as SDA1

i2cDevice.Dispose(); // release I2C device
var gpio2 = controller.OpenPin(2); // succeeds now that GPIO2 is available
```

## <a name="serial-uart"></a>UART serie

Hay un UART serie disponible en el RPi2/3: **UART0**

* Anclar 8 - **UART0 TX**
* Anclar 10 - **UART0 RX**

El ejemplo siguiente inicializa **UART0** y realiza una operación de escritura seguido por una lectura:


```csharp
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART0");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;                                             /* mini UART: only standard baudrates */
    SerialPort.Parity = SerialParity.None;                                  /* mini UART: no parities */  
    SerialPort.StopBits = SerialStopBitCount.One;                           /* mini UART: 1 stop bit */
    SerialPort.DataBits = 8;

    /* Write a string out over serial */
    string txBuffer = "Hello Serial";
    DataWriter dataWriter = new DataWriter();
    dataWriter.WriteString(txBuffer);
    uint bytesWritten = await SerialPort.OutputStream.WriteAsync(dataWriter.DetachBuffer());

    /* Read data in from the serial port */
    const uint maxReadLength = 1024;
    DataReader dataReader = new DataReader(SerialPort.InputStream);
    uint bytesToRead = await dataReader.LoadAsync(maxReadLength);
    string rxBuffer = dataReader.ReadString(bytesToRead);
}
```

Tenga en cuenta que debe agregar la funcionalidad siguiente a la **Package.appxmanifest** archivo del proyecto UWP para ejecutar código UART serie:

Visual Studio 2017 tiene un problema conocido en el Diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la capacidad de serialcommunication.  Si su appxmanifest agrega la capacidad de serialcommunication, modificar su appxmanifest con el diseñador dañará su appxmanifest (el elemento secundario xml de dispositivo se perderán).  Puede solucionar este problema mediante la edición de mano el appxmanifest haciendo clic en su appxmanifest y seleccione Ver código en el menú contextual.

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a>Bus i2c

Vamos a examinar el bus I2C disponible en este dispositivo.

### <a name="i2c-overview"></a>Información general de i2c

Hay un controlador I2C **I2C1** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**. 1.8 K&#x2126; resistencias pull-up interno ya están instalados en el panel para este bus.

> | Nombre de señal | Número de Pin de encabezado | Número de GPIO |
> |-------------|-------------------|-------------|
> | SDA         | 3                 | 2           |
> | SCL         | 5                 | 3           |

El ejemplo siguiente inicializa **I2C1** y escribe datos en un dispositivo I2C con dirección **0 x 40**:

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Create an I2cDevice with the specified I2C settings
    var controller = await I2cController.GetDefaultAsync();

    using (I2cDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

## <a name="spi-bus"></a>Bus SPI

Hay dos controladores de bus SPI en RPi2/3.

### <a name="spi0"></a>SPI0

> | Nombre de señal | Número de Pin de encabezado | Número de GPIO |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | MISO        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | Nombre de señal | Número de Pin de encabezado | Número de GPIO |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | MISO        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>Ejemplo SPI

Un ejemplo de cómo realizar un IRP de escritura en el bus **SPI0** mediante select chip 0 se muestra a continuación:

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz 
    settings.ClockFrequency = 10000000;

    // Get a selector string that will return our wanted SPI controller
    string aqs = SpiDevice.GetDeviceSelector("SPI0");
    
    // Find the SPI bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);
    
    // Create an SpiDevice with our selected bus controller and Spi settings
    using (SpiDevice device = await SpiDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

