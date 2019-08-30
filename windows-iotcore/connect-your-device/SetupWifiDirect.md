---
title: Usar Wi-Fi Direct en el dispositivo de Windows 10 IOT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo configurar, probar y usar Wi-Fi Direct en dispositivos con un adaptador Wi-Fi USB habilitado.
keywords: Windows IOT, WiFi Direct, instalación, WiFi, dispositivos
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169412"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>Usar Wi-Fi Direct en el dispositivo de Windows 10 IoT Core

WiFi Direct es compatible con dispositivos Windows 10 IoT Core mediante el uso de un adaptador Wi-Fi USB habilitado para Wi-Fi. Para asegurarse de que Wi-Fi Direct está habilitado, deben cumplirse dos cosas:
* el hardware del adaptador WiFi USB debe ser compatible con Wi-Fi Direct,
* el controlador correspondiente del adaptador WiFi USB debe ser compatible con Wi-Fi Direct. 

Wi-Fi Direct proporciona una solución para la conectividad de dispositivo a dispositivo WiFi sin necesidad de que un punto de acceso inalámbrico (AP inalámbrico) Configure la conexión. Eche un vistazo a las API de UWP disponibles en el [espacio de nombres Windows. Devices. WiFiDirect](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) para ver lo que puede hacer con WiFiDirect.

## <a name="supported-adapters"></a>Adaptadores admitidos

Puede encontrar una lista de adaptadores de Wi-Fi que se han probado en Windows 10 IoT Core en nuestra página de [hardware compatible](../learn-about-hardware/HardwareCompatList.md) . 

## <a name="basic-sample-for-wifi-direct"></a>Ejemplo básico para Wi-Fi Direct

Puede probar fácilmente la funcionalidad de Wi-Fi Direct con el [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)de Wi-Fi Direct UWP. Usaremos la C# versión y ejecutaremos el ejemplo de dos dispositivos.

### <a name="set-up-the-two-devices"></a>Configurar los dos dispositivos
* MinnowBoardMax (MBM) con Windows 10 IoT Core (consulte las instrucciones aquí), con un dispositivo de protección WiFi de CanaKit
* Conectar monitor, teclado y mouse al MBM
* Un equipo con Windows 10 que ejecute la última actualización de aniversario de Windows 10. El equipo (o portátil) tendrá que tener compatibilidad con WiFi Direct (por ejemplo, una superficie de Microsoft).
* Instalación de Visual Studio 2017 en el equipo con Windows 10
* Clone o descargue el [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)de Wi-Fi Direct UWP (la raíz del repositorio de github está [aquí](https://github.com/Microsoft/Windows-universal-samples)).
* Carga de C# la versión del ejemplo de Wi-Fi Direct UWP en Visual Studio 2017

#### <a name="run-the-sample-on-the-two-devices"></a>Ejecutar el ejemplo en los dos dispositivos
* Compile el ejemplo e impleméntelo/ejecútelo en MBM:

    * Establecer el cuadro combinado "plataformas de solución" en "x86"
    * Seleccione "equipo remoto" en la lista desplegable "ejecutar".
    * Inicie el ejemplo en MBM sin depurar (presionando Ctrl-F5 o seleccionando "iniciar sin depurar" en el menú "depurar").
    * Debería ver el ejemplo de Wi-Fi Direct en ejecución en el monitor conectado a MBM
* Compile el ejemplo e impleméntelo y ejecútelo en el equipo con Windows 10:
    * Establecer el cuadro combinado "plataformas de solución" en "x86"
    * Seleccione "local" en la lista desplegable "ejecutar".
    * Inicie el ejemplo (F5 o Ctrl-F5).
    * Debería ver el ejemplo de Wi-Fi Direct en ejecución en su equipo con Windows 10.

### <a name="set-up-advertiser-and-connector"></a>Configurar el anunciante y el conector
* En MBM, seleccione (1) "anunciador" y presione el botón "iniciar anuncio".

    * El MBM comenzará a anunciarse en el canal Wi-Fi Direct

        ![Pantalla de configuración del anunciante](../media/SetupWiFiDirect/Advertiser01.png)

        Observe el banner "Advertisement status" (estado de anuncio) en la parte inferior de la aplicación.
    
* En el equipo con Windows 10, seleccione (2) "conector" y presione el botón "iniciar monitor". 

    * El equipo con Windows 10 iniciará el examen de las conexiones Wi-Fi Direct disponibles
    * Una vez completado el análisis, debería ver el nombre de la MBM en la lista "dispositivos detectados"

        ![Pantalla de configuración del conector](../media/SetupWiFiDirect/Connector01.png)

        Puede ver dos dispositivos en la lista (estamos interesados en "Ale-mbm01") y el mensaje "error de enumeración de DeviceWatcher completado".

### <a name="pair-the-devices"></a>Emparejar los dispositivos
* En el equipo con Windows 10, seleccione MBM ("Ale-mbm01" en nuestro ejemplo) en la lista "dispositivos detectados" y presione el botón "conectar".
* En el equipo con Windows 10, presione "sí" para iniciar el proceso de emparejamiento.

    ![Emparejamiento de inicio del conector](../media/SetupWiFiDirect/Connector02.png)

* En el monitor de MBM, debe un mensaje con el PIN

    ![Cuadro de diálogo de anclaje del anunciante](../media/SetupWiFiDirect/Advertiser02.png)

* En el equipo con Windows 10, debería ver un cuadro de diálogo en el que debe escribir el PIN

    ![Cuadro de diálogo PIN del conector](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>Hable en el canal
* Los dos dispositivos deben estar conectados. Debería ver un identificador de dispositivo generado aleatoriamente ("hqffpzhz. GGG" en nuestro ejemplo) en ambas pantallas de la lista "dispositivos conectados".

    ![Dispositivo conectado al anunciante](../media/SetupWiFiDirect/Advertiser03.png)

    ![Dispositivo conectado al conector](../media/SetupWiFiDirect/Connector04.png)

* Ahora tiene una configuración de canal (o Socket) dúplex completo

    * en MBM, seleccione el dispositivo ("hqffpzhz. GGG") de la lista "dispositivos conectados".
    * Escriba un mensaje en el cuadro de texto "Escriba un mensaje"
    * Presione el botón "enviar"
    * debería ver el mensaje que se recibe desde el equipo con Windows 10.
    * intente enviar un mensaje desde el equipo con Windows 10 a MBM
