---
title: 'Actualización de octubre de 2018: compilación 17763'
ms.date: 10/02/2018
ms.topic: article
description: Obtén información sobre las novedades de la actualización de octubre de 2018 para Windows.
keywords: Windows IoT, actualización de octubre de 2018, notas de la versión
ms.openlocfilehash: 5b5b6e45552d099426019626ca52000635e308a5
ms.sourcegitcommit: 34928850d3b1b2fe22a92ebd1d75c01b3d4bf0aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/24/2020
ms.locfileid: "75721880"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Notas de la versión de la actualización de octubre de 2018 para Windows 10 IoT
Número de compilación 17763. Octubre de 2018

> [!IMPORTANT]
> Si usas la [actualización de octubre de 2018](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/october2018update), usa la versión [Actualización de octubre (con el paquete de mantenimiento de enero, compilación 17763.253)](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/17763) en su lugar. Encontramos que hay problemas conocidos que afectan a los usuarios de la actualización de octubre de 2018. 

Windows 10 IoT permite el desarrollo de dispositivos integrados o dedicados, y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para dispositivos inteligentes.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT.

## <a name="privacy-statement"></a>Declaración de privacidad

La declaración de privacidad para esta versión del sistema operativo Windows se puede consultar en [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-october-2018-update"></a>Novedades de la actualización de octubre de 2018

_Windows 10 IoT Enterprise y Windows 10 IoT Core_
* La actualización de Windows 10 IoT de octubre de 2018 tendrá 10 años de soporte técnico tanto para IoT Core como para IoT Enterprise.
* [Azure IoT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) es un servicio totalmente administrado que ofrece inteligencia en la nube localmente mediante la implementación y ejecución de cargas de trabajo artificiales (IA), servicios de Azure y lógica personalizada directamente en dispositivos con Windows 10 IoT.
* [Windows Machine Learning](https://docs.microsoft.com/windows/ai/) permite a los desarrolladores usar en sus aplicaciones modelos de Machine Learning previamente entrenados. Estos modelos suelen entrenarse en la nube para que se evalúen en el perímetro. La evaluación local en los dispositivos que ejecutan Windows 10 IoT ayuda a mitigar los problemas de conectividad, ancho de banda y privacidad de los datos.  

_Windows 10 IoT Core_
* La suscripción a [Windows 10 IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) ahora está disponible con carácter general. Esta suscripción incluye tres ventajas principales, entre las que se incluyen 10 años de soporte técnico para el sistema operativo, el control de actualizaciones con el [Centro de actualización de dispositivos](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center) y Atestación de estado de dispositivo (DHA).
* Para satisfacer la creciente demanda de clientes y partners en relación con la diversidad de placas, Microsoft, en estrecha colaboración con NXP, ha agregado a Windows 10 IoT Core compatibilidad con los procesadores de NXP i.MX de las series 6, 7 y 8. 
* Qualcomm y Microsoft han creado una solución que combina Windows 10 IoT Enterprise con procesadores Snapdragon para crear dispositivos que consumen menos energía, están siempre conectados y se activan al instante. La larga duración de la batería permite que dispositivos dedicados, como POS móviles y tabletas de línea de negocio, duren un día completo de uso intensivo. 
* [La aplicación predeterminada de Windows 10 IoT Core](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) tiene más características que los usuarios pueden aprovechar para sus propias aplicaciones, sobre todo al llevar sus dispositivos al mercado. Estas características incluyen el clima, capacidades de entrada manuscrita y capacidades de audio. 
* Si va a crear un dispositivo minorista abierto para la implementación comercial en una "instalación específica/limitada" (es decir, fábrica o tienda de venta directa) donde el usuario final se encarga de la configuración final y usted manifiesta a los clientes que estos deben [obtener un certificado para WDP e instalarlo tanto en WDP como en los exploradores que se conectan, y que contraseñas se cambian en WDP](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), el uso de WDP en esta instancia comercial limitada es aceptable. Las imágenes comerciales de este escenario no deben incluir IOT_TOOLKIT, sino que deben usar el paquete de IOT_WEBBEXTN para incorporar en WDP. 
* Ahora, Limpet.exe está disponible como [proyecto de código abierto](https://github.com/ms-iot/azure-dm-client). Para facilitar las pruebas, tenemos disponible una versión no firmada y precompilada de Limpet.exe, y se puede descargar directamente desde WDP. Obtén más información sobre esta característica en la [documentación del Portal de dispositivos Windows](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal).  
* Con RS5, los desarrolladores ahora pueden reiniciar FFU personalizadas en su dispositivo mediante el Panel. Esto puede hacerse con DragonBoard 410C o NXP. Obtén más información y empieza [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup).
* Windows 10 IoT Core ahora usa los mismos componentes de teclado táctil que la edición de escritorio de Windows, lo que permite que las características como el modo de dictado, todo el conjunto de diseños de idioma del teclado de Windows y mucho más. Esta nueva actualización también incluye compatibilidad con emoticonos, la mayoría de los "ámbitos" de entrada y una mejor compatibilidad con varios idiomas. Obtén información sobre cómo aprovechar estas características [aquí](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard).
* Obtén información acerca de cómo [configurar el dispositivo para pueda desactivarse](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch) mientras no está en uso y vuelva a activarse cuando un usuario toque una pantalla.
* Bluetooth A2DP-SINK ahora se admite opcionalmente (por ejemplo, permite la reproducción desde un origen remoto, como iPhone a un dispositivo IoT), y Bluetooth A2DP-SRC es ahora un paquete opcional (disponible de forma predeterminada en la versión de abril de 2018). Puedes controlar las preferencias de los perfiles Bluetooth A2DP-SRC y A2DP-SINK cuando ambos están presentes y al emparejar con otro dispositivo que también admite ambos. 
* Por diseño, Windows 10 IoT Core no muestra un marco de aplicación en torno a la ventana de una aplicación: en otras palabras, una aplicación se muestra como pantalla completa. Sin embargo, con esta versión, los desarrolladores tienen la opción de [configurar barras de título](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars).
* Las herramientas de bus que permiten interactuar con Gpio, I2c, Spi y UART ahora están disponibles en [nuestro repositorio de ejemplos](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools). Estas herramientas se ejecutarán en cualquier edición de Windows, incluidas Windows 10 IoT Core y Windows Enterprise. 
* [La API de espacio de nombres Windows.System.Update](https://docs.microsoft.com/uwp/api/windows.system.update) permite las llamadas para el control interactivo de las actualizaciones del sistema. Este espacio de nombres solo está disponible para Windows 10 IoT Core.
* Si quieres usar IoT Central como parte de una solución de Windows 10 IoT, ahora puedes preparar y [conectar un dispositivo de Windows 10 IoT Core a tu aplicación de Azure IoT Central](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore). 
* La versión para Raspberry Pi 3B+ (el archivo ISO descargable se puede encontrar [aquí](https://go.microsoft.com/fwlink/?LinkID=708576)) es una versión preliminar técnica, y actualmente no hay ningún cronograma para una versión de lanzamiento. Para obtener una mejor experiencia de evaluación y para cualquier producto comercial, usa Raspberry Pi 3B u otros dispositivos con SoC de Intel, Qualcomm o NXP admitidos. 

## <a name="iot-enterprise-manufacturing-guide"></a>Guía de fabricación de IoT Enterprise

* [Ya está disponible](https://docs.microsoft.com/windows-hardware/manufacture/desktop/iot-ent-overview) una nueva guía de fabricación para Windows 10 IoT Enterprise. 

## <a name="improvements-in-assigned-access"></a>Mejoras en Acceso asignado 

_Windows 10 IoT Enterprise_

* Los quioscos y carteles digitales suelen colocarse en lugares públicos, donde la gente puede ver claramente si hay problemas. Con los informes de estado integrados, los sistemas de administración de dispositivos son conscientes de los problemas automáticamente y pueden emitir acciones correctivas, como reiniciar el dispositivo o enviar un técnico de servicio. 
* Reducir los costos de implementación y administración son motores clave del retorno de la inversión. Windows 10 IoT Enterprise ha mejorado las características para configurar una experiencia de quiosco a través de un nuevo asistente en la aplicación de configuración, administrar los quioscos con varias aplicaciones y personalizar la [experiencia del explorador Microsoft Edge para dispositivos de quiosco](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy).
* Aunque los fabricantes de dispositivos tienen una gran flexibilidad para configurar Acceso asignado mediante paquetes de aprovisionamiento, la aplicación de configuración y los sistemas de administración de dispositivos móviles, algunos clientes todavía necesitan más. [Al usar un nuevo conjunto de API de Acceso asignado](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings), los desarrolladores ahora pueden configurar mediante programación de Acceso asignado desde dentro de sus aplicaciones.
* Con la versión de octubre de 2018, los clientes pueden especificar una experiencia de inicio automático como parte de la configuración de Acceso asignado de varias aplicaciones, por lo que el usuario final puede tener siempre una experiencia de aplicación principal predeterminada.
* Puedes controlar lo que el usuario ve desde el momento en que se enciende el dispositivo hasta que se apaga. Comienza por mostrar tu logotipo en lugar del logotipo de Windows en el arranque, o haz que las aplicaciones se reinicien automáticamente sin mensajes de error después del bloqueo de una aplicación, un problema del sistema o una interrupción de la alimentación. 
* Puedes usar la característica Filtro de escritura unificado (UWF) para crear un dispositivo de "solo lectura" que vuelva a un estado conocido después de un reinicio al mantener en la memoria los cambios de disco en lugar de escribirlos en el disco. También puedes combinar UWF con la característica Hibernar una vez, reanudar varias veces (HORM) para reanudar una sesión predefinida. 


## <a name="more-management-support"></a>Más soporte de administración

_Windows 10 IoT Enterprise_
* Azure IoT Hub ofrece características de administración ligera de dispositivos y un modelo de extensibilidad que permite a los desarrolladores de dispositivos y en la nube crear sólidas soluciones de administración de dispositivos. La integración en [Administración de dispositivos con Azure IoT](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) ahora está disponible para Windows 10 IoT Core y Enterprise. 

_Windows 10 IoT Core_
* Las empresas que usan [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) para la administración de sus dispositivos ahora pueden administrar dispositivos de Windows 10 IoT Core junto con sus dispositivos de Windows 10 IoT Enterprise y otros dispositivos administrados. Esto da a los operadores una manera coherente de administrar los dispositivos de Windows 10 IoT con la misma interfaz de administración y los mismos controles. 


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


## <a name="known-issues"></a>Problemas conocidos
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrarse manualmente en el dispositivo.
* Los dispositivos que se han instalado a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.
