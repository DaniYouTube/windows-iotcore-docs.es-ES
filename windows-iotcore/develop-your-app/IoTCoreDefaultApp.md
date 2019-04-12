---
title: Aplicación de Windows 10 IoT Core predeterminada
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Obtenga información sobre la aplicación de predeterminado de Windows 10 IoT Core y sus características.
keywords: Windows iot core de windows 10 iot, aplicación predeterminada
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514304"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Información general de aplicación de Windows 10 IoT Core predeterminada

> [!TIP]
> Si encuentra que gustaría ver una característica agregada a esta aplicación de ejemplo, [abra una incidencia](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) en GitHub para hacernos saber. Si desea archivar un error, siga las instrucciones para el centro de comentarios [aquí](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).

Cuando inicialmente flash de Windows 10 IoT Core, se le mostrará con Windows 10 IoT Core predeterminado ella tras el inicio, que tiene este aspecto:

![Captura de pantalla de la aplicación predeterminada de IoT Core](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

El propósito de esta aplicación no es solo para proporcionarle un shell para interactuar con cuando arranca por primera vez seguridad de Windows 10 IoT Core descriptivo, pero se ha abierto el código para esta aplicación [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para que puede de plug and play con estos características en sus propias aplicaciones personalizadas.

En este artículo le proporcionará un resumen de las diferentes características que la aplicación de predeterminado de Windows 10 IoT Core ofrece también cómo puede aprovechar estas características diferentes para sus propias aplicaciones.

## <a name="leveraging-the-iot-core-default-app"></a>Aprovechamiento de la aplicación predeterminada de IoT Core 

> [!IMPORTANT]
> No use maker imágenes para la comercialización. Si se commercializing un dispositivo, debe usar un FFU personalizado para una seguridad óptima. Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

Se pueden personalizar y extender la aplicación predeterminada de IoT Core, o puede usar el código fuente como ejemplo para su propia aplicación. Para probar esto por sí mismo, descargue el archivo zip de nuestros ejemplos o revise el código para la aplicación predeterminada de IoT Core [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp). Si tiene alguna pregunta, registre un problema en nuestro repositorio de ejemplos [aquí](https://github.com/Microsoft/Windows-iotcore-samples/issues).

Como se muestra en el [sección configuración](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) a continuación, en algunos casos, puede configurar características y la configuración predeterminada en el sistema de cliente en nombre del usuario final. Sin embargo, si desactiva estas opciones y características de forma predeterminada o si diagnósticos están por encima de la configuración básica, debe:

* Notificar al usuario final que estas características han sido enable y proporcionan al usuario final con el vínculo a la página de web de declaración de privacidad de Microsoft [aquí](http://go.microsoft.com/fwlink/?LinkId=521839). 
* Proteja el consentimiento del usuario final correspondiente para habilitar estas características de forma predeterminada (según sea necesario por la ley aplicable).
* Proporcionar a los usuarios finales la capacidad de volver a cambiar la configuración de diagnóstico a la configuración básica.
* Si habilita Microsoft Accounts y tener acceso a los datos de usuario final, si el usuario final elimina la Account de Microsoft, debe habilitar su eliminación simultánea de datos de Microsoft Account todas las del usuario final en el dispositivo. 

## <a name="out-of-box-experience-oobe"></a>Experiencia de out-of-Box (OOBE)

Es tan eficiente a medida que la experiencia de out-of-box para la aplicación predeterminada de IoT Core. Las primeras páginas le pedirá una configuración predeterminada de idioma y wi-fi. Desde allí, en orden para su aplicación para que sea compatible con GDPR, debe tener una pantalla de datos de diagnóstico y, si planea realizar un seguimiento de ubicación, deberá tener también una pantalla de permisos de ubicación. A continuación se muestran ejemplos de ambos. 

![Configuración de ubicación de OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![configuración de diagnóstico de la bienvenida de Windows](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>Barra de comandos
La barra de comandos es la barra de horizonatal persistente en la parte inferior de la pantalla. Esto proporciona un acceso sencillo a la funcionalidad siguiente:
- Navegación de páginas hacia delante y hacia atrás
- Información básica del dispositivo sin salir de la página actual
- Activar o desactivar el modo de pantalla completa
- Métodos abreviados de avance
- Botones de página específicos

Hay muchos botones en la barra de comandos y, a veces, estos botones pueden ser confuso u oculto. Para expandir la barra de comandos y obtener acceso a esos botones, haga clic en el botón de menú en la parte inferior derecha:

![Cómo expandir la barra de comandos](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>Iniciar menú - Play

El menú Inicio es donde residen la mayoría de las características de plug and play.

### <a name="weather"></a>El Tiempo
Con datos del servicio meteorológico nacional, la página de tiempo representa la información meteorológica en su ubicación actual.

### <a name="web-browser"></a>Explorador Web
El explorador web permite extraer la mayoría de los sitios de la web.

### <a name="music"></a>Música
Esta página reproducirá los archivos MP3 y WAV desde el **biblioteca de música**, que se puede acceder mediante el [Windows Device Portal](../manage-your-device/DevicePortal.md).  Para cargar archivos en el Reproductor de música, deberá navegar a la de Windows Device Portal, haga clic en la lista desplegable de "Aplicaciones", vaya a "Explorador de archivos", seleccione "Música" y cargar los archivos a partir de ahí.


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>Presentación
Esta página mostrará los archivos de imagen PNG o JPEG desde el **biblioteca imágenes**, que puede obtenerse a través de la [Windows Device Portal](../manage-your-device/DevicePortal.md). Para cargar imágenes en la presentación de diapositivas, deberá navegar a la de Windows Device Portal, haga clic en la lista desplegable de "Aplicaciones", vaya a "Explorador de archivos", seleccione "Imágenes" y cargar los archivos a partir de ahí.


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>Dibujar
Esta página permite probar las capacidades de Windows 10 IoT Core escritura a mano.

## <a name="start-menu---explore"></a>Menú - Inicio explorar 

### <a name="apps"></a>Aplicaciones 
Esta página permite iniciar otras aplicaciones de primer plano instaladas en el dispositivo. Iniciar una aplicación, se suspenderá IoT Core predeterminado aplicación, que puede ser una nueva versión mediante el Administrador de la aplicación en [Windows Device Portal](../manage-your-device/DevicePortal.md).

Se necesita nada especial para que la aplicación de primer plano que aparece en la página, simplemente [instalar](AppInstaller.md) o [implementar](AppDeployment.md) la aplicación. Después de la correcta instalación o implementación, vuelva a navegar a la página de aplicaciones para actualizar la lista de aplicaciones.

Tenga en cuenta que existen un par de SO generado automáticamente relacionados con las aplicaciones que se filtran, puede encontrar la lista de nombres de aplicación [aquí](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).

### <a name="notifications"></a>Notificaciones
Esta página mostrará una lista de los últimos 20 notificaciones desde que se inició la aplicación predeterminada de IoT Core. Cuando la aplicación de IoT Core predeterminada se ejecuta en modo de depuración, se agregan botones que creará la prueba de las notificaciones.

### <a name="logs"></a>Registros
Esta página mostrará cualquier automáticamente registros generados por el bloqueo o error, que, a continuación, pueden retirar el dispositivo y analizar.

### <a name="github"></a>GitHub
Esta página le llevará a la ubicación de GitHub con código abierto del código de aplicación predeterminado de IoT Core.

## <a name="start-menu---windows-device-portal"></a>Menú - Inicio de Windows Device Portal

Las páginas de esta sección aprovechan las API de REST de Windows Device Portal, que requiere que inicie sesión con sus credenciales de Windows Device Portal.

## <a name="device-information"></a>Información del dispositivo

Esta página permite ver las distintas características del dispositivo incluyen Ethernet OS versión, los dispositivos conectados y mucho más.

## <a name="command-line"></a>Línea de comandos

Esta página permite ejecutar comandos directamente en el dispositivo.

Para habilitar esta característica que tiene que establecer una clave del registro para que la aplicación puede ejecutar los comandos. La primera vez que intenta ejecutar un comando verá un vínculo que le permite establecer la clave del registro mediante una llamada a Windows Device Portal. Haga clic en el vínculo para habilitar el dispositivo ejecutar comandos.

Algunos comandos requieren acceso de administrador. Por motivos de seguridad la aplicación usa una cuenta sin derechos administrativos de forma predeterminada para ejecutar comandos. Si necesita ejecutar un comando como un administrador puede escribir "RunAsAdmin <your command>" en el símbolo del sistema de línea de comandos.

## <a name="settings"></a>Configuración
Podrá configurar varias opciones de configuración incluidas aquí Wi-Fi, Bluetooth, opciones de energía y mucho más.

### <a name="app-settings"></a>Configuración de la aplicación
El **configuración de la aplicación** sección permite configurar diversas opciones para las páginas en la aplicación.  

Algunas de las configuraciones que puede personalizar son:

##### <a name="general-settings"></a>Configuración general
* Establecer la página predeterminada que aparece cuando se inicia la aplicación
* Habilitar o deshabilitar el protector de pantalla

##### <a name="weather-settings"></a>Configuración de meteorología
* Cambiar la ubicación
  > Esta característica solo está habilitada si se ha proporcionado un válido [Bing mapa de servicio de Token](https://msdn.microsoft.com/library/ff428642.aspx).  Para pasar el token a la aplicación, cree un **MapToken.config** archivo en la carpeta LocalState de la aplicación (por ejemplo, C:\Data\USERS\\\AppData\Packages [cuenta de usuario]\\\LocalState\ [nombre completo del paquete] MapToken.config) y reinicie la aplicación.
* Expanda el mapa
* Habilitar o deshabilitar asignar Voltear para que el mapa y el conmutador meteorológicos coloca periódicamente para evitar la grabación en pantalla

##### <a name="web-browser-settings"></a>Configuración del explorador Web
* Establecer la página principal del explorador Web

##### <a name="slideshow-settings"></a>Configuración de presentación con diapositivas
* Establecer el intervalo de presentación con diapositivas

##### <a name="appearance"></a>Apariencia
* Use MDL2 activos en lugar de Emojis para los iconos de mosaico
* Establecer el icono ancho y alto
* Conjunto de escalado de la interfaz de usuario: el escalado automático se establece de forma predeterminada
* Establecer el color del icono

#### <a name="system"></a>Sistema
Cambiar el idioma, la distribución del teclado y la zona horaria.

#### <a name="network--wi-fi"></a>Red & Wi-Fi
Ver propiedades del adaptador de red o conectarse a una red Wi-Fi disponible.

#### <a name="bluetooth"></a>Bluetooth
Emparejar con un dispositivo Bluetooth.

#### <a name="app-updates"></a>Actualizaciones de aplicaciones
Comprobar si hay actualizaciones de la aplicación o cambiar la configuración de actualización automática.

#### <a name="power-options"></a>Opciones de energía
Reinicio o apagado del dispositivo.

#### <a name="diagnostics"></a>Diagnóstico
Seleccione la cantidad de datos de diagnóstico que desea proporcionar a Microsoft.  Le animamos a los usuarios participar en **completa** datos de diagnóstico para que podamos diagnosticar rápidamente problemas y realizar mejoras en el producto.

##### <a name="basic"></a>Básico 
Enviar sólo información sobre el dispositivo, su configuración y capacidades, y si se realiza correctamente.

##### <a name="full"></a>Completo
Enviar todos los datos de diagnóstico básicos, junto con información sobre los sitios Web que examina y cómo usar aplicaciones y características, además de información adicional sobre el estado del dispositivo, la actividad del dispositivo e informes de error mejorados.

#### <a name="location"></a>Ubicación
Permitir o denegar el acceso a la aplicación a su ubicación.
