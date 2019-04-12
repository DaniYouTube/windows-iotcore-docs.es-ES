---
title: Pérdidas de memoria de investigación
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: Obtenga información sobre cómo investigar pérdidas de memoria.
keywords: pérdidas de iot, Visual Studio, Windows, solución de problemas
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514472"
---
# <a name="investigating-memory-leaks"></a>Investigación de pérdidas de memoria

La mejor herramienta para investigar pérdidas de memoria en Windows IoT Core con Visual Studio es el integrado [herramientas de diagnóstico](https://docs.microsoft.com/visualstudio/profiling/memory-usage)

![Herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticTools.PNG)

Para las aplicaciones de primer plano puede [siga la documentación](https://docs.microsoft.com/visualstudio/profiling/memory-usage).

Sin embargo, estas herramientas no funcionan directamente con un Windows IoT Core **aplicación en segundo plano**. Es una forma de perfilar el código utilizado en una aplicación en segundo plano incluirlo en una aplicación en primer plano para el análisis:

1. Agregar un **aplicación vacía** a la **aplicación en segundo plano** solución
2. Haga clic en el **aplicación vacía** hace referencia y agregue una referencia a la **aplicación en segundo plano**
3. Cambiar el **aplicación en segundo plano** método Run() para comprobar si el parámetro taskInstance es null y controlarlos casos de manera diferente.
4. Desde el **BlankApp** llamar BackgroundApp::Run(null)
5. Establezca un punto de interrupción en la llamada a BackgroundApp::Run
6. Cuando se alcanza el punto de interrupción, busque el **herramientas de diagnóstico** windows y haga clic en el ![instantánea](../media/MemoryLeaks/Snapshot.PNG) botón.

8. Reproducir el problema
9. Toma otra instantánea
10. Use la **herramientas de diagnóstico** ventana para diagnosticar la pérdida.

## <a name="create-a-test-app"></a>Crear una aplicación de prueba

Comencemos con una aplicación que asigna memoria y no lo libere para simular una pérdida.
Empiece por crear un nuevo C# en segundo plano de la aplicación: [Desarrollo de aplicaciones en segundo plano](./BackgroundApplications.md)

Reemplace el código de StartupTask.cs con este
```C#
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Threading;
using Windows.ApplicationModel.Background;
using Windows.System;

namespace LeakyBackgroundApp
{
    public sealed class StartupTask : IBackgroundTask
    {
        private Timer timer;
        private BackgroundTaskDeferral deferral;
        List<byte[]> buffer = new List<byte[]>();
        private const ulong minRemaining = 300 * 1024 * 1024;

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            deferral = taskInstance.GetDeferral();
            timer = new Timer(Timer_Tick, null, 500, 500);
        }

        private void Timer_Tick(object state)
        {
            ulong remaining = (MemoryManager.AppMemoryUsageLimit - MemoryManager.AppMemoryUsage);
            ulong chunkSize = remaining / 100;

            try
            {
                if (remaining > minRemaining)
                {
                    var chunk = new byte[chunkSize];

                    // force virtual memory to be commited by writing to it
                    for (int i = 0; i < chunk.Length; i += 4096)
                    {
                        chunk[i] = 0xDA;
                    }

                    // "leak" memory by adding it to the list
                    buffer.Add(chunk);
                    Debug.WriteLine(String.Format("Allocated {0} chunk(s)", buffer.Count));
                }
                else
                {
                    timer.Change(Timeout.Infinite, Timeout.Infinite);
                }
            }
            catch (OutOfMemoryException ex)
            {
                Debug.Write(ex.Message);
                timer.Change(Timeout.Infinite, Timeout.Infinite);
            }
        }
    }
}
```

En este punto si ejecuta la aplicación en segundo plano en el dispositivo de IoT debe consumir una gran cantidad de memoria y nunca lo libere. Si intenta usar las herramientas de diagnóstico en este momento verá algo parecido a esto, porque no se admite actualmente con las herramientas con las aplicaciones en segundo plano.

![Aplicación de fondo de las herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

Para solucionar este problema, vamos a agregar una aplicación de primer plano a la solución. En el **el Explorador de soluciones** haga doble clic en la carpeta de soluciones y, a continuación, seleccione **Add.New proyecto**.

![Agregar nuevo proyecto](../media/MemoryLeaks/AddNewProject.png)

Elija **Visual C#> Windows Universal > aplicación vacía** como el tipo de proyecto, el nombre del proyecto y haga clic en **Aceptar**.

![Agregar nuevo proyecto](../media/MemoryLeaks/NewForegroundApp.PNG)

Haga doble clic en el nuevo primer plano del proyecto de aplicación **referencias** nodo y seleccione **Agregar referencia...**

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReference.PNG)

En el **Administrador de referencias** cuadro de diálogo Elegir **proyectos** en el panel izquierdo.  En el panel central, agregar una comprobación en la casilla de verificación situada junto a su proyecto de aplicación en segundo plano y haga clic en **Aceptar**.

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReferenceDialog.PNG)

A continuación, haga clic en el proyecto de aplicación de primer plano y haga clic en **establecer como proyecto de inicio**.

![Agregar nuevo proyecto](../media/MemoryLeaks/SetAsStartup.PNG)

Agregue código para crear una instancia del objeto de aplicación de fondo y llamar pasando null como el único parámetro de ejecución.
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

A continuación, en ejecución de la aplicación en segundo plano Compruebe método taskInstance que no es null antes de usarlo.

```C#
public void Run(IBackgroundTaskInstance taskInstance)
{
    if (taskInstance != null)
    {
        deferral = taskInstance.GetDeferral();
    }

    timer = new Timer(Timer_Tick, null, 500, 500);
}
```

1. Establecer un punto de interrupción en la llamada a la tarea. Run(null).
2. Establecer otro punto de interrupción en el temporizador. Cambio en Timer_Tick en StartupTask.cs (Timeout.Infinite, Timeout.Infinite).
3. Presione F5 para comenzar la depuración
4. Cuando se alcanza la prensa de punto de interrupción primera el botón de instantánea para la línea de base para comparar

![Instantánea](../media/MemoryLeaks/Snapshot.PNG)

5. Presione F5
6. Cuando se alcanza el segundo punto de interrupción haga clic en la instantánea botón nuevo para capturar el estado actual.

Ahora las herramientas de diagnóstico deben mostrar un gráfico con el aumento de uso de memoria y la instantánea 2 similar al siguiente:

![Herramientas de diagnóstico con pérdidas](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

Examine la fila 2 de la columna de tamaño del montón. Haga clic en el segundo número con el signo más y la flecha arriba. Debería ver algo parecido a esto:

![Tabla de instantánea](../media/MemoryLeaks/Snapshot2_1.PNG)

Ordenar por la diferencia de tamaño para que sea el número más grande en la parte superior, a continuación, haga clic en la fila superior. Por encima de la segunda tabla de detalles, haga clic en **hace referencia a tipos**.  La segunda tabla debería aparecer ahora **lista\<Byte []\>**  como origen de todo el uso de memoria.

![Tabla de instantánea](../media/MemoryLeaks/Snapshot2_2.PNG)
