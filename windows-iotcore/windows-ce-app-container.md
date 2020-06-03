---
title: Información general de Windows CE contenedor de aplicaciones
ms.date: 05/22/2020
ms.topic: article
description: Obtener acceso a la versión preliminar privada del contenedor de la aplicación Windows CE
keywords: Windows 10 IoT Core, Windows CE, migración de aplicaciones, CEPAL
ms.openlocfilehash: 9231e3def5c3da5efee49c1cd6026cca782058da
ms.sourcegitcommit: 7b9353b2bf60b242d70f0d2f21a4006439639194
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2020
ms.locfileid: "84274493"
---
# <a name="an-overview-of-the-windows-ce-app-container"></a>Información general sobre el contenedor de la aplicación Windows CE
Microsoft ha proporcionado plataformas y sistemas operativos para dispositivos incrustados durante décadas. Como las nuevas ofertas como Windows 10 IoT están disponibles, nuestros clientes y asociados están cada vez más interesados en las características de seguridad avanzada, plataforma y conectividad en la nube que ofrecen estos sistemas operativos. Los clientes que se mueven de la mayoría de las ediciones anteriores de Windows, como Windows XP y Windows 7, pueden hacerlo con poco esfuerzo debido a las aplicaciones compatibles con binario. Otros sistemas operativos, como Windows CE, requieren que los generadores de dispositivos modifiquen el código fuente. La migración de aplicaciones como esta puede ser desafiante.

Para ayudar a estos clientes a migrar a Windows 10 IoT y aprovechar toda la eficacia del perímetro inteligente, como inteligencia artificial y aprendizaje automático, Microsoft está desarrollando tecnología que permitirá a la mayoría de los clientes ejecutar sus aplicaciones de Windows CE sin modificar existentes en IoT de Windows 10 mientras continúan invirtiendo en la actualización de sus aplicaciones. Puede obtener más información sobre cómo funciona esta tecnología en el episodio de IoT show <a href="https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices">Windows CE los dispositivos</a>.

## <a name="how-to-get-started-with-the-private-preview"></a>Cómo empezar a trabajar con la versión preliminar privada

Tenemos previsto tener la tecnología de contenedor de aplicaciones Windows CE disponible con carácter general a partir de este año como parte de <a href="https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iotcoreservicesoverview">Windows 10 IOT Core Services</a>. Sin embargo, si es un desarrollador comercial con una solución Windows CE y desea comenzar a evaluar la tecnología, póngase en contacto con <a href="mailto:cemigrat@microsoft.com">cemigrat@microsoft.com</a> desde su cuenta de correo electrónico de empresa para acceder a la versión preliminar privada.

## <a name="what-are-the-platform-requirements"></a>¿Cuáles son los requisitos de la plataforma? 
La tecnología de migración de aplicaciones Windows CE funciona mediante la ejecución de una instancia de Windows CE 2013 sobre Windows 10 IoT Core. 

La solución funciona con código de aplicación de 32 bits y requiere una plataforma base ARM32 o x64 que sea <a href="https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards">compatible</a> con Windows 10 IOT Core.
Debe estar familiarizado con la creación de una imagen del sistema Windows CE 2013 mediante el generador de plataformas, así como la creación de una imagen para Windows 10 IoT Core.
