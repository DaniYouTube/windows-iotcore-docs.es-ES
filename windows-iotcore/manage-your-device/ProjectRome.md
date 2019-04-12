---
title: Uso de proyecto Roma con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: Obtenga información y conocer los pasos para aprovechar el dispositivo Windows IoT en el mercado.
keywords: dispositivos de Windows 10 IoT Core, proyecto Roma, remotos
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515053"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>Uso de proyecto Roma con Windows 10 IoT Core 
 
[Proyecto Roma](https://developer.microsoft.com/en-us/windows/project-rome) permite trabajar de forma remota con los dispositivos que ejecutan Windows 10 IoT Core utilizando el RemoteSystems y AppServiceProvider APIs. 
 
En este artículo, analizaremos cómo detectar, control y conectarse a dispositivos que ejecutan Windows 10 IoT Core con Roma del proyecto.  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>Detección de dispositivos de IoT Core con las APIs RemoteSystem 
 
_Programa de instalación:_
* Ejecute el ejemplo RemoteSystems en un equipo de escritorio mientras ha iniciado sesión en su cuenta de Microsoft.  
* Con ninguna aplicación que se ejecutan en IoT Core, inicie sesión en su cuenta de Microsoft, vaya a Cortana al inicio de sesión. 
 
_Pasos a seguir:_
1. Ejecutar el ejemplo de RemoteSystems en el escritorio 
2. Detectando"(1)," haga clic en "Buscar sistemas" 

![Búsqueda de sistemas](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>Controlar los dispositivos de IoT Core con RemoteSystems.LaunchUri 
 
_Programa de instalación:_
* Ejecute el [RemoteSystems ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras [ha iniciado sesión en su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).
* Con ninguna aplicación que se ejecutan en IoT Core, inicie sesión en su cuenta de Microsoft, vaya a Cortana al inicio de sesión. 
 
_Pasos a seguir:_
1. Encienda la máquina virtual de IoT Core con Cortana e inicie sesión en su cuenta de Microsoft de Cortana. 
2. Ejecute el ejemplo RemoteSystems en escritorio. 
3. Detectando"(1)", haga clic en "Buscar sistemas". 
4. En "(2) inicio URI", seleccione el dispositivo de IoT Core que se está ejecutando Cortana. 
5. Escriba este identificador URI y el lanzamiento. 

![URI de inicio](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>Conectar con el servicio de aplicación remota que se ejecutan en IoT Core 
_Programa de instalación:_
* Ejecute el [RemoteSystems ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras [ha iniciado sesión en su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement). 
* Asegúrese de tener la [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) implementado y ejecutándose en al menos un dispositivo de IoT Core. 
 
_Pasos a seguir:_
1. Convertir en la máquina Virtual de IoT Core con Cortana e inicie sesión en su cuenta de Microsoft de Cortana. Implementar la aplicación AppServiceProvider, ejecútelo una vez y cerrarlo. 
2. Ejecute el ejemplo RemoteSystems en escritorio. 
3. Detectando"(1)", haga clic en "Buscar sistemas". 
4. En"(3) inicio App Services," select IoT core dispositivo que tenga la aplicación AppServiceProvider implementada y se ha ejecutado anteriormente. 
5. Generar un número aleatorio.  

![Iniciar los servicios de aplicaciones](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>Controlar otros dispositivos y servicios de aplicaciones desde un dispositivo de IoT Core 

_Programa de instalación:_
* Ejecute el [RemoteSystems ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) implementada en un dispositivo de IoT Core mientras [ha iniciado sesión en su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) desde la aplicación de Cortana. 
* Tiene un equipo de escritorio con el [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) implementado y que se ha ejecutado al menos una vez. 
 
_Pasos a seguir:_
1. Ejecute el ejemplo RemoteSystems. 
2. Detectando"(1)", haga clic en "Buscar sistemas". 
3. En "(2) inicio URI", seleccione el equipo de escritorio e inicie. 
4. En "(3) servicios de aplicación de inicio", seleccione la máquina de escritorio.  
 
> [!NOTE] 
> En el primer intento, esto puede tardar mucho tiempo. Inténtelo de nuevo para una cantidad de respuesta más rápida. 
 
### <a name="helpful-links"></a>Vínculos útiles: 
* [Documentación del proyecto Roma en MSDN](https://developer.microsoft.com/en-us/windows/project-rome )
* [Uso de Roma de proyecto para UWP](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
