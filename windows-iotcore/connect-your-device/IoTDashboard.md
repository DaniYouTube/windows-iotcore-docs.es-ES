---
title: Panel de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre lo que hace el panel de Windows 10 IoT Core y cómo empezar a trabajar.
keywords: Windows iot, panel de windows 10 iot core, panel de windows iot, los dispositivos
ms.openlocfilehash: d21b67dad15d510564ec7fae28a2431d28faf8be
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514960"
---
# <a name="windows-10-iot-core-dashboard"></a>Panel de Windows 10 IoT Core

Panel de Windows 10 IoT Core es la mejor manera de descargar, configurar y conectar sus dispositivos Windows 10 IoT Core, todo ello desde su PC.

Puede descargar el [IoT Core aquí panel](http://go.microsoft.com/fwlink/?LinkID=708576).

> [!NOTE]
> Si se detecta que está obteniendo una pantalla en blanco al abrir el panel de IoT después de descargar, puede que debido a un problema de controlador. Para solucionar este problema, necesitará descargar el [formato zip](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) del controlador de gráficos Intel e instalar manualmente el controlador. 

## <a name="set-up-a-new-device"></a>Configurar un dispositivo nuevo

> [!NOTE]
> No se puede utilizar el panel usado para configurar el dispositivo Raspberry Pi 3B +. Si tiene un dispositivo 3B +, debe usar el [vista previa técnica de 3B +](https://www.microsoft.com/en-us/software-download/windowsiot). Consulte la [limitaciones conocidas](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) de technical preview para determinar si esto es adecuado para el desarrollo.

> [!NOTE]
> Actualmente no hay un problema conocido, donde el sistema operativo pasa por las particiones en la tarjeta SD y pide 'Format'... mensaje para una partición de datos específicos que no contiene ningún sistema de archivos. Haciendo clic en Cancelar para descartar este mensaje. Mientras trabajamos en una solución, se recomienda que si hace clic en "Format ahora", programar la tarjeta SD, con la imagen FFU nuevo como los efectos de acción de formato que el proceso de actualización y el dispositivo no podrá actualizar.


El panel de IoT facilita la configuración de un dispositivo nuevo. Para obtener instrucciones detalladas sobre cómo empezar, vea el [comenzar](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) página.

![Página de configuración del panel de IoT](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>Tarjeta SD
El tipo, la marca y el modelo de la tarjeta SD afecta en gran medida el rendimiento y la calidad de IoT Core.
Una tarjeta lenta puede tardar hasta cinco veces más en arrancar que nuestro [recomienda tarjetas](../learn-about-hardware/hardwarecompatlist.md).
No puede funcionar una tarjeta SD más antiguo y menos confiable. Si sigues experimenta problemas al instalar, considere la posibilidad de reemplazar la tarjeta SD.

### <a name="device-name"></a>Nombre del dispositivo
El nombre del dispositivo de forma predeterminada es minwinpc. Se recomienda cambiar a un elemento único así resulta más fácil encontrar el dispositivo en la red. El nombre del dispositivo puede tener como máximo 15 caracteres de longitud y puede incluir letras, números y los siguientes símbolos: @ # $ % ^ & ') (. -_ {} ~ Si cambia el nombre del dispositivo en el panel de IoT al configurar el dispositivo, un reinicio automático se realizará la primera vez en cuando de energía en el dispositivo.

### <a name="password"></a>Contraseña
Contraseña de un campo es obligatorio y debe establecerse. Establecer una contraseña en el panel de IoT modifica la contraseña de usuario administrador cuyo valor predeterminado es "p@ssw0rd".

### <a name="wi-fi-network-connection"></a>Conexión de red Wi-Fi
Panel de IoT muestra todas las redes disponibles que se ha conectado anteriormente a su PC. Si no ve la red Wi-Fi que desee en la lista, asegúrese de que está conectado a ella en su PC.
Si desactiva la casilla, debe conectarse mediante un cable Ethernet a la placa después de parpadear.

### <a name="first-boot"></a>Primer arranque
El primer arranque siempre tardará más que todos los arranques posteriores. El sistema operativo tardará algún tiempo para instalar y conectar a la red.
Tiempo de arranque puede variar considerablemente en función de la tarjeta SD. Por ejemplo, un Raspberry Pi 3 que se ejecutan en la tarjeta SD recomendada tarda 3 a 4 minutos para el primer arranque. En el mismo Pi con una tarjeta SD de baja calidad, hemos visto arranque veces más de 15 minutos.

### <a name="connecting-to-the-internet"></a>Conexión a internet
Es esencial contar con el dispositivo de IoT Core se conecten a internet. Muchos de los paneles más recientes vienen con integrado en adaptadores Wi-Fi. Si tiene problemas para conectarse a la red, intente lo siguiente:

* Reiniciar el dispositivo
* Conectar un cable Ethernet
* Conectar un monitor al dispositivo. Esto mostrará información de diagnóstico sobre el dispositivo

> [!NOTE]
> El adaptador Wi-Fi de Raspberry Pi 2 oficial puede ser inestable al conectarse a Wi-Fi.


## <a name="my-devices"></a>Mis dispositivos
___
Después de que el dispositivo está conectado a internet, el panel de IoT detectará automáticamente el dispositivo.
Para buscar el dispositivo, vaya a **Mis dispositivos**. Si el dispositivo no aparece, intente reiniciar el dispositivo. Asegúrese de que si hay varios dispositivos en la red, cada uno de ellos tiene un nombre único. Además, asegúrese de que su **windows10iotcoredashboard.exe** puede comunicarse a través de Firewall de Windows siguiendo los pasos siguientes:

1. Abra **centro de redes y recursos compartidos** y, a continuación, busque el tipo de red (dominio/privado/público) que está conectado su equipo.
2. Abra **Panel de Control** y haga clic en **sistema y seguridad**.
3. Haga clic en **permitir que una aplicación a través de Firewall de Windows** en **Windows Firewall**.
4. Haga clic en **cambiar la configuración de**.
5. Buscar **windows10iotcoredashboard.exe** en **aplicaciones y características permitidas** y, a continuación, habilite la casilla de verificación de red adecuado (es decir, el tipo de red que se encuentra en el paso 1).


### <a name="connect-to-your-device"></a>Conectarse al dispositivo

> [!NOTE]
> Si no puede encontrar el dispositivo en el panel, pruebe a escribir su [dirección IP] y [: 8080] en el explorador para obtener Windows Device Portal en marcha. Para obtener el dispositivo para mostrar en el panel, pruebe a reiniciar el dispositivo.


Haga clic y seleccione **abrir en el Portal de dispositivo**. Esto iniciará el [Windows Device Portal](../manage-your-device/DevicePortal.md) página y es la mejor manera de interactuar y administrar el dispositivo.

![IoTDashboard ver dispositivos](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

También puede conectarse al dispositivo mediante Windows PowerShell.

## <a name="connect-to-azure"></a>Conectarse a Azure
___
Panel de IoT le permite aprovisionar dispositivos de IoT Core con Azure IoT Hub. Puede leer más información al respecto en esto [entrada de blog](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).

[Obtenga información sobre cómo usar el panel de IoT con Azure](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>Ejemplos de ejecución rápidas
___

Ejecutar rápido ejemplos no requieren ninguna compilación de código, la instalación de Visual studio o descargar el SDK. Son excelentes para comprobar rápidamente lo que puede hacer IoT Core.

### <a name="network-3d-printer"></a>Impresora de red 3D
Use el ejemplo 3D de impresora de red para conectar la impresora 3D a la placa puede hacer que pueda detectar a través de la red doméstica. 

![Impresora de red IoTDashboard 3D](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>Internet radio
Convierta el dispositivo Windows 10 IoT Core en una radio por internet que puede controlarse desde cualquier lugar del hogar.

![Radio por IoTDashboard Internet](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT Core Blockly
Ejemplo de IoT Core Blockly permite su programa una Pi2 Raspberry o 3 y un "sombrero" sentido de Raspberry Pi mediante un editor de "bloque" desde el explorador.

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
