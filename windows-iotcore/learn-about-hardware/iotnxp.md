---
title: Windows IoT y NXP i.MX
author: chsha
ms.author: chsha
ms.date: 02/22/2019
ms.topic: article
description: Obtenga información sobre Windows 10 IoT Core y NXP i.MX Qualcomm
keywords: Windows 10 IoT Core, introducción, i.MX, NXP
ms.openlocfilehash: a6331b8f5695c2a432e1b22f1ba275cd48c549e4
ms.sourcegitcommit: 3eacb968296e79e7e981fdc2a6f7f4f69c0920d1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65040184"
---
# <a name="window-10-iot-core-and-nxp-imx-socs"></a><span data-ttu-id="bc6b1-104">Windows 10 IoT Core y NXP Qualcomm i.MX</span><span class="sxs-lookup"><span data-stu-id="bc6b1-104">Window 10 IoT Core and NXP i.MX SoCs</span></span>

<span data-ttu-id="bc6b1-105">En 2018, NXP y Microsoft anunciaron una versión preliminar privada de Windows 10 IoT Core en NXP i.MX 6 y 7 i.MX silicon y empezó a trabajar en el i.MX 8M Qualcomm.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-105">In 2018, Microsoft and NXP announced a private preview of Windows 10 IoT Core on NXP i.MX 6 and i.MX 7 silicon and began work on the i.MX 8M SoCs.</span></span> <span data-ttu-id="bc6b1-106">Cientos de los desarrolladores comerciales, los investigadores y responsables de expresan su interés en la combinación de 10 años de actualizaciones de seguridad de Windows y la flexibilidad y confiabilidad de silicio NXP.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-106">Hundreds of commercial developers, researchers, and Makers expressed their interest in the combination of 10 years of Windows security updates and the flexibility and reliability of NXP silicon.</span></span> 
 
<span data-ttu-id="bc6b1-107">Durante la versión preliminar, los ingenieros de Microsoft y NXP gastado miles de horas de optimización y mejora la BSP basan en la entrada de aquellos que evaluar la solución.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-107">During the preview, Microsoft and NXP engineers spent thousands of hours tuning and improving the BSP based on input from those evaluating the solution.</span></span> <span data-ttu-id="bc6b1-108">Hemos trabajado con los clientes interesados en la modernización heredado industrial controladores, desarrollo nuevo en la nube conectados compilar soluciones de automatización y las puertas de enlace con seguridad líder de clase, como [confianza E/S](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).</span><span class="sxs-lookup"><span data-stu-id="bc6b1-108">We worked with customers interested in modernizing legacy industrial controllers, developing new cloud connected building automation solutions, and gateways with class leading security such as [trusted I/O](https://blogs.windows.com/windowsexperience/2018/04/24/trusted-cyber-physical-systems-looks-to-protect-your-critical-infrastructure-from-modern-threats-in-the-world-of-iot/#A0WkfgLBpgbLaFe3.97).</span></span>
 
<span data-ttu-id="bc6b1-109">Según el abrumador interés en la solución, Microsoft y NXP están avanzando BSP para el i.MX 6 y 7 i.MX i.MX 8M familia de Qualcomm disponible como versión preliminar pública no comercial.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-109">Based on the overwhelming interest in the solution, Microsoft and NXP are now making BSPs for the i.MX 6, i.MX 7, and i.MX 8M family of SoCs available as a non-commercial public preview.</span></span> <span data-ttu-id="bc6b1-110">Debido a la larga historia de Microsoft y NXP tienen en los datos incrustados y mercados de IoT, somos conscientes de la necesidad de flexibilidad de diseño.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-110">Because of the long history Microsoft and NXP have in the embedded and IoT markets, we understand the need for design flexibility.</span></span> <span data-ttu-id="bc6b1-111">Por lo tanto, además de varios equipos de la placa única y del sistema en las soluciones del módulo Microsoft, NXP y nuestro han habilitado los asociados de hardware, el i.MX 6 y 7 i.MX i.MX 8 M BSP se proporciona bajo licencia de código abierto.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-111">Therefore, in addition to the multiple single board computers and system on module solutions Microsoft, NXP, and our hardware partners have enabled, the i.MX 6, i.MX 7, and i.MX 8M BSPs are provided under open source licensing.</span></span> <span data-ttu-id="bc6b1-112">Ahora, todos los usuarios podrán tener acceso al contenido BSP completando para el i.MX 6 y 7 i.MX i.MX 8M familias de productos con fines de evaluación del hardware junto con la versión de octubre de 2018 de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-112">Now, everyone will be able to access the complete BSP contents for the i.MX 6, i.MX 7, and i.MX 8M product families for evaluation use on their hardware along with the October 2018 release of Windows 10 IoT Core.</span></span>


## <a name="bsp-access"></a><span data-ttu-id="bc6b1-113">Acceso BSP</span><span class="sxs-lookup"><span data-stu-id="bc6b1-113">BSP Access</span></span>

<span data-ttu-id="bc6b1-114">Si le interesa habilitar la compatibilidad con su propio hardware i.MX, vaya a la fuente BSP y documentación en [Github]( https://github.com/ms-iot/imx-iotcore).</span><span class="sxs-lookup"><span data-stu-id="bc6b1-114">If you are interested to enable support for your own i.MX hardware, please access the BSP source and documentation on [Github]( https://github.com/ms-iot/imx-iotcore).</span></span> <span data-ttu-id="bc6b1-115">A menos que se ha indicado, la mayor parte del origen se proporciona bajo licencia MIT.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-115">Unless noted, the majority of the source is provided under MIT license.</span></span> <span data-ttu-id="bc6b1-116">El código está aún en desarrollo.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-116">The code is still under development.</span></span> <span data-ttu-id="bc6b1-117">No todas las características de plataforma totalmente están habilitadas u optimizadas.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-117">Not all platform features are fully enabled or optimized.</span></span> <span data-ttu-id="bc6b1-118">El código actualmente está pensado para el desarrollo no comercial solo en tiempo de tiempo.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-118">The code is currently intended for non-commercial development only at time time.</span></span> <span data-ttu-id="bc6b1-119">Se espera que una versión de calidad comercial más adelante en 2019.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-119">A commercial quality release is expected later in 2019.</span></span>

<span data-ttu-id="bc6b1-120">Si tiene preguntas de NXP hardware/BSP respectivo o comentarios acerca de cómo el BSP puede funcionar mejor con su solución de destino, publíquelas en el [NXP Comunidad](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D).</span><span class="sxs-lookup"><span data-stu-id="bc6b1-120">If you have NXP hardware/BSP releated questions or feedback on how the BSP can better support your targeted solution, please post to the [NXP Community](https://community.nxp.com/community/imx/content?filterID=contentstatus%5Bpublished%5D%7Ecategory%5Bwindows%5D).</span></span> <span data-ttu-id="bc6b1-121">Para las preguntas relacionadas con Windows, utilice el [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).</span><span class="sxs-lookup"><span data-stu-id="bc6b1-121">For any Windows related questions, please use the [Microsoft Community](https://social.msdn.microsoft.com/forums/en-US/home?forum=WindowsIoT).</span></span>


## <a name="ecosystem-resources"></a><span data-ttu-id="bc6b1-122">Recursos del ecosistema</span><span class="sxs-lookup"><span data-stu-id="bc6b1-122">Ecosystem Resources</span></span>

<span data-ttu-id="bc6b1-123">Varios socios de Microsoft y NXP habilitó comercial i.MX 6, 7, i.MX y i.MX 8M dispositivos con soporte técnico para Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-123">Several Microsoft and NXP partners have enabled commercial i.MX 6, i.MX 7, and i.MX 8M devices with support for Windows 10 IoT Core.</span></span> <span data-ttu-id="bc6b1-124">Póngase en contacto con el asociado directamente para hardware y una imagen de plataforma.</span><span class="sxs-lookup"><span data-stu-id="bc6b1-124">Please contact the partner directly for hardware and a platform image.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="bc6b1-125">Dispositivo</span><span class="sxs-lookup"><span data-stu-id="bc6b1-125">Device</span></span></th>
<th align="left"><span data-ttu-id="bc6b1-126">Contacto</span><span class="sxs-lookup"><span data-stu-id="bc6b1-126">Contact</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-127"><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">PICO de Aaeon-IMX6</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-127"><a href="https://www.aaeon.com/en/p/pico-itx-boards-pico-imx6/">Aaeon PICO-IMX6</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-128"><a href="mailto:davidhung@aaeon.com.tw">David Hung</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-128"><a href="mailto:davidhung@aaeon.com.tw">David Hung</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-129"><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-129"><a href="http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858">Advantech RSB-4411</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:buy@advantech.com">buy@advantech.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-130"><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Puertas Compulab IoT</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-130"><a href="https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/">Compulab IoT-Gate</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-131"><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-131"><a href="mailto:igor@compulab.co.il">Igor Vaisbein</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-132"><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-P7</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-132"><a href="https://www.geniatech.com/product/som-imx6q-q7/">Geniatech SoM-iMX6Q-Q7</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> o <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-133"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-134"><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-134"><a href="https://www.geniatech.com/product/som-imx7d/">Geniatech SoM-iMX7D</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> o <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-135"><a href="mailto:mike.decker@geniatech.com">Mike Decker</a> or <a href="mailto:Fjj@geniatech.com">Fang Jijun</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-136"><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka Ro Electronics TX6UL, TX6S, TX6DL y TX6Q</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-136"><a href="https://www.karo-electronics.de/tx-standard.html?&L=1">Ka-Ro Electronics TX6UL, TX6S, TX6DL, and TX6Q</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-137"><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-137"><a href="mailto:us@karo-electronics.de">Uwe Steinkohl</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-138"><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith & Koep pConXS</a> con <a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-138"><a href="https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/">Keith & Koep pConXS</a> with <a href="https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/">Trizeps VII</a></span></span></p></td>
<td align="left"><p><p><a href="mailto:contact@keith-koep.com">contact@keith-koep.com</a></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-139"><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-139"><a href="https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html">Kontron SMARC-sAMX6i</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-140"><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-140"><a href="mailto:martin.unverdorben@kontron.com">Martin Unverdorben</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-141"><a href="https://phytec.com/product/phyboard-imx7-development-kit/">Kit de desarrollo de phyBOARD-i.MX 7</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-141"><a href="https://phytec.com/product/phyboard-imx7-development-kit/">phyBOARD-i.MX 7 Development Kit</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-142"><a href="mailto:sales@phytec.com">Fernando Benitez</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-142"><a href="mailto:sales@phytec.com">Fernando Benitez</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-143"><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Sólido ejecutar Edge Hummingboard</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-143"><a href="https://www.solid-run.com/imx6-win-10-iot-core/">Solid Run Hummingboard Edge</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-144"><a href="mailto:ilya@solid-run.com">Ilya Viten</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-144"><a href="mailto:ilya@solid-run.com">Ilya Viten</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-145"><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-145"><a href="https://www.viaembeddedstore.com/shop/boards/vab-820/">VIA VAB-820</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> o <a href="mailto:dreamku@via.com.tw">soñar Ku</span><span class="sxs-lookup"><span data-stu-id="bc6b1-146"><a href="mailto:MichaelFox@via.com.tw">Michael Fox</a> or <a href="mailto:dreamku@via.com.tw">Dream Ku</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-147"><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-147"><a href="https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors/evaluation-kit-for-the-i.mx-6ull-and-6ulz-applications-processor:MCIMX6ULL-EVK">MCIMX6ULL-EVK</a></span></span></p></td>
<td align="left"><p><p><span data-ttu-id="bc6b1-148"><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-148"><a href="mailto:Wei.A.Wang@nxp.com">Wei Wang</a></span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-149"><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-149"><a href="https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK">MCIMX8M-EVK</a></span></span></p></td>
<td align="left"></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="bc6b1-150"><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></span><span class="sxs-lookup"><span data-stu-id="bc6b1-150"><a href="http://www.nxp.com/imx8mminievk">MCIMX8MMINI-EVK</a></span></span></p></td>
<td align="left"></td>
</tr>
</tbody>
</table>
