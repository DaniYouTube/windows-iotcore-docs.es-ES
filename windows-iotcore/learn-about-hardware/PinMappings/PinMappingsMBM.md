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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="50df8-104">Asignaciones de Pin máxima MinnowBoard</span><span class="sxs-lookup"><span data-stu-id="50df8-104">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="50df8-105">Para comparar esta asignación de pin a versiones más recientes de la Minnowboard, visite la documentación [aquí](https://minnowboard.org/minnowboard-turbot/documentation).</span><span class="sxs-lookup"><span data-stu-id="50df8-105">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="50df8-106">Información general</span><span class="sxs-lookup"><span data-stu-id="50df8-106">Overview</span></span>

![Encabezado de Pin máxima MinnowBoard](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="50df8-108">Interfaces de hardware para el número máximo de MinnowBoard se exponen a través del encabezado de 26 clavijas **JP1** en el panel.</span><span class="sxs-lookup"><span data-stu-id="50df8-108">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="50df8-109">La funcionalidad incluye:</span><span class="sxs-lookup"><span data-stu-id="50df8-109">Functionality includes:</span></span>

* <span data-ttu-id="50df8-110">**10 x** -pines GPIO</span><span class="sxs-lookup"><span data-stu-id="50df8-110">**10x** - GPIO pins</span></span>
* <span data-ttu-id="50df8-111">**2 x** -UARTs serie</span><span class="sxs-lookup"><span data-stu-id="50df8-111">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="50df8-112">**1 x** -bus SPI</span><span class="sxs-lookup"><span data-stu-id="50df8-112">**1x** - SPI bus</span></span>
* <span data-ttu-id="50df8-113">**1 x** -bus I2C</span><span class="sxs-lookup"><span data-stu-id="50df8-113">**1x** - I2C bus</span></span>
* <span data-ttu-id="50df8-114">**1 x** -pin de alimentación de 5 v</span><span class="sxs-lookup"><span data-stu-id="50df8-114">**1x** - 5V power pin</span></span>
* <span data-ttu-id="50df8-115">**1 x** : 3,3 v pin de energía</span><span class="sxs-lookup"><span data-stu-id="50df8-115">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="50df8-116">**2 x** -masa PIN</span><span class="sxs-lookup"><span data-stu-id="50df8-116">**2x** - Ground pins</span></span>

<span data-ttu-id="50df8-117">Los niveles de lógica de usos 3,3 v MinnowBoard Max en todas las patillas de E/S.</span><span class="sxs-lookup"><span data-stu-id="50df8-117">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="50df8-118">Además se almacenan en búfer todos los bolos por [TXS0104E](http://www.ti.com/product/txs0104e) shifters, a excepción de la tierra de energía y de PIN de nivel.</span><span class="sxs-lookup"><span data-stu-id="50df8-118">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="50df8-119">Estos shifters nivel se muestran como resultados de recopilador abierto con un **10K&#x2126; subida del electromagnético y la subida del está presente, independientemente de si la operación de E/S está establecida en entrada o salida.**</span><span class="sxs-lookup"><span data-stu-id="50df8-119">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="50df8-120">La naturaleza de recopilador de apertura de los medios shifters nivel es que el PIN pueden devolver ' 0 'fuertemente, pero solo débil de salida ' 1'.</span><span class="sxs-lookup"><span data-stu-id="50df8-120">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="50df8-121">Esto es importante tener en cuenta al conectar los dispositivos que dibujar actual de los bolos (por ejemplo, un LED).</span><span class="sxs-lookup"><span data-stu-id="50df8-121">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="50df8-122">Consulte la [ejemplo llamativa](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) para la forma correcta un LED MinnowBoard máxima de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="50df8-122">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="50df8-123">Pines GPIO</span><span class="sxs-lookup"><span data-stu-id="50df8-123">GPIO Pins</span></span>

<span data-ttu-id="50df8-124">Las clavijas GPIO siguientes son accesibles a través de API:</span><span class="sxs-lookup"><span data-stu-id="50df8-124">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="50df8-125">GPIO #</span><span class="sxs-lookup"><span data-stu-id="50df8-125">GPIO#</span></span> | <span data-ttu-id="50df8-126">Pin de encabezado</span><span class="sxs-lookup"><span data-stu-id="50df8-126">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="50df8-127">0</span><span class="sxs-lookup"><span data-stu-id="50df8-127">0</span></span>     | <span data-ttu-id="50df8-128">21</span><span class="sxs-lookup"><span data-stu-id="50df8-128">21</span></span>                 |
> | <span data-ttu-id="50df8-129">1</span><span class="sxs-lookup"><span data-stu-id="50df8-129">1</span></span>     | <span data-ttu-id="50df8-130">23</span><span class="sxs-lookup"><span data-stu-id="50df8-130">23</span></span>                 |
> | <span data-ttu-id="50df8-131">2</span><span class="sxs-lookup"><span data-stu-id="50df8-131">2</span></span>     | <span data-ttu-id="50df8-132">25</span><span class="sxs-lookup"><span data-stu-id="50df8-132">25</span></span>                 |
> | <span data-ttu-id="50df8-133">3</span><span class="sxs-lookup"><span data-stu-id="50df8-133">3</span></span>     | <span data-ttu-id="50df8-134">14</span><span class="sxs-lookup"><span data-stu-id="50df8-134">14</span></span>                 |
> | <span data-ttu-id="50df8-135">4</span><span class="sxs-lookup"><span data-stu-id="50df8-135">4</span></span>     | <span data-ttu-id="50df8-136">16</span><span class="sxs-lookup"><span data-stu-id="50df8-136">16</span></span>                 |
> | <span data-ttu-id="50df8-137">5</span><span class="sxs-lookup"><span data-stu-id="50df8-137">5</span></span>     | <span data-ttu-id="50df8-138">18</span><span class="sxs-lookup"><span data-stu-id="50df8-138">18</span></span>                 |
> | <span data-ttu-id="50df8-139">6</span><span class="sxs-lookup"><span data-stu-id="50df8-139">6</span></span>     | <span data-ttu-id="50df8-140">20</span><span class="sxs-lookup"><span data-stu-id="50df8-140">20</span></span>                 |
> | <span data-ttu-id="50df8-141">7</span><span class="sxs-lookup"><span data-stu-id="50df8-141">7</span></span>     | <span data-ttu-id="50df8-142">22</span><span class="sxs-lookup"><span data-stu-id="50df8-142">22</span></span>                 |
> | <span data-ttu-id="50df8-143">8</span><span class="sxs-lookup"><span data-stu-id="50df8-143">8</span></span>     | <span data-ttu-id="50df8-144">24</span><span class="sxs-lookup"><span data-stu-id="50df8-144">24</span></span>                 |
> | <span data-ttu-id="50df8-145">9</span><span class="sxs-lookup"><span data-stu-id="50df8-145">9</span></span>     | <span data-ttu-id="50df8-146">26</span><span class="sxs-lookup"><span data-stu-id="50df8-146">26</span></span>                 |

<span data-ttu-id="50df8-147">**Nota:** **GPIO 4** y **GPIO 5** se usan por el número máximo de MinnowBoard como anclajes de configuración de arranque en el BIOS.</span><span class="sxs-lookup"><span data-stu-id="50df8-147">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="50df8-148">Asegúrese de que los dispositivos conectados no controlar estos GPIO baja durante el arranque, ya que esto podría impedir que el MBM arranque.</span><span class="sxs-lookup"><span data-stu-id="50df8-148">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="50df8-149">Después de iniciarse la MBM más allá de la BIOS, normalmente se puede usar estos GPIO.</span><span class="sxs-lookup"><span data-stu-id="50df8-149">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="50df8-150">Ejemplo GPIO</span><span class="sxs-lookup"><span data-stu-id="50df8-150">GPIO Sample</span></span>

<span data-ttu-id="50df8-151">Por ejemplo, el siguiente código se abre **GPIO 5** como salida y escribe un digitales '**1**' out en el pin:</span><span class="sxs-lookup"><span data-stu-id="50df8-151">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="50df8-152">UART serie</span><span class="sxs-lookup"><span data-stu-id="50df8-152">Serial UART</span></span>

<span data-ttu-id="50df8-153">Hay dos UARTS serie en el MBM: **UART1** y **UART2**</span><span class="sxs-lookup"><span data-stu-id="50df8-153">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="50df8-154">**UART1** tiene la norma **UART1 TX** y **UART1 RX** señales de líneas, junto con el flujo de controlan **UART1 CTS** y **UART1 RTS**.</span><span class="sxs-lookup"><span data-stu-id="50df8-154">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="50df8-155">Anclar 6 - **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="50df8-155">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="50df8-156">Anclar 8 - **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="50df8-156">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="50df8-157">Anclar 10 - **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="50df8-157">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="50df8-158">Anclar 12 - **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="50df8-158">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="50df8-159">UART1 no funciona a partir de la compilación 10240.</span><span class="sxs-lookup"><span data-stu-id="50df8-159">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="50df8-160">Use UART2 o un convertidor de USB a serie.</span><span class="sxs-lookup"><span data-stu-id="50df8-160">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="50df8-161">**UART2** incluye solamente el **UART2 TX** y **UART2 RX** líneas.</span><span class="sxs-lookup"><span data-stu-id="50df8-161">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="50df8-162">Anclar 17 - **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="50df8-162">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="50df8-163">Anclar 19 - **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="50df8-163">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="50df8-164">UART2 no admite el control de flujo, para tener acceso a las siguientes propiedades de SerialDevice puede dar lugar a una excepción:</span><span class="sxs-lookup"><span data-stu-id="50df8-164">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="50df8-165">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="50df8-165">BreakSignalState</span></span>
 * <span data-ttu-id="50df8-166">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="50df8-166">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="50df8-167">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="50df8-167">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="50df8-168">Protocolo de enlace - SerialHandshake.None solo se admite</span><span class="sxs-lookup"><span data-stu-id="50df8-168">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="50df8-169">El ejemplo siguiente inicializa **UART2** y realiza una operación de escritura seguido por una lectura:</span><span class="sxs-lookup"><span data-stu-id="50df8-169">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="50df8-170">Tenga en cuenta que debe agregar la funcionalidad siguiente a la **Package.appxmanifest** archivo del proyecto UWP para ejecutar código UART serie:</span><span class="sxs-lookup"><span data-stu-id="50df8-170">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="50df8-171">Visual Studio 2017 tiene un problema conocido en el Diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la capacidad de serialcommunication.</span><span class="sxs-lookup"><span data-stu-id="50df8-171">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="50df8-172">Si su appxmanifest agrega la capacidad de serialcommunication, modificar su appxmanifest con el diseñador dañará su appxmanifest (el elemento secundario xml de dispositivo se perderán).</span><span class="sxs-lookup"><span data-stu-id="50df8-172">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="50df8-173">Puede solucionar este problema mediante la edición de mano el appxmanifest haciendo clic en su appxmanifest y seleccione Ver código en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="50df8-173">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="50df8-174">Bus i2c</span><span class="sxs-lookup"><span data-stu-id="50df8-174">I2C Bus</span></span>

<span data-ttu-id="50df8-175">Vamos a examinar el bus I2C disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="50df8-175">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="50df8-176">Información general de i2c</span><span class="sxs-lookup"><span data-stu-id="50df8-176">I2C Overview</span></span>

<span data-ttu-id="50df8-177">Hay un controlador I2C **I2C5** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**.</span><span class="sxs-lookup"><span data-stu-id="50df8-177">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="50df8-178">10K&#x2126; resistencias pull-up interno ya están presentes en estas líneas.</span><span class="sxs-lookup"><span data-stu-id="50df8-178">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="50df8-179">Anclar 15 - **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="50df8-179">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="50df8-180">Anclar 13 - **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="50df8-180">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="50df8-181">Ejemplo de i2c</span><span class="sxs-lookup"><span data-stu-id="50df8-181">I2C Sample</span></span>

<span data-ttu-id="50df8-182">El ejemplo siguiente inicializa **I2C5** y escribe datos en un dispositivo I2C con dirección **0 x 40**:</span><span class="sxs-lookup"><span data-stu-id="50df8-182">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="50df8-183">Problemas de i2c</span><span class="sxs-lookup"><span data-stu-id="50df8-183">I2C Issues</span></span>

<span data-ttu-id="50df8-184">El número máximo de MinnowBoard tiene un problema conocido con el bus I2C, lo que provoca problemas de comunicación con determinados dispositivos I2C.</span><span class="sxs-lookup"><span data-stu-id="50df8-184">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="50df8-185">Normalmente, un dispositivo I2C reconocerá su dirección durante una solicitud de bus.</span><span class="sxs-lookup"><span data-stu-id="50df8-185">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="50df8-186">Sin embargo, en determinadas condiciones esta confirmación no se propague hacia atrás por el nivel shifters a la MBM, y como resultado la CPU piensa que el dispositivo no ha respondido y cancela la transacción de bus.</span><span class="sxs-lookup"><span data-stu-id="50df8-186">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="50df8-187">El problema parece estar relacionado con la [TXS0104E](http://www.ti.com/product/txs0104e) shifters en las patillas de la E/S, que pueden desencadenar prematuramente debido a picos de voltaje de la línea de nivel.</span><span class="sxs-lookup"><span data-stu-id="50df8-187">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="50df8-188">La solución actual consiste en Insertar una resistencia 100 ohm en serie con la línea SCK I2C, lo que ayuda a suprimir los picos.</span><span class="sxs-lookup"><span data-stu-id="50df8-188">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="50df8-189">No todos los dispositivos se ven afectados, por lo que esta solución solo es necesario si tiene problemas para obtener una respuesta de bus.</span><span class="sxs-lookup"><span data-stu-id="50df8-189">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="50df8-190">Un dispositivo que se sabe que requieren esta solución alternativa es la HTU21D.</span><span class="sxs-lookup"><span data-stu-id="50df8-190">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="50df8-191">Bus SPI</span><span class="sxs-lookup"><span data-stu-id="50df8-191">SPI Bus</span></span>

<span data-ttu-id="50df8-192">Echemos un vistazo del bus SPI disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="50df8-192">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="50df8-193">Información general SPI</span><span class="sxs-lookup"><span data-stu-id="50df8-193">SPI Overview</span></span>

<span data-ttu-id="50df8-194">Hay un controlador SPI **SPI0** disponible en el MBM:</span><span class="sxs-lookup"><span data-stu-id="50df8-194">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="50df8-195">Anclar 9 - **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="50df8-195">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="50df8-196">Anclar 7 - **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="50df8-196">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="50df8-197">Anclar 11 - **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="50df8-197">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="50df8-198">Anclar 5 - **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="50df8-198">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="50df8-199">Ejemplo SPI</span><span class="sxs-lookup"><span data-stu-id="50df8-199">SPI Sample</span></span>

<span data-ttu-id="50df8-200">Un ejemplo sobre cómo realizar un IRP de escritura en el bus **SPI0** se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="50df8-200">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

