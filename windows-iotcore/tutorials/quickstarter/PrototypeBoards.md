---
title: Prototipos de placas de sugerido
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: Obtenga información acerca de los paneles de prototipo sugerido para Windows 10 IoT.
keywords: Windows iot, los dispositivos de desarrollo, paneles, Raspberry Pi 2, Raspberry Pi 3, Minnowboard Max, Dragonboard
ms.openlocfilehash: fc13f44a183e79a4c3f7381c3a12d8b5dcba8895
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514251"
---
# <a name="suggested-prototype-boards"></a>Prototipos de placas de sugerido

## <a name="windows-10-iot-core-development-devices"></a>Dispositivos de desarrollo de Windows 10 IoT Core
A continuación encontrará los paneles que le sugerimos que le ayudarán a empezar a trabajar con Windows 10 IoT Core. Estas placas ofrecen una imagen de actualización de Flash completa (FFU), lo que agiliza el desarrollo de prototipos con una imagen listos para usar y que el proceso de intermitencia en Windows 10 IoT Core pan comido.

> [!IMPORTANT]
> Debe crear sus propias imágenes y no usar las imágenes proporcionadas a continuación si planea comercializar su dispositivo.

> [!NOTE]
> El dispositivo Raspberry Pi 3B + ha limitado la compatibilidad con Windows 10 IoT Core. Consulte la [notas de la versión](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/insider/17744) para obtener más información. Para una experiencia más completa de Windows 10 IoT Core, use un dispositivo de Up2 Board o NXP 3B, DragonBoard, Raspberry Pi. 


| Paneles | Más información | Vínculo FFU | Cómo configurar | Comenzar |
|-----------|----------|---------|---------|---------|---------|-------|
| [AAEON copia al cuadrado](https://up-board.org/upsquared/specifications/) | [Seguridad de sitio del panel](https://up-shop.org/28-up-squared) | [Descargar FFU](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) | [eMMC (para la seguridad al cuadrado, Intel)](DeviceSetup.md#flashing-with-emmc-for-up-squared-other-intel-devices) | [Commercialize](https://up-shop.org/home/270-up-squared.html) | 
| [DragonBoard 410c](https://developer.qualcomm.com/hardware/dragonboard-410c) | [Sitio de flecha](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | [Descargar FFU](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Panel IoT](DeviceSetup.md#using-the-iot-dashboard-dragonboard-410c),<br>[eMMC (para c de 410, Qualcomm DragonBoard)](DeviceSetup.md#flashing-with-emmc-for-up-squared-other-intel-devices) | [Commercialize](https://www.arrow.com/en/products/dragonboard410c/arrow-development-tools) | 
| [MinnowBoard Turbot](https://minnowboard.org) | [Sitio Minnowboard](https://minnowboard.org/get-a-board) | [Descargar FFU](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Panel de IoT](DeviceSetup.md#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | N/D |
| [NXP i.MX 6](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [Sitio NXP](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-6-processors:IMX6X_SERIES) | [Descargar FFU](https://github.com/ms-iot/imx-iotcore) | [Panel de IoT](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Commercialize](https://www.solid-run.com/nxp-family/hummingboard/imx6-win-10-iot-core/) | 
| [NXP i.MX 7](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [Sitio NXP](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-7-processors:IMX7-SERIES) | [Descargar FFU](https://github.com/ms-iot/imx-iotcore) | [Panel de IoT](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Commercialize](https://www.compulab.com/products/iot-gateways/iot-gate-imx7-nxp-i-mx-7-internet-of-things-gateway/) | 
| [NXP i.MX 8M / 8M Mini](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [Sitio NXP](https://www.nxp.com/products/processors-and-microcontrollers/arm-based-processors-and-mcus/i.mx-applications-processors/i.mx-8-processors:IMX8-SERIES) | [Descargar FFU](https://github.com/ms-iot/imx-iotcore) | [Panel de IoT](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/devicesetup#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Kit de desarrollo de 8M](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-applications-processor:MCIMX8M-EVK) o [Kit de desarrollo Mini de 8 M](https://www.nxp.com/support/developer-resources/software-development-tools/i.mx-developer-resources/evaluation-kit-for-the-i.mx-8m-mini-applications-processor:8MMINILPD4-EVK) |
| [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/)<br> (1.2 no admitidas) | [Sitio de raspberry Pi](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/) | [Descargar FFU](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Panel de IoT (Raspberry Pi, MinnowBoard)](DeviceSetup.md#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Kit de Adafruit](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/adafruitkit) | 
| [Raspberry Pi 3B](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/)<br> (3B + es una versión preliminar técnica no admitida) | [Sitio de raspberry Pi](https://www.raspberrypi.org/products/raspberry-pi-3-model-b/) | [Descargar FFU](https://www.microsoft.com/en-us/software-download/windows10IoTCore#!) | [Panel de IoT](DeviceSetup.md#using-the-iot-dashboard-raspberry-pi-minnowboard-nxp) | [Kit de Adafruit](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/adafruitkit) |
