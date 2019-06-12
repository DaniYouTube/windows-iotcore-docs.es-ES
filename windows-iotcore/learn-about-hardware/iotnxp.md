---
title: Windows IoT y NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: Obtenga información sobre Windows 10 IoT Core y NXP i.MX Qualcomm
keywords: Windows 10 IoT Core, introducción, i.MX, NXP
ms.openlocfilehash: b27589d574db0f459e42d4a8170defa2689fa001
ms.sourcegitcommit: fa4a29fcd5af464924a0a5ab581f08f631a3ad72
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835594"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core y NXP Qualcomm i.MX

En 2018, NXP y Microsoft anunciaron una versión preliminar privada de Windows 10 IoT Core en NXP i.MX 6 y 7 i.MX silicon y empezó a trabajar en el i.MX 8M Qualcomm. Cientos de los desarrolladores comerciales, los investigadores y responsables de expresan su interés en la combinación de 10 años de actualizaciones de seguridad de Windows y la flexibilidad y confiabilidad de silicio NXP. 
 
Durante la versión preliminar, los ingenieros de Microsoft y NXP gastado miles de horas de optimización y mejora la BSP basan en la entrada de aquellos que evaluar la solución. Hemos trabajado con los clientes interesados en la modernización heredado industrial controladores, desarrollo nuevo en la nube conectados compilar soluciones de automatización y las puertas de enlace con seguridad líder de clase, como [confianza E/S](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).
 
Según el abrumador interés en la solución, Microsoft y NXP están avanzando BSP para el i.MX 6 y 7 i.MX i.MX 8M familia de Qualcomm disponible como versión preliminar pública no comercial. Debido a la larga historia de Microsoft y NXP tienen en los datos incrustados y mercados de IoT, somos conscientes de la necesidad de flexibilidad de diseño. Por lo tanto, además de varios equipos de la placa única y del sistema en las soluciones del módulo Microsoft, NXP y nuestro han habilitado los asociados de hardware, el i.MX 6 y 7 i.MX i.MX 8 M BSP se proporciona bajo licencia de código abierto. Ahora, todos los usuarios podrán tener acceso al contenido BSP completando para el i.MX 6 y 7 i.MX i.MX 8M familias de productos con fines de evaluación del hardware junto con la versión de octubre de 2018 de Windows 10 IoT Core.


## <a name="bsp-access"></a>Acceso BSP

Si le interesa habilitar la compatibilidad con su propio hardware i.MX, vaya a la fuente BSP y documentación en [Github]( https://github.com/ms-iot/imx-iotcore). A menos que se ha indicado, la mayor parte del origen se proporciona bajo licencia MIT. El código se publica para uso comercial con soporte técnico proporcionado por NXP y pueden encontrarse [aquí](https://www.nxp.com/support/developer-resources/evaluation-and-development-boards/i.mx-evaluation-and-development-boards/i.mx-software-and-development-tool:IMX-SW).

Si tiene preguntas de NXP hardware/BSP respectivo o comentarios acerca de cómo el BSP puede funcionar mejor con su solución de destino, publíquelas en el [NXP Comunidad](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D). Para las preguntas relacionadas con Windows, utilice el [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).


## <a name="ecosystem-resources"></a>Recursos del ecosistema

Varios socios de Microsoft y NXP habilitó comercial i.MX 6, 7, i.MX y i.MX 8M dispositivos con soporte técnico para Windows 10 IoT Core. Póngase en contacto con el asociado directamente para hardware y una imagen de plataforma.


> | Dispositivo | Contacto |
> |-------|------|
> | [PICO de Aaeon-IMX6](https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/) | [David Hung](mailto:davidhung@aaeon.com.tw) |
> | [Advantech RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) | [buy@advantech.com](mailto:buy@advantech.com) |
> | [Puertas Compulab IoT](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | [Igor Vaisbein](mailto:igor@compulab.co.il) | 
> | [Geniatech SoM-iMX6Q-P7](https://www.geniatech.com/product/som-imx6q-q7/) | [Mike Decker](mailto:mike.decker@geniatech.com) o [Fang Jijun](mailto:Fjj@geniatech.com) |
> | [Geniatech SoM-iMX7D](https://www.geniatech.com/product/som-imx7d/) | [Mike Decker](mailto:mike.decker@geniatech.com) o [Fang Jijun](mailto:Fjj@geniatech.com) |
> | [Ka Ro Electronics TX6UL, TX6S, TX6DL y TX6Q](https://www.karo-electronics.de/tx-standard.html?&L=1) | [Uwe Steinkohl](mailto:us@karo-electronics.de) |
> | [Keith & Koep pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/) con [Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) | [contact@keith-koep.com](mailto:contact@keith-koep.com) |
> | [Kontron SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) | [Martin Unverdorben](mailto:martin.unverdorben@kontron.com) |
> | [Kit de desarrollo de phyBOARD-i.MX 7](https://phytec.com/product/phyboard-imx7-development-kit/) | [Fernando Benitez](mailto:sales@phytec.com) |
> | [Sólido ejecutar Edge Hummingboard](https://www.solid-run.com/imx6-win-10-iot-core/) | [Ilya Viten](mailto:ilya@solid-run.com) |
> | [VIA VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) | [Michael Fox](mailto:MichaelFox@via.com.tw) o [soñar Ku](mailto:dreamku@via.com.tw) |
> | [WeAreDev WAD-MX6W](http://www.wearedev.net/?mod=wadmx6w) | [help@wearedev.net](mailto:help@wearedev.net) |
> | [MCIMX6ULL-EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK) | [Wei Wang](mailto:Wei.A.Wang@nxp.com) |
> | [MCIMX8M-EVK](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) |  |
> | [MCIMX8MMINI-EVK](http://www.nxp.com/imx8mminievk) | []() |
