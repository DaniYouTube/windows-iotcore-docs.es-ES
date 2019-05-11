---
title: Información general sobre depuración
author: saraclay
ms.author: saclayt
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre las distintas formas que puede depurar Windows 10 IoT Core.
keywords: Windows iot, depuración, PowerShell, SSH
ms.openlocfilehash: 64fa743416823a849deb2cb7826c149f9023a893
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535835"
---
# <a name="debugging-on-windows-iot-core"></a>Depuración en Windows IoT Core
Una vez que tenga la configuración de la imagen de IoT Core con la ejecución de aplicación, es importante que puede depurar la aplicación o el sistema según sea necesario. Es el mejor momento para depurar y probar el sistema mientras el estado de la imagen de prueba. Una vez sistemas basadas en el núcleo de IoT horizontal en estado salvaje, la depuración puede convertirse en challanging. Que es no quiere decir que no es posible, pero con niveles adicionales de las dificultades que se agrega al depurar comparar con una prueba fases. Puede usar lo siguiente para depurar su aplicación o la imagen en el modo de prueba:

## <a name="device-portal"></a>Device Portal
Windows Device Portal (WDP) permite configurar y administrar su remoately de dispositivo IoT a través de la red local. WDP puede ser accesible a través de la dirección ip local del dispositivo de IoT. Puede encontrar información adicional en WDP en IoT [aquí](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/DevicePortal).

### <a name="collecting-etw--wpp-logs"></a>Recopilación de ETW / WPP Logs 
-----

### <a name="file-sharing"></a>Uso compartido de archivos
El Explorador de archivos de la aplicación puede permitir el acceso a los directorios que pueden tener acceso las aplicaciones * vCameraRoll se comparte entre todas las aplicaciones
* Documentos se comparte entre todas las aplicaciones
* LocalAppData contiene carpetas específicas de cada aplicación. Esta carpeta será el mismo nombre que la aplicación y otras aplicaciones no pueden acceder a él.
Consulte más arriba del vínculo para obtener más información.

### <a name="kernel-debug"></a>Depuración de kernel
Puede descargar volcados del núcleo en vivo a través de WDP también. Cualquier sistema bloqueos será automáticamente ser registran y están disponibles para su descarga. Consulte más arriba del vínculo para obtener más información.

### <a name="enable-crash-dump"></a>Habilitar el volcado de memoria
Puede descargar los volcados de memoria de aplicaciones en dispositivos IoT a través de WDP. Consulte más arriba del vínculo para obtener más información.

## <a name="sshpowershelltshell"></a>SSH/PowerShell/TShell
PowerShell es un shell de línea de comandos basado en tareas y lenguaje de scripting diseñado especialmente para la administración del sistema. Puede encontrar más información sobre la depuración y la configuración de powershell [aquí](../connect-your-device/powershell.md).

## <a name="debug-through-visual-studio-deployment"></a>Depurar a través de la implementación de Visual Studio
Implementar y depurar la aplicación son sencilla con Visual Studio. La característica de depuración remota se puede usar para implementar y depurar la aplicación en el dispositivo Windows 10 IoT Core conectado localmente. Detallada sobre la implementación y depuración pueden encontrarse [aquí](../develop-your-app/RemoteDebugging.md).

-----
## <a name="live-app-debug"></a>Depuración de la aplicación en directo
En Visual Studio (2015 y versiones posteriores), puede analizar el rendimiento y diagnosticar problemas en la aplicación web ASP.NET tanto en depuración en producción, con datos de telemetría de Azure Application Insights. La característica más adelante se extiende para incluir aplicaciones de escritorio y UWP en Visual Studio 2017 y a través del Portal de Azure. Puede encontrar información adicional sobre la depuración del proyecto [aquí](https://docs.microsoft.com/en-us/azure/azure-monitor/app/visual-studio) y supervisión del uso y rendimiento en el escritorio o aplicaciones para UWP puede encontrarse [aquí](https://docs.microsoft.com/en-us/azure/azure-monitor/app/windows-desktop).
