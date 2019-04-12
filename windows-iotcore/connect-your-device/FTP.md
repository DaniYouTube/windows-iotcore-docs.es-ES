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
# <a name="file-transfer-protocol"></a><span data-ttu-id="5efce-104">Protocolo de transferencia de archivos</span><span class="sxs-lookup"><span data-stu-id="5efce-104">File Transfer Protocol</span></span>
<span data-ttu-id="5efce-105">El protocolo de transferencia de archivos (FTP) le permite transferir archivos a y desde el dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="5efce-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5efce-106">FTP se recomienda por lo general para que desarrolladores facilitar el proceso de desarrollo inicial.</span><span class="sxs-lookup"><span data-stu-id="5efce-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="5efce-107">No se recomienda usar FTP en dispositivos de venta directa.</span><span class="sxs-lookup"><span data-stu-id="5efce-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="5efce-108">Iniciar el servidor FTP en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="5efce-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="5efce-109">De forma predeterminada, el servidor FTP está deshabilitado en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5efce-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="5efce-110">Para iniciar el servidor FTP en el dispositivo, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="5efce-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="5efce-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="5efce-111">Type</span></span> `start C:\Windows\System32\ftpd.exe`
* <span data-ttu-id="5efce-112">Puede comprobar que el servidor se está ejecutando escribiendo `tlist`, que enumera todos los procesos en ejecución.</span><span class="sxs-lookup"><span data-stu-id="5efce-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="5efce-113">Si se está ejecutando el servidor FTP, debería ver `ftpd.exe` en la lista.</span><span class="sxs-lookup"><span data-stu-id="5efce-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![Inicio de FTP](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="5efce-115">Detener el servidor FTP en el dispositivo<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="5efce-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="5efce-116">Para detener el servidor FTP en el dispositivo de IoT Core, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="5efce-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="5efce-117">Si se conectó mediante PowerShell, escriba `kill -processname ftpd*` para detener el proceso FTP.</span><span class="sxs-lookup"><span data-stu-id="5efce-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![Detención de PowerShell FTP](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="5efce-119">Si ha conectado mediante SSH, escriba `kill ftpd*` para detener el proceso FTP.</span><span class="sxs-lookup"><span data-stu-id="5efce-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![Detención SSH de FTP](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="5efce-121">Acceder a los archivos a través de FTP</span><span class="sxs-lookup"><span data-stu-id="5efce-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="5efce-122">El servidor FTP en el dispositivo de IoT Core se inicia automáticamente en el arranque.</span><span class="sxs-lookup"><span data-stu-id="5efce-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="5efce-123">Para conectarse a él, necesita la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5efce-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="5efce-124">Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5efce-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![DefaultApp en Windows IoT Core](../media/ftp/DefaultApp.png)

* <span data-ttu-id="5efce-126">Una vez que la dirección IP, abra **Explorador de archivos** en su PC y el tipo `ftp://<TARGET_DEVICE>`, donde `<TARGET_DEVICE>` es el nombre o la dirección IP de su dispositivo y, después, presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="5efce-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="5efce-127">Si se le solicite, escriba el nombre de usuario administrador y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="5efce-127">Enter your administrator username and password if prompted.</span></span>

![Explorador FTP](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="5efce-129">Ahora puede tener acceso a los archivos en el dispositivo a través de FTP.</span><span class="sxs-lookup"><span data-stu-id="5efce-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="5efce-130">Cambiar el directorio raíz FTP</span><span class="sxs-lookup"><span data-stu-id="5efce-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="5efce-131">De forma predeterminada el FTP server muestra todas las carpetas en el directorio de raíz del dispositivo C:\\.</span><span class="sxs-lookup"><span data-stu-id="5efce-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="5efce-132">Para cambiar el directorio raíz, siga los mismos pasos para iniciar el servidor FTP, excepto que necesita pasar en el directorio raíz como un parámetro.</span><span class="sxs-lookup"><span data-stu-id="5efce-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="5efce-133">Para cambiarlo, primero conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [SSH](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="5efce-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="5efce-134">[Detener](#stopftp) el proceso FTP si ya se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="5efce-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="5efce-135">Tipo `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como el directorio raíz, como `C:\Users\DefaultAccount`.</span><span class="sxs-lookup"><span data-stu-id="5efce-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![Inicio de FTP con parámetros](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="5efce-137">Ahora, cuando se conecta al dispositivo a través de FTP, verá el contenido del directorio raíz que se establece.</span><span class="sxs-lookup"><span data-stu-id="5efce-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![Explorador con el nuevo directorio raíz FTP](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="5efce-139">Con el fin de realizar este cambio permanente, deberá agregar una llamada a `start ftpd.exe <PATH_TO_DIRECTORY>` donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como el directorio raíz, como `C:\Data\Users\DefaultAccount` a OEMCustomization.cmd y colóquelo en</span><span class="sxs-lookup"><span data-stu-id="5efce-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in</span></span> `C:\Windows\System32`
