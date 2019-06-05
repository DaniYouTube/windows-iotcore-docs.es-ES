---
title: Creación de dispositivos más seguros con Windows 10 IoT Core
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear dispositivos más seguros al habilitar el arranque seguro, la implementación de TPM y mucho más.
keywords: Windows iot, seguridad, firmware, el arranque seguro, TPM, Bitlocker, cifrado
ms.openlocfilehash: b7340ce168f766eb13e00bfca39619e92a931c30
ms.sourcegitcommit: 2e7e9555fe71ca60b5f41dbf06051a50520a368a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491722"
---
# <a name="building-more-secure-devices-with-windows-10-iot-core"></a>Creación de dispositivos más seguros con Windows 10 IoT Core

## <a name="introduction"></a>Introducción  

Windows 10 IoT Core proporciona empresarial strong, características de seguridad que se pueden aprovechar en clases más pequeñas, con recursos limitados de dispositivos IoT. Para que estas características de seguridad ofrecer beneficios tangibles, la plataforma de hardware también debe proporcionar un medio para fijarlos. Este artículo proporciona orientación de alto nivel para los generadores de dispositivo de OEM y seguridad consciente responsables de decisiones que desean seleccionar hardware adecuado y compilación, configurar y distribuir un dispositivo de IoT más seguro a sus clientes.
![Seguridad de los datos](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-more-secure-iot-device"></a>Creación de un dispositivo de IoT más seguro  
El proceso de creación de dispositivos de IoT más seguros con IoT Core incluye la selección de hardware para admitir las características de seguridad de plataforma, así como la producción de dispositivos de IoT con seguridad habilitada.

![Proceso de compilación del dispositivo](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>Elegir el hardware con seguridad habilitada
Aunque IoT Core tiene capacidades de seguridad integradas en la plataforma para proteger los datos del cliente, se basa en las características de seguridad de hardware para poder utilizar todas estas funcionalidades. De hecho, software no puede protegerse a sí mismo porque se puede manipular la memoria y no hay ningún anclaje de veracidad o identidad de dispositivo inmutable que puede proporcionarse a través de software por sí solo. Hay varias formas de proporcionar seguridad basada en hardware, como tarjetas inteligentes, el módulo de plataforma segura (TPM) o las características de seguridad integradas en el Soc. 

Para obtener más información sobre las plataformas de hardware compatibles, consulte [Qualcomm y paneles personalizados](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards). 

### <a name="trusted-platform-module"></a>Módulo de plataforma segura
IoT Core usa Trusted Platform Module 2.0 (2.0 de TPM) como plataforma de seguridad de hardware. Se recomienda que los OEM usen una plataforma de hardware que proporciona TPM 2.0 para aprovechar completamente las características de seguridad de IoT Core, como BitLocker, el arranque seguro, almacenamiento de credenciales de Azure y otros. Hay dos opciones para dispositivos de producción implementar un TPM: como discreta TPM (dTPM) o como el firmware TPM (fTPM). TPM discretos están disponibles en varios fabricantes, como Infineon, NazionZ y otros. Algunos fabricantes de SoC proporcionan implementaciones fTPM como parte de un paquete de soporte técnico de la placa (BSP). 

Para obtener más información acerca de TPM, consulte [información general de TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm) y [cómo configurar un TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm).

### <a name="storage-options"></a>Opciones de almacenamiento
Paneles de desarrollo, como la Raspberry Pi 3 populares, proporcionan flexibilidad y permiten a los desarrolladores arrancar fácilmente cualquier plataforma mediante una tarjeta SD extraíble. Para la mayoría de los dispositivos de IoT del sector, esta flexibilidad no es deseable y puede quedar un objetivo fácil para los ataques de dispositivos. En su lugar, al diseñar el hardware, considere la posibilidad de usar un almacenamiento eMMC para los dispositivos de IoT más pequeños y de bajo costo. Almacenamiento incrustado facilita mucho más difícil separar el contenido desde el dispositivo y, a su vez, reduce la posibilidad de robo de datos o la introducción de tipos de malware en el dispositivo.

## <a name="create-a-retail-image"></a>Crear una imagen de venta directa 
Cuando [creación de una imagen de venta directa de Windows IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide), asegúrese de que no hay herramientas de desarrollo que permiten remotas acceder y depuración están presentes en los sistemas de producción como estos potencialmente pueden abrir el dispositivo a los ataques. Si usa herramientas de desarrollo como [Windows Device Portal](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay), [servidor FTP](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp), [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh), o [PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell) en sus imágenes durante desarrollo, asegúrese de probar y validar los escenarios en retail IoT Core imágenes que no incluyen estas herramientas.

### <a name="user-accounts"></a>Cuentas de usuario
La mayoría de los usuarios están familiarizados con la noción de toma de *propiedad* de dispositivos como equipos y teléfonos: la idea de personalización de un dispositivo al que se aplica la conversión unboxing y configurar las credenciales para acceder al dispositivo. A diferencia de consumidor de los equipos y teléfonos, dispositivos de IoT no pretenden servir como dispositivos informáticos de uso general. En su lugar, son dispositivos de aplicación normalmente solo para fines fijo. Aunque Windows admite la noción de administradores de dispositivos que puede conectarse de forma remota a los dispositivos durante un ciclo de desarrollo, dicha compatibilidad en dispositivos de IoT del sector puede suponer una amenaza, especialmente cuando se usan contraseñas poco seguras. En general, se recomienda que no hay cuentas predeterminadas o las contraseñas de crearse en los dispositivos de IoT Core.

## <a name="lockdown-a-retail-image"></a>Bloqueo de una imagen de venta directa
En informática de dispositivos, como PC, de propósito general a los usuarios pueden instalar aplicaciones y cambiar la configuración, incluidas características de seguridad, para garantizar que el dispositivo se ajusta mejor a sus necesidades. La mayoría de los dispositivos de IoT son fijos-función-dispositivos que no cambiará su finalidad durante el ciclo de vida del dispositivo. Que reciben las actualizaciones de software o habilitar las actualizaciones funcionales dentro de sus límites operativos, como una interfaz de usuario mejorada o Reglamento de temperatura en un termostato inteligente. Esta información puede ser utilizado totalmente bloquear un dispositivo IoT solo tiene que permitir la ejecución de código conocida y de confianza. Device Guard en Windows 10 IoT Core puede ayudar a proteger los dispositivos de IoT, lo que garantiza que no se puede ejecutar código ejecutable desconocido o que no se confía en los dispositivos bloqueados.

Microsoft ofrece el [paquete de seguridad de llave en mano](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) para facilitar la habilitación de las características de la clave de seguridad de dispositivos de IoT Core. Esto permite a los generadores de dispositivo crear totalmente bloqueado dispositivos IoT. El paquete ayudará con:

* Aprovisionamiento de claves de arranque seguro y habilitar la característica en admiten plataformas de IoT.
* El programa de instalación y configuración de cifrado del dispositivo mediante BitLocker. 
* Iniciando el bloqueo del dispositivo para solo permitir la ejecución de las aplicaciones firmadas y controladores.

Instrucciones paso a paso se describen en el [Device Guard, BitLocker y habilitar el arranque seguro](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker) sección.

## <a name="device-production"></a>Producción de dispositivo
Una vez validada la imagen de bloqueo, se puede usar para la fabricación. Para obtener más información, consulte [IoT Core fabricación](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/).
