---
title: Desarrollo de aplicaciones de primer plano
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre los lenguajes y los tipos de aplicaciones compatibles con IoT Core.
keywords: Windows IOT, idiomas, tipos de aplicaciones, UWP, compatible
ms.openlocfilehash: e0eb046ba874e8433e7632d3f88a63a90b88fa2b
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627399"
---
# <a name="developing-foreground-applications"></a>Desarrollo de aplicaciones de primer plano
Obtenga información sobre los idiomas que se admiten en Windows 10 IoT Core, así como en los tipos de aplicaciones UWP y no UWP que se admiten en IoT Core.


> [!NOTE]
> Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.

## <a name="application-types"></a>Tipos de aplicación
___

### <a name="universal-windows-platform-uwp-apps"></a>Aplicaciones Plataforma universal de Windows (UWP)
IoT Core es un sistema operativo centrado en UWP y las aplicaciones para UWP son el tipo de aplicación principal.

Plataforma universal de Windows (UWP) es una plataforma de aplicaciones común en todas las versiones de Windows 10, incluida Windows 10 IoT Core.  UWP es una evolución de Windows Runtime (WinRT). Puede encontrar más información y una introducción a UWP [aquí](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

Visual Studio es la herramienta principal para escribir aplicaciones para UWP para IoT Core y en general. Puede encontrar una lista detallada de los requisitos de compatibilidad de Visual Studio [aquí](https://docs.microsoft.com/visualstudio/productinfo/vs2017-compatibility-vs).


### <a name="traditional-uwp-apps"></a>Aplicaciones de UWP tradicionales
Las aplicaciones para UWP funcionan solo en IoT Core, al igual que en otras ediciones de Windows 10. Una aplicación XAML sencilla y vacía en Visual Studio se implementará correctamente en el dispositivo IoT Core tal como lo haría en un teléfono o en un equipo con Windows 10. Todos los lenguajes y plantillas de proyecto estándar de UWP son totalmente compatibles con IoT Core.

Hay algunas adiciones al modelo de aplicación de UWP tradicional para admitir escenarios de IoT y cualquier aplicación para UWP que se beneficie de ellas necesitará la información correspondiente agregada a su manifiesto. En particular, el espacio de nombres "IOT" debe agregarse al manifiesto de estas aplicaciones estándar de UWP. 

Dentro del <Package> atributo del manifiesto, debe definir el xmlns de IOT y agregarlo a la lista IgnorableNamespaces. El XML final debería ser similar al siguiente: 

```
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:iot="http://schemas.microsoft.com/appx/manifest/iot/windows10"
  IgnorableNamespaces="uap mp iot">
```

### <a name="background-apps"></a>Aplicaciones en segundo plano
Además de las aplicaciones de interfaz de usuario tradicionales, IoT Core ha agregado un nuevo tipo de aplicación de UWP denominado "aplicaciones en segundo plano". Estas aplicaciones no tienen un componente de interfaz de usuario, pero en su lugar tienen una clase que implementa la interfaz "IBackgroundTask". Después, registran esa clase como "StartupTask" para que se ejecute en el arranque del sistema. Dado que todavía son aplicaciones para UWP, tienen acceso al mismo conjunto de API y son compatibles con el mismo lenguaje. La única diferencia es que no hay ningún punto de entrada de la interfaz de usuario.

Cada tipo de IBackgroundTask obtiene su propia Directiva de recursos. Esto suele ser restrictivo para mejorar la duración de la batería y los recursos de la máquina en los dispositivos en los que estas aplicaciones en segundo plano son componentes secundarios de aplicaciones de interfaz de usuario de primer plano. En los dispositivos IoT, las aplicaciones en segundo plano suelen ser la función principal del dispositivo, por lo que estas StartupTasks obtienen una directiva de recursos que refleja las aplicaciones de interfaz de usuario de primer plano en otros dispositivos.

En el ejemplo siguiente se muestra el código necesario para C# compilar una aplicación en segundo plano que parpadee un LED:

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

### <a name="non-uwp-apps"></a>Aplicaciones que no son de UWP
IoT Core admite determinados tipos de aplicaciones Win32 tradicionales, como aplicaciones de consola Win32 y servicios NT. Estas aplicaciones se compilan y ejecutan de la misma manera que en el escritorio de Windows 10. Además, hay una plantilla de proyecto C++ de consola de IOT Core que facilita la compilación de aplicaciones con Visual Studio.

Existen dos limitaciones principales en estas aplicaciones que no son de UWP:
1. *No compatible con la interfaz de usuario de Win32 heredada:* IoT Core no contiene las API para crear ventanas clásicas (HWND). Los métodos heredados como CreateWindow () y CreateWindowEx () o cualquier otro método que trate con identificadores de Windows (HWND) no están disponibles. Posteriormente, los marcos que dependen de estas API, como MFC, Windows Forms y WPF, no se admiten en IoT Core
2. *C++Solo aplicaciones:* Actualmente, solo C++ se admite para desarrollar aplicaciones Win32 en IOT Core.

## <a name="programming-languages"></a>Lenguajes de programación
___

IoT Core admite una amplia variedad de lenguajes de programación.

### <a name="in-box-languages"></a>Idiomas en caja
Los lenguajes de UWP tradicionales se incluyen de forma predeterminada en Visual Studio. Todos los lenguajes integrados admiten las aplicaciones de interfaz de usuario y en segundo plano
 
* Idiomas
  * C#
  * C++
  * Código
  * Visual Basic

### <a name="arduino-wiring"></a>Cableado de Arduino
 El cableado Arduino requiere la descarga de las "plantillas de proyecto de Windows IoT Core" desde las extensiones de Visual Studio **Tools-> y updates** Manager.  El cableado Arduino solo admite aplicaciones en segundo plano. También puede compilar *componentes* de C#Windows Runtime C++mediante, o Visual Basic y, después, hacer referencia a esas bibliotecas desde cualquier otro lenguaje.

### <a name="c-and-visual-basic-vb"></a>C#y Visual Basic (VB)
C#y VB se admiten como aplicaciones UWP y tienen acceso a la parte de .NET Framework disponible para las aplicaciones de UWP. Admiten aplicaciones de interfaz de usuario compiladas con XAML y aplicaciones en segundo plano. También puede compilar *componentes de Windows Runtime* que se pueden usar desde otros idiomas admitidos.

Assembl


* [C#Sin periféricos](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CS)
* [Parpadeo de VB sin periféricos](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/VB)
* [C#Aplicación de interfaz de usuario de parpadeo](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/CS)


### <a name="javascript"></a>Código
Puede usar JavaScript para compilar aplicaciones en la interfaz de usuario y en segundo plano. Las aplicaciones de interfaz de usuario funcionan de la misma manera que en todas las ediciones de UWP. Las aplicaciones en segundo plano son nuevas para IoT Core, pero son muy sencillas. En el código de ejemplo siguiente se muestra la salida de una *plantilla de proyecto New de JS*:

```javascript
// The Background Application template is documented at http://go.microsoft.com/fwlink/?LinkID=533884&clcid=0x409
(function () {
    "use strict";

    // TODO: Insert code here for the startup task

})();
```

### <a name="c"></a>C++
Con C++ puede compilar aplicaciones de interfaz de usuario de DirectX o XAML, así como proyectos en segundo plano para UWP y aplicaciones *de Win32 que no son de interfaz de usuario* .

Assembl

* [Sin periféricos](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinkyBackground/CPP)
* [Punta de parpadeo](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky/Cpp)
* [Aplicación de consola](https://github.com/microsoft/Windows-iotcore-samples/tree/develop/Samples/MemoryStatus/CPP)

> [!NOTE]
> En el caso de aquellos que planean escribir su C++aplicación en, debe activar la casilla de C++ UWP al descargar.

![C++para Visual Studio](../media/BuildingAppsForIoTCore/VS-CPP.jpg)


### <a name="arduino-wiring"></a>Cableado de Arduino
Gracias a la compatibilidad con el cableado Arduino, puede crear aplicaciones en el cableado de Arduino para muchos componentes y periféricos populares en el ecosistema de IoT.

Nuestra [Guía de proyecto de Arduino cables](../learn-about-hardware/ArduinoWiringProjectGuide.md) proporciona instrucciones completas sobre cómo configurar para compilar estas aplicaciones. Los ejemplos copiados y vinculados a continuación le ayudarán a empezar a crear el suyo propio.  Incluso puede compilar [componentes de WinRT en Arduino](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) que luego se pueden usar desde otros idiomas. 

*Código de ejemplo de parpadeo* El [código de ejemplo completo y los documentos](https://github.com/ms-iot/samples/tree/develop/ArduinoLibraryBlinky) están disponibles en nuestra página de ejemplos y puede encontrar el código completo siguiente:

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
