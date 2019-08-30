---
title: Depurar la aplicación mediante la depuración de aplicaciones de consola remota
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: Obtenga información sobre cómo depurar de forma remota la aplicación de consola de IoT Core en Visual Studio.
keywords: Windows IOT, Visual Studio, implementación de aplicaciones, depuración remota
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170582"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>Depurar la aplicación mediante la depuración de aplicaciones de consola remota

Aquí se muestra cómo depurar la aplicación de consola de IoT Core de forma remota en Visual Studio:

* En primer lugar, debe configurar el depurador remoto en el dispositivo Windows IoT Core. En primer lugar, siga los pasos que se indican a [continuación](AppDeployment.md) para implementar cualquier otra aplicación universal de Windows en el dispositivo (Pruebe el proyecto HelloWorld). Se copiarán todos los archivos binarios necesarios en el dispositivo. 

* Para iniciar el depurador remoto en el dispositivo, abra un explorador Web en su PC y apunte a `http://<device name/IP address>:8080` para iniciar el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md). En el cuadro de diálogo credenciales, use el nombre de `Administrator`usuario `p@ssw0rd`y la contraseña predeterminados:,. La administración de dispositivos Windows debe iniciar y mostrar la pantalla de inicio de administración web.

* Ahora, vaya a la sección configuración de depuración del portal de dispositivos de Windows y haga clic en el botón Inicio en iniciar Visual Studio Remote Debugger. 

    ![WindowsDevicePortalDebugSettings iniciar el depurador remoto](../media/Console/device_portal_start_debugger.png)

* Se mostrará un cuadro de mensaje emergente que le proporcionará la información de conexión. 

*  En Visual Studio, puede configurar el destino editando las propiedades del proyecto (Asegúrese de realizar todos los cambios resaltados según corresponda al nombre o la dirección IP del panel):

    ![Definimos configuración del proyecto de equipo remoto](../media/Console/console_project_settings.png)
    
> [!NOTE]
> Si no ve la imagen anterior, vaya al "Explorador de soluciones" en el menú contextual y vaya a "propiedades del proyecto". Puede encontrar más información sobre las propiedades del proyecto [aquí](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).

> [!TIP]
> Puede usar la dirección IP en lugar del nombre de dispositivo de Windows IoT Core.

* La configuración del proyecto debe modificarse para habilitar la implementación.  Para ello, abra el Configuration Manager seleccionando el administrador de configuración en el menú desplegable Configuración de soluciones de la barra de herramientas.

    ![Definimos SolutionConfiguration](../media/Console/configuration_management.png)

    En el Configuration Manager, asegúrese de que la casilla implementar está seleccionada para la configuración del proyecto (si esta opción está deshabilitada, es probable que las opciones de implementación no se hayan introducido completamente en la pestaña depuración de las propiedades del proyecto)

    ![Definimos configuración del proyecto de equipo remoto](../media/Console/deploy_checkbox.png)

* Ahora estamos listos para implementar en el dispositivo Windows IoT Core remoto. Simplemente presione F5 (o seleccione \| depurar iniciar depuración) para iniciar la depuración de la aplicación. También puede usar la solución \| de implementación de compilación para implementar simplemente la aplicación sin iniciar una sesión de depuración.

> [!NOTE]
> Cuando se ejecuta desde Visual Studio, la salida no se mostrará en ningún lugar, pero podrá establecer puntos de interrupción, ver valores de variables, etc.

* Para detener la aplicación, presione el botón "detener depuración" (o seleccione Depurar \| detener depuración).

* Ahora puede ejecutar la aplicación.  Simplemente abra una conexión de PowerShell o SSH (las instrucciones se pueden encontrar [aquí para PowerShell](../connect-your-device/PowerShell.md) y [aquí para ssh](../connect-your-device/SSH.md)) y escriba el comando remoto que especificó anteriormente.

    ![Salida de definimos](../media/Console/console_output.png)

* Una vez que haya terminado de depurar la aplicación, recuerde detener el depurador remoto en el dispositivo Windows IoT Core. Para ello, vaya a la sección configuración de depuración del portal de dispositivos de Windows y haga clic en el botón detener el depurador remoto.

    ![WindowsDevicePortalDebugSettings detener el depurador remoto](../media/Console/device_portal_stop_debugger.PNG)

