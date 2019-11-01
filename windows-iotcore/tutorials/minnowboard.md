---
title: Configuración de un dispositivo MinnowBoard
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo MinnowBoard con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, MinnowBoard
ms.custom: RS5
ms.openlocfilehash: f74d15a5a20a6869544ad47798457067422590f4
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918652"
---
# <a name="setting-up-a-minnowboard"></a>Configuración de un dispositivo MinnowBoard

## <a name="overview"></a>Introducción

> [!IMPORTANT]
> El firmware de 64 bits más reciente para MinnowBoard Turbot se puede encontrar en el [sitio web de MinnowBoard](https://minnowboard.org/tutorials/updating-the-firmware) (omita el paso 4 en las instrucciones del sitio de MinnowBoard).

> [!IMPORTANT]
> Cuando aparezca el mensaje emergente "formatear el disco", _no_ lo formatee. Estamos trabajando en una solución para este problema.

Al configurar un dispositivo MinnowBoard para crear prototipos, se recomienda usar el Panel de Windows 10 IoT Core. Si lo que quiere es fabricar con un dispositivo MinnowBoard, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No se pueden usar imágenes del creador para la fabricación.
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>Uso del panel

Para instalar una imagen de IoT Core o descargarlo en el dispositivo MinnowBoard, necesitará lo siguiente:
* Un equipo que ejecute Windows 10 
* El [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)
* Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk
* Una pantalla externa
* Otros periféricos (por ejemplo, mouse, teclado, etc.)

### <a name="instructions"></a>Instrucciones

1. Ejecute el Panel de Windows 10 IoT Core, haga clic en *Set up a new device* (Configurar un nuevo dispositivo) e inserte una tarjeta SD en el equipo.
2. Conecte el dispositivo MinnowBoard a una pantalla externa.
3. Rellene los campos. Seleccione "Intel [MinnowBoard Turbox/MAX (x64)]" como el tipo de dispositivo. Asegúrese de asignar un nombre y una contraseña nuevos al dispositivo. En caso contrario, las credenciales predeterminadas permanecerán como:

```
Device: minwinpc
Password: p@ssw0rd
```

4. Acepte los términos de licencia de software y haga clic en *Descargar e instalar*. Si todo es correcto, verá que Windows 10 IoT Core instala una imagen en la tarjeta SD.

![Captura de pantalla del panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)

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
