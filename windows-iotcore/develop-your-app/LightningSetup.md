---
title: Guía de instalación de Lightning
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo cambiar el controlador de controlador predeterminado para el controlador Lightning DMAP en un dispositivo.
keywords: Windows IOT, Lightning, instalación, Lightning, Windows Device portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167869"
---
# <a name="lightning-setup-guide"></a>Guía de instalación de Lightning

Esta guía le guiará a través de los pasos necesarios para cambiar el controlador de controlador predeterminado por el controlador de acceso directo a memoria asignado (DMAP) en un dispositivo Windows IoT Core. Esto permitirá el uso de aplicaciones con un relámpago en ese dispositivo.

## <a name="change-the-default-controller-driver"></a>Cambiar el controlador de controlador predeterminado

Le interesaremos abrir el portal de dispositivos de Windows.

1. Busque la dirección IP del dispositivo, ya sea mediante el uso de la aplicación Windows 10 IoT Core Dashboard o enlazando el panel a un monitor.

2. En el equipo local, abra la página web del portal de dispositivos de Windows. para ello, escriba esta dirección http://{BoardIPAddress}: 8080/en el explorador Web.
   ![Portal de dispositivos Windows](../media/LightningSetup/dmap1.png)

3. La página del portal de dispositivos de Windows debe solicitar sus credenciales. El nombre de usuario `Administrator` predeterminado es y `p@ssw0rd` la contraseña es Nota, después de escribir el nombre de usuario y la contraseña, el portal le preguntará si necesita cambiar la contraseña. Siempre es una buena práctica cambiarla.
   ![Credenciales del portal de dispositivos Windows](../media/LightningSetup/dmap2.png)

4. Haga clic en dispositivos en el menú de navegación para abrir la ![página dispositivos página dispositivos.](../media/LightningSetup/dmap3.png)

5. La página dispositivos muestra los controladores de controlador disponibles. De forma predeterminada, el controlador de bandeja de entrada se establece en actual.

6. Cambie al controlador de Lightning; para ello, elija el controlador asignación de memoria directa en el menú desplegable y haga clic en el botón Actualizar controlador.<br/>
   ![Seleccionar controlador asignado a memoria directa](../media/LightningSetup/dmap4.png)

7. Espere hasta que la página le permita saber cuándo se ha completado la instalación del controlador.
   ![Instalación de controladores completada](../media/LightningSetup/dmap5.png)

8. Si se requiere un reinicio, la página le indicará también. Puede reiniciar con el botón reiniciar en la parte superior de la página.

9. Ahora está listo para crear y usar aplicaciones que usan el controlador asignado a la memoria de Lightning Direct.
