---
title: Configuración de un dispositivo Raspberry Pi
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo Raspberry Pi con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 7a79931bc4ce1976a047d51f64a8ba6d4cc590a1
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "75721726"
---
# <a name="setting-up-a-raspberry-pi"></a>Configuración de un dispositivo Raspberry Pi

## <a name="overview"></a>Introducción

> [!NOTE]
> El panel de información no se puede utilizar para configurar Raspberry Pi 3B+. Si tiene un dispositivo 3B+, debe usar la [versión preliminar técnica de 3B+](https://www.microsoft.com/en-us/software-download/windowsiot). Consulte las [limitaciones conocidas](https://docs.microsoft.com/windows/iot-core/troubleshooting) de la versión preliminar técnica para determinar si esto es adecuado para el desarrollo.

> [!IMPORTANT]
> Cuando aparezca el mensaje emergente "formatear el disco", _no_ lo formatee. Estamos trabajando en una solución para este problema.

Al configurar un dispositivo Raspberry Pi para crear prototipos, se recomienda usar el Panel de Windows 10 IoT Core. Pero si lo que quiere es fabricar con un dispositivo Raspberry Pi, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No se pueden usar imágenes del creador para la fabricación.
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>Uso del panel

Para instalar una imagen de IoT Core o descargarlo en el dispositivo Raspberry Pi, necesitará lo siguiente:
* Un equipo que ejecute Windows 10 
* El [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/downloads)
* Una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk
* Una pantalla externa
* Otros periféricos (por ejemplo, mouse, teclado, etc.)

### <a name="instructions"></a>Instrucciones

1. Ejecute el Panel de Windows 10 IoT Core, haga clic en *Set up a new device* (Configurar un nuevo dispositivo) e inserte una tarjeta SD en el equipo.
2. Conecte el dispositivo Raspberry Pi a una pantalla externa.
3. Rellene los campos. Seleccione "Broadcomm [Raspberry Pi 2 & 3]" como el tipo de dispositivo. Asegúrese de asignar un nombre y una contraseña nuevos al dispositivo. En caso contrario, las credenciales predeterminadas permanecerán como:

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
> En el equipo la Wi-Fi debe estar activada para poder buscar otras redes.

## <a name="connect-to-windows-device-portal"></a>Conexión al Portal de dispositivos Windows

Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles. 
