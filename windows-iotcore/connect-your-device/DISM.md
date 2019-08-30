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
# <a name="use-dism-to-flash-windows-10-iot-core"></a>Usar DISM para Flash Windows 10 IoT Core

> [!NOTE]
> No se admite el mantenimiento sin conexión de DISM. Recibirá el siguiente error si intenta montar un FFU para IoT Core: No se admite la solicitud.
> La imagen no tiene un nombre y es probable que sea una FFU móvil/Onecore, que no se admite actualmente.
> Error de FfuMountImage # 160 con 0x80070032.

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a>Un método alternativo al panel de IoT para hacer parpadear un FFU

Puede usar administración y mantenimiento de imágenes de implementación (DISM. exe) para Flash Windows 10 IoT Core en la tarjeta SD. Necesitará un archivo de imagen FFU que se corresponda con el tipo de dispositivo. 

* Abra un símbolo del sistema de administrador y navegue hasta la carpeta que contiene el archivo Flash. FFU local.

* Conecte la tarjeta SD al equipo. 

* Busque el número de disco que tiene la tarjeta SD en el equipo.  Se usará cuando la imagen se aplique en el paso siguiente.  Para ello, puede usar la utilidad Diskpart.  Ejecute los comandos siguientes:

        c:\FFUFolder>diskpart

        DISKPART>list disk

    Debería mostrar todos los dispositivos de almacenamiento conectados al equipo. 

    ![Disco de lista de DISM](../media/Dism/DiskpartListDisk.png)

    Anote el número de disco y escriba Exit para salir de Diskpart. 

        DISKPART>exit

* Con el símbolo del sistema de administrador, aplique la imagen a la tarjeta SD ejecutando el siguiente comando (Asegúrese de reemplazar PhysicalDriveN por el valor que encontró en el paso anterior, por ejemplo, en este caso, la tarjeta SD es el número de disco 4, `/ApplyDrive:\\.\PhysicalDrive4` por lo que usaremos menor

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* Haga clic en el icono "quitar hardware de forma segura" en la bandeja de tareas y seleccione el lector de tarjetas USB SD para quitarlo del sistema de forma segura.  Si no lo hace, puede provocar daños en la imagen.
