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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="02e6e-104">MinnowBoard asignaciones de PIN máx.</span><span class="sxs-lookup"><span data-stu-id="02e6e-104">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="02e6e-105">Para comparar esta asignación de pin con las versiones más recientes de Minnowboard, visite la documentación [aquí](https://minnowboard.org/minnowboard-turbot/documentation).</span><span class="sxs-lookup"><span data-stu-id="02e6e-105">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="02e6e-106">Información general</span><span class="sxs-lookup"><span data-stu-id="02e6e-106">Overview</span></span>

![MinnowBoard encabezado Max PIN](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="02e6e-108">Las interfaces de hardware para el máximo de MinnowBoard se exponen a través del encabezado de 26 pines **JP1** en el panel.</span><span class="sxs-lookup"><span data-stu-id="02e6e-108">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="02e6e-109">La funcionalidad incluye:</span><span class="sxs-lookup"><span data-stu-id="02e6e-109">Functionality includes:</span></span>

* <span data-ttu-id="02e6e-110">PIN de **10 veces** -GPIO</span><span class="sxs-lookup"><span data-stu-id="02e6e-110">**10x** - GPIO pins</span></span>
* <span data-ttu-id="02e6e-111">**2x** -UART en serie</span><span class="sxs-lookup"><span data-stu-id="02e6e-111">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="02e6e-112">Bus **1x** -SPI</span><span class="sxs-lookup"><span data-stu-id="02e6e-112">**1x** - SPI bus</span></span>
* <span data-ttu-id="02e6e-113">Bus **1x** -I2C</span><span class="sxs-lookup"><span data-stu-id="02e6e-113">**1x** - I2C bus</span></span>
* <span data-ttu-id="02e6e-114">PIN de alimentación de **1x** -5V</span><span class="sxs-lookup"><span data-stu-id="02e6e-114">**1x** - 5V power pin</span></span>
* <span data-ttu-id="02e6e-115">**1x** -3,3 v de alimentación</span><span class="sxs-lookup"><span data-stu-id="02e6e-115">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="02e6e-116">pines de **doble** fondo</span><span class="sxs-lookup"><span data-stu-id="02e6e-116">**2x** - Ground pins</span></span>

<span data-ttu-id="02e6e-117">MinnowBoard Max usa los niveles de lógica de 3,3 V en todos los pin de e/s.</span><span class="sxs-lookup"><span data-stu-id="02e6e-117">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="02e6e-118">Además, todos los PIN se almacenan en búfer mediante los desplazadores de nivel de [TXS0104E](http://www.ti.com/product/txs0104e) , con la excepción de las clavijas de alimentación y de alimentación.</span><span class="sxs-lookup"><span data-stu-id="02e6e-118">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="02e6e-119">Estos desplazadores de nivel aparecen como salidas del recopilador abierto con una **extracción resistente de&#x2126; 10 000 y la extracción está presente independientemente de si la e/s está establecida en entrada o salida.**</span><span class="sxs-lookup"><span data-stu-id="02e6e-119">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="02e6e-120">La naturaleza de Open-Collector de los desplazamientos de nivel significa que los pin pueden generar un "0" firmemente, pero solo se genera de forma débil un "1".</span><span class="sxs-lookup"><span data-stu-id="02e6e-120">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="02e6e-121">Es importante tener en cuenta cuando se conectan los dispositivos que dibujan el actual a partir de las clavijas (por ejemplo, un LED).</span><span class="sxs-lookup"><span data-stu-id="02e6e-121">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="02e6e-122">Vea el [ejemplo de parpadeo](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) para obtener la manera correcta de interactuar con el LED MinnowBoard Max.</span><span class="sxs-lookup"><span data-stu-id="02e6e-122">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="02e6e-123">PIN de GPIO</span><span class="sxs-lookup"><span data-stu-id="02e6e-123">GPIO Pins</span></span>

<span data-ttu-id="02e6e-124">Se puede acceder a los siguientes PIN de GPIO a través de las API:</span><span class="sxs-lookup"><span data-stu-id="02e6e-124">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="02e6e-125">GPIO #</span><span class="sxs-lookup"><span data-stu-id="02e6e-125">GPIO#</span></span> | <span data-ttu-id="02e6e-126">PIN de encabezado</span><span class="sxs-lookup"><span data-stu-id="02e6e-126">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="02e6e-127">0</span><span class="sxs-lookup"><span data-stu-id="02e6e-127">0</span></span>     | <span data-ttu-id="02e6e-128">21</span><span class="sxs-lookup"><span data-stu-id="02e6e-128">21</span></span>                 |
> | <span data-ttu-id="02e6e-129">1</span><span class="sxs-lookup"><span data-stu-id="02e6e-129">1</span></span>     | <span data-ttu-id="02e6e-130">23</span><span class="sxs-lookup"><span data-stu-id="02e6e-130">23</span></span>                 |
> | <span data-ttu-id="02e6e-131">2</span><span class="sxs-lookup"><span data-stu-id="02e6e-131">2</span></span>     | <span data-ttu-id="02e6e-132">25</span><span class="sxs-lookup"><span data-stu-id="02e6e-132">25</span></span>                 |
> | <span data-ttu-id="02e6e-133">3</span><span class="sxs-lookup"><span data-stu-id="02e6e-133">3</span></span>     | <span data-ttu-id="02e6e-134">14</span><span class="sxs-lookup"><span data-stu-id="02e6e-134">14</span></span>                 |
> | <span data-ttu-id="02e6e-135">4</span><span class="sxs-lookup"><span data-stu-id="02e6e-135">4</span></span>     | <span data-ttu-id="02e6e-136">16</span><span class="sxs-lookup"><span data-stu-id="02e6e-136">16</span></span>                 |
> | <span data-ttu-id="02e6e-137">5</span><span class="sxs-lookup"><span data-stu-id="02e6e-137">5</span></span>     | <span data-ttu-id="02e6e-138">18</span><span class="sxs-lookup"><span data-stu-id="02e6e-138">18</span></span>                 |
> | <span data-ttu-id="02e6e-139">6</span><span class="sxs-lookup"><span data-stu-id="02e6e-139">6</span></span>     | <span data-ttu-id="02e6e-140">20</span><span class="sxs-lookup"><span data-stu-id="02e6e-140">20</span></span>                 |
> | <span data-ttu-id="02e6e-141">7</span><span class="sxs-lookup"><span data-stu-id="02e6e-141">7</span></span>     | <span data-ttu-id="02e6e-142">22</span><span class="sxs-lookup"><span data-stu-id="02e6e-142">22</span></span>                 |
> | <span data-ttu-id="02e6e-143">8</span><span class="sxs-lookup"><span data-stu-id="02e6e-143">8</span></span>     | <span data-ttu-id="02e6e-144">24</span><span class="sxs-lookup"><span data-stu-id="02e6e-144">24</span></span>                 |
> | <span data-ttu-id="02e6e-145">9</span><span class="sxs-lookup"><span data-stu-id="02e6e-145">9</span></span>     | <span data-ttu-id="02e6e-146">26</span><span class="sxs-lookup"><span data-stu-id="02e6e-146">26</span></span>                 |

<span data-ttu-id="02e6e-147">**Nota:** Los pin de configuración Max **4** y **GPIO 5** se usan en las clavijas de configuración MinnowBoard Max as bootstrap del BIOS.</span><span class="sxs-lookup"><span data-stu-id="02e6e-147">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="02e6e-148">Asegúrese de que los dispositivos conectados no controlan el nivel de GPIO bajo durante el arranque, ya que esto podría impedir el arranque de MBM.</span><span class="sxs-lookup"><span data-stu-id="02e6e-148">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="02e6e-149">Después de que MBM haya arrancado más allá del BIOS, estos GPIO se pueden usar con normalidad.</span><span class="sxs-lookup"><span data-stu-id="02e6e-149">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="02e6e-150">Ejemplo de GPIO</span><span class="sxs-lookup"><span data-stu-id="02e6e-150">GPIO Sample</span></span>

<span data-ttu-id="02e6e-151">Como ejemplo, el código siguiente abre **GPIO 5** como salida y escribe un '**1**' digital en el PIN:</span><span class="sxs-lookup"><span data-stu-id="02e6e-151">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="02e6e-152">UART en serie</span><span class="sxs-lookup"><span data-stu-id="02e6e-152">Serial UART</span></span>

<span data-ttu-id="02e6e-153">Hay dos UART en serie disponibles en MBM: **UART1** y **UART2**</span><span class="sxs-lookup"><span data-stu-id="02e6e-153">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="02e6e-154">**UART1** tiene las líneas de RX estándar **UART1 TX** y **UART1** , junto con las señales de control de flujo **UART1 CTS** y **UART1 RTS**.</span><span class="sxs-lookup"><span data-stu-id="02e6e-154">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="02e6e-155">Patilla 6: **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="02e6e-155">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="02e6e-156">Pin 8- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="02e6e-156">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="02e6e-157">PIN 10- **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="02e6e-157">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="02e6e-158">Pin 12- **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="02e6e-158">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="02e6e-159">UART1 no funciona a partir de la compilación 10240.</span><span class="sxs-lookup"><span data-stu-id="02e6e-159">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="02e6e-160">Use UART2 o un convertidor USB-serie.</span><span class="sxs-lookup"><span data-stu-id="02e6e-160">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="02e6e-161">**UART2** incluye solo las líneas RX **UART2 TX** y **UART2** .</span><span class="sxs-lookup"><span data-stu-id="02e6e-161">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="02e6e-162">PIN 17- **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="02e6e-162">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="02e6e-163">Pin 19- **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="02e6e-163">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="02e6e-164">UART2 no admite el control de flujo, por lo que el acceso a las siguientes propiedades de SerialDevice puede dar lugar a que se produzca una excepción:</span><span class="sxs-lookup"><span data-stu-id="02e6e-164">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="02e6e-165">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="02e6e-165">BreakSignalState</span></span>
 * <span data-ttu-id="02e6e-166">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="02e6e-166">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="02e6e-167">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="02e6e-167">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="02e6e-168">Solo se admite el protocolo de enlace SerialHandshake. None</span><span class="sxs-lookup"><span data-stu-id="02e6e-168">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="02e6e-169">En el ejemplo siguiente se inicializa **UART2** y se realiza una escritura seguida de una lectura:</span><span class="sxs-lookup"><span data-stu-id="02e6e-169">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="02e6e-170">Tenga en cuenta que debe agregar la siguiente funcionalidad al archivo **Package. appxmanifest** en el proyecto de UWP para ejecutar el código UART en serie:</span><span class="sxs-lookup"><span data-stu-id="02e6e-170">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="02e6e-171">Visual Studio 2017 tiene un error conocido en el diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la funcionalidad serialcommunication.</span><span class="sxs-lookup"><span data-stu-id="02e6e-171">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="02e6e-172">Si el appxmanifest agrega la funcionalidad serialcommunication, la modificación de appxmanifest con el diseñador dañará el appxmanifest (se perderá el elemento secundario XML del dispositivo).</span><span class="sxs-lookup"><span data-stu-id="02e6e-172">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="02e6e-173">Puede solucionar este problema de forma manual editaba el appxmanifest; para ello, haga clic con el botón derecho en el appxmanifest y seleccione Ver código en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="02e6e-173">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="02e6e-174">Bus I2C</span><span class="sxs-lookup"><span data-stu-id="02e6e-174">I2C Bus</span></span>

<span data-ttu-id="02e6e-175">Echemos un vistazo al bus I2C disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="02e6e-175">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="02e6e-176">Información general de I2C</span><span class="sxs-lookup"><span data-stu-id="02e6e-176">I2C Overview</span></span>

<span data-ttu-id="02e6e-177">Hay un **I2C5** de controlador i2c expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**.</span><span class="sxs-lookup"><span data-stu-id="02e6e-177">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="02e6e-178">10&#x2126; 000 resistencias internas de extracción ya están presentes en estas líneas.</span><span class="sxs-lookup"><span data-stu-id="02e6e-178">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="02e6e-179">PIN 15- **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="02e6e-179">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="02e6e-180">PIN 13- **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="02e6e-180">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="02e6e-181">Ejemplo de I2C</span><span class="sxs-lookup"><span data-stu-id="02e6e-181">I2C Sample</span></span>

<span data-ttu-id="02e6e-182">En el ejemplo siguiente se inicializa **I2C5** y se escriben datos en un dispositivo I2C con la dirección **0x40**:</span><span class="sxs-lookup"><span data-stu-id="02e6e-182">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="02e6e-183">Problemas de I2C</span><span class="sxs-lookup"><span data-stu-id="02e6e-183">I2C Issues</span></span>

<span data-ttu-id="02e6e-184">MinnowBoard Max tiene un problema conocido con el bus I2C que causa problemas de comunicación con determinados dispositivos I2C.</span><span class="sxs-lookup"><span data-stu-id="02e6e-184">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="02e6e-185">Normalmente, un dispositivo I2C confirma su dirección durante una solicitud de bus.</span><span class="sxs-lookup"><span data-stu-id="02e6e-185">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="02e6e-186">Sin embargo, en determinadas condiciones, este reconocimiento no puede propagarse de nuevo a través de los desplazamientos de nivel a MBM y, como resultado, la CPU considera que el dispositivo no respondió y cancela la transacción de bus.</span><span class="sxs-lookup"><span data-stu-id="02e6e-186">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="02e6e-187">El problema parece estar relacionado con los desplazadores de nivel de [TXS0104E](http://www.ti.com/product/txs0104e) en los pines de e/s, que pueden desencadenarse prematuramente debido a picos de tensión en la línea.</span><span class="sxs-lookup"><span data-stu-id="02e6e-187">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="02e6e-188">La solución actual es insertar una resistencia de 100 Ohm en serie con la línea I2C SCK, que ayuda a suprimir los picos.</span><span class="sxs-lookup"><span data-stu-id="02e6e-188">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="02e6e-189">No todos los dispositivos se ven afectados, por lo que esta solución solo es necesaria si tiene problemas para obtener una respuesta de bus.</span><span class="sxs-lookup"><span data-stu-id="02e6e-189">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="02e6e-190">Un dispositivo que se sabe que requiere esta solución es el HTU21D.</span><span class="sxs-lookup"><span data-stu-id="02e6e-190">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="02e6e-191">Bus SPI</span><span class="sxs-lookup"><span data-stu-id="02e6e-191">SPI Bus</span></span>

<span data-ttu-id="02e6e-192">Echemos un vistazo al bus SPI disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="02e6e-192">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="02e6e-193">Información general sobre SPI</span><span class="sxs-lookup"><span data-stu-id="02e6e-193">SPI Overview</span></span>

<span data-ttu-id="02e6e-194">Hay un **SPI0** de controlador de SPI disponible en MBM:</span><span class="sxs-lookup"><span data-stu-id="02e6e-194">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="02e6e-195">PIN 9- **SPI0 Mosi**</span><span class="sxs-lookup"><span data-stu-id="02e6e-195">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="02e6e-196">PIN 7: **SPI0**</span><span class="sxs-lookup"><span data-stu-id="02e6e-196">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="02e6e-197">PIN 11- **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="02e6e-197">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="02e6e-198">Pin 5- **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="02e6e-198">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="02e6e-199">Ejemplo de SPI</span><span class="sxs-lookup"><span data-stu-id="02e6e-199">SPI Sample</span></span>

<span data-ttu-id="02e6e-200">A continuación se muestra un ejemplo de cómo realizar una escritura SPI en el bus **SPI0** :</span><span class="sxs-lookup"><span data-stu-id="02e6e-200">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

