---
title: Aplicación predeterminada de Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Obtenga información sobre la aplicación predeterminada de Windows 10 IoT Core y sus características.
keywords: Windows IOT, Windows 10 IOT Core, aplicación predeterminada
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168032"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="c8eed-104">Introducción a la aplicación predeterminada de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="c8eed-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="c8eed-105">Si le gustaría ver una característica agregada a esta aplicación de ejemplo, [abra un problema](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) en github para que podamos saberlo.</span><span class="sxs-lookup"><span data-stu-id="c8eed-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="c8eed-106">Si desea archivar un error, siga las instrucciones del centro de comentarios [aquí](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span><span class="sxs-lookup"><span data-stu-id="c8eed-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="c8eed-107">La primera vez que Flash Windows 10 IoT Core, se le presentará la aplicación Windows 10 IoT Core predeterminada en el inicio, que tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="c8eed-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![Captura de pantalla de la aplicación predeterminada de IoT Core](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="c8eed-109">La finalidad de esta aplicación no es solo proporcionar un shell sencillo para interactuar con la primera vez que se arranca Windows 10 IoT Core, pero se ha proporcionado código abierto para esta aplicación [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para que pueda conectarse y jugar con estas características en su propia cu aplicaciones sonalizado.</span><span class="sxs-lookup"><span data-stu-id="c8eed-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="c8eed-110">En este artículo se proporciona un resumen de las distintas características que ofrece la aplicación predeterminada de Windows 10 IoT Core, así como cómo puede aprovechar estas características diferentes para sus propias aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c8eed-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="c8eed-111">Aprovechamiento de la aplicación predeterminada de IoT Core</span><span class="sxs-lookup"><span data-stu-id="c8eed-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c8eed-112">No use las imágenes del creador con fines comerciales.</span><span class="sxs-lookup"><span data-stu-id="c8eed-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="c8eed-113">Si se comercializa un dispositivo, debe usar una FFU personalizada para una seguridad óptima.</span><span class="sxs-lookup"><span data-stu-id="c8eed-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="c8eed-114">Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="c8eed-114">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="c8eed-115">La aplicación predeterminada de IoT Core puede personalizarse y ampliarse, o bien se puede usar el código fuente como ejemplo para su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8eed-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="c8eed-116">Para probarlo, descargue el archivo. zip de nuestros ejemplos o consulte el código de la aplicación de IoT Core predeterminada [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="c8eed-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="c8eed-117">Si tiene alguna pregunta, envíe un problema en nuestro repositorio de ejemplos [aquí](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span><span class="sxs-lookup"><span data-stu-id="c8eed-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="c8eed-118">Como se muestra en [la sección](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) configuración siguiente, en algunos casos, puede configurar la configuración y las características predeterminadas en el sistema del cliente en nombre del usuario final.</span><span class="sxs-lookup"><span data-stu-id="c8eed-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="c8eed-119">Sin embargo, si activa esta configuración y las características de forma predeterminada o si los diagnósticos están por encima de la configuración básica, debe:</span><span class="sxs-lookup"><span data-stu-id="c8eed-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="c8eed-120">Notifique al usuario final que se han habilitado estas características y proporcione al usuario final el vínculo a la Página Web de la declaración de privacidad de Microsoft [aquí](http://go.microsoft.com/fwlink/?LinkId=521839).</span><span class="sxs-lookup"><span data-stu-id="c8eed-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="c8eed-121">Consentimiento seguro del usuario final relevante para habilitar dichas características de forma predeterminada (según lo requiera la ley aplicable).</span><span class="sxs-lookup"><span data-stu-id="c8eed-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="c8eed-122">Proporcionar a los usuarios finales la capacidad de volver a cambiar la configuración de diagnóstico a la configuración básica.</span><span class="sxs-lookup"><span data-stu-id="c8eed-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="c8eed-123">Si habilita las cuentas de Microsoft y tiene acceso a los datos del usuario final, si el usuario final elimina la cuenta de Microsoft, debe habilitar la eliminación simultánea de todos los datos de la cuenta de Microsoft del usuario final en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c8eed-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="c8eed-124">La experiencia rápida (OOBE)</span><span class="sxs-lookup"><span data-stu-id="c8eed-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="c8eed-125">La configuración rápida de la aplicación predeterminada de IoT Core es tan eficiente como se obtiene.</span><span class="sxs-lookup"><span data-stu-id="c8eed-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="c8eed-126">Las primeras páginas solicitarán un idioma y una configuración de Wi-Fi predeterminados.</span><span class="sxs-lookup"><span data-stu-id="c8eed-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="c8eed-127">A partir de ahí, para que la aplicación sea compatible con RGPD, debe tener una pantalla de datos de diagnóstico y, si tiene previsto realizar un seguimiento de la ubicación, deberá tener también una pantalla de permisos de ubicación.</span><span class="sxs-lookup"><span data-stu-id="c8eed-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="c8eed-128">A continuación se muestran ejemplos de ambos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-128">Examples of both are shown below.</span></span> 

<span data-ttu-id="c8eed-129">![Configuración de la ubicación](../media/IoTCoreDefaultApp/OOBE3.jpg)
de la configuración de diagnóstico de Oobe![para Oobe](../media/IoTCoreDefaultApp/OOBE4.jpg)</span><span class="sxs-lookup"><span data-stu-id="c8eed-129">![Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE](../media/IoTCoreDefaultApp/OOBE4.jpg)</span></span>

## <a name="command-bar"></a><span data-ttu-id="c8eed-130">Barra de comandos</span><span class="sxs-lookup"><span data-stu-id="c8eed-130">Command Bar</span></span>
<span data-ttu-id="c8eed-131">La barra de comandos es la barra horizonatal persistente que se encuentra en la parte inferior de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="c8eed-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="c8eed-132">Esto proporciona acceso sencillo a la siguiente funcionalidad de:</span><span class="sxs-lookup"><span data-stu-id="c8eed-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="c8eed-133">Navegación de página hacia delante y hacia atrás</span><span class="sxs-lookup"><span data-stu-id="c8eed-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="c8eed-134">Información básica del dispositivo sin pasar a la página actual</span><span class="sxs-lookup"><span data-stu-id="c8eed-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="c8eed-135">Activar o desactivar el modo de pantalla completa</span><span class="sxs-lookup"><span data-stu-id="c8eed-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="c8eed-136">Métodos abreviados avanzados</span><span class="sxs-lookup"><span data-stu-id="c8eed-136">Advance shortcuts</span></span>
- <span data-ttu-id="c8eed-137">Botones específicos de la página</span><span class="sxs-lookup"><span data-stu-id="c8eed-137">Page specific buttons</span></span>

<span data-ttu-id="c8eed-138">Hay un gran número de botones en la barra de comandos y, a veces, estos botones pueden ser confusos u ocultos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="c8eed-139">Para expandir la barra de comandos y acceder a esos botones, presione el botón de menú de la parte inferior derecha:</span><span class="sxs-lookup"><span data-stu-id="c8eed-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![Cómo expandir la barra de comandos](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="c8eed-141">Menú Inicio-reproducir</span><span class="sxs-lookup"><span data-stu-id="c8eed-141">Start Menu - Play</span></span>

<span data-ttu-id="c8eed-142">En el menú Inicio se encuentra en directo la mayoría de las características de plug and Play.</span><span class="sxs-lookup"><span data-stu-id="c8eed-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="c8eed-143">El Tiempo</span><span class="sxs-lookup"><span data-stu-id="c8eed-143">Weather</span></span>
<span data-ttu-id="c8eed-144">Con los datos del servicio de Meteorología nacional, la página de Meteorología representa información meteorológica en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="c8eed-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="c8eed-145">Explorador Web</span><span class="sxs-lookup"><span data-stu-id="c8eed-145">Web Browser</span></span>
<span data-ttu-id="c8eed-146">El explorador Web permite extraer la mayoría de los sitios de la Web.</span><span class="sxs-lookup"><span data-stu-id="c8eed-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="c8eed-147">Música</span><span class="sxs-lookup"><span data-stu-id="c8eed-147">Music</span></span>
<span data-ttu-id="c8eed-148">En esta página se reproducirán archivos MP3 y WAV de la **biblioteca de música**, a los que se puede tener acceso a través del portal de [dispositivos de Windows](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="c8eed-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="c8eed-149">Para cargar archivos en el reproductor de música, debe ir al portal de dispositivos de Windows, hacer clic en la lista desplegable "aplicaciones", navegar a "explorador de archivos", seleccionar "música" y cargar los archivos desde allí.</span><span class="sxs-lookup"><span data-stu-id="c8eed-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="c8eed-151">Presentación</span><span class="sxs-lookup"><span data-stu-id="c8eed-151">Slideshow</span></span>
<span data-ttu-id="c8eed-152">Esta página mostrará los archivos de imagen PNG o JPEG de la **biblioteca de imágenes**, a los que se puede tener acceso a través del [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="c8eed-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="c8eed-153">Para cargar imágenes en la presentación de diapositivas, debe ir al portal de dispositivos de Windows, hacer clic en la lista desplegable "aplicaciones", navegar a "explorador de archivos", seleccionar "imágenes" y cargar los archivos desde allí.</span><span class="sxs-lookup"><span data-stu-id="c8eed-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="c8eed-155">Dibujar</span><span class="sxs-lookup"><span data-stu-id="c8eed-155">Draw</span></span>
<span data-ttu-id="c8eed-156">Esta página le permite probar las funcionalidades de entrada manuscrita de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c8eed-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="c8eed-157">Menú Inicio-explorar</span><span class="sxs-lookup"><span data-stu-id="c8eed-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="c8eed-158">Aplicaciones</span><span class="sxs-lookup"><span data-stu-id="c8eed-158">Apps</span></span> 
<span data-ttu-id="c8eed-159">Esta página permite iniciar otras aplicaciones de primer plano instaladas en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c8eed-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="c8eed-160">Al iniciar una aplicación, se suspenderá la aplicación predeterminada de IoT Core, que se puede volver a iniciar mediante App Manager en el [portal de dispositivos de Windows](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="c8eed-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="c8eed-161">No es necesario nada especial para que la aplicación de primer plano aparezca en la página, simplemente [Instale](AppInstaller.md) o [implemente](AppDeployment.md) la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8eed-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="c8eed-162">Después de una instalación o una implementación correcta, vuelva a navegar a la página aplicaciones para actualizar la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c8eed-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="c8eed-163">Tenga en cuenta que hay un par de aplicaciones relacionadas con el sistema operativo generadas automáticamente que se filtran, puede encontrar la lista de nombres de aplicación [aquí](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span><span class="sxs-lookup"><span data-stu-id="c8eed-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="c8eed-164">Notificaciones</span><span class="sxs-lookup"><span data-stu-id="c8eed-164">Notifications</span></span>
<span data-ttu-id="c8eed-165">En esta página se enumeran las últimas 20 notificaciones, ya que se ha iniciado la aplicación predeterminada de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c8eed-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="c8eed-166">Cuando la aplicación predeterminada de IoT Core se ejecuta en modo de depuración, se agregan botones que crearán notificaciones de prueba.</span><span class="sxs-lookup"><span data-stu-id="c8eed-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="c8eed-167">Registros</span><span class="sxs-lookup"><span data-stu-id="c8eed-167">Logs</span></span>
<span data-ttu-id="c8eed-168">En esta página se enumeran los registros de errores o bloqueos generados automáticamente que se pueden quitar del dispositivo y analizarlos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="c8eed-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="c8eed-169">GitHub</span></span>
<span data-ttu-id="c8eed-170">Esta página le llevará a la ubicación de GitHub de código abierto del código de aplicación predeterminado de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c8eed-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="c8eed-171">Menú Inicio-Windows Device portal</span><span class="sxs-lookup"><span data-stu-id="c8eed-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="c8eed-172">En las páginas de esta sección se aprovechan las API de REST de Windows Device portal, que requiere que inicie sesión con sus credenciales de Windows Device portal.</span><span class="sxs-lookup"><span data-stu-id="c8eed-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="c8eed-173">Información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c8eed-173">Device Information</span></span>

<span data-ttu-id="c8eed-174">Esta página le permite ver las distintas características del dispositivo, como Ethernet, la versión del sistema operativo, los dispositivos conectados, etc.</span><span class="sxs-lookup"><span data-stu-id="c8eed-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="c8eed-175">Línea de comandos</span><span class="sxs-lookup"><span data-stu-id="c8eed-175">Command Line</span></span>

<span data-ttu-id="c8eed-176">Esta página le permite ejecutar comandos directamente en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c8eed-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="c8eed-177">Para habilitar esta característica, debe establecer una clave del registro para que la aplicación pueda ejecutar los comandos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="c8eed-178">La primera vez que intente ejecutar un comando, verá un vínculo que le permite establecer la clave del registro mediante una llamada a Windows Device portal.</span><span class="sxs-lookup"><span data-stu-id="c8eed-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="c8eed-179">Haga clic en el vínculo para habilitar el dispositivo para ejecutar comandos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="c8eed-180">Algunos comandos requieren acceso de administrador.</span><span class="sxs-lookup"><span data-stu-id="c8eed-180">Some commands require administrator access.</span></span> <span data-ttu-id="c8eed-181">Por motivos de seguridad, la aplicación usa una cuenta que no es de administrador de forma predeterminada para ejecutar comandos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="c8eed-182">Si necesita ejecutar un comando como administrador, puede escribir "RunAsAdmin <your command>" en el símbolo de la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="c8eed-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="c8eed-183">Configuración</span><span class="sxs-lookup"><span data-stu-id="c8eed-183">Settings</span></span>
<span data-ttu-id="c8eed-184">Aquí podrá configurar una serie de opciones, como Wi-Fi, Bluetooth, opciones de energía, etc.</span><span class="sxs-lookup"><span data-stu-id="c8eed-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="c8eed-185">Configuración de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c8eed-185">App Settings</span></span>
<span data-ttu-id="c8eed-186">La sección configuración de la **aplicación** permite configurar varias opciones para las páginas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8eed-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="c8eed-187">Algunas de las opciones que puede personalizar son:</span><span class="sxs-lookup"><span data-stu-id="c8eed-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="c8eed-188">Configuración general</span><span class="sxs-lookup"><span data-stu-id="c8eed-188">General Settings</span></span>
* <span data-ttu-id="c8eed-189">Establecer la página predeterminada que aparece cuando se inicia la aplicación</span><span class="sxs-lookup"><span data-stu-id="c8eed-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="c8eed-190">Habilitar o deshabilitar el protector de la</span><span class="sxs-lookup"><span data-stu-id="c8eed-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="c8eed-191">Configuración meteorológica</span><span class="sxs-lookup"><span data-stu-id="c8eed-191">Weather Settings</span></span>
* <span data-ttu-id="c8eed-192">Cambiar la ubicación</span><span class="sxs-lookup"><span data-stu-id="c8eed-192">Change the location</span></span>
  > <span data-ttu-id="c8eed-193">Esta característica solo está habilitada si se ha proporcionado un [token de servicio de mapa de Bing](https://msdn.microsoft.com/library/ff428642.aspx)válido.</span><span class="sxs-lookup"><span data-stu-id="c8eed-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="c8eed-194">Para pasar el token a la aplicación, cree un archivo **MapToken. config** en la carpeta LocalState de la aplicación (por ejemplo,\\C:\Data\USERS [cuenta de usuario\\] \AppData\Packages [nombre completo del paquete] \LocalState\MapToken.config) y reinicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8eed-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="c8eed-195">Expandir el mapa</span><span class="sxs-lookup"><span data-stu-id="c8eed-195">Expand the map</span></span>
* <span data-ttu-id="c8eed-196">Habilitar o deshabilitar el volteo de mapas para que el mapa y el interruptor meteorológico se coloquen periódicamente para evitar la grabación de la pantalla</span><span class="sxs-lookup"><span data-stu-id="c8eed-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="c8eed-197">Configuración del explorador Web</span><span class="sxs-lookup"><span data-stu-id="c8eed-197">Web Browser Settings</span></span>
* <span data-ttu-id="c8eed-198">Establecer la Página principal del explorador Web</span><span class="sxs-lookup"><span data-stu-id="c8eed-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="c8eed-199">Configuración de la presentación</span><span class="sxs-lookup"><span data-stu-id="c8eed-199">Slideshow Settings</span></span>
* <span data-ttu-id="c8eed-200">Establecer el intervalo de presentación de diapositivas</span><span class="sxs-lookup"><span data-stu-id="c8eed-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="c8eed-201">Apariencia</span><span class="sxs-lookup"><span data-stu-id="c8eed-201">Appearance</span></span>
* <span data-ttu-id="c8eed-202">Usar activos de MDL2 en lugar de emojis para los iconos de icono</span><span class="sxs-lookup"><span data-stu-id="c8eed-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="c8eed-203">Establecer el ancho y el alto del mosaico</span><span class="sxs-lookup"><span data-stu-id="c8eed-203">Set the tile width and height</span></span>
* <span data-ttu-id="c8eed-204">Establecer escala de IU: el escalado automático se establece de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="c8eed-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="c8eed-205">Establecer el color del mosaico</span><span class="sxs-lookup"><span data-stu-id="c8eed-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="c8eed-206">Sistema</span><span class="sxs-lookup"><span data-stu-id="c8eed-206">System</span></span>
<span data-ttu-id="c8eed-207">Cambiar el idioma, la distribución del teclado y la zona horaria.</span><span class="sxs-lookup"><span data-stu-id="c8eed-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="c8eed-208">Red & Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c8eed-208">Network & Wi-Fi</span></span>
<span data-ttu-id="c8eed-209">Ver las propiedades del adaptador de red o conectarse a una red Wi-Fi disponible.</span><span class="sxs-lookup"><span data-stu-id="c8eed-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="c8eed-210">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c8eed-210">Bluetooth</span></span>
<span data-ttu-id="c8eed-211">Emparejar con un dispositivo Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="c8eed-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="c8eed-212">Actualizaciones de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="c8eed-212">App Updates</span></span>
<span data-ttu-id="c8eed-213">Compruebe si hay actualizaciones de la aplicación o cambie la configuración de actualización automática.</span><span class="sxs-lookup"><span data-stu-id="c8eed-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="c8eed-214">Opciones de energía</span><span class="sxs-lookup"><span data-stu-id="c8eed-214">Power Options</span></span>
<span data-ttu-id="c8eed-215">Reiniciar o apagar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c8eed-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="c8eed-216">Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="c8eed-216">Diagnostics</span></span>
<span data-ttu-id="c8eed-217">Seleccione la cantidad de datos de diagnóstico que desea proporcionar a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c8eed-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="c8eed-218">Se recomienda a los usuarios que opten por los datos de diagnóstico **completos** para que podamos diagnosticar problemas rápidamente y realizar mejoras en el producto.</span><span class="sxs-lookup"><span data-stu-id="c8eed-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="c8eed-219">Básica</span><span class="sxs-lookup"><span data-stu-id="c8eed-219">Basic</span></span> 
<span data-ttu-id="c8eed-220">Envíe solo información sobre el dispositivo, su configuración y capacidades, y si funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="c8eed-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="c8eed-221">Completo</span><span class="sxs-lookup"><span data-stu-id="c8eed-221">Full</span></span>
<span data-ttu-id="c8eed-222">Enviar todos los datos de diagnóstico básicos, junto con información sobre los sitios web que se examinan y cómo se usan las aplicaciones y características, además de información adicional sobre el estado del dispositivo, la actividad del dispositivo y el informe de errores mejorado.</span><span class="sxs-lookup"><span data-stu-id="c8eed-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="c8eed-223">Location</span><span class="sxs-lookup"><span data-stu-id="c8eed-223">Location</span></span>
<span data-ttu-id="c8eed-224">Permita o deniegue el acceso de la aplicación a su ubicación.</span><span class="sxs-lookup"><span data-stu-id="c8eed-224">Allow or deny the app access to your location.</span></span>
