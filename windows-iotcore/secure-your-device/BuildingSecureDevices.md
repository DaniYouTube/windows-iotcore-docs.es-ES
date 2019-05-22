---
title: Creación de dispositivos segura con Windows 10 IoT Core
author: TorstenStein
ms.author: torstens
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear dispositivos seguros al habilitar el arranque seguro, la implementación de TPM y mucho más.
keywords: Windows iot, seguridad, firmware, el arranque seguro, TPM, Bitlocker, cifrado
ms.openlocfilehash: 611d82af25d9c4959335aa208e0d06b49daa5f9f
ms.sourcegitcommit: c4232e384e7347f97477e5cd3cc941de492f6a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986489"
---
# <a name="building-secure-devices-with-windows-10-iot-core"></a>Creación de dispositivos segura con Windows 10 IoT Core

## <a name="introduction"></a>Introducción  

Con Windows 10 IoT Core, Microsoft ofrece enterprise seguro las características de seguridad de nivel que se pueden aprovechar en las clases de restricción de recursos más pequeñas, de dispositivos IoT. Para que estas características de seguridad ofrecer beneficios tangibles, la plataforma de hardware también debe proporcionar un medio para fijarlos. Este documento proporciona orientación a los generadores de dispositivo de OEM y la seguridad de alto nivel conscientes 'creadores' que desean seleccionar el hardware apropiado y generar, configurar y enviar un dispositivo de IoT seguro a sus clientes.
![Seguridad de los datos](../media/SecurityFlowAndCertificates/DataRestExecutionMotion.png)

## <a name="building-a-secure-iot-devices"></a>Creación de un dispositivo de IoT segura  
En esta sección le ayudará a los OEM y a los desarrolladores a través del proceso de creación de proteger los dispositivos de IoT con Windows IoT Core. Nos referiremos a la selección de hardware para admitir las características de seguridad de plataforma, así como la producción de dispositivos de IoT con seguridad habilitada.

![Proceso de compilación del dispositivo](../media/SecurityFlowAndCertificates/DeviceBuildProcess.png)


## <a name="choosing-security-enabled-hardware"></a>Elegir el hardware de seguridad habilitada
Aunque Windows IoT Core tiene capacidades de seguridad de compilación la plataforma para proteger los datos del cliente, se basa en las características de seguridad de hardware para poder utilizar todas estas funcionalidades. De hecho, software no puede protegerse a sí mismo como se puede manipular la memoria y no hay ningún anclaje de veracidad o identidad de dispositivo inmutable que puede proporcionarse a través de software por sí solo. Hay varias formas de proporcionar seguridad basada en hardware, por ejemplo, tarjetas inteligentes, de confianza (TPM) de módulos de plataforma o características de seguridad de compilación en el Soc. 

Para obtener más información acerca del hardware compatible con plataformas consulte sección [Qualcomm y paneles personalizados](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards) 

### <a name="trusted-platform-module"></a>Módulo de plataforma segura
Windows IoT Core usa TPM 2.0 como plataforma de seguridad de hardware. Los OEM se recomiendan que use una plataforma de hardware que proporciona TPM 2.0 para sacar el máximo provecho de las características de seguridad de Windows IoT Core, como BitLocker, el arranque seguro, almacenamiento de credenciales de Azure y otros. Hay dos opciones para dispositivos de producción implementa un TPM, como discreta TPM (dTPM) o como el firmware TPM (fTPM). TPM discretos están disponibles en varios fabricantes como Infineon, NazionZ y otros. Algunos fabricantes SoC proporcionan implementaciones fTPM como parte de la BSP. 

Para obtener más información acerca de TPM, consulte [información general de TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/tpm) y [cómo configurar un TPM](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/setuptpm).

### <a name="storage-options"></a>Opciones de almacenamiento
Paneles de desarrollo, como la Raspberry Pi 3 populares, proporcionan flexibilidad y permiten a los desarrolladores arrancar fácilmente cualquier plataforma mediante una tarjeta SD extraíble. La mayoría de los dispositivos de IoT del sector, dicha flexibilidad no es deseable y puede realizar un objetivo fácil para los ataques de dichos dispositivos. En su lugar, al diseñar el hardware, considere el uso de un almacenamiento eMMC para los dispositivos de IoT más pequeños y de bajo costos. Almacenamiento incrustado facilita mucho más difícil separar el contenido desde el dispositivo y a su vez, reduce el riesgo de introducir código malintencionado en el robo de datos o el dispositivo.

## <a name="creating-a-retail-image"></a>Creación de una imagen de venta directa 
Cuando [creación de una imagen de venta directa de Windows IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide), asegúrese de que no hay herramientas de desarrollo que permiten remotas acceder y depuración están presentes en los sistemas de producción como estos potencialmente pueden abrir el dispositivo a los ataques. Asegúrese de que, si usa herramientas de desarrollo como [Windows Device Portal](https://docs.microsoft.com/en-us/windows/iot-core/manage-your-device/remotedisplay), [servidor FTP](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ftp), [SSH](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/ssh), o [PowerShell](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/powershell) en sus imágenes durante el desarrollo, probar y validar los escenarios de imágenes de IoT Core comerciales que no incluyen estas herramientas.

### <a name="user-accounts"></a>Cuentas de usuario
La mayoría de los usuarios están familiarizados con la noción de toma de "propiedad" de dispositivos como equipos y teléfonos - la idea de personalizar el dispositivo cuando la conversión unboxing y configurar las credenciales para acceder al dispositivo. A diferencia de consumidor de los equipos y teléfonos, dispositivos de IoT no pretenden servir como dispositivos informáticos de uso general. En su lugar, son dispositivos de aplicación normalmente solo para fines fijo. Aunque Windows admite la noción de administradores de dispositivos que puede conectarse de forma remota a los dispositivos durante un ciclo de desarrollo, dicha compatibilidad en dispositivos de IoT del sector puede suponer una amenaza, especialmente cuando se usan contraseñas poco seguras. En general, Microsoft recomienda que no se deben crear ninguna cuenta de "default" o las contraseñas en los dispositivos Windows 10 IoT Core.

## <a name="lockdown-a-retail-image"></a>Bloqueo de una imagen de venta directa
En informática de dispositivos, como PC, de propósito general, los usuarios pueden instalar aplicaciones, cambiar la configuración, incluida para que características de seguridad, para definir la función del dispositivo suite mejor sus necesidades operativas. La mayoría de los dispositivos de IoT son fijos-función-dispositivos que no cambiará el propósito durante el ciclo de vida del dispositivo. Estos dispositivos todavía recibirán actualizaciones de software o habilitar las actualizaciones funcionales dentro de sus límites operativos, por ejemplo, ha mejorado el Reglamento de temperatura o de interfaz de usuario en un termostato inteligente. Esta información puede ser utilizado totalmente bloquear un dispositivo IoT solo tiene que permitir la ejecución de código conocida y de confianza. Device Guard en Windows 10 IoT Core puede ayudar a proteger los dispositivos de IoT, lo que garantiza que no se puede ejecutar código ejecutable desconocido o que no se confía en los dispositivos bloqueados.

Microsoft ofrece el [paquete de seguridad de llave en mano](https://github.com/ms-iot/security/tree/master/TurnkeySecurity) para facilitar la fácil habilitación de características clave de seguridad en dispositivos de IoT Core, que permite a los generadores de dispositivo crear completamente bloqueado de los dispositivos de IoT. El paquete ayudará con:

* Aprovisionamiento de claves de arranque seguro y habilitar la característica en las plataformas admitidas de IoT
* Instalación y configuración de cifrado del dispositivo con BitLocker 
* Iniciando el bloqueo del dispositivo para solo permitir la ejecución de las aplicaciones firmadas y controladores

Una guía paso a paso se describe en el [Device Guard, BitLocker y habilitar el arranque seguro](https://docs.microsoft.com/en-us/windows/iot-core/secure-your-device/securebootandbitlocker) sección.

## <a name="device-production"></a>Producción de dispositivo
Una vez validada la imagen de bloqueo se puede usar para la fabricación. Para obtener más información, consulte [IoT Core fabricación](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/).
