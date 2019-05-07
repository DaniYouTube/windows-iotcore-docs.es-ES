---
title: Información general de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Obtenga información sobre las novedades de Windows 10 IoT Core y lo que puede hacer con él.
keywords: Windows 10 IoT Core, superficie pequeña, sin periféricos
ms.openlocfilehash: d5b9c59ad735d66b4812e6303f6298a33da44d33
ms.sourcegitcommit: 1f6afcfee0cb5557dc21c7b15e199bc557d8eedb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65171358"
---
# <a name="windows-10-iot-core"></a>Windows 10 IoT Core

> [!NOTE]
> Contenedores de Windows 10 solo pueden usarse con Windows IoT Core y Windows IoT Enterprise para las implementaciones comerciales de uso de Microsoft Azure IoT Edge.

## <a name="what-is-windows-10-iot-core"></a>¿Qué es Windows 10 IoT Core?
Windows 10 IoT Core es una versión de Windows 10 que está optimizado para los dispositivos más pequeños con o sin una pantalla que se ejecutan en tanto ARM y dispositivos x86/x64. La documentación de Windows IoT Core, proporciona información sobre conectar, administrar, actualizar, proteger los dispositivos y mucho más. 

## <a name="getting-started"></a>Introducción
Para empezar a trabajar con Windows 10 IoT Core, hemos creado un [Windows 10 IoT Core Quickstarter](tutorials/Tutorials.md) que le ayudarán a familiarizarse con la plataforma rápidamente. 

Desde allí, aún puede experimentar con la plataforma mediante el desarrollo de su propia aplicación o comenzar a hacer planes para poner el dispositivo en el mercado para comercializar su dispositivo. Para empezar a trabajar con commercializing, consulte los Traer un dispositivo en el mercado de la sección en la [artículo de introducción](https://docs.microsoft.com/windows/iot-core/getstarted).

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Diferencias entre el escritorio de Windows 10 y Windows 10 IoT Core

### <a name="different-features-available-on-desktop-and-iot-core"></a>Distintas características disponibles en el escritorio y IoT Core

* Inbox Cortana ya no está disponible en Windows 10 IoT Core desde la versión 1809 (17763). Si desea para poner un dispositivo habilitado por voz al mercado rápidamente, puede integrar el soporte técnico de Cortana en el dispositivo mediante el [preview del SDK de dispositivos de Cortana](https://developer.microsoft.com/en-us/cortana/devices).
* El [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) no se admite en Windows 10 IoT Core. Para obtener acceso a las unidades locales o almacenamiento extraíble, puede implementar en su propia aplicación.
* El dispositivo Windows 10 IoT Core arrancará en el [aplicación predeterminada](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) en lugar de un PC de sobremesa. El propósito de esta aplicación no es solo para proporcionarle un shell descriptivo para interactuar con tras el primer arranque, pero que también le permite usar el [código abierto](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para esta aplicación para que se pueden usar estas características para de plug and play sus propias aplicaciones personalizadas.

### <a name="differences-in-driver-supported-areas"></a>Diferencias en las áreas compatibles con el controlador

* Windows 10 escritorio más ha admitido controladores de Windows 10 IoT Core. Para que el mismo dispositivos funcionan en Windows 10 IoT Core, como en el escritorio, es posible que necesite compilar un controlador de origen para un dispositivo Windows 10 IoT Core o buscar otra solución alternativa, especialmente para la arquitectura ARM.
* No hay ningún controlador de fábrica para libusb para Windows 10 IoT Core (ARM) - deberá compilar del origen al destino de la arquitectura ARM.

### <a name="differences-in-available-registry-set"></a>Diferencias en el conjunto disponible en el registro

* En el escritorio, hay una opción para "Automáticamente ocultar las barras de desplazamiento en Windows" que se pueden establecer en off. Se controla mediante la entrada del registro siguiente: 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* No hay ningún registro de este tipo en los dispositivos Windows 10 IoT Core de forma predeterminada. Deberá agregar un registro de "Barras de desplazamiento dinámico" Si lo desea.
* Para habilitar las barras de desplazamiento de ocultar automáticamente en una aplicación de UWP, puede agregar el "DynamicScrollbars" registrar y establecer el valor en "1" similar al siguiente:

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* Debe establecer la clave del registro de la cuenta predeterminada. Si la configuración de XAML de ScrollViewer es "Visible", el valor del registro nEl 0 forzará la barra de desplazamiento aparezcan regardlss si no hay suficiente contenido para que el desplazamiento aparezca en la interfaz de usuario. El valor del registro 1 mantendrá la barra de desplazamiento oculta hasta que no hay suficiente contenido.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* Por último, si la configuración de ScrollViewer XAML es "Auto", a continuación, el valor del registro 0 sólo mostrará la barra de desplazamiento completo cuando no hay suficiente contenido para mostrar la barra de desplazamiento. Cuando la configuración del registro es 1, aparecerá la barra de desplazamiento, a continuación, cuando no hay suficiente contenido u oculta si no hay ningún contenido.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>Diferentes comandos admitidos

* El comando Remove-AppxPackage de PowerShell funciona en el escritorio, pero no en Windows 10 IoT Core.
* No todas las carpetas en el dispositivo son accesibles para las aplicaciones universales de Windows. Puede usar la herramienta FolderPermissions para crear una carpeta accesibles para una aplicación para UWP en Windows 10 IoT Core. Por ejemplo, ejecute FolderPermissions c:\test -e para dar acceso de aplicaciones UWP a la carpeta c:\test. Sin embargo, esto no está disponible en el escritorio.

Todas las diferencias que se describen en esta publicación pueden no ser válidas en el futuro porque se actualiza constantemente de Windows 10 IoT Core.

## <a name="helpful-resources"></a>Recursos útiles
[Lea nuestra documentación](https://docs.microsoft.com/windows/iot-core/) para obtener más información acerca de Windows 10 IoT Core.
