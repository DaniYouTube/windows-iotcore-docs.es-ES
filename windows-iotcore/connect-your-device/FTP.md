---
title: Protocolo de transferencia de archivos
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar File Transfer Protocol (FTP) para transferir archivos a y desde sus dispositivos.
keywords: Windows IOT, FTP, protocolo de transferencia de archivos, transferencia de archivos, dispositivos
ms.openlocfilehash: 43a64e186c2e783624bb47b89e4fa6322c93e04d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169192"
---
# <a name="file-transfer-protocol"></a><span data-ttu-id="a75c4-104">Protocolo de transferencia de archivos</span><span class="sxs-lookup"><span data-stu-id="a75c4-104">File Transfer Protocol</span></span>
<span data-ttu-id="a75c4-105">El File Transfer Protocol (FTP) permite transferir archivos desde y hacia el dispositivo de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="a75c4-105">The File Transfer Protocol (FTP) allows you to transfer files to and from your Windows 10 IoT Core device</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a75c4-106">Por lo general, se recomienda usar FTP para que los desarrolladores puedan facilitar el proceso de desarrollo inicial.</span><span class="sxs-lookup"><span data-stu-id="a75c4-106">FTP is recommended generally for developers to ease the initial development process.</span></span> <span data-ttu-id="a75c4-107">No se recomienda usar FTP en los dispositivos de venta directa.</span><span class="sxs-lookup"><span data-stu-id="a75c4-107">We do not recommend using FTP in retail devices.</span></span>

## <a name="starting-the-ftp-server-on-your-device"></a><span data-ttu-id="a75c4-108">Inicio del servidor FTP en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="a75c4-108">Starting the FTP server on your device</span></span>
* <span data-ttu-id="a75c4-109">De forma predeterminada, el servidor FTP está deshabilitado en el dispositivo IoT Core.</span><span class="sxs-lookup"><span data-stu-id="a75c4-109">By default, the FTP server is disabled on your IoT Core device.</span></span>  <span data-ttu-id="a75c4-110">Para iniciar el servidor FTP en el dispositivo, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="a75c4-110">In order to start the FTP server on your device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="a75c4-111">Type `start C:\Windows\System32\ftpd.exe`</span><span class="sxs-lookup"><span data-stu-id="a75c4-111">Type `start C:\Windows\System32\ftpd.exe`</span></span>
* <span data-ttu-id="a75c4-112">Para comprobar que el servidor se está ejecutando, escriba `tlist`, que enumerará todos los procesos en ejecución.</span><span class="sxs-lookup"><span data-stu-id="a75c4-112">You can check that the server is running by typing `tlist`, which will list all the running processes.</span></span>  <span data-ttu-id="a75c4-113">Si el servidor FTP se está ejecutando, debería ver `ftpd.exe` en la lista.</span><span class="sxs-lookup"><span data-stu-id="a75c4-113">If the FTP server is running, you should see `ftpd.exe` in the list.</span></span>

![Inicio de FTP](../media/ftp/ftp_start.png)

## <a name="stopping-the-ftp-server-on-your-devicea-namestopftp"></a><span data-ttu-id="a75c4-115">Detención del servidor FTP en el dispositivo<a name="stopftp"/></span><span class="sxs-lookup"><span data-stu-id="a75c4-115">Stopping the FTP server on your device<a name="stopftp"/></span></span>
* <span data-ttu-id="a75c4-116">Para detener el servidor FTP en el dispositivo de IoT Core, primero debe conectarse al dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="a75c4-116">In order to stop the FTP server on your IoT Core device, first you need to connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="a75c4-117">Si se conectó mediante PowerShell, escriba `kill -processname ftpd*` para detener el proceso FTP.</span><span class="sxs-lookup"><span data-stu-id="a75c4-117">If you connected using PowerShell, type `kill -processname ftpd*` to stop the FTP process.</span></span>

![Detención de PowerShell de FTP](../media/ftp/ftp_kill_powershell.png)

* <span data-ttu-id="a75c4-119">Si se conectó mediante SSH, escriba `kill ftpd*` para detener el proceso FTP.</span><span class="sxs-lookup"><span data-stu-id="a75c4-119">If you connected using SSH, type `kill ftpd*` to stop the FTP process.</span></span>

![Detención de SSH de FTP](../media/ftp/ftp_kill_ssh.png)

## <a name="accessing-your-files-over-ftp"></a><span data-ttu-id="a75c4-121">Obtener acceso a los archivos a través de FTP</span><span class="sxs-lookup"><span data-stu-id="a75c4-121">Accessing your files over FTP</span></span>
* <span data-ttu-id="a75c4-122">El servidor FTP del dispositivo IoT Core se inicia automáticamente en el arranque.</span><span class="sxs-lookup"><span data-stu-id="a75c4-122">The FTP server on your IoT Core device starts automatically on boot.</span></span>  <span data-ttu-id="a75c4-123">Para conectarse a él, necesita la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a75c4-123">In order to connect to it, you need the IP address of your device.</span></span>  <span data-ttu-id="a75c4-124">Puede encontrar la dirección IP en la aplicación predeterminada que se inicia cuando se inicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a75c4-124">You can find the IP address on the default app that boots when your device starts.</span></span>

![DefaultApp en Windows IoT Core](../media/ftp/DefaultApp.png)

* <span data-ttu-id="a75c4-126">Una vez que tenga la IP, abra el **Explorador de archivos** en su PC `ftp://<TARGET_DEVICE>`y escriba `<TARGET_DEVICE>` , donde es el nombre o la dirección IP del dispositivo y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="a75c4-126">Once you have the IP, open up **File Explorer** on your PC and type `ftp://<TARGET_DEVICE>`, where `<TARGET_DEVICE>` is either the name or the IP address of your device, then hit Enter.</span></span>  <span data-ttu-id="a75c4-127">Si se le solicita, escriba el nombre de usuario y la contraseña del administrador.</span><span class="sxs-lookup"><span data-stu-id="a75c4-127">Enter your administrator username and password if prompted.</span></span>

![Explorador FTP](../media/ftp/ftp_explorer.png)

* <span data-ttu-id="a75c4-129">Ahora puede tener acceso a los archivos del dispositivo a través de FTP.</span><span class="sxs-lookup"><span data-stu-id="a75c4-129">Now you can access the files on your device through FTP.</span></span>

## <a name="changing-the-root-ftp-directory"></a><span data-ttu-id="a75c4-130">Cambiar el directorio raíz FTP</span><span class="sxs-lookup"><span data-stu-id="a75c4-130">Changing the root FTP directory</span></span>
* <span data-ttu-id="a75c4-131">De forma predeterminada, el servidor FTP muestra todas las carpetas del directorio raíz del dispositivo C\\:.</span><span class="sxs-lookup"><span data-stu-id="a75c4-131">By default the FTP server displays all the folders in the device's root directory C:\\.</span></span>  <span data-ttu-id="a75c4-132">Para cambiar el directorio raíz, siga los mismos pasos para iniciar el servidor FTP, salvo que debe pasar el directorio raíz como un parámetro.</span><span class="sxs-lookup"><span data-stu-id="a75c4-132">In order to change the root directory, follow the same steps to start the FTP server, except you need to pass in the root directory as a parameter.</span></span>
* <span data-ttu-id="a75c4-133">Para cambiarlo, primero Conéctese a su dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md) o [ssh](../connect-your-device/SSH.md).</span><span class="sxs-lookup"><span data-stu-id="a75c4-133">In order to change it, first connect to your device through [PowerShell](../connect-your-device/PowerShell.md) or [SSH](../connect-your-device/SSH.md).</span></span>
* <span data-ttu-id="a75c4-134">[Detenga](#stopftp) el proceso FTP si ya se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="a75c4-134">[Stop](#stopftp) the FTP process if it's already running.</span></span>
* <span data-ttu-id="a75c4-135">Escriba `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como directorio `C:\Users\DefaultAccount`raíz, como.</span><span class="sxs-lookup"><span data-stu-id="a75c4-135">Type `start C:\Windows\System32\ftpd.exe <PATH_TO_DIRECTORY>`, where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Users\DefaultAccount`.</span></span>

![Parámetro FTP Start with](../media/ftp/ftp_start_parameter.png)

<span data-ttu-id="a75c4-137">Ahora, cuando se conecte a su dispositivo a través de FTP, verá el contenido del directorio raíz que estableció.</span><span class="sxs-lookup"><span data-stu-id="a75c4-137">Now when you connect to your device through FTP, you will see the contents of the root directory you set.</span></span>

![Explorador FTP con nuevo directorio raíz](../media/ftp/ftp_explorer_parameter.png)

<span data-ttu-id="a75c4-139">Para que este cambio sea permanente, debe agregar una llamada a `start ftpd.exe <PATH_TO_DIRECTORY>` , donde `<PATH_TO_DIRECTORY>` es la ruta de acceso absoluta al directorio que desea establecer como directorio `C:\Data\Users\DefaultAccount` raíz, como OEMCustomization. cmd y colocarlo en`C:\Windows\System32`</span><span class="sxs-lookup"><span data-stu-id="a75c4-139">In order to make this change permanent, you need to add a call to `start ftpd.exe <PATH_TO_DIRECTORY>` where `<PATH_TO_DIRECTORY>` is the absolute path to the directory you want to set as the root directory, such as `C:\Data\Users\DefaultAccount` to OEMCustomization.cmd and place it in `C:\Windows\System32`</span></span>
