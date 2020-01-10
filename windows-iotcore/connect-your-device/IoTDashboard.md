---
title: Panel de Windows 10 IoT Core
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre lo que hace el panel de IoT Core de Windows 10 y cómo empezar.
keywords: Windows IOT, Windows 10 IOT Core Dashboard, panel de Windows IOT, dispositivos
ms.openlocfilehash: 53a8be4e29f93ab3f6d9979e247c598ea5e637c8
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721490"
---
# <a name="windows-10-iot-core-dashboard"></a>Panel de Windows 10 IoT Core

Panel de Windows 10 IoT Core es la mejor manera de descargar, configurar y conectar sus dispositivos Windows 10 IoT Core, todo desde su PC.

Puede descargar el [Panel de IOT Core aquí](https://go.microsoft.com/fwlink/?LinkID=708576).

> [!NOTE]
> Si encuentra que está recibiendo una pantalla en blanco al abrir el panel de IoT después de la descarga, puede deberse a un problema con el controlador. Para solucionar este problema, debe descargar el [formato zip](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) del controlador de gráficos Intel e instalar el controlador manualmente. 

## <a name="set-up-a-new-device"></a>Configuración de un dispositivo nuevo

> [!NOTE]
> El panel de información no se puede usar para configurar Raspberry Pi 3B+. Si tiene un dispositivo 3B+, debe usar la [versión preliminar técnica de 3B+](https://www.microsoft.com/software-download/windowsiot). Vea las [limitaciones conocidas](https://docs.microsoft.com/windows/iot-core/troubleshooting) de la versión preliminar técnica para determinar si esto es adecuado para el desarrollo.

> [!NOTE]
> Actualmente hay un problema conocido en el que el sistema operativo atraviesa las particiones de la tarjeta SD y solicita un "formato..." mensaje para una partición de datos específica que no contiene ningún sistema de archivos. Descartar este mensaje presionando cancelar. Aunque trabajamos en una solución, se recomienda que, si hace clic en "formatear ahora", vuelva a crear la tarjeta SD con la imagen FFU cuando la acción de formato afecte al proceso de actualización y el dispositivo no se actualizará.


El panel de IoT facilita la configuración de un nuevo dispositivo. Para obtener instrucciones detalladas sobre cómo empezar, [consulte la página de introducción.](https://docs.microsoft.com/windows/iot-core/getstarted)

![Página de configuración del panel de IoT](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>Tarjeta SD
El tipo, marca y modelo de la tarjeta SD afecta en gran medida al rendimiento y a la calidad de IoT Core.
Una tarjeta lenta puede tardar hasta cinco veces más en arrancar que las [tarjetas recomendadas](../learn-about-hardware/hardwarecompatlist.md).
Una tarjeta SD más antigua y menos confiable podría no funcionar siquiera. Si sigue teniendo problemas para instalar, considere la posibilidad de reemplazar la tarjeta SD.

### <a name="device-name"></a>Nombre del dispositivo
El nombre de dispositivo predeterminado es minwinpc. Se recomienda cambiarla a algo único, ya que esto facilita la búsqueda del dispositivo en la red. El nombre del dispositivo puede tener una longitud de 15 caracteres como máximo y puede incluir letras, números y los siguientes símbolos: @ # $% ^ & ') (. -_ {} ~ Si cambia el nombre del dispositivo en el panel de IoT al configurar el dispositivo, se producirá un reinicio automático la primera vez que encienda el dispositivo.

### <a name="password"></a>Contraseña
La contraseña es un campo obligatorio y debe establecerse. Al establecer una contraseña en el panel de IoT, se modifica la contraseña del usuario administrador que, de forma predeterminada, es "p@ssw0rd".

### <a name="wi-fi-network-connection"></a>Conexión de red Wi-Fi
En el panel de IoT se muestran todas las redes disponibles a las que se ha conectado el equipo previamente. Si no ve la red Wi-Fi deseada en la lista, asegúrese de que está conectado a ella en su PC.
Si desactiva la casilla, debe conectar un cable Ethernet a la placa después del parpadeo.

### <a name="first-boot"></a>Primer arranque
El primer arranque siempre tardará más que todos los arranques posteriores. El sistema operativo tardará algún tiempo en instalarse y conectarse a la red.
El tiempo de arranque puede variar considerablemente en función de la tarjeta SD. Por ejemplo, un Raspberry PI 3 que se ejecuta en la tarjeta SD recomendada tarda 3-4 minutos en iniciarse por primera vez. En el mismo PI con una tarjeta SD de baja calidad, hemos detectado tiempos de arranque de más de 15 minutos.

### <a name="connecting-to-the-internet"></a>Conectarse a Internet
Es esencial tener el dispositivo IoT Core conectado a Internet. Muchas de las placas más recientes incorporan adaptadores Wi-Fi integrados. Si tiene problemas para conectarse a la red, intente lo siguiente:

* Reinicio del dispositivo
* Conexión de un cable Ethernet
* Conectando un monitor al dispositivo. Esto le mostrará información de diagnóstico sobre el dispositivo.

> [!NOTE]
> El adaptador de Wi-Fi oficial de Raspberry pi 2 puede ser inestable al conectarse a Wi-Fi.


## <a name="my-devices"></a>Mis dispositivos
___
Una vez que el dispositivo esté conectado a Internet, el panel de IoT detectará automáticamente el dispositivo.
Para encontrar el dispositivo, vaya a **mis dispositivos**. Si el dispositivo no aparece en la lista, intente reiniciar el dispositivo. Asegúrese de que, si hay más de un dispositivo en la red, cada uno tiene un nombre único. Asegúrese también de que **windows10iotcoredashboard. exe** se puede comunicar a través de Firewall de Windows mediante los pasos siguientes:

1. Abra el **centro de redes y recursos compartidos** y busque el tipo de red (dominio, privado o público) al que está conectado su equipo.
2. Abra el **Panel de control** y haga clic en **sistema y seguridad**.
3. Haga clic en **permitir una aplicación a través de Firewall de Windows** en **firewall de Windows**.
4. Haz clic en **Cambiar configuración**.
5. Busque **windows10iotcoredashboard. exe** en **aplicaciones y características permitidas** y, a continuación, habilite la casilla red adecuada (es decir, el tipo de red que encontró en el paso 1).


### <a name="connect-to-your-device"></a>Conexión al dispositivo

> [!NOTE]
> Si no puede encontrar el dispositivo en el panel, intente escribir su [dirección IP] y [: 8080] en el explorador para poner en marcha el portal de dispositivos de Windows. Para que el dispositivo se muestre en el panel, intente reiniciar el dispositivo.


Haga clic con el botón derecho y seleccione **abrir en el portal de dispositivos**. Esto iniciará la página del [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md) y es la mejor manera de interactuar y administrar el dispositivo.

![IoTDashboard ver dispositivos](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

También puede conectarse al dispositivo mediante Windows PowerShell.

## <a name="connect-to-azure"></a>Conexión a Azure AD
___
El panel de IoT le permite aprovisionar dispositivos IoT Core con Azure IoT Hub. Puede obtener más información en esta entrada de [blog](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).

[Aprenda a usar el panel de IoT con Azure](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>Ejemplos de ejecución rápida
___

Los ejemplos de ejecución rápida no requieren la compilación de código, la instalación de Visual Studio o la descarga del SDK. Son ideales para comprobar rápidamente lo que puede hacer IoT Core.

### <a name="network-3d-printer"></a>Impresora de red 3D
Use el ejemplo de impresora de red 3D para conectar la impresora 3D a la placa, lo que puede hacer que se pueda detectar a través de la red doméstica. 

![Impresora IoTDashboard Network 3D](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>Radio por Internet
Convierta el dispositivo de Windows 10 IoT Core en una radio de Internet que se pueda controlar desde cualquier lugar de su hogar.

![IoTDashboard radio por Internet](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT Core sin bloqueos
El ejemplo de IoT Core permite que el programa sea un pi2 o 3 de Raspberry y un sombrero de sentido de Raspberry PI mediante un editor de "bloque" desde el explorador.

![IoTDashboard bloque](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
