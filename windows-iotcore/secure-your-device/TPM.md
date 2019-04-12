---
title: Módulo de plataforma segura (TPM)
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar un módulo de plataforma segura para habilitar las capacidades de cifrado para proteger mejor los dispositivos.
keywords: Windows iot, seguridad, módulo de plataforma segura, TPM, criptografía, las claves
ms.openlocfilehash: cf22811cbf45b5c715a19b8e12d7b00c2afaa9b8
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514515"
---
# <a name="trusted-platform-module-tpm-on-windows-10-iot-core"></a>Módulo de plataforma segura (TPM) en Windows 10 IoT Core

## <a name="what-is-tpm"></a>¿Qué es TPM?
Una plataforma segura Module (TPM), es un coprocesador criptográfico que incluye capacidades de generación de números aleatorios, generación segura de claves criptográficas y la limitación de su uso. También incluye capacidades como la autorización remota y almacenamiento sealed.
Especificación técnica del TPM está disponible públicamente, controlado por el Trusted Computing Group (TCG). La última versión 2.0 de TPM (publicado en octubre de 2014), es un cambio de diseño principal de la especificación que agrega nuevas funcionalidades y corrige los puntos débiles de la anterior 1.2 de TPM.

## <a name="why-tpm"></a>¿Por qué TPM?  
Los equipos que incorporan TPM pueden crear claves criptográficas y cifrarlas para que solo se puedan descifrar con el TPM. Este proceso, a menudo denominado **"encapsulado"** o **"enlace"** una clave, puede ayudar a proteger la clave de la divulgación. Cada TPM tiene una clave de "encapsulado" maestra, denominada clave de raíz de almacenamiento, que se almacena dentro del propio TPM. La parte privada de una clave creada en un TPM nunca se expone a cualquier otro componente, software, proceso o persona.  

Los equipos que incorporan un TPM también pueden crear una clave que no sólo se haya encapsulado, sino también esté ligada a ciertas medidas de la plataforma. Este tipo de clave solo puede ser sin ajustar cuando esas mediciones de plataforma tienen los mismos valores que tenían cuando se creó la clave. Este proceso se denomina **"sellar"** la clave en el TPM. Descifrar la clave se denomina **"desprecintado"**. TPM también puede sellar y quitar el sello de datos generados fuera de TPM. Con esta clave sellada y software como cifrado de unidad BitLocker, puede bloquear los datos hasta que se cumplan las condiciones de software o hardware específico.  

Con un TPM, las partes privadas de los pares de claves se mantienen separadas de la memoria controlada por el sistema operativo. Las claves se pueden sellar en TPM y comprobar determinadas garantías sobre el estado de un sistema (controles que definen el "nivel de confianza" de un sistema) pueden realizarse antes de que las claves son y liberarlas para su uso. Dado que el TPM usa su propio firmare interno y circuitos de lógica para las instrucciones de procesamiento, no se basa en el sistema operativo y no se expone a las vulnerabilidades que puedan existir en el sistema operativo o el software de aplicación.

## <a name="tpm-architecture"></a>Arquitectura TPM
_Diferencia entre 1.2 y 2.0 de TPM._  
La especificación de TPM se ha desarrollado dos veces. La primera vez, desarrolló desde 1.1b 1.2, que incorpora nuevas capacidades solicitado/identificado por el Comité de especificación. Este formulario sobrante de la característica de la evolución que realizan la especificación TPM 1.2 final muy complicado. Finalmente, los puntos débiles criptográficos SHA-1 (que era el algoritmo más seguro comercial en TPM 1.2) se han revelado que ha causado la necesidad de un cambio. Se ha rediseñado la arquitectura TPM desde cero, lo que resulta en el diseño mucho más integrado y unificado de TPM 2.0.  

Los cambios y mejoras en comparación con el TPM 1.2 anteriores incluyen:

* Compatibilidad con algoritmos criptográficos adicionales
* Mejoras en la disponibilidad de TPM a las aplicaciones
* Mecanismos de autorización mejorada
* Administración simplificada de TPM
* Capacidades adicionales para mejorar la seguridad de servicios de plataforma

Tenga en cuenta que Windows IoT Core es compatible con sólo TPM 2.0 y no es compatible con el TPM 1.2 obsoleta.

## <a name="what-is-tbs"></a>¿Qué es TB? 
La característica Servicios de Base TPM (TBS) es un servicio de sistema que permite el uso compartido de los recursos TPM. Comparte los recursos TPM entre varias aplicaciones en la misma máquina física a través de llamadas a procedimiento remoto (RPC). Centraliza el acceso a TPM a través de las aplicaciones que usan las prioridades especificadas por las aplicaciones que realiza la llamada.  

El TPM proporciona funciones de cifrado diseñadas para proporcionar la confianza en la plataforma. Dado que el TPM se implementa en el hardware, tiene recursos finitos. El TCG define una pila de Software TPM (TSS) que hace uso de estos recursos para proporcionar operaciones de confianza para software de la aplicación. Sin embargo, se ha realizado ninguna disposición para ejecutar un TSS implementación side-by-side con software de sistema operativo que también pueden usar los recursos TPM. La característica TBS soluciona este problema habilitando cada pila de software que se comunica con TBS usar recursos TPM comprobación para otras pilas de software que se estén ejecutando en el equipo.

## <a name="tpm-solutions-available-on-windows-iot-core"></a>Soluciones TPM disponibles en Windows IoT Core  
_Unas palabras sobre Software TPM (sTPM), el Firmware de TPM (fTPM), TPM discreto (dTPM)..._

### <a name="firmware-tpm-ftpm"></a>Firmware TPM (fTPM)  
Firmware TPM (fTPM) requiere compatibilidad de procesador/SoC especial que no está implementada actualmente en Raspberry Pi 2 o 3. MinnowBoard Max necesita la versión de firmware 0,80 o superior. DragonBoard410c proporciona capacidades de fTPM fuera de la casilla habilitado de forma predeterminada.  

### <a name="discrete-tpm-dtpm"></a>TPM discreto (dTPM)  
TPM discreto (dTPM) se considera la solución de confianza mayor de todas maneras.  
Hay varios fabricantes de chips dTPM y módulos PCB que se admiten en Windows IoT Core:

> | Fabricante | Página Web | Tipo de Modul | Chip de TPM |
> |-------------|----------|----------|----------| 
> | Infineon | [TPM Infineon](https://www.infineon.com/cms/en/product/evaluation-boards/iridium9670-tpm2.0-linux/)| Evalboard | [Infineon SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |
> | Pi3g | [Pi3g.com](https://pi3g.com/eigene-produkte/)| Evalboard & producto masivo | [Infineon SLB9670 TPM 2.0](https://www.infineon.com/cms/de/product/security-smart-card-solutions/optiga-embedded-security-solutions/optiga-tpm/slb-9670vq2.0/) |


### <a name="software-tpm-stpm"></a>Software TPM (sTPM)  
Software TPM (sTPM) también se conoce como el simulador de TPM. Es independiente de la plataforma, compatible con Windows IoT Core.  

> [!NOTE]
> sTPM está pensado únicamente con fines de desarrollo y no se proporciona ninguna ventaja de seguridad real.  


## <a name="samples"></a>Muestras  
<!--
* [TBSSample project C++](https://developer.microsoft.com/en-us/windows/iot/samples/tbssample)
  This tutorial demonstrates how to create a basic C++ application that uses TBS to poll the TPM.  -->
* [Ejemplo de la biblioteca urchin](https://github.com/ms-iot/security/tree/master/Urchin/Lib) en este tutorial se muestra cómo crear un ejemplo C++ aplicación que utiliza las funciones TPM mediante el [biblioteca Urchin](https://github.com/ms-iot/security). Urchin es una biblioteca de especificación conforme derivada de la implementación de referencia de TPM 2.0. Proporciona al cliente la funcionalidad para serializar/deserializar todas las estructuras de datos, correctamente calcular las autorizaciones, realizar el cifrado de parámetros y realizar la auditoría.

## <a name="additional-resources"></a>Recursos adicionales  
* [Especificaciones de plataforma segura (TPM) del módulo](http://www.trustedcomputinggroup.org/developers/trusted_platform_module) 
* [Especificación de la biblioteca de TCG TPM 2.0](http://www.trustedcomputinggroup.org/resources/tpm_library_specification)
* [Servicios de Base TPM](https://msdn.microsoft.com/library/windows/desktop/aa446796(v=vs.85).aspx) 
* [Habilitación de BitLocker y el arranque seguro](SecureBootAndBitLocker.md)

