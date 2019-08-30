---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo usar el portal de dispositivos de Windows para configurar y administrar el dispositivo de forma remota.
keywords: Windows IOT, Windows Device portal, Remote, portal de dispositivos
ms.openlocfilehash: 8e430365ea09509f5638d86ac77b151226df488f
ms.sourcegitcommit: 8932969dc50805113c330bc2ba6ec9003d067b3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412149"
---
# <a name="windows-device-portal"></a>Windows Device Portal
   Windows Device portal (WDP) le permite configurar y administrar el dispositivo de forma remota a través de la red local.
Las características principales se documentan en la [Página de información general del portal de dispositivos de Windows](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)

![Página principal del portal de dispositivos](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> No use las imágenes del creador con fines comerciales. Si se comercializa un dispositivo, debe usar una FFU personalizada para una seguridad óptima. Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

> [!WARNING]
> Actualmente no se puede realizar la depuración del kernel activo para dispositivos ARM. Estamos trabajando para solucionar este problema.

> [!IMPORTANT]
> Si va a crear un dispositivo minorista abierto para la implementación comercial en una "instalación específica/limitada" (es decir, en fábrica o en tienda) donde el usuario final realiza la configuración final y documenta a los clientes que deben [obtener un certificado para WDP y lo instala en WDP y los exploradores y las contraseñas se cambian en WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), y se acepta el uso de WDP en esta instancia comercial estrecha. Las imágenes comerciales de este escenario *no* deben incluir IOT_TOOLKIT, pero deben usar el paquete IOT_WEBBEXTN para extraer de WDP. 

## <a name="shared-documentation"></a>Documentación compartida
WDP es una herramienta de desarrollo compartida entre todos los dispositivos de Windows 10. Cada producto tiene sus propias características únicas, pero la funcionalidad básica es la misma.
La documentación de las principales características se encuentra en la [Página de información general del portal de dispositivos de Windows](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal). El resto de la documentación siguiente será específico de IoT.

## <a name="set-up"></a>Configuración

Hay dos maneras de poner en marcha el portal de dispositivos de Windows.

### <a name="1-windows-10-iot-dashboard"></a>1. Panel de Windows 10 IoT

En primer lugar, querrá descargar el [Panel de IOT de Windows 10](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), una herramienta de desarrollador que facilita la configuración de nuevos dispositivos. Una vez que haya usado el panel para crear una imagen de Windows 10 IoT Core en el dispositivo, compruebe que el dispositivo aparece en "mis dispositivos". 

Desde allí, use los puntos suspensivos en "acciones" para seleccionar "abrir en el portal de dispositivos". Desde allí, se le dirigirá a la página de autenticación del portal de dispositivos, donde, a menos que haya cambiado las credenciales inicialmente, las credenciales predeterminadas son: 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2. Browser
Si no puede encontrar el dispositivo en el panel o prefiere omitir el uso del panel, también puede abrir el portal de dispositivos escribiendo la dirección IP del dispositivo más `:8080` al final. Cuando se realiza correctamente, debería tener un aspecto similar al siguiente:


   ![IoTDashboard ver dispositivos](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>Características específicas de IoT

### <a name="device-settings"></a>Configuración del dispositivo

IoT Core agrega una casilla para habilitar o deshabilitar el [teclado en pantalla](../develop-your-app/OnScreenKeyboard.md) .
> [!NOTE]
> Esta casilla tiene un error conocido en el que se desactivará "Flash" en no comprobada. Actualice la página (F5) después de hacer clic para asegurarse de que la casilla muestra el estado deseado.

### <a name="apps"></a>Aplicaciones
Proporciona la funcionalidad de instalación y desinstalación de paquetes AppX y agrupaciones en el dispositivo.
![Lista de aplicaciones](../media/DevicePortal/AppList.png)

IoT Core es único, ya que solo permite ejecutar una aplicación en primer plano al mismo tiempo. La lista de aplicaciones se modifica para asegurarse de que este es el caso. En la columna **Inicio** , puede seleccionar tantas aplicaciones en segundo plano como se inicien de forma predeterminada, pero solo puede establecer una aplicación en primer plano.  

### <a name="app-file-explorer"></a>Explorador de archivos de la aplicación

El explorador de archivos de aplicación muestra los directorios a los que pueden acceder las aplicaciones.

* CameraRoll se comparte entre todas las aplicaciones
* Los documentos se comparten entre todas las aplicaciones
* LocalAppData contiene carpetas específicas de cada aplicación. Esta carpeta tendrá el mismo nombre que la aplicación y otras aplicaciones no podrán acceder a ella.

### <a name="debugging"></a>Depuración

#### <a name="kernel-dumps"></a>Volcados de kernel
![Depuración con volcados de kernel](../media/DevicePortal/Debug1.png)

Los bloqueos del sistema se registrarán automáticamente y estarán disponibles para su visualización a través de la herramienta de administración web.  Después, puede descargar el volcado del kernel e intentar averiguar lo que está ocurriendo.

#### <a name="process-dumps"></a>Procesos de volcado
![Depuración con volcados de proceso](../media/DevicePortal/Debug2.png)

Esto es similar a los volcados de kernel en vivo, pero para los procesos de modo de usuario. Al hacer clic en el botón **Descargar** se producirá un "minivolcado" y se descargará todo el estado de ese proceso. Esto es adecuado para depurar procesos de bloqueo.

#### <a name="kernel-crash-settings"></a>Configuración de bloqueo de kernel
![Configuración de bloqueo de kernel](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>Bluetooth
En esta página se muestran todos los dispositivos emparejados con Bluetooth y todos los dispositivos que se pueden detectar. Para emparejar con otro dispositivo Bluetooth, coloque el dispositivo en modo de emparejamiento y espere a que aparezca en la lista dispositivos disponibles.  
![Lista de dispositivos Bluetooth](../media/DevicePortal/Bluetooth.png)

Haga clic en el **vínculo emparejar** para emparejar el dispositivo. Si el dispositivo requiere un PIN para el emparejamiento, aparecerá un cuadro de mensaje que muestra el PIN. Una vez que el dispositivo se empareja, se mostrará en la lista de dispositivos emparejados. Para desemparejar el dispositivo, haga clic en **quitar**. 

Una vez que navegue a la página de Bluetooth, el dispositivo será reconocible para otros dispositivos. También puede encontrarla desde su PC/teléfono y emparejarla desde allí.

Puede encontrar más información sobre Bluetooth en la [Página de Bluetooth](https://go.microsoft.com/fwlink/?linkid=823223).

### <a name="iot-onboarding"></a>Incorporación de IoT

La incorporación de IoT proporciona compatibilidad para configurar las opciones de conectividad Wi-Fi de un dispositivo IoT.

**Conexión compartida a Internet (ICS)** Conexión compartida a Internet permite compartir el acceso a Internet del dispositivo con otros dispositivos conectados al dispositivo a través de la SoftAP Wi-Fi.
Para usar esta característica, el dispositivo de IoT de Windows 10 debe tener acceso a Internet (por ejemplo, mediante una conexión LAN cableada).  En ' Conectividad-> incorporación: > configuración de SoftAP ' haga clic en ' habilitar ' y establezca el nombre y la contraseña del SSID.  A continuación, en ' Conectividad-> conexión compartida a Internet ' para ' adaptador de punto de acceso ' Seleccione ' adaptador virtual de Microsoft Wi-FI Direct #2 ' y para ' adaptador de red compartido ' Seleccione el adaptador Ethernet con cable.  Por último, haga clic en ' iniciar acceso compartido '.  Una vez que se haya iniciado, conecte un dispositivo Wi-Fi compatible con el SoftAP en el dispositivo de IoT de Windows 10.  Una vez establecida una conexión, el dispositivo Wi-Fi compatible con Wi-Fi podrá conectarse a Internet a través del dispositivo de IoT de Windows 10.

> [!NOTE]
> ICS se deshabilita cuando existe un perfil de Wi-Fi en el dispositivo. Por ejemplo, ICS se deshabilitará si se conecta a un punto de acceso Wi-Fi y activa "crear perfil (volver a conectar automáticamente)".

**Configuración de SofTap** La configuración de SoftAP le permite controlar si el SoftAP de su dispositivo está habilitado o no.  También proporciona un medio para configurar el SSID de SoftAP y la clave WPA2-PSK necesaria para conectar el SoftAP desde otro dispositivo.

**Configuración de incorporación de AllJoyn** La configuración de incorporación de AllJoyn le permite controlar si la conexión Wi-Fi de su dispositivo puede configurarse a través del productor de incorporación de AllJoyn de su dispositivo.  Cuando un dispositivo independiente que ejecuta una aplicación de consumidor de incorporación AllJoyn se conecta a su SoftAP de IoT de Windows 10, la aplicación de consumidor de incorporación AllJoyn se puede usar para configurar el adaptador Wi-Fi del dispositivo IoT.  Cuando está habilitada, la aplicación de productor de incorporación de AllJoyn (IoTOnboarding) usa el método de autenticación de ECDHE_NULL. 

> [!NOTE]
> Para usar la incorporación de AllJoyn con las compilaciones de IoT de Windows 10 10.0.14393 o anterior, se requiere una actualización del ejemplo <strong>IotOnboarding</strong> que se puede [Descargar aquí](https://github.com/ms-iot/samples).

![Incorporación a la incorporación de](../media/DevicePortal/OnboardingAllJoyn.png)
AllJoyn![en ICS](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> El adaptador de punto de acceso es el adaptador WiFi que actúa como punto de acceso WiFi (normalmente tiene una dirección IP como 192.168.137.1).
> Adaptador de red compartido es el adaptador que se conecta a Internet (por ejemplo: Adaptador Ethernet).

![Incorporación a AP blando](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> El prefijo "AJ_" de SoftAP SSID se prefijará automáticamente si la incorporación de AllJoyn está habilitada y se ha posfijado con la dirección MAC del adaptador WiFi. La frase de contraseña de SoftAP debe tener entre 8 y 63 caracteres ASCII.


### <a name="tpm-configuration"></a>Configuración de TPM
El Módulo de plataforma segura (TPM) es un coprocesador criptográfico que incluye funcionalidades para la generación de números aleatorios, la generación segura de claves criptográficas y la limitación de su uso. También incluye funcionalidades como la atestación remota y el almacenamiento sellado. Para obtener información sobre el TPM y la seguridad en IoT Core, visite la página [creación de dispositivos seguros](../secure-your-device/BuildingSecureDevices.md) y la página [TPM](../secure-your-device/TPM.md) .

> [!IMPORTANT]
> Limpet. exe que se usa para formar parte de Windows IoT Core. A partir del 2018 de octubre, ahora está disponible como Porject de código abierto [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client)en.

Para facilitar las pruebas, tenemos una versión pregenerada no firmada de limpet. exe disponible y se puede descargar directamente desde WDP. Solo tiene que ir a la pestaña "configuración de TPM" y hacer clic en el botón "instalar latest". 

> [!NOTE]
> Esta versión de limpet. exe no se debe enviar con el producto final. En su lugar, debe compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.

### <a name="azure-clients-configuration"></a>Configuración de clientes de Azure

Los dispositivos de IoT se pueden administrar de forma remota a través de Cloud Services. Azure proporciona un conjunto muy completo de servicios para habilitar tales escenarios. Hemos creado un cliente de administración de dispositivos que complementa el servicio de aprovisionamiento de dispositivos (DPS) de Azure y el servicio IoT Hub de Azure en la plataforma Windows y que también expone varias características de administración de Windows.

Los clientes se proporcionarán como proyectos de código abierto. Para que sea más fácil probarla, se proporcionarán archivos binarios predefinidos. Puede usar la pestaña "clientes de Azure" de WDP para instalar y ejecutar esos archivos binarios de prueba.

> [!NOTE]
> Esta versión de las herramientas no se debe enviar con el producto final. En su lugar, debe compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.

Esta documentación se actualizará una vez que los proyectos de código abierto estén disponibles para su consumo.

### <a name="remote"></a>Control remoto
El servidor remoto de IoT de Windows permite a los usuarios ver lo que muestra su dispositivo sin necesidad de conectar un monitor físico al teclado.


## <a name="additional-information"></a>Información adicional 

### <a name="changing-the-default-port"></a>Cambiar el puerto predeterminado
 
1. Inicie PowerShell y [Conéctese a su dispositivo.](../connect-your-device/PowerShell.md)
2. Descargue la herramienta [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) , genérelo y cópiela en el dispositivo. 
3. Tomar posesión de la clave del registro para el servicio ejecutando

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. Establecer el puerto deseado modificando la configuración del registro 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. Reinicie el servicio de administración de webmanagement ejecutando a continuación o reiniciando el dispositivo.

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>Usar HTTPS 

Si desea usar HTTPS, tome primero la propiedad de la clave del registro como se describe en la sección anterior y establezca las claves del registro HttpsPort y EncryptionMode como se indica a continuación y, a continuación, reinicie el servicio de administración de webmanagement.

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a>Aprovisionamiento portal de dispositivos con un certificado SSL personalizado

En Windows 10 Creators Update, el portal de dispositivos de Windows agregó una manera de que los administradores de dispositivos instalaran un certificado personalizado para su uso en la comunicación HTTPS.

Para obtener más información, [Lea la documentación de los documentos de Windows Device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl). 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a>Configuración de volcado de memoria para capturar el volcado de memoria:

Para capturar un volcado de memoria completo, haga lo siguiente:

1. Conéctese a un dispositivo IoT a través de WDP.

2. En depurar-> configuración de depuración-> configuración de bloqueo del kernel-> tipo de volcado de memoria. 

3. No Volcado de memoria completo (en uso de memoria).
    Asegúrese de que el dispositivo se reinicie para que la configuración surta efecto. 
    
4. Compruebe que `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` está establecido en 0x1.

5. Actualice `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` a 0X0.

6. Asegúrese de que tiene suficiente espacio en el dispositivo para que se genere este volcado. Puede configurar el cambio de la ubicación del volcado de página desde aquí:`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`


## <a name="additional-resources"></a>Recursos adicionales
___ 

1. [Página de información general del portal de dispositivos de Windows](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
