---
title: Conectar el dispositivo a la nube
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar el dispositivo a la nube.
keywords: seguridad de Azure, de iot, Windows, el módulo de plataforma segura, SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515023"
---
# <a name="connect-your-device-to-the-cloud"></a>Conectar el dispositivo a la nube

Almacenar información segura, como una contraseña o un certificado en un dispositivo podría hacer que un dispositivo sea vulnerable a la exposición. Una contraseña filtrada es una manera reír para poner en peligro la seguridad de un dispositivo o un sistema completo. En la familia Windows, la tecnología que admite la seguridad del sistema operativo es el módulo de plataforma segura.

Un [módulo de plataforma segura](https://en.wikipedia.org/wiki/Trusted_Platform_Module) dispositivo (TPM) es un microcontrolador que puede almacenar datos y realizar cálculos. Puede ser un chip discreto soldado a la placa base de un equipo o un módulo integrado en el sistema en un chip (SoC) por el fabricante. 

## <a name="inside-the-tpm"></a>Dentro de TPM 

Una capacidad clave de TPM es su memoria de solo escritura. En función de los datos en ella, TPM también puede calcular un hash criptográfico (como el [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), en función de esos datos.
No es posible descubrir el secreto dado el hash, pero si se conoce el secreto para ambas partes de comunicación, es posible determinar si se ha generado el hash recibido de otra entidad desde ese secreto.

La idea básica mediante claves criptográficas: se establece el secreto (también denominado clave de acceso compartido) y se comparte entre el dispositivo de IoT y la nube durante el proceso de aprovisionamiento de dispositivos. Desde ese momento, un HMAC que se deriva el secreto se usarán para autenticar el dispositivo de IoT.

## <a name="device-provisioning"></a>Aprovisionamiento de dispositivos 

La herramienta que aprovisiona los dispositivos Windows 10 IoT Core se denomina el panel de IoT Core y puede descargarse desde [la página de descargas](http://go.microsoft.com/fwlink/?LinkID=708576).

El panel genera una imagen del sistema operativo y conecta el dispositivo con seguridad en Azure. Esto se hace mediante la asociación del dispositivo físico con el identificador de dispositivo en IoT Hub de Azure e impresiones de la clave específica del dispositivo de acceso compartido en TPM del dispositivo. 

Para los dispositivos que no tienen un chip de TPM, la herramienta puede instalar un TPM de software emulados. Esto no proporciona seguridad, pero le permite desarrollar aplicaciones mediante un dispositivo maker (como Raspberry Pi 2 o 3) y tiene seguridad "iluminada" en un dispositivo con el hardware TPM sin tener que cambiar la aplicación. 

Para conectar el dispositivo a Azure, haga clic en la pestaña "Conectar a Azure":

![Abrir conectarse a la pestaña de Azure](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

Se le pedirá que inicie sesión en su cuenta de Azure. Seleccione la instancia de Azure IoT Hub deseada y asociar el dispositivo físico. Si no tiene ninguna instancia de IoT Hub en su suscripción de Azure, la herramienta permitirá crear una instancia gratuita. 

Una vez haya seleccionado el centro de IoT y el identificador de dispositivo para asociar el dispositivo con, puede transmitir la clave de acceso compartido de ese dispositivo en el TPM:

![Dispositivo de provisión](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

El dispositivo ahora está listo para conectarse a Azure de forma segura. 

También puede usar el Windows Device Portal para adquirir una cadena de conexión de IoT Hub de forma dinámica cuando primero se conecta a internet después de que se está aprovisionando. Esto puede hacerse desde la pestaña "Clientes de Azure" en el Portal de dispositivo.

![Pestaña de clientes de Azure](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a>Recursos útiles:
* [Conectar la aplicación a Azure](../connect-to-cloud/ConnectAppToCloud.md)
* [Creación de aplicaciones seguras para IoT Core](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
