---
title: Guía de instalación de rayo
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo cambiar el controlador del controlador predeterminado del controlador relámpago DMAP en un dispositivo.
keywords: Windows iot, relámpago, el programa de instalación, el programa de instalación de rayos, Windows Device Portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514700"
---
# <a name="lightning-setup-guide"></a>Guía de instalación de rayo

Esta guía le guiará por los pasos necesarios para cambiar el controlador del controlador predeterminado para el controlador de acceso asignado (DMAP) de memoria directa relámpago en un dispositivo Windows IoT Core. Esto permitirá que el uso de las aplicaciones habilitadas por el rayo en ese dispositivo.

## <a name="change-the-default-controller-driver"></a>Cambiar el controlador del controlador predeterminado

Queremos abrir la Windows Device Portal.

1. Busque la dirección IP del dispositivo, ya sea mediante la aplicación de panel de Windows 10 IoT Core o la placa a un monitor de enlace.

2. Desde el equipo local, abra la página web de Portal de dispositivos de Windows escribiendo esta http://{BoardIPAddress}:8080/ dirección en el explorador web.
   ![Portal de dispositivos de Windows](../media/LightningSetup/dmap1.png)

3. La página de Portal de dispositivos de Windows debe pedir las credenciales. El nombre de usuario predeterminado es `Administrator` y la contraseña es `p@ssw0rd` tenga en cuenta que después de escribir el nombre de usuario y la contraseña, el Portal le preguntará si debe cambiar la contraseña. Siempre es una buena práctica para cambiarlo.
   ![Credenciales de Portal de dispositivos de Windows](../media/LightningSetup/dmap2.png)

4. Haga clic en los dispositivos en el menú de navegación para abrir la página dispositivos ![página dispositivos](../media/LightningSetup/dmap3.png)

5. La página de dispositivos enumera los controladores disponibles. De forma predeterminada, el controlador de bandeja de entrada se establece al actual.

6. Cambiar al controlador relámpago eligiendo el controlador de asignar memoria directa desde el menú desplegable y haga clic en el botón Actualizar controlador<br/>
   ![Seleccione el controlador asignado memoria directa](../media/LightningSetup/dmap4.png)

7. Espere hasta que la página le permite saber cuando se completa la instalación del controlador.
   ![Instalación del controlador completa](../media/LightningSetup/dmap5.png)

8. Si se requiere un reinicio, la página le permitirá saber también. Puede reiniciar mediante el botón de reinicio en la parte superior de la página.

9. Ahora está listo para crear y usar aplicaciones hacen uso del controlador asignado en memoria directa relámpago.
