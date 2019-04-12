---
title: Conexión de banda ancha móvil
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Obtenga información sobre cómo usar Mobile Broadband conexión para Windows 10 IoT Core.
keywords: conexión de banda ancha móvil de Windows iot, MBB,
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514888"
---
## <a name="mobile-broadband-connection"></a>Conexión de banda ancha móvil

Conexión de banda ancha móvil es compatible con [Windows 10 IoT Core](http://windowsondevices.com). Si la puerta de enlace de IoT es compatible con el módulo de módem de banda ancha móvil, puede usar el `MBBConnect` herramienta para ayudar a configuraciones de instalación para la conexión de banda ancha móvil en IoT Core.

`MBBConnect` Recupera la información relevante para conectar, por ejemplo, Id. de suscriptor, Id. de ICC SIM, nombre de la interfaz y nombre del proveedor de inicio, etcetera. A continuación, crea el perfil de conexión. Lo único que necesita hacer es proporcionar APN y podrá configurar la conexión automáticamente.

`MBBConnect` está desarrollado y probado con MinnowBoard máximo en función de puerta de enlace de IoT con IoT Core versión 16299 y el módulo de módem de banda ancha móvil con la tarjeta SIM de proveedor de telecomunicaciones principales de Taiwán.

### <a name="usage"></a>Uso

1. Copia `MBBConnect.exe` a puerta de enlace de IoT.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Conectar la puerta de enlace mediante Powershell o SSH.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. Cambie a la carpeta donde `MBBConnect.exe` se encuentra. 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a>Ejemplo
El ejemplo siguiente utiliza MBBConnect.exe en PowerShell. Por ejemplo, si el APN de la tarjeta SIM es "Internet", use `MBBConnect.exe Internet` para conectarse.
 
El mensaje de salida muestra el flujo:

* Se cambia el estado de no conectado a conectado. 

* Red WWAN está configurado correctamente.

Pruebe el ejemplo para la conexión de banda ancha móvil [aquí](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).
