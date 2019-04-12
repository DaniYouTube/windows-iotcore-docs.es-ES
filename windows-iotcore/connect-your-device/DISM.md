---
title: Use DISM para flash de Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar DISM para flash de Windows 10 IoT Core en un tarjeta SD micro.
keywords: Windows iot, DISM, administración de mantenimiento de imágenes implementación, tarjeta SD, flash, sistema operativo
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515234"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a><span data-ttu-id="de062-104">Use DISM para flash de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="de062-104">Use DISM to flash Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="de062-105">No se admite el mantenimiento sin conexión de DISM.</span><span class="sxs-lookup"><span data-stu-id="de062-105">DISM offline servicing isn't supported.</span></span> <span data-ttu-id="de062-106">Si intenta montar un FFU para IoT Core, recibirá el siguiente error: No se admite la solicitud.</span><span class="sxs-lookup"><span data-stu-id="de062-106">You will receive the error below if you try to mount an FFU for IoT Core: The request is not supported.</span></span>
> <span data-ttu-id="de062-107">La imagen no tiene un nombre y es probable que sea un FFU Mobile/Onecore, que no se admite actualmente.</span><span class="sxs-lookup"><span data-stu-id="de062-107">The image doesn't have a name and it's likely to be a Mobile/Onecore FFU, which is currently not supported.</span></span>
> <span data-ttu-id="de062-108">Error 0 x 80070032 FfuMountImage #160.</span><span class="sxs-lookup"><span data-stu-id="de062-108">FfuMountImage#160 failed with 0x80070032.</span></span>

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a><span data-ttu-id="de062-109">Un método alternativo para el panel de IoT de intermitencia en un FFU</span><span class="sxs-lookup"><span data-stu-id="de062-109">An alternative method to IoT Dashboard for Flashing a FFU</span></span>

<span data-ttu-id="de062-110">Puede usar Management(Dism.exe) y mantenimiento de imágenes de implementación para Windows 10 IoT Core en la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="de062-110">You can use Deployment Image Servicing and Management(Dism.exe) to flash Windows 10 IoT Core on your SD card.</span></span> <span data-ttu-id="de062-111">Necesitará un archivo de imagen FFU correspondiente al tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="de062-111">You will need a FFU image file corresponding to your device type.</span></span> 

* <span data-ttu-id="de062-112">Abra un símbolo del sistema de administrador y navegue hasta la carpeta que contiene el archivo flash.ffu local.</span><span class="sxs-lookup"><span data-stu-id="de062-112">Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.</span></span>

* <span data-ttu-id="de062-113">Complemento tarjeta la SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="de062-113">Plug-in your SD card to your machine.</span></span> 

* <span data-ttu-id="de062-114">Buscar el número de disco que se encuentra la tarjeta SD en el equipo.</span><span class="sxs-lookup"><span data-stu-id="de062-114">Find the disk number that your SD card is on your computer.</span></span>  <span data-ttu-id="de062-115">Se usará cuando se aplica la imagen en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="de062-115">This will be used when the image is applied in the next step.</span></span>  <span data-ttu-id="de062-116">Para ello, puede usar la utilidad diskpart.</span><span class="sxs-lookup"><span data-stu-id="de062-116">To do this, you can use the diskpart utility.</span></span>  <span data-ttu-id="de062-117">Ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="de062-117">Run the following commands:</span></span>

        c:\FFUFolder>diskpart

        DISKPART>list disk

    <span data-ttu-id="de062-118">Deben enumerar todos los dispositivos de almacenamiento conectados al equipo.</span><span class="sxs-lookup"><span data-stu-id="de062-118">It should list all the storage devices attached to the computer.</span></span> 

    ![Disco de la lista DISM](../media/Dism/DiskpartListDisk.png)

    <span data-ttu-id="de062-120">Tenga en cuenta el número de disco y escriba diskpart exit para salir.</span><span class="sxs-lookup"><span data-stu-id="de062-120">Note the disk number and type exit to exit diskpart.</span></span> 

        DISKPART>exit

* <span data-ttu-id="de062-121">Mediante el símbolo del sistema de administrador, aplique la imagen a la tarjeta SD, ejecute el comando siguiente (no olvide reemplazar PhysicalDriveN con el valor que se encuentra en el paso anterior, por ejemplo, en este caso tarjeta SD es el número de disco 4, por lo que usaremos `/ApplyDrive:\\.\PhysicalDrive4` a continuación)</span><span class="sxs-lookup"><span data-stu-id="de062-121">Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use  `/ApplyDrive:\\.\PhysicalDrive4` below)</span></span>

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* <span data-ttu-id="de062-122">Haga clic en el icono "Quitar Hardware de forma segura" en su Bandeja de tareas y seleccione su lector de tarjetas SD USB para quitarlo de forma segura desde el sistema.</span><span class="sxs-lookup"><span data-stu-id="de062-122">Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system.</span></span>  <span data-ttu-id="de062-123">No se puede hacer esto puede provocar daños en la imagen.</span><span class="sxs-lookup"><span data-stu-id="de062-123">Failing to do this can cause corruption of the image.</span></span>
