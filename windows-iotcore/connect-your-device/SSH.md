---
title: Secure Shell (SSH)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar secure shell para administrar de forma remota y configurar el dispositivo de IoT Core.
keywords: Windows iot, shell seguro, remoto, cliente SSH PuTTY, SSH
ms.openlocfilehash: 2c83184507a840c6017b1dfe36ac915004057d9a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514716"
---
# <a name="secure-shell-ssh"></a><span data-ttu-id="43426-104">Secure Shell (SSH)</span><span class="sxs-lookup"><span data-stu-id="43426-104">Secure Shell (SSH)</span></span>
<span data-ttu-id="43426-105">Shell seguro (SSH) le permite administrar de forma remota y configurar el dispositivo Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="43426-105">Secure Shell (SSH) allows you to remotely administer and configure your Windows IoT Core device</span></span>

## <a name="using-the-windows-10-openssh-client"></a><span data-ttu-id="43426-106">Mediante el cliente de Windows 10 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="43426-106">Using the Windows 10 OpenSSH client</span></span>
> [!IMPORTANT]
> <span data-ttu-id="43426-107">El cliente OpenSSH Windows requiere que el host del cliente SSH del sistema operativo es Windows 10 versión 1803(17134).</span><span class="sxs-lookup"><span data-stu-id="43426-107">The Windows OpenSSH client requires that your SSH client host OS is Windows 10 version 1803(17134).</span></span> <span data-ttu-id="43426-108">Además, el dispositivo Windows 10 IoT Core debe ejecutar RS5 Windows Insider Preview versión 17723 o superior.</span><span class="sxs-lookup"><span data-stu-id="43426-108">Also, the Windows 10 IoT Core device must be running RS5 Windows Insider Preview release 17723 or greater.</span></span>

<span data-ttu-id="43426-109">El **cliente OpenSSH** se agregó a Windows 10 en 1803 (compilación 17134) como una característica opcional.</span><span class="sxs-lookup"><span data-stu-id="43426-109">The **OpenSSH Client** was added to Windows 10 in 1803 (build 17134) as an optional feature.</span></span> <span data-ttu-id="43426-110">Para instalar el cliente puede buscar **administrar características opcionales** en configuración de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="43426-110">To install the client you can search for **Manage Optional Features** in Windows 10 settings.</span></span> <span data-ttu-id="43426-111">Si el **cliente OpenSSH** no aparece en la lista de las características instaladas, a continuación, elija **agregar una característica**.</span><span class="sxs-lookup"><span data-stu-id="43426-111">If the **OpenSSH Client** is not listed in the list of installed features then choose **Add a feature**.</span></span>

![Agregar una característica](../media/SSH/add_a_feature.png)

<span data-ttu-id="43426-113">A continuación, seleccione **cliente OpenSSH** en la lista y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="43426-113">Next select **OpenSSH Client** in the list and click **Install**.</span></span>

![Instalación de cliente OpenSSH](../media/SSH/optional_features.png)

<span data-ttu-id="43426-115">Para iniciar sesión con una nombre de usuario y contraseña, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="43426-115">To login with a username and password use the following command:</span></span>

```cmd
ssh administrator@host
```

<span data-ttu-id="43426-116">Donde host es la dirección IP del dispositivo Windows IoT Core o el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43426-116">Where host is either the IP address of the Windows IoT Core device or the device name.</span></span>

<span data-ttu-id="43426-117">La primera vez que conecte verá un mensaje similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="43426-117">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="43426-118">Tipo **Sí** y presione **escriba**.</span><span class="sxs-lookup"><span data-stu-id="43426-118">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="43426-119">Si tiene que iniciar sesión como **DefaultAccount** en lugar de como administrador deberá generar una clave y usar la clave para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="43426-119">If you need to log in as **DefaultAccount** rather than as administrator you will need to generate a key and use the key to log in.</span></span>  <span data-ttu-id="43426-120">En el escritorio que pretende conectarse al dispositivo de IoT, abra una ventana de powershell y cambie a la carpeta datos personales (p. ej. cd ~)</span><span class="sxs-lookup"><span data-stu-id="43426-120">From the desktop that you intend to connect to your IoT Device from, open a powershell window and change to your personal data folder (e.g cd ~)</span></span>

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

<span data-ttu-id="43426-121">Registre la clave con ssh-agent (opcional, para la experiencia de inicio de sesión único).</span><span class="sxs-lookup"><span data-stu-id="43426-121">Register the key with ssh-agent (optional, for single sign-on experience).</span></span>  <span data-ttu-id="43426-122">Tenga en cuenta que ssh-agregar debe realizarse desde una carpeta que sea incorporarse a usted como la sesión de usuario (Builtin\Administrators y el usuario NT_AUTHORITY\System también son Aceptar).</span><span class="sxs-lookup"><span data-stu-id="43426-122">Note that ssh-add must be performed from a folder that is  ACL'd to you as the signed-in user (Builtin\Administrators and the NT_AUTHORITY\System user are also ok).</span></span>  <span data-ttu-id="43426-123">CD predeterminado ~ desde powershell debe ser suficiente, ya que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="43426-123">By default cd ~ from powershell should be sufficient as shown below.</span></span>

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> <span data-ttu-id="43426-124">Si recibe un mensaje que se ha deshabilitado el servicio ssh-agent puede habilitarla con **inicio ssh-agent de sc.exe config = auto**</span><span class="sxs-lookup"><span data-stu-id="43426-124">If you receive a message that the ssh-agent service is disabled you can enable it with **sc.exe config ssh-agent start=auto**</span></span>

<span data-ttu-id="43426-125">Para habilitar el inicio de sesión único anexa la clave pública en el dispositivo Windows IoT Core **authorized_keys** archivo.</span><span class="sxs-lookup"><span data-stu-id="43426-125">To enable single sign append the public key to the Windows IoT Core device **authorized_keys** file.</span></span>  <span data-ttu-id="43426-126">O si solo tiene una clave copie el archivo de clave pública en el servidor remoto **authorized_keys** archivo.</span><span class="sxs-lookup"><span data-stu-id="43426-126">Or if you only have one key you copy the public key file to the remote **authorized_keys** file.</span></span>

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

<span data-ttu-id="43426-127">Si la clave no está registrada con ssh-agent debe especificarse en la línea de comandos para el inicio de sesión:</span><span class="sxs-lookup"><span data-stu-id="43426-127">If the key is not registered with ssh-agent it must be specified on the command line to login:</span></span> 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

<span data-ttu-id="43426-128">Si se registra la clave privada con ssh-agent, solo deberá especificar <strong>DefaultAccount@host</strong>:</span><span class="sxs-lookup"><span data-stu-id="43426-128">If the private key is registered with ssh-agent then you only need to specify <strong>DefaultAccount@host</strong>:</span></span>

```cmd
ssh DefaultAccount@host
```

<span data-ttu-id="43426-129">La primera vez que conecte verá un mensaje similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="43426-129">The first time you connect you see a message like the following:</span></span>

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

<span data-ttu-id="43426-130">Tipo **Sí** y presione **escriba**.</span><span class="sxs-lookup"><span data-stu-id="43426-130">Type **yes** and press **enter**.</span></span>

<span data-ttu-id="43426-131">Debe estar conectado como **DefaultAccount**</span><span class="sxs-lookup"><span data-stu-id="43426-131">You should now be connected as **DefaultAccount**</span></span>

<span data-ttu-id="43426-132">Usar inicio de sesión único con el **administrador** cuenta, la clave pública se anexa al c:\data\ProgramData\ssh\administrators_authorized_keys en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="43426-132">To use single sign-on with the **administrator** account, append your public key to c:\data\ProgramData\ssh\administrators_authorized_keys on the Windows IoT Core device.</span></span> 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="43426-133">También deberá establecer la ACL para administrators_authorized_keys para que coincida con la ACL de ssh_host_dsa_key en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="43426-133">You will also need to set the ACL for administrators_authorized_keys to match the ACL of ssh_host_dsa_key in the same directory.</span></span>

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

<span data-ttu-id="43426-134">Para establecer la ACL mediante powershell</span><span class="sxs-lookup"><span data-stu-id="43426-134">To set the ACL using powershell</span></span>

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> <span data-ttu-id="43426-135">Si ve un **CAMBIADO de identificación del HOST remoto** mensaje después de realizar cambios en el dispositivo Windows 10 IoT Core, a continuación, editar C:\Users\<username >\.ssh\known_hosts y quitar el host que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="43426-135">If you see a **REMOTE HOST IDENTIFICATION CHANGED** message after making changes to the Windows 10 IoT Core device, then edit C:\Users\<username>\.ssh\known_hosts and remove the host that has changed.</span></span>

<span data-ttu-id="43426-136">Consulte también: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span><span class="sxs-lookup"><span data-stu-id="43426-136">See also: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)</span></span>

## <a name="using-putty"></a><span data-ttu-id="43426-137">Uso de PuTTY</span><span class="sxs-lookup"><span data-stu-id="43426-137">Using PuTTY</span></span>

### <a name="download-a-ssh-client"></a><span data-ttu-id="43426-138">Descargar a un cliente SSH</span><span class="sxs-lookup"><span data-stu-id="43426-138">Download a SSH client</span></span>
<span data-ttu-id="43426-139">Para conectarse a su dispositivo mediante SSH, primero debe descargar un cliente SSH, como [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span><span class="sxs-lookup"><span data-stu-id="43426-139">In order to connect to your device using SSH, you'll first need to download a SSH client, such as [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).</span></span>

### <a name="connect-to-your-device"></a><span data-ttu-id="43426-140">Conectarse al dispositivo</span><span class="sxs-lookup"><span data-stu-id="43426-140">Connect to your device</span></span>
* <span data-ttu-id="43426-141">Para conectarse al dispositivo, deberá primero obtener la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43426-141">In order to connect to your device, you need to first get the IP address of the device.</span></span>  <span data-ttu-id="43426-142">Después de arrancar el dispositivo Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo:</span><span class="sxs-lookup"><span data-stu-id="43426-142">After booting your Windows IoT Core device, an IP address will be shown on the screen attached to the device:</span></span>

    ![DefaultApp en Windows IoT Core](../media/SSH/DefaultApp.png)

* <span data-ttu-id="43426-144">Ahora inicie PuTTY y escriba la dirección IP en el `Host Name` cuadro de texto y asegúrese de que el `SSH` botón de radio está seleccionado.</span><span class="sxs-lookup"><span data-stu-id="43426-144">Now launch PuTTY and enter the IP address in the `Host Name` text box and make sure the `SSH` radio button is selected.</span></span>  <span data-ttu-id="43426-145">A continuación, haga clic en `Open`.</span><span class="sxs-lookup"><span data-stu-id="43426-145">Then click `Open`.</span></span>

    ![Configuración de puTTY](../media/SSH/putty_config.png)

* <span data-ttu-id="43426-147">Si se conecta al dispositivo por primera vez desde su equipo, verá la siguiente alerta de seguridad.</span><span class="sxs-lookup"><span data-stu-id="43426-147">If you're connecting to your device for the first time from your computer, you may see the following security alert.</span></span>  <span data-ttu-id="43426-148">Simplemente haga clic en `Yes` para continuar.</span><span class="sxs-lookup"><span data-stu-id="43426-148">Just click `Yes` to continue.</span></span>

    ![Alerta de seguridad de puTTY](../media/SSH/putty_security_prompt.png)

* <span data-ttu-id="43426-150">Si la conexión se realizó correctamente, debería ver `login as:` en la pantalla, que le solicitará que inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="43426-150">If the connection was successful, you should see `login as:` on the screen, prompting you to login.</span></span>  
    <span data-ttu-id="43426-151">Escriba `Administrator` y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="43426-151">Enter `Administrator` and press enter.</span></span>  <span data-ttu-id="43426-152">A continuación, escriba la contraseña predeterminada `p@ssw0rd` como la contraseña y presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="43426-152">Then enter the default password `p@ssw0rd` as the password and press enter.</span></span>

    ![Inicio de sesión de puTTY](../media/SSH/putty_login.png)

    <span data-ttu-id="43426-154">Si puede iniciar sesión correctamente, debería ver algo parecido a esto:</span><span class="sxs-lookup"><span data-stu-id="43426-154">If you were able to login successfully, you should see something like this:</span></span>

    ![Consola de puTTY](../media/ssh/putty_console.png)

### <a name="update-account-password"></a><span data-ttu-id="43426-156">Actualizar la contraseña de cuenta</span><span class="sxs-lookup"><span data-stu-id="43426-156">Update account password</span></span>

<span data-ttu-id="43426-157">Es **recomienda** que actualizar la contraseña predeterminada para la cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="43426-157">It is **highly recommended** that you update the default password for the Administrator account.</span></span>

<span data-ttu-id="43426-158">Para ello, escriba el siguiente comando en la consola de PuTTY, reemplazando `[new password]` con una contraseña segura:</span><span class="sxs-lookup"><span data-stu-id="43426-158">To do this, enter the following command in the PuTTY console, replacing `[new password]` with a strong password:</span></span>
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a><span data-ttu-id="43426-159">Configurar el dispositivo Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="43426-159">Configure your Windows IoT Core device</span></span>
* <span data-ttu-id="43426-160">Para poder implementar aplicaciones desde Visual Studio 2017, deberá asegurarse de que se está ejecutando Visual Studio Remote Debugger en el dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="43426-160">To be able to deploy applications from Visual Studio 2017, you will need to make sure the Visual Studio Remote Debugger is running on your Windows IoT Core device.</span></span> <span data-ttu-id="43426-161">El depurador remoto debe ejecutarse automáticamente en tiempo de arranque de la máquina.</span><span class="sxs-lookup"><span data-stu-id="43426-161">The remote debugger should launch automatically at machine boot time.</span></span> <span data-ttu-id="43426-162">Para volver a comprobar, use el comando de tlist para enumerar todos los procesos de ejecución de powershell.</span><span class="sxs-lookup"><span data-stu-id="43426-162">To double check, use the tlist command to list all the running processes from powershell.</span></span> <span data-ttu-id="43426-163">Debe haber dos instancias de msvsmon.exe que se ejecutan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43426-163">There should be two instances of msvsmon.exe running on the device.</span></span>

* <span data-ttu-id="43426-164">Es posible que el depurador remoto de Visual Studio en tiempo de espera tras un largo período de inactividad.</span><span class="sxs-lookup"><span data-stu-id="43426-164">It is possible for the Visual Studio Remote Debugger to time out after long periods of inactivity.</span></span> <span data-ttu-id="43426-165">Si Visual Studio no puede conectarse a su dispositivo Windows IoT Core, intente reiniciar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43426-165">If Visual Studio cannot connect to your Windows IoT Core device, try rebooting the device.</span></span>

* <span data-ttu-id="43426-166">Si lo desea, también puede cambiar el nombre del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="43426-166">If you want, you can also rename your device.</span></span> <span data-ttu-id="43426-167">Para cambiar el nombre del equipo, use el `setcomputername` utilidad:</span><span class="sxs-lookup"><span data-stu-id="43426-167">To change the 'computer name', use the `setcomputername` utility:</span></span>

        setcomputername <new-name>

    <span data-ttu-id="43426-168">Deberá reiniciar el dispositivo para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="43426-168">You will need to reboot the device for the change to take effect.</span></span> <span data-ttu-id="43426-169">Puede usar el `shutdown` comando como sigue:</span><span class="sxs-lookup"><span data-stu-id="43426-169">You can use the `shutdown` command as follows:</span></span>

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a><span data-ttu-id="43426-170">Frecuente utilidades</span><span class="sxs-lookup"><span data-stu-id="43426-170">Commonly used utilities</span></span>

<span data-ttu-id="43426-171">Consulte la [utilidades de línea de comandos](../manage-your-device/CommandLineUtils.md) para obtener una lista de comandos y utilidades que puede utilizar con SSH.</span><span class="sxs-lookup"><span data-stu-id="43426-171">See the [Command Line Utils](../manage-your-device/CommandLineUtils.md) page for a list of commands and utilities you can use with SSH.</span></span>
