---
title: Glosario de Windows IoT
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre los distintos términos relacionados con Windows IoT Core en nuestra documentación.
keywords: windows iot, glosario, términos, terminología, definiciones
ms.openlocfilehash: 109ddbb9e9c6c163fdc5a8d0219b89dde3a2bbf2
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918429"
---
# <a name="glossary-for-windows-iot"></a>Glosario de Windows IoT

**Interfaz avanzada de configuración y energía (ACPI)** ACPI es una especificación abierta del sector desarrollada de forma conjunta por Hewlett-Packard, Intel, Microsoft, Phoenix y Toshiba.  ACPI establece interfaces estándar del sector que permiten la configuración dirigida al sistema operativo, la administración de energía y la administración térmica de plataformas de dispositivos móviles, de escritorio y servidor.

**Sistema básico de entrada y salida (BIOS)** El conjunto de rutinas de software fundamentales que prueban el hardware al inicio, inician el sistema operativo y permiten la transferencia de datos entre dispositivos de hardware.

**Comercializar** El desarrollo y la fabricación de un dispositivo con la intención de ofrecerlo comercialmente al público.

**Entrada y salida de uso general (GPIO)** GPIO es un pin genérico en un circuito integrado, cuyo comportamiento, incluido si se trata de un pin de entrada o salida, lo puede controlar el usuario en tiempo de ejecución.  Puede usar el espacio de nombres Windows.Devices.Gpio en la aplicación para manipular los pines GPIO de la placa.

**Con periféricos** Windows IoT Core pueden estar en modo con periféricos o sin periféricos. La diferencia entre estos dos modos es la presencia o ausencia de cualquier forma de interfaz de usuario. De forma predeterminada, Windows 10 IoT Core está en modo con periféricos y muestra información del sistema, como el nombre del equipo y la dirección IP.

**Sin periféricos** En este modo, no hay ninguna pila de interfaz de usuario disponible y las aplicaciones no son interactivas. Las aplicaciones en modo "sin periféricos" se pueden considerar servicios.

**Circuitos inter-integrados (I2C)** Sencillos buses bidireccionales de datos en serie (SDA) y reloj en serie (SCL) de dos cables para el control de circuitos inter-integrados.  Puede usar el espacio de nombres Windows.Devices.I2c en la aplicación para comunicarse con un dispositivo a través de I2C.

**Diodo emisor de luz (LED)** Un LED es una fuente de luz semiconductora de dos electrodos. Es un diodo de unión PN que emite luz cuando se activa.

**Marco de controlador en modo kernel (KMDF) de Microsoft Windows** Marco de desarrollo de Microsoft que permite a los desarrolladores de controladores exponer la funcionalidad del controlador en modo kernel, lo que permite al controlador acceder a la memoria y el hardware del sistema.

**Prototipo** El desarrollo de una versión más básica de una versión final del dispositivo que se pretende crear. Se recomienda encarecidamente la creación de prototipos, cuando no es un paso obligatorio del proceso de fabricación. Esta fase se debe usar para probar todas las características que espera usar para la versión final del dispositivo.

**Bus de interfaz periférica en serie (SPI)** El bus SPI es una especificación de interfaz de comunicación en serie sincrónica que se usa para la comunicación de corta distancia, principalmente en sistemas insertados.  Puede usar el espacio de nombres Windows.Devices.Spi en la aplicación para comunicarse con un dispositivo a través de SPI.

**Transmisor/Receptor asincrónico universal (UART)** UART es un elemento de hardware informático que toma bytes de datos y transmite los bits individuales en serie.

**Plataforma universal de Windows (UWP)** La Plataforma universal de Windows proporciona una capa de API básica garantizada en todos los dispositivos.  Puede crear un único paquete de la aplicación para instalarlo en una amplia gama de dispositivos.

**Máquina virtual (VM)**<br/>
Software que actúa como interfaz entre el código binario del compilador y el microprocesador que realmente ejecuta las instrucciones del programa.  En Windows, puede usar el Administrador de Hyper-V para administrar máquinas virtuales.

**Consola del dispositivo de Windows (Devcon.exe)** DevCon (Devcon.exe), la consola del dispositivo, es una herramienta de línea de comandos que muestra información detallada sobre los dispositivos de equipos que ejecutan Windows. Puede usar DevCon para habilitar, deshabilitar, instalar, configurar y quitar dispositivos.  Esta herramienta se usa principalmente para instalar y quitar controladores de forma manual.
