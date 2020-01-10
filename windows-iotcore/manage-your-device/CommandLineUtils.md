---
title: Utilidades de la línea de comandos de IoT Core de Windows 10
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de las utilidades de línea de comandos que debe usar con PowreShell después de conectarse al dispositivo.
keywords: Windows IOT, línea de comandos, utilidades de línea de comandos, PowerShell
ms.openlocfilehash: 9e654e59f3019522f209107acd1b1ed64155d446
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721613"
---
# <a name="windows-10-iot-core-command-line-utils"></a><span data-ttu-id="02f93-104">Utilidades de la línea de comandos de IoT Core de Windows 10</span><span class="sxs-lookup"><span data-stu-id="02f93-104">Windows 10 IoT Core Command Line Utils</span></span>

<span data-ttu-id="02f93-105">¿Desea configurar algunas opciones en el dispositivo?</span><span class="sxs-lookup"><span data-stu-id="02f93-105">Looking to configure some of the settings on your device?</span></span> <span data-ttu-id="02f93-106">Las siguientes herramientas están disponibles a su disposición.</span><span class="sxs-lookup"><span data-stu-id="02f93-106">The below tools are available at your disposal.</span></span> <span data-ttu-id="02f93-107">Use PowerShell para ejecutar estos comandos después [de conectarse al dispositivo](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="02f93-107">Use PowerShell to run these commands after [connecting to your device](../connect-your-device/PowerShell.md).</span></span>

> [!NOTE]
> <span data-ttu-id="02f93-108">Estas herramientas no están precargadas; deberá incluir los identificadores de características correspondientes para obtener estas herramientas en la imagen.</span><span class="sxs-lookup"><span data-stu-id="02f93-108">These tools are not pre-loaded - you will need to include appropriate feature IDs to get these tools in the image.</span></span>

## <a name="iot-core-specific-command-line-utils"></a><span data-ttu-id="02f93-109">Utilidades de la línea de comandos específicas de IoT Core</span><span class="sxs-lookup"><span data-stu-id="02f93-109">IoT Core-specific Command Line Utils</span></span>

### <a name="setting-startup-app"></a><span data-ttu-id="02f93-110">**Configuración de la aplicación de Inicio:**</span><span class="sxs-lookup"><span data-stu-id="02f93-110">**Setting startup app:**</span></span>
<span data-ttu-id="02f93-111">Use el editor de inicio para configurar aplicaciones de inicio en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="02f93-111">Use the startup editor to configure startup apps on your Windows IoT Core device.</span></span> <span data-ttu-id="02f93-112">Ejecute `IotStartup` con cualquiera de las siguientes opciones:</span><span class="sxs-lookup"><span data-stu-id="02f93-112">Run `IotStartup` with any of the following options:</span></span>

* <span data-ttu-id="02f93-113">`IotStartup list` muestra las aplicaciones instaladas</span><span class="sxs-lookup"><span data-stu-id="02f93-113">`IotStartup list` lists installed applications</span></span>
* <span data-ttu-id="02f93-114">`IotStartup list headed` muestra las aplicaciones instaladas</span><span class="sxs-lookup"><span data-stu-id="02f93-114">`IotStartup list headed` lists installed headed applications</span></span>
* <span data-ttu-id="02f93-115">`IotStartup list headless` muestra las aplicaciones desatendidas instaladas</span><span class="sxs-lookup"><span data-stu-id="02f93-115">`IotStartup list headless` lists installed headless applications</span></span>
* <span data-ttu-id="02f93-116">`IotStartup list [MyApp]` enumerar las aplicaciones instaladas que coinciden con el patrón `MyApp`</span><span class="sxs-lookup"><span data-stu-id="02f93-116">`IotStartup list [MyApp]` list installed applications that match pattern `MyApp`</span></span>
* <span data-ttu-id="02f93-117">`IotStartup add` agrega aplicaciones con encabezado y sin periféricos</span><span class="sxs-lookup"><span data-stu-id="02f93-117">`IotStartup add` adds headed and headless applications</span></span>
* <span data-ttu-id="02f93-118">`IotStartup add headed [MyApp]` agrega aplicaciones de encabezado que coinciden con `MyApp`de patrón.</span><span class="sxs-lookup"><span data-stu-id="02f93-118">`IotStartup add headed [MyApp]` adds headed applications that match pattern `MyApp`.</span></span>  <span data-ttu-id="02f93-119">El patrón solo debe coincidir con una aplicación.</span><span class="sxs-lookup"><span data-stu-id="02f93-119">Pattern must match only one application.</span></span>
* <span data-ttu-id="02f93-120">`IotStartup add headless [Task1]` agrega aplicaciones desatendidas que coinciden con el patrón `Task1`</span><span class="sxs-lookup"><span data-stu-id="02f93-120">`IotStartup add headless [Task1]` adds headless applications that match pattern `Task1`</span></span>
* <span data-ttu-id="02f93-121">`IotStartup remove` quita las aplicaciones de encabezado y sin periféricos</span><span class="sxs-lookup"><span data-stu-id="02f93-121">`IotStartup remove` removes headed and headless applications</span></span>
* <span data-ttu-id="02f93-122">`IotStartup remove headed [MyApp]` quita las aplicaciones que coinciden con el patrón `MyApp`</span><span class="sxs-lookup"><span data-stu-id="02f93-122">`IotStartup remove headed [MyApp]` removes headed applications that match pattern `MyApp`</span></span>
* <span data-ttu-id="02f93-123">`IotStartup remove headless [Task1]` quita las aplicaciones desatendidas que coinciden con el patrón `Task1`</span><span class="sxs-lookup"><span data-stu-id="02f93-123">`IotStartup remove headless [Task1]` removes headless applications that match pattern `Task1`</span></span>
* <span data-ttu-id="02f93-124">`IotStartup startup` enumera las aplicaciones con encabezado y sin periféricos registradas para el inicio</span><span class="sxs-lookup"><span data-stu-id="02f93-124">`IotStartup startup` lists headed and headless applications registered for startup</span></span>
* <span data-ttu-id="02f93-125">`IotStartup startup [MyApp]` enumera las aplicaciones con encabezado y sin periféricos registradas para el inicio que coinciden con el patrón `MyApp`</span><span class="sxs-lookup"><span data-stu-id="02f93-125">`IotStartup startup [MyApp]` lists headed and headless applications registered for startup that match pattern `MyApp`</span></span>
* <span data-ttu-id="02f93-126">`IotStartup startup headed [MyApp]` enumera las aplicaciones registradas para el inicio que coinciden `MyApp`</span><span class="sxs-lookup"><span data-stu-id="02f93-126">`IotStartup startup headed [MyApp]` lists headed applications registered for startup that match `MyApp`</span></span>
* <span data-ttu-id="02f93-127">`IotStartup startup headless [Task1]` muestra las aplicaciones desatendidas registradas para el inicio que coinciden `Task1`</span><span class="sxs-lookup"><span data-stu-id="02f93-127">`IotStartup startup headless [Task1]` lists headless applications registered for startup that match `Task1`</span></span>
* <span data-ttu-id="02f93-128">`IotStartup run [MyApp]` iniciar la aplicación identificada por `MyApp`</span><span class="sxs-lookup"><span data-stu-id="02f93-128">`IotStartup run [MyApp]` start app identified by `MyApp`</span></span>
* <span data-ttu-id="02f93-129">`IotStartup stop [MyApp]` detener la aplicación identificada por `MyApp`</span><span class="sxs-lookup"><span data-stu-id="02f93-129">`IotStartup stop [MyApp]` stop app identified by `MyApp`</span></span>
* <span data-ttu-id="02f93-130">Para obtener más ayuda, pruebe `IotStartup help`</span><span class="sxs-lookup"><span data-stu-id="02f93-130">For further help, try `IotStartup help`</span></span>

### <a name="change-settings-for-region-and-user-or-speech-language"></a><span data-ttu-id="02f93-131">**Cambiar la configuración de la región y el idioma del usuario o de la voz:**</span><span class="sxs-lookup"><span data-stu-id="02f93-131">**Change settings for region and user or speech language:**</span></span>

<span data-ttu-id="02f93-132">La herramienta `IoTSettings` cambia la región, el idioma del usuario o el idioma de la voz.</span><span class="sxs-lookup"><span data-stu-id="02f93-132">The `IoTSettings` tool changes region, user language or speech language.</span></span> <span data-ttu-id="02f93-133">Se trata de una herramienta de línea de comandos que se puede invocar desde una aplicación mediante la API de ProcessLauncher.</span><span class="sxs-lookup"><span data-stu-id="02f93-133">This is a command line tool that can be invoked from an application using the ProcessLauncher API.</span></span> <span data-ttu-id="02f93-134">Estos comandos se deben ejecutar como cuenta predeterminada, no como administrador.</span><span class="sxs-lookup"><span data-stu-id="02f93-134">These commands must be run as default account, not administrator.</span></span>

* <span data-ttu-id="02f93-135">`IotSettings del account {all | username}` elimina todas las cuentas de MSA o AAD en el sistema o en una cuenta específica.</span><span class="sxs-lookup"><span data-stu-id="02f93-135">`IotSettings del account {all | username}` deletes all MSA or AAD accounts on the system or a specific account.</span></span>  <span data-ttu-id="02f93-136">Las cuentas específicas tienen el formato username@provider.com</span><span class="sxs-lookup"><span data-stu-id="02f93-136">Specific accounts take the form username@provider.com</span></span>
* <span data-ttu-id="02f93-137">`IotSettings del diagnostics` elimina la información de diagnóstico en la nube para el dispositivo actual.</span><span class="sxs-lookup"><span data-stu-id="02f93-137">`IotSettings del diagnostics` deletes diagnostic information in the cloud for the current device.</span></span>  <span data-ttu-id="02f93-138">Tenga en cuenta que esto quita el historial hasta el momento de la invocación.</span><span class="sxs-lookup"><span data-stu-id="02f93-138">Note that this removes the history up to the time of invocation.</span></span>  <span data-ttu-id="02f93-139">Se seguirá registrando la nueva información de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="02f93-139">New diagnostics information will continue to be logged.</span></span>
* <span data-ttu-id="02f93-140">en `IotSettings list account` se enumeran todas las cuentas de MSA o AAD que han iniciado sesión en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="02f93-140">`IotSettings list account` lists all MSA or AAD accounts that have been signed into the device.</span></span>
* <span data-ttu-id="02f93-141">`IotSettings list uilanguage` enumera todos los idiomas de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="02f93-141">`IotSettings list uilanguage` lists all UI languages</span></span>
* <span data-ttu-id="02f93-142">`IotSettings list speechlanguage` enumera todos los lenguajes de voz</span><span class="sxs-lookup"><span data-stu-id="02f93-142">`IotSettings list speechlanguage` lists all speech languages</span></span>
* <span data-ttu-id="02f93-143">`IotSettings get uilanguage` muestra el idioma actual de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="02f93-143">`IotSettings get uilanguage` displays current UI language</span></span>
* <span data-ttu-id="02f93-144">`IotSettings get speechlanguage` muestra el idioma actual de la voz</span><span class="sxs-lookup"><span data-stu-id="02f93-144">`IotSettings get speechlanguage` displays current speech language</span></span>
* <span data-ttu-id="02f93-145">`IotSettings get region` muestra la región actual</span><span class="sxs-lookup"><span data-stu-id="02f93-145">`IotSettings get region` displays current region</span></span>
* <span data-ttu-id="02f93-146">`IotSettings set uilanguage language\_tag - (e.g. fr-CA)` establece el idioma de interfaz de usuario predeterminado francés canadiense)</span><span class="sxs-lookup"><span data-stu-id="02f93-146">`IotSettings set uilanguage language\_tag - (e.g. fr-CA)` sets default UI language French Canadian)</span></span>
* <span data-ttu-id="02f93-147">`IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` establece el idioma de voz francés canadiense)</span><span class="sxs-lookup"><span data-stu-id="02f93-147">`IotSettings set speechlanguage language\_tag - (e.g. fr-CA)` sets speech language French Canadian)</span></span>
* <span data-ttu-id="02f93-148">`IotSettings set region region\_code - (e.g. CA)` establece la región predeterminada en Canadá)</span><span class="sxs-lookup"><span data-stu-id="02f93-148">`IotSettings set region region\_code - (e.g. CA)` sets default region to Canada)</span></span>
* <span data-ttu-id="02f93-149">`IotSettings set bluetoothpref {sink | source}` especifica la preferencia de rol de Bluetooth que se debe seleccionar cuando los dispositivos compilados con las características de IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK se conectan a otro dispositivo que también admite ambos roles.</span><span class="sxs-lookup"><span data-stu-id="02f93-149">`IotSettings set bluetoothpref {sink | source}` Specifies the Bluetooth role preference to select when devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK features connect to another device that also supports both roles.</span></span>
* <span data-ttu-id="02f93-150">`IotSettings get bluetoothpref` devuelve la preferencia de rol de Bluetooth actual para dispositivos compilados con IOT_BLUETOOTH_A2DP_SOURCE y IOT_BLUETOOTH_A2DP_SINK.</span><span class="sxs-lookup"><span data-stu-id="02f93-150">`IotSettings get bluetoothpref` returns the current Bluetooth role preference for devices built with both IOT_BLUETOOTH_A2DP_SOURCE and IOT_BLUETOOTH_A2DP_SINK.</span></span>  <span data-ttu-id="02f93-151">El valor predeterminado es Source.</span><span class="sxs-lookup"><span data-stu-id="02f93-151">The default is source.</span></span>

> [!TIP]
> <span data-ttu-id="02f93-152">`IoTSettings -list uiLanguage` devolverá la lista de idioma de interfaz de usuario admitido (en la versión de la imagen de Windows IoT Core con la que se ha ejecutado).</span><span class="sxs-lookup"><span data-stu-id="02f93-152">`IoTSettings -list uiLanguage` will give back the list of supported UI language (in the version of Windows IoT core image it has been executed against)</span></span>
    
### <a name="change-default-audio-device-and-volume"></a><span data-ttu-id="02f93-153">**Cambiar el dispositivo de audio y el volumen predeterminados:**</span><span class="sxs-lookup"><span data-stu-id="02f93-153">**Change default audio device and volume:**</span></span>

<span data-ttu-id="02f93-154">La herramienta `IoTCoreAudioControlTool` controla las opciones relacionadas con el audio, como establecer los dispositivos de captura y reproducción predeterminados y cambiar el volumen.</span><span class="sxs-lookup"><span data-stu-id="02f93-154">The `IoTCoreAudioControlTool` tool controls audio related options, such as setting default capture and playback devices and changing the volume.</span></span> <span data-ttu-id="02f93-155">Para obtener una lista completa de parámetros, ejecute `IoTCoreAudioControlTool h`.</span><span class="sxs-lookup"><span data-stu-id="02f93-155">For a full list of parameters, run `IoTCoreAudioControlTool h`.</span></span>

### <a name="manually-installing-appx-files"></a><span data-ttu-id="02f93-156">**Instalación manual. Archivos APPX:**</span><span class="sxs-lookup"><span data-stu-id="02f93-156">**Manually installing .APPX files:**</span></span>
<span data-ttu-id="02f93-157">DeployAppx permite instalar y quitar en. Paquetes APPX en escenarios de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="02f93-157">DeployAppx enables installing, and removing in .APPX packages in development scenarios.</span></span>  <span data-ttu-id="02f93-158">El método correcto para instalar. Los paquetes APPX en imágenes de producción usan un paquete de aprovisionamiento, tal como se documenta en el tema [instalación de la aplicación](https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) .</span><span class="sxs-lookup"><span data-stu-id="02f93-158">The correct method for installing .APPX packages in production images is to use a provisioning package as documented in the [Install your app](https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller#using-provisioning-package-from-wcd) subject.</span></span>  <span data-ttu-id="02f93-159">DeployAppx también admite la consulta. Información del paquete APPX.</span><span class="sxs-lookup"><span data-stu-id="02f93-159">DeployAppx also supports querying .APPX package information.</span></span>

*  <span data-ttu-id="02f93-160">`DeployAppx install MyApp.appx` instala. APPX y el certificado del mismo nombre si se encuentra.</span><span class="sxs-lookup"><span data-stu-id="02f93-160">`DeployAppx install MyApp.appx` installs the .APPX and the certificate of the same name if found.</span></span>
* <span data-ttu-id="02f93-161">`DeployAppx install force MyApp.appx` fuerza la desinstalación de la instalada actualmente. APPX con el mismo nombre de paquete si se encuentra antes de instalar el nuevo. APPX.</span><span class="sxs-lookup"><span data-stu-id="02f93-161">`DeployAppx install force MyApp.appx` forces uninstalling the currently installed .APPX with the same package name if found before installing the new .APPX.</span></span>  <span data-ttu-id="02f93-162">Esto resulta útil para instalar un. APPX con el mismo número de versión o inferior que el instalado actualmente. APPX.</span><span class="sxs-lookup"><span data-stu-id="02f93-162">This is useful for installing an .APPX with the same or lower version number as the currently installed .APPX.</span></span>
* <span data-ttu-id="02f93-163">`DeployAppx install retry MyApp.appx` reintentar la instalación del. APPX 10 veces en caso de error con un retraso de 2 segundos entre intentos.</span><span class="sxs-lookup"><span data-stu-id="02f93-163">`DeployAppx install retry MyApp.appx` retry installing the .APPX 10 times on failure with 2 second delay between attempts.</span></span>
* <span data-ttu-id="02f93-164">`DeployAppx uninstall App_1.0.1.0_x86__publisherid123` desinstalar el. appx con el nombre completo del paquete coincidente.</span><span class="sxs-lookup"><span data-stu-id="02f93-164">`DeployAppx uninstall App_1.0.1.0_x86__publisherid123` uninstall the .appx with the matching package full name.</span></span>
*  <span data-ttu-id="02f93-165">`DeployAppx uninstall MyApp.appx` desinstalar cualquier instalado. APPX con un nombre de familia de paquete coincidente.</span><span class="sxs-lookup"><span data-stu-id="02f93-165">`DeployAppx uninstall MyApp.appx` uninstall any installed .APPX with a matching package family name.</span></span>
* <span data-ttu-id="02f93-166">en `DeployAppx getpackages` se enumeran los nombres completos del paquete instalado.</span><span class="sxs-lookup"><span data-stu-id="02f93-166">`DeployAppx getpackages` lists installed package full names.</span></span>
* <span data-ttu-id="02f93-167">`DeployAppx getpackageid IotCoreDefaultApp.appx` imprime el nombre del paquete, el nombre de la familia del paquete y el nombre completo del paquete para. APPX.</span><span class="sxs-lookup"><span data-stu-id="02f93-167">`DeployAppx getpackageid IotCoreDefaultApp.appx` prints out the package name, the package family name, and the package full name for the .APPX.</span></span>
```cmd
DeployAppx getpackageid IotCoreDefaultApp.appx
         Package Name: 16454Windows10IOTCore.IOTCoreDefaultApplication
  Package Family Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58
    Package Full Name: 16454Windows10IOTCore.IOTCoreDefaultApplication_2.0.8.0_arm__rz84sjny4rf58
```
* <span data-ttu-id="02f93-168">`DeployAppx register appxmanifest.xml` no compatible</span><span class="sxs-lookup"><span data-stu-id="02f93-168">`DeployAppx register appxmanifest.xml` unsupported</span></span>


## <a name="general-command-line-utils"></a><span data-ttu-id="02f93-169">Utilidades generales de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="02f93-169">General Command Line Utils</span></span>

### <a name="update-account-password"></a><span data-ttu-id="02f93-170">**Actualizar contraseña de la cuenta:**</span><span class="sxs-lookup"><span data-stu-id="02f93-170">**Update account password:**</span></span>

<span data-ttu-id="02f93-171">Se recomienda encarecidamente que actualice la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="02f93-171">It is highly recommended that you update the default password for the Administrator account.</span></span> <span data-ttu-id="02f93-172">Para ello, puede emitir el comando siguiente: `net user Administrator [new password]` donde `[new password]` representa una contraseña segura de su elección.</span><span class="sxs-lookup"><span data-stu-id="02f93-172">To do this, you can issue the following command: `net user Administrator [new password]` where `[new password]` represents a strong password of your choice.</span></span>

### <a name="create-local-user-accounts"></a><span data-ttu-id="02f93-173">**Crear cuentas de usuario locales:**</span><span class="sxs-lookup"><span data-stu-id="02f93-173">**Create local user accounts:**</span></span>

<span data-ttu-id="02f93-174">Si desea conceder a otros usuarios acceso a su dispositivo Windows IoT Core, puede crear cuentas de usuario locales adicionales mediante PS escribiendo `net user [username] [password] /add`.</span><span class="sxs-lookup"><span data-stu-id="02f93-174">If you wish to give others access to your Windows IoT Core device, you can create additional local user accounts using PS by typing in `net user [username] [password] /add`.</span></span> <span data-ttu-id="02f93-175">Si desea agregar este usuario a otros grupos, como el grupo de administradores, use `net localgroup Administrators [username] /add`.</span><span class="sxs-lookup"><span data-stu-id="02f93-175">If you wish to add this user to other groups, such as the Administrator group, use `net localgroup Administrators [username] /add`.</span></span>

### <a name="set-password"></a><span data-ttu-id="02f93-176">**Establecer contraseña:**</span><span class="sxs-lookup"><span data-stu-id="02f93-176">**Set password:**</span></span>

<span data-ttu-id="02f93-177">Para cambiar la contraseña en una cuenta del dispositivo, ejecute `net user [account-username] [new-password]` para cambiar la contraseña de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="02f93-177">To change the password on an account on your device, run `net user [account-username] [new-password]` to change the account password.</span></span>

### <a name="query-and-set-device-name"></a><span data-ttu-id="02f93-178">**Consultar y establecer el nombre del dispositivo:**</span><span class="sxs-lookup"><span data-stu-id="02f93-178">**Query and set device name:**</span></span>

<span data-ttu-id="02f93-179">Para identificar el nombre de dispositivo actual, simplemente escriba `hostname`.</span><span class="sxs-lookup"><span data-stu-id="02f93-179">To identify your current device name, simply type `hostname`.</span></span> <span data-ttu-id="02f93-180">Para cambiar el nombre del dispositivo Windows IoT Core, escriba `SetComputerName [new machinename]`.</span><span class="sxs-lookup"><span data-stu-id="02f93-180">To change the name of your Windows IoT Core device, type `SetComputerName [new machinename]`.</span></span> <span data-ttu-id="02f93-181">Es posible que tenga que reiniciar el dispositivo para que el cambio de nombre surta efecto.</span><span class="sxs-lookup"><span data-stu-id="02f93-181">You may need to restart your device for the name change to take effect.</span></span>

### <a name="basic-network-configuration"></a><span data-ttu-id="02f93-182">**Configuración de red básica:**</span><span class="sxs-lookup"><span data-stu-id="02f93-182">**Basic network configuration:**</span></span>

<span data-ttu-id="02f93-183">Muchas de las utilidades básicas de configuración de red con las que es posible que ya esté familiarizado están disponibles en Windows IoT Core, incluidos comandos como `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`y `arp.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-183">Many of the basic network configuration utilities you may already be familiar with are available in Windows IoT Core, including commands such as `ping.exe`, `netstat.exe`, `netsh.exe`, `ipconfig.exe`, `tracert.exe`, and `arp.exe`.</span></span>

### <a name="copy-utilities"></a><span data-ttu-id="02f93-184">**Copiar Utilidades:**</span><span class="sxs-lookup"><span data-stu-id="02f93-184">**Copy utilities:**</span></span>

<span data-ttu-id="02f93-185">Microsoft proporciona herramientas que ya conoce, como `sfpcopy.exe`, así como `xcopy.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-185">Microsoft is providing familiar tools, including `sfpcopy.exe` as well as `xcopy.exe`.</span></span>

### <a name="process-management"></a><span data-ttu-id="02f93-186">**Administración de procesos:**</span><span class="sxs-lookup"><span data-stu-id="02f93-186">**Process Management:**</span></span>

<span data-ttu-id="02f93-187">Para ver los procesos que se están ejecutando actualmente, puede intentar `get-process` o, como alternativa, `tlist.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-187">To view currently running processes, you can try either `get-process` or alternatively `tlist.exe`.</span></span> <span data-ttu-id="02f93-188">Para detener un proceso en ejecución, escriba `kill.exe [pid or process name]`.</span><span class="sxs-lookup"><span data-stu-id="02f93-188">To stop a running process, type `kill.exe [pid or process name]`.</span></span>


### <a name="set-boot-option-headless-vs-headed-boot"></a><span data-ttu-id="02f93-189">**Configuración de la opción de arranque (Inicio frente a Inicio de la cabeza):**</span><span class="sxs-lookup"><span data-stu-id="02f93-189">**Set Boot Option (Headless vs. headed boot):**</span></span>

<span data-ttu-id="02f93-190">Los dispositivos Windows IoT Core pueden establecerse en la punta (cuando se requieren capacidades de visualización) o sin periféricos (cuando una pantalla no es necesaria o disponible) modo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="02f93-190">Windows IoT Core devices can be set to headed (when display capabilities are required) or headless (when a display is not required or available) device mode.</span></span> <span data-ttu-id="02f93-191">Para cambiar esta configuración, use `setbootoption.exe [headed | headless]`.</span><span class="sxs-lookup"><span data-stu-id="02f93-191">To change this setting, use `setbootoption.exe [headed | headless]`.</span></span>

> [!NOTE]
> <span data-ttu-id="02f93-192">El cambio de esta configuración requerirá un reinicio para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="02f93-192">Changing this setting will require a reboot in order for the change to take effect.</span></span>

### <a name="task-scheduler"></a><span data-ttu-id="02f93-193">**Programador de tareas:**</span><span class="sxs-lookup"><span data-stu-id="02f93-193">**Task scheduler:**</span></span>

<span data-ttu-id="02f93-194">Para ver la lista actual de tareas programadas, use el comando `schtasks.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-194">To view the current list of scheduled tasks, use the `schtasks.exe` command.</span></span> <span data-ttu-id="02f93-195">Puede crear tareas nuevas con el `/create` modificador o ejecutar tareas a petición con el conmutador `/run`.</span><span class="sxs-lookup"><span data-stu-id="02f93-195">You can create new tasks with the `/create` switch or run on-demand tasks with the `/run` switch.</span></span> <span data-ttu-id="02f93-196">Para obtener una lista completa de los parámetros admitidos, use `schtasks.exe /?`</span><span class="sxs-lookup"><span data-stu-id="02f93-196">For a full list of supported parameters, use `schtasks.exe /?`</span></span>

### <a name="device-drivers"></a><span data-ttu-id="02f93-197">**Controladores de dispositivos:**</span><span class="sxs-lookup"><span data-stu-id="02f93-197">**Device drivers:**</span></span>

<span data-ttu-id="02f93-198">La utilidad de la consola del dispositivo es útil para identificar y administrar los dispositivos y controladores instalados.</span><span class="sxs-lookup"><span data-stu-id="02f93-198">The device console utility is useful in identifying and managing installed devices and drivers.</span></span> <span data-ttu-id="02f93-199">Para obtener una lista completa de parámetros, use `devcon.exe /?`</span><span class="sxs-lookup"><span data-stu-id="02f93-199">For a full list of parameters, use `devcon.exe /?`</span></span>

### <a name="registry-access"></a><span data-ttu-id="02f93-200">**Acceso al registro:**</span><span class="sxs-lookup"><span data-stu-id="02f93-200">**Registry Access:**</span></span>

<span data-ttu-id="02f93-201">Si necesita tener acceso al registro para ver o modificar la configuración, use el comando `reg.exe /?` para obtener la lista completa de parámetros admitidos.</span><span class="sxs-lookup"><span data-stu-id="02f93-201">If you need to access the registry to view or modify settings, use the `reg.exe /?` Command for the full list of supported parameters.</span></span>

### <a name="services"></a><span data-ttu-id="02f93-202">**Servicios:**</span><span class="sxs-lookup"><span data-stu-id="02f93-202">**Services:**</span></span>

<span data-ttu-id="02f93-203">La administración de servicios de Windows se puede realizar a través del comando `net.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-203">Managing Windows services can be accomplished via the `net.exe` command.</span></span> <span data-ttu-id="02f93-204">Para ver una lista de los servicios en ejecución, escriba `net start`.</span><span class="sxs-lookup"><span data-stu-id="02f93-204">To see a list of running services, type `net start`.</span></span> <span data-ttu-id="02f93-205">Para iniciar o detener un servicio específico, escriba `net [start | stop] [service name]`.</span><span class="sxs-lookup"><span data-stu-id="02f93-205">To start or stop a specific service, type `net [start | stop] [service name]`.</span></span> <span data-ttu-id="02f93-206">También puede usar el administrador de control de servicios a través de `sc.exe` comando.</span><span class="sxs-lookup"><span data-stu-id="02f93-206">Alternatively, you can also use the service control manager via `sc.exe` command.</span></span>

### <a name="boot-configuration"></a><span data-ttu-id="02f93-207">**Configuración de arranque:**</span><span class="sxs-lookup"><span data-stu-id="02f93-207">**Boot configuration:**</span></span>

<span data-ttu-id="02f93-208">Puede realizar cambios en la configuración de arranque del dispositivo Windows IoT Core mediante `bcdedit.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-208">You can make changes to the boot configuration of your Windows IoT Core device by using `bcdedit.exe`.</span></span> <span data-ttu-id="02f93-209">Por ejemplo, puede habilitar testsigning con `bcdedit –set testsigning on` comando.</span><span class="sxs-lookup"><span data-stu-id="02f93-209">For instance, you can enable testsigning with `bcdedit –set testsigning on` command.</span></span>

### <a name="shutdownrestart-device"></a><span data-ttu-id="02f93-210">**Apagar o reiniciar el dispositivo:**</span><span class="sxs-lookup"><span data-stu-id="02f93-210">**Shutdown/restart device:**</span></span>

<span data-ttu-id="02f93-211">Para apagar el dispositivo, escriba `shutdown /s /t 0`.</span><span class="sxs-lookup"><span data-stu-id="02f93-211">To shut down your device, type `shutdown /s /t 0`.</span></span> <span data-ttu-id="02f93-212">Para reiniciar el dispositivo, utilice el modificador `/r` en su lugar con el `shutdown /r /t 0`de comandos.</span><span class="sxs-lookup"><span data-stu-id="02f93-212">To restart the device, use the `/r` switch instead with the command `shutdown /r /t 0`.</span></span>

### <a name="viewing-and-changing-display-settings"></a><span data-ttu-id="02f93-213">**Ver y cambiar la configuración de pantalla**</span><span class="sxs-lookup"><span data-stu-id="02f93-213">**Viewing and changing display settings**</span></span>
<span data-ttu-id="02f93-214">La herramienta SetDisplayResolution se puede usar para enumerar la configuración de pantalla actual y para mostrar la lista de valores admitidos.</span><span class="sxs-lookup"><span data-stu-id="02f93-214">The SetDisplayResolution tool may be used for listing the current display settings and to show the list of supported values.</span></span>  <span data-ttu-id="02f93-215">Se puede usar para ajustar la resolución, la frecuencia de actualización y la orientación de la pantalla a los valores admitidos por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="02f93-215">It can further be used for adjusting the display's resolution, refresh rate and/or orientation to values supported by your platform.</span></span>  <span data-ttu-id="02f93-216">La utilidad acepta los siguientes argumentos de la línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="02f93-216">The utility accepts the following command line arguments:</span></span>

* <span data-ttu-id="02f93-217">`SetDisplayResolution` muestra el resoltuion de presentación actual.</span><span class="sxs-lookup"><span data-stu-id="02f93-217">`SetDisplayResolution` Lists the current display resoltuion.</span></span>
* <span data-ttu-id="02f93-218">`SetDisplayResolution -list` muestra las resoluciones de pantalla compatibles.</span><span class="sxs-lookup"><span data-stu-id="02f93-218">`SetDisplayResolution -list` Lists supported display resolutions.</span></span>
* <span data-ttu-id="02f93-219">`SetDisplayResolution -orientation:[n]` cambiar la orientación de la pantalla, donde n = 0, 90180 o 270.</span><span class="sxs-lookup"><span data-stu-id="02f93-219">`SetDisplayResolution -orientation:[n]` Change the display orientation, where n=0,90,180 or 270.</span></span>
* <span data-ttu-id="02f93-220">`SetDisplayResolution [width] [height]` cambiar el ancho y el alto en píxeles</span><span class="sxs-lookup"><span data-stu-id="02f93-220">`SetDisplayResolution [width] [height]` Change the width and height in pixels</span></span> 
* <span data-ttu-id="02f93-221">`SetDisplayResolution [width] [height] [refreshrate]` cambiar el ancho, el alto y la frecuencia de actualización, donde el ancho y el alto se encuentran en píxeles y en un máximo de Hz</span><span class="sxs-lookup"><span data-stu-id="02f93-221">`SetDisplayResolution [width] [height] [refreshrate]` Change width, height and refresh rate where width and height are in pixels and refreshrate in Hz</span></span> 
* <span data-ttu-id="02f93-222">`SetDisplayResolution [width] [height] [refreshrate] [orientation]` cambiar el ancho, el alto, el valor de frecuencia y la orientación de la pantalla donde el ancho y el alto se encuentran en píxeles, el valor máximo en Hz y la orientación es uno de 0, 90, 180 o 270.</span><span class="sxs-lookup"><span data-stu-id="02f93-222">`SetDisplayResolution [width] [height] [refreshrate] [orientation]` Change width, height, refreshrate and screen orientation where width and height are in pixels, refreshrate in Hz and orientation is one of 0, 90, 180 or 270.</span></span>

### <a name="take-screenshot"></a><span data-ttu-id="02f93-223">**Captura de pantalla:**</span><span class="sxs-lookup"><span data-stu-id="02f93-223">**Take screenshot:**</span></span>

<span data-ttu-id="02f93-224">Puede realizar la captura de pantalla de su dispositivo IoTCore de Windows mediante `ScreenCapture.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f93-224">You can take the screenshot of your Windows IoTCore device by using `ScreenCapture.exe`.</span></span> <span data-ttu-id="02f93-225">Por ejemplo, ejecute `ScreenCapture c:\folder\screencap.jpg` llevará a cabo la captura de pantalla y la guardará en el archivo captura. jpg.</span><span class="sxs-lookup"><span data-stu-id="02f93-225">For example, run `ScreenCapture c:\folder\screencap.jpg` will take the screenshot and save it in screencap.jpg file.</span></span>

### <a name="get-information-about-network-adapters"></a><span data-ttu-id="02f93-226">**Obtener información acerca de los adaptadores de red:**</span><span class="sxs-lookup"><span data-stu-id="02f93-226">**Get information about Network Adapters:**</span></span>

<span data-ttu-id="02f93-227">Para ver la lista de todos los adaptadores de red disponibles, ejecute `GetAdapterInfo` herramienta.</span><span class="sxs-lookup"><span data-stu-id="02f93-227">To view the list of all the available network adapters, run `GetAdapterInfo` tool.</span></span>

### <a name="set-folder-permissions-for-uwp-apps"></a><span data-ttu-id="02f93-228">**Establecer permisos de carpeta para aplicaciones UWP:**</span><span class="sxs-lookup"><span data-stu-id="02f93-228">**Set folder permissions for UWP apps:**</span></span>

<span data-ttu-id="02f93-229">No todas las carpetas de su dispositivo son accesible para aplicaciones universales de Windows.</span><span class="sxs-lookup"><span data-stu-id="02f93-229">Not all folders on your device are accesible by Universal Windows Apps.</span></span> <span data-ttu-id="02f93-230">Para hacer que una carpeta sea accesible para una aplicación para UWP, puede usar `FolderPermissions` herramienta.</span><span class="sxs-lookup"><span data-stu-id="02f93-230">To make a folder accesible to a UWP app, you can use `FolderPermissions` tool.</span></span> <span data-ttu-id="02f93-231">Por ejemplo, ejecute `FolderPermissions c:\test -e` para proporcionar a las aplicaciones para UWP acceso a `c:\test` carpeta.</span><span class="sxs-lookup"><span data-stu-id="02f93-231">For example run `FolderPermissions c:\test -e` to give UWP apps access to `c:\test` folder.</span></span> <span data-ttu-id="02f93-232">Tenga en cuenta que esto solo funcionará con las API de Win32 nativas, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="02f93-232">Note this will work only with native Win32 apis for eg.</span></span> <span data-ttu-id="02f93-233">CreateFile2 y no con las API de WinRT como StorageFolder, StorageFile, etc.</span><span class="sxs-lookup"><span data-stu-id="02f93-233">CreateFile2 and not with WinRT apis like StorageFolder, StorageFile etc.</span></span>

### <a name="work-with-serial-ports"></a><span data-ttu-id="02f93-234">**Trabajar con puertos serie:**</span><span class="sxs-lookup"><span data-stu-id="02f93-234">**Work with Serial Ports:**</span></span>
<span data-ttu-id="02f93-235">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) permite trabajar con puertos serie desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="02f93-235">[MinComm](https://github.com/ms-iot/samples/tree/develop/MinComm) allows you to work with serial ports from the command line.</span></span> <span data-ttu-id="02f93-236">Se proporciona como un proyecto de ejemplo en el repositorio de ejemplos de MS-iot.</span><span class="sxs-lookup"><span data-stu-id="02f93-236">It is provided as a sample project in the ms-iot samples repo.</span></span> 

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


