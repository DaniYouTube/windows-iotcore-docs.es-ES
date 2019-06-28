---
title: Configuración de un dispositivo DragonBoard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo DragonBoard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, DragonBoard
ms.custom: RS5
ms.openlocfilehash: 6488237a41f42c7acbe9e5e1c68466548577ab38
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "66835609"
---
# <a name="setting-up-a-dragonboard"></a>Configuración de un dispositivo DragonBoard

> [!IMPORTANT]
> Cuando trabaja con un nuevo dispositivo DragonBoard, viene con Android instalado. Deberá borrar y cargar el dispositivo mediante el método de instalación de imagen eMMC, como se indica [aquí](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm).

> [!NOTE]
> Si experimenta problemas relacionados con el audio con DragonBoard, le recomendamos que consulte el manual de Qualcomm [aquí](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf). 

Al configurar un dispositivo DragonBoard para crear prototipos, se recomienda usar el Panel de Windows 10 IoT Core. Si lo que quiere es fabricar con un dispositivo DragonBoard, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No se pueden usar imágenes del creador para la fabricación.
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a>Uso del panel

Para instalar una imagen de IoT Core o descargarlo en su dispositivo MinnowBoard, necesitará lo siguiente:
* Un equipo que ejecute Windows 10 
* El [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)
* Un cable microUSB
* Una pantalla externa
* Otros periféricos (por ejemplo, mouse, teclado, etc.)

### <a name="instructions"></a>Instrucciones

1. Ejecute el Panel de Windows 10 IoT Core y haga clic en *Set up a new device* (Configurar un nuevo dispositivo).
2. Seleccione "Qualcomm [DragonBoard 410c]" como tipo de dispositivo.
3. Conecte el dispositivo DragonBoard a su equipo con un cable microUSB.
4. Conecte el dispositivo DragongBoard a una pantalla externa.
5. Encienda el dispositivo DragonBoard con una fuente de alimentación de 12 V (> 1 A) mientras mantiene presionado el botón de subir volumen (+). El dispositivo, cuando se conecta a una pantalla, debe mostrar la imagen de un martillo, un rayo y un engranaje.
6. Ahora, el dispositivo debe estar visible en el panel, como se muestra debajo. Seleccione el dispositivo correspondiente.
7. Acepte los términos de licencia de software y, después, haga clic en **Descargar e instalar**. Verá que Windows 10 IoT Core instala una imagen en el dispositivo.

![DragonBoard en modo sobrescribir](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a>Conexión a una red
### <a name="wired-connection"></a>Conexión por cable
Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.

### <a name="wireless-connection"></a>Conexión inalámbrica
Si el dispositivo admite la conectividad Wi-Fi y ha conectado una pantalla, deberá hacer lo siguiente:

1. Vaya a la aplicación predeterminada y haga clic en el botón Configuración situado junto al reloj.
2. En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).
3. El dispositivo realizará una exploración de redes inalámbricas.
4. Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.

Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:

1. Vaya al Panel de IoT y haga clic en _Mis dispositivos_.
2. Busque la placa no configurada en la lista. El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68). Si la placa no aparece después de unos minutos, intente reiniciarla.
3. Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red. Esto conectará la placa a la red.

> [!NOTE]
> La Wi-Fi debe estar activada en el equipo para poder buscar otras redes.

## <a name="connect-to-windows-device-portal"></a>Conexión a Portal de dispositivos Windows

Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles. 

