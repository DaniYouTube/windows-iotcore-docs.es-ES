---
title: Protocolo de transferencia de archivos
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar File Transfer Protocol (FTP) para transferir archivos a y desde sus dispositivos.
keywords: Windows IOT, FTP, protocolo de transferencia de archivos, transferencia de archivos, dispositivos
ms.openlocfilehash: a15fdca4443b6fdc6e1b3aed49c16444bbe97a33
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918321"
---
# <a name="file-transfer-protocol"></a>Protocolo de transferencia de archivos
El File Transfer Protocol (FTP) permite transferir archivos desde y hacia el dispositivo de Windows 10 IoT Core.

> [!IMPORTANT]
> Por lo general, se recomienda usar FTP para que los desarrolladores puedan facilitar el proceso de desarrollo inicial. No se recomienda usar FTP en los dispositivos de venta directa.

## <a name="starting-the-ftp-server-on-your-device"></a>Inicio del servidor FTP en el dispositivo
* De forma predeterminada, el servidor FTP está deshabilitado en el dispositivo IoT Core.  Para iniciar el servidor FTP en el dispositivo, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md).
* Type `start C:\Windows\System32\ftpd.exe`
* Para comprobar que el servidor se está ejecutando, escriba `tlist`, que enumerará todos los procesos en ejecución.  Si el servidor FTP se está ejecutando, debería ver `ftpd.exe` en la lista.

![Inicio de FTP](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a>Detener el servidor FTP en el dispositivo<a name="stopftp"/>
* Para detener el servidor FTP en el dispositivo de IoT Core, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md).
* Si se conectó mediante PowerShell, escriba `kill -processname ftpd*` para detener el proceso FTP.

![Detención de PowerShell de FTP](../media/ftp/ftp_kill_powershell.png)

* Si se conectó mediante SSH, escriba `kill ftpd*` para detener el proceso FTP.

![Detención de SSH de FTP](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>Obtener acceso a los archivos a través de FTP
* El servidor FTP del dispositivo IoT Core se inicia automáticamente en el arranque.  Para conectarse a él, necesita la dirección IP del dispositivo.  Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.

![DefaultApp en Windows IoT Core](../media/ftp/DefaultApp.png)

* Una vez que tenga la dirección IP, abra el **Explorador de archivos** en su PC y escriba `ftp://<TARGET_DEVICE>`, donde `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo y presione Entrar.  Si se le solicita, escriba el nombre de usuario y la contraseña del administrador.

![Explorador FTP](../media/ftp/ftp_explorer.png)

* Ahora puede tener acceso a los archivos del dispositivo a través de FTP.

## <a name="changing-the-root-ftp-directory"></a>Cambiar el directorio raíz FTP
* De forma predeterminada, el servidor FTP muestra todas las carpetas del directorio raíz del dispositivo C:\\.  Para cambiar el directorio raíz, siga los mismos pasos para iniciar el servidor FTP, salvo que debe pasar el directorio raíz como un parámetro.
* Para cambiarlo, primero Conéctese a su dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md).
* [Detenga](#stopftp) el proceso FTP si ya se está ejecutando.
* Escriba `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como directorio raíz, como `C:\Users\DefaultAccount`.

![Parámetro FTP Start with](../media/ftp/ftp_start_parameter.png)

Ahora, cuando se conecte a su dispositivo a través de FTP, verá el contenido del directorio raíz que estableció.

![Explorador FTP con nuevo directorio raíz](../media/ftp/ftp_explorer_parameter.png)

Para que este cambio sea permanente, debe agregar una llamada a `start ftpd.exe <PATH_TO_DIRECTORY>` donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como directorio raíz, como `C:\Data\Users\DefaultAccount` en OEMCustomization. cmd y colocarlo en `C:\Windows\System32`
