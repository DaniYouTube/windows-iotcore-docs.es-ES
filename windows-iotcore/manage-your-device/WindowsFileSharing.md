---
title: Uso compartido de archivos de Windows
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar el uso compartido de archivos de Windows para transferir archivos hacia y desde el dispositivo.
keywords: Windows IOT, transferencia de archivos, recurso compartido de archivos, uso compartido de archivos de Windows
ms.openlocfilehash: 00dc17ded4b9c4fbea05faca794766f965d0632a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170402"
---
# <a name="windows-file-sharing"></a>Uso compartido de archivos de Windows

Puede usar el uso compartido de archivos de Windows para transferir archivos hacia y desde el dispositivo.

## <a name="accessing-your-files-using-windows-file-sharing"></a>Acceder a los archivos mediante el uso compartido de archivos de Windows
* El servidor de uso compartido de archivos en el dispositivo Windows IoT Core se inicia automáticamente en el arranque.  Para conectarse a él, necesita la dirección IP del dispositivo.  Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.

    ![DefaultApp en Windows IoT Core](../media/WindowsFileSharing/DefaultApp.png)
    
* Una vez que tenga la IP, abra el **Explorador de archivos** en el equipo `\\<TARGET_DEVICE>\c$`y escriba `<TARGET_DEVICE>` , donde es el nombre o la dirección IP del dispositivo de Windows IOT Core y presione Entrar.  

Si se le solicita, escriba el nombre de usuario y la contraseña del administrador. El nombre de usuario debe tener el prefijo de la dirección IP del dispositivo de Windows IoT Core. Ejemplo: **Nombre** `192.168.1.118\Administrator`  **Contraseña:** `{your_password}`.

![Explorador de archivos](../media/WindowsFileSharing/smb_file_explorer.png)

* Ahora puede acceder a los archivos del dispositivo mediante el uso compartido de archivos de Windows.

## <a name="starting-and-stopping-the-file-sharing-server"></a>Iniciar y detener el servidor de uso compartido de archivos
* Conéctese al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [ssh](../connect-your-device/ssh.md).
* De forma predeterminada, el servidor de uso compartido de archivos se inicia cuando se arranca el dispositivo.
* Para detener el servidor de uso compartido de archivos, escriba`net stop Server /y`
* Para iniciar el servidor de uso compartido de archivos, escriba`net start Server`

    ![Inicio y detención del servidor](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a>Deshabilitar y habilitar el servidor de uso compartido de archivos en el inicio
* Conéctese al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [ssh](../connect-your-device/ssh.md).
* De forma predeterminada, el servidor de uso compartido de archivos se inicia cuando se arranca el dispositivo.
* Para deshabilitar el servidor de uso compartido de archivos para que no se inicie cuando se inicie el dispositivo, escriba`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* Para habilitar el servidor de uso compartido de archivos para que se inicie cuando se inicie el dispositivo, escriba`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![Habilitar deshabilitar del servidor](../media/WindowsFileSharing/smb_enable_disable.png)
