---
title: Uso de PowerShell para Windows IoT
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar PowerShell para conectarse al dispositivo, así como para administrar el dispositivo.
keywords: Windows IOT, PowerShell, Windows PowerShell, línea de comandos, Shell de línea de comandos
ms.openlocfilehash: 1519fb9dd61a8d6521757fdd97999f03b74afa7d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168169"
---
# <a name="using-powershell-for-windows-iot"></a><span data-ttu-id="f5f15-104">Uso de PowerShell para Windows IoT</span><span class="sxs-lookup"><span data-stu-id="f5f15-104">Using PowerShell for Windows IoT</span></span>

<span data-ttu-id="f5f15-105">Configure y administre de forma remota cualquier dispositivo de Windows 10 IoT Core mediante Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f15-105">Remotely configure and manage any Windows 10 IoT Core device by using Windows PowerShell.</span></span>
<span data-ttu-id="f5f15-106">PowerShell es un shell de línea de comandos basado en tareas y un lenguaje de scripting diseñado especialmente para la administración del sistema.</span><span class="sxs-lookup"><span data-stu-id="f5f15-106">PowerShell is a task-based command-line shell and scripting language, designed especially for system administration.</span></span>

<span data-ttu-id="f5f15-107">Asegúrese de seguir estos pasos para configurar correctamente el dispositivo que ejecuta Windows 10 IoT Core para que funcione bien con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f5f15-107">Make sure to follow these steps to correctly configure your device running Windows 10 IoT Core to work well with Visual Studio 2017.</span></span>

## <a name="initiating-a-powershell-session"></a><span data-ttu-id="f5f15-108">Iniciar una sesión de PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5f15-108">Initiating a PowerShell session</span></span>
1. <span data-ttu-id="f5f15-109">Para iniciar una sesión de PowerShell con el dispositivo de Windows 10 IoT Core, primero deberá crear una relación de confianza entre el equipo host y el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-109">To start a PowerShell session with your Windows 10 IoT Core device, you'll first need to create a trust relationship between your host PC and your device.</span></span> <span data-ttu-id="f5f15-110">Después de iniciar el dispositivo de Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-110">After starting your Windows IoT Core device, an IP address will be shown on the screen attached to the device.</span></span>

    ![DefaultApp en Windows 10 IoT Core](../media/PowerShell/DefaultApp.png)

   <span data-ttu-id="f5f15-112">Puede encontrar la misma información en el panel de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f5f15-112">You can find the same information on the Windows 10 IoT Core Dashboard.</span></span>

2. <span data-ttu-id="f5f15-113">Abra una consola de administrador de PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="f5f15-113">Open an administrator PowerShell console on your local PC.</span></span> <span data-ttu-id="f5f15-114">Escriba **PowerShell** en el cuadro **Buscar en la web y Windows** cerca del menú Inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="f5f15-114">Type **powershell** in the **Search the web and Windows** box near the Windows Start menu.</span></span> <span data-ttu-id="f5f15-115">Windows buscará PowerShell en su equipo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-115">Windows will find PowerShell on your PC.</span></span>

    ![Búsqueda de PowerShell](../media/PowerShell/start-ps.png)

3. <span data-ttu-id="f5f15-117">Para iniciar PowerShell como administrador, haga clic con el botón derecho en **Windows PowerShell**y, a continuación, seleccione **Ejecutar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="f5f15-117">To start PowerShell as an administrator, right-click **Windows PowerShell**, and then select **Run as administrator**.</span></span>

    ![Ejecutar PowerShell como administrador](../media/PowerShell/start-ps2.png)

   <span data-ttu-id="f5f15-119">Ahora debería ver la consola de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f15-119">Now you should see the PowerShell console.</span></span>

    ![Consola de PowerShell](../media/PowerShell/ps.PNG)

4. <span data-ttu-id="f5f15-121">Es posible que tenga que iniciar el servicio WinRM en el escritorio para habilitar las conexiones remotas.</span><span class="sxs-lookup"><span data-stu-id="f5f15-121">You may need to start the WinRM service on your desktop to enable remote connections.</span></span> <span data-ttu-id="f5f15-122">Para ello, en la consola de PowerShell, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="f5f15-122">To do so, from the PowerShell console, type the following command:</span></span>

        net start WinRM

5. <span data-ttu-id="f5f15-123">En la consola de PowerShell, escriba lo siguiente, sustituyendo `<machine-name or IP address>` el valor adecuado (con el **nombre del equipo** es el más sencillo, pero si el dispositivo no tiene un nombre único en la red, pruebe la dirección IP):</span><span class="sxs-lookup"><span data-stu-id="f5f15-123">From the PowerShell console, type the following, substituting `<machine-name or IP address>` with the appropriate value (using your **machine-name** is the easiest, but if your device is not uniquely named on your network, try the IP address):</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. <span data-ttu-id="f5f15-124">Escriba `Y` para confirmar el cambio.</span><span class="sxs-lookup"><span data-stu-id="f5f15-124">Enter `Y` to confirm the change.</span></span>

> [!NOTE]
> <span data-ttu-id="f5f15-125">Si desea conectar varios dispositivos, puede usar comas y comillas para separar cada dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-125">If you want to connect multiple devices, you can use commas and quotation marks to separate each device.</span></span>
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. <span data-ttu-id="f5f15-126">Ahora puede iniciar una sesión con el dispositivo de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f5f15-126">Now you can start a session with your Windows IoT Core device.</span></span> <span data-ttu-id="f5f15-127">En la consola de PowerShell del administrador, escriba:</span><span class="sxs-lookup"><span data-stu-id="f5f15-127">From you administrator PowerShell console, type:</span></span>

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. <span data-ttu-id="f5f15-128">En el cuadro de diálogo de credenciales, escriba la siguiente contraseña predeterminada:`p@ssw0rd`</span><span class="sxs-lookup"><span data-stu-id="f5f15-128">In the credential dialog, enter the following default password: `p@ssw0rd`</span></span>
    
    <div class="alert alert-note">
      <h5><span data-ttu-id="f5f15-129"><span class="win-icon win-icon-Page"></span>TENGA EN CUENTA</span><span class="sxs-lookup"><span data-stu-id="f5f15-129"><span class="win-icon win-icon-Page"></span> NOTE</span></span> </h5>
      <p><span data-ttu-id="f5f15-130">El proceso de conexión no es inmediato y puede tardar hasta 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="f5f15-130">The connection process is not immediate and can take up to 30 seconds.</span></span></p>
    </div>    
    
    <span data-ttu-id="f5f15-131">Si se conectó correctamente al dispositivo, debería ver la dirección IP del dispositivo antes de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="f5f15-131">If you successfully connected to the device, you should see the IP address of your device before the prompt.</span></span>

    ![Consola de PowerShell](../media/PowerShell/ps_device.png)

9. <span data-ttu-id="f5f15-133">Actualice la contraseña de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="f5f15-133">Update your account password.</span></span> <span data-ttu-id="f5f15-134">Se *recomienda encarecidamente* que actualice la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="f5f15-134">We *highly recommend* that you update the default password for the Administrator account.</span></span> <span data-ttu-id="f5f15-135">Para ello, emita los siguientes comandos en la conexión de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f5f15-135">To do this, issue the following commands in your PowerShell connection:</span></span>

    <span data-ttu-id="f5f15-136">a.</span><span class="sxs-lookup"><span data-stu-id="f5f15-136">a.</span></span> <span data-ttu-id="f5f15-137">Reemplace `[new password]` con una contraseña segura:</span><span class="sxs-lookup"><span data-stu-id="f5f15-137">Replace `[new password]` with a strong password:</span></span>
    
            net user Administrator [new password]
            
    <span data-ttu-id="f5f15-138">b.</span><span class="sxs-lookup"><span data-stu-id="f5f15-138">b.</span></span> <span data-ttu-id="f5f15-139">A continuación, establezca una nueva sesión de `Exit-PSSession` PowerShell `Enter-PSSession` con y con las nuevas credenciales.</span><span class="sxs-lookup"><span data-stu-id="f5f15-139">Next, establish a new PowerShell session using `Exit-PSSession` and `Enter-PSSession` with the new credentials.</span></span>
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a><span data-ttu-id="f5f15-140">Comandos de PowerShell de uso frecuente</span><span class="sxs-lookup"><span data-stu-id="f5f15-140">Commonly used PowerShell commands</span></span>

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a><span data-ttu-id="f5f15-141">Solución de problemas con Visual Studio Remote Debugger</span><span class="sxs-lookup"><span data-stu-id="f5f15-141">Troubleshooting with Visual Studio Remote Debugger</span></span>

<span data-ttu-id="f5f15-142">Para poder implementar aplicaciones desde Visual Studio 2017, tendrá que asegurarse de que el Visual Studio Remote Debugger se está ejecutando en el dispositivo de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f5f15-142">To be able to deploy applications from Visual Studio 2017, you will need to make sure that the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="f5f15-143">El depurador remoto debe abrirse automáticamente al iniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-143">The remote debugger should open automatically when you start your computer.</span></span> <span data-ttu-id="f5f15-144">Para realizar una doble comprobación, `tlist` use el comando para enumerar todos los procesos en ejecución de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f15-144">To double check, use the `tlist` command to list all the running processes from PowerShell.</span></span> <span data-ttu-id="f5f15-145">Debe haber dos instancias de msvsmon. exe en ejecución en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-145">There should be two instances of msvsmon.exe running on the device.</span></span>

<span data-ttu-id="f5f15-146">Es posible que el Visual Studio Remote Debugger agote el tiempo de espera después de largos períodos de inactividad.</span><span class="sxs-lookup"><span data-stu-id="f5f15-146">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="f5f15-147">Si Visual Studio no se puede conectar al dispositivo de Windows IoT Core, intente reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-147">If Visual Studio cannot connect to your Windows IoT Core device, try restarting the device.</span></span>

### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="f5f15-148">Configuración del dispositivo de Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="f5f15-148">Configure your Windows IoT Core device</span></span>

<span data-ttu-id="f5f15-149">Si lo desea, puede cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5f15-149">If you want, you can rename your device.</span></span> 

1. <span data-ttu-id="f5f15-150">Para cambiar el nombre del equipo, use `setcomputername` la utilidad:</span><span class="sxs-lookup"><span data-stu-id="f5f15-150">To change the computer name, use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

2. <span data-ttu-id="f5f15-151">Reinicie el dispositivo para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="f5f15-151">Restart the device for the change to take effect.</span></span> <span data-ttu-id="f5f15-152">Puede usar el comando `shutdown` de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="f5f15-152">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0

3. <span data-ttu-id="f5f15-153">Dado que se ha cambiado el nombre del equipo, después de reiniciar deberá volver a ejecutar este comando para conectarse a su dispositivo con el nuevo nombre:</span><span class="sxs-lookup"><span data-stu-id="f5f15-153">Because the computer name was changed, after you restart you will need to rerun this command to connect to your device using the new name:</span></span>

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
<span data-ttu-id="f5f15-154">El dispositivo Windows IoT Core ahora debe estar configurado correctamente y listo para usarse.</span><span class="sxs-lookup"><span data-stu-id="f5f15-154">Your Windows IoT Core device should now be properly configured and ready to use!</span></span>

### <a name="commonly-used-utilities"></a><span data-ttu-id="f5f15-155">Utilidades usadas comúnmente</span><span class="sxs-lookup"><span data-stu-id="f5f15-155">Commonly used utilities</span></span>

<span data-ttu-id="f5f15-156">Para obtener una lista de comandos y utilidades que puede usar con PowerShell, consulte la página de utilidades de la [línea de comandos](../manage-your-device/CommandLineUtils.md) .</span><span class="sxs-lookup"><span data-stu-id="f5f15-156">For a list of commands and utilities that you can use with PowerShell, see the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page.</span></span>

## <a name="known-issues-and-workarounds"></a><span data-ttu-id="f5f15-157">Problemas y soluciones conocidos</span><span class="sxs-lookup"><span data-stu-id="f5f15-157">Known issues and workarounds</span></span>

<span data-ttu-id="f5f15-158">**PROBLEMA**: Un error conocido en las directivas de seguridad de PowerShell provoca el manifiesto de los siguientes problemas en la sesión remota:</span><span class="sxs-lookup"><span data-stu-id="f5f15-158">**ISSUE**: A known bug in PowerShell security policies causes the following issues to manifest within the remote session:</span></span>
* <span data-ttu-id="f5f15-159">Get-Help devuelve coincidencias inesperadas.</span><span class="sxs-lookup"><span data-stu-id="f5f15-159">Get-Help returns unexpected matches.</span></span>
* <span data-ttu-id="f5f15-160">Get-command en un módulo especificado devuelve una lista de comandos vacía.</span><span class="sxs-lookup"><span data-stu-id="f5f15-160">Get-Command on a specified module returns an empty command list.</span></span>
* <span data-ttu-id="f5f15-161">La ejecución de un cmdlet desde cualquiera de estos módulos produce CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span><span class="sxs-lookup"><span data-stu-id="f5f15-161">Running a cmdlet from any of these modules throws CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.</span></span>
* <span data-ttu-id="f5f15-162">Import-Module en cualquiera de los módulos anteriores produce una excepción PSSecurityException con UnauthorizedAccess.</span><span class="sxs-lookup"><span data-stu-id="f5f15-162">Import-Module on any of the above modules throws PSSecurityException exception with UnauthorizedAccess.</span></span> <span data-ttu-id="f5f15-163">La carga automática de módulos no parece funcionar.</span><span class="sxs-lookup"><span data-stu-id="f5f15-163">Module auto loading does not seem to work either.</span></span>

<span data-ttu-id="f5f15-164">**Solución**: Modifique la Directiva de ejecución en la sesión remota de PowerShell a **RemoteSigned**.</span><span class="sxs-lookup"><span data-stu-id="f5f15-164">**Workaround**: Modify the execution policy within the remote PowerShell session to **RemoteSigned**.</span></span> <span data-ttu-id="f5f15-165">Para obtener más información sobre las diferentes directivas de ejecución, consulte [uso del cmdlet Set-ExecutionPolicy](https://technet.microsoft.com/library/ee176961.aspx).</span><span class="sxs-lookup"><span data-stu-id="f5f15-165">For more details on the different execution policies, see [Using the Set-ExecutionPolicy Cmdlet](https://technet.microsoft.com/library/ee176961.aspx).</span></span>

<span data-ttu-id="f5f15-166">**PROBLEMA**: En ocasiones, los cmdlets de algunos módulos, como NetAdapter, no son visibles.</span><span class="sxs-lookup"><span data-stu-id="f5f15-166">**ISSUE**: Cmdlets from some modules such as NetAdapter are sometimes not visible.</span></span> <span data-ttu-id="f5f15-167">Por ejemplo, Get-Module NetAdapter devuelve una lista vacía.</span><span class="sxs-lookup"><span data-stu-id="f5f15-167">For example, Get-Module NetAdapter returns an empty list.</span></span> 

<span data-ttu-id="f5f15-168">**Solución**: Use el parámetro-Force con Import-Module.</span><span class="sxs-lookup"><span data-stu-id="f5f15-168">**Workaround**: Use the -Force parameter with Import-Module.</span></span> <span data-ttu-id="f5f15-169">Por ejemplo: `Import-Module NetAdapter -Force`.</span><span class="sxs-lookup"><span data-stu-id="f5f15-169">For example, `Import-Module NetAdapter -Force`.</span></span>

<span data-ttu-id="f5f15-170">**PROBLEMA**: La configuración de la Directiva de ejecución en "AllSigned" interrumpe la comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f15-170">**ISSUE**: Setting execution policy to "AllSigned" breaks PowerShell remoting.</span></span> <span data-ttu-id="f5f15-171">Los intentos posteriores de crear una sesión remota producirán un error con una excepción de carga Typesv3. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="f5f15-171">Subsequent attempts to create a remote session fail with a SecurityException loading Typesv3.ps1xml.</span></span> 

<span data-ttu-id="f5f15-172">**Solución**: Use Winrs. exe para restaurar la Directiva de ejecución de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f5f15-172">**Workaround**: Use winrs.exe to restore PowerShell's execution policy:</span></span>
* <span data-ttu-id="f5f15-173">Cambiar página de códigos de la consola`Chcp 65001`</span><span class="sxs-lookup"><span data-stu-id="f5f15-173">Change console code page `Chcp 65001`</span></span>
* <span data-ttu-id="f5f15-174">Iniciar sesión en un shell de cmd. exe remoto`Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`</span><span class="sxs-lookup"><span data-stu-id="f5f15-174">Log on to a remote cmd.exe shell `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`</span></span>
* <span data-ttu-id="f5f15-175">En cmd. exe remoto, modifique la clave del registro adecuada.`reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`</span><span class="sxs-lookup"><span data-stu-id="f5f15-175">Within remote cmd.exe, modify the appropriate registry key `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`</span></span>
* <span data-ttu-id="f5f15-176">Salir de la sesión remota de cmd. exe`exit`</span><span class="sxs-lookup"><span data-stu-id="f5f15-176">Exit remote cmd.exe session `exit`</span></span>

### <a name="other-known-issues"></a><span data-ttu-id="f5f15-177">Otros problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="f5f15-177">Other known issues</span></span>

- <span data-ttu-id="f5f15-178">En los scripts de PowerShell, los atributos de la clase o enumeración de PowerShell no funcionan.</span><span class="sxs-lookup"><span data-stu-id="f5f15-178">In PowerShell scripts, attributes to PowerShell class or enumeration do not work.</span></span> <span data-ttu-id="f5f15-179">Al agregar los resultados con atributos se produce la siguiente excepción: *El tipo debe ser un objeto de tipo en tiempo de ejecución*.</span><span class="sxs-lookup"><span data-stu-id="f5f15-179">Adding attributed results in the following exception thrown: *Type must be a runtime Type object*.</span></span>

- <span data-ttu-id="f5f15-180">No se admite CIM saliente y la comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5f15-180">Outbound CIM and PowerShell remoting is not supported.</span></span> <span data-ttu-id="f5f15-181">La funcionalidad relevante en los cmdlets de confianza no funcionará.</span><span class="sxs-lookup"><span data-stu-id="f5f15-181">Relevant functionality in relying cmdlets will not work.</span></span> <span data-ttu-id="f5f15-182">Entre ellas se incluyen Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command y Copy-Item.</span><span class="sxs-lookup"><span data-stu-id="f5f15-182">These include  Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command, and Copy-Item.</span></span>

- <span data-ttu-id="f5f15-183">Los comandos SecureString ConvertFrom-SecureString y ConvertTo-SecureString no funcionan a menos que la sesión se cree mediante la autenticación CredSSP.</span><span class="sxs-lookup"><span data-stu-id="f5f15-183">SecureString commands ConvertFrom-SecureString and ConvertTo-SecureString do not work unless the session is created using CredSSP authentication.</span></span> <span data-ttu-id="f5f15-184">De lo contrario, debe especificarse el parámetro-Key.</span><span class="sxs-lookup"><span data-stu-id="f5f15-184">Otherwise, the -Key parameter must be specified.</span></span> <span data-ttu-id="f5f15-185">Para obtener más información sobre la configuración de la autenticación CredSSP, vea [el problema de "salto doble"](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span><span class="sxs-lookup"><span data-stu-id="f5f15-185">For details on configuring CredSSP authentication, see [The “Double-Hop” Problem](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).</span></span>


