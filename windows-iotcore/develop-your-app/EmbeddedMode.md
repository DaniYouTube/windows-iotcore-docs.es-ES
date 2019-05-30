---
title: Modo insertado
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Obtenga información sobre cómo configurar Windows para permitir el modo incrustado, habilitación de aplicaciones en segundo plano y otras capacidades.
keywords: Windows iot, modo incrustado, las aplicaciones en segundo plano
ms.openlocfilehash: ca8124d97a9161a1539eff92c55cf3630cf0a049
ms.sourcegitcommit: b719e66699372e1339c2316cab45df2a474d09a0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66252175"
---
# <a name="embedded-mode"></a><span data-ttu-id="2bd99-104">Modo insertado</span><span class="sxs-lookup"><span data-stu-id="2bd99-104">Embedded mode</span></span>

<span data-ttu-id="2bd99-105">Modo incrustado se admite en Windows IoT Core y Windows IoT Enterprise.</span><span class="sxs-lookup"><span data-stu-id="2bd99-105">Embedded Mode is supported on Windows IoT Core and Windows IoT Enterprise.</span></span> <span data-ttu-id="2bd99-106">Habilita el modo incrustado:</span><span class="sxs-lookup"><span data-stu-id="2bd99-106">Embedded Mode enables:</span></span>

* [<span data-ttu-id="2bd99-107">Aplicaciones en segundo plano (más)</span><span class="sxs-lookup"><span data-stu-id="2bd99-107">Background Applications (read more)</span></span>](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* <span data-ttu-id="2bd99-108">Uso de la capacidad de lowLevelDevice</span><span class="sxs-lookup"><span data-stu-id="2bd99-108">Use of the lowLevelDevice capability</span></span>
* <span data-ttu-id="2bd99-109">Uso de capacidad systemManagement</span><span class="sxs-lookup"><span data-stu-id="2bd99-109">Use of systemManagement capability</span></span>

<span data-ttu-id="2bd99-110">Modo incrustado siempre está habilitado en la ventana IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2bd99-110">Embedded mode is always enabled on Window IoT Core.</span></span>
<span data-ttu-id="2bd99-111">Modo incrustado debe habilitarse siguiendo los pasos siguientes en Windows IoT Enterprise.</span><span class="sxs-lookup"><span data-stu-id="2bd99-111">Embedded mode must be enabled by following the steps below on Windows IoT Enterprise.</span></span>

## <a name="background-applications"></a><span data-ttu-id="2bd99-112">Aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="2bd99-112">Background Applications</span></span>

<span data-ttu-id="2bd99-113">Aplicaciones en segundo plano se crean mediante la plantilla de aplicación en segundo plano (IoT) de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2bd99-113">Background Applications are created using the Background Application (IoT) template in Visual Studio.</span></span>
<span data-ttu-id="2bd99-114">Obtenga más información sobre crear [aplicaciones en segundo plano](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span><span class="sxs-lookup"><span data-stu-id="2bd99-114">Read more about creating [Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).</span></span>

<span data-ttu-id="2bd99-115">En segundo plano de las aplicaciones se ejecutan sin necesidad de detener y sin límites de recursos.</span><span class="sxs-lookup"><span data-stu-id="2bd99-115">Background applications run without stopping and without resource limits.</span></span> <span data-ttu-id="2bd99-116">Además, si la aplicación en segundo plano se detiene por alguna razón y embedded está habilitado el modo se reiniciará la aplicación en segundo plano por el sistema.</span><span class="sxs-lookup"><span data-stu-id="2bd99-116">Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.</span></span>

<span data-ttu-id="2bd99-117">Mientras el sistema reiniciará automáticamente aplicaciones en segundo plano, las características de bloqueo del sistema deben habilitarse para impedir que los usuarios deteniendo o interfieran con el funcionamiento de aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="2bd99-117">While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.</span></span>

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a><span data-ttu-id="2bd99-118">dispositivo lowLevel capacidad de capacidad y lowLevelDevice</span><span class="sxs-lookup"><span data-stu-id="2bd99-118">lowLevel device Capability and lowLevelDevice capability</span></span>

<span data-ttu-id="2bd99-119">El **lowLevel** dispositivo capacidad proporciona acceso a las interfaces de hardware de bajo nivel como I2C, SPI y GPIO.</span><span class="sxs-lookup"><span data-stu-id="2bd99-119">The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.</span></span>

* [<span data-ttu-id="2bd99-120">Sample(GPIO) llamativa</span><span class="sxs-lookup"><span data-stu-id="2bd99-120">Blinky Sample(GPIO)</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [<span data-ttu-id="2bd99-121">Ejemplo de acelerómetro</span><span class="sxs-lookup"><span data-stu-id="2bd99-121">Accelerometer Sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

<span data-ttu-id="2bd99-122">El **lowLevelDevices** capacidad permite a las aplicaciones tener acceso a dispositivos personalizados cuando se cumple una serie de requisitos adicionales.</span><span class="sxs-lookup"><span data-stu-id="2bd99-122">The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met.</span></span> <span data-ttu-id="2bd99-123">Esta funcionalidad no debe confundirse con la funcionalidad del dispositivo lowLevel, que permite el acceso a los dispositivos GPIO, I2C, SPI y PWM.</span><span class="sxs-lookup"><span data-stu-id="2bd99-123">This capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.</span></span>

<span data-ttu-id="2bd99-124">Consulte [declaraciones de funcionalidades de aplicación](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="2bd99-124">Refer to [App capability declarations](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) for details.</span></span>

## <a name="systemmanagment-capability"></a><span data-ttu-id="2bd99-125">systemManagment capacidad</span><span class="sxs-lookup"><span data-stu-id="2bd99-125">systemManagment Capability</span></span>

<span data-ttu-id="2bd99-126">Al habilitar las capacidades de systemManagment para la aplicación trata el conjunto de API que desbloquea:</span><span class="sxs-lookup"><span data-stu-id="2bd99-126">When you enable the systemManagment capabilities for your application this is the set of APIs that gets unlocked:</span></span>  

* [<span data-ttu-id="2bd99-127">Windows.System.ProcessLauncher</span><span class="sxs-lookup"><span data-stu-id="2bd99-127">Windows.System.ProcessLauncher</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [<span data-ttu-id="2bd99-128">Windows.System.TimeZoneSettings</span><span class="sxs-lookup"><span data-stu-id="2bd99-128">Windows.System.TimeZoneSettings</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [<span data-ttu-id="2bd99-129">Windows.System.ShutdownManager</span><span class="sxs-lookup"><span data-stu-id="2bd99-129">Windows.System.ShutdownManager</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [<span data-ttu-id="2bd99-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span><span class="sxs-lookup"><span data-stu-id="2bd99-130">Windows.Globalization.Language.TrySetInputMethodLanguageTag</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a><span data-ttu-id="2bd99-131">Depuración de aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="2bd99-131">Debugging Background Applications</span></span>

<span data-ttu-id="2bd99-132">Si está depurando en un dispositivo que no se está ejecutando Windows IoT Core y ve alguno de los siguientes mensajes de error debe asegurarse de AllowEmbeddedMode está habilitado en el dispositivo y que se está ejecutando el servicio en modo incrustado:</span><span class="sxs-lookup"><span data-stu-id="2bd99-132">If you are debugging on a device that is not running Windows IoT Core and you see either of the following error messages you need to ensure AllowEmbeddedMode is enabled on the device and that the Embedded Mode service is running:</span></span>

* <span data-ttu-id="2bd99-133">No hay no hay más extremos disponibles desde el endpoint mapper.</span><span class="sxs-lookup"><span data-stu-id="2bd99-133">There are no more endpoints available from the endpoint mapper.</span></span>
* <span data-ttu-id="2bd99-134">Este programa está bloqueado por la directiva de grupo.</span><span class="sxs-lookup"><span data-stu-id="2bd99-134">This program is blocked by group policy.</span></span> <span data-ttu-id="2bd99-135">Para obtener más información, póngase en contacto con el administrador del sistema.</span><span class="sxs-lookup"><span data-stu-id="2bd99-135">For more information, contact your system administrator.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="2bd99-136">Cambiar el modo</span><span class="sxs-lookup"><span data-stu-id="2bd99-136">Changing the mode</span></span>
<span data-ttu-id="2bd99-137">Para habilitar el modo incrustado que deberá crear un paquete de aprovisionamiento en la creación de imágenes y configuraciones de diseñador (ICD) que establece AllowEmbeddedMode = 1.</span><span class="sxs-lookup"><span data-stu-id="2bd99-137">To enable embedded mode you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1.</span></span>  <span data-ttu-id="2bd99-138">Para instalar ICD deberá descargar e instalar Windows ADK para Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2bd99-138">To install ICD you need to download and install the Windows ADK for Windows 10.</span></span>

* [<span data-ttu-id="2bd99-139">Descargue el Windows ADK para Windows 10</span><span class="sxs-lookup"><span data-stu-id="2bd99-139">Download the Windows ADK for Windows 10</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* <span data-ttu-id="2bd99-140">[Obtenga información sobre cuáles son las novedades en Windows ADK para Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="2bd99-140">[Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)</span></span>

1. <span data-ttu-id="2bd99-141">Al instalar el ADK, seleccione **creación de imágenes y configuraciones de diseñador (ICD)**</span><span class="sxs-lookup"><span data-stu-id="2bd99-141">When installing the ADK select **Imaging and Configuration Designer (ICD)**</span></span>
2. <span data-ttu-id="2bd99-142">Una vez completada la instalación, ejecute Windows Imaging y Diseñador de configuración (WICD).</span><span class="sxs-lookup"><span data-stu-id="2bd99-142">After installation is complete run Windows Imaging and Configuration Designer (WICD).</span></span>

    ![Icono WICD](../media/EmbeddedMode/WICD_Icon.png)

3. <span data-ttu-id="2bd99-144">Haz clic en **Aprovisionamiento avanzado**.</span><span class="sxs-lookup"><span data-stu-id="2bd99-144">Click **Advanced provisioning**.</span></span>  <span data-ttu-id="2bd99-145">Denomine el proyecto **AllowEmbeddedMode** y haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="2bd99-145">Name the project **AllowEmbeddedMode** and click **Next**.</span></span>
    <span data-ttu-id="2bd99-146">![Paso 3](../media/EmbeddedMode/Step3.png)</span><span class="sxs-lookup"><span data-stu-id="2bd99-146">![Step3](../media/EmbeddedMode/Step3.png)</span></span>

4. <span data-ttu-id="2bd99-147">Elija **comunes a todas las ediciones de Windows** , a continuación, **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="2bd99-147">Choose **Common to all Windows editions** then **Next**.</span></span>
    <span data-ttu-id="2bd99-148">![Paso 4](../media/EmbeddedMode/Step4.png)</span><span class="sxs-lookup"><span data-stu-id="2bd99-148">![Step4](../media/EmbeddedMode/Step4.png)</span></span>

5. <span data-ttu-id="2bd99-149">Haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="2bd99-149">Click **Finish**.</span></span>

    ![Paso5](../media/EmbeddedMode/Step5.png)

6. <span data-ttu-id="2bd99-151">En el cuadro Buscar, escriba **EmbeddedMode** y, a continuación, haga clic en **AllowEmbeddedMode**.</span><span class="sxs-lookup"><span data-stu-id="2bd99-151">In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.</span></span>

    ![Paso6](../media/EmbeddedMode/Step6.png)

7. <span data-ttu-id="2bd99-153">En el centro de panel de establece el valor de **AllowEmbeddedMode** a **Sí** ![Step7](../media/EmbeddedMode/Step7.png)</span><span class="sxs-lookup"><span data-stu-id="2bd99-153">In the center pane set the value of **AllowEmbeddedMode** to **Yes** ![Step7](../media/EmbeddedMode/Step7.png)</span></span>

8. <span data-ttu-id="2bd99-154">Haga clic en Exportar > paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="2bd99-154">Click Export > Provisioning Package</span></span>

    ![Step8](../media/EmbeddedMode/Step8.png)

9. <span data-ttu-id="2bd99-156">Haga clic en Siguiente.</span><span class="sxs-lookup"><span data-stu-id="2bd99-156">Click Next.</span></span>

    ![Step9](../media/EmbeddedMode/Step9.png)

10. <span data-ttu-id="2bd99-158">Haga clic en Siguiente.</span><span class="sxs-lookup"><span data-stu-id="2bd99-158">Click Next.</span></span>

    ![Step10](../media/EmbeddedMode/Step10.png)

11. <span data-ttu-id="2bd99-160">Haga clic en Siguiente.</span><span class="sxs-lookup"><span data-stu-id="2bd99-160">Click Next.</span></span>

    ![Step11](../media/EmbeddedMode/Step11.png)

12. <span data-ttu-id="2bd99-162">Haga clic en generar.</span><span class="sxs-lookup"><span data-stu-id="2bd99-162">Click Build.</span></span>

    ![12](../media/EmbeddedMode/Step12.png)

13. <span data-ttu-id="2bd99-164">Para instalar el modo incrustado. PPKG en Windows IoT Enterprise haga doble clic en el. PPKG.</span><span class="sxs-lookup"><span data-stu-id="2bd99-164">To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.</span></span>

14. <span data-ttu-id="2bd99-165">Haz clic en **Sí, agrégalo**.</span><span class="sxs-lookup"><span data-stu-id="2bd99-165">Click **Yes, add it**.</span></span>
    <span data-ttu-id="2bd99-166">Haga clic en Sí en el cuadro de diálogo LUA si aparece y haga clic en **Sí, agregarlo** en el cuadro de diálogo se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="2bd99-166">Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.</span></span>
    <span data-ttu-id="2bd99-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span><span class="sxs-lookup"><span data-stu-id="2bd99-167">![Step14Standard](../media/EmbeddedMode/Step14Standard.png)</span></span>


## <a name="configuring-a-background-application-to-run-automatically"></a><span data-ttu-id="2bd99-168">Configurar una aplicación en segundo plano para ejecutarse automáticamente</span><span class="sxs-lookup"><span data-stu-id="2bd99-168">Configuring a Background Application to Run automatically</span></span>
1. <span data-ttu-id="2bd99-169">Para configurar una aplicación en segundo plano para ejecutar automáticamente, tendrá que seguir las instrucciones para [crear una tarjeta SD de MinnowBoardMax](https://developer.microsoft.com/en-us/windows/iot/getstarted) y copie `D:\windows\system32\iotstartup.exe` (donde D: es la tarjeta SD).</span><span class="sxs-lookup"><span data-stu-id="2bd99-169">To configure a Background Application to automatically run you will need to follow the directions to [create an MinnowBoardMax SD Card](https://developer.microsoft.com/en-us/windows/iot/getstarted) and copy `D:\windows\system32\iotstartup.exe` (where D: is your SD Card).</span></span>

2. <span data-ttu-id="2bd99-170">Para obtener una lista de tipos de aplicaciones en segundo plano instaladas:</span><span class="sxs-lookup"><span data-stu-id="2bd99-170">To get a list of installed Background Applications type:</span></span>

        C:\> iotstartup list BackgroundApplication1

3. <span data-ttu-id="2bd99-171">La salida debe incluir el nombre completo de cada aplicación instalada en segundo plano, que tendrá un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="2bd99-171">The output should include the full name of each installed Background Application, which will look like this:</span></span>

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. <span data-ttu-id="2bd99-172">Para configurar esta aplicación se ejecute en el tipo de arranque:</span><span class="sxs-lookup"><span data-stu-id="2bd99-172">To configure this app to run at boot type:</span></span>

        C:\> iotstartup add headless BackgroundApplication1

6. <span data-ttu-id="2bd99-173">Si la aplicación en segundo plano se ha agregado correctamente a la lista de inicio verá esto:</span><span class="sxs-lookup"><span data-stu-id="2bd99-173">If the Background Application has been successfully added to the startup list you should see this:</span></span>

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. <span data-ttu-id="2bd99-174">Reinicie el dispositivo en modo incrustado:</span><span class="sxs-lookup"><span data-stu-id="2bd99-174">Restart the embedded mode device:</span></span>

8. <span data-ttu-id="2bd99-175">Una vez que se haya reiniciado el dispositivo, se iniciará automáticamente la aplicación en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="2bd99-175">Once the device has restarted, your Background Application will start automatically.</span></span>  <span data-ttu-id="2bd99-176">El servicio de modo incrustado que administra aplicaciones en segundo plano puede tardar unos minutos en iniciarse.</span><span class="sxs-lookup"><span data-stu-id="2bd99-176">The Embedded Mode service which manages Background Applications can take a few minutes to start.</span></span>  <span data-ttu-id="2bd99-177">El servicio de modo incrustado supervisar aplicaciones en segundo plano en la lista de inicio y asegúrese de que obtenga reinicia si detiene.</span><span class="sxs-lookup"><span data-stu-id="2bd99-177">The embedded mode service will monitor Background Applications on the startup list and make sure they get restarted if they stops.</span></span>  <span data-ttu-id="2bd99-178">Si una aplicación en segundo plano se detiene varias veces en un breve período de tiempo ya no se reiniciará.</span><span class="sxs-lookup"><span data-stu-id="2bd99-178">If a Background Application stops several times in a short period of time it will no longer be restarted.</span></span>

9. <span data-ttu-id="2bd99-179">Para quitar la aplicación en segundo plano desde el tipo de lista de inicio:</span><span class="sxs-lookup"><span data-stu-id="2bd99-179">To remove your Background Application from the startup list type:</span></span>

        C:\> iotstartup remove headless BackgroundApplication1

10. <span data-ttu-id="2bd99-180">Si la aplicación en segundo plano se quita de la lista de inicio la salida tendrá este aspecto:</span><span class="sxs-lookup"><span data-stu-id="2bd99-180">If the Background Application is removed from the startup list the output will look like this:</span></span>

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
