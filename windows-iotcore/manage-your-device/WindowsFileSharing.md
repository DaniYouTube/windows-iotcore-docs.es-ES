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
# <a name="windows-file-sharing"></a><span data-ttu-id="f328f-104">Uso compartido de archivos de Windows</span><span class="sxs-lookup"><span data-stu-id="f328f-104">Windows file sharing</span></span>

<span data-ttu-id="f328f-105">Puede utilizar el uso compartido de archivos de Windows para transferir archivos a y desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f328f-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="f328f-106">Acceder a los archivos de uso compartido de archivos de Windows</span><span class="sxs-lookup"><span data-stu-id="f328f-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="f328f-107">El archivo de uso compartido de servidor en el dispositivo Windows IoT Core se inicia automáticamente en el arranque.</span><span class="sxs-lookup"><span data-stu-id="f328f-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="f328f-108">Para conectarse a él, necesita la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f328f-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="f328f-109">Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f328f-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![DefaultApp en Windows IoT Core](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="f328f-111">Una vez que la dirección IP, abra **Explorador de archivos** en su equipo y escriba `\\<TARGET_DEVICE>\c$`, donde `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo Windows IoT Core, a continuación, presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="f328f-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="f328f-112">Si se le solicite, escriba el nombre de usuario administrador y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="f328f-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="f328f-113">Debe agregarse como prefijo el nombre de usuario con la dirección IP del dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="f328f-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="f328f-114">Por ejemplo: **Nombre de usuario:** `192.168.1.118\Administrator`  **Contraseña:** `{your_password}`.</span><span class="sxs-lookup"><span data-stu-id="f328f-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![Explorador de archivos](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="f328f-116">Ahora puede tener acceso a los archivos en el dispositivo mediante el uso compartido de archivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="f328f-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="f328f-117">Iniciar y detener el uso compartido de servidor de archivos</span><span class="sxs-lookup"><span data-stu-id="f328f-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="f328f-118">Conectarse al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [SSH](../connect-your-device/ssh.md).</span><span class="sxs-lookup"><span data-stu-id="f328f-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="f328f-119">De forma predeterminada, el uso compartido de servidor de archivos se inicia cuando se arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f328f-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="f328f-120">Para detener el uso compartido de servidor de archivos, escriba</span><span class="sxs-lookup"><span data-stu-id="f328f-120">To stop the file sharing  server, type</span></span> `net stop Server /y`
* <span data-ttu-id="f328f-121">Para iniciar el uso compartido de servidor de archivos, escriba</span><span class="sxs-lookup"><span data-stu-id="f328f-121">To start the file sharing  server, type</span></span> `net start Server`

    ![Detención e inicio del servidor](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="f328f-123">Deshabilitar y habilitar el uso compartido de servidor en el inicio de archivos</span><span class="sxs-lookup"><span data-stu-id="f328f-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="f328f-124">Conectarse al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [SSH](../connect-your-device/ssh.md).</span><span class="sxs-lookup"><span data-stu-id="f328f-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="f328f-125">De forma predeterminada, el uso compartido de servidor de archivos se inicia cuando se arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f328f-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="f328f-126">Para deshabilitar el archivo de uso compartido de servidor para que no se inicia cuando se inicia el dispositivo, escriba</span><span class="sxs-lookup"><span data-stu-id="f328f-126">To disable the file sharing  server so that it does not start when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`
* <span data-ttu-id="f328f-127">Para habilitar el archivo de uso compartido de servidor para se inicia cuando se inicia el dispositivo, escriba</span><span class="sxs-lookup"><span data-stu-id="f328f-127">To enable the file sharing  server so that starts when the device starts, type</span></span> `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`

    ![Habilitar deshabilitar el servidor](../media/WindowsFileSharing/smb_enable_disable.png)
