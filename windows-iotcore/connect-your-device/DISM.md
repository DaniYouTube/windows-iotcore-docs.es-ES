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
# <a name="use-dism-to-flash-windows-10-iot-core"></a>Use DISM para flash de Windows 10 IoT Core

> [!NOTE]
> No se admite el mantenimiento sin conexión de DISM. Si intenta montar un FFU para IoT Core, recibirá el siguiente error: No se admite la solicitud.
> La imagen no tiene un nombre y es probable que sea un FFU Mobile/Onecore, que no se admite actualmente.
> Error 0 x 80070032 FfuMountImage #160.

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a>Un método alternativo para el panel de IoT de intermitencia en un FFU

Puede usar Management(Dism.exe) y mantenimiento de imágenes de implementación para Windows 10 IoT Core en la tarjeta SD. Necesitará un archivo de imagen FFU correspondiente al tipo de dispositivo. 

* Abra un símbolo del sistema de administrador y navegue hasta la carpeta que contiene el archivo flash.ffu local.

* Complemento tarjeta la SD en el equipo. 

* Buscar el número de disco que se encuentra la tarjeta SD en el equipo.  Se usará cuando se aplica la imagen en el paso siguiente.  Para ello, puede usar la utilidad diskpart.  Ejecute los siguientes comandos:

        c:\FFUFolder>diskpart

        DISKPART>list disk

    Deben enumerar todos los dispositivos de almacenamiento conectados al equipo. 

    ![Disco de la lista DISM](../media/Dism/DiskpartListDisk.png)

    Tenga en cuenta el número de disco y escriba diskpart exit para salir. 

        DISKPART>exit

* Mediante el símbolo del sistema de administrador, aplique la imagen a la tarjeta SD, ejecute el comando siguiente (no olvide reemplazar PhysicalDriveN con el valor que se encuentra en el paso anterior, por ejemplo, en este caso tarjeta SD es el número de disco 4, por lo que usaremos `/ApplyDrive:\\.\PhysicalDrive4` a continuación)

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* Haga clic en el icono "Quitar Hardware de forma segura" en su Bandeja de tareas y seleccione su lector de tarjetas SD USB para quitarlo de forma segura desde el sistema.  No se puede hacer esto puede provocar daños en la imagen.
