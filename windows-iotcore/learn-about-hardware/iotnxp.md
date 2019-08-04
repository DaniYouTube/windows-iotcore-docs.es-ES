---
title: Windows IoT y NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: Más información sobre Windows 10 IoT Core y NXP i.MX SOC
keywords: Windows 10 IoT Core, introducción, i.MX, NXP
ms.openlocfilehash: 244d767507393680df7a48487522ff62be40692d
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739812"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core y NXP i.MX SOC

En 2018, Microsoft y NXP anunció una versión preliminar privada de Windows 10 IoT Core en NXP i.MX 6 y i.MX 7 Silicon y empezó a trabajar en la i.mx 8 m 8 m. Cientos de desarrolladores, investigadores y desarrolladores comerciales expresaron su interés en la combinación de 10 años de actualizaciones de seguridad de Windows y la flexibilidad y confiabilidad de NXP Silicon. 
 
Durante la versión preliminar, los ingenieros de Microsoft y NXP dedican miles de horas a ajustar y mejorar el BSP en función de la entrada de los que evalúan la solución. Trabajamos con clientes interesados en la modernización de controladores industriales heredados, el desarrollo de nuevas soluciones de automatización para la creación de conexiones en la nube y puertas de enlace con seguridad líder de clase, como [e/s de confianza](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).
 
En función del interesante interés de la solución, Microsoft y NXP ahora están haciendo que BSP para la familia i.MX 6, i.MX 7 y i.MX 8 $ de SOC disponible como versión preliminar pública no comercial. Debido al largo historial que Microsoft y NXP tiene en los mercados de IoT y Embedded, somos conscientes de la necesidad de flexibilidad de diseño. Por lo tanto, además de los equipos de varios paneles y del sistema en las soluciones de módulos, Microsoft, NXP y nuestros asociados de hardware han habilitado, los i.MX 6, i.MX 7 y i.MX 8 $ BSP se proporcionan con licencia de código abierto. Ahora, todo el mundo podrá acceder al contenido de BSP completo de las familias de productos i.MX 6, i.MX 7 y i.MXn para su evaluación en su hardware, junto con la versión 2018 de octubre de Windows 10 IoT Core.


## <a name="bsp-access"></a>Acceso BSP

Si está interesado en habilitar la compatibilidad con su propio hardware de i.MX, acceda a la documentación y el origen de BSP en [GitHub]( https://github.com/ms-iot/imx-iotcore). A menos que se indique lo contrario, la mayoría del origen se proporciona en la licencia MIT. El código se publica para uso comercial con soporte técnico proporcionado por NXP y se puede encontrar [aquí](https://www.nxp.com/support/developer-resources/evaluation-and-development-boards/i.mx-evaluation-and-development-boards/i.mx-software-and-development-tool:IMX-SW).

Si tiene preguntas de NXP de hardware/BSP respectivo o comentarios sobre cómo el BSP puede admitir mejor su solución de destino, publique en la [comunidad de NXP](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D). Si tiene alguna pregunta relacionada con Windows, use la [comunidad de Microsoft](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).


## <a name="ecosystem-resources"></a>Recursos del ecosistema

Varios asociados de Microsoft y NXP han habilitado los dispositivos comerciales i.MX 6, i.MX 7 y i.MX 8M compatibles con Windows 10 IoT Core. Póngase en contacto directamente con el asociado para hardware y una imagen de plataforma.


> | Dispositivo | Contacto |
> |-------|------|
> | [AAEON PICO-IMX6](https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/) | [David bloqueado](mailto:davidhung@aaeon.com.tw) |
> | [Advantech RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) | [buy@advantech.com](mailto:buy@advantech.com) |
> | [Compulab IoT-Gate](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | [Igor Vaisbein](mailto:igor@compulab.co.il) | 
> | [FS Eletronik sistema armStone A9](https://www.fs-net.de/en/products/armstone/armstonea9/) | [support@fs-net.de](mailto:support@fs-net.de) |
> | [Geniatech SoM-iMX6Q-Q7](https://www.geniatech.com/product/som-imx6q-q7/) | [Mike Decker](mailto:mike.decker@geniatech.com) o [Fang Jijun](mailto:Fjj@geniatech.com) |
> | [Geniatech SoM-iMX7D](https://www.geniatech.com/product/som-imx7d/) | [Mike Decker](mailto:mike.decker@geniatech.com) o [Fang Jijun](mailto:Fjj@geniatech.com) |
> | [TX6UL, TX6S, TX6DL y TX6Q de electrónica Ka](https://www.karo-electronics.de/tx-standard.html?&L=1) | [Uwe Steinkohl](mailto:us@karo-electronics.de) |
> | [Keith & Koep pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/) con [Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) | [contact@keith-koep.com](mailto:contact@keith-koep.com) |
> | [Kontron SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) | [Martin Unverdorben](mailto:martin.unverdorben@kontron.com) |
> | [Novtech Meerkat](http://novtech.com/products/meerkat96.html) | [sales@novtech.com](mailto:sales@novtech.com) |
> | [Kit de desarrollo de phyBOARD-i.MX 7](https://phytec.com/product/phyboard-imx7-development-kit/) | [Fernando Benitez](mailto:sales@phytec.com) |
> | [Borde Hummingboard de ejecución sólida](https://www.solid-run.com/imx6-win-10-iot-core/) | [Ilya Viten](mailto:ilya@solid-run.com) |
> | [A TRAVÉS DE VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) | [Michael Fox](mailto:MichaelFox@via.com.tw) o [sueño Ku](mailto:dreamku@via.com.tw) |
> | [WeAreDev WAD-MX6W](http://www.wearedev.net/?mod=wadmx6w) | [help@wearedev.net](mailto:help@wearedev.net) |
> | [MCIMX6ULL-EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK) | [Wei Wang](mailto:Wei.A.Wang@nxp.com) |
> | [MCIMX8M-EVK](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) |  |
> | [MCIMX8MMINI-EVK](http://www.nxp.com/imx8mminievk) | []() |
