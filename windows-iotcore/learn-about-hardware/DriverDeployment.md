---
title: Implementación de controladores
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Obtenga información sobre cómo compilar e implementar un controlador con Visual Studio.
keywords: Windows 10 IoT Core, implementación de controladores
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169860"
---
# <a name="driver-deployment"></a><span data-ttu-id="5dc8e-104">Implementación de controladores</span><span class="sxs-lookup"><span data-stu-id="5dc8e-104">Driver deployment</span></span>

<span data-ttu-id="5dc8e-105">Implemente un controlador en Windows 10 IoT Core con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-105">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span> 

<span data-ttu-id="5dc8e-106">Configure el proyecto de controlador de Visual Studio para que pueda compilar e implementar un controlador para una plataforma específica durante la fase de desarrollo del controlador.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-106">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span> 

<span data-ttu-id="5dc8e-107">Para este ejercicio, puede usar el [controlador de ejemplo gpiokmdfdemo](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-107">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="5dc8e-108">Si desea agregar un controlador a una imagen, consulte las instrucciones de nuestra guía de fabricación de [IOT](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-108">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1--setup"></a><span data-ttu-id="5dc8e-109">Paso 1: Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="5dc8e-109">Step 1 : Setup</span></span> 
___

### <a name="on-the-device"></a><span data-ttu-id="5dc8e-110">En el dispositivo</span><span class="sxs-lookup"><span data-stu-id="5dc8e-110">On the device</span></span>

* <span data-ttu-id="5dc8e-111">Asegúrese de que el dispositivo tiene instalada una imagen de IoTCore siguiendo las [instrucciones de introducción](https://go.microsoft.com/fwlink/?linkid=860461).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-111">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="5dc8e-112">Conéctese a su dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-112">Connect to your device via [Powershell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="5dc8e-113">En el equipo</span><span class="sxs-lookup"><span data-stu-id="5dc8e-113">On the PC</span></span>

* <span data-ttu-id="5dc8e-114">Asegúrese de que ha instalado Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-114">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="5dc8e-115">Instale el [Kit de controladores de Windows](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-115">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="5dc8e-116">Tendrá que instalar el SDK y WDK.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-116">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="5dc8e-117">Instale los certificados para que el controlador se firme correctamente y se pueda ejecutar en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-117">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="5dc8e-118">Desde un símbolo del sistema con privilegios elevados, ejecute los comandos que se enumeran a continuación:</span><span class="sxs-lookup"><span data-stu-id="5dc8e-118">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* <span data-ttu-id="5dc8e-119">Aplicar corrección para habilitar la implementación de F5 desde VS.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-119">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="5dc8e-120">En el símbolo del sistema con privilegios elevados, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="5dc8e-120">In the elevated command prompt, execute the following commands:</span></span>

    1.  <span data-ttu-id="5dc8e-121">`cd %TEMP%`(cambiará el directorio `c:\users\<usernsme>\Appdata\Local\Temp`a)</span><span class="sxs-lookup"><span data-stu-id="5dc8e-121">`cd %TEMP%` ( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="5dc8e-122">`md “WdkTempFiles”`Cree manualmente un directorio "WdkTempFiles". esta es una solución alternativa para un error en las herramientas y debe realizarse una *sola vez* en el equipo.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-122">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2--provision-device-with-visual-studio"></a><span data-ttu-id="5dc8e-123">Paso 2: Aprovisionamiento de dispositivos con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5dc8e-123">Step 2 : Provision device with Visual Studio</span></span> 
___
* <span data-ttu-id="5dc8e-124">Abra Visual Studio y seleccione **Driver > Test > configurar dispositivos > agregar nuevo dispositivo** .</span><span class="sxs-lookup"><span data-stu-id="5dc8e-124">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="5dc8e-125">Si no se muestra la opción de menú controlador, compruebe si el SDK está instalado.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-125">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="5dc8e-126">En el cuadro de diálogo **configuración del dispositivo** ,</span><span class="sxs-lookup"><span data-stu-id="5dc8e-126">In the **Device Configuration** dialog,</span></span> 
    * <span data-ttu-id="5dc8e-127">Escriba un nombre para mostrar descriptivo para el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="5dc8e-127">Enter a user friendly Display Name for your target device</span></span>
    * <span data-ttu-id="5dc8e-128">Seleccionar tipo de dispositivo = móvil</span><span class="sxs-lookup"><span data-stu-id="5dc8e-128">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="5dc8e-129">En la lista que se muestra, ordene por dirección IP y busque la dirección del dispositivo IoT y seleccione.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-129">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="5dc8e-130">Si hay dos entradas, seleccione la que tenga el GUID distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-130">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="5dc8e-131">Asegúrese de que la fila esté seleccionada; debe resaltar azul</span><span class="sxs-lookup"><span data-stu-id="5dc8e-131">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="5dc8e-132">En la parte inferior del cuadro de diálogo hay dos botones de radio.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-132">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="5dc8e-133">Seleccione la que dice **aprovisionar dispositivo y elija Configuración**del depurador.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-133">Select the one which says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="5dc8e-134">Seleccionar **siguiente**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-134">Select **Next**</span></span>

* <span data-ttu-id="5dc8e-135">En la **configuración de configurar**el depurador, establezca la configuración adecuada.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-135">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="5dc8e-136">Tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5dc8e-136">Note the following:</span></span>
   * <span data-ttu-id="5dc8e-137">El MinnowBoardMax puede usar la red para la depuración.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-137">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="5dc8e-138">Usar **red** de tipo de conexión</span><span class="sxs-lookup"><span data-stu-id="5dc8e-138">Use connection type **Network**</span></span>
       * <span data-ttu-id="5dc8e-139">Seleccionar un puerto: se puede usar el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-139">Select some port – default can be used</span></span>
       * <span data-ttu-id="5dc8e-140">Seleccionar alguna clave: se puede usar el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-140">Select some key – default can be used</span></span>
       * <span data-ttu-id="5dc8e-141">Seleccione la dirección IP del host de la máquina que ejecuta Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-141">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="5dc8e-142">No use la dirección de Autonet (169.xxx).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-142">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="5dc8e-143">Seleccionar **siguiente**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-143">Select **Next**</span></span>
       
  ![Configurar las opciones de depuración](../media/DriverDeployment/confdbgsettings.png)
       
    * <span data-ttu-id="5dc8e-145">Raspberry PI usa serial para la depuración de kernel.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-145">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="5dc8e-146">Conectar el cable de depuración serie adecuado a PI y el equipo host</span><span class="sxs-lookup"><span data-stu-id="5dc8e-146">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="5dc8e-147">Seleccionar **serie** para el tipo de conexión</span><span class="sxs-lookup"><span data-stu-id="5dc8e-147">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="5dc8e-148">Rellene el resto de los parámetros según corresponda para el Raspberry PI.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-148">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="5dc8e-149">Seleccionar **siguiente**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-149">Select **Next**</span></span>

* <span data-ttu-id="5dc8e-150">El WDK, a través de VS, aprovisionará ahora el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-150">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="5dc8e-151">TAEF y WDTF se instalarán en el dispositivo y el dispositivo se configurará para la depuración del kernel según la configuración proporcionada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-151">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="5dc8e-152">Cuando haya finalizado, es posible que el dispositivo se reinicie.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-152">When complete, the device may reboot.</span></span>  <span data-ttu-id="5dc8e-153">La pantalla de progreso de la **configuración del dispositivo** proporcionará el estado y se mostrará cuando el dispositivo de IOT haya completado la instalación.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-153">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="5dc8e-154">Presione **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-154">Press **Finish**.</span></span>

![Configurar el progreso](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="5dc8e-156">El dispositivo ya está aprovisionado y el estado de la **configuración de prueba del dispositivo** muestra **configurado para las pruebas de controladores**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-156">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a><span data-ttu-id="5dc8e-158">Paso 3: Configurar proyecto de controlador de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5dc8e-158">Step 3 : Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="5dc8e-159">Inicie Visual Studio en modo de administrador y abra el proyecto de controlador de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-159">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="5dc8e-160">Asegúrese de que la versión de la plataforma de destino coincide con el SDK instalado en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-160">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="5dc8e-161">Seleccione propiedades del proyecto en la ventana Explorador de soluciones.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-161">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="5dc8e-162">En propiedades de configuración general, asegúrese de que la versión de la plataforma de destino coincide con el SDK instalado en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-162">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="5dc8e-163">Puede comprobar la versión del SDK en el panel de **Control > programas > programas y características**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-163">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="5dc8e-164">En **proyecto > agregar nuevo elemento > Visual C++ > controlador de Windows**, seleccione **manifiesto del paquete** y, a continuación, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-164">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 <span data-ttu-id="5dc8e-166">`Package.pkg.xml`el archivo se agregará al proyecto.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-166">`Package.pkg.xml` file will be added to the project.</span></span> <span data-ttu-id="5dc8e-167">En este archivo, especifique las etiquetas de propietario, plataforma, componente y subcomponente.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-167">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span> 
 
![Package-pkg-XML](../media/DriverDeployment/Package-pkg-xml.png)
 
4. <span data-ttu-id="5dc8e-169">Establezca el número de versión del paquete en **las propiedades del proyecto > PackageGen > versión**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-169">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="5dc8e-170">Tenga en cuenta que cada vez que necesite realizar una instalación o reinstalación del controlador, se debe incrementar este número de versión.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-170">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="5dc8e-172">En **propiedades del proyecto > firma de controladores > certificado de prueba**, seleccione certificado de prueba (certificado de prueba de OEM de teléfono).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-172">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="5dc8e-174">Vaya a **instalar controlador** y seleccione **implementación** .</span><span class="sxs-lookup"><span data-stu-id="5dc8e-174">Go to **Driver Install** and select **Deployment**</span></span>

![InstallOptions](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="5dc8e-176">En el menú desplegable **nombre del dispositivo de destino** , seleccione el destino creado anteriormente en el proceso de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-176">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="5dc8e-177">Tenga en cuenta las dos opciones de **instalación/reinstalación** y reinstalación **rápida**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-177">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="5dc8e-178">Elija una opción y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-178">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="5dc8e-179">**Instalar/reinstalar** se usa para la instalación inicial de un controlador en el destino.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-179">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="5dc8e-180">Esto instala el paquete de controladores mediante la pila de Windows Update y puede tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-180">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="5dc8e-181">Debe usarse cada vez que se cambie el archivo INF.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-181">This must be used every time the INF file is changed.</span></span> 
    
> [!TIP]
> <span data-ttu-id="5dc8e-182">Cada vez que se usa esta opción para instalar un controlador después de la instalación inicial, se debe incrementar el número de versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-182">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="5dc8e-183">La **reinstalación rápida** se puede usar una vez que se ha instalado un controlador y no hay cambios posteriores en el archivo INF de los controladores que afecten al registro.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-183">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file which affect the registry.</span></span>  <span data-ttu-id="5dc8e-184">Este método omite el proceso de instalación, apaga todos los devnodes asociados al controlador, copia el controlador en y reinicia devnode.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-184">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="5dc8e-185">Esto tarda unos pocos (< 20) segundos.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-185">This takes a few (<20) seconds.</span></span>

    
> [!WARNING]
> <span data-ttu-id="5dc8e-186">No se garantiza que este método se realice correctamente; si por alguna razón no se puede apagar un devnode para liberar el controlador, se producirá un error en la operación.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-186">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="5dc8e-187">Esto puede deberse a un hardware defectuoso o a una implementación defectuosa del controlador.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-187">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="5dc8e-188">En este caso, se debe utilizar la opción instalar/reinstalar.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-188">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="5dc8e-189">El proyecto de Visual Studio ya está listo para compilar e implementar un controlador en el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-189">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="5dc8e-190">Si usa el controlador gpiokmdfdemo de ejemplo, debe generar la tabla ACPI y copiarla en el dispositivo de destino. a continuación, siga los pasos de [creación del controlador en Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span><span class="sxs-lookup"><span data-stu-id="5dc8e-190">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4--build-and-deploy-driver"></a><span data-ttu-id="5dc8e-191">Paso 4: Compilar e implementar controlador</span><span class="sxs-lookup"><span data-stu-id="5dc8e-191">Step 4 : Build and deploy driver</span></span>
___
<span data-ttu-id="5dc8e-192">Esto se puede hacer de dos maneras, mediante la tecla **F5** y el uso de la opción **implementar** .</span><span class="sxs-lookup"><span data-stu-id="5dc8e-192">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="5dc8e-193">En ambos sentidos, el controlador se compilará e implementará (es decir, lo instala en el dispositivo) y F5 conectará el depurador de kernel de Visual Studio al controlador instalado y cargado.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-193">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span> 

<span data-ttu-id="5dc8e-194">Algunos usuarios prefieren usar la funcionalidad de **implementación** y asociar un depurador de kernel diferente, como WinDbg o KD.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-194">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="5dc8e-195">Esto puede proporcionar más flexibilidad que usar el depurador de VS.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-195">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="5dc8e-196">Implementar</span><span class="sxs-lookup"><span data-stu-id="5dc8e-196">Deploy</span></span>
1.  <span data-ttu-id="5dc8e-197">Haga clic con el botón derecho en el proyecto en el explorador de soluciones.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-197">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="5dc8e-198">Seleccionar **implementar**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-198">Select **Deploy**</span></span>

![Implementar](../media/DriverDeployment/deploy.png) 

3.  <span data-ttu-id="5dc8e-200">El proceso de implementación debe continuar.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-200">The deployment process should proceed.</span></span>  <span data-ttu-id="5dc8e-201">El dispositivo de IoT se reiniciará después de la implementación y debería mostrar la pantalla "engranajes" mientras se realiza la instalación.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-201">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="5dc8e-202">La salida de la compilación está en la ventana de **salida** el estado de implementación también está en la ventana de salida cuando se completa la instalación, el dispositivo se reiniciará de nuevo y la pantalla de salida de vs indicará si se ha realizado correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-202">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="5dc8e-203">F5</span><span class="sxs-lookup"><span data-stu-id="5dc8e-203">F5</span></span>

1.  <span data-ttu-id="5dc8e-204">En la ventana compilar, asegúrese de que las configuraciones son correctas: el arco de compilación actual es el mismo que el del dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-204">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="5dc8e-205">Aquí es donde es útil tener el Arch en el nombre de destino.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-205">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="5dc8e-206">El destino se mostrará en el cuadro de vista de la barra de menús en VS en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-206">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="5dc8e-207">Presione **F5**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-207">Press **F5**.</span></span>  <span data-ttu-id="5dc8e-208">El destino se compilará, implementará y adjuntará al depurador de kernel de VS.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-208">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="5dc8e-209">Después del reinicio, asegúrese de que PowerShell sigue conectado a él; de lo contrario, vuelva a conectarse al dispositivo de destino mediante `enter-pssession` el comando de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-209">After the reboot, make sure PowerShell is still connected to it, otherwise, re-connect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="5dc8e-210">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="5dc8e-210">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="5dc8e-211">Errores de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="5dc8e-211">Provisioning Errors</span></span>
<span data-ttu-id="5dc8e-212">Una condición de carrera durante la interacción con MinnowBoardMax puede producir un error detectado durante el aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-212">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="5dc8e-213">De hecho, lo más probable es que el aprovisionamiento se haya realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-213">In fact, the provisioning most likely succeeded.</span></span>

<span data-ttu-id="5dc8e-214">**Lista de errores:**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-214">**List of Errors:**</span></span>
 
* <span data-ttu-id="5dc8e-215">ERROR: La tarea "registrando WDTF" no se pudo completar correctamente.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-215">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="5dc8e-216">ERROR: La tarea "Configurando la configuración del depurador de kernel (posible reinicio)" no se pudo completar correctamente</span><span class="sxs-lookup"><span data-stu-id="5dc8e-216">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="5dc8e-217">**Solución:** Es posible que no se puedan pasar por alto estos errores.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-217">**Workaround:** These error can almost certainly be ignored.</span></span>

<span data-ttu-id="5dc8e-218">**Indicaciones**</span><span class="sxs-lookup"><span data-stu-id="5dc8e-218">**Details:**</span></span>

<span data-ttu-id="5dc8e-219">El siguiente error se mostrará en el cuadro de diálogo de progreso de la configuración del **dispositivo** :</span><span class="sxs-lookup"><span data-stu-id="5dc8e-219">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully 
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

<span data-ttu-id="5dc8e-220">Llegados a este punto, puede hacer clic en el **final** con seguridad y, a continuación, en **aplicar** y **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-220">At this point you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="5dc8e-221">Se trata de un error benigno formado por una condición de carrera que hace que un registro de resultados tenga un formato incorrecto.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-221">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="5dc8e-222">Para comprobarlo, examine el archivo de registro en la siguiente área:</span><span class="sxs-lookup"><span data-stu-id="5dc8e-222">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="5dc8e-223">Abra una conexión FTP con la dirección IP del dispositivo (como se muestra en la pantalla del dispositivo) `Data/test/bin/DriverTest/Run` en el directorio.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-223">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="5dc8e-224">ej.`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`</span><span class="sxs-lookup"><span data-stu-id="5dc8e-224">e.g. `ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`</span></span>

2. <span data-ttu-id="5dc8e-225">Copie el `Configuring_computer_settings_(possible_reboot)_identifier.wtl` archivo en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-225">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="5dc8e-226">Tenga en cuenta que el nombre del archivo de registro coincide con el nombre de la tarea con error.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-226">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="5dc8e-227">Abra el archivo en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-227">Open the file in notepad</span></span>
4. <span data-ttu-id="5dc8e-228">Desplácese hasta la parte inferior del registro.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-228">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="5dc8e-229">El siguiente texto estará presente, lo que indica que el aprovisionamiento se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="5dc8e-229">The following text will be present, indicating that the provisioning is successful.</span></span>

```
<PFRollup 
    Total="1" 
    Passed="1" 
    Failed="0" 
    Blocked="0" 
    Warned="0" 
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```

