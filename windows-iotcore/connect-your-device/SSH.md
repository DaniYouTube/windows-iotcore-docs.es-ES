---
title: Secure Shell (SSH)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar Secure Shell para administrar y configurar de forma remota el dispositivo de IoT Core.
keywords: Windows IOT, shell seguro, remoto, cliente SSH, PuTTy, SSH
ms.openlocfilehash: 2c83184507a840c6017b1dfe36ac915004057d9a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168772"
---
# <a name="secure-shell-ssh"></a><span data-ttu-id="a244e-104">Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="a244e-104">Secure Shell (SSH)</span></span>
<span data-ttu-id="a244e-105">Secure Shell (SSH) permite administrar y configurar de forma remota el dispositivo de Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="a244e-105">Secure Shell (SSH) allows you to remotely administer and configure your Windows IoT Core device</span></span>

## <a name="using-the-windows-10-openssh-client"></a><span data-ttu-id="a244e-106">Uso del cliente OpenSSH de Windows 10</span><span class="sxs-lookup"><span data-stu-id="a244e-106">Using the Windows 10 OpenSSH client</span></span>
> [!IMPORTANT]
> <span data-ttu-id="a244e-107">El cliente OpenSSH de Windows requiere que el sistema operativo del host del cliente SSH sea Windows 10 versión 1803 (17134).</span><span class="sxs-lookup"><span data-stu-id="a244e-107">The Windows OpenSSH client requires that your SSH client host OS is Windows 10 version 1803(17134).</span></span> <span data-ttu-id="a244e-108">Además, el dispositivo Windows 10 IoT Core debe ejecutar RS5 Windows Insider Preview versión 17723 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a244e-108">Also, the Windows 10 IoT Core device must be running RS5 Windows Insider Preview release 17723 or greater.</span></span>

<span data-ttu-id="a244e-109">El **cliente OpenSSH** se ha agregado a Windows 10 en 1803 (compilación 17134) como una característica opcional.</span><span class="sxs-lookup"><span data-stu-id="a244e-109">The **OpenSSH Client** was added to Windows 10 in 1803 (build 17134) as an optional feature.</span></span> <span data-ttu-id="a244e-110">Para instalar el cliente, puede buscar **administrar características opcionales** en la configuración de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a244e-110">To install the client you can search for **Manage Optional Features** in Windows 10 settings.</span></span> <span data-ttu-id="a244e-111">Si el **cliente OpenSSH** no aparece en la lista de características instaladas, elija **Agregar una característica**.</span><span class="sxs-lookup"><span data-stu-id="a244e-111">If the **OpenSSH Client** is not listed in the list of installed features then choose **Add a feature**.</span></span>

![Agregar una característica](../media/SSH/add_a_feature.png)

<span data-ttu-id="a244e-113">A continuación, seleccione **cliente OpenSSH** en la lista y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="a244e-113">Next select **OpenSSH Client** in the list and click **Install**.</span></span>

![Instalación del cliente OpenSSH](../media/SSH/optional_features.png)

<span data-ttu-id="a244e-115">Para iniciar sesión con un nombre de usuario y una contraseña, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="a244e-115">To login with a username and password use the following command:</span></span>

```cmd
ssh administrator@host
```

<span data-ttu-id="a244e-116">Donde host es la dirección IP del dispositivo Windows IoT Core o el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a244e-116">Where host is either the IP address of the Windows IoT Core device or the device name.</span></span>

<span data-ttu-id="a244e-117">La primera vez que se conecte, verá un mensaje similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="a244e-117">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="a244e-118">Escriba **sí** y presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="a244e-118">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="a244e-119">Si necesita iniciar sesión como **DefaultAccount** en lugar de como administrador, debe generar una clave y usar la clave para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="a244e-119">If you need to log in as **DefaultAccount** rather than as administrator you will need to generate a key and use the key to log in.</span></span>  <span data-ttu-id="a244e-120">Desde el escritorio que quiere conectar a su dispositivo de IoT desde, abra una ventana de PowerShell y cambie a la carpeta de datos personales (por ejemplo, CD ~).</span><span class="sxs-lookup"><span data-stu-id="a244e-120">From the desktop that you intend to connect to your IoT Device from, open a powershell window and change to your personal data folder (e.g cd ~)</span></span>

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

<span data-ttu-id="a244e-121">Registre la clave con ssh-agent (opcional, para la experiencia de inicio de sesión único).</span><span class="sxs-lookup"><span data-stu-id="a244e-121">Register the key with ssh-agent (optional, for single sign-on experience).</span></span>  <span data-ttu-id="a244e-122">Tenga en cuenta que ssh-add debe realizarse desde una carpeta que sea una ACL como el usuario con sesión iniciada (Builtin\Administrators y el usuario NT_AUTHORITY\System también son correctos).</span><span class="sxs-lookup"><span data-stu-id="a244e-122">Note that ssh-add must be performed from a folder that is  ACL'd to you as the signed-in user (Builtin\Administrators and the NT_AUTHORITY\System user are also ok).</span></span>  <span data-ttu-id="a244e-123">De forma predeterminada, el CD ~ de PowerShell debe ser suficiente como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="a244e-123">By default cd ~ from powershell should be sufficient as shown below.</span></span>

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> <span data-ttu-id="a244e-124">Si recibe un mensaje que indica que el servicio ssh-agent está deshabilitado, puede habilitarlo con **SC. exe config ssh-agent Start = Auto**</span><span class="sxs-lookup"><span data-stu-id="a244e-124">If you receive a message that the ssh-agent service is disabled you can enable it with **sc.exe config ssh-agent start=auto**</span></span>

<span data-ttu-id="a244e-125">Para habilitar el inicio de sesión único, anexe la clave pública al archivo **authorized_keys** de dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="a244e-125">To enable single sign append the public key to the Windows IoT Core device **authorized_keys** file.</span></span>  <span data-ttu-id="a244e-126">O bien, si solo tiene una clave, copie el archivo de clave pública en el archivo **authorized_keys** remoto.</span><span class="sxs-lookup"><span data-stu-id="a244e-126">Or if you only have one key you copy the public key file to the remote **authorized_keys** file.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

<span data-ttu-id="a244e-127">Si la clave no está registrada con ssh-agent, debe especificarse en la línea de comandos para iniciar sesión:</span><span class="sxs-lookup"><span data-stu-id="a244e-127">If the key is not registered with ssh-agent it must be specified on the command line to login:</span></span> 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

<span data-ttu-id="a244e-128">Si la clave privada está registrada con ssh-agent, solo tiene que especificar <strong>DefaultAccount@host</strong>:</span><span class="sxs-lookup"><span data-stu-id="a244e-128">If the private key is registered with ssh-agent then you only need to specify <strong>DefaultAccount@host</strong>:</span></span>

```cmd
ssh DefaultAccount@host
```

<span data-ttu-id="a244e-129">La primera vez que se conecte, verá un mensaje similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="a244e-129">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="a244e-130">Escriba **sí** y presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="a244e-130">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="a244e-131">Ahora debería estar conectado como **DefaultAccount**</span><span class="sxs-lookup"><span data-stu-id="a244e-131">You should now be connected as **DefaultAccount**</span></span>

<span data-ttu-id="a244e-132">Para usar el inicio de sesión único con la cuenta de **Administrador** , anexe la clave pública a c:\data\ProgramData\ssh\administrators_authorized_keys en el dispositivo Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="a244e-132">To use single sign-on with the **administrator** account, append your public key to c:\data\ProgramData\ssh\administrators_authorized_keys on the Windows IoT Core device.</span></span> 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="a244e-133">También tendrá que establecer la ACL de administrators_authorized_keys para que coincida con la ACL de ssh_host_dsa_key en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="a244e-133">You will also need to set the ACL for administrators_authorized_keys to match the ACL of ssh_host_dsa_key in the same directory.</span></span>

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="a244e-134">Para establecer la ACL mediante PowerShell</span><span class="sxs-lookup"><span data-stu-id="a244e-134">To set the ACL using powershell</span></span>

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> <span data-ttu-id="a244e-135">Si ve un mensaje de **identificación de host remoto cambiado** después de realizar cambios en el dispositivo de Windows 10 IOT Core,\<Edite\.C:\Users username > ssh\known_hosts y quite el host que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="a244e-135">If you see a **REMOTE HOST IDENTIFICATION CHANGED** message after making changes to the Windows 10 IoT Core device, then edit C:\Users\<username>\.ssh\known_hosts and remove the host that has changed.</span></span>

<span data-ttu-id="a244e-136">Consulte también: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span><span class="sxs-lookup"><span data-stu-id="a244e-136">See also: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span></span>

## <a name="using-putty"></a><span data-ttu-id="a244e-137">Usar PuTTy</span><span class="sxs-lookup"><span data-stu-id="a244e-137">Using PuTTY</span></span>

### <a name="download-a-ssh-client"></a><span data-ttu-id="a244e-138">Descarga de un cliente SSH</span><span class="sxs-lookup"><span data-stu-id="a244e-138">Download a SSH client</span></span>
<span data-ttu-id="a244e-139">Para conectarse a su dispositivo mediante SSH, primero deberá descargar un cliente SSH, como [Putty](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span><span class="sxs-lookup"><span data-stu-id="a244e-139">In order to connect to your device using SSH, you'll first need to download a SSH client, such as [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span></span>

### <a name="connect-to-your-device"></a><span data-ttu-id="a244e-140">Conectarse al dispositivo</span><span class="sxs-lookup"><span data-stu-id="a244e-140">Connect to your device</span></span>
* <span data-ttu-id="a244e-141">Para conectarse a su dispositivo, primero debe obtener la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a244e-141">In order to connect to your device, you need to first get the IP address of the device.</span></span>  <span data-ttu-id="a244e-142">Después de arrancar el dispositivo Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo:</span><span class="sxs-lookup"><span data-stu-id="a244e-142">After booting your Windows IoT Core device, an IP address will be shown on the screen attached to the device:</span></span>

    ![DefaultApp en Windows IoT Core](../media/SSH/DefaultApp.png)

* <span data-ttu-id="a244e-144">Ahora, inicie Putty y escriba la dirección IP en `Host Name` el cuadro de texto y asegúrese `SSH` de que el botón de radio está seleccionado.</span><span class="sxs-lookup"><span data-stu-id="a244e-144">Now launch PuTTY and enter the IP address in the `Host Name` text box and make sure the `SSH` radio button is selected.</span></span>  <span data-ttu-id="a244e-145">A continuación `Open`, haga clic en.</span><span class="sxs-lookup"><span data-stu-id="a244e-145">Then click `Open`.</span></span>

    ![Configuración de PuTTy](../media/SSH/putty_config.png)

* <span data-ttu-id="a244e-147">Si se va a conectar al dispositivo por primera vez desde el equipo, es posible que vea la alerta de seguridad siguiente.</span><span class="sxs-lookup"><span data-stu-id="a244e-147">If you're connecting to your device for the first time from your computer, you may see the following security alert.</span></span>  <span data-ttu-id="a244e-148">Basta con `Yes` hacer clic para continuar.</span><span class="sxs-lookup"><span data-stu-id="a244e-148">Just click `Yes` to continue.</span></span>

    ![Alerta de seguridad de PuTTy](../media/SSH/putty_security_prompt.png)

* <span data-ttu-id="a244e-150">Si la conexión se realizó correctamente, debería ver `login as:` en la pantalla, donde se le pide que inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="a244e-150">If the connection was successful, you should see `login as:` on the screen, prompting you to login.</span></span>  
    <span data-ttu-id="a244e-151">Escriba `Administrator` y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="a244e-151">Enter `Administrator` and press enter.</span></span>  <span data-ttu-id="a244e-152">A continuación, escriba la `p@ssw0rd` contraseña predeterminada como contraseña y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="a244e-152">Then enter the default password `p@ssw0rd` as the password and press enter.</span></span>

    ![Inicio de sesión de PuTTy](../media/SSH/putty_login.png)

    <span data-ttu-id="a244e-154">Si ha podido iniciar sesión correctamente, debería ver algo parecido a esto:</span><span class="sxs-lookup"><span data-stu-id="a244e-154">If you were able to login successfully, you should see something like this:</span></span>

    ![Consola de PuTTy](../media/ssh/putty_console.png)

### <a name="update-account-password"></a><span data-ttu-id="a244e-156">Actualizar contraseña de la cuenta</span><span class="sxs-lookup"><span data-stu-id="a244e-156">Update account password</span></span>

<span data-ttu-id="a244e-157">Se **recomienda encarecidamente** que actualice la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="a244e-157">It is **highly recommended** that you update the default password for the Administrator account.</span></span>

<span data-ttu-id="a244e-158">Para ello, escriba el siguiente comando en la consola de Putty y reemplace `[new password]` con una contraseña segura:</span><span class="sxs-lookup"><span data-stu-id="a244e-158">To do this, enter the following command in the PuTTY console, replacing `[new password]` with a strong password:</span></span>
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="a244e-159">Configuración del dispositivo de Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="a244e-159">Configure your Windows IoT Core device</span></span>
* <span data-ttu-id="a244e-160">Para poder implementar aplicaciones desde Visual Studio 2017, tendrá que asegurarse de que el Visual Studio Remote Debugger se está ejecutando en el dispositivo de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="a244e-160">To be able to deploy applications from Visual Studio 2017, you will need to make sure the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="a244e-161">El depurador remoto debe iniciarse automáticamente al arrancar el equipo.</span><span class="sxs-lookup"><span data-stu-id="a244e-161">The remote debugger should launch automatically at machine boot time.</span></span> <span data-ttu-id="a244e-162">Para realizar una doble comprobación, use el comando Tlist para enumerar todos los procesos en ejecución de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a244e-162">To double check, use the tlist command to list all the running processes from powershell.</span></span> <span data-ttu-id="a244e-163">Debe haber dos instancias de msvsmon. exe en ejecución en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a244e-163">There should be two instances of msvsmon.exe running on the device.</span></span>

* <span data-ttu-id="a244e-164">Es posible que el Visual Studio Remote Debugger agote el tiempo de espera después de largos períodos de inactividad.</span><span class="sxs-lookup"><span data-stu-id="a244e-164">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="a244e-165">Si Visual Studio no se puede conectar al dispositivo de Windows IoT Core, intente reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a244e-165">If Visual Studio cannot connect to your Windows IoT Core device, try rebooting the device.</span></span>

* <span data-ttu-id="a244e-166">Si lo desea, también puede cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a244e-166">If you want, you can also rename your device.</span></span> <span data-ttu-id="a244e-167">Para cambiar el nombre de equipo, use la `setcomputername` utilidad:</span><span class="sxs-lookup"><span data-stu-id="a244e-167">To change the 'computer name', use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

    <span data-ttu-id="a244e-168">Tendrá que reiniciar el dispositivo para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="a244e-168">You will need to reboot the device for the change to take effect.</span></span> <span data-ttu-id="a244e-169">Puede usar el comando `shutdown` de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a244e-169">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a><span data-ttu-id="a244e-170">Utilidades usadas comúnmente</span><span class="sxs-lookup"><span data-stu-id="a244e-170">Commonly used utilities</span></span>

<span data-ttu-id="a244e-171">Consulte la página de utilidades de la [línea de comandos](../manage-your-device/CommandLineUtils.md) para obtener una lista de comandos y utilidades que puede usar con SSH.</span><span class="sxs-lookup"><span data-stu-id="a244e-171">See the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page for a list of commands and utilities you can use with SSH.</span></span>
