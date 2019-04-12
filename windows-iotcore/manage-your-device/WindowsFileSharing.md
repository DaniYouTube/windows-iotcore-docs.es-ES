---
title: Uso compartido de archivos de Windows
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo utilizar el uso compartido de archivos de Windows para transferir archivos a y desde el dispositivo.
keywords: Windows iot, transferencia de archivos, recurso compartido de archivos, el uso compartido de archivos de windows
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515036"
---
# <a name="windows-file-sharing"></a>Uso compartido de archivos de Windows

Puede utilizar el uso compartido de archivos de Windows para transferir archivos a y desde el dispositivo.

## <a name="accessing-your-files-using-windows-file-sharing"></a>Acceder a los archivos de uso compartido de archivos de Windows
* El archivo de uso compartido de servidor en el dispositivo Windows IoT Core se inicia automáticamente en el arranque.  Para conectarse a él, necesita la dirección IP del dispositivo.  Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.

    ![DefaultApp en Windows IoT Core](../media/WindowsFileSharing/DefaultApp.png)
    
* Una vez que la dirección IP, abra **Explorador de archivos** en su equipo y escriba `\\<TARGET_DEVICE>\c$`, donde `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo Windows IoT Core, a continuación, presione ENTRAR.  

Si se le solicite, escriba el nombre de usuario administrador y la contraseña. Debe agregarse como prefijo el nombre de usuario con la dirección IP del dispositivo Windows IoT Core. Por ejemplo: **Nombre de usuario:** `192.168.1.118\Administrator`  **Contraseña:** `{your_password}`.

![Explorador de archivos](../media/WindowsFileSharing/smb_file_explorer.png)

* Ahora puede tener acceso a los archivos en el dispositivo mediante el uso compartido de archivos de Windows.

## <a name="starting-and-stopping-the-file-sharing-server"></a>Iniciar y detener el uso compartido de servidor de archivos
* Conectarse al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [SSH](../connect-your-device/ssh.md).
* De forma predeterminada, el uso compartido de servidor de archivos se inicia cuando se arranca el dispositivo.
* Para detener el uso compartido de servidor de archivos, escriba `net stop Server /y`
* Para iniciar el uso compartido de servidor de archivos, escriba `net start Server`

    ![Detención e inicio del servidor](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>Deshabilitar y habilitar el uso compartido de servidor en el inicio de archivos
* Conectarse al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [SSH](../connect-your-device/ssh.md).
* De forma predeterminada, el uso compartido de servidor de archivos se inicia cuando se arranca el dispositivo.
* Para deshabilitar el archivo de uso compartido de servidor para que no se inicia cuando se inicia el dispositivo, escriba `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* Para habilitar el archivo de uso compartido de servidor para se inicia cuando se inicia el dispositivo, escriba `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![Habilitar deshabilitar el servidor](../media/WindowsFileSharing/smb_enable_disable.png)
