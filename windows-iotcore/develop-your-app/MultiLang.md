---
title: Compatibilidad con idiomas de Windows 10 IoT Core
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/17
ms.topic: article
description: Obtenga información sobre la compatibilidad con varios idiomas en las aplicaciones de UWP y el sistema operativo en IoT Core.
keywords: Windows iot, idiomas, los tipos de aplicaciones, UWP, sistema operativo
ms.openlocfilehash: 211ed2ee8350d8c92d6f959f8d9e7b5d6f567af7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514295"
---
# <a name="language-support"></a>Compatibilidad con idiomas

Compatibilidad de idioma puede habilitarse en dos niveles, el nivel de aplicación y el nivel de sistema operativo, dependiendo de los recursos de idioma están disponibles en la imagen.

## <a name="languages-in-uwp-applications"></a>Lenguajes en aplicaciones UWP
Idiomas de la aplicación de UWP no se limitan a los idiomas incluidos en el sistema operativo.  De hecho, un dispositivo de IoT que desencadenan el shell de interfaz de usuario o utilizar los recursos de voz no puede proporcionar una experiencia de dispositivo en varios idiomas a través de sus aplicaciones para UWP, aunque el SO subyacente de Windows 10 IoT Core se basa simplemente en el modo predeterminado en-US. 

Las aplicaciones de UWP deben proporcionar los recursos para los idiomas que deben ser compatibles. [Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) API pueden usarse para especificar las preferencias de idioma.

Vea las aplicaciones de ejemplo siguientes:

* [Ejemplo de IoTDefaultApp](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [Ejemplo de ApplicationResources](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>Idiomas en el sistema operativo

Kits de Windows 10 IoTCore ahora incluyen los recursos de idioma para los idiomas siguientes:

> | Lenguaje  | Código | Region |
> |-------------|-----|-----|
> | Inglés (Estados Unidos) | en-US | Norteamérica | 
> | Inglés (Reino Unido) | en-GB | Europa |
> | Francés (Francia) | fr-FR | Europa |
> | Francés (Canadá) | fr-CA | Norteamérica |
> | Español (España) | es-ES | Europa |
> | Español (México) | es-MX | Norteamérica |
> | Chino | zh-CN | Asia | 
> | Árabe | ar-SA | Asia |
> | Alemán | de-DE | Europa |
> | Italiano | it-IT | Europa | 
> | Japonés | ja-JP | Asia |
> | Coreano | ko-KR | Asia |
> | Neerlandés | nl-NL | Europa |
> | Polaco | pl-PL | Europa | 
> | Rumano | ro-RO | Europa |
> | Ruso | ro-RU | Europa |
> | Griego | el-GR | Europa |
> | Portugués (Brasil) | pt-BR | Sudamérica y Europa |
> | Portuese (Portugal) | pt-PR | Sudamérica y Europa |

Estos recursos de idioma contienen cadenas de interfaz de usuario, idiomas de voz y voces (síntesis de voz). Se pueden crear imágenes de Windows IoT con uno o varios de estos recursos y se debe especificar durante el tiempo de imagen y no se puede modificar más adelante. Tenga en cuenta que el idioma de interfaz de usuario relacionados con los recursos son independientes de lenguaje de voz y los recursos de voz.

### <a name="specifying-ui-and-speech-resources"></a>Especificar recursos de la interfaz de usuario y de voz 
En el archivo xml de entrada de OEM, la interfaz de usuario necesaria e idiomas de voz se especifican como se muestra a continuación

``` xml
  <SupportedLanguages>
    <UserInterface>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </UserInterface>
    <Keyboard>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Keyboard>
    <Speech>
      <Language>en-US</Language>
      <Language>en-GB</Language> 
      <Language>fr-CA</Language> 
      <Language>es-MX</Language> 
      <Language>es-ES</Language> 
      <Language>fr-FR</Language>
    </Speech>
  </SupportedLanguages>
  <BootUILanguage>en-us</BootUILanguage>
  <BootLocale>en-us</BootLocale>
```


### <a name="specifying-speech-data-resources"></a>Especificar recursos de datos de voz
En el archivo xml de entrada de OEM, se especifican los recursos de datos de voz necesarios tal como se muestra a continuación,

``` xml
    <Microsoft>
       ...
      <Feature>IOT_SPEECHDATA_EN_CA</Feature>
      <Feature>IOT_SPEECHDATA_ES_MX</Feature> 
      <Feature>IOT_SPEECHDATA_FR_CA</Feature> 
      <Feature>IOT_SPEECHDATA_EN_GB</Feature>
      <Feature>IOT_SPEECHDATA_ES_ES</Feature>  
      <Feature>IOT_SPEECHDATA_FR_FR</Feature> 
    </Microsoft>
```

> [!NOTE]
> De forma predeterminada, los datos de voz en-US se incluyen en la imagen.

### <a name="samples"></a>Muestras
* Consulte [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) para admiten varios idiomas
* Consulte [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) idioma fr-FR con en-US como idioma de reserva.
    * Tenga en cuenta que cuando se cambia el idioma de interfaz de usuario de inicio, la `administrator` también se traduce el nombre de la cuenta en el idioma de interfaz de usuario de arranque. Por lo tanto, en fr-FR es `administrateur`. Consulte [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>Cambiar las preferencias del usuario (idioma, región, voz y voz)

Aplicación de UWP puede usar WinRT APIs para establecer la región, lista de idiomas de interfaz de usuario preferido, lenguaje de voz y voz que se debe usar de forma predeterminada. Conjunto de lista de idioma de interfaz de usuario una vez preferido, aplicación de UWP intentará cargar los recursos correspondientes (a menos que la aplicación mediante programación impide dicho).
 
Si la aplicación no tiene los recursos correspondientes, se cargarán los recursos de reserva. De forma similar, si los recursos del sistema operativo para el idioma preferido no forman parte de la imagen de Windows IoT, IoT Windows usará los reserva probable inglés (en-US).

* Establece la región mediante `TrySetHomeGeographicRegion` en [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* Idioma de interfaz de usuario de conjunto con `TrySetLanguages` en [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* Conjunto de voz idioma mediante `TrySetSystemSpeechLanguageAsync` en [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* Establecer mediante voz `TrySetDefaultVoiceAsync` en [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> Para que funcione correctamente, Cortana requiere la región, el idioma de interfaz de usuario y lenguaje de voz para que sea coherente, p. ej.: región FR, la interfaz de usuario y la voz idiomas fr-FR o región ES, la interfaz de usuario y la voz idiomas es-es al directorio. Cortana usa su propia voz, aplicación de UWP no puede cambiar.

## <a name="iotsettingsexe"></a>IoTSettings.exe

Para más información acerca de cómo cambiar la configuración de región y el usuario o el lenguaje de voz crear productos de Cortana habilitado, lea nuestra [utilidades de línea de comandos](../manage-your-device/CommandLineUtils.md) documentación.
