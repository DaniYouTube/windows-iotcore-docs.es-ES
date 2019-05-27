---
title: Cómo configurar un dispositivo NXP
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo NXP con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, NXP
ms.custom: RS5
ms.openlocfilehash: 58bed6c49a5a05afe0852572051132f8731dfcb1
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182177"
---
# <a name="setting-up-a-nxp-device"></a>Cómo configurar un dispositivo NXP

## <a name="overview"></a>Información general

> [!IMPORTANT]
> Cuando el "dar formato al disco" pop hasta, hacer _no_ formatear el disco. Estamos trabajando en una solución para este problema.

Al configurar un dispositivo NXP para crear prototipos, se recomienda usar el panel de Windows 10 IoT Core. Sin embargo, si busca para fabricar con un dispositivo NXP, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No puede usar imágenes de creador de fabricación.
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>Uso del panel

Para flash o descargar IoT Core en su dispositivo NXP, necesitará:
* Un equipo que ejecuta Windows 10 
* [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)
* Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk
* Una pantalla externa
* Cualquier otro periférico (por ejemplo, mouse, teclado, etcetera.)

### <a name="instructions"></a>Instrucciones

1. Ejecutar el panel de Windows 10 IOT Core y haga clic en *configurar un nuevo dispositivo* e inserte una tarjeta SD en el equipo.
2. Conecte el dispositivo NXP a una pantalla externa.
3. Rellene los campos. Seleccione "NXP [i.MX6/i.MX7]" como el tipo de dispositivo. Asegúrese de dar a su dispositivo un nuevo nombre y una contraseña. En caso contrario, las credenciales predeterminadas permanecerá como:

```
Device: minwinpc
Password: p@ssw0rd
```

4. Cargue el archivo de imagen descargada previamente mediante la función "Examinar". Para obtener más información, consulte nuestra [documentación NXP](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp).
5. Acepte los términos de licencia de software y haga clic en *descargue e instale*. Si todo va bien, verá que ahora es Windows 10 IoT Core intermitencia en la tarjeta SD.

![Captura de pantalla de panel](../media/DeviceSetup/Dashboard-Screenshot.jpg)


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
