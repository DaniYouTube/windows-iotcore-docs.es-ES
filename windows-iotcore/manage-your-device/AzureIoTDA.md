---
title: Agente de dispositivo IoT de Azure
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos mediante el agente de dispositivo IoT de Azure en Windows IoT.
keywords: Windows iot, IoT de Azure, Azure agente de dispositivos, administración de dispositivos, administración remota
ms.openlocfilehash: 4f7336cd1c4c2af903c0a74254e1b8e73ff077b9
ms.sourcegitcommit: 823ca02f515a577a2bdc469602a228365cb6ebf8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67467687"
---
# <a name="azure-iot-device-agent"></a>Agente de dispositivo IoT de Azure

En cuanto a los dispositivos conectados, administración de dispositivo remoto es una de las características clave que necesitan de operadores de sistema. Permite a los operadores configurar propiedades y actualización de software en el dispositivo de forma remota, sin necesidad de tener acceso local o físico al dispositivo. Con Windows IoT Core y Windows IoT Enterprise que se ejecutan en dispositivos como aparatos domésticos, sistemas HVAC y otros usuarios, es necesario para una solución de administración de dispositivos ligeros personalizable. Mientras que las versiones de Windows 10 ya ofrece Mobile Device Management (MDM) en función de [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management), esto se utiliza principalmente en soluciones empresariales con herramientas de administración como SCCM o Intune. Aunque estas soluciones son adecuadas para los dispositivos que se colocan en un entorno empresarial, plantea desafíos en la configuración más diverso que vemos en soluciones de IoT. Los dispositivos de IoT también requieren una solución de administración de dispositivo de superficie ligera, pequeño que puede ser un desafío. Microsoft también ofrece dispositivo capacidades de administración usando [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview) y su [SDK](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-devguide-sdks). El [agente de dispositivo IoT de Azure](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) reúne ambas funciones: las funcionalidades de administración de dispositivos en la nube a través de IoT Hub que funciona con el mismo estándar [Configuration Service Providers(CSP)](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference) ya que usa administración de dispositivos móviles. Con el agente de dispositivo de Azure, los OEM pueden crear los dispositivos que ofrecen estas capacidades de administración de dispositivos sin escribir ningún código. 

El agente de dispositivos de Azure es un paquete de código abierto listo para la compilación que permite capacidades de administración de dispositivo remoto. El agente de dispositivo de Azure es compatible con Windows 10 IoT Core y Windows 10 IoT Enterprise y funciona en los dispositivos conectados a través de IoT Hub. Los OEM pueden crear ahora dispositivos compatibles con SCCM, Intune o Azure IoT Hub para administración de dispositivos y dejar en manos de sus clientes para seleccionar la solución de administración de dispositivos que se adapte a su mejor.   

![Administración de dispositivos de IOT de Azure](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>¿Cómo funciona?

El [agente de dispositivo IoT de Azure](https://aka.ms/iot-core-azure-dm-client) consta de 2 componentes principales. 

El cliente del servicio de aprovisionamiento de dispositivos (cliente de DPS) automatiza el aprovisionamiento de dispositivos. Se conecta al servicio Azure Device Provisioning con ScopeID DPS y la clave de inscripción del dispositivo. El servicio DPS Azure identifica el dispositivo y lo aprovisiona en el centro de IoT configurado y devuelve una cadena de conexión al dispositivo. El cliente DPS, a continuación, utiliza esta cadena de conexión para conectar el dispositivo a la versión apropiada de IoT Hub.  

El cliente de administración de dispositivos permite funcionalidades de administración de dispositivos remotos mediante el [proveedores de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP) capacidades de administración remota del agente de la Azure dispositivo es compatible con un modelo de complemento que permite a Seleccione solo las capacidades que necesita. Además de eso, la arquitectura de complementos es extensible. Puede escribir su propio complemento para una funcionalidad de administración del dispositivo que necesita y agregarlo al agente de dispositivo de Azure. Todas las capacidades de administración de dispositivos son accesibles de forma remota con el dispositivo gemelo o las propiedades del módulo gemelo y comandos, lo que permite un enfoque de administración único panel de vidrio para todos los dispositivos de Windows IoT. Para obtener una lista completa de administración de dispositivos, las funcionalidades disponibles hacen referencia a [esto](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md)

Además, el agente de dispositivos de Azure también crea y administra los tokens de SAS para otras aplicaciones de UWP que se ejecutan en el dispositivo. El agente de dispositivos de Azure puede aprovisionar otras aplicaciones UWP, como un dispositivo gemelo o como un módulo gemelo y agregar sus cadenas de conexión a los respectivos espacios TPM. El aprovechamiento de la aplicación UWP el [puente de UWP](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md) para leer su conexión de cadena de la ranura TPM y que puede usar para conectarse a IoT Hub. 

## <a name="how-to-get-started"></a>¿Cómo empezar a trabajar?

El agente de dispositivo IoT de Azure está disponible en GitHub. El proyecto también incluye ejemplos para empezar a trabajar rápidamente. Para obtener más información, visite nuestro GitHub [repositorio](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md)

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>Migración de dispositivos de Azure agente V1 a V2
Si actualmente utiliza la versión v1 del agente de dispositivo, un cambio importante entre V1 y V2 es que en la versión V2, el agente de dispositivos de Azure ya no comparte la conexión con una aplicación UWP. Con mejoras en el centro de IoT puede tener ahora la aplicación para UWP y el agente de dispositivos de Azure con cadenas de conexión independiente y todavía se puede asociar con el mismo dispositivo en IoT Hub. Consulte [aquí](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md) para obtener más detalles.

Para obtener más información sobre el agente de dispositivo de Azure V1, consulte [aquí](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/azureiotdm).

## <a name="other-useful-tools"></a>Otras herramientas útiles 
### <a name="dm-mock-portal"></a>Portal de simulacro de DM
[Portal de simulación de DM](https://github.com/ms-iot/azure-client-tools/blob/master/docs/dm-mock-portal/dm-mock-portal.md) es una aplicación que se puede usar para establecer las propiedades de dispositivo gemelo o módulo gemelo en un dispositivo individual o a través de varios dispositivos, con capacidades de administración automática de dispositivos del centro de IoT. 

### <a name="tpm-tool---limpetexe"></a>Herramienta TPM - Limpet.exe
El servicio Azure Device Provisioning permite a los clientes que se asociarán automáticamente y configurar un dispositivo con una producción posterior a la instancia de IoT Hub. Este proceso, el servicio Device Provisioning necesitará un identificador de dispositivo único y challengeable para ayudarle a configurar el dispositivo de forma segura cuando el dispositivo se coloca en la operación. Servicio Device Provisioning usa la clave de aprobación pública del TPM (EKeyPub) para este propósito. Para registrar el dispositivo en DPS, el EKeyPub debe ser recopiladas desde el dispositivo. Es el momento que prefiera para este paso durante la producción (durante las pruebas finales de línea del dispositivo). Sin embargo, el proceso también puede realizarse postproducción si es necesario.  

Microsoft proporciona una herramienta videocámara para simplificar el proceso de registro del servicio Device Provisioning. Según la configuración de fabricación, si hay una conexión en línea, se puede registrar el dispositivo mediante videocámara directamente con el servicio Device Provisioning o videocámara puede recopilar el EKeyPub para un registro más adelante, sin conexión del dispositivo con el dispositivo Servicio de aprovisionamiento.

Para obtener más detalles sobre el proceso de registro del servicio Device Provisioning con videocámara, consulte este [repositorio](https://github.com/ms-iot/azure-client-tools/blob/master/docs/limpet/limpet.md).

Licencia: Videocámara con licencia bajo la licencia de código abierto de MIT. 
