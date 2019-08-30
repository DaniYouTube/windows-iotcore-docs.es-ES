---
title: Módulo de plataforma segura (TPM)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo usar un Módulo de plataforma segura para habilitar las capacidades criptográficas para mejorar la seguridad de los dispositivos.
keywords: Windows IOT, seguridad, Módulo de plataforma segura, TPM, criptografía, claves
ms.openlocfilehash: 70552a5f98891281879f1d45cbdbd671b56dd902
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533319"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>Módulo de plataforma segura (TPM) en Windows 10 IoT Core

## <a name="what-is-tpm"></a>¿Qué es TPM?
Un Módulo de plataforma segura (TPM) es un coprocesador criptográfico que incluye funcionalidades para la generación de números aleatorios, la generación segura de claves criptográficas y la limitación de su uso. También incluye funcionalidades como la atestación remota y el almacenamiento sellado.
La especificación técnica del TPM está disponible públicamente, controlada por el Trusted Computing Group (TCG). La versión más reciente del TPM 2,0 (Publicada en octubre de 2014) es un rediseño importante de la especificación que agrega nuevas funcionalidades y corrige los puntos débiles del antiguo TPM 1,2.

## <a name="why-tpm"></a>¿Por qué TPM?  
Los equipos que incorporan TPM pueden crear claves criptográficas y cifrarlas para que solo se puedan descifrar con el TPM. Este proceso, a menudo denominado **"Encapsular"** o **"enlazar"** una clave, puede ayudar a proteger la clave contra la divulgación. Cada TPM tiene una clave de "encapsulado" maestra, denominada clave raíz de almacenamiento, que se almacena en el propio TPM. La parte privada de una clave creada en un TPM nunca se expone a ningún otro componente, software, proceso o persona.  

Los equipos que incorporan un TPM también pueden crear una clave que no sólo se haya encapsulado, sino que también esté ligada a determinadas mediciones de la plataforma. Este tipo de clave solo se puede desempaquetar cuando esas mediciones de plataforma tienen los mismos valores que tenían cuando se creó la clave. Este proceso se denomina **"sellar"** la clave en el TPM. El descifrado de la clave se denomina **"dessellado"** . El TPM también puede sellar y anular la sellado de los datos generados fuera de TPM. Con esta clave sellada y software como Cifrado de unidad BitLocker, puede bloquear los datos hasta que se cumplan las condiciones específicas de hardware o software.  

Con un TPM, las partes privadas de pares de claves se mantienen independientes de la memoria controlada por el sistema operativo. Las claves se pueden sellar en el TPM y se pueden realizar ciertas garantías sobre el estado de un sistema (las garantías que definen el "grado de confiabilidad" de un sistema) antes de que las claves se dessellen y se liberen para su uso. Dado que el TPM usa su propio firmware interno y circuitos lógicos para las instrucciones de procesamiento, no se basa en el sistema operativo y no se expone a las vulnerabilidades que pueden existir en el software del sistema operativo o de la aplicación.

## <a name="tpm-architecture"></a>Arquitectura de TPM
_Diferencia entre TPM 1,2 y TPM 2,0._  
La especificación del TPM se ha desarrollado dos veces. La primera vez, desarrollada de la versión 1.1 b a la 1,2, que incorpora nuevas capacidades solicitadas/identificadas por el Comité de especificaciones. Esta forma de evolución de la característica ha hecho que la especificación final del TPM 1,2 sea muy complicada. Finalmente, se revelaron los puntos débiles criptográficos de SHA-1 (que era el algoritmo comercial más fuerte en TPM 1,2), lo que hizo que se produjeron cambios. La arquitectura de TPM se ha rediseñado desde cero, lo que produce un diseño unificado y mucho más integrado de TPM 2,0.  

Los cambios y las mejoras que se comparan con el TPM 1,2 anterior incluyen:

* Compatibilidad con algoritmos criptográficos adicionales
* Mejoras en la disponibilidad del TPM en las aplicaciones
* Mecanismos de autorización mejorados
* Administración simplificada de TPM
* Capacidades adicionales para mejorar la seguridad de los servicios de la plataforma

> [!NOTE] 
> Windows IoT Core solo admite TPM 2,0 y no es compatible con el TPM 1,2 obsoleto.

## <a name="what-is-tbs"></a>¿Qué es TBS? 
La característica servicios base de TPM (TBS) es un servicio del sistema que permite el uso compartido transparente de los recursos de TPM. Comparte los recursos de TPM entre varias aplicaciones en el mismo equipo físico a través de llamadas a procedimiento remoto (RPC). Centraliza el acceso de TPM entre aplicaciones utilizando las prioridades especificadas por las aplicaciones que llaman.  

El TPM proporciona funciones criptográficas diseñadas para proporcionar confianza en la plataforma. Dado que el TPM está implementado en hardware, tiene recursos finitos. El TCG define una pila de software de TPM (TSS) que hace uso de estos recursos para proporcionar operaciones de confianza para el software de la aplicación. Sin embargo, no se realiza ninguna disposición para ejecutar una implementación de TSS en paralelo con el software del sistema operativo que también puede usar recursos de TPM. La característica TBS resuelve este problema habilitando cada pila de software que se comunica con TBS para usar la comprobación de recursos de TPM para cualquier otra pila de software que pueda estar ejecutándose en la máquina.

## <a name="tpm-solutions-available-on-windows-iot-core"></a>Soluciones de TPM disponibles en Windows IoT Core  
_Algunas palabras sobre el TPM de software (sTPM), el TPM de firmware (fTPM), el TPM discreto (dTPM)..._

### <a name="firmware-tpm-ftpm"></a>Firmware TPM (fTPM)  
El TPM de firmware (fTPM) requiere una compatibilidad especial con el procesador o SoC que no está implementada actualmente en Raspberry pi 2 ó 3. MinnowBoard Max necesita firmware versión 0,80 o superior. DragonBoard410c proporciona funcionalidades de fTPM de forma predeterminada, que están habilitadas de manera predeterminada.  

### <a name="discrete-tpm-dtpm"></a>TPM discreto (dTPM)  
El TPM discreto (dTPM) se considera la solución más confiable por todos los medios.  
Hay varios fabricantes de chips de dTPM y módulos PCB que se admiten en Windows IoT Core:

> | Fabricante | Página Web | Tipo Modul | Chip TPM |
> |-------------|----------|----------|----------| 
> | Infineon | [TPM de Infineon](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [TPM SLB9670 TPM 2,0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| & De producto masivo Evalboard | [TPM SLB9670 TPM 2,0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>TPM de software (sTPM)  
El TPM de software (sTPM) también se conoce como simulador de TPM. Es independiente de la plataforma, compatible con Windows IoT Core.  

> [!NOTE]
> sTPM está pensado únicamente para fines de desarrollo y no proporciona ninguna ventaja de seguridad real.  


## <a name="samples"></a>Muestras  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Ejemplo de biblioteca Urchin](https://github.com/ms-iot/security/tree/master/Urchin/Lib) En este tutorial se muestra cómo crear una C++ aplicación de ejemplo que ejercita la funcionalidad de TPM mediante la [biblioteca Urchin](https://github.com/ms-iot/security). Urchin es una biblioteca compatible con especificaciones derivada de la implementación de referencia de TPM 2,0. Proporciona al cliente la funcionalidad para calcular las referencias de todas las estructuras de datos y anular su serialización, calcular correctamente las autorizaciones, realizar el cifrado de parámetros y realizar auditorías.

## <a name="additional-resources"></a>Recursos adicionales  
* [Especificaciones de Módulo de plataforma segura (TPM)](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [Especificación de biblioteca 2,0 de TCG TPM](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [Servicios base de TPM](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [Habilitación del arranque seguro y BitLocker](SecureBootAndBitLocker.md)

