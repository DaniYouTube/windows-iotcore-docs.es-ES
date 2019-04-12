---
title: Protocolo de transferencia de archivos
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar el protocolo de transferencia de archivos (FTP) para transferir archivos a y desde los dispositivos.
keywords: Protocolo de transferencia de archivos de Windows iot, FTP, transferencia de archivos, los dispositivos
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514432"
---
# <a name="file-transfer-protocol"></a>Protocolo de transferencia de archivos
El protocolo de transferencia de archivos (FTP) le permite transferir archivos a y desde el dispositivo Windows 10 IoT Core

> [!IMPORTANT]
> FTP se recomienda por lo general para que desarrolladores facilitar el proceso de desarrollo inicial. No se recomienda usar FTP en dispositivos de venta directa.

## <a name="starting-the-ftp-server-on-your-device"></a>Iniciar el servidor FTP en el dispositivo
* De forma predeterminada, el servidor FTP está deshabilitado en el dispositivo de IoT Core.  Para iniciar el servidor FTP en el dispositivo, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md).
* Tipo `start C:\Windows\System32\ftpd.exe`
* Puede comprobar que el servidor se está ejecutando escribiendo `tlist`, que enumera todos los procesos en ejecución.  Si se está ejecutando el servidor FTP, debería ver `ftpd.exe` en la lista.

![Inicio de FTP](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a>Detener el servidor FTP en el dispositivo<a name="stopftp"/>
* Para detener el servidor FTP en el dispositivo de IoT Core, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md).
* Si se conectó mediante PowerShell, escriba `kill -processname ftpd*` para detener el proceso FTP.

![Detención de PowerShell FTP](../media/ftp/ftp_kill_powershell.png)

* Si ha conectado mediante SSH, escriba `kill ftpd*` para detener el proceso FTP.

![Detención SSH de FTP](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a>Acceder a los archivos a través de FTP
* El servidor FTP en el dispositivo de IoT Core se inicia automáticamente en el arranque.  Para conectarse a él, necesita la dirección IP del dispositivo.  Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.

![DefaultApp en Windows IoT Core](../media/ftp/DefaultApp.png)

* Una vez que la dirección IP, abra **Explorador de archivos** en su PC y el tipo `ftp://<TARGET_DEVICE>`, donde `<TARGET_DEVICE>` es el nombre o la dirección IP de su dispositivo y, después, presione ENTRAR.  Si se le solicite, escriba el nombre de usuario administrador y la contraseña.

![Explorador FTP](../media/ftp/ftp_explorer.png)

* Ahora puede tener acceso a los archivos en el dispositivo a través de FTP.

## <a name="changing-the-root-ftp-directory"></a>Cambiar el directorio raíz FTP
* De forma predeterminada el FTP server muestra todas las carpetas en el directorio de raíz del dispositivo C:\\.  Para cambiar el directorio raíz, siga los mismos pasos para iniciar el servidor FTP, excepto que necesita pasar en el directorio raíz como un parámetro.
* Para cambiarlo, primero conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md).
* [Detener](#stopftp) el proceso FTP si ya se está ejecutando.
* Tipo `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como el directorio raíz, como `C:\Users\DefaultAccount`.

![Inicio de FTP con parámetros](../media/ftp/ftp_start_parameter.png)

Ahora, cuando se conecta al dispositivo a través de FTP, verá el contenido del directorio raíz que se establece.

![Explorador con el nuevo directorio raíz FTP](../media/ftp/ftp_explorer_parameter.png)

Con el fin de realizar este cambio permanente, deberá agregar una llamada a `start ftpd.exe <PATH_TO_DIRECTORY>` donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como el directorio raíz, como `C:\Data\Users\DefaultAccount` a OEMCustomization.cmd y colóquelo en `C:\Windows\System32`
