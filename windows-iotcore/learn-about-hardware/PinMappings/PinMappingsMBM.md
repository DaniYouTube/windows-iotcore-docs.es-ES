---
title: Minnowboard asignaciones de PIN máx.
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la funcionalidad de las asignaciones de PIN para Minnowboard Max.
keywords: Windows IOT, Minnowboard Max, asignaciones de PIN, GPIO
ms.openlocfilehash: 884d9ee0d93167a13f39a28b28454daccb2eebad
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167501"
---
# <a name="minnowboard-max-pin-mappings"></a>MinnowBoard asignaciones de PIN máx.

> [!NOTE] 
> Para comparar esta asignación de pin con las versiones más recientes de Minnowboard, visite la documentación [aquí](https://minnowboard.org/minnowboard-turbot/documentation).

## <a name="overview"></a>Información general

![MinnowBoard encabezado Max PIN](../../media/PinMappingsMBM/MBM_Pinout.png)

Las interfaces de hardware para el máximo de MinnowBoard se exponen a través del encabezado de 26 pines **JP1** en el panel. La funcionalidad incluye:

* PIN de **10 veces** -GPIO
* **2x** -UART en serie
* Bus **1x** -SPI
* Bus **1x** -I2C
* PIN de alimentación de **1x** -5V
* **1x** -3,3 v de alimentación
* pines de **doble** fondo

MinnowBoard Max usa los niveles de lógica de 3,3 V en todos los pin de e/s. Además, todos los PIN se almacenan en búfer mediante los desplazadores de nivel de [TXS0104E](http://www.ti.com/product/txs0104e) , con la excepción de las clavijas de alimentación y de alimentación.
Estos desplazadores de nivel aparecen como salidas del recopilador abierto con una **extracción resistente de&#x2126; 10 000 y la extracción está presente independientemente de si la e/s está establecida en entrada o salida.**
 
La naturaleza de Open-Collector de los desplazamientos de nivel significa que los pin pueden generar un "0" firmemente, pero solo se genera de forma débil un "1". Es importante tener en cuenta cuando se conectan los dispositivos que dibujan el actual a partir de las clavijas (por ejemplo, un LED). Vea el [ejemplo de parpadeo](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) para obtener la manera correcta de interactuar con el LED MinnowBoard Max.

## <a name="gpio-pins"></a>PIN de GPIO

Se puede acceder a los siguientes PIN de GPIO a través de las API:

> | GPIO # | PIN de encabezado         |
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

**Nota:** Los pin de configuración Max **4** y **GPIO 5** se usan en las clavijas de configuración MinnowBoard Max as bootstrap del BIOS.
Asegúrese de que los dispositivos conectados no controlan el nivel de GPIO bajo durante el arranque, ya que esto podría impedir el arranque de MBM.
Después de que MBM haya arrancado más allá del BIOS, estos GPIO se pueden usar con normalidad.
     
## <a name="gpio-sample"></a>Ejemplo de GPIO

Como ejemplo, el código siguiente abre **GPIO 5** como salida y escribe un '**1**' digital en el PIN:
         
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

## <a name="serial-uart"></a>UART en serie

Hay dos UART en serie disponibles en MBM: **UART1** y **UART2**

**UART1** tiene las líneas de RX estándar **UART1 TX** y **UART1** , junto con las señales de control de flujo **UART1 CTS** y **UART1 RTS**.

* Patilla 6: **UART1 TX**
* Pin 8- **UART1 RX**
* PIN 10- **UART1 CTS**
* Pin 12- **UART1 RTS**

UART1 no funciona a partir de la compilación 10240. Use UART2 o un convertidor USB-serie.

**UART2** incluye solo las líneas RX **UART2 TX** y **UART2** .

* PIN 17- **UART2 TX**
* Pin 19- **UART2 RX**

UART2 no admite el control de flujo, por lo que el acceso a las siguientes propiedades de SerialDevice puede dar lugar a que se produzca una excepción:

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * Solo se admite el protocolo de enlace SerialHandshake. None

En el ejemplo siguiente se inicializa **UART2** y se realiza una escritura seguida de una lectura:

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

Tenga en cuenta que debe agregar la siguiente funcionalidad al archivo **Package. appxmanifest** en el proyecto de UWP para ejecutar el código UART en serie:

Visual Studio 2017 tiene un error conocido en el diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la funcionalidad serialcommunication.  Si el appxmanifest agrega la funcionalidad serialcommunication, la modificación de appxmanifest con el diseñador dañará el appxmanifest (se perderá el elemento secundario XML del dispositivo).  Puede solucionar este problema de forma manual editaba el appxmanifest; para ello, haga clic con el botón derecho en el appxmanifest y seleccione Ver código en el menú contextual.

```
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

Hay un **I2C5** de controlador i2c expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**. 10&#x2126; 000 resistencias internas de extracción ya están presentes en estas líneas.

* PIN 15- **I2C5 SDA**
* PIN 13- **I2C5 SCL**

### <a name="i2c-sample"></a>Ejemplo de I2C

En el ejemplo siguiente se inicializa **I2C5** y se escriben datos en un dispositivo I2C con la dirección **0x40**:

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

### <a name="i2c-issues"></a>Problemas de I2C

MinnowBoard Max tiene un problema conocido con el bus I2C que causa problemas de comunicación con determinados dispositivos I2C. Normalmente, un dispositivo I2C confirma su dirección durante una solicitud de bus.
Sin embargo, en determinadas condiciones, este reconocimiento no puede propagarse de nuevo a través de los desplazamientos de nivel a MBM y, como resultado, la CPU considera que el dispositivo no respondió y cancela la transacción de bus.
El problema parece estar relacionado con los desplazadores de nivel de [TXS0104E](http://www.ti.com/product/txs0104e) en los pines de e/s, que pueden desencadenarse prematuramente debido a picos de tensión en la línea.
La solución actual es insertar una resistencia de 100 Ohm en serie con la línea I2C SCK, que ayuda a suprimir los picos. No todos los dispositivos se ven afectados, por lo que esta solución solo es necesaria si tiene problemas para obtener una respuesta de bus. Un dispositivo que se sabe que requiere esta solución es el HTU21D.

## <a name="spi-bus"></a>Bus SPI

Echemos un vistazo al bus SPI disponible en este dispositivo.

### <a name="spi-overview"></a>Información general sobre SPI

Hay un **SPI0** de controlador de SPI disponible en MBM:

* PIN 9- **SPI0 Mosi**
* PIN 7: **SPI0**
* PIN 11- **SPI0 SCLK**
* Pin 5- **SPI0 CS0**


### <a name="spi-sample"></a>Ejemplo de SPI

A continuación se muestra un ejemplo de cómo realizar una escritura SPI en el bus **SPI0** :

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

