---
title: Creación de un controlador universal
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a crear controladores universales para habilitar la creación de paquetes de un solo controlador en todos los dispositivos.
keywords: Windows IOT, controladores universales, controladores, Windows 10, UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169583"
---
# <a name="universal-driver-creation"></a>Creación de un controlador universal

Este documento le guiará a través de la creación de controladores universales para el dispositivo de IoT Core.

Los controladores universales le permiten crear un único paquete de controladores que se ejecuta en varios tipos de dispositivos que ejecutan las ediciones basadas en UWP de Windows 10, incluido IoT Core.

Este paquete de controladores contiene un archivo INF universal y varios archivos binarios. Los requisitos para cada uno de ellos son los siguientes:
- Los archivos INF universales solo pueden usar [el subconjunto de la sintaxis de INF que se admite en las ediciones basadas en UWP de Windows](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file). Mientras escribe el archivo INF, use la [herramienta InfVerif](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif) para comprobar que el archivo se adhiere a esa sintaxis.

- los archivos binarios solo pueden usar interfaces de controlador de dispositivo compatibles con las ediciones basadas en UWP de Windows 10 (marcadas como universal en las páginas de referencia de la documentación): [KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index), [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)o el modelo de controlador de Windows (WDM). También pueden llamar a las API incluidas en el subconjunto OneCore. Use la [herramienta ApiValidator](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers) para comprobar que las API que llaman a los archivos binarios son válidas.

Para obtener información sobre cómo **crear un paquete de controladores en Visual Studio**, visite [creación de un paquete de controladores](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package) .

Si quiere **obtener un ejemplo para ayudarle a crear un controlador universal en IOT Core**, visite nuestro [ejemplo de controlador universal](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab) .

## <a name="additional-universal-driver-resources"></a>Recursos adicionales del controlador universal

1. Para obtener más información sobre los **principios de diseño** y los **procedimientos recomendados** para desarrollar un paquete de controladores universales, visite [Introducción con controladores universales](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers) .

2. Para obtener ayuda para depurar **el controlador universal**, visite depurar [un controlador universal de Windows](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver).

