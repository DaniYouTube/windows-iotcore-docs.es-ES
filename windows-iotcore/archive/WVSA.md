---
title: Información general de las pantallas virtuales de Windows para Arduino
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Aprenda a configurar las pletinas virtuales de Windows para Arduino y a compilar su primera aplicación de Windows 10 IoT Core.
keywords: Windows IOT, WVSA, protección virtual de Windows, Arduino, aplicación
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169003"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="set-up-windows-virtual-shields-for-arduino"></a>Configuración de escudos virtuales de Windows para Arduino

## <a name="overview"></a>Información general
Si ha usado un [Arduino](https://www.arduino.cc), está familiarizado con el concepto de un escudo. Cada escudo tiene un propósito especializado (por ejemplo, un escudo de temperatura, una pletina de acelerómetro) y la creación de un dispositivo con varias pletinas puede ser compleja, costosa y poco eficiente de espacio. Ahora Imagine que puede usar un teléfono de Windows Lumia de bajo costo como un conjunto compacto de escudos. El boceto de Arduino podría tener acceso a cientos de dólares de recursos y capacidades en el Windows Phone a través de llamadas de biblioteca fáciles de usar.

Esto es exactamente lo que los blindajes virtuales de Windows para la biblioteca Arduino permite a los desarrolladores. Y eso no es lo mejor: esta tecnología funciona en todos los dispositivos de Windows 10, por lo que también puede usar los sensores y las capacidades en su PC o superficie. Además, el Arduino puede descargar tareas caros computacionales, como el reconocimiento de voz y el análisis web, al dispositivo complementario de Windows 10.

Vamos a obtener información sobre cómo configurar el hardware y el software para trabajar con las pletinas virtuales de Windows para Arduino.


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1. Preparar el dispositivo con Windows 10 para el desarrollo de proyectos con escudos virtuales de Windows para Arduino.

En esta sección del tutorial, va a preparar un dispositivo de Windows 10 de su elección mediante su carga en la aplicación de escudos virtuales de Windows para Arduino. esta aplicación universal de Windows permite usar el dispositivo como "escudo virtual" para una placa Arduino.  Esto da como resultado algunas posibilidades eficaces para los responsables de ti, permitiéndoles usar el reconocimiento de voz, pantallas táctiles y la potencia de cálculo de Windows con relativa facilidad.

### <a name="hardware"></a>Hardware
La aplicación de escudos virtuales de Windows para Arduino se puede ejecutar en cualquier dispositivo de Windows 10, pero en este tutorial se explicará el programa de instalación con un Windows Phone.

*Lo que necesita* Windows Phone que ejecutan Windows 10, se recomienda usar [lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) o [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).

*Configurar el Windows Phone*

Si su teléfono no está ejecutando Windows 10, hay opciones para instalar versiones preliminares del software.  Windows Phone 8 usuarios pueden ir a la aplicación de Microsoft Store para descargar la aplicación "Windows Insider": esta aplicación permite al usuario participar en la recepción de las versiones preliminares técnicas de Windows 10 como actualizaciones.  Siga las indicaciones y las instrucciones al abrir la aplicación y continúe una vez que el teléfono ejecute correctamente Windows 10.

### <a name="software"></a>Software

Hay dos opciones para instalar las pantallas virtuales de Windows para la aplicación Arduino para UWP en el Windows Phone.  Descargar la aplicación es la opción más fácil y rápida.

* Descargue la aplicación desde el Microsoft Store
* Transferir localmente la aplicación con un PC y Visual Studio

*Opción 1: Descargue la aplicación desde el Microsoft Store*

Siga este [vínculo](https://www.microsoft.com/store/apps/9nblgggz0mld) a la página Microsoft Store de las pantallas virtuales de Windows para Arduino, descargue la aplicación y, a continuación, instale. Después, puede abrir la aplicación para asegurarse de que se ejecuta correctamente.  El dispositivo ya está configurado para usarse como "escudo virtual" para un Arduino.  Puede pasar a la página siguiente.

*Opción 2: Transferir localmente la aplicación con un equipo y visual*Studio
_lo que necesita_
* Visual Studio 2017 para transferir localmente las pletinas virtuales de Windows para la aplicación Arduino a un teléfono desbloqueado por el desarrollador.
* Este [repositorio](https://github.com/ms-iot/virtual-shields-universal) contiene el código para la aplicación de protección virtual de Windows para Arduino.  Clone el repositorio o descárguelo como un archivo ZIP en el disco local.  Si no está familiarizado con git y desea realizar un clon adecuado, siga las instrucciones que se indican [aquí](https://help.github.com/articles/cloning-a-repository).

_Configurar Visual Studio 2017_
1. Instale Visual Studio 2017 con las herramientas de vista previa de Windows 10 Developer desde [dev.Windows.com](https://developer.microsoft.com/en-us/windows/downloads).  Se recomienda la versión gratuita de la comunidad de Visual Studio, pero tanto Enterprise como Professional funcionarán también.  Si ya tiene Visual Studio instalado, vaya al paso siguiente.
2. En Visual Studio, cargue el Shield. sln del repositorio descargado en la sección "lo que necesita" anterior.
3. Asegúrese de que el dispositivo Windows 10 (en este caso, un Windows Phone) está desbloqueado por el desarrollador. En [esta página](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) se explica cómo desbloquear Windows Phone 8,1, 8 y 7,1; sin embargo, los pasos son los mismos para los teléfonos con Windows 10.
4. Conecte el dispositivo Windows 10 al equipo e implemente el programa Shield. sln en el dispositivo.  Para ello, implemente en un "equipo local" y asegúrese de establecer la arquitectura del dispositivo como "ARM".
5. Ejecute los escudos virtuales de Windows recién instalados para la aplicación Arduino en el teléfono para asegurarse de que la implementación se realizó correctamente.  El dispositivo Windows 10 ya está configurado para usarse como escudo virtual.

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2. Configuración de Arduino para usar las pletinas virtuales de Windows para la biblioteca de Arduino 
Una vez que el dispositivo complementario de Windows 10 esté configurado correctamente, vamos a preparar el Arduino para usar las pletinas virtuales de Windows para la biblioteca de Arduino. Puede establecer una conexión entre el Arduino y el "escudo virtual" de Windows 10 a través de USB, Bluetooth o Wi-Fi. En este tutorial concreto se explicará cómo completar la instalación mediante una conexión Bluetooth, pero no dude en experimentar con las demás opciones.

### <a name="hardware"></a>Hardware
*Lo que necesita*
* Arduino uno o dispositivo compatible
* Conexión de hilos
* Un equipo que se usa para cargar los bocetos de Arduino
* Estándar a a estándar B USB: necesario para cargar bocetos en el dispositivo Arduino
* Opcional: Módulo Bluetooth: solo es necesario si decide conectarse mediante Bluetooth.
* Opcional: Módulo de Wi-Fi: solo es necesario si decide conectarse mediante Wi-Fi.

* Configuración de Arduino
* Prepare el módulo Bluetooth si es necesario (es posible que el módulo Bluetooth deba tener encabezados soldados en él).
* A excepción de lo que se indica a continuación, conecte el módulo Bluetooth a Arduino por [el diagrama de cableado](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).

  * Hay Use los pin 0 y 1 en lugar de 2 y 3:
    * La transmisión de Bluetooth debe conectarse al pin 0 (Arduino RX o RX0).
    * El RX de Bluetooth debe conectarse al pin 1 (Arduino TX o TX1).

### <a name="software"></a>Software
*Lo que necesita*
* Arduino IDE 1,6 o superior
* Biblioteca ArduinoJSON
* [Este repositorio](https://github.com/ms-iot/virtual-shields-arduino), que contiene el boceto de ejemplo que se ejecutará en Arduino.

*Configuración del IDE de Arduino*
* Descargue e instale el IDE de Arduino y, a continuación, inicie el programa.
* Compruebe que tiene seleccionada la placa Arduino correcta en *herramientas > placa*.
* Compruebe que tiene seleccionado el puerto COM correcto en *herramientas > puerto*. El nombre del panel debe aparecer junto a cada opción, lo que facilita la elección de la opción correcta.

*Configuración de la biblioteca ArduinoJSON*
* En el [repositorio de ArduinoJson](https://github.com/bblanchon/ArduinoJson), Clone el repositorio o descargue el archivo zip.
* Coloque todo el repositorio en la carpeta de bibliotecas (es `Documents\Arduino\libraries\ArduinoJson\`decir,).

*Configuración de las pletinas virtuales de Windows para la biblioteca Arduino*
* Clone [este repositorio](https://github.com/ms-iot/virtual-shields-arduino) o descargue el archivo zip. Si no está familiarizado con git y desea realizar un clon adecuado, siga las instrucciones que se indican [aquí](https://help.github.com/articles/cloning-a-repository/).
* Copie la carpeta "VirtualShield", que se encuentra en la carpeta "Arduino\Libraries" del repositorio que acaba de descargar, en la carpeta de la biblioteca `Documents\Arduino\libraries\VirtualShield\`de Arduino (es decir,).

*Prueba de la configuración*
* En el IDE de Arduino, vaya al elemento de menú *File-> examples-> virtual Shield-> HelloWorld-Speech-Eventing*. Esto debe cargar el ejemplo de reconocimiento de voz basado Hola mundo que estamos usando para este tutorial.
* Antes de cargar el boceto en el Arduino, quite temporalmente los cables TX y RX de Bluetooth de la Arduino (solo hay un puerto serie compartido entre el USB y Bluetooth: el Bluetooth interfiere con la carga).
* Cargue el boceto presionando el botón "cargar" en el IDE.
* Reemplace los cables TX y RX de Bluetooth a los pin de Arduino (TX de Bluetooth a Arduino RX (o RX0) y RX de Bluetooth a Arduino TX o (TX1)).
* En el teléfono (u otro dispositivo de Windows) preparado en la página anterior, empareje con el dispositivo Bluetooth en el Arduino de configuración de Bluetooth. Si usa BlueSMiRF, el código PIN predeterminado es 1234. 

> [!NOTE]
> La luz roja parpadeante en el BlueSMiRF continúa parpadeando en rojo después de un emparejamiento correcto. Esto es de esperar. Solo se vuelve verde después de conectarse a la aplicación de protección virtual de Windows para Arduino.


## <a name="3-write-your-first-app-hello-blinky"></a>3. Escriba su primera aplicación: ¡ Hola, parpadeo! 

### <a name="hello-world-speech-enabled-led-example"></a>Hola mundo ejemplo de LED habilitado para voz
Con su Windows Phone (o potencialmente cualquier dispositivo de Windows 10) y su Arduino preparado tal y como se detallan en los pasos anteriores de este tutorial, ya está listo para probar el ejemplo.

1. Prepare la placa de Arduino enlazando un LED con una resistencia al vástago 8.
2. Asegúrese de que el Arduino todavía se carga con el ejemplo HelloWorld-Speech-Eventing y, a continuación, conecte el Arduino a una fuente de alimentación.
3. Ejecute la aplicación de protección virtual de Windows para Arduino en el Windows Phone que preparó previamente.
4. Si todo se ha configurado correctamente, el teléfono debe conectarse al boceto de Arduino y le agradecemos la señal de audio. Ahora puede decir "activado" u "desactivado" en el dispositivo Windows 10 para cambiar el LED en el Arduino entre on y OFF.

### <a name="arduino-wiring-sketch-hello-world-example"></a>Boceto del cableado de Arduino: Ejemplo de Hola mundo

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


