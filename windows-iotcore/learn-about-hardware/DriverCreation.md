---
title: Creación de controlador universal
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear controladores Universal para habilitar la creación de paquetes de controlador único en todos los dispositivos.
keywords: Windows iot, universales controladores, controladores, Windows 10, UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514264"
---
# <a name="universal-driver-creation"></a>Creación de controlador universal

Este documento le guiará a través de la creación de controladores Universal para el dispositivo de IoT Core.

Controladores universales permiten crear un paquete de controlador único que se ejecuta a través de varios tipos de dispositivos que ejecutan las ediciones basadas en UWP de Windows 10, incluidos IoT Core.

Este paquete de controladores contiene un archivo INF Universal y varios binarios. Los requisitos para cada uno de ellos son los siguientes:
- Solo pueden usar archivos INF universal [el subconjunto de sintaxis INF admitidos en las ediciones basadas en UWP de Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file). Al escribir el archivo INF, utilice el [InfVerif herramienta](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) para comprobar que el archivo se ajusta a esa sintaxis.

- los archivos binarios solo pueden usar interfaces del controlador de dispositivo compatibles con las ediciones basadas en UWP de Windows 10 (marcados como Universal en las páginas de documentación de referencia): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2), o el modelo de controladores de Windows (WDM). Solo pueden llamar a API que se incluyen en el subconjunto de OneCore. Use la [ApiValidator herramienta](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) para comprobar que se llame las API de los archivos binarios son válidos.

Para obtener información sobre cómo **crear un paquete de controladores en Visual Studio**, visite [crear un paquete de controladores](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)

Si desea que **muestra un ejemplo para ayudarle a crear un controlador Universal en IoT Core**, visite nuestro [ejemplo de controlador Universal](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)

## <a name="additional-universal-driver-resources"></a>Recursos adicionales del controlador Universal

1. Para obtener más detalles sobre **principios de diseño** y **procedimientos recomendados** al desarrollar un paquete de controladores universales, visite [Introducción a los controladores Universal](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)

2. Para obtener ayuda **depuración su controlador Universal**, visite [depurar un controlador de Windows Universal](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).

