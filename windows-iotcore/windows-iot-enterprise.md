---
title: Introducción a Windows 10 IoT Enterprise
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Obtenga información acerca de qué es Windows 10 IoT Enterprise y lo que se puede hacer con él.
keywords: Windows 10 IoT Enterprise, Enterprise, binario, Windows
ms.openlocfilehash: 0d7347e86e3fd3eb6b5b7ad0eccc0825611a9225
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739831"
---
# <a name="an-overview-of-windows-10-iot-enterprise"></a>Introducción a Windows 10 IoT Enterprise

> [!NOTE]
> Se admiten contenedores Windows para implementaciones comerciales en Windows Server, Windows IoT Server, Windows IoT Enterprise y Windows IoT Core.  A partir de la actualización de octubre de 2018 de Windows (compilación 17763), los contenedores Windows solo se pueden usar con Windows Enterprise y Professional para fines de desarrollo y pruebas.

## <a name="what-is-windows-10-iot-enterprise"></a>¿Qué es Windows 10 IoT Enterprise?
Windows 10 IoT Enterprise es una versión completa de Windows 10 que ofrece seguridad y capacidad de administración empresarial a las soluciones de IoT. Windows 10 IoT Enterprise comparte todos los beneficios del ecosistema mundial de Windows. Es un binario equivalente a Windows 10 Enterprise, por lo que puede usar las mismas herramientas de desarrollo y administración que los PC y portátiles cliente.  Sin embargo, en lo referente a licencias y distribución, la versión de escritorio y versiones de IoT son diferentes. Tenga en cuenta que Windows 10 IoT Enterprise ofrece las opciones de Canal de mantenimiento a largo plazo (LTSC) y Canal semianual (SAC). Los OEM pueden elegir la versión que necesitan para sus dispositivos.

## <a name="getting-started"></a>Introducción 

Para iniciar su recorrido con Windows 10 IoT Enterprise, tendrá que ponerse en contacto con alguno de los distribuidores de [esta lista](https://go.microsoft.com/fwlink/?linkid=2094697).

También puede probar una copia de evaluación de Windows 10 IoT Enterprise [aquí](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-10-enterprise).

Desde ahí, puede aprender a fabricar con Windows 10 IoT Enterprise con la [Guía de fabricación con Windows 10 IoT Enterprise](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview). 

## <a name="fixed-purpose-devices"></a>Dispositivos de propósito fijo 

> [!TIP]
> En el contrato de licencia encontrará una guía completa para todos los escenarios de uso de Windows 10 IoT Enterprise. Si no tiene este contrato de licencia, solicite el contrato comercial al fabricante de equipos originales con el que trabaje. 

Windows es conocido por ser el sistema operativo de los portátiles y dispositivos de escritorio que usan consumidores y empresas de todo el mundo.  Lo que no es tanto de dominio público es que, durante años, Windows también lo han usado muchos cajeros automáticos, terminales de punto de venta, sistemas de automatización industrial, clientes ligeros, dispositivos médicos, señalización digital, quioscos y otros dispositivos de propósito fijo.  Windows 10 IoT Enterprise permite crear dispositivos de propósito fijo con asignaciones y restricciones específicas en el contrato de licencia.  

Los dispositivos de propósito fijo difieren de los de propósito general en lo siguiente:  
* El dispositivo se bloquea en una aplicación individual o un conjunto fijo de aplicaciones a través de las características Acceso asignado o Iniciador de shell.  
* La experiencia del dispositivo es inmediata cuando el cliente lo enciende. Para ello se configura la imagen del dispositivo para que omita la configuración rápida normal de Windows. 
* Los teclados, los puertos USB y las directivas del dispositivos se bloquean para restringir el dispositivo para que se use solo en su propósito fijo.  
* El fabricante de equipos originales concede la licencia del dispositivo al usuario con el software adjunto al dispositivo como un producto completo y se usan los términos específicos de Windows en sus propios contratos.
* El fabricante de equipos originales proporciona atención al cliente para el producto completo, lo que incluye las funciones del sistema operativo.

## <a name="long-term-servicing-channel-ltsc"></a>Canal de mantenimiento a largo plazo (LTSC)

Los sistemas especializados, como los PC que controlan equipos médicos, sistemas de punto de venta y cajeros automáticos, a menudo requieren una opción de mantenimiento prolongado debido a su finalidad. Por lo general, estos dispositivos realizan una única tarea importante y no necesitan actualizaciones de características tan frecuentemente como otros dispositivos de la organización. En estos dispositivos es más importante que sean estables y seguros que estén actualizados con los últimos cambios en la interfaz de usuario. El modelo de servicio LTSC impide que los dispositivos LTSC de Windows 10 Enterprise reciban las actualizaciones de características habituales y proporciona solo actualizaciones de calidad para garantizar que la seguridad de los dispositivos se mantenga actualizada. Con esto en mente, las actualizaciones de calidad siguen estando disponibles inmediatamente para los clientes LTSC de Windows 10 IoT Enterprise, pero los clientes pueden elegir aplazarlas mediante una de las herramientas de mantenimiento mencionadas en la sección Herramientas de mantenimiento.

* [Más información acerca de LTSC](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)

> [!NOTE]
> Dada la larga duración de las versiones LTSC y la ventaja de mantener una versión específica durante 10 años, se cobrará una tarifa de actualización a los clientes que pasen de una versión LTSC a otra.

## <a name="long-term-support-silicon-details"></a>Detalles de soporte técnico para procesadores a largo plazo

La versión Windows 10 IoT Enterprise 2019 será una versión LTSC. La siguiente lista engloba todos los procesadores que se espera que sean compatibles con esta versión. Si planea usar una versión anterior de Windows 10 IoT Enterprise, puede encontrar detalles acerca de los procesadores compatibles [aquí](https://docs.microsoft.com/windows-hardware/design/minimum/windows-processor-requirements#windows-iot-enterprise--embedded-processor-table).

> | Windows 10 IoT Enterprise  |
> |-------------|
> | Procesadores AMD® de 6ª generación de la serie Ax-8xxx y de la serie E Ex-8xxx y FX - 870 K | 
> | Procesadores AMD® de 7ª generación de la serie Ax-9xxx y de la serie E Ex-9xxx y FX-9xxx | 
> | AMD® Ryzen™ 3/5/7 1xxx | 
> | AMD® Ryzen™ 3/5/7 2xxx | 
> | AMD® serie G | 
> | AMD® serie R | 
> | AMD® V1xxx | 
> | Procesadores Intel® Core™ de 4ª generación | 
> | Procesadores Intel® Core™ de 5ª generación |
> | Procesadores Intel® Core™ de 6ª generación |
> | Procesadores Intel® Core™ de 7ª generación |
> | Procesadores Intel® Core™ de 8ª generación |
> | Procesador Intel® Atom™ de la serie E3900 |
> | Procesador Intel® Atom™ x5-E8000 |
> | Procesador Intel® Atom™ x5-Z8350 |
> | Familia de productos del procesador Intel® Atom™ E3800 |
> | Procesador Intel® Pentium® y Celeron® de las series N y J |

## <a name="helpful-resources"></a>Recursos útiles
> [!NOTE]
> Su distribuidor puede tener recursos adicionales disponibles para explicar la activación OEM de Windows EPKEA y proporcionar una guía para la generación de una imagen de dispositivo [WIM](https://msdn.microsoft.com/library/windows/desktop/dd861280.aspx) Windows IoT Enterprise lista para la fabricación.

* [Personalizaciones para enterprise desktop](https://docs.microsoft.com/windows-hardware/customize/enterprise/enterprise-custom-portal)
* [Filtro de escritura unificado para Windows 10](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter)
* [Acceso asignado para Enterprise & Pro](https://docs.microsoft.com/windows-hardware/customize/enterprise/assigned-access)
* [Selector de shell para las ediciones Enterprise y Education](https://docs.microsoft.com/windows-hardware/customize/enterprise/shell-launcher)
* [Recursos de bloqueo](https://docs.microsoft.com/windows-hardware/customize/enterprise/create-a-kiosk-image) 
* [Habilitación del modo insertado y uso de tareas en segundo plano en Windows IoT Enterprise](https://docs.microsoft.com/windows/iot-core/develop-your-app/embeddedmode)
* [Configuración de la telemetría de Windows en una organización](https://docs.microsoft.com/windows/configuration/configure-windows-telemetry-in-your-organization )
* [Configuración de dispositivos compartidos y de quioscos que ejecutan ediciones de escritorio de Windows](https://docs.microsoft.com/windows/configuration/kiosk-shared-pc)
* [Fabricación de escritorio](https://docs.microsoft.com/windows-hardware/manufacture/desktop/)
