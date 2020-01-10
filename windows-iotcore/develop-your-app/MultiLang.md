---
title: Compatibilidad con idiomas principales de IoT de Windows 10
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/2017
ms.topic: article
description: Obtenga información sobre la compatibilidad con varios idiomas en aplicaciones y sistemas operativos UWP en IoT Core.
keywords: Windows IOT, idiomas, tipos de aplicaciones, UWP, so
ms.openlocfilehash: ea54ee9dac93866065313e00caccb91ac1dc7c7f
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721688"
---
# <a name="language-support"></a>Compatibilidad con idiomas

La compatibilidad con idiomas se puede habilitar en dos niveles, nivel de aplicación y nivel de sistema operativo, en función de los recursos de idioma disponibles en la imagen.

## <a name="languages-in-uwp-applications"></a>Lenguajes en aplicaciones para UWP
Los lenguajes de aplicación de UWP no se limitan a los idiomas incluidos en el sistema operativo.  De hecho, un dispositivo de IoT que no desencadena la interfaz de usuario de Shell ni emplea recursos de voz puede proporcionar una experiencia de dispositivo en muchos lenguajes diferentes a través de sus aplicaciones UWP, aunque el sistema operativo Windows 10 IoT Core subyacente se crea simplemente en el modo predeterminado en-US. 

Las aplicaciones de UWP deben proporcionar los recursos para los idiomas que se necesitan para admitir. Las API de [Windows. Globalization. ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) se pueden usar para especificar las preferencias relacionadas con el idioma.

Vea las aplicaciones de ejemplo siguientes:

* [Ejemplo de IoTDefaultApp](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [Ejemplo de ApplicationResources](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a>Idiomas en el sistema operativo

Los kits de IoTCore de Windows 10 ahora incluyen los recursos de idioma para los siguientes idiomas:

> | Idioma  | Código | Región |
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
> | japonés | ja-JP | Asia |
> | Coreano | ko-KR | Asia |
> | Neerlandés | nl-NL | Europa |
> | Polaco | pl-PL | Europa | 
> | Rumano | ro-RO | Europa |
> | Ruso | ru-RU | Europa |
> | Griego | el-GR | Europa |
> | Portugués (Brasil) | pt-BR | Sudamérica/Europa |
> | Portuese (Portugal) | pt-PT | Sudamérica/Europa |

Estos recursos de idioma contienen cadenas de interfaz de usuario, lenguaje de voz y voces (síntesis de voz). Las imágenes de Windows IoT pueden compilarse con uno o varios de estos recursos, y deben especificarse durante el tiempo de la imagen y no se pueden modificar posteriormente. Tenga en cuenta que los recursos relacionados con el idioma de la interfaz de usuario son independientes de los de voz.

### <a name="specifying-ui-and-speech-resources"></a>Especificar recursos de interfaz de usuario y voz 
En el archivo XML de entrada OEM, los idiomas de interfaz de usuario y voz necesarios se especifican como se muestra a continuación

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


### <a name="specifying-speech-data-resources"></a>Especificar los recursos de datos de voz
En el archivo XML de entrada OEM, los recursos de datos de voz necesarios se especifican como se muestra a continuación.

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
> De forma predeterminada, los datos de voz en-US están incluidos en la imagen.

### <a name="samples"></a>Muestras
* Consulte [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) para compatibilidad con varios idiomas
* Consulte [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) para el idioma FR-fr con en-US como lenguaje de reserva.
    * Tenga en cuenta que cuando se cambia el idioma de la interfaz de usuario de arranque, el nombre de la cuenta de `administrator` también se traduce en el idioma de la interfaz de usuario de arranque. Por lo tanto, en fr-FR es `administrateur`. Vea [OEMCustomization. cmd.](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)

## <a name="changing-user-preferences-language-region-speech-and-voice"></a>Cambiar las preferencias del usuario (idioma, región, voz y voz)

La aplicación UWP puede usar las API de WinRT para establecer la región, la lista de idiomas preferidos de la interfaz de usuario, el idioma de voz y la voz que deben usarse de forma predeterminada. Una vez que se establece la lista de idiomas de interfaz de usuario preferida, la aplicación UWP intentará cargar los recursos correspondientes (a menos que la aplicación lo impida mediante programación).
 
Si la aplicación no tiene los recursos correspondientes, se cargarán los recursos de reserva. Del mismo modo, si los recursos del sistema operativo para los idiomas preferidos no forman parte de la imagen de Windows IoT, Windows IoT usará su reserva probablemente en inglés (en-US).

* Establecimiento de la región mediante `TrySetHomeGeographicRegion` en [Windows. System. userprofile. GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* Establezca el idioma de la interfaz de usuario mediante `TrySetLanguages` en [Windows. System. userprofile. GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)
* Establecimiento del lenguaje de voz mediante `TrySetSystemSpeechLanguageAsync` en [Windows. Media. SpeechRecognition. SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)
* Establecer Voice mediante `TrySetDefaultVoiceAsync` en [Windows. Media. SpeechSynthesis. SpeechSynthesizer](https://docs.microsoft.com/uwp/api/windows.media.speechsynthesis.speechsynthesizer)

> [!NOTE]
> Para un funcionamiento correcto, Cortana requiere que la región, el idioma de la interfaz de usuario y el idioma de la voz sean coherentes, por ejemplo: región FR, interfaz de usuario y lenguajes de voz fr-FR o región ES, interfaz de usuario y lenguajes de voz es-ES. Cortana usa su propia voz; la aplicación UWP no puede cambiarla.

## <a name="iotsettingsexe"></a>IoTSettings. exe

Para obtener más información sobre cómo cambiar la configuración de la región y el idioma del usuario o de la voz para crear productos habilitados para Cortana, lea la documentación de los [utils](../manage-your-device/CommandLineUtils.md) de la línea de comandos.
