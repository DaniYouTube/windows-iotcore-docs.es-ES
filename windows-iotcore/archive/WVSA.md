---
title: Shields Virtual de Windows para la introducción a Arduino
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Aprenda a configurar Windows Virtual Shields de Arduino y construya su primera aplicación de Windows 10 IoT Core.
keywords: aplicación de Windows Virtual Shields, Arduino, iot, WVSA, de Windows
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514688"
---
> [!NOTE]
> <span data-ttu-id="2ef0b-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-104">You are viewing archived documentation.</span></span> <span data-ttu-id="2ef0b-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="2ef0b-106">Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="2ef0b-107">Configurar Windows Virtual Shields de Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="2ef0b-108">Información general</span><span class="sxs-lookup"><span data-stu-id="2ef0b-108">Overview</span></span>
<span data-ttu-id="2ef0b-109">Si ha usado un [Arduino](https://www.arduino.cc), está familiarizado con el concepto de un icono de escudo.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="2ef0b-110">Cada icono de escudo tiene una finalidad especializada (por ejemplo, una temperatura shield, un icono de escudo de acelerómetro) y creación de un dispositivo con varios shields puede ser complejo, costoso y espacio ineficaz.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="2ef0b-111">Ahora Imagínese que puede usar un teléfono Lumia de Windows de bajo costo como un conjunto compacto de shields.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="2ef0b-112">El boceto de Arduino podrán tener acceso a cientos de dólares de sensores y capacidades en su Windows Phone a través de llamadas a bibliotecas de fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="2ef0b-113">Esto es exactamente lo que permite la Shields Virtual de Windows para la biblioteca de Arduino para desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="2ef0b-114">Y no es la mejor parte: esta tecnología funciona en todos los dispositivos Windows 10, para que pueda usar las capacidades y los sensores en un equipo o la superficie también.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="2ef0b-115">Además, Arduino puede descargar tareas consumen muchos recursos, como el reconocimiento de voz y web de análisis para el dispositivo complementario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="2ef0b-116">Vamos a aprender a configurar el hardware y software para trabajar con Windows Virtual Shields de Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="2ef0b-117">1. Preparar el dispositivo Windows 10 para desarrollar proyectos que usan Windows Virtual Shields de Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="2ef0b-118">En esta sección del tutorial, se preparará un dispositivo Windows 10 de su elección, cargue los Shields Virtual de Windows para la aplicación de Arduino: esta aplicación Universal de Windows permite usar el dispositivo como un "escudo virtual" para una placa de Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="2ef0b-119">Algunas posibilidades poderosas para responsables de decisiones, lo que les permite usar el reconocimiento de voz, el resultado tocar las pantallas y la potencia de cálculo de Windows con relativa facilidad.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="2ef0b-120">Hardware</span><span class="sxs-lookup"><span data-stu-id="2ef0b-120">Hardware</span></span>
<span data-ttu-id="2ef0b-121">Puede ejecutar los Shields Virtual de Windows para la aplicación de Arduino en cualquier dispositivo Windows 10, pero en este tutorial se explica el programa de instalación con un Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="2ef0b-122">*Lo que necesita* Windows Phone que ejecutan Windows 10 - se recomienda la [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) o [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

*<span data-ttu-id="2ef0b-123">Configurar su Windows Phone</span><span class="sxs-lookup"><span data-stu-id="2ef0b-123">Set up your Windows Phone</span></span>*

<span data-ttu-id="2ef0b-124">Si el teléfono no se está ejecutando Windows 10, hay opciones para instalar las versiones preliminares del software.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="2ef0b-125">Los usuarios de Windows Phone 8 pueden ir a la aplicación de Microsoft Store para descargar la aplicación de "Windows Insider": esta aplicación permite al usuario optar por recibir Windows 10 Technical Preview como las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="2ef0b-126">Siga las indicaciones e instrucciones al abrir la aplicación y seguir una vez que el teléfono ejecuta correctamente en Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="2ef0b-127">Software</span><span class="sxs-lookup"><span data-stu-id="2ef0b-127">Software</span></span>

<span data-ttu-id="2ef0b-128">Hay dos opciones para instalar los Shields Virtual de Windows para la aplicación de UWP de Arduino en su Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="2ef0b-129">Descargar la aplicación es la opción más fácil y rápida.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="2ef0b-130">Descargar la aplicación desde la Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="2ef0b-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="2ef0b-131">Transferir localmente la aplicación utiliza un PC y Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ef0b-131">Sideload the app using a PC and Visual Studio</span></span>

*<span data-ttu-id="2ef0b-132">Opción 1: Descargar la aplicación desde la Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="2ef0b-132">Option 1: Download the app from the Microsoft Store</span></span>*

<span data-ttu-id="2ef0b-133">Siga este [vínculo](https://www.microsoft.com/store/apps/9nblgggz0mld) a la página de Microsoft Store para Shields Virtual de Windows para Arduino, descargue la aplicación y, a continuación, instalar.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="2ef0b-134">A continuación, puede abrir la aplicación para asegurarse de que se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="2ef0b-135">El dispositivo ahora está configurado para utilizarse como un "escudo virtual" para Arduino!</span><span class="sxs-lookup"><span data-stu-id="2ef0b-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="2ef0b-136">Puede continuar a la página siguiente.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-136">You can proceed to the next page.</span></span>

<span data-ttu-id="2ef0b-137">*Opción 2: Transferir localmente la aplicación utiliza un PC y Visual Studio*
_lo que necesita_</span><span class="sxs-lookup"><span data-stu-id="2ef0b-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="2ef0b-138">Visual Studio 2017 para transferir localmente la Shields Virtual de Windows para la aplicación de Arduino en un teléfono desbloqueado por el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="2ef0b-139">Esto [repositorio](https://github.com/ms-iot/virtual-shields-universal) que contiene el código para los Shields Virtual de Windows para la aplicación de Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="2ef0b-140">Clone el repositorio o descargarlo como un archivo ZIP en el disco local.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="2ef0b-141">Si no está familiarizado con git y realizar un clon adecuado, siga las instrucciones [aquí](https://help.github.com/articles/cloning-a-repository).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

_<span data-ttu-id="2ef0b-142">Configurar Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2ef0b-142">Set up Visual Studio 2017</span></span>_
1. <span data-ttu-id="2ef0b-143">Instalar Visual Studio 2017 con las herramientas de vista previa de Windows 10 para desarrolladores de [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="2ef0b-144">Se recomienda la gratuita Community versión de Visual Studio, pero Enterprise y Professional también funcionan correctamente.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="2ef0b-145">Si ya tiene instalado Visual Studio, vaya al paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="2ef0b-146">En Visual Studio carga el Shield.sln desde el repositorio se descargó en el "lo que necesita" sección anterior.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="2ef0b-147">Asegúrese de que el dispositivo Windows 10 (en este caso un Windows Phone) es el desbloqueo de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="2ef0b-148">[Esta página](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explica cómo desbloquear Windows Phone 8.1, 8 y 7.1; sin embargo, los pasos son los mismos para teléfonos con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="2ef0b-149">Conecte su dispositivo Windows 10 en su equipo e implementar el programa Shield.sln al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="2ef0b-150">Para ello, implemente en un "equipo Local" y asegúrese de establecer la arquitectura del dispositivo como "ARM".</span><span class="sxs-lookup"><span data-stu-id="2ef0b-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="2ef0b-151">Ejecute recién instalado Shields Virtual de Windows para la aplicación de Arduino en el teléfono para garantizar la implementación fue correcta.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="2ef0b-152">El dispositivo Windows 10 ahora está configurado para utilizarse como un icono de escudo virtual!</span><span class="sxs-lookup"><span data-stu-id="2ef0b-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="2ef0b-153">2. Configurar su Arduino para usar los Shields Virtual de Windows para la biblioteca de Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="2ef0b-154">Con nuestro dispositivo complementario de Windows 10 correctamente configurado, vamos a nuestra Arduino listo para usar los Shields Virtual de Windows para la biblioteca de Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="2ef0b-155">Puede establecer una conexión entre su Arduino y Windows 10 "virtual escudo" a través de Wi-Fi, Bluetooth o USB.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="2ef0b-156">En este tutorial particular se explica cómo completar la instalación mediante una conexión Bluetooth, pero no dude en experimentar con las otras opciones.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="2ef0b-157">Hardware</span><span class="sxs-lookup"><span data-stu-id="2ef0b-157">Hardware</span></span>
*<span data-ttu-id="2ef0b-158">Lo que necesita</span><span class="sxs-lookup"><span data-stu-id="2ef0b-158">What you need</span></span>*
* <span data-ttu-id="2ef0b-159">Arduino Uno u otro dispositivo compatible</span><span class="sxs-lookup"><span data-stu-id="2ef0b-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="2ef0b-160">Cables de conexión</span><span class="sxs-lookup"><span data-stu-id="2ef0b-160">Connecting wires</span></span>
* <span data-ttu-id="2ef0b-161">Un equipo que se use para cargar los bocetos de Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="2ef0b-162">Estándar A estándar USB B - necesario para cargar dibujos en el dispositivo de Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="2ef0b-163">Opcional: Módulo de Bluetooth: solo es necesario si decide conectar mediante Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="2ef0b-164">Opcional: Módulo de Wi-fi: solo es necesario si decide conectar mediante wi-fi.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="2ef0b-165">Configurar su Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-165">Set up your Arduino</span></span>
* <span data-ttu-id="2ef0b-166">Si es necesario (el módulo de Bluetooth que deba tener encabezados soldados en él), prepare el módulo de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="2ef0b-167">Excepto el otro se indica a continuación, conectado el módulo de Bluetooth a Arduino por [el diagrama de cableado](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="2ef0b-168">Diferencia: Usar el PIN 0 y 1 en lugar de 2 y 3:</span><span class="sxs-lookup"><span data-stu-id="2ef0b-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="2ef0b-169">TX Bluetooth debe conectarse a la clavija de 0 (RX de Arduino o RX0).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="2ef0b-170">Debe conectar RX de Bluetooth del pin 1 (TX de Arduino o TX1).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="2ef0b-171">Software</span><span class="sxs-lookup"><span data-stu-id="2ef0b-171">Software</span></span>
*<span data-ttu-id="2ef0b-172">Lo que necesita</span><span class="sxs-lookup"><span data-stu-id="2ef0b-172">What you need</span></span>*
* <span data-ttu-id="2ef0b-173">Arduino IDE 1.6 o superior</span><span class="sxs-lookup"><span data-stu-id="2ef0b-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="2ef0b-174">Biblioteca ArduinoJSON</span><span class="sxs-lookup"><span data-stu-id="2ef0b-174">ArduinoJSON library</span></span>
* <span data-ttu-id="2ef0b-175">[Este repositorio](https://github.com/ms-iot/virtual-shields-arduino), que contiene el boceto de ejemplo que se ejecutará en Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

*<span data-ttu-id="2ef0b-176">Configurar el IDE de Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-176">Set up your Arduino IDE</span></span>*
* <span data-ttu-id="2ef0b-177">Descargue e instale el IDE de Arduino, inicie el programa.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="2ef0b-178">Compruebe que dispone de la placa de Arduino correcta seleccionada en *Herramientas > panel*.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="2ef0b-179">Compruebe que tiene el puerto COM correcto seleccionado en *Herramientas > puerto*.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="2ef0b-180">El nombre del panel debe aparecer junto a cada opción, lo que facilita a elegir la opción correcta.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

*<span data-ttu-id="2ef0b-181">Configurar la biblioteca ArduinoJSON</span><span class="sxs-lookup"><span data-stu-id="2ef0b-181">Set up the ArduinoJSON library</span></span>*
* <span data-ttu-id="2ef0b-182">Desde el [ArduinoJson repositorio](https://github.com/bblanchon/ArduinoJson), clone el repositorio o descargue el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="2ef0b-183">Colocar el repositorio completo en la carpeta de bibliotecas (es decir, `Documents\Arduino\libraries\ArduinoJson\`).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

*<span data-ttu-id="2ef0b-184">Configurar los Shields Virtual de Windows para la biblioteca de Arduino</span><span class="sxs-lookup"><span data-stu-id="2ef0b-184">Set up the Windows Virtual Shields for Arduino Library</span></span>*
* <span data-ttu-id="2ef0b-185">Clon [este repositorio](https://github.com/ms-iot/virtual-shields-arduino) o descargue el archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="2ef0b-186">Si no está familiarizado con git y realizar un clon adecuado, siga las instrucciones [aquí](https://help.github.com/articles/cloning-a-repository/).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="2ef0b-187">Copie la carpeta "VirtualShield", que se encuentra en la carpeta "Arduino\Libraries" del repositorio que acaba de descargar, a la carpeta de biblioteca de Arduino (es decir, `Documents\Arduino\libraries\VirtualShield\`).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

*<span data-ttu-id="2ef0b-188">Probar la configuración</span><span class="sxs-lookup"><span data-stu-id="2ef0b-188">Test your setup</span></span>*
* <span data-ttu-id="2ef0b-189">En el IDE de Arduino, vaya al elemento de menú *archivo -> ejemplos -> Virtual escudo -> HelloWorld de voz-eventos*.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="2ef0b-190">Esto debería cargar en el ejemplo de Hello World en función de reconocimiento de voz, que vamos a usar para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="2ef0b-191">Antes de cargar el boceto a su Arduino, quitar temporalmente los cables Bluetooth TX y RX de Arduino (solo hay un puerto serie que se comparte entre el USB y Bluetooth, el Bluetooth interfiere con la carga).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="2ef0b-192">Carga del boceto presionando el botón "Cargar" en el IDE.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="2ef0b-193">Reemplace los cables Bluetooth TX y RX en las clavijas de Arduino (Bluetooth RX para Arduino TX y Bluetooth TX Arduino RX (o RX0) o (TX1)).</span><span class="sxs-lookup"><span data-stu-id="2ef0b-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="2ef0b-194">En el teléfono (u otro dispositivo de Windows) preparado en la página anterior, emparejar con el dispositivo Bluetooth en su Arduino en la configuración de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="2ef0b-195">Si usas el BlueSMiRF, el código pin predeterminado es 1234.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="2ef0b-196">La luz roja parpadeante en la BlueSMiRF continúa hacer parpadear rojo después de un emparejamiento correcto.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="2ef0b-197">Esto es de esperar.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-197">This is expected.</span></span> <span data-ttu-id="2ef0b-198">Solo se vuelve verde después de una conexión con los Shields Virtual de Windows para la aplicación de Arduino.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="2ef0b-199">3. Escribir su primera aplicación: Hola llamativa.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="2ef0b-200">Ejemplo de Hola mundo compatibles con voz LED</span><span class="sxs-lookup"><span data-stu-id="2ef0b-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="2ef0b-201">Con su Windows Phone (o potencialmente a cualquier dispositivo de Windows 10) y su Arduino preparada tal como se detalla en los pasos anteriores de este tutorial, ahora está listo para probar nuestro ejemplo.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="2ef0b-202">Preparar la placa de Arduino para conectar un LED con una resistencia a la clavija de 8.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="2ef0b-203">Asegúrese de que su Arduino todavía se carga con el ejemplo HelloWorld de voz-eventos y, a continuación, conecte el Arduino en una fuente de alimentación.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="2ef0b-204">Ejecute los Shields Virtual de Windows para la aplicación de Arduino en el Windows Phone que preparó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="2ef0b-205">Si todo ha correctamente el programa de instalación, el teléfono debe conectar con el boceto de Arduino y le damos la bienvenida con una indicación de audio.</span><span class="sxs-lookup"><span data-stu-id="2ef0b-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="2ef0b-206">Ahora puede decir 'on' u 'off' en el dispositivo Windows 10 para pasar el LED en su Arduino y desactivar!</span><span class="sxs-lookup"><span data-stu-id="2ef0b-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="2ef0b-207">El cableado de boceto de Arduino: Hello World, ejemplo</span><span class="sxs-lookup"><span data-stu-id="2ef0b-207">Arduino Wiring Sketch: Hello World example</span></span>

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


