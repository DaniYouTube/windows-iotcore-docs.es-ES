---
title: Información general de Windows 10 IoT Enterprise
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Obtenga información sobre las novedades de Windows 10 IoT Enterprise y lo que puede hacer con él.
keywords: Binario de Windows 10 IoT Enterprise, Enterprise, Windows
ms.openlocfilehash: abf6fa3478991a188b8980ceaf838648f6a89feb
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694123"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Información general de Windows 10 IoT Enterprise

> [!NOTE]
> Contenedores de Windows 10 solo pueden usarse con Windows IoT Core y Windows IoT Enterprise para las implementaciones comerciales de uso de Microsoft Azure IoT Edge.

## <a name="what-is-windows-10-iot-enterprise"></a>¿Qué es Windows 10 IoT Enterprise?
Windows 10 IoT Enterprise es una versión completa de Windows 10 que ofrece seguridad y capacidad de administración empresarial para las soluciones de IoT. Windows 10 IoT Enterprise comparte todos los beneficios del ecosistema de Windows en todo el mundo. Es un archivo binario equivalente a Windows 10 Enterprise, por lo que puede usar el mismo desarrollo conocido y las herramientas de administración como los equipos cliente y equipos portátiles.  Sin embargo, cuando se trata de licencias y distribución, la versión de escritorio y versiones de IoT son diferentes. Tenga en cuenta que Windows 10 IoT Enterprise ofrece opciones de canal de mantenimiento a largo plazo (LTSC) y canal semianual (SAC). Los OEM pueden elegir la versión que se necesitan para sus dispositivos.

## <a name="getting-started"></a>Introducción 

Para iniciar su recorrido en fabricación con Windows 10 IoT Enterprise, es necesario llegar a un distribuidor de [esta lista](https://go.microsoft.com/fwlink/p/?linkid=2093270).

Desde allí, puede aprender fabricar con Windows 10 IoT Enterprise con nuestro [la Guía de fabricación de Windows 10 IoT Enterprise](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview). 

## <a name="fixed-purpose-devices"></a>Dispositivos de propósito fijo 

> [!TIP]
> Consulte el contrato de licencia para una guía completa sobre todos los escenarios de uso de Windows 10 IoT Enterprise. Si no tiene este contrato de licencia, consulte a lo OEM que trabaja para el acuerdo comercial. 

Windows es conocido como los sistemas operativos en equipos portátiles y escritorios usados por los consumidores y empresas en todo el mundo.  ¿Qué es menos conocida es que durante años, Windows han también usa muchas cajeros automáticos, terminales de punto de venta, los sistemas de automatización industrial, clientes ligeros, dispositivos médicos, señalización digital, quioscos y otros dispositivos de propósito fijo.  Windows 10 IoT Enterprise le permite crear dispositivos de propósito fijo con asignaciones específicas y las restricciones en el contrato de licencia.  

Un dispositivo de propósito fijo difiere de un dispositivo de propósito general de las maneras siguientes:  
* El dispositivo está bloqueado hasta una sola aplicación o un conjunto fijo de aplicaciones a través de las características de acceso asignado o selector de Shell.  
* La experiencia de dispositivos es inmediata cuando competencias en el cliente. Esto se logra mediante la configuración de la imagen del dispositivo para omitir las experiencias de out-of-box normales de Windows. 
* Teclados, puertos USB y las directivas de dispositivos están bloqueadas para restringir el dispositivo que se usará solo en su propósito fijo.  
* El OEM licencias el dispositivo del usuario con el software conectado al dispositivo como un producto completo y pasa a través de términos específicos de Windows en sus propios contratos.
* El OEM proporciona el soporte al cliente para su producto completo, incluidas las funciones realizadas por el sistema operativo.

## <a name="long-term-servicing-channel-ltsc"></a>Canal de mantenimiento a largo plazo (LTSC)

A menudo, los sistemas especializados, como los PC que controlan equipos médicos, sistemas de punto de venta y cajeros automáticos, requieren una opción de mantenimiento ya debido a su propósito. Por lo general, estos dispositivos realizan una única tarea importante y no necesitan actualizaciones de características tan frecuentemente como otros dispositivos de la organización. Es más importante que estos dispositivos se mantengan tan seguro como sea posible que estén actualizados con los cambios de la interfaz de usuario y estable. El modelo de servicio de LTSC impide que los dispositivos Windows 10 Enterprise LTSB reciba las actualizaciones de características habituales y proporciona sólo las actualizaciones de calidad para asegurarse de que la seguridad de los dispositivos más actualizada. Con esto en mente, las actualizaciones de calidad siguen estando inmediatamente disponibles para los clientes de Windows 10 Enterprise LTSB, pero los clientes pueden elegir aplácelos mediante el uso de una de las herramientas de mantenimiento que se ha mencionado en la sección de herramientas de mantenimiento.

* [Más información sobre LTSC](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)

## <a name="long-term-support-silicon-details"></a>Detalles de silicio compatibilidad a largo plazo

La versión de Windows 10 IoT Enterprise 2019 será una versión LTSC. La siguiente lista abarca todos los procesadores que se espera que se admiten en esta versión. Si va a usar una versión anterior de Windows 10 IoT Enterprise, puede encontrar detalles sobre la compatibilidad de procesador [aquí](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processor-table).

> | Windows 10 IoT Enterprise  |
> |-------------|
> | AMD® 6ª generación procesadores serie Ax-8xxx serie E Ex-8xxx & FX - 870 K | 
> | AMD® 7 generación procesadores serie Ax-9xxx serie E Ex-9xxx & FX 9xxx | 
> | 1xxx de AMD® Ryzen™ 3/5/7 | 
> | 2xxx de AMD® Ryzen™ 3/5/7 | 
> | Serie G AMD® | 
> | Serie AMD® R | 
> | AMD® V1xxx | 
> | 4 procesadores Intel® Core™ de generación | 
> | 5 de generación de procesadores de Intel® Core™ |
> | 6 de generación de procesadores de Intel® Core™ |
> | 7 de generación de procesadores de Intel® Core™ |
> | 8 procesadores Intel® Core™ de generación |
> | Procesador Intel® Atom™ E3900 serie |
> | Procesador de x5 E8000™ Atom de Intel® |
> | Procesador de x5 Z8350™ Atom de Intel® |
> | Familia de productos de E3800 de procesador Intel® Atom™ |
> | Procesadores Intel® Pentium® y procesador Celeron® N y serie J |

## <a name="helpful-resources"></a>Recursos útiles
> [!NOTE]
> Recursos adicionales pueden estar disponibles en el distribuidor para explicar la activación de OEM de Windows EPKEA y proporcionan orientación acerca de la generación de la empresa de fabricación listos para Windows IoT [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) imagen del dispositivo.

* [Personalizaciones de escritorio empresarial](https://docs.microsoft.com/windows-hardware/customize/enterprise/enterprise-custom-portal)
* [Filtro de escritura unificado para Windows 10](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Acceso asignado para Enterprise & Pro](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Selector de shell para las ediciones Enterprise y Education](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [Recursos de bloqueo](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Habilitar el modo incrustado y el uso de tareas en segundo plano en Windows IoT Enterprise](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [Configurar la telemetría de Windows en su organización](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Configura el quiosco y dispositivos compartidos que se ejecutan las ediciones de escritorio de Windows](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
* [Fabricación de escritorio](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
