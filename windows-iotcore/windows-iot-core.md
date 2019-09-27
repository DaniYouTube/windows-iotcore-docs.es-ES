---
title: Información general de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 01/18/2018
ms.topic: article
description: Obtenga información sobre qué es Windows 10 IoT Core y lo que puede hacer con él.
keywords: Windows 10 IoT Core, superficie pequeña, equipo sin periféricos
ms.openlocfilehash: a1f2ce0835dcb40efc71f2b4d0d4733b781b0799
ms.sourcegitcommit: e3457de2e13ff89142a91cb8af2da4bf2e41ad20
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "70159286"
---
# <a name="an-overview-of-windows-10-iot-core"></a>Información general de Windows 10 IoT Core

> [!NOTE]
> Se admiten contenedores Windows para implementaciones comerciales en Windows Server, Windows IoT Server, Windows IoT Enterprise y Windows IoT Core.  A partir de la actualización de octubre de 2018 de Windows (compilación 17763), los contenedores Windows solo se pueden usar con Windows Enterprise y Professional para fines de desarrollo y pruebas.

## <a name="what-is-windows-10-iot-core"></a>¿Qué es Windows 10 IoT Core?
Windows 10 IoT Core es una versión de Windows 10 optimizada para dispositivos más pequeños con o sin pantalla, y que se ejecutan en dispositivos ARM y x86 o x64. La documentación de Windows IoT Core, proporciona información sobre la conexión, administración, actualización y protección de los dispositivos, y mucho más. 

Si está listo para pasar al siguiente nivel y empezar a comercializar la solución, puede aprender a fabricar con Windows 10 IoT Core con nuestra [Guía de fabricación de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). 

## <a name="getting-started"></a>Introducción

Antes de intentar fabricar un dispositivo, primero es recomendable probar y diseñar un prototipo de un dispositivo con Windows 10 IoT Core. De este modo, puede comprender las características que va a necesitar y las configuraciones que le interesarán cuando llegue el momento de la fabricación.

<table>  
<colgroup> <col width="50%" /> <col width="50%" /> </colgroup>  
<thead>  
<tr class="header">  
<th align="left">Tema</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. Selección de una placa de prototipo</a></p></td>
<td align="left"><p>Examine placas de prototipo comunes y elija una con la que empezar a crear prototipos.</p></td>
</tr>

<tr class="odd">
<td align="left"><p>2. Instalación de una imagen de prototipo</p></td>
<td align="left"><p>Vaya a las secciones de los tutoriales para obtener información sobre cómo instalar imágenes de prototipo en los dispositivos seleccionados. </p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appinstaller">2. 3. Instalación de la aplicación</a></p></td>
<td align="left"><p>Obtenga información sobre cómo instalar la aplicación mediante distintas herramientas.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/appdeployment">4. Implementación de la aplicación</a></p></td>
<td align="left"><p>Obtenga información sobre cómo implementar una aplicación mediante Visual Studio.</p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Diferencias entre Windows 10 Desktop y Windows 10 IoT Core

### <a name="different-features-available-on-desktop-and-iot-core"></a>Distintas características disponibles en Desktop e IoT Core

* Inbox Cortana ya no está disponible en Windows 10 IoT Core desde la versión 1809 (17763). Si lo que busca es comercializar rápidamente un dispositivo habilitado para voz, puede integrar la compatibilidad con Cortana en el dispositivo mediante la [versión preliminar del SDK de dispositivos de Cortana](https://developer.microsoft.com/en-us/cortana/devices).
* [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) no se admite en Windows 10 IoT Core. Para acceder a unidades locales o almacenamiento extraíble, puede implementar esto en una aplicación propia.
* De fábrica, el dispositivo Windows 10 IoT Core arrancará en la [aplicación predeterminada](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) en lugar de un PC de estilo escritorio. Pero para la comercialización, **es obligatorio** reemplazar esta aplicación predeterminada por una personalizada o una aplicación predeterminada que se pueda modificar. El propósito de esta aplicación no es solo proporcionar un shell descriptivo con el que interactuar tras el primer arranque, sino también permitir el uso del [código abierto](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para esta aplicación con el fin de poder utilizar estas características para conectar aplicaciones personalizadas propias.

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

* El comando Remove-AppxPackage de PowerShell funciona en Desktop pero no en Windows 10 IoT Core.
* No todas las carpetas del dispositivo son accesibles para las aplicaciones universales de Windows. En Windows 10 IoT Core puede usar la herramienta FolderPermissions para hacer que una carpeta sea accesible para una aplicación para UWP. Por ejemplo, ejecute FolderPermissions c:\test -e para conceder a las aplicaciones para UWP acceso a la carpeta c:\test. Pero esto no está disponible en Desktop.

Todas las diferencias que se describen en esta publicación pueden no ser válidas en el futuro, ya que Windows 10 IoT Core se actualiza constantemente.

## <a name="helpful-resources"></a>Recursos útiles
[Lea nuestra documentación](https://docs.microsoft.com/windows/iot-core/) para obtener más información sobre Windows 10 IoT Core.
