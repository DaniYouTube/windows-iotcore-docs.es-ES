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
# <a name="secure-shell-ssh"></a>Secure Shell (SSH)
Shell seguro (SSH) le permite administrar de forma remota y configurar el dispositivo Windows IoT Core

## <a name="using-the-windows-10-openssh-client"></a>Mediante el cliente de Windows 10 OpenSSH
> [!IMPORTANT]
> El cliente OpenSSH Windows requiere que el host del cliente SSH del sistema operativo es Windows 10 versión 1803(17134). Además, el dispositivo Windows 10 IoT Core debe ejecutar RS5 Windows Insider Preview versión 17723 o superior.

El **cliente OpenSSH** se agregó a Windows 10 en 1803 (compilación 17134) como una característica opcional. Para instalar el cliente puede buscar **administrar características opcionales** en configuración de Windows 10. Si el **cliente OpenSSH** no aparece en la lista de las características instaladas, a continuación, elija **agregar una característica**.

![Agregar una característica](../media/SSH/add_a_feature.png)

A continuación, seleccione **cliente OpenSSH** en la lista y haga clic en **instalar**.

![Instalación de cliente OpenSSH](../media/SSH/optional_features.png)

Para iniciar sesión con una nombre de usuario y contraseña, use el siguiente comando:

```cmd
ssh administrator@host
```

Donde host es la dirección IP del dispositivo Windows IoT Core o el nombre del dispositivo.

La primera vez que conecte verá un mensaje similar al siguiente:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

Tipo **Sí** y presione **escriba**.

Si tiene que iniciar sesión como **DefaultAccount** en lugar de como administrador deberá generar una clave y usar la clave para iniciar sesión.  En el escritorio que pretende conectarse al dispositivo de IoT, abra una ventana de powershell y cambie a la carpeta datos personales (p. ej. cd ~)

```cmd
cd ~
ssh-keygen -t rsa -f id_rsa
```

Registre la clave con ssh-agent (opcional, para la experiencia de inicio de sesión único).  Tenga en cuenta que ssh-agregar debe realizarse desde una carpeta que sea incorporarse a usted como la sesión de usuario (Builtin\Administrators y el usuario NT_AUTHORITY\System también son Aceptar).  CD predeterminado ~ desde powershell debe ser suficiente, ya que se muestra a continuación.

```cmd
cd ~
net start ssh-agent
ssh-add id_rsa
```

> [!TIP]
> Si recibe un mensaje que se ha deshabilitado el servicio ssh-agent puede habilitarla con **inicio ssh-agent de sc.exe config = auto**

Para habilitar el inicio de sesión único anexa la clave pública en el dispositivo Windows IoT Core **authorized_keys** archivo.  O si solo tiene una clave copie el archivo de clave pública en el servidor remoto **authorized_keys** archivo.

```cmd
net use X: \\host\c$ /user:host\administrator
if not exist x:\data\users\defaultaccount\.ssh md x:\data\users\defaultaccount\.ssh
copy .\id_rsa.pub x:\data\users\defaultaccount\.ssh\authorized_keys
```

Si la clave no está registrada con ssh-agent debe especificarse en la línea de comandos para el inicio de sesión: 

```cmd
ssh -i .\id_rsa DefaultAccount@host
```

Si se registra la clave privada con ssh-agent, solo deberá especificar <strong>DefaultAccount@host</strong>:

```cmd
ssh DefaultAccount@host
```

La primera vez que conecte verá un mensaje similar al siguiente:

```cmd
The authenticity of host 'hostname (192.168.0.12)' can't be established.
ECDSA key fingerprint is SHA256:RahZpBFpecRiPmw8NGSa+7VKs8mgqQi/j2i1Qr9lUNU.
Are you sure you want to continue connecting (yes/no)?
```

Tipo **Sí** y presione **escriba**.

Debe estar conectado como **DefaultAccount**

Usar inicio de sesión único con el **administrador** cuenta, la clave pública se anexa al c:\data\ProgramData\ssh\administrators_authorized_keys en el dispositivo Windows IoT Core. 

```cmd
net use X: \\host\c$ /user:host\administrator
copy .\id_rsa.pub x:\data\ProgramData\ssh\administrators_authorized_keys
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icaclsx:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

También deberá establecer la ACL para administrators_authorized_keys para que coincida con la ACL de ssh_host_dsa_key en el mismo directorio.

```cmd
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /remove "NT AUTHORITY\Authenticated Users"
icacls x:\data\ProgramData\ssh\administrators_authorized_keys /inheritance:r
```

Para establecer la ACL mediante powershell

```cmd
get-acl x:\data\ProgramData\ssh\ssh_host_dsa_key | set-acl x:\data\ProgramData\ssh\administrators_authorized_keys
```

> [!NOTE]
> Si ve un **CAMBIADO de identificación del HOST remoto** mensaje después de realizar cambios en el dispositivo Windows 10 IoT Core, a continuación, editar C:\Users\<username >\.ssh\known_hosts y quitar el host que ha cambiado.

Consulte también: [Win32-OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/ssh.exe-examples)

## <a name="using-putty"></a>Uso de PuTTY

### <a name="download-a-ssh-client"></a>Descargar a un cliente SSH
Para conectarse a su dispositivo mediante SSH, primero debe descargar un cliente SSH, como [PuTTY](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe).

### <a name="connect-to-your-device"></a>Conectarse al dispositivo
* Para conectarse al dispositivo, deberá primero obtener la dirección IP del dispositivo.  Después de arrancar el dispositivo Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo:

    ![DefaultApp en Windows IoT Core](../media/SSH/DefaultApp.png)

* Ahora inicie PuTTY y escriba la dirección IP en el `Host Name` cuadro de texto y asegúrese de que el `SSH` botón de radio está seleccionado.  A continuación, haga clic en `Open`.

    ![Configuración de puTTY](../media/SSH/putty_config.png)

* Si se conecta al dispositivo por primera vez desde su equipo, verá la siguiente alerta de seguridad.  Simplemente haga clic en `Yes` para continuar.

    ![Alerta de seguridad de puTTY](../media/SSH/putty_security_prompt.png)

* Si la conexión se realizó correctamente, debería ver `login as:` en la pantalla, que le solicitará que inicie sesión.  
    Escriba `Administrator` y presione ENTRAR.  A continuación, escriba la contraseña predeterminada `p@ssw0rd` como la contraseña y presione ENTRAR.

    ![Inicio de sesión de puTTY](../media/SSH/putty_login.png)

    Si puede iniciar sesión correctamente, debería ver algo parecido a esto:

    ![Consola de puTTY](../media/ssh/putty_console.png)

### <a name="update-account-password"></a>Actualizar la contraseña de cuenta

Es **recomienda** que actualizar la contraseña predeterminada para la cuenta de administrador.

Para ello, escriba el siguiente comando en la consola de PuTTY, reemplazando `[new password]` con una contraseña segura:
    
    net user Administrator [new password]
    
### <a name="configure-your-windows-iot-core-device"></a>Configurar el dispositivo Windows IoT Core
* Para poder implementar aplicaciones desde Visual Studio 2017, deberá asegurarse de que se está ejecutando Visual Studio Remote Debugger en el dispositivo Windows IoT Core. El depurador remoto debe ejecutarse automáticamente en tiempo de arranque de la máquina. Para volver a comprobar, use el comando de tlist para enumerar todos los procesos de ejecución de powershell. Debe haber dos instancias de msvsmon.exe que se ejecutan en el dispositivo.

* Es posible que el depurador remoto de Visual Studio en tiempo de espera tras un largo período de inactividad. Si Visual Studio no puede conectarse a su dispositivo Windows IoT Core, intente reiniciar el dispositivo.

* Si lo desea, también puede cambiar el nombre del dispositivo. Para cambiar el nombre del equipo, use el `setcomputername` utilidad:

        setcomputername <new-name>

    Deberá reiniciar el dispositivo para que el cambio surta efecto. Puede usar el `shutdown` comando como sigue:

        shutdown /r /t 0
        
### <a name="commonly-used-utilities"></a>Frecuente utilidades

Consulte la [utilidades de línea de comandos](../manage-your-device/CommandLineUtils.md) para obtener una lista de comandos y utilidades que puede utilizar con SSH.
