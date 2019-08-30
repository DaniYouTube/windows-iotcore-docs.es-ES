---
title: Implementar una aplicación con Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo implementar una aplicación mediante la característica de depuración remota de Visual Studio.
keywords: Windows IOT, Visual Studio, implementación de aplicaciones, depuración remota
ms.openlocfilehash: ea0d95fc3702e1cec7f6bda35450c5da495cd837
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533387"
---
# <a name="deploying-an-app-with-visual-studio"></a>Implementar una aplicación con Visual Studio

La implementación y depuración de la aplicación es sencilla con Visual Studio. Usaremos la característica de depuración **remota** para implementar la aplicación en el dispositivo de Windows 10 IOT Core conectado localmente. 

> [!NOTE]
> Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.

> [!NOTE]
> Para usar la depuración remota, el dispositivo de IoT Core primero debe estar conectado a la misma red local que el equipo de desarrollo y se deben permitir las comunicaciones UDP/TCP en la red. En caso de duda, consulte con su equipo en el tráfico de red permitido. Consulte [conexión a un dispositivo](../connect-your-device/SetupWiFi.md) para obtener instrucciones.

## <a name="deploy-apps-to-your-windows-10-iot-core-device"></a>Implementación de aplicaciones en el dispositivo de Windows 10 IoT Core

1. Con la aplicación abierta en Visual Studio, establezca la arquitectura en el menú desplegable de la barra de herramientas. Si va a compilar un máximo de Minnowboard `x86`, seleccione. Si va a compilar para Raspberry pi 2, Raspberry PI 3 o Dragonboard, seleccione `ARM`.

2. Después, en la barra de herramientas de Visual Studio, `Local Machine` haga clic en `Remote Machine`la lista desplegable y seleccione.

![Equipo remoto en Visual Studio](../media/AppDeployment/remote-vs.png)

3. En este momento, Visual Studio presentará el cuadro de diálogo **conexiones remotas** . Si anteriormente usó [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirlo aquí (en este ejemplo, vamos a usar **el dispositivo**). De lo contrario, use la dirección IP de su dispositivo Windows IoT Core.

4. Después de escribir el nombre del dispositivo/ `Universal (Unencrypted Protocol)` IP, seleccione el modo de autenticación y haga clic en **seleccionar**. 

![Modo de autenticación universal](../media/AppDeployment/remote-connections.png)

Puede comprobar o modificar estos valores Si navega a las propiedades del proyecto (seleccione **propiedades** en el explorador de soluciones) y elige la `Debug` pestaña de la izquierda:

![Pestaña Depurar](../media/AppDeployment/debug-tab.png)

5. Ahora estamos listos para implementar. Simplemente presione F5 (o seleccione Depurar | Inicie la depuración) para iniciar la depuración de la aplicación. Debería ver que la aplicación aparece en la pantalla del dispositivo.

6. Una vez implementado, puede establecer puntos de interrupción, ver valores de variables, etc. Para detener la aplicación, presione el botón "detener depuración" (o seleccione Depurar | Detener la depuración).

7. Después de implementar y depurar la aplicación de UWP correctamente, cree una versión de lanzamiento. cambie la lista desplegable `Debug` de `Release`configuración de la barra de herramientas de Visual Studio de a.  Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando compilar | Recompilar solución y compilar | Implemente la solución.
