---
title: Administración de dispositivos IoT de Azure
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos mediante la administración de dispositivos IoT de Azure y Windows IoT.
keywords: Windows IOT, Azure IoT, administración de dispositivos de Azure, administración de dispositivos
ms.openlocfilehash: 6ab98a1b684c21042395dbd3af0c5cd3d2fa215c
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917384"
---
# <a name="azure-iot-device-management"></a>Administración de dispositivos IoT de Azure   

En cuanto a los dispositivos conectados, la administración remota de dispositivos es una de las características clave que usan los operadores del sistema. Permite a los operadores volver a configurar y actualizar el software y los parámetros del dispositivo de forma remota sin necesidad de tener acceso local y físico al dispositivo. Con Windows 10 IoT Core, los OEM pueden compilar dispositivos que ofrecen estas funcionalidades de una versión a la. Windows 10 IoT Core, así como otras versiones de Windows 10, ya ofrecen administración de dispositivos móviles (MDM) basada en [OMA DM](https://en.wikipedia.org/wiki/OMA_Device_Management). Esto se utiliza principalmente en soluciones empresariales con herramientas de administración como SCCM o Intune. Aunque esas soluciones son adecuadas para los dispositivos que se encuentran en una configuración empresarial, tienen desafíos en la configuración más diversa que vemos en las soluciones de IoT. Estos desafíos también se ven en los dispositivos de IoT que requieren la administración de dispositivos ligeros. Para esos dispositivos, Microsoft ofrece [Administración de dispositivos a través de Azure IOT Hub](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview).    

## <a name="scalable-device-management-with-windows-iot"></a>Administración de dispositivos escalable con Windows IoT  

Con Windows IoT Core ejecutándose en dispositivos como dispositivos domésticos, sistemas HVAC y otros, es necesario disponer de una solución de administración de dispositivos ligera y personalizable. En Windows Creator Edition, Microsoft habilita [Azure IOT Hub la administración de dispositivos](https://docs.microsoft.com/azure/iot-hub/iot-hub-device-management-overview). Los OEM pueden usar la [biblioteca de cliente de Azure DM para Windows IOT](https://aka.ms/iot-core-azure-dm-client) para agregar funcionalidades de administración de dispositivos a sus dispositivos conectados a Azure IOT Hub. Esta biblioteca tendrá acceso a los componentes estándar de administración de dispositivos Windows ([proveedores de servicios de configuración](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference), CSP).  Ahora, los OEM pueden compilar dispositivos que admiten SCCM, Intune y Azure IoT Hub para la administración de dispositivos y dejar que los clientes seleccionen la solución de tipo DM que mejor se adapta a ellos.   

![Azure IoT Hub la administración de dispositivos](../media/AzureIoTDM/azureDM.png) 

## <a name="how-does-it-work"></a>¿Cómo funciona?    

La [biblioteca de cliente de Azure DM para Windows IOT](https://aka.ms/iot-core-azure-dm-client) está vinculada en la aplicación host. Comparte la conexión de Azure IoT Hub con la aplicación host. Por lo tanto, es necesario efectuar una inscripción adicional para habilitar la administración de dispositivos. En la imagen siguiente se muestra la arquitectura de una solución Azure IoT Hub DM mediante la biblioteca de cliente de Azure DM para Windows IoT.     

![Gráfico de flujo de Azure DM](../media/AzureIoTDM/AzureDM-Architecture.png)    

Microsoft proporciona dos componentes del sistema, CommProxy. exe y SystemConfigurator. exe, que el OEM debe incluir en la imagen del dispositivo. Estos componentes proporcionan acceso a los CSP. IoTDMClientLib asigna la interfaz de CSP a las funciones que puede usar Azure IoT Hub la administración de dispositivos. También proporciona funciones DM que no usan un CSP, por ejemplo, establecer la zona horaria. IoTDMClientLib se proporciona como componente de código abierto. Los fabricantes OEM pueden extenderlo para agregar capacidades de DM que son específicas de su dispositivo, como las configuraciones de sensores o accionadores.  

## <a name="device-health-attestation"></a>Certificación de estado del dispositivo    
Para una operación segura de dispositivos IoT, es esencial evaluar si un dispositivo se inicia en un estado de confianza y compatible. Con los operadores de [Windows IoT atestación de estado de dispositivo (DHA)](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md) , puede comprobar el estado de seguridad de un dispositivo y tomar las medidas correctivas adecuadas si es necesario a través de [Azure IOT Hub la administración de dispositivos](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/README.md). DHA forma parte del cliente de administración de dispositivos de Azure de Windows IoT Core. Para usar la funcionalidad DHA en la solución, es necesario tener acceso al servicio Microsoft DHA. Una suscripción al servicio está disponible a través de la [Windows 10 IOT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview). 

### <a name="reference"></a>Referencia   
[Atestación de estado de dispositivo para Azure IoT DM](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/device-health-attestation.md)  

[Implementación de recursos de Azure para Atestación de estado de dispositivo](https://github.com/ms-iot/iot-core-azure-dm-client/blob/master/docs/dha-deploy.md#deploy-azure-resources-for-device-health-attestation)  


## <a name="how-to-get-started"></a>¿Cómo empezar?  

La biblioteca de cliente de Azure DM para Windows IoT está disponible en GitHub. Junto al proyecto IoTDMClientLib también se incluyen ejemplos para empezar a trabajar rápidamente. Para obtener más información, vea los vínculos siguientes.    

### <a name="project-github-page"></a>Página de GitHub del proyecto 

La [biblioteca de cliente de Azure DM para Windows IOT](https://aka.ms/iot-core-azure-dm-client) está disponible en github.  

### <a name="dm-dashboard"></a>Panel de DM    

El [Panel de DM](https://aka.ms/iot-core-azure-dm-client-dashboard) es una aplicación para probar la función DM en un dispositivo. La aplicación se conecta al dispositivo a través de Azure IoT Hub. La aplicación se puede usar para validar las capacidades de DM del dispositivo. Se puede extender para probar las funciones DM de terceros que se agregaron a IoTDMClientLib.    

### <a name="dm-background-application"></a>Aplicación en segundo plano de DM   

La [aplicación DM Background](https://aka.ms/iot-core-azure-dm-client-backgroundapp) muestra cómo se puede usar IoTDMClientLib en una aplicación que se conecta a Azure IOT Hub y debe ejecutarse como aplicación en segundo plano en Windows IOT Core.    

### <a name="toaster-application"></a>Aplicación del tostador 

La [aplicación tostadora](https://aka.ms/iot-core-azure-dm-client-toasterapp), como aplicación en segundo plano de administración de dispositivos, habilitará las capacidades de Azure DM para un dispositivo. Esta aplicación se ejecutará en primer plano y permitirá el acceso a los parámetros y funciones de DM a través de la interfaz de usuario de los dispositivos.   

### <a name="registering-your-device-with-the-azure-device-provision-service-dps"></a>Registro del dispositivo con el servicio de aprovisionamiento de dispositivos de Azure (DPS)   

El servicio Azure Device Provisioning permite a los clientes asociar y configurar automáticamente un dispositivo con un IoT Hub posterior a la producción. En este proceso, el servicio de aprovisionamiento de dispositivos necesitará un identificador de dispositivo único y desafiable para ayudar a configurar el dispositivo de forma segura cuando el dispositivo se ponga en funcionamiento. El servicio Device provisioning usa la clave de aprobación pública (EKeyPub) del TPM para este fin. Para registrar el dispositivo con DPS, el EKeyPub debe recolectarse desde el dispositivo. La hora preferida para este paso es durante la producción (durante las pruebas de final de línea del dispositivo). Sin embargo, el proceso también puede realizarse después de la producción si es necesario.   

Microsoft proporciona la herramienta limpet para simplificar el proceso de registro del servicio Device provisioning. En función de la configuración de fabricación, si hay una conexión en línea disponible, el dispositivo se puede registrar mediante limpet directamente con el servicio Device provisioning o limpet puede recopilar el EKeyPub para un registro posterior sin conexión del dispositivo con el dispositivo. Servicio de aprovisionamiento.  

Para más información sobre el proceso de registro del servicio Device provisioning con limpet, consulte la sección [inscripción del dispositivo en el servicio Device provisioning](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md#setup-azure-cloud-resources) en la [documentación de limpet](https://github.com/ms-iot/azure-dm-client/blob/master/docs/limpet.md).    

Repositorio del proyecto: [repositorio del proyecto de limpet](https://github.com/ms-iot/azure-dm-client/)     


Licencia: limpet tiene licencia en virtud de la licencia de código abierto MIT   

