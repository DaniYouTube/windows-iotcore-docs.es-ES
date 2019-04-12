---
title: Administrar dispositivos Windows con Azure IoT Hub
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos de Windows con Azure IoT Hub.
keywords: Windows iot, Azure, DM, administración de dispositivos Azure IoT Hub, IoT Hub, el estado del dispositivo
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514679"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a>Administrar dispositivos Windows con Azure IoT Hub

## <a name="overview"></a>Información general
Administración de dispositivos (DM) permite a los operadores configurar y supervisar simultáneamente muy grandes volúmenes de dispositivos IoT de forma remota.

Configuración de los dispositivos se puede insertar en los dispositivos, si los dispositivos de destino están en línea o sin conexión. Si el dispositivo está desconectado recogerá la nueva configuración cuando se vuelve a conectar. Operadores de dispositivo también pueden recuperar el estado de cada dispositivo, incluso si las actualizaciones de configuración de dispositivo se han aplicado correctamente o no.

Habilitar estas características para los dispositivos de IoT requiere una central, sólida y confiable mecanismo para almacenar e implementar los datos de configuración para los dispositivos de destino y supervisar el estado de dispositivo, a escala.

Una solución completa requiere lo siguiente:

* Un servicio de nube sólida y escalable para almacenar los Estados deseados y notificados de los diversos dispositivos.
  * Azure IoT Hub y administración de dispositivos de Azure ofrecen un servicio en la nube altamente escalable y eficaz para administrar millones de dispositivos.

* Un cliente que se ejecuta en el dispositivo y puede aplicar la configuración deseada y notificar el estado del dispositivo.
  * El cliente de minería de datos Windows Azure de IoT (un código abierto SDK + en tiempo de ejecución), junto con Azure IoT Hub, puede aplicar y notificar un gran conjunto de común, en ocasiones, crítico, las configuraciones de Windows.

* Un Portal o una aplicación que se utilizará el operador para configurar y consultar los dispositivos de forma remota.
  * Esto debe personalizarse para dispositivos con el dispositivo de OEM u operador. Como parte de esta solución, también proporcionamos un modelo de datos de código abierto y ejemplo de implementación para la interacción sea más fácil con el almacenamiento de IoT Hub y el cliente de Windows IoT.

Para obtener más información sobre la administración de dispositivos para dispositivos de Windows, visite principal [repositorio de administración de cliente de dispositivo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).
