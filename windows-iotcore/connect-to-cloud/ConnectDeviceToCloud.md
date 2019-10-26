---
title: Conectar el dispositivo a la nube
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar el dispositivo a la nube.
keywords: Windows IOT, Azure, seguridad, Módulo de plataforma segura, SoC
ms.openlocfilehash: 6bce16b45175c4c19156f30f35f6d3502f675930
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918397"
---
# <a name="connect-your-device-to-the-cloud"></a>Conectar el dispositivo a la nube

Almacenar información segura, como una contraseña o un certificado en un dispositivo, puede hacer que un dispositivo sea vulnerable a la exposición. Una contraseña filtrada es una forma SureFire de poner en peligro la seguridad de un dispositivo o de un sistema completo. En la familia de Windows, la tecnología que admite la seguridad del sistema operativo es la Módulo de plataforma segura.

Un dispositivo [módulo de plataforma segura](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) es un microcontrolador que puede almacenar datos y realizar cálculos. Puede ser un chip discreto soldado a la placa base de un equipo o un módulo integrado en el sistema en un chip (SoC) por el fabricante. 

## <a name="inside-the-tpm"></a>Dentro de TPM 

Una funcionalidad clave de TPM es la memoria de solo escritura. En función de los datos que contenga, TPM también puede calcular un hash criptográfico (como [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), basado en esos datos.
No es posible descubrir el secreto dado el hash, pero si ambas partes de la comunicación conocen el secreto, es posible determinar si el hash recibido de otra entidad se produjo a partir de ese secreto.

La idea básica detrás del uso de claves criptográficas: el secreto (también denominado clave de acceso compartido) se establece y comparte entre el dispositivo IoT y la nube durante el proceso de aprovisionamiento de dispositivos. A partir de ese momento, se usará un HMAC derivado del secreto para autenticar el dispositivo de IoT.

## <a name="device-provisioning"></a>Aprovisionamiento de dispositivos 

La herramienta que aprovisiona dispositivos Windows 10 IoT Core se denomina panel de IoT Core y se puede descargar desde [la página de descargas](http://go.microsoft.com/fwlink/?LinkID=708576).

El panel genera una imagen del sistema operativo y conecta de forma segura el dispositivo a Azure. Esto se realiza asociando el dispositivo físico con el identificador del dispositivo en el Azure IoT Hub e imprime la clave de acceso compartida específica del dispositivo en el TPM del dispositivo. 

En el caso de los dispositivos que no tienen un chip de TPM, la herramienta puede instalar un TPM emulado por software. Esto no proporciona seguridad, pero permite desarrollar la aplicación mediante un dispositivo de creador (como Raspberry pi 2 o 3) y hacer que la seguridad "se ilumine" en un dispositivo con el TPM de hardware sin tener que cambiar la aplicación. 

Para conectar el dispositivo a Azure, haga clic en la pestaña "conectar con Azure":

![Abra la pestaña conectar a Azure.](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

Se le pedirá que inicie sesión en su cuenta de Azure. Seleccione la instancia deseada de Azure IoT Hub y asocie el dispositivo físico con ella. Si no tiene ninguna instancia de IoT Hub en su suscripción de Azure, la herramienta le permitirá crear una instancia gratuita. 

Una vez que haya seleccionado el IoT Hub y el ID. de dispositivo con el que asociar el dispositivo, puede incluir la clave de acceso compartido de dicho dispositivo en el TPM:

![Aprovisionar dispositivo](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

El dispositivo ya está listo para conectarse a Azure de forma segura. 

También puede usar el portal de dispositivos de Windows para adquirir dinámicamente una cadena de conexión de IoT Hub cuando se conecta por primera vez a Internet después de aprovisionarse. Esto puede realizarse desde la pestaña "clientes de Azure" en el portal de dispositivos.

![Pestaña clientes de Azure](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a>Recursos útiles:
* [Conexión de la aplicación a Azure](../connect-to-cloud/ConnectAppToCloud.md)
* [Compilación de aplicaciones seguras para IoT Core](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
