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
# <a name="investigating-memory-leaks"></a><span data-ttu-id="e9ea8-104">Investigación de pérdidas de memoria</span><span class="sxs-lookup"><span data-stu-id="e9ea8-104">Investigating Memory Leaks</span></span>

<span data-ttu-id="e9ea8-105">La mejor herramienta para investigar pérdidas de memoria en Windows IoT Core con Visual Studio es el integrado [herramientas de diagnóstico](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span><span class="sxs-lookup"><span data-stu-id="e9ea8-105">The best tool for investigating memory leaks on Windows IoT Core with Visual Studio is the integrated [Diagnostic Tools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span></span>

![Herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticTools.PNG)

<span data-ttu-id="e9ea8-107">Para las aplicaciones de primer plano puede [siga la documentación](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span><span class="sxs-lookup"><span data-stu-id="e9ea8-107">For foreground applications you can [follow the documentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span></span>

<span data-ttu-id="e9ea8-108">Sin embargo, estas herramientas no funcionan directamente con un Windows IoT Core **aplicación en segundo plano**.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-108">However, these tools don't work directly with a Windows IoT Core **Background Application**.</span></span> <span data-ttu-id="e9ea8-109">Es una forma de perfilar el código utilizado en una aplicación en segundo plano incluirlo en una aplicación en primer plano para el análisis:</span><span class="sxs-lookup"><span data-stu-id="e9ea8-109">One way to profile code used in a background application is to wrap it in a foreground app for analysis:</span></span>

1. <span data-ttu-id="e9ea8-110">Agregar un **aplicación vacía** a la **aplicación en segundo plano** solución</span><span class="sxs-lookup"><span data-stu-id="e9ea8-110">Add a **Blank App** to the **Background App** solution</span></span>
2. <span data-ttu-id="e9ea8-111">Haga clic en el **aplicación vacía** hace referencia y agregue una referencia a la **aplicación en segundo plano**</span><span class="sxs-lookup"><span data-stu-id="e9ea8-111">Right-click the **Blank App** references and add a reference to the **Background App**</span></span>
3. <span data-ttu-id="e9ea8-112">Cambiar el **aplicación en segundo plano** método Run() para comprobar si el parámetro taskInstance es null y controlarlos casos de manera diferente.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-112">Change the **Background App** Run() method to check if the taskInstance parameter is null and handle those cases differently.</span></span>
4. <span data-ttu-id="e9ea8-113">Desde el **BlankApp** llamar BackgroundApp::Run(null)</span><span class="sxs-lookup"><span data-stu-id="e9ea8-113">From the **BlankApp** call BackgroundApp::Run(null)</span></span>
5. <span data-ttu-id="e9ea8-114">Establezca un punto de interrupción en la llamada a BackgroundApp::Run</span><span class="sxs-lookup"><span data-stu-id="e9ea8-114">Set a breakpoint on the call to BackgroundApp::Run</span></span>
6. <span data-ttu-id="e9ea8-115">Cuando se alcanza el punto de interrupción, busque el **herramientas de diagnóstico** windows y haga clic en el ![instantánea](../media/MemoryLeaks/Snapshot.PNG) botón.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-115">When the breakpoint is hit find the **Diagnostic Tools** windows and click the ![Snapshot](../media/MemoryLeaks/Snapshot.PNG) button.</span></span>

8. <span data-ttu-id="e9ea8-116">Reproducir el problema</span><span class="sxs-lookup"><span data-stu-id="e9ea8-116">Reproduce the problem</span></span>
9. <span data-ttu-id="e9ea8-117">Toma otra instantánea</span><span class="sxs-lookup"><span data-stu-id="e9ea8-117">Take another snapshot</span></span>
10. <span data-ttu-id="e9ea8-118">Use la **herramientas de diagnóstico** ventana para diagnosticar la pérdida.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-118">Use the **Diagnostic Tools** window to diagnose the leak.</span></span>

## <a name="create-a-test-app"></a><span data-ttu-id="e9ea8-119">Crear una aplicación de prueba</span><span class="sxs-lookup"><span data-stu-id="e9ea8-119">Create a test app</span></span>

<span data-ttu-id="e9ea8-120">Comencemos con una aplicación que asigna memoria y no lo libere para simular una pérdida.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-120">Let's start with an application that allocates memory and doesn't free it to simulate a leak.</span></span>
<span data-ttu-id="e9ea8-121">Empiece por crear un nuevo C# en segundo plano de la aplicación: [Desarrollo de aplicaciones en segundo plano](./BackgroundApplications.md)</span><span class="sxs-lookup"><span data-stu-id="e9ea8-121">Begin by creating a new C# Background application: [Developing Background Applications](./BackgroundApplications.md)</span></span>

<span data-ttu-id="e9ea8-122">Reemplace el código de StartupTask.cs con este</span><span class="sxs-lookup"><span data-stu-id="e9ea8-122">Replace the code in StartupTask.cs with this</span></span>
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

<span data-ttu-id="e9ea8-123">En este punto si ejecuta la aplicación en segundo plano en el dispositivo de IoT debe consumir una gran cantidad de memoria y nunca lo libere.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-123">At this point if you run the background application on your IoT device it should use up a lot of memory and never free it.</span></span> <span data-ttu-id="e9ea8-124">Si intenta usar las herramientas de diagnóstico en este momento verá algo parecido a esto, porque no se admite actualmente con las herramientas con las aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-124">If you try to use the diagnostic tools at this point you will see something that looks like this, because using the tools with background apps is currently unsupported.</span></span>

![Aplicación de fondo de las herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

<span data-ttu-id="e9ea8-126">Para solucionar este problema, vamos a agregar una aplicación de primer plano a la solución.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-126">To work around this we are going to add a foreground app to the solution.</span></span> <span data-ttu-id="e9ea8-127">En el **el Explorador de soluciones** haga doble clic en la carpeta de soluciones y, a continuación, seleccione **Add.New proyecto**.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-127">In the **Solution Explorer** right-click on the solution folder and then select **Add.New Project**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/AddNewProject.png)

<span data-ttu-id="e9ea8-129">Elija **Visual C#> Windows Universal > aplicación vacía** como el tipo de proyecto, el nombre del proyecto y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-129">Choose **Visual C#>Windows Universal>Blank App** as the project type, name your project and click **OK**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/NewForegroundApp.PNG)

<span data-ttu-id="e9ea8-131">Haga doble clic en el nuevo primer plano del proyecto de aplicación **referencias** nodo y seleccione **Agregar referencia...**</span><span class="sxs-lookup"><span data-stu-id="e9ea8-131">Right-click on the new foreground app project's **References** node and select **Add Reference...**</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReference.PNG)

<span data-ttu-id="e9ea8-133">En el **Administrador de referencias** cuadro de diálogo Elegir **proyectos** en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-133">In the **Reference Manager** dialog choose **Projects** in the left-hand pane.</span></span>  <span data-ttu-id="e9ea8-134">En el panel central, agregar una comprobación en la casilla de verificación situada junto a su proyecto de aplicación en segundo plano y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-134">In the center pane add a check in the checkbox next to your background application project and click **OK**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReferenceDialog.PNG)

<span data-ttu-id="e9ea8-136">A continuación, haga clic en el proyecto de aplicación de primer plano y haga clic en **establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-136">Next right-click the foreground app project and click **Set as StartUp Project**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/SetAsStartup.PNG)

<span data-ttu-id="e9ea8-138">Agregue código para crear una instancia del objeto de aplicación de fondo y llamar pasando null como el único parámetro de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-138">Add code to create an instance of your background application object and call Run passing in null as the only parameter.</span></span>
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

<span data-ttu-id="e9ea8-139">A continuación, en ejecución de la aplicación en segundo plano Compruebe método taskInstance que no es null antes de usarlo.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-139">Then in your background app's Run method check to make sure taskInstance is not null before using it.</span></span>

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

1. <span data-ttu-id="e9ea8-140">Establecer un punto de interrupción en la llamada a la tarea. Run(null).</span><span class="sxs-lookup"><span data-stu-id="e9ea8-140">Set a breakpoint on the call to task.Run(null).</span></span>
2. <span data-ttu-id="e9ea8-141">Establecer otro punto de interrupción en el temporizador. Cambio en Timer_Tick en StartupTask.cs (Timeout.Infinite, Timeout.Infinite).</span><span class="sxs-lookup"><span data-stu-id="e9ea8-141">Set another breakpoint on timer.Change(Timeout.Infinite, Timeout.Infinite) in Timer_Tick in StartupTask.cs.</span></span>
3. <span data-ttu-id="e9ea8-142">Presione F5 para comenzar la depuración</span><span class="sxs-lookup"><span data-stu-id="e9ea8-142">Press F5 to begin debugging</span></span>
4. <span data-ttu-id="e9ea8-143">Cuando se alcanza la prensa de punto de interrupción primera el botón de instantánea para la línea de base para comparar</span><span class="sxs-lookup"><span data-stu-id="e9ea8-143">When you hit the first breakpoint press the snapshot button to set the baseline to compare against</span></span>

![Instantánea](../media/MemoryLeaks/Snapshot.PNG)

5. <span data-ttu-id="e9ea8-145">Presione F5</span><span class="sxs-lookup"><span data-stu-id="e9ea8-145">Press F5</span></span>
6. <span data-ttu-id="e9ea8-146">Cuando se alcanza el segundo punto de interrupción haga clic en la instantánea botón nuevo para capturar el estado actual.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-146">When you hit the second breakpoint press the snapshot button again to capture the current state.</span></span>

<span data-ttu-id="e9ea8-147">Ahora las herramientas de diagnóstico deben mostrar un gráfico con el aumento de uso de memoria y la instantánea 2 similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="e9ea8-147">Now the diagnostic tools should show a graph with increasing memory use and 2 snapshot like this:</span></span>

![Herramientas de diagnóstico con pérdidas](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

<span data-ttu-id="e9ea8-149">Examine la fila 2 de la columna de tamaño del montón.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-149">Look at row 2 in the Heap Size column.</span></span> <span data-ttu-id="e9ea8-150">Haga clic en el segundo número con el signo más y la flecha arriba.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-150">Click the second number with the plus sign and up arrow.</span></span> <span data-ttu-id="e9ea8-151">Debería ver algo parecido a esto:</span><span class="sxs-lookup"><span data-stu-id="e9ea8-151">You should see something like this:</span></span>

![Tabla de instantánea](../media/MemoryLeaks/Snapshot2_1.PNG)

<span data-ttu-id="e9ea8-153">Ordenar por la diferencia de tamaño para que sea el número más grande en la parte superior, a continuación, haga clic en la fila superior.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-153">Sort by size diff so that the largest number is at the top, then click the top row.</span></span> <span data-ttu-id="e9ea8-154">Por encima de la segunda tabla de detalles, haga clic en **hace referencia a tipos**.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-154">Above the second detail table click **Referenced Types**.</span></span>  <span data-ttu-id="e9ea8-155">La segunda tabla debería aparecer ahora **lista\<Byte []\>**  como origen de todo el uso de memoria.</span><span class="sxs-lookup"><span data-stu-id="e9ea8-155">The second table should now show **List\<Byte[]\>** as the source of all the memory usage.</span></span>

![Tabla de instantánea](../media/MemoryLeaks/Snapshot2_2.PNG)
