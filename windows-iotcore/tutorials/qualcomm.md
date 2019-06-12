---
title: Configuración de dispositivos de Qualcomm
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo de Qualcomm con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 02f6c013c428a271d3b3956c88edc1ce8f4fdbf2
ms.sourcegitcommit: fa4a29fcd5af464924a0a5ab581f08f631a3ad72
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835612"
---
# <a name="setting-up-a-qualcomm-device"></a>Cómo configurar un dispositivo de Qualcomm

Si busca para fabricar con un dispositivo de Qualcomm, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No puede usar imágenes de creador de fabricación.

> [!NOTE]
> Asegúrese de que el dispositivo ahora consiste en arrancar desde la memoria eMMC volver a escribir la configuración del BIOS y cambiando el orden de la unidad de arranque cargar de la unidad en lugar de desde la unidad USB.

## <a name="using-emmc"></a>Uso de eMMC

1. Descargue e instale la herramienta de actualización DragonBoard para su [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) o [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) máquina.
2. Descargue el [Windows 10 IoT Core DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads).
3. Haga doble clic en el archivo ISO descargado y busque la montado Virtual-unidad de CD. Esta unidad contendrá un archivo de instalador (.msi); Haga doble clic en él. Esto crea un nuevo directorio en su equipo bajo `C:\Program Files (x86)\Microsoft IoT\FFU\` en lo que debería ver un archivo de imagen, "flash.ffu".
4. Asegúrese de que su DragonBoard está en modo de descarga estableciendo el primer arranque cambie en el panel a USB de arranque, como se muestra a continuación. Conectar el DragonBoard con el equipo host a través de un cable microUSB, a continuación, conecte el DragonBoard a un 12V (> 1A) fuente de alimentación.
5. Inicie la herramienta de actualización DragonBoard, que debe detectar que el DragonBoard se conecte al equipo con un círculo verde. "Examinar" para el DragonBoard FFU que ha descargado, a continuación, haga clic en el _programa_ botón.
6. Haga clic en "Examinar" nuevo y seleccione "rawprogram0.xml" que se generó en el paso 5. A continuación, haga clic en el botón "Programa".
7. Una vez completada la descarga, desconecte el cable de alimentación de suministro y microUSB desde el panel y alternar el modificador de arranque USB al _OFF_. Conectar una pantalla HDMI, un mouse y teclado para el DragonBoard y volver a conectar la fuente de alimentación. Después de unos minutos, debería ver la aplicación predeterminada de Windows 10 IoT Core. 

![DragonBoard en modo de descarga](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a>Conectarse a una red

### <a name="wired-connection"></a>Conexión con cable
Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.

### <a name="wireless-connection"></a>Conexión inalámbrica
Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:

1. Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.
2. En la página de configuración, seleccione _red y Wi-Fi_.
3. El dispositivo realizará un examen para redes inalámbricas.
4. Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.

Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:

1. Vaya al panel de IoT y haga clic en _Mis dispositivos_.
2. Encuentre la placa no configurada en la lista. Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68). Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.
3. Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red. La placa de esto conectará a la red.

> [!NOTE]
> Wi-Fi en el equipo debe estar activada para poder buscar otras redes.

## <a name="connect-to-windows-device-portal"></a>Conectarse a Windows Device Portal

Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos. 



