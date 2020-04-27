---
title: 'Actualización de abril de 2018: compilación 17134'
ms.date: 05/01/2018
ms.topic: article
description: Obtén información sobre las novedades de la actualización de abril de 2018 para Windows 10 IoT.
keywords: Windows IoT, actualización de abril de 2018, notas de la versión
ms.openlocfilehash: b06378db14ba78fc5a3eb60e842e1555e56a66ac
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "75721758"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Notas de la versión de la actualización de abril de 2018 para Windows 10 IoT
Número de compilación 17134. Mayo de 2018

Windows 10 IoT permite el desarrollo de dispositivos integrados o dedicados, y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para dispositivos inteligentes.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT.

## <a name="privacy-statement"></a>Declaración de privacidad

La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar en [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-april-2018-update"></a>Novedades de la actualización de abril de 2018
* La [plataforma de prueba de Visual Studio](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/) que se incluye con [Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) admite ahora pruebas en Windows 10 IoT Core. Al [escribir pruebas unitarias](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/) para un proyecto en Visual Studio 2017 que tiene como destino Windows 10 IoT Core, los desarrolladores ahora pueden ejecutar esas pruebas unitarias de forma remota en el dispositivo directamente desde Visual Studio, en lugar de tener que implementar las pruebas en el dispositivo y ejecutarlas manualmente.
* Los desarrolladores pueden aprovechar las funcionalidades de la [plataforma de IA de Windows](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/) en Windows 10 IoT para crear dispositivos más inteligentes y acelerar la evaluación de los modelos de ML mediante CPU o GPU.
* Los OEM que buscan comercializar rápidamente un dispositivo habilitado para voz pueden integrar la compatibilidad con Cortana en el dispositivo mediante la [versión preliminar del SDK de dispositivos de Cortana](https://www.aka.ms/cortanadevices).
* Los OEM pueden aprovechar el conjunto enriquecido de CSP disponibles en Windows para la configuración y la administración remotas de dispositivos a escala mediante la [Administración de dispositivos con Azure IoT](https://github.com/ms-iot/iot-core-azure-dm-client). Esta nueva implementación de ejemplo combina un cliente local, un servicio en la nube y un portal de administración, lo que permite a los operadores de IoT administrar los dispositivos a escala de nube.
* Con esta versión, puedes escribir [aplicaciones de consola para UWP](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp) que se ejecutan en un host de consola, como una consola de comandos o PowerShell. Las aplicaciones de consola para UWP también pueden usar las API de Win32 disponibles para las aplicaciones para UWP, y se pueden publicar y actualizar mediante Microsoft Store.
* Hemos agregado un nuevo [paquete de características de Miracast](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast) para IoT Core junto con un [conjunto de API de conversión](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) para permitir que un dispositivo actúe como transmisor o receptor de Miracast.
* Hemos agregado compatibilidad con el perfil [Bluetooth A2DP-SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth), que permite que un dispositivo actúe como origen de audio para el streaming Bluetooth, incluidas las funcionalidades de control remoto a través de Bluetooth mediante el perfil AVRCP.
* Uno de nuestros paneles Qualcomm más populares, DragonBoard 410c, se ha vuelto mucho más en reiniciar con esta versión. Con la versión más reciente del [Panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), simplemente conecte el panel, colóquelo en modo sobrescribir y [reinicie el dispositivo](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice) directamente desde el panel.
* Para buscar redes Wi-Fi y conectarse a ellas, hemos actualizado el [ejemplo de conector Wi-Fi](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS) para que esté a la altura del comando netcmd que anteriormente quedó en desuso. Este ejemplo usa las [API de WiFiAdapter](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) para administrar adaptadores y conexiones de red inalámbrica.
* Tenemos nuevas API relacionadas con el tiempo para establecer automáticamente el reloj del sistema en la [hora local](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) y la [zona horaria](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_) según la ubicación del dispositivo, lo que permite a los OEM crear una experiencia integrada más simplificada.
* Tenemos nuevas API de idiomas para establecer el [idioma](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__) preferido del usuario, la [región](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), el idioma predeterminado de [voz](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) y la [voz](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync) predeterminada.
* Con un nuevo [paquete de características de MTP](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md), puedes transferir archivos hacia y desde un dispositivo con Windows 10 IoT Core a través de USB mediante el protocolo de transferencia multimedia (MTP). Esto incluye los archivos ubicados en el almacenamiento interno del dispositivo y la tarjeta SD, si hay una.
* Hemos publicado un nuevo [ejemplo en GitHub](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) y un [vídeo en Channel 9](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central) que muestra lo fácil que es integrar un dispositivo de Windows 10 IoT en Azure IoT Central. También hemos actualizado la documentación para describir [cómo conectar dispositivos](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) que ejecutan Windows 10 IoT Core con Azure IoT Central.

## <a name="improvements-in-assigned-access"></a>Mejoras en Acceso asignado
* Hemos agregado soporte para varias pantallas para casos de uso de señalización digital.
* La página Estado de inscripción ahora incluye la capacidad de garantizar que todas las configuraciones de MDM se apliquen en el dispositivo antes de entrar en el acceso asignado.
* Hemos agregado la capacidad de configurar y ejecutar el Selector de Shell, además de las aplicaciones de Store para UWP existentes.
* Los dispositivos que usan el acceso asignado se pueden configurar para que adopten automáticamente un estado deseado después de un reinicio mediante un proceso simplificado para crear y configurar una cuenta de inicio de sesión automático.
* Para dispositivos de varios usuarios, en lugar de especificar todos los usuarios, ahora es posible asignar configuraciones de acceso asignado diferentes a grupos de Azure AD o grupos de Active Directory.
* Para ayudar a solucionar problemas, ahora puedes ver informes de errores generados si una aplicación configurada con acceso asignado tiene problemas.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Características en versión preliminar para escenarios de desarrollo y pruebas
* El Centro de actualización de dispositivos [versión preliminar] permite a los OEM administrar de forma global sus aplicaciones e insertar actualizaciones para el sistema operativo, las aplicaciones, la configuración y los archivos desde la nube en dispositivos para mantenerlos actualizados y protegidos.
* Compatibilidad con el hospedaje de [contenedores de Nano Server](https://docs.microsoft.com/virtualization/windowscontainers/about/index) en las ediciones de 64 bits de Windows 10 IoT Core y Enterprise, lo que permite que las aplicaciones y sus datos se puedan aislar unos de otros y pasar rápidamente de desarrollo a producción o de la nube al perímetro.
* El servicio Atestación de estado de dispositivo [versión preliminar] de Windows usa características de hardware y servicios en la nube para proporcionar protección contra alteraciones y atestación remota del estado de los dispositivos en función de las métricas de nivel de hardware y los datos acreditados.
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) en Windows IoT [versión preliminar] permite que las soluciones de IoT coordinen la inteligencia entre los dispositivos perimetrales y de la nube para garantizar que las aplicaciones y los servicios pueden actuar en función de los datos de IoT siempre que resulte más conveniente.
* El [servicio de aprovisionamiento de dispositivos [versión preliminar]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) de Azure IoT Hub permite crear dispositivos de Windows 10 IoT con una imagen común durante la fabricación y configurarlos para que se conecten automáticamente en el primer arranque a Azure IoT Hub para recuperar la información de aprovisionamiento específica del dispositivo.

## <a name="windows-10-iot-core-reference-images"></a>Imágenes de referencia de Windows 10 IoT Core
___ 
* Minnowboard Max
  * Procesador: Intel Atom E3825
  * Arquitectura: x86

* Raspberry Pi 3 modelo B
  * Procesador: Broadcom BCM2837
  * Arquitectura: ARM

* DragonBoard 410c
  * Procesador: Qualcomm Snapdragon 410
  * Arquitectura: ARM
  * Versión de BSP: 2120.0.0.0

## <a name="additional-information"></a>Información adicional
* En función del anuncio reciente de Intel para dejar de producir la plataforma Intel Joule, se interrumpieron las FFU para Intel Joule en la versión anterior. Los clientes que están pensando en Intel Joule deben identificar una plataforma alternativa con uno de los otros SoC admitidos; consulta [Paneles sugeridos y SoC](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) para obtener una lista.

## <a name="known-issues"></a>Problemas conocidos
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrarse manualmente en el dispositivo.
* Los dispositivos que se han instalado a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.
