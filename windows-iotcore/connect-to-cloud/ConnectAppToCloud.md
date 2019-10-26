---
title: Conectar la aplicación a la nube
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar la aplicación a la nube.
keywords: Windows IOT, Cloud, Azure, Azure IoT Hub
ms.openlocfilehash: 281befbbbe5b71dece9b2bc139be1564f5c24a98
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918405"
---
# <a name="connect-your-app-to-the-cloud"></a>Conectar la aplicación a la nube

Esta guía paso a paso le permitirá familiarizarse con Windows 10 IoT Core, configurar el dispositivo y crear la primera aplicación que se conecta a Azure IoT Hub.

## <a name="step-1-prepare-your-device"></a>Paso 1: preparar el dispositivo

Puede encontrar instrucciones sobre cómo preparar el dispositivo en la [Página INTRODUCCIÓN](https://developer.microsoft.com/en-us/windows/iot/getstarted) y asegurarse de que [aprovisiona el TPM del dispositivo](../connect-to-cloud/ConnectDeviceToCloud.md)

## <a name="step-2-install-visual-studio-2017-and-tools"></a>Paso 2: instalar Visual Studio 2017 y herramientas

Instale [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=845271). Puede instalar cualquier edición de Visual Studio, incluida la edición gratuita Community.

Asegúrese de seleccionar las **herramientas de desarrollo de aplicaciones universales de Windows**, el componente necesario para escribir aplicaciones Windows 10:

![Herramientas de desarrollo de aplicaciones universales de Windows](../media/ConnectAppToCloud/install_tools_for_windows10.png)

## <a name="step-3-install-the-connected-services-for-azure-iot-hub"></a>Paso 3: instalar el Servicios conectados de Azure IoT Hub

La Servicios conectados de Azure IoT Hub extensión de Visual Studio le permite conectarse e iniciar la interacción con Azure IoT Hub en menos de un minuto.

Puede instalar la extensión desde la [Galería de vs](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery).

## <a name="step-4-create-a-visual-studio-uwp-solution"></a>Paso 4: creación de una solución de UWP de Visual Studio

Para crear una solución de UWP en Visual Studio, en el menú **archivo** , haga clic en **nuevo** y en **proyecto**:

![Creación de nuevo proyecto](../media/ConnectAppToCloud/new_project_menu.png)

En el cuadro de diálogo nuevo proyecto que aparece, seleccione **aplicación en blanco (Windows universal C#)** . Asigne un nombre al proyecto (e.x. **MyFirstIoTCoreApp**):

![Cuadro de diálogo Nueva solución](../media/ConnectAppToCloud/new_solution.png)

## <a name="use-the-connected-services-for-azure-iot-hub-to-connect-to-azure-iot-hub"></a>Use el Servicios conectados para que Azure IoT Hub se conecte a Azure IoT Hub

Siga las instrucciones de la [herramienta servicios conectados](https://aka.ms/azure-iot-hub-vs-2017-cs-vs-gallery) para conectar el proyecto a Azure IOT Hub. La herramienta generará dos funciones, `SendDeviceToCloudMessageAsync` y `ReceiveCloudToDeviceMessageAsync` que puede invocar en cualquier parte de la aplicación. Puede modificar estas funciones como considere oportuno.  

