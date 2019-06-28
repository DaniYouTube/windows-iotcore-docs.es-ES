---
title: Agente de dispositivo IoT de Azure
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos mediante el agente de dispositivo IoT de Azure en Windows IoT.
keywords: Windows iot, IoT de Azure, Azure agente de dispositivos, administración de dispositivos, administración remota
ms.openlocfilehash: 63c51d6281651e8f80fb3a0bdb350f919301fa69
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412309"
---
# <a name="azure-iot-device-agent"></a>Agente de dispositivo IoT de Azure

En cuanto a los dispositivos conectados, administración de dispositivo remoto es una de las características clave que se utilizan operadores de sistema. Permite a los operadores volver a configurar y actualizar el software y los parámetros del dispositivo de forma remota sin necesidad de tener acceso físico al dispositivo local. Con Windows 10 IoT Core, los OEM pueden crear los dispositivos que ofrecen estas capacidades fuera-listos. Windows 10 IoT Core, así como otras versiones de Windows 10, ya que ofrece Mobile Device Management (MDM) en función de [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management). Esto se utiliza principalmente en soluciones empresariales con herramientas de administración como SCCM o Intune. Aunque estas soluciones son adecuadas para los dispositivos que se colocan en un entorno empresarial, plantea desafíos en la configuración más diverso que vemos en soluciones de IoT. Dichos desafíos también se ven en dispositivos de IoT que requieren la administración de dispositivos ligeros. Para estos dispositivos, Microsoft ofrece [administración de dispositivos a través de Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview).

## <a name="scalable-device-management-with-windows-iot"></a>Administración de dispositivos escalables con Windows IoT

Con Windows IoT Core que se ejecutan en dispositivos como aparatos domésticos, sistemas HVAC y otros usuarios, es necesario para una solución de administración de dispositivos ligeros personalizable. Los OEM pueden usar el [agente de dispositivo IoT de Azure](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) agregar capacidades de administración de dispositivos a su IoT Hub de Azure de los dispositivos conectados. Este paquete de código abierto listo para la compilación que habilitan las capacidades de administración de dispositivo remoto mediante el acceso a los componentes de administración de dispositivos de Windows estándares ([proveedores de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP).  Los OEM pueden crear ahora dispositivos compatibles con SCCM, Intune y Azure IoT Hub para administración de dispositivos y dejar en manos de sus clientes para seleccionar la solución de administración de dispositivos que se adapte a su mejor. 

![Administración de dispositivos de IOT de Azure](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>¿Cómo funciona?

![Agente de dispositivo IoT de Azure](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/high-level-e2e.png) el [agente de dispositivo IoT de Azure](https://aka.ms/iot-core-azure-dm-client) consta de 2 componentes principales. El dispositivo aprovisionamiento Client(DPS) automatiza el aprovisionamiento de dispositivos. Se conecta al servicio Azure Device Provisioning con ScopeID DPS y la clave de inscripción del dispositivo. El servicio DPS Azure identifica el dispositivo y lo aprovisiona en el centro de IoT configurado y devuelve una cadena de conexión al dispositivo. El cliente DPS, a continuación, utiliza esta cadena de conexión para conectar el dispositivo a la versión apropiada de IoT Hub.  

El cliente de administración de dispositivos permite capacidades de administración remota mediante el aprovechamiento de las capacidades que están disponibles a través de la ([proveedores de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP) son funciones de administración remota del agente de la Azure dispositivo se basa en una arquitectura de complemento que permite elegir de forma selectiva las capacidades que desea incluir en el dispositivo. Además de eso, la arquitectura de complementos es extensible. Puede escribir su propio complemento para una funcionalidad de administración del dispositivo que necesita y agregarlo al agente de dispositivo de Azure. Todas las capacidades de administración de dispositivos son accesibles de forma remota con el dispositivo gemelo o las propiedades del módulo gemelo y comandos, lo que permite un enfoque de administración único panel de vidrio para todos los dispositivos de Windows IoT implementado. Para obtener una lista completa de administración de dispositivos, las funcionalidades disponibles hacen referencia a [esto](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md)

Además, el agente de dispositivos de Azure también crea y administra los tokens de SAS para otras aplicaciones de UWP que se ejecutan en el dispositivo. El agente de dispositivos de Azure puede aprovisionar otras aplicaciones UWP, como un dispositivo gemelo o como un módulo gemelo y agregar sus cadenas de conexión a los respectivos espacios TPM. La aplicación para UWP aprovecha el [puente de UWP] (https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md) para leer su conexión de cadena de la ranura TPM y que puede usar para conectarse a IoT Hub. 

## <a name="how-to-get-started"></a>¿Cómo empezar a trabajar?

El agente de dispositivo IoT de Azure está disponible en GitHub. El proyecto también incluye ejemplos para empezar a trabajar rápidamente. Para obtener más información, consulte los vínculos siguientes.

### <a name="project-github-page"></a>Página de GitHub del proyecto

[Agente de dispositivo IoT de Azure](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) está disponible en GitHub.

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>Migración de dispositivos de Azure agente V1 a V2
Si actualmente utiliza la versión v1 del agente de dispositivo, un cambio importante entre V1 y V2 es que en la versión V2, el agente de dispositivos de Azure ya no comparte la conexión con una aplicación UWP. Con mejoras en el centro de IoT puede tener ahora la aplicación para UWP y el agente de dispositivos de Azure con cadenas de conexión independiente y todavía se puede asociar con el mismo dispositivo en IoT Hub. Consulte [aquí](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md) para obtener más detalles.
Para obtener más información sobre el agente de dispositivo de Azure V1, consulte [aquí](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/azureiotdm)

## <a name="other-useful-tools"></a>Otras herramientas útiles 
### <a name="dm-dashboard"></a>Panel de DM
[Panel de DM](https://aka.ms/iot-core-azure-dm-client-dashboard) es una aplicación para probar la función de minería de datos en un dispositivo. La aplicación se conecta al dispositivo a través de Azure IoT Hub. La aplicación puede usarse para validar las funciones de minería de datos del dispositivo. Se puede ampliar para probar las funciones de DM de terceros que se agregaron al agente de dispositivo de Azure.

### <a name="tpm-tool---limpetexe"></a>Herramienta TPM - Limpet.exe
El servicio Azure Device Provisioning permite a los clientes que se asociarán automáticamente y configurar un dispositivo con una producción posterior a la instancia de IoT Hub. Por este proceso, servicio Device Provisioning es un identificador de dispositivo único y challengeable para ayudarle a configurar el dispositivo de forma segura cuando el dispositivo se coloca en la operación. Servicio Device Provisioning usa la clave de aprobación pública del TPM (EKeyPub) para este propósito. Para registrar el dispositivo en DPS, el EKeyPub debe ser recopiladas desde el dispositivo. Es el momento que prefiera para este paso durante la producción (durante las pruebas finales de línea del dispositivo). Sin embargo, el proceso también puede realizarse postproducción si es necesario.  

Microsoft proporciona una herramienta videocámara para simplificar el proceso de registro del servicio Device Provisioning. Según la configuración de fabricación, si hay una conexión en línea, se puede registrar el dispositivo mediante videocámara directamente con el servicio Device Provisioning o videocámara puede recopilar el EKeyPub para un registro más adelante, sin conexión del dispositivo con el dispositivo Servicio de aprovisionamiento.

Para obtener más detalles sobre el proceso de registro del servicio Device Provisioning con videocámara, consulte el [inscribir el dispositivo en el servicio Device Provisioning](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) sección la [documentación videocámara](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md). 

Repositorio del proyecto: ([repositorio del proyecto videocámara]https://github.com/ms-iot/azure-dm-client/) 

Licencia: Videocámara con licencia bajo la licencia de código abierto de MIT 

## <a name="device-health-attestation"></a>Certificación de estado del dispositivo
Para una operación segura de dispositivos de IoT es esencial para evaluar si se arranca un dispositivo en un estado compatible y de confianza. Con [atestación de estado de dispositivo (DHA) de Windows IoT](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) operadores pueden comprobar el estado de seguridad de un dispositivo y realizar acciones correctoras adecuadas si es necesario a través de [administración de dispositivos de Azure IoT Hub](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md). DHA forma parte del cliente de administración de dispositivos de Azure de Windows IoT Core. Para usar la capacidad DHA en su solución requiere acceso al servicio Microsoft DHA. Una suscripción al servicio está disponible a través de la [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview).

### <a name="reference"></a>Referencia
[Atestación de estado de dispositivo IoT de Azure DM](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)

[Implemente recursos de Azure para la atestación de estado de dispositivo](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)








### <a name="more-about-the-azure-device-provision-service-dps"></a>Más información sobre el servicio de aprovisionamiento de dispositivos de Azure (DPS) 


  
  

