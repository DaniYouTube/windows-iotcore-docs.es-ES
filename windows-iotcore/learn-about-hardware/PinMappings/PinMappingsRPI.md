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
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="72461-104">Asignaciones de raspberry Pi 2 & 3 Pin</span><span class="sxs-lookup"><span data-stu-id="72461-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Encabezado de raspberry Pi 2 & 3 Pin](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="72461-106">Interfaces de hardware para el dispositivo Raspberry Pi 2 y Raspberry Pi 3 se exponen a través del encabezado de 40-pin **celda J8** en el panel.</span><span class="sxs-lookup"><span data-stu-id="72461-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="72461-107">La funcionalidad incluye:</span><span class="sxs-lookup"><span data-stu-id="72461-107">Functionality includes:</span></span>

* <span data-ttu-id="72461-108">**24 x** -pines GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="72461-109">**1 x** -UARTs serie (RPi3 sólo incluye mini UART)</span><span class="sxs-lookup"><span data-stu-id="72461-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="72461-110">**2 x** -bus SPI</span><span class="sxs-lookup"><span data-stu-id="72461-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="72461-111">**1 x** -bus I2C</span><span class="sxs-lookup"><span data-stu-id="72461-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="72461-112">**2 x** -PIN de alimentación de 5 v</span><span class="sxs-lookup"><span data-stu-id="72461-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="72461-113">**2 x** : 3,3 v power PIN</span><span class="sxs-lookup"><span data-stu-id="72461-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="72461-114">**8 x** -masa PIN</span><span class="sxs-lookup"><span data-stu-id="72461-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="72461-115">Pines GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-115">GPIO Pins</span></span>

<span data-ttu-id="72461-116">Echemos un vistazo a la GPIO disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="72461-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="72461-117">Información general sobre el Pin GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-117">GPIO Pin Overview</span></span>

<span data-ttu-id="72461-118">Las clavijas GPIO siguientes son accesibles a través de API:</span><span class="sxs-lookup"><span data-stu-id="72461-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="72461-119">GPIO #</span><span class="sxs-lookup"><span data-stu-id="72461-119">GPIO#</span></span> | <span data-ttu-id="72461-120">Incorporación de cambios de encendido</span><span class="sxs-lookup"><span data-stu-id="72461-120">Power-on Pull</span></span> | <span data-ttu-id="72461-121">Funciones alternativas</span><span class="sxs-lookup"><span data-stu-id="72461-121">Alternate Functions</span></span> | <span data-ttu-id="72461-122">Pin de encabezado</span><span class="sxs-lookup"><span data-stu-id="72461-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="72461-123">2</span><span class="sxs-lookup"><span data-stu-id="72461-123">2</span></span>     | <span data-ttu-id="72461-124">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-124">PullUp</span></span>        | <span data-ttu-id="72461-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="72461-125">I2C1 SDA</span></span>            | <span data-ttu-id="72461-126">3</span><span class="sxs-lookup"><span data-stu-id="72461-126">3</span></span>                  |
> | <span data-ttu-id="72461-127">3</span><span class="sxs-lookup"><span data-stu-id="72461-127">3</span></span>     | <span data-ttu-id="72461-128">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-128">PullUp</span></span>        | <span data-ttu-id="72461-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="72461-129">I2C1 SCL</span></span>            | <span data-ttu-id="72461-130">5</span><span class="sxs-lookup"><span data-stu-id="72461-130">5</span></span>                  |
> | <span data-ttu-id="72461-131">4</span><span class="sxs-lookup"><span data-stu-id="72461-131">4</span></span>     | <span data-ttu-id="72461-132">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-132">PullUp</span></span>        |                     | <span data-ttu-id="72461-133">7</span><span class="sxs-lookup"><span data-stu-id="72461-133">7</span></span>                  |
> | <span data-ttu-id="72461-134">5</span><span class="sxs-lookup"><span data-stu-id="72461-134">5</span></span>     | <span data-ttu-id="72461-135">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-135">PullUp</span></span>        |                     | <span data-ttu-id="72461-136">29</span><span class="sxs-lookup"><span data-stu-id="72461-136">29</span></span>                 |
> | <span data-ttu-id="72461-137">6</span><span class="sxs-lookup"><span data-stu-id="72461-137">6</span></span>     | <span data-ttu-id="72461-138">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-138">PullUp</span></span>        |                     | <span data-ttu-id="72461-139">31</span><span class="sxs-lookup"><span data-stu-id="72461-139">31</span></span>                 |
> | <span data-ttu-id="72461-140">7</span><span class="sxs-lookup"><span data-stu-id="72461-140">7</span></span>     | <span data-ttu-id="72461-141">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-141">PullUp</span></span>        | <span data-ttu-id="72461-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="72461-142">SPI0 CS1</span></span>            | <span data-ttu-id="72461-143">26</span><span class="sxs-lookup"><span data-stu-id="72461-143">26</span></span>                 |
> | <span data-ttu-id="72461-144">8</span><span class="sxs-lookup"><span data-stu-id="72461-144">8</span></span>     | <span data-ttu-id="72461-145">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-145">PullUp</span></span>        | <span data-ttu-id="72461-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="72461-146">SPI0 CS0</span></span>            | <span data-ttu-id="72461-147">24</span><span class="sxs-lookup"><span data-stu-id="72461-147">24</span></span>                 |
> | <span data-ttu-id="72461-148">9</span><span class="sxs-lookup"><span data-stu-id="72461-148">9</span></span>     | <span data-ttu-id="72461-149">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-149">PullDown</span></span>      | <span data-ttu-id="72461-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="72461-150">SPI0 MISO</span></span>           | <span data-ttu-id="72461-151">21</span><span class="sxs-lookup"><span data-stu-id="72461-151">21</span></span>                 |
> | <span data-ttu-id="72461-152">10</span><span class="sxs-lookup"><span data-stu-id="72461-152">10</span></span>    | <span data-ttu-id="72461-153">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-153">PullDown</span></span>      | <span data-ttu-id="72461-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="72461-154">SPI0 MOSI</span></span>           | <span data-ttu-id="72461-155">19</span><span class="sxs-lookup"><span data-stu-id="72461-155">19</span></span>                 |
> | <span data-ttu-id="72461-156">11</span><span class="sxs-lookup"><span data-stu-id="72461-156">11</span></span>    | <span data-ttu-id="72461-157">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-157">PullDown</span></span>      | <span data-ttu-id="72461-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="72461-158">SPI0 SCLK</span></span>           | <span data-ttu-id="72461-159">23</span><span class="sxs-lookup"><span data-stu-id="72461-159">23</span></span>                 |
> | <span data-ttu-id="72461-160">12</span><span class="sxs-lookup"><span data-stu-id="72461-160">12</span></span>    | <span data-ttu-id="72461-161">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-161">PullDown</span></span>      |                     | <span data-ttu-id="72461-162">32</span><span class="sxs-lookup"><span data-stu-id="72461-162">32</span></span>                 |
> | <span data-ttu-id="72461-163">13</span><span class="sxs-lookup"><span data-stu-id="72461-163">13</span></span>    | <span data-ttu-id="72461-164">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-164">PullDown</span></span>      |                     | <span data-ttu-id="72461-165">33</span><span class="sxs-lookup"><span data-stu-id="72461-165">33</span></span>                 |
> | <span data-ttu-id="72461-166">16</span><span class="sxs-lookup"><span data-stu-id="72461-166">16</span></span>    | <span data-ttu-id="72461-167">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-167">PullDown</span></span>      | <span data-ttu-id="72461-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="72461-168">SPI1 CS0</span></span>            | <span data-ttu-id="72461-169">36</span><span class="sxs-lookup"><span data-stu-id="72461-169">36</span></span>                 |
> | <span data-ttu-id="72461-170">17</span><span class="sxs-lookup"><span data-stu-id="72461-170">17</span></span>    | <span data-ttu-id="72461-171">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-171">PullDown</span></span>      |                     | <span data-ttu-id="72461-172">11</span><span class="sxs-lookup"><span data-stu-id="72461-172">11</span></span>                 |
> | <span data-ttu-id="72461-173">18</span><span class="sxs-lookup"><span data-stu-id="72461-173">18</span></span>    | <span data-ttu-id="72461-174">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-174">PullDown</span></span>      |                     | <span data-ttu-id="72461-175">12</span><span class="sxs-lookup"><span data-stu-id="72461-175">12</span></span>                 |
> | <span data-ttu-id="72461-176">19</span><span class="sxs-lookup"><span data-stu-id="72461-176">19</span></span>    | <span data-ttu-id="72461-177">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-177">PullDown</span></span>      | <span data-ttu-id="72461-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="72461-178">SPI1 MISO</span></span>           | <span data-ttu-id="72461-179">35</span><span class="sxs-lookup"><span data-stu-id="72461-179">35</span></span>                 |
> | <span data-ttu-id="72461-180">20</span><span class="sxs-lookup"><span data-stu-id="72461-180">20</span></span>    | <span data-ttu-id="72461-181">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-181">PullDown</span></span>      | <span data-ttu-id="72461-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="72461-182">SPI1 MOSI</span></span>           | <span data-ttu-id="72461-183">38</span><span class="sxs-lookup"><span data-stu-id="72461-183">38</span></span>                 |
> | <span data-ttu-id="72461-184">21</span><span class="sxs-lookup"><span data-stu-id="72461-184">21</span></span>    | <span data-ttu-id="72461-185">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-185">PullDown</span></span>      | <span data-ttu-id="72461-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="72461-186">SPI1 SCLK</span></span>           | <span data-ttu-id="72461-187">40</span><span class="sxs-lookup"><span data-stu-id="72461-187">40</span></span>                 |
> | <span data-ttu-id="72461-188">22</span><span class="sxs-lookup"><span data-stu-id="72461-188">22</span></span>    | <span data-ttu-id="72461-189">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-189">PullDown</span></span>      |                     | <span data-ttu-id="72461-190">15</span><span class="sxs-lookup"><span data-stu-id="72461-190">15</span></span>                 |
> | <span data-ttu-id="72461-191">23</span><span class="sxs-lookup"><span data-stu-id="72461-191">23</span></span>    | <span data-ttu-id="72461-192">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-192">PullDown</span></span>      |                     | <span data-ttu-id="72461-193">16</span><span class="sxs-lookup"><span data-stu-id="72461-193">16</span></span>                 |
> | <span data-ttu-id="72461-194">24</span><span class="sxs-lookup"><span data-stu-id="72461-194">24</span></span>    | <span data-ttu-id="72461-195">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-195">PullDown</span></span>      |                     | <span data-ttu-id="72461-196">18</span><span class="sxs-lookup"><span data-stu-id="72461-196">18</span></span>                 |
> | <span data-ttu-id="72461-197">25</span><span class="sxs-lookup"><span data-stu-id="72461-197">25</span></span>    | <span data-ttu-id="72461-198">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-198">PullDown</span></span>      |                     | <span data-ttu-id="72461-199">22</span><span class="sxs-lookup"><span data-stu-id="72461-199">22</span></span>                 |
> | <span data-ttu-id="72461-200">26</span><span class="sxs-lookup"><span data-stu-id="72461-200">26</span></span>    | <span data-ttu-id="72461-201">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-201">PullDown</span></span>      |                     | <span data-ttu-id="72461-202">37</span><span class="sxs-lookup"><span data-stu-id="72461-202">37</span></span>                 |
> | <span data-ttu-id="72461-203">27</span><span class="sxs-lookup"><span data-stu-id="72461-203">27</span></span>    | <span data-ttu-id="72461-204">PullDown</span><span class="sxs-lookup"><span data-stu-id="72461-204">PullDown</span></span>      |                     | <span data-ttu-id="72461-205">13</span><span class="sxs-lookup"><span data-stu-id="72461-205">13</span></span>                 |
> | <span data-ttu-id="72461-206">35\*</span><span class="sxs-lookup"><span data-stu-id="72461-206">35\*</span></span>   | <span data-ttu-id="72461-207">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-207">PullUp</span></span>        |                     | <span data-ttu-id="72461-208">LED de alimentación rojo</span><span class="sxs-lookup"><span data-stu-id="72461-208">Red Power LED</span></span>      |
> | <span data-ttu-id="72461-209">47\*</span><span class="sxs-lookup"><span data-stu-id="72461-209">47\*</span></span>   | <span data-ttu-id="72461-210">Subida</span><span class="sxs-lookup"><span data-stu-id="72461-210">PullUp</span></span>        |                     | <span data-ttu-id="72461-211">LED verde de la actividad</span><span class="sxs-lookup"><span data-stu-id="72461-211">Green Activity LED</span></span> |

<span data-ttu-id="72461-212">\* = Raspberry Pi 2 solo.</span><span class="sxs-lookup"><span data-stu-id="72461-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="72461-213">GPIO 35 & 47 no están disponibles en Raspberry Pi 3.</span><span class="sxs-lookup"><span data-stu-id="72461-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="72461-214">Ejemplo GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-214">GPIO Sample</span></span>

<span data-ttu-id="72461-215">Por ejemplo, el siguiente código se abre **GPIO 5** como salida y escribe un digitales '**1**' out en el pin:</span><span class="sxs-lookup"><span data-stu-id="72461-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="72461-216">Al abrir un pin, estará en su estado de encendido, que puede incluir una resistencia de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="72461-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="72461-217">Para desconectar las resistencias de incorporación de cambios y obtener una entrada de impedancia de alta, establezca el modo de unidad en GpioPinDriveMode.Input:</span><span class="sxs-lookup"><span data-stu-id="72461-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>

    pin.SetDriveMode(GpioPinDriveMode.Input);

<span data-ttu-id="72461-218">Cuando se cierra un pin, revierte a su estado de encendido.</span><span class="sxs-lookup"><span data-stu-id="72461-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="72461-219">PIN Muxing</span><span class="sxs-lookup"><span data-stu-id="72461-219">Pin Muxing</span></span>

<span data-ttu-id="72461-220">Algunos pines GPIO pueden realizar varias funciones.</span><span class="sxs-lookup"><span data-stu-id="72461-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="72461-221">De forma predeterminada, el PIN se configuran como entradas GPIO.</span><span class="sxs-lookup"><span data-stu-id="72461-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="72461-222">Cuando abre una función alternativa mediante una llamada a `I2cDevice.FromIdAsync()` o `SpiDevice.FromIdAsync()` , el PIN requeridos por la función son automáticamente conmutada ("MUX") a la función correcta.</span><span class="sxs-lookup"><span data-stu-id="72461-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="72461-223">Cuando se cierra el dispositivo mediante una llamada a `I2cDevice.Dispose()` o `SpiDevice.Dispose()`, el PIN se restablecerá a su función de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="72461-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="72461-224">Si intenta usar un pin para dos funciones diferentes a la vez, se producirá una excepción al intentar abrir la función en conflicto.</span><span class="sxs-lookup"><span data-stu-id="72461-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="72461-225">Por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="72461-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="72461-226">UART serie</span><span class="sxs-lookup"><span data-stu-id="72461-226">Serial UART</span></span>

<span data-ttu-id="72461-227">Hay un UART serie disponible en el RPi2/3: **UART0**</span><span class="sxs-lookup"><span data-stu-id="72461-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="72461-228">Anclar 8 - **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="72461-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="72461-229">Anclar 10 - **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="72461-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="72461-230">El ejemplo siguiente inicializa **UART0** y realiza una operación de escritura seguido por una lectura:</span><span class="sxs-lookup"><span data-stu-id="72461-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="72461-231">Tenga en cuenta que debe agregar la funcionalidad siguiente a la **Package.appxmanifest** archivo del proyecto UWP para ejecutar código UART serie:</span><span class="sxs-lookup"><span data-stu-id="72461-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="72461-232">Visual Studio 2017 tiene un problema conocido en el Diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la capacidad de serialcommunication.</span><span class="sxs-lookup"><span data-stu-id="72461-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="72461-233">Si su appxmanifest agrega la capacidad de serialcommunication, modificar su appxmanifest con el diseñador dañará su appxmanifest (el elemento secundario xml de dispositivo se perderán).</span><span class="sxs-lookup"><span data-stu-id="72461-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="72461-234">Puede solucionar este problema mediante la edición de mano el appxmanifest haciendo clic en su appxmanifest y seleccione Ver código en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="72461-234">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="72461-235">Bus i2c</span><span class="sxs-lookup"><span data-stu-id="72461-235">I2C Bus</span></span>

<span data-ttu-id="72461-236">Vamos a examinar el bus I2C disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="72461-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="72461-237">Información general de i2c</span><span class="sxs-lookup"><span data-stu-id="72461-237">I2C Overview</span></span>

<span data-ttu-id="72461-238">Hay un controlador I2C **I2C1** expuestos en el encabezado de pin con dos líneas **SDA** y **SCL**.</span><span class="sxs-lookup"><span data-stu-id="72461-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="72461-239">1.8 K&#x2126; resistencias pull-up interno ya están instalados en el panel para este bus.</span><span class="sxs-lookup"><span data-stu-id="72461-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="72461-240">Nombre de señal</span><span class="sxs-lookup"><span data-stu-id="72461-240">Signal Name</span></span> | <span data-ttu-id="72461-241">Número de Pin de encabezado</span><span class="sxs-lookup"><span data-stu-id="72461-241">Header Pin Number</span></span> | <span data-ttu-id="72461-242">Número de GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="72461-243">SDA</span><span class="sxs-lookup"><span data-stu-id="72461-243">SDA</span></span>         | <span data-ttu-id="72461-244">3</span><span class="sxs-lookup"><span data-stu-id="72461-244">3</span></span>                 | <span data-ttu-id="72461-245">2</span><span class="sxs-lookup"><span data-stu-id="72461-245">2</span></span>           |
> | <span data-ttu-id="72461-246">SCL</span><span class="sxs-lookup"><span data-stu-id="72461-246">SCL</span></span>         | <span data-ttu-id="72461-247">5</span><span class="sxs-lookup"><span data-stu-id="72461-247">5</span></span>                 | <span data-ttu-id="72461-248">3</span><span class="sxs-lookup"><span data-stu-id="72461-248">3</span></span>           |

<span data-ttu-id="72461-249">El ejemplo siguiente inicializa **I2C1** y escribe datos en un dispositivo I2C con dirección **0 x 40**:</span><span class="sxs-lookup"><span data-stu-id="72461-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="72461-250">Bus SPI</span><span class="sxs-lookup"><span data-stu-id="72461-250">SPI Bus</span></span>

<span data-ttu-id="72461-251">Hay dos controladores de bus SPI en RPi2/3.</span><span class="sxs-lookup"><span data-stu-id="72461-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="72461-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="72461-252">SPI0</span></span>

> | <span data-ttu-id="72461-253">Nombre de señal</span><span class="sxs-lookup"><span data-stu-id="72461-253">Signal Name</span></span> | <span data-ttu-id="72461-254">Número de Pin de encabezado</span><span class="sxs-lookup"><span data-stu-id="72461-254">Header Pin Number</span></span> | <span data-ttu-id="72461-255">Número de GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="72461-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="72461-256">MOSI</span></span>        | <span data-ttu-id="72461-257">19</span><span class="sxs-lookup"><span data-stu-id="72461-257">19</span></span>                | <span data-ttu-id="72461-258">10</span><span class="sxs-lookup"><span data-stu-id="72461-258">10</span></span>          |
> | <span data-ttu-id="72461-259">MISO</span><span class="sxs-lookup"><span data-stu-id="72461-259">MISO</span></span>        | <span data-ttu-id="72461-260">21</span><span class="sxs-lookup"><span data-stu-id="72461-260">21</span></span>                | <span data-ttu-id="72461-261">9</span><span class="sxs-lookup"><span data-stu-id="72461-261">9</span></span>           |
> | <span data-ttu-id="72461-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="72461-262">SCLK</span></span>        | <span data-ttu-id="72461-263">23</span><span class="sxs-lookup"><span data-stu-id="72461-263">23</span></span>                | <span data-ttu-id="72461-264">11</span><span class="sxs-lookup"><span data-stu-id="72461-264">11</span></span>          |
> | <span data-ttu-id="72461-265">CS0</span><span class="sxs-lookup"><span data-stu-id="72461-265">CS0</span></span>         | <span data-ttu-id="72461-266">24</span><span class="sxs-lookup"><span data-stu-id="72461-266">24</span></span>                | <span data-ttu-id="72461-267">8</span><span class="sxs-lookup"><span data-stu-id="72461-267">8</span></span>           |
> | <span data-ttu-id="72461-268">CS1</span><span class="sxs-lookup"><span data-stu-id="72461-268">CS1</span></span>         | <span data-ttu-id="72461-269">26</span><span class="sxs-lookup"><span data-stu-id="72461-269">26</span></span>                | <span data-ttu-id="72461-270">7</span><span class="sxs-lookup"><span data-stu-id="72461-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="72461-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="72461-271">SPI1</span></span>

> | <span data-ttu-id="72461-272">Nombre de señal</span><span class="sxs-lookup"><span data-stu-id="72461-272">Signal Name</span></span> | <span data-ttu-id="72461-273">Número de Pin de encabezado</span><span class="sxs-lookup"><span data-stu-id="72461-273">Header Pin Number</span></span> | <span data-ttu-id="72461-274">Número de GPIO</span><span class="sxs-lookup"><span data-stu-id="72461-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="72461-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="72461-275">MOSI</span></span>        | <span data-ttu-id="72461-276">38</span><span class="sxs-lookup"><span data-stu-id="72461-276">38</span></span>                | <span data-ttu-id="72461-277">20</span><span class="sxs-lookup"><span data-stu-id="72461-277">20</span></span>          |
> | <span data-ttu-id="72461-278">MISO</span><span class="sxs-lookup"><span data-stu-id="72461-278">MISO</span></span>        | <span data-ttu-id="72461-279">35</span><span class="sxs-lookup"><span data-stu-id="72461-279">35</span></span>                | <span data-ttu-id="72461-280">19</span><span class="sxs-lookup"><span data-stu-id="72461-280">19</span></span>          |
> | <span data-ttu-id="72461-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="72461-281">SCLK</span></span>        | <span data-ttu-id="72461-282">40</span><span class="sxs-lookup"><span data-stu-id="72461-282">40</span></span>                | <span data-ttu-id="72461-283">21</span><span class="sxs-lookup"><span data-stu-id="72461-283">21</span></span>          |
> | <span data-ttu-id="72461-284">CS0</span><span class="sxs-lookup"><span data-stu-id="72461-284">CS0</span></span>         | <span data-ttu-id="72461-285">36</span><span class="sxs-lookup"><span data-stu-id="72461-285">36</span></span>                | <span data-ttu-id="72461-286">16</span><span class="sxs-lookup"><span data-stu-id="72461-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="72461-287">Ejemplo SPI</span><span class="sxs-lookup"><span data-stu-id="72461-287">SPI Sample</span></span>

<span data-ttu-id="72461-288">Un ejemplo de cómo realizar un IRP de escritura en el bus **SPI0** mediante select chip 0 se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="72461-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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

