---
title: Información general de Windows 10 IoT Enterprise
author: saraclay
ms.author: saclayt
ms.date: 01/18/2017
ms.topic: article
description: Obtenga información sobre las novedades de Windows 10 IoT Enterprise y lo que puede hacer con él.
keywords: Binario de Windows 10 IoT Enterprise, Enterprise, Windows
ms.openlocfilehash: 1f13c4df2c40dcc4449f2e6cdd16005b1bc0069f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514687"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Información general de Windows 10 IoT Enterprise

## <a name="what-is-windows-10-iot-enterprise"></a>¿Qué es Windows 10 IoT Enterprise?
Windows 10 IoT Enterprise es una versión completa de Windows 10 que ofrece seguridad y capacidad de administración empresarial para las soluciones de IoT. Es un archivo binario equivalente a Windows 10 Enterprise, por lo que si ya sabe cómo funciona Windows 10 Enterprise, muchos de esos conocimientos es transferibles a Windows 10 IoT Enterprise. Sin embargo, cuando se trata de licencias y distribución, la versión de escritorio y la versión de IoT son diferentes. 

## <a name="getting-started"></a>Introducción 
Antes de ponerse en contacto con un distribuidor incrustados/IoT, se recomienda trabajar con uno de [estos dispositivos](https://solutionsdirectory.intel.com/solutions-directory/processors/736/processors/766/processors/782/processors/788/processors/869/processors/879/processors/883/processors/888/processors/1053/processors/1058/processors/1103/processors/1107/processors/1110/processors/1117/processors/1133/processors/1135/processors/1139/processors/1141/processors/1175/processors/1192/processors/1344/processors/1348/processors/1349/processors/1371/processors/1392/processors/1729/processors/2284).  Puede cargar su PC o dispositivo recomendada con un [copia de evaluación](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise) de Windows 10 Enterprise para poder empezar a crear prototipos de inmediato.

Para iniciar su recorrido en fabricación con Windows 10 IoT Enterprise, deberá llegar a un distribuidor de [esta lista](http://wincom.blob.core.windows.net/documents/Windows_IoT_Distributor_Information.pdf). 

## <a name="fixed-purpose-devices"></a>Dispositivos de propósito fijo 

> [!TIP]
> Consulte el contrato de licencia para una guía completa sobre todos los escenarios de uso de Windows 10 IoT Enterprise.

La edición Windows 10 IoT Enterprise tiene licencia para permitirle crear dispositivos de propósito fijo, como clientes ligeros, cajeros automáticos, terminales de puntos de venta, sistemas de automatización Industrial, etcetera.  Hay asignaciones específicas y las restricciones en el contrato de licencia. 

En general un dispositivo de propósito fijo difiere de un dispositivo de propósito general de las maneras siguientes:  
* El dispositivo está bloqueado hasta una sola aplicación o un conjunto fijo de aplicaciones a través de las características de acceso asignado o selector de Shell.  
* El dispositivo competencias en inmediatamente a la experiencia cuando recibe el cliente final. Esto se logra mediante la configuración de la imagen del dispositivo para omitir las experiencias de out-of-box normales de Windows.
* Teclados, puertos USB y las directivas de dispositivos están bloqueadas para restringir el dispositivo que se usará solo en su propósito fijo.  
* El OEM licencias el dispositivo del usuario con el software conectado al dispositivo como un producto completo y pasa a través de términos específicos de Windows en sus propios contratos.

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Diferencias entre Windows 10 IoT Enterprise y Windows 10 IoT Core
Aunque Windows 10 IoT Core y Windows 10 IoT Enterprise son similares en nombre, hay diferencias en lo que ofrecen, así como lo admiten. A continuación es una lista de características que se resalta las diferencias de edición.

Para obtener detalles de requisitos mínimos, visite [el sitio de Windows Hardware](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

> |             | Windows 10 IoT Core  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | Experiencia del usuario | Solo aplicación UWP que se ejecuta en el inicio con compatibilidad con servicios y aplicaciones en segundo plano. | Shell de Windows tradicional con características avanzadas de bloqueo |
> | Sin periféricos compatibles | Sí | Sí |
> | Arquitectura de aplicaciones compatibles | UWP solo | UWP y Win32 |
> | Cortana | *SDK de Cortana* | Sí |
> | Unión a un dominio | Sólo AAD | AAD y dominio tradicionales |
> | Management | MDM | MDM |
> | Tecnologías de seguridad del dispositivo | Arranque seguro, TPM, BitLocker, atestación de estado del dispositivo y Device Guard para IoT | Arranque seguro, TPM, BitLocker, Device Guard, Defender ATP y atestación de estado de dispositivo |
> | Compatibilidad con la arquitectura de CPU | x86 x64 y ARM | x86 x64 y ARM64 |
> | Concesión de licencias | En línea licencias de contrato y acuerdos de OEM incrustado, libre de regalías | Contratos directos e indirectos OEM incrustado |
> | Escenarios de uso | Señalización digital, edificio inteligente, puerta de enlace de IoT, HMI, Home, Smart ponibles | Tabletas del sector, PDV, pantalla completa, señalización Digital, ATM, dispositivos médicos, dispositivos, de fabricación de cliente ligero |

## <a name="helpful-resources"></a>Recursos útiles
> [!NOTE]
> Recursos adicionales pueden estar disponibles desde el distribuidor para explicar la activación de OEM de Windows EPKEA y proporcionan orientación acerca de la generación de la empresa de fabricación listos para Windows IoT [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) imagen del dispositivo.

* [Fabricación de escritorio](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
* [Filtro de escritura unificado para Windows 10](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Acceso asignado para Enterprise & Pro](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Selector de shell para las ediciones Enterprise y Education](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [Recursos de bloqueo](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Habilitar el modo incrustado y el uso de tareas en segundo plano en Windows IoT Enterprise](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [Configurar la telemetría de Windows en la organización](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Configurar dispositivos compartidos y de quiosco multimedia que ejecutan ediciones de escritorio de Windows](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
