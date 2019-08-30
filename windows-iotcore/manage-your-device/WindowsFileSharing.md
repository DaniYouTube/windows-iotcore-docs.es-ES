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
# <a name="windows-file-sharing"></a><span data-ttu-id="3f120-104">Uso compartido de archivos de Windows</span><span class="sxs-lookup"><span data-stu-id="3f120-104">Windows file sharing</span></span>

<span data-ttu-id="3f120-105">Puede usar el uso compartido de archivos de Windows para transferir archivos hacia y desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3f120-105">You can use Windows file sharing to transfer files to and from your device.</span></span>

## <a name="accessing-your-files-using-windows-file-sharing"></a><span data-ttu-id="3f120-106">Acceder a los archivos mediante el uso compartido de archivos de Windows</span><span class="sxs-lookup"><span data-stu-id="3f120-106">Accessing your files using Windows file sharing</span></span>
* <span data-ttu-id="3f120-107">El servidor de uso compartido de archivos en el dispositivo Windows IoT Core se inicia automáticamente en el arranque.</span><span class="sxs-lookup"><span data-stu-id="3f120-107">The file sharing server on your Windows IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="3f120-108">Para conectarse a él, necesita la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3f120-108">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="3f120-109">Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3f120-109">You can find the IP address on the default app that boots when your device starts.</span></span>

    ![DefaultApp en Windows IoT Core](../media/WindowsFileSharing/DefaultApp.png)
    
* <span data-ttu-id="3f120-111">Una vez que tenga la IP, abra el **Explorador de archivos** en el equipo `\\<TARGET_DEVICE>\c$`y escriba `<TARGET_DEVICE>` , donde es el nombre o la dirección IP del dispositivo de Windows IOT Core y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="3f120-111">Once you have the IP, open up **File Explorer** on your computer and type `\\<TARGET_DEVICE>\c$`, where `<TARGET_DEVICE>` is either the name or the IP Address of your Windows IoT Core device, then hit Enter.</span></span>  

<span data-ttu-id="3f120-112">Si se le solicita, escriba el nombre de usuario y la contraseña del administrador.</span><span class="sxs-lookup"><span data-stu-id="3f120-112">Enter your administrator username and password if prompted.</span></span> <span data-ttu-id="3f120-113">El nombre de usuario debe tener el prefijo de la dirección IP del dispositivo de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="3f120-113">The username should be prefixed with the IP Address of your Windows IoT Core device.</span></span> <span data-ttu-id="3f120-114">Ejemplo: **Nombre** `192.168.1.118\Administrator`  **Contraseña:** `{your_password}`.</span><span class="sxs-lookup"><span data-stu-id="3f120-114">Example: **Username:** `192.168.1.118\Administrator`  **Password:** `{your_password}`.</span></span>

![Explorador de archivos](../media/WindowsFileSharing/smb_file_explorer.png)

* <span data-ttu-id="3f120-116">Ahora puede acceder a los archivos del dispositivo mediante el uso compartido de archivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="3f120-116">Now you can access the files on your device using Windows file sharing.</span></span>

## <a name="starting-and-stopping-the-file-sharing-server"></a><span data-ttu-id="3f120-117">Iniciar y detener el servidor de uso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="3f120-117">Starting and stopping the file sharing server</span></span>
* <span data-ttu-id="3f120-118">Conéctese al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [ssh](../connect-your-device/ssh.md).</span><span class="sxs-lookup"><span data-stu-id="3f120-118">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="3f120-119">De forma predeterminada, el servidor de uso compartido de archivos se inicia cuando se arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3f120-119">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="3f120-120">Para detener el servidor de uso compartido de archivos, escriba`net stop Server /y`</span><span class="sxs-lookup"><span data-stu-id="3f120-120">To stop the file sharing  server, type `net stop Server /y`</span></span>
* <span data-ttu-id="3f120-121">Para iniciar el servidor de uso compartido de archivos, escriba`net start Server`</span><span class="sxs-lookup"><span data-stu-id="3f120-121">To start the file sharing  server, type `net start Server`</span></span>

    ![Inicio y detención del servidor](../media/WindowsFileSharing/smb_start_stop.png)
    
## <a name="disabling-and-enabling-the-file-sharing-server-on-startup"></a><span data-ttu-id="3f120-123">Deshabilitar y habilitar el servidor de uso compartido de archivos en el inicio</span><span class="sxs-lookup"><span data-stu-id="3f120-123">Disabling and enabling the file sharing server on startup</span></span>
* <span data-ttu-id="3f120-124">Conéctese al dispositivo a través de [PowerShell](../connect-your-device/powershell.md) o [ssh](../connect-your-device/ssh.md).</span><span class="sxs-lookup"><span data-stu-id="3f120-124">Connect to your device through [PowerShell](../connect-your-device/powershell.md) or [SSH](../connect-your-device/ssh.md).</span></span>
* <span data-ttu-id="3f120-125">De forma predeterminada, el servidor de uso compartido de archivos se inicia cuando se arranca el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3f120-125">By default the file sharing  server is started when the device is booted.</span></span>
* <span data-ttu-id="3f120-126">Para deshabilitar el servidor de uso compartido de archivos para que no se inicie cuando se inicie el dispositivo, escriba`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span><span class="sxs-lookup"><span data-stu-id="3f120-126">To disable the file sharing  server so that it does not start when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x3 /f`</span></span>
* <span data-ttu-id="3f120-127">Para habilitar el servidor de uso compartido de archivos para que se inicie cuando se inicie el dispositivo, escriba`reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span><span class="sxs-lookup"><span data-stu-id="3f120-127">To enable the file sharing  server so that starts when the device starts, type `reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\lanmanserver /v Start /t REG_DWORD /d 0x2 /f`</span></span>

    ![Habilitar deshabilitar del servidor](../media/WindowsFileSharing/smb_enable_disable.png)
