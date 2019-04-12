---
title: Asignaciones de Pin máxima Minnowboard
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de la funcionalidad de las asignaciones de pin para Minnowboard Max.
keywords: Windows iot, Minnowboard Max, asignaciones de pin, GPIO
ms.openlocfilehash: 884d9ee0d93167a13f39a28b28454daccb2eebad
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514792"
---
# <a name="minnowboard-max-pin-mappings"></a>Asignaciones de Pin máxima MinnowBoard

> [!NOTE] 
> Para comparar esta asignación de pin a versiones más recientes de la Minnowboard, visite la documentación [aquí](https://minnowboard.org/minnowboard-turbot/documentation).

## <a name="overview"></a>Información general

![Encabezado de Pin máxima MinnowBoard](../../media/PinMappingsMBM/MBM_Pinout.png)

Interfaces de hardware para el número máximo de MinnowBoard se exponen a través del encabezado de 26 clavijas **JP1** en el panel. La funcionalidad incluye:

* **10 x** -pines GPIO
* **2 x** -UARTs serie
* **1 x** -bus SPI
* **1 x** -bus I2C
* **1 x** -pin de alimentación de 5 v
* **1 x** : 3,3 v pin de energía
* **2 x** -masa PIN

Los niveles de lógica de usos 3,3 v MinnowBoard Max en todas las patillas de E/S. Además se almacenan en búfer todos los bolos por [TXS0104E](http://www.ti.com/product/txs0104e) shifters, a excepción de la tierra de energía y de PIN de nivel.
Estos shifters nivel se muestran como resultados de recopilador abierto con un **10K&#x2126; subida del electromagnético y la subida del está presente, independientemente de si la operación de E/S está establecida en entrada o salida.**
 
La naturaleza de recopilador de apertura de los medios shifters nivel es que el PIN pueden devolver ' 0 'fuertemente, pero solo débil de salida ' 1'. Esto es importante tener en cuenta al conectar los dispositivos que dibujar actual de los bolos (por ejemplo, un LED). Consulte la [ejemplo llamativa](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) para la forma correcta un LED MinnowBoard máxima de la interfaz.

## <a name="gpio-pins"></a>Pines GPIO

Las clavijas GPIO siguientes son accesibles a través de API:

> | GPIO # | Pin de encabezado         |
> |-------|--------------------|
> | 0     | 21                 |
> | 1     | 23                 |
> | 2     | 25                 |
> | 3     | 14                 |
> | 4     | 16                 |
> | 5     | 18                 |
> | 6     | 20                 |
> | 7     | 22                 |
> | 8     | 24                 |
> | 9     | 26                 |

**Nota:** **GPIO 4** y **GPIO 5** se usan por el número máximo de MinnowBoard como anclajes de configuración de arranque en el BIOS.
Asegúrese de que los dispositivos conectados no controlar estos GPIO baja durante el arranque, ya que esto podría impedir que el MBM arranque.
Después de iniciarse la MBM más allá de la BIOS, normalmente se puede usar estos GPIO.
     
## <a name="gpio-sample"></a>Ejemplo GPIO

Por ejemplo, el siguiente código se abre **GPIO 5** como salida y escribe un digitales '**1**' out en el pin:
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(5);        /* Open GPIO 5                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

## <a name="serial-uart"></a>UART serie

Hay dos UARTS serie en el MBM: **UART1** y **UART2**

**UART1** tiene la norma **UART1 TX** y **UART1 RX** señales de líneas, junto con el flujo de controlan **UART1 CTS** y **UART1 RTS**.

* Anclar 6 - **UART1 TX**
* Anclar 8 - **UART1 RX**
* Anclar 10 - **UART1 CTS**
* Anclar 12 - **UART1 RTS**

UART1 no funciona a partir de la compilación 10240. Use UART2 o un convertidor de USB a serie.

**UART2** incluye solamente el **UART2 TX** y **UART2 RX** líneas.

* Anclar 17 - **UART2 TX**
* Anclar 19 - **UART2 RX**

UART2 no admite el control de flujo, para tener acceso a las siguientes propiedades de SerialDevice puede dar lugar a una excepción:

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * Protocolo de enlace - SerialHandshake.None solo se admite

El ejemplo siguiente inicializa **UART2** y realiza una operación de escritura seguido por una lectura:

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART2");                   /* Find the selector string for the serial device   */
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

Tenga en cuenta que debe agregar la funcionalidad siguiente a la **Package.appxmanifest** archivo del proyecto UWP para ejecutar código UART serie:

Visual Studio 2017 tiene un problema conocido en el Diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la capacidad de serialcommunication.  Si su appxmanifest agrega la capacidad de serialcommunication, modificar su appxmanifest con el diseñador dañará su appxmanifest (el elemento secundario xml de dispositivo se perderán).  Puede solucionar este problema mediante la edición de mano el appxmanifest haciendo clic en su appxmanifest y seleccione Ver código en el menú contextual.

```
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

Hay un controlador I2C **I2C5** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**. 10K&#x2126; resistencias pull-up interno ya están presentes en estas líneas.

* Anclar 15 - **I2C5 SDA**
* Anclar 13 - **I2C5 SCL**

### <a name="i2c-sample"></a>Ejemplo de i2c

El ejemplo siguiente inicializa **I2C5** y escribe datos en un dispositivo I2C con dirección **0 x 40**:

```C#
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

### <a name="i2c-issues"></a>Problemas de i2c

El número máximo de MinnowBoard tiene un problema conocido con el bus I2C, lo que provoca problemas de comunicación con determinados dispositivos I2C. Normalmente, un dispositivo I2C reconocerá su dirección durante una solicitud de bus.
Sin embargo, en determinadas condiciones esta confirmación no se propague hacia atrás por el nivel shifters a la MBM, y como resultado la CPU piensa que el dispositivo no ha respondido y cancela la transacción de bus.
El problema parece estar relacionado con la [TXS0104E](http://www.ti.com/product/txs0104e) shifters en las patillas de la E/S, que pueden desencadenar prematuramente debido a picos de voltaje de la línea de nivel.
La solución actual consiste en Insertar una resistencia 100 ohm en serie con la línea SCK I2C, lo que ayuda a suprimir los picos. No todos los dispositivos se ven afectados, por lo que esta solución solo es necesario si tiene problemas para obtener una respuesta de bus. Un dispositivo que se sabe que requieren esta solución alternativa es la HTU21D.

## <a name="spi-bus"></a>Bus SPI

Echemos un vistazo del bus SPI disponible en este dispositivo.

### <a name="spi-overview"></a>Información general SPI

Hay un controlador SPI **SPI0** disponible en el MBM:

* Anclar 9 - **SPI0 MOSI**
* Anclar 7 - **SPI0 MISO**
* Anclar 11 - **SPI0 SCLK**
* Anclar 5 - **SPI0 CS0**


### <a name="spi-sample"></a>Ejemplo SPI

Un ejemplo sobre cómo realizar un IRP de escritura en el bus **SPI0** se muestra a continuación:

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz
    settings.ClockFrequency = 10000000;

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

