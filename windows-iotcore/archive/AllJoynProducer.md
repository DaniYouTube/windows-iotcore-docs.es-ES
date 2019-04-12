---
title: Productores AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo hacer que un productor AllJoyn por aprender y creación introspección XML y sus características diferentes.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514512"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="alljoyn-producers"></a>Productores AllJoyn

AllJoyn, creado por el [AllSeen Alliance](https://allseenalliance.org/), proporciona un marco excelente para hacer que los dispositivos conectados y aplicaciones en una red articulaciones próximas y Windows proporciona la mejor experiencia para el uso de AllJoyn con las [AllJoyn Studio ](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extensión para Visual Studio.  Mientras que sobresale con nuestras herramientas de creación de aplicaciones para los productores y consumidores, puede resultar muy confuso a partir de un nuevo dispositivo AllJoyn desde cero.

Si tiene alguna idea para el dispositivo conectado excelente siguiente o un juguete nuevo con la que se va a realizar ajustes y explore, es posible que no pueda usar una de las interfaces estándares que ofrece la alianza AllSeen.  Si es así, deberá crear un productor AllJoyn completamente nuevo.

Un desarrollador que desean realizar un productor AllJoyn nuevo debe crear su propio XML introspección, pero crear XML de introspección requiere experiencia en la materia y tiene una considerable curva de aprendizaje para desarrolladores nuevo.  Esta entrada de blog, reduce la curva de aprendizaje desglosando los distintos componentes de introspección XML, que describe el propósito y las restricciones de cada componente, y proporcionando buenos ejemplos en términos asequible.

## <a name="existing-documentation"></a>Documentación existente

Un examen de los siguientes recursos que se combina con esta entrada de blog debe acelerar developer comprensión de introspección XML:

1. [Guía de la API de acciones y eventos de AllJoyn](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn información general y detalles de implementación.
2. [Instrucciones de diseño de AllJoyn interfaz Review Board](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -estructurar estrictos y la especificación para AllJoyn introspección XML.
3. [Especificación de Bus de D](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn basa introspección XML en esta especificación.

__Los tres tipos de introspección XML__

Como leer detenidamente la documentación de AllJoyn, encontrará tres tipos de introspección XML:

1. XML de especificación de Bus de D: comunicación entre procesos, de baja sobrecarga con un formato de tipo para la representación de datos.
2. Introspección AllJoyn XML: amplía XML de especificación de Bus de D con las etiquetas XML que contiene descripciones textuales al aplicar también AllJoyn principios para la especificación.
3. Había extendido AllJoyn introspección XML: evolución de la introducción de introspección XML clásico había denominado tipos para las estructuras y diccionarios.

AllJoyn Studio actualmente es compatible con XML de especificación de Bus de D y AllJoyn introspección XML; este blog determinará cómo crear y formulario AllJoyn introspección XML.  Interfaz Review Board (IRB de la alianza AllSeen) usa el nuevo introspección de AllJoyn extendido como el formato para envíos formales para las revisiones de estandarización, pero está trabajando en un formato XML de introspección unificada para el futuro próximo.

## <a name="introspection-high-level-overview"></a>Introducción de alto nivel introspección

Cada productor AllJoyn anuncia públicamente un archivo XML de introspección presenta funcionalidad admitida del productor: interfaces como se describe a través de las señales, propiedades y métodos.  Soluciones de generación de código, como el de la extensión AllJoyn Studio, dependen de introspección XML para crear el código necesario para acelerar el desarrollo.  Introspección XML describe la funcionalidad de un productor de forma no ambigua y legible que dos distintos fabricantes pueden usar el código XML para implementar un productor con la misma funcionalidad.  Con el mismo token, los desarrolladores con ningún conocimiento anterior de un productor AllJoyn deberían poder desarrollar en que el productor según su XML.

__Interfaces de AllJoyn__

Para hacerlo, AllJoyn dividir un archivo XML de introspección en diversas "interfaces" que representan diferentes agrupaciones lógicas de comportamiento y las funcionalidades.  Interfaces de AllJoyn se denominan utilizando una convención de DNS inversa. Por ejemplo, la interfaz de "Foo" creada por Contoso Ltd., que posee el dominio contoso.com, se escribiría como:

    <interface name="com.contoso.Foo">

Un productor puede implementar cualquier número de interfaces, pero debe implementar todos los componentes de una interfaz que anuncie.  Con el fin de diferenciar y extender el comportamiento, AllJoyn admite crear interfaces nuevas con respecto a una jerarquía de interfaz existente; es decir, `com.contoso.Foo.Bar` define nuevas capacidades de las cosas en el `Foo.Bar` categoría, pero no tiene ninguna dependencia explícita en el `com.contoso.Foo` interfaz. 

Por ejemplo, tenemos dos interfaces: `com.contoso.Sensor` y `com.contoso.Sensor.Humidity` : "Humedad" lógicamente cae por debajo de la categoría "Sensor".  Alguien desarrollar un productor de humedad podría optar por admitir solamente el `com.contoso.Sensor.Humdity` interfaz, pero también podría optar por admitir la `com.contoso.Sensor` interfaz.  En cualquier caso, si anuncia una interfaz, a continuación, los productores deben admitir todas sus funciones.

El `<description>` etiqueta se utiliza para describir interfaces, capacidades y los argumentos y se pueden localizar para varios idiomas.  El uso racional de la `<description>` etiqueta a la que hace que el código XML sea más comprensible y elimina la ambigüedad.

Una práctica estándar dicta el uso de la `org.alljoyn.Bus.Secure` anotación en una interfaz para habilitar la autenticación y seguridad.  Para una autenticación segura, utilice una clave precompartida (PSK) o un intercambio de claves de certificado (ECDSA).  En caso contrario, una autenticación de "null" se convierte en el comportamiento predeterminado.  **El mecanismo de autenticación real se produce en la implementación, no la declaración**. Esta anotación habilita la seguridad pero no especifica el tipo de seguridad que utilizan o cómo se implementarán.

___Ejemplo___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <annotation name="org.allJoyn.Bus.Secure" value="true" />
 
    <description language="en">
 
      Private interface for a Door the consumer owns. 
 
    </description>
 
  </interface>
 
</node>
```

En este ejemplo se muestra una interfaz expuesta por un dispositivo: `com.example.Door.PrivateDoor`. En el ámbito de la interfaz, lo único que nos preocupa es si debe protegerse comunicación cuando se usa esa interfaz, no se está usando el tipo de mecanismo.

__Capacidades de interfaz__

Las interfaces declarar sus capacidades con tres miembros de interfaz: métodos, propiedades o señales. Introspección XML también admite las anotaciones que describan una funcionalidad adicional o restricciones.  Estas funcionalidades con notación UpperCamelCase mientras lowerCamelCase con argumentos de notación.

### <a name="argument-types"></a>Tipos de argumento

Los miembros de interfaz enviar y reciben los argumentos que se indica con un código de tipo ASCII.  Según el tipo de miembro de interfaz, argumentos han se pueden enviar al productor del consumidor (dirección = "out") o desde el productor al consumidor (dirección = "in").  En la tabla siguiente proporciona una breve descripción de los tipos más comunes:

> | *Nombre convencional* | *Tipo de código* | *Usar* |
> |----------------- |---------| --- |
> |**BOOLEANO** | b | Representa TRUE (1) o FALSE (0). Se usa para información binaria simple o Estados. |
> |**BYTES** | y | Valor entero comprendido entre 0 y 255. Se utiliza cuando se trabaja con un número positivo pequeño. |
> |**UINT16** | q | Valor entero entre 0 y 2 ^ 16-1 |
> |**UINT32** | u | Valor entero entre 0 y 2 ^ 32-1 |
> |**UINT64** | tar | Valor entero entre 0 y 2 ^ 64-1 |
> |**INT16** | per? | Valor entero entre –(2^15) y 2 ^ 15-1 |
> |**INT32** | i | Valor entero entre –(2^31) y 2 ^ 31-1 |
> |**INT64** | x | Valor entero entre –(2^63) y 2 ^ 63-1 |
> |**DOBLE** | d | Precisión de números decimales de –(2^127) a 2 ^ 127-1 |
> |**CADENA** | s | Cadena UTF-8 |
 
Para obtener una descripción más exhaustiva de todos los tipos admitidos, consulte [aquí](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).

Cuando se redactó este documento, use las unidades que sea posible y denotar claramente unidades deseadas. Cuando sea posible, elija el tipo de código más restrictivo para su escenario; Por ejemplo, si va a representar la edad de una persona en años, a continuación, utilizar BYTE, no UINT16 o INT16, ya que nadie será una negativo edad o más de 255 años de antigüedad.  Siga siempre la versión más reciente [AllJoyn interfaz Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) directrices.

La tabla siguiente resume las unidades comunes:


> |*Cantidad* | *Unidad*|
> |-------- | ---- |
> |**Tiempo absoluto (fecha y hora)** | Segundos transcurridos desde la época de UNIX (00: 00:00 en 1 de enero de 1970) |
> |**Hora del día** | Segundos transcurridos desde medianoche |
> |**Intervalo de tiempo** | Segundos |
> |**Ancho de banda** | Bits por segundo |
> |**Tamaño de los datos** | Bytes |
 
### <a name="methods"></a>Métodos

Los consumidores de llamar a métodos para modificar el estado de un productor y sus nombres deben empezar con un verbo, ya que representan las solicitudes para el productor realizar una acción.  Los métodos pueden tener de entrada y salida argumentos; en el caso de que no hay que enviar ningún mensaje de retorno, se aplica la anotación "org.freedesktop.DBus.Method.NoReply".  Sin embargo, métodos de AllJoyn normalmente devuelven un SuccessResult o un FailureResult, ofreciendo a comentarios de los consumidores acerca de la llamada al método.  El tipo de los argumentos debe cumplir el [D Bus especificación](http://dbus.freedesktop.org/doc/dbus-specification.html). 

___Ejemplo (excepto la información de la interfaz para su comodidad)___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!-- Method showing arguments with only directions in -->
 
    <method name="SetPasscode">
 
      <description language="en">
 
        Allows owner of the door to change the code needed to unlock it.
 
      </description>
 
      <argument name="currentPasscode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="newPasscode" type="u" direction="in">
 
        <description language="en">
 
          New code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!-- Method showing both arguments in and out -->
 
    <method name="UnlockDoor">
 
      <description language="en">
 
        Allows guests with the code to unlock the door.
 
      </description>
 
      <argument name="passcode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="welcomeMessage" type="s" direction="out">
 
        <description language="en">
 
          Message from the owner of the door.
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
</node>
```

*Nota: En la mayoría de los casos, las propiedades deben usarse en lugar de métodos para tener acceso a estado del productor (por ejemplo, usar una propiedad de Color en lugar de un método GetColor).*

### <a name="properties"></a>Propiedades

Propiedades principalmente permiten el acceso al estado del productor.  Aunque técnicamente, las propiedades tienen valores de acceso de "lectura", "readwrite" o "escritura", funcionalidad de modificación de estado generalmente pertenece a los métodos, por lo tanto, los desarrolladores deben esforzarse por mantener propiedades como "lectura" y use "readwrite" solo cuando el estado representado por esa propiedad es independiente de todas las demás propiedades.  Las propiedades nunca deben ser simplemente "escritura": modificar el estado sin observación es la función de los métodos.

Se deben anotar propiedades a los consumidores alertas cuando cambian sus valores (si lo desea, las propiedades pueden heredar esta anotación de su interfaz primaria).  La anotación `org.freedesktop.DBus.Property.EmitsChangedSignal` puede tener cuatro valores:

* "true": cuando se cambia la propiedad, el productor emitirá una señal que indica la propiedad que ha cambiado y el nuevo valor. Se utiliza en las propiedades que se utilizan con frecuencia y que requieren una supervisión activa, como "LockState" para una puerta.
* "invalida": cuando cambia la propiedad, el productor emitirá una señal que indica la propiedad que ha cambiado, pero no el nuevo valor. Se utiliza en las propiedades que no requieren supervisión pesada (por ejemplo, el "WashMode" un secador de ropas) o representan una gran cantidad de datos, como un contenedor.
* "false": cuando se cambia la propiedad, el productor no emite ninguna señal. Se utiliza en las propiedades que actualizan rápidamente, por ejemplo, una propiedad "TransitCounter" en un torniquete metro seguimiento de personas que realiza el metro. Si no se especifica, las propiedades de AllJoyn Úselo como valor predeterminado.
* "const": la propiedad nunca cambiará valor y nunca emitir una señal modificada. Se trata de introducidas en la versión 16.04 AllJoyn; hasta entonces, utilice "true".

___Ejemplo___

Ampliar el ejemplo anterior, hemos modificado el código XML para incluir propiedades (excepto los métodos por razones de brevedad).

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Read property that sends a signal when the value changes -->
 
    <property name="IsLocked" type="b" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door may freely lock and unlock the door.
 
      </description>
 
    </property>  
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!—- Read-only property that never sends a signal and never changes -->
 
    <property name="Owner" type="s" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door is public knowledge.
 
      </description>
 
    </property>
 
  </interface>
 
</node>
```

### <a name="signals"></a>Señales

Señales de uso para informar a los consumidores de un evento que no puede determinar consultando el productor.  Apertura de una puerta se podría transmitir a través de propiedad de un productor DoorOpen con una anotación EmitsChangedProperty "true".  Alguien pasa a través de la puerta, sin embargo, no puede derivar de los cambios de propiedades, por lo que esto provocaría una señal de buena independiente.  Nos referimos a estos tipos de eventos como "sin estado".  Puesto que las señales son unidireccionales del productor al consumidor, solo puede contener "argumentos out".

___Ejemplos___ 

(excepto los métodos y propiedades para su comodidad):

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Signals may contain arguments about non-state information -->
 
    <signal name="ThresholdCrossed" sessioncast="true">
 
      <description>
 
        Signal to notify owner whenever anyone passes through the door.
 
      </description>
 
      <argument name="crossedInward" type="b" direction="out">
 
        If true, someone entered; if false, someone left.
 
      </argument>
 
    </signal>
 
  </interface>
 
</node>
```

Normalmente puesto que las señales tienen este tipo de un ámbito restringido, pocos aparecen en el XML del productor.

### <a name="containers"></a>Contenedores

No combine varios argumentos en una colección compleja como una cadena JSON serializada. La especificación de Bus de D hace prestaciones para los contenedores de datos, STRUCT, matriz, variante y DICT_ENTRY.  Úselas para pasar argumentos que requieren más de los tipos básicos.

___VARIANT___

Las variantes se denotan mediante el tipo "v" y puede contener ninguno [único de tipo completo](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type). Sin embargo, las variantes deben evitarse siempre que sea posible porque agregan ambigüedad definiciones XML.

___STRUCT___

Uso de STRUCTs "(" y ")" para denotar el principio y al final de una estructura de datos: un único tipo completo.  Estas estructuras de datos pueden estar anidadas.

Ejemplos:

Un tipo de "(iii)" denota una estructura de tres enteros; "(i(ii))" denota una estructura de un entero y una estructura de dos enteros, que es distinta del tipo "((ii))".

___MATRIZ___

Las matrices de usar el código de tipo "a" y debe ir seguido por un único tipo completo.  Las matrices no tienen longitudes de conjunto, por lo que son similares a una estructura de datos de lista. Matrices representan un único tipo completo.

Ejemplos:

Un tipo de "ai" representa una matriz de enteros, mientras que "aai" representa una matriz de una matriz de enteros.  Una matriz se puede utilizar con las estructuras también: "a(ii)".

___DICT_ENTRY___

Función DICT_ENTRYs similar a un STRUCT con mayores restricciones: usan "{" y "}", solo se puede producir como un tipo de elemento de matriz y debe tener exactamente dos tipos entre las llaves completos.  El primer tipo representa una "clave" en una estructura de datos de diccionario y la segunda representa el "valor" par de clave-valor del diccionario.  Una clave debe ser única en un diccionario.

Por ejemplo:

Un tipo de una {sy} denota un diccionario de claves de cadena y valores de tipo byte.  Usar <description> etiquetas para describir los valores y claves válidas. 

__Final ejemplo y ajxmlcop__

El concepto de contenedores mejora las capacidades de XML existente, además de proporcionar una vía para nuevos miembros de interfaz útil.

Cuando haya terminado de escribir el código XML, utilice la herramienta de línea de comandos ajxmlcop.exe (disponible en el AllJoyn [git origen](https://git.allseenalliance.org/cgit/core/alljoyn.git/) o [aquí](https://github.com/MS-brock/AllJoynToasterDemo)) para validar el XML.  Use ajxmlcop.exe con el archivo XML como el argumento de entrada (por ejemplo, `C:\>ajxmlcop.exe doorExample.xml`) para recibir el error, advertencia y mensajes informativos.  Esta herramienta proporciona valiosos comentarios sobre la estructura y el formato de XML y el uso de las señales, propiedades y métodos.

``` xml
<node>
  <interface name="com.example.Door.PrivateDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door.  Private interface that can only be used by the producer’s owner.
    </description>
    <method name="SetPasscode">
      <description language="en">
        Change the code needed to unlock the door.
      </description>
      <argument name="currentPasscode" type="u" direction="in">
        <description language="en">
          Current code needed to unlock door
        </description>
      </argument>
      <argument name="newPasscode" type="u" direction="in">
        <description language="en">
          New code needed to unlock door
        </description>
      </argument>
    </method>
    <method name="UpdateGuestRatings">
      <description language="en">
        Update the list of guests and their personality scores.
      </description>
      <annotation name="org.freedesktop.DBus.Method.NoReply" value="true" />
      <argument name="guestName" type="s">
        <description language="en">
          The name of the guest being entered.
        </description>
      </argument>
      <argument name="qualityScores" type="a{sy}">
        <description language="en">
          DICTIONARY[Key:(string)guestQuality, Value:(byte)score]
          KEYs: "Friendly", "Social", "Punctual" 
          VALUEs: [0-10]
          The qualities of the guest, scored appropriately. If the guestName matches an existing entry, this updates that entry.
        </description>
      </argument>
    </method>
    <method name="SetDoorSecurity">
      <description language="en">
        Close and lock the door or unlock the door.
      </description>
      <argument name="secured" type="b" direction="in">
        <description language="en">
          If TRUE, shut and lock the door.
          If FALSE, unlock the door.
        </description>
      </argument>
    </method>
    <property name="MessageBook" type="a(ss)" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="invalidates"/>
      <description language="en">
        (struct)[(string)guestName, (string)message]
        A list of names of people and the messages they have left.
      </description>
    </property>
    <property name="GuestRatings" type="a(sa{sy})" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        ARRAY[(string)guestName, DICTIONARY(Key:(string)guestQuality, Value:(byte)score)]
        KEYs: "Friendly", "Social", "Punctual"
        VALUEs: [0-10]
        A collection of the previous guests and their scored qualities.
      </description>
    </property>
    <property name="IsLocked" type="b" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">
        Owner of the door may freely lock and unlock the door.
      </description>
    </property>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <signal name="ThresholdCrossed" sessioncast="true">
      <description>
        Signal to notify owner whenever anyone passes through the door.
      </description>
      <argument name="crossedInwards" type="b" direction="out">
        If true, someone entered; if false, someone left.
      </argument>    
    </signal>
  </interface>
  <interface name="com.example.Door.PublicDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door. Public interface that can be used by any consumer.
    </description>
    <method name="UnlockDoor">
      <description language="en">
        Allows guests with the code to unlock the door.
      </description>
      <argument name="passcode" type="u" direction="in">
        <description language="en">
          Current code (00000000 to 99999999) needed to unlock door
        </description>
      </argument>
      <argument name="welcomeMessage" type="s" direction="out">
        <description language="en">
          Message from the owner of the door.
        </description>
      </argument>
    </method>
    <method name="LeaveMessage">
      <description language="en">
        Leave a message for the owner of the door.
      </description>
      <argument name="guestName" type="s" direction="in">
        <description language="en">
          Name of guest leaving a message
        </description>
      </argument>
      <argument name="message" type="s" direction="in">
        <description language="en">
          Message left for owner of the door
        </description>
      </argument>
    </method>
    <method name="AnnouncePresence">
      <description language="en">
        Send a message to the owner of the door.
      </description>
      <argument name="announcingGuest" type="s" direction="in">
        <description language="en">
          Name of the guest announcing their presence.
        </description>
      </argument>
      <argument name="forcefulnessOfAnnouncment" type="y" direction="in">
        <description language="en">
          Degree to which the guest attempts to make their presence known, on bounds [1:10], where 1 is softly and 10 is aggressively.
        </description>
      </argument>
    </method>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <property name="Owner" type="s" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Owner of the door is public knowledge.
      </description>
    </property>
  </interface>
</node>
```

