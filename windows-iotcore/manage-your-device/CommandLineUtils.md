---
title: Utilidades de línea de comandos de Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las utilidades de línea de comandos para usar con PowreShell después de conectarse al dispositivo.
keywords: Windows iot, línea de comandos, utilidades de línea de comandos, PowerShell
ms.openlocfilehash: 2fb009115dc929540c30d5403c1877051f6b7037
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514771"
---
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="de614-104">Utilidades de línea de comandos de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="de614-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="de614-105">¿Desea para configurar algunos de los valores en el dispositivo?</span><span class="sxs-lookup"><span data-stu-id="de614-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="de614-106">Las siguientes herramientas están disponibles a su disposición.</span><span class="sxs-lookup"><span data-stu-id="de614-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="de614-107">Use PowerShell para ejecutar estos comandos [conectarse al dispositivo](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="de614-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="de614-108">Estas herramientas no se cargan previamente, deberá incluir identificadores de características correspondiente para obtener estas herramientas en la imagen.</span><span class="sxs-lookup"><span data-stu-id="de614-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="de614-109">Utilidades de línea de comandos específicas de IoT Core</span><span class="sxs-lookup"><span data-stu-id="de614-109">IoT Core-specific Command Line Utils</span></span>

### **<a name="setting-startup-app"></a><span data-ttu-id="de614-110">Aplicación de inicio de configuración:</span><span class="sxs-lookup"><span data-stu-id="de614-110">Setting startup app:</span></span>**
<span data-ttu-id="de614-111">Use el editor de inicio para configurar las aplicaciones de inicio en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="de614-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="de614-112">Ejecute `IotStartup` con cualquiera de las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="de614-112">Run `IotStartup` with any of the following options:</span></span>

* `IotStartup list` <span data-ttu-id="de614-113">las listas de las aplicaciones instaladas</span><span class="sxs-lookup"><span data-stu-id="de614-113">lists installed applications</span></span>
* `IotStartup list headed` <span data-ttu-id="de614-114">listas instaladas puntas de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="de614-114">lists installed headed applications</span></span>
* `IotStartup list headless` <span data-ttu-id="de614-115">aplicaciones sin periféricos listas instaladas</span><span class="sxs-lookup"><span data-stu-id="de614-115">lists installed headless applications</span></span>
* `IotStartup list [MyApp]` <span data-ttu-id="de614-116">lista de aplicaciones instaladas que coinciden con el patrón</span><span class="sxs-lookup"><span data-stu-id="de614-116">list installed applications that match pattern</span></span> `MyApp`
* `IotStartup add` <span data-ttu-id="de614-117">Agrega aplicaciones puntas y sin periféricos</span><span class="sxs-lookup"><span data-stu-id="de614-117">adds headed and headless applications</span></span>
* `IotStartup add headed [MyApp]` <span data-ttu-id="de614-118">Agrega las puntas de las aplicaciones que coinciden con el patrón `MyApp`.</span><span class="sxs-lookup"><span data-stu-id="de614-118">adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="de614-119">Patrón debe coincidir con sólo una aplicación.</span><span class="sxs-lookup"><span data-stu-id="de614-119">Pattern must match only one application.</span></span>
* `IotStartup add headless [Task1]` <span data-ttu-id="de614-120">Agrega aplicaciones sin periféricos que coinciden con el patrón</span><span class="sxs-lookup"><span data-stu-id="de614-120">adds headless applications that match pattern</span></span> `Task1`
* `IotStartup remove` <span data-ttu-id="de614-121">Quita puntas y las aplicaciones sin periféricos</span><span class="sxs-lookup"><span data-stu-id="de614-121">removes headed and headless applications</span></span>
* `IotStartup remove headed [MyApp]` <span data-ttu-id="de614-122">Quita las aplicaciones que coinciden con el patrón de puntas</span><span class="sxs-lookup"><span data-stu-id="de614-122">removes headed applications that match pattern</span></span> `MyApp`
* `IotStartup remove headless [Task1]` <span data-ttu-id="de614-123">Quita las aplicaciones sin periféricos que coinciden con el patrón</span><span class="sxs-lookup"><span data-stu-id="de614-123">removes headless applications that match pattern</span></span> `Task1`
* `IotStartup startup` <span data-ttu-id="de614-124">listas puntas y las aplicaciones sin periféricos registradas para el inicio</span><span class="sxs-lookup"><span data-stu-id="de614-124">lists headed and headless applications registered for startup</span></span>
* `IotStartup startup [MyApp]` <span data-ttu-id="de614-125">listas puntas y las aplicaciones sin periféricos registran para el inicio de ese patrón de coincidencia</span><span class="sxs-lookup"><span data-stu-id="de614-125">lists headed and headless applications registered for startup that match pattern</span></span> `MyApp`
* `IotStartup startup headed [MyApp]` <span data-ttu-id="de614-126">listas puntas registradas para el inicio de aplicaciones que coinciden con</span><span class="sxs-lookup"><span data-stu-id="de614-126">lists headed applications registered for startup that match</span></span> `MyApp`
* `IotStartup startup headless [Task1]` <span data-ttu-id="de614-127">Enumera las aplicaciones sin periféricos registradas para el inicio que coinciden con</span><span class="sxs-lookup"><span data-stu-id="de614-127">lists headless applications registered for startup that match</span></span> `Task1`

    * <span data-ttu-id="de614-128">Para obtener más ayuda, pruebe</span><span class="sxs-lookup"><span data-stu-id="de614-128">For further help, try</span></span> `IotStartup help`
    
### **<a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="de614-129">Cambiar la configuración de idioma de la región y de usuario o de voz:</span><span class="sxs-lookup"><span data-stu-id="de614-129">Change settings for region and user or speech language:</span></span>**

<span data-ttu-id="de614-130">El `IoTSettings` herramienta cambia la región, el idioma del usuario o el idioma de voz.</span><span class="sxs-lookup"><span data-stu-id="de614-130">The `IoTSettings` tool changes region, user language or speech language.</span></span> <span data-ttu-id="de614-131">Esto es una herramienta de línea de comandos que se puede invocar desde una aplicación mediante la API ProcessLauncher.</span><span class="sxs-lookup"><span data-stu-id="de614-131">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="de614-132">Estos comandos se deben ejecutar como cuenta predeterminada, no administrador.</span><span class="sxs-lookup"><span data-stu-id="de614-132">These commands must be run as default account, not administrator.</span></span>

* `IotSettings del account {all | username}` <span data-ttu-id="de614-133">Elimina todas las MSA o AAD cuentas del sistema o una cuenta específica.</span><span class="sxs-lookup"><span data-stu-id="de614-133">deletes all MSA or AAD accounts on the system or a specific account.</span></span>  <span data-ttu-id="de614-134">Cuentas específicas adoptan la forma username@provider.com</span><span class="sxs-lookup"><span data-stu-id="de614-134">Specific accounts take the form username@provider.com</span></span>
* `IotSettings del diagnostics` <span data-ttu-id="de614-135">elimina la información de diagnóstico en la nube para el dispositivo actual.</span><span class="sxs-lookup"><span data-stu-id="de614-135">deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="de614-136">Tenga en cuenta que esto quita el historial hasta el momento de invocación.</span><span class="sxs-lookup"><span data-stu-id="de614-136">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="de614-137">Nueva información de diagnóstico seguirán se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="de614-137">New diagnostics information will continue to be logged.</span></span>
* `IotSettings list account` <span data-ttu-id="de614-138">Enumera todas las MSA o AAD cuentas que han sido firmadas en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="de614-138">lists all MSA or AAD accounts that have been signed into the device.</span></span>
* `IotSettings list uilanguage` <span data-ttu-id="de614-139">Enumera todos los idiomas de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="de614-139">lists all UI languages</span></span>
* `IotSettings list speechlanguage` <span data-ttu-id="de614-140">Enumera todos los idiomas de voz</span><span class="sxs-lookup"><span data-stu-id="de614-140">lists all speech languages</span></span>
* `IotSettings get uilanguage` <span data-ttu-id="de614-141">Muestra el idioma de interfaz de usuario actual</span><span class="sxs-lookup"><span data-stu-id="de614-141">displays current UI language</span></span>
* `IotSettings get speechlanguage` <span data-ttu-id="de614-142">Muestra el idioma actual de voz</span><span class="sxs-lookup"><span data-stu-id="de614-142">displays current speech language</span></span>
* `IotSettings get region` <span data-ttu-id="de614-143">Muestra la región actual</span><span class="sxs-lookup"><span data-stu-id="de614-143">displays current region</span></span>
* `IotSettings set uilanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="de614-144">establece el idioma predeterminado de la interfaz de usuario francés canadiense)</span><span class="sxs-lookup"><span data-stu-id="de614-144">sets default UI language French Canadian)</span></span>
* `IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` <span data-ttu-id="de614-145">establece el idioma francés canadiense de voz)</span><span class="sxs-lookup"><span data-stu-id="de614-145">sets speech language French Canadian)</span></span>
* `IotSettings set region region\_code - (e.g. CA)` <span data-ttu-id="de614-146">establece la región predeterminada para Canadá)</span><span class="sxs-lookup"><span data-stu-id="de614-146">sets default region to Canada)</span></span>
* `IotSettings set bluetoothpref {sink | source}` <span data-ttu-id="de614-147">Especifica la preferencia de función Bluetooth para seleccionar cuando se conectan los dispositivos integrados con las características de IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK a otro dispositivo que también admite ambos roles.</span><span class="sxs-lookup"><span data-stu-id="de614-147">Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* `IotSettings get bluetoothpref` <span data-ttu-id="de614-148">Devuelve la preferencia de rol de Bluetooth actual para los dispositivos integrados con IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK.</span><span class="sxs-lookup"><span data-stu-id="de614-148">returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="de614-149">El valor predeterminado es el origen.</span><span class="sxs-lookup"><span data-stu-id="de614-149">The default is source.</span></span>

> [!TIP]
> `IoTSettings -list uiLanguage` <span data-ttu-id="de614-150">proporcionará volver la lista de idioma de interfaz de usuario compatible (en la versión de imagen de Windows IoT core con que se ha ejecutado)</span><span class="sxs-lookup"><span data-stu-id="de614-150">will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### **<a name="change-default-audio-device-and-volume"></a><span data-ttu-id="de614-151">Cambiar el dispositivo de audio predeterminado y el volumen:</span><span class="sxs-lookup"><span data-stu-id="de614-151">Change default audio device and volume:</span></span>**

<span data-ttu-id="de614-152">El `IoTCoreAudioControlTool` herramienta controla las opciones relacionadas audio como valor predeterminado de los dispositivos de captura y reproducción y cambiar el volumen.</span><span class="sxs-lookup"><span data-stu-id="de614-152">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="de614-153">Para obtener una lista completa de parámetros, ejecute `IoTCoreAudioControlTool h`.</span><span class="sxs-lookup"><span data-stu-id="de614-153">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### **<a name="manually-installing-appx-files"></a><span data-ttu-id="de614-154">Instalación manual. Archivos APPX:</span><span class="sxs-lookup"><span data-stu-id="de614-154">Manually installing .APPX files:</span></span>**
<span data-ttu-id="de614-155">DeployAppx permite instalar y quitar en. Paquetes APPX en escenarios de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="de614-155">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="de614-156">El método correcto para la instalación. Los paquetes APPX en imágenes de producción es usar un paquete de aprovisionamiento como se documenta en el [instalar la aplicación](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) asunto.</span><span class="sxs-lookup"><span data-stu-id="de614-156">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="de614-157">DeployAppx también admite las consultas. Información del paquete APPX.</span><span class="sxs-lookup"><span data-stu-id="de614-157">DeployAppx also supports querying .APPX package information.</span></span>

*  `DeployAppx install MyApp.appx` <span data-ttu-id="de614-158">instala el. APPX y el certificado del mismo nombre si se encuentra.</span><span class="sxs-lookup"><span data-stu-id="de614-158">installs the .APPX and the certificate of the same name if found.</span></span>
* `DeployAppx install force MyApp.appx` <span data-ttu-id="de614-159">fuerza la desinstalación instalado actualmente. Nombre de Instalada con el mismo paquete si se encuentra antes de instalar el nuevo. APPX.</span><span class="sxs-lookup"><span data-stu-id="de614-159">forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="de614-160">Esto es útil para instalar una. APPX con el número de versión igual o menor que la instalada actualmente. APPX.</span><span class="sxs-lookup"><span data-stu-id="de614-160">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* `DeployAppx install retry MyApp.appx` <span data-ttu-id="de614-161">Vuelva a intentar instalar el. APPX 10 veces en caso de error con 2 segundo intervalo entre intentos.</span><span class="sxs-lookup"><span data-stu-id="de614-161">retry installing the .APPX 10 times on failure with 2 second delay between attempts.</span></span>
* `DeployAppx uninstall App_1.0.1.0_x86__publisherid123` <span data-ttu-id="de614-162">Desinstale el archivo .appx con el nombre completo del paquete correspondiente.</span><span class="sxs-lookup"><span data-stu-id="de614-162">uninstall the .appx with the matching package full name.</span></span>
*  `DeployAppx uninstall MyApp.appx` <span data-ttu-id="de614-163">Desinstale cualquier instalado. APPX con un nombre de familia de paquete coincidente.</span><span class="sxs-lookup"><span data-stu-id="de614-163">uninstall any installed .APPX with a matching package family name.</span></span>
* `DeployAppx getpackages` <span data-ttu-id="de614-164">Muestra los nombres completos de paquetes instalados.</span><span class="sxs-lookup"><span data-stu-id="de614-164">lists installed package full names.</span></span>
* `DeployAppx getpackageid IotCoreDefaultApp.appx` <span data-ttu-id="de614-165">Imprime el nombre del paquete, el nombre de familia de paquete y el paquete de nombre completo para el. APPX.</span><span class="sxs-lookup"><span data-stu-id="de614-165">prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* `DeployAppx register appxmanifest.xml` <span data-ttu-id="de614-166">no admitido</span><span class="sxs-lookup"><span data-stu-id="de614-166">unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="de614-167">Utilidades de línea de comandos general</span><span class="sxs-lookup"><span data-stu-id="de614-167">General Command Line Utils</span></span>

### **<a name="update-account-password"></a><span data-ttu-id="de614-168">Actualizar la contraseña de cuenta:</span><span class="sxs-lookup"><span data-stu-id="de614-168">Update account password:</span></span>**

<span data-ttu-id="de614-169">Se recomienda encarecidamente que actualice la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="de614-169">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="de614-170">Para ello, puede emitir el comando siguiente: `net user Administrator [new password]` donde `[new password]` representa una contraseña segura de su elección.</span><span class="sxs-lookup"><span data-stu-id="de614-170">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### **<a name="create-local-user-accounts"></a><span data-ttu-id="de614-171">Crear cuentas de usuario local:</span><span class="sxs-lookup"><span data-stu-id="de614-171">Create local user accounts:</span></span>**

<span data-ttu-id="de614-172">Si desea asignar a otros usuarios acceso a su dispositivo Windows IoT Core, puede crear cuentas de usuario local adicional mediante PS escribiendo en `net user [username] [password] /add`.</span><span class="sxs-lookup"><span data-stu-id="de614-172">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="de614-173">Si desea agregar este usuario a otros grupos, como el grupo de administradores, utilice `net localgroup Administrators [username] /add`.</span><span class="sxs-lookup"><span data-stu-id="de614-173">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### **<a name="set-password"></a><span data-ttu-id="de614-174">Establecer contraseña:</span><span class="sxs-lookup"><span data-stu-id="de614-174">Set password:</span></span>**

<span data-ttu-id="de614-175">Para cambiar la contraseña en una cuenta en el dispositivo, ejecute `net user [account-username] [new-password]` para cambiar la contraseña de cuenta.</span><span class="sxs-lookup"><span data-stu-id="de614-175">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### **<a name="query-and-set-device-name"></a><span data-ttu-id="de614-176">Consultar y establecer el nombre del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="de614-176">Query and set device name:</span></span>**

<span data-ttu-id="de614-177">Para identificar el nombre del dispositivo actual, simplemente escriba `hostname`.</span><span class="sxs-lookup"><span data-stu-id="de614-177">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="de614-178">Para cambiar el nombre de su dispositivo Windows IoT Core, escriba `SetComputerName [new machinename]`.</span><span class="sxs-lookup"><span data-stu-id="de614-178">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="de614-179">Es posible que deba reiniciar el dispositivo para que surta efecto el cambio de nombre.</span><span class="sxs-lookup"><span data-stu-id="de614-179">You may need to restart your device for the name change to take effect.</span></span>

### **<a name="basic-network-configuration"></a><span data-ttu-id="de614-180">Configuración de red básica:</span><span class="sxs-lookup"><span data-stu-id="de614-180">Basic network configuration:</span></span>**

<span data-ttu-id="de614-181">Muchas de las utilidades de configuración básica de la red, puede que ya esté familiarizado con están disponibles en Windows IoT Core, incluidos los comandos como `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, y `arp.exe`.</span><span class="sxs-lookup"><span data-stu-id="de614-181">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### **<a name="copy-utilities"></a><span data-ttu-id="de614-182">Utilidades de copia:</span><span class="sxs-lookup"><span data-stu-id="de614-182">Copy utilities:</span></span>**

<span data-ttu-id="de614-183">Microsoft ofrece herramientas familiares, como `sfpcopy.exe` como `xcopy.exe`.</span><span class="sxs-lookup"><span data-stu-id="de614-183">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### **<a name="process-management"></a><span data-ttu-id="de614-184">Administración de procesos:</span><span class="sxs-lookup"><span data-stu-id="de614-184">Process Management:</span></span>**

<span data-ttu-id="de614-185">Para ver los procesos que se está ejecutando, puede intentar `get-process` o bien puede `tlist.exe`.</span><span class="sxs-lookup"><span data-stu-id="de614-185">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="de614-186">Para detener un proceso en ejecución, escriba `kill.exe [pid or process name]`.</span><span class="sxs-lookup"><span data-stu-id="de614-186">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### **<a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="de614-187">Establezca la opción de arranque (sin periféricos frente a arranque con cabezal):</span><span class="sxs-lookup"><span data-stu-id="de614-187">Set Boot Option (Headless vs. headed boot):</span></span>**

<span data-ttu-id="de614-188">Los dispositivos de Windows IoT Core pueden establecerse a puntas (cuando se requieren funciones de visualización) o sin periféricos (cuando una pantalla no es necesaria o está disponible) el modo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="de614-188">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="de614-189">Para cambiar esta configuración, use `setbootoption.exe [headed | headless]`.</span><span class="sxs-lookup"><span data-stu-id="de614-189">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="de614-190">Si cambia esta configuración, se requerirá un reinicio en orden para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="de614-190">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### **<a name="task-scheduler"></a><span data-ttu-id="de614-191">Programador de tareas:</span><span class="sxs-lookup"><span data-stu-id="de614-191">Task scheduler:</span></span>**

<span data-ttu-id="de614-192">Para ver la lista actual de las tareas programadas, use el `schtasks.exe` comando.</span><span class="sxs-lookup"><span data-stu-id="de614-192">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="de614-193">Puede crear nuevas tareas con el `/create` cambiar o ejecutar tareas y a petición con la `/run` cambie.</span><span class="sxs-lookup"><span data-stu-id="de614-193">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="de614-194">Para obtener una lista completa de parámetros admitidos, utilice</span><span class="sxs-lookup"><span data-stu-id="de614-194">For a full list of supported parameters, use</span></span> `schtasks.exe /?`

### **<a name="device-drivers"></a><span data-ttu-id="de614-195">Controladores de dispositivos:</span><span class="sxs-lookup"><span data-stu-id="de614-195">Device drivers:</span></span>**

<span data-ttu-id="de614-196">La utilidad de la consola del dispositivo es útil para identificar y administrar los dispositivos instalados y los controladores.</span><span class="sxs-lookup"><span data-stu-id="de614-196">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="de614-197">Para obtener una lista completa de parámetros, use</span><span class="sxs-lookup"><span data-stu-id="de614-197">For a full list of parameters, use</span></span> `devcon.exe /?`

### **<a name="registry-access"></a><span data-ttu-id="de614-198">Acceso al registro:</span><span class="sxs-lookup"><span data-stu-id="de614-198">Registry Access:</span></span>**

<span data-ttu-id="de614-199">Si necesita tener acceso al registro para ver o modificar la configuración, utilice el `reg.exe /?` comando para obtener la lista completa de parámetros admitidos.</span><span class="sxs-lookup"><span data-stu-id="de614-199">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### **<a name="services"></a><span data-ttu-id="de614-200">Servicios:</span><span class="sxs-lookup"><span data-stu-id="de614-200">Services:</span></span>**

<span data-ttu-id="de614-201">Administración de servicios de Windows se puede realizar mediante el `net.exe` comando.</span><span class="sxs-lookup"><span data-stu-id="de614-201">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="de614-202">Para ver una lista de servicios en ejecución, escriba `net start`.</span><span class="sxs-lookup"><span data-stu-id="de614-202">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="de614-203">Para iniciar o detener un servicio específico, escriba `net [start | stop] [service name]`.</span><span class="sxs-lookup"><span data-stu-id="de614-203">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="de614-204">Como alternativa, también puede usar el Administrador de control de servicios a través de `sc.exe` comando.</span><span class="sxs-lookup"><span data-stu-id="de614-204">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### **<a name="boot-configuration"></a><span data-ttu-id="de614-205">Configuración de arranque:</span><span class="sxs-lookup"><span data-stu-id="de614-205">Boot configuration:</span></span>**

<span data-ttu-id="de614-206">Puede realizar cambios a la configuración de arranque del dispositivo Windows IoT Core mediante `bcdedit.exe`.</span><span class="sxs-lookup"><span data-stu-id="de614-206">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="de614-207">Por ejemplo, puede habilitar testsigning con `bcdedit –set testsigning on` comando.</span><span class="sxs-lookup"><span data-stu-id="de614-207">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### **<a name="shutdownrestart-device"></a><span data-ttu-id="de614-208">Cierre o reinicio del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="de614-208">Shutdown/restart device:</span></span>**

<span data-ttu-id="de614-209">Para apagar el dispositivo, escriba `shutdown /s /t 0`.</span><span class="sxs-lookup"><span data-stu-id="de614-209">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="de614-210">Para reiniciar el dispositivo, use el `/r` en su lugar cambiar con el comando `shutdown /r /t 0`.</span><span class="sxs-lookup"><span data-stu-id="de614-210">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### **<a name="viewing-and-changing-display-settings"></a><span data-ttu-id="de614-211">Ver y cambiar la configuración de pantalla</span><span class="sxs-lookup"><span data-stu-id="de614-211">Viewing and changing display settings</span></span>**
<span data-ttu-id="de614-212">La herramienta SetDisplayResolution puede utilizarse para enumerar la configuración de pantalla actual y para mostrar la lista de valores admitidos.</span><span class="sxs-lookup"><span data-stu-id="de614-212">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="de614-213">Además puede utilizarse para ajustar la resolución de la presentación, frecuencia de actualización u orientación a los valores admitidos por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="de614-213">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="de614-214">La utilidad acepta los argumentos de línea de comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="de614-214">The utility accepts the following command line arguments:</span></span>

* `SetDisplayResolution` <span data-ttu-id="de614-215">Enumera lo resoltuion de presentación actual.</span><span class="sxs-lookup"><span data-stu-id="de614-215">Lists the current display resoltuion.</span></span>
* `SetDisplayResolution -list` <span data-ttu-id="de614-216">Las listas admiten resoluciones de pantalla.</span><span class="sxs-lookup"><span data-stu-id="de614-216">Lists supported display resolutions.</span></span>
* `SetDisplayResolution -orientation:[n]` <span data-ttu-id="de614-217">Cambiar la orientación de pantalla, donde n = 0, 90, 180 o 270.</span><span class="sxs-lookup"><span data-stu-id="de614-217">Change the display orientation, where n=0,90,180 or 270.</span></span>
* `SetDisplayResolution [width] [height]` <span data-ttu-id="de614-218">Cambiar el ancho y alto en píxeles</span><span class="sxs-lookup"><span data-stu-id="de614-218">Change the width and height in pixels</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate]` <span data-ttu-id="de614-219">Cambiar ancho, alto y frecuencia de actualización donde son la anchura y altura en píxeles y refreshrate en Hz</span><span class="sxs-lookup"><span data-stu-id="de614-219">Change width, height and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* `SetDisplayResolution [width] [height] [refreshrate] [orientation]` <span data-ttu-id="de614-220">Cambiar la orientación de ancho, alto, refreshrate y pantalla donde son de ancho y alto en píxeles, refreshrate en Hz y orientación es uno de 0, 90, 180 o 270.</span><span class="sxs-lookup"><span data-stu-id="de614-220">Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### **<a name="take-screenshot"></a><span data-ttu-id="de614-221">Obtener captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="de614-221">Take screenshot:</span></span>**

<span data-ttu-id="de614-222">Puede realizar la captura de pantalla del dispositivo Windows IoTCore mediante `ScreenCapture.exe`.</span><span class="sxs-lookup"><span data-stu-id="de614-222">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="de614-223">Por ejemplo, ejecute `ScreenCapture c:\folder\screencap.jpg` tomará la captura de pantalla y guardarla en el archivo screencap.jpg.</span><span class="sxs-lookup"><span data-stu-id="de614-223">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### **<a name="get-information-about-network-adapters"></a><span data-ttu-id="de614-224">Obtenga información acerca de los adaptadores de red:</span><span class="sxs-lookup"><span data-stu-id="de614-224">Get information about Network Adapters:</span></span>**

<span data-ttu-id="de614-225">Para ver la lista de todos los adaptadores de red disponible, ejecute `GetAdapterInfo` herramienta.</span><span class="sxs-lookup"><span data-stu-id="de614-225">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### **<a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="de614-226">Establecer permisos de carpeta para las aplicaciones para UWP:</span><span class="sxs-lookup"><span data-stu-id="de614-226">Set folder permissions for UWP apps:</span></span>**

<span data-ttu-id="de614-227">No todas las carpetas en el dispositivo están accesible mediante aplicaciones universales de Windows.</span><span class="sxs-lookup"><span data-stu-id="de614-227">Not all folders on your device are accesible by Universal Windows Apps.</span></span> <span data-ttu-id="de614-228">Para hacer accesible a una carpeta en una aplicación para UWP, puede usar `FolderPermissions` herramienta.</span><span class="sxs-lookup"><span data-stu-id="de614-228">To make a folder accesible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="de614-229">Por ejemplo ejecutar `FolderPermissions c:\test -e` para brindar acceso de aplicaciones para UWP a `c:\test` carpeta.</span><span class="sxs-lookup"><span data-stu-id="de614-229">For example run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="de614-230">Tenga en cuenta que esto funcionará sólo con las API de Win32 nativas para p. ej.</span><span class="sxs-lookup"><span data-stu-id="de614-230">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="de614-231">CreateFile2 y no con las API de WinRT como StorageFolder, etcetera StorageFile.</span><span class="sxs-lookup"><span data-stu-id="de614-231">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### **<a name="work-with-serial-ports"></a><span data-ttu-id="de614-232">Trabajar con los puertos serie:</span><span class="sxs-lookup"><span data-stu-id="de614-232">Work with Serial Ports:</span></span>**
<span data-ttu-id="de614-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) le permite trabajar con los puertos serie desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="de614-233">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="de614-234">Se proporciona como un proyecto de ejemplo en el repositorio de ejemplos de iot de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="de614-234">It is provided as a sample project in the ms-iot samples repo.</span></span> 

``` 
Usage: MinComm.exe [-list] device_path [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]

  -list                List all available serial ports on the system and exit.
  device_path          Device path or COM port to open (e.g. COM1)
  baud=<B>             Specifies the transmission rate in bits per second.
  parity={n|e|o|m|s}   Specifies how the system uses the parity bit to check
                       for transmission errors. The abbreviations stand for
                       none, even, odd, mark, and space.
  data={5|6|7|8}       Specifies the number of data bits in a character.
  stop={1|1.5|2}       Specifies the number of stop bits that define the end of
                       a character.
  xon={on|off}         Specifies whether the xon or xoff protocol for data-flow
                       control is on or off.
  odsr={on|off}        Specifies whether output handshaking that uses the
                       Data Set Ready (DSR) circuit is on or off.
  octs={on|off}        Specifies whether output handshaking that uses the
                       Clear To Send (CTS) circuit is on or off.
  dtr={on|off|hs}      Specifies whether the Data Terminal Ready (DTR) circuit
                       is on or off or set to handshake.
  rts={on|off|hs|tg}   Specifies whether the Request To Send (RTS) circuit is
                       set to on, off, handshake, or toggle.
  idsr={on|off}        Specifies whether the DSR circuit sensitivity is on
                       or off.

Parameters that are not specified will default to the port's current
configuration. For more information on the connection parameters, see the
Technet documentation for the Mode command:
  https://technet.microsoft.com/library/cc732236.aspx

Examples:
  Connect to the first serial port found in the port's current configuration:
    MinComm.exe

  List all serial ports on the system:
    MinComm.exe -list

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe COM1 baud=115200 parity=n data=8 stop=1

  Open COM1 in 115200 8N1 configuration:
    MinComm.exe \\.\COM1 baud=115200 parity=n data=8 stop=1

  Open device interface in 115200 8N1 configuration:
    MinComm.exe \\?\USB#VID_FFFF&PID_0005#{86e0d1e0-8089-11d0-9ce4-08003e301f73} baud=115200 parity=n data=8 stop=1```


