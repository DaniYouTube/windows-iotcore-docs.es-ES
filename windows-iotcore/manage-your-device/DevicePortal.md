---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo usar el Windows Device Portal para configurar y administrar de forma remota el dispositivo.
keywords: portal de dispositivo remoto, de Windows iot, Windows Device Portal,
ms.openlocfilehash: 715e9c138e86efcd82b485d832c5fbdd536398dd
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514307"
---
# <a name="windows-device-portal"></a>Windows Device Portal
   La herramienta Windows Device Portal (WDP) le permite configurar y administrar el dispositivo de forma remota a través de la red local.
Las características principales se documentan en el [página de información general de Windows Device Portal](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)

![Dispositivo principal del Portal](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> No use maker imágenes para la comercialización. Si se commercializing un dispositivo, debe usar un FFU personalizado para una seguridad óptima. Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

> [!WARNING]
> Depuración de kernel en vivo actualmente se producen errores para dispositivos ARM. Estamos trabajando para conseguir que esto se ha corregido.

> [!IMPORTANT]
> Si está creando un dispositivo comercial abierto para la implementación comercial en una "instalación específico o limitado" (es decir, almacén de fábrica o comercial) donde el usuario final realiza la configuración final y documentar los clientes que deben [obtener una certificado de WDP e instalar en tanto WDP y conecta los exploradores y las contraseñas se cambian en WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), a continuación, uso de WDP en esta instancia comercial estrecha es aceptable. Imágenes de venta directa en este escenario deben seguir *no* incluyen IOT_TOOLKIT, pero debe usar el paquete IOT_WEBBEXTN para extraer WDP. 

## <a name="shared-documentation"></a>Documentación compartida
WDP es una herramienta de desarrollador que se comparte entre todos los dispositivos Windows 10. Cada producto tiene sus propias características únicas, pero la funcionalidad básica es la misma.
Documentación de las características principales se encuentran en el [página de información general de Windows Device Portal](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal). El resto de la documentación siguiente será IoT específico.

## <a name="set-up"></a>Configuración

Hay dos maneras de obtener el Windows Device Portal en marcha.

### <a name="1-windows-10-iot-dashboard"></a>1. Panel de Windows 10 IoT

En primer lugar, es conveniente que descargue el [panel de Windows 10 IoT](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard), una herramienta para desarrolladores que facilita la configuración de nuevos dispositivos. Una vez que ha usado el panel que se instalará una imagen de Windows 10 IoT Core en el dispositivo, compruebe que el dispositivo aparece en "Mis dispositivos". 

Desde allí, use el botón de puntos suspensivos en "Acciones" para seleccionar "Abrir en Portal de dispositivos". Desde allí, se le dirigirá a la página de autenticación de dispositivo Portal donde, a menos que cambie las credenciales inicialmente, las credenciales predeterminadas son: 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2. Browser
Si no se puede encontrar el dispositivo en el panel o prefiere omitir el uso del panel, también puede abrir Device Portal escribiendo la dirección IP del dispositivo más `:8080` al final. Cuando se realiza correctamente, debe tener un aspecto similar al siguiente:


   ![IoTDashboard ver dispositivos](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>Características específicas de IoT

### <a name="device-settings"></a>Configuración del dispositivo

IoT Core agrega una casilla de verificación para habilitar o deshabilitar la [teclado en pantalla](../develop-your-app/OnScreenKeyboard.md)
> [!NOTE]
> Esta casilla de verificación tiene un problema conocido, donde "parpadeará" desde comprueba para que no es activado. Actualice la página (F5) después de hacer clic para asegurarse de que la casilla muestre el estado deseado.

### <a name="apps"></a>Aplicaciones
Proporciona funcionalidad de instalación o desinstalación de paquetes AppX y agrupaciones en el dispositivo.
![Lista de aplicaciones](../media/DevicePortal/AppList.png)

IoT Core es único, que solo permite que una aplicación en primer plano ejecutar al mismo tiempo. Para asegurarse de que este es el caso, se modifica la lista de aplicaciones. En el **inicio** columna, puede seleccionar tantas aplicaciones en segundo plano para iniciarse de forma predeterminada, pero solo se puede establecer una aplicación en primer plano.  

### <a name="app-file-explorer"></a>Explorador de archivos de la aplicación

El Explorador de archivos de la aplicación muestra los directorios que se pueden tener acceso sus aplicaciones.

* CameraRoll se comparte entre todas las aplicaciones
* Documentos se comparte entre todas las aplicaciones
* LocalAppData contiene carpetas específicas de cada aplicación. Esta carpeta será el mismo nombre que la aplicación y otras aplicaciones no pueden acceder a él.

### <a name="debugging"></a>Depuración

#### <a name="kernel-dumps"></a>Volcados de memoria del núcleo
![Depuración de volcados de memoria del núcleo](../media/DevicePortal/Debug1.png)

Los bloqueos del sistema será automáticamente registran y están disponibles para ver a través de la herramienta de administración web.  A continuación, puede descargar el volcado de memoria del núcleo e intentar averiguar qué está sucediendo.

#### <a name="process-dumps"></a>Volcados de proceso
![Depuración de volcados de memoria de proceso](../media/DevicePortal/Debug2.png)

Esto es similar a volcados de memoria del kernel en vivo, pero para los procesos de modo de usuario. Al hacer clic en el **descargar** botón provocarán un minivolcado' ', y se descargará todo el estado de ese proceso. Esto es útil para depurar procesos francesa.

#### <a name="kernel-crash-settings"></a>Configuración de bloqueo de kernel
![Configuración de bloqueo de kernel](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>Bluetooth
Esta página muestra todos los dispositivos bluetooth emparejado y todos los dispositivos que son reconocibles. Para emparejar con otro dispositivo Bluetooth, el dispositivo entrará en modo de emparejamiento y espere a que aparezca en la lista dispositivos disponibles.  
![Lista de dispositivos Bluetooth](../media/DevicePortal/Bluetooth.png)

Haga clic en **vínculo par** para emparejar el dispositivo. Si el dispositivo requiere un PIN para emparejamiento, aparecerá un cuadro de mensaje muestra el PIN. Una vez que se corresponde el dispositivo, se mostrará en la lista de dispositivos emparejada. Puede anular par haciendo clic en el dispositivo **quitar**. 

Una vez que navegue a la página de Bluetooth, el dispositivo podrán detectar otros dispositivos. También puede encontrarlo en su PC o teléfono y emparéjelo desde allí.

Encontrará más información sobre el bluetooth en el [bluetooth página](https://go.microsoft.com/fwlink/?linkid=823223).

### <a name="iot-onboarding"></a>Incorporación de IoT

IoT Onboarding proporciona compatibilidad para configurar las opciones de conectividad de Wi-Fi de un dispositivo de IoT.

**Conexión compartida a Internet (ICS)** conexión compartida a Internet le permite compartir el acceso a Internet del dispositivo con otros dispositivos conectados al dispositivo a través de la SoftAP Wi-Fi.
Para usar esta característica, debe tener acceso a internet (por ejemplo, mediante una conexión LAN con cable) el dispositivo de Windows 10 IoT.  En ' conectividad -> incorporación -> clic SoftAP configuración 'enable' y establezca el nombre SSID y la contraseña.  A continuación, en "Conectividad -> conexión compartida a Internet" de "Adaptador Wi-FI de Microsoft directo Virtual #2", seleccione 'adaptador de punto de acceso' y 'adaptador de red compartida' Seleccione el adaptador ethernet con cable.  Por último, haga clic en "start acceso compartido".  Una vez iniciado, conecte un dispositivo de Wi-Fi habilitada independiente para el SoftAP en el dispositivo Windows 10 IoT.  Una vez establecida una conexión de su dispositivo Wi-Fi habilitada independiente será capaz de conectarse a internet a través de su dispositivo Windows 10 IoT.

> [!NOTE]
> ICS está deshabilitado cuando existe un perfil de Wi-Fi en el dispositivo. Por ejemplo, se deshabilitará ICS si se conecta a un punto de acceso Wi-Fi y compruebe "Crear perfil (automáticamente volver a conectar)".

**Configuración de SoftAP** The SoftAP configuración le permite controlar si SoftAP su dispositivo está habilitada.  También proporciona un medio para configurar su SoftAP SSID y la WPA2-PSK clave que son necesarios para conectar el SoftAP desde otro dispositivo.

**Configuración de incorporación de AllJoyn** la configuración de incorporación de AllJoyn le permiten controlar o no conexión de Wi-Fi del dispositivo se puede configurar a través AllJoyn incorporación productor de su dispositivo.  Cuando un dispositivo independiente que se ejecuta un consumidor de incorporación de AllJoyn aplicación se conecta a su SoftAP de Windows 10 IoT, la aplicación de consumidor de incorporación de AllJoyn puede usarse para configurar el adaptador de Wi-Fi del dispositivo de IoT.  Cuando se habilita, la aplicación de productor de incorporación de AllJoyn (IoTOnboarding) usa el método de autenticación ECDHE_NULL. 

> [!NOTE]
> Para usar AllJoyn incorporación con Windows 10 IoT compilaciones 10.0.14393 o versiones anteriores requiere una actualización para el <strong>IotOnboarding</strong> ejemplo que puede ser [descargar aquí](https://github.com/ms-iot/samples).

![Incorporación a AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![incorporación en ICS](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> Adaptador de punto de acceso es el adaptador de Wi-Fi que actúan como un punto de acceso Wi-Fi (normalmente tiene una dirección IP como 192.168.137.1).
> Adaptador de red compartida es el adaptador que se conecta a Internet (p. ej.: Adaptador Ethernet).

![Incorporar en el punto de acceso temporal](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> SoftAP SSID tendrá automáticamente el prefijo por "AJ_" si AllJoyn incorporación está habilitado y postfija con la dirección MAC del adaptador Wi-Fi. La frase de contraseña SoftAP debe tener entre 8 y 63 caracteres ASCII.


### <a name="tpm-configuration"></a>Configuración de TPM
El módulo de plataforma segura (TPM) es un coprocesador criptográfico que incluye capacidades de generación de números aleatorios, generación segura de claves criptográficas y la limitación de su uso. También incluye capacidades como la autorización remota y almacenamiento sealed. Para obtener información sobre el TPM y la seguridad en IoT Core, visite la [crear dispositivos seguros](../secure-your-device/BuildingSecureDevices.md) página y el [TPM](../secure-your-device/TPM.md) página.

> [!IMPORTANT]
> Limpet.exe usa para formar parte de Windows IoT Core. A partir de octubre de 2018, está ahora disponible como un porject de código abierto en [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client).

Para facilitar las pruebas, se tiene una versión pregenerada de Limpet.exe disponible sin firmar y puede descargarse desde WDP. Simplemente deberá ir a la pestaña "Configuración de TPM" y haga clic en el botón "Instalar Latest". 

> [!NOTE]
> Esta versión de Limpet.exe no debe enviarse con el producto final. En su lugar, deberá compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.

### <a name="azure-clients-configuration"></a>Configuración de clientes de Azure

Dispositivos de IoT pueden administrarse de forma remota a través de servicios en la nube. Azure proporciona un conjunto muy rico de servicios para habilitar estos escenarios. Hemos creado a un cliente de administración de dispositivos que complementa el servicio IoT Hub de Azure y de servicio de aprovisionamiento de dispositivos (DPS de Azure) de la plataforma de Windows y que también expone varias características de capacidad de administración de Windows.

Los clientes se proporcionará como proyectos de código abierto. Para facilitar la fase de pruebas, proporcionaremos archivos binarios compilados previamente. Puede usar la ficha 'Azure clientes' en WDP para instalar y ejecutar los archivos binarios de prueba.

> [!NOTE]
> Esta versión de las herramientas no debe enviarse con el producto final. En su lugar, deberá compilar el proyecto de código abierto, firmarlo y empaquetarlo con la imagen.

Una vez que los proyectos de código abierto están disponibles para su uso, actualizaremos esta documentación.

### <a name="remote"></a>Control remoto
El servidor remoto de Windows IoT permite a los usuarios ver lo que se muestra su dispositivo sin necesidad de conectarse a un monitor físico para el teclado.


## <a name="additional-information"></a>Información adicional 

### <a name="changing-the-default-port"></a>Cambiar el puerto predeterminado
 
1. Inicie powershell y [conectarse al dispositivo.](../connect-your-device/PowerShell.md)
2. Descargar [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) herramienta, compílelo y cópielo en el dispositivo. 
3. Tomar posesión de la clave del registro para el servicio mediante la ejecución

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. Establezca el puerto deseado al modificar la configuración del registro 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. Reinicie el servicio WebManagement mediante la ejecución siguiente o reiniciando el dispositivo

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>Uso de HTTPS 

Si desea usar HTTPS, en primer lugar tomar la posesión de la clave del registro como se describe en la sección anterior y establecer las claves del registro HttpsPort y EncryptionMode como la siguiente y, a continuación, reinicie el servicio de webmanagement

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a>Portal de aprovisionamiento de dispositivos con un certificado SSL personalizado

En Windows 10 Creators Update, el de Windows Device Portal agregado a los administradores de dispositivos instalar un certificado personalizado para su uso en la comunicación HTTPS.

Para obtener más información, [lea la documentación en los documentos de Windows Device Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl). 


## <a name="additional-resources"></a>Recursos adicionales
___ 

1. [Página de información general de Windows Device Portal](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
