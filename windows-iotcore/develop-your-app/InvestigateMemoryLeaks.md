---
title: Investigar pérdidas de memoria
author: paulmon
ms.author: paulmon
ms.date: 09/20/2017
ms.topic: article
description: Obtenga información sobre cómo investigar pérdidas de memoria.
keywords: Windows IOT, Visual Studio, fugas, solución de problemas
ms.openlocfilehash: 8385ae621c18c079d0a2ec7bf7b0b4042359eccc
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168619"
---
# <a name="investigating-memory-leaks"></a>Investigar pérdidas de memoria

La mejor herramienta para investigar pérdidas de memoria en Windows IoT Core con Visual Studio es la [herramientas de diagnóstico](https://docs.microsoft.com/visualstudio/profiling/memory-usage) integrada

![Herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticTools.PNG)

En el caso de las aplicaciones de primer plano, puede [seguir la documentación](https://docs.microsoft.com/visualstudio/profiling/memory-usage).

Sin embargo, estas herramientas no funcionan directamente con una **aplicación en segundo plano**de Windows IOT Core. Una manera de generar perfiles del código usado en una aplicación en segundo plano es encapsularla en una aplicación en primer plano para su análisis:

1. Agregar una **aplicación vacía** a la solución de **aplicación en segundo plano**
2. Haga clic con el botón derecho en las referencias de **aplicación vacía** y agregue una referencia a la **aplicación en segundo plano** .
3. Cambie el método de ejecución de la **aplicación en segundo plano** () para comprobar si el parámetro taskInstance es NULL y administrar esos casos de manera diferente.
4. Desde la llamada **BlankApp** BackgroundApp:: Run (NULL)
5. Establezca un punto de interrupción en la llamada a BackgroundApp:: Run
6. Cuando se alcance el punto de interrupción, busque el **herramientas de diagnóstico** ventanas ![y](../media/MemoryLeaks/Snapshot.PNG) haga clic en el botón instantánea.

8. Reproducir el problema
9. Tomar otra instantánea
10. Use la ventana de **herramientas de diagnóstico** para diagnosticar la fuga.

## <a name="create-a-test-app"></a>Crear una aplicación de prueba

Comencemos con una aplicación que asigna memoria y no la libera para simular una fuga.
Empiece por crear una nueva C# aplicación en segundo plano: [Desarrollo de aplicaciones en segundo plano](./BackgroundApplications.md)

Reemplace el código de StartupTask.cs por este
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

En este momento, si ejecuta la aplicación en segundo plano en el dispositivo IoT, debe usar una gran cantidad de memoria y nunca liberarla. Si intenta usar las herramientas de diagnóstico en este momento verá algo parecido a esto, ya que actualmente no se admite el uso de las herramientas con aplicaciones en segundo plano.

![Aplicación en segundo plano de Herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

Para evitar esto, vamos a agregar una aplicación en primer plano a la solución. En el **Explorador de soluciones** haga clic con el botón secundario en la carpeta de la solución y seleccione **Agregar. nuevo proyecto**.

![Agregar nuevo proyecto](../media/MemoryLeaks/AddNewProject.png)

Elija **Visual C#> Windows universal > aplicación vacía** como el tipo de proyecto, asigne un nombre al proyecto y haga clic en **Aceptar**.

![Agregar nuevo proyecto](../media/MemoryLeaks/NewForegroundApp.PNG)

Haga clic con el botón derecho en el nodo **referencias** del nuevo proyecto de aplicación de primer plano y seleccione **Agregar referencia..** .

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReference.PNG)

En el cuadro de diálogo **Administrador de referencias** , elija **proyectos** en el panel izquierdo.  En el panel central, agregue una marca de verificación al lado de su proyecto de aplicación en segundo plano y haga clic en **Aceptar**.

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReferenceDialog.PNG)

Después, haga clic con el botón derecho en el proyecto de aplicación de primer plano y haga clic en **establecer como proyecto de inicio**.

![Agregar nuevo proyecto](../media/MemoryLeaks/SetAsStartup.PNG)

Agregue código para crear una instancia del objeto de aplicación en segundo plano y llamar a Run pasando NULL como único parámetro.
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

Después, en el método de ejecución de la aplicación en segundo plano, compruebe que taskInstance no es NULL antes de usarlo.

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

1. Establezca un punto de interrupción en la llamada a la tarea. Ejecutar (NULL).
2. Establezca otro punto de interrupción en el temporizador. Cambie (timeout. Infinite, timeout. Infinite) en Timer_Tick en StartupTask.cs.
3. Presione F5 para iniciar la depuración
4. Al alcanzar el primer punto de interrupción, presione el botón instantánea para establecer la línea base con la que comparar

![Instantánea](../media/MemoryLeaks/Snapshot.PNG)

5. Presione F5
6. Cuando llegue al segundo punto de interrupción, vuelva a presionar el botón de instantánea para capturar el estado actual.

Ahora las herramientas de diagnóstico deben mostrar un gráfico con un uso de memoria creciente y dos instantáneas como esta:

![Herramientas de diagnóstico con fugas](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

Fíjese en la fila 2 en la columna tamaño del montón. Haga clic en el segundo número con el signo más y la flecha arriba. Verá algo parecido a esto:

![Tabla de instantáneas](../media/MemoryLeaks/Snapshot2_1.PNG)

Ordenar por diferencia de tamaño para que el mayor número esté en la parte superior, haga clic en la fila superior. Encima de la segunda tabla de detalles, haga clic en tipos a los **que se hace referencia**.  La segunda tabla debería mostrar ahora **List\<Byte []\>**  como el origen de todo el uso de memoria.

![Tabla de instantáneas](../media/MemoryLeaks/Snapshot2_2.PNG)
