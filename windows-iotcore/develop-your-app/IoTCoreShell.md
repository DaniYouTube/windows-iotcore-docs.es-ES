---
title: Información general sobre el shell de IoT
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo aprovechar el shell de IoT para navegar entre las navegaciones del dispositivo.
keywords: Windows IOT, Shell de IoT Core, aplicaciones, aplicaciones de primer plano, aplicaciones en segundo plano
ms.openlocfilehash: e23f121073a84f9c36a390eb126e83b4f4215fee
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918240"
---
# <a name="iot-shell-overview"></a>Información general sobre el shell de IoT

En este documento se tratan el shell de IoT, las aplicaciones de primer plano y en segundo plano, y cómo navegar entre estas aplicaciones en el dispositivo.

## <a name="iot-shell-foreground-and-background-apps"></a>Aplicaciones de Shell de IoT, de primer plano y en segundo plano

El dispositivo de IoT Core ejecuta el shell de IoT. Tiene muchas responsabilidades, pero su trabajo principal es asegurarse de que se inician las aplicaciones de inicio registradas. Tiene dos modos: con cabeza y sin periféricos. En el modo de cabeza, el shell de IoT iniciará una sola aplicación de inicio registrada que mostrará su interfaz de usuario en pantalla completa (también conocida como aplicación de encabezado). El modo de cabeza supone que tiene una pantalla conectada y muestra la interfaz de usuario. En el modo sin periféricos (se explica con detalle [aquí](../learn-about-hardware/HeadlessMode.md)), no hay ninguna interfaz de usuario; el shell de IoT solo inicia aplicaciones en segundo plano.

Estas son las principales diferencias entre las aplicaciones de primer y segundo plano:

- **Las aplicaciones de primer plano** tienen una interfaz de usuario. Una de ellas se inicia en el inicio cuando el dispositivo está en modo de cabeza. Todas las aplicaciones en primer plano están registradas en el dispositivo y el usuario puede cambiar entre las aplicaciones en primer plano durante el funcionamiento del dispositivo.

- **Las aplicaciones en segundo plano** no tienen interfaz de usuario y, por tanto, guardan recursos de dispositivo desactivando la pila de IU. Las aplicaciones en segundo plano se ejecutan a menudo continuamente desde el inicio y a menudo se usan para supervisar el dispositivo.

## <a name="switching-between-apps-with-a-home-app"></a>Cambiar entre aplicaciones con una aplicación principal

En este momento, la aplicación de inicio le permite crear una aplicación doméstica para Windows 10 IoT Core, que le permite cambiar entre diferentes aplicaciones de primer plano. 

La **aplicación de inicio de IOT** ([ejemplo](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) representa una sencilla aplicación de inicio que enumera las aplicaciones instaladas en el dispositivo y, a continuación, inicia una mediante las API de PackageManager.

## <a name="switching-between-apps-with-hid-injection-keys"></a>Cambiar entre aplicaciones con claves de inyección de HID

Las instrucciones siguientes muestran cómo activar la compatibilidad con la tecla de acceso rápido a través de entradas en el registro. Si va a compilar su propia imagen y desea admitir las siguientes teclas de acceso rápido (Inicio, aplicación anterior y aplicación siguiente) sin necesidad de acceder al registro, puede incluir un paquete de características opcional que se ocupe de estos pasos.

Se llama al paquete de características que se va a buscar: **Microsoft-OneCore-IoTUAP-Shell-hotkeys-Feature-package. cab** y la característica se denomina **IOT_SHELL_HOTKEY_SUPPORT**. Vea el [paquete de ejemplo Settings. Hotkey](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) para obtener un ejemplo.

En el resto de este documento se explica cómo implementar esta característica de forma manual.

### <a name="return-home"></a>Devolver Inicio

Con la actualización de aniversario de Windows 10 IoT (1607), el shell de IoT permite poner la ventana de la aplicación predeterminada en primer plano cuando otra aplicación se está ejecutando presionando la tecla "ir a Inicio", que se establece en la versión del botón de Windows de un teclado. Si no tiene un teclado en el dispositivo IoT y necesita insertar eventos de teclado de bajo nivel a través de la [inyección de HID](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), o si solo desea volver a asignar la funcionalidad "ir a la Página principal" a otra clave de la aplicación, puede ajustar el valor de clave en el registro. Por ejemplo, para habilitar la tecla ESC (0x1B) en "GO HOME", escriba el siguiente comando en el registro:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

Como archivo REG, tiene el siguiente aspecto:

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>Cambiar entre aplicaciones

Como alternativa, si desea cambiar entre las aplicaciones de primer plano, puede configurar la funcionalidad de la pestaña Alt (aplicación siguiente) y Mayús-Alt-Tab (aplicación anterior) en la imagen. para ello, escriba el siguiente comando en el registro:

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

Como archivo REG, tiene el siguiente aspecto: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>Traducción de bits

Las entradas del archivo REG anteriores descodifican de izquierda a derecha como se indica a continuación:

- Bits 0-15: código de tecla virtual (es decir, 1B, 00 para ESCAPE). Consulte el [código de tecla virtual](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) para ver la lista completa de valores de código clave.
- Bits 16-19: tecla modificadora. 0X0 = sin modificador, 0x1 = ALT, 0X2 = CTRL y 0x4 = Mayús. La combinación de claves suma los valores (es decir, ALT + MAYÚS es 0X5)
- Bits 20-47: reservado para uso futuro; debe ser 0
- Bits 48-62: acción
    - 0 = Inicio
    - 1 = vista anterior (puede que no funcione en versiones futuras)
    - 2 = vista siguiente (puede que no funcione en versiones futuras)
- Bit 63: reservado; debe ser 0

