---
title: Introducción al Shell de IoT
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo aprovechar el IoT Shell para navegar entre navegaciones en el dispositivo.
keywords: Windows iot, IoT core shell, las aplicaciones, aplicaciones de primer plano, aplicaciones en segundo plano
ms.openlocfilehash: be72fabc91fc5748a029b61ebd9a306deb23f726
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514764"
---
# <a name="iot-shell-overview"></a>Introducción al Shell de IoT

Este documento describe las aplicaciones de IoT Shell, primer y segundo plano y cómo navegar entre estas aplicaciones en el dispositivo.

## <a name="iot-shell-foreground-and-background-apps"></a>Shell de IoT, primer plano y aplicaciones en segundo plano

El dispositivo de IoT Core ejecuta el IoT Shell. Tiene muchas responsabilidades, pero su trabajo principal consiste en asegurarse de que se inician las aplicaciones de inicio registrados. Tiene dos modos: Puntas y sin periféricos. En el modo de Headed, el IoT Shell se iniciará una aplicación de inicio registrados único que se mostrará su interfaz de usuario en pantalla completa (también conocido como una aplicación Headed). Modo con cabezal supone que tiene una pantalla conectada y muestra la interfaz de usuario. En el modo "desatendido" (se explica en detalle [aquí](../learn-about-hardware/HeadlessMode.md)), no hay ninguna interfaz de usuario; solo las aplicaciones en segundo plano se inicia el IoT Shell.

Estas son las principales diferencias entre las aplicaciones de primer y segundo plano:

- **Las aplicaciones de primer plano** tiene una interfaz de usuario. Uno de ellos se inicia en el inicio cuando el dispositivo está en modo con cabezal. Todas las aplicaciones de primer plano se registran en el dispositivo y el usuario puede cambiar entre las aplicaciones de primer plano durante la operación del dispositivo.

- **En segundo plano aplicaciones** no tiene ninguna interfaz de usuario y, por tanto, guardar los recursos de dispositivo mediante la desactivación de la pila de la interfaz de usuario. Aplicaciones en segundo plano a menudo ejecutan continuamente a partir del inicio y a menudo se utilizan para supervisar el dispositivo.

## <a name="switching-between-apps-with-a-home-app"></a>Cambiar entre las aplicaciones con una aplicación de inicio

En este momento, la aplicación de inicio permite crear una aplicación principal para Windows 10 IoT Core, que le permite cambiar entre las aplicaciones de primer plano diferentes. 

El **aplicación de inicio de IoT** ([ejemplo](https://developer.microsoft.com/en-us/windows/iot/samples/iotstartapp) representa una aplicación de inicio simple que enumera las aplicaciones instaladas en el dispositivo y, después, inicia una mediante las APIs PackageManager.

## <a name="switching-between-apps-with-hid-injection-keys"></a>Cambiar entre las aplicaciones con las claves de inserción de HID

Las instrucciones siguientes muestran cómo activar la compatibilidad con teclas de acceso rápido a través de entradas en el registro. Si está creando su propia imagen y para admitir la debajo de teclas de acceso rápido (principal, la aplicación anterior y siguiente aplicación) sin necesidad de tener acceso al registro, puede incluir un paquete de la característica opcional que controla estos pasos para usted.

Se llama para buscar el paquete de características: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** y la característica se denomina **IOT_SHELL_HOTKEY_SUPPORT**. Consulte la [paquete de ejemplo Settings.HotKey](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) para obtener un ejemplo.

El resto de este documento explica cómo implementar manualmente esta característica.

### <a name="return-home"></a>Página principal de retorno

Con Windows 10 IoT Anniversary Update (1607), el IoT Shell admite traer la ventana de la aplicación de forma predeterminada al primer plano cuando se está ejecutando otra aplicación al presionar la tecla "GO HOME", que se establece en la versión de Windows en el botón un teclado. Si no tiene un teclado en el dispositivo de IoT y necesite insertar eventos de teclado de bajo nivel a través de [HID inyección](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), o si desea volver a asignar la funcionalidad "GO HOME" a una clave diferente en la aplicación, puede ajustar el valor de clave en el registro. Por ejemplo, para habilitar al presionar el ESCAPE de clave (0x1B) a "GO HOME", escriba el siguiente comando en el registro:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

Como un archivo de registro, esto tiene el aspecto siguiente:

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>Cambiar entre las aplicaciones

Como alternativa, si desea cambiar entre las aplicaciones de primer plano, puede configurar ALT+TAB (próxima aplicación) y la funcionalidad de Alt-Mayús-Tab (aplicación anterior) en la imagen, escriba el comando siguiente en el registro:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

Como un archivo de registro, esto tiene el aspecto siguiente:
``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>Bit Translation

Las entradas anteriores del archivo REG descodificación de izquierda a derecha como sigue:

- Bits 0-15: Código de tecla virtual (es decir, 1B, 00 para ESCAPE). Consulte [código de tecla Virtual](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) para una lista completa de los valores de código de tecla
- 19 de 16 bits: Tecla modificadora. 0 x 0 no = ningún modificador, 0 x 1 = ALT, 0 x 2 = CTRL y 0 x 4 = MAYÚS. Combinación de teclas suma los valores (es decir, ALT + MAYÚS es 0 x 5)
- Bits de 20: 47: Reservado para uso futuro; debe ser 0
- 62 de 48 bits:  Acción
    - 0 = Inicio
    - 1 = la vista anterior (no funcionen en futuras versiones)
    - 2 = vista siguiente (no funcionen en futuras versiones)
- Bit 63: Reservado; debe ser 0

