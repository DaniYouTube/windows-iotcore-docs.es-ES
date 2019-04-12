---
title: Conectar su aplicación a la nube
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar su aplicación a la nube.
keywords: Windows iot, en la nube, Azure, Azure IoT Hub
ms.openlocfilehash: 3f7f50ba87e269fa8ac958f80affbd2fd0af5c53
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514776"
---
# <a name="connect-your-app-to-the-cloud"></a>Conectar su aplicación a la nube

Esta guía paso a paso le permitirá familiarizarse con Windows 10 IoT Core, configurar el dispositivo y crear su primera aplicación que se conecta a Azure IoT Hub.

## <a name="step-1-prepare-your-device"></a>Paso 1: Preparar el dispositivo

Puede encontrar instrucciones sobre cómo preparar el dispositivo en el [obtener la página de introducción de](https://developer.microsoft.com/en-us/windows/iot/getstarted) asegurarse de que se [aprovisione el TPM del dispositivo](../connect-to-cloud/ConnectDeviceToCloud.md)

## <a name="step-2-install-visual-studio-2017-and-tools"></a>Paso 2: Instalar Visual Studio 2017 y herramientas

Instalar [de Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271). Puede instalar cualquier edición de Visual Studio, incluida la edición Community gratis.

Asegúrese de seleccionar el **herramientas de desarrollo de aplicaciones universales de Windows**, el componente necesario para escribir aplicaciones de Windows 10:

![Herramientas de desarrollo de aplicaciones de Windows universal](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>Paso 3: Instalar los servicios conectados para Azure IoT Hub

Los servicios conectados de la extensión de Visual Studio de Azure IoT Hub le permite conectarse y empezar a interactuar con Azure IoT Hub en menos de un minuto.

Puede instalar la extensión desde el [VS galería](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>Paso 4: Crear una solución de UWP de Visual Studio

Para crear una solución UWP en Visual Studio, en el **archivo** menú, haga clic en **New** , a continuación, **proyecto**:

![Crear un proyecto](../media/ConnectAppToCloud/new_project_menu.png)

En el cuadro de diálogo nuevo proyecto que aparece, seleccione **Visual de la aplicación vacía (Windows Universal) C#** . Asigne al proyecto un nombre (e.x. **MyFirstIoTCoreApp**):

![Cuadro de diálogo nueva solución](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>Usar los servicios conectados para Azure IoT Hub para conectarse a Azure IoT Hub

Siga las instrucciones de la [herramienta Connected Services](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) para conectar el proyecto a Azure IoT Hub. La herramienta generará dos funciones `SendDeviceToCloudMessageAsync` y `ReceiveCloudToDeviceMessageAsync` que se puede invocar en cualquier lugar en la aplicación. Puede modificar estas funciones como considere oportuno.  

