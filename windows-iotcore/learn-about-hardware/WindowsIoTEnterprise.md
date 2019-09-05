---
title: Introducción a Windows 10 IoT Enterprise
author: saraclay
ms.author: saclayt
ms.date: 01/18/2017
ms.topic: article
description: Obtenga información acerca de qué es Windows 10 IoT Enterprise y lo que se puede hacer con él.
keywords: Windows 10 IoT Enterprise, Enterprise, binario, Windows
ms.openlocfilehash: 4dd488ece7ae60074de75756272f52f392ebf322
ms.sourcegitcommit: 38de3aad11845248dac393ffc51b18c5596af4c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68155384"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Introducción a Windows 10 IoT Enterprise

## <a name="what-is-windows-10-iot-enterprise"></a>¿Qué es Windows 10 IoT Enterprise?
Windows 10 IoT Enterprise es una versión completa de Windows 10 que ofrece seguridad y capacidad de administración empresarial a las soluciones de IoT. Es un archivo binario equivalente a Windows 10 Enterprise, por lo que si ya sabe cómo funciona Windows 10 Enterprise, muchos de esos conocimientos es transferibles a Windows 10 IoT Enterprise. Sin embargo, cuando se trata de licencias y distribución, la versión de escritorio y la versión de IoT son diferentes. 

## <a name="getting-started"></a>Introducción 
Antes de ponerse en contacto con un distribuidor incrustados/IoT, se recomienda trabajar con uno de [estos dispositivos](https://solutionsdirectory.intel.com/solutions-directory/processors/736/processors/766/processors/782/processors/788/processors/869/processors/879/processors/883/processors/888/processors/1053/processors/1058/processors/1103/processors/1107/processors/1110/processors/1117/processors/1133/processors/1135/processors/1139/processors/1141/processors/1175/processors/1192/processors/1344/processors/1348/processors/1349/processors/1371/processors/1392/processors/1729/processors/2284).  Puede cargar su PC o dispositivo recomendada con un [copia de evaluación](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise) de Windows 10 Enterprise para poder empezar a crear prototipos de inmediato.

Para iniciar su recorrido en fabricación con Windows 10 IoT Enterprise, deberá llegar a un distribuidor de [esta lista](http://wincom.blob.core.windows.net/documents/Windows_IoT_Distributor_Information.pdf). 

## <a name="fixed-purpose-devices"></a>Dispositivos de propósito fijo 

> [!TIP]
> En el contrato de licencia encontrará una guía completa para todos los escenarios de uso de Windows 10 IoT Enterprise.

La edición Windows 10 IoT Enterprise tiene licencia para permitirle crear dispositivos de propósito fijo, como clientes ligeros, cajeros automáticos, terminales de puntos de venta, sistemas de automatización Industrial, etcetera.  Hay asignaciones específicas y las restricciones en el contrato de licencia. 

En general un dispositivo de propósito fijo difiere de un dispositivo de propósito general de las maneras siguientes:  
* El dispositivo se bloquea en una aplicación individual o un conjunto fijo de aplicaciones a través de las características Acceso asignado o Iniciador de shell.  
* El dispositivo competencias en inmediatamente a la experiencia cuando recibe el cliente final. Para ello se configura la imagen del dispositivo para que omita la configuración rápida normal de Windows.
* Los teclados, los puertos USB y las directivas del dispositivos se bloquean para restringir el dispositivo para que se use solo en su propósito fijo.  
* El fabricante de equipos originales concede la licencia del dispositivo al usuario con el software adjunto al dispositivo como un producto completo y se usan los términos específicos de Windows en sus propios contratos.

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Diferencias entre Windows 10 IoT Core y Windows 10 IoT Enterprise
Aunque Windows 10 IoT Core y Windows 10 IoT Enterprise son similares en el nombre, hay diferencias en lo que ofrecen y también en lo que admiten. A continuación se muestra una lista de características en la que se resaltan las diferencias de cada edición.

Para obtener detalles sobre los requisitos mínimos, visite [el sitio de hardware de Windows](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

> |             | Windows 10 IoT Core  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | Experiencia del usuario | Solo aplicación UWP que se ejecuta en el inicio con compatibilidad con servicios y aplicaciones en segundo plano. | Shell de Windows tradicional con características avanzadas de bloqueo |
> | Compatibilidad con equipos sin periféricos | Sí | Sí |
> | Arquitectura de aplicaciones compatible | UWP solo | UWP y Win32 |
> | Cortana | *SDK de Cortana* | Sí |
> | Unión a un dominio | Solo AAD | AAD y dominio tradicional |
> | Administración | MDM | MDM |
> | Tecnologías de seguridad del dispositivo | Arranque seguro, TPM, BitLocker, atestación de estado del dispositivo y Device Guard para IoT | Arranque seguro, TPM, BitLocker, Device Guard, Defender ATP y atestación de estado de dispositivo |
> | Compatibilidad con arquitecturas de CPU | x86, x64 ARM32 y ARM64 | x86 x64 y ARM64 |
> | Concesión de licencias | Contrato de licencia en línea y contratos de OEM insertados, libres de regalías | Contratos de OEM insertados directos e indirectos |
> | Escenarios de uso | Señalización digital, edificio inteligente, puerta de enlace de IoT, HMI, Home, Smart ponibles | Tabletas del sector, PDV, pantalla completa, señalización Digital, ATM, dispositivos médicos, dispositivos, de fabricación de cliente ligero |

## <a name="helpful-resources"></a>Recursos útiles
> [!NOTE]
> Recursos adicionales pueden estar disponibles desde el distribuidor para explicar la activación de OEM de Windows EPKEA y proporcionan orientación acerca de la generación de la empresa de fabricación listos para Windows IoT [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) imagen del dispositivo.

* [Fabricación de escritorio](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
* [Filtro de escritura unificado para Windows 10](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Acceso asignado para Enterprise & Pro](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Selector de shell para las ediciones Enterprise y Education](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [Recursos de bloqueo](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Habilitación del modo insertado y uso de tareas en segundo plano en Windows IoT Enterprise](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [Configuración de la telemetría de Windows en una organización](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Configuración de dispositivos compartidos y de quioscos que ejecutan ediciones de escritorio de Windows](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
