---
title: Modo insertado
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Obtenga información acerca de cómo configurar Windows para permitir el modo incrustado, habilitar aplicaciones en segundo plano y otras funcionalidades.
keywords: Windows IOT, modo incrustado, aplicaciones en segundo plano
ms.openlocfilehash: ca8124d97a9161a1539eff92c55cf3630cf0a049
ms.sourcegitcommit: b719e66699372e1339c2316cab45df2a474d09a0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66252175"
---
# <a name="embedded-mode"></a><span data-ttu-id="11a0e-104">Modo insertado</span><span class="sxs-lookup"><span data-stu-id="11a0e-104">Embedded mode</span></span>

<span data-ttu-id="11a0e-105">El modo incrustado se admite en Windows IoT Core y Windows IoT Enterprise.</span><span class="sxs-lookup"><span data-stu-id="11a0e-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="11a0e-106">El modo incrustado habilita:</span><span class="sxs-lookup"><span data-stu-id="11a0e-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="11a0e-107">Aplicaciones en segundo plano (más información)</span><span class="sxs-lookup"><span data-stu-id="11a0e-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="11a0e-108">Uso de la funcionalidad lowLevelDevice</span><span class="sxs-lookup"><span data-stu-id="11a0e-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="11a0e-109">Uso de la funcionalidad systemManagement</span><span class="sxs-lookup"><span data-stu-id="11a0e-109">Use of systemManagement capability</span></span>

<span data-ttu-id="11a0e-110">El modo incrustado siempre está habilitado en la ventana IoT Core.</span><span class="sxs-lookup"><span data-stu-id="11a0e-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="11a0e-111">El modo incrustado debe estar habilitado siguiendo los pasos que se indican a continuación en Windows IoT Enterprise.</span><span class="sxs-lookup"><span data-stu-id="11a0e-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="11a0e-112">Aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="11a0e-112">Background Applications</span></span>

<span data-ttu-id="11a0e-113">Las aplicaciones en segundo plano se crean mediante la plantilla aplicación en segundo plano (IoT) de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11a0e-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="11a0e-114">Obtenga más información sobre la creación de [aplicaciones en segundo plano](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span><span class="sxs-lookup"><span data-stu-id="11a0e-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="11a0e-115">Las aplicaciones en segundo plano se ejecutan sin detenerse y sin límites de recursos.</span><span class="sxs-lookup"><span data-stu-id="11a0e-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="11a0e-116">Además, si la aplicación en segundo plano se detiene por alguna razón y el modo incrustado está habilitado, el sistema reiniciará la aplicación en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="11a0e-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="11a0e-117">Aunque el sistema reiniciará automáticamente las aplicaciones en segundo plano, las características de bloqueo del sistema deben estar habilitadas para impedir que los usuarios se detengan o interfieran con el funcionamiento de las aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="11a0e-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a><span data-ttu-id="11a0e-118">funcionalidad del dispositivo lowLevel y capacidad de lowLevelDevice</span><span class="sxs-lookup"><span data-stu-id="11a0e-118">lowLevel device Capability and lowLevelDevice capability</span></span>

<span data-ttu-id="11a0e-119">La funcionalidad del dispositivo **lowLevel** proporciona acceso a interfaces de hardware de bajo nivel como GPIO, SPI y I2C.</span><span class="sxs-lookup"><span data-stu-id="11a0e-119">The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="11a0e-120">Ejemplo de parpadeo (GPIO)</span><span class="sxs-lookup"><span data-stu-id="11a0e-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="11a0e-121">Ejemplo de acelerómetro</span><span class="sxs-lookup"><span data-stu-id="11a0e-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

<span data-ttu-id="11a0e-122">La funcionalidad **lowLevelDevices** permite a las aplicaciones tener acceso a dispositivos personalizados cuando se cumplen varios requisitos adicionales.</span><span class="sxs-lookup"><span data-stu-id="11a0e-122">The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met.</span></span> <span data-ttu-id="11a0e-123">Esta funcionalidad no se debe confundir con la funcionalidad de dispositivo lowLevel, que permite el acceso a dispositivos GPIO, I2C, SPI y PWM.</span><span class="sxs-lookup"><span data-stu-id="11a0e-123">This capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.</span></span>

<span data-ttu-id="11a0e-124">Consulte [declaraciones de funcionalidades de aplicación](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="11a0e-124">Refer to [App capability declarations](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) for details.</span></span>

## <a name="systemmanagment-capability"></a><span data-ttu-id="11a0e-125">Funcionalidad de systemManagment</span><span class="sxs-lookup"><span data-stu-id="11a0e-125">systemManagment Capability</span></span>

<span data-ttu-id="11a0e-126">Cuando se habilitan las capacidades de systemManagment para la aplicación, este es el conjunto de API que se desbloquea:</span><span class="sxs-lookup"><span data-stu-id="11a0e-126">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="11a0e-127">Windows. System. ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="11a0e-127">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="11a0e-128">Windows. System. TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="11a0e-128">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="11a0e-129">Windows. System. ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="11a0e-129">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="11a0e-130">Windows. Globalization. Language. TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="11a0e-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="11a0e-131">Depurar aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="11a0e-131">Debugging Background Applications</span></span>

<span data-ttu-id="11a0e-132">Si está depurando en un dispositivo que no ejecuta Windows IoT Core y ve alguno de los siguientes mensajes de error, debe asegurarse de que AllowEmbeddedMode está habilitado en el dispositivo y de que el servicio de modo incrustado se está ejecutando:</span><span class="sxs-lookup"><span data-stu-id="11a0e-132">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="11a0e-133">No hay más extremos disponibles desde el asignador de extremos.</span><span class="sxs-lookup"><span data-stu-id="11a0e-133">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="11a0e-134">Este programa está bloqueado por la Directiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="11a0e-134">This program is blocked by group policy.</span></span> <span data-ttu-id="11a0e-135">Para obtener más información, póngase en contacto con el administrador del sistema.</span><span class="sxs-lookup"><span data-stu-id="11a0e-135">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="11a0e-136">Cambiar el modo</span><span class="sxs-lookup"><span data-stu-id="11a0e-136">Changing the mode</span></span>
<span data-ttu-id="11a0e-137">Para habilitar el modo incrustado, debe crear un paquete de aprovisionamiento en el diseñador de imágenes y configuraciones (ICD) que establece AllowEmbeddedMode = 1.</span><span class="sxs-lookup"><span data-stu-id="11a0e-137">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="11a0e-138">Para instalar ICD, debe descargar e instalar Windows ADK para Windows 10.</span><span class="sxs-lookup"><span data-stu-id="11a0e-138">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="11a0e-139">Descargar Windows ADK para Windows 10</span><span class="sxs-lookup"><span data-stu-id="11a0e-139">Download the Windows ADK for Windows 10</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* <span data-ttu-id="11a0e-140">[Obtener información sobre las novedades de Windows ADK para Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="11a0e-140">[Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span></span>

1. <span data-ttu-id="11a0e-141">Al instalar el ADK, seleccione **Imaging and Configuration Designer (ICD)**</span><span class="sxs-lookup"><span data-stu-id="11a0e-141">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="11a0e-142">Una vez completada la instalación, ejecute el diseñador de imágenes y configuraciones de Windows (WICD).</span><span class="sxs-lookup"><span data-stu-id="11a0e-142">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![Icono de WICD](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="11a0e-144">Haz clic en **Aprovisionamiento avanzado**.</span><span class="sxs-lookup"><span data-stu-id="11a0e-144">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="11a0e-145">Asigne al proyecto el nombre **AllowEmbeddedMode** y haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="11a0e-145">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    <span data-ttu-id="11a0e-146">![Step3](../media/EmbeddedMode/Step3.png)</span><span class="sxs-lookup"><span data-stu-id="11a0e-146">![Step3](../media/EmbeddedMode/Step3.png)</span></span>

4. <span data-ttu-id="11a0e-147">Elija **común a todas las ediciones de Windows** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="11a0e-147">Choose **Common to all Windows editions** then **Next**.</span></span>
    <span data-ttu-id="11a0e-148">![Paso4](../media/EmbeddedMode/Step4.png)</span><span class="sxs-lookup"><span data-stu-id="11a0e-148">![Step4](../media/EmbeddedMode/Step4.png)</span></span>

5. <span data-ttu-id="11a0e-149">Haga clic en **Finalizar**</span><span class="sxs-lookup"><span data-stu-id="11a0e-149">Click **Finish**.</span></span>

    ![Paso5](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="11a0e-151">En el cuadro de búsqueda, escriba **EmbeddedMode** y, a continuación, haga clic en **AllowEmbeddedMode**.</span><span class="sxs-lookup"><span data-stu-id="11a0e-151">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![Paso6](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="11a0e-153">En el panel central, establezca el valor de **AllowEmbeddedMode** en **sí** ![STEP7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="11a0e-153">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="11a0e-154">Haga clic en Exportar > paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="11a0e-154">Click Export > Provisioning Package</span></span>

    ![Step8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="11a0e-156">Haga clic en Siguiente.</span><span class="sxs-lookup"><span data-stu-id="11a0e-156">Click Next.</span></span>

    ![Step9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="11a0e-158">Haga clic en Siguiente.</span><span class="sxs-lookup"><span data-stu-id="11a0e-158">Click Next.</span></span>

    ![Step10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="11a0e-160">Haga clic en Siguiente.</span><span class="sxs-lookup"><span data-stu-id="11a0e-160">Click Next.</span></span>

    ![Step11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="11a0e-162">Haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="11a0e-162">Click Build.</span></span>

    ![Step12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="11a0e-164">Para instalar el modo incrustado. PPKG en Windows IoT Enterprise haga doble clic en el. PPKG.</span><span class="sxs-lookup"><span data-stu-id="11a0e-164">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="11a0e-165">Haz clic en **Sí, agrégalo**.</span><span class="sxs-lookup"><span data-stu-id="11a0e-165">Click **Yes, add it**.</span></span>
    <span data-ttu-id="11a0e-166">Haga clic en sí en el cuadro de diálogo LUA, si aparece, y en **sí, agréguelo** en el cuadro de diálogo que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="11a0e-166">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    <span data-ttu-id="11a0e-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span><span class="sxs-lookup"><span data-stu-id="11a0e-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span></span>


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="11a0e-168">Configurar una aplicación en segundo plano para que se ejecute automáticamente</span><span class="sxs-lookup"><span data-stu-id="11a0e-168">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="11a0e-169">Para configurar una aplicación en segundo plano para que se ejecute automáticamente, tendrá que seguir las instrucciones para [crear una tarjeta MinnowBoardMax SD](https://developer.microsoft.com/en-us/windows/iot/getstarted) y copiar `D:\windows\system32\iotstartup.exe` (donde D: es la tarjeta SD).</span><span class="sxs-lookup"><span data-stu-id="11a0e-169">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="11a0e-170">Para obtener una lista de las aplicaciones en segundo plano instaladas, escriba:</span><span class="sxs-lookup"><span data-stu-id="11a0e-170">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="11a0e-171">La salida debe incluir el nombre completo de cada aplicación en segundo plano instalada, que tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="11a0e-171">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="11a0e-172">Para configurar esta aplicación de forma que se ejecute en el tipo de arranque:</span><span class="sxs-lookup"><span data-stu-id="11a0e-172">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="11a0e-173">Si la aplicación en segundo plano se ha agregado correctamente a la lista de inicio, debería ver lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="11a0e-173">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="11a0e-174">Reinicie el dispositivo en modo incrustado:</span><span class="sxs-lookup"><span data-stu-id="11a0e-174">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="11a0e-175">Una vez que se haya reiniciado el dispositivo, la aplicación en segundo plano se iniciará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="11a0e-175">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="11a0e-176">El servicio de modo incrustado que administra las aplicaciones en segundo plano puede tardar unos minutos en iniciarse.</span><span class="sxs-lookup"><span data-stu-id="11a0e-176">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="11a0e-177">El servicio de modo incrustado supervisará las aplicaciones en segundo plano en la lista de inicio y se asegurará de que se reinicien si se detienen.</span><span class="sxs-lookup"><span data-stu-id="11a0e-177">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="11a0e-178">Si una aplicación en segundo plano se detiene varias veces en un breve período de tiempo, ya no se reiniciará.</span><span class="sxs-lookup"><span data-stu-id="11a0e-178">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="11a0e-179">Para quitar la aplicación en segundo plano del tipo de lista de Inicio:</span><span class="sxs-lookup"><span data-stu-id="11a0e-179">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="11a0e-180">Si la aplicación en segundo plano se quita de la lista de inicio, la salida tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="11a0e-180">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
