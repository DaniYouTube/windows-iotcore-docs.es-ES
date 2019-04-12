---
title: Impresora de red 3D con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: Obtenga información sobre cómo activar el dispositivo Windows 10 IoT Core en un servidor de impresión y conectarse a la impresora en 3D.
keywords: Windows iot 3D, impresión en 3D, impresión, servidor de impresora de red 3D
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514288"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>Impresora de red 3D con Windows 10 IoT Core

Activar el dispositivo Windows 10 IoT Core en un servidor de impresión y conectarse a la impresora en 3D. Podrá obtener acceso a la impresora de forma inalámbrica desde otros dispositivos.

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1. Instalación de Windows 10 IoT Core en el dispositivo
___
Antes de empezar, necesitará:

* Un panel con la versión más reciente de Windows 10 IoT Core Insider Preview instalado. Siga el [Guía de introducción](https://developer.microsoft.com/en-us/windows/iot/getstarted) para obtener la aplicación de panel de IoT e instalar Windows 10 IoT Core.
* Una impresora 3D compatible con nuestra aplicación impresora de red 3D:

    * Lulzbot Taz 6
    * Makergear M2
    * Printrbot Play, además y Simple
    * Prusa i3 Mk2
    * Ultimaker Original y Original +
    * Ultimaker 2 y 2 +
    * Ultimaker 2 extendido y extendidos +
    * CraftBot 2
    * CraftBot PLUS
    * LulzBot Mini
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2. Conecte la impresora 3D al dispositivo
___
* Complemento la impresora a la de Windows 10 IoT Core 3D del panel mediante el cable USB.

    ![Conectar la impresora en 3D con el dispositivo](../media/3DPrintServer/connect-3d-printer.png)

* Abra la aplicación de panel de IoT y compruebe que el dispositivo aparece en la **Mis dispositivos** ficha.

    ![Compruebe que el dispositivo aparece en el panel de IoT](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3. Implementar la red de la aplicación de impresión en 3D
___
* En el panel de IoT, haga clic en el **Pruebe algunos ejemplos** sección.
* Seleccione la aplicación de ejemplo de impresora 3D de red.

   ![Instalar la impresora de red 3D](../media/3dprintserver/dashboard-samples.png)

* Seleccione el modelo de impresora y presione 3D el **implementar y ejecutar** botón para implementar la aplicación en el dispositivo de IoT Core. 

    ![Instalar la impresora de red 3D](../media/3dprintserver/dashboard-app.png)

    [Imagen 6 de TAZ LulzBot](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) por [alef objetos, Inc.](https://www.alephobjects.com/) arreglo [CC BY SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
    
    Si desea instalar una opción de seleccionar "personalizado" personalizados de impresora desde la lista de impresoras. Custom impresoras 3d necesitan un archivo xml de configuración llamado archivo PrintDeviceCapabilities.xml proporcionarse correctamente conectarse e imprimir en la impresora en 3d. Un archivo de ejemplo PrintDeviceCapabilities.xml puede encontrarse aquí https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   Son los mínimos cambios que deba realizar en el archivo xml actualizar las secciones siguientes con los valores correctos específicos de la impresora compatible.

Estos valores especifican las dimensiones de la cama impresión de la impresora 3d a la segmentación de datos al procesar el modelo 3d

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


El valor de la etiqueta xml de psk3dx:baudrate controla la velocidad en baudios específica para usar al comunicarse con la impresora de la raspberry pi3 3d. Establecer la velocidad en baudios adecuado específicas para su impresión en 3d. 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

Los demás valores en el xml PrintDeviceCapabilities se usan para notificar a la segmentación de datos en el controlador de impresión en 3d para ajustar su funcionamiento con una determinada impresora compatible.
Más información sobre todos estos valores se proporcionan [aquí](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings).

    
    
## <a name="4-add-your-3d-printer"></a>4. Agregar la impresora en 3D
___
* Vaya a su PC de Windows 10 y a **configuración** -> **dispositivos** -> **, impresoras y escáneres**.
* Presione **agregar una impresora o un escáner**.

     ![Configuración de Windows agrega dispositivo](../media/3dprintserver/add-printer.png)

* Seleccione la impresora y pulse 3D **Agregar dispositivo**. La impresora se instalará automáticamente.

     ![Configuración de Windows agrega dispositivo](../media/3dprintserver/add-device.png)

Enhorabuena, que ahora se ha instalado la impresora y se comportará exactamente como si se ha conectado con un cable USB.
Ahora puede imprimir utilizando [generador 3D](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).
