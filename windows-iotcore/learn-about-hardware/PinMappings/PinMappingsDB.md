---
title: Asignaciones de Dragonboard PIN
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la funcionalidad de las asignaciones de PIN para Dragonboard.
keywords: asignaciones de Windows IOT, Dragonboard, PIN, GPIO
ms.openlocfilehash: 170b14ce640fed33754f90bd4df188f4629f04c2
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917962"
---
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="7313a-104">Asignaciones de Dragonboard PIN</span><span class="sxs-lookup"><span data-stu-id="7313a-104">Dragonboard Pin Mappings</span></span>

![Encabezado Dragonboard PIN](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="7313a-106">Las interfaces de hardware de Dragonboard se exponen a través del encabezado 40-PIN en el panel.</span><span class="sxs-lookup"><span data-stu-id="7313a-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="7313a-107">La funcionalidad incluye:</span><span class="sxs-lookup"><span data-stu-id="7313a-107">Functionality includes:</span></span>

* <span data-ttu-id="7313a-108">PIN de **11x** -GPIO</span><span class="sxs-lookup"><span data-stu-id="7313a-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="7313a-109">**2x** -UART en serie</span><span class="sxs-lookup"><span data-stu-id="7313a-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="7313a-110">Bus **1x** -SPI</span><span class="sxs-lookup"><span data-stu-id="7313a-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="7313a-111">Bus **2x** -I2C</span><span class="sxs-lookup"><span data-stu-id="7313a-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="7313a-112">PIN de alimentación de **1x** -5V</span><span class="sxs-lookup"><span data-stu-id="7313a-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="7313a-113">**1x** -1,8 v Power PIN</span><span class="sxs-lookup"><span data-stu-id="7313a-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="7313a-114">pines de la base **4x**</span><span class="sxs-lookup"><span data-stu-id="7313a-114">**4x** - Ground pins</span></span>

<span data-ttu-id="7313a-115">Tenga en cuenta que Dragonboard usa niveles de lógica de 1,8 V en todos los pin de e/s.</span><span class="sxs-lookup"><span data-stu-id="7313a-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="7313a-116">PIN de GPIO</span><span class="sxs-lookup"><span data-stu-id="7313a-116">GPIO Pins</span></span>

<span data-ttu-id="7313a-117">Echemos un vistazo al GPIO disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7313a-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="7313a-118">Tabla de PIN de GPIO</span><span class="sxs-lookup"><span data-stu-id="7313a-118">GPIO Pin Table</span></span>

<span data-ttu-id="7313a-119">Se puede acceder a los siguientes PIN de GPIO a través de las API:</span><span class="sxs-lookup"><span data-stu-id="7313a-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="7313a-120">GPIO #</span><span class="sxs-lookup"><span data-stu-id="7313a-120">GPIO#</span></span> | <span data-ttu-id="7313a-121">PIN de encabezado</span><span class="sxs-lookup"><span data-stu-id="7313a-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="7313a-122">36</span><span class="sxs-lookup"><span data-stu-id="7313a-122">36</span></span>    | <span data-ttu-id="7313a-123">23</span><span class="sxs-lookup"><span data-stu-id="7313a-123">23</span></span>                 |
> | <span data-ttu-id="7313a-124">12</span><span class="sxs-lookup"><span data-stu-id="7313a-124">12</span></span>    | <span data-ttu-id="7313a-125">24</span><span class="sxs-lookup"><span data-stu-id="7313a-125">24</span></span>                 |
> | <span data-ttu-id="7313a-126">13</span><span class="sxs-lookup"><span data-stu-id="7313a-126">13</span></span>    | <span data-ttu-id="7313a-127">25</span><span class="sxs-lookup"><span data-stu-id="7313a-127">25</span></span>                 |
> | <span data-ttu-id="7313a-128">69</span><span class="sxs-lookup"><span data-stu-id="7313a-128">69</span></span>    | <span data-ttu-id="7313a-129">26</span><span class="sxs-lookup"><span data-stu-id="7313a-129">26</span></span>                 |
> | <span data-ttu-id="7313a-130">115</span><span class="sxs-lookup"><span data-stu-id="7313a-130">115</span></span>   | <span data-ttu-id="7313a-131">27</span><span class="sxs-lookup"><span data-stu-id="7313a-131">27</span></span>                 |
> | <span data-ttu-id="7313a-132">24</span><span class="sxs-lookup"><span data-stu-id="7313a-132">24</span></span>    | <span data-ttu-id="7313a-133">29</span><span class="sxs-lookup"><span data-stu-id="7313a-133">29</span></span>                 |
> | <span data-ttu-id="7313a-134">25</span><span class="sxs-lookup"><span data-stu-id="7313a-134">25</span></span>    | <span data-ttu-id="7313a-135">30</span><span class="sxs-lookup"><span data-stu-id="7313a-135">30</span></span>                 |
> | <span data-ttu-id="7313a-136">35</span><span class="sxs-lookup"><span data-stu-id="7313a-136">35</span></span>    | <span data-ttu-id="7313a-137">31</span><span class="sxs-lookup"><span data-stu-id="7313a-137">31</span></span>                 |
> | <span data-ttu-id="7313a-138">34</span><span class="sxs-lookup"><span data-stu-id="7313a-138">34</span></span>    | <span data-ttu-id="7313a-139">32</span><span class="sxs-lookup"><span data-stu-id="7313a-139">32</span></span>                 |
> | <span data-ttu-id="7313a-140">28</span><span class="sxs-lookup"><span data-stu-id="7313a-140">28</span></span>    | <span data-ttu-id="7313a-141">33</span><span class="sxs-lookup"><span data-stu-id="7313a-141">33</span></span>                 |
> | <span data-ttu-id="7313a-142">33</span><span class="sxs-lookup"><span data-stu-id="7313a-142">33</span></span>    | <span data-ttu-id="7313a-143">34</span><span class="sxs-lookup"><span data-stu-id="7313a-143">34</span></span>                 |
> | <span data-ttu-id="7313a-144">21</span><span class="sxs-lookup"><span data-stu-id="7313a-144">21</span></span>    | <span data-ttu-id="7313a-145">LED de usuario 1</span><span class="sxs-lookup"><span data-stu-id="7313a-145">User LED 1</span></span>         | 
> | <span data-ttu-id="7313a-146">120</span><span class="sxs-lookup"><span data-stu-id="7313a-146">120</span></span>   | <span data-ttu-id="7313a-147">LED de usuario 2</span><span class="sxs-lookup"><span data-stu-id="7313a-147">User LED 2</span></span>         |         


<span data-ttu-id="7313a-148">Como ejemplo, el código siguiente abre **GPIO 35** como salida y escribe un '**1**' digital en el PIN:</span><span class="sxs-lookup"><span data-stu-id="7313a-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="7313a-149">Problemas de GPIO</span><span class="sxs-lookup"><span data-stu-id="7313a-149">GPIO Issues</span></span>

* <span data-ttu-id="7313a-150">La salida no funciona en GPIO 24.</span><span class="sxs-lookup"><span data-stu-id="7313a-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="7313a-151">La entrada funciona bien.</span><span class="sxs-lookup"><span data-stu-id="7313a-151">Input works fine.</span></span>
* <span data-ttu-id="7313a-152">Los PIN se configuran como InputPullDown en el arranque, pero cambiarán a la entrada (flotante) la primera vez que se abran.</span><span class="sxs-lookup"><span data-stu-id="7313a-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="7313a-153">Los PIN no revierten a su estado predeterminado al cerrarse</span><span class="sxs-lookup"><span data-stu-id="7313a-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="7313a-154">Se pueden producir interrupciones falsas cuando las interrupciones están habilitadas en varios PIN</span><span class="sxs-lookup"><span data-stu-id="7313a-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="7313a-155">UART en serie</span><span class="sxs-lookup"><span data-stu-id="7313a-155">Serial UART</span></span>

<span data-ttu-id="7313a-156">Hay dos UART en serie disponibles en Dragonboard **UART0** y **UART1**</span><span class="sxs-lookup"><span data-stu-id="7313a-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="7313a-157">**UART0** tiene las líneas de RX estándar **UART0 TX** y **UART0** , junto con las señales de control de flujo **UART0 CTS** y **UART0 RTS**.</span><span class="sxs-lookup"><span data-stu-id="7313a-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="7313a-158">Pin 5- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="7313a-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="7313a-159">PIN 7- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="7313a-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="7313a-160">PIN 3- **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="7313a-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="7313a-161">PIN 9- **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="7313a-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="7313a-162">**UART1** incluye solo las líneas RX **UART1 TX** y **UART1** .</span><span class="sxs-lookup"><span data-stu-id="7313a-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="7313a-163">PIN 11- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="7313a-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="7313a-164">PIN 13- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="7313a-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="7313a-165">En el ejemplo siguiente se inicializa **UART1** y se realiza una escritura seguida de una lectura:</span><span class="sxs-lookup"><span data-stu-id="7313a-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="7313a-166">Visual Studio 2017 tiene un error conocido en el diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la funcionalidad serialcommunication.</span><span class="sxs-lookup"><span data-stu-id="7313a-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="7313a-167">Si el appxmanifest agrega la funcionalidad serialcommunication, la modificación de appxmanifest con el diseñador dañará el appxmanifest (se perderá el elemento secundario XML del dispositivo).</span><span class="sxs-lookup"><span data-stu-id="7313a-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="7313a-168">Puede solucionar este problema de forma manual editaba el appxmanifest; para ello, haga clic con el botón derecho en el appxmanifest y seleccione Ver código en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="7313a-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="7313a-169">Debe agregar la siguiente funcionalidad al archivo **Package. appxmanifest** en el proyecto de UWP para ejecutar el código de UART en serie:</span><span class="sxs-lookup"><span data-stu-id="7313a-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="7313a-170">Bus I2C</span><span class="sxs-lookup"><span data-stu-id="7313a-170">I2C Bus</span></span>

<span data-ttu-id="7313a-171">Echemos un vistazo a los buses I2C disponibles en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7313a-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="7313a-172">Clavijas I2C</span><span class="sxs-lookup"><span data-stu-id="7313a-172">I2C Pins</span></span>

<span data-ttu-id="7313a-173">**I2C0** expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**</span><span class="sxs-lookup"><span data-stu-id="7313a-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="7313a-174">PIN 17- **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="7313a-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="7313a-175">PIN 15- **I2C0 SCL**</span><span class="sxs-lookup"><span data-stu-id="7313a-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="7313a-176">**I2C1** expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**</span><span class="sxs-lookup"><span data-stu-id="7313a-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="7313a-177">Patilla 21- **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="7313a-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="7313a-178">Pin 19- **I2C1 SCL**</span><span class="sxs-lookup"><span data-stu-id="7313a-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="7313a-179">Ejemplo de I2C</span><span class="sxs-lookup"><span data-stu-id="7313a-179">I2C Sample</span></span>

<span data-ttu-id="7313a-180">En el ejemplo siguiente se inicializa **I2C0** y se escriben datos en un dispositivo I2C con la dirección **0x40**:</span><span class="sxs-lookup"><span data-stu-id="7313a-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="7313a-181">Bus SPI</span><span class="sxs-lookup"><span data-stu-id="7313a-181">SPI Bus</span></span>

<span data-ttu-id="7313a-182">Echemos un vistazo al bus SPI disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7313a-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="7313a-183">Clavijas SPI</span><span class="sxs-lookup"><span data-stu-id="7313a-183">SPI Pins</span></span>

<span data-ttu-id="7313a-184">Hay un **SPI0** de controlador de SPI disponible en la base de</span><span class="sxs-lookup"><span data-stu-id="7313a-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="7313a-185">PIN de 10 a **SPI0**</span><span class="sxs-lookup"><span data-stu-id="7313a-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="7313a-186">PIN 14- **SPI0 Mosi**</span><span class="sxs-lookup"><span data-stu-id="7313a-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="7313a-187">Pin 8- **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="7313a-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="7313a-188">Pin 12- **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="7313a-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="7313a-189">Problemas con SPI</span><span class="sxs-lookup"><span data-stu-id="7313a-189">SPI Issues</span></span>

<span data-ttu-id="7313a-190">El reloj SPI se fija a 4,8 MHz.</span><span class="sxs-lookup"><span data-stu-id="7313a-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="7313a-191">Se omitirá el reloj SPI solicitado.</span><span class="sxs-lookup"><span data-stu-id="7313a-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="7313a-192">Ejemplo de SPI</span><span class="sxs-lookup"><span data-stu-id="7313a-192">SPI Sample</span></span>

<span data-ttu-id="7313a-193">A continuación se muestra un ejemplo de cómo realizar una escritura SPI en el bus **SPI0** :</span><span class="sxs-lookup"><span data-stu-id="7313a-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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
