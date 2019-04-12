---
title: Aplicaciones en segundo plano
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo desarrollar aplicaciones en segundo plano para el dispositivo de IoT.
keywords: Windows iot, aplicaciones en segundo plano
ms.openlocfilehash: 1b3fd831a4cdf3ebb8bc2d80c544344b13115617
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514559"
---
# <a name="developing-background-applications"></a>Desarrollo de aplicaciones en segundo plano

> [!NOTE]
> Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.

Aplicaciones en segundo plano son aplicaciones que no tengan ninguna interfaz de usuario directa. Una vez implementado y configurado, estas aplicaciones se ejecutan durante el inicio de la máquina y ejecutan continuamente sin recursos de administración de limitaciones de usar cualquier duración de proceso. Si bloqueará o salir reiniciará automáticamente el sistema de ellos.
Estas aplicaciones en segundo plano tienen un modelo de ejecución muy sencilla. Las plantillas de crean una clase que implementa la interfaz "IBackgroundTask" y genera el método vacío "Run". Este método de "Run" es el punto de entrada a la aplicación.

![Tarea en segundo plano](../media/BackgroundApplications/backgroundTaskScreenshot.png)

Hay un punto importante a tener en cuenta: de forma predeterminada, la aplicación se cerrará cuando finalice el método de ejecución. Esto significa que las aplicaciones que siguen el patrón de IoT comunes de la ejecución de un servidor en espera para la entrada o en un temporizador encontrará prematuramente la salida de la aplicación. Para evitar que esto suceda debe llamar al método "GetDeferral" para evitar que la aplicación sale. Puede encontrar más información sobre el patrón de aplazamiento [aquí](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).

## <a name="where-can-background-applications-be-installed-from"></a>¿Dónde se puede instalar aplicaciones en segundo plano desde? 

Puede descargar e instalar las plantillas de IoT para habilitar las aplicaciones en segundo plano desde la Galería de Visual Studio [aquí](https://go.microsoft.com/fwlink/?linkid=847472).  Como alternativa, pueden encontrarse las plantillas mediante la búsqueda de `Windows IoT Core Project Templates` en el [Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/) o directamente desde Visual Studio en el cuadro de diálogo Extensiones y actualizaciones (Herramientas > extensiones y actualizaciones > en línea).

## <a name="what-languages-are-available"></a>¿En qué idiomas están disponibles?

**En segundo plano (IoT) de la aplicación** encontrará plantillas para:

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* **JavaScript** `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core`

## <a name="how-are-background-applications-used"></a>¿Cómo se usan aplicaciones en segundo plano? 

Creación de una aplicación en segundo plano es muy similar a la creación de una tarea en segundo plano.  Cuando se inicia la aplicación en segundo plano, se llama al método de ejecución:

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

Cuando finaliza el método Run, a menos que se crea un objeto aplazamiento, finaliza la aplicación en segundo plano. La práctica común para la programación asincrónica es tomar un aplazamiento similar al siguiente:

```csharp
private BackgroundTaskDeferral deferral;
public void Run(IBackgroundTaskInstance taskInstance)
{
    deferral = taskInstance.GetDeferral();
    
    //
    // TODO: Insert code to start one or more asynchronous methods
    //
}
```

Una vez que se toma un aplazamiento, la aplicación en segundo plano continuará hasta que se llama al método Complete del objeto aplazamiento.

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>¿Cómo iniciar aplicaciones en segundo plano?

Esta pregunta puede dividirse en implementación y la invocación.  

Para implementar una aplicación en segundo plano, puede:

* Use F5 de Visual Studio (que compilar, implementar e invocar).  Para obtener más información, consulte nuestra [ejemplo Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) donde se describe cómo implementar e iniciar desde Visual Studio.

> [!NOTE]
> No configurará la aplicación en segundo plano para iniciarse cuando arranca el dispositivo.

* Crear un elemento AppX en Visual Studio seleccionando el proyecto > Store > crear paquetes de aplicaciones.  Una vez haya creado un AppX, puede usar [Windows Device Portal](../manage-your-device/DevicePortal.md) para implementarla en su dispositivo Windows 10 IoT Core.

Para invocar una aplicación en segundo plano, puede:

* Como se mencionó anteriormente, F5 funcionalidad de Visual Studio implementará y comenzar inmediatamente la aplicación en segundo plano.

> [!NOTE]
> No configurará la aplicación en segundo plano para iniciarse cuando arranca el dispositivo.

* Para una aplicación en segundo plano que se ha implementado en un dispositivo de IoT, puede usar la utilidad iotstartup.exe para configurar la aplicación en segundo plano para iniciarse cuando arranca el dispositivo.  Para especificar la aplicación en segundo plano como una aplicación de inicio, siga estas instrucciones (**sustituir el nombre de la aplicación** para `BackgroundApplication1` a continuación):

1. Inicie una sesión de PowerShell (PS) con el dispositivo Windows IoT Core, como se describe [aquí](../connect-your-device/PowerShell.md).

2. En la sesión de PS, escriba:
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. Debería ver el nombre completo de la aplicación en segundo plano, es decir, algo como:

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. La utilidad es confirmar que la aplicación en segundo plano es una aplicación "sin periféricos" y se ha instalado correctamente.  Es probable que vea una entrada Headed también para las aplicaciones en segundo plano, pero pueden omitir.

5. Ahora, es fácil de configurar esta aplicación como una aplicación de' inicio'. Basta con escribir el comando:

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. La utilidad se confirmará que la aplicación en segundo plano se ha agregado a la lista de equipos sin periféricos "aplicaciones de inicio":

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. Siga adelante y reinicie el dispositivo Windows IoT Core. En la sesión de PS, puede emitir el comando de apagado:

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. Una vez que se haya reiniciado el dispositivo, la aplicación en segundo plano se iniciará automáticamente y Windows 10 IoT Core se asegurará de que se reinicia cada vez que se detiene.  

> [!NOTE]
> Una vez que una aplicación en segundo plano se registra para ejecutarse automáticamente, si la aplicación se cierra o se bloquea se reiniciará automáticamente.  La aplicación no se informará del motivo por el que se está iniciando o lo reinicia si desea hacer nada especial en un reinicio, deberá realizar un seguimiento del estado de la aplicación en la aplicación.

9. Puede quitar la aplicación en segundo plano de la lista de aplicaciones de inicio sin periféricos escribiendo el comando:

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. La utilidad se confirmará que la aplicación en segundo plano se ha quitado de la lista de equipos sin periféricos "aplicaciones de inicio":

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

# <a name="see-also"></a>Vea también
Para agregar una aplicación en segundo plano cuando se crea una imagen personalizada, consulte [crear un paquete Appx](../build-your-image/createinstallpackage.md)
