---
title: 'Actualización de abril de 2018: compilación 17134'
ms.date: 05/01/2018
ms.topic: article
description: Obtenga información sobre las novedades de la actualización de abril de 2018 para Windows 10 IoT.
keywords: Windows IoT, actualización de abril de 2018, notas de la versión
ms.openlocfilehash: b06378db14ba78fc5a3eb60e842e1555e56a66ac
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721758"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Notas de la versión de abril de 2018 para Windows 10 IoT
Número de compilación 17134. Mayo de 2018

Windows 10 IoT permite el desarrollo de dispositivos integrados o dedicados y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para Smart Devices.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT.

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad de esta versión del sistema operativo Windows se puede ver en [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-april-2018-update"></a>Novedades de la actualización 2018 de abril
* La [plataforma de prueba de Visual Studio](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/) que se incluye con [Visual Studio 15,6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) ahora admite pruebas en Windows 10 IOT Core. Al [escribir pruebas unitarias](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/) para un proyecto en Visual Studio 2017 que tiene como destino Windows 10 IOT Core, los desarrolladores ahora pueden ejecutar esas pruebas unitarias de forma remota en el dispositivo directamente desde Visual Studio en lugar de tener que implementar las pruebas en el dispositivo y ejecutarlas manualmente.
* Los desarrolladores pueden aprovechar las funcionalidades de la [plataforma Windows AI](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/) en Windows 10 IOT para crear dispositivos más inteligentes y acelerar la evaluación de los modelos de aprendizaje automático mediante la CPU o la GPU.
* Los fabricantes de equipos originales que quieran traer rápidamente un dispositivo habilitado para voz pueden integrar la compatibilidad con Cortana en sus dispositivos mediante la [versión preliminar del SDK de dispositivos de Cortana](https://www.aka.ms/cortanadevices).
* Los fabricantes OEM pueden aprovechar el rico conjunto de CSP disponibles en Windows para realizar la configuración y la administración remota de dispositivos a escala mediante la [Administración de dispositivos IOT de Azure](https://github.com/ms-iot/iot-core-azure-dm-client). Esta nueva implementación de ejemplo combina un cliente local, un servicio en la nube y un portal de administración, lo que permite a los operadores de IoT realizar la administración de dispositivos a escala de nube.
* Con esta versión, puede escribir [aplicaciones de consola de UWP](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp) que se ejecuten en un host de consola, como una consola de comandos o PowerShell. Las aplicaciones de consola de UWP también pueden usar las API de Win32 disponibles para las aplicaciones UWP y se pueden publicar y actualizar mediante el Microsoft Store.
* Hemos agregado un nuevo [paquete de características de Miracast](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast) para IOT Core junto con un [conjunto de API de conversión](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) para permitir que un dispositivo actúe como transmisor o receptor de Miracast.
* Hemos agregado compatibilidad con el perfil [Bluetooth A2DP-src](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) , que permite que un dispositivo actúe como origen de audio para el streaming de Bluetooth, incluidas las capacidades de control remoto a través de Bluetooth mediante el perfil AVRCP.
* Uno de nuestros paneles Qualcomm más populares, el 410C DragonBoard, se ha convertido mucho más en Flash con esta versión. Con la versión más reciente del [Panel de Windows 10 IOT Core](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), simplemente conecte el panel, colóquelo en modo flash y [parpadee el dispositivo](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice) directamente desde el panel.
* Para buscar y conectarse a redes Wi-Fi, hemos actualizado el [ejemplo de conector Wi-Fi](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS) para que esté en su par con el comando netcmd que antes quedó en desuso. En este ejemplo se usan las [API de WiFiAdapter](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) para administrar adaptadores y conexiones de red inalámbrica.
* Tenemos nuevas API relacionadas con el tiempo para establecer automáticamente el reloj del sistema en la [zona](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_) horaria y [hora local](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) en función de la ubicación del dispositivo, lo que permite a los OEM crear una experiencia integrada más simplificada.
* Tenemos nuevas API de lenguaje para establecer el [idioma](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__)de usuario preferido, la [región](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), el idioma de [voz](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) predeterminado y la [voz](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync)predeterminada.
* Con un nuevo [paquete de características de MTP](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md), puede transferir archivos a y desde un dispositivo de Windows 10 IOT Core a través de USB mediante el protocolo de transferencia multimedia (MTP). Esto incluye los archivos ubicados en el almacenamiento interno y la tarjeta SD del dispositivo, si están presentes.
* Hemos publicado un nuevo [ejemplo en github](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) y [vídeo de Channel 9](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central) en el que se muestra lo fácil que es obtener un dispositivo de IOT de Windows 10 integrado en Azure IOT central. También hemos actualizado nuestra documentación para describir [Cómo conectar los dispositivos](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) que ejecutan Windows 10 IOT Core a Azure IOT central.

## <a name="improvements-in-assigned-access"></a>Mejoras en el acceso asignado
* Hemos agregado compatibilidad con varias pantallas para casos de uso de anuncios digitales.
* La página estado de inscripción ahora incluye la capacidad de garantizar que todas las configuraciones de MDM se aplican en el dispositivo antes de especificar el acceso asignado.
* Hemos agregado la capacidad de configurar y ejecutar el iniciador de Shell además de las aplicaciones de la tienda para UWP existentes.
* Los dispositivos que usan acceso asignado se pueden configurar para que escriban automáticamente el estado deseado después de un reinicio mediante un proceso simplificado para crear y configurar una cuenta de inicio de sesión automático.
* En el caso de los dispositivos de varios usuarios, en lugar de especificar todos los usuarios, ahora es posible asignar diferentes configuraciones de acceso asignadas a Azure AD grupos o grupos de Active Directory.
* Para ayudar a solucionar problemas, ahora puedes ver informes de errores generados si una aplicación configurada con acceso asignado tiene problemas.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Características en versión preliminar para escenarios de desarrollo y pruebas
* El centro de actualización de dispositivos [versión preliminar] permite a los OEM administrar de forma global sus aplicaciones e instalar actualizaciones para el sistema operativo, las aplicaciones, la configuración y los archivos de la nube en dispositivos para mantenerlos actualizados y seguros.
* Compatibilidad con el hospedaje de [contenedores de nano Server](https://docs.microsoft.com/virtualization/windowscontainers/about/index) en ediciones de 64 bits de Windows 10 IOT Core y Enterprise, la habilitación de aplicaciones y sus datos se puede aislar entre sí y pasar rápidamente de un desarrollo a un entorno de producción o de nube al perímetro.
* El servicio Windows Atestación de estado de dispositivo [versión preliminar] utiliza características de hardware y servicios en la nube para proporcionar una prueba de alteración y la atestación remota del estado de los dispositivos en función de las métricas de nivel de hardware y los datos acreditados.
* [Azure IOT Edge](https://azure.microsoft.com/campaigns/iot-edge/) en Windows IOT [Preview] permite que las soluciones de IOT coordinen la inteligencia entre los dispositivos perimetrales y de la nube para garantizar que las aplicaciones y los servicios pueden actuar en los datos de IOT siempre que resulte más conveniente.
* Azure IoT Hub [servicio Device provisioning [versión preliminar]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) permite crear dispositivos IOT de Windows 10 con una imagen común durante la fabricación y configurarse para conectarse automáticamente en el primer arranque a Azure IOT hub para recuperar la información de aprovisionamiento específica del dispositivo.

## <a name="windows-10-iot-core-reference-images"></a>Imágenes de referencia de Windows 10 IoT Core
___ 
* Minnowboard Max
  * Procesador: Intel Atom E3825
  * Arquitectura: x86

* Modelo B de Raspberry PI 3
  * Procesador: Broadcom BCM2837
  * Arquitectura: ARM

* DragonBoard 410c
  * Procesador: Qualcomm Snapdragon 410
  * Arquitectura: ARM
  * Versión de BSP: 2120.0.0.0

## <a name="additional-information"></a>Información adicional
* En función del anuncio reciente de Intel para dejar de producir la plataforma Intel Joule (, FFUs para Intel Joule (dejó de estar en la versión anterior. Los clientes que evalúen Intel Joule (deben identificar una plataforma alternativa con uno de los otros SOC admitidos; consulte los [paneles sugeridos y SOC](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) para obtener una lista.

## <a name="known-issues"></a>Problemas conocidos
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrarse manualmente en el dispositivo.
* Los dispositivos que se han instalado a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.
