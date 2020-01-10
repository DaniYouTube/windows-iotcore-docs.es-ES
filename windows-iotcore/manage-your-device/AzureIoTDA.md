---
title: Agente de dispositivos Azure IoT
author: rcheeran
ms.author: rcheeran
ms.date: 06/25/2019
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos con el agente de dispositivos IoT de Azure en Windows IoT.
keywords: Windows IOT, Azure IoT, agente de dispositivos de Azure, administración de dispositivos, administración remota
ms.openlocfilehash: 762ac7c3e0b40ce3bbe5cd33fba13838318198d7
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721450"
---
# <a name="azure-iot-device-agent"></a>Agente de dispositivos Azure IoT

En cuanto a los dispositivos conectados, la administración remota de dispositivos es una de las características clave que los operadores de sistema necesitan. Permite a los operadores configurar propiedades y actualizar el software en el dispositivo de forma remota, sin necesidad de tener acceso local o físico al dispositivo. Con Windows IoT Core y Windows IoT Enterprise que se ejecutan en dispositivos como dispositivos domésticos, sistemas HVAC y otros, es necesario disponer de una solución de administración de dispositivos ligera y personalizable. Aunque las versiones de Windows 10 ya ofrecen administración de dispositivos móviles (MDM) basadas en [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management), se usa principalmente en soluciones empresariales con herramientas de administración como SCCM o Intune. Aunque esas soluciones son adecuadas para los dispositivos que se encuentran en una configuración empresarial, tienen desafíos en la configuración más diversa que vemos en las soluciones de IoT. Los dispositivos de IoT también requieren una solución de administración de dispositivos ligera y pequeña, lo que puede ser un reto. Microsoft también ofrece funcionalidades de administración de dispositivos con [Azure IOT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview) y su [SDK](https://docs.microsoft.com/azure/iot-hub/iot-hub-devguide-sdks). El [agente de dispositivos IOT de Azure](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) reúne estas capacidades: capacidades de administración de dispositivos en la nube a través del IOT Hub que funciona con los mismos [proveedores de servicios de configuración (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) estándar que usa la administración de dispositivos móviles. Con el agente de dispositivos de Azure, los OEM pueden compilar dispositivos que ofrecen estas capacidades de administración de dispositivos sin necesidad de escribir ningún código. 

El agente de dispositivos de Azure es un paquete de código abierto listo para compilar que habilita las funcionalidades de administración de dispositivos remotos. Azure Device Agent es compatible con Windows 10 IoT Core y Windows 10 IoT Enterprise y funciona en dispositivos conectados a través de la IoT Hub. Los OEM ahora pueden compilar dispositivos que admitan SCCM, Intune o Azure IoT Hub para la administración de dispositivos y dejar que los clientes seleccionen la solución de administración de dispositivos que mejor se adapten a ellos.   

![Azure IoT Hub la administración de dispositivos](../media/AzureIoTDM/azureDM.png)


## <a name="how-does-it-work"></a>¿Cómo funciona?

El [agente de dispositivos IOT de Azure](https://aka.ms/iot-core-azure-dm-client) consta de dos componentes principales. 

El cliente del servicio Device provisioning (cliente DPS) automatiza el aprovisionamiento de dispositivos. Se conecta al servicio Azure Device provisioning con la clave de inscripción del dispositivo e DPS ScopeID. El servicio DPS de Azure identifica el dispositivo y lo aprovisiona en el IoT Hub configurado y devuelve una cadena de conexión al dispositivo. Después, el cliente de DPS usa esta cadena de conexión para conectar el dispositivo a la derecha IoT Hub.  

El cliente de administración de dispositivos habilita las funcionalidades de administración remota de dispositivos mediante los [proveedores de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP). las capacidades de administración remota del agente de dispositivos de Azure admiten un modelo de complemento que permite seleccionar solo las capacidades que necesita. Además, la arquitectura del complemento es ampliable. Puede escribir su propio complemento para una funcionalidad de administración de dispositivos que necesite y agregarlo al agente de dispositivos de Azure. Todas las funcionalidades de administración de dispositivos se pueden acceder de forma remota mediante los comandos y las propiedades de los módulos gemelas o del módulo, lo que permite un enfoque de administración de un solo panel de cristal para todos los dispositivos de Windows IoT. [Para obtener](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/reference.md) una lista completa de las capacidades de administración de dispositivos disponibles, consulte

Además, el agente de dispositivos de Azure también crea y administra tokens de SAS para otras aplicaciones UWP que se ejecutan en el dispositivo. El agente de dispositivos de Azure puede aprovisionar otras aplicaciones UWP como un dispositivo gemela o como un módulo gemela y agregar sus cadenas de conexión a las ranuras de TPM respectivas. La aplicación UWP aprovecha el [puente UWP](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/uwp-bridge.md) para leer su cadena de conexión de la ranura TPM y puede utilizarla para conectarse al IOT Hub. 

## <a name="how-to-get-started"></a>Cómo empezar

El agente de dispositivos IoT de Azure está disponible en GitHub. El proyecto también incluye ejemplos para empezar a trabajar rápidamente. Para obtener más información, consulte nuestro [repositorio](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/device-agent.md) de github.

## <a name="migrating-from-azure-device-agent-v1-to-v2"></a>Migración desde Azure Device Agent v1 a V2
Si actualmente usa la versión V1 del agente de dispositivos, un cambio significativo entre V1 y V2 es que, en la versión V2, el agente de dispositivos de Azure ya no comparte la conexión con una aplicación de UWP. Con mejoras en el IoT Hub puede tener ahora la aplicación para UWP y el agente de dispositivos de Azure que tienen cadenas de conexión independientes y que todavía están asociadas con el mismo dispositivo en IoT Hub. Consulte [aquí](https://github.com/ms-iot/azure-client-tools/blob/master/docs/device-agent/migration-from-old-client.md) para obtener más detalles.

Para más información sobre Azure Device Agent v1, consulte [aquí](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm).

## <a name="other-useful-tools"></a>Otras herramientas útiles 
### <a name="dm-mock-portal"></a>Portal ficticio de DM
El [portal ficticio de DM](https://github.com/ms-iot/azure-client-tools/blob/master/docs/dm-mock-portal/dm-mock-portal.md) es una aplicación que se puede usar para establecer las propiedades gemelas de un dispositivo o de módulo en un dispositivo individual o en varios dispositivos, mediante las funciones de administración automática de dispositivos del IOT Hub. 

### <a name="tpm-tool---limpetexe"></a>Herramienta TPM: limpet. exe
El servicio Azure Device Provisioning permite a los clientes asociar y configurar automáticamente un dispositivo con un IoT Hub posterior a la producción. En este proceso, el servicio Device provisioning necesitará un identificador de dispositivo único y desafiable para ayudar a configurar el dispositivo de forma segura cuando el dispositivo se ponga en funcionamiento. El servicio Device provisioning usa la clave de aprobación pública (EKeyPub) del TPM para este fin. Para registrar el dispositivo con DPS, el EKeyPub debe recolectarse desde el dispositivo. La hora preferida para este paso es durante la producción (durante las pruebas de final de línea del dispositivo). Sin embargo, el proceso también puede realizarse después de la producción si es necesario.  

Microsoft proporciona la herramienta limpet para simplificar el proceso de registro del servicio Device provisioning. En función de la configuración de fabricación, si hay una conexión en línea disponible, el dispositivo se puede registrar mediante limpet directamente con el servicio Device provisioning o limpet puede recopilar el EKeyPub para un registro posterior sin conexión del dispositivo con el dispositivo. Servicio de aprovisionamiento.

Para más información sobre el proceso de registro del servicio Device provisioning con limpet, consulte este [repositorio](https://github.com/ms-iot/azure-client-tools/blob/master/docs/limpet/limpet.md).

Licencia: limpet tiene licencia bajo la licencia de código abierto MIT. 
