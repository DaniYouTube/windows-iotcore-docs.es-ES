---
title: Administrar dispositivos Windows con el Azure IoT Hub
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Obtenga información acerca de cómo administrar los dispositivos Windows con el Azure IoT Hub.
keywords: Windows IOT, Azure, DM, administración de dispositivos, Azure IoT Hub, IoT Hub, estado del dispositivo
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169043"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a>Administrar dispositivos Windows con el Azure IoT Hub

## <a name="overview"></a>Información general
La administración de dispositivos (DM) permite a los operadores configurar y supervisar de forma remota volúmenes muy altos de dispositivos IoT de forma simultánea.

La configuración de los dispositivos se puede insertar en los dispositivos, independientemente de si están en línea o sin conexión. Si el dispositivo está sin conexión, recogerá la nueva configuración cuando vuelva a conectarse. Los operadores de dispositivo también pueden recuperar el estado de cada dispositivo, incluso si las actualizaciones de configuración del dispositivo se han aplicado correctamente o no.

Habilitar estas características para dispositivos IoT requiere un mecanismo central, sólido y confiable para almacenar e implementar los datos de configuración en los dispositivos de destino y supervisar el estado del dispositivo a escala.

Una solución completa requiere lo siguiente:

* Un servicio en la nube sólido y escalable para almacenar los Estados deseados e indicados de los distintos dispositivos.
  * Azure IoT Hub y la administración de dispositivos de Azure ofrecen un servicio en la nube muy escalable y eficaz para administrar millones de dispositivos.

* Un cliente que se ejecuta en el dispositivo y puede aplicar la configuración deseada e informar del estado del dispositivo.
  * El cliente de Windows IoT Azure DM (un SDK + Runtime de código abierto), junto con Azure IoT Hub, puede aplicar e informar sobre un gran conjunto de configuraciones de Windows comunes, en ocasiones críticas.

* Un portal o una aplicación que usará el operador para configurar y consultar los dispositivos de forma remota.
  * Este debe personalizarse para dispositivos por el OEM o el operador del dispositivo. Como parte de esta solución, también proporcionamos un modelo de datos de código abierto y una implementación de ejemplo para facilitar la interacción con el almacenamiento de IoT Hub y el cliente de Windows IoT.

Para obtener más información acerca de la administración de dispositivos para dispositivos Windows, visite el repositorio principal del [cliente de administración de dispositivos](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).
