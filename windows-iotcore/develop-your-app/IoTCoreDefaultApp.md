---
title: Aplicación predeterminada de Windows 10 IoT Core
ms.date: 08/08/2018
ms.topic: article
description: Obtenga información sobre la aplicación predeterminada de Windows 10 IoT Core y sus características.
keywords: Windows IOT, Windows 10 IOT Core, aplicación predeterminada
ms.custom: RS5
ms.openlocfilehash: a0e26d54f1c6694cd408de6f54cf0c0fba263156
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918248"
---
# <a name="windows-10-iot-core-default-app-overview"></a>Introducción a la aplicación predeterminada de Windows 10 IoT Core

> [!TIP]
> Si le gustaría ver una característica agregada a esta aplicación de ejemplo, [abra un problema](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) en github para que podamos saberlo. Si desea archivar un error, siga las instrucciones del centro de comentarios [aquí](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).

La primera vez que Flash Windows 10 IoT Core, se le presentará la aplicación Windows 10 IoT Core predeterminada en el inicio, que tiene el siguiente aspecto:

![Captura de pantalla de la aplicación predeterminada de IoT Core](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

La finalidad de esta aplicación no es solo proporcionar un shell sencillo para interactuar con la primera vez que se arranca Windows 10 IoT Core, pero se ha proporcionado código abierto para esta aplicación [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para que pueda conectarse y jugar con estas características en su propia cu aplicaciones sonalizado.

En este artículo se proporciona un resumen de las distintas características que ofrece la aplicación predeterminada de Windows 10 IoT Core, así como cómo puede aprovechar estas características diferentes para sus propias aplicaciones.

## <a name="leveraging-the-iot-core-default-app"></a>Aprovechamiento de la aplicación predeterminada de IoT Core 

> [!IMPORTANT]
> No use las imágenes del creador con fines comerciales. Si se comercializa un dispositivo, debe usar una FFU personalizada para una seguridad óptima. Puedes obtener más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

La aplicación predeterminada de IoT Core puede personalizarse y ampliarse, o bien se puede usar el código fuente como ejemplo para su propia aplicación. Para probarlo, descargue el archivo. zip de nuestros ejemplos o consulte el código de la aplicación de IoT Core predeterminada [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp). Si tiene alguna pregunta, envíe un problema en nuestro repositorio de ejemplos [aquí](https://github.com/Microsoft/Windows-iotcore-samples/issues).

Como se muestra en la [sección configuración](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) siguiente, en algunos casos, puede configurar la configuración y las características predeterminadas en el sistema del cliente en nombre del usuario final. Sin embargo, si activa esta configuración y las características de forma predeterminada o si los diagnósticos están por encima de la configuración básica, debe:

* Notifique al usuario final que se han habilitado estas características y proporcione al usuario final el vínculo a la Página Web de la declaración de privacidad de Microsoft [aquí](http://go.microsoft.com/fwlink/?LinkId=521839). 
* Consentimiento seguro del usuario final relevante para habilitar dichas características de forma predeterminada (según lo requiera la ley aplicable).
* Proporcionar a los usuarios finales la capacidad de volver a cambiar la configuración de diagnóstico a la configuración básica.
* Si habilita las cuentas de Microsoft y tiene acceso a los datos del usuario final, si el usuario final elimina la cuenta de Microsoft, debe habilitar la eliminación simultánea de todos los datos de la cuenta de Microsoft del usuario final en el dispositivo. 

## <a name="out-of-box-experience-oobe"></a>La experiencia rápida (OOBE)

La configuración rápida de la aplicación predeterminada de IoT Core es tan eficiente como se obtiene. Las primeras páginas solicitarán un idioma y una configuración de Wi-Fi predeterminados. A partir de ahí, para que la aplicación sea compatible con RGPD, debe tener una pantalla de datos de diagnóstico y, si tiene previsto realizar un seguimiento de la ubicación, deberá tener también una pantalla de permisos de ubicación. A continuación se muestran ejemplos de ambos. 

![configuración de ubicación de OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![configuración de diagnóstico para OOBE](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a>Barra de comandos
La barra de comandos es la barra horizonatal persistente que se encuentra en la parte inferior de la pantalla. Esto proporciona acceso sencillo a la siguiente funcionalidad de:
- Navegación de página hacia delante y hacia atrás
- Información básica del dispositivo sin pasar a la página actual
- Activar o desactivar el modo de pantalla completa
- Métodos abreviados avanzados
- Botones específicos de la página

Hay un gran número de botones en la barra de comandos y, a veces, estos botones pueden ser confusos u ocultos. Para expandir la barra de comandos y acceder a esos botones, presione el botón de menú de la parte inferior derecha:

![Cómo expandir la barra de comandos](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a>Menú Inicio-reproducir

En el menú Inicio se encuentra en directo la mayoría de las características de plug and Play.

### <a name="weather"></a>El Tiempo
Con los datos del servicio de Meteorología nacional, la página de Meteorología representa información meteorológica en su ubicación actual.

### <a name="web-browser"></a>Explorador Web
El explorador Web permite extraer la mayoría de los sitios de la Web.

### <a name="music"></a>Música
En esta página se reproducirán archivos MP3 y WAV de la **biblioteca de música**, a los que se puede tener acceso a través del portal de [dispositivos de Windows](../manage-your-device/DevicePortal.md).  Para cargar archivos en el reproductor de música, debe ir al portal de dispositivos de Windows, hacer clic en la lista desplegable "aplicaciones", navegar a "explorador de archivos", seleccionar "música" y cargar los archivos desde allí.


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a>Presentación
Esta página mostrará los archivos de imagen PNG o JPEG de la **biblioteca de imágenes**, a los que se puede tener acceso a través del [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md). Para cargar imágenes en la presentación de diapositivas, debe ir al portal de dispositivos de Windows, hacer clic en la lista desplegable "aplicaciones", navegar a "explorador de archivos", seleccionar "imágenes" y cargar los archivos desde allí.


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a>Dibujar
Esta página le permite probar las funcionalidades de entrada manuscrita de Windows 10 IoT Core.

## <a name="start-menu---explore"></a>Menú Inicio-explorar 

### <a name="apps"></a>Aplicaciones 
Esta página permite iniciar otras aplicaciones de primer plano instaladas en el dispositivo. Al iniciar una aplicación, se suspenderá la aplicación predeterminada de IoT Core, que se puede volver a iniciar mediante App Manager en el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md).

No es necesario nada especial para que la aplicación de primer plano aparezca en la página, simplemente [Instale](AppInstaller.md) o [implemente](AppDeployment.md) la aplicación. Después de una instalación o una implementación correcta, vuelva a navegar a la página aplicaciones para actualizar la lista de aplicaciones.

Tenga en cuenta que hay un par de aplicaciones relacionadas con el sistema operativo generadas automáticamente que se filtran, puede encontrar la lista de nombres de aplicación [aquí](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).

### <a name="notifications"></a>Notificaciones
En esta página se enumeran las últimas 20 notificaciones, ya que se ha iniciado la aplicación predeterminada de IoT Core. Cuando la aplicación predeterminada de IoT Core se ejecuta en modo de depuración, se agregan botones que crearán notificaciones de prueba.

### <a name="logs"></a>Registros
En esta página se enumeran los registros de errores o bloqueos generados automáticamente que se pueden quitar del dispositivo y analizarlos.

### <a name="github"></a>GitHub
Esta página le llevará a la ubicación de GitHub de código abierto del código de aplicación predeterminado de IoT Core.

## <a name="start-menu---windows-device-portal"></a>Menú Inicio-Windows Device portal

En las páginas de esta sección se aprovechan las API de REST de Windows Device portal, que requiere que inicie sesión con sus credenciales de Windows Device portal.

## <a name="device-information"></a>Información del dispositivo

Esta página le permite ver las distintas características del dispositivo, como Ethernet, la versión del sistema operativo, los dispositivos conectados, etc.

## <a name="command-line"></a>Línea de comandos

Esta página le permite ejecutar comandos directamente en el dispositivo.

Para habilitar esta característica, debe establecer una clave del registro para que la aplicación pueda ejecutar los comandos. La primera vez que intente ejecutar un comando, verá un vínculo que le permite establecer la clave del registro mediante una llamada a Windows Device portal. Haga clic en el vínculo para habilitar el dispositivo para ejecutar comandos.

Algunos comandos requieren acceso de administrador. Por motivos de seguridad, la aplicación usa una cuenta que no es de administrador de forma predeterminada para ejecutar comandos. Si necesita ejecutar un comando como administrador, puede escribir "RunAsAdmin <your command>" en el símbolo del sistema.

## <a name="settings"></a>Configuración
Aquí podrá configurar una serie de opciones, como Wi-Fi, Bluetooth, opciones de energía, etc.

### <a name="app-settings"></a>Configuración de la aplicación
La sección configuración de la **aplicación** permite configurar varias opciones para las páginas de la aplicación.  

Algunas de las opciones que puede personalizar son:

##### <a name="general-settings"></a>Configuración general
* Establecer la página predeterminada que aparece cuando se inicia la aplicación
* Habilitar o deshabilitar el protector de la

##### <a name="weather-settings"></a>Configuración meteorológica
* Cambiar la ubicación
  > Esta característica solo está habilitada si se ha proporcionado un [token de servicio de mapa de Bing](https://msdn.microsoft.com/library/ff428642.aspx)válido.  Para pasar el token a la aplicación, cree un archivo **MapToken. config** en la carpeta LocalState de la aplicación (por ejemplo, C:\Data\USERS\\[cuenta de usuario] \AppData\Packages\\[nombre completo del paquete] \LocalState\MapToken.config) y reinicie la aplicación.
* Expandir el mapa
* Habilitar o deshabilitar el volteo de mapas para que el mapa y el interruptor meteorológico se coloquen periódicamente para evitar la grabación de la pantalla

##### <a name="web-browser-settings"></a>Configuración del explorador Web
* Establecer la Página principal del explorador Web

##### <a name="slideshow-settings"></a>Configuración de la presentación
* Establecer el intervalo de presentación de diapositivas

##### <a name="appearance"></a>Aparición
* Usar activos de MDL2 en lugar de emojis para los iconos de icono
* Establecer el ancho y el alto del mosaico
* Establecer escala de IU: el escalado automático se establece de forma predeterminada
* Establecer el color del mosaico

#### <a name="system"></a>Sistema
Cambiar el idioma, la distribución del teclado y la zona horaria.

#### <a name="network--wi-fi"></a>Red & Wi-Fi
Ver las propiedades del adaptador de red o conectarse a una red Wi-Fi disponible.

#### <a name="bluetooth"></a>Bluetooth,
Emparejar con un dispositivo Bluetooth.

#### <a name="app-updates"></a>Actualizaciones de aplicaciones
Compruebe si hay actualizaciones de la aplicación o cambie la configuración de actualización automática.

#### <a name="power-options"></a>Opciones de energía
Reiniciar o apagar el dispositivo.

#### <a name="diagnostics"></a>Diagnóstico
Seleccione la cantidad de datos de diagnóstico que desea proporcionar a Microsoft.  Se recomienda a los usuarios que opten por los datos de diagnóstico **completos** para que podamos diagnosticar problemas rápidamente y realizar mejoras en el producto.

##### <a name="basic"></a>Básico 
Envíe solo información sobre el dispositivo, su configuración y capacidades, y si funciona correctamente.

##### <a name="full"></a>Completo
Enviar todos los datos de diagnóstico básicos, junto con información sobre los sitios web que se examinan y cómo se usan las aplicaciones y características, además de información adicional sobre el estado del dispositivo, la actividad del dispositivo y el informe de errores mejorado.

#### <a name="location"></a>Ubicación
Permita o deniegue el acceso de la aplicación a su ubicación.
