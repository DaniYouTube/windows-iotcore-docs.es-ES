---
title: Compatibilidad con idiomas principales de IoT de Windows 10
author: msalehmsft
ms.author: msaleh
ms.date: 09/12/2017
ms.topic: article
description: Obtenga información sobre la compatibilidad con varios idiomas en aplicaciones y sistemas operativos UWP en IoT Core.
keywords: Windows IOT, idiomas, tipos de aplicaciones, UWP, so
ms.openlocfilehash: 5bc44fb090e6e198525e95d6aee6815afd0095da
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918227"
---
# <a name="language-support"></a><span data-ttu-id="a13cc-104">Compatibilidad con idiomas</span><span class="sxs-lookup"><span data-stu-id="a13cc-104">Language Support</span></span>

<span data-ttu-id="a13cc-105">La compatibilidad con idiomas se puede habilitar en dos niveles, nivel de aplicación y nivel de sistema operativo, en función de los recursos de idioma disponibles en la imagen.</span><span class="sxs-lookup"><span data-stu-id="a13cc-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="a13cc-106">Lenguajes en aplicaciones para UWP</span><span class="sxs-lookup"><span data-stu-id="a13cc-106">Languages in UWP Applications</span></span>
<span data-ttu-id="a13cc-107">Los lenguajes de aplicación de UWP no se limitan a los idiomas incluidos en el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="a13cc-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="a13cc-108">De hecho, un dispositivo de IoT que no desencadena la interfaz de usuario de Shell ni emplea recursos de voz puede proporcionar una experiencia de dispositivo en muchos lenguajes diferentes a través de sus aplicaciones UWP, aunque el sistema operativo Windows 10 IoT Core subyacente se crea simplemente en el modo predeterminado en-US.</span><span class="sxs-lookup"><span data-stu-id="a13cc-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="a13cc-109">Las aplicaciones de UWP deben proporcionar los recursos para los idiomas que se necesitan para admitir.</span><span class="sxs-lookup"><span data-stu-id="a13cc-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="a13cc-110">Las API de [Windows. Globalization. ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) se pueden usar para especificar las preferencias relacionadas con el idioma.</span><span class="sxs-lookup"><span data-stu-id="a13cc-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="a13cc-111">Vea las aplicaciones de ejemplo siguientes:</span><span class="sxs-lookup"><span data-stu-id="a13cc-111">See the below sample applications:</span></span>

* [<span data-ttu-id="a13cc-112">Ejemplo de IoTDefaultApp</span><span class="sxs-lookup"><span data-stu-id="a13cc-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="a13cc-113">Ejemplo de ApplicationResources</span><span class="sxs-lookup"><span data-stu-id="a13cc-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="a13cc-114">Idiomas en el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="a13cc-114">Languages in OS</span></span>

<span data-ttu-id="a13cc-115">Los kits de IoTCore de Windows 10 ahora incluyen los recursos de idioma para los siguientes idiomas:</span><span class="sxs-lookup"><span data-stu-id="a13cc-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="a13cc-116">Idioma</span><span class="sxs-lookup"><span data-stu-id="a13cc-116">Language</span></span>  | <span data-ttu-id="a13cc-117">Código</span><span class="sxs-lookup"><span data-stu-id="a13cc-117">Code</span></span> | <span data-ttu-id="a13cc-118">Región</span><span class="sxs-lookup"><span data-stu-id="a13cc-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="a13cc-119">Inglés (Estados Unidos)</span><span class="sxs-lookup"><span data-stu-id="a13cc-119">English (United States)</span></span> | <span data-ttu-id="a13cc-120">en-US</span><span class="sxs-lookup"><span data-stu-id="a13cc-120">en-US</span></span> | <span data-ttu-id="a13cc-121">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="a13cc-121">North America</span></span> | 
> | <span data-ttu-id="a13cc-122">Inglés (Reino Unido)</span><span class="sxs-lookup"><span data-stu-id="a13cc-122">English (UK)</span></span> | <span data-ttu-id="a13cc-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="a13cc-123">en-GB</span></span> | <span data-ttu-id="a13cc-124">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-124">Europe</span></span> |
> | <span data-ttu-id="a13cc-125">Francés (Francia)</span><span class="sxs-lookup"><span data-stu-id="a13cc-125">French (France)</span></span> | <span data-ttu-id="a13cc-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="a13cc-126">fr-FR</span></span> | <span data-ttu-id="a13cc-127">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-127">Europe</span></span> |
> | <span data-ttu-id="a13cc-128">Francés (Canadá)</span><span class="sxs-lookup"><span data-stu-id="a13cc-128">French (Canada)</span></span> | <span data-ttu-id="a13cc-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="a13cc-129">fr-CA</span></span> | <span data-ttu-id="a13cc-130">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="a13cc-130">North America</span></span> |
> | <span data-ttu-id="a13cc-131">Español (España)</span><span class="sxs-lookup"><span data-stu-id="a13cc-131">Spanish (Spain)</span></span> | <span data-ttu-id="a13cc-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="a13cc-132">es-ES</span></span> | <span data-ttu-id="a13cc-133">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-133">Europe</span></span> |
> | <span data-ttu-id="a13cc-134">Español (México)</span><span class="sxs-lookup"><span data-stu-id="a13cc-134">Spanish (Mexico)</span></span> | <span data-ttu-id="a13cc-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="a13cc-135">es-MX</span></span> | <span data-ttu-id="a13cc-136">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="a13cc-136">North America</span></span> |
> | <span data-ttu-id="a13cc-137">Chino</span><span class="sxs-lookup"><span data-stu-id="a13cc-137">Chinese</span></span> | <span data-ttu-id="a13cc-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="a13cc-138">zh-CN</span></span> | <span data-ttu-id="a13cc-139">Asia</span><span class="sxs-lookup"><span data-stu-id="a13cc-139">Asia</span></span> | 
> | <span data-ttu-id="a13cc-140">Árabe</span><span class="sxs-lookup"><span data-stu-id="a13cc-140">Arabic</span></span> | <span data-ttu-id="a13cc-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="a13cc-141">ar-SA</span></span> | <span data-ttu-id="a13cc-142">Asia</span><span class="sxs-lookup"><span data-stu-id="a13cc-142">Asia</span></span> |
> | <span data-ttu-id="a13cc-143">Alemán</span><span class="sxs-lookup"><span data-stu-id="a13cc-143">German</span></span> | <span data-ttu-id="a13cc-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="a13cc-144">de-DE</span></span> | <span data-ttu-id="a13cc-145">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-145">Europe</span></span> |
> | <span data-ttu-id="a13cc-146">Italiano</span><span class="sxs-lookup"><span data-stu-id="a13cc-146">Italian</span></span> | <span data-ttu-id="a13cc-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="a13cc-147">it-IT</span></span> | <span data-ttu-id="a13cc-148">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-148">Europe</span></span> | 
> | <span data-ttu-id="a13cc-149">japonés</span><span class="sxs-lookup"><span data-stu-id="a13cc-149">Japanese</span></span> | <span data-ttu-id="a13cc-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="a13cc-150">ja-JP</span></span> | <span data-ttu-id="a13cc-151">Asia</span><span class="sxs-lookup"><span data-stu-id="a13cc-151">Asia</span></span> |
> | <span data-ttu-id="a13cc-152">Coreano</span><span class="sxs-lookup"><span data-stu-id="a13cc-152">Korean</span></span> | <span data-ttu-id="a13cc-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="a13cc-153">ko-KR</span></span> | <span data-ttu-id="a13cc-154">Asia</span><span class="sxs-lookup"><span data-stu-id="a13cc-154">Asia</span></span> |
> | <span data-ttu-id="a13cc-155">Neerlandés</span><span class="sxs-lookup"><span data-stu-id="a13cc-155">Dutch</span></span> | <span data-ttu-id="a13cc-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="a13cc-156">nl-NL</span></span> | <span data-ttu-id="a13cc-157">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-157">Europe</span></span> |
> | <span data-ttu-id="a13cc-158">Polaco</span><span class="sxs-lookup"><span data-stu-id="a13cc-158">Polish</span></span> | <span data-ttu-id="a13cc-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="a13cc-159">pl-PL</span></span> | <span data-ttu-id="a13cc-160">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-160">Europe</span></span> | 
> | <span data-ttu-id="a13cc-161">Rumano</span><span class="sxs-lookup"><span data-stu-id="a13cc-161">Romanian</span></span> | <span data-ttu-id="a13cc-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="a13cc-162">ro-RO</span></span> | <span data-ttu-id="a13cc-163">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-163">Europe</span></span> |
> | <span data-ttu-id="a13cc-164">Ruso</span><span class="sxs-lookup"><span data-stu-id="a13cc-164">Russian</span></span> | <span data-ttu-id="a13cc-165">ru-RU</span><span class="sxs-lookup"><span data-stu-id="a13cc-165">ru-RU</span></span> | <span data-ttu-id="a13cc-166">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-166">Europe</span></span> |
> | <span data-ttu-id="a13cc-167">Griego</span><span class="sxs-lookup"><span data-stu-id="a13cc-167">Greek</span></span> | <span data-ttu-id="a13cc-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="a13cc-168">el-GR</span></span> | <span data-ttu-id="a13cc-169">Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-169">Europe</span></span> |
> | <span data-ttu-id="a13cc-170">Portugués (Brasil)</span><span class="sxs-lookup"><span data-stu-id="a13cc-170">Portugese (Brazil)</span></span> | <span data-ttu-id="a13cc-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="a13cc-171">pt-BR</span></span> | <span data-ttu-id="a13cc-172">Sudamérica/Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-172">South America/Europe</span></span> |
> | <span data-ttu-id="a13cc-173">Portuese (Portugal)</span><span class="sxs-lookup"><span data-stu-id="a13cc-173">Portuese (Portugal)</span></span> | <span data-ttu-id="a13cc-174">pt-PT</span><span class="sxs-lookup"><span data-stu-id="a13cc-174">pt-PT</span></span> | <span data-ttu-id="a13cc-175">Sudamérica/Europa</span><span class="sxs-lookup"><span data-stu-id="a13cc-175">South America/Europe</span></span> |

<span data-ttu-id="a13cc-176">Estos recursos de idioma contienen cadenas de interfaz de usuario, lenguaje de voz y voces (síntesis de voz).</span><span class="sxs-lookup"><span data-stu-id="a13cc-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="a13cc-177">Las imágenes de Windows IoT pueden compilarse con uno o varios de estos recursos, y deben especificarse durante el tiempo de la imagen y no se pueden modificar posteriormente.</span><span class="sxs-lookup"><span data-stu-id="a13cc-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="a13cc-178">Tenga en cuenta que los recursos relacionados con el idioma de la interfaz de usuario son independientes de los de voz.</span><span class="sxs-lookup"><span data-stu-id="a13cc-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="a13cc-179">Especificar recursos de interfaz de usuario y voz</span><span class="sxs-lookup"><span data-stu-id="a13cc-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="a13cc-180">En el archivo XML de entrada OEM, los idiomas de interfaz de usuario y voz necesarios se especifican como se muestra a continuación</span><span class="sxs-lookup"><span data-stu-id="a13cc-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

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


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="a13cc-181">Especificar los recursos de datos de voz</span><span class="sxs-lookup"><span data-stu-id="a13cc-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="a13cc-182">En el archivo XML de entrada OEM, los recursos de datos de voz necesarios se especifican como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="a13cc-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

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
> <span data-ttu-id="a13cc-183">De forma predeterminada, los datos de voz en-US están incluidos en la imagen.</span><span class="sxs-lookup"><span data-stu-id="a13cc-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="a13cc-184">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="a13cc-184">Samples</span></span>
* <span data-ttu-id="a13cc-185">Consulte [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) para compatibilidad con varios idiomas</span><span class="sxs-lookup"><span data-stu-id="a13cc-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="a13cc-186">Consulte [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) para el idioma FR-fr con en-US como lenguaje de reserva.</span><span class="sxs-lookup"><span data-stu-id="a13cc-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="a13cc-187">Tenga en cuenta que cuando se cambia el idioma de la interfaz de usuario de arranque, el nombre de la cuenta de `administrator` también se traduce en el idioma de la interfaz de usuario de arranque.</span><span class="sxs-lookup"><span data-stu-id="a13cc-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="a13cc-188">Por lo tanto, en fr-FR es `administrateur`.</span><span class="sxs-lookup"><span data-stu-id="a13cc-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="a13cc-189">Vea [OEMCustomization. cmd.](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="a13cc-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="a13cc-190">Cambiar las preferencias del usuario (idioma, región, voz y voz)</span><span class="sxs-lookup"><span data-stu-id="a13cc-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="a13cc-191">La aplicación UWP puede usar las API de WinRT para establecer la región, la lista de idiomas preferidos de la interfaz de usuario, el idioma de voz y la voz que deben usarse de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a13cc-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="a13cc-192">Una vez que se establece la lista de idiomas de interfaz de usuario preferida, la aplicación UWP intentará cargar los recursos correspondientes (a menos que la aplicación lo impida mediante programación).</span><span class="sxs-lookup"><span data-stu-id="a13cc-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="a13cc-193">Si la aplicación no tiene los recursos correspondientes, se cargarán los recursos de reserva.</span><span class="sxs-lookup"><span data-stu-id="a13cc-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="a13cc-194">Del mismo modo, si los recursos del sistema operativo para los idiomas preferidos no forman parte de la imagen de Windows IoT, Windows IoT usará su reserva probablemente en inglés (en-US).</span><span class="sxs-lookup"><span data-stu-id="a13cc-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="a13cc-195">Establecimiento de la región mediante `TrySetHomeGeographicRegion` en [Windows. System. userprofile. GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a13cc-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a13cc-196">Establezca el idioma de la interfaz de usuario mediante `TrySetLanguages` en [Windows. System. userprofile. GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="a13cc-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="a13cc-197">Establecimiento del lenguaje de voz mediante `TrySetSystemSpeechLanguageAsync` en [Windows. Media. SpeechRecognition. SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="a13cc-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="a13cc-198">Establecer Voice mediante `TrySetDefaultVoiceAsync` en [Windows. Media. SpeechSynthesis. SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="a13cc-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="a13cc-199">Para un funcionamiento correcto, Cortana requiere que la región, el idioma de la interfaz de usuario y el idioma de la voz sean coherentes, por ejemplo: región FR, interfaz de usuario y lenguajes de voz fr-FR o región ES, interfaz de usuario y lenguajes de voz es-ES.</span><span class="sxs-lookup"><span data-stu-id="a13cc-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="a13cc-200">Cortana usa su propia voz; la aplicación UWP no puede cambiarla.</span><span class="sxs-lookup"><span data-stu-id="a13cc-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="a13cc-201">IoTSettings. exe</span><span class="sxs-lookup"><span data-stu-id="a13cc-201">IoTSettings.exe</span></span>

<span data-ttu-id="a13cc-202">Para obtener más información sobre cómo cambiar la configuración de la región y el idioma del usuario o de la voz para crear productos habilitados para Cortana, lea la documentación de los [utils](../manage-your-device/CommandLineUtils.md) de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="a13cc-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
