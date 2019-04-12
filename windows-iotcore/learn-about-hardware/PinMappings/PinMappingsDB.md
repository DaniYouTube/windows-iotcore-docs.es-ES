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
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="19f0f-104">Asignaciones de Dragonboard Pin</span><span class="sxs-lookup"><span data-stu-id="19f0f-104">Dragonboard Pin Mappings</span></span>

![Encabezado Dragonboard Pin](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="19f0f-106">Interfaces de hardware para el Dragonboard se exponen a través del encabezado de 40-pin en el panel.</span><span class="sxs-lookup"><span data-stu-id="19f0f-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="19f0f-107">La funcionalidad incluye:</span><span class="sxs-lookup"><span data-stu-id="19f0f-107">Functionality includes:</span></span>

* <span data-ttu-id="19f0f-108">**x 11** -pines GPIO</span><span class="sxs-lookup"><span data-stu-id="19f0f-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="19f0f-109">**2 x** -UARTs serie</span><span class="sxs-lookup"><span data-stu-id="19f0f-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="19f0f-110">**1 x** -bus SPI</span><span class="sxs-lookup"><span data-stu-id="19f0f-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="19f0f-111">**2 x** -bus I2C</span><span class="sxs-lookup"><span data-stu-id="19f0f-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="19f0f-112">**1 x** -pin de alimentación de 5 v</span><span class="sxs-lookup"><span data-stu-id="19f0f-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="19f0f-113">**1 x** : 1,8 pin de energía</span><span class="sxs-lookup"><span data-stu-id="19f0f-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="19f0f-114">**4 x** -masa PIN</span><span class="sxs-lookup"><span data-stu-id="19f0f-114">**4x** - Ground pins</span></span>

<span data-ttu-id="19f0f-115">Tenga en cuenta que el Dragonboard usa 1,8 niveles de lógica en todas las patillas de E/S.</span><span class="sxs-lookup"><span data-stu-id="19f0f-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="19f0f-116">Pines GPIO</span><span class="sxs-lookup"><span data-stu-id="19f0f-116">GPIO Pins</span></span>

<span data-ttu-id="19f0f-117">Echemos un vistazo a la GPIO disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="19f0f-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="19f0f-118">Tabla GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="19f0f-118">GPIO Pin Table</span></span>

<span data-ttu-id="19f0f-119">Las clavijas GPIO siguientes son accesibles a través de API:</span><span class="sxs-lookup"><span data-stu-id="19f0f-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="19f0f-120">GPIO #</span><span class="sxs-lookup"><span data-stu-id="19f0f-120">GPIO#</span></span> | <span data-ttu-id="19f0f-121">Pin de encabezado</span><span class="sxs-lookup"><span data-stu-id="19f0f-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="19f0f-122">36</span><span class="sxs-lookup"><span data-stu-id="19f0f-122">36</span></span>    | <span data-ttu-id="19f0f-123">23</span><span class="sxs-lookup"><span data-stu-id="19f0f-123">23</span></span>                 |
> | <span data-ttu-id="19f0f-124">12</span><span class="sxs-lookup"><span data-stu-id="19f0f-124">12</span></span>    | <span data-ttu-id="19f0f-125">24</span><span class="sxs-lookup"><span data-stu-id="19f0f-125">24</span></span>                 |
> | <span data-ttu-id="19f0f-126">13</span><span class="sxs-lookup"><span data-stu-id="19f0f-126">13</span></span>    | <span data-ttu-id="19f0f-127">25</span><span class="sxs-lookup"><span data-stu-id="19f0f-127">25</span></span>                 |
> | <span data-ttu-id="19f0f-128">69</span><span class="sxs-lookup"><span data-stu-id="19f0f-128">69</span></span>    | <span data-ttu-id="19f0f-129">26</span><span class="sxs-lookup"><span data-stu-id="19f0f-129">26</span></span>                 |
> | <span data-ttu-id="19f0f-130">115</span><span class="sxs-lookup"><span data-stu-id="19f0f-130">115</span></span>   | <span data-ttu-id="19f0f-131">27</span><span class="sxs-lookup"><span data-stu-id="19f0f-131">27</span></span>                 |
> | <span data-ttu-id="19f0f-132">24</span><span class="sxs-lookup"><span data-stu-id="19f0f-132">24</span></span>    | <span data-ttu-id="19f0f-133">29</span><span class="sxs-lookup"><span data-stu-id="19f0f-133">29</span></span>                 |
> | <span data-ttu-id="19f0f-134">25</span><span class="sxs-lookup"><span data-stu-id="19f0f-134">25</span></span>    | <span data-ttu-id="19f0f-135">30</span><span class="sxs-lookup"><span data-stu-id="19f0f-135">30</span></span>                 |
> | <span data-ttu-id="19f0f-136">35</span><span class="sxs-lookup"><span data-stu-id="19f0f-136">35</span></span>    | <span data-ttu-id="19f0f-137">31</span><span class="sxs-lookup"><span data-stu-id="19f0f-137">31</span></span>                 |
> | <span data-ttu-id="19f0f-138">34</span><span class="sxs-lookup"><span data-stu-id="19f0f-138">34</span></span>    | <span data-ttu-id="19f0f-139">32</span><span class="sxs-lookup"><span data-stu-id="19f0f-139">32</span></span>                 |
> | <span data-ttu-id="19f0f-140">28</span><span class="sxs-lookup"><span data-stu-id="19f0f-140">28</span></span>    | <span data-ttu-id="19f0f-141">33</span><span class="sxs-lookup"><span data-stu-id="19f0f-141">33</span></span>                 |
> | <span data-ttu-id="19f0f-142">33</span><span class="sxs-lookup"><span data-stu-id="19f0f-142">33</span></span>    | <span data-ttu-id="19f0f-143">34</span><span class="sxs-lookup"><span data-stu-id="19f0f-143">34</span></span>                 |
> | <span data-ttu-id="19f0f-144">21</span><span class="sxs-lookup"><span data-stu-id="19f0f-144">21</span></span>    | <span data-ttu-id="19f0f-145">1 de LED de usuario</span><span class="sxs-lookup"><span data-stu-id="19f0f-145">User LED 1</span></span>         | 
> | <span data-ttu-id="19f0f-146">120</span><span class="sxs-lookup"><span data-stu-id="19f0f-146">120</span></span>   | <span data-ttu-id="19f0f-147">2 de LED de usuario</span><span class="sxs-lookup"><span data-stu-id="19f0f-147">User LED 2</span></span>         |         


<span data-ttu-id="19f0f-148">Por ejemplo, el siguiente código se abre **GPIO 35** como salida y escribe un digitales '**1**' out en el pin:</span><span class="sxs-lookup"><span data-stu-id="19f0f-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="19f0f-149">Problemas GPIO</span><span class="sxs-lookup"><span data-stu-id="19f0f-149">GPIO Issues</span></span>

* <span data-ttu-id="19f0f-150">Salida no funciona en GPIO 24.</span><span class="sxs-lookup"><span data-stu-id="19f0f-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="19f0f-151">Entrada funciona bien.</span><span class="sxs-lookup"><span data-stu-id="19f0f-151">Input works fine.</span></span>
* <span data-ttu-id="19f0f-152">PIN se configuran como InputPullDown durante el arranque, pero cambiará a la entrada (flotante) la primera vez que se abren.</span><span class="sxs-lookup"><span data-stu-id="19f0f-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="19f0f-153">Los PIN no volverá a su estado predeterminado al cerrar</span><span class="sxs-lookup"><span data-stu-id="19f0f-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="19f0f-154">Interrupciones falsas pueden verse cuando están habilitadas las interrupciones en varios PIN</span><span class="sxs-lookup"><span data-stu-id="19f0f-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="19f0f-155">UART serie</span><span class="sxs-lookup"><span data-stu-id="19f0f-155">Serial UART</span></span>

<span data-ttu-id="19f0f-156">Hay dos UARTS serie en el Dragonboard **UART0** y **UART1**</span><span class="sxs-lookup"><span data-stu-id="19f0f-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="19f0f-157">**UART0** tiene la norma **UART0 TX** y **UART0 RX** señales de líneas, junto con el flujo de controlan **UART0 CTS** y **UART0 RTS**.</span><span class="sxs-lookup"><span data-stu-id="19f0f-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="19f0f-158">Anclar 5 - **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="19f0f-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="19f0f-159">Anclar 7 - **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="19f0f-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="19f0f-160">Anclar 3 - **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="19f0f-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="19f0f-161">Anclar 9 - **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="19f0f-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="19f0f-162">**UART1** incluye solamente el **UART1 TX** y **UART1 RX** líneas.</span><span class="sxs-lookup"><span data-stu-id="19f0f-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="19f0f-163">Anclar 11 - **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="19f0f-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="19f0f-164">Anclar 13 - **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="19f0f-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="19f0f-165">El ejemplo siguiente inicializa **UART1** y realiza una operación de escritura seguido por una lectura:</span><span class="sxs-lookup"><span data-stu-id="19f0f-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="19f0f-166">Visual Studio 2017 tiene un problema conocido en el Diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la capacidad de serialcommunication.</span><span class="sxs-lookup"><span data-stu-id="19f0f-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="19f0f-167">Si su appxmanifest agrega la capacidad de serialcommunication, modificar su appxmanifest con el diseñador dañará su appxmanifest (el elemento secundario xml de dispositivo se perderán).</span><span class="sxs-lookup"><span data-stu-id="19f0f-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="19f0f-168">Puede solucionar este problema mediante la edición de mano el appxmanifest haciendo clic en su appxmanifest y seleccione Ver código en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="19f0f-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="19f0f-169">Debe agregar la funcionalidad siguiente a la **Package.appxmanifest** archivo del proyecto UWP para ejecutar código UART serie:</span><span class="sxs-lookup"><span data-stu-id="19f0f-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="19f0f-170">Bus i2c</span><span class="sxs-lookup"><span data-stu-id="19f0f-170">I2C Bus</span></span>

<span data-ttu-id="19f0f-171">Echemos un vistazo a lo buses de I2C disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="19f0f-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="19f0f-172">PIN i2c</span><span class="sxs-lookup"><span data-stu-id="19f0f-172">I2C Pins</span></span>

<span data-ttu-id="19f0f-173">**I2C0** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**</span><span class="sxs-lookup"><span data-stu-id="19f0f-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="19f0f-174">Anclar 17 - **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="19f0f-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="19f0f-175">Anclar 15 - **I2C0 SCL**</span><span class="sxs-lookup"><span data-stu-id="19f0f-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="19f0f-176">**I2C1** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**</span><span class="sxs-lookup"><span data-stu-id="19f0f-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="19f0f-177">Anclar 21 - **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="19f0f-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="19f0f-178">Anclar 19 - **I2C1 SCL**</span><span class="sxs-lookup"><span data-stu-id="19f0f-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="19f0f-179">Ejemplo de i2c</span><span class="sxs-lookup"><span data-stu-id="19f0f-179">I2C Sample</span></span>

<span data-ttu-id="19f0f-180">El ejemplo siguiente inicializa **I2C0** y escribe datos en un dispositivo I2C con dirección **0 x 40**:</span><span class="sxs-lookup"><span data-stu-id="19f0f-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="19f0f-181">Bus SPI</span><span class="sxs-lookup"><span data-stu-id="19f0f-181">SPI Bus</span></span>

<span data-ttu-id="19f0f-182">Echemos un vistazo del bus SPI disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="19f0f-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="19f0f-183">PIN SPI</span><span class="sxs-lookup"><span data-stu-id="19f0f-183">SPI Pins</span></span>

<span data-ttu-id="19f0f-184">Hay un controlador SPI **SPI0** disponible en la base de datos</span><span class="sxs-lookup"><span data-stu-id="19f0f-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="19f0f-185">Anclar 10 - **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="19f0f-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="19f0f-186">Anclar 14 - **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="19f0f-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="19f0f-187">Anclar 8 - **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="19f0f-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="19f0f-188">Anclar 12 - **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="19f0f-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="19f0f-189">Problemas SPI</span><span class="sxs-lookup"><span data-stu-id="19f0f-189">SPI Issues</span></span>

<span data-ttu-id="19f0f-190">El reloj SPI se fija en 4.8 mhz.</span><span class="sxs-lookup"><span data-stu-id="19f0f-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="19f0f-191">Se omitirá el reloj SPI solicitado.</span><span class="sxs-lookup"><span data-stu-id="19f0f-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="19f0f-192">Ejemplo SPI</span><span class="sxs-lookup"><span data-stu-id="19f0f-192">SPI Sample</span></span>

<span data-ttu-id="19f0f-193">Un ejemplo sobre cómo realizar un IRP de escritura en el bus **SPI0** se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="19f0f-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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
