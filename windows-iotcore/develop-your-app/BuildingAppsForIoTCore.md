---
title: Desarrollo de aplicaciones de primer plano
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los lenguajes y tipos de aplicaciones que son compatibles con IoT Core.
keywords: Windows iot, idiomas, tipos de aplicaciones, UWP, compatibles
ms.openlocfilehash: e0eb046ba874e8433e7632d3f88a63a90b88fa2b
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627399"
---
# <a name="developing-foreground-applications"></a>Desarrollo de aplicaciones de primer plano
Obtenga información sobre los lenguajes que se admiten en Windows 10 IoT Core, así como la UWP y tipos de aplicaciones no de UWP que se admiten en IoT Core.


> [!NOTE]
> Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.

## <a name="application-types"></a>Tipos de aplicación
___

### <a name="universal-windows-platform-uwp-apps"></a>Aplicaciones de universal Windows Platform (UWP)
IoT Core es un sistema de operativo centrado en UWP y aplicaciones para UWP son su tipo de aplicación principal.

Plataforma universal de Windows (UWP) es una plataforma de aplicaciones común entre todas las versiones de Windows 10, incluidos Windows 10 IoT Core.  UWP es una evolución de Windows en tiempo de ejecución (WinRT). Puede encontrar más información y una introducción a UWP [aquí](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

Visual Studio es la herramienta principal para escribir aplicaciones para UWP para IoT Core y en general. Puede encontrar una lista detallada de los requisitos de compatibilidad para Visual Studio [aquí](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).


### <a name="traditional-uwp-apps"></a>Aplicaciones tradicionales de UWP
Aplicaciones para UWP solo funcionan en IoT Core, al igual que en otras ediciones de Windows 10. Una simple aplicación Xaml en blanco en Visual Studio se implementará correctamente en el dispositivo de IoT Core tal como lo haría en un teléfono o un equipo con Windows 10. Todos los idiomas estándar de UWP y las plantillas de proyecto son totalmente compatibles con IoT Core.

Hay algunas adiciones en el tradicional UWP-modelo de aplicación para admitir escenarios de IoT y cualquier aplicación para UWP que aprovecha las ventajas de ellas necesitará la información correspondiente agregada a su manifiesto. En concreto el espacio de nombres "iot" debe agregarse al manifiesto de estas aplicaciones para UWP estándares. 

Dentro de la <Package> atributo del manifiesto, deberá definir xmlns iot y agregarlo a la lista IgnorableNamespaces. El código xml final debe tener este aspecto: 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a>Aplicaciones en segundo plano
Además de las aplicaciones de interfaz de usuario tradicionales, IoT Core agregó un nuevo tipo de aplicación UWP denominado "Aplicaciones en segundo plano". Estas aplicaciones no tiene un componente de interfaz de usuario, pero en su lugar, tienen una clase que implementa la interfaz "IBackgroundTask". A continuación, se registran esa clase como un "StartupTask" para ejecutar al arrancar el sistema. Puesto que siguen estando aplicaciones para UWP, tienen acceso al mismo conjunto de API y se admiten en el mismo idioma. La única diferencia es que no hay ningún punto de entrada de la interfaz de usuario.

Cada tipo de IBackgroundTask obtiene su propia directiva de recursos. Esto es normalmente más restrictiva para mejorar los recursos de vida y la máquina de la batería en dispositivos donde estas aplicaciones en segundo plano son componentes secundarios de interfaz de usuario de aplicaciones de primer plano. En los dispositivos de IoT, las aplicaciones en segundo plano son a menudo la función principal del dispositivo y por lo que estos StartupTasks obtener una directiva de recursos refleja las aplicaciones de interfaz de usuario de primer plano en otros dispositivos.

El ejemplo siguiente muestra el código necesario para compilar un C# aplicación en segundo plano que hace parpadear un LED:

```C#
namespace BlinkyHeadlessCS
{
    public sealed class StartupTask : IBackgroundTask
    {
        BackgroundTaskDeferral deferral;
        private GpioPinValue value = GpioPinValue.High;
        private const int LED_PIN = 5;
        private GpioPin pin;
        private ThreadPoolTimer timer;

        public void Run(IBackgroundTaskInstance taskInstance)        {
            deferral = taskInstance.GetDeferral();
            InitGPIO();
            timer = ThreadPoolTimer.CreatePeriodicTimer(Timer_Tick, TimeSpan.FromMilliseconds(500));

        }
        private void InitGPIO()
        {
            pin = GpioController.GetDefault().OpenPin(LED_PIN);
            pin.Write(GpioPinValue.High);
            pin.SetDriveMode(GpioPinDriveMode.Output);
        }

        private void Timer_Tick(ThreadPoolTimer timer)
        {
            value = (value == GpioPinValue.High) ? GpioPinValue.Low : GpioPinValue.High;
            pin.Write(value);
        }
    }
}
```

Puede encontrar información detallada sobre las aplicaciones en segundo plano [aquí](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).

### <a name="non-uwp-apps"></a>Aplicaciones no de UWP
IoT Core es compatible con ciertos tipos de aplicación tradicionales de Win32, como aplicaciones de consola Win32 y servicios NT. Estas aplicaciones están integradas y ejecutar la misma manera que en el escritorio de Windows 10. Además, hay un IoT Core C++ plantilla de proyecto de consola para que sea fácil crear estas aplicaciones con Visual Studio.

Hay dos limitaciones principales en estas aplicaciones no de UWP:
1. *No hay compatibilidad heredada de la interfaz de usuario de Win32:* IoT Core no contiene las API para crear clásico Windows (HWND). Métodos heredados como CreateWindow() y CreateWindowEx() o cualquier otro método que se encargan de identificadores de Windows (HWND) no está disponible. Posteriormente, los marcos de trabajo que dependen de estas API como MFC, Windows Forms y WPF, no se admiten en IoT Core
2. *C++Solo aplicaciones:* Actualmente, solo C++ se admite para el desarrollo de aplicaciones de Win32 en IoT Core.

## <a name="programming-languages"></a>Lenguajes de programación
___

IoT Core es compatible con una amplia gama de lenguajes de programación.

### <a name="in-box-languages"></a>En el cuadro idiomas
Los lenguajes tradicionales de UWP se suministran con soporte técnico de Visual Studio de forma predeterminada. Todos los idiomas en listos para admiten la interfaz de usuario y aplicaciones en segundo plano
 
* Idiomas
  * C#
  * C++
  * Javascript
  * Visual Basic

### <a name="arduino-wiring"></a>Conexión de Arduino
 Conexión de Arduino requiere la descarga de las "Windows IoT Core plantillas de proyecto" de Visual Studio **Herramientas -> extensiones y actualizaciones** manager.  Conexión de Arduino admite solo las aplicaciones en segundo plano. También puede compilar *componentes de Windows en tiempo de ejecución* mediante C#, C++, o Visual Basic y, a continuación, hacer referencia a esas bibliotecas desde cualquier otro lenguaje.

### <a name="c-and-visual-basic-vb"></a>C#y Visual Basic (VB)
C#y se admiten como aplicaciones para UWP de VB y tener acceso a la parte de .net Framework disponible para las aplicaciones de UWP. Admiten las aplicaciones de interfaz de usuario creadas con Xaml, así como aplicaciones en segundo plano. También puede compilar *componentes de Windows en tiempo de ejecución* que puede usarse desde otros lenguajes compatibles.

Ejemplos:


* [C#Llamativa sin periféricos](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [VB llamativa sin periféricos](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [C#Aplicación de interfaz de usuario de forma llamativa](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a>Javascript
Puede usar Javascript para crear la interfaz de usuario y aplicaciones en segundo plano. Las aplicaciones de interfaz de usuario funcionan del mismo modo que lo hacen en todas las ediciones de UWP. Las aplicaciones en segundo plano son nuevas para IoT Core, pero son muy sencillas. El código de ejemplo siguiente muestra la salida de una la *JS nueva plantilla de proyecto*:

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a>C++
Con C++ compilación Xaml o DirectX UI aplicaciones, así como proyectos de UWP en segundo plano y *sin interfaz de usuario* aplicaciones de Win32.

Ejemplos:

* [Llamativa sin periféricos](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [Llamativa puntas](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [Aplicación de consola](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> Para aquellos que se va a escribir su aplicación con C++, deberá comprobar la UWP C++ casilla de verificación tras la descarga.

![C++para Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a>Conexión de Arduino
Puede compilar las aplicaciones de conexión de Arduino para muchos componentes populares y periféricos en el ecosistema de IoT con soporte de conexión de Arduino.

Nuestro [Guía de proyecto de cableado de Arduino](../learn-about-hardware/ArduinoWiringProjectGuide.md) proporciona instrucciones completas sobre cómo configurar la aplicación para crear estas aplicaciones. Los ejemplos de copiado y vinculado a continuación le ayudarán a empezar a crear la suya propia.  Puede incluso [crear componentes de WinRT en Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) que, a continuación, se puede utilizar desde otros lenguajes. 

*Código de ejemplo llamativa* completo [docs y código muestra](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) están disponibles en nuestros ejemplos de página y se puede encontrar el código completo siguiente:

```C++
void setup()
{
    // put your setup code here, to run once:

    pinMode(GPIO5, OUTPUT);
}

void loop()
{
    // put your main code here, to run repeatedly:

    digitalWrite(GPIO5, LOW);
    delay(500);
    digitalWrite(GPIO5, HIGH);
    delay(500);
}
```
