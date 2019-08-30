---
title: Especificar los diseños de idioma de teclado en pantalla disponibles
author: johntasler
ms.author: jtasler
ms.date: 09/12/2018
ms.topic: article
description: Obtenga información acerca de cómo especificar los diseños de idioma del teclado en pantalla que están disponibles para los usuarios de su dispositivo de Windows IoT.
keywords: Windows 10 IoT Core, Commercial, Osk de idioma de teclado en pantalla
ms.openlocfilehash: 003f280236733763b33f096f6574aad04921841f
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169622"
---
# <a name="on-screen-keyboard-language-layouts"></a>Diseños de idioma del teclado en pantalla

> [!IMPORTANT]
> A partir de Windows 10 IoT Core, versión 1809, este artículo ya no es aplicable. Consulte la página [teclado en pantalla para dispositivos](./OnScreenKeyboard.md) de la documentación actual.

El teclado en pantalla (OSK) de Windows 10 IoT Core, versiones 1703, 1709 y 1803, admite diseños para los siguientes idiomas:

| Etiqueta de idioma  | Descripción             | Código de diseño |
| :------------ | :---------------------- | -----------:|
| en-US         | Inglés (Estados Unidos) |    00000409 |
| en-AU         | Inglés (Australia)     |    00000C09 |
| en-CA         | Inglés (Canadá)        |    00001009 |
| en-GB         | Inglés (Reino Unido) |    00000809 |
| es-ES         | Español (España)         |    0000040A |
| es-MX         | Español (México)        |    0000080A |
| de-DE         | Alemán                  |    00000407 |
| fr-CA         | Francés (Canadá)         |    00000C0C |
| fr-FR         | Francés (Francia)         |    0000040C |
| it-IT         | Italiano                 |    00000410 |
| pt-BR         | Portugués (Brasil)     |    00000416 |

Al presionar y mantener presionado el botón "& 123", el usuario puede seleccionar el diseño que quiera usar:

![Todos los idiomas](../media/OnScreenKeyboard/AllLanguages.png)
 
No obstante, como OEM, puede limitar las opciones de diseño que se muestran al usuario. Para limitar qué diseños se van a mostrar al usuario, primero debe hacer referencia a las instrucciones de la [distribución del teclado doucmentation en TechNet](https://technet.microsoft.com/library/cc978687.aspx).
 
Para un ejemplo concreto, si desea permitir solo los diseños de idioma Norteamérica (en-US, en-CA, es-MX, FR-CA), puede agregar lo siguiente al script OEMCustomization. cmd:

```console
call "%~dp0\setKeyboardLanguages.cmd"
```

Donde setKeyboardLanguages. cmd es un script en el mismo directorio que lo contiene:
 
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

El efecto resultante del script de comandos anterior será:

![Idiomas de Norteamérica](../media/OnScreenKeyboard/NorthAmericanLanguages.png)

### <a name="some-things-to-note"></a>Algunos aspectos que hay que tener en cuenta:
*  Los nombres de valor indican una secuencia decimal.
*  Los valores son valores de cadena (REG_SZ).
*  El texto del script anterior, por supuesto, se podría agregar directamente en el script OEMCustomization. cmd.
*  **No** elimine la clave del registro "preload", ya que tiene permisos establecidos específicamente para permitir que la aplicación de teclado en pantalla lea sus valores.
*  Un requisito previo para que se apliquen estas instrucciones es que la imagen debe incluir las siguientes características *:
   * IOT_SHELL_ONSCREEN_KEYBOARD
   * IOT_SHELL_ONSCREEN_KEYBOARD_FOLLOWFOCUS

Para obtener más información sobre las características de IoT, consulte [lista de características de IOT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-feature-list).
