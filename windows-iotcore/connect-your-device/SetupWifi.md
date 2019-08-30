---
title: Usar Wi-Fi en el dispositivo de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar, configurar y configurar Wi-Fi en el dispositivo de Windows 10 IoT Core.
keywords: Windows IOT, Wi-Fi, instalación, dispositivos
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169499"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a>Usar Wi-Fi en el dispositivo de Windows 10 IoT Core

Wi-Fi es compatible con dispositivos Windows 10 IoT Core mediante el uso de un adaptador de USB WiFi. El uso de la red Wi-Fi proporciona toda la funcionalidad de una conexión cableada, como [ssh](../connect-your-device/SSH.md), [PowerShell](../connect-your-device/PowerShell.md), el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md)y la depuración e implementación de aplicaciones.

> [!NOTE]
> La conexión de un cable Ethernet cableado invalidará Wi-Fi como la interfaz de red predeterminada.

### <a name="supported-adapters"></a>Adaptadores admitidos
Puede encontrar una lista de adaptadores de Wi-Fi que se han probado en Windows 10 IoT Core en nuestra página de [hardware compatible](../learn-about-hardware/HardwareCompatList.md) .

### <a name="configuring-wifi"></a>Configuración de Wi-Fi
Para usar Wi-Fi, debe proporcionar Windows 10 IoT Core con las credenciales de red WiFi. Además de la documentación sobre cómo crear soluciones personalizadas de aplicación y WPS, hay varias opciones para hacerlo que se indican a continuación.

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a>Ejemplos de incorporación de aplicaciones complementarias & WPS Wi-Fi

Actualmente, ofrecemos varias maneras para que los desarrolladores creen una solución de incorporación Wi-Fi personalizada para su dispositivo. 

> | Muestras | Descripción | Ventajas  |  Desventajas  |
> |-------------|----------|---------|---------|
> | [Aplicación complementaria](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | Cree una aplicación de Xamarin sencilla que pueda configurar la Wi-Fi del dispositivo. |  Fácil de usar; Con cabeza o sin cabezal para IoT Core; Los clientes funcionan entre plataformas | El desarrollador está creando su propio protocolo; requiere que el desarrollador implemente la seguridad |
> | [Incorporación de IoT con Bluetooth RFCOMM](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | Cree una solución para configurar el dispositivo IoT sin periféricos con el fin de conectarse a la red Wi-Fi mediante Bluetooth RFCOMM.  | Relevante en dispositivos con cabeza o sin periféricos; Utiliza tecnologías y conceptos conocidos; No requiere que el dispositivo IoT inicie un SoftAP; No es necesario ajustar la configuración del firewall | Requiere compatibilidad con Bluetooth para dispositivos cliente y servidor; El ejemplo solo proporciona la aplicación cliente para Windows 10; La aplicación de servidor define previamente o codifica los nombres del dispositivo cliente. |
> | [Incorporación de IoT con AllJoyn](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | Unir de forma remota el dispositivo de IoT sin periféricos con la red Wi-Fi doméstica. | Funciona con AllJoyn | Parte de la compatibilidad con AllJoyn está en desuso. |
> | API de instalación protegida Wi-Fi (WPS) para dispositivos | Realice la detección de WPS para consultar los métodos WPS admitidos por la red. | Simplemente aproveche los métodos [WiFiAdapter. GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) y [WiFiAdapter. ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) para conectar dispositivos Wi-Fi a redes específicas. | Deberá familiarizarse con estas API para aprovecharlas. solo compatible con enrutadores habilitados para WPS|

## <a name="headed-options"></a>Opciones de cabeza:

### <a name="option-1-startup-configuration"></a>Opción 1: Configuración de inicio
**Requisitos previos** El dispositivo Windows 10 IoT Core necesita un mouse, un teclado, una pantalla y un adaptador WiFi USB conectados

La primera vez que inicie Windows 10 IoT Core con un adaptador de USB WiFi compatible, aparecerá una pantalla de configuración.
En la pantalla Configuración, seleccione la red Wi-Fi a la que le gustaría conectarse y proporcione la contraseña. Haga clic en **conectar** para iniciar la conexión.

![Pantalla de configuración de Wi-Fi de inicio](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a>Opción 2: Configuración predeterminada de la aplicación
**Requisitos previos** El dispositivo Windows 10 IoT Core necesita un mouse, un teclado, una pantalla y un adaptador WiFi USB conectados

Una manera alternativa de configurar Wi-Fi es usar la aplicación predeterminada. Puede usar esta opción para configurar o modificar la configuración de Wi-Fi una vez arrancado el dispositivo.

1. Haga clic en el icono de configuración con forma de engranaje de la Página principal.
2. Seleccionar **red & Wi-Fi** en el panel izquierdo
3. Haga clic en la red Wi-Fi a la que desea conectarse. Proporcione la contraseña si se le solicita y haga clic en **conectar** .

![Configuración de la aplicación Wi-Fi predeterminada](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a>Opciones sin periféricos:




### <a name="option-1-web-based-configuration"></a>Opción 1: Configuración basada en Web
**Requisitos previos** El dispositivo ya tendrá que estar conectado a la red local a través de Ethernet y debe tener un adaptador de USB WiFi conectado

Si tiene el dispositivo a sin interfaz de usuario, pantalla o dispositivos de entrada, todavía puede configurarlo a través del [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md).
En el **Panel de Windows 10 IOT Core**, *haga clic* en el icono **abrir en el portal de dispositivos** del dispositivo.

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. Escriba **Administrador** para el nombre de usuario y proporcione su contraseñap@ssw0rd (de forma predeterminada).
2. Haga clic en **red** en el panel izquierdo.
3. En **redes disponibles**, seleccione la red a la que desea conectarse y proporcione las credenciales de conexión. Haga clic en **conectar** para iniciar la conexión.

![Configuración de Wi-Fi basada en Web](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a>Opción 2: Conexión mediante perfiles de Wi-Fi

**Requisitos previos** El dispositivo ya tendrá que estar conectado a la red local a través de Ethernet y debe tener un adaptador de USB WiFi conectado. También necesita un equipo Windows con capacidad WiFi.

La configuración de Wi-Fi mediante perfiles inalámbricos se admite en Windows 10 IoT Core. Consulte [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) para obtener más información y ejemplos.

1. Conecte el equipo Windows a la red inalámbrica deseada y cree el archivo XML del perfil de Wi-Fi con estos comandos:

    * `netsh wlan show profiles`-> buscar el nombre del perfil que acaba de agregar

    * `netsh wlan export profile name=<your profilename>` Se exportará el perfil a un archivo XML.

2. Abra una ventana del **Explorador de archivos** y, en la barra de `\\<TARGET_DEVICE>\C$\` direcciones, escriba y presione Entrar.  En este caso concreto, `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo de Windows 10 IOT Core:

    ![SMB con el explorador de archivos](../media/SetupWifi/smb1.png)

    Si se le pide un nombre de usuario y una contraseña, use las credenciales siguientes:

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![SMB con el explorador de archivos](../media/SetupWifi/cred1.png)

> [!NOTE]
> Se **recomienda encarecidamente** que actualice la contraseña predeterminada para la cuenta de administrador.  Siga las instrucciones que se encuentran [aquí](../connect-your-device/PowerShell.md).

3. Copiar el archivo XML del perfil de Wi-Fi exportado del equipo de Windows en el dispositivo de Windows 10 IoT Core

4. Conéctese al dispositivo mediante [PowerShell](../connect-your-device/PowerShell.md) y agregue el nuevo perfil de Wi-Fi al dispositivo mediante la ejecución de los siguientes comandos.

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. Conexión del dispositivo Windows 10 IoT Core a la red inalámbrica a través de Netsh

    * `netsh wlan connect name=<profile name>`

6. Compruebe que el dispositivo está conectado a la red inalámbrica y puede conectarse a Internet.

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a>Conexión a redes personales WPA2-PSK

Si necesita conectarse a una red Wi-Fi personal WiFi, siga primero las instrucciones anteriores, pero realice los cambios siguientes en el archivo XML. La única diferencia es que cuando el equipo Windows exporta el XML, cifra la contraseña.

> [!WARNING] 
> Esto hará que la conexión no sea segura.

Perfil XML exportado desde PC Windows:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


Cambios necesarios para trabajar en Windows 10 IoT Core:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
