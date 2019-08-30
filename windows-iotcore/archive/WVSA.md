---
title: Información general de las pantallas virtuales de Windows para Arduino
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Aprenda a configurar las pletinas virtuales de Windows para Arduino y a compilar su primera aplicación de Windows 10 IoT Core.
keywords: Windows IOT, WVSA, protección virtual de Windows, Arduino, aplicación
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169003"
---
> [!NOTE]
> <span data-ttu-id="95706-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="95706-104">You are viewing archived documentation.</span></span> <span data-ttu-id="95706-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="95706-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="95706-106">Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.</span><span class="sxs-lookup"><span data-stu-id="95706-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="95706-107">Configuración de escudos virtuales de Windows para Arduino</span><span class="sxs-lookup"><span data-stu-id="95706-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="95706-108">Información general</span><span class="sxs-lookup"><span data-stu-id="95706-108">Overview</span></span>
<span data-ttu-id="95706-109">Si ha usado un [Arduino](https://www.arduino.cc), está familiarizado con el concepto de un escudo.</span><span class="sxs-lookup"><span data-stu-id="95706-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="95706-110">Cada escudo tiene un propósito especializado (por ejemplo, un escudo de temperatura, una pletina de acelerómetro) y la creación de un dispositivo con varias pletinas puede ser compleja, costosa y poco eficiente de espacio.</span><span class="sxs-lookup"><span data-stu-id="95706-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="95706-111">Ahora Imagine que puede usar un teléfono de Windows Lumia de bajo costo como un conjunto compacto de escudos.</span><span class="sxs-lookup"><span data-stu-id="95706-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="95706-112">El boceto de Arduino podría tener acceso a cientos de dólares de recursos y capacidades en el Windows Phone a través de llamadas de biblioteca fáciles de usar.</span><span class="sxs-lookup"><span data-stu-id="95706-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="95706-113">Esto es exactamente lo que los blindajes virtuales de Windows para la biblioteca Arduino permite a los desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="95706-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="95706-114">Y eso no es lo mejor: esta tecnología funciona en todos los dispositivos de Windows 10, por lo que también puede usar los sensores y las capacidades en su PC o superficie.</span><span class="sxs-lookup"><span data-stu-id="95706-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="95706-115">Además, el Arduino puede descargar tareas caros computacionales, como el reconocimiento de voz y el análisis web, al dispositivo complementario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="95706-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="95706-116">Vamos a obtener información sobre cómo configurar el hardware y el software para trabajar con las pletinas virtuales de Windows para Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="95706-117">1. Preparar el dispositivo con Windows 10 para el desarrollo de proyectos con escudos virtuales de Windows para Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="95706-118">En esta sección del tutorial, va a preparar un dispositivo de Windows 10 de su elección mediante su carga en la aplicación de escudos virtuales de Windows para Arduino. esta aplicación universal de Windows permite usar el dispositivo como "escudo virtual" para una placa Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="95706-119">Esto da como resultado algunas posibilidades eficaces para los responsables de ti, permitiéndoles usar el reconocimiento de voz, pantallas táctiles y la potencia de cálculo de Windows con relativa facilidad.</span><span class="sxs-lookup"><span data-stu-id="95706-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="95706-120">Hardware</span><span class="sxs-lookup"><span data-stu-id="95706-120">Hardware</span></span>
<span data-ttu-id="95706-121">La aplicación de escudos virtuales de Windows para Arduino se puede ejecutar en cualquier dispositivo de Windows 10, pero en este tutorial se explicará el programa de instalación con un Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="95706-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="95706-122">*Lo que necesita* Windows Phone que ejecutan Windows 10, se recomienda usar [lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) o [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span><span class="sxs-lookup"><span data-stu-id="95706-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

<span data-ttu-id="95706-123">*Configurar el Windows Phone*</span><span class="sxs-lookup"><span data-stu-id="95706-123">*Set up your Windows Phone*</span></span>

<span data-ttu-id="95706-124">Si su teléfono no está ejecutando Windows 10, hay opciones para instalar versiones preliminares del software.</span><span class="sxs-lookup"><span data-stu-id="95706-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="95706-125">Windows Phone 8 usuarios pueden ir a la aplicación de Microsoft Store para descargar la aplicación "Windows Insider": esta aplicación permite al usuario participar en la recepción de las versiones preliminares técnicas de Windows 10 como actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="95706-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="95706-126">Siga las indicaciones y las instrucciones al abrir la aplicación y continúe una vez que el teléfono ejecute correctamente Windows 10.</span><span class="sxs-lookup"><span data-stu-id="95706-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="95706-127">Software</span><span class="sxs-lookup"><span data-stu-id="95706-127">Software</span></span>

<span data-ttu-id="95706-128">Hay dos opciones para instalar las pantallas virtuales de Windows para la aplicación Arduino para UWP en el Windows Phone.</span><span class="sxs-lookup"><span data-stu-id="95706-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="95706-129">Descargar la aplicación es la opción más fácil y rápida.</span><span class="sxs-lookup"><span data-stu-id="95706-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="95706-130">Descargue la aplicación desde el Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="95706-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="95706-131">Transferir localmente la aplicación con un PC y Visual Studio</span><span class="sxs-lookup"><span data-stu-id="95706-131">Sideload the app using a PC and Visual Studio</span></span>

<span data-ttu-id="95706-132">*Opción 1: Descargue la aplicación desde el Microsoft Store*</span><span class="sxs-lookup"><span data-stu-id="95706-132">*Option 1: Download the app from the Microsoft Store*</span></span>

<span data-ttu-id="95706-133">Siga este [vínculo](https://www.microsoft.com/store/apps/9nblgggz0mld) a la página Microsoft Store de las pantallas virtuales de Windows para Arduino, descargue la aplicación y, a continuación, instale.</span><span class="sxs-lookup"><span data-stu-id="95706-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="95706-134">Después, puede abrir la aplicación para asegurarse de que se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="95706-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="95706-135">El dispositivo ya está configurado para usarse como "escudo virtual" para un Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="95706-136">Puede pasar a la página siguiente.</span><span class="sxs-lookup"><span data-stu-id="95706-136">You can proceed to the next page.</span></span>

<span data-ttu-id="95706-137">*Opción 2: Transferir localmente la aplicación con un equipo y visual*Studio
_lo que necesita_</span><span class="sxs-lookup"><span data-stu-id="95706-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="95706-138">Visual Studio 2017 para transferir localmente las pletinas virtuales de Windows para la aplicación Arduino a un teléfono desbloqueado por el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="95706-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="95706-139">Este [repositorio](https://github.com/ms-iot/virtual-shields-universal) contiene el código para la aplicación de protección virtual de Windows para Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="95706-140">Clone el repositorio o descárguelo como un archivo ZIP en el disco local.</span><span class="sxs-lookup"><span data-stu-id="95706-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="95706-141">Si no está familiarizado con git y desea realizar un clon adecuado, siga las instrucciones que se indican [aquí](https://help.github.com/articles/cloning-a-repository).</span><span class="sxs-lookup"><span data-stu-id="95706-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

<span data-ttu-id="95706-142">_Configurar Visual Studio 2017_</span><span class="sxs-lookup"><span data-stu-id="95706-142">_Set up Visual Studio 2017_</span></span>
1. <span data-ttu-id="95706-143">Instale Visual Studio 2017 con las herramientas de vista previa de Windows 10 Developer desde [dev.Windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span><span class="sxs-lookup"><span data-stu-id="95706-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="95706-144">Se recomienda la versión gratuita de la comunidad de Visual Studio, pero tanto Enterprise como Professional funcionarán también.</span><span class="sxs-lookup"><span data-stu-id="95706-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="95706-145">Si ya tiene Visual Studio instalado, vaya al paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="95706-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="95706-146">En Visual Studio, cargue el Shield. sln del repositorio descargado en la sección "lo que necesita" anterior.</span><span class="sxs-lookup"><span data-stu-id="95706-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="95706-147">Asegúrese de que el dispositivo Windows 10 (en este caso, un Windows Phone) está desbloqueado por el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="95706-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="95706-148">En [esta página](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) se explica cómo desbloquear Windows Phone 8,1, 8 y 7,1; sin embargo, los pasos son los mismos para los teléfonos con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="95706-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="95706-149">Conecte el dispositivo Windows 10 al equipo e implemente el programa Shield. sln en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="95706-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="95706-150">Para ello, implemente en un "equipo local" y asegúrese de establecer la arquitectura del dispositivo como "ARM".</span><span class="sxs-lookup"><span data-stu-id="95706-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="95706-151">Ejecute los escudos virtuales de Windows recién instalados para la aplicación Arduino en el teléfono para asegurarse de que la implementación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="95706-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="95706-152">El dispositivo Windows 10 ya está configurado para usarse como escudo virtual.</span><span class="sxs-lookup"><span data-stu-id="95706-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="95706-153">2. Configuración de Arduino para usar las pletinas virtuales de Windows para la biblioteca de Arduino</span><span class="sxs-lookup"><span data-stu-id="95706-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="95706-154">Una vez que el dispositivo complementario de Windows 10 esté configurado correctamente, vamos a preparar el Arduino para usar las pletinas virtuales de Windows para la biblioteca de Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="95706-155">Puede establecer una conexión entre el Arduino y el "escudo virtual" de Windows 10 a través de USB, Bluetooth o Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="95706-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="95706-156">En este tutorial concreto se explicará cómo completar la instalación mediante una conexión Bluetooth, pero no dude en experimentar con las demás opciones.</span><span class="sxs-lookup"><span data-stu-id="95706-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="95706-157">Hardware</span><span class="sxs-lookup"><span data-stu-id="95706-157">Hardware</span></span>
<span data-ttu-id="95706-158">*Lo que necesita*</span><span class="sxs-lookup"><span data-stu-id="95706-158">*What you need*</span></span>
* <span data-ttu-id="95706-159">Arduino uno o dispositivo compatible</span><span class="sxs-lookup"><span data-stu-id="95706-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="95706-160">Conexión de hilos</span><span class="sxs-lookup"><span data-stu-id="95706-160">Connecting wires</span></span>
* <span data-ttu-id="95706-161">Un equipo que se usa para cargar los bocetos de Arduino</span><span class="sxs-lookup"><span data-stu-id="95706-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="95706-162">Estándar a a estándar B USB: necesario para cargar bocetos en el dispositivo Arduino</span><span class="sxs-lookup"><span data-stu-id="95706-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="95706-163">Opcional: Módulo Bluetooth: solo es necesario si decide conectarse mediante Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="95706-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="95706-164">Opcional: Módulo de Wi-Fi: solo es necesario si decide conectarse mediante Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="95706-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="95706-165">Configuración de Arduino</span><span class="sxs-lookup"><span data-stu-id="95706-165">Set up your Arduino</span></span>
* <span data-ttu-id="95706-166">Prepare el módulo Bluetooth si es necesario (es posible que el módulo Bluetooth deba tener encabezados soldados en él).</span><span class="sxs-lookup"><span data-stu-id="95706-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="95706-167">A excepción de lo que se indica a continuación, conecte el módulo Bluetooth a Arduino por [el diagrama de cableado](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span><span class="sxs-lookup"><span data-stu-id="95706-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="95706-168">Hay Use los pin 0 y 1 en lugar de 2 y 3:</span><span class="sxs-lookup"><span data-stu-id="95706-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="95706-169">La transmisión de Bluetooth debe conectarse al pin 0 (Arduino RX o RX0).</span><span class="sxs-lookup"><span data-stu-id="95706-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="95706-170">El RX de Bluetooth debe conectarse al pin 1 (Arduino TX o TX1).</span><span class="sxs-lookup"><span data-stu-id="95706-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="95706-171">Software</span><span class="sxs-lookup"><span data-stu-id="95706-171">Software</span></span>
<span data-ttu-id="95706-172">*Lo que necesita*</span><span class="sxs-lookup"><span data-stu-id="95706-172">*What you need*</span></span>
* <span data-ttu-id="95706-173">Arduino IDE 1,6 o superior</span><span class="sxs-lookup"><span data-stu-id="95706-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="95706-174">Biblioteca ArduinoJSON</span><span class="sxs-lookup"><span data-stu-id="95706-174">ArduinoJSON library</span></span>
* <span data-ttu-id="95706-175">[Este repositorio](https://github.com/ms-iot/virtual-shields-arduino), que contiene el boceto de ejemplo que se ejecutará en Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

<span data-ttu-id="95706-176">*Configuración del IDE de Arduino*</span><span class="sxs-lookup"><span data-stu-id="95706-176">*Set up your Arduino IDE*</span></span>
* <span data-ttu-id="95706-177">Descargue e instale el IDE de Arduino y, a continuación, inicie el programa.</span><span class="sxs-lookup"><span data-stu-id="95706-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="95706-178">Compruebe que tiene seleccionada la placa Arduino correcta en *herramientas > placa*.</span><span class="sxs-lookup"><span data-stu-id="95706-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="95706-179">Compruebe que tiene seleccionado el puerto COM correcto en *herramientas > puerto*.</span><span class="sxs-lookup"><span data-stu-id="95706-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="95706-180">El nombre del panel debe aparecer junto a cada opción, lo que facilita la elección de la opción correcta.</span><span class="sxs-lookup"><span data-stu-id="95706-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

<span data-ttu-id="95706-181">*Configuración de la biblioteca ArduinoJSON*</span><span class="sxs-lookup"><span data-stu-id="95706-181">*Set up the ArduinoJSON library*</span></span>
* <span data-ttu-id="95706-182">En el [repositorio de ArduinoJson](https://github.com/bblanchon/ArduinoJson), Clone el repositorio o descargue el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="95706-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="95706-183">Coloque todo el repositorio en la carpeta de bibliotecas (es `Documents\Arduino\libraries\ArduinoJson\`decir,).</span><span class="sxs-lookup"><span data-stu-id="95706-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

<span data-ttu-id="95706-184">*Configuración de las pletinas virtuales de Windows para la biblioteca Arduino*</span><span class="sxs-lookup"><span data-stu-id="95706-184">*Set up the Windows Virtual Shields for Arduino Library*</span></span>
* <span data-ttu-id="95706-185">Clone [este repositorio](https://github.com/ms-iot/virtual-shields-arduino) o descargue el archivo zip.</span><span class="sxs-lookup"><span data-stu-id="95706-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="95706-186">Si no está familiarizado con git y desea realizar un clon adecuado, siga las instrucciones que se indican [aquí](https://help.github.com/articles/cloning-a-repository/).</span><span class="sxs-lookup"><span data-stu-id="95706-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="95706-187">Copie la carpeta "VirtualShield", que se encuentra en la carpeta "Arduino\Libraries" del repositorio que acaba de descargar, en la carpeta de la biblioteca `Documents\Arduino\libraries\VirtualShield\`de Arduino (es decir,).</span><span class="sxs-lookup"><span data-stu-id="95706-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

<span data-ttu-id="95706-188">*Prueba de la configuración*</span><span class="sxs-lookup"><span data-stu-id="95706-188">*Test your setup*</span></span>
* <span data-ttu-id="95706-189">En el IDE de Arduino, vaya al elemento de menú *File-> examples-> virtual Shield-> HelloWorld-Speech-Eventing*.</span><span class="sxs-lookup"><span data-stu-id="95706-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="95706-190">Esto debe cargar el ejemplo de reconocimiento de voz basado Hola mundo que estamos usando para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="95706-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="95706-191">Antes de cargar el boceto en el Arduino, quite temporalmente los cables TX y RX de Bluetooth de la Arduino (solo hay un puerto serie compartido entre el USB y Bluetooth: el Bluetooth interfiere con la carga).</span><span class="sxs-lookup"><span data-stu-id="95706-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="95706-192">Cargue el boceto presionando el botón "cargar" en el IDE.</span><span class="sxs-lookup"><span data-stu-id="95706-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="95706-193">Reemplace los cables TX y RX de Bluetooth a los pin de Arduino (TX de Bluetooth a Arduino RX (o RX0) y RX de Bluetooth a Arduino TX o (TX1)).</span><span class="sxs-lookup"><span data-stu-id="95706-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="95706-194">En el teléfono (u otro dispositivo de Windows) preparado en la página anterior, empareje con el dispositivo Bluetooth en el Arduino de configuración de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="95706-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="95706-195">Si usa BlueSMiRF, el código PIN predeterminado es 1234.</span><span class="sxs-lookup"><span data-stu-id="95706-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="95706-196">La luz roja parpadeante en el BlueSMiRF continúa parpadeando en rojo después de un emparejamiento correcto.</span><span class="sxs-lookup"><span data-stu-id="95706-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="95706-197">Esto es de esperar.</span><span class="sxs-lookup"><span data-stu-id="95706-197">This is expected.</span></span> <span data-ttu-id="95706-198">Solo se vuelve verde después de conectarse a la aplicación de protección virtual de Windows para Arduino.</span><span class="sxs-lookup"><span data-stu-id="95706-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="95706-199">3. Escriba su primera aplicación: ¡ Hola, parpadeo!</span><span class="sxs-lookup"><span data-stu-id="95706-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="95706-200">Hola mundo ejemplo de LED habilitado para voz</span><span class="sxs-lookup"><span data-stu-id="95706-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="95706-201">Con su Windows Phone (o potencialmente cualquier dispositivo de Windows 10) y su Arduino preparado tal y como se detallan en los pasos anteriores de este tutorial, ya está listo para probar el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="95706-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="95706-202">Prepare la placa de Arduino enlazando un LED con una resistencia al vástago 8.</span><span class="sxs-lookup"><span data-stu-id="95706-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="95706-203">Asegúrese de que el Arduino todavía se carga con el ejemplo HelloWorld-Speech-Eventing y, a continuación, conecte el Arduino a una fuente de alimentación.</span><span class="sxs-lookup"><span data-stu-id="95706-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="95706-204">Ejecute la aplicación de protección virtual de Windows para Arduino en el Windows Phone que preparó previamente.</span><span class="sxs-lookup"><span data-stu-id="95706-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="95706-205">Si todo se ha configurado correctamente, el teléfono debe conectarse al boceto de Arduino y le agradecemos la señal de audio.</span><span class="sxs-lookup"><span data-stu-id="95706-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="95706-206">Ahora puede decir "activado" u "desactivado" en el dispositivo Windows 10 para cambiar el LED en el Arduino entre on y OFF.</span><span class="sxs-lookup"><span data-stu-id="95706-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="95706-207">Boceto del cableado de Arduino: Ejemplo de Hola mundo</span><span class="sxs-lookup"><span data-stu-id="95706-207">Arduino Wiring Sketch: Hello World example</span></span>

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


