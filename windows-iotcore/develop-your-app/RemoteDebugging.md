---
title: Depurar la aplicación con la depuración remota de aplicaciones de consola
author: bfjelds
ms.author: bfjelds
ms.date: 09/12/17
ms.topic: article
description: Obtenga información sobre cómo depurar la aplicación de consola IoT Core remotamente en Visual Studio de forma remota.
keywords: Windows iot, visual studio, la implementación de aplicaciones, la depuración remota
ms.openlocfilehash: dc3afad193bc6356a5f897f386f5061adaf6bc01
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514547"
---
# <a name="debug-your-app-using-remote-console-app-debugging"></a>Depurar la aplicación con la depuración remota de aplicaciones de consola

Aquí le mostramos cómo depurar la aplicación de consola IoT Core remotamente en Visual Studio:

* En primer lugar, deberá configurar al depurador remoto en el dispositivo Windows IoT Core. En primer lugar, siga los pasos [aquí](AppDeployment.md) para implementar cualquier otra aplicación Windows Universal en el dispositivo (pruebe el proyecto HelloWorld). Esto copiará todos los archivos binarios necesarios a su dispositivo. 

* Para iniciar el depurador remoto en el dispositivo, abra un explorador Web en su PC y haga que señale a `http://<device name/IP address>:8080` para iniciar [Windows Device Portal](../manage-your-device/DevicePortal.md). En el cuadro de diálogo de credenciales, utilice el nombre de usuario predeterminado y la contraseña: `Administrator`, `p@ssw0rd`. Administración de dispositivos de Windows debe iniciar y mostrar la pantalla principal de administración de web.

* Ahora, vaya a la sección de configuración de depuración de Windows Device Portal y haga clic en el botón Inicio en iniciar Visual Studio Remote Debugger. 

    ![Depurador remoto WindowsDevicePortalDebugSettings inicio](../media/Console/device_portal_start_debugger.png)

* Esto mostrará emergente de un cuadro de mensaje y le proporcionarán la información de conexión. 

*  En Visual Studio, puede configurar el destino mediante la edición de las propiedades del proyecto (asegúrese de que todos los cambios resaltados según corresponda al nombre o dirección IP de la placa):

    ![Configuración del proyecto de equipo remoto de la aplicación de consola](../media/Console/console_project_settings.png)
    
> [!NOTE]
> Si no ve la imagen anterior, vaya a "Explorador de soluciones" en el menú contextual y vaya a "Propiedades del proyecto". Puede encontrar más información para las propiedades del proyecto [aquí](https://docs.microsoft.com/visualstudio/ide/managing-project-and-solution-properties?view=vs-2017).

> [!TIP]
> Puede usar la dirección IP en lugar del nombre de dispositivo Windows IoT Core.

* La configuración del proyecto debe modificarse para habilitar la implementación.  Para ello, abra el Administrador de configuración seleccionando el Administrador de configuración en el menú desplegable de configuración de soluciones en la barra de herramientas.

    ![Aplicación de consola SolutionConfiguration](../media/Console/configuration_management.png)

    Desde el Administrador de configuración, asegúrese de que esté seleccionada la casilla de verificación de implementación para la configuración del proyecto (si esta opción está deshabilitada, es probable que las opciones de implementación no se han escrito completamente en la pestaña de depuración de las propiedades del proyecto)

    ![Configuración del proyecto de equipo remoto de la aplicación de consola](../media/Console/deploy_checkbox.png)

* Ahora estamos listos para implementar en el dispositivo remoto de Windows IoT Core. Bastará que presione F5 (o seleccione Depurar \| Iniciar depuración) para iniciar la depuración de nuestra aplicación. También puede usar la compilación \| implementar la solución para simplemente implementar la aplicación sin iniciar una sesión de depuración.

> [!NOTE]
> Cuando se ejecuta desde Visual Studio, el resultado no se mostrará en cualquier lugar, pero podrá establecer puntos de interrupción, vea los valores de variable, etcetera.

* Para detener la aplicación, pulse en el botón 'Detener depuración' (o seleccione Depurar \| Detener depuración).

* Ahora puede ejecutar la aplicación.  Solo tiene que abrir una conexión de PowerShell o SSH (puede encontrar instrucciones [aquí para PowerShell](../connect-your-device/PowerShell.md) y [aquí para SSH](../connect-your-device/SSH.md)) y escriba el comando remoto especificado anteriormente.

    ![Salida de la aplicación de consola](../media/Console/console_output.png)

* Una vez que termine de depurar la aplicación, no olvide detener el depurador remoto en el dispositivo Windows IoT Core. Puede hacerlo navegando para depurar la sección de configuración de Windows Device Portal y haga clic en el botón detener el depurador remoto.

    ![Depurador remoto WindowsDevicePortalDebugSettings Stop](../media/Console/device_portal_stop_debugger.PNG)

