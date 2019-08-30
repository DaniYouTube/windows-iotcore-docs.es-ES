---
title: Productores de AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo crear un productor de AllJoyn aprendiendo y creando XML introspección y sus distintas características.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167409"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="alljoyn-producers"></a>Productores de AllJoyn

AllJoyn, creado por [AllSeen Alliance](https://allseenalliance.org/), proporciona un marco de trabajo excelente para la creación de aplicaciones y dispositivos conectados en una red proximal, y Windows proporciona la mejor experiencia para usar AllJoyn con la extensión [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) para Visual Studio.  Aunque nuestras herramientas de Excel en la creación de aplicaciones para productores y consumidores, el inicio de un nuevo dispositivo de AllJoyn desde cero puede resultar bastante confuso.

Si tiene una idea para el siguiente dispositivo conectado o un nuevo juguete con el que Tinker y explore, es posible que no pueda usar una de las interfaces estándar ofrecidas por AllSeen Alliance.  Si es así, debe crear un productor AllJoyn nuevo.

Un desarrollador que desea hacer que un nuevo productor de AllJoyn tenga que crear su propio XML de introspección, pero crear introspección XML requiere conocimientos sobre la materia y tiene una curva de aprendizaje significativa para los nuevos desarrolladores.  Este blog reducirá la curva de aprendizaje al desglosar los distintos componentes de introspección XML, describir el propósito y las restricciones de cada componente, y proporcionar buenos ejemplos en términos aproximables.

## <a name="existing-documentation"></a>Documentación existente

Un examen de cursores de los siguientes recursos combinados con este blog debe acelerar la comprensión del desarrollador de introspección XML:

1. [Guía de la API de eventos y acciones de alljoyn](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) : detalles e información general sobre la implementación de alljoyn.
2. [Directrices de diseño del panel de revisión de la interfaz alljoyn](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) : estructura y especificación rigurosas para ALLJOYN introspección XML.
3. [Especificación de bus D](http://dbus.freedesktop.org/doc/dbus-specification.html) : AllJoyn basa introspección XML en esta especificación.

__Los tres tipos de XML de introspección__

Al igual que en la documentación de AllJoyn, encontrará tres tipos de introspección XML:

1. XML de especificación de bus D: baja sobrecarga, comunicación entre procesos con un formato de tipo para la representación de datos.
2. AllJoyn introspección XML: extiende el XML de especificación de bus D con etiquetas XML para almacenar descripciones de texto y aplicar también principios de AllJoyn a la especificación.
3. Introspección de AllJoyn extendido XML: evolución del XML clásico de introspección introducción de tipos con nombre para estructuras y diccionarios.

AllJoyn Studio admite actualmente la especificación de bus D XML y AllJoyn introspección XML; este blog determinará cómo crear y formar el XML introspección de AllJoyn.  El panel de revisión de interfaz (IRB) de AllSeen Alliance usa la nueva introspección de AllJoyn extendida como formato para los envíos formales para las revisiones de estandarización, pero está trabajando en un formato XML Unificado de introspección en un futuro próximo.

## <a name="introspection-high-level-overview"></a>Información general de alto nivel de introspección

Cada productor de AllJoyn anuncia públicamente un XML introspección que muestra la funcionalidad admitida por el productor, tal como se describe a través de señales, propiedades y métodos.  Las soluciones de generación de código, como la de la extensión AllJoyn Studio, se basan en el XML de introspección para crear el código necesario para acelerar el desarrollo.  El XML introspección describe la funcionalidad de un productor en una manera no ambigua y legible, de modo que dos fabricantes diferentes pueden utilizar el XML para implementar un productor con la misma funcionalidad.  Con el mismo token, los desarrolladores sin ningún conocimiento previo de un productor de AllJoyn deberían ser capaces de desarrollar en ese productor en función de su XML.

__Interfaces AllJoyn__

AllJoyn consigue esto dividiendo un XML introspección en varias "interfaces" que representan diferentes agrupaciones lógicas de comportamiento y capacidades.  Las interfaces AllJoyn se denominan mediante una Convención de DNS inverso. Por ejemplo, la interfaz "foo" de la interfaz creada por contoso Ltd., que posee el dominio contoso.com, se escribiría como:

    <interface name="com.contoso.Foo">

Un productor puede implementar cualquier número de interfaces, pero debe implementar todos los componentes de una interfaz que anuncien.  Con el fin de diferenciar y extender los comportamientos, AllJoyn admite la creación de nuevas interfaces con respecto a una jerarquía de interfaz existente. es decir, `Foo.Bar` `com.contoso.Foo` define nuevas funcionalidades para las cosas en la categoría, pero no tiene ninguna dependencia explícita en la interfaz. `com.contoso.Foo.Bar` 

Por ejemplo, tenemos dos interfaces: `com.contoso.Sensor` y `com.contoso.Sensor.Humidity` – "humedad" se encuentra lógicamente en la categoría "sensor".  Alguien que desarrolle un productor de humedad podría optar `com.contoso.Sensor.Humdity` por admitir solo la interfaz, pero también podría optar por admitir la `com.contoso.Sensor` interfaz.  Independientemente de si anuncian una interfaz, los productores deben admitir todas sus funciones.

La `<description>` etiqueta se usa para describir interfaces, funcionalidades y argumentos, y se puede localizar para varios idiomas.  El uso liberal de `<description>` la etiqueta hace que el código XML sea más comprensible y elimine la ambigüedad.

La práctica estándar dicta el uso de la `org.alljoyn.Bus.Secure` anotación en una interfaz para habilitar la seguridad y la autenticación.  Para una autenticación segura, use una clave previamente compartida (PSK) o un intercambio de claves de certificado (ECDSA).  De lo contrario, una autenticación "null" se convierte en el comportamiento predeterminado.  **El mecanismo de autenticación real se produce en la implementación, no en la declaración**. Esta anotación habilita la seguridad pero no especifica el tipo de seguridad utilizado o cómo se implementará.

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

En este ejemplo se muestra una interfaz expuesta por un `com.example.Door.PrivateDoor`dispositivo:. En el ámbito de la interfaz, lo único que nos preocupa es si la comunicación se debe proteger al usar esa interfaz, no qué tipo de mecanismo se está usando.

__Capacidades de interfaz__

Las interfaces declaran sus capacidades con tres miembros de interfaz: métodos, propiedades o señales. Introspección XML también admite anotaciones que describen funcionalidad o restricciones adicionales.  Estas funcionalidades usan la notación UpperCamelCase mientras que los argumentos usan la notación lowerCamelCase.

### <a name="argument-types"></a>Tipos de argumento

Los miembros de interfaz envían y reciben argumentos indicados por un código de tipo ASCII.  Dependiendo del tipo de miembro de interfaz, es posible que los argumentos se hayan enviado al productor desde el consumidor (Direction = "out") o desde el consumidor hasta el productor (Direction = "in").  En la tabla siguiente se proporciona una breve descripción de los tipos usados comúnmente:

> | *Nombre convencional* | *Código de tipo* | *Uso* |
> |----------------- |---------| --- |
> |**BOOLEANO** | b | Representa TRUE (1) o FALSE (0). Se utiliza para obtener información o Estados binarios simples. |
> |**BYTES** | y | Valor entero comprendido entre 0 y 255. Se usa cuando se trabaja con números positivos pequeños. |
> |**UINT16** | q | Valor entero de 0 a 2 ^ 16-1 |
> |**UINT32** | 5\.50 | Valor entero de 0 a 2 ^ 32-1 |
> |**UINT64** | t | Valor entero de 0 a 2 ^ 64-1 |
> |**INT16** | per? | Valor entero de – (2 ^ 15) a 2 ^ 15-1 |
> |**INT32** | i | Valor entero de – (2 ^ 31) a 2 ^ 31-1 |
> |**INT64** | x | Valor entero de – (2 ^ 63) a 2 ^ 63-1 |
> |**HACE** | d | Números de punto flotante de precisión desde – (2 ^ 127) hasta 2 ^ 127-1 |
> |**STRING@** | s | Cadena UTF-8 |
 
Para obtener información general más exhaustiva sobre todos los tipos admitidos, consulte [aquí](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).

En el punto de redactar este documento, use las unidades SI siempre que sea posible y denote claramente las unidades prepensadas. Cuando sea posible, elija el código de tipo más restrictivo para su escenario; por ejemplo, si está representando la edad de una persona en años, use BYTE, no UINT16 o INT16, ya que nadie tendrá una edad negativa o más de 255 años.  Siga siempre las instrucciones más recientes del panel de revisión de la [interfaz AllJoyn (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) .

En la tabla siguiente se resumen las unidades comunes:


> |*Volumen* | *Unidad*|
> |-------- | ---- |
> |**Tiempo absoluto (fecha & hora)** | Segundos desde la época de UNIX (00:00:00 el 1 de enero de 1970) |
> |**Hora del día** | Segundos desde la medianoche |
> |**Intervalo de tiempo** | Segundos |
> |**Consumo** | Bits por segundo |
> |**Tamaño de los datos** | Bytes |
 
### <a name="methods"></a>Métodos

Los consumidores llaman a métodos para modificar el estado de un productor y sus nombres deben empezar con un verbo porque representan solicitudes para que el productor realice una acción.  Los métodos pueden tener argumentos de entrada y salida; en el caso de que no sea necesario enviar ningún mensaje de retorno, aplique la anotación "org. freedesktop. dBu. Method. noresponse".  Sin embargo, los métodos AllJoyn normalmente devuelven un SuccessResult o un FailureResult, lo que otorga a los consumidores comentarios sobre la llamada al método.  El tipo de los argumentos debe cumplir la [especificación de bus D](http://dbus.freedesktop.org/doc/dbus-specification.html). 

___Ejemplo (excluir información de interfaz para mayor comodidad)___

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

*Nota: En la mayoría de los casos, se deben usar propiedades en lugar de métodos para tener acceso al estado de un productor (por ejemplo, usar una propiedad de color en lugar de un método GetColor).*

### <a name="properties"></a>Propiedades

Las propiedades permiten principalmente el acceso al estado de un productor.  Aunque las propiedades técnicamente tienen los valores de acceso de "lectura", "ReadWrite" o "escritura", la funcionalidad de modificación de Estado suele pertenecer a métodos, como tal, los desarrolladores deben tratar de mantener las propiedades como "lectura" y usar "ReadWrite" solo cuando el estado representado esa propiedad es independiente de todas las demás propiedades.  Las propiedades nunca deben ser simplemente "write": modificar el estado sin observación es el rol de los métodos.

Las propiedades se deben anotar para avisar a los consumidores cuando cambian sus valores (opcionalmente, las propiedades pueden heredar esta anotación de su interfaz primaria).  La anotación `org.freedesktop.DBus.Property.EmitsChangedSignal` puede tener cuatro valores:

* "true": cuando cambia la propiedad, el productor emitirá una señal que denota la propiedad cambiada y el nuevo valor. Se utiliza en las propiedades que se usan con frecuencia y requieren supervisión activa, como un "LockState" para una puerta.
* "invalidaciones": cuando la propiedad cambia, el productor emitirá una señal que denota la propiedad modificada pero no el nuevo valor. Se usa en las propiedades que no requieren mucha supervisión (por ejemplo, "WashMode" de una secadora de ropa) o que representan una gran cantidad de datos, como un contenedor.
* "false": cuando cambia la propiedad, el productor no emite ninguna señal. Se usa en las propiedades que se actualizan rápidamente, como una propiedad "TransitCounter" en un próximo de seguimiento de guión de la próximo. Si no se especifica, las propiedades AllJoyn lo utilizan como valor predeterminado.
* "const": la propiedad nunca cambiará el valor y nunca emitirá una señal modificada. Esto se presentará en la versión AllJoyn 16,04; hasta entonces, use "true".

___Ejemplo___

Al expandir el ejemplo anterior, hemos modificado el código XML para incluir las propiedades (excepto los métodos para mayor brevedad).

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

### <a name="signals"></a>Simultáneamente

Use señales para informar a los consumidores de un evento que no pudieron determinar consultando el productor.  Una abertura de puerta se transmitiría a través de la propiedad DoorOpen de un productor con una anotación EmitsChangedProperty "true".  No obstante, alguien que pase a través de la puerta no se puede derivar de cualquier cambio de propiedad, por lo que esto haría una buena señal independiente.  Hacemos referencia a estos tipos de eventos como "sin estado".  Dado que las señales son unidireccionales desde el productor hasta el consumidor, solo pueden contener argumentos "out".

___Example___ 

(sin incluir métodos y propiedades para mayor comodidad):

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

Dado que las señales tienen un ámbito tan estrecho, normalmente aparecen pocas en el XML de un productor.

### <a name="containers"></a>Contenedores

No Combine varios argumentos en una colección compleja como una cadena JSON serializada. La especificación de bus D realiza prestaciones para contenedores de datos: STRUCT, ARRAY, VARIANT y DICT_ENTRY.  Úselos para pasar argumentos que requieran más de tipos básicos.

___VARIANTE___

Las variantes se indican mediante el tipo "v" y pueden contener cualquier [tipo completo](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type). Sin embargo, las variantes deben evitarse siempre que sea posible porque agregan ambigüedad a las definiciones XML.

___DESTRUCTOR___

Los STRUCTs usan "(" y ")" para indicar el principio y el final de una estructura de datos, un solo tipo completo.  Estas estructuras de datos pueden estar anidadas.

Ejemplos:

Un tipo de "(III)" denota una estructura de tres enteros; "(i (II))" denota una estructura de un entero y una estructura de dos enteros, que es diferente del tipo "((II) i)".

___MATRIZ___

Las matrices usan el código de tipo "a" y deben ir seguidos de un único tipo completo.  Las matrices no tienen longitudes fijas, por lo que son similares a una estructura de datos de lista. Las matrices representan un único tipo completo.

Ejemplos:

Un tipo de "AI" representa una matriz de enteros, mientras que "AAI" representa una matriz de enteros.  También se puede utilizar una matriz con STRUCTs: "a (II)".

___DICT_ENTRY___

DICT_ENTRYs función similar a una estructura con restricciones mayores: usan "{" y "}", solo se puede producir como un tipo de elemento de matriz y deben tener exactamente dos tipos completos dentro de las llaves.  El primer tipo representa una "clave" en una estructura de datos del diccionario y la segunda representa el "valor" en el par clave-valor del diccionario.  Una clave debe ser única en un diccionario.

Ejemplo:

Un tipo de {SY} denota un diccionario de claves de cadena y valores de byte.  Usar <description> Etiquetas para describir claves y valores válidos. 

__Ejemplo final y ajxmlcop__

El concepto de contenedores mejora las capacidades del XML existente y proporciona una vía para los nuevos miembros de interfaz útiles.

Una vez que haya terminado de escribir el código XML, use la herramienta de línea de comandos ajxmlcop. exe (disponible en el [origen de Git](https://git.allseenalliance.org/cgit/core/alljoyn.git/) de AllJoyn o [aquí](https://github.com/MS-brock/AllJoynToasterDemo)) para validar el XML.  Use ajxmlcop. exe con el archivo XML como argumento de entrada (por ejemplo, `C:\>ajxmlcop.exe doorExample.xml`) para recibir mensajes de error, de advertencia e informativos.  Esta herramienta proporciona comentarios valiosos sobre la estructura y el formato del XML y el uso de señales, propiedades y métodos.

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

