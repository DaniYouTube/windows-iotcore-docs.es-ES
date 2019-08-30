---
title: Información general de AllJoynCodeGen
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre AllJoynCodeGen, una herramienta de generación de código que genera un Windows Runtime componente completo mediante interfaces AllJoyn.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: c8e9f08c5565c7e4252e1b15858c08402eedb712
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167751"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="alljoyncodegen-overview"></a>Información general de AllJoynCodeGen

Hemos creado una herramienta de generación de código, AllJoynCodeGen, que genera un componente Windows Runtime completo mediante una descripción XML de una o varias interfaces AllJoyn derivadas de una especificación o un dispositivo.

El componente de Windows Runtime generado por esta herramienta se puede usar en cualquier lenguaje compatible (JS C#, C++,/CX, etc.) mediante las API que están disponibles en la Windows SDK universal. Esto significa que se puede usar el mismo componente en cualquier plataforma que tenga el paquete OneCore AllJoyn (servicio de enrutador y dll de la API de C). Un desarrollador puede usar el componente para crear un productor o un consumidor de esa interfaz. 

**Nota:**  Para obtener más información sobre las API de C de AllJoyn, puede descargar el SDK del núcleo de AllJoyn y la documentación en [AllSeen Alliance](http://go.microsoft.com/fwlink/?LinkId=524584).

## <a name="how-does-alljoyncodegen-work"></a>¿Cómo funciona AllJoynCodeGen?

El flujo básico es el siguiente:

1. Un archivo XML creado en el XML AllJoyn (actualmente, el formato dBu introspección) que describe el servicio se introduce en la herramienta CODEGEN.
2. La herramienta AllJoynCodeGen genera código que da como resultado un componente de Windows Runtime. Este código generado se basa en **MSAJAPI. lib** y [Windows. Devices. AllJoyn](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.alljoyn.aspx) del SDK de Windows 10.
3. El desarrollador crea una aplicación que consume este componente.
4. En tiempo de ejecución, la aplicación del desarrollador cargará el componente de Windows Runtime generado por la herramienta (por ejemplo: foo. dll,) así como los archivos dll **MSAJAPI. dll** y **Windows. Devices. AllJoyn. dll**.

El siguiente diagrama de flujo de trabajo ilustra este proceso:

![Diagrama de la CodeGen de AllJoyn](../media/AllJoyn/alljoyncodegen.png)

## <a name="running-from-the-command-line"></a>Ejecutar desde la línea de comandos

La herramienta AllJoynCodeGen existe actualmente como una herramienta de línea de comandos incluida con el SDK de Windows 10. Para ejecutar la herramienta, pase un archivo XML válido mediante la siguiente cadena:

    AllJoynCodeGen –i Foo.xml –o c:\users\developer1\documents\Foo\

## <a name="reviewing-the-output"></a>Revisar la salida

Las clases generadas ajustan la funcionalidad expuesta por la API básica de C. Dado que el código generado es una abstracción, no se trata de una asignación de uno a uno. En la tabla siguiente se muestran C++ las API principales que incluyen cada clase de código generado. Los siguientes marcadores de posición se utilizan para los nombres generados en la tabla:

* `<Foo>`es el nombre de la interfaz definida en el archivo XML.
* `<Signal>`es el nombre de una señal tomada del archivo XML
* `<Method>`es el nombre de un método, tomado del archivo XML.
* `<Property>`es el nombre de una propiedad tomada del archivo XML.


> | Windows Runtime (clase) |  | Descripción | API C++ principal |
> | ------------------------ | --- | --------- | ---------- |
> | `<Foo>`Monitor |  | Busca productores que anuncian el servicio de destino. | Clase *BusListener* ; Clase *BusAttachment* |
> | `<Foo>`JoinSessionResult |  | Notifica si la combinación se ha realizado correctamente o no, y expone una `<Foo>Consumer` instancia de para la sesión si la combinación se realizó correctamente. | Clase *JoinSessionAsyncCB* ; *QStatus* |
> | `<Foo>`Creador |  | Anuncia un servicio y expone Controladores para eventos AllJoyn. | Clase *BusObject* ; Clase *BusAttachment* ; Clase *InterfaceDescription* ; Clase *SessionPortListener* ; *Message* (clase) |
> | `<Foo>`Simultáneamente |  | Expone métodos y controladores para enviar y recibir señales. Lo usan los productores y los consumidores. | Clase *BusObject* ; Clase *InterfaceDescription* ; *Message* (clase) |
> | `<Foo>`Independiente |  | Interactúa con un servicio una vez detectado. | Clase *ProxyBusObject* ; Clase *InterfaceDescription* ; Clase *SessionListener* ; *Message* (clase) |
> | `<Foo>``<Method>`CalledEventArgs |  | Argumentos pasados a métodos en `EventAdapters.<Foo>ServiceEventAdapter`. | *Message* (clase) |
> | `<Foo>``<Method>`Da |  | Lo usan las implementaciones de métodos<Foo>en el servicio I para informar del éxito o error de la llamada, así como de los valores devueltos. | Clase de *mensaje* ; *QStatus* |
> | `<Foo>``<Signal>`ReceivedEventArgs |  | Argumentos pasados a una señal en <Foo>señales. | *Message* (clase) |


## <a name="build-guide"></a>Guía de compilación

#### <a name="creating-the-component"></a>Crear el componente

El código generado debe estar incluido en un componente que comparta el mismo nombre de interfaz que el XML. Por ejemplo, si el XML de un sistema tostador se define como com. Microsoft. sample. tostador, crearía un componente de tiempo de ejecución com. Microsoft. sample. 

Como alternativa, puede asignar al componente el nombre que desee (por ejemplo, fooCodeGenComponent), pero debe actualizar manualmente el espacio de nombres raíz en las propiedades del proyecto para que sea el mismo que el nombre de la interfaz.

> [!TIP]
> Puede encontrar el espacio de nombres raíz en el archivo PCH. h que se genera a partir de la herramienta AllJoynCodeGen.
