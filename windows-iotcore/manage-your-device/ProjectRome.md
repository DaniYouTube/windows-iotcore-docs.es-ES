---
title: Usar Project Roma con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: Conozca y comprenda los pasos necesarios para poner el dispositivo de Windows IoT en el mercado.
keywords: Windows 10 IoT Core, proyecto Roma, dispositivos remotos
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170401"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>Usar Project Roma con Windows 10 IoT Core 
 
[Project Roma](https://developer.microsoft.com/en-us/windows/project-rome) le permite trabajar de forma remota con dispositivos que ejecutan Windows 10 IOT Core con las API de RemoteSystems y AppServiceProvider. 
 
En este artículo, veremos cómo detectar, controlar y conectar con dispositivos que ejecutan Windows 10 IoT Core con el proyecto Roma.  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>Detección de dispositivos IoT Core con las API de RemoteSystem 
 
_Archivo_
* Ejecute el ejemplo RemoteSystems en un escritorio mientras está conectado a su cuenta de Microsoft.  
* Sin ninguna aplicación que se ejecute en IoT Core, inicie sesión en su cuenta de Microsoft yendo a Cortana para iniciar sesión. 
 
_Pasos_
1. Ejecutar el ejemplo RemoteSystems en el escritorio 
2. En "1" detección ", haga clic en" buscar sistemas ". 

![Buscar sistemas](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>Control de dispositivos IoT Core con RemoteSystems. LaunchUri 
 
_Archivo_
* Ejecute el [ejemplo RemoteSystems](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras está [conectado a su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement).
* Sin ninguna aplicación que se ejecute en IoT Core, inicie sesión en su cuenta de Microsoft yendo a Cortana para iniciar sesión. 
 
_Pasos_
1. Encienda la máquina virtual de IoT Core con Cortana e inicie sesión en el cuenta de Microsoft de Cortana. 
2. Ejecute el ejemplo RemoteSystems en el escritorio. 
3. En "1) detección", haga clic en "buscar sistemas". 
4. En "2) URI de inicio", seleccione el dispositivo de IoT Core que ejecuta Cortana. 
5. Escriba este URI e inicie. 

![Inicio del URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>Conexión al App Service remoto que se ejecuta en IoT Core 
_Archivo_
* Ejecute el [ejemplo RemoteSystems](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) en un escritorio mientras está [conectado a su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement). 
* Asegúrese de que la [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) se ha implementado y se está ejecutando en al menos un dispositivo IOT Core. 
 
_Pasos_
1. Encienda la máquina virtual de IoT Core con Cortana e inicie sesión en el cuenta de Microsoft de Cortana. Implemente la aplicación AppServiceProvider, ejecútela una vez y ciérrela. 
2. Ejecute el ejemplo RemoteSystems en el escritorio. 
3. En "1) detección", haga clic en "buscar sistemas". 
4. En "3) iniciar App Services", seleccione el dispositivo de IoT Core que tiene implementada la aplicación AppServiceProvider y que se ejecutó anteriormente. 
5. Generar un número aleatorio.  

![Iniciar App Services](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>Control de otros dispositivos y servicios de aplicaciones desde un dispositivo IoT Core 

_Archivo_
* Ejecute el [ejemplo RemoteSystems](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems) implementado en un dispositivo de IOT Core mientras está [conectado a su cuenta de Microsoft](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) desde la aplicación de Cortana. 
* Tener una máquina de escritorio con la [aplicación AppServiceProvider](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) implementada y que se haya ejecutado al menos una vez. 
 
_Pasos_
1. Ejecute el ejemplo RemoteSystems. 
2. En "1) detección", haga clic en "buscar sistemas". 
3. En "2) URI de inicio", seleccione la máquina de escritorio y el inicio. 
4. En "3) iniciar App Services", seleccione la máquina de escritorio.  
 
> [!NOTE] 
> En el primer intento, esto puede tardar mucho tiempo. Vuelva a intentarlo para obtener una respuesta mucho más rápida. 
 
### <a name="helpful-links"></a>Vínculos útiles: 
* [Documentación de Project Roma en MSDN](https://developer.microsoft.com/en-us/windows/project-rome )
* [Usar Project Roma para UWP](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
