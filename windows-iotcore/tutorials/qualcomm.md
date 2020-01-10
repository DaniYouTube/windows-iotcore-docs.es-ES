---
title: Configuración de dispositivos Qualcomm
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo Qualcomm con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Qualcomm
ms.custom: RS5
ms.openlocfilehash: cb9c1e07219b30aafe8b036c99710b49bcddee66
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721470"
---
# <a name="setting-up-a-qualcomm-device"></a>Configuración de un dispositivo Qualcomm

Si lo que quiere es fabricar con un dispositivo Qualcomm, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No se pueden usar imágenes del creador para la fabricación.

> [!NOTE]
> Para asegurarse de que el dispositivo ahora arranca desde la memoria eMMC, escriba de nuevo la configuración del BIOS y cambie el orden de la unidad de arranque para que se cargue desde el disco duro en lugar de la unidad USB.

## <a name="using-emmc"></a>Uso de eMMC

1. Descargue e instale la herramienta de actualización de DragonBoard para el equipo [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) o [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip).
2. Descargue la [FFU de DragonBoard de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads).
3. Haga doble clic en el archivo ISO descargado y busque la unidad de Virtual CD montada. Esta unidad contendrá un archivo de instalador (.msi); haga doble clic en él. Esto crea un directorio en el equipo en  `C:\Program Files (x86)\Microsoft IoT\FFU\` donde debería ver un archivo de imagen, "flash.ffu".
4. Para asegurarse de que DragonBoard está en modo de descarga, establezca que el primer arranque cambie en la placa a arranque de USB, como se muestra a continuación. Después, conecte DragonBoard al equipo host a través de un cable microUSB y, luego, conecte DragonBoard a una fuente de alimentación de 12 V (> 1 A).
5. Inicie la herramienta de actualización de DragonBoard, que debe detectar que DragonBoard se conecta al equipo con un círculo verde. Haga clic en "Examinar" en la FFU del DragonBoard que ha descargado y, después, haga clic en el botón _Programa_.
6. Haga clic otra vez en "Examinar" y seleccione "rawprogram0.xml", que se ha generado en el paso 5. Luego haga clic en el botón "Programa".
7. Una vez completada la descarga, desconecte la fuente de alimentación y el cable microUSB de la placa y cambie el conmutador de arranque USB a _OFF_. Conecte una pantalla HDMI, un ratón y un teclado a DragonBoard y vuelva a conectar la fuente de alimentación. Pasados unos minutos, debería ver la aplicación predeterminada Windows 10 IoT Core. 

![DragonBoard en modo de descarga](../media/DeviceSetup/db1.png)

## <a name="connect-to-a-network"></a>Conexión a una red

### <a name="wired-connection"></a>Conexión por cable
Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.

### <a name="wireless-connection"></a>Conexión inalámbrica
Si el dispositivo admite la conectividad Wi-Fi y le ha conectado una pantalla, deberá hacer lo siguiente:

1. Vaya a la aplicación predeterminada y haga clic en el botón de configuración situado junto al reloj.
2. En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).
3. El dispositivo realizará una exploración de redes inalámbricas.
4. Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.

Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:

1. Vaya al Panel de IoT y haga clic en _Mis dispositivos_.
2. Busque la placa no configurada en la lista. El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68). Si la placa no aparece después de unos minutos, intente reiniciarla.
3. Haga clic en _Configurar dispositivo_ y escriba las credenciales de red. Esto conectará la placa a la red.

> [!NOTE]
> La Wi-Fi debe estar activada en el equipo para poder buscar otras redes.

## <a name="connect-to-windows-device-portal"></a>Conexión al Portal de dispositivos Windows

Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles. 



