---
title: Configurar un Dragonboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar su Dragonboard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 8e4acc77d902124934e1bdae249f76c7f76306a6
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182277"
---
# <a name="setting-up-a-dragonboard"></a>Configurar un Dragonboard

> [!IMPORTANT]
> Cuando está trabajando con un nuevo Dragonboard, acompañada de Android instalado. Deberá borrar y cargar el dispositivo mediante el método eMMC parpadeante.

> [!NOTE]
> Si experimenta problemas relacionados con el audio con su DragonBoard, le recomendamos que lea manual de Qualcomm [aquí](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf). 

Al configurar un Dragonboard para crear prototipos, se recomienda usar el panel de Windows 10 IoT Core. Sin embargo, si busca para fabricar con un Dragonboard, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No puede usar imágenes de creador de fabricación.
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a>Uso del panel

Para flash o descargar IoT Core en su MinnowBoard, necesitará:
* Un equipo que ejecuta Windows 10 
* [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)
* Cable MicroUSB
* Una pantalla externa
* Cualquier otro periférico (por ejemplo, mouse, teclado, etcetera.)

### <a name="instructions"></a>Instrucciones

1. Ejecutar el panel de Windows 10 IoT Core y haga clic en *configurar un nuevo dispositivo*.
2. Seleccione "Qualcomm [DragonBoard 410c]" como el tipo de dispositivo.
3. Conecte el DragonBoard a su compuetr mediante un cable microUSB.
4. Conecte su DragongBoard a una pantalla externa.
5. Encender su Dragonboard mediante un 12V (> 1A) alimentación mientras mantiene presionada (+) para Subir volumen botón. El dispositivo - cuando se conecta a una pantalla - debe aparecer la imagen de un martillo, un rayo y un engranaje.
6. Ahora, el dispositivo debe estar visible en el panel, como se muestra a continuación. Seleccione el dispositivo adecuado.
7. Acepte los términos de licnse y haga clic en **descargue e instale**. Verá que ahora parpadea en su dispositivo Windows 10 IoT Core.

![DragonBoard en modo de flash](../media/DeviceSetup/db4.png)

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

