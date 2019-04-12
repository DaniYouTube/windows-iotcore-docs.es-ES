---
title: Uso de PowerShell para Windows IoT
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar PowerShell para conectarse al dispositivo, así como para administrar el dispositivo.
keywords: Windows iot, PowerShell, Windows PowerShell, línea de comandos, el shell de línea de comandos
ms.openlocfilehash: 1519fb9dd61a8d6521757fdd97999f03b74afa7d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515066"
---
# <a name="using-powershell-for-windows-iot"></a><span data-ttu-id="39272-104">Uso de PowerShell para Windows IoT</span><span class="sxs-lookup"><span data-stu-id="39272-104">Using PowerShell for Windows IoT</span></span>

<span data-ttu-id="39272-105">Configurar y administrar cualquier dispositivo Windows 10 IoT Core con Windows PowerShell de forma remota.</span><span class="sxs-lookup"><span data-stu-id="39272-105">Remotely configure and manage any Windows 10 IoT Core device by using Windows PowerShell.</span></span>
<span data-ttu-id="39272-106">PowerShell es un shell de línea de comandos basado en tareas y lenguaje de scripting diseñado especialmente para la administración del sistema.</span><span class="sxs-lookup"><span data-stu-id="39272-106">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span>

<span data-ttu-id="39272-107">Asegúrese de seguir estos pasos para configurar correctamente un dispositivo que ejecuta Windows 10 IoT Core para funcionar bien con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="39272-107">Make sure to follow these steps to correctly configure your device running Windows 10 IoT Core to work well with Visual Studio 2017.</span></span>

## <a name="initiating-a-powershell-session"></a><span data-ttu-id="39272-108">Iniciar una sesión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="39272-108">Initiating a PowerShell session</span></span>
1. <span data-ttu-id="39272-109">Para iniciar una sesión de PowerShell con el dispositivo Windows 10 IoT Core, primero deberá crear una relación de confianza entre el equipo host y el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39272-109">To start a PowerShell session with your Windows 10 IoT Core device, you'll first need to create a trust relationship between your host PC and your device.</span></span> <span data-ttu-id="39272-110">Después de iniciar el dispositivo Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39272-110">After starting your Windows IoT Core device, an IP address will be shown on the screen attached to the device.</span></span>

    ![DefaultApp en Windows 10 IoT Core](../media/PowerShell/DefaultApp.png)

   <span data-ttu-id="39272-112">Puede encontrar la misma información en el panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="39272-112">You can find the same information on the Windows 10 IoT Core Dashboard.</span></span>

2. <span data-ttu-id="39272-113">Abra una consola de PowerShell del administrador del equipo local.</span><span class="sxs-lookup"><span data-stu-id="39272-113">Open an administrator PowerShell console on your local PC.</span></span> <span data-ttu-id="39272-114">Tipo **powershell** en el **buscar en la web y Windows** cuadro situado en el menú Inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="39272-114">Type **powershell** in the **Search the web and Windows** box near the Windows Start menu.</span></span> <span data-ttu-id="39272-115">Windows encontrará PowerShell en su PC.</span><span class="sxs-lookup"><span data-stu-id="39272-115">Windows will find PowerShell on your PC.</span></span>

    ![Encontrar PowerShell](../media/PowerShell/start-ps.png)

3. <span data-ttu-id="39272-117">Para iniciar PowerShell como administrador, haga clic en **Windows PowerShell**y, a continuación, seleccione **ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="39272-117">To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>

    ![Ejecute PowerShell como administrador](../media/PowerShell/start-ps2.png)

   <span data-ttu-id="39272-119">Ahora debería ver la consola de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39272-119">Now you should see the PowerShell console.</span></span>

    ![Consola de PowerShell](../media/PowerShell/ps.PNG)

4. <span data-ttu-id="39272-121">Es posible que deba iniciar el servicio WinRM en el escritorio para habilitar conexiones remotas.</span><span class="sxs-lookup"><span data-stu-id="39272-121">You may need to start the WinRM service on your desktop to enable remote connections.</span></span> <span data-ttu-id="39272-122">Para ello, desde la consola de PowerShell, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="39272-122">To do so, from the PowerShell console, type the following command:</span></span>

        net start WinRM

5. <span data-ttu-id="39272-123">Desde la consola de PowerShell, escriba lo siguiente, sustituyendo `<machine-name or IP address>` con el valor adecuado (mediante su **nombre-equipo** es más fácil, pero si el dispositivo no tiene un nombre exclusivo en la red, pruebe la dirección IP):</span><span class="sxs-lookup"><span data-stu-id="39272-123">From the PowerShell console, type the following, substituting `<machine-name or IP address>` with the appropriate value (using your **machine-name** is the easiest, but if your device is not uniquely named on your network, try the IP address):</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. <span data-ttu-id="39272-124">Escriba `Y` para confirmar el cambio.</span><span class="sxs-lookup"><span data-stu-id="39272-124">Enter `Y` to confirm the change.</span></span>

> [!NOTE]
> <span data-ttu-id="39272-125">Si desea conectar varios dispositivos, puede utilizar comas y comillas para separar cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39272-125">If you want to connect multiple devices, you can use commas and quotation marks to separate each device.</span></span>
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. <span data-ttu-id="39272-126">Ahora puede iniciar una sesión con su dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="39272-126">Now you can start a session with your Windows IoT Core device.</span></span> <span data-ttu-id="39272-127">Desde PowerShell consola de administrador, escriba:</span><span class="sxs-lookup"><span data-stu-id="39272-127">From you administrator PowerShell console, type:</span></span>

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. <span data-ttu-id="39272-128">En el cuadro de diálogo de credenciales, escriba la contraseña predeterminada siguiente:</span><span class="sxs-lookup"><span data-stu-id="39272-128">In the credential dialog, enter the following default password:</span></span> `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span data-ttu-id="39272-129"><span class="win-icon win-icon-Page"></span> TENGA EN CUENTA</span><span class="sxs-lookup"><span data-stu-id="39272-129"><span class="win-icon win-icon-Page"></span> NOTE</span></span> </h5>
      <p><span data-ttu-id="39272-130">El proceso de conexión no es inmediato y puede tardar hasta 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="39272-130">The connection process is not immediate and can take up to 30 seconds.</span></span></p>
    </div>    
    
    <span data-ttu-id="39272-131">Si se ha conectado correctamente al dispositivo, debería ver la dirección IP del dispositivo antes del símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="39272-131">If you successfully connected to the device, you should see the IP address of your device before the prompt.</span></span>

    ![Consola de PowerShell](../media/PowerShell/ps_device.png)

9. <span data-ttu-id="39272-133">Actualizar la contraseña de cuenta.</span><span class="sxs-lookup"><span data-stu-id="39272-133">Update your account password.</span></span> <span data-ttu-id="39272-134">Nos *recomienda* que actualizar la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="39272-134">We *highly recommend* that you update the default password for the Administrator account.</span></span> <span data-ttu-id="39272-135">Para ello, emita los siguientes comandos en la conexión de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="39272-135">To do this, issue the following commands in your PowerShell connection:</span></span>

    <span data-ttu-id="39272-136">a.</span><span class="sxs-lookup"><span data-stu-id="39272-136">a.</span></span> <span data-ttu-id="39272-137">Reemplace `[new password]` con una contraseña segura:</span><span class="sxs-lookup"><span data-stu-id="39272-137">Replace `[new password]` with a strong password:</span></span>
    
            net user Administrator [new password]
            
    <span data-ttu-id="39272-138">b.</span><span class="sxs-lookup"><span data-stu-id="39272-138">b.</span></span> <span data-ttu-id="39272-139">A continuación, establecer una nueva sesión de PowerShell con `Exit-PSSession` y `Enter-PSSession` con las nuevas credenciales.</span><span class="sxs-lookup"><span data-stu-id="39272-139">Next, establish a new PowerShell session using `Exit-PSSession` and `Enter-PSSession` with the new credentials.</span></span>
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a><span data-ttu-id="39272-140">Normalmente se usan comandos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="39272-140">Commonly used PowerShell commands</span></span>

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a><span data-ttu-id="39272-141">Solución de problemas con Visual Studio Remote Debugger</span><span class="sxs-lookup"><span data-stu-id="39272-141">Troubleshooting with Visual Studio Remote Debugger</span></span>

<span data-ttu-id="39272-142">Para poder implementar aplicaciones desde Visual Studio 2017, deberá asegurarse de que se está ejecutando Visual Studio Remote Debugger en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="39272-142">To be able to deploy applications from Visual Studio 2017, you will need to make sure that the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="39272-143">El depurador remoto debería abrirse automáticamente al iniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="39272-143">The remote debugger should open automatically when you start your computer.</span></span> <span data-ttu-id="39272-144">Para comprobar la doble, utilice el `tlist` procesa el comando para enumerar todos los de la ejecución de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39272-144">To double check, use the `tlist` command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="39272-145">Debe haber dos instancias de msvsmon.exe que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39272-145">There should be two instances of msvsmon.exe running on the device.</span></span>

<span data-ttu-id="39272-146">Es posible que el depurador remoto de Visual Studio en tiempo de espera tras un largo período de inactividad.</span><span class="sxs-lookup"><span data-stu-id="39272-146">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="39272-147">Si Visual Studio no puede conectarse a su dispositivo Windows IoT Core, pruebe a reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39272-147">If Visual Studio cannot connect to your Windows IoT Core device, try restarting the device.</span></span>

### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="39272-148">Configurar el dispositivo Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="39272-148">Configure your Windows IoT Core device</span></span>

<span data-ttu-id="39272-149">Si lo desea, puede cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="39272-149">If you want, you can rename your device.</span></span> 

1. <span data-ttu-id="39272-150">Para cambiar el nombre del equipo, use el `setcomputername` utilidad:</span><span class="sxs-lookup"><span data-stu-id="39272-150">To change the computer name, use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

2. <span data-ttu-id="39272-151">Reinicie el dispositivo para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="39272-151">Restart the device for the change to take effect.</span></span> <span data-ttu-id="39272-152">Puede usar el `shutdown` comando como sigue:</span><span class="sxs-lookup"><span data-stu-id="39272-152">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0

3. <span data-ttu-id="39272-153">Dado que se ha cambiado el nombre del equipo, después de reiniciar, tendrá que volver a ejecutar este comando para conectarse al dispositivo con el nuevo nombre:</span><span class="sxs-lookup"><span data-stu-id="39272-153">Because the computer name was changed, after you restart you will need to rerun this command to connect to your device using the new name:</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
<span data-ttu-id="39272-154">El dispositivo Windows IoT Core ahora debería estar configurado y listo para usar correctamente!</span><span class="sxs-lookup"><span data-stu-id="39272-154">Your Windows IoT Core device should now be properly configured and ready to use!</span></span>

### <a name="commonly-used-utilities"></a><span data-ttu-id="39272-155">Frecuente utilidades</span><span class="sxs-lookup"><span data-stu-id="39272-155">Commonly used utilities</span></span>

<span data-ttu-id="39272-156">Para obtener una lista de comandos y utilidades que puede usar con PowerShell, vea el [utilidades de línea de comandos](../manage-your-device/CommandLineUtils.md) página.</span><span class="sxs-lookup"><span data-stu-id="39272-156">For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page.</span></span>

## <a name="known-issues-and-workarounds"></a><span data-ttu-id="39272-157">Problemas y soluciones conocidos</span><span class="sxs-lookup"><span data-stu-id="39272-157">Known issues and workarounds</span></span>

<span data-ttu-id="39272-158">**PROBLEMA**: Un problema conocido en las directivas de seguridad de PowerShell hace que los siguientes problemas al manifiesto dentro de la sesión remota:</span><span class="sxs-lookup"><span data-stu-id="39272-158">**ISSUE**: A known bug in PowerShell security policies causes the following issues to manifest within the remote session:</span></span>
* <span data-ttu-id="39272-159">Get-Help devuelve a coincidencias inesperadas.</span><span class="sxs-lookup"><span data-stu-id="39272-159">Get-Help returns unexpected matches.</span></span>
* <span data-ttu-id="39272-160">Get-Command en un módulo especificado devuelve una lista de comandos vacía.</span><span class="sxs-lookup"><span data-stu-id="39272-160">Get-Command on a specified module returns an empty command list.</span></span>
* <span data-ttu-id="39272-161">Ejecución de un cmdlet desde cualquiera de estos módulos genera CommandNotFoundException: AppX, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span><span class="sxs-lookup"><span data-stu-id="39272-161">Running a cmdlet from any of these modules throws CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span></span>
* <span data-ttu-id="39272-162">Import-Module en cualquiera de los módulos anteriores produce la excepción de PSSecurityException con obtener acceso no autorizado.</span><span class="sxs-lookup"><span data-stu-id="39272-162">Import-Module on any of the above modules throws PSSecurityException exception with UnauthorizedAccess.</span></span> <span data-ttu-id="39272-163">Carga automática de módulos no parece funcionar bien.</span><span class="sxs-lookup"><span data-stu-id="39272-163">Module auto loading does not seem to work either.</span></span>

<span data-ttu-id="39272-164">**Solución**: Modificar la directiva de ejecución dentro de la sesión remota de PowerShell para **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="39272-164">**Workaround**: Modify the execution policy within the remote PowerShell session to **RemoteSigned**.</span></span> <span data-ttu-id="39272-165">Para obtener más detalles sobre las directivas de ejecución diferente, consulte [mediante el Cmdlet Set-ExecutionPolicy](https://technet.microsoft.com/library/ee176961.aspx).</span><span class="sxs-lookup"><span data-stu-id="39272-165">For more details on the different execution policies, see [Using the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx).</span></span>

<span data-ttu-id="39272-166">**PROBLEMA**: Cmdlets de algunos módulos, como NetAdapter a veces no son visibles.</span><span class="sxs-lookup"><span data-stu-id="39272-166">**ISSUE**: Cmdlets from some modules such as NetAdapter are sometimes not visible.</span></span> <span data-ttu-id="39272-167">Por ejemplo, Get-Module NetAdapter devuelve una lista vacía.</span><span class="sxs-lookup"><span data-stu-id="39272-167">For example, Get-Module NetAdapter returns an empty list.</span></span> 

<span data-ttu-id="39272-168">**Solución**: Use el parámetro - Force con Import-Module.</span><span class="sxs-lookup"><span data-stu-id="39272-168">**Workaround**: Use the -Force parameter with Import-Module.</span></span> <span data-ttu-id="39272-169">Por ejemplo: `Import-Module NetAdapter -Force`.</span><span class="sxs-lookup"><span data-stu-id="39272-169">For example, `Import-Module NetAdapter -Force`.</span></span>

<span data-ttu-id="39272-170">**PROBLEMA**: Configuración de directiva de ejecución "AllSigned" interrumpe la comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="39272-170">**ISSUE**: Setting execution policy to "AllSigned" breaks PowerShell remoting.</span></span> <span data-ttu-id="39272-171">Intenta crear una sesión remota producirá un error con una SecurityException cargando Typesv3.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="39272-171">Subsequent attempts to create a remote session fail with a SecurityException loading Typesv3.ps1xml.</span></span> 

<span data-ttu-id="39272-172">**Solución**: Use winrs.exe para restaurar la directiva de ejecución de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="39272-172">**Workaround**: Use winrs.exe to restore PowerShell's execution policy:</span></span>
* <span data-ttu-id="39272-173">Página de códigos de consola de cambio</span><span class="sxs-lookup"><span data-stu-id="39272-173">Change console code page</span></span> `Chcp 65001`
* <span data-ttu-id="39272-174">Inicie sesión en un shell de cmd.exe remoto</span><span class="sxs-lookup"><span data-stu-id="39272-174">Log on to a remote cmd.exe shell</span></span> `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* <span data-ttu-id="39272-175">En cmd.exe remoto, modifique la clave del Registro adecuados</span><span class="sxs-lookup"><span data-stu-id="39272-175">Within remote cmd.exe, modify the appropriate registry key</span></span> `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* <span data-ttu-id="39272-176">Salga de sesión remoto cmd.exe</span><span class="sxs-lookup"><span data-stu-id="39272-176">Exit remote cmd.exe session</span></span> `exit`

### <a name="other-known-issues"></a><span data-ttu-id="39272-177">Otros problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="39272-177">Other known issues</span></span>

- <span data-ttu-id="39272-178">En los scripts de PowerShell, atributos de enumeración o clase de PowerShell no funcionan.</span><span class="sxs-lookup"><span data-stu-id="39272-178">In PowerShell scripts, attributes to PowerShell class or enumeration do not work.</span></span> <span data-ttu-id="39272-179">Adición de atribuir los resultados en la siguiente excepción: *Tipo debe ser un objeto de tipo en tiempo de ejecución*.</span><span class="sxs-lookup"><span data-stu-id="39272-179">Adding attributed results in the following exception thrown: *Type must be a runtime Type object*.</span></span>

- <span data-ttu-id="39272-180">No se admite la comunicación remota de PowerShell y CIM saliente.</span><span class="sxs-lookup"><span data-stu-id="39272-180">Outbound CIM and PowerShell remoting is not supported.</span></span> <span data-ttu-id="39272-181">La funcionalidad pertinente en los cmdlets de usuario de confianza no funcionará.</span><span class="sxs-lookup"><span data-stu-id="39272-181">Relevant functionality in relying cmdlets will not work.</span></span> <span data-ttu-id="39272-182">Estos incluyen Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command y Copy-Item.</span><span class="sxs-lookup"><span data-stu-id="39272-182">These include  Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command, and Copy-Item.</span></span>

- <span data-ttu-id="39272-183">Comandos de SecureString ConvertFrom-SecureString y ConvertTo-SecureString no funcionan a menos que se crea la sesión mediante la autenticación CredSSP.</span><span class="sxs-lookup"><span data-stu-id="39272-183">SecureString commands ConvertFrom-SecureString and ConvertTo-SecureString do not work unless the session is created using CredSSP authentication.</span></span> <span data-ttu-id="39272-184">En caso contrario,-Key debe especificarse el parámetro.</span><span class="sxs-lookup"><span data-stu-id="39272-184">Otherwise, the -Key parameter must be specified.</span></span> <span data-ttu-id="39272-185">Para obtener más información sobre cómo configurar la autenticación CredSSP, vea [el problema de "Salto doble"](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span><span class="sxs-lookup"><span data-stu-id="39272-185">For details on configuring CredSSP authentication, see [The “Double-Hop” Problem](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span></span>


