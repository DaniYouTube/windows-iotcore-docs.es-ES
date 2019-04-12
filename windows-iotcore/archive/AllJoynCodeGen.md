---
title: Información general de AllJoynCodeGen
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre AllJoynCodeGen, una herramienta de generación de código que genera un componente en tiempo de ejecución de Windows completo mediante interfaces de AllJoyn.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: c8e9f08c5565c7e4252e1b15858c08402eedb712
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514967"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="alljoyncodegen-overview"></a>Información general de AllJoynCodeGen

Hemos creado una herramienta de generación de código, AllJoynCodeGen, que genera un componente en tiempo de ejecución de Windows completo con una descripción XML de una o varias interfaces de AllJoyn derivado de una especificación o dispositivo.

El componente de Windows en tiempo de ejecución generado por esta herramienta puede usarse en cualquier lenguaje compatible (JS, C#, C++/CX, etc.) mediante las API que están disponibles en el SDK de Windows Universal. Esto significa que puede utilizarse el mismo componente en cualquier plataforma que tiene el paquete de AllJoyn OneCore (servicio de enrutador y dll de la API de C). Un desarrollador, a continuación, puede usar el componente para crear un productor o consumidor de esa interfaz. 

**Tenga en cuenta** para obtener más detalles sobre las AllJoyn C APIs, puede descargar el SDK de Core AllJoyn y documentación en [The Alliance AllSeen](http://go.microsoft.com/fwlink/?LinkId=524584).

## <a name="how-does-alljoyncodegen-work"></a>¿Cómo funciona AllJoynCodeGen?

El flujo básico es como sigue:

1. Un archivo XML creado en el XML de AllJoyn (actualmente en el formato de dBu introspección) que describe el servicio se introduce en la herramienta de generación de código.
2. La herramienta AllJoynCodeGen genera código que da como resultado un componente de Windows en tiempo de ejecución. Este código generado se basa en **MSAJAPI.lib** y [Windows.Devices.AllJoyn](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx) desde el SDK de Windows 10.
3. El desarrollador compila una aplicación que consume este componente.
4. En tiempo de ejecución, la aplicación del desarrollador cargará el componente de Windows en tiempo de ejecución generado por la herramienta (p. ej.: foo.dll,), así como las DLL en el cuadro **MSAJAPI.dll** y **Windows.Devices.AllJoyn.dll**.

El siguiente diagrama de flujo de trabajo ilustra este proceso:

![Diagrama de AllJoyn CodeGen](../media/AllJoyn/alljoyncodegen.png)

## <a name="running-from-the-command-line"></a>Ejecutar desde la línea de comandos

La herramienta AllJoynCodeGen actualmente existe como una herramienta de línea de comandos se incluye con el SDK de Windows 10. Para ejecutar la herramienta pase un archivo XML válido mediante la siguiente cadena:

    AllJoynCodeGen –i Foo.xml –o c:\users\developer1\documents\Foo\

## <a name="reviewing-the-output"></a>Revisar la salida

Las clases generadas encapsular funcionalidad expuesta por la API de C de núcleo. Dado que el código generado es una abstracción, esto es no es una asignación 1 a 1. La siguiente tabla muestra qué núcleo C++ cada clase de código generado se incluyen las API. Los siguientes marcadores de posición se utilizan para los nombres generados en la tabla:

* `<Foo>` es el nombre de la interfaz definida en el archivo xml
* `<Signal>` es el nombre de una señal, tomado del archivo xml
* `<Method>` es el nombre de un método, tomado del archivo xml
* `<Property>` es el nombre de una propiedad, tomado del archivo xml


> | Clase de Windows en tiempo de ejecución |  | Descripción | Core C++ API |
> | ------------------------ | --- | --------- | ---------- |
> | `<Foo>`Monitor |  | Búsqueda de productores que anuncia el servicio de destino | *BusListener* clase; *BusAttachment* clase |
> | `<Foo>`JoinSessionResult |  | Notifica el éxito o fracaso de participar en una sesión y expone un `<Foo>Consumer` de instancia para la sesión si la combinación se realizó correctamente. | *JoinSessionAsyncCB* clase; *QStatus* |
> | `<Foo>`Producer |  | Anuncia un servicio y expone los controladores de eventos de AllJoyn. | *BusObject* clase; *BusAttachment* clase; *InterfaceDescription* clase; *SessionPortListener* clase; *Mensaje* clase |
> | `<Foo>`Señales |  | Expone métodos y controladores para enviar y recibir señales. Usa los productores y consumidores. | *BusObject* clase; *InterfaceDescription* clase; *Mensaje* clase |
> | `<Foo>`Consumidor |  | Interactúa con un servicio después de que se ha descubierto. | *ProxyBusObject* clase; *InterfaceDescription* clase; *SessionListener* clase; *Mensaje* clase |
> | `<Foo>``<Method>`CalledEventArgs |  | Argumentos pasan a métodos en `EventAdapters.<Foo>ServiceEventAdapter`. | *Mensaje* clase |
> | `<Foo>``<Method>`Resultado |  | Utilizado por las implementaciones de método en el<Foo>servicio para informar el éxito o fracaso de la llamada, así como los valores de devolución. | *Mensaje* clase; *QStatus* |
> | `<Foo>``<Signal>`ReceivedEventArgs |  | Argumentos pasados a una señal en <Foo>señales. | *Mensaje* clase |


## <a name="build-guide"></a>Guía de generación

#### <a name="creating-the-component"></a>Crear el componente

El código generado debe incluirse en un componente que comparte el mismo nombre de la interfaz que el XML. Por ejemplo, si el XML de una Tostadora se define como com.microsoft.sample.toaster, se crearía un com.microsoft.sample del componente en tiempo de ejecución. 

Como alternativa, puede asignar el nombre del componente que desee (por ejemplo, fooCodeGenComponent), pero debe actualizar manualmente el espacio de nombres raíz en las propiedades del proyecto para ser el mismo que el nombre de interfaz.

> [!TIP]
> Puede encontrar el espacio de nombres raíz en el archivo pch.h que se genera a partir de la herramienta AllJoynCodeGen.
