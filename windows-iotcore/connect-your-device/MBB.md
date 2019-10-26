---
title: Conexión de banda ancha móvil
ms.date: 06/12/2018
ms.topic: article
description: Obtenga información sobre cómo usar la conexión de banda ancha móvil para Windows 10 IoT Core.
keywords: Windows IOT, MBB, conexión de banda ancha móvil
ms.openlocfilehash: 2bf9a153fb77ab7f92bad727847cdf581d0b7729
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918332"
---
# <a name="mobile-broadband-connection"></a>Conexión de banda ancha móvil

La conexión de banda ancha móvil es compatible con [Windows 10 IOT Core](http://windowsondevices.com). Si la puerta de enlace de IoT es compatible con el módulo de módem de banda ancha móvil, puede usar la herramienta de `MBBConnect` para ayudar a configurar las configuraciones de conexión de banda ancha móvil en IoT Core.

`MBBConnect` recupera la información relevante para la conexión, como el identificador del suscriptor, el identificador de ICC de SIM, el nombre de la interfaz y el nombre del proveedor de inicio, etc. A continuación, crea el perfil de conexión. Lo único que debe hacer es proporcionar el APN y el programa de instalación de la conexión automáticamente.

`MBBConnect` se desarrolla y prueba con la puerta de enlace de IoT basada en MinnowBoard Max que ejecuta IoT Core versión 16299 y el módulo de módem de banda ancha móvil con la tarjeta SIM del proveedor de telecomunicaciones principal en Taiwán.

### <a name="usage"></a>Uso

1. Copie `MBBConnect.exe` en la puerta de enlace de IoT.

   * [FTP](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. Conecte la puerta de enlace mediante PowerShell o SSH.

   * [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [SSH](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. Cambie a la carpeta donde se encuentra `MBBConnect.exe`. 
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
