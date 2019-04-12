---
title: Shields Virtual de Windows para la introducción a Arduino
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Aprenda a configurar Windows Virtual Shields de Arduino y construya su primera aplicación de Windows 10 IoT Core.
keywords: aplicación de Windows Virtual Shields, Arduino, iot, WVSA, de Windows
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514688"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="set-up-windows-virtual-shields-for-arduino"></a>Configurar Windows Virtual Shields de Arduino

## <a name="overview"></a>Información general
Si ha usado un [Arduino](https://www.arduino.cc), está familiarizado con el concepto de un icono de escudo. Cada icono de escudo tiene una finalidad especializada (por ejemplo, una temperatura shield, un icono de escudo de acelerómetro) y creación de un dispositivo con varios shields puede ser complejo, costoso y espacio ineficaz. Ahora Imagínese que puede usar un teléfono Lumia de Windows de bajo costo como un conjunto compacto de shields. El boceto de Arduino podrán tener acceso a cientos de dólares de sensores y capacidades en su Windows Phone a través de llamadas a bibliotecas de fácil de usar.

Esto es exactamente lo que permite la Shields Virtual de Windows para la biblioteca de Arduino para desarrolladores. Y no es la mejor parte: esta tecnología funciona en todos los dispositivos Windows 10, para que pueda usar las capacidades y los sensores en un equipo o la superficie también. Además, Arduino puede descargar tareas consumen muchos recursos, como el reconocimiento de voz y web de análisis para el dispositivo complementario de Windows 10.

Vamos a aprender a configurar el hardware y software para trabajar con Windows Virtual Shields de Arduino.


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a>1. Preparar el dispositivo Windows 10 para desarrollar proyectos que usan Windows Virtual Shields de Arduino.

En esta sección del tutorial, se preparará un dispositivo Windows 10 de su elección, cargue los Shields Virtual de Windows para la aplicación de Arduino: esta aplicación Universal de Windows permite usar el dispositivo como un "escudo virtual" para una placa de Arduino.  Algunas posibilidades poderosas para responsables de decisiones, lo que les permite usar el reconocimiento de voz, el resultado tocar las pantallas y la potencia de cálculo de Windows con relativa facilidad.

### <a name="hardware"></a>Hardware
Puede ejecutar los Shields Virtual de Windows para la aplicación de Arduino en cualquier dispositivo Windows 10, pero en este tutorial se explica el programa de instalación con un Windows Phone.

*Lo que necesita* Windows Phone que ejecutan Windows 10 - se recomienda la [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) o [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).

*Configurar su Windows Phone*

Si el teléfono no se está ejecutando Windows 10, hay opciones para instalar las versiones preliminares del software.  Los usuarios de Windows Phone 8 pueden ir a la aplicación de Microsoft Store para descargar la aplicación de "Windows Insider": esta aplicación permite al usuario optar por recibir Windows 10 Technical Preview como las actualizaciones.  Siga las indicaciones e instrucciones al abrir la aplicación y seguir una vez que el teléfono ejecuta correctamente en Windows 10.

### <a name="software"></a>Software

Hay dos opciones para instalar los Shields Virtual de Windows para la aplicación de UWP de Arduino en su Windows Phone.  Descargar la aplicación es la opción más fácil y rápida.

* Descargar la aplicación desde la Microsoft Store
* Transferir localmente la aplicación utiliza un PC y Visual Studio

*Opción 1: Descargar la aplicación desde la Microsoft Store*

Siga este [vínculo](https://www.microsoft.com/store/apps/9nblgggz0mld) a la página de Microsoft Store para Shields Virtual de Windows para Arduino, descargue la aplicación y, a continuación, instalar. A continuación, puede abrir la aplicación para asegurarse de que se ejecuta correctamente.  El dispositivo ahora está configurado para utilizarse como un "escudo virtual" para Arduino!  Puede continuar a la página siguiente.

*Opción 2: Transferir localmente la aplicación utiliza un PC y Visual Studio*
_lo que necesita_
* Visual Studio 2017 para transferir localmente la Shields Virtual de Windows para la aplicación de Arduino en un teléfono desbloqueado por el desarrollador.
* Esto [repositorio](https://github.com/ms-iot/virtual-shields-universal) que contiene el código para los Shields Virtual de Windows para la aplicación de Arduino.  Clone el repositorio o descargarlo como un archivo ZIP en el disco local.  Si no está familiarizado con git y realizar un clon adecuado, siga las instrucciones [aquí](https://help.github.com/articles/cloning-a-repository).

_Configurar Visual Studio 2017_
1. Instalar Visual Studio 2017 con las herramientas de vista previa de Windows 10 para desarrolladores de [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).  Se recomienda la gratuita Community versión de Visual Studio, pero Enterprise y Professional también funcionan correctamente.  Si ya tiene instalado Visual Studio, vaya al paso siguiente.
2. En Visual Studio carga el Shield.sln desde el repositorio se descargó en el "lo que necesita" sección anterior.
3. Asegúrese de que el dispositivo Windows 10 (en este caso un Windows Phone) es el desbloqueo de desarrollador. [Esta página](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explica cómo desbloquear Windows Phone 8.1, 8 y 7.1; sin embargo, los pasos son los mismos para teléfonos con Windows 10.
4. Conecte su dispositivo Windows 10 en su equipo e implementar el programa Shield.sln al dispositivo.  Para ello, implemente en un "equipo Local" y asegúrese de establecer la arquitectura del dispositivo como "ARM".
5. Ejecute recién instalado Shields Virtual de Windows para la aplicación de Arduino en el teléfono para garantizar la implementación fue correcta.  El dispositivo Windows 10 ahora está configurado para utilizarse como un icono de escudo virtual!

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a>2. Configurar su Arduino para usar los Shields Virtual de Windows para la biblioteca de Arduino 
Con nuestro dispositivo complementario de Windows 10 correctamente configurado, vamos a nuestra Arduino listo para usar los Shields Virtual de Windows para la biblioteca de Arduino. Puede establecer una conexión entre su Arduino y Windows 10 "virtual escudo" a través de Wi-Fi, Bluetooth o USB. En este tutorial particular se explica cómo completar la instalación mediante una conexión Bluetooth, pero no dude en experimentar con las otras opciones.

### <a name="hardware"></a>Hardware
*Lo que necesita*
* Arduino Uno u otro dispositivo compatible
* Cables de conexión
* Un equipo que se use para cargar los bocetos de Arduino
* Estándar A estándar USB B - necesario para cargar dibujos en el dispositivo de Arduino
* Opcional: Módulo de Bluetooth: solo es necesario si decide conectar mediante Bluetooth.
* Opcional: Módulo de Wi-fi: solo es necesario si decide conectar mediante wi-fi.

* Configurar su Arduino
* Si es necesario (el módulo de Bluetooth que deba tener encabezados soldados en él), prepare el módulo de Bluetooth.
* Excepto el otro se indica a continuación, conectado el módulo de Bluetooth a Arduino por [el diagrama de cableado](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).

  * Diferencia: Usar el PIN 0 y 1 en lugar de 2 y 3:
    * TX Bluetooth debe conectarse a la clavija de 0 (RX de Arduino o RX0).
    * Debe conectar RX de Bluetooth del pin 1 (TX de Arduino o TX1).

### <a name="software"></a>Software
*Lo que necesita*
* Arduino IDE 1.6 o superior
* Biblioteca ArduinoJSON
* [Este repositorio](https://github.com/ms-iot/virtual-shields-arduino), que contiene el boceto de ejemplo que se ejecutará en Arduino.

*Configurar el IDE de Arduino*
* Descargue e instale el IDE de Arduino, inicie el programa.
* Compruebe que dispone de la placa de Arduino correcta seleccionada en *Herramientas > panel*.
* Compruebe que tiene el puerto COM correcto seleccionado en *Herramientas > puerto*. El nombre del panel debe aparecer junto a cada opción, lo que facilita a elegir la opción correcta.

*Configurar la biblioteca ArduinoJSON*
* Desde el [ArduinoJson repositorio](https://github.com/bblanchon/ArduinoJson), clone el repositorio o descargue el archivo zip.
* Colocar el repositorio completo en la carpeta de bibliotecas (es decir, `Documents\Arduino\libraries\ArduinoJson\`).

*Configurar los Shields Virtual de Windows para la biblioteca de Arduino*
* Clon [este repositorio](https://github.com/ms-iot/virtual-shields-arduino) o descargue el archivo ZIP. Si no está familiarizado con git y realizar un clon adecuado, siga las instrucciones [aquí](https://help.github.com/articles/cloning-a-repository/).
* Copie la carpeta "VirtualShield", que se encuentra en la carpeta "Arduino\Libraries" del repositorio que acaba de descargar, a la carpeta de biblioteca de Arduino (es decir, `Documents\Arduino\libraries\VirtualShield\`).

*Probar la configuración*
* En el IDE de Arduino, vaya al elemento de menú *archivo -> ejemplos -> Virtual escudo -> HelloWorld de voz-eventos*. Esto debería cargar en el ejemplo de Hello World en función de reconocimiento de voz, que vamos a usar para este tutorial.
* Antes de cargar el boceto a su Arduino, quitar temporalmente los cables Bluetooth TX y RX de Arduino (solo hay un puerto serie que se comparte entre el USB y Bluetooth, el Bluetooth interfiere con la carga).
* Carga del boceto presionando el botón "Cargar" en el IDE.
* Reemplace los cables Bluetooth TX y RX en las clavijas de Arduino (Bluetooth RX para Arduino TX y Bluetooth TX Arduino RX (o RX0) o (TX1)).
* En el teléfono (u otro dispositivo de Windows) preparado en la página anterior, emparejar con el dispositivo Bluetooth en su Arduino en la configuración de Bluetooth. Si usas el BlueSMiRF, el código pin predeterminado es 1234. 

> [!NOTE]
> La luz roja parpadeante en la BlueSMiRF continúa hacer parpadear rojo después de un emparejamiento correcto. Esto es de esperar. Solo se vuelve verde después de una conexión con los Shields Virtual de Windows para la aplicación de Arduino.


## <a name="3-write-your-first-app-hello-blinky"></a>3. Escribir su primera aplicación: Hola llamativa. 

### <a name="hello-world-speech-enabled-led-example"></a>Ejemplo de Hola mundo compatibles con voz LED
Con su Windows Phone (o potencialmente a cualquier dispositivo de Windows 10) y su Arduino preparada tal como se detalla en los pasos anteriores de este tutorial, ahora está listo para probar nuestro ejemplo.

1. Preparar la placa de Arduino para conectar un LED con una resistencia a la clavija de 8.
2. Asegúrese de que su Arduino todavía se carga con el ejemplo HelloWorld de voz-eventos y, a continuación, conecte el Arduino en una fuente de alimentación.
3. Ejecute los Shields Virtual de Windows para la aplicación de Arduino en el Windows Phone que preparó anteriormente.
4. Si todo ha correctamente el programa de instalación, el teléfono debe conectar con el boceto de Arduino y le damos la bienvenida con una indicación de audio. Ahora puede decir 'on' u 'off' en el dispositivo Windows 10 para pasar el LED en su Arduino y desactivar!

### <a name="arduino-wiring-sketch-hello-world-example"></a>El cableado de boceto de Arduino: Hello World, ejemplo

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


