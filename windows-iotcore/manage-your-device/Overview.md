---
title: Información general sobre depuración
ms.date: 05/10/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre las distintas formas en que puede depurar Windows 10 IoT Core.
keywords: Windows IOT, depuración, PowerShell, SSH
ms.openlocfilehash: 2fbfbbd9b181455b56964678d105f106acefa789
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721600"
---
# <a name="debugging-on-windows-iot-core"></a>Depuración en Windows IoT Core
Una vez que tenga la configuración de la imagen de IoT Core con la aplicación en ejecución, es importante que pueda depurar la aplicación o el sistema según sea necesario. El mejor momento para depurar y probar el sistema es el estado de la imagen de prueba. Una vez que los sistemas basados en IoT Core están fuera de la naturaleza, la depuración puede convertirse en Challanging. Esto no se puede decir que no se puede hacer, pero con capas adicionales de dificultades agregadas para depurar Comparar con las fases de prueba. Puede usar lo siguiente para depurar la aplicación o imagen en modo de prueba:

## <a name="device-portal"></a>Device Portal
Windows Device portal (WDP) permite configurar y administrar el dispositivo de IoT remoately a través de la red local. Se puede tener acceso a WDP a través de la dirección IP local del dispositivo IoT. Puede encontrar información adicional sobre WDP en IoT [aquí](https://docs.microsoft.com/windows/iot-core/manage-your-device/DevicePortal).

### <a name="collecting-etw--wpp-logs"></a>Recopilación de registros de ETW/WPP 
-----

### <a name="file-sharing"></a>Uso compartido de archivos
El explorador de archivos de la aplicación puede permitir el acceso a los directorios a los que pueden acceder las aplicaciones * vCameraRoll se comparte entre todas las aplicaciones.
* Los documentos se comparten entre todas las aplicaciones
* LocalAppData contiene carpetas específicas de cada aplicación. Esta carpeta tendrá el mismo nombre que la aplicación y otras aplicaciones no podrán acceder a ella.
Vea el vínculo anterior para obtener más información.

### <a name="kernel-debug"></a>Depuración de kernel
También puede descargar volcados de kernel en directo a través de WDP. Los bloqueos del sistema se registrarán automáticamente y estarán disponibles para su descarga. Vea el vínculo anterior para obtener más información.

### <a name="enable-crash-dump"></a>Habilitar volcado de memoria
Puede descargar volcados de memoria de aplicaciones en un dispositivo IoT a través de WDP. Vea el vínculo anterior para obtener más información.

## <a name="sshpowershelltshell"></a>SSH/PowerShell/TShell
PowerShell es un shell de línea de comandos basado en tareas y un lenguaje de scripting diseñado especialmente para la administración del sistema. Puede encontrar más información sobre la depuración y configuración de PowerShell [aquí](../connect-your-device/powershell.md).

## <a name="debug-through-visual-studio-deployment"></a>Depurar a través de la implementación de Visual Studio
La implementación y depuración de la aplicación es sencilla con Visual Studio. La característica de depuración remota se puede usar para implementar y depurar la aplicación en el dispositivo de Windows 10 IoT Core conectado localmente. [Aquí](../develop-your-app/RemoteDebugging.md)encontrará información detallada sobre la implementación y la depuración.

-----
## <a name="live-app-debug"></a>Depuración de aplicación activa
En Visual Studio (2015 y versiones posteriores), puede analizar el rendimiento y diagnosticar problemas en la aplicación Web de ASP.NET en la depuración y en producción, mediante la telemetría de Aplicación de Azure Insights. La característica se extiende posteriormente para incluir aplicaciones de escritorio y UWP en Visual Studio 2017 y a través de Azure portal. Puede encontrar información adicional sobre cómo depurar el proyecto [aquí](https://docs.microsoft.com/azure/azure-monitor/app/visual-studio) y supervisar el uso, y el rendimiento de las aplicaciones de escritorio o UWP [aquí](https://docs.microsoft.com/azure/azure-monitor/app/windows-desktop).
