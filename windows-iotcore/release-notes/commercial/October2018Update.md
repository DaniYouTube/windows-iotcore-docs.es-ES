---
title: 'Actualización de octubre de 2018: compilación 17763'
ms.date: 10/02/2018
ms.topic: article
description: Obtenga información sobre las novedades de la actualización de octubre de 2018 para Windows.
keywords: Windows IoT, actualización de octubre de 2018, notas de la versión
ms.openlocfilehash: 5b5b6e45552d099426019626ca52000635e308a5
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721880"
---
# <a name="october-2018-update-release-notes-for-windows-10-iot"></a>Notas de la versión de octubre de 2018 para Windows 10 IoT
Número de compilación 17763. Octubre de 2018

> [!IMPORTANT]
> Si usa la actualización de [octubre de 2018](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/october2018update), use la versión de la [actualización de octubre (con el paquete de mantenimiento de enero, compilación 17763,253)](https://docs.microsoft.com/windows/iot-core/release-notes/commercial/17763) en su lugar. Encontramos problemas conocidos que afectan a los usuarios de la actualización de octubre de 2018. 

Windows 10 IoT permite el desarrollo de dispositivos integrados o dedicados y es la opción para los OEM y desarrolladores que compilan soluciones de Windows para Smart Devices.

En este documento se proporciona información que complementa otros contenidos y documentación de esta versión de Windows 10 IoT.

## <a name="privacy-statement"></a>Declaración de privacidad en línea

La declaración de privacidad de esta versión del sistema operativo Windows se puede ver en [https://go.microsoft.com/fwlink/?LinkId=521839](https://go.microsoft.com/fwlink/?LinkId=521839).

## <a name="whats-new-in-october-2018-update"></a>Novedades de la actualización 2018 de octubre

_Windows 10 IoT Enterprise & Windows 10 IoT Core_
* La actualización de Windows 10 IoT de octubre de 2018 tendrá 10 años de compatibilidad con IoT Core y IoT Enterprise.
* [Azure IOT Edge](https://docs.microsoft.com/azure/iot-edge/quickstart) es un servicio totalmente administrado que ofrece inteligencia en la nube localmente mediante la implementación y ejecución de cargas de trabajo artificiales (AI), servicios de Azure y lógica personalizada directamente en dispositivos de IOT de Windows 10.
* [Windows machine learning](https://docs.microsoft.com/windows/ai/) permite a los desarrolladores usar modelos de aprendizaje automático previamente entrenados en sus aplicaciones. Estos modelos suelen entrenarse en la nube para que se evalúen en el perímetro. La evaluación local en los dispositivos que ejecutan Windows 10 IoT ayuda a mitigar los problemas de conectividad, ancho de banda y privacidad de los datos.  

_Windows 10 IoT Core_
* [Windows 10 IOT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) suscripción está ya disponible con carácter general. Esta suscripción incluye tres ventajas principales, entre las que se incluyen 10 años de soporte del sistema operativo, el control de actualizaciones con el [centro de actualizaciones de dispositivos](https://docs.microsoft.com/windows-hardware/service/iot/using-device-update-center)y atestación de estado de dispositivo (DHA).
* Para satisfacer la creciente demanda de clientes y asociados de silicio Diversity, Microsoft, en estrecha colaboración con NXP, ha agregado compatibilidad con los procesadores de NXP i.MX 6, 7 y 8 de Windows 10 IoT Core. 
* Qualcomm y Microsoft han creado una solución que combina Windows 10 IoT Enterprise con procesadores de Snapdragon para crear dispositivos que consumen menos energía, siempre se conectan y reactivan al instante. La larga duración de la batería permite que dispositivos dedicados, como Mobile POS y tabletas de línea de negocio, duren un día completo de uso intensivo. 
* [La aplicación predeterminada de Windows 10 IOT Core](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) tiene más características que los usuarios pueden aprovechar para sus propias aplicaciones, sobre todo cuando traen sus dispositivos al mercado. Estas características incluyen el tiempo, las capacidades de entrada manuscrita y las capacidades de audio. 
* Si va a crear un dispositivo de venta al por menor abierto para la implementación comercial en una "instalación específica/limitada" (es decir, en fábrica o en tienda) donde el usuario final realiza la configuración final y documenta a los clientes que deben [obtener un certificado para WDP e instalarlo tanto en WDP como en los exploradores y contraseñas de conexión](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl), se cambia el uso de WDP en esta instancia Las imágenes comerciales de este escenario no deben incluir IOT_TOOLKIT, sino que deben usar el paquete de IOT_WEBBEXTN para extraer de WDP. 
* Limpet. exe ahora está disponible como [proyecto de código abierto](https://github.com/ms-iot/azure-dm-client). Para facilitar las pruebas, tenemos una versión no firmada pregenerada de limpet. exe disponible y se puede descargar directamente desde WDP. Obtenga más información sobre esta característica en la [documentación del portal de dispositivos de Windows](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal).  
* Con RS5, los desarrolladores ahora pueden hacer Flash de FFUs personalizadas en su dispositivo mediante el panel. Esto puede hacerse con DragonBoard 410C o NXP. Obtenga más información y comience [aquí](https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/devicesetup).
* Windows 10 IoT Core ahora usa los mismos componentes de teclado táctil que la edición de escritorio de Windows, que permite características como el modo de dictado, todo el conjunto de diseños de idioma del teclado de Windows y mucho más. Esta nueva actualización también incluye supprt para los emoticonos, la mayoría de los "ámbitos" y una mejor compatibilidad con varios idiomas. Obtenga información sobre cómo aprovechar estas características [aquí](https://docs.microsoft.com/windows/iot-core/develop-your-app/onscreenkeyboard).
* Obtenga información acerca de cómo [configurar el dispositivo para que deje de estar](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/wakeontouch) apagado mientras no está en uso y se activa cuando un usuario toca una pantalla.
* Bluetooth A2DP-SINK ahora se admite opcionalmente (por ejemplo, permite la reproducción desde un origen remoto, como iPhone a un dispositivo IoT) y Bluetooth A2DP-SRC es ahora un paquete opcional (disponible de forma predeterminada en la versión de abril de 2018). Puede controlar las preferencias de perfil Bluetooth A2DP-SRC y A2DP-SINK cuando ambos perfiles están presentes y cuando se emparejan con otro dispositivo que también admite ambos. 
* Por diseño, Windows 10 IoT Core no muestra un marco de aplicación en torno a la ventana de una aplicación: en el orden de las palabras, una aplicación se muestra como pantalla completa. Sin embargo, con esta versión, los desarrolladores tienen la opción de [configurar las barras de título](https://docs.microsoft.com/windows/iot-core/develop-your-app/signindialogtitlebars).
* Las herramientas de bus que permiten interactuar con GPIO, I2C, SPI y UART ahora están disponibles en [nuestro repositorio de ejemplos](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/BusTools). Estas herramientas se ejecutarán en cualquier edición de Windows, incluidas Windows 10 IoT Core y Windows Enterprise. 
* [La API de espacio de nombres Windows. System. Update](https://docs.microsoft.com/uwp/api/windows.system.update) habilita las llamadas para el control interactivo de las actualizaciones del sistema. Este espacio de nombres solo está disponible para Windows 10 IoT Core.
* Si desea usar IoT Central como parte de una solución de IoT de Windows 10, ahora puede preparar y [conectar un dispositivo de Windows 10 IOT Core a su aplicación de Azure IOT central](https://docs.microsoft.com/azure/iot-central/howto-connect-windowsiotcore). 
* La versión de Raspberry PI 3B + (la ISO descargable se puede encontrar [aquí](https://go.microsoft.com/fwlink/?LinkID=708576)) es una vista previa técnica y actualmente no hay ninguna escala de tiempo para una versión de lanzamiento. Para obtener una mejor experiencia de evaluación y fr en el caso de los productos comerciales, use el Raspberry PI 3B u otros dispositivos con los SOC de Intel, Qualcomm o NXP admitidos. 

## <a name="iot-enterprise-manufacturing-guide"></a>Guía de fabricación empresarial de IoT

* [Ahora hay disponible](https://docs.microsoft.com/windows-hardware/manufacture/desktop/iot-ent-overview)una nueva guía de fabricación para Windows 10 IOT Enterprise. 

## <a name="improvements-in-assigned-access"></a>Mejoras en el acceso asignado 

_Windows 10 IoT Enterprise_

* Los quioscos y los signos digitales suelen colocarse en lugares públicos en los que los usuarios ven ampliamente los problemas. Con los informes de estado integrados, los sistemas de administración de dispositivos son conscientes de los problemas automáticamente y pueden emitir acciones correctivas como reiniciar el dispositivo o enviar un técnico de servicio. 
* Reducir los costos de implementación y administración son controladores clave de ROI. Windows 10 IoT Enterprise ha mejorado las características para configurar una experiencia de quiosco a través de un nuevo asistente en la aplicación de configuración, la administración de quioscos con varias aplicaciones y la personalización de la [experiencia del explorador Microsoft Edge para dispositivos de pantalla completa](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy).
* Aunque los generadores de dispositivos tienen una gran flexibilidad para configurar el acceso asignado mediante paquetes de aprovisionamiento, la aplicación de configuración y los sistemas de administración de dispositivos móviles, algunos clientes todavía necesitan más. [Mediante el uso de un nuevo conjunto de API de acceso asignadas](https://docs.microsoft.com/uwp/api/windows.system.userprofile.assignedaccesssettings), los desarrolladores ahora pueden configurar mediante programación el acceso asignado desde dentro de sus aplicaciones.
* Con la versión de octubre de 2018, los clientes pueden especificar una experiencia de inicio automático como parte de la configuración de acceso asignado de varias aplicaciones, por lo que el usuario final siempre puede tener una experiencia de aplicación principal predeterminada.
* Puede controlar lo que el usuario ve en el momento en que se enciende el dispositivo hasta que se apaga. Comience por mostrar su logotipo en lugar del logotipo de Windows en el arranque o aplicaciones de reinicio automático sin mensajes de error después de un bloqueo de la aplicación, un problema del sistema o una interrupción de la alimentación. 
* Puede usar la característica de filtro de escritura unificado (UWF) para crear un dispositivo de "solo lectura" que vuelva a un estado conocido después de un ciclo de energía manteniendo los cambios de disco en la memoria en lugar de escribirlos en el disco. También puede combinar el UWF con la característica de hibernación una vez, reanudar muchos (HORM) para reanudar una sesión predefinida. 


## <a name="more-management-support"></a>Más soporte de administración

_Windows 10 IoT Enterprise_
* Azure IoT Hub ofrece características de administración de dispositivos ligeros y un modelo de extensibilidad que permite a los desarrolladores de dispositivos y en la nube crear soluciones de administración de dispositivos sólidas. La integración con la [Administración de dispositivos IOT de Azure](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotdm) ya está disponible tanto para Windows 10 IOT Core como para la empresa. 

_Windows 10 IoT Core_
* Las empresas que usan [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) para su administración de dispositivos ahora pueden administrar dispositivos de Windows 10 IOT Core junto con sus dispositivos empresariales de Windows 10 IOT y otros dispositivos administrados. Esto proporciona a los operadores una manera coherente de administrar dispositivos IoT de Windows 10 mediante la misma interfaz de administración y los mismos controles. 


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


## <a name="known-issues"></a>Problemas conocidos
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core. Los controladores deben copiarse y registrarse manualmente en el dispositivo.
* Los dispositivos que se han instalado a través de NOOBS no pueden ejecutar la herramienta bcdedit para habilitar al depurador de kernel.
* El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.
