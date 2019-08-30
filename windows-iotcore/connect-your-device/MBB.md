---
title: Conexión de banda ancha móvil
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Obtenga información sobre cómo usar la conexión de banda ancha móvil para Windows 10 IoT Core.
keywords: Windows IOT, MBB, conexión de banda ancha móvil
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168053"
---
## <a name="mobile-broadband-connection"></a>Conexión de banda ancha móvil

La conexión de banda ancha móvil es compatible con [Windows 10 IOT Core](http://windowsondevices.com). Si la puerta de enlace de IOT es compatible con el módulo de módem de `MBBConnect` banda ancha móvil, puede usar la herramienta para ayudar a configurar las configuraciones de conexión de banda ancha móvil en IOT Core.

`MBBConnect`Recupera la información relevante para la conexión, como el identificador del suscriptor, el identificador de ICC de SIM, el nombre de la interfaz y el nombre del proveedor de inicio, etc. A continuación, crea el perfil de conexión. Lo único que debe hacer es proporcionar el APN y el programa de instalación de la conexión automáticamente.

`MBBConnect`se desarrolla y prueba con la puerta de enlace de IoT basada en MinnowBoard Max que ejecuta IoT Core versión 16299 y el módulo de módem de banda ancha móvil con la tarjeta SIM del proveedor de telecomunicaciones principal en Taiwán.

### <a name="usage"></a>Uso

1. Copiar `MBBConnect.exe` a la puerta de enlace de IOT.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Conecte la puerta de enlace mediante PowerShell o SSH.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. Cambie a la carpeta donde `MBBConnect.exe` se encuentra. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>Ejemplo
En el ejemplo siguiente se usa MBBConnect. exe en PowerShell. Por ejemplo, si el APN de la tarjeta SIM es "Internet", use `MBBConnect.exe Internet` para conectarse.
 
El mensaje de salida mostrará el flujo:

* El estado cambia de no conectado a conectado. 

* La red WWAN está configurada correctamente.

Pruebe el ejemplo de conexión de banda ancha móvil [aquí](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).
