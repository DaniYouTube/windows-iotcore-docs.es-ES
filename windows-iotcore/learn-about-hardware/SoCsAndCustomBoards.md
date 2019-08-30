---
title: SOC y paneles personalizados para Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de las características de hardware para una variedad de paneles sugeridos y dispositivos de la comunidad.
keywords: Windows IOT, dispositivos de desarrollo, paneles, SOC, SOM, sistema en chips, Raspberry pi 2, Raspberry PI 3, Minnowboard Max, DragonBoard
ms.openlocfilehash: 85625926a5aaa474ba2ea86ff6c2890553669131
ms.sourcegitcommit: 8bb162cbfa286107e243a0286fe53b3b9cc3f359
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67345116"
---
# <a name="socs-and-custom-boards"></a>SOC y paneles personalizados

## <a name="microsoft-enabled-socs"></a>SOC habilitado para Microsoft

Microsoft trabaja junto con Broadcom, Intel, NXP y Qualcomm para comprobar la compatibilidad con Windows 10 IoT Core en el sistema de varios proveedores en un chip (SOC). Estos SOC de IoT Core se usan en cientos de distintos dispositivos que puede usar para prototipo y comercializar su idea.

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Intel® Atom® Processor E3900 Series (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016)](https://www.qualcomm.com/products/snapdragon/processors/410) | [Familia i.MX 6](http://aka.ms/iotnxp) |
| BCM2836 | [Procesador Intel® Celeron® N3350 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009)](https://www.qualcomm.com/products/snapdragon/processors/212) | [Familia i.MX 7](http://aka.ms/iotnxp)     |
|         | [Plataforma N4200 Intel® Pentium® Processor (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [Familia mini de i.MX 8 m y 8 m](http://aka.ms/iotnxp) |
|         | [Intel® Pentium® y Celeron® Processor N3000 Series (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Procesador Intel® Atom® X5-E8000 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Procesador Intel® Atom® X5-Z8350 (Cherry Trail)](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Familia de productos E3800 de Intel® Atom® Processor (bastidor Trail-I)](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Procesador Intel® Pentium® y Celeron® Series N y J (pista de Bahía-M/D)](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

El SoC que decida adoptar dependerá de consideraciones como los requisitos de rendimiento, el perfil de energía, el costo, las opciones de conectividad física, la compatibilidad a largo plazo y las condiciones de funcionamiento.

También necesitará decidir si desea usar una placa o dispositivo fuera del sistema, crear un dispositivo personalizado mediante un sistema de un módulo (SoM) más una placa de transportista personalizada o crear un panel personalizado completo. El costo y el grado de personalización son los factores clave de esta decisión, y ambos suelen aumentar según la personalización.

## <a name="windows-10-iot-core-features-by-processor-family"></a>Características principales de IoT de Windows 10 por familia de procesadores

> [!NOTE]
> En esta lista se tienen en cuenta los procesadores que se encuentran en la versión preliminar pública no comercial.

Para ayudarle a seleccionar la plataforma correcta para el dispositivo, en la tabla siguiente se muestran las características compatibles con la familia de procesadores con Windows 10 IoT Core. Todas las características que se enumeran a continuación se admiten en Windows 10 IoT Core; sin embargo, es posible que algunos SOC no tengan la dirección IP específica incluida en su diseño y se indiquen con "N/A". En tales casos, se puede incorporar una solución de terceros en el diseño para proporcionar la funcionalidad necesaria.  En un número limitado de casos en los que una característica de Windows 10 IoT Core no se implementa en un procesador, la entrada se deja en blanco.

> |    | Intel  |  Qualcomm  | NXP i. MX6 | NXP i. MX7 | NXP i. MX8M | Broadcom |
> |----|--------|------------|-----------|-----------|------------|----------|
> | Audio | x | x | x | x | x | x |
> | GPIO | x | x | x | x | x | x |
> | I2C | x | x | x | x | x | x |
> | Ethernet | x | N/D | x | x | x | x |
> | SPI | x | x | x | x | x | x |
> | Pantalla | x | x | x | x | x | x |
> | UART | x | x | x | x | x | x |
> | USB | x | x | x | x | x | x |
> | PCIe | x | N/D | x | En desarrollo | En desarrollo | N/D |
> |MIPI-CSI | N/D | x | N/D | N/D | N/D | N/D |
> | Gráficos/vídeo | x | x | Software-representado | Software-representado | Software-representado | Software-representado |
> | GPS | N/D | x | N/D | N/D | N/D | N/D |
> | Wi-Fi/BT | N/D | x | N/D | N/D | N/D | N/D |
> | E/s de confianza | N/D | N/D | x | x | x | N/D |
> | Administración de energía del procesador |  | x | x | x | En desarrollo | |
> | TPM | x | x | x | x | x | N/D |
> | Arranque seguro | x | x | En desarrollo | En desarrollo | En desarrollo | |
> | Hibernar | x | | | | | | 
> | PWM | x | N/D | x | x | x | |
> | JTAG | x | N/D | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>Paneles personalizados

Si un dispositivo fuera del estante está en un factor de forma que incluye las opciones de conectividad que funcionan para los escenarios, a menudo será la opción más rentable y rentable.  

Para la mayoría de los usuarios, el desarrollo de un panel personalizado completo tendría sentido cuando se espera que el producto se venda en volúmenes superiores a decenas o incluso cientos de miles de unidades. En el caso de los volúmenes más pequeños, el uso de un SoM y el diseño de una placa de portadora personalizada, en lugar de diseñar un panel completamente nuevo, puede reducir significativamente el costo y el tiempo de comercialización, así como optimizar el desarrollo y la integración de software.

Cada una de las plataformas tiene peculiaridades únicas que requieren atención durante la implementación.  A continuación se muestran algunas sugerencias sobre cómo empezar. Y aunque hay muchas empresas que se compilan en Windows 10 IoT Core, aquí se muestra una lista de algunas que tienen una experiencia probada con Windows 10 IoT Core:

* __[Raspberry PI](#raspberry-pi-derived-custom-design)__
* __[Procesador](#intel-based-custom-design)__
* __[Qualcomm](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*Si es un proveedor de SOM o un ODM y desea agregarlo a la lista siguiente, envíe un correo electrónico a [winiotsomhelp@microsoft.com](mailto:winiotsomhelp@microsoft.com) o edite directamente esta página y envíe una solicitud de incorporación de cambios.*

*Muchas de las compañías que se enumeran aquí son grandes y complejas.  Si tiene problemas para llegar a la persona adecuada, envíe [winiotsomhelp@microsoft.com](mailto:winiotsomhelp@microsoft.com) un correo electrónico y haremos todo lo posible para conectarse a las personas adecuadas.*

### <a name="raspberry-pi-derived-custom-design"></a>**Diseño personalizado derivado de Raspberry PI**

El [elemento 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service) ofrece el servicio de personalización del panel de Raspberry PI para que pueda agregar o quitar opciones de conectividad. Si también necesita personalizar el BSP, puede aprovechar el [código de BSP de código abierto en github](https://github.com/ms-iot/rpi-iotcore).

### <a name="intel-based-custom-design"></a>**Diseño personalizado basado en Intel**

Existe un ecosistema vibrante de [generadores de dispositivos Intel experimentados](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349) para Windows con los que puede trabajar. Un dispositivo Intel diseñado para ejecutar Windows 10 IoT Core tiene un par de diferencias con respecto a los equipos más comunes:

1. Si necesita proporcionar acceso a la API del modo de usuario Plataforma universal de Windows (UWP) a buses simples como I2C, GPIO y SPI, debe asegurarse de que la tabla ACPI en el firmware UEFI contiene entradas adecuadas para RHProxy. Para obtener más información, consulte [acceso al modo de usuario](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) .
2. Debe asegurarse de que el SMBIOS en el firmware contiene información como se indica en el [requisito de licencia OEM](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements).

Si va a crear su propio panel, póngase en contacto con su proveedor de BIOS si necesita instrucciones sobre los cambios de ACPI o SMBIOS.

#### <a name="experienced-partners"></a>*Asociados con experiencia*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech](http://www.advantech.com/) -buy@advantech.tw
* [Kontron](http://www.kontron.com/) -martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### <a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>**Diseño personalizado basado en Qualcomm DragonBoard 410C (APQ8016)**

El BSP binario para DragonBoard 410C (basado en Qualcomm AQP8016 SoC) se puede descargar desde la [red de desarrolladores de Qualcomm](https://developer.qualcomm.com/hardware/dragonboard-410c/software).

El paquete BSP incluye el código fuente para que ACPI permita una simple personalización de hardware que solo requiere cambios de ACPI.  

> [!IMPORTANT] 
> Si necesita más personalizaciones de hardware, como el uso de un panel de visualización MIPI-DSI específico, habilitación del arranque seguro de plataforma, calibración y certificación de RF (por ejemplo, FCC, CE), debe convertirse en un licenciatario de código fuente de Qualcomm BSP o para trabajar con un proveedor que tenga acceso (consulte a continuación los asociados experimentados).

Recomendaciones:

1. Si es posible, trabaje con un proveedor de SoM experimentado para habilitar el diseño personalizado.
2. Si va a crear un panel personalizado, trabaje con un proveedor de SoM o con un proveedor de servicios de personalización de Qualcomm BSP con experiencia, como [Intrinsyc](https://www.intrinsyc.com/) o [Thundersoft](http://www.thundersoft.com/) para la personalización de BSP y la asistencia para el diseño.
3. Si espera tener un volumen muy alto (millones), [póngase en contacto con Qualcomm](https://assets.qualcomm.com/contact-sales-iot.html).

#### <a name="experienced-partners"></a>*Asociados con experiencia*

* [Intrinsyc](https://www.intrinsyc.com/computing-platforms/410-som/) -Mark WALDENBERG (mwaldenberg@intrinsyc.com)
* [Keith & Koep](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/) -contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) -welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) -Sam (saml@tw.ute.com); Perry (perryt@te.ute.com)

### <a name="nxp-preview"></a>**Vista previa de NXP**

La compatibilidad con NXP para Windows 10 IoT Core está en versión preliminar pública. Para obtener más información, el acceso al BSP o para encontrar un asociado de hardware, visite la [Página de NXP SOC](http://aka.ms/iotnxp).

También puede ponerse en contacto con los asociados con los que estamos trabajando:

* Advantech [RSB-4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) -buy@advantech.tw
* Keith & Koep [pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/
) con [Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) -contact@keith-koep.com
* Kontron [SMARC-sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) -Martin Unverdorben (martin.unverdorben@kontron.com)
* Ejecución sólida [Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/ )-Ilya Viten (ilya@solid-run.com)
* Geniatech [SOM-iMX6Q-Q7](https://www.geniatech.com/product/som-imx6q-q7/) & [SOM-iMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike Decker (mike.decker@geniatech.com) o Fang Jijun (Fjj@geniatech.com)
* A través [de VAB-820](https://www.viaembeddedstore.com/shop/boards/vab-820/) -MichaelMichaelFox@via.com.twFox () o dedreamku@via.com.twsueño Ku ()
* Phytec [phyBOARD-i. MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com)


## <a name="other-options"></a>Otras opciones

Si encuentra que todavía desea crear un panel personalizado, hemos proporcionado algunas sugerencias de los fabricantes siguientes que pueden ayudarle con los esquemas y el diseño de una placa.

* [Todas las PCB](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [PCB DE JLC](https://jlcpcb.com/)
* [PCB de Myro](http://www.myropcb.com/)
* [OSH PARK](https://oshpark.com/)
* [Seeed Studio](https://www.seeedstudio.com/)
