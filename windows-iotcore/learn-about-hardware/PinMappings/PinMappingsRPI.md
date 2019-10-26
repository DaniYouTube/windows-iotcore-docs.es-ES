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
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="a5dcc-104">Asignaciones de Raspberry pi 2 & 3 pin</span><span class="sxs-lookup"><span data-stu-id="a5dcc-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Encabezado Raspberry pi 2 & 3 pin](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="a5dcc-106">Las interfaces de hardware para Raspberry pi 2 y Raspberry PI 3 se exponen a través del encabezado de 40 **J8** en el panel.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="a5dcc-107">La funcionalidad incluye:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-107">Functionality includes:</span></span>

* <span data-ttu-id="a5dcc-108">PIN de **24x** a GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="a5dcc-109">**1x** : UART en serie (RPi3 solo incluye mini UART)</span><span class="sxs-lookup"><span data-stu-id="a5dcc-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="a5dcc-110">Bus **2x** -SPI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="a5dcc-111">Bus **1x** -I2C</span><span class="sxs-lookup"><span data-stu-id="a5dcc-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="a5dcc-112">clavijas de potencia **2x** -5V</span><span class="sxs-lookup"><span data-stu-id="a5dcc-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="a5dcc-113">**2x** -3,3 clavijas de alimentación</span><span class="sxs-lookup"><span data-stu-id="a5dcc-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="a5dcc-114">pines de **8X**</span><span class="sxs-lookup"><span data-stu-id="a5dcc-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="a5dcc-115">PIN de GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-115">GPIO Pins</span></span>

<span data-ttu-id="a5dcc-116">Echemos un vistazo al GPIO disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="a5dcc-117">Introducción al pin de GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-117">GPIO Pin Overview</span></span>

<span data-ttu-id="a5dcc-118">Se puede acceder a los siguientes PIN de GPIO a través de las API:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="a5dcc-119">GPIO #</span><span class="sxs-lookup"><span data-stu-id="a5dcc-119">GPIO#</span></span> | <span data-ttu-id="a5dcc-120">Extracción de energía</span><span class="sxs-lookup"><span data-stu-id="a5dcc-120">Power-on Pull</span></span> | <span data-ttu-id="a5dcc-121">Funciones alternativas</span><span class="sxs-lookup"><span data-stu-id="a5dcc-121">Alternate Functions</span></span> | <span data-ttu-id="a5dcc-122">PIN de encabezado</span><span class="sxs-lookup"><span data-stu-id="a5dcc-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="a5dcc-123">2</span><span class="sxs-lookup"><span data-stu-id="a5dcc-123">2</span></span>     | <span data-ttu-id="a5dcc-124">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-124">PullUp</span></span>        | <span data-ttu-id="a5dcc-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="a5dcc-125">I2C1 SDA</span></span>            | <span data-ttu-id="a5dcc-126">3</span><span class="sxs-lookup"><span data-stu-id="a5dcc-126">3</span></span>                  |
> | <span data-ttu-id="a5dcc-127">3</span><span class="sxs-lookup"><span data-stu-id="a5dcc-127">3</span></span>     | <span data-ttu-id="a5dcc-128">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-128">PullUp</span></span>        | <span data-ttu-id="a5dcc-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="a5dcc-129">I2C1 SCL</span></span>            | <span data-ttu-id="a5dcc-130">5</span><span class="sxs-lookup"><span data-stu-id="a5dcc-130">5</span></span>                  |
> | <span data-ttu-id="a5dcc-131">4</span><span class="sxs-lookup"><span data-stu-id="a5dcc-131">4</span></span>     | <span data-ttu-id="a5dcc-132">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-132">PullUp</span></span>        |                     | <span data-ttu-id="a5dcc-133">7</span><span class="sxs-lookup"><span data-stu-id="a5dcc-133">7</span></span>                  |
> | <span data-ttu-id="a5dcc-134">5</span><span class="sxs-lookup"><span data-stu-id="a5dcc-134">5</span></span>     | <span data-ttu-id="a5dcc-135">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-135">PullUp</span></span>        |                     | <span data-ttu-id="a5dcc-136">29</span><span class="sxs-lookup"><span data-stu-id="a5dcc-136">29</span></span>                 |
> | <span data-ttu-id="a5dcc-137">6</span><span class="sxs-lookup"><span data-stu-id="a5dcc-137">6</span></span>     | <span data-ttu-id="a5dcc-138">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-138">PullUp</span></span>        |                     | <span data-ttu-id="a5dcc-139">31</span><span class="sxs-lookup"><span data-stu-id="a5dcc-139">31</span></span>                 |
> | <span data-ttu-id="a5dcc-140">7</span><span class="sxs-lookup"><span data-stu-id="a5dcc-140">7</span></span>     | <span data-ttu-id="a5dcc-141">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-141">PullUp</span></span>        | <span data-ttu-id="a5dcc-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="a5dcc-142">SPI0 CS1</span></span>            | <span data-ttu-id="a5dcc-143">26</span><span class="sxs-lookup"><span data-stu-id="a5dcc-143">26</span></span>                 |
> | <span data-ttu-id="a5dcc-144">8</span><span class="sxs-lookup"><span data-stu-id="a5dcc-144">8</span></span>     | <span data-ttu-id="a5dcc-145">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-145">PullUp</span></span>        | <span data-ttu-id="a5dcc-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="a5dcc-146">SPI0 CS0</span></span>            | <span data-ttu-id="a5dcc-147">24</span><span class="sxs-lookup"><span data-stu-id="a5dcc-147">24</span></span>                 |
> | <span data-ttu-id="a5dcc-148">9</span><span class="sxs-lookup"><span data-stu-id="a5dcc-148">9</span></span>     | <span data-ttu-id="a5dcc-149">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-149">PullDown</span></span>      | <span data-ttu-id="a5dcc-150">SPI0</span><span class="sxs-lookup"><span data-stu-id="a5dcc-150">SPI0 MISO</span></span>           | <span data-ttu-id="a5dcc-151">21</span><span class="sxs-lookup"><span data-stu-id="a5dcc-151">21</span></span>                 |
> | <span data-ttu-id="a5dcc-152">10</span><span class="sxs-lookup"><span data-stu-id="a5dcc-152">10</span></span>    | <span data-ttu-id="a5dcc-153">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-153">PullDown</span></span>      | <span data-ttu-id="a5dcc-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-154">SPI0 MOSI</span></span>           | <span data-ttu-id="a5dcc-155">19</span><span class="sxs-lookup"><span data-stu-id="a5dcc-155">19</span></span>                 |
> | <span data-ttu-id="a5dcc-156">11</span><span class="sxs-lookup"><span data-stu-id="a5dcc-156">11</span></span>    | <span data-ttu-id="a5dcc-157">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-157">PullDown</span></span>      | <span data-ttu-id="a5dcc-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="a5dcc-158">SPI0 SCLK</span></span>           | <span data-ttu-id="a5dcc-159">23</span><span class="sxs-lookup"><span data-stu-id="a5dcc-159">23</span></span>                 |
> | <span data-ttu-id="a5dcc-160">12</span><span class="sxs-lookup"><span data-stu-id="a5dcc-160">12</span></span>    | <span data-ttu-id="a5dcc-161">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-161">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-162">32</span><span class="sxs-lookup"><span data-stu-id="a5dcc-162">32</span></span>                 |
> | <span data-ttu-id="a5dcc-163">13</span><span class="sxs-lookup"><span data-stu-id="a5dcc-163">13</span></span>    | <span data-ttu-id="a5dcc-164">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-164">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-165">33</span><span class="sxs-lookup"><span data-stu-id="a5dcc-165">33</span></span>                 |
> | <span data-ttu-id="a5dcc-166">16</span><span class="sxs-lookup"><span data-stu-id="a5dcc-166">16</span></span>    | <span data-ttu-id="a5dcc-167">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-167">PullDown</span></span>      | <span data-ttu-id="a5dcc-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="a5dcc-168">SPI1 CS0</span></span>            | <span data-ttu-id="a5dcc-169">36</span><span class="sxs-lookup"><span data-stu-id="a5dcc-169">36</span></span>                 |
> | <span data-ttu-id="a5dcc-170">17</span><span class="sxs-lookup"><span data-stu-id="a5dcc-170">17</span></span>    | <span data-ttu-id="a5dcc-171">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-171">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-172">11</span><span class="sxs-lookup"><span data-stu-id="a5dcc-172">11</span></span>                 |
> | <span data-ttu-id="a5dcc-173">18</span><span class="sxs-lookup"><span data-stu-id="a5dcc-173">18</span></span>    | <span data-ttu-id="a5dcc-174">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-174">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-175">12</span><span class="sxs-lookup"><span data-stu-id="a5dcc-175">12</span></span>                 |
> | <span data-ttu-id="a5dcc-176">19</span><span class="sxs-lookup"><span data-stu-id="a5dcc-176">19</span></span>    | <span data-ttu-id="a5dcc-177">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-177">PullDown</span></span>      | <span data-ttu-id="a5dcc-178">SPI1</span><span class="sxs-lookup"><span data-stu-id="a5dcc-178">SPI1 MISO</span></span>           | <span data-ttu-id="a5dcc-179">35</span><span class="sxs-lookup"><span data-stu-id="a5dcc-179">35</span></span>                 |
> | <span data-ttu-id="a5dcc-180">20</span><span class="sxs-lookup"><span data-stu-id="a5dcc-180">20</span></span>    | <span data-ttu-id="a5dcc-181">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-181">PullDown</span></span>      | <span data-ttu-id="a5dcc-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-182">SPI1 MOSI</span></span>           | <span data-ttu-id="a5dcc-183">38</span><span class="sxs-lookup"><span data-stu-id="a5dcc-183">38</span></span>                 |
> | <span data-ttu-id="a5dcc-184">21</span><span class="sxs-lookup"><span data-stu-id="a5dcc-184">21</span></span>    | <span data-ttu-id="a5dcc-185">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-185">PullDown</span></span>      | <span data-ttu-id="a5dcc-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="a5dcc-186">SPI1 SCLK</span></span>           | <span data-ttu-id="a5dcc-187">40</span><span class="sxs-lookup"><span data-stu-id="a5dcc-187">40</span></span>                 |
> | <span data-ttu-id="a5dcc-188">22</span><span class="sxs-lookup"><span data-stu-id="a5dcc-188">22</span></span>    | <span data-ttu-id="a5dcc-189">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-189">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-190">15</span><span class="sxs-lookup"><span data-stu-id="a5dcc-190">15</span></span>                 |
> | <span data-ttu-id="a5dcc-191">23</span><span class="sxs-lookup"><span data-stu-id="a5dcc-191">23</span></span>    | <span data-ttu-id="a5dcc-192">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-192">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-193">16</span><span class="sxs-lookup"><span data-stu-id="a5dcc-193">16</span></span>                 |
> | <span data-ttu-id="a5dcc-194">24</span><span class="sxs-lookup"><span data-stu-id="a5dcc-194">24</span></span>    | <span data-ttu-id="a5dcc-195">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-195">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-196">18</span><span class="sxs-lookup"><span data-stu-id="a5dcc-196">18</span></span>                 |
> | <span data-ttu-id="a5dcc-197">25</span><span class="sxs-lookup"><span data-stu-id="a5dcc-197">25</span></span>    | <span data-ttu-id="a5dcc-198">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-198">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-199">22</span><span class="sxs-lookup"><span data-stu-id="a5dcc-199">22</span></span>                 |
> | <span data-ttu-id="a5dcc-200">26</span><span class="sxs-lookup"><span data-stu-id="a5dcc-200">26</span></span>    | <span data-ttu-id="a5dcc-201">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-201">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-202">37</span><span class="sxs-lookup"><span data-stu-id="a5dcc-202">37</span></span>                 |
> | <span data-ttu-id="a5dcc-203">27</span><span class="sxs-lookup"><span data-stu-id="a5dcc-203">27</span></span>    | <span data-ttu-id="a5dcc-204">Combinan</span><span class="sxs-lookup"><span data-stu-id="a5dcc-204">PullDown</span></span>      |                     | <span data-ttu-id="a5dcc-205">13</span><span class="sxs-lookup"><span data-stu-id="a5dcc-205">13</span></span>                 |
> | <span data-ttu-id="a5dcc-206">35 \*</span><span class="sxs-lookup"><span data-stu-id="a5dcc-206">35\*</span></span>   | <span data-ttu-id="a5dcc-207">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-207">PullUp</span></span>        |                     | <span data-ttu-id="a5dcc-208">LED de alimentación rojo</span><span class="sxs-lookup"><span data-stu-id="a5dcc-208">Red Power LED</span></span>      |
> | <span data-ttu-id="a5dcc-209">47 \*</span><span class="sxs-lookup"><span data-stu-id="a5dcc-209">47\*</span></span>   | <span data-ttu-id="a5dcc-210">PullUp</span><span class="sxs-lookup"><span data-stu-id="a5dcc-210">PullUp</span></span>        |                     | <span data-ttu-id="a5dcc-211">LED de actividad verde</span><span class="sxs-lookup"><span data-stu-id="a5dcc-211">Green Activity LED</span></span> |

<span data-ttu-id="a5dcc-212">\* = Raspberry pi 2 solamente.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="a5dcc-213">GPIO 35 & 47 no están disponibles en Raspberry PI 3.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="a5dcc-214">Ejemplo de GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-214">GPIO Sample</span></span>

<span data-ttu-id="a5dcc-215">Como ejemplo, el código siguiente abre **GPIO 5** como salida y escribe un '**1**' digital en el PIN:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="a5dcc-216">Al abrir un PIN, estará en su estado de encendido, que puede incluir una resistencia de extracción.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="a5dcc-217">Para desconectar las resistencias de extracción y obtener una entrada de alta impedancia, establezca el modo de unidad en GpioPinDriveMode. Input:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>

    pin.SetDriveMode(GpioPinDriveMode.Input);

<span data-ttu-id="a5dcc-218">Cuando se cierra un PIN, vuelve a su estado de encendido.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="a5dcc-219">Multiplexación de PIN</span><span class="sxs-lookup"><span data-stu-id="a5dcc-219">Pin Muxing</span></span>

<span data-ttu-id="a5dcc-220">Algunos PIN de GPIO pueden realizar varias funciones.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="a5dcc-221">De forma predeterminada, los PIN se configuran como entradas de GPIO.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="a5dcc-222">Cuando se abre una función alternativa llamando a `I2cDevice.FromIdAsync()` o `SpiDevice.FromIdAsync()`, los pin requeridos por la función se cambian automáticamente ("MUX") a la función correcta.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="a5dcc-223">Cuando el dispositivo se cierra llamando a `I2cDevice.Dispose()` o `SpiDevice.Dispose()`, los pin vuelven a su función predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="a5dcc-224">Si intenta usar un PIN para dos funciones diferentes a la vez, se producirá una excepción al intentar abrir la función en conflicto.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="a5dcc-225">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="a5dcc-226">UART en serie</span><span class="sxs-lookup"><span data-stu-id="a5dcc-226">Serial UART</span></span>

<span data-ttu-id="a5dcc-227">Hay un UART en serie disponible en RPi2/3: **UART0**</span><span class="sxs-lookup"><span data-stu-id="a5dcc-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="a5dcc-228">Pin 8- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="a5dcc-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="a5dcc-229">PIN 10- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="a5dcc-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="a5dcc-230">En el ejemplo siguiente se inicializa **UART0** y se realiza una escritura seguida de una lectura:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="a5dcc-231">Tenga en cuenta que debe agregar la siguiente funcionalidad al archivo **Package. appxmanifest** en el proyecto de UWP para ejecutar el código UART en serie:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="a5dcc-232">Visual Studio 2017 tiene un error conocido en el diseñador de manifiestos (el editor visual para archivos appxmanifest) que afecta a la funcionalidad serialcommunication.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="a5dcc-233">Si el appxmanifest agrega la funcionalidad serialcommunication, la modificación de appxmanifest con el diseñador dañará el appxmanifest (se perderá el elemento secundario XML del dispositivo).</span><span class="sxs-lookup"><span data-stu-id="a5dcc-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="a5dcc-234">Puede solucionar este problema de forma manual editaba el appxmanifest; para ello, haga clic con el botón derecho en el appxmanifest y seleccione Ver código en el menú contextual.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-234">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="a5dcc-235">Bus I2C</span><span class="sxs-lookup"><span data-stu-id="a5dcc-235">I2C Bus</span></span>

<span data-ttu-id="a5dcc-236">Echemos un vistazo al bus I2C disponible en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="a5dcc-237">Información general de I2C</span><span class="sxs-lookup"><span data-stu-id="a5dcc-237">I2C Overview</span></span>

<span data-ttu-id="a5dcc-238">Hay un **I2C1** de controlador i2c expuesto en el encabezado del PIN con dos líneas **sda** y **SCL**.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="a5dcc-239">en el&#x2126; panel de este bus ya están instaladas las resistencias de extracción internas de 1,8 k.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="a5dcc-240">Nombre de señal</span><span class="sxs-lookup"><span data-stu-id="a5dcc-240">Signal Name</span></span> | <span data-ttu-id="a5dcc-241">Número de PIN del encabezado</span><span class="sxs-lookup"><span data-stu-id="a5dcc-241">Header Pin Number</span></span> | <span data-ttu-id="a5dcc-242">Número de GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="a5dcc-243">EMPAQUETADO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-243">SDA</span></span>         | <span data-ttu-id="a5dcc-244">3</span><span class="sxs-lookup"><span data-stu-id="a5dcc-244">3</span></span>                 | <span data-ttu-id="a5dcc-245">2</span><span class="sxs-lookup"><span data-stu-id="a5dcc-245">2</span></span>           |
> | <span data-ttu-id="a5dcc-246">FICHERO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-246">SCL</span></span>         | <span data-ttu-id="a5dcc-247">5</span><span class="sxs-lookup"><span data-stu-id="a5dcc-247">5</span></span>                 | <span data-ttu-id="a5dcc-248">3</span><span class="sxs-lookup"><span data-stu-id="a5dcc-248">3</span></span>           |

<span data-ttu-id="a5dcc-249">En el ejemplo siguiente se inicializa **I2C1** y se escriben datos en un dispositivo I2C con la dirección **0x40**:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="a5dcc-250">Bus SPI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-250">SPI Bus</span></span>

<span data-ttu-id="a5dcc-251">Hay dos controladores de bus SPI disponibles en RPi2/3.</span><span class="sxs-lookup"><span data-stu-id="a5dcc-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="a5dcc-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="a5dcc-252">SPI0</span></span>

> | <span data-ttu-id="a5dcc-253">Nombre de señal</span><span class="sxs-lookup"><span data-stu-id="a5dcc-253">Signal Name</span></span> | <span data-ttu-id="a5dcc-254">Número de PIN del encabezado</span><span class="sxs-lookup"><span data-stu-id="a5dcc-254">Header Pin Number</span></span> | <span data-ttu-id="a5dcc-255">Número de GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="a5dcc-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-256">MOSI</span></span>        | <span data-ttu-id="a5dcc-257">19</span><span class="sxs-lookup"><span data-stu-id="a5dcc-257">19</span></span>                | <span data-ttu-id="a5dcc-258">10</span><span class="sxs-lookup"><span data-stu-id="a5dcc-258">10</span></span>          |
> | <span data-ttu-id="a5dcc-259">PERMISOS</span><span class="sxs-lookup"><span data-stu-id="a5dcc-259">MISO</span></span>        | <span data-ttu-id="a5dcc-260">21</span><span class="sxs-lookup"><span data-stu-id="a5dcc-260">21</span></span>                | <span data-ttu-id="a5dcc-261">9</span><span class="sxs-lookup"><span data-stu-id="a5dcc-261">9</span></span>           |
> | <span data-ttu-id="a5dcc-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="a5dcc-262">SCLK</span></span>        | <span data-ttu-id="a5dcc-263">23</span><span class="sxs-lookup"><span data-stu-id="a5dcc-263">23</span></span>                | <span data-ttu-id="a5dcc-264">11</span><span class="sxs-lookup"><span data-stu-id="a5dcc-264">11</span></span>          |
> | <span data-ttu-id="a5dcc-265">CS0</span><span class="sxs-lookup"><span data-stu-id="a5dcc-265">CS0</span></span>         | <span data-ttu-id="a5dcc-266">24</span><span class="sxs-lookup"><span data-stu-id="a5dcc-266">24</span></span>                | <span data-ttu-id="a5dcc-267">8</span><span class="sxs-lookup"><span data-stu-id="a5dcc-267">8</span></span>           |
> | <span data-ttu-id="a5dcc-268">CS1</span><span class="sxs-lookup"><span data-stu-id="a5dcc-268">CS1</span></span>         | <span data-ttu-id="a5dcc-269">26</span><span class="sxs-lookup"><span data-stu-id="a5dcc-269">26</span></span>                | <span data-ttu-id="a5dcc-270">7</span><span class="sxs-lookup"><span data-stu-id="a5dcc-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="a5dcc-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="a5dcc-271">SPI1</span></span>

> | <span data-ttu-id="a5dcc-272">Nombre de señal</span><span class="sxs-lookup"><span data-stu-id="a5dcc-272">Signal Name</span></span> | <span data-ttu-id="a5dcc-273">Número de PIN del encabezado</span><span class="sxs-lookup"><span data-stu-id="a5dcc-273">Header Pin Number</span></span> | <span data-ttu-id="a5dcc-274">Número de GPIO</span><span class="sxs-lookup"><span data-stu-id="a5dcc-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="a5dcc-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-275">MOSI</span></span>        | <span data-ttu-id="a5dcc-276">38</span><span class="sxs-lookup"><span data-stu-id="a5dcc-276">38</span></span>                | <span data-ttu-id="a5dcc-277">20</span><span class="sxs-lookup"><span data-stu-id="a5dcc-277">20</span></span>          |
> | <span data-ttu-id="a5dcc-278">PERMISOS</span><span class="sxs-lookup"><span data-stu-id="a5dcc-278">MISO</span></span>        | <span data-ttu-id="a5dcc-279">35</span><span class="sxs-lookup"><span data-stu-id="a5dcc-279">35</span></span>                | <span data-ttu-id="a5dcc-280">19</span><span class="sxs-lookup"><span data-stu-id="a5dcc-280">19</span></span>          |
> | <span data-ttu-id="a5dcc-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="a5dcc-281">SCLK</span></span>        | <span data-ttu-id="a5dcc-282">40</span><span class="sxs-lookup"><span data-stu-id="a5dcc-282">40</span></span>                | <span data-ttu-id="a5dcc-283">21</span><span class="sxs-lookup"><span data-stu-id="a5dcc-283">21</span></span>          |
> | <span data-ttu-id="a5dcc-284">CS0</span><span class="sxs-lookup"><span data-stu-id="a5dcc-284">CS0</span></span>         | <span data-ttu-id="a5dcc-285">36</span><span class="sxs-lookup"><span data-stu-id="a5dcc-285">36</span></span>                | <span data-ttu-id="a5dcc-286">16</span><span class="sxs-lookup"><span data-stu-id="a5dcc-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="a5dcc-287">Ejemplo de SPI</span><span class="sxs-lookup"><span data-stu-id="a5dcc-287">SPI Sample</span></span>

<span data-ttu-id="a5dcc-288">A continuación se muestra un ejemplo de cómo realizar una escritura SPI en el bus **SPI0** con el chip Select 0:</span><span class="sxs-lookup"><span data-stu-id="a5dcc-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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

