---
title: Implementar una aplicación con Visual Studio
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo implementar una aplicación mediante la característica de depuración remota de Visual Studio.
keywords: Windows iot, visual studio, la implementación de aplicaciones, la depuración remota
ms.openlocfilehash: 218cbf43a1b63a517091b80315f327954b3eae5a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514720"
---
# <a name="deploying-an-app-with-visual-studio"></a>Implementar una aplicación con Visual Studio

Implementar y depurar la aplicación son sencilla con Visual Studio. Vamos a usar el **depuración remota** característica para implementar la aplicación en su dispositivo Windows 10 IoT Core conectado localmente. 

> [!NOTE]
> Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.

> [!NOTE]
> Para poder usar la depuración remota, el dispositivo de IoT Core en primer lugar debe estar conectado a la misma red local que el equipo de desarrollo.  
>Consulte la [conectarse a un dispositivo](../connect-your-device/SetupWiFi.md) instrucciones.

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>Implementar un C# aplicación en el dispositivo Windows 10 IoT Core 
___

1. Con la aplicación abierta en Visual Studio, establezca la arquitectura en la lista desplegable de la barra de herramientas. Si va a compilar para Minnowboard Max, seleccione `x86`. Si va a compilar para Raspberry Pi 2, Raspberry Pi 3 o el Dragonboard, seleccione `ARM`.

2. A continuación, en la barra de herramientas de Visual Studio, haga clic en el `Local Machine` lista desplegable y seleccione `Remote Machine`.

![Máquina remota en Visual Studio](../media/AppDeployment/cs-remote-machine-debugging.png)

3. En este punto, Visual Studio presentará la **conexiones remotas** cuadro de diálogo. Si usó anteriormente [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirla aquí (en este ejemplo, estamos usando **mi dispositivo**). En caso contrario, utilice la dirección IP del dispositivo Windows IoT Core.

4. Después de escribir el nombre de dispositivo o dirección IP, seleccione `Universal (Unencrypted Protocol)` modo de autenticación, a continuación, haga clic en **seleccione**. 

![Modo de autenticación universal](../media/AppDeployment/cs-remote-connections.png)

Puede comprobar o modificar estos valores, vaya a las propiedades del proyecto (seleccione **propiedades** en el Explorador de soluciones) y eligiendo la `Debug` ficha a la izquierda:

![Pestaña Depurar](../media/AppDeployment/cs-debug-project-properties.png)

5. Ahora ya estamos listos para implementar. Bastará que presione F5 (o seleccione Depurar \| Iniciar depuración) para iniciar la depuración de nuestra aplicación. Debería ver la aplicación y actuar en la pantalla del dispositivo.

6. Una vez implementado, puede establecer puntos de interrupción, vea los valores de variable, etcetera. Para detener la aplicación de prensa en el botón 'Detener depuración' (o seleccione Depurar \| Detener depuración).

7. Después de implementar y depurar la aplicación para UWP, crear correctamente una versión de lanzamiento: cambiar la lista desplegable Configuración de barra de herramientas de Visual Studio desde `Debug` a `Release`.  Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando las compilación \| recompilar solución y compilación \| implementar solución.

## <a name="deploy-a-c-app-to-your-windows-10-iot-core-device"></a>Implementar un C++ aplicación en el dispositivo Windows 10 IoT Core

1. Con la aplicación abierta en Visual Studio, establezca la arquitectura en la lista desplegable de la barra de herramientas. Si va a compilar para Minnowboard Max, seleccione `86`. Si va a compilar para Raspberry Pi 2 o 3, seleccione `ARM`.

2. A continuación, en la barra de herramientas de Visual Studio, haga clic en el `Local Machine` lista desplegable y seleccione `Remote Machine`

![Máquina local en Visual Studio](../media/AppDeployment/cpp-remote-machine-debugging.png)

3. A continuación, haga clic en el proyecto en el **el Explorador de soluciones** panel. Seleccione **Propiedades**. 

![Propiedades en Visual Studio](../media/AppDeployment/cpp-project-properties.png)

4. En **propiedades de configuración -> depuración**, modifique los campos siguientes:

    * **Nombre de equipo**: Si usó anteriormente [PowerShell](../connect-your-device/PowerShell.md) para establecer un nombre único para el dispositivo, puede escribirla aquí (en este ejemplo, estamos usando **mi dispositivo**). En caso contrario, utilice la dirección IP del dispositivo Windows IoT Core.
    * **Modo de autenticación**: Establecido en **Universal (protocolo sin cifrar)**
    
![Modo de autenticación universal](../media/AppDeployment/cpp-debug-project-properties.png)

5. Ahora ya estamos listos para implementar. Bastará que presione F5 (o seleccione Depurar \| Iniciar depuración) para iniciar la depuración de nuestra aplicación. Debería ver que la aplicación aparezca en la pantalla del dispositivo Windows IoT Core.

6. Una vez implementado, puede establecer puntos de interrupción, vea los valores de variable, etcetera. Para detener la aplicación, pulse en el botón 'Detener depuración' (o seleccione Depurar \| Detener depuración).

7. Tener correctamente implementado y depurar la aplicación para UWP, cree una versión de lanzamiento: cambiar la lista desplegable Configuración de barra de herramientas de Visual Studio desde `Debug` a `Release`.  Ahora puede compilar e implementar la aplicación en el dispositivo seleccionando las compilación \| recompilar solución y compilación \| implementar solución.

