---
title: Guía de migración de cableado de Arduino
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las modificaciones y problemas comunes que surgen al implementar proyectos de conexión de Arduino.
keywords: migración de Windows iot, Arduino, cables, Visual Studio
ms.openlocfilehash: 9b1d54807c21a54d8186d7f7ddabc31f16d3dab3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514311"
---
# <a name="arduino-wiring-porting-guide"></a><span data-ttu-id="76e44-104">Guía de migración de cableado de Arduino</span><span class="sxs-lookup"><span data-stu-id="76e44-104">Arduino Wiring Porting Guide</span></span>

<span data-ttu-id="76e44-105">Arduino cableado Bocetos y las bibliotecas se pueden copiar y pegar en un proyecto de cableado de Arduino en Visual Studio y ejecutar en Raspberry Pi 2, Raspberry Pi 3 o Minnowboard Max.</span><span class="sxs-lookup"><span data-stu-id="76e44-105">Arduino Wiring sketches and libraries can be copy/pasted into an Arduino Wiring project inside Visual Studio and run on Raspberry Pi 2, Raspberry Pi 3 or Minnowboard Max.</span></span> <span data-ttu-id="76e44-106">A veces hay ligeras modificaciones que deben realizarse a estos archivos para que sean más compatibles con el entorno de Windows o el panel que está trabajando.</span><span class="sxs-lookup"><span data-stu-id="76e44-106">Sometimes there are slight modifications that need to be made to these files in order to make them more compatible with the Windows environment, or the board you are working with.</span></span> <span data-ttu-id="76e44-107">Esta guía tratará dichas modificaciones, así como los problemas comunes que pueden surgir al implementar proyectos de conexión de Arduino.</span><span class="sxs-lookup"><span data-stu-id="76e44-107">This guide will cover those modifications as well as common issues that you may run into when deploying Arduino Wiring projects.</span></span>

## <a name="porting"></a><span data-ttu-id="76e44-108">Migración</span><span class="sxs-lookup"><span data-stu-id="76e44-108">Porting</span></span>

### <a name="updating-pins"></a><span data-ttu-id="76e44-109">Actualizar PIN</span><span class="sxs-lookup"><span data-stu-id="76e44-109">Updating Pins</span></span>

<span data-ttu-id="76e44-110">Quizás dé como resultado no sea necesario decirlo, pero muchas Bocetos y bibliotecas (especialmente las de shields de arduino) pueden contener referencias a las clavijas del conector específico para los dispositivos de Arduino.</span><span class="sxs-lookup"><span data-stu-id="76e44-110">It might go without saying, but many sketches and libraries (especially those for arduino shields) may contain references to specific connector pins for Arduino devices.</span></span> <span data-ttu-id="76e44-111">Desea personalizar los bocetos para usar las clavijas del conector adecuado para el dispositivo que está trabajando y la configuración que usa.</span><span class="sxs-lookup"><span data-stu-id="76e44-111">You'll want to customize your sketches to use the appropriate connector pins for the device you are working on and the configuration you are using.</span></span>

<span data-ttu-id="76e44-112">Conexión de Arduino en última instancia se requiere un número pin de conector físico para las funciones que hacen referencia a 'PIN'.</span><span class="sxs-lookup"><span data-stu-id="76e44-112">Arduino Wiring ultimately requires a physical connector pin number for any functions that refer to 'pins'.</span></span> <span data-ttu-id="76e44-113">Puede usar estos números directamente, pero también hemos proporcionado algunos nombres de pin predefinidos que corresponden a las clavijas del conector en paneles específicos.</span><span class="sxs-lookup"><span data-stu-id="76e44-113">You can use these numbers directly, but we've also provided some pre-defined pin names which correspond to connector pins on specific boards.</span></span>

<span data-ttu-id="76e44-114">Por ejemplo, el pin de conector físico 29 en un Raspberry Pi 2 y 3 es también conocida como `GPIO5`.</span><span class="sxs-lookup"><span data-stu-id="76e44-114">For example, the physical connector pin 29 on a Raspberry Pi 2 and 3 is also known as `GPIO5`.</span></span> <span data-ttu-id="76e44-115">Puede establecer los pines GPIO 5 a un estado alta en un Raspberry Pi 2 y 3 mediante cualquiera de los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="76e44-115">You may set GPIO pin 5 to a HIGH state on a Raspberry Pi 2 and 3 by using either of the following commands:</span></span>
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

<span data-ttu-id="76e44-116">o bien</span><span class="sxs-lookup"><span data-stu-id="76e44-116">or</span></span>

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

<span data-ttu-id="76e44-117">Los nombres predefinidos pin pueden encontrarse en [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) y se incluye en cada proyecto de cableado de Arduino, pero, ya que habrá clavijas del conector físicos diferentes disponibles dependiendo de la configuración de hardware que se va a compilar para, hemos También incluye una tabla aquí para describir qué nombres pin están disponibles para cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="76e44-117">The pre-defined pin names can be found in [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) and included in every Arduino Wiring project, but since there will be different physical connector pins available depending on the hardware setup you are building for, we've also included a table here to describe which pin names are available for each device.</span></span>

#### <a name="raspberry-pi-2-and-3"></a><span data-ttu-id="76e44-118">Raspberry Pi 2 y 3</span><span class="sxs-lookup"><span data-stu-id="76e44-118">Raspberry Pi 2 and 3</span></span>

![Diagrama de PIN](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="76e44-120">Definir el PIN</span><span class="sxs-lookup"><span data-stu-id="76e44-120">Pin Define</span></span> | <span data-ttu-id="76e44-121">Número de Pin correspondiente</span><span class="sxs-lookup"><span data-stu-id="76e44-121">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="76e44-122">LED_BUILTIN</span><span class="sxs-lookup"><span data-stu-id="76e44-122">LED_BUILTIN</span></span> | *<span data-ttu-id="76e44-123">incorporar LED</span><span class="sxs-lookup"><span data-stu-id="76e44-123">onboard LED</span></span>* |
> | <span data-ttu-id="76e44-124">GPIO \* _donde \* se refiere a [0, 27]_</span><span class="sxs-lookup"><span data-stu-id="76e44-124">GPIO\* _where \* refers to [0, 27]_</span></span> | *<span data-ttu-id="76e44-125">consulte el diagrama de PIN</span><span class="sxs-lookup"><span data-stu-id="76e44-125">refer to pinout diagram</span></span>* |
> | <span data-ttu-id="76e44-126">GCLK</span><span class="sxs-lookup"><span data-stu-id="76e44-126">GCLK</span></span> | <span data-ttu-id="76e44-127">7</span><span class="sxs-lookup"><span data-stu-id="76e44-127">7</span></span> |
> | <span data-ttu-id="76e44-128">GEN \* _donde \* se refiere a [0, 5]_</span><span class="sxs-lookup"><span data-stu-id="76e44-128">GEN\* _where \* refers to [0, 5]_</span></span> | <span data-ttu-id="76e44-129">\* consulte el diagrama de PIN</span><span class="sxs-lookup"><span data-stu-id="76e44-129">\*refer to pinout diagram</span></span> |
> | <span data-ttu-id="76e44-130">SCL1</span><span class="sxs-lookup"><span data-stu-id="76e44-130">SCL1</span></span> | <span data-ttu-id="76e44-131">5</span><span class="sxs-lookup"><span data-stu-id="76e44-131">5</span></span> |
> | <span data-ttu-id="76e44-132">SDA1</span><span class="sxs-lookup"><span data-stu-id="76e44-132">SDA1</span></span> | <span data-ttu-id="76e44-133">3</span><span class="sxs-lookup"><span data-stu-id="76e44-133">3</span></span> |
> | <span data-ttu-id="76e44-134">CS0 (o CE0 o SS)</span><span class="sxs-lookup"><span data-stu-id="76e44-134">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="76e44-135">24</span><span class="sxs-lookup"><span data-stu-id="76e44-135">24</span></span> |
> | <span data-ttu-id="76e44-136">CS1 (o CE1)</span><span class="sxs-lookup"><span data-stu-id="76e44-136">CS1 (or CE1)</span></span> | <span data-ttu-id="76e44-137">26</span><span class="sxs-lookup"><span data-stu-id="76e44-137">26</span></span> |
> | <span data-ttu-id="76e44-138">Bloq Despl (o SCK)</span><span class="sxs-lookup"><span data-stu-id="76e44-138">SCLK (or SCK)</span></span> | <span data-ttu-id="76e44-139">23</span><span class="sxs-lookup"><span data-stu-id="76e44-139">23</span></span> |
> | <span data-ttu-id="76e44-140">MISO</span><span class="sxs-lookup"><span data-stu-id="76e44-140">MISO</span></span> | <span data-ttu-id="76e44-141">21</span><span class="sxs-lookup"><span data-stu-id="76e44-141">21</span></span> |
> | <span data-ttu-id="76e44-142">MOSI</span><span class="sxs-lookup"><span data-stu-id="76e44-142">MOSI</span></span> | <span data-ttu-id="76e44-143">19</span><span class="sxs-lookup"><span data-stu-id="76e44-143">19</span></span> |
> | <span data-ttu-id="76e44-144">RXD</span><span class="sxs-lookup"><span data-stu-id="76e44-144">RXD</span></span> | <span data-ttu-id="76e44-145">10</span><span class="sxs-lookup"><span data-stu-id="76e44-145">10</span></span> |
> | <span data-ttu-id="76e44-146">TXD</span><span class="sxs-lookup"><span data-stu-id="76e44-146">TXD</span></span> | <span data-ttu-id="76e44-147">8</span><span class="sxs-lookup"><span data-stu-id="76e44-147">8</span></span> |

#### <a name="minnowboard-max"></a><span data-ttu-id="76e44-148">Minnowboard máx.</span><span class="sxs-lookup"><span data-stu-id="76e44-148">Minnowboard Max</span></span>

![Diagrama de PIN](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="76e44-150">Definir el PIN</span><span class="sxs-lookup"><span data-stu-id="76e44-150">Pin Define</span></span> | <span data-ttu-id="76e44-151">Número de Pin correspondiente</span><span class="sxs-lookup"><span data-stu-id="76e44-151">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="76e44-152">GPIO \* _donde \* se refiere a [0, 9]_</span><span class="sxs-lookup"><span data-stu-id="76e44-152">GPIO\* _where \* refers to [0, 9]_</span></span>  | *<span data-ttu-id="76e44-153">consulte el diagrama de PIN</span><span class="sxs-lookup"><span data-stu-id="76e44-153">refer to pinout diagram</span></span>* |
> | <span data-ttu-id="76e44-154">SCL</span><span class="sxs-lookup"><span data-stu-id="76e44-154">SCL</span></span> | <span data-ttu-id="76e44-155">13</span><span class="sxs-lookup"><span data-stu-id="76e44-155">13</span></span> |
> | <span data-ttu-id="76e44-156">SDA</span><span class="sxs-lookup"><span data-stu-id="76e44-156">SDA</span></span> | <span data-ttu-id="76e44-157">15</span><span class="sxs-lookup"><span data-stu-id="76e44-157">15</span></span> |
> | <span data-ttu-id="76e44-158">CS0 (o CE0 o SS)</span><span class="sxs-lookup"><span data-stu-id="76e44-158">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="76e44-159">5</span><span class="sxs-lookup"><span data-stu-id="76e44-159">5</span></span> |
> | <span data-ttu-id="76e44-160">Bloq Despl (o SCK)</span><span class="sxs-lookup"><span data-stu-id="76e44-160">SCLK  (or SCK)</span></span>| <span data-ttu-id="76e44-161">11</span><span class="sxs-lookup"><span data-stu-id="76e44-161">11</span></span> |
> | <span data-ttu-id="76e44-162">MISO</span><span class="sxs-lookup"><span data-stu-id="76e44-162">MISO</span></span> |<span data-ttu-id="76e44-163">7</span><span class="sxs-lookup"><span data-stu-id="76e44-163">7</span></span> |
> | <span data-ttu-id="76e44-164">MOSI</span><span class="sxs-lookup"><span data-stu-id="76e44-164">MOSI</span></span> | <span data-ttu-id="76e44-165">9</span><span class="sxs-lookup"><span data-stu-id="76e44-165">9</span></span> |
> | <span data-ttu-id="76e44-166">CTS1</span><span class="sxs-lookup"><span data-stu-id="76e44-166">CTS1</span></span> | <span data-ttu-id="76e44-167">10</span><span class="sxs-lookup"><span data-stu-id="76e44-167">10</span></span> |
> | <span data-ttu-id="76e44-168">RTS1</span><span class="sxs-lookup"><span data-stu-id="76e44-168">RTS1</span></span> | <span data-ttu-id="76e44-169">12</span><span class="sxs-lookup"><span data-stu-id="76e44-169">12</span></span> |
> | <span data-ttu-id="76e44-170">RX1</span><span class="sxs-lookup"><span data-stu-id="76e44-170">RX1</span></span> | <span data-ttu-id="76e44-171">8</span><span class="sxs-lookup"><span data-stu-id="76e44-171">8</span></span> |
> | <span data-ttu-id="76e44-172">TX1</span><span class="sxs-lookup"><span data-stu-id="76e44-172">TX1</span></span> | <span data-ttu-id="76e44-173">6</span><span class="sxs-lookup"><span data-stu-id="76e44-173">6</span></span> |
> | <span data-ttu-id="76e44-174">RX2</span><span class="sxs-lookup"><span data-stu-id="76e44-174">RX2</span></span> | <span data-ttu-id="76e44-175">19</span><span class="sxs-lookup"><span data-stu-id="76e44-175">19</span></span> |
> | <span data-ttu-id="76e44-176">TX2</span><span class="sxs-lookup"><span data-stu-id="76e44-176">TX2</span></span> | <span data-ttu-id="76e44-177">17</span><span class="sxs-lookup"><span data-stu-id="76e44-177">17</span></span> |


## <a name="common-problems"></a><span data-ttu-id="76e44-178">Problemas comunes</span><span class="sxs-lookup"><span data-stu-id="76e44-178">Common Problems</span></span>

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a><span data-ttu-id="76e44-179">No se puede encontrar Visual "Conexión de aplicación de Arduino" C++ plantilla de proyecto en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="76e44-179">Can't find "Arduino Wiring Application" Visual C++ project template in Visual Studio</span></span>

<span data-ttu-id="76e44-180">**Causa**: La extensión de plantillas de proyecto de IoT de Windows para Visual Studio no está instalada.</span><span class="sxs-lookup"><span data-stu-id="76e44-180">**Cause**: The Windows IoT Project Templates extension for Visual Studio is not installed.</span></span>

<span data-ttu-id="76e44-181">**Solución**: Debe instalar la extensión de Visual Studio para Windows IoT Project Templates antes de poder crear proyectos de conexión de Arduino en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76e44-181">**Solution**: You must install the Visual Studio Extension for Windows IoT Project Templates before you can create Arduino Wiring projects in Visual Studio.</span></span> <span data-ttu-id="76e44-182">Diríjase a [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la Galería de Visual Studio!</span><span class="sxs-lookup"><span data-stu-id="76e44-182">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>

### <a name="error-identifier-not-found-when-calling-a-function"></a><span data-ttu-id="76e44-183">ERROR: "identificador no encontrado" al llamar a una función</span><span class="sxs-lookup"><span data-stu-id="76e44-183">ERROR: "identifier not found" when calling a function</span></span>

<span data-ttu-id="76e44-184">**Causa**: Este error se produce durante el proceso del vinculador cuando se invoca una función que aún no se ha declarado en el documento.</span><span class="sxs-lookup"><span data-stu-id="76e44-184">**Cause**: This error occurs during the linker process when a function is invoked that has not yet been declared in the document.</span></span>

<span data-ttu-id="76e44-185">**Solución**: En C++, todas las funciones se deben declarar antes de que se invocan.</span><span class="sxs-lookup"><span data-stu-id="76e44-185">**Solution**: In C++, all functions must be declared before they are invoked.</span></span> <span data-ttu-id="76e44-186">Si ha definido una función nueva en el archivo de boceto, la declaración o en toda la implementación de la función debe ser por encima de cualquier intento de invocarlo (normalmente al principio del documento).</span><span class="sxs-lookup"><span data-stu-id="76e44-186">If you have defined a new function in your sketch file, either the declaration or the entire implementation of the function must be above any attempts to invoke it (typically at the top of the document).</span></span>

<span data-ttu-id="76e44-187">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="76e44-187">**Example**:</span></span>

<span data-ttu-id="76e44-188">El siguiente bloque de código, producirá el error "'myFunction': no se encontró el identificador"</span><span class="sxs-lookup"><span data-stu-id="76e44-188">The following block of code will raise the error "'myFunction': identifier not found"</span></span>

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

<span data-ttu-id="76e44-189">Hay dos soluciones.</span><span class="sxs-lookup"><span data-stu-id="76e44-189">There are two solutions.</span></span> <span data-ttu-id="76e44-190">En primer lugar, puede declarar la función por encima de cualquier invocación.</span><span class="sxs-lookup"><span data-stu-id="76e44-190">First, you may declare the function above any invocations.</span></span> <span data-ttu-id="76e44-191">Normalmente, esta declaración se realiza en la parte superior del archivo.</span><span class="sxs-lookup"><span data-stu-id="76e44-191">Typically, this declaration is done at the top of the file.</span></span>

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

<span data-ttu-id="76e44-192">Como alternativa, puede mover toda la implementación de la función por encima de cualquier invocación.</span><span class="sxs-lookup"><span data-stu-id="76e44-192">Alternatively, you can move the entire implementation of the function above any invocations.</span></span> <span data-ttu-id="76e44-193">Esto tiene el efecto de declarar y definir la función al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="76e44-193">This has the effect of both declaring and defining the function at the same time.</span></span>

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

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a><span data-ttu-id="76e44-194">Mi solución se bloquea indefinidamente al que se está inicializando</span><span class="sxs-lookup"><span data-stu-id="76e44-194">My solution hangs infinitely when being initialized</span></span>

<span data-ttu-id="76e44-195">Hay un problema conocido que puede provocar un C++ solución deje de responder indefinidamente (bloqueo) al que se va a inicializar.</span><span class="sxs-lookup"><span data-stu-id="76e44-195">There is a known issue which can cause a C++ solution to hang infinitely (deadlock) when being initialized.</span></span> <span data-ttu-id="76e44-196">Si encuentra que la solución parece que se bloquea indefinidamente y no puede utilizar el depurador se "interrumpan" a cualquier instrucción en las secciones de la aplicación de conexión de Arduino setup() o loop(), es posible que experimente este tipo de problema.</span><span class="sxs-lookup"><span data-stu-id="76e44-196">You may be experiencing this type of issue if you find that your solution appears to hang forever and you are unable to use the debugger to 'break in' to any statement in the setup() or loop() sections of your Arduino Wiring application.</span></span>

<span data-ttu-id="76e44-197">**Causa**: Se crea un objeto o una función se llama lo que da lugar a una acción asincrónica antes de que acabe de inicializarse la solución.</span><span class="sxs-lookup"><span data-stu-id="76e44-197">**Cause**: An object is being created or a function is being called which leads to an asyncronous action before the solution has finished initializing.</span></span> <span data-ttu-id="76e44-198">Es probable que deba desde un constructor de objeto llamada a una función de API como `pinMode`.</span><span class="sxs-lookup"><span data-stu-id="76e44-198">It is likely caused from an object's constructor calling an API function like `pinMode`.</span></span>

<span data-ttu-id="76e44-199">**Solución**: Cualquier objeto de constructores de movimiento y la función llamadas fuera de la sección de inicialización del código y en el `setup()` bloque.</span><span class="sxs-lookup"><span data-stu-id="76e44-199">**Solution**: Move any object constructors and function calls away from the initialization section of code and into the `setup()` block.</span></span>

<span data-ttu-id="76e44-200">**Ejemplo 1**:</span><span class="sxs-lookup"><span data-stu-id="76e44-200">**Example 1**:</span></span>

<span data-ttu-id="76e44-201">La ejecución de este esquema llama a una función denominada `setPinModes()` antes de que se ha inicializado la propia solución.</span><span class="sxs-lookup"><span data-stu-id="76e44-201">The execution of this sketch calls a function called `setPinModes()` before the solution itself has been initialized.</span></span> <span data-ttu-id="76e44-202">La solución aparecerá pero ejecutar bloquearse indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="76e44-202">The solution will appear to execute but will hang infinitely.</span></span>

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

<span data-ttu-id="76e44-203">La solución está por debajo, simplemente hemos pasamos la ejecución de `setPinModes()` a la `setup()` función:</span><span class="sxs-lookup"><span data-stu-id="76e44-203">The solution is below, we've simply moved the execution of `setPinModes()` to the `setup()` function:</span></span>

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

<span data-ttu-id="76e44-204">**Ejemplo 2**:</span><span class="sxs-lookup"><span data-stu-id="76e44-204">**Example 2**:</span></span>

<span data-ttu-id="76e44-205">La ejecución de este esquema crea un objeto en la pila antes `setup()` se ha llamado.</span><span class="sxs-lookup"><span data-stu-id="76e44-205">The execution of this sketch creates an object on the stack before `setup()` has been called.</span></span> <span data-ttu-id="76e44-206">Desde las llamadas de objeto `pinMode` en su constructor, esto hará que un interbloqueo.</span><span class="sxs-lookup"><span data-stu-id="76e44-206">Since the object calls `pinMode` in its constructor, this will also cause a deadlock.</span></span> <span data-ttu-id="76e44-207">Esto es un problema habitual, pero pueden producirse con objetos de ciertas bibliotecas (al igual que Arduino `LiquidCrystal` biblioteca).</span><span class="sxs-lookup"><span data-stu-id="76e44-207">This is an uncommon issue, but may occur with objects from certain libraries (like the Arduino `LiquidCrystal` library).</span></span>

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

<span data-ttu-id="76e44-208">La solución está por debajo.</span><span class="sxs-lookup"><span data-stu-id="76e44-208">The solution is below.</span></span> <span data-ttu-id="76e44-209">Hemos cambiado el objeto a un puntero de objeto y hemos movido la inicialización del objeto para `setup()`.</span><span class="sxs-lookup"><span data-stu-id="76e44-209">We've changed the object to an object pointer and moved the initialization of the object to `setup()`.</span></span>

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

### <a name="using-serialprint-and-serialprintln"></a><span data-ttu-id="76e44-210">Uso de `Serial.print()` y `Serial.println()`</span><span class="sxs-lookup"><span data-stu-id="76e44-210">Using `Serial.print()` and `Serial.println()`</span></span>

<span data-ttu-id="76e44-211">Usar muchos bocetos de Arduino `Serial` para imprimir los datos en la consola en serie (si está abierto) o para escribir en las líneas de serie (USB o recepción y transmisión).</span><span class="sxs-lookup"><span data-stu-id="76e44-211">Many Arduino sketches use `Serial` to print data to the serial console (if opened) or to write to the serial lines (USB or tx/rx).</span></span> <span data-ttu-id="76e44-212">En las versiones anteriores del SDK de rayos, Hardware `Serial` soporte técnico no incluido, por lo que nos proporciona un `Log()` ventana en Visual Studio de salida de función que se imprimirá en el depurador.</span><span class="sxs-lookup"><span data-stu-id="76e44-212">In prior versions of the Lightning SDK, Hardware `Serial` support wasn't included, so we provided a `Log()` function which will print to the debugger output window in Visual Studio.</span></span> `Serial.print*()` <span data-ttu-id="76e44-213">o `Serial.write()` tenía que quitarse.</span><span class="sxs-lookup"><span data-stu-id="76e44-213">or `Serial.write()` had to be removed.</span></span>

<span data-ttu-id="76e44-214">Sin embargo, a partir de _relámpago SDK v1.1.0_, hemos agregado `Hardware Serial` soporte técnico y ambos `Serial.print*()` o `Serial.write()` funciones son totalmente compatibles.</span><span class="sxs-lookup"><span data-stu-id="76e44-214">However, starting with _Lightning SDK v1.1.0_, we've added `Hardware Serial` support and both `Serial.print*()` or `Serial.write()` functions are fully supported.</span></span> <span data-ttu-id="76e44-215">Por lo tanto, si va a copiar un esbozo creado para Arduino, no tendrá que reemplazar cualquiera de estas referencias en la versión de Windows IoT del boceto de serie.</span><span class="sxs-lookup"><span data-stu-id="76e44-215">So, if you are copying a sketch built for an Arduino, you won't need to replace any of these Serial references in the Windows IoT version of the sketch.</span></span>

<span data-ttu-id="76e44-216">Además, nos hemos ampliado la funcionalidad de `Serial.print()` y `Serial.println()`, para enviar a la ventana del depurador cuando se adjunta un depurador - además de escribir en el PIN de serie del hardware.</span><span class="sxs-lookup"><span data-stu-id="76e44-216">Furthermore, we've extended the functionality of `Serial.print()` and `Serial.println()`, to output to the debugger window when a debugger is attached - in addition to writing to the hardware serial pins.</span></span>
<span data-ttu-id="76e44-217">La depuración de salida de impresión establecida como predeterminada desde la lectura de que el resultado es lo que los usuarios la mayoría querría cuando se está ejecutando los dibujos.</span><span class="sxs-lookup"><span data-stu-id="76e44-217">The debug output printing is set as the default since reading that output is what most users would want when running their sketches.</span></span> <span data-ttu-id="76e44-218">Sin embargo, se puede deshabilitar esta funcionalidad también; Por ejemplo, para mejorar el rendimiento, basta con llamar a `Serial.enablePrintDebugOutput(false);` para deshabilitarlo en el boceto.</span><span class="sxs-lookup"><span data-stu-id="76e44-218">However, that functionality can be disabled as well; e.g. to improve performance, simply call `Serial.enablePrintDebugOutput(false);` to disable it in your sketch.</span></span> <span data-ttu-id="76e44-219">Para volver a habilitarla, llame a `Serial.enablePrintDebugOutput(true);`.</span><span class="sxs-lookup"><span data-stu-id="76e44-219">To re-enable it, call `Serial.enablePrintDebugOutput(true);`.</span></span> <span data-ttu-id="76e44-220">Escribir en el PIN de serie del hardware no se ve afectado por las llamadas.</span><span class="sxs-lookup"><span data-stu-id="76e44-220">Writing to the hardware serial pins is not affected by those calls.</span></span>

<span data-ttu-id="76e44-221">Tenga en cuenta que no es necesario adjuntar cualquier periférico a sus PIN serie como un FTDI, para obtener el resultado enviado a la ventana del depurador.</span><span class="sxs-lookup"><span data-stu-id="76e44-221">Note, you do NOT need to attach any peripheral to your serial pins such as an FTDI, to get output sent to the debugger window.</span></span> <span data-ttu-id="76e44-222">Sin embargo, deberá asegurarse de que está abierta la ventana del depurador mientras se está depurando la aplicación.</span><span class="sxs-lookup"><span data-stu-id="76e44-222">However, you'll need to make sure the debugger window is open while your application is being debugged.</span></span>

![Salida del depurador](../media/ArduinoWiringPortingGuide/debugger_output.png)

<span data-ttu-id="76e44-224">Se han actualizado las plantillas de proyecto en el [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para habilitar el uso de Hardware `Serial` de fábrica.</span><span class="sxs-lookup"><span data-stu-id="76e44-224">The project templates have been updated on the [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to enable using Hardware `Serial` out of the box.</span></span> <span data-ttu-id="76e44-225">Sin embargo, si ya se ha creado la aplicación de conexión de Arduino con una versión anterior de plantilla de proyecto, necesitará 1) actualizar el proyecto al último SDK de rayos, v1.1.0 o versiones posteriores y (2) agregar la funcionalidad del dispositivo de serie del Hardware necesaria para su AppxManifest para poder usar `Serial`.</span><span class="sxs-lookup"><span data-stu-id="76e44-225">However, if your Arduino Wiring application has already been created using an older project template version, you'll need to 1) Upgrade your project to the latest Lightning SDK, v1.1.0 or later, and 2) add the required Hardware Serial device capability to your AppxManifest to be able to use `Serial`.</span></span>

### <a name="hardware-serial-device-capability-requirements"></a><span data-ttu-id="76e44-226">Requisitos de capacidad de serie del dispositivo de hardware</span><span class="sxs-lookup"><span data-stu-id="76e44-226">Hardware Serial device capability requirements</span></span>

<span data-ttu-id="76e44-227">Funcionalidad de serie de hardware en Windows 10 IoT Core requiere declaraciones de funcionalidades de dispositivo que agregó al manifiesto AppX.</span><span class="sxs-lookup"><span data-stu-id="76e44-227">Hardware Serial functionality in Windows 10 IoT Core requires device capability declarations added to the AppX manifest.</span></span>

<span data-ttu-id="76e44-228">Busque el archivo `Package.appxmanifest` en el proyecto, escriba el nombre de archivo en el Explorador de soluciones.</span><span class="sxs-lookup"><span data-stu-id="76e44-228">Find the file `Package.appxmanifest` in your project, by typing the file name in the solution explorer.</span></span> <span data-ttu-id="76e44-229">A continuación, a la derecha, haga clic en el archivo y elija 'Abrir con...'.</span><span class="sxs-lookup"><span data-stu-id="76e44-229">Then, right click the file and choose 'Open With...'.</span></span> <span data-ttu-id="76e44-230">Elija "Editor XML (texto)" y haga clic en 'Aceptar'.</span><span class="sxs-lookup"><span data-stu-id="76e44-230">Choose 'XML (Text) Editor' and click 'OK'.</span></span>

![Actualizando Package.appxmanifest](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

<span data-ttu-id="76e44-232">En el editor del archivo de manifiesto appx, agregue el `serialcommunication` DeviceCapability al proyecto como se muestra en el fragmento XML siguiente:</span><span class="sxs-lookup"><span data-stu-id="76e44-232">In the appx manifest file editor, add the `serialcommunication` DeviceCapability to your project as in the following XML snippet:</span></span>

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a><span data-ttu-id="76e44-233">Actualizar un proyecto al último SDK de rayo</span><span class="sxs-lookup"><span data-stu-id="76e44-233">Upgrade your project to the latest Lightning SDK</span></span>

<span data-ttu-id="76e44-234">Dependen de los proyectos de la conexión de Arduino los [paquete Nuget del SDK relámpago](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) para implementar las funciones necesarias de conexión de Arduino y declaraciones como así como interfaz con el controlador de rayo.</span><span class="sxs-lookup"><span data-stu-id="76e44-234">The Arduino Wiring projects depend on the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) to implement the required Arduino Wiring functions and declarations as well as interface with the Lightning driver.</span></span> <span data-ttu-id="76e44-235">El último SDK de rayo contendrá las últimas mejoras y correcciones de errores.</span><span class="sxs-lookup"><span data-stu-id="76e44-235">The latest Lightning SDK will contain the latest improvements and bug fixes.</span></span> <span data-ttu-id="76e44-236">Para actualizar al último SDK de rayos, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="76e44-236">To upgrade to the latest Lightning SDK, follow these steps:</span></span>

- <span data-ttu-id="76e44-237">En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y haga clic en 'Administrar paquetes Nuget...'</span><span class="sxs-lookup"><span data-stu-id="76e44-237">In the Solution Explorer, right click on your project and click 'Manage Nuget Packages...'</span></span>
- <span data-ttu-id="76e44-238">En el Administrador de paquetes de NuGet, vaya a la pestaña 'Instalar'. Debería ver el paquete Microsoft.IoT.Lightning instalado</span><span class="sxs-lookup"><span data-stu-id="76e44-238">In the NuGet Package Manager, go to the 'Installed' tab. You should see the Microsoft.IoT.Lightning package installed</span></span>
- <span data-ttu-id="76e44-239">Las versiones disponibles se mostrarán en el cuadro combinado de 'Version'.</span><span class="sxs-lookup"><span data-stu-id="76e44-239">Available versions will be listed inside the 'Version' combobox.</span></span>
- <span data-ttu-id="76e44-240">Elija la versión más reciente y haga clic en Actualizar para actualizar el paquete.</span><span class="sxs-lookup"><span data-stu-id="76e44-240">Choose the latest version, and click 'Update' to update your package.</span></span>
- <span data-ttu-id="76e44-241">Aviso para actualizar a una versión preliminar, asegúrese de activar la casilla "Incluir versión preliminar".</span><span class="sxs-lookup"><span data-stu-id="76e44-241">Notice, to upgrade to a prerelease version, make sure to check the 'Include prerelease' checkbox as well.</span></span>

![Administrador de paquetes de NuGet](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
