---
title: Asignaciones de Raspberry pi 2 & 3 pin
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la funcionalidad de las asignaciones de PIN para Raspberry pi 2 y 3.
keywords: Windows IOT, Rasperry pi 2, Raspberry PI 3, asignaciones de PIN, GPIO
ms.openlocfilehash: 2a3155b28fb01434ff8596de6e2f75b06b42f6ae
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917849"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Asignaciones de Raspberry pi 2 & 3 pin

![Encabezado Raspberry pi 2 & 3 pin](../../media/PinMappingsRPI/RP2_Pinout.png)

Las interfaces de hardware para Raspberry pi 2 y Raspberry PI 3 se exponen a través del encabezado de 40 **J8** en el panel. La funcionalidad incluye:

* PIN de **24x** a GPIO
* **1x** : UART en serie (RPi3 solo incluye mini UART)
* Bus **2x** -SPI
* Bus **1x** -I2C
* clavijas de potencia **2x** -5V
* **2x** -3,3 clavijas de alimentación
* pines de **8X**

## <a name="gpio-pins"></a>PIN de GPIO

Echemos un vistazo al GPIO disponible en este dispositivo.

### <a name="gpio-pin-overview"></a>Introducción al pin de GPIO

Se puede acceder a los siguientes PIN de GPIO a través de las API:

> | GPIO # | Extracción de energía | Funciones alternativas | PIN de encabezado         |
> |-------|---------------|---------------------|--------------------|
> | 2     | PullUp        | I2C1 SDA            | 3                  |
> | 3     | PullUp        | I2C1 SCL            | 5                  |
> | 4     | PullUp        |                     | 7                  |
> | 5     | PullUp        |                     | 29                 |
> | 6     | PullUp        |                     | 31                 |
> | 7     | PullUp        | SPI0 CS1            | 26                 |
> | 8     | PullUp        | SPI0 CS0            | 24                 |
> | 9     | Combinan      | SPI0           | 21                 |
> | 10    | Combinan      | SPI0 MOSI           | 19                 |
> | 11    | Combinan      | SPI0 SCLK           | 23                 |
> | 12    | Combinan      |                     | 32                 |
> | 13    | Combinan      |                     | 33                 |
> | 16    | Combinan      | SPI1 CS0            | 36                 |
> | 17    | Combinan      |                     | 11                 |
> | 18    | Combinan      |                     | 12                 |
> | 19    | Combinan      | SPI1           | 35                 |
> | 20    | Combinan      | SPI1 MOSI           | 38                 |
> | 21    | Combinan      | SPI1 SCLK           | 40                 |
> | 22    | Combinan      |                     | 15                 |
> | 23    | Combinan      |                     | 16                 |
> | 24    | Combinan      |                     | 18                 |
> | 25    | Combinan      |                     | 22                 |
> | 26    | Combinan      |                     | 37                 |
> | 27    | Combinan      |                     | 13                 |
> | 35 *   | PullUp        |                     | LED de alimentación rojo      |
> | 47 *   | PullUp        |                     | LED de actividad verde |

\* = Raspberry pi 2 solamente. GPIO 35 & 47 no están disponibles en Raspberry PI 3.

### <a name="gpio-sample"></a>Ejemplo de GPIO

Como ejemplo, el código siguiente abre **GPIO 5** como salida y escribe un '**1**' digital en el PIN:

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

Al abrir un PIN, estará en su estado de encendido, que puede incluir una resistencia de extracción. Para desconectar las resistencias de extracción y obtener una entrada de alta impedancia, establezca el modo de unidad en GpioPinDriveMode. Input:

    pin.SetDriveMode(GpioPinDriveMode.Input);

Cuando se cierra un PIN, vuelve a su estado de encendido.

### <a name="pin-muxing"></a>Multiplexación de PIN

Algunos PIN de GPIO pueden realizar varias funciones. De forma predeterminada, los PIN se configuran como entradas de GPIO. Cuando se abre una función alternativa llamando a `I2cDevice.FromIdAsync()` o `SpiDevice.FromIdAsync()`, los pin requeridos por la función se cambian automáticamente ("MUX") a la función correcta. Cuando el dispositivo se cierra llamando a `I2cDevice.Dispose()` o `SpiDevice.Dispose()`, los pin vuelven a su función predeterminada. Si intenta usar un PIN para dos funciones diferentes a la vez, se producirá una excepción al intentar abrir la función en conflicto. Por ejemplo:

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

## <a name="serial-uart"></a>UART en serie

Hay un UART en serie disponible en RPi2/3: **UART0**

* Pin 8- **UART0 TX**
* PIN 10- **UART0 RX**

En el ejemplo siguiente se inicializa **UART0** y se realiza una escritura seguida de una lectura:


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

Tenga en cuenta que debe agregar la siguiente funcionalidad al archivo **Package. appxmanifest** en el proyecto de UWP para ejecutar el código UART en serie:

Visual Studio 2017 tiene un error conocido en el diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la funcionalidad serialcommunication.  Si el appxmanifest agrega la funcionalidad serialcommunication, la modificación de appxmanifest con el diseñador dañará el appxmanifest (se perderá el elemento secundario XML del dispositivo).  Puede solucionar este problema de forma manual editaba el appxmanifest; para ello, haga clic con el botón derecho en el appxmanifest y seleccione Ver código en el menú contextual.

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a>Bus I2C

Echemos un vistazo al bus I2C disponible en este dispositivo.

### <a name="i2c-overview"></a>Información general de I2C

Hay un **I2C1** de controlador i2c expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**. en el&#x2126; panel de este bus ya están instaladas las resistencias de extracción internas de 1,8 k.

> | Nombre de señal | Número de PIN del encabezado | Número de GPIO |
> |-------------|-------------------|-------------|
> | EMPAQUETADO         | 3                 | 2           |
> | FICHERO         | 5                 | 3           |

En el ejemplo siguiente se inicializa **I2C1** y se escriben datos en un dispositivo I2C con la dirección **0x40**:

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

Hay dos controladores de bus SPI disponibles en RPi2/3.

### <a name="spi0"></a>SPI0

> | Nombre de señal | Número de PIN del encabezado | Número de GPIO |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | PERMISOS        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | Nombre de señal | Número de PIN del encabezado | Número de GPIO |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | PERMISOS        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>Ejemplo de SPI

A continuación se muestra un ejemplo de cómo realizar una escritura SPI en el bus **SPI0** con el chip Select 0:

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

