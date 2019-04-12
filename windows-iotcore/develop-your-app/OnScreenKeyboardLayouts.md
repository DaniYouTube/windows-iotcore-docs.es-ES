---
title: En la pantalla especificar disponibles lenguaje distribuciones del teclado
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: Obtenga información sobre cómo especificar que el idioma de teclado en pantalla diseños están disponibles para los usuarios de su dispositivo Windows IoT.
keywords: Windows 10 IoT Core, comercializar, diseños de idioma de teclado en pantalla de osk
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514615"
---
# <a name="on-screen-keyboard-language-layouts"></a>Diseños de idioma de teclado en pantalla

> [!IMPORTANT]
> A partir de Windows 10 IoT Core, versión 1809, ya no es aplicable en este artículo. Consulte la [teclado en pantalla para dispositivos con cabezal](./OnScreenKeyboard.md) página para obtener la documentación actual.

El que aparecen en pantalla teclado (OSK) en Windows 10 IoT Core, versiones 1803, 1703 y 1709 admite diseños para los siguientes idiomas:

| Etiqueta de idioma  | Descripción             | Código del diseño |
| :------------ | :---------------------- | -----------:|
| en-US         | Inglés (Estados Unidos) |    00000409 |
| en-AU         | Inglés (Australia)     |    00000C09 |
| en-CA         | Inglés (Canadá)        |    00001009 |
| en-GB         | Inglés (Gran Bretaña) |    00000809 |
| es-ES         | Español (España)         |    0000040A |
| es-MX         | Español (México)        |    0000080A |
| de-DE         | Alemán                  |    00000407 |
| fr-CA         | Francés (Canadá)         |    00000C0C |
| fr-FR         | Francés (Francia)         |    0000040C |
| it-IT         | Italiano                 |    00000410 |
| pt-BR         | Portugués (Brasil)     |    00000416 |

Presionando y manteniendo presionado el OSK botón "& 123", el usuario puede seleccionar qué diseño desean usar:

![Todos los idiomas](../media/OnScreenKeyboard/AllLanguages.png)
 
Sin embargo, como OEM, puede limitar qué opciones de diseño se muestran al usuario. Para limitar qué diseños para mostrar al usuario, hacer referencia a la orientación de la [doucmentation de distribución del teclado en TechNet](https://technet.microsoft.com/library/cc978687.aspx).
 
Para obtener un ejemplo concreto, si desea permitir que solo los diseños de lenguaje de América del Norte (en-US, en-CA, es-MX, fr-CA), podría agregar lo siguiente al script OEMCustomization.cmd:

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

Donde setKeyboardLanguages.cmd es una secuencia de comandos en el mismo directorio que contiene este:
 
```console
@echo off

set getDefaultAccountSID="wmic.exe useraccount where name='DefaultAccount' get sid"

for /F "tokens=2 usebackq delims== " %%s in (`%getDefaultAccountSID%`) do (
    set registryKey="HKEY_USERS\%%~s\Keyboard Layout\Preload"
    goto :setRegistry
  )
)
echo Unable to determine SID for DefaultAccount
goto :eof

:setRegistry
  echo on
  REG ADD %registryKey% /v "1" /d "00000409" /f
  REG ADD %registryKey% /v "2" /d "00001009" /f
  REG ADD %registryKey% /v "3" /d "0000080A" /f
  REG ADD %registryKey% /v "4" /d "00000C0C" /f
  @echo off
goto :eof
```

Será el efecto resultante de la secuencia de comandos anterior:

![Idiomas de América del Norte](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>Algunos aspectos a tener en cuenta:
*  Los nombres de los valores indican una secuencia decimal.
*  Los valores son valores de cadena (REG_SZ).
*  Por supuesto, el texto del script anterior, se puede agregar directamente en la secuencia de comandos OEMCustomization.cmd.
*  **No** eliminar la clave del registro de "Precarga", ya que tiene los permisos establecidos en ella específicamente para permitir que el teclado en pantalla de la aplicación para leer sus valores.
*  Un requisito previo para estas instrucciones para que sea aplicable, es que la imagen debe incluir las siguientes características *:
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

Para obtener más información acerca de las características de IoT, consulte [lista de características de IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list).
