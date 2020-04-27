---
title: 'Fall Creators Update: compilación 16299'
ms.date: 10/12/2017
ms.topic: article
description: Obtén información sobre las novedades de Fall Creators Update para Windows 10 IoT.
keywords: Windows IoT, Fall Creators Update, notas de la versión
ms.openlocfilehash: 35dbe905cfb25613d1225ab8e6d4b8fd636134d9
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "72918692"
---
# <a name="fall-creators-update-release-notes-for-windows-10-iot"></a>Notas de la versión de Fall Creators Update para Windows 10 IoT
Número de compilación 16299. Octubre de 2017

Windows 10 IoT permite el desarrollo de dispositivos integrados o dedicados, y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para dispositivos inteligentes.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT.

Para descargar esta compilación más reciente, así como los paquetes, visita la página de [descargas de Windows Insider Preview](https://www.microsoft.com/en-us/software-download/windowsiot).

## <a name="privacy-statement"></a>Declaración de privacidad

La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar en [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-fall-creators-update"></a>Novedades de Fall Creators Update
* [.NET para aplicaciones para UWP](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx?f=255&mspperror=-2147217396), el conjunto de tipos administrados que se pueden usar para compilar aplicaciones para la Plataforma universal de Windows mediante C# o Visual Basic ha ampliado en [miles de nuevas API](https://blogs.msdn.microsoft.com/dotnet/2017/08/25/uwp-net-standard-2-0-preview/) para que sea compatible con .NET Standard 2.0.
* Se ha actualizado la compatibilidad con idiomas en Windows 10 IoT Core, incluidos inglés (en-US y en-GB), francés (fr-FR y fr-CA), español (es-ES y es-MX) y chino simplificado (zh-CN). Puedes crear FFU que admitan varios idiomas; consulta [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/MultiLangSample) y [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/16299/Source-arm/Products/SingleLangSample) para más información.
* Compatibilidad con [Servicios de administración de emergencia](https://technet.microsoft.com/library/cc736319(v=ws.10).aspx) en Windows 10 IoT Core.
* [Compatibilidad mejorada con la entrada de lápiz](https://docs.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) en Windows 10 IoT Core. Con un digitalizador de lápiz compatible, ahora puedes emplear las API de DirectInk para el resaltado, el lápiz y la entrada de lápiz basada en vectores. También hemos agregado controles de entrada de lápiz de XAML para UWP, incluidos InkCanvas e InkToolbar, que habilitan las galerías de símbolos, como las reglas y los transportadores, y las interacciones multimodales, como el lápiz simultáneo y la función táctil en el hardware compatible. No se admiten las características de entrada de lápiz inteligente, como el reconocimiento de entrada de lápiz y el análisis de entrada de lápiz.
* Compatibilidad adicional para controlar las pantallas de líneas, incluida la personalización del estilo de cursor, el brillo, la velocidad de intermitencia y los conjuntos de caracteres. También hemos agregado compatibilidad con los glifos personalizados, los descriptores de transacción y el modo de marquesina para el texto en desplazamiento.
* En Windows 10 IoT Enterprise, hemos habilitado el acceso a buses estándar del sector, como GPIO, I2C, SPI y UART, desde el modo de usuario a través de las [API de Windows.Devices](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).
* [Acceso asignado](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) es una característica de Windows 10 IoT Enterprise que te permite restringir una cuenta de usuario específica para usar solo una aplicación universal de Windows. Hemos ampliado la compatibilidad de Acceso asignado para permitir la ejecución de varias aplicaciones para UWP y Win32 en una experiencia de bloqueo y para administrar esa configuración desde la nube.
* Puedes cambiar el idioma del sistema mediante IoTSettings.exe o las nuevas API. Para obtener más información, consulta la sección de configuración de idioma en la documentación de [Utilidades de línea de comandos](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang) y [Compatibilidad con idiomas](https://docs.microsoft.com/windows/iot-core/develop-your-app/multilang).
* Actualizaciones de Raspberry Pi UEFI para habilitar el monitor de volumen de arranque.
* Se agregó el controlador de red SMSC a todas las arquitecturas de Windows 10 IoT Core.
* Se habilitaron los [flujos de audio de modo exclusivo](https://msdn.microsoft.com/library/windows/desktop/dd370844(v=vs.85).aspx) para dispositivos de punto de conexión de audio en Windows 10 IoT Core.
* Se han agregado nuevas API en WinRT para establecer la fecha y la hora del sistema en Windows 10 IoT Core.
* Se ha agregado compatibilidad con [Universal BSP (wm.xml)](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-packages). Usa iot-adk-addonkit v4.0 con la versión actual del ADK.
* Se ha agregado la selección de idioma y diseños localizados al teclado en pantalla. Para más información, consulta [Distribuciones de teclado en pantalla](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboardlayouts).

## <a name="features-in-preview-for-dev-and-test-scenarios"></a>Características en versión preliminar para escenarios de desarrollo y pruebas
* El servicio de actualización de componentes [versión preliminar] permite a los OEM administrar de forma global sus aplicaciones e insertar actualizaciones para el sistema operativo, las aplicaciones, la configuración y los archivos desde la nube en dispositivos para mantenerlos actualizados y protegidos.
* Compatibilidad con el hospedaje de [contenedores de Nano Server](https://docs.microsoft.com/virtualization/windowscontainers/about/index) en las ediciones de 64 bits de Windows 10 IoT Core y Enterprise, lo que permite que las aplicaciones y sus datos se puedan aislar unos de otros y pasar rápidamente de desarrollo a producción o de la nube al perímetro.
* El servicio Atestación de estado de dispositivo [versión preliminar] de Windows usa características de hardware y servicios en la nube para proporcionar protección contra alteraciones y atestación remota del estado de los dispositivos en función de las métricas de nivel de hardware y los datos acreditados.
* [Azure IoT Edge](https://azure.microsoft.com/campaigns/iot-edge/) en Windows IoT [versión preliminar] permite que las soluciones de IoT coordinen la inteligencia entre los dispositivos perimetrales y de la nube para garantizar que las aplicaciones y los servicios pueden actuar en función de los datos de IoT siempre que resulte más conveniente.
* El [servicio de aprovisionamiento de dispositivos [versión preliminar]](https://blogs.windows.com/buildingapps/2017/10/05/windows-10-iot-enables-complete-iot-lifecycle/) de Azure IoT Hub permite crear dispositivos de Windows 10 IoT con una imagen común durante la fabricación y configurarlos para que se conecten automáticamente en el primer arranque a Azure IoT Hub para recuperar la información de aprovisionamiento específica del dispositivo.
* La [Administración de dispositivos con Azure IoT [versión preliminar]](https://docs.microsoft.com/windows/iot-core/manage-your-device/AzureIoTDM) permite a los operadores de IoT administrar la configuración de dispositivos, como las aplicaciones instaladas, las actualizaciones de Windows, los certificados y la configuración de red, de forma remota desde la nube.

## <a name="windows-10-iot-core-reference-images"></a>Imágenes de referencia de Windows 10 IoT Core
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
* En función del anuncio reciente de Intel para dejar de producir la plataforma Intel Joule, se interrumpen las FFU para Intel Joule en esta versión. Los clientes que están pensando en Intel Joule deben identificar una plataforma alternativa con uno de los otros SoC admitidos; consulta [Paneles sugeridos y SoC](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/prototypeboards) para obtener una lista.
* La característica IOT_WEBB_EXTN se ha refactorizado para quitar la característica de incorporación, que ahora está disponible como IOT_ONBOARDING_APP. Con esta actualización, se quitará la característica de incorporación, y los dispositivos que usen esta característica se deben volver a crear para volver a obtener esta característica.

## <a name="known-issues"></a>Problemas conocidos
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrarse manualmente en el dispositivo.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.
