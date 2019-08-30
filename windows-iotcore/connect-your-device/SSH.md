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
# <a name="secure-shell-ssh"></a>Secure Shell (SSH)
Secure Shell (SSH) permite administrar y configurar de forma remota el dispositivo de Windows IoT Core

## <a name="using-the-windows-10-openssh-client"></a>Uso del cliente OpenSSH de Windows 10
> [!IMPORTANT]
> El cliente OpenSSH de Windows requiere que el sistema operativo del host del cliente SSH sea Windows 10 versión 1803 (17134). Además, el dispositivo Windows 10 IoT Core debe ejecutar RS5 Windows Insider Preview versión 17723 o posterior.

El **cliente OpenSSH** se ha agregado a Windows 10 en 1803 (compilación 17134) como una característica opcional. Para instalar el cliente, puede buscar **administrar características opcionales** en la configuración de Windows 10. Si el **cliente OpenSSH** no aparece en la lista de características instaladas, elija **Agregar una característica**.

![Agregar una característica](../media/SSH/add_a_feature.png)

A continuación, seleccione **cliente OpenSSH** en la lista y haga clic en **instalar**.

![Instalación del cliente OpenSSH](../media/SSH/optional_features.png)

Para iniciar sesión con un nombre de usuario y una contraseña, use el siguiente comando:

```cmd
ssh administrator@host
```

Donde host es la dirección IP del dispositivo Windows IoT Core o el nombre del dispositivo.

La primera vez que se conecte, verá un mensaje similar al siguiente:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

Escriba **sí** y presione **entrar**.

Si necesita iniciar sesión como **DefaultAccount** en lugar de como administrador, debe generar una clave y usar la clave para iniciar sesión.  Desde el escritorio que quiere conectar a su dispositivo de IoT desde, abra una ventana de PowerShell y cambie a la carpeta de datos personales (por ejemplo, CD ~).

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

Registre la clave con ssh-agent (opcional, para la experiencia de inicio de sesión único).  Tenga en cuenta que ssh-add debe realizarse desde una carpeta que sea una ACL como el usuario con sesión iniciada (Builtin\Administrators y el usuario NT_AUTHORITY\System también son correctos).  De forma predeterminada, el CD ~ de PowerShell debe ser suficiente como se muestra a continuación.

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> Si recibe un mensaje que indica que el servicio ssh-agent está deshabilitado, puede habilitarlo con **SC. exe config ssh-agent Start = Auto**

Para habilitar el inicio de sesión único, anexe la clave pública al archivo **authorized_keys** de dispositivo Windows IOT Core.  O bien, si solo tiene una clave, copie el archivo de clave pública en el archivo **authorized_keys** remoto.

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

Si la clave no está registrada con ssh-agent, debe especificarse en la línea de comandos para iniciar sesión: 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

Si la clave privada está registrada con ssh-agent, solo tiene que especificar <strong>DefaultAccount@host</strong>:

```cmd
ssh DefaultAccount@host
```

La primera vez que se conecte, verá un mensaje similar al siguiente:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

Escriba **sí** y presione **entrar**.

Ahora debería estar conectado como **DefaultAccount**

Para usar el inicio de sesión único con la cuenta de **Administrador** , anexe la clave pública a c:\data\ProgramData\ssh\administrators_authorized_keys en el dispositivo Windows IOT Core. 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

También tendrá que establecer la ACL de administrators_authorized_keys para que coincida con la ACL de ssh_host_dsa_key en el mismo directorio.

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

Para establecer la ACL mediante PowerShell

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> Si ve un mensaje de **identificación de host remoto cambiado** después de realizar cambios en el dispositivo de Windows 10 IOT Core,\<Edite\.C:\Users username > ssh\known_hosts y quite el host que ha cambiado.

Consulte también: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>Usar PuTTy

### <a name="download-a-ssh-client"></a>Descarga de un cliente SSH
Para conectarse a su dispositivo mediante SSH, primero deberá descargar un cliente SSH, como [Putty](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).

### <a name="connect-to-your-device"></a>Conectarse al dispositivo
* Para conectarse a su dispositivo, primero debe obtener la dirección IP del dispositivo.  Después de arrancar el dispositivo Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo:

    ![DefaultApp en Windows IoT Core](../media/SSH/DefaultApp.png)

* Ahora, inicie Putty y escriba la dirección IP en `Host Name` el cuadro de texto y asegúrese `SSH` de que el botón de radio está seleccionado.  A continuación `Open`, haga clic en.

    ![Configuración de PuTTy](../media/SSH/putty_config.png)

* Si se va a conectar al dispositivo por primera vez desde el equipo, es posible que vea la alerta de seguridad siguiente.  Basta con `Yes` hacer clic para continuar.

    ![Alerta de seguridad de PuTTy](../media/SSH/putty_security_prompt.png)

* Si la conexión se realizó correctamente, debería ver `login as:` en la pantalla, donde se le pide que inicie sesión.  
    Escriba `Administrator` y presione Entrar.  A continuación, escriba la `p@ssw0rd` contraseña predeterminada como contraseña y presione Entrar.

    ![Inicio de sesión de PuTTy](../media/SSH/putty_login.png)

    Si ha podido iniciar sesión correctamente, debería ver algo parecido a esto:

    ![Consola de PuTTy](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>Actualizar contraseña de la cuenta

Se **recomienda encarecidamente** que actualice la contraseña predeterminada para la cuenta de administrador.

Para ello, escriba el siguiente comando en la consola de Putty y reemplace `[new password]` con una contraseña segura:
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a>Configuración del dispositivo de Windows IoT Core
* Para poder implementar aplicaciones desde Visual Studio 2017, tendrá que asegurarse de que el Visual Studio Remote Debugger se está ejecutando en el dispositivo de Windows IoT Core. El depurador remoto debe iniciarse automáticamente al arrancar el equipo. Para realizar una doble comprobación, use el comando Tlist para enumerar todos los procesos en ejecución de PowerShell. Debe haber dos instancias de msvsmon. exe en ejecución en el dispositivo.

* Es posible que el Visual Studio Remote Debugger agote el tiempo de espera después de largos períodos de inactividad. Si Visual Studio no se puede conectar al dispositivo de Windows IoT Core, intente reiniciar el dispositivo.

* Si lo desea, también puede cambiar el nombre del dispositivo. Para cambiar el nombre de equipo, use la `setcomputername` utilidad:

        setcomputername <new-name>

    Tendrá que reiniciar el dispositivo para que el cambio surta efecto. Puede usar el comando `shutdown` de la siguiente manera:

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a>Utilidades usadas comúnmente

Consulte la página de utilidades de la [línea de comandos](../manage-your-device/CommandLineUtils.md) para obtener una lista de comandos y utilidades que puede usar con SSH.
