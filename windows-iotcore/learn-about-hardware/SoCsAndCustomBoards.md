---
title: QUALCOMM y paneles personalizados para Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las características de hardware para una variedad de paneles sugeridos y los dispositivos de la Comunidad.
keywords: Windows iot, dispositivos de desarrollo, paneles, SOC, SOM, sistema de chips, 2 de Raspberry Pi, Raspberry Pi 3, Minnowboard Max, DragonBoard
ms.openlocfilehash: b4225937fef1338182c77baa0fd288b7ed597d45
ms.sourcegitcommit: 3eacb968296e79e7e981fdc2a6f7f4f69c0920d1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65040194"
---
# <a name="socs-and-custom-boards"></a>QUALCOMM y paneles personalizados

## <a name="microsoft-enabled-socs"></a>QUALCOMM habilitada por Microsoft

Microsoft trabaja junto con Broadcom, Intel, NXP y Qualcomm para comprobar la compatibilidad con Windows 10 IoT Core en el sistema de varios proveedores en un chip (Qualcomm). Se utiliza estos Qualcomm con tecnología de IoT Core en cientos de dispositivos diferentes que puede usar para crear prototipos y comercializar sus ideas.

| Broadcom | Intel | Qualcomm | NXP |
|----------|-------|----------|-----|
| BCM2837 | [Procesador Intel® Atom E3900 series (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                | [Snapdragon 410 (APQ8016)](https://www.qualcomm.com/products/snapdragon/processors/410) | [i.MX 6 familia](http://aka.ms/iotnxp) |
| BCM2836 | [Procesador Intel® Celeron® N3350 (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                                    | [Snapdragon 212 (APQ8009)](https://www.qualcomm.com/products/snapdragon/processors/212) | [i.MX 7 familia](http://aka.ms/iotnxp)     |
|         | [Plataforma de procesador N4200 Intel® Pentium® (Apollo Lake)](https://ark.intel.com/products/codename/80644/#@embedded)                           |                                                                                         | [Familia de i.MX de 8 M](http://aka.ms/iotnxp) |
|         | [Procesadores Intel® Pentium® y Celeron® procesador N3000 serie (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                    |                                                                                         |      |
|         | [Procesador de Atom de Intel® x5 E8000 (Braswell)](http://ark.intel.com/products/codename/66094/#@embedded)                                        |                                                                                         |  |
|         | [Procesador de Atom de Intel® x5 Z8350 (Trail Cherry)](https://ark.intel.com/products/93361/Intel-Atom-x5-Z8350-Processor-2M-Cache-up-to-1_92-GHz) |                                                                                         |     |
|         | [Familia de productos de E3800 de procesador Intel® Atom (rastro de la bahía-I)](http://ark.intel.com/products/codename/55844/#@Embedded)                     |                                                                                         |  |
|         | [Procesadores Intel® Pentium® y procesador Celeron® N y serie J (Bay traza-M/D)](http://ark.intel.com/products/codename/55844/)                     |                                                                                         |       |

El SoC que decide adoptar dependerá de las consideraciones como requisitos de rendimiento de perfil de energía, costo, opciones de conectividad física, cuánto tiempo término y la compatibilidad con las condiciones de funcionamiento.

Podrá también necesita para decidir si desea usar un dispositivo, o un panel listos para usar un dispositivo personalizado mediante un sistema en un módulo (SoM) además de un panel personalizado de transportista de compilación, o crear un panel personalizado completo. Costo y el grado de personalización son los factores clave en esta decisión, con ambos generalmente aumentando a medida que personaliza aún más.

## <a name="windows-10-iot-core-features-by-processor-family"></a>Características de Windows 10 IoT Core por familia de procesadores

> [!NOTE]
> Esta lista tiene en procesadores de consideración que se encuentran en versión preliminar pública de no comercial.

Para ayudarle a seleccionar la plataforma correcta para el dispositivo, en la tabla siguiente muestra las características que son compatibles con la familia de procesadores con Windows 10 IoT Core. Todas las características enumeradas a continuación se admiten en Windows 10 IoT Core, sin embargo, algunos QUALCOMM no puede tener la dirección IP específica incluida en su diseño y, por ejemplo, se indican con "N/D". En tales casos, una solución de terceros 3rd puede incorporar en el diseño para ofrecer la funcionalidad necesaria.  En un número limitado de los casos donde una característica de Windows 10 IoT Core no está implementada en un procesador, la entrada se deja en blanco.

> |    | Intel  |  Qualcomm  | NXP i.MX6 | NXP i.MX7 | NXP i.MX8M | Broadcom |
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
> | Gráficos y vídeo | x | x | Representados de software | Representados de software | Representados de software | Representados de software |
> | GPS | N/D | x | N/D | N/D | N/D | N/D |
> | Wi-Fi/BT | N/D | x | N/D | N/D | N/D | N/D |
> | E/S de confianza | N/D | N/D | x | x | x | N/D |
> | Administración de energía del procesador |  | x | x | x | En desarrollo | |
> | TPM | x | x | x | x | x | N/D |
> | Arranque seguro | x | x | En desarrollo | En desarrollo | En desarrollo | |
> | Hibernar | x | | | | | | 
> | PWM | x | N/D | x | x | x | |
> | JTAG | x | N/D | x | x | x | |
> | eMMC | x | x | x | x | x | |
> | SDHC | x | x | x | x | x | x |

## <a name="customized-boards"></a>Paneles personalizados

Si es un dispositivo listos para usar en un factor de forma que incluya las opciones de conectividad que funcionan para los escenarios, que a menudo será la elección más y tiempo-rentable.  

Para la mayoría de las personas, desarrollo de un panel personalizado completo tendría sentido cuando se espera que el producto se vende en volúmenes de mayor que decenas o incluso cientos, miles de unidades. Para volúmenes menores, con un ámbito de administración y diseñar un panel personalizado de transportista, en lugar de diseñar un panel completamente nuevo, pueden reducir significativamente el costo y tiempo de comercialización, así como optimizar el desarrollo de software e integración.

Cada una de las plataformas tiene peculiaridades únicos que necesitan atención durante la implementación.  A continuación se muestran algunas sugerencias sobre cómo empezar a trabajar. Y aunque hay muchas de las empresas que crean en Windows 10 IoT Core, esta es una lista de algunas que han demostrado ser experiencia con Windows 10 IoT Core:

* __[Raspberry Pi](#raspberry-pi-derived-custom-design)__
* __[Intel](#intel-based-custom-design)__
* __[QUALCOMM](#qualcomm-dragonboard-410c-apq8016-based-custom-design)__
* __[NXP](#nxp-preview)__

*Si es un proveedor de SoM o un ODM y le gustaría agregar a la siguiente lista, envíe un correo electrónico a [ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com) o directamente editar esta página y enviar una solicitud de incorporación de cambios.*

*Muchas compañías enumeradas aquí son grandes y complejas.  Si tiene problemas para conectarse con la persona adecuada, envíe un correo electrónico [ winiotsomhelp@microsoft.com ](mailto:winiotsomhelp@microsoft.com) y haremos todo lo posible para conectarse a las personas adecuadas.*

### <a name="raspberry-pi-derived-custom-design"></a>**Raspberry Pi derivada de diseño personalizado**

[Elemento 14](https://www.element14.com/community/docs/DOC-76955/l/raspberry-pi-customization-service) ofertas de servicio de personalización para Raspberry Pi para que pueda agregar o quitar opciones de conectividad del panel. Si también tiene que realizar personalizaciones en el BSP, puede aprovechar la [Abrir origen BSP código en Github](https://github.com/ms-iot/rpi-iotcore).

### <a name="intel-based-custom-design"></a>**Diseño personalizado basados en Intel**

Hay un vibrante ecosistema de [experimentado los generadores de dispositivo Intel](https://solutionsdirectory.intel.com/solutions-directory/processors/278/processors/309/processors/402/processors/782/processors/788/processors/1103/processors/1107/processors/1110/processors/1175/processors/1344/processors/1348/processors/1349) para Windows puede trabajar con. Un dispositivo Intel diseñado para ejecutarse en Windows 10 IoT Core tiene un par de diferencias con respecto a los equipos más comunes:

1. Si tiene que proporcionar acceso de API de plataforma Universal de Windows (UWP) de modo de usuario a buses simple como GPIO, I2C y el SPI, tiene que realizar seguro de que la tabla ACPI en el firmware UEFI contiene las entradas adecuadas para RHProxy. Consulte [acceso en modo usuario](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access) para obtener más información.
2. Debe asegurarse de que el SMBIOS en el firmware contiene información como se muestra en [requisito de licencia OEM](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/oemlicenserequirements).

Si va a compilar su propio panel, póngase en contacto con el proveedor del BIOS si necesita instrucciones sobre cómo los cambios ACPI o SMBIOS.

#### <a name="experienced-partners"></a>*Partners con experiencia*

* [Aaeon](http://www.aaeon.com/en/)
* [Advantech](http://www.advantech.com/) - buy@advantech.tw
* [Kontron](http://www.kontron.com/) - martin.unverdorben@kontron.com
* [Nexcom](http://www.nexcom.com/)

### <a name="qualcomm-dragonboard-410c-apq8016-based-custom-design"></a>**QUALCOMM DragonBoard 410c (APQ8016)-el diseño personalizado basado en**

BSP binario para DragonBoard c de 410 (basado en SoC de Qualcomm AQP8016) puede descargarse desde [Qualcomm Developer Network](https://developer.qualcomm.com/hardware/dragonboard-410c/software).

El paquete BSP incluye el código fuente de ACPI permitir las personalizaciones de hardware simple que solo se requieren cambios ACPI.  

> [!IMPORTANT] 
> Si necesita personalizaciones adicionales de hardware, como el uso de una específica MIPI-DSI Mostrar panel, lo que permite el arranque seguro de plataforma, calibración de RF y certificación (p ej. FCC, CE), necesita estará el Licenciatario un código de origen de Qualcomm BSP o para trabajar con un proveedor que tiene acceso (vea partners con experiencia a continuación).

Recomendaciones:

1. Si es posible, trabajar con un proveedor de SoM experimentado para habilitar el diseño personalizado.
2. Si va a crear un panel personalizado, trabajar con un proveedor de SoM o un proveedor de servicios de personalización de Qualcomm BSP experimentado, tales como [conocemos](https://www.intrinsyc.com/) o [Thundersoft](http://www.thundersoft.com/) para obtener ayuda de personalización y diseño BSP.
3. Si piensa tener un volumen muy elevado (varios millones), [póngase en contacto con Qualcomm](https://assets.qualcomm.com/contact-sales-iot.html).

#### <a name="experienced-partners"></a>*Partners con experiencia*

* [Intrinsyc](https://www.intrinsyc.com/computing-platforms/410-som/) - Mark Waldenberg (mwaldenberg@intrinsyc.com)
* [Keith & Koep](https://keith-koep.com/en/products/products-som/myon-1-features-snapdragon-410/) - contact@keith-koep.com
* [Reycom](http://www.reycom.swiss/en/home-swiss.html) - welcome@reycom.swiss
* [Unitech](http://ute.com/products_info.php?pc1=4&pc2=461&rbu=0&pid=2395) -Sam (saml@tw.ute.com); Perry (perryt@te.ute.com)

### <a name="nxp-preview"></a>**Vista previa NXP**

NXP compatibilidad con Windows 10 IoT Core está en versión preliminar pública. Para obtener más información, el acceso a la BSP, o busque un asociado de hardware, vaya a la [NXP SoC página](http://aka.ms/iotnxp).

Puede ponerse en horizontal a los socios comerciales que estamos trabajando con:

* Advantech [RSB 4411](http://www.advantech.com/products/single_board_computer/rsb-4411/mod_d3901250-b0a0-4a5f-9762-b26fa0c36858) - buy@advantech.tw
* Keith & Koep [pConXS](https://keith-koep.com/de/produkte/produkte-baseboards/pconxs-baseboard-vollausstattung-technische-daten/) con [Trizeps VII](https://keith-koep.com/de/produkte/produkte-trizeps/trizeps-vii-technische-daten-imx6/) - contact@keith-koep.com
* Kontron [SMARC sAMX6i](https://www.kontron.com/products/boards-and-standard-form-factors/smarc/smarc-samx6i.html) -Martin Unverdorben (martin.unverdorben@kontron.com)
* Ejecución sólido [Hummingboard Edge](https://www.solid-run.com/imx6-win-10-iot-core/ )-Ilya Viten (ilya@solid-run.com)
* Geniatech [SoM-iMX6Q-P7](https://www.geniatech.com/product/som-imx6q-q7/) & [SoM iMX7D](https://www.geniatech.com/product/som-imx7d/) -Mike Decker (mike.decker@geniatech.com) o Fang Jijun (Fjj@geniatech.com)
* A través de [VAB 820](https://www.viaembeddedstore.com/shop/boards/vab-820/) -Michael Fox (MichaelFox@via.com.tw) o soñar Ku (dreamku@via.com.tw)
* Phytec [phyBOARD i.MX7](https://phytec.com/products/single-board-computers/phyboard-i.mx7/) -Brad Dodson (sales@phytec.com)


## <a name="other-options"></a>Otras opciones

Si encuentra que todavía le gustaría crear un panel personalizado, se proporcionan algunas sugerencias de los fabricantes a continuación que pueden ayudarle con esquemas y el diseño de un panel.

* [Todos los PCB](http://www.allpcb.com/)
* [Geppetto/Gumstix](https://www.gumstix.com/geppetto/)
* [JLC PCB](https://jlcpcb.com/)
* [Myro PCB](http://www.myropcb.com/)
* [OSH PARK](https://oshpark.com/)
* [seeed studio](https://www.seeedstudio.com/)
