---
title: Implementación de controladores
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Obtenga información sobre cómo compilar e implementar un controlador mediante Visual Studio.
keywords: Windows 10 IoT Core, implementación de controladores
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514976"
---
# <a name="driver-deployment"></a><span data-ttu-id="bba59-104">Implementación de controladores</span><span class="sxs-lookup"><span data-stu-id="bba59-104">Driver deployment</span></span>

<span data-ttu-id="bba59-105">Implementar un controlador en Windows 10 IoT Core con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bba59-105">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span> 

<span data-ttu-id="bba59-106">Configurar el proyecto de controlador de Visual Studio para que puede compilar e implementar un controlador para una plataforma específica durante la fase de desarrollo de controladores.</span><span class="sxs-lookup"><span data-stu-id="bba59-106">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span> 

<span data-ttu-id="bba59-107">Para este ejercicio puede usar el [controlador de ejemplo gpiokmdfdemo](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span><span class="sxs-lookup"><span data-stu-id="bba59-107">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="bba59-108">Si desea para agregar un controlador a una imagen, visite las instrucciones de nuestro [IoT fabricación guía](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span><span class="sxs-lookup"><span data-stu-id="bba59-108">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1--setup"></a><span data-ttu-id="bba59-109">Paso 1: Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="bba59-109">Step 1 : Setup</span></span> 
___

### <a name="on-the-device"></a><span data-ttu-id="bba59-110">En el dispositivo</span><span class="sxs-lookup"><span data-stu-id="bba59-110">On the device</span></span>

* <span data-ttu-id="bba59-111">Asegúrese de que el dispositivo tiene una imagen IoTCore instalada siguiendo el [instrucciones de introducción](https://go.microsoft.com/fwlink/?linkid=860461).</span><span class="sxs-lookup"><span data-stu-id="bba59-111">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="bba59-112">Conectarse al dispositivo a través de [Powershell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="bba59-112">Connect to your device via [Powershell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="bba59-113">En el equipo</span><span class="sxs-lookup"><span data-stu-id="bba59-113">On the PC</span></span>

* <span data-ttu-id="bba59-114">Asegúrese de que ha instalado Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bba59-114">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="bba59-115">Instalar el [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span><span class="sxs-lookup"><span data-stu-id="bba59-115">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="bba59-116">Deberá instalar el SDK y WDK.</span><span class="sxs-lookup"><span data-stu-id="bba59-116">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="bba59-117">Instalar los certificados para que el controlador está firmado correctamente y puede ejecutarse en su dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bba59-117">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="bba59-118">Desde un símbolo del sistema con privilegios elevados, ejecute los comandos enumerados a continuación:</span><span class="sxs-lookup"><span data-stu-id="bba59-118">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* <span data-ttu-id="bba59-119">Aplicar corrección para habilitar la implementación de F5 desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bba59-119">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="bba59-120">En el símbolo del sistema con privilegios elevados, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="bba59-120">In the elevated command prompt, execute the following commands:</span></span>

    1.  `cd %TEMP%` <span data-ttu-id="bba59-121">(cambie el directorio a `c:\users\<usernsme>\Appdata\Local\Temp`)</span><span class="sxs-lookup"><span data-stu-id="bba59-121">( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="bba59-122">`md “WdkTempFiles”` Crear manualmente un directorio "WdkTempFiles" es una solución a un error en las herramientas y requiere hacerse *sólo una vez* en el equipo.</span><span class="sxs-lookup"><span data-stu-id="bba59-122">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2--provision-device-with-visual-studio"></a><span data-ttu-id="bba59-123">Paso 2: Dispositivo de provisión con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bba59-123">Step 2 : Provision device with Visual Studio</span></span> 
___
* <span data-ttu-id="bba59-124">Abra Visual Studio y seleccione **controlador > prueba > configuración de dispositivos > Agregar nuevo dispositivo**</span><span class="sxs-lookup"><span data-stu-id="bba59-124">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="bba59-125">Si no se muestra la opción de menú del controlador, compruebe si está instalado el SDK.</span><span class="sxs-lookup"><span data-stu-id="bba59-125">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="bba59-126">En el **configuración del dispositivo** cuadro de diálogo,</span><span class="sxs-lookup"><span data-stu-id="bba59-126">In the **Device Configuration** dialog,</span></span> 
    * <span data-ttu-id="bba59-127">Escriba un usuario de nombre para mostrar descriptivo para el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="bba59-127">Enter a user friendly Display Name for your target device</span></span>
    * <span data-ttu-id="bba59-128">Seleccione el tipo de dispositivo = móvil</span><span class="sxs-lookup"><span data-stu-id="bba59-128">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="bba59-129">En la lista mostrada, ordenar por dirección IP y busque la dirección para el dispositivo de IoT y seleccione.</span><span class="sxs-lookup"><span data-stu-id="bba59-129">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="bba59-130">Si hay dos entradas, seleccione el otro con el GUID distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="bba59-130">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="bba59-131">Asegúrese de que la fila seleccionada: debe resaltar azul</span><span class="sxs-lookup"><span data-stu-id="bba59-131">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="bba59-132">En la parte inferior del cuadro de diálogo hay dos botones de radio.</span><span class="sxs-lookup"><span data-stu-id="bba59-132">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="bba59-133">Seleccione la que dice que **aprovisionar el dispositivo y elija la configuración del depurador**.</span><span class="sxs-lookup"><span data-stu-id="bba59-133">Select the one which says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="bba59-134">Seleccione **siguiente**</span><span class="sxs-lookup"><span data-stu-id="bba59-134">Select **Next**</span></span>

* <span data-ttu-id="bba59-135">En el **configurar el depurador**, establezca la configuración apropiada.</span><span class="sxs-lookup"><span data-stu-id="bba59-135">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="bba59-136">Tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="bba59-136">Note the following:</span></span>
   * <span data-ttu-id="bba59-137">El MinnowBoardMax puede usar la red para la depuración.</span><span class="sxs-lookup"><span data-stu-id="bba59-137">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="bba59-138">Utilice el tipo de conexión **red**</span><span class="sxs-lookup"><span data-stu-id="bba59-138">Use connection type **Network**</span></span>
       * <span data-ttu-id="bba59-139">Seleccione algún puerto: se puede usar el valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="bba59-139">Select some port – default can be used</span></span>
       * <span data-ttu-id="bba59-140">Seleccione alguna clave: se puede usar el valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="bba59-140">Select some key – default can be used</span></span>
       * <span data-ttu-id="bba59-141">Seleccione la dirección IP del host de la máquina que ejecuta visual studio.</span><span class="sxs-lookup"><span data-stu-id="bba59-141">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="bba59-142">No use la dirección autonet (169.xxx).</span><span class="sxs-lookup"><span data-stu-id="bba59-142">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="bba59-143">Seleccione **siguiente**</span><span class="sxs-lookup"><span data-stu-id="bba59-143">Select **Next**</span></span>
       
  ![Configurar opciones de depuración](../media/DriverDeployment/confdbgsettings.png)
       
    * <span data-ttu-id="bba59-145">Raspberry Pi usa serie para la depuración del kernel.</span><span class="sxs-lookup"><span data-stu-id="bba59-145">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="bba59-146">Conecte el cable de la depuración serie adecuado para el PI y el equipo host</span><span class="sxs-lookup"><span data-stu-id="bba59-146">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="bba59-147">Seleccione **serie** para el tipo de conexión</span><span class="sxs-lookup"><span data-stu-id="bba59-147">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="bba59-148">Rellene el resto de los parámetros según corresponda para Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="bba59-148">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="bba59-149">Seleccione **siguiente**</span><span class="sxs-lookup"><span data-stu-id="bba59-149">Select **Next**</span></span>

* <span data-ttu-id="bba59-150">Ahora, el WDK, a través de VS, proporcionará el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="bba59-150">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="bba59-151">TAEF y WDTF se instalará en el dispositivo y el dispositivo se configurará para depuración por la configuración proporcionada por encima del kernel.</span><span class="sxs-lookup"><span data-stu-id="bba59-151">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="bba59-152">Cuando haya terminado, puede reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bba59-152">When complete, the device may reboot.</span></span>  <span data-ttu-id="bba59-153">La pantalla de progreso en la **configuración del dispositivo** proporcionará el estado y se muestra en completarse cuando se haya completado la instalación del dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="bba59-153">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="bba59-154">Presione **finalizar**.</span><span class="sxs-lookup"><span data-stu-id="bba59-154">Press **Finish**.</span></span>

![Configurar el progreso](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="bba59-156">El dispositivo ya está aprovisionado y el **configuración de prueba de dispositivo** estado aparezca **configurado para las pruebas de controladores**</span><span class="sxs-lookup"><span data-stu-id="bba59-156">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a><span data-ttu-id="bba59-158">Paso 3: Configurar el proyecto de controlador de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bba59-158">Step 3 : Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="bba59-159">Inicie Visual Studio en el modo de administrador y abra el proyecto de controlador de visual studio.</span><span class="sxs-lookup"><span data-stu-id="bba59-159">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="bba59-160">Asegúrese de que la versión de la plataforma de destino coincide con el SDK instalado en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="bba59-160">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="bba59-161">Seleccione las propiedades del proyecto en la ventana Explorador de soluciones.</span><span class="sxs-lookup"><span data-stu-id="bba59-161">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="bba59-162">En Propiedades de configuración General de garantizar que las coincidencias de la versión de la plataforma de destino que el SDK instalado en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="bba59-162">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="bba59-163">Puede comprobar la versión del SDK desde la **Panel de Control > Programas > programas y características**.</span><span class="sxs-lookup"><span data-stu-id="bba59-163">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="bba59-164">En **proyecto > Agregar nuevo elemento > Visual C++ > Windows Driver**, seleccione **manifiesto del paquete** y presione **agregar**.</span><span class="sxs-lookup"><span data-stu-id="bba59-164">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` <span data-ttu-id="bba59-166">archivo se agregará al proyecto.</span><span class="sxs-lookup"><span data-stu-id="bba59-166">file will be added to the project.</span></span> <span data-ttu-id="bba59-167">En este archivo, especifique las etiquetas de propietario, plataforma, componente y del subcomponente.</span><span class="sxs-lookup"><span data-stu-id="bba59-167">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span> 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. <span data-ttu-id="bba59-169">Establecer el número de versión del paquete en **las propiedades del proyecto > PackageGen > versión**.</span><span class="sxs-lookup"><span data-stu-id="bba59-169">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="bba59-170">Tenga en cuenta que cada vez que necesita realizar una instalación o reinstalación del controlador, el número de versión va a incrementar.</span><span class="sxs-lookup"><span data-stu-id="bba59-170">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="bba59-172">En **las propiedades del proyecto > firma de controladores > certificado de prueba**, seleccione prueba certificate (certificado de prueba de OEM de teléfono)</span><span class="sxs-lookup"><span data-stu-id="bba59-172">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="bba59-174">Vaya a **instalar controlador** y seleccione **implementación**</span><span class="sxs-lookup"><span data-stu-id="bba59-174">Go to **Driver Install** and select **Deployment**</span></span>

![InstallOptions](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="bba59-176">Desde el **nombre de dispositivo de destino** lista desplegable, seleccione el destino que creó anteriormente en el proceso de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="bba59-176">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="bba59-177">Tenga en cuenta las dos opciones para **instalar o reinstalar** y **rápido volver a instalar**.</span><span class="sxs-lookup"><span data-stu-id="bba59-177">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="bba59-178">Elija una opción y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="bba59-178">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="bba59-179">**Instalar o reinstalar** se usa para la instalación inicial de un controlador para el destino.</span><span class="sxs-lookup"><span data-stu-id="bba59-179">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="bba59-180">Esto instala el paquete de controladores mediante la pila de Windows update y puede tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="bba59-180">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="bba59-181">Esto se debe usar cada vez que se modifica el archivo INF.</span><span class="sxs-lookup"><span data-stu-id="bba59-181">This must be used every time the INF file is changed.</span></span> 
    
> [!TIP]
> <span data-ttu-id="bba59-182">Cada vez que se utiliza esta opción para instalar a un controlador después de la instalación inicial, se debe incrementar el número de versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="bba59-182">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="bba59-183">**Rápida Reinstall** puede usarse una vez que se ha instalado un controlador, y no hay ningún cambio posterior en el archivo INF de controladores que afectan al registro.</span><span class="sxs-lookup"><span data-stu-id="bba59-183">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file which affect the registry.</span></span>  <span data-ttu-id="bba59-184">Este método omite el proceso de instalación, se cierra devnodes todos los asociados con el controlador, copia el controlador a través de y reinicia el devnode.</span><span class="sxs-lookup"><span data-stu-id="bba59-184">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="bba59-185">Este proceso tarda unos pocos (< 20) segundos.</span><span class="sxs-lookup"><span data-stu-id="bba59-185">This takes a few (<20) seconds.</span></span>

    
> [!WARNING]
> <span data-ttu-id="bba59-186">Este método no garantiza que se realice correctamente, si por alguna razón que un devnode no puede estar apagado para liberar el controlador, la operación dará error.</span><span class="sxs-lookup"><span data-stu-id="bba59-186">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="bba59-187">Esto puede ser debido a errores de hardware o una implementación defectuosa inicial del controlador.</span><span class="sxs-lookup"><span data-stu-id="bba59-187">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="bba59-188">La opción de instalar o reinstalar debe usarse en este caso.</span><span class="sxs-lookup"><span data-stu-id="bba59-188">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="bba59-189">El proyecto de Visual Studio ahora está listo para compilar e implementar un controlador para el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="bba59-189">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="bba59-190">Si utiliza el controlador de gpiokmdfdemo de ejemplo que necesita para generar la tabla ACPI y copiar en el dispositivo de destino, a continuación, siga los pasos de [generar el controlador en Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span><span class="sxs-lookup"><span data-stu-id="bba59-190">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4--build-and-deploy-driver"></a><span data-ttu-id="bba59-191">Paso 4: Compilación e implementación de controlador</span><span class="sxs-lookup"><span data-stu-id="bba59-191">Step 4 : Build and deploy driver</span></span>
___
<span data-ttu-id="bba59-192">Esto puede hacerse de dos maneras: mediante el **F5** clave y usar el **implementar** opción.</span><span class="sxs-lookup"><span data-stu-id="bba59-192">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="bba59-193">En ambos sentidos, se creará e implementará el controlador (es decir, lo instala en el dispositivo) y la F5 asocia el depurador del núcleo de Visual Studio a los controladores instalados y cargados.</span><span class="sxs-lookup"><span data-stu-id="bba59-193">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span> 

<span data-ttu-id="bba59-194">Algunos usuarios prefieren usar la **implementar** funcionalidad y adjuntar un depurador de kernel diferente, como WinDBG, KD.</span><span class="sxs-lookup"><span data-stu-id="bba59-194">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="bba59-195">Esto puede proporcionar más flexibilidad que utilizar al depurador de VS.</span><span class="sxs-lookup"><span data-stu-id="bba59-195">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="bba59-196">Implementar</span><span class="sxs-lookup"><span data-stu-id="bba59-196">Deploy</span></span>
1.  <span data-ttu-id="bba59-197">Haga doble clic en el proyecto en el Explorador de soluciones</span><span class="sxs-lookup"><span data-stu-id="bba59-197">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="bba59-198">Seleccione **implementar**</span><span class="sxs-lookup"><span data-stu-id="bba59-198">Select **Deploy**</span></span>

![Implementar](../media/DriverDeployment/deploy.png) 

3.  <span data-ttu-id="bba59-200">Debe continuar el proceso de implementación.</span><span class="sxs-lookup"><span data-stu-id="bba59-200">The deployment process should proceed.</span></span>  <span data-ttu-id="bba59-201">El dispositivo de IoT se reiniciará después de la implementación y debe mostrar la pantalla "Gears" mientras está realizando la instalación.</span><span class="sxs-lookup"><span data-stu-id="bba59-201">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="bba59-202">Generar salida está en el **salida** implementación de la ventana de estado también está en la ventana de salida de instalación cuando se complete, volverán a reiniciar el dispositivo y la pantalla de salida de VS indica éxito o error.</span><span class="sxs-lookup"><span data-stu-id="bba59-202">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="bba59-203">F5</span><span class="sxs-lookup"><span data-stu-id="bba59-203">F5</span></span>

1.  <span data-ttu-id="bba59-204">En la ventana de compilación, asegúrese de que las configuraciones son correctas, la arquitectura de compilación actual es igual que la arquitectura de dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="bba59-204">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="bba59-205">Esto es donde es útil tener el arco en el nombre de destino.</span><span class="sxs-lookup"><span data-stu-id="bba59-205">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="bba59-206">El destino se mostrará en el cuadro de vista en la barra de menú en Visual Studio en la parte central derecha superior.</span><span class="sxs-lookup"><span data-stu-id="bba59-206">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="bba59-207">Presione **F5**.</span><span class="sxs-lookup"><span data-stu-id="bba59-207">Press **F5**.</span></span>  <span data-ttu-id="bba59-208">El destino se creado, implementado y asociado al depurador de Kernel de VS.</span><span class="sxs-lookup"><span data-stu-id="bba59-208">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="bba59-209">Después del reinicio, asegúrese de que PowerShell todavía está conectado a ella, en caso contrario, vuelva a conectarse al dispositivo de destino mediante el PowerShell `enter-pssession` comando...</span><span class="sxs-lookup"><span data-stu-id="bba59-209">After the reboot, make sure PowerShell is still connected to it, otherwise, re-connect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="bba59-210">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="bba59-210">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="bba59-211">Errores de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="bba59-211">Provisioning Errors</span></span>
<span data-ttu-id="bba59-212">Una condición de carrera durante la interacción con MinnowBoardMax puede producir un error notificado durante el aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="bba59-212">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="bba59-213">De hecho, más probable es que el aprovisionamiento correcto.</span><span class="sxs-lookup"><span data-stu-id="bba59-213">In fact, the provisioning most likely succeeded.</span></span>

**<span data-ttu-id="bba59-214">Lista de errores:</span><span class="sxs-lookup"><span data-stu-id="bba59-214">List of Errors:</span></span>**
 
* <span data-ttu-id="bba59-215">ERROR: Tarea "registrar WDTF" no se pudo completar correctamente.</span><span class="sxs-lookup"><span data-stu-id="bba59-215">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="bba59-216">ERROR: No se pudo completar correctamente la tarea "Configurar kernel configuración del depurador (reinicio posible)"</span><span class="sxs-lookup"><span data-stu-id="bba59-216">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="bba59-217">**Solución:** Casi seguro que se pueden omitir estos errores.</span><span class="sxs-lookup"><span data-stu-id="bba59-217">**Workaround:** These error can almost certainly be ignored.</span></span>

**<span data-ttu-id="bba59-218">Detalles:</span><span class="sxs-lookup"><span data-stu-id="bba59-218">Details:</span></span>**

<span data-ttu-id="bba59-219">Se mostrará el siguiente error en la **progreso de la configuración de dispositivo configuración** cuadro de diálogo:</span><span class="sxs-lookup"><span data-stu-id="bba59-219">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

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

<span data-ttu-id="bba59-220">En este momento puede hacer clic con seguridad en el **finalizar** y, a continuación, el **aplicar** y **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="bba59-220">At this point you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="bba59-221">Se trata de un error inofensivo formado por una condición de carrera que provoca que un registro de resultados tener un formato incorrecto.</span><span class="sxs-lookup"><span data-stu-id="bba59-221">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="bba59-222">Esto se puede comprobar examinando el archivo de registro en las áreas siguientes:</span><span class="sxs-lookup"><span data-stu-id="bba59-222">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="bba59-223">Abra una conexión FTP a la dirección IP del dispositivo (como se muestra en la pantalla del dispositivo) para el `Data/test/bin/DriverTest/Run` directory.</span><span class="sxs-lookup"><span data-stu-id="bba59-223">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="bba59-224">P. ej.</span><span class="sxs-lookup"><span data-stu-id="bba59-224">e.g.</span></span>
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. <span data-ttu-id="bba59-225">copia el `Configuring_computer_settings_(possible_reboot)_identifier.wtl` archivo en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="bba59-225">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="bba59-226">Tenga en cuenta que el nombre de archivo de registro coincide con el nombre de la tarea con errores.</span><span class="sxs-lookup"><span data-stu-id="bba59-226">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="bba59-227">Abra el archivo en el Bloc de notas</span><span class="sxs-lookup"><span data-stu-id="bba59-227">Open the file in notepad</span></span>
4. <span data-ttu-id="bba59-228">Desplácese hasta el final del registro.</span><span class="sxs-lookup"><span data-stu-id="bba59-228">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="bba59-229">El siguiente texto estará presente, que indica que el aprovisionamiento sea correcto.</span><span class="sxs-lookup"><span data-stu-id="bba59-229">The following text will be present, indicating that the provisioning is successful.</span></span>

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

