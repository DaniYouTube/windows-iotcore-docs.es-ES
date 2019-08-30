---
title: Configuración del dispositivo con el teclado Windows 10 IoT Core en pantalla
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: Obtenga información sobre el nuevo teclado en pantalla y cómo configurarlo en Windows 10 IoT Core, versión 1809.
keywords: Windows 10 IoT Core, Touch, teclado, OSK, en pantalla, en pantalla, SIP, entrada, IME, punta, dictado, voz, voz
ms.custom: RS5
ms.openlocfilehash: 100aeb484690c462deac56dcadf7d17667487ae2
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169213"
---
# <a name="on-screen-keyboard-for-headed-devices"></a>Teclado en pantalla para dispositivos con cabeza

En Windows 10 IoT Core, versión 1809, el componente teclado en pantalla ha cambiado significativamente y, para mejorar el rendimiento. IoT Core ahora usa los mismos componentes de teclado táctil que la edición de escritorio de Windows.

## <a name="new-features"></a>Características nuevas
La nueva implementación de teclado proporciona las siguientes ventajas al desarrollo de dispositivos:

* [Todo el conjunto de diseños de idioma del teclado de Windows](#windows-keyboard-language-layouts)
* [Compatibilidad con ámbitos de entrada (por ejemplo, la dirección de correo electrónico, el PIN numérico, el campo de búsqueda, etc.)](#support-for-input-scopes)
* [Editor de métodos de entrada (IME)](#input-method-editor-ime)
* [Campos de entrada de texto no ocultos](#non-obscured-text-input-fields)
* [Modo de dictado](#dictation-mode)
* [Selección de las preferencias de la interfaz de usuario](#user-interface-configuration)

## <a name="feature-packages"></a>Paquetes de características

En el caso de las imágenes de creación de prototipos (desarrollo), la característica de teclado en pantalla ya está incluida, pero tendrá que habilitarla en la configuración del dispositivo en el [portal de dispositivos de Windows](../manage-your-device/deviceportal.md#iot-specific-features).

Para la comercialización, los siguientes paquetes de características opcionales agregarán el teclado en pantalla a la imagen:
* IOT_SHELL_ONSCREEN_KEYBOARD
* IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

> [!TIP]
> Para más información sobre las características principales de IoT, consulte la [lista de características principales](/windows-hardware/manufacture/iot/iot-core-feature-list) de IOT y la [Guía de fabricación de IOT Core](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

## <a name="windows-keyboard-language-layouts"></a>Diseños de idioma del teclado de Windows

Con esta versión, los diseños de idioma admitidos se han expandido para incluir el conjunto completo de los disponibles en la edición de escritorio de Windows. Para permitir que los usuarios seleccionen entre diferentes diseños de idioma, normalmente incluiría la interfaz de usuario de selección en el área de configuración de la aplicación. La siguiente API se proporciona para permitir que la aplicación establezca el idioma que usará el teclado en pantalla:

[Windows. Globalization. Language. TrySetInputMethodLanguageTag](/uwp/api/windows.globalization.language.trysetinputmethodlanguagetag)

Puede verse un ejemplo de esta API en la [aplicación de ejemplo IoTCoreDefaultApp](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp), en el archivo [LanguageManager.CS](https://github.com/Microsoft/Windows-iotcore-samples/blob/develop/Samples/IoTCoreDefaultApp/CS/IoTCoreDefaultApp/Presenters/LanguageManager.cs) .

## <a name="support-for-input-scopes"></a>Compatibilidad con ámbitos de entrada

En versiones anteriores, solo estaba disponible el ámbito de entrada EmailSmtpAddress. En esta versión, el conjunto completo de ámbitos de entrada está disponible. En el tema siguiente se explican los ámbitos de entrada y cómo usarlos en las aplicaciones:

[Usar el ámbito de entrada para cambiar el teclado táctil](/windows/uwp/design/input/use-input-scope-to-change-the-touch-keyboard)

## <a name="input-method-editor-ime"></a>Editor de métodos de entrada (IME)

Esta versión proporciona un editor de métodos de entrada, que es necesario para cualquier idioma que tenga más graphemes que claves en el teclado, como el chino, el japonés y el coreano.

## <a name="non-obscured-text-input-fields"></a>Campos de entrada de texto no ocultos

En versiones anteriores, el teclado táctil podría ocultar el campo de texto enfocado para que el usuario no pudiera ver lo que estaba escribiendo. Esta versión corrige este problema desplazando automáticamente el campo de texto a la vista para que ya no esté oculto por el teclado táctil.

## <a name="dictation-mode"></a>Modo de dictado

Cuando el idioma de entrada se establece en el idioma del sistema operativo, que es el valor predeterminado, la característica de entrada de reconocimiento de voz está disponible.
Para mostrar el botón dictado en el teclado, consulte la sección siguiente sobre configuración de la [interfaz de usuario](#user-interface-configuration).

## <a name="user-interface-configuration"></a>Configuración de la interfaz de usuario

El teclado en pantalla proporciona varias opciones configurables para su interfaz de usuario. Estos se configuran a través del registro.
Durante el desarrollo, puede usar [PowerShell](/windows/iot-core/connect-your-device/powershell) o [Secure Shell (SSH)](/windows/iot-core/connect-your-device/ssh). Para crear una imagen de OEM, el mecanismo preferido para establecer los valores del `OEMInput.xml` registro es el archivo que se describe aquí:

[Personalizaciones en tiempo de ejecución](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)

> [!NOTE]
> La mayoría de los valores de configuración del registro que se documentan aquí entrarán en vigor mientras esté visible el teclado en pantalla.
> Esto le permite desarrollar fácilmente diferentes combinatations de valores de configuración y ver inmediatamente los cambios resultantes en tiempo real. Si una configuración no surte efecto inmediatamente, deberá reiniciar el dispositivo para ver los cambios en la interfaz de usuario del teclado.

### <a name="keyboard-height"></a>Altura del teclado

De forma predeterminada, el teclado táctil usará el 45% inferior del alto de la pantalla. Esto puede parecer demasiado grande o pequeño en el dispositivo, en función de su tamaño y resolución. Puede ajustar el alto hasta un máximo de dos tercios en el alto de la pantalla. Cualquier valor que no esté dentro del intervalo se fijará en el intervalo. Dado que se especifica como un valor de punto flotante, permite la precisión de nivel de píxel. Simplemente aplique la siguiente fórmula para calcular el porcentaje:

`percentage = (100 * <desired_pixel_height>) / <screen_height>`

Por ejemplo, para cambiar el alto a 56,783%, debe establecer el siguiente valor del registro:
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
> El tipo de valor del registro debe ser una`REG_SZ`cadena (), de modo que los valores fraccionarios puedan representarse con.
> separador decimal. El uso de`REG_DWORD`DWORD () _no_ funcionará, ni siquiera para porcentajes enteros.

### <a name="additional-preferences"></a>Preferencias adicionales

El conjunto de preferencias restante es un valor de cadena en la subclave de preferencias:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\OSK\Preferences
```

| Valor del registro               | Valor predeterminado      | Descripción                                                                                         |
| ---------------------------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| AudioFeedback_Disabled       | 0,1                | "0" habilita la clave de clic en los comentarios de audio; "1" lo deshabilita.                                          |
| Dictation_Disabled           | "1"                | "0" muestra el botón dictado (reconocimiento de voz); "1" lo oculta.<br/> (consulte la nota siguiente)             |
| KeyboardModeEnabled_full     | 0,1                | "0" deshabilita el modo de teclado completo; "1" lo habilita.                                                |
| KeyboardModeEnabled_narrow   | "1"                | "0" deshabilita el modo de teclado estrecho; "1" lo habilita.                                              |
| KeyboardModeEnabled_wide     | "1"                | "0" deshabilita el modo de teclado ancho; "1" lo habilita.                                                |
| ModeOrder                    | "Wide; Narrow; completo" | El orden (de izquierda a derecha) en el que se enumeran los modos en el menú desplegable modo, si está habilitado |
| SettingsMenuKey_Collapsed    | 0,1                | Oculta el menú desplegable modo. Establézcalo en "1" si solo está habilitado un modo.                         |
| Paste_Disabled               | 0,1                | "0" muestra el botón pegar; "1" lo oculta.<br/> El cambio surte efecto después del reinicio.                    |
| CloseButton_Disabled         | 0,1                | "0" muestra el botón cerrar; "1" oculta el botón cerrar<br/> El cambio surte efecto después del reinicio.       |
| EmojiKeyEnabled              | 0,1                | "0" oculta la clave de Emoji; "1" lo muestra, lo que permite al usuario escribir caracteres de Emoji.                 |

> [!NOTE]
> El modo de dictado requiere la instalación de un paquete de voz para el idioma de entrada seleccionado, así como un dispositivo de entrada de audio. Si no hay instalado ningún paquete de voz coincidente, no se mostrará el botón dictado.
> 
> Todas las imágenes incluyen el lenguaje de voz en-US. Otros paquetes de voz se instalan como características opcionales.
> Para más información sobre las características de IoT, consulte la [lista de características principales](/windows-hardware/manufacture/iot/iot-core-feature-list) de IOT y la [Guía de fabricación de IOT Core](/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

Por ejemplo, para habilitar solo `wide` el modo de teclado, en PowerShell, puede hacer lo siguiente:
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
