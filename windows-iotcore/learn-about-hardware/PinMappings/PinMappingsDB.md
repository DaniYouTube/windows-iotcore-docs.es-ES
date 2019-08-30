---
title: Asignaciones de Dragonboard PIN
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la funcionalidad de las asignaciones de PIN para Dragonboard.
keywords: asignaciones de Windows IOT, Dragonboard, PIN, GPIO
ms.openlocfilehash: f6df962c6d05aa912013f8f0819c0789bfc393ce
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167691"
---
# <a name="dragonboard-pin-mappings"></a>Asignaciones de Dragonboard PIN

![Encabezado Dragonboard PIN](../../media/PinMappingsDB/DB_Pinout.png)

Las interfaces de hardware de Dragonboard se exponen a través del encabezado 40-PIN en el panel. La funcionalidad incluye:

* PIN de **11x** -GPIO
* **2x** -UART en serie
* Bus **1x** -SPI
* Bus **2x** -I2C
* PIN de alimentación de **1x** -5V
* **1x** -1,8 v Power PIN
* pines de la base **4x**

Tenga en cuenta que Dragonboard usa niveles de lógica de 1,8 V en todos los pin de e/s. 

## <a name="gpio-pins"></a>PIN de GPIO

Echemos un vistazo al GPIO disponible en este dispositivo.

### <a name="gpio-pin-table"></a>Tabla de PIN de GPIO

Se puede acceder a los siguientes PIN de GPIO a través de las API:

> | GPIO # | PIN de encabezado         |
> |-------|--------------------|
> | 36    | 23                 |
> | 12    | 24                 |
> | 13    | 25                 |
> | 69    | 26                 |
> | 115   | 27                 |
> | 24    | 29                 |
> | 25    | 30                 |
> | 35    | 31                 |
> | 34    | 32                 |
> | 28    | 33                 |
> | 33    | 34                 |
> | 21    | LED de usuario 1         | 
> | 120   | LED de usuario 2         |         


Como ejemplo, el código siguiente abre **GPIO 35** como salida y escribe un '**1**' digital en el PIN:
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(35);       /* Open GPIO 35                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

### <a name="gpio-issues"></a>Problemas de GPIO

* La salida no funciona en GPIO 24. La entrada funciona bien.
* Los PIN se configuran como InputPullDown en el arranque, pero cambiarán a la entrada (flotante) la primera vez que se abran.
* Los PIN no revierten a su estado predeterminado al cerrarse
* Se pueden producir interrupciones falsas cuando las interrupciones están habilitadas en varios PIN


## <a name="serial-uart"></a>UART en serie

Hay dos UART en serie disponibles en Dragonboard **UART0** y **UART1**

**UART0** tiene las líneas de RX estándar **UART0 TX** y **UART0** , junto con las señales de control de flujo **UART0 CTS** y **UART0 RTS**.

* Pin 5- **UART0 TX**
* PIN 7- **UART0 RX**
* PIN 3- **UART0 CTS**
* PIN 9- **UART0 RTS**


**UART1** incluye solo las líneas RX **UART1 TX** y **UART1** .

* PIN 11- **UART1 TX**
* PIN 13- **UART1 RX**

En el ejemplo siguiente se inicializa **UART1** y se realiza una escritura seguida de una lectura:

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART1");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;
    SerialPort.Parity = SerialParity.None;         
    SerialPort.StopBits = SerialStopBitCount.One;
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
> [!NOTE]
> Visual Studio 2017 tiene un error conocido en el diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la funcionalidad serialcommunication.  Si el appxmanifest agrega la funcionalidad serialcommunication, la modificación de appxmanifest con el diseñador dañará el appxmanifest (se perderá el elemento secundario XML del dispositivo).  Puede solucionar este problema de forma manual editaba el appxmanifest; para ello, haga clic con el botón derecho en el appxmanifest y seleccione Ver código en el menú contextual.

Debe agregar la siguiente funcionalidad al archivo **Package. appxmanifest** en el proyecto de UWP para ejecutar el código de UART en serie:

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

Echemos un vistazo a los buses I2C disponibles en este dispositivo.

### <a name="i2c-pins"></a>Clavijas I2C

**I2C0** expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**

* PIN 17- **I2C0 SDA**
* PIN 15- **I2C0 SCL**

**I2C1** expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**

* Patilla 21- **I2C1 SDA**
* Pin 19- **I2C1 SCL**

### <a name="i2c-sample"></a>Ejemplo de I2C

En el ejemplo siguiente se inicializa **I2C0** y se escriben datos en un dispositivo I2C con la dirección **0x40**:

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Get a selector string that will return our wanted I2C controller
    string aqs = I2cDevice.GetDeviceSelector("I2C0");
    
    // Find the I2C bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);

    // Create an I2cDevice with our selected bus controller and I2C settings 
    using (I2cDevice device = await I2cDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```


## <a name="spi-bus"></a>Bus SPI

Echemos un vistazo al bus SPI disponible en este dispositivo.

### <a name="spi-pins"></a>Clavijas SPI

Hay un **SPI0** de controlador de SPI disponible en la base de

* PIN de 10 a **SPI0**
* PIN 14- **SPI0 Mosi**
* Pin 8- **SPI0 SCLK**
* Pin 12- **SPI0 CS0**

### <a name="spi-issues"></a>Problemas con SPI

El reloj SPI se fija a 4,8 MHz. Se omitirá el reloj SPI solicitado. 


### <a name="spi-sample"></a>Ejemplo de SPI

A continuación se muestra un ejemplo de cómo realizar una escritura SPI en el bus **SPI0** :

```C3
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```
