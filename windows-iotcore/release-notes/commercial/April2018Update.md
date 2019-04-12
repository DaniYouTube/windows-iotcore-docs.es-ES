---
title: Actualización de abril de 2018 - compilación 17134
author: saraclay
ms.author: saclayt
ms.date: 05/01/2018
ms.topic: article
description: Obtenga información sobre lo que ha de la de abril de 2018 actualización para Windows 10 IoT.
keywords: Windows IoT, la actualización de abril de 2018, notas de la versión
ms.openlocfilehash: b61ee94651c2bea0ec0582669b62867d47c85a0c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514271"
---
# <a name="april-2018-update-release-notes-for-windows-10-iot"></a>Notas de actualización de abril de 2018 de Windows 10 IoT
17134 del número de compilación. Mayo de 2018

Windows 10 IoT permite el desarrollo de dispositivos incrustados o dedicado de propósito y es la opción para los OEM y los desarrolladores que crean soluciones de Windows para dispositivos inteligentes.

Este documento proporciona información que complementa otros contenido y la documentación de esta versión de Windows 10 IoT.

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad para esta versión del sistema operativo Windows se puede ver en [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-april-2018-update"></a>Novedades de abril de 2018 Update
* El [Visual Studio Test Platform](https://blogs.msdn.microsoft.com/devops/2017/02/12/evolving-the-visual-studio-test-platform-part-4-together-in-the-open/) que se incluye con [Visual Studio 15.6 RTW](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes#Win10_IoT_Core_Testing_Support) ahora es compatible con las pruebas en Windows 10 IoT Core. Cuando [escribir pruebas unitarias](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/) para un proyecto de Visual Studio 2017 que tenga como destino Windows 10 IoT Core, los desarrolladores ahora pueden ejecutar esas pruebas unitarias remotamente en el dispositivo directamente desde Visual Studio en lugar de tener que implementar las pruebas en el dispositivo y ejecutarlos manualmente.
* Los desarrolladores pueden aprovechar las capacidades de la [plataforma de inteligencia artificial Windows](https://blogs.windows.com/buildingapps/2018/03/07/ai-platform-windows-developers/) en Windows 10 IoT para crear más dispositivos inteligentes y acelerar el aprendizaje automático de uso de CPU o GPU de evaluación del modelo.
* Los OEM que desean para poner un dispositivo habilitado por voz al mercado rápidamente pueden integrar el soporte técnico de Cortana en sus dispositivos mediante el [preview del SDK de dispositivos de Cortana](http://www.aka.ms/cortanadevices).
* Los OEM pueden aprovechar el amplio conjunto de CSP disponibles en Windows para realizar la configuración remota y administración de dispositivos a escala con [administración de dispositivos de IoT de Azure](https://github.com/ms-iot/iot-core-azure-dm-client). Esta nueva implementación de ejemplo combina un cliente local, el servicio en la nube y el portal de administración, permitir que los operadores de IoT realizar la administración de dispositivos a escala de nube.
* Con esta versión, puede escribir [consola las aplicaciones para UWP](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp) que se ejecutan en un host de consola, como una consola de comandos o PowerShell. Aplicaciones de consola de UWP también puede usar las API de Win32 en aplicaciones para UWP y se pueden publicar y actualizar a través de la Microsoft Store.
* Hemos agregado un nuevo [paquete de artículos de Miracast](https://docs.microsoft.com/windows/iot-core/connect-your-device/miracast) para IoT Core junto con un [conjunto de API de conversión](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) para habilitar un dispositivo para que actúe como un transmisor Miracast o receptor.
* Hemos agregado compatibilidad para la [Bluetooth A2DP-SRC](https://docs.microsoft.com/windows/iot-core/connect-your-device/bluetooth) perfil que permite que un dispositivo para que actúe como un origen de audio para el streaming de Bluetooth, incluidas las capacidades de control remoto a través de Bluetooth con el perfil AVRCP.
* Uno de nuestros paneles de Qualcomm más populares, el DragonBoard 410c, se ha convertido en mucho más fácil de flash con esta versión. Con la versión más reciente de la [panel de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard), basta con conectar la placa, ponerlo en modo de flash, y [el dispositivo flash](https://developer.microsoft.com/en-us/windows/iot/getstarted/prototype/setupdevice) directamente desde el panel.
* Para buscar y conectarse a redes Wi-Fi, hemos actualizado la [ejemplo de conector de Wi-Fi](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/WiFiConnector/CS) ser a la par el comando netcmd que previamente ha quedado en desuso. Este ejemplo se utiliza el [WiFiAdapter APIs](https://docs.microsoft.com/uwp/api/Windows.Devices.WiFi.WiFiAdapter) para administrar conexiones de red inalámbrica y adaptadores.
* Tenemos nuevas API relacionadas con el tiempo para establecer automáticamente el reloj del sistema en el [hora local](https://docs.microsoft.com/uwp/api/windows.system.datetimesettings.setsystemdatetime) y [zona horaria](https://docs.microsoft.com/uwp/api/windows.system.timezonesettings.autoupdatetimezoneasync#Windows_System_TimeZoneSettings_AutoUpdateTimeZoneAsync_Windows_Foundation_TimeSpan_) basándose en la ubicación del dispositivo, permitir a los OEM crear una experiencia más sencilla.
* Tenemos un nuevo lenguaje de las API para establecer el usuario preferido [lenguaje](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysetlanguages#Windows_System_UserProfile_GlobalizationPreferences_TrySetLanguages_Windows_Foundation_Collections_IIterable_System_String__), [región](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences.trysethomegeographicregion#Windows_System_UserProfile_GlobalizationPreferences_TrySetHomeGeographicRegion_System_String_), predeterminada [voz](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer.trysetsystemspeechlanguageasync) predeterminada y lenguaje [voz](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer.trysetdefaultvoiceasync).
* Con un nuevo [paquete de artículos de MTP](https://github.com/PawelWMS/windows-iotcore-docs/blob/MTP_Optional_Feature_Instructions/windows-iotcore/connect-your-device/MTP.md), puede transferir archivos a y desde un dispositivo Windows 10 IoT Core a través de USB mediante el protocolo de transferencia multimedia (MTP). Esto incluye los archivos ubicados en el dispositivo de almacenamiento interno y tarjeta SD, si está presente.
* Hemos publicado un nuevo [ejemplo en GitHub](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/Azure/IoTHubClients) y [vídeo de Channel 9](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Connecting-Windows-IoT-Devices-To-IoT-Central) que muestra lo fácil que es obtener un Windows 10 IoT dispositivos integrados en Azure IoT Central. También hemos actualizado nuestra documentación para describir [cómo conectar dispositivos](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore) ejecutan Windows 10 IoT Core para Azure IoT Central.

## <a name="improvements-in-assigned-access"></a>Mejoras de acceso asignado
* Hemos agregado compatibilidad con varias pantallas para casos de uso de señalización digital.
* La página de estado de inscripción ahora incluye la capacidad para asegurarse de que se aplican todas las configuraciones de MDM en el dispositivo antes de escribir el acceso asignado.
* Hemos agregado la capacidad de configurar y ejecutar el selector de Shell además de las aplicaciones existentes de UWP Store.
* Dispositivos con acceso asignado pueden configurarse para entrar automáticamente en un estado deseado tras un reinicio mediante un proceso simplificado para crear y configurar una cuenta de inicio de sesión automático.
* Para los dispositivos de varios usuarios, en lugar de especificar todos los usuarios, es posible asignar configuraciones diferentes de acceso asignado a grupos de Azure AD o grupos de Active Directory.
* Para ayudar a solucionar problemas, ahora puedes ver informes de errores generados si una aplicación configurada con acceso asignado tiene problemas.

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Características en versión preliminar para desarrollo y pruebas
* Centro de actualizaciones de dispositivo [versión preliminar] permite a los OEM globalmente administrar sus aplicaciones y actualizaciones para los archivos del sistema operativo, aplicaciones, configuración y de inserción desde la nube a dispositivos para mantenerlos actualizados y seguros.
* Soporte para alojar [Nano Server contenedores](https://docs.microsoft.com/virtualization/windowscontainers/about/index) en las ediciones de 64 bits de Windows 10 IoT Core y Enterprise, habilitan aplicaciones y sus datos puede ser aislada entre sí y mover rápidamente desde el desarrollo a producción o en la nube para el borde.
* Servicio de atestación de estado de dispositivo de Windows [vista previa] usa características de hardware y servicios en la nube para proporcionar la alteración de corrección y la autorización remota del estado del dispositivo según las métricas de nivel de hardware y certificada de datos.
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) en Windows IoT [versión preliminar] permite que las soluciones de IoT organizar la inteligencia entre los dispositivos en la nube y perimetrales para asegurarse de que las aplicaciones y servicios pueden actuar en datos de IoT donde tenga más sentido.
* Azure IoT Hub [Device Provisioning Service [versión preliminar]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) permite a los dispositivos Windows 10 IoT se creó con una imagen común durante la fabricación y configurado para conectarse automáticamente en el primer arranque para Azure IoT Hub para recuperar información de aprovisionamiento específico del dispositivo.

## <a name="windows-10-iot-core-reference-images"></a>Imágenes de referencia de Windows 10 IoT Core
___ 
* Minnowboard máx.
  * Procesador: Intel Atom E3825
  * Arquitectura: x86

* Raspberry Pi 3 modelo B
  * Procesador: Broadcom BCM2837
  * Arquitectura: ARM

* DragonBoard 410c
  * Procesador: Qualcomm Snapdragon 410
  * Arquitectura: ARM
  * Versión BSP: 2120.0.0.0

## <a name="additional-information"></a>Información adicional
* Según el reciente anuncio de Intel para detener la producción de la plataforma de julio de Intel, FFUs para julio de Intel no se incluyeron en la versión anterior. Los clientes evaluar Intel Joule deben identificar una alternativa plataforma mediante uno de los otros compatibles Qualcomm, consulte [sugiere placas y QUALCOMM](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/suggestedboards) para obtener una lista.

## <a name="known-issues"></a>Problemas conocidos
* Implementación de controladores de F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrados en el dispositivo manualmente.
* Los dispositivos que se instalaron a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.
* El cliente de Windows IoT remoto no funciona para Raspberry Pi. Usar un panel con gráficos acelerados como Minnowboard Max o Dragonboard o adjuntar a un monitor para visualización local.
