---
title: Creación de dispositivos más seguros con Windows 10 IoT Core
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a crear dispositivos más seguros habilitando el arranque seguro, implementando TPM, etc.
keywords: Windows IOT, seguridad, firmware, arranque seguro, TPM, BitLocker, cifrado
ms.openlocfilehash: b7340ce168f766eb13e00bfca39619e92a931c30
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491722"
---
# <a name="building-more-secure-devices-with-windows-10-iot-core"></a>Creación de dispositivos más seguros con Windows 10 IoT Core

## <a name="introduction"></a>Introducción  

Windows 10 IoT Core ofrece sólidas características de seguridad de nivel empresarial que se pueden aprovechar en clases de dispositivos IoT más pequeñas y con restricciones de recursos. Para que estas características de seguridad ofrezcan ventajas tangibles, la plataforma de hardware también debe proporcionar un medio para delimitarlas. En este artículo se proporciona una guía de alto nivel para los generadores de dispositivos OEM y los creadores conscientes de la seguridad que desean seleccionar el hardware adecuado y compilar, configurar y enviar un dispositivo de IoT más seguro a sus clientes.
![Seguridad de datos](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-more-secure-iot-device"></a>Creación de un dispositivo IoT más seguro  
El proceso de creación de dispositivos IoT más seguros con IoT Core incluye la selección de hardware para admitir las características de seguridad de la plataforma, así como la producción de dispositivos IoT con seguridad habilitada.

![Proceso de compilación de dispositivos](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>Elección del hardware con seguridad habilitada
Aunque IoT Core tiene capacidades de seguridad integradas en la plataforma para proteger los datos de los clientes, se basa en las características de seguridad de hardware para utilizar estas funcionalidades por completo. De hecho, el software no puede protegerse a sí mismo porque se puede manipular la memoria y no hay ningún anclaje de veracidad o identidad de dispositivo inmutable que se pueda proporcionar mediante software por sí solo. Hay varias maneras de proporcionar seguridad basada en hardware, como tarjetas inteligentes, módulo de plataforma segura (TPM) o características de seguridad integradas en el SoC. 

Para obtener más información sobre las plataformas de hardware admitidas, consulte [SOC y paneles personalizados](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards). 

### <a name="trusted-platform-module"></a>Módulo de plataforma segura
IoT Core usa Módulo de plataforma segura 2,0 (TPM 2,0) como plataforma de seguridad de hardware. Se recomienda que los OEM usen una plataforma de hardware que proporcione TPM 2,0 para sacar el máximo partido de las características de seguridad de IoT Core, como BitLocker, el arranque seguro, el almacenamiento de credenciales de Azure y otros. Hay dos opciones para que los dispositivos de producción implementen un TPM: como TPM discreto (dTPM) o como firmware TPM (fTPM). Los TPM discretos están disponibles en varios fabricantes, como Infineon, NazionZ y otros. Algunos fabricantes de SoC proporcionan implementaciones de fTPM como parte de un paquete de soporte técnico de la placa (BSP). 

Para obtener más información acerca de los TPM, consulte [información general del TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm) y [Cómo configurar un TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm).

### <a name="storage-options"></a>Opciones de almacenamiento
Los paneles de desarrollo, como el popular Raspberry PI 3, ofrecen flexibilidad y permiten a los desarrolladores arrancar fácilmente cualquier plataforma a través de una tarjeta SD extraíble. Para la mayoría de los dispositivos IoT del sector, esta flexibilidad no es deseable y puede hacer que los dispositivos sean un destino sencillo para los ataques. En su lugar, al diseñar el hardware, considere la posibilidad de usar un almacenamiento de eMMC para dispositivos IoT más pequeños y de bajo costo. El almacenamiento incrustado hace que sea mucho más difícil separar el contenido del dispositivo y, a su vez, reduce el potencial de robo de datos o la introducción de malware en el dispositivo.

## <a name="create-a-retail-image"></a>Creación de una imagen comercial 
Al [crear una imagen comercial de Windows IOT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide), asegúrese de que no haya ninguna herramienta de desarrollador que permita el acceso remoto y la depuración en sistemas de producción, ya que estos podrían abrir el dispositivo a ataques. Si usa herramientas de desarrollo como el [portal de dispositivos de Windows](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay), el [servidor FTP](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp), [ssh](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh)o [PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell) en sus imágenes durante el desarrollo, asegúrese de probar y validar los escenarios en las imágenes de IOT Core comerciales que no incluyen Estas herramientas.

### <a name="user-accounts"></a>Cuentas de usuario
La mayoría de los usuarios están familiarizados con la noción de tomar *posesión* de dispositivos como PC y teléfonos: la idea de personalizar un dispositivo cuando se le aplica la conversión unboxing y de configurar las credenciales para acceder al dispositivo. A diferencia de los equipos de consumidor y los teléfonos, los dispositivos de IoT no están diseñados para servir como dispositivos informáticos de uso general. En su lugar, suelen ser dispositivos de una sola aplicación y de propósito fijo. Aunque Windows admite la noción de administradores de dispositivos que se pueden conectar de forma remota a los dispositivos durante un ciclo de desarrollo, la compatibilidad con los dispositivos IoT del sector puede suponer una amenaza, especialmente cuando se usan contraseñas débiles. En general, se recomienda que no se creen cuentas ni contraseñas predeterminadas en los dispositivos IoT Core.

## <a name="lockdown-a-retail-image"></a>Bloqueo de una imagen comercial
En los dispositivos informáticos de uso general, como los equipos, los usuarios pueden instalar aplicaciones y cambiar la configuración, incluidas las características de seguridad, para asegurarse de que el dispositivo se adapta mejor a sus necesidades. La mayoría de los dispositivos IoT son dispositivos de funciones fijas que no cambiarán su finalidad a lo largo de la duración del dispositivo. Reciben actualizaciones de software o habilitan las actualizaciones funcionales dentro de sus límites operativos, como una mejora de la interfaz de usuario o el Reglamento de temperatura en un termostato inteligente. Esta información se puede usar para el bloqueo completo de un dispositivo IoT, ya que solo se permite la ejecución de código conocido y de confianza. Device Guard en Windows 10 IoT Core puede ayudar a proteger los dispositivos IoT asegurándose de que no se pueda ejecutar código ejecutable desconocido o que no sea de confianza en dispositivos bloqueados.

Microsoft proporciona el [paquete de seguridad Llave](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) en mano para facilitar la habilitación de las características de seguridad clave en los dispositivos IOT Core. Esto permite que los creadores de dispositivos creen dispositivos IoT completamente bloqueados. El paquete le ayudará con:

* Aprovisionamiento de claves de arranque seguras y habilitación de la característica en plataformas de IoT compatibles.
* Instalación y configuración del cifrado de dispositivos con BitLocker. 
* Iniciar el bloqueo de dispositivo para permitir solo la ejecución de aplicaciones y controladores firmados.

La guía paso a paso se describe en la sección [habilitación del arranque seguro, BitLocker y Device Guard](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker) .

## <a name="device-production"></a>Producción de dispositivos
Una vez validada la imagen de bloqueo, se puede usar para la fabricación. Para obtener más información, consulte [IOT Core Manufacturing](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/).
