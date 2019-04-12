---
title: Actualización de octubre de 2018 - compilación 17763
author: saraclay
ms.author: saclayt
ms.date: 10/02/2018
ms.topic: article
description: Obtenga información sobre novedades de la actualización de octubre de 2018 para Windows.
keywords: Windows IoT, la actualización de octubre de 2018, notas de la versión
ms.openlocfilehash: 886f86a733f53632dee73d0af7b2c172693bc3a5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515252"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Notas de la versión de octubre de 2018 actualización para Windows 10 IoT
17763 del número de compilación. Octubre de 2018

> [!IMPORTANT]
> Si usas el [actualización de octubre de 2018](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/october2018update), use el [actualización de octubre (con enero mantenimiento pack, compilación 17763.253)](https://docs.microsoft.com/en-us/windows/iot-core/release-notes/commercial/17763) versión en su lugar. Hemos encontrado que existen problemas conocidos que afectan a los usuarios de la de octubre de 2018 Update. 

Windows 10 IoT permite el desarrollo de dispositivos incrustados o dedicado de propósito y es la opción para los OEM y los desarrolladores que crean soluciones de Windows para dispositivos inteligentes.

Este documento proporciona información que complementa otros contenido y la documentación de esta versión de Windows 10 IoT.

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad para esta versión del sistema operativo Windows se puede ver en [ https://go.microsoft.com/fwlink/?LinkId=521839 ](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-october-2018-update"></a>Novedades de octubre de 2018 Update

_Windows 10 IoT Enterprise y Windows 10 IoT Core_
* La IoT Windows 10 de octubre de 2018 actualización tendrá 10 años de soporte técnico para IoT Core y IoT Enterprise.
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) es un servicio totalmente administrado que ofrece inteligencia en la nube localmente al implementar y ejecutar cargas de trabajo artificiales (IA), servicios de Azure y lógica personalizada directamente en dispositivos Windows 10 IoT.
* [Windows Machine Learning](https://docs.microsoft.com/windows/ai/) permite a los desarrolladores usar modelos en sus aplicaciones de aprendizaje de automático previamente entrenado. Estos modelos se entrenan normalmente en la nube que se debe evaluar en el perímetro. Evaluación local en los dispositivos que ejecutan Windows 10 IoT ayuda a mitigar los problemas de conectividad, ancho de banda y la privacidad de los datos.  

_Windows 10 IoT Core_
* [Servicios de Windows 10 IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) suscripción ahora está disponible con carácter general. Esta suscripción viene con tres ventajas principales incluidos 10 años de sistema operativo admite, actualice el control con el [centro de actualizaciones de dispositivo](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)y atestación de estado de dispositivo (DHA).
* Para cumplir con los clientes en aumento y la demanda de socio de diversidad de silicon, Microsoft, en estrecha colaboración con NXP, ha agregado compatibilidad con procesadores de serie M de NXP i.MX 6, 7 y 8 para Windows 10 IoT Core. 
* QUALCOMM y Microsoft han creado una solución que combina Windows 10 IoT Enterprise con procesadores Snapdragon crear dispositivos que consumen menos energía, están siempre conectados y reactivación al instante. Batería de larga duración permite que los dispositivos dedicados como los PC móviles y tabletas de línea de negocio hasta el último un día completo de un uso intensivo. 
* [La aplicación de predeterminado de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) tiene más características que los usuarios pueden aprovechar para sus propias aplicaciones, especialmente cuando lleva sus dispositivos en el mercado. Estas características incluyen el tiempo, capacidades de escritura a mano, capacidades de audio. 
* Si está creando un dispositivo comercial abierto para la implementación comercial en una "instalación específico o limitado" (es decir, almacén de fábrica o comercial) donde el usuario final realiza la configuración final y documentar los clientes que deben [obtener una certificado de WDP e instalar en tanto WDP y conecta los exploradores y las contraseñas se cambian en WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), a continuación, uso de WDP en esta instancia comercial estrecha es aceptable. Imágenes de venta directa en este escenario aún no deben incluir IOT_TOOLKIT, pero deben usar el paquete IOT_WEBBEXTN para extraer WDP. 
* Limpet.exe ahora está disponible como un [proyecto de código abierto](https://github.com/ms-iot/azure-dm-client). Para facilitar las pruebas, se tiene una versión sin firmar, precompilada de Limpet.exe disponible y puede descargarse desde WDP. Más información sobre esta característica desde el [documentación de Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal).  
* Con RS5, los desarrolladores son capaces de flash FFUs personalizados en su dispositivo mediante el panel. Esto puede hacerse con las 410C DragonBoard o NXP. Obtenga más información y empezar a trabajar [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup).
* Windows 10 IoT Core ahora usa los mismos componentes de teclado táctil como la edición de escritorio de Windows que permite que las características como el modo de dictado, todo el conjunto de diseños de idioma de teclado de Windows y mucho más. Esta nueva actualización también incluye supprt de iconos gestuales, más entrados "ámbitos" y una mejor compatibilidad de varios lenguajes. Obtenga información sobre cómo aprovechar estas características [aquí](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard).
* Obtenga información sobre cómo [configurar el dispositivo para permitir el apagado](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch) mientras no en uso y activarse cuando un usuario toca una pantalla.
* RECEPTOR de Bluetooth A2DP ahora se admite opcionalmente (p. ej. permite la reproducción desde un origen remoto, como iPhone al dispositivo de IoT) y Bluetooth A2DP-SRC ahora es un paquete opcional (estaba disponible de forma predeterminada en el de abril de 2018 versión). Puede controlar las preferencias de perfiles de Bluetooth A2DP-SRC y A2DP receptor cuando ambos perfiles estén presentes y al emparejar con otro dispositivo que también es compatible con ambos. 
* Por diseño, Windows 10 IoT Core no se muestra un marco de aplicación en torno a una ventana de aplicación: en las palabras de orden, una aplicación se muestra como pantalla completa. Pero con esta versión, los desarrolladores tienen la opción de [configuración de las barras de título](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars).
* Ahora están disponibles en herramientas de bus que le permitan interactuar con Gpio, I2c, Spi y UART [nuestro repositorio de ejemplos](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools). Estas herramientas se ejecutarán en cualquier edición de Windows, incluidos Windows 10 IoT Core y Enterprise de Windows. 
* [La API de Namespace Windows.System.Update](https://docs.microsoft.com/uwp/api/windows.system.update) habilita las llamadas para el control interactivo de las actualizaciones del sistema. Este espacio de nombres solo está disponible para Windows 10 IoT Core.
* Si desea para usar IoT Central como parte de una solución de Windows 10 IoT, ahora puede preparar y [conectar un dispositivo Windows 10 IoT Core a una aplicación de Azure IoT Central](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore). 
* La versión para el dispositivo Raspberry Pi 3B + (se puede encontrar la imagen ISO descargable [aquí](http://go.microsoft.com/fwlink/?LinkID=708576)) es una versión preliminar técnica y actualmente no hay ninguna escala de tiempo para una versión de lanzamiento. Para una mejor experiencia de evaluación y fr los productos comerciales, use el 3B Raspberry Pi u otros dispositivos con admite Intel, Qualcomm o NXP Qualcomm. 

## <a name="iot-enterprise-manufacturing-guide"></a>Guía de fabricación de IoT empresarial

* Es una nueva guía de fabricación para Windows 10 IoT Enterprise [disponibles ahora](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/iot-ent-overview). 

## <a name="improvements-in-assigned-access"></a>Mejoras de acceso asignado 

_Windows 10 IoT Enterprise_

* Quioscos y firma digital se suelen colocar en lugares públicos, donde se ven ampliamente los problemas por personas. Con informes de estado integrada, sistemas de administración de dispositivos automáticamente conocen la existencia de problemas y pueden emitir las acciones correctivas, como reiniciar el dispositivo o enviar a un técnico de servicio. 
* Reducción de costos de implementación y administración es controladores clave de rendimiento de la inversión. Windows 10 IoT Enterprise ha mejorado las características para configurar una experiencia de pantalla completa a través de un Asistente para nueva en la aplicación de configuración, administración quioscos con varias aplicaciones y adaptar el [experiencia del explorador Microsoft Edge para dispositivos de pantalla completa](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy).
* Mientras que los generadores de dispositivo tienen una gran flexibilidad para configurar el acceso asignado mediante paquetes de aprovisionamiento, la aplicación de configuración y los sistemas de administración de dispositivos móviles, algunos clientes necesitan aún más. [Uso de un nuevo conjunto de API de acceso asignado](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings), los desarrolladores ahora pueden configurar asignada por el acceso mediante programación desde dentro de sus aplicaciones.
* Con la versión de octubre de 2018, los clientes pueden especificar una experiencia de iniciar automáticamente como parte de la configuración de acceso asignada con varias aplicaciones para que el usuario final pueda tener siempre una experiencia de aplicación principal de forma predeterminada.
* Puede controlar lo que ve el usuario desde el momento en que se activa el dispositivo hasta que está apagada. Iniciando mostrando su logotipo en lugar del logotipo de Windows en el inicio o reinicio automático de aplicaciones sin mensaje de error después de un bloqueo de la aplicación, un problema del sistema o una interrupción de la alimentación. 
* Puede usar la característica de filtro de escritura unificado (UWF) para crear un dispositivo de "solo lectura" que se devuelve a un estado conocido después de un ciclo de alimentación manteniendo los cambios en el disco en memoria en lugar de escribirlos en el disco. También puede combinar UWF con la hibernación una vez, característica reanudar muchas (HORN) para reanudar una sesión predefinido. 


## <a name="more-management-support"></a>Más compatibilidad con la administración

_Windows 10 IoT Enterprise_
* Azure IoT Hub ofrece características de administración de dispositivos ligeros y un modelo de extensibilidad que permiten a los desarrolladores de dispositivos y en la nube compilar soluciones de administración sólida de dispositivo. Integración con [administración de dispositivos de IoT de Azure](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) ahora está disponible para Windows 10 IoT Core y Enterprise. 

_Windows 10 IoT Core_
* Las empresas que usan [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) para su dispositivo management puede administrar dispositivos Windows 10 IoT Core junto con sus dispositivos Windows 10 IoT Enterprise y otros dispositivos administrados. Esto ofrece a los operadores para administrar dispositivos Windows 10 IoT con la misma interfaz de administración y los controles de forma coherente. 


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


## <a name="known-issues"></a>Problemas conocidos
* Implementación de controladores de F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrados en el dispositivo manualmente.
* Los dispositivos que se instalaron a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.
* El cliente de Windows IoT remoto no funciona para Raspberry Pi. Usar un panel con gráficos acelerados como Minnowboard Max o Dragonboard o adjuntar a un monitor para visualización local.
