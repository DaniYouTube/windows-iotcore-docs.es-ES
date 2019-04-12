---
title: Glosario de Windows IoT
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre los distintos términos de Windows IoT Core a través de nuestra documentación.
keywords: Windows iot, glosario, términos, definiciones, terminología
ms.openlocfilehash: 155de380459cbb74642352ff2a2ff718ebfe1ed7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514955"
---
# <a name="glossary-for-windows-iot"></a>Glosario de Windows IoT

**Advanced Power Interface (ACPI) y configuración** ACPI (configuración avanzada y Power Interface) es una especificación abierta desarrollada conjuntamente por Hewlett-Packard, Intel, Microsoft, Phoenix y Toshiba.  ACPI establece interfaces estándar del sector Habilitar configuración dirigido al sistema operativo, la administración de energía y administración térmica de plataformas móviles, escritorio y servidor.

**Sistema básico de entrada/salida (BIOS)** el conjunto de rutinas de software fundamentales que prueban el hardware en el inicio, inicie el sistema operativo y permiten la transferencia de datos entre dispositivos de hardware.

**Comercializar** vías de desarrollo y la fabricación de un dispositivo con la intención de colocar comercialmente horizontal para el público.

**Entrada/salida de propósito general (GPIO)** GPIO es un pin genérico en un circuito integrado, cuyo comportamiento, incluso si se trata de un pin de entrada o salido, puede controlarse por el usuario en tiempo de ejecución.  Puede usar el espacio de nombres en la aplicación para manipular el GPIO se ancla en la placa de Windows.Devices.Gpio.

**Puntas** Windows IoT Core pueden estar en modo con cabezal o sin periféricos. La diferencia entre estos dos modos es la presencia o ausencia de cualquier forma de interfaz de usuario. De forma predeterminada, Windows 10 IoT Core está en modo con cabezal y muestra información del sistema, como el nombre del equipo y la dirección IP.

**Equipos sin periféricos** en modo "desatendido", no hay ninguna pila de la interfaz de usuario y las aplicaciones no son interactivas. Las aplicaciones de modo "desatendido" pueden considerarse como servicios.

**Entre integrado circuitos (I2C)** datos en Simple bidireccional dos cables serie (SDA) y buses de serie de reloj (SCL) para integran entre control circuito.  Puede usar el espacio de nombres Windows.Devices.I2c en su aplicación comunicarse con un dispositivo a través de I2C.

**Diodos emisores de – luz (LED)** un LED es una fuente de luz semiconductor responsable de dos. Es un diodos pn-junction, que emite luz cuando activa.

**Modo Driver Framework (KMDF) de Microsoft Windows Kernel** marco de desarrollo de Microsoft que permite a los desarrolladores de controladores exponer la funcionalidad de controlador en modo de kernel, lo que proporciona el acceso de controlador a la memoria del sistema y de hardware.

**Prototipo** desarrollando una versión sin procesar más de una versión final de un dispositivo que usted desea crear. Creación de prototipos se recomienda encarecidamente, si no es un paso obligatorio en el proceso de fabricación. Esta fase debe usarse para probar todas las características que usted desea usar para la versión final de su dispositivo.

**Interfaz de Bus periféricos serie (SPI)** bus SPI es una especificación de interfaz de comunicación en serie sincrónica utilizada para la comunicación de corta distancia, principalmente en sistemas incrustados.  Puede usar el espacio de nombres Windows.Devices.Spi en su aplicación comunicarse con un dispositivo a través de SPI.

**Receptor/transmisor asincrónico universal (UART)** UART es una pieza de hardware del equipo que toma los bytes de datos y transmite los bits individuales en serie.

**Plataforma universal de Windows (UWP)** la plataforma Universal de Windows proporciona una capa de API garantizada de principal en todos los dispositivos.  Puede crear un paquete de aplicación única que puede instalarse en una amplia gama de dispositivos.

**Máquina virtual (VM)**<br/>
Software que actúa como interfaz entre código binario del compilador y el microprocesador que realmente realiza las instrucciones del programa.  En Windows, puede usar el Administrador de Hyper-V para administrar máquinas virtuales.

**Consola del dispositivo de Windows (Devcon.exe)** DevCon (Devcon.exe), la consola del dispositivo, es una herramienta de línea de comandos que muestra información detallada acerca de los dispositivos en equipos que ejecutan Windows. Puede utilizar DevCon para habilitar, deshabilitar, instalar, configurar y quitar dispositivos.  Esta herramienta se usa principalmente para instalar y quitar controladores manualmente.
