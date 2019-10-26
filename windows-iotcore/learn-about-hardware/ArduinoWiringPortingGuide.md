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
# <a name="arduino-wiring-porting-guide"></a>Guía de migración de cableado de Arduino

Los bocetos y las bibliotecas de Arduino se pueden copiar y pegar en un proyecto de cableado de Arduino dentro de Visual Studio y ejecutarse en Raspberry pi 2, Raspberry PI 3 o Minnowboard Max. A veces, se deben realizar pequeñas modificaciones para estos archivos con el fin de que sean más compatibles con el entorno de Windows o con el panel con el que está trabajando. En esta guía se tratan las modificaciones y los problemas comunes que se pueden tener en la implementación de proyectos de cableado de Arduino.

## <a name="porting"></a>Migración

### <a name="updating-pins"></a>Actualizar PIN

Podría ir sin decir, pero muchos bocetos y bibliotecas (especialmente los de las pletinas de Arduino) pueden contener referencias a clavijas de conector específicas para dispositivos Arduino. Querrá personalizar los bocetos para usar las clavijas del conector adecuadas para el dispositivo en el que está trabajando y la configuración que está usando.

En última instancia, el cableado de Arduino requiere un número de PIN del conector físico para cualquier función que haga referencia a "clavijas". Estos números se pueden usar directamente, pero también se proporcionan algunos nombres de PIN predefinidos que corresponden a las clavijas del conector en paneles específicos.

Por ejemplo, el PIN del conector físico 29 en un Raspberry pi 2 y 3 también se conoce como `GPIO5`. Puede establecer el PIN de GPIO 5 en un estado alto en un Raspberry pi 2 y 3 con cualquiera de los siguientes comandos:
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

o

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

Los nombres de anclaje predefinidos se pueden encontrar en [pins_arduino. h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) y se incluyen en cada proyecto de cableado de Arduino, pero, dado que habrá diferentes clavijas del conector físico disponibles en función de la configuración de hardware que se está creando para, también se incluye una tabla. Aquí se describen los nombres de los PIN que están disponibles para cada dispositivo.

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 y 3

![Diagrama de pines](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | Definir PIN | Número PIN correspondiente|
> |-------------|----------|
> | LED_BUILTIN | *LED incorporado* |
> | GPIO * _donde * hace referencia a [0, 27]_ | *Consulte el diagrama de pines* |
> | GCLK | 7 |
> | GEN * _, donde * hace referencia a [0, 5]_ | \* Consulte el diagrama de pines |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (o CE0 o SS) | 24 |
> | CS1 (o CE1) | 26 |
> | SCLK (o SCK) | 23 |
> | PERMISOS | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard Max

![Diagrama de pines](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | Definir PIN | Número PIN correspondiente|
> |-------------|----------|
> | GPIO * _donde * hace referencia a [0,9]_  | *Consulte el diagrama de pines* |
> | FICHERO | 13 |
> | EMPAQUETADO | 15 |
> | CS0 (o CE0 o SS) | 5 |
> | SCLK (o SCK)| 11 |
> | PERMISOS |7 |
> | MOSI | 9 |
> | CTS1 | 10 |
> | RTS1 | 12 |
> | RX1 | 8 |
> | TX1 | 6 |
> | RX2 | 19 |
> | TX2 | 17 |


## <a name="common-problems"></a>Problemas comunes

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>No se encuentra la plantilla de proyecto visual C++ "Arduino cableado Application" en Visual Studio

**Causa**: la extensión de plantillas de proyecto de Windows IOT para Visual Studio no está instalada.

**Solución**: debe instalar la extensión de Visual Studio para las plantillas de proyecto de Windows IOT antes de poder crear proyectos de cableado de Arduino en Visual Studio. Vaya a la [Página de la extensión de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la galería de Visual Studio.

### <a name="error-identifier-not-found-when-calling-a-function"></a>ERROR: "no se encontró el identificador" al llamar a una función

**Causa**: este error se produce durante el proceso del enlazador cuando se invoca una función que aún no se ha declarado en el documento.

**Solución**: en C++, todas las funciones deben declararse antes de que se invoquen. Si ha definido una función nueva en el archivo de boceto, la declaración o la implementación completa de la función debe estar por encima de cualquier intento de invocarla (normalmente en la parte superior del documento).

**Ejemplo**:

El siguiente bloque de código generará el error "' myFunction ': no se encuentra el identificador"

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

Hay dos soluciones. En primer lugar, puede declarar la función por encima de cualquier invocación. Normalmente, esta declaración se realiza en la parte superior del archivo.

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

Como alternativa, puede trasladar toda la implementación de la función por encima de cualquier invocación. Esto tiene el efecto de declarar y definir la función al mismo tiempo.

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

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>Mi solución se bloquea infinitamente al inicializarse

Existe un problema conocido que puede provocar que una C++ solución se bloquee infinitamente (interbloqueo) al inicializarse. Es posible que experimente este tipo de problema si observa que la solución parece dejar de responder indefinidamente y no puede usar el depurador para "interrumpir" en las secciones de configuración () o bucle () de la aplicación de cableado de Arduino.

**Causa**: se está creando un objeto o se está llamando a una función que conduce a una acción asyncronous antes de que la solución termine de inicializarse. Probablemente se deba a que el constructor de un objeto llama a una función de la API como `pinMode`.

**Solución**: mueva cualquier constructor de objetos y las llamadas de función fuera de la sección de inicialización del código y al bloque `setup()`.

**Ejemplo 1**:

La ejecución de este boceto llama a una función llamada `setPinModes()` antes de que se haya inicializado la propia solución. La solución parecerá ejecutarse, pero se bloqueará infinitamente.

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

La solución se encuentra a continuación, simplemente hemos cambiado la ejecución de `setPinModes()` a la función `setup()`:

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

**Ejemplo 2**:

La ejecución de este boceto crea un objeto en la pila antes de que se haya llamado a `setup()`. Puesto que el objeto llama a `pinMode` en su constructor, también se producirá un interbloqueo. Se trata de un problema poco frecuente, pero puede producirse con objetos de ciertas bibliotecas (como la biblioteca `LiquidCrystal` Arduino).

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

La solución se encuentra a continuación. Hemos cambiado el objeto a un puntero de objeto y se ha pasado la inicialización del objeto a `setup()`.

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

### <a name="using-serialprint-and-serialprintln"></a>Usar `Serial.print()` y `Serial.println()`

Muchos bocetos de Arduino usan `Serial` para imprimir datos en la consola serie (si se abren) o para escribir en las líneas serie (USB o TX/RX). En versiones anteriores del rayo SDK, no se incluía compatibilidad con hardware `Serial`, por lo que proporcionamos una función `Log()` que se imprimirá en la ventana de salida del depurador en Visual Studio. `Serial.print*()` o `Serial.write()` tuvieron que quitarse.

Sin embargo, a partir de _Lightning SDK v 1.1.0_, hemos agregado compatibilidad con `Hardware Serial` y las funciones de `Serial.print*()` o `Serial.write()` son totalmente compatibles. Por lo tanto, si va a copiar un boceto creado para un Arduino, no necesitará reemplazar ninguna de estas referencias en serie en la versión de Windows IoT del boceto.

Además, hemos ampliado la funcionalidad de `Serial.print()` y `Serial.println()`para generar la salida en la ventana del depurador cuando se adjunta un depurador, además de escribir en las clavijas de serie del hardware.
La impresión de salida de depuración se establece como el valor predeterminado, ya que la lectura de la salida es lo que la mayoría de los usuarios querrán al ejecutar sus bocetos. Sin embargo, esa funcionalidad también se puede deshabilitar; por ejemplo, para mejorar el rendimiento, simplemente llame a `Serial.enablePrintDebugOutput(false);` para deshabilitarlo en el boceto. Para volver a habilitarla, llame a `Serial.enablePrintDebugOutput(true);`. Estas llamadas no afectan a la escritura en las clavijas de serialización de hardware.

Tenga en cuenta que no es necesario que conecte ningún periférico a los Pin serie, como un FTDI, para obtener la salida enviada a la ventana del depurador. Sin embargo, deberá asegurarse de que la ventana del depurador está abierta mientras se depura la aplicación.

![Salida del depurador](../media/ArduinoWiringPortingGuide/debugger_output.png)

Las plantillas de proyecto se han actualizado en la página de la [extensión de plantillas de proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472) para habilitar el uso de hardware `Serial` de la caja. Sin embargo, si la aplicación de cableado de Arduino ya se ha creado con una versión anterior de la plantilla de proyecto, deberá 1) actualizar el proyecto a la versión más reciente de Lightning SDK, v 1.1.0 o posterior y 2) agregar la funcionalidad de dispositivo serie de hardware necesaria a su AppxManifest para poder usar `Serial`.

### <a name="hardware-serial-device-capability-requirements"></a>Requisitos de funcionalidad del dispositivo serie de hardware

La funcionalidad de serie de hardware en Windows 10 IoT core requiere declaraciones de funcionalidad de dispositivo agregadas al manifiesto AppX.

Busque el archivo `Package.appxmanifest` en el proyecto; para ello, escriba el nombre del archivo en el explorador de soluciones. A continuación, haga clic con el botón derecho en el archivo y elija "abrir con...". Elija editor XML (texto) y haga clic en "Aceptar".

![Actualizando package. appxmanifest](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

En el editor del archivo de manifiesto appx, agregue el `serialcommunication` DeviceCapability al proyecto como en el siguiente fragmento de código XML:

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>Actualice el proyecto a la versión más reciente del SDK de Lightning

Los proyectos de cableado de Arduino dependen del [paquete Nuget de Lightning SDK](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) para implementar las funciones y declaraciones de cableado Arduino necesarias, así como la interfaz con el controlador de Lightning. El último SDK de Lightning contendrá las mejoras y correcciones de errores más recientes. Para actualizar a la versión más reciente de Lightning SDK, siga estos pasos:

- En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y haga clic en "administrar paquetes Nuget".
- En el administrador de paquetes NuGet, vaya a la pestaña ' instalado '. Debería ver el paquete Microsoft. IoT. Lightning instalado
- Las versiones disponibles se enumerarán en el cuadro combinado ' version '.
- Elija la versión más reciente y haga clic en "actualizar" para actualizar el paquete.
- Tenga en cuenta que, para actualizar a una versión preliminar, asegúrese de activar la casilla "incluir versión preliminar" también.

![Administrador de paquetes NuGet](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
