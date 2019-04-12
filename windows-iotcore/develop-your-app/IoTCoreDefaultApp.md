---
title: Aplicación de Windows 10 IoT Core predeterminada
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: Obtenga información sobre la aplicación de predeterminado de Windows 10 IoT Core y sus características.
keywords: Windows iot core de windows 10 iot, aplicación predeterminada
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514304"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="62d26-104">Información general de aplicación de Windows 10 IoT Core predeterminada</span><span class="sxs-lookup"><span data-stu-id="62d26-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="62d26-105">Si encuentra que gustaría ver una característica agregada a esta aplicación de ejemplo, [abra una incidencia](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) en GitHub para hacernos saber.</span><span class="sxs-lookup"><span data-stu-id="62d26-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="62d26-106">Si desea archivar un error, siga las instrucciones para el centro de comentarios [aquí](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span><span class="sxs-lookup"><span data-stu-id="62d26-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="62d26-107">Cuando inicialmente flash de Windows 10 IoT Core, se le mostrará con Windows 10 IoT Core predeterminado ella tras el inicio, que tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="62d26-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![Captura de pantalla de la aplicación predeterminada de IoT Core](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="62d26-109">El propósito de esta aplicación no es solo para proporcionarle un shell para interactuar con cuando arranca por primera vez seguridad de Windows 10 IoT Core descriptivo, pero se ha abierto el código para esta aplicación [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para que puede de plug and play con estos características en sus propias aplicaciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="62d26-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="62d26-110">En este artículo le proporcionará un resumen de las diferentes características que la aplicación de predeterminado de Windows 10 IoT Core ofrece también cómo puede aprovechar estas características diferentes para sus propias aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="62d26-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="62d26-111">Aprovechamiento de la aplicación predeterminada de IoT Core</span><span class="sxs-lookup"><span data-stu-id="62d26-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="62d26-112">No use maker imágenes para la comercialización.</span><span class="sxs-lookup"><span data-stu-id="62d26-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="62d26-113">Si se commercializing un dispositivo, debe usar un FFU personalizado para una seguridad óptima.</span><span class="sxs-lookup"><span data-stu-id="62d26-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="62d26-114">Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="62d26-114">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="62d26-115">Se pueden personalizar y extender la aplicación predeterminada de IoT Core, o puede usar el código fuente como ejemplo para su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="62d26-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="62d26-116">Para probar esto por sí mismo, descargue el archivo zip de nuestros ejemplos o revise el código para la aplicación predeterminada de IoT Core [aquí](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="62d26-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="62d26-117">Si tiene alguna pregunta, registre un problema en nuestro repositorio de ejemplos [aquí](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span><span class="sxs-lookup"><span data-stu-id="62d26-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="62d26-118">Como se muestra en el [sección configuración](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) a continuación, en algunos casos, puede configurar características y la configuración predeterminada en el sistema de cliente en nombre del usuario final.</span><span class="sxs-lookup"><span data-stu-id="62d26-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="62d26-119">Sin embargo, si desactiva estas opciones y características de forma predeterminada o si diagnósticos están por encima de la configuración básica, debe:</span><span class="sxs-lookup"><span data-stu-id="62d26-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="62d26-120">Notificar al usuario final que estas características han sido enable y proporcionan al usuario final con el vínculo a la página de web de declaración de privacidad de Microsoft [aquí](http://go.microsoft.com/fwlink/?LinkId=521839).</span><span class="sxs-lookup"><span data-stu-id="62d26-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="62d26-121">Proteja el consentimiento del usuario final correspondiente para habilitar estas características de forma predeterminada (según sea necesario por la ley aplicable).</span><span class="sxs-lookup"><span data-stu-id="62d26-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="62d26-122">Proporcionar a los usuarios finales la capacidad de volver a cambiar la configuración de diagnóstico a la configuración básica.</span><span class="sxs-lookup"><span data-stu-id="62d26-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="62d26-123">Si habilita Microsoft Accounts y tener acceso a los datos de usuario final, si el usuario final elimina la Account de Microsoft, debe habilitar su eliminación simultánea de datos de Microsoft Account todas las del usuario final en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="62d26-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="62d26-124">Experiencia de out-of-Box (OOBE)</span><span class="sxs-lookup"><span data-stu-id="62d26-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="62d26-125">Es tan eficiente a medida que la experiencia de out-of-box para la aplicación predeterminada de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="62d26-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="62d26-126">Las primeras páginas le pedirá una configuración predeterminada de idioma y wi-fi.</span><span class="sxs-lookup"><span data-stu-id="62d26-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="62d26-127">Desde allí, en orden para su aplicación para que sea compatible con GDPR, debe tener una pantalla de datos de diagnóstico y, si planea realizar un seguimiento de ubicación, deberá tener también una pantalla de permisos de ubicación.</span><span class="sxs-lookup"><span data-stu-id="62d26-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="62d26-128">A continuación se muestran ejemplos de ambos.</span><span class="sxs-lookup"><span data-stu-id="62d26-128">Examples of both are shown below.</span></span> 

![<span data-ttu-id="62d26-129">Configuración de ubicación de OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![configuración de diagnóstico de la bienvenida de Windows</span><span class="sxs-lookup"><span data-stu-id="62d26-129">Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE</span></span>](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a><span data-ttu-id="62d26-130">Barra de comandos</span><span class="sxs-lookup"><span data-stu-id="62d26-130">Command Bar</span></span>
<span data-ttu-id="62d26-131">La barra de comandos es la barra de horizonatal persistente en la parte inferior de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="62d26-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="62d26-132">Esto proporciona un acceso sencillo a la funcionalidad siguiente:</span><span class="sxs-lookup"><span data-stu-id="62d26-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="62d26-133">Navegación de páginas hacia delante y hacia atrás</span><span class="sxs-lookup"><span data-stu-id="62d26-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="62d26-134">Información básica del dispositivo sin salir de la página actual</span><span class="sxs-lookup"><span data-stu-id="62d26-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="62d26-135">Activar o desactivar el modo de pantalla completa</span><span class="sxs-lookup"><span data-stu-id="62d26-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="62d26-136">Métodos abreviados de avance</span><span class="sxs-lookup"><span data-stu-id="62d26-136">Advance shortcuts</span></span>
- <span data-ttu-id="62d26-137">Botones de página específicos</span><span class="sxs-lookup"><span data-stu-id="62d26-137">Page specific buttons</span></span>

<span data-ttu-id="62d26-138">Hay muchos botones en la barra de comandos y, a veces, estos botones pueden ser confuso u oculto.</span><span class="sxs-lookup"><span data-stu-id="62d26-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="62d26-139">Para expandir la barra de comandos y obtener acceso a esos botones, haga clic en el botón de menú en la parte inferior derecha:</span><span class="sxs-lookup"><span data-stu-id="62d26-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![Cómo expandir la barra de comandos](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="62d26-141">Iniciar menú - Play</span><span class="sxs-lookup"><span data-stu-id="62d26-141">Start Menu - Play</span></span>

<span data-ttu-id="62d26-142">El menú Inicio es donde residen la mayoría de las características de plug and play.</span><span class="sxs-lookup"><span data-stu-id="62d26-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="62d26-143">El Tiempo</span><span class="sxs-lookup"><span data-stu-id="62d26-143">Weather</span></span>
<span data-ttu-id="62d26-144">Con datos del servicio meteorológico nacional, la página de tiempo representa la información meteorológica en su ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="62d26-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="62d26-145">Explorador Web</span><span class="sxs-lookup"><span data-stu-id="62d26-145">Web Browser</span></span>
<span data-ttu-id="62d26-146">El explorador web permite extraer la mayoría de los sitios de la web.</span><span class="sxs-lookup"><span data-stu-id="62d26-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="62d26-147">Música</span><span class="sxs-lookup"><span data-stu-id="62d26-147">Music</span></span>
<span data-ttu-id="62d26-148">Esta página reproducirá los archivos MP3 y WAV desde el **biblioteca de música**, que se puede acceder mediante el [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="62d26-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="62d26-149">Para cargar archivos en el Reproductor de música, deberá navegar a la de Windows Device Portal, haga clic en la lista desplegable de "Aplicaciones", vaya a "Explorador de archivos", seleccione "Música" y cargar los archivos a partir de ahí.</span><span class="sxs-lookup"><span data-stu-id="62d26-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="62d26-151">Presentación</span><span class="sxs-lookup"><span data-stu-id="62d26-151">Slideshow</span></span>
<span data-ttu-id="62d26-152">Esta página mostrará los archivos de imagen PNG o JPEG desde el **biblioteca imágenes**, que puede obtenerse a través de la [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="62d26-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="62d26-153">Para cargar imágenes en la presentación de diapositivas, deberá navegar a la de Windows Device Portal, haga clic en la lista desplegable de "Aplicaciones", vaya a "Explorador de archivos", seleccione "Imágenes" y cargar los archivos a partir de ahí.</span><span class="sxs-lookup"><span data-stu-id="62d26-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![Cómo cargar archivos de música](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="62d26-155">Dibujar</span><span class="sxs-lookup"><span data-stu-id="62d26-155">Draw</span></span>
<span data-ttu-id="62d26-156">Esta página permite probar las capacidades de Windows 10 IoT Core escritura a mano.</span><span class="sxs-lookup"><span data-stu-id="62d26-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="62d26-157">Menú - Inicio explorar</span><span class="sxs-lookup"><span data-stu-id="62d26-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="62d26-158">Aplicaciones</span><span class="sxs-lookup"><span data-stu-id="62d26-158">Apps</span></span> 
<span data-ttu-id="62d26-159">Esta página permite iniciar otras aplicaciones de primer plano instaladas en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="62d26-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="62d26-160">Iniciar una aplicación, se suspenderá IoT Core predeterminado aplicación, que puede ser una nueva versión mediante el Administrador de la aplicación en [Windows Device Portal](../manage-your-device/DevicePortal.md).</span><span class="sxs-lookup"><span data-stu-id="62d26-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="62d26-161">Se necesita nada especial para que la aplicación de primer plano que aparece en la página, simplemente [instalar](AppInstaller.md) o [implementar](AppDeployment.md) la aplicación.</span><span class="sxs-lookup"><span data-stu-id="62d26-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="62d26-162">Después de la correcta instalación o implementación, vuelva a navegar a la página de aplicaciones para actualizar la lista de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="62d26-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="62d26-163">Tenga en cuenta que existen un par de SO generado automáticamente relacionados con las aplicaciones que se filtran, puede encontrar la lista de nombres de aplicación [aquí](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span><span class="sxs-lookup"><span data-stu-id="62d26-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="62d26-164">Notificaciones</span><span class="sxs-lookup"><span data-stu-id="62d26-164">Notifications</span></span>
<span data-ttu-id="62d26-165">Esta página mostrará una lista de los últimos 20 notificaciones desde que se inició la aplicación predeterminada de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="62d26-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="62d26-166">Cuando la aplicación de IoT Core predeterminada se ejecuta en modo de depuración, se agregan botones que creará la prueba de las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="62d26-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="62d26-167">Registros</span><span class="sxs-lookup"><span data-stu-id="62d26-167">Logs</span></span>
<span data-ttu-id="62d26-168">Esta página mostrará cualquier automáticamente registros generados por el bloqueo o error, que, a continuación, pueden retirar el dispositivo y analizar.</span><span class="sxs-lookup"><span data-stu-id="62d26-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="62d26-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="62d26-169">GitHub</span></span>
<span data-ttu-id="62d26-170">Esta página le llevará a la ubicación de GitHub con código abierto del código de aplicación predeterminado de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="62d26-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="62d26-171">Menú - Inicio de Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="62d26-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="62d26-172">Las páginas de esta sección aprovechan las API de REST de Windows Device Portal, que requiere que inicie sesión con sus credenciales de Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="62d26-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="62d26-173">Información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="62d26-173">Device Information</span></span>

<span data-ttu-id="62d26-174">Esta página permite ver las distintas características del dispositivo incluyen Ethernet OS versión, los dispositivos conectados y mucho más.</span><span class="sxs-lookup"><span data-stu-id="62d26-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="62d26-175">Línea de comandos</span><span class="sxs-lookup"><span data-stu-id="62d26-175">Command Line</span></span>

<span data-ttu-id="62d26-176">Esta página permite ejecutar comandos directamente en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="62d26-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="62d26-177">Para habilitar esta característica que tiene que establecer una clave del registro para que la aplicación puede ejecutar los comandos.</span><span class="sxs-lookup"><span data-stu-id="62d26-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="62d26-178">La primera vez que intenta ejecutar un comando verá un vínculo que le permite establecer la clave del registro mediante una llamada a Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="62d26-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="62d26-179">Haga clic en el vínculo para habilitar el dispositivo ejecutar comandos.</span><span class="sxs-lookup"><span data-stu-id="62d26-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="62d26-180">Algunos comandos requieren acceso de administrador.</span><span class="sxs-lookup"><span data-stu-id="62d26-180">Some commands require administrator access.</span></span> <span data-ttu-id="62d26-181">Por motivos de seguridad la aplicación usa una cuenta sin derechos administrativos de forma predeterminada para ejecutar comandos.</span><span class="sxs-lookup"><span data-stu-id="62d26-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="62d26-182">Si necesita ejecutar un comando como un administrador puede escribir "RunAsAdmin <your command>" en el símbolo del sistema de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="62d26-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="62d26-183">Configuración</span><span class="sxs-lookup"><span data-stu-id="62d26-183">Settings</span></span>
<span data-ttu-id="62d26-184">Podrá configurar varias opciones de configuración incluidas aquí Wi-Fi, Bluetooth, opciones de energía y mucho más.</span><span class="sxs-lookup"><span data-stu-id="62d26-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="62d26-185">Configuración de la aplicación</span><span class="sxs-lookup"><span data-stu-id="62d26-185">App Settings</span></span>
<span data-ttu-id="62d26-186">El **configuración de la aplicación** sección permite configurar diversas opciones para las páginas en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="62d26-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="62d26-187">Algunas de las configuraciones que puede personalizar son:</span><span class="sxs-lookup"><span data-stu-id="62d26-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="62d26-188">Configuración general</span><span class="sxs-lookup"><span data-stu-id="62d26-188">General Settings</span></span>
* <span data-ttu-id="62d26-189">Establecer la página predeterminada que aparece cuando se inicia la aplicación</span><span class="sxs-lookup"><span data-stu-id="62d26-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="62d26-190">Habilitar o deshabilitar el protector de pantalla</span><span class="sxs-lookup"><span data-stu-id="62d26-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="62d26-191">Configuración de meteorología</span><span class="sxs-lookup"><span data-stu-id="62d26-191">Weather Settings</span></span>
* <span data-ttu-id="62d26-192">Cambiar la ubicación</span><span class="sxs-lookup"><span data-stu-id="62d26-192">Change the location</span></span>
  > <span data-ttu-id="62d26-193">Esta característica solo está habilitada si se ha proporcionado un válido [Bing mapa de servicio de Token](https://msdn.microsoft.com/library/ff428642.aspx).</span><span class="sxs-lookup"><span data-stu-id="62d26-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="62d26-194">Para pasar el token a la aplicación, cree un **MapToken.config** archivo en la carpeta LocalState de la aplicación (por ejemplo, C:\Data\USERS\\\AppData\Packages [cuenta de usuario]\\\LocalState\ [nombre completo del paquete] MapToken.config) y reinicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="62d26-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="62d26-195">Expanda el mapa</span><span class="sxs-lookup"><span data-stu-id="62d26-195">Expand the map</span></span>
* <span data-ttu-id="62d26-196">Habilitar o deshabilitar asignar Voltear para que el mapa y el conmutador meteorológicos coloca periódicamente para evitar la grabación en pantalla</span><span class="sxs-lookup"><span data-stu-id="62d26-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="62d26-197">Configuración del explorador Web</span><span class="sxs-lookup"><span data-stu-id="62d26-197">Web Browser Settings</span></span>
* <span data-ttu-id="62d26-198">Establecer la página principal del explorador Web</span><span class="sxs-lookup"><span data-stu-id="62d26-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="62d26-199">Configuración de presentación con diapositivas</span><span class="sxs-lookup"><span data-stu-id="62d26-199">Slideshow Settings</span></span>
* <span data-ttu-id="62d26-200">Establecer el intervalo de presentación con diapositivas</span><span class="sxs-lookup"><span data-stu-id="62d26-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="62d26-201">Apariencia</span><span class="sxs-lookup"><span data-stu-id="62d26-201">Appearance</span></span>
* <span data-ttu-id="62d26-202">Use MDL2 activos en lugar de Emojis para los iconos de mosaico</span><span class="sxs-lookup"><span data-stu-id="62d26-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="62d26-203">Establecer el icono ancho y alto</span><span class="sxs-lookup"><span data-stu-id="62d26-203">Set the tile width and height</span></span>
* <span data-ttu-id="62d26-204">Conjunto de escalado de la interfaz de usuario: el escalado automático se establece de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="62d26-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="62d26-205">Establecer el color del icono</span><span class="sxs-lookup"><span data-stu-id="62d26-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="62d26-206">Sistema</span><span class="sxs-lookup"><span data-stu-id="62d26-206">System</span></span>
<span data-ttu-id="62d26-207">Cambiar el idioma, la distribución del teclado y la zona horaria.</span><span class="sxs-lookup"><span data-stu-id="62d26-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="62d26-208">Red & Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="62d26-208">Network & Wi-Fi</span></span>
<span data-ttu-id="62d26-209">Ver propiedades del adaptador de red o conectarse a una red Wi-Fi disponible.</span><span class="sxs-lookup"><span data-stu-id="62d26-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="62d26-210">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="62d26-210">Bluetooth</span></span>
<span data-ttu-id="62d26-211">Emparejar con un dispositivo Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="62d26-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="62d26-212">Actualizaciones de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="62d26-212">App Updates</span></span>
<span data-ttu-id="62d26-213">Comprobar si hay actualizaciones de la aplicación o cambiar la configuración de actualización automática.</span><span class="sxs-lookup"><span data-stu-id="62d26-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="62d26-214">Opciones de energía</span><span class="sxs-lookup"><span data-stu-id="62d26-214">Power Options</span></span>
<span data-ttu-id="62d26-215">Reinicio o apagado del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="62d26-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="62d26-216">Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="62d26-216">Diagnostics</span></span>
<span data-ttu-id="62d26-217">Seleccione la cantidad de datos de diagnóstico que desea proporcionar a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="62d26-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="62d26-218">Le animamos a los usuarios participar en **completa** datos de diagnóstico para que podamos diagnosticar rápidamente problemas y realizar mejoras en el producto.</span><span class="sxs-lookup"><span data-stu-id="62d26-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="62d26-219">Básico</span><span class="sxs-lookup"><span data-stu-id="62d26-219">Basic</span></span> 
<span data-ttu-id="62d26-220">Enviar sólo información sobre el dispositivo, su configuración y capacidades, y si se realiza correctamente.</span><span class="sxs-lookup"><span data-stu-id="62d26-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="62d26-221">Completo</span><span class="sxs-lookup"><span data-stu-id="62d26-221">Full</span></span>
<span data-ttu-id="62d26-222">Enviar todos los datos de diagnóstico básicos, junto con información sobre los sitios Web que examina y cómo usar aplicaciones y características, además de información adicional sobre el estado del dispositivo, la actividad del dispositivo e informes de error mejorados.</span><span class="sxs-lookup"><span data-stu-id="62d26-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="62d26-223">Ubicación</span><span class="sxs-lookup"><span data-stu-id="62d26-223">Location</span></span>
<span data-ttu-id="62d26-224">Permitir o denegar el acceso a la aplicación a su ubicación.</span><span class="sxs-lookup"><span data-stu-id="62d26-224">Allow or deny the app access to your location.</span></span>
