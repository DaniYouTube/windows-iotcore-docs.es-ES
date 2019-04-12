---
title: Fall Creators Update - compilación 16299
author: saraclay
ms.author: saclayt
ms.date: 10/12/2017
ms.topic: article
description: Obtenga información sobre cuáles son las novedades en Fall Creators Update para Windows 10 IoT.
keywords: Notas de la versión de Windows IoT, Fall Creators Update,
ms.openlocfilehash: 00daad18d5519eee9be695105332aced81a1133f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514268"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Fall Creators Update notas de la versión para Windows 10 IoT
16299 del número de compilación. Octubre de 2017

Windows 10 IoT permite el desarrollo de dispositivos incrustados o dedicado de propósito y es la opción para los OEM y los desarrolladores que crean soluciones de Windows para dispositivos inteligentes.

Este documento proporciona información que complementa otros contenido y la documentación de esta versión de Windows 10 IoT.

Para descargar esta compilación más reciente, así como paquetes, visite la [página de descargas de Windows Insider Preview](https://www.microsoft.com/en-us/software-download/windowsiot).

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad para esta versión del sistema operativo Windows se puede ver en [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-fall-creators-update"></a>Novedades Fall Creators Update
* [.NET para aplicaciones UWP](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396), el conjunto de tipos administrados que puede usarse para crear aplicaciones de plataforma Universal de Windows con C# o Visual Basic, se ha ampliado con [miles de nuevas API](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/) para que sea compatible con .NET Standard 2.0.
* Actualiza la compatibilidad de idioma en Windows 10 IoT Core incluido inglés (en-US y en-GB), francés (fr-FR y fr-CA), español (es-es y es-MX) y chino simplificado (zh-CN). Se puede crear FFUs compatibilidad con varios idiomas, consulte [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) y [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample) para obtener más información.
* Compatibilidad con [servicios de administración de emergencia](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx) en Windows 10 IoT Core.
* Mejorado [compatibilidad con la tinta](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) en Windows 10 IoT Core. Con un digitalizador lápiz compatible, puede usar ahora DirectInk APIs de marcador de resaltado, el lápiz y entrada de lápiz basada en vectores. También hemos agregado los controles de entrada de lápiz XAML para UWP, incluidos InkCanvas y InkToolbar, que permiten las galerías de símbolos, como reglas y protractors e interacciones multimodales, como la pluma simultánea y toque en hardware compatible. No se admiten las funciones de entrada manuscrita inteligentes como reconocimiento de tinta y el análisis de tinta.
* Soporte técnico adicional para controlar la muestra de línea como la personalización del estilo de cursor, brillo, velocidad de intermitencia y juegos de caracteres. También hemos agregado compatibilidad para los glifos personalizados, los descriptores de transacción y el modo de marquesina de desplazamiento de texto.
* En Windows 10 IoT Enterprise, hemos habilitado el acceso a los buses de estándar del sector, como GPIO, I2C, SPI y UART del modo de usuario a través de la [Windows.Devices APIs](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).
* [Asignar acceso](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) es una característica de Windows 10 IoT Enterprise que le permite restringir una cuenta de usuario para usar solo una aplicación Windows Universal. Nos hemos ampliado la compatibilidad con acceso asignado para permitir que se ejecutan varios UWP y aplicaciones de Win32 en un bloqueo de experimentan y administración esas configuraciones en la nube.
* Puede cambiar el idioma del sistema mediante IoTSettings.exe o nuevas API. Para obtener más información, vea la sección de configuración de idioma de la [utilidades de línea de comandos](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) y [compatibilidad con idiomas](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) documentación.
* Actualizaciones a Raspberry Pi UEFI para habilitar la supervisión del volumen de arranque.
* Controlador de red SMSC agregado para todas las arquitecturas de Windows 10 IoT Core.
* Habilitado [secuencias de audio de modo exclusivo](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx) para los dispositivos de punto de conexión de audio en Windows 10 IoT Core.
* Se ha agregado nuevas API de WinRT para establecer la fecha del sistema y la hora en Windows 10 IoT Core.
* Ha agregado compatibilidad con [BSP Universal (wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages). Utilice el v4.0 adk-iot-addonkit con la versión actual de ADK.
* Selección de idioma agregado y diseños localizados para el teclado en pantalla. Para obtener más información, consulte [distribuciones del teclado en pantalla](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts).

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Características en versión preliminar para desarrollo y pruebas
* Servicio de actualización de componente [versión preliminar] permite a los OEM globalmente administrar sus aplicaciones y actualizaciones para los archivos del sistema operativo, aplicaciones, configuración y de inserción desde la nube a dispositivos para mantenerlos actualizados y seguros.
* Soporte para alojar [Nano Server contenedores](https://docs.microsoft.com/virtualization/windowscontainers/about/index) en las ediciones de 64 bits de Windows 10 IoT Core y Enterprise, habilitan aplicaciones y sus datos puede ser aislada entre sí y mover rápidamente desde el desarrollo a producción o en la nube para el borde.
* Servicio de atestación de estado de dispositivo de Windows [vista previa] usa características de hardware y servicios en la nube para proporcionar la alteración de corrección y la autorización remota del estado del dispositivo según las métricas de nivel de hardware y certificada de datos.
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) en Windows IoT [versión preliminar] permite que las soluciones de IoT organizar la inteligencia entre los dispositivos en la nube y perimetrales para asegurarse de que las aplicaciones y servicios pueden actuar en datos de IoT donde tenga más sentido.
* Azure IoT Hub [Device Provisioning Service [versión preliminar]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) permite a los dispositivos Windows 10 IoT se creó con una imagen común durante la fabricación y configurado para conectarse automáticamente en el primer arranque para Azure IoT Hub para recuperar información de aprovisionamiento específico del dispositivo.
* [Administración de dispositivos IoT de Azure [versión preliminar]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM) permite a los operadores de IoT administrar aplicaciones de configuración, como instalada dispositivos, las actualizaciones de Windows, certificados y configuración de forma remota desde la nube de red.

## <a name="windows-10-iot-core-reference-images"></a>Imágenes de referencia de Windows 10 IoT Core
___ 
* Minnowboard máx.
  * Procesador: Intel Atom E3825
  * Arquitectura: x86
  * Versión BSP: 10.0.4.0
* Raspberry Pi 3
  * Procesador: Broadcom BCM2837
  * Arquitectura: ARM
  * Versión BSP: 10.0.16248.1001
* DragonBoard 410c
  * Procesador: Qualcomm Snapdragon 410
  * Arquitectura: ARM
  * Versión BSP: 2112.0.0.0

## <a name="additional-information"></a>Información adicional
* Según el reciente anuncio de Intel para detener la producción de la plataforma de julio de Intel, FFUs para julio de Intel no se pueden utilizar en esta versión. Los clientes evaluar Intel Joule deben identificar una alternativa plataforma mediante uno de los otros compatibles Qualcomm, consulte [sugiere placas y QUALCOMM](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards) para obtener una lista.
* La característica IOT_WEBB_EXTN se ha refactorizado para quitar la característica de incorporación que ahora está disponible como IOT_ONBOARDING_APP. Con esta actualización, se quitará la característica de incorporación y dispositivos que usan esta característica deben ser reflashed para obtener de nuevo, esta característica.

## <a name="known-issues"></a>Problemas conocidos
* Implementación de controladores de F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrados en el dispositivo manualmente.
* El cliente de Windows IoT remoto no funciona para Raspberry Pi. Usar un panel con gráficos acelerados como Minnowboard Max o Dragonboard o adjuntar a un monitor para visualización local.
