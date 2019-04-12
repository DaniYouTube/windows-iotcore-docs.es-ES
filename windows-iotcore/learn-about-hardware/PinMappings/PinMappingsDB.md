---
title: Asignaciones de Dragonboard Pin
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de la funcionalidad de las asignaciones de pin para Dragonboard.
keywords: asignaciones de Windows iot, Dragonboard, pin, GPIO
ms.openlocfilehash: f6df962c6d05aa912013f8f0819c0789bfc393ce
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515078"
---
# <a name="dragonboard-pin-mappings"></a>Asignaciones de Dragonboard Pin

![Encabezado Dragonboard Pin](../../media/PinMappingsDB/DB_Pinout.png)

Interfaces de hardware para el Dragonboard se exponen a través del encabezado de 40-pin en el panel. La funcionalidad incluye:

* **x 11** -pines GPIO
* **2 x** -UARTs serie
* **1 x** -bus SPI
* **2 x** -bus I2C
* **1 x** -pin de alimentación de 5 v
* **1 x** : 1,8 pin de energía
* **4 x** -masa PIN

Tenga en cuenta que el Dragonboard usa 1,8 niveles de lógica en todas las patillas de E/S. 

## <a name="gpio-pins"></a>Pines GPIO

Echemos un vistazo a la GPIO disponible en este dispositivo.

### <a name="gpio-pin-table"></a>Tabla GPIO Pin

Las clavijas GPIO siguientes son accesibles a través de API:

> | GPIO # | Pin de encabezado         |
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
> | 21    | 1 de LED de usuario         | 
> | 120   | 2 de LED de usuario         |         


Por ejemplo, el siguiente código se abre **GPIO 35** como salida y escribe un digitales '**1**' out en el pin:
         
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

### <a name="gpio-issues"></a>Problemas GPIO

* Salida no funciona en GPIO 24. Entrada funciona bien.
* PIN se configuran como InputPullDown durante el arranque, pero cambiará a la entrada (flotante) la primera vez que se abren.
* Los PIN no volverá a su estado predeterminado al cerrar
* Interrupciones falsas pueden verse cuando están habilitadas las interrupciones en varios PIN


## <a name="serial-uart"></a>UART serie

Hay dos UARTS serie en el Dragonboard **UART0** y **UART1**

**UART0** tiene la norma **UART0 TX** y **UART0 RX** señales de líneas, junto con el flujo de controlan **UART0 CTS** y **UART0 RTS**.

* Anclar 5 - **UART0 TX**
* Anclar 7 - **UART0 RX**
* Anclar 3 - **UART0 CTS**
* Anclar 9 - **UART0 RTS**


**UART1** incluye solamente el **UART1 TX** y **UART1 RX** líneas.

* Anclar 11 - **UART1 TX**
* Anclar 13 - **UART1 RX**

El ejemplo siguiente inicializa **UART1** y realiza una operación de escritura seguido por una lectura:

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
> Visual Studio 2017 tiene un problema conocido en el Diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la capacidad de serialcommunication.  Si su appxmanifest agrega la capacidad de serialcommunication, modificar su appxmanifest con el diseñador dañará su appxmanifest (el elemento secundario xml de dispositivo se perderán).  Puede solucionar este problema mediante la edición de mano el appxmanifest haciendo clic en su appxmanifest y seleccione Ver código en el menú contextual.

Debe agregar la funcionalidad siguiente a la **Package.appxmanifest** archivo del proyecto UWP para ejecutar código UART serie:

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

Echemos un vistazo a lo buses de I2C disponible en este dispositivo.

### <a name="i2c-pins"></a>PIN i2c

**I2C0** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**

* Anclar 17 - **I2C0 SDA**
* Anclar 15 - **I2C0 SCL**

**I2C1** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**

* Anclar 21 - **I2C1 SDA**
* Anclar 19 - **I2C1 SCL**

### <a name="i2c-sample"></a>Ejemplo de i2c

El ejemplo siguiente inicializa **I2C0** y escribe datos en un dispositivo I2C con dirección **0 x 40**:

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

Echemos un vistazo del bus SPI disponible en este dispositivo.

### <a name="spi-pins"></a>PIN SPI

Hay un controlador SPI **SPI0** disponible en la base de datos

* Anclar 10 - **SPI0 MISO**
* Anclar 14 - **SPI0 MOSI**
* Anclar 8 - **SPI0 SCLK**
* Anclar 12 - **SPI0 CS0**

### <a name="spi-issues"></a>Problemas SPI

El reloj SPI se fija en 4.8 mhz. Se omitirá el reloj SPI solicitado. 


### <a name="spi-sample"></a>Ejemplo SPI

Un ejemplo sobre cómo realizar un IRP de escritura en el bus **SPI0** se muestra a continuación:

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
