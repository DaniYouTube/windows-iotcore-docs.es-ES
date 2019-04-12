---
title: Windows IoT y NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: Obtenga información sobre Windows 10 IoT Core y NXP i.MX Qualcomm
keywords: Windows 10 IoT Core, introducción, i.MX, NXP
ms.openlocfilehash: 2dc212fa403e2d8d4c32bffbae3c8bcd97b5b022
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514431"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a>Windows 10 IoT Core y NXP Qualcomm i.MX

En 2018, NXP y Microsoft anunciaron una versión preliminar privada de Windows 10 IoT Core en NXP i.MX 6 y 7 i.MX silicon y empezó a trabajar en el i.MX 8M Qualcomm. Cientos de los desarrolladores comerciales, los investigadores y responsables de expresan su interés en la combinación de 10 años de actualizaciones de seguridad de Windows y la flexibilidad y confiabilidad de silicio NXP. 
 
Durante la versión preliminar, los ingenieros de Microsoft y NXP gastado miles de horas de optimización y mejora la BSP basan en la entrada de aquellos que evaluar la solución. Hemos trabajado con los clientes interesados en la modernización heredado industrial controladores, desarrollo nuevo en la nube conectados compilar soluciones de automatización y las puertas de enlace con seguridad líder de clase, como [confianza E/S](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).
 
Según el abrumador interés en la solución, Microsoft y NXP están avanzando BSP para el i.MX 6 y 7 i.MX i.MX 8M familia de Qualcomm disponible como versión preliminar pública no comercial. Debido a la larga historia de Microsoft y NXP tienen en los datos incrustados y mercados de IoT, somos conscientes de la necesidad de flexibilidad de diseño. Por lo tanto, además de varios equipos de la placa única y del sistema en las soluciones del módulo Microsoft, NXP y nuestro han habilitado los asociados de hardware, el i.MX 6 y 7 i.MX i.MX 8 M BSP se proporciona bajo licencia de código abierto. Ahora, todos los usuarios podrán tener acceso al contenido BSP completando para el i.MX 6 y 7 i.MX i.MX 8M familias de productos con fines de evaluación del hardware junto con la versión de octubre de 2018 de Windows 10 IoT Core.


## <a name="bsp-access"></a>Acceso BSP

Si le interesa habilitar la compatibilidad con su propio hardware i.MX, vaya a la fuente BSP y documentación en [Github]( https://github.com/ms-iot/imx-iotcore). A menos que se ha indicado, la mayor parte del origen se proporciona bajo licencia MIT. El código está aún en desarrollo. No todas las características de plataforma totalmente están habilitadas u optimizadas. El código actualmente está pensado para el desarrollo no comercial solo en tiempo de tiempo. Se espera que una versión de calidad comercial más adelante en 2019.

Si tiene preguntas de NXP hardware/BSP respectivo o comentarios acerca de cómo el BSP puede funcionar mejor con su solución de destino, publíquelas en el [NXP Comunidad](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D). Para las preguntas relacionadas con Windows, utilice el [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).


## <a name="ecosystem-resources"></a>Recursos del ecosistema

Varios socios de Microsoft y NXP habilitó comercial i.MX 6, 7, i.MX y i.MX 8M dispositivos con soporte técnico para Windows 10 IoT Core. Póngase en contacto con el asociado directamente para hardware y una imagen de plataforma.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Dispositivo</th>
<th align="left">Contacto</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">PICO de Aaeon-IMX6</a></p></td>
<td align="left"><p><p><a href="mailto:davidhung@aaeon.com.tw">David Hung</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Puertas Compulab IoT</a></p></td>
<td align="left"><p><p><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-P7</a></p></td>
<td align="left"><p><p><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> o <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></p></td>
<td align="left"><p><p><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> o <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka Ro Electronics TX6UL, TX6S, TX6DL y TX6Q</a></p></td>
<td align="left"><p><p><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://wce.keith-koep.com/en/products/pconxs-ff/">Keith & Koep pConXS</a> con <a href="http://wce.keith-koep.com/en/products/trizeps7-i.MX6/">Trizeps VII</a></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></p></td>
<td align="left"><p><p><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://phytec.com/product/phyboard-imx7-development-kit/">Kit de desarrollo de phyBOARD-i.MX 7</a></p></td>
<td align="left"><p><p><a href="mailto:sales@phytec.com">Fernando Benitez</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Sólido ejecutar Edge Hummingboard</a></p></td>
<td align="left"><p><p><a href="mailto:ilya@solid-run.com">Ilya Viten</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></p></td>
<td align="left"><p><p><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> o <a href="mailto:dreamku@via.com.tw">soñar Ku</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></p></td>
<td align="left"><p><p><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
