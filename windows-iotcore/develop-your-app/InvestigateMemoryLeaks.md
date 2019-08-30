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
# <a name="investigating-memory-leaks"></a><span data-ttu-id="4cc73-104">Investigar pérdidas de memoria</span><span class="sxs-lookup"><span data-stu-id="4cc73-104">Investigating Memory Leaks</span></span>

<span data-ttu-id="4cc73-105">La mejor herramienta para investigar pérdidas de memoria en Windows IoT Core con Visual Studio es la [herramientas de diagnóstico](https://docs.microsoft.com/visualstudio/profiling/memory-usage) integrada</span><span class="sxs-lookup"><span data-stu-id="4cc73-105">The best tool for investigating memory leaks on Windows IoT Core with Visual Studio is the integrated [Diagnostic Tools](https://docs.microsoft.com/visualstudio/profiling/memory-usage)</span></span>

![Herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticTools.PNG)

<span data-ttu-id="4cc73-107">En el caso de las aplicaciones de primer plano, puede [seguir la documentación](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span><span class="sxs-lookup"><span data-stu-id="4cc73-107">For foreground applications you can [follow the documentation](https://docs.microsoft.com/visualstudio/profiling/memory-usage).</span></span>

<span data-ttu-id="4cc73-108">Sin embargo, estas herramientas no funcionan directamente con una **aplicación en segundo plano**de Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="4cc73-108">However, these tools don't work directly with a Windows IoT Core **Background Application**.</span></span> <span data-ttu-id="4cc73-109">Una manera de generar perfiles del código usado en una aplicación en segundo plano es encapsularla en una aplicación en primer plano para su análisis:</span><span class="sxs-lookup"><span data-stu-id="4cc73-109">One way to profile code used in a background application is to wrap it in a foreground app for analysis:</span></span>

1. <span data-ttu-id="4cc73-110">Agregar una **aplicación vacía** a la solución de **aplicación en segundo plano**</span><span class="sxs-lookup"><span data-stu-id="4cc73-110">Add a **Blank App** to the **Background App** solution</span></span>
2. <span data-ttu-id="4cc73-111">Haga clic con el botón derecho en las referencias de **aplicación vacía** y agregue una referencia a la **aplicación en segundo plano** .</span><span class="sxs-lookup"><span data-stu-id="4cc73-111">Right-click the **Blank App** references and add a reference to the **Background App**</span></span>
3. <span data-ttu-id="4cc73-112">Cambie el método de ejecución de la **aplicación en segundo plano** () para comprobar si el parámetro taskInstance es NULL y administrar esos casos de manera diferente.</span><span class="sxs-lookup"><span data-stu-id="4cc73-112">Change the **Background App** Run() method to check if the taskInstance parameter is null and handle those cases differently.</span></span>
4. <span data-ttu-id="4cc73-113">Desde la llamada **BlankApp** BackgroundApp:: Run (NULL)</span><span class="sxs-lookup"><span data-stu-id="4cc73-113">From the **BlankApp** call BackgroundApp::Run(null)</span></span>
5. <span data-ttu-id="4cc73-114">Establezca un punto de interrupción en la llamada a BackgroundApp:: Run</span><span class="sxs-lookup"><span data-stu-id="4cc73-114">Set a breakpoint on the call to BackgroundApp::Run</span></span>
6. <span data-ttu-id="4cc73-115">Cuando se alcance el punto de interrupción, busque el **herramientas de diagnóstico** ventanas ![y](../media/MemoryLeaks/Snapshot.PNG) haga clic en el botón instantánea.</span><span class="sxs-lookup"><span data-stu-id="4cc73-115">When the breakpoint is hit find the **Diagnostic Tools** windows and click the ![Snapshot](../media/MemoryLeaks/Snapshot.PNG) button.</span></span>

8. <span data-ttu-id="4cc73-116">Reproducir el problema</span><span class="sxs-lookup"><span data-stu-id="4cc73-116">Reproduce the problem</span></span>
9. <span data-ttu-id="4cc73-117">Tomar otra instantánea</span><span class="sxs-lookup"><span data-stu-id="4cc73-117">Take another snapshot</span></span>
10. <span data-ttu-id="4cc73-118">Use la ventana de **herramientas de diagnóstico** para diagnosticar la fuga.</span><span class="sxs-lookup"><span data-stu-id="4cc73-118">Use the **Diagnostic Tools** window to diagnose the leak.</span></span>

## <a name="create-a-test-app"></a><span data-ttu-id="4cc73-119">Crear una aplicación de prueba</span><span class="sxs-lookup"><span data-stu-id="4cc73-119">Create a test app</span></span>

<span data-ttu-id="4cc73-120">Comencemos con una aplicación que asigna memoria y no la libera para simular una fuga.</span><span class="sxs-lookup"><span data-stu-id="4cc73-120">Let's start with an application that allocates memory and doesn't free it to simulate a leak.</span></span>
<span data-ttu-id="4cc73-121">Empiece por crear una nueva C# aplicación en segundo plano: [Desarrollo de aplicaciones en segundo plano](./BackgroundApplications.md)</span><span class="sxs-lookup"><span data-stu-id="4cc73-121">Begin by creating a new C# Background application: [Developing Background Applications](./BackgroundApplications.md)</span></span>

<span data-ttu-id="4cc73-122">Reemplace el código de StartupTask.cs por este</span><span class="sxs-lookup"><span data-stu-id="4cc73-122">Replace the code in StartupTask.cs with this</span></span>
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

<span data-ttu-id="4cc73-123">En este momento, si ejecuta la aplicación en segundo plano en el dispositivo IoT, debe usar una gran cantidad de memoria y nunca liberarla.</span><span class="sxs-lookup"><span data-stu-id="4cc73-123">At this point if you run the background application on your IoT device it should use up a lot of memory and never free it.</span></span> <span data-ttu-id="4cc73-124">Si intenta usar las herramientas de diagnóstico en este momento verá algo parecido a esto, ya que actualmente no se admite el uso de las herramientas con aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="4cc73-124">If you try to use the diagnostic tools at this point you will see something that looks like this, because using the tools with background apps is currently unsupported.</span></span>

![Aplicación en segundo plano de Herramientas de diagnóstico](../media/MemoryLeaks/DiagnosticToolsBackgroundApp.png)

<span data-ttu-id="4cc73-126">Para evitar esto, vamos a agregar una aplicación en primer plano a la solución.</span><span class="sxs-lookup"><span data-stu-id="4cc73-126">To work around this we are going to add a foreground app to the solution.</span></span> <span data-ttu-id="4cc73-127">En el **Explorador de soluciones** haga clic con el botón secundario en la carpeta de la solución y seleccione **Agregar. nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="4cc73-127">In the **Solution Explorer** right-click on the solution folder and then select **Add.New Project**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/AddNewProject.png)

<span data-ttu-id="4cc73-129">Elija **Visual C#> Windows universal > aplicación vacía** como el tipo de proyecto, asigne un nombre al proyecto y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4cc73-129">Choose **Visual C#>Windows Universal>Blank App** as the project type, name your project and click **OK**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/NewForegroundApp.PNG)

<span data-ttu-id="4cc73-131">Haga clic con el botón derecho en el nodo **referencias** del nuevo proyecto de aplicación de primer plano y seleccione **Agregar referencia..** .</span><span class="sxs-lookup"><span data-stu-id="4cc73-131">Right-click on the new foreground app project's **References** node and select **Add Reference...**</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReference.PNG)

<span data-ttu-id="4cc73-133">En el cuadro de diálogo **Administrador de referencias** , elija **proyectos** en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="4cc73-133">In the **Reference Manager** dialog choose **Projects** in the left-hand pane.</span></span>  <span data-ttu-id="4cc73-134">En el panel central, agregue una marca de verificación al lado de su proyecto de aplicación en segundo plano y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4cc73-134">In the center pane add a check in the checkbox next to your background application project and click **OK**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/AddReferenceDialog.PNG)

<span data-ttu-id="4cc73-136">Después, haga clic con el botón derecho en el proyecto de aplicación de primer plano y haga clic en **establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="4cc73-136">Next right-click the foreground app project and click **Set as StartUp Project**.</span></span>

![Agregar nuevo proyecto](../media/MemoryLeaks/SetAsStartup.PNG)

<span data-ttu-id="4cc73-138">Agregue código para crear una instancia del objeto de aplicación en segundo plano y llamar a Run pasando NULL como único parámetro.</span><span class="sxs-lookup"><span data-stu-id="4cc73-138">Add code to create an instance of your background application object and call Run passing in null as the only parameter.</span></span>
```C#
public MainPage()
{
    this.InitializeComponent();
    LeakyBackgroundApp.StartupTask task = new LeakyBackgroundApp.StartupTask();
    task.Run(null);
}
```

<span data-ttu-id="4cc73-139">Después, en el método de ejecución de la aplicación en segundo plano, compruebe que taskInstance no es NULL antes de usarlo.</span><span class="sxs-lookup"><span data-stu-id="4cc73-139">Then in your background app's Run method check to make sure taskInstance is not null before using it.</span></span>

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

1. <span data-ttu-id="4cc73-140">Establezca un punto de interrupción en la llamada a la tarea. Ejecutar (NULL).</span><span class="sxs-lookup"><span data-stu-id="4cc73-140">Set a breakpoint on the call to task.Run(null).</span></span>
2. <span data-ttu-id="4cc73-141">Establezca otro punto de interrupción en el temporizador. Cambie (timeout. Infinite, timeout. Infinite) en Timer_Tick en StartupTask.cs.</span><span class="sxs-lookup"><span data-stu-id="4cc73-141">Set another breakpoint on timer.Change(Timeout.Infinite, Timeout.Infinite) in Timer_Tick in StartupTask.cs.</span></span>
3. <span data-ttu-id="4cc73-142">Presione F5 para iniciar la depuración</span><span class="sxs-lookup"><span data-stu-id="4cc73-142">Press F5 to begin debugging</span></span>
4. <span data-ttu-id="4cc73-143">Al alcanzar el primer punto de interrupción, presione el botón instantánea para establecer la línea base con la que comparar</span><span class="sxs-lookup"><span data-stu-id="4cc73-143">When you hit the first breakpoint press the snapshot button to set the baseline to compare against</span></span>

![Instantánea](../media/MemoryLeaks/Snapshot.PNG)

5. <span data-ttu-id="4cc73-145">Presione F5</span><span class="sxs-lookup"><span data-stu-id="4cc73-145">Press F5</span></span>
6. <span data-ttu-id="4cc73-146">Cuando llegue al segundo punto de interrupción, vuelva a presionar el botón de instantánea para capturar el estado actual.</span><span class="sxs-lookup"><span data-stu-id="4cc73-146">When you hit the second breakpoint press the snapshot button again to capture the current state.</span></span>

<span data-ttu-id="4cc73-147">Ahora las herramientas de diagnóstico deben mostrar un gráfico con un uso de memoria creciente y dos instantáneas como esta:</span><span class="sxs-lookup"><span data-stu-id="4cc73-147">Now the diagnostic tools should show a graph with increasing memory use and 2 snapshot like this:</span></span>

![Herramientas de diagnóstico con fugas](../media/MemoryLeaks/DiagnosticToolsWithLeaks.PNG)

<span data-ttu-id="4cc73-149">Fíjese en la fila 2 en la columna tamaño del montón.</span><span class="sxs-lookup"><span data-stu-id="4cc73-149">Look at row 2 in the Heap Size column.</span></span> <span data-ttu-id="4cc73-150">Haga clic en el segundo número con el signo más y la flecha arriba.</span><span class="sxs-lookup"><span data-stu-id="4cc73-150">Click the second number with the plus sign and up arrow.</span></span> <span data-ttu-id="4cc73-151">Verá algo parecido a esto:</span><span class="sxs-lookup"><span data-stu-id="4cc73-151">You should see something like this:</span></span>

![Tabla de instantáneas](../media/MemoryLeaks/Snapshot2_1.PNG)

<span data-ttu-id="4cc73-153">Ordenar por diferencia de tamaño para que el mayor número esté en la parte superior, haga clic en la fila superior.</span><span class="sxs-lookup"><span data-stu-id="4cc73-153">Sort by size diff so that the largest number is at the top, then click the top row.</span></span> <span data-ttu-id="4cc73-154">Encima de la segunda tabla de detalles, haga clic en tipos a los **que se hace referencia**.</span><span class="sxs-lookup"><span data-stu-id="4cc73-154">Above the second detail table click **Referenced Types**.</span></span>  <span data-ttu-id="4cc73-155">La segunda tabla debería mostrar ahora **List\<Byte []\>**  como el origen de todo el uso de memoria.</span><span class="sxs-lookup"><span data-stu-id="4cc73-155">The second table should now show **List\<Byte[]\>** as the source of all the memory usage.</span></span>

![Tabla de instantáneas](../media/MemoryLeaks/Snapshot2_2.PNG)
