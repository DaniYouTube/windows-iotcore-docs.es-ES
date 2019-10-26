---
title: Fall Creators Update (compilación 16299)
ms.date: 10/12/2017
ms.topic: article
description: Obtenga información sobre las novedades de la actualización de Fall Creators para Windows 10 IoT.
keywords: Windows IoT, Fall Creators Update, notas de la versión
ms.openlocfilehash: 35dbe905cfb25613d1225ab8e6d4b8fd636134d9
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918692"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Notas de la versión de Fall Creators Update para Windows 10 IoT
Número de compilación 16299. Octubre de 2017

Windows 10 IoT permite el desarrollo de dispositivos integrados o dedicados y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para Smart Devices.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT.

Para descargar esta compilación más reciente, así como los paquetes, visite la [Página de descargas de Windows Insider Preview](https://www.microsoft.com/en-us/software-download/windowsiot).

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad de esta versión del sistema operativo Windows se puede ver en [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-fall-creators-update"></a>Novedades de Fall Creators Update
* [.Net para aplicaciones UWP](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396), el conjunto de tipos administrados que se pueden usar para compilar C# aplicaciones plataforma universal de Windows con o Visual Basic, se ha ampliado con [miles de API nuevas](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/) para que sea compatible con .net Standard 2,0.
* Compatibilidad con idiomas actualizados en Windows 10 IoT Core, incluidos inglés (en-US y en-GB), francés (fr-FR y FR-CA), español (es-ES y es-MX) y chino simplificado (zh-CN). Puede crear FFUs que admitan varios idiomas; vea [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) y [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample) para obtener más información.
* Compatibilidad con los [servicios de administración de emergencia](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx) en Windows 10 IOT Core.
* [Compatibilidad mejorada con las entradas manuscritas](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) en Windows 10 IOT Core. Con un digitalizador de lápiz compatible, ahora puede emplear las API de DirectInk para el resaltado, el lápiz y la entrada de lápiz basada en vectores. También hemos agregado controles de entrada de lápiz de XAML para UWP, incluidos InkCanvas e InkToolbar, que habilitan las galerías de símbolos como las reglas y los intercambios, y las interacciones multimodales como el lápiz simultáneo y el toque en el hardware compatible. No se admiten características de tinta inteligente como el reconocimiento de tinta y el análisis de tinta.
* Compatibilidad adicional para controlar las pantallas de línea, incluida la personalización del estilo de cursor, el brillo, la velocidad de intermitencia y los juegos de caracteres. También hemos agregado compatibilidad con los glifos personalizados, los descriptores de transacción y el modo de Marquesina para el texto desplazado.
* En Windows 10 IoT Enterprise, hemos habilitado el acceso a buses estándar del sector como GPIO, I2C, SPI y UART desde el modo de usuario a través de las [API de Windows. Devices](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).
* El [acceso asignado](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) es una característica de Windows 10 IOT Enterprise que le permite restringir una cuenta de usuario específica para usar solo una aplicación universal de Windows. Hemos ampliado el soporte de acceso asignado para permitir la ejecución de varias aplicaciones de UWP y Win32 en una experiencia de bloqueo y administrar esa configuración desde la nube.
* Puede cambiar el idioma del sistema mediante IoTSettings. exe o las nuevas API. Para obtener más información, consulte la sección configuración de idioma de la documentación de la [línea de comandos](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) y la [compatibilidad con lenguajes](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) .
* Actualizaciones de Raspberry PI UEFI para habilitar el monitor de volumen de arranque.
* Controlador de red SMSC agregado a todas las arquitecturas de Windows 10 IoT Core.
* Se han habilitado las [secuencias de audio en modo exclusivo](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx) para dispositivos de punto de conexión de audio en Windows 10 IOT Core.
* Se han agregado nuevas API en WinRT para establecer la fecha y la hora del sistema en Windows 10 IoT Core.
* Se ha agregado compatibilidad con el [BSP universal (WM. xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages). Use IOT-ADK-addonkit v 4.0 con la versión actual del ADK.
* Se ha agregado selección de idioma y diseños adaptados al teclado en pantalla. Para obtener más información, vea [distribuciones de teclado en pantalla](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts).

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Características en versión preliminar para escenarios de desarrollo y pruebas
* El servicio de actualización de componentes [versión preliminar] permite a los OEM administrar de forma global sus aplicaciones e instalar actualizaciones para el sistema operativo, las aplicaciones, la configuración y los archivos de la nube en dispositivos para mantenerlos actualizados y seguros.
* Compatibilidad con el hospedaje de [contenedores de nano Server](https://docs.microsoft.com/virtualization/windowscontainers/about/index) en ediciones de 64 bits de Windows 10 IOT Core y Enterprise, la habilitación de aplicaciones y sus datos se puede aislar entre sí y pasar rápidamente de un desarrollo a un entorno de producción o de nube al perímetro.
* El servicio Windows Atestación de estado de dispositivo [versión preliminar] utiliza características de hardware y servicios en la nube para proporcionar una prueba de alteración y la atestación remota del estado de los dispositivos en función de las métricas de nivel de hardware y los datos acreditados.
* [Azure IOT Edge](https://azure.microsoft.com/campaigns/iot-edge/) en Windows IOT [Preview] permite que las soluciones de IOT coordinen la inteligencia entre los dispositivos perimetrales y de la nube para garantizar que las aplicaciones y los servicios pueden actuar en los datos de IOT siempre que resulte más conveniente.
* Azure IoT Hub [servicio Device provisioning [versión preliminar]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) permite crear dispositivos IOT de Windows 10 con una imagen común durante la fabricación y configurarse para conectarse automáticamente en el primer arranque a Azure IOT hub para recuperar el aprovisionamiento específico del dispositivo. informaciones.
* La [Administración de dispositivos IOT de Azure [versión preliminar]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM) permite a los operadores de IOT administrar la configuración de dispositivos, como las aplicaciones instaladas, las actualizaciones de Windows, los certificados y la configuración de red de forma remota desde la nube.

## <a name="windows-10-iot-core-reference-images"></a>Imágenes de referencia de Windows 10 IoT Core
___ 
* Minnowboard Max
  * Procesador: Intel Atom E3825
  * Arquitectura: x86
  * Versión de BSP: 10.0.4.0
* Raspberry Pi 3
  * Procesador: Broadcom BCM2837
  * Arquitectura: ARM
  * Versión de BSP: 10.0.16248.1001
* DragonBoard 410c
  * Procesador: Qualcomm Snapdragon 410
  * Arquitectura: ARM
  * Versión de BSP: 2112.0.0.0

## <a name="additional-information"></a>Información adicional
* En función del anuncio reciente de Intel para dejar de producir la plataforma Intel Joule (, FFUs para Intel Joule (no se incluyen en esta versión. Los clientes que evalúen Intel Joule (deben identificar una plataforma alternativa con uno de los otros SOC admitidos; consulte los [paneles sugeridos y SOC](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards) para obtener una lista.
* La característica IOT_WEBB_EXTN se ha refactorizado para quitar la característica de incorporación, que ahora está disponible como IOT_ONBOARDING_APP. Con esta actualización, se quitará la característica de incorporación y los dispositivos que usen esta característica se deben volver a crear para volver a obtener esta característica.

## <a name="known-issues"></a>Problemas conocidos
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrarse manualmente en el dispositivo.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.
