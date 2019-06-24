---
title: Introducción al Shell de IoT
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo aprovechar el IoT Shell para navegar entre navegaciones en el dispositivo.
keywords: Windows iot, IoT core shell, las aplicaciones, aplicaciones de primer plano, aplicaciones en segundo plano
ms.openlocfilehash: 74d8406036aa18dc5f8dcaa871e116eb7f8ec29b
ms.sourcegitcommit: beed912a2266d6dbc06a8a26b85ff49f1feffd69
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2019
ms.locfileid: "67316625"
---
# <a name="iot-shell-overview"></a><span data-ttu-id="9e508-104">Introducción al Shell de IoT</span><span class="sxs-lookup"><span data-stu-id="9e508-104">IoT Shell Overview</span></span>

<span data-ttu-id="9e508-105">Este documento describe las aplicaciones de IoT Shell, primer y segundo plano y cómo navegar entre estas aplicaciones en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e508-105">This document covers the IoT Shell, foreground and background applications, and how to navigate between these applications on your device.</span></span>

## <a name="iot-shell-foreground-and-background-apps"></a><span data-ttu-id="9e508-106">Shell de IoT, primer plano y aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="9e508-106">IoT Shell, Foreground, and Background Apps</span></span>

<span data-ttu-id="9e508-107">El dispositivo de IoT Core ejecuta el IoT Shell.</span><span class="sxs-lookup"><span data-stu-id="9e508-107">Your IoT Core device runs the IoT Shell.</span></span> <span data-ttu-id="9e508-108">Tiene muchas responsabilidades, pero su trabajo principal consiste en asegurarse de que se inician las aplicaciones de inicio registrados.</span><span class="sxs-lookup"><span data-stu-id="9e508-108">It has many responsibilities, but its primary job is to make sure registered startup apps are launched.</span></span> <span data-ttu-id="9e508-109">Tiene dos modos: Puntas y sin periféricos.</span><span class="sxs-lookup"><span data-stu-id="9e508-109">It has two modes: Headed and Headless.</span></span> <span data-ttu-id="9e508-110">En el modo de Headed, el IoT Shell se iniciará una aplicación de inicio registrados único que se mostrará su interfaz de usuario en pantalla completa (también conocido como una aplicación Headed).</span><span class="sxs-lookup"><span data-stu-id="9e508-110">In Headed mode, the IoT Shell will launch a single registered startup app that will show its UI in full screen (also known as a Headed app).</span></span> <span data-ttu-id="9e508-111">Modo con cabezal supone que tiene una pantalla conectada y muestra la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e508-111">Headed mode assumes you have a screen connected and shows UI.</span></span> <span data-ttu-id="9e508-112">En el modo "desatendido" (se explica en detalle [aquí](../learn-about-hardware/HeadlessMode.md)), no hay ninguna interfaz de usuario; solo las aplicaciones en segundo plano se inicia el IoT Shell.</span><span class="sxs-lookup"><span data-stu-id="9e508-112">In Headless mode (explained in detail [here](../learn-about-hardware/HeadlessMode.md)), there is no UI; the IoT Shell launches background applications only.</span></span>

<span data-ttu-id="9e508-113">Estas son las principales diferencias entre las aplicaciones de primer y segundo plano:</span><span class="sxs-lookup"><span data-stu-id="9e508-113">Here are the main differences between foreground and background applications:</span></span>

- <span data-ttu-id="9e508-114">**Las aplicaciones de primer plano** tiene una interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e508-114">**Foreground applications** have a UI.</span></span> <span data-ttu-id="9e508-115">Uno de ellos se inicia en el inicio cuando el dispositivo está en modo con cabezal.</span><span class="sxs-lookup"><span data-stu-id="9e508-115">One of these is launched at startup when the device is in headed mode.</span></span> <span data-ttu-id="9e508-116">Todas las aplicaciones de primer plano se registran en el dispositivo y el usuario puede cambiar entre las aplicaciones de primer plano durante la operación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e508-116">All foreground apps are registered on the device and the user can switch between foreground apps during device operation.</span></span>

- <span data-ttu-id="9e508-117">**En segundo plano aplicaciones** no tiene ninguna interfaz de usuario y, por tanto, guardar los recursos de dispositivo mediante la desactivación de la pila de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e508-117">**Background applications** have no UI and thus save device resources by turning off the UI stack.</span></span> <span data-ttu-id="9e508-118">Aplicaciones en segundo plano a menudo ejecutan continuamente a partir del inicio y a menudo se utilizan para supervisar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9e508-118">Background applications often run continuously from startup and are often used to monitor the device.</span></span>

## <a name="switching-between-apps-with-a-home-app"></a><span data-ttu-id="9e508-119">Cambiar entre las aplicaciones con una aplicación de inicio</span><span class="sxs-lookup"><span data-stu-id="9e508-119">Switching between apps with a Home App</span></span>

<span data-ttu-id="9e508-120">En este momento, la aplicación de inicio permite crear una aplicación principal para Windows 10 IoT Core, que le permite cambiar entre las aplicaciones de primer plano diferentes.</span><span class="sxs-lookup"><span data-stu-id="9e508-120">At the moment, the Startup App allows you to create a home app for Windows 10 IoT Core, which allows you to switch between different foreground applications.</span></span> 

<span data-ttu-id="9e508-121">El **aplicación de inicio de IoT** ([ejemplo](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) representa una aplicación de inicio simple que enumera las aplicaciones instaladas en el dispositivo y, después, inicia una mediante las APIs PackageManager.</span><span class="sxs-lookup"><span data-stu-id="9e508-121">The **IoT Startup App** ([sample](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) represents a simple startup app that lists the installed apps on your device, then launches one using the PackageManager APIs.</span></span>

## <a name="switching-between-apps-with-hid-injection-keys"></a><span data-ttu-id="9e508-122">Cambiar entre las aplicaciones con las claves de inserción de HID</span><span class="sxs-lookup"><span data-stu-id="9e508-122">Switching between apps with HID Injection Keys</span></span>

<span data-ttu-id="9e508-123">Las instrucciones siguientes muestran cómo activar la compatibilidad con teclas de acceso rápido a través de entradas en el registro.</span><span class="sxs-lookup"><span data-stu-id="9e508-123">The below instructions show you how to turn on Hotkey support through entries to the registry.</span></span> <span data-ttu-id="9e508-124">Si está creando su propia imagen y para admitir la debajo de teclas de acceso rápido (principal, la aplicación anterior y siguiente aplicación) sin necesidad de tener acceso al registro, puede incluir un paquete de la característica opcional que controla estos pasos para usted.</span><span class="sxs-lookup"><span data-stu-id="9e508-124">If you are building your own image and want to support the below hotkeys (Home, previous app, and next app) without needing to access the registry, you can include an optional feature package that handles these steps for you.</span></span>

<span data-ttu-id="9e508-125">Se llama para buscar el paquete de características: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** y la característica se denomina **IOT_SHELL_HOTKEY_SUPPORT**.</span><span class="sxs-lookup"><span data-stu-id="9e508-125">The feature package to look for is called: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** and the feature is called **IOT_SHELL_HOTKEY_SUPPORT**.</span></span> <span data-ttu-id="9e508-126">Consulte la [paquete de ejemplo Settings.HotKey](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) para obtener un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="9e508-126">See the [Settings.HotKey sample package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) for an example.</span></span>

<span data-ttu-id="9e508-127">El resto de este documento explica cómo implementar manualmente esta característica.</span><span class="sxs-lookup"><span data-stu-id="9e508-127">The rest of this document covers how to implement this feature manually.</span></span>

### <a name="return-home"></a><span data-ttu-id="9e508-128">Página principal de retorno</span><span class="sxs-lookup"><span data-stu-id="9e508-128">Return Home</span></span>

<span data-ttu-id="9e508-129">Con Windows 10 IoT Anniversary Update (1607), el IoT Shell admite traer la ventana de la aplicación de forma predeterminada al primer plano cuando se está ejecutando otra aplicación al presionar la tecla "GO HOME", que se establece en la versión de Windows en el botón un teclado.</span><span class="sxs-lookup"><span data-stu-id="9e508-129">With the Windows 10 IoT Anniversary Update (1607), the IoT Shell supports bringing the default application window to the foreground when another application is running by pressing the "GO HOME" key, which is set to the release of the Windows Button on a keyboard.</span></span> <span data-ttu-id="9e508-130">Si no tiene un teclado en el dispositivo de IoT y necesite insertar eventos de teclado de bajo nivel a través de [HID inyección](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), o si desea volver a asignar la funcionalidad "GO HOME" a una clave diferente en la aplicación, puede ajustar el valor de clave en el registro.</span><span class="sxs-lookup"><span data-stu-id="9e508-130">If you don't have a keyboard on your IoT Device and need to inject low-level keyboard events through [HID Injection](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), or if you just want to re-map the "GO HOME" functionality to a different key in your app, you can adjust the key value in the registry.</span></span> <span data-ttu-id="9e508-131">Por ejemplo, para habilitar al presionar el ESCAPE de clave (0x1B) a "GO HOME", escriba el siguiente comando en el registro:</span><span class="sxs-lookup"><span data-stu-id="9e508-131">For example, to enable pressing the ESCAPE key (0x1B) to "GO HOME", enter the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

<span data-ttu-id="9e508-132">Como un archivo de registro, esto tiene el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="9e508-132">As a REG file, this looks as follows:</span></span>

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a><span data-ttu-id="9e508-133">Cambiar entre las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="9e508-133">Switch Between Apps</span></span>

<span data-ttu-id="9e508-134">Como alternativa, si desea cambiar entre las aplicaciones de primer plano, puede configurar ALT+TAB (próxima aplicación) y la funcionalidad de Alt-Mayús-Tab (aplicación anterior) en la imagen, escriba el comando siguiente en el registro:</span><span class="sxs-lookup"><span data-stu-id="9e508-134">Alternatively, if you want to switch between your foreground apps, you can set up Alt-Tab (next app) and Shift-Alt-Tab (previous app) functionality in your image by entering the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

<span data-ttu-id="9e508-135">Como un archivo de registro, esto tiene el aspecto siguiente: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span><span class="sxs-lookup"><span data-stu-id="9e508-135">As a REG file, this looks as follows: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span></span>

### <a name="bit-translation"></a><span data-ttu-id="9e508-136">Bit Translation</span><span class="sxs-lookup"><span data-stu-id="9e508-136">Bit Translation</span></span>

<span data-ttu-id="9e508-137">Las entradas anteriores del archivo REG descodificación de izquierda a derecha como sigue:</span><span class="sxs-lookup"><span data-stu-id="9e508-137">The above REG file entries decode left to right as follows:</span></span>

- <span data-ttu-id="9e508-138">Bits 0-15: Código de tecla virtual (es decir, 1B, 00 para ESCAPE).</span><span class="sxs-lookup"><span data-stu-id="9e508-138">Bits 0-15: Virtual Key Code (i.e. 1B,00 for ESCAPE).</span></span> <span data-ttu-id="9e508-139">Consulte [código de tecla Virtual](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) para una lista completa de los valores de código de tecla</span><span class="sxs-lookup"><span data-stu-id="9e508-139">See [Virtual Key Code](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) for the complete list of key code values</span></span>
- <span data-ttu-id="9e508-140">19 de 16 bits: Tecla modificadora.</span><span class="sxs-lookup"><span data-stu-id="9e508-140">Bits 16-19: Modifier Key.</span></span> <span data-ttu-id="9e508-141">0 x 0 no = ningún modificador, 0 x 1 = ALT, 0 x 2 = CTRL y 0 x 4 = MAYÚS.</span><span class="sxs-lookup"><span data-stu-id="9e508-141">0x0 = No Modifier, 0x1 = ALT, 0x2 = CTRL, and 0x4 = SHIFT.</span></span> <span data-ttu-id="9e508-142">Combinación de teclas suma los valores (es decir, ALT + MAYÚS es 0 x 5)</span><span class="sxs-lookup"><span data-stu-id="9e508-142">Combining keys adds the values together (i.e. ALT+SHIFT is 0x5)</span></span>
- <span data-ttu-id="9e508-143">Bits de 20: 47: Reservado para uso futuro; debe ser 0</span><span class="sxs-lookup"><span data-stu-id="9e508-143">Bits 20-47: Reserved for future use; must be 0</span></span>
- <span data-ttu-id="9e508-144">62 de 48 bits:  Acción</span><span class="sxs-lookup"><span data-stu-id="9e508-144">Bits 48-62:  Action</span></span>
    - <span data-ttu-id="9e508-145">0 = Inicio</span><span class="sxs-lookup"><span data-stu-id="9e508-145">0 = Home</span></span>
    - <span data-ttu-id="9e508-146">1 = la vista anterior (no funcionen en futuras versiones)</span><span class="sxs-lookup"><span data-stu-id="9e508-146">1 = Previous View (may not work in future releases)</span></span>
    - <span data-ttu-id="9e508-147">2 = vista siguiente (no funcionen en futuras versiones)</span><span class="sxs-lookup"><span data-stu-id="9e508-147">2 = Next View (may not work in future releases)</span></span>
- <span data-ttu-id="9e508-148">Bit 63: Reservado; debe ser 0</span><span class="sxs-lookup"><span data-stu-id="9e508-148">Bit 63: Reserved; must be 0</span></span>

