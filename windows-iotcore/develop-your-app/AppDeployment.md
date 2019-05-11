---
title: Implementar una aplicación con Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo implementar una aplicación mediante la característica de depuración remota de Visual Studio.
keywords: Windows iot, visual studio, la implementación de aplicaciones, la depuración remota
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533387"
---
# <a name="deploying-an-app-with-visual-studio"></a>Implementar una aplicación con Visual Studio

Implementar y depurar la aplicación son sencilla con Visual Studio. Vamos a usar el **depuración remota** característica para implementar la aplicación en su dispositivo Windows 10 IoT Core conectado localmente. 

> [!NOTE]
> Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.

> [!NOTE]
> Para poder usar la depuración remota, el dispositivo de IoT Core en primer lugar debe estar conectado a la misma red local que el equipo de desarrollo y las comunicaciones TCP/UDP deben permitirse en la red. En caso de duda, póngase en contacto con el departamento de TI en el tráfico de red permitido. Consulte [conectarse a un dispositivo](../connect-your-device/SetupWiFi.md) para obtener instrucciones.

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a>Implementar aplicaciones en su dispositivo Windows 10 IoT Core

1. Con la aplicación abierta en Visual Studio, establezca la arquitectura en la lista desplegable de la barra de herramientas. Si va a compilar para un máximo Minnowboard, seleccione `x86`. Si va a compilar para Raspberry Pi 2, Raspberry Pi 3 o el Dragonboard, seleccione `ARM`.

2. A continuación, en la barra de herramientas de Visual Studio, haga clic en el `Local Machine` lista desplegable y seleccione `Remote Machine`.

![Máquina remota en Visual Studio](../media/AppDeployment/remote-vs.png)

3. En este punto, Visual Studio presentará la **conexiones remotas** cuadro de diálogo. Si usó anteriormente [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirla aquí (en este ejemplo, estamos usando **mi dispositivo**). En caso contrario, utilice la dirección IP del dispositivo Windows IoT Core.

4. Después de escribir el nombre de dispositivo o dirección IP, seleccione `Universal (Unencrypted Protocol)` modo de autenticación, a continuación, haga clic en **seleccione**. 

![Modo de autenticación universal](../media/AppDeployment/remote-connections.png)

Puede comprobar o modificar estos valores, vaya a las propiedades del proyecto (seleccione **propiedades** en el Explorador de soluciones) y eligiendo la `Debug` ficha a la izquierda:

![Pestaña Depurar](../media/AppDeployment/debug-tab.png)

5. Ahora ya estamos listos para implementar. Bastará que presione F5 (o seleccione Depurar | Iniciar depuración) para iniciar la depuración de nuestra aplicación. Debería ver la aplicación y actuar en la pantalla del dispositivo.

6. Una vez implementado, puede establecer puntos de interrupción, vea los valores de variable, etcetera. Para detener la aplicación de prensa en el botón 'Detener depuración' (o seleccione Depurar | Detenga la depuración).

7. Después de implementar y depurar la aplicación para UWP, crear correctamente una versión de lanzamiento: cambiar la lista desplegable Configuración de barra de herramientas de Visual Studio desde `Debug` a `Release`.  Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando las compilación | Solución de regeneración y compilación | Implementar la solución.
