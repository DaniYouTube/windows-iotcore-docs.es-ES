---
title: Aplicaciones en segundo plano
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a desarrollar aplicaciones en segundo plano para su dispositivo IoT.
keywords: Windows IOT, aplicaciones en segundo plano
ms.openlocfilehash: ab9e4f66f3829c9758cbc40abfcde50df597a2d3
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918270"
---
# <a name="developing-background-applications"></a>Desarrollo de aplicaciones en segundo plano

> [!NOTE]
> Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.

Las aplicaciones en segundo plano son aplicaciones que no tienen interfaz de usuario directa. Una vez implementadas y configuradas, estas aplicaciones se inician en el inicio del equipo y se ejecutan de forma continua sin limitaciones de uso de recursos de administración de la duración. Si se bloquea o sale del sistema, se reiniciarán automáticamente.
Estas aplicaciones en segundo plano tienen un modelo de ejecución muy simple. Las plantillas crean una clase que implementa la interfaz "IBackgroundTask" y genera el método vacío "Run". Este método "ejecutar" es el punto de entrada a la aplicación.

![Tarea en segundo plano](../media/BackgroundApplications/backgroundTaskScreenshot.png)

Hay un punto crítico a tener en cuenta: de forma predeterminada, la aplicación se cerrará cuando se complete el método Run. Esto significa que las aplicaciones que siguen el patrón de IoT común de ejecutar un servidor que espera la entrada o en un temporizador encontrarán la salida prematura de la aplicación. Para evitar que esto suceda, debe llamar al método "GetDeferral" para evitar que se salga de la aplicación. Puede encontrar más información sobre el patrón de aplazamiento [aquí](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Background.BackgroundTaskDeferral).

## <a name="where-can-background-applications-be-installed-from"></a>¿Dónde se pueden instalar las aplicaciones en segundo plano? 

Puede descargar e instalar plantillas de IoT para habilitar las aplicaciones en segundo plano desde la galería de Visual Studio [aquí](https://go.microsoft.com/fwlink/?linkid=847472).  Como alternativa, puede encontrar las plantillas buscando `Windows IoT Core Project Templates` en la [Galería de Visual Studio](https://visualstudiogallery.msdn.microsoft.com/) o directamente desde Visual Studio en el cuadro de diálogo extensiones y actualizaciones (Herramientas > extensiones y actualizaciones > en línea).

## <a name="what-languages-are-available"></a>¿Qué idiomas están disponibles?

Se pueden encontrar plantillas de **aplicación en segundo plano (IOT)** para:

* **C++** `File > New > Project > Installed > Visual C++ > Windows > Windows IoT Core`
* **C#** `File > New > Project > Installed > Visual C# > Windows > Windows IoT Core`
* **Visual Basic** `File > New > Project > Installed > Visual Basic > Windows > Windows IoT Core`
* `File > New > Project > Installed > JavaScript > Windows > Windows IoT Core` de **JavaScript**

## <a name="how-are-background-applications-used"></a>¿Cómo se usan las aplicaciones en segundo plano? 

La creación de una aplicación en segundo plano es muy similar a la creación de una tarea en segundo plano.  Cuando se inicia la aplicación en segundo plano, se llama al método Run:

```csharp
public void Run(IBackgroundTaskInstance taskInstance)
{
}
```

Cuando finaliza el método Run, a menos que se cree un objeto de aplazamiento, finaliza la aplicación en segundo plano. La práctica habitual, para la programación asincrónica, es realizar un aplazamiento como este:

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

Una vez que se toma un aplazamiento, la aplicación en segundo plano continuará hasta que se llame al método complete del objeto de aplazamiento.

```csharp
deferral.Complete();
```

## <a name="how-do-background-applications-start"></a>¿Cómo se inician las aplicaciones en segundo plano?

Esta pregunta puede dividirse en la implementación y la invocación.  

Para implementar una aplicación en segundo plano, puede:

* Use F5 de Visual Studio (que se compilará, implementará e invocará).  Para obtener más información, consulte nuestro [ejemplo de Hola mundo](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/HelloWorld) en el que se describe cómo implementar e iniciar desde Visual Studio.

> [!NOTE]
> Esto no configurará la aplicación en segundo plano para que se inicie cuando se arranque el dispositivo.

* Cree un AppX en Visual Studio seleccionando Project > Store > crear paquetes de aplicaciones.  Una vez que haya creado un AppX, puede usar el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md) para implementarlo en el dispositivo de Windows 10 IOT Core.

Para invocar una aplicación en segundo plano, puede:

* Como se mencionó anteriormente, la funcionalidad F5 de Visual Studio se implementará e iniciará inmediatamente la aplicación en segundo plano.

> [!NOTE]
> Esto no configurará la aplicación en segundo plano para que se inicie cuando se arranque el dispositivo.

* En el caso de una aplicación en segundo plano que se ha implementado en un dispositivo IoT, puede usar la utilidad iotstartup. exe para configurar la aplicación en segundo plano para que se inicie cuando se arranque el dispositivo.  Para especificar la aplicación en segundo plano como una aplicación de inicio, siga estas instrucciones (**sustituya el nombre** de la aplicación por `BackgroundApplication1` a continuación):

1. Inicie una sesión de PowerShell (PS) con el dispositivo Windows IoT Core tal como se describe [aquí](../connect-your-device/PowerShell.md).

2. En la sesión de PS, escriba:
            
`[<your IP address>]: PS C:\> iotstartup list BackgroundApplication1`

3. Debería ver el nombre completo de la aplicación en segundo plano, es decir, algo parecido a lo siguiente:

`Headed   : BackgroundApplication1-uwp_cqewk5knvpvee!App
Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

4. La utilidad confirma que la aplicación en segundo plano es una aplicación "sin periféricos" y se instala correctamente.  Probablemente verá una entrada para las aplicaciones en segundo plano, pero esto puede no tenerse en cuenta.

5. Ahora, es fácil establecer esta aplicación como una aplicación de inicio. Simplemente escriba el comando:

`[<your IP address>]: PS C:\> iotstartup add headless BackgroundApplication1`

6. La utilidad confirmará que la aplicación en segundo plano se ha agregado a la lista de aplicaciones de inicio sin periféricos:

`Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1`

7. Continúe y reinicie el dispositivo Windows IoT Core. Desde la sesión de PS, puede emitir el comando Shutdown:

`[<your IP address>]: PS C:\> shutdown /r /t 0`

8. Una vez que el dispositivo se haya reiniciado, la aplicación en segundo plano se iniciará automáticamente y Windows 10 IoT Core se asegurará de que se reinicie cada vez que se detenga.  

> [!NOTE]
> Una vez que se registra una aplicación en segundo plano para que se ejecute automáticamente, si la aplicación se cierra o se bloquea, se reiniciará automáticamente.  La aplicación no está informada de la razón por la que se inicia o se reinicia, por lo que si quiere realizar una acción especial en un reinicio, deberá realizar un seguimiento del estado de la aplicación en la aplicación.

9. Puede quitar la aplicación en segundo plano de la lista de aplicaciones de inicio sin periféricos. para ello, escriba el comando:

`[<your IP address>]: PS C:\> iotstartup remove headless BackgroundApplication1`

10. La utilidad confirmará que se ha quitado la aplicación en segundo plano de la lista de aplicaciones de inicio sin periféricos:

`Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee`

## <a name="see-also"></a>Consulta también
Para agregar una aplicación en segundo plano al compilar una imagen personalizada, consulte [crear un paquete appx](../build-your-image/createinstallpackage.md) .
