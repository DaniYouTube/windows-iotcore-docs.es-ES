---
title: Guía de migración de cableado de Arduino
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las modificaciones y los problemas comunes que surgen al implementar proyectos de cableado de Arduino.
keywords: Windows IOT, Arduino, cableado, Visual Studio, portabilidad
ms.openlocfilehash: 7f3f70101fb28fab001dbd38d3159a7a10fa5586
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918137"
---
# <a name="arduino-wiring-porting-guide"></a><span data-ttu-id="208e3-104">Guía de migración de cableado de Arduino</span><span class="sxs-lookup"><span data-stu-id="208e3-104">Arduino Wiring Porting Guide</span></span>

<span data-ttu-id="208e3-105">Los bocetos y las bibliotecas de Arduino se pueden copiar y pegar en un proyecto de cableado de Arduino dentro de Visual Studio y ejecutarse en Raspberry pi 2, Raspberry PI 3 o Minnowboard Max.</span><span class="sxs-lookup"><span data-stu-id="208e3-105">Arduino Wiring sketches and libraries can be copy/pasted into an Arduino Wiring project inside Visual Studio and run on Raspberry Pi 2, Raspberry Pi 3 or Minnowboard Max.</span></span> <span data-ttu-id="208e3-106">A veces, se deben realizar pequeñas modificaciones para estos archivos con el fin de que sean más compatibles con el entorno de Windows o con el panel con el que está trabajando.</span><span class="sxs-lookup"><span data-stu-id="208e3-106">Sometimes there are slight modifications that need to be made to these files in order to make them more compatible with the Windows environment, or the board you are working with.</span></span> <span data-ttu-id="208e3-107">En esta guía se tratan las modificaciones y los problemas comunes que se pueden tener en la implementación de proyectos de cableado de Arduino.</span><span class="sxs-lookup"><span data-stu-id="208e3-107">This guide will cover those modifications as well as common issues that you may run into when deploying Arduino Wiring projects.</span></span>

## <a name="porting"></a><span data-ttu-id="208e3-108">Migración</span><span class="sxs-lookup"><span data-stu-id="208e3-108">Porting</span></span>

### <a name="updating-pins"></a><span data-ttu-id="208e3-109">Actualizar PIN</span><span class="sxs-lookup"><span data-stu-id="208e3-109">Updating Pins</span></span>

<span data-ttu-id="208e3-110">Podría ir sin decir, pero muchos bocetos y bibliotecas (especialmente los de las pletinas de Arduino) pueden contener referencias a clavijas de conector específicas para dispositivos Arduino.</span><span class="sxs-lookup"><span data-stu-id="208e3-110">It might go without saying, but many sketches and libraries (especially those for arduino shields) may contain references to specific connector pins for Arduino devices.</span></span> <span data-ttu-id="208e3-111">Querrá personalizar los bocetos para usar las clavijas del conector adecuadas para el dispositivo en el que está trabajando y la configuración que está usando.</span><span class="sxs-lookup"><span data-stu-id="208e3-111">You'll want to customize your sketches to use the appropriate connector pins for the device you are working on and the configuration you are using.</span></span>

<span data-ttu-id="208e3-112">En última instancia, el cableado de Arduino requiere un número de PIN del conector físico para cualquier función que haga referencia a "clavijas".</span><span class="sxs-lookup"><span data-stu-id="208e3-112">Arduino Wiring ultimately requires a physical connector pin number for any functions that refer to 'pins'.</span></span> <span data-ttu-id="208e3-113">Estos números se pueden usar directamente, pero también se proporcionan algunos nombres de PIN predefinidos que corresponden a las clavijas del conector en paneles específicos.</span><span class="sxs-lookup"><span data-stu-id="208e3-113">You can use these numbers directly, but we've also provided some pre-defined pin names which correspond to connector pins on specific boards.</span></span>

<span data-ttu-id="208e3-114">Por ejemplo, el PIN del conector físico 29 en un Raspberry pi 2 y 3 también se conoce como `GPIO5`.</span><span class="sxs-lookup"><span data-stu-id="208e3-114">For example, the physical connector pin 29 on a Raspberry Pi 2 and 3 is also known as `GPIO5`.</span></span> <span data-ttu-id="208e3-115">Puede establecer el PIN de GPIO 5 en un estado alto en un Raspberry pi 2 y 3 con cualquiera de los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="208e3-115">You may set GPIO pin 5 to a HIGH state on a Raspberry Pi 2 and 3 by using either of the following commands:</span></span>
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

<span data-ttu-id="208e3-116">o</span><span class="sxs-lookup"><span data-stu-id="208e3-116">or</span></span>

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

<span data-ttu-id="208e3-117">Los nombres de anclaje predefinidos se pueden encontrar en [pins_arduino. h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) y se incluyen en cada proyecto de cableado de Arduino, pero, dado que habrá diferentes clavijas del conector físico disponibles en función de la configuración de hardware que se está creando para, también se incluye una tabla. Aquí se describen los nombres de los PIN que están disponibles para cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="208e3-117">The pre-defined pin names can be found in [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) and included in every Arduino Wiring project, but since there will be different physical connector pins available depending on the hardware setup you are building for, we've also included a table here to describe which pin names are available for each device.</span></span>

#### <a name="raspberry-pi-2-and-3"></a><span data-ttu-id="208e3-118">Raspberry Pi 2 y 3</span><span class="sxs-lookup"><span data-stu-id="208e3-118">Raspberry Pi 2 and 3</span></span>

![Diagrama de pines](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="208e3-120">Definir PIN</span><span class="sxs-lookup"><span data-stu-id="208e3-120">Pin Define</span></span> | <span data-ttu-id="208e3-121">Número PIN correspondiente</span><span class="sxs-lookup"><span data-stu-id="208e3-121">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="208e3-122">LED_BUILTIN</span><span class="sxs-lookup"><span data-stu-id="208e3-122">LED_BUILTIN</span></span> | <span data-ttu-id="208e3-123">*LED incorporado*</span><span class="sxs-lookup"><span data-stu-id="208e3-123">*onboard LED*</span></span> |
> | <span data-ttu-id="208e3-124">GPIO \* _donde \* hace referencia a [0, 27]_</span><span class="sxs-lookup"><span data-stu-id="208e3-124">GPIO\* _where \* refers to [0, 27]_</span></span> | <span data-ttu-id="208e3-125">*Consulte el diagrama de pines*</span><span class="sxs-lookup"><span data-stu-id="208e3-125">*refer to pinout diagram*</span></span> |
> | <span data-ttu-id="208e3-126">GCLK</span><span class="sxs-lookup"><span data-stu-id="208e3-126">GCLK</span></span> | <span data-ttu-id="208e3-127">7</span><span class="sxs-lookup"><span data-stu-id="208e3-127">7</span></span> |
> | <span data-ttu-id="208e3-128">GEN \* _, donde \* hace referencia a [0, 5]_</span><span class="sxs-lookup"><span data-stu-id="208e3-128">GEN\* _where \* refers to [0, 5]_</span></span> | <span data-ttu-id="208e3-129">\* Consulte el diagrama de pines</span><span class="sxs-lookup"><span data-stu-id="208e3-129">\*refer to pinout diagram</span></span> |
> | <span data-ttu-id="208e3-130">SCL1</span><span class="sxs-lookup"><span data-stu-id="208e3-130">SCL1</span></span> | <span data-ttu-id="208e3-131">5</span><span class="sxs-lookup"><span data-stu-id="208e3-131">5</span></span> |
> | <span data-ttu-id="208e3-132">SDA1</span><span class="sxs-lookup"><span data-stu-id="208e3-132">SDA1</span></span> | <span data-ttu-id="208e3-133">3</span><span class="sxs-lookup"><span data-stu-id="208e3-133">3</span></span> |
> | <span data-ttu-id="208e3-134">CS0 (o CE0 o SS)</span><span class="sxs-lookup"><span data-stu-id="208e3-134">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="208e3-135">24</span><span class="sxs-lookup"><span data-stu-id="208e3-135">24</span></span> |
> | <span data-ttu-id="208e3-136">CS1 (o CE1)</span><span class="sxs-lookup"><span data-stu-id="208e3-136">CS1 (or CE1)</span></span> | <span data-ttu-id="208e3-137">26</span><span class="sxs-lookup"><span data-stu-id="208e3-137">26</span></span> |
> | <span data-ttu-id="208e3-138">SCLK (o SCK)</span><span class="sxs-lookup"><span data-stu-id="208e3-138">SCLK (or SCK)</span></span> | <span data-ttu-id="208e3-139">23</span><span class="sxs-lookup"><span data-stu-id="208e3-139">23</span></span> |
> | <span data-ttu-id="208e3-140">PERMISOS</span><span class="sxs-lookup"><span data-stu-id="208e3-140">MISO</span></span> | <span data-ttu-id="208e3-141">21</span><span class="sxs-lookup"><span data-stu-id="208e3-141">21</span></span> |
> | <span data-ttu-id="208e3-142">MOSI</span><span class="sxs-lookup"><span data-stu-id="208e3-142">MOSI</span></span> | <span data-ttu-id="208e3-143">19</span><span class="sxs-lookup"><span data-stu-id="208e3-143">19</span></span> |
> | <span data-ttu-id="208e3-144">RXD</span><span class="sxs-lookup"><span data-stu-id="208e3-144">RXD</span></span> | <span data-ttu-id="208e3-145">10</span><span class="sxs-lookup"><span data-stu-id="208e3-145">10</span></span> |
> | <span data-ttu-id="208e3-146">TXD</span><span class="sxs-lookup"><span data-stu-id="208e3-146">TXD</span></span> | <span data-ttu-id="208e3-147">8</span><span class="sxs-lookup"><span data-stu-id="208e3-147">8</span></span> |

#### <a name="minnowboard-max"></a><span data-ttu-id="208e3-148">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="208e3-148">Minnowboard Max</span></span>

![Diagrama de pines](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="208e3-150">Definir PIN</span><span class="sxs-lookup"><span data-stu-id="208e3-150">Pin Define</span></span> | <span data-ttu-id="208e3-151">Número PIN correspondiente</span><span class="sxs-lookup"><span data-stu-id="208e3-151">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="208e3-152">GPIO \* _donde \* hace referencia a [0,9]_</span><span class="sxs-lookup"><span data-stu-id="208e3-152">GPIO\* _where \* refers to [0, 9]_</span></span>  | <span data-ttu-id="208e3-153">*Consulte el diagrama de pines*</span><span class="sxs-lookup"><span data-stu-id="208e3-153">*refer to pinout diagram*</span></span> |
> | <span data-ttu-id="208e3-154">FICHERO</span><span class="sxs-lookup"><span data-stu-id="208e3-154">SCL</span></span> | <span data-ttu-id="208e3-155">13</span><span class="sxs-lookup"><span data-stu-id="208e3-155">13</span></span> |
> | <span data-ttu-id="208e3-156">EMPAQUETADO</span><span class="sxs-lookup"><span data-stu-id="208e3-156">SDA</span></span> | <span data-ttu-id="208e3-157">15</span><span class="sxs-lookup"><span data-stu-id="208e3-157">15</span></span> |
> | <span data-ttu-id="208e3-158">CS0 (o CE0 o SS)</span><span class="sxs-lookup"><span data-stu-id="208e3-158">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="208e3-159">5</span><span class="sxs-lookup"><span data-stu-id="208e3-159">5</span></span> |
> | <span data-ttu-id="208e3-160">SCLK (o SCK)</span><span class="sxs-lookup"><span data-stu-id="208e3-160">SCLK  (or SCK)</span></span>| <span data-ttu-id="208e3-161">11</span><span class="sxs-lookup"><span data-stu-id="208e3-161">11</span></span> |
> | <span data-ttu-id="208e3-162">PERMISOS</span><span class="sxs-lookup"><span data-stu-id="208e3-162">MISO</span></span> |<span data-ttu-id="208e3-163">7</span><span class="sxs-lookup"><span data-stu-id="208e3-163">7</span></span> |
> | <span data-ttu-id="208e3-164">MOSI</span><span class="sxs-lookup"><span data-stu-id="208e3-164">MOSI</span></span> | <span data-ttu-id="208e3-165">9</span><span class="sxs-lookup"><span data-stu-id="208e3-165">9</span></span> |
> | <span data-ttu-id="208e3-166">CTS1</span><span class="sxs-lookup"><span data-stu-id="208e3-166">CTS1</span></span> | <span data-ttu-id="208e3-167">10</span><span class="sxs-lookup"><span data-stu-id="208e3-167">10</span></span> |
> | <span data-ttu-id="208e3-168">RTS1</span><span class="sxs-lookup"><span data-stu-id="208e3-168">RTS1</span></span> | <span data-ttu-id="208e3-169">12</span><span class="sxs-lookup"><span data-stu-id="208e3-169">12</span></span> |
> | <span data-ttu-id="208e3-170">RX1</span><span class="sxs-lookup"><span data-stu-id="208e3-170">RX1</span></span> | <span data-ttu-id="208e3-171">8</span><span class="sxs-lookup"><span data-stu-id="208e3-171">8</span></span> |
> | <span data-ttu-id="208e3-172">TX1</span><span class="sxs-lookup"><span data-stu-id="208e3-172">TX1</span></span> | <span data-ttu-id="208e3-173">6</span><span class="sxs-lookup"><span data-stu-id="208e3-173">6</span></span> |
> | <span data-ttu-id="208e3-174">RX2</span><span class="sxs-lookup"><span data-stu-id="208e3-174">RX2</span></span> | <span data-ttu-id="208e3-175">19</span><span class="sxs-lookup"><span data-stu-id="208e3-175">19</span></span> |
> | <span data-ttu-id="208e3-176">TX2</span><span class="sxs-lookup"><span data-stu-id="208e3-176">TX2</span></span> | <span data-ttu-id="208e3-177">17</span><span class="sxs-lookup"><span data-stu-id="208e3-177">17</span></span> |


## <a name="common-problems"></a><span data-ttu-id="208e3-178">Problemas comunes</span><span class="sxs-lookup"><span data-stu-id="208e3-178">Common Problems</span></span>

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a><span data-ttu-id="208e3-179">No se encuentra la plantilla de proyecto visual C++ "Arduino cableado Application" en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="208e3-179">Can't find "Arduino Wiring Application" Visual C++ project template in Visual Studio</span></span>

<span data-ttu-id="208e3-180">**Causa**: la extensión de plantillas de proyecto de Windows IOT para Visual Studio no está instalada.</span><span class="sxs-lookup"><span data-stu-id="208e3-180">**Cause**: The Windows IoT Project Templates extension for Visual Studio is not installed.</span></span>

<span data-ttu-id="208e3-181">**Solución**: debe instalar la extensión de Visual Studio para las plantillas de proyecto de Windows IOT antes de poder crear proyectos de cableado de Arduino en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="208e3-181">**Solution**: You must install the Visual Studio Extension for Windows IoT Project Templates before you can create Arduino Wiring projects in Visual Studio.</span></span> <span data-ttu-id="208e3-182">Vaya a la [Página de la extensión de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la galería de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="208e3-182">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>

### <a name="error-identifier-not-found-when-calling-a-function"></a><span data-ttu-id="208e3-183">ERROR: "no se encontró el identificador" al llamar a una función</span><span class="sxs-lookup"><span data-stu-id="208e3-183">ERROR: "identifier not found" when calling a function</span></span>

<span data-ttu-id="208e3-184">**Causa**: este error se produce durante el proceso del enlazador cuando se invoca una función que aún no se ha declarado en el documento.</span><span class="sxs-lookup"><span data-stu-id="208e3-184">**Cause**: This error occurs during the linker process when a function is invoked that has not yet been declared in the document.</span></span>

<span data-ttu-id="208e3-185">**Solución**: en C++, todas las funciones deben declararse antes de que se invoquen.</span><span class="sxs-lookup"><span data-stu-id="208e3-185">**Solution**: In C++, all functions must be declared before they are invoked.</span></span> <span data-ttu-id="208e3-186">Si ha definido una función nueva en el archivo de boceto, la declaración o la implementación completa de la función debe estar por encima de cualquier intento de invocarla (normalmente en la parte superior del documento).</span><span class="sxs-lookup"><span data-stu-id="208e3-186">If you have defined a new function in your sketch file, either the declaration or the entire implementation of the function must be above any attempts to invoke it (typically at the top of the document).</span></span>

<span data-ttu-id="208e3-187">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="208e3-187">**Example**:</span></span>

<span data-ttu-id="208e3-188">El siguiente bloque de código generará el error "' myFunction ': no se encuentra el identificador"</span><span class="sxs-lookup"><span data-stu-id="208e3-188">The following block of code will raise the error "'myFunction': identifier not found"</span></span>

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

<span data-ttu-id="208e3-189">Hay dos soluciones.</span><span class="sxs-lookup"><span data-stu-id="208e3-189">There are two solutions.</span></span> <span data-ttu-id="208e3-190">En primer lugar, puede declarar la función por encima de cualquier invocación.</span><span class="sxs-lookup"><span data-stu-id="208e3-190">First, you may declare the function above any invocations.</span></span> <span data-ttu-id="208e3-191">Normalmente, esta declaración se realiza en la parte superior del archivo.</span><span class="sxs-lookup"><span data-stu-id="208e3-191">Typically, this declaration is done at the top of the file.</span></span>

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

<span data-ttu-id="208e3-192">Como alternativa, puede trasladar toda la implementación de la función por encima de cualquier invocación.</span><span class="sxs-lookup"><span data-stu-id="208e3-192">Alternatively, you can move the entire implementation of the function above any invocations.</span></span> <span data-ttu-id="208e3-193">Esto tiene el efecto de declarar y definir la función al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="208e3-193">This has the effect of both declaring and defining the function at the same time.</span></span>

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a><span data-ttu-id="208e3-194">Mi solución se bloquea infinitamente al inicializarse</span><span class="sxs-lookup"><span data-stu-id="208e3-194">My solution hangs infinitely when being initialized</span></span>

<span data-ttu-id="208e3-195">Existe un problema conocido que puede provocar que una C++ solución se bloquee infinitamente (interbloqueo) al inicializarse.</span><span class="sxs-lookup"><span data-stu-id="208e3-195">There is a known issue which can cause a C++ solution to hang infinitely (deadlock) when being initialized.</span></span> <span data-ttu-id="208e3-196">Es posible que experimente este tipo de problema si observa que la solución parece dejar de responder indefinidamente y no puede usar el depurador para "interrumpir" en las secciones de configuración () o bucle () de la aplicación de cableado de Arduino.</span><span class="sxs-lookup"><span data-stu-id="208e3-196">You may be experiencing this type of issue if you find that your solution appears to hang forever and you are unable to use the debugger to 'break in' to any statement in the setup() or loop() sections of your Arduino Wiring application.</span></span>

<span data-ttu-id="208e3-197">**Causa**: se está creando un objeto o se está llamando a una función que conduce a una acción asyncronous antes de que la solución termine de inicializarse.</span><span class="sxs-lookup"><span data-stu-id="208e3-197">**Cause**: An object is being created or a function is being called which leads to an asyncronous action before the solution has finished initializing.</span></span> <span data-ttu-id="208e3-198">Probablemente se deba a que el constructor de un objeto llama a una función de la API como `pinMode`.</span><span class="sxs-lookup"><span data-stu-id="208e3-198">It is likely caused from an object's constructor calling an API function like `pinMode`.</span></span>

<span data-ttu-id="208e3-199">**Solución**: mueva cualquier constructor de objetos y las llamadas de función fuera de la sección de inicialización del código y al bloque `setup()`.</span><span class="sxs-lookup"><span data-stu-id="208e3-199">**Solution**: Move any object constructors and function calls away from the initialization section of code and into the `setup()` block.</span></span>

<span data-ttu-id="208e3-200">**Ejemplo 1**:</span><span class="sxs-lookup"><span data-stu-id="208e3-200">**Example 1**:</span></span>

<span data-ttu-id="208e3-201">La ejecución de este boceto llama a una función llamada `setPinModes()` antes de que se haya inicializado la propia solución.</span><span class="sxs-lookup"><span data-stu-id="208e3-201">The execution of this sketch calls a function called `setPinModes()` before the solution itself has been initialized.</span></span> <span data-ttu-id="208e3-202">La solución parecerá ejecutarse, pero se bloqueará infinitamente.</span><span class="sxs-lookup"><span data-stu-id="208e3-202">The solution will appear to execute but will hang infinitely.</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="208e3-203">La solución se encuentra a continuación, simplemente hemos cambiado la ejecución de `setPinModes()` a la función `setup()`:</span><span class="sxs-lookup"><span data-stu-id="208e3-203">The solution is below, we've simply moved the execution of `setPinModes()` to the `setup()` function:</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="208e3-204">**Ejemplo 2**:</span><span class="sxs-lookup"><span data-stu-id="208e3-204">**Example 2**:</span></span>

<span data-ttu-id="208e3-205">La ejecución de este boceto crea un objeto en la pila antes de que se haya llamado a `setup()`.</span><span class="sxs-lookup"><span data-stu-id="208e3-205">The execution of this sketch creates an object on the stack before `setup()` has been called.</span></span> <span data-ttu-id="208e3-206">Puesto que el objeto llama a `pinMode` en su constructor, también se producirá un interbloqueo.</span><span class="sxs-lookup"><span data-stu-id="208e3-206">Since the object calls `pinMode` in its constructor, this will also cause a deadlock.</span></span> <span data-ttu-id="208e3-207">Se trata de un problema poco frecuente, pero puede producirse con objetos de ciertas bibliotecas (como la biblioteca `LiquidCrystal` Arduino).</span><span class="sxs-lookup"><span data-stu-id="208e3-207">This is an uncommon issue, but may occur with objects from certain libraries (like the Arduino `LiquidCrystal` library).</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

<span data-ttu-id="208e3-208">La solución se encuentra a continuación.</span><span class="sxs-lookup"><span data-stu-id="208e3-208">The solution is below.</span></span> <span data-ttu-id="208e3-209">Hemos cambiado el objeto a un puntero de objeto y se ha pasado la inicialización del objeto a `setup()`.</span><span class="sxs-lookup"><span data-stu-id="208e3-209">We've changed the object to an object pointer and moved the initialization of the object to `setup()`.</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a><span data-ttu-id="208e3-210">Usar `Serial.print()` y `Serial.println()`</span><span class="sxs-lookup"><span data-stu-id="208e3-210">Using `Serial.print()` and `Serial.println()`</span></span>

<span data-ttu-id="208e3-211">Muchos bocetos de Arduino usan `Serial` para imprimir datos en la consola serie (si se abren) o para escribir en las líneas serie (USB o TX/RX).</span><span class="sxs-lookup"><span data-stu-id="208e3-211">Many Arduino sketches use `Serial` to print data to the serial console (if opened) or to write to the serial lines (USB or tx/rx).</span></span> <span data-ttu-id="208e3-212">En versiones anteriores del rayo SDK, no se incluía compatibilidad con hardware `Serial`, por lo que proporcionamos una función `Log()` que se imprimirá en la ventana de salida del depurador en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="208e3-212">In prior versions of the Lightning SDK, Hardware `Serial` support wasn't included, so we provided a `Log()` function which will print to the debugger output window in Visual Studio.</span></span> <span data-ttu-id="208e3-213">`Serial.print*()` o `Serial.write()` tuvieron que quitarse.</span><span class="sxs-lookup"><span data-stu-id="208e3-213">`Serial.print*()` or `Serial.write()` had to be removed.</span></span>

<span data-ttu-id="208e3-214">Sin embargo, a partir de _Lightning SDK v 1.1.0_, hemos agregado compatibilidad con `Hardware Serial` y las funciones de `Serial.print*()` o `Serial.write()` son totalmente compatibles.</span><span class="sxs-lookup"><span data-stu-id="208e3-214">However, starting with _Lightning SDK v1.1.0_, we've added `Hardware Serial` support and both `Serial.print*()` or `Serial.write()` functions are fully supported.</span></span> <span data-ttu-id="208e3-215">Por lo tanto, si va a copiar un boceto creado para un Arduino, no necesitará reemplazar ninguna de estas referencias en serie en la versión de Windows IoT del boceto.</span><span class="sxs-lookup"><span data-stu-id="208e3-215">So, if you are copying a sketch built for an Arduino, you won't need to replace any of these Serial references in the Windows IoT version of the sketch.</span></span>

<span data-ttu-id="208e3-216">Además, hemos ampliado la funcionalidad de `Serial.print()` y `Serial.println()`para generar la salida en la ventana del depurador cuando se adjunta un depurador, además de escribir en las clavijas de serie del hardware.</span><span class="sxs-lookup"><span data-stu-id="208e3-216">Furthermore, we've extended the functionality of `Serial.print()` and `Serial.println()`, to output to the debugger window when a debugger is attached - in addition to writing to the hardware serial pins.</span></span>
<span data-ttu-id="208e3-217">La impresión de salida de depuración se establece como el valor predeterminado, ya que la lectura de la salida es lo que la mayoría de los usuarios querrán al ejecutar sus bocetos.</span><span class="sxs-lookup"><span data-stu-id="208e3-217">The debug output printing is set as the default since reading that output is what most users would want when running their sketches.</span></span> <span data-ttu-id="208e3-218">Sin embargo, esa funcionalidad también se puede deshabilitar; por ejemplo, para mejorar el rendimiento, simplemente llame a `Serial.enablePrintDebugOutput(false);` para deshabilitarlo en el boceto.</span><span class="sxs-lookup"><span data-stu-id="208e3-218">However, that functionality can be disabled as well; e.g. to improve performance, simply call `Serial.enablePrintDebugOutput(false);` to disable it in your sketch.</span></span> <span data-ttu-id="208e3-219">Para volver a habilitarla, llame a `Serial.enablePrintDebugOutput(true);`.</span><span class="sxs-lookup"><span data-stu-id="208e3-219">To re-enable it, call `Serial.enablePrintDebugOutput(true);`.</span></span> <span data-ttu-id="208e3-220">Estas llamadas no afectan a la escritura en las clavijas de serialización de hardware.</span><span class="sxs-lookup"><span data-stu-id="208e3-220">Writing to the hardware serial pins is not affected by those calls.</span></span>

<span data-ttu-id="208e3-221">Tenga en cuenta que no es necesario que conecte ningún periférico a los Pin serie, como un FTDI, para obtener la salida enviada a la ventana del depurador.</span><span class="sxs-lookup"><span data-stu-id="208e3-221">Note, you do NOT need to attach any peripheral to your serial pins such as an FTDI, to get output sent to the debugger window.</span></span> <span data-ttu-id="208e3-222">Sin embargo, deberá asegurarse de que la ventana del depurador está abierta mientras se depura la aplicación.</span><span class="sxs-lookup"><span data-stu-id="208e3-222">However, you'll need to make sure the debugger window is open while your application is being debugged.</span></span>

![Salida del depurador](../media/ArduinoWiringPortingGuide/debugger_output.png)

<span data-ttu-id="208e3-224">Las plantillas de proyecto se han actualizado en la página de la [extensión de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) para habilitar el uso de hardware `Serial` de la caja.</span><span class="sxs-lookup"><span data-stu-id="208e3-224">The project templates have been updated on the [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to enable using Hardware `Serial` out of the box.</span></span> <span data-ttu-id="208e3-225">Sin embargo, si la aplicación de cableado de Arduino ya se ha creado con una versión anterior de la plantilla de proyecto, deberá 1) actualizar el proyecto a la versión más reciente de Lightning SDK, v 1.1.0 o posterior y 2) agregar la funcionalidad de dispositivo serie de hardware necesaria a su AppxManifest para poder usar `Serial`.</span><span class="sxs-lookup"><span data-stu-id="208e3-225">However, if your Arduino Wiring application has already been created using an older project template version, you'll need to 1) Upgrade your project to the latest Lightning SDK, v1.1.0 or later, and 2) add the required Hardware Serial device capability to your AppxManifest to be able to use `Serial`.</span></span>

### <a name="hardware-serial-device-capability-requirements"></a><span data-ttu-id="208e3-226">Requisitos de funcionalidad del dispositivo serie de hardware</span><span class="sxs-lookup"><span data-stu-id="208e3-226">Hardware Serial device capability requirements</span></span>

<span data-ttu-id="208e3-227">La funcionalidad de serie de hardware en Windows 10 IoT core requiere declaraciones de funcionalidad de dispositivo agregadas al manifiesto AppX.</span><span class="sxs-lookup"><span data-stu-id="208e3-227">Hardware Serial functionality in Windows 10 IoT Core requires device capability declarations added to the AppX manifest.</span></span>

<span data-ttu-id="208e3-228">Busque el archivo `Package.appxmanifest` en el proyecto; para ello, escriba el nombre del archivo en el explorador de soluciones.</span><span class="sxs-lookup"><span data-stu-id="208e3-228">Find the file `Package.appxmanifest` in your project, by typing the file name in the solution explorer.</span></span> <span data-ttu-id="208e3-229">A continuación, haga clic con el botón derecho en el archivo y elija "abrir con...".</span><span class="sxs-lookup"><span data-stu-id="208e3-229">Then, right click the file and choose 'Open With...'.</span></span> <span data-ttu-id="208e3-230">Elija editor XML (texto) y haga clic en "Aceptar".</span><span class="sxs-lookup"><span data-stu-id="208e3-230">Choose 'XML (Text) Editor' and click 'OK'.</span></span>

![Actualizando package. appxmanifest](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

<span data-ttu-id="208e3-232">En el editor del archivo de manifiesto appx, agregue el `serialcommunication` DeviceCapability al proyecto como en el siguiente fragmento de código XML:</span><span class="sxs-lookup"><span data-stu-id="208e3-232">In the appx manifest file editor, add the `serialcommunication` DeviceCapability to your project as in the following XML snippet:</span></span>

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a><span data-ttu-id="208e3-233">Actualice el proyecto a la versión más reciente del SDK de Lightning</span><span class="sxs-lookup"><span data-stu-id="208e3-233">Upgrade your project to the latest Lightning SDK</span></span>

<span data-ttu-id="208e3-234">Los proyectos de cableado de Arduino dependen del [paquete Nuget de Lightning SDK](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) para implementar las funciones y declaraciones de cableado Arduino necesarias, así como la interfaz con el controlador de Lightning.</span><span class="sxs-lookup"><span data-stu-id="208e3-234">The Arduino Wiring projects depend on the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) to implement the required Arduino Wiring functions and declarations as well as interface with the Lightning driver.</span></span> <span data-ttu-id="208e3-235">El último SDK de Lightning contendrá las mejoras y correcciones de errores más recientes.</span><span class="sxs-lookup"><span data-stu-id="208e3-235">The latest Lightning SDK will contain the latest improvements and bug fixes.</span></span> <span data-ttu-id="208e3-236">Para actualizar a la versión más reciente de Lightning SDK, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="208e3-236">To upgrade to the latest Lightning SDK, follow these steps:</span></span>

- <span data-ttu-id="208e3-237">En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y haga clic en "administrar paquetes Nuget".</span><span class="sxs-lookup"><span data-stu-id="208e3-237">In the Solution Explorer, right click on your project and click 'Manage Nuget Packages...'</span></span>
- <span data-ttu-id="208e3-238">En el administrador de paquetes NuGet, vaya a la pestaña ' instalado '. Debería ver el paquete Microsoft. IoT. Lightning instalado</span><span class="sxs-lookup"><span data-stu-id="208e3-238">In the NuGet Package Manager, go to the 'Installed' tab. You should see the Microsoft.IoT.Lightning package installed</span></span>
- <span data-ttu-id="208e3-239">Las versiones disponibles se enumerarán en el cuadro combinado ' version '.</span><span class="sxs-lookup"><span data-stu-id="208e3-239">Available versions will be listed inside the 'Version' combobox.</span></span>
- <span data-ttu-id="208e3-240">Elija la versión más reciente y haga clic en "actualizar" para actualizar el paquete.</span><span class="sxs-lookup"><span data-stu-id="208e3-240">Choose the latest version, and click 'Update' to update your package.</span></span>
- <span data-ttu-id="208e3-241">Tenga en cuenta que, para actualizar a una versión preliminar, asegúrese de activar la casilla "incluir versión preliminar" también.</span><span class="sxs-lookup"><span data-stu-id="208e3-241">Notice, to upgrade to a prerelease version, make sure to check the 'Include prerelease' checkbox as well.</span></span>

![Administrador de paquetes NuGet](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
