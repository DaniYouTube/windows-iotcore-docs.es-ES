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
# <a name="arduino-wiring-porting-guide"></a>Guía de migración de cableado de Arduino

Arduino cableado Bocetos y las bibliotecas se pueden copiar y pegar en un proyecto de cableado de Arduino en Visual Studio y ejecutar en Raspberry Pi 2, Raspberry Pi 3 o Minnowboard Max. A veces hay ligeras modificaciones que deben realizarse a estos archivos para que sean más compatibles con el entorno de Windows o el panel que está trabajando. Esta guía tratará dichas modificaciones, así como los problemas comunes que pueden surgir al implementar proyectos de conexión de Arduino.

## <a name="porting"></a>Migración

### <a name="updating-pins"></a>Actualizar PIN

Quizás dé como resultado no sea necesario decirlo, pero muchas Bocetos y bibliotecas (especialmente las de shields de arduino) pueden contener referencias a las clavijas del conector específico para los dispositivos de Arduino. Desea personalizar los bocetos para usar las clavijas del conector adecuado para el dispositivo que está trabajando y la configuración que usa.

Conexión de Arduino en última instancia se requiere un número pin de conector físico para las funciones que hacen referencia a 'PIN'. Puede usar estos números directamente, pero también hemos proporcionado algunos nombres de pin predefinidos que corresponden a las clavijas del conector en paneles específicos.

Por ejemplo, el pin de conector físico 29 en un Raspberry Pi 2 y 3 es también conocida como `GPIO5`. Puede establecer los pines GPIO 5 a un estado alta en un Raspberry Pi 2 y 3 mediante cualquiera de los siguientes comandos:
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

o bien

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

Los nombres predefinidos pin pueden encontrarse en [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) y se incluye en cada proyecto de cableado de Arduino, pero, ya que habrá clavijas del conector físicos diferentes disponibles dependiendo de la configuración de hardware que se va a compilar para, hemos También incluye una tabla aquí para describir qué nombres pin están disponibles para cada dispositivo.

#### <a name="raspberry-pi-2-and-3"></a>Raspberry Pi 2 y 3

![Diagrama de PIN](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | Definir el PIN | Número de Pin correspondiente|
> |-------------|----------|
> | LED_BUILTIN | *incorporar LED* |
> | GPIO * _donde * se refiere a [0, 27]_ | *consulte el diagrama de PIN* |
> | GCLK | 7 |
> | GEN * _donde * se refiere a [0, 5]_ | * consulte el diagrama de PIN |
> | SCL1 | 5 |
> | SDA1 | 3 |
> | CS0 (o CE0 o SS) | 24 |
> | CS1 (o CE1) | 26 |
> | Bloq Despl (o SCK) | 23 |
> | MISO | 21 |
> | MOSI | 19 |
> | RXD | 10 |
> | TXD | 8 |

#### <a name="minnowboard-max"></a>Minnowboard máx.

![Diagrama de PIN](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | Definir el PIN | Número de Pin correspondiente|
> |-------------|----------|
> | GPIO * _donde * se refiere a [0, 9]_  | *consulte el diagrama de PIN* |
> | SCL | 13 |
> | SDA | 15 |
> | CS0 (o CE0 o SS) | 5 |
> | Bloq Despl (o SCK)| 11 |
> | MISO |7 |
> | MOSI | 9 |
> | CTS1 | 10 |
> | RTS1 | 12 |
> | RX1 | 8 |
> | TX1 | 6 |
> | RX2 | 19 |
> | TX2 | 17 |


## <a name="common-problems"></a>Problemas comunes

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a>No se puede encontrar Visual "Conexión de aplicación de Arduino" C++ plantilla de proyecto en Visual Studio

**Causa**: La extensión de plantillas de proyecto de IoT de Windows para Visual Studio no está instalada.

**Solución**: Debe instalar la extensión de Visual Studio para Windows IoT Project Templates antes de poder crear proyectos de conexión de Arduino en Visual Studio. Diríjase a [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para descargar la extensión desde la Galería de Visual Studio!

### <a name="error-identifier-not-found-when-calling-a-function"></a>ERROR: "identificador no encontrado" al llamar a una función

**Causa**: Este error se produce durante el proceso del vinculador cuando se invoca una función que aún no se ha declarado en el documento.

**Solución**: En C++, todas las funciones se deben declarar antes de que se invocan. Si ha definido una función nueva en el archivo de boceto, la declaración o en toda la implementación de la función debe ser por encima de cualquier intento de invocarlo (normalmente al principio del documento).

**Ejemplo**:

El siguiente bloque de código, producirá el error "'myFunction': no se encontró el identificador"

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

Como alternativa, puede mover toda la implementación de la función por encima de cualquier invocación. Esto tiene el efecto de declarar y definir la función al mismo tiempo.

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

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a>Mi solución se bloquea indefinidamente al que se está inicializando

Hay un problema conocido que puede provocar un C++ solución deje de responder indefinidamente (bloqueo) al que se va a inicializar. Si encuentra que la solución parece que se bloquea indefinidamente y no puede utilizar el depurador se "interrumpan" a cualquier instrucción en las secciones de la aplicación de conexión de Arduino setup() o loop(), es posible que experimente este tipo de problema.

**Causa**: Se crea un objeto o una función se llama lo que da lugar a una acción asincrónica antes de que acabe de inicializarse la solución. Es probable que deba desde un constructor de objeto llamada a una función de API como `pinMode`.

**Solución**: Cualquier objeto de constructores de movimiento y la función llamadas fuera de la sección de inicialización del código y en el `setup()` bloque.

**Ejemplo 1**:

La ejecución de este esquema llama a una función denominada `setPinModes()` antes de que se ha inicializado la propia solución. La solución aparecerá pero ejecutar bloquearse indefinidamente.

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

La solución está por debajo, simplemente hemos pasamos la ejecución de `setPinModes()` a la `setup()` función:

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

La ejecución de este esquema crea un objeto en la pila antes `setup()` se ha llamado. Desde las llamadas de objeto `pinMode` en su constructor, esto hará que un interbloqueo. Esto es un problema habitual, pero pueden producirse con objetos de ciertas bibliotecas (al igual que Arduino `LiquidCrystal` biblioteca).

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

La solución está por debajo. Hemos cambiado el objeto a un puntero de objeto y hemos movido la inicialización del objeto para `setup()`.

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

### <a name="using-serialprint-and-serialprintln"></a>Uso de `Serial.print()` y `Serial.println()`

Usar muchos bocetos de Arduino `Serial` para imprimir los datos en la consola en serie (si está abierto) o para escribir en las líneas de serie (USB o recepción y transmisión). En las versiones anteriores del SDK de rayos, Hardware `Serial` soporte técnico no incluido, por lo que nos proporciona un `Log()` ventana en Visual Studio de salida de función que se imprimirá en el depurador. `Serial.print*()` o `Serial.write()` tenía que quitarse.

Sin embargo, a partir de _relámpago SDK v1.1.0_, hemos agregado `Hardware Serial` soporte técnico y ambos `Serial.print*()` o `Serial.write()` funciones son totalmente compatibles. Por lo tanto, si va a copiar un esbozo creado para Arduino, no tendrá que reemplazar cualquiera de estas referencias en la versión de Windows IoT del boceto de serie.

Además, nos hemos ampliado la funcionalidad de `Serial.print()` y `Serial.println()`, para enviar a la ventana del depurador cuando se adjunta un depurador - además de escribir en el PIN de serie del hardware.
La depuración de salida de impresión establecida como predeterminada desde la lectura de que el resultado es lo que los usuarios la mayoría querría cuando se está ejecutando los dibujos. Sin embargo, se puede deshabilitar esta funcionalidad también; Por ejemplo, para mejorar el rendimiento, basta con llamar a `Serial.enablePrintDebugOutput(false);` para deshabilitarlo en el boceto. Para volver a habilitarla, llame a `Serial.enablePrintDebugOutput(true);`. Escribir en el PIN de serie del hardware no se ve afectado por las llamadas.

Tenga en cuenta que no es necesario adjuntar cualquier periférico a sus PIN serie como un FTDI, para obtener el resultado enviado a la ventana del depurador. Sin embargo, deberá asegurarse de que está abierta la ventana del depurador mientras se está depurando la aplicación.

![Salida del depurador](../media/ArduinoWiringPortingGuide/debugger_output.png)

Se han actualizado las plantillas de proyecto en el [página de la extensión de plantillas de proyecto de Windows IoT Core](https://go.microsoft.com/fwlink/?linkid=847472) para habilitar el uso de Hardware `Serial` de fábrica. Sin embargo, si ya se ha creado la aplicación de conexión de Arduino con una versión anterior de plantilla de proyecto, necesitará 1) actualizar el proyecto al último SDK de rayos, v1.1.0 o versiones posteriores y (2) agregar la funcionalidad del dispositivo de serie del Hardware necesaria para su AppxManifest para poder usar `Serial`.

### <a name="hardware-serial-device-capability-requirements"></a>Requisitos de capacidad de serie del dispositivo de hardware

Funcionalidad de serie de hardware en Windows 10 IoT Core requiere declaraciones de funcionalidades de dispositivo que agregó al manifiesto AppX.

Busque el archivo `Package.appxmanifest` en el proyecto, escriba el nombre de archivo en el Explorador de soluciones. A continuación, a la derecha, haga clic en el archivo y elija 'Abrir con...'. Elija "Editor XML (texto)" y haga clic en 'Aceptar'.

![Actualizando Package.appxmanifest](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

En el editor del archivo de manifiesto appx, agregue el `serialcommunication` DeviceCapability al proyecto como se muestra en el fragmento XML siguiente:

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

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a>Actualizar un proyecto al último SDK de rayo

Dependen de los proyectos de la conexión de Arduino los [paquete Nuget del SDK relámpago](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) para implementar las funciones necesarias de conexión de Arduino y declaraciones como así como interfaz con el controlador de rayo. El último SDK de rayo contendrá las últimas mejoras y correcciones de errores. Para actualizar al último SDK de rayos, siga estos pasos:

- En el Explorador de soluciones, haga clic con el botón derecho en el proyecto y haga clic en 'Administrar paquetes Nuget...'
- En el Administrador de paquetes de NuGet, vaya a la pestaña 'Instalar'. Debería ver el paquete Microsoft.IoT.Lightning instalado
- Las versiones disponibles se mostrarán en el cuadro combinado de 'Version'.
- Elija la versión más reciente y haga clic en Actualizar para actualizar el paquete.
- Aviso para actualizar a una versión preliminar, asegúrese de activar la casilla "Incluir versión preliminar".

![Administrador de paquetes de NuGet](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
