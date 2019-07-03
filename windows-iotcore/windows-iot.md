---
title: Información general de Windows 10 IoT
author: saraclay
ms.author: saclayt
ms.date: 01/30/2018
ms.topic: article
description: Obtenga información sobre qué es Windows 10 IoT y lo que puede hacer con él.
keywords: Windows 10 IoT Enterprise, Windows 10 IoT Core, equipo sin periféricos, voz, características, edición binaria, ediciones
ms.openlocfilehash: 1e1d2769513005a705c48522d4dc7dc034f5d7b9
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "66760392"
---
# <a name="an-overview-of-windows-10-iot"></a>Información general de Windows 10 IoT 

> [!NOTE]
> Los contenedores de Windows 10 solo se pueden usar con Windows IoT Core y Windows IoT Enterprise para implementaciones comerciales en las que se usa Microsoft Azure IoT Edge.

## <a name="what-is-windows-10-iot"></a>¿Qué es Windows 10 IoT?
Windows 10 IoT es un miembro de la familia Windows 10 que aporta potencia de clase empresarial, seguridad y facilidad de uso para el Internet de las cosas.  Aprovecha la experiencia, el ecosistema y la conectividad de la nube que incluye Windows, lo que permite a las organizaciones crear su Internet de las cosas con dispositivos seguros que se pueden aprovisionar con rapidez, son fáciles de administrar y se conectan sin problema a una estrategia de nube global.  

## <a name="windows-10-iot-editions"></a>Ediciones de Windows 10 IoT
Windows 10 IoT está disponible en dos ediciones.  Windows 10 IoT Core es el miembro más pequeño de la familia de sistemas operativos Windows 10.  Aunque solo ejecuta una aplicación, conserva la facilidad de administración y la seguridad que se esperan de Windows 10.  En cambio, Windows 10 IoT Enterprise es una versión completa de Windows 10 con características especializadas para crear dispositivos dedicados que se limitan un conjunto específico de aplicaciones y periféricos. 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Diferencias entre Windows 10 IoT Core y Windows 10 IoT Enterprise

Aunque Windows 10 IoT Core y Windows 10 IoT Enterprise son similares en el nombre, hay diferencias en lo que ofrecen y también en lo que admiten. A continuación se muestra una lista de características en la que se resaltan las diferencias de cada edición.

> |             | Windows 10 IoT Core  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | Experiencia del usuario | Una aplicación para UWP en primer plano a la vez (vea la [documentación de IoT Shell](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoreshell) para el control de la pila de retroceso de aplicaciones) con servicios y aplicaciones complementarios en segundo plano. | Shell de Windows tradicional con características avanzadas de bloqueo |
> | Compatibilidad con equipos sin periféricos | Sí | Sí |
> | Arquitectura de aplicaciones compatible | Solo IU de UWP | Compatibilidad completa con la interfaz de usuario de Windows (por ejemplo, UWP, WinForms, etc.) |
> | Cortana | [*SDK de Cortana*](https://developer.microsoft.com/en-us/cortana/devices) | Sí |
> | Unión a un dominio | Solo AAD | AAD y dominio tradicional |
> | Management | MDM | MDM |
> | Tecnologías de seguridad del dispositivo | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [Arranque seguro, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) y Atestación de estado de dispositivo | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [Arranque seguro, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) y Atestación de estado de dispositivo |
> | Compatibilidad con arquitecturas de CPU | x86, x64 y ARM | x86 y x64 |
> | Concesión de licencias | Contrato de licencia en línea y contratos de OEM insertados, libres de regalías | Contratos de OEM insertados directos e indirectos |
> | Escenarios de uso | [Señalización digital](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), edificio inteligente, puerta de enlace de IoT, HMI, hogar inteligente, dispositivos transportables | Tabletas industriales, punto de servicio comercial, pantalla completa, [señalización digital](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), cajeros automáticos, dispositivos médicos, dispositivos de fabricación, cliente ligero |

Para obtener detalles sobre los requisitos mínimos, visite [el sitio de hardware de Windows](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

Si le interesa obtener más información sobre Punto de servicio, visite la [documentación de UWP sobre este tema](https://aka.ms/pointofservice).

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Diferencias entre Windows 10 Desktop y Windows 10 IoT Core

### <a name="different-features-available-on-desktop-and-iot-core"></a>Distintas características disponibles en Desktop e IoT Core

* Inbox Cortana ya no está disponible en Windows 10 IoT Core desde la versión 1809 (17763). Si lo que busca es comercializar rápidamente un dispositivo habilitado para voz, puede integrar la compatibilidad con Cortana en el dispositivo mediante la [versión preliminar del SDK de dispositivos de Cortana](https://developer.microsoft.com/en-us/cortana/devices).
* [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) no se admite en Windows 10 IoT Core. Para acceder a unidades locales o almacenamiento extraíble, puede implementar esto en una aplicación propia.
* El dispositivo Windows 10 IoT Core arrancará en la [aplicación predeterminada](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) en lugar de un PC de estilo escritorio. El propósito de esta aplicación no es solo proporcionar un shell descriptivo con el que interactuar tras el primer arranque, sino también permitir el uso del [código abierto](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para esta aplicación con el fin de poder utilizar estas características para conectar aplicaciones personalizadas propias.

### <a name="differences-in-driver-supported-areas"></a>Diferencias en las áreas compatibles con el controlador

* Windows 10 Desktop tiene más controladores compatibles que Windows 10 IoT Core. Para hacer que los mismos dispositivos funcionen en Windows 10 IoT Core y en Desktop, es posible que tenga que compilar un controlador a partir de código fuente para un dispositivo Windows 10 IoT Core, o bien buscar otra solución alternativa, especialmente para la arquitectura ARM.
* No hay ningún controlador de fábrica para libusb para Windows 10 IoT Core (ARM); tendrá que compilar a partir del código fuente para seleccionar la arquitectura ARM como destino.

### <a name="differences-in-available-registry-set"></a>Diferencias en el conjunto de registros disponibles

* En Desktop, hay una opción para "ocultar automáticamente las barras de desplazamiento en Windows" que se puede desactivar. Se controla mediante la entrada del Registro siguiente: 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* De forma predeterminada, en los dispositivos Windows 10 IoT Core no hay ningún Registro de este tipo. Tendrá que agregar una entrada del Registro "DynamicScrollbars" si lo quiere.
* Para permitir que las barras de desplazamiento se oculten de forma automática en una aplicación de UWP, puede agregar la entrada del Registro "DynamicScrollbars" y establecer el valor en "1" de esta forma:

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* La clave del Registro se debe establecer desde la cuenta predeterminada. Si el valor XAML ScrollViewer es "Visible", el valor del Registro de 0 forzará la aparición de la barra de desplazamiento, con independencia de que haya contenido suficiente para que se muestre en la interfaz de usuario. Un valor del Registro de 1 mantendrá oculta la barra de desplazamiento hasta que haya contenido suficiente.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* Por último, si el valor de XAML ScrollViewer es "Auto", el valor del Registro de 0 solo mostrará la barra de desplazamiento completa cuando haya contenido suficiente para mostrarla. Cuando el valor del Registro es 1, la barra de desplazamiento aparecerá cuando haya contenido suficiente, o bien se ocultará si no lo hay.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>Diferentes comandos admitidos

* El comando Remove-AppxPackage de PowerShell funciona en Dekstop pero no en Windows 10 IoT Core.
* No todas las carpetas del dispositivo son accesibles para las aplicaciones universales de Windows. En Windows 10 IoT Core puede usar la herramienta FolderPermissions para hacer que una carpeta sea accesible para una aplicación para UWP. Por ejemplo, ejecute FolderPermissions c:\test -e para conceder a las aplicaciones para UWP acceso a la carpeta c:\test. Pero esto no está disponible en Desktop.

Es posible que los comandos que se muestran en esta publicación cambien con el tiempo, ya que Windows 10 IoT Core se actualiza continuamente.

## <a name="iot-edge-support-for-windows-10-iot"></a>Compatibilidad de IoT Edge con Windows 10 IoT
Para más información sobre la compatibilidad de IoT Edge con Windows 10 IoT, puede leer más sobre "Sistemas operativos" en el artículo de Azure IoT Edge [aquí](https://docs.microsoft.com/en-us/azure/iot-edge/support#operating-systems).


## <a name="helpful-resources"></a>Recursos útiles
* [Windows 10 IoT Enterprise](windows-iot-enterprise.md)
* [Windows 10 IoT Core](windows-iot-core.md)
