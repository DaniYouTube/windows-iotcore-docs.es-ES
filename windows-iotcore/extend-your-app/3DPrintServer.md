---
title: Impresora de red 3D con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: Obtenga información sobre cómo convertir el dispositivo de Windows 10 IoT Core en un servidor de impresión y conectar su impresora 3D a él.
keywords: Windows IOT, 3D, impresora 3D, servidor de impresión, impresora 3D de red
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170492"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>Impresora de red 3D con Windows 10 IoT Core

Convierta el dispositivo de Windows 10 IoT Core en un servidor de impresión y conecte la impresora 3D a él. Podrá acceder a la impresora de forma inalámbrica desde otros dispositivos.

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1. Instalación de Windows 10 IoT Core en el dispositivo
___
Antes de empezar, necesitará lo siguiente:

* Un panel con la versión más reciente de Windows 10 IoT Core Insider instalada. Siga la [Guía de introducción](https://developer.microsoft.com/en-us/windows/iot/getstarted) para obtener la aplicación de panel de IOT e instalar Windows 10 IOT Core.
* Una impresora 3D compatible con nuestra aplicación de impresora 3D de red:

    * Lulzbot taz 6
    * Makergear m2
    * Printrbot Play, Plus y simple
    * Prusa i3 MK2
    * Ultimaker original y original +
    * Ultimaker 2 y 2 +
    * Extendido y extendido de Ultimaker 2
    * CraftBot 2
    * CraftBot PLUS
    * LulzBot
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2. Conectar la impresora 3D al dispositivo
___
* Conecte la impresora 3D a la placa de Windows 10 IoT Core con el cable USB.

    ![Conectar la impresora 3D al dispositivo](../media/3DPrintServer/connect-3d-printer.png)

* Abra la aplicación de panel de IoT y compruebe que el dispositivo aparece en la pestaña **mis dispositivos** .

    ![Comprobar que el dispositivo aparece en el panel de IoT](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3. Implementar la aplicación de impresora 3D de red
___
* En el panel de IoT, haga clic en la sección **probar algunos ejemplos** .
* Seleccione la aplicación de ejemplo de impresora Network 3D.

   ![Instalar impresora de red 3D](../media/3dprintserver/dashboard-samples.png)

* Seleccione el modelo de impresora 3D y presione el botón **implementar y ejecutar** para implementar la aplicación en el dispositivo de IOT Core. 

    ![Instalar impresora de red 3D](../media/3dprintserver/dashboard-app.png)

    [LULZBOT taz 6 Image](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png) by [Aleph Objects, Inc.](https://www.alephobjects.com/) tiene una licencia de [CC por-SA 4,0](https://creativecommons.org/licenses/by-sa/4.0/).
    
    Si desea instalar una impresora personalizada, seleccione la opción "personalizado" en la lista de impresoras. Las impresoras 3D personalizadas necesitan un XML de configuración denominado archivo PrintDeviceCapabilities. XML que se va a proporcionar para conectarse e imprimir correctamente en la impresora 3D. Aquí puede encontrar un archivo PrintDeviceCapabilities. XML de ejemplo https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   Los cambios mínimos que debe realizar en el archivo XML son actualizar las secciones siguientes con los valores correctos específicos de la impresora compatible.

Estos valores especifican las dimensiones de la cama de impresión de la impresora 3D en la segmentación al procesar el modelo 3D.

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


El valor de la etiqueta XML psk3dx: Baudrate controla la velocidad en baudios específica que se va a usar al comunicarse con la impresora 3D desde Raspberry PI3. Establezca la velocidad de baudios adecuada específica de la impresora 3D. 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

Los demás valores en el XML de PrintDeviceCapabilities se usan para notificar a la segmentación de los controladores de impresión 3D para ajustar su funcionamiento con la impresora compatible específica.
[Aquí](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)se proporciona más información sobre todos estos valores.

    
    
## <a name="4-add-your-3d-printer"></a>4. Agregar la impresora 3D
___
* Vaya a su equipo con Windows 10 y vaya a **configuración** -> **dispositivos** -> **impresoras impresoras & escáneres**.
* Presione **Agregar una impresora o un escáner**.

     ![Configuración de Windows Agregar dispositivo](../media/3dprintserver/add-printer.png)

* Seleccione la impresora 3D y presione **Agregar dispositivo**. La impresora se instalará automáticamente.

     ![Configuración de Windows Agregar dispositivo](../media/3dprintserver/add-device.png)

Enhorabuena, la impresora ya está instalada y se comportará exactamente como si estuviera conectada con un cable USB.
Ahora puede imprimir en él con el [generador 3D](https://msdn.microsoft.com/windows/hardware/mt561568.aspx).
