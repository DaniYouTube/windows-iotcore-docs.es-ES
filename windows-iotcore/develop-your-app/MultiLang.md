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
# <a name="language-support"></a><span data-ttu-id="2e099-104">Compatibilidad con idiomas</span><span class="sxs-lookup"><span data-stu-id="2e099-104">Language Support</span></span>

<span data-ttu-id="2e099-105">Compatibilidad de idioma puede habilitarse en dos niveles, el nivel de aplicación y el nivel de sistema operativo, dependiendo de los recursos de idioma están disponibles en la imagen.</span><span class="sxs-lookup"><span data-stu-id="2e099-105">Language support can be enabled at two levels, Application level and OS level, depending on the language resources made available on the image.</span></span>

## <a name="languages-in-uwp-applications"></a><span data-ttu-id="2e099-106">Lenguajes en aplicaciones UWP</span><span class="sxs-lookup"><span data-stu-id="2e099-106">Languages in UWP Applications</span></span>
<span data-ttu-id="2e099-107">Idiomas de la aplicación de UWP no se limitan a los idiomas incluidos en el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="2e099-107">UWP application languages are not limited to the languages included in the OS.</span></span>  <span data-ttu-id="2e099-108">De hecho, un dispositivo de IoT que desencadenan el shell de interfaz de usuario o utilizar los recursos de voz no puede proporcionar una experiencia de dispositivo en varios idiomas a través de sus aplicaciones para UWP, aunque el SO subyacente de Windows 10 IoT Core se basa simplemente en el modo predeterminado en-US.</span><span class="sxs-lookup"><span data-stu-id="2e099-108">In fact, an IoT device that does not trigger shell UI or utilize speech resources can provide a device experience in many different languages through its UWP applications even though the underlying Windows 10 IoT Core OS is built simply in the en-US default mode.</span></span> 

<span data-ttu-id="2e099-109">Las aplicaciones de UWP deben proporcionar los recursos para los idiomas que deben ser compatibles.</span><span class="sxs-lookup"><span data-stu-id="2e099-109">UWP applications must provide the resources for the languages that are required to be supported.</span></span> <span data-ttu-id="2e099-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) API pueden usarse para especificar las preferencias de idioma.</span><span class="sxs-lookup"><span data-stu-id="2e099-110">[Windows.Globalization.ApplicationLanguage](https://docs.microsoft.com/uwp/api/windows.globalization.applicationlanguages) APIs can be used to specify the language-related preferences.</span></span>

<span data-ttu-id="2e099-111">Vea las aplicaciones de ejemplo siguientes:</span><span class="sxs-lookup"><span data-stu-id="2e099-111">See the below sample applications:</span></span>

* [<span data-ttu-id="2e099-112">Ejemplo de IoTDefaultApp</span><span class="sxs-lookup"><span data-stu-id="2e099-112">IoTDefaultApp sample</span></span>](https://developer.microsoft.com/en-us/windows/iot/samples/iotdefaultapp)

* [<span data-ttu-id="2e099-113">Ejemplo de ApplicationResources</span><span class="sxs-lookup"><span data-stu-id="2e099-113">ApplicationResources sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ApplicationResources)


## <a name="languages-in-os"></a><span data-ttu-id="2e099-114">Idiomas en el sistema operativo</span><span class="sxs-lookup"><span data-stu-id="2e099-114">Languages in OS</span></span>

<span data-ttu-id="2e099-115">Kits de Windows 10 IoTCore ahora incluyen los recursos de idioma para los idiomas siguientes:</span><span class="sxs-lookup"><span data-stu-id="2e099-115">Windows 10 IoTCore kits now include the language resources for the following languages:</span></span>

> | <span data-ttu-id="2e099-116">Lenguaje</span><span class="sxs-lookup"><span data-stu-id="2e099-116">Language</span></span>  | <span data-ttu-id="2e099-117">Código</span><span class="sxs-lookup"><span data-stu-id="2e099-117">Code</span></span> | <span data-ttu-id="2e099-118">Region</span><span class="sxs-lookup"><span data-stu-id="2e099-118">Region</span></span> |
> |-------------|-----|-----|
> | <span data-ttu-id="2e099-119">Inglés (Estados Unidos)</span><span class="sxs-lookup"><span data-stu-id="2e099-119">English (United States)</span></span> | <span data-ttu-id="2e099-120">en-US</span><span class="sxs-lookup"><span data-stu-id="2e099-120">en-US</span></span> | <span data-ttu-id="2e099-121">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="2e099-121">North America</span></span> | 
> | <span data-ttu-id="2e099-122">Inglés (Reino Unido)</span><span class="sxs-lookup"><span data-stu-id="2e099-122">English (UK)</span></span> | <span data-ttu-id="2e099-123">en-GB</span><span class="sxs-lookup"><span data-stu-id="2e099-123">en-GB</span></span> | <span data-ttu-id="2e099-124">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-124">Europe</span></span> |
> | <span data-ttu-id="2e099-125">Francés (Francia)</span><span class="sxs-lookup"><span data-stu-id="2e099-125">French (France)</span></span> | <span data-ttu-id="2e099-126">fr-FR</span><span class="sxs-lookup"><span data-stu-id="2e099-126">fr-FR</span></span> | <span data-ttu-id="2e099-127">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-127">Europe</span></span> |
> | <span data-ttu-id="2e099-128">Francés (Canadá)</span><span class="sxs-lookup"><span data-stu-id="2e099-128">French (Canada)</span></span> | <span data-ttu-id="2e099-129">fr-CA</span><span class="sxs-lookup"><span data-stu-id="2e099-129">fr-CA</span></span> | <span data-ttu-id="2e099-130">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="2e099-130">North America</span></span> |
> | <span data-ttu-id="2e099-131">Español (España)</span><span class="sxs-lookup"><span data-stu-id="2e099-131">Spanish (Spain)</span></span> | <span data-ttu-id="2e099-132">es-ES</span><span class="sxs-lookup"><span data-stu-id="2e099-132">es-ES</span></span> | <span data-ttu-id="2e099-133">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-133">Europe</span></span> |
> | <span data-ttu-id="2e099-134">Español (México)</span><span class="sxs-lookup"><span data-stu-id="2e099-134">Spanish (Mexico)</span></span> | <span data-ttu-id="2e099-135">es-MX</span><span class="sxs-lookup"><span data-stu-id="2e099-135">es-MX</span></span> | <span data-ttu-id="2e099-136">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="2e099-136">North America</span></span> |
> | <span data-ttu-id="2e099-137">Chino</span><span class="sxs-lookup"><span data-stu-id="2e099-137">Chinese</span></span> | <span data-ttu-id="2e099-138">zh-CN</span><span class="sxs-lookup"><span data-stu-id="2e099-138">zh-CN</span></span> | <span data-ttu-id="2e099-139">Asia</span><span class="sxs-lookup"><span data-stu-id="2e099-139">Asia</span></span> | 
> | <span data-ttu-id="2e099-140">Árabe</span><span class="sxs-lookup"><span data-stu-id="2e099-140">Arabic</span></span> | <span data-ttu-id="2e099-141">ar-SA</span><span class="sxs-lookup"><span data-stu-id="2e099-141">ar-SA</span></span> | <span data-ttu-id="2e099-142">Asia</span><span class="sxs-lookup"><span data-stu-id="2e099-142">Asia</span></span> |
> | <span data-ttu-id="2e099-143">Alemán</span><span class="sxs-lookup"><span data-stu-id="2e099-143">German</span></span> | <span data-ttu-id="2e099-144">de-DE</span><span class="sxs-lookup"><span data-stu-id="2e099-144">de-DE</span></span> | <span data-ttu-id="2e099-145">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-145">Europe</span></span> |
> | <span data-ttu-id="2e099-146">Italiano</span><span class="sxs-lookup"><span data-stu-id="2e099-146">Italian</span></span> | <span data-ttu-id="2e099-147">it-IT</span><span class="sxs-lookup"><span data-stu-id="2e099-147">it-IT</span></span> | <span data-ttu-id="2e099-148">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-148">Europe</span></span> | 
> | <span data-ttu-id="2e099-149">Japonés</span><span class="sxs-lookup"><span data-stu-id="2e099-149">Japanese</span></span> | <span data-ttu-id="2e099-150">ja-JP</span><span class="sxs-lookup"><span data-stu-id="2e099-150">ja-JP</span></span> | <span data-ttu-id="2e099-151">Asia</span><span class="sxs-lookup"><span data-stu-id="2e099-151">Asia</span></span> |
> | <span data-ttu-id="2e099-152">Coreano</span><span class="sxs-lookup"><span data-stu-id="2e099-152">Korean</span></span> | <span data-ttu-id="2e099-153">ko-KR</span><span class="sxs-lookup"><span data-stu-id="2e099-153">ko-KR</span></span> | <span data-ttu-id="2e099-154">Asia</span><span class="sxs-lookup"><span data-stu-id="2e099-154">Asia</span></span> |
> | <span data-ttu-id="2e099-155">Neerlandés</span><span class="sxs-lookup"><span data-stu-id="2e099-155">Dutch</span></span> | <span data-ttu-id="2e099-156">nl-NL</span><span class="sxs-lookup"><span data-stu-id="2e099-156">nl-NL</span></span> | <span data-ttu-id="2e099-157">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-157">Europe</span></span> |
> | <span data-ttu-id="2e099-158">Polaco</span><span class="sxs-lookup"><span data-stu-id="2e099-158">Polish</span></span> | <span data-ttu-id="2e099-159">pl-PL</span><span class="sxs-lookup"><span data-stu-id="2e099-159">pl-PL</span></span> | <span data-ttu-id="2e099-160">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-160">Europe</span></span> | 
> | <span data-ttu-id="2e099-161">Rumano</span><span class="sxs-lookup"><span data-stu-id="2e099-161">Romanian</span></span> | <span data-ttu-id="2e099-162">ro-RO</span><span class="sxs-lookup"><span data-stu-id="2e099-162">ro-RO</span></span> | <span data-ttu-id="2e099-163">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-163">Europe</span></span> |
> | <span data-ttu-id="2e099-164">Ruso</span><span class="sxs-lookup"><span data-stu-id="2e099-164">Russian</span></span> | <span data-ttu-id="2e099-165">ro-RU</span><span class="sxs-lookup"><span data-stu-id="2e099-165">ro-RU</span></span> | <span data-ttu-id="2e099-166">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-166">Europe</span></span> |
> | <span data-ttu-id="2e099-167">Griego</span><span class="sxs-lookup"><span data-stu-id="2e099-167">Greek</span></span> | <span data-ttu-id="2e099-168">el-GR</span><span class="sxs-lookup"><span data-stu-id="2e099-168">el-GR</span></span> | <span data-ttu-id="2e099-169">Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-169">Europe</span></span> |
> | <span data-ttu-id="2e099-170">Portugués (Brasil)</span><span class="sxs-lookup"><span data-stu-id="2e099-170">Portugese (Brazil)</span></span> | <span data-ttu-id="2e099-171">pt-BR</span><span class="sxs-lookup"><span data-stu-id="2e099-171">pt-BR</span></span> | <span data-ttu-id="2e099-172">Sudamérica y Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-172">South America/Europe</span></span> |
> | <span data-ttu-id="2e099-173">Portuese (Portugal)</span><span class="sxs-lookup"><span data-stu-id="2e099-173">Portuese (Portugal)</span></span> | <span data-ttu-id="2e099-174">pt-PR</span><span class="sxs-lookup"><span data-stu-id="2e099-174">pt-PR</span></span> | <span data-ttu-id="2e099-175">Sudamérica y Europa</span><span class="sxs-lookup"><span data-stu-id="2e099-175">South America/Europe</span></span> |

<span data-ttu-id="2e099-176">Estos recursos de idioma contienen cadenas de interfaz de usuario, idiomas de voz y voces (síntesis de voz).</span><span class="sxs-lookup"><span data-stu-id="2e099-176">These language resources contain UI strings, speech language and voices (speech synthesis).</span></span> <span data-ttu-id="2e099-177">Se pueden crear imágenes de Windows IoT con uno o varios de estos recursos y se debe especificar durante el tiempo de imagen y no se puede modificar más adelante.</span><span class="sxs-lookup"><span data-stu-id="2e099-177">Windows IoT images can be built with one or more of these resources and they must be specified during the image time and cannot be modified later.</span></span> <span data-ttu-id="2e099-178">Tenga en cuenta que el idioma de interfaz de usuario relacionados con los recursos son independientes de lenguaje de voz y los recursos de voz.</span><span class="sxs-lookup"><span data-stu-id="2e099-178">Note that UI language related resources are independent than speech language and voice resources.</span></span>

### <a name="specifying-ui-and-speech-resources"></a><span data-ttu-id="2e099-179">Especificar recursos de la interfaz de usuario y de voz</span><span class="sxs-lookup"><span data-stu-id="2e099-179">Specifying UI and Speech resources</span></span> 
<span data-ttu-id="2e099-180">En el archivo xml de entrada de OEM, la interfaz de usuario necesaria e idiomas de voz se especifican como se muestra a continuación</span><span class="sxs-lookup"><span data-stu-id="2e099-180">In the OEM Input xml file, the required UI and speech languages are specified as shown below</span></span>

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


### <a name="specifying-speech-data-resources"></a><span data-ttu-id="2e099-181">Especificar recursos de datos de voz</span><span class="sxs-lookup"><span data-stu-id="2e099-181">Specifying Speech Data resources</span></span>
<span data-ttu-id="2e099-182">En el archivo xml de entrada de OEM, se especifican los recursos de datos de voz necesarios tal como se muestra a continuación,</span><span class="sxs-lookup"><span data-stu-id="2e099-182">In the OEM Input xml file, the required speech data resources are specified as shown below,</span></span>

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
> <span data-ttu-id="2e099-183">De forma predeterminada, los datos de voz en-US se incluyen en la imagen.</span><span class="sxs-lookup"><span data-stu-id="2e099-183">By default, en-US speech data is included in the image.</span></span>

### <a name="samples"></a><span data-ttu-id="2e099-184">Muestras</span><span class="sxs-lookup"><span data-stu-id="2e099-184">Samples</span></span>
* <span data-ttu-id="2e099-185">Consulte [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) para admiten varios idiomas</span><span class="sxs-lookup"><span data-stu-id="2e099-185">See [MultiLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/MultiLangSample) for multiple languages support</span></span>
* <span data-ttu-id="2e099-186">Consulte [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) idioma fr-FR con en-US como idioma de reserva.</span><span class="sxs-lookup"><span data-stu-id="2e099-186">See [SingleLangSample](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample) for fr-FR language with en-US as fallback language.</span></span>
    * <span data-ttu-id="2e099-187">Tenga en cuenta que cuando se cambia el idioma de interfaz de usuario de inicio, la `administrator` también se traduce el nombre de la cuenta en el idioma de interfaz de usuario de arranque.</span><span class="sxs-lookup"><span data-stu-id="2e099-187">Note that when the boot UI language is changed, the `administrator` account name is also translated in the boot UI language.</span></span> <span data-ttu-id="2e099-188">Por lo tanto, en fr-FR es `administrateur`.</span><span class="sxs-lookup"><span data-stu-id="2e099-188">So, in fr-FR it is `administrateur`.</span></span> <span data-ttu-id="2e099-189">Consulte [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span><span class="sxs-lookup"><span data-stu-id="2e099-189">See [OEMCustomization.cmd](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Products/SingleLangSample/oemcustomization.cmd)</span></span>

## <a name="changing-user-preferences-language-region-speech-and-voice"></a><span data-ttu-id="2e099-190">Cambiar las preferencias del usuario (idioma, región, voz y voz)</span><span class="sxs-lookup"><span data-stu-id="2e099-190">Changing user preferences (language, region, speech and voice)</span></span>

<span data-ttu-id="2e099-191">Aplicación de UWP puede usar WinRT APIs para establecer la región, lista de idiomas de interfaz de usuario preferido, lenguaje de voz y voz que se debe usar de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="2e099-191">UWP application can use WinRT APIs to set the region, preferred UI language list, speech language and voice that should be by default used.</span></span> <span data-ttu-id="2e099-192">Conjunto de lista de idioma de interfaz de usuario una vez preferido, aplicación de UWP intentará cargar los recursos correspondientes (a menos que la aplicación mediante programación impide dicho).</span><span class="sxs-lookup"><span data-stu-id="2e099-192">Once preferred UI language list set, UWP application will try to load the corresponding resources (unless application programmatically prevents that).</span></span>
 
<span data-ttu-id="2e099-193">Si la aplicación no tiene los recursos correspondientes, se cargarán los recursos de reserva.</span><span class="sxs-lookup"><span data-stu-id="2e099-193">If the application doesn’t have the corresponding resources, then fallback resources will be loaded.</span></span> <span data-ttu-id="2e099-194">De forma similar, si los recursos del sistema operativo para el idioma preferido no forman parte de la imagen de Windows IoT, IoT Windows usará los reserva probable inglés (en-US).</span><span class="sxs-lookup"><span data-stu-id="2e099-194">Similarly, if the OS resources for the preferred languages aren’t part of the Windows IoT image, Windows IoT will use its fallback ones likely English (en-US).</span></span>

* <span data-ttu-id="2e099-195">Establece la región mediante `TrySetHomeGeographicRegion` en [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="2e099-195">Set region using `TrySetHomeGeographicRegion` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="2e099-196">Idioma de interfaz de usuario de conjunto con `TrySetLanguages` en [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span><span class="sxs-lookup"><span data-stu-id="2e099-196">Set UI language using `TrySetLanguages` in [Windows.System.UserProfile.GlobalizationPreferences](https://docs.microsoft.com/uwp/api/windows.system.userprofile.globalizationpreferences)</span></span>
* <span data-ttu-id="2e099-197">Conjunto de voz idioma mediante `TrySetSystemSpeechLanguageAsync` en [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span><span class="sxs-lookup"><span data-stu-id="2e099-197">Set speech language using `TrySetSystemSpeechLanguageAsync` in [Windows.Media.SpeechRecognition.SpeechRecognizer](https://docs.microsoft.com/uwp/api/windows.media.speechrecognition.speechrecognizer)</span></span>
* <span data-ttu-id="2e099-198">Establecer mediante voz `TrySetDefaultVoiceAsync` en [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span><span class="sxs-lookup"><span data-stu-id="2e099-198">Set voice using `TrySetDefaultVoiceAsync` in [Windows.Media.SpeechSynthesis.SpeechSynthesizer](https://docs.microsoft.com/en-us/uwp/api/windows.media.speechsynthesis.speechsynthesizer)</span></span>

> [!NOTE]
> <span data-ttu-id="2e099-199">Para que funcione correctamente, Cortana requiere la región, el idioma de interfaz de usuario y lenguaje de voz para que sea coherente, p. ej.: región FR, la interfaz de usuario y la voz idiomas fr-FR o región ES, la interfaz de usuario y la voz idiomas es-es al directorio.</span><span class="sxs-lookup"><span data-stu-id="2e099-199">For proper functioning, Cortana requires the region, UI language and speech language to be consistent, e.g.: region FR, UI and speech languages fr-FR or region ES, UI and speech languages es-ES.</span></span> <span data-ttu-id="2e099-200">Cortana usa su propia voz, aplicación de UWP no puede cambiar.</span><span class="sxs-lookup"><span data-stu-id="2e099-200">Cortana uses its own voice, UWP application cannot change it.</span></span>

## <a name="iotsettingsexe"></a><span data-ttu-id="2e099-201">IoTSettings.exe</span><span class="sxs-lookup"><span data-stu-id="2e099-201">IoTSettings.exe</span></span>

<span data-ttu-id="2e099-202">Para más información acerca de cómo cambiar la configuración de región y el usuario o el lenguaje de voz crear productos de Cortana habilitado, lea nuestra [utilidades de línea de comandos](../manage-your-device/CommandLineUtils.md) documentación.</span><span class="sxs-lookup"><span data-stu-id="2e099-202">To learn more about changing settings for region and user or speech language to build Cortana enabled products, please read our [Command Line Utils](../manage-your-device/CommandLineUtils.md) documentation.</span></span>
