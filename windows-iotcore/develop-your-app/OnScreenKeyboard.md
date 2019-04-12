---
title: Configurar el dispositivo con cabezal con el de Windows 10 IoT Core en pantalla teclado
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Información en pantalla sobre el nuevo teclado y cómo configurarlo en Windows 10 IoT Core, versión 1809.
keywords: Windows 10 IoT Core, táctil, teclado, en la pantalla, en la pantalla, sip, entrada, el ime, echar dictado, voz, speech, osk
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514275"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>Teclado en pantalla para dispositivos puntas

En Windows 10 IoT Core, versión 1809, el que aparecen en pantalla componente teclado ha cambiado significativamente y mejor! IoT Core ahora usa los mismos componentes de teclado táctil como la edición de escritorio de Windows.

## <a name="new-features"></a>Nuevas características
La nueva implementación de teclado proporciona las siguientes ventajas para el desarrollo con cabezal del dispositivo:

* [Todo el conjunto de diseños de idioma de teclado de Windows](#windows-keyboard-language-layouts)
* [Compatibilidad con los ámbitos de entrada (por ejemplo, dirección de correo electrónico, PIN numérico, el campo de búsqueda, etcetera.)](#support-for-input-scopes)
* [Editor de métodos de entrada (IME)](#input-method-editor-ime)
* [Los campos de entrada de texto oculto para que no sean](#non-obscured-text-input-fields)
* [Modo de dictado](#dictation-mode)
* [Una selección de preferencias de la interfaz de usuario](#user-interface-configuration)

## <a name="feature-packages"></a>Paquetes de características

Para las imágenes de la creación de prototipos (desarrollo), el que aparecen en pantalla ya se incluye la característica de teclado, pero deberá habilitarlo desde la configuración de dispositivos en el [Windows Device Portal](../manage-your-device/deviceportal.md#iot-specific-features).

Agregará los siguientes paquetes de la característica opcional para la comercialización, el teclado en pantalla a la imagen:
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> Para obtener más información acerca de las características de IoT Core, consulte [lista de características de IoT Core](/windows-hardware/manufacture/iot/iot-core-feature-list) y [Guía de fabricación de IoT Core](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

## <a name="windows-keyboard-language-layouts"></a>Diseños de idioma de teclado de Windows

Con esta versión, los diseños de idioma admitidos ha expandido para incluir el conjunto completo de los que están disponibles en la edición de Windows desktop. Para permitir que los usuarios seleccionar entre los diseños de otro idioma, normalmente incluiría la interfaz de usuario de selección en el área de configuración de la aplicación. La siguiente API se proporciona para habilitar la aplicación para establecer el idioma que la pantalla usará teclado:

[Windows.Globalization.Language.TrySetInputMethodLanguageTag](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

Un ejemplo de esta API puede verse en la [aplicación de ejemplo IoTCoreDefaultApp](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp), en el [LanguageManager.cs](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) archivo.

## <a name="support-for-input-scopes"></a>Compatibilidad con los ámbitos de entrada

En versiones anteriores, el ámbito de entrada EmailSmtpAddress estaba disponible. En esta versión, el conjunto completo de ámbitos de entrada están disponibles. El siguiente tema explica los ámbitos de entrada y cómo usarlos en sus aplicaciones:

[Usar el ámbito de entrada para cambiar el teclado táctil](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>Editor de métodos de entrada (IME)

Esta versión proporciona un Editor de métodos de entrada, que es necesario para cualquier lenguaje que tenga más graphemes que hay teclas del teclado, como el chino, japonés y coreano.

## <a name="non-obscured-text-input-fields"></a>Los campos de entrada de texto oculto para que no sean

En versiones anteriores, el teclado táctil podría interferir con el campo de texto con foco para que el usuario no pudo ver lo que se escribe. Esta versión corrige este problema si se desplaza automáticamente el campo de texto en la vista para que ya no está oculto por la pantalla táctil.

## <a name="dictation-mode"></a>Modo de dictado

Cuando se establece el idioma de entrada en el idioma del sistema operativo, que es la predeterminada, la característica de entrada de reconocimiento de voz está disponible.
Para mostrar el botón de dictado en el teclado, consulte la sección siguiente sobre [configuración de la interfaz de usuario](#user-interface-configuration).

## <a name="user-interface-configuration"></a>Configuración de la interfaz de usuario

El teclado en pantalla proporciona varias opciones configurables para su interfaz de usuario. Estas se configuran mediante el registro.
Durante el desarrollo puede usar [PowerShell](/windows/iot-core/connect-your-device/powershell) o [Secure Shell (SSH)](/windows/iot-core/connect-your-device/ssh). Para crear una imagen de OEM, el mecanismo preferido para establecer los valores del registro es el `OEMInput.xml` archivo que se trata aquí:

[Personalizaciones en tiempo de ejecución](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> La mayoría de los valores del registro que se documentan aquí surtirá efecto mientras el teclado en pantalla es visible.
> Esto le permite durante el desarrollo para probar fácilmente diferentes combinatations de valores de configuración, ver inmediatamente los cambios resultantes en tiempo real. Si una configuración no surte efecto inmediatamente, deberá reiniciar el dispositivo para ver los cambios en la interfaz de usuario de teclado.

### <a name="keyboard-height"></a>Alto del teclado

De forma predeterminada, el teclado táctil usará el 45% inferior del alto de la pantalla. Esto puede parecer demasiado grande o pequeño en su dispositivo, dependiendo de su tamaño y resolución. Puede ajustar el alto hasta un máximo de dos tercios el alto de la pantalla. Cualquier valor fuera del intervalo se unirá en intervalo. Dado que esto se especifica como un punto flotante de valor, permite para la precisión de nivel de píxeles. Solo tiene que aplicar la siguiente fórmula para calcular el porcentaje:

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

Por ejemplo, para cambiar el alto en % 56.783, establecería el valor del registro siguiente:
```console
set OskRootKey=HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK
reg.exe ADD "%OskRootKey%" /v MaxHeightPercentage /t REG_SZ /d "56.783" /f
```
o desde PowerShell:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
Set-ItemProperty -Path . -Name MaxHeightPercentage -Type String -Value 56.783
```

> [!NOTE]
> El tipo de valor del registro debe ser una cadena (`REG_SZ`), de modo que pueden representar con los valores fraccionarios.
> un separador decimal. Uso de DWord (`REG_DWORD`) le _no_ profesional, incluso para los porcentajes de números enteros.

### <a name="additional-preferences"></a>Preferencias adicionales

El conjunto de preferencias restantes son valores de cadena en la subclave preferencias:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| Valor del registro               | Valor predeterminado      | Descripción                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | "0"                | "0" permite a los comentarios clave en audio; "1", se deshabilita.                                          |
| Dictation_Disabled           | "1"                | "0" se muestra el botón de dictado (reconocimiento de voz); "1" lo oculta.<br/> (vea la nota siguiente)             |
| KeyboardModeEnabled_full     | "0"                | "0" deshabilita el modo de teclado completo; "1" lo habilita.                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0" deshabilita el modo de teclado estrecha; "1" lo habilita.                                              |
| KeyboardModeEnabled_wide     | "1"                | "0" deshabilita el modo de ancho de teclado; "1" lo habilita.                                                |
| ModeOrder                    | "ancho; restringir; total" | El orden (de izquierda a derecha) en el que los modos se enumeran en el menú desplegable modo, si habilitado |
| SettingsMenuKey_Collapsed    | "0"                | Oculta el menú desplegable modo. Establezca esta opción en "1" Si está habilitado el modo de solo uno.                         |
| Paste_Disabled               | "0"                | "0" se muestra el botón Pegar; "1" lo oculta.<br/> Cambio surte efecto después de reiniciar el equipo.                    |
| CloseButton_Disabled         | "0"                | "0" se muestra el botón de cierre; "1", se oculta el botón Cerrar<br/> Cambio surte efecto después de reiniciar el equipo.       |
| EmojiKeyEnabled              | "0"                | "0" oculta la clave Emoji; "1" se muestra, lo que permite al usuario que escriba caracteres Emoji.                 |

> [!NOTE]
> Modo de dictado requiere un paquete de voz para la instalación de idioma de entrada seleccionado, así como un dispositivo de entrada de audio. Si una coincidencia paquetes de voz no está instalado, no se mostrará el botón de dictado.
> 
> Todas las imágenes incluyen el lenguaje de voz en-US. Se instalan otros paquetes de voz como características opcionales.
> Para obtener más información acerca de las características de IoT, consulte [lista de características de IoT Core](/windows-hardware/manufacture/iot/iot-core-feature-list) y [Guía de fabricación de IoT Core](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

Por ejemplo, para habilitar solamente `wide` modo de teclado, en PowerShell, podría hacer lo siguiente:
```powershell
set OskRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK"
cd $OskRootKey
mkdir Preferences
cd Preferences
Set-ItemProperty . -Name KeyboardModeEnabled_full -Value "0"      # Optional, since the default is "0"
Set-ItemProperty . -Name KeyboardModeEnabled_narrow -Value "0"
Set-ItemProperty . -Name KeyboardModeEnabled_wide -Value "1"      # Optional, since the default is "1"
Set-ItemProperty . -Name SettingsMenuKey_Collapsed -Value "1"
```
