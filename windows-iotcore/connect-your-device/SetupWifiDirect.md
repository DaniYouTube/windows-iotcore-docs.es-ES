---
title: Uso de Wi-Fi Direct en su dispositivo con Windows 10 Iot Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a configurar, probar y usar direct de Wi-Fi en dispositivos con un adaptador de red Wi-Fi USB habilitado.
keywords: Windows iot, Wi-Fi direct, el programa de instalación, Wi-Fi, los dispositivos
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514803"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>Uso de Wi-Fi Direct en su dispositivo Windows 10 IoT Core

Se admite la Wi-Fi Direct habilitan para el adaptador de USB Wi-Fi en Windows 10 IoT Core dispositivos mediante el uso directo de una red Wi-Fi. Para asegurarse de que Wi-Fi Direct es dos cosas habilitadas debe ser true:
* debe admitir Wi-Fi Direct, el hardware del adaptador de USB Wi-Fi
* el controlador del adaptador de USB Wi-Fi correspondiente debe admitir Wi-Fi Direct. 

Wi-Fi Direct proporciona una solución para la conectividad de dispositivo a otro de Wi-Fi sin necesidad de ya sea un punto de acceso inalámbrico (AP inalámbrico) para configurar la conexión. Eche un vistazo a las API de UWP disponibles en el [espacio de nombres Windows.Devices.WiFiDirect](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx) para ver lo que puede hacer con WiFiDirect.

## <a name="supported-adapters"></a>Adaptadores compatibles

Una lista de adaptadores de red Wi-Fi que se han probado en Windows 10 IoT Core puede encontrarse en nuestra [Hardware admite](../learn-about-hardware/HardwareCompatList.md) página. 

## <a name="basic-sample-for-wifi-direct"></a>Ejemplo básico de Wi-Fi Direct

Puede probar fácilmente la funcionalidad de Wi-Fi Direct con Wi-Fi Direct UWP [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect). Usaremos el C# versión y ejecute el ejemplo de dos dispositivos.

### <a name="set-up-the-two-devices"></a>Configurar los dos dispositivos
* MinnowBoardMax (MBM) ejecuta Windows 10 IoT Core (consulte estas instrucciones), con una llave CanaKit WiFi
* Conectar el monitor, teclado y mouse a la MBM
* Un equipo de Windows 10 con la versión más reciente de Windows 10 Anniversary Update. El PC (o equipo portátil) deberán tener Wi-Fi Direct admite (por ejemplo, un Microsoft Surface)
* Instale Visual Studio 2017 en tu PC con Windows 10
* Clone o descargue Wi-Fi Direct UWP [ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(es la raíz del repositorio de GitHub [aquí](https://github.com/Microsoft/Windows-universal-samples)).
* Carga el C# versión de la muestra de Wi-Fi Direct UWP en Visual Studio 2017

#### <a name="run-the-sample-on-the-two-devices"></a>Ejecutar el ejemplo en los dos dispositivos
* Compile el ejemplo y la implementación y ejecución, en el MBM:

    * Establezca el cuadro combinado de "plataformas de solución" a "x86"
    * Seleccione "Máquina remota" en la lista desplegable "Run"
    * Iniciar el ejemplo en el MBM sin depuración (presionando Ctrl-F5 o seleccionando "Iniciar sin depurar" en el menú "Debug")
    * Debería ver el ejemplo de Wi-Fi Direct, que se ejecutan en el monitor conectado a la MBM
* Compile el ejemplo y la implementación y ejecución, en el equipo de Windows 10:
    * Establezca el cuadro combinado de "plataformas de solución" a "x86"
    * Seleccione "Local" en la lista desplegable "Run"
    * Iniciar el ejemplo (F5 o CTRL+F5)
    * Debería ver el ejemplo de Wi-Fi Direct, que se ejecutan en los equipos Windows 10

### <a name="set-up-advertiser-and-connector"></a>Configurar el anunciante y el conector
* En el MBM, seleccione "Anunciante" (1) y presione el botón "Iniciar anuncio"

    * Iniciará el MBM anuncia a sí mismo en el canal de Wi-Fi Direct

        ![Pantalla de configuración del anunciante](../media/SetupWiFiDirect/Advertiser01.png)

        Tenga en cuenta el banner "Advertisement Status" en la parte inferior de la aplicación.
    
* En el equipo con Windows 10, seleccione "Conector" (2) y presione el botón "Iniciar el monitor" 

    * El equipo con Windows 10 iniciará la exploración para conexiones Wi-Fi Direct disponibles
    * Cuando se completa el análisis, debería ver el nombre de su MBM en la lista "Dispositivos detectados"

        ![Pantalla de configuración del conector](../media/SetupWiFiDirect/Connector01.png)

        Puede ver la lista aparecen dos dispositivos (estamos interesados en "ale-mbm01") y el mensaje "Se completó la enumeración DeviceWatcher".

### <a name="pair-the-devices"></a>Empareje los dispositivos
* En el equipo con Windows 10, seleccione el MBM ("ale-mbm01" en nuestro ejemplo) en la lista "Dispositivos detectados" y presione el botón "Conectar"
* En el equipo con Windows 10, pulse "Sí" para iniciar el proceso de emparejamiento

    ![Emparejamiento de inicio de conector](../media/SetupWiFiDirect/Connector02.png)

* En el monitor MBM debería un mensaje con el PIN

    ![Cuadro de diálogo de NIP de anunciante](../media/SetupWiFiDirect/Advertiser02.png)

* En el equipo con Windows 10, debería ver un cuadro de diálogo donde debe escribir el PIN

    ![Cuadro de diálogo de NIP de conector](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>Hablar en el canal
* Los dos dispositivos deben estar conectados. Debería ver un identificador de dispositivo generado al azar ("hqffpzhz.ggg" en nuestro ejemplo) en ambas pantallas en la lista "Dispositivos conectados"

    ![Dispositivo conectado de anunciante](../media/SetupWiFiDirect/Advertiser03.png)

    ![Dispositivo conectado de conector](../media/SetupWiFiDirect/Connector04.png)

* Ahora tiene un canal de dúplex completo (o socket) configurar

    * en el MBM, seleccione el dispositivo ("hqffpzhz.ggg") en la lista "Dispositivos conectados"
    * Escriba un mensaje en el cuadro de texto "Escriba un mensaje de"
    * Presione el botón "Enviar"
    * debería ver el mensaje recibido desde el equipo con Windows 10
    * Intente enviar un mensaje desde el equipo con Windows 10 a la MBM
