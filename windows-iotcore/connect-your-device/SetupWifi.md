---
title: Uso de Wi-Fi en el dispositivo Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar, de instalación y configuración de Wi-Fi en el dispositivo Windows 10 IoT Core.
keywords: Windows iot, Wi-Fi, el programa de instalación, los dispositivos
ms.openlocfilehash: 20f61114323baa60c8052038df68a8c172ce1c95
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514800"
---
# <a name="using-wifi-on-your-windows-10-iot-core-device"></a>Uso de Wi-Fi en el dispositivo Windows 10 IoT Core

Wi-Fi se admite en dispositivos Windows 10 IoT Core mediante el uso de un adaptador USB Wi-Fi. Uso de Wi-Fi proporciona toda la funcionalidad de una conexión con cable, incluidos [SSH](../connect-your-device/SSH.md), [Powershell](../connect-your-device/PowerShell.md), [Windows Device Portal](../manage-your-device/DevicePortal.md)y depurar la aplicación e implementación.

> [!NOTE]
> Conexión de un cable Ethernet con cable invalidará Wi-Fi como la interfaz de red predeterminada.

### <a name="supported-adapters"></a>Adaptadores compatibles
Una lista de adaptadores de red Wi-Fi que se han probado en Windows 10 IoT Core puede encontrarse en nuestra [Hardware admite](../learn-about-hardware/HardwareCompatList.md) página.

### <a name="configuring-wifi"></a>Configuración de Wi-Fi
Para utilizar Wi-Fi, deberá proporcionar las credenciales de red Wi-Fi a Windows 10 IoT core. Además de la documentación sobre cómo compilar la aplicación complementaria y soluciones personalizadas de WPS, hay varias opciones diferentes para hacerlo, por lo que se enumeran a continuación.

## <a name="custom-companion-app--wps-wi-fi-onboarding-samples"></a>Aplicación personalizada complementaria y ejemplos de incorporación de Wi-Fi WPS

Actualmente, se ofrecen una serie de formas para que los desarrolladores crear una solución de incorporación de red Wi-Fi personalizado para su dispositivo. 

> | Muestras | Descripción | Ventajas  |  Inconvenientes  |
> |-------------|----------|---------|---------|
> | [Aplicación complementaria](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CompanionApp) | Creación de una aplicación simple que puede configurar Wi-Fi su dispositivo. |  Fácil de usar; Puntas o sin periféricos de IoT Core; Los clientes funcionan en varias plataformas | Programador crea su propio protocolo; requiere que el desarrollador implementar la seguridad |
> | [Incorporación de IoT con RFCOMM de Bluetooth](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding_RFCOMM) | Crear soluciones para configurar el dispositivo sin periféricos de IoT para conectar con su red Wi-Fi mediante RFCOMM de Bluetooth.  | Relevantes en dispositivos con cabezal o sin periféricos; Usa tecnologías conocidas y conceptos: No requiere de dispositivo IoT para iniciar un SoftAP; No es necesario ajustar la configuración de firewall | Requiere compatibilidad con Bluetooth para dispositivos de cliente y servidor; Ejemplo proporciona sólo la aplicación cliente para Windows 10; Servidor aplicación pre-defines/codifica los nombres de los dispositivos cliente. |
> | [Incorporación de IoT con AllJoyn](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTOnboarding) | Unirse de forma remota el dispositivo de IoT sin periféricos con la red Wi-Fi doméstica. | Funciona con AllJoyn | Compatibilidad para AllJoyn está en desuso |
> | Wi-Fi Protected Setup (WPS) API para los dispositivos | Ejecutar la detección WPS para consultar los métodos WPS admitidos por la red. | Simplemente Aproveche el [WiFiAdapter.GetWpsConfigurationAsync (WiFiAvailableNetwork](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.getwpsconfigurationasync) y [WiFiAdapter.ConnectAsync](https://docs.microsoft.com/uwp/api/windows.devices.wifi.wifiadapter.connectasync) métodos para conectar dispositivos de wi-fi a redes específicas. | Deberá familiarizarse con estas API aprovecharlas.; solo es compatible con enrutadores compatibles con WPS|

## <a name="headed-options"></a>Opciones de punta:

### <a name="option-1-startup-configuration"></a>Opción 1: Configuración de inicio
**Requisito previo:** El dispositivo de Windows 10 IoT core necesita un mouse, teclado, mostrar y adaptador de Wi-Fi USB conectado

La primera vez que arranque Windows 10 IoT Core con un adaptador USB Wi-Fi compatible, se le mostrará una pantalla de configuración.
En la pantalla de configuración, seleccione la red Wi-Fi que le gustaría conectar a y proporcionar la contraseña. Haga clic en **conectar** para iniciar la conexión.

![Pantalla de inicio de configuración de Wi-Fi](../media/SetupWiFi/WiFiStartupConfig.png)

### <a name="option-2-default-app-configuration"></a>Opción 2: Configuración de la aplicación predeterminada
**Requisito previo:** El dispositivo de Windows 10 IoT core necesita un mouse, teclado, mostrar y adaptador de Wi-Fi USB conectado

Configuración de Wi-Fi de forma alternativa es usar la aplicación predeterminada. Puede utilizarlo para configurar o modificar la configuración de Wi-Fi después de que el dispositivo se ha iniciado.

1. Haga clic en el icono de configuración en forma de engranaje en la página principal
2. Seleccione **Wi-Fi & red** en el panel izquierdo
3. Haga clic en la red Wi-Fi que desea conectarse. Escriba la contraseña si se le solicita y haga clic en **Connect**

![Configuración de Wi-Fi de aplicación predeterminada](../media/SetupWiFi/DefaultAppWiFiConfig.png)

## <a name="headless-options"></a>Opciones sin periféricos:




### <a name="option-1-web-based-configuration"></a>Opción 1: Configuración basada en Web
**Requisito previo:** El dispositivo ya debe estar conectado a la red local a través de Ethernet y debe conectado un adaptador de USB Wi-Fi

Si tiene dispositivos un con ninguna interfaz de usuario, mostrar o dispositivos de entrada, puede configurar a través de la [Windows Device Portal](../manage-your-device/DevicePortal.md).
En **panel de Windows 10 IoT Core**, *haga clic en* en el **abrir en el Portal de dispositivo** icono para el dispositivo.

<!-- This content is replicated at en-US/Docs/KitSetupRPI.md -->

1. Escriba **administrador** para el nombre de usuario y proporcione la contraseña (p@ssw0rd de forma predeterminada)
2. Haga clic en **red** en el panel izquierdo
3. En **redes disponibles**, seleccione que le gustaría conectar a y proporcionar las credenciales de conexión de red. Haga clic en **Connect** para iniciar la conexión

![Configuración de Wi-Fi basado en Web](../media/SetupWiFi/WebBWiFiConfig.png)

<!-- End of Replicated Content -->


### <a name="option-2-connect-using-wifi-profiles"></a>Opción 2: Conectarse mediante perfiles de Wi-Fi

**Requisito previo:** El dispositivo ya debe estar conectado a la red local a través de Ethernet y debe conectado un adaptador de USB Wi-Fi. También necesita un equipo Windows con la funcionalidad de Wi-Fi.

Se admite la configuración de Wi-Fi mediante perfiles inalámbricos en Windows 10 IoT Core. Consulte [MSDN](https://msdn.microsoft.com/library/windows/desktop/aa369853) para obtener información detallada y ejemplos.

1. Conectar el equipo de Windows a la red inalámbrica deseada y cree el archivo XML de perfil de Wi-Fi con estos comandos:

    * `netsh wlan show profiles` -> Buscar el nombre del perfil que acaba de agregar

    * `netsh wlan export profile name=<your profilename>`. El perfil se exportarán a un archivo XML

2. Abra un **Explorador de archivos** ventana y en el tipo de la barra de dirección `\\<TARGET_DEVICE>\C$\` y, a continuación, presione ENTRAR.  En este caso concreto, `<TARGET_DEVICE>` es el nombre o la dirección IP del dispositivo Windows 10 IoT Core:

    ![SMB con el Explorador de archivos](../media/SetupWifi/smb1.png)

    Si se le pide un nombre de usuario y contraseña, utilice las credenciales siguientes:

        User Name: <TARGET_DEVICE>\Administrator
        Password:  p@ssw0rd

    ![SMB con el Explorador de archivos](../media/SetupWifi/cred1.png)

> [!NOTE]
> Es **recomienda** que actualizar la contraseña predeterminada para la cuenta de administrador.  Siga las instrucciones que encontrará [aquí](../connect-your-device/PowerShell.md).

3. Copie el archivo XML de perfil de Wi-Fi exportado desde el equipo de Windows para el dispositivo Windows 10 IoT Core

4. Conéctese a su dispositivo con [PowerShell](../connect-your-device/PowerShell.md) y agregue el nuevo perfil de Wi-Fi a su dispositivo mediante la ejecución de los siguientes comandos

    * `netsh wlan add profile filename=<copied XML path>`

    * `netsh wlan show profiles`

5. Conecte el dispositivo de Windows 10 IoT Core a una red inalámbrica a través de netsh

    * `netsh wlan connect name=<profile name>`

6. Compruebe que el dispositivo está conectado a la red inalámbrica y puede conectarse a internet

    * `netsh wlan show interfaces`

    * `ipconfig /all`

    * `ping /S <your WiFi adapter ip address> bing.com`


#### <a name="connecting-to-wpa2-psk-personal-networks"></a>Conexión a redes WPA2-PSK Personal

Si necesita conectarse a una red Wi-Fi de WPA2-PSK Personal, siga las instrucciones anteriores en primer lugar, pero realizar los cambios siguientes en el archivo XML. La única diferencia es que, cuando su PC de Windows se exporta el código XML cifra la contraseña.

> [!WARNING] 
> Esto hará que la conexión no segura.

Perfil XML exportado desde PC Windows:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>true</protected>
        <keyMaterial><Your Encrypted password></keyMaterial>
    </sharedKey>


Los cambios necesitan para trabajar en Windows 10 IoT Core:

    <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial><Your Unencrypted password></keyMaterial>
    </sharedKey>
