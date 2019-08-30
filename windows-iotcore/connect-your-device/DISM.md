---
title: Usar DISM para Flash Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar DISM para Flash Windows 10 IoT Core en una tarjeta micro SD.
keywords: Windows IOT, DISM, administración de mantenimiento de imágenes de implementación, tarjeta SD, Flash, OS
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168941"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a><span data-ttu-id="71cba-104">Usar DISM para Flash Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="71cba-104">Use DISM to flash Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="71cba-105">No se admite el mantenimiento sin conexión de DISM.</span><span class="sxs-lookup"><span data-stu-id="71cba-105">DISM offline servicing isn't supported.</span></span> <span data-ttu-id="71cba-106">Recibirá el siguiente error si intenta montar un FFU para IoT Core: No se admite la solicitud.</span><span class="sxs-lookup"><span data-stu-id="71cba-106">You will receive the error below if you try to mount an FFU for IoT Core: The request is not supported.</span></span>
> <span data-ttu-id="71cba-107">La imagen no tiene un nombre y es probable que sea una FFU móvil/Onecore, que no se admite actualmente.</span><span class="sxs-lookup"><span data-stu-id="71cba-107">The image doesn't have a name and it's likely to be a Mobile/Onecore FFU, which is currently not supported.</span></span>
> <span data-ttu-id="71cba-108">Error de FfuMountImage # 160 con 0x80070032.</span><span class="sxs-lookup"><span data-stu-id="71cba-108">FfuMountImage#160 failed with 0x80070032.</span></span>

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a><span data-ttu-id="71cba-109">Un método alternativo al panel de IoT para hacer parpadear un FFU</span><span class="sxs-lookup"><span data-stu-id="71cba-109">An alternative method to IoT Dashboard for Flashing a FFU</span></span>

<span data-ttu-id="71cba-110">Puede usar administración y mantenimiento de imágenes de implementación (DISM. exe) para Flash Windows 10 IoT Core en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="71cba-110">You can use Deployment Image Servicing and Management(Dism.exe) to flash Windows 10 IoT Core on your SD card.</span></span> <span data-ttu-id="71cba-111">Necesitará un archivo de imagen FFU que se corresponda con el tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="71cba-111">You will need a FFU image file corresponding to your device type.</span></span> 

* <span data-ttu-id="71cba-112">Abra un símbolo del sistema de administrador y navegue hasta la carpeta que contiene el archivo Flash. FFU local.</span><span class="sxs-lookup"><span data-stu-id="71cba-112">Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.</span></span>

* <span data-ttu-id="71cba-113">Conecte la tarjeta SD al equipo.</span><span class="sxs-lookup"><span data-stu-id="71cba-113">Plug-in your SD card to your machine.</span></span> 

* <span data-ttu-id="71cba-114">Busque el número de disco que tiene la tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="71cba-114">Find the disk number that your SD card is on your computer.</span></span>  <span data-ttu-id="71cba-115">Se usará cuando la imagen se aplique en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="71cba-115">This will be used when the image is applied in the next step.</span></span>  <span data-ttu-id="71cba-116">Para ello, puede usar la utilidad Diskpart.</span><span class="sxs-lookup"><span data-stu-id="71cba-116">To do this, you can use the diskpart utility.</span></span>  <span data-ttu-id="71cba-117">Ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="71cba-117">Run the following commands:</span></span>

        c:\FFUFolder>diskpart

        DISKPART>list disk

    <span data-ttu-id="71cba-118">Debería mostrar todos los dispositivos de almacenamiento conectados al equipo.</span><span class="sxs-lookup"><span data-stu-id="71cba-118">It should list all the storage devices attached to the computer.</span></span> 

    ![Disco de lista de DISM](../media/Dism/DiskpartListDisk.png)

    <span data-ttu-id="71cba-120">Anote el número de disco y escriba Exit para salir de Diskpart.</span><span class="sxs-lookup"><span data-stu-id="71cba-120">Note the disk number and type exit to exit diskpart.</span></span> 

        DISKPART>exit

* <span data-ttu-id="71cba-121">Con el símbolo del sistema de administrador, aplique la imagen a la tarjeta SD ejecutando el siguiente comando (Asegúrese de reemplazar PhysicalDriveN por el valor que encontró en el paso anterior, por ejemplo, en este caso, la tarjeta SD es el número de disco 4, `/ApplyDrive:\\.\PhysicalDrive4` por lo que usaremos menor</span><span class="sxs-lookup"><span data-stu-id="71cba-121">Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use  `/ApplyDrive:\\.\PhysicalDrive4` below)</span></span>

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* <span data-ttu-id="71cba-122">Haga clic en el icono "quitar hardware de forma segura" en la bandeja de tareas y seleccione el lector de tarjetas USB SD para quitarlo del sistema de forma segura.</span><span class="sxs-lookup"><span data-stu-id="71cba-122">Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system.</span></span>  <span data-ttu-id="71cba-123">Si no lo hace, puede provocar daños en la imagen.</span><span class="sxs-lookup"><span data-stu-id="71cba-123">Failing to do this can cause corruption of the image.</span></span>
