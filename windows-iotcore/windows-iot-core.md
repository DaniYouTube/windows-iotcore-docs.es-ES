---
title: Información general de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Obtenga información sobre las novedades de Windows 10 IoT Core y lo que puede hacer con él.
keywords: Windows 10 IoT Core, superficie pequeña, sin periféricos
ms.openlocfilehash: 0fbcc6a96f8e35227acf32a9507ed3c7a038a83d
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174049"
---
# <a name="an-overview-of-windows-10-iot-core"></a>Información general de Windows 10 IoT Core

> [!NOTE]
> Contenedores de Windows 10 solo pueden usarse con Windows IoT Core y Windows IoT Enterprise para las implementaciones comerciales de uso de Microsoft Azure IoT Edge.

## <a name="what-is-windows-10-iot-core"></a>¿Qué es Windows 10 IoT Core?
Windows 10 IoT Core es una versión de Windows 10 que está optimizado para los dispositivos más pequeños con o sin una pantalla que se ejecutan en tanto ARM y dispositivos x86/x64. La documentación de Windows IoT Core, proporciona información sobre conectar, administrar, actualizar, proteger los dispositivos y mucho más. 

Si está listo para ir al siguiente nivel e inicio commercializing la solución, puede aprender fabricar con Windows 10 IoT Core con nuestro [Guía de fabricación de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). 

## <a name="getting-started"></a>Introducción

Antes de intentar fabricar un dispositivo, es mejor primera try y prototipo de un dispositivo con Windows 10 IoT Core. De este modo, puede comprender las características que necesitará y qué configuraciones que deseará cuando se trata en la fabricación.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Tema</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. Elija un tablero de prototipo</a></p></td>
<td align="left"><p>Eche un vistazo a los prototipos de placas comunes y elija uno para iniciar con la creación de prototipos.</p></td>
</tr>

<tr class="odd">
<td align="left"><p>2. Flash una imagen de prototipo</p></td>
<td align="left"><p>Vaya a nuestras secciones tutoriales para aprender a flash imágenes de prototipo en los dispositivos seleccionados. </p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">2. 3. Instalar la aplicación</a></p></td>
<td align="left"><p>Obtenga información sobre cómo instalar la aplicación con distintas herramientas.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. Implementar la aplicación</a></p></td>
<td align="left"><p>Obtenga información sobre cómo implementar una aplicación mediante Visual Studio.</p></td>
</tr>

</tbody>
</table>

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
