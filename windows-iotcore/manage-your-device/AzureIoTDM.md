---
title: Administración de dispositivos IoT de Azure
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos con administración de dispositivos de IoT de Azure y Windows IoT.
keywords: Windows iot, IoT de Azure, administración de dispositivos de Azure, administración de dispositivos
ms.openlocfilehash: eb8f99c91ec5d4b6bdb27d7aa0b1cd7e7f20cc2b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514724"
---
# <a name="azure-iot-device-management"></a>Administración de dispositivos IoT de Azure

En cuanto a los dispositivos conectados, administración de dispositivo remoto es una de las características clave que se utilizan operadores de sistema. Permite a los operadores volver a configurar y actualizar el software y los parámetros del dispositivo de forma remota sin necesidad de tener acceso físico al dispositivo local. Con Windows 10 IoT Core, los OEM pueden crear los dispositivos que ofrecen estas capacidades fuera-listos. Windows 10 IoT Core, así como otras versiones de Windows 10, ya que ofrece Mobile Device Management (MDM) en función de [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management). Esto se utiliza principalmente en soluciones empresariales con herramientas de administración como SCCM o Intune. Aunque estas soluciones son adecuadas para los dispositivos que se colocan en un entorno empresarial, plantea desafíos en la configuración más diverso que vemos en soluciones de IoT. Dichos desafíos también se ven en dispositivos de IoT que requieren la administración de dispositivos ligeros. Para estos dispositivos, Microsoft ofrece [administración de dispositivos a través de Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview).

## <a name="scalable-device-management-with-windows-iot"></a>Administración de dispositivos escalables con Windows IoT

Con Windows IoT Core que se ejecutan en dispositivos como aparatos domésticos, sistemas HVAC y otros usuarios, es necesario para una solución de administración de dispositivos ligeros personalizable. En la edición de creador de Windows, Microsoft permite [administración de dispositivos Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview). Los OEM pueden usar el [Windows IoT Azure biblioteca de cliente](https://aka.ms/iot-core-azure-dm-client) agregar capacidades de administración de dispositivos a su centro de IoT de Azure de los dispositivos conectados. Esta biblioteca tendrá acceso a los componentes de administración de dispositivos de Windows estándares ([proveedores de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP).  Los OEM pueden crear ahora dispositivos compatibles con SCCM, Intune y Azure IoT Hub para administración de dispositivos y dejar en manos de sus clientes para seleccionar el tipo de solución de minería de datos que se adapte a su mejor. 

![Administración de dispositivos de IOT de Azure](../media/AzureIoTDM/azureDM.png)

## <a name="how-does-it-work"></a>¿Cómo funciona?

El [Windows IoT Azure biblioteca de cliente](https://aka.ms/iot-core-azure-dm-client) está vinculada a la aplicación host. Comparte la conexión de Azure IoT Hub con la aplicación host. Lo que hace que la inscripción adicionales para habilitar la administración de dispositivos innecesaria. La siguiente imagen muestra la arquitectura de una solución de DM de Azure IoT Hub mediante la biblioteca de cliente de DM de Azure IoT de Windows. 

![Diagrama de flujo de DM de Azure](../media/AzureIoTDM/AzureDM-Architecture.png)

Microsoft proporciona dos componentes del sistema, CommProxy.exe y SystemConfigurator.exe, que el OEM debe incluir en la imagen del dispositivo. Estos componentes proporcionan acceso a los CSP. El IoTDMClientLib asigne la interfaz CSP a las funciones que pueden utilizarse en la administración de dispositivos Azure IoT Hub. También proporciona funciones de minería de datos que no usan un CSP, por ejemplo, establecer la zona de horaria. El IoTDMClientLib se proporciona como un componente de código abierto. Los OEM pueden ampliarlo para agregar las características que son específicas de su dispositivo, como las configuraciones de sensores o actuadores. 

## <a name="device-health-attestation"></a>Certificación de estado del dispositivo
Para una operación segura de dispositivos de IoT es esencial para evaluar si se arranca un dispositivo en un estado compatible y de confianza. Con [atestación de estado de dispositivo (DHA) de Windows IoT](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) operadores pueden comprobar el estado de seguridad de un dispositivo y realizar acciones correctoras adecuadas si es necesario a través de [administración de dispositivos de Azure IoT Hub](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md). DHA forma parte del cliente de administración de dispositivos de Azure de Windows IoT Core. Para usar la capacidad DHA en su solución requiere acceso al servicio Microsoft DHA. Una suscripción al servicio está disponible a través de la [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview).

### <a name="reference"></a>Referencia
[Atestación de estado de dispositivo IoT de Azure DM](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)

[Implemente recursos de Azure para la atestación de estado de dispositivo](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)


## <a name="how-to-get-started"></a>¿Cómo empezar a trabajar?

Biblioteca de cliente de DM de Azure IoT Windows está disponible en GitHub. Junto al proyecto IoTDMClientLib también incluye ejemplos para empezar a trabajar rápidamente. Para obtener más información, consulte los vínculos siguientes.

### <a name="project-github-page"></a>Página de GitHub del proyecto

[Biblioteca de cliente de DM de Azure IoT Windows](https://aka.ms/iot-core-azure-dm-client) está disponible en GitHub.

### <a name="dm-dashboard"></a>Panel de DM

[Panel de DM](https://aka.ms/iot-core-azure-dm-client-dashboard) es una aplicación para probar la función de minería de datos en un dispositivo. La aplicación se conecta al dispositivo a través de Azure IoT Hub. La aplicación puede usarse para validar las funciones de minería de datos del dispositivo. Se puede ampliar para probar las funciones de minería de datos de terceros que se agregaron a la IoTDMClientLib.

### <a name="dm-background-application"></a>Aplicación de minería de datos en segundo plano

El [aplicación en segundo plano de DM](https://aka.ms/iot-core-azure-dm-client-backgroundapp) muestra cómo se puede usar el IoTDMClientLib en una aplicación que se conecta a Azure IoT Hub y debe ejecutarse como aplicación en segundo plano en Windows IoT Core. 

### <a name="toaster-application"></a>Aplicación Toaster

El [aplicación Toaster](https://aka.ms/iot-core-azure-dm-client-toasterapp), como la aplicación de fondo de la administración de dispositivos anterior, se habilitará las capacidades de DM de Azure para un dispositivo. Esta aplicación se ejecutará en primer plano y permitir el acceso a los parámetros de minería de datos y funciones a través de los dispositivos de interfaz de usuario. 

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>Registrar el dispositivo con el servicio de aprovisionamiento de dispositivo de Azure (DPS) 

El servicio Azure Device Provisioning permite a los clientes que se asociarán automáticamente y configurar un dispositivo con una producción posterior a la instancia de IoT Hub. Por este proceso, servicio Device Provisioning es un identificador de dispositivo único y challengeable para ayudarle a configurar el dispositivo de forma segura cuando el dispositivo se coloca en la operación. Servicio Device Provisioning usa la clave de aprobación pública del TPM (EKeyPub) para este propósito. Para registrar el dispositivo en DPS, el EKeyPub debe ser recopiladas desde el dispositivo. Es el momento que prefiera para este paso durante la producción (durante las pruebas finales de línea del dispositivo). Sin embargo, el proceso también puede realizarse postproducción si es necesario.  

Microsoft proporciona una herramienta videocámara para simplificar el proceso de registro del servicio Device Provisioning. Según la configuración de fabricación, si hay una conexión en línea, se puede registrar el dispositivo mediante videocámara directamente con el servicio Device Provisioning o videocámara puede recopilar el EKeyPub para un registro más adelante, sin conexión del dispositivo con el dispositivo Servicio de aprovisionamiento.

Para obtener más detalles sobre el proceso de registro del servicio Device Provisioning con videocámara, consulte el [inscribir el dispositivo en el servicio Device Provisioning](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) sección la [documentación videocámara](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md). 

Repositorio del proyecto: [Repositorio del proyecto videocámara](https://github.com/ms-iot/azure-dm-client/) 


Licencia: Videocámara con licencia bajo la licencia de código abierto de MIT 

  
  

