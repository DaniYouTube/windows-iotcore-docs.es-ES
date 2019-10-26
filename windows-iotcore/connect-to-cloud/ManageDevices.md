---
title: Administrar dispositivos Windows con el Azure IoT Hub
ms.date: 01/08/2018
ms.topic: article
description: Obtenga información acerca de cómo administrar los dispositivos Windows con el Azure IoT Hub.
keywords: Windows IOT, Azure, DM, administración de dispositivos, Azure IoT Hub, IoT Hub, estado del dispositivo
ms.openlocfilehash: 7eea1a8d3ccfd35bcdb7ebae44803135db05f824
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918386"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a>Administrar dispositivos Windows con el Azure IoT Hub

## <a name="overview"></a>Introducción
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
