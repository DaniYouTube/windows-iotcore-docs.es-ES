---
title: Información general sobre el shell de IoT
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo aprovechar el shell de IoT para navegar entre las navegaciones del dispositivo.
keywords: Windows IOT, Shell de IoT Core, aplicaciones, aplicaciones de primer plano, aplicaciones en segundo plano
ms.openlocfilehash: e23f121073a84f9c36a390eb126e83b4f4215fee
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918240"
---
# <a name="iot-shell-overview"></a><span data-ttu-id="9fea9-104">Información general sobre el shell de IoT</span><span class="sxs-lookup"><span data-stu-id="9fea9-104">IoT Shell Overview</span></span>

<span data-ttu-id="9fea9-105">En este documento se tratan el shell de IoT, las aplicaciones de primer plano y en segundo plano, y cómo navegar entre estas aplicaciones en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9fea9-105">This document covers the IoT Shell, foreground and background applications, and how to navigate between these applications on your device.</span></span>

## <a name="iot-shell-foreground-and-background-apps"></a><span data-ttu-id="9fea9-106">Aplicaciones de Shell de IoT, de primer plano y en segundo plano</span><span class="sxs-lookup"><span data-stu-id="9fea9-106">IoT Shell, Foreground, and Background Apps</span></span>

<span data-ttu-id="9fea9-107">El dispositivo de IoT Core ejecuta el shell de IoT.</span><span class="sxs-lookup"><span data-stu-id="9fea9-107">Your IoT Core device runs the IoT Shell.</span></span> <span data-ttu-id="9fea9-108">Tiene muchas responsabilidades, pero su trabajo principal es asegurarse de que se inician las aplicaciones de inicio registradas.</span><span class="sxs-lookup"><span data-stu-id="9fea9-108">It has many responsibilities, but its primary job is to make sure registered startup apps are launched.</span></span> <span data-ttu-id="9fea9-109">Tiene dos modos: con cabeza y sin periféricos.</span><span class="sxs-lookup"><span data-stu-id="9fea9-109">It has two modes: Headed and Headless.</span></span> <span data-ttu-id="9fea9-110">En el modo de cabeza, el shell de IoT iniciará una sola aplicación de inicio registrada que mostrará su interfaz de usuario en pantalla completa (también conocida como aplicación de encabezado).</span><span class="sxs-lookup"><span data-stu-id="9fea9-110">In Headed mode, the IoT Shell will launch a single registered startup app that will show its UI in full screen (also known as a Headed app).</span></span> <span data-ttu-id="9fea9-111">El modo de cabeza supone que tiene una pantalla conectada y muestra la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9fea9-111">Headed mode assumes you have a screen connected and shows UI.</span></span> <span data-ttu-id="9fea9-112">En el modo sin periféricos (se explica con detalle [aquí](../learn-about-hardware/HeadlessMode.md)), no hay ninguna interfaz de usuario; el shell de IoT solo inicia aplicaciones en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="9fea9-112">In Headless mode (explained in detail [here](../learn-about-hardware/HeadlessMode.md)), there is no UI; the IoT Shell launches background applications only.</span></span>

<span data-ttu-id="9fea9-113">Estas son las principales diferencias entre las aplicaciones de primer y segundo plano:</span><span class="sxs-lookup"><span data-stu-id="9fea9-113">Here are the main differences between foreground and background applications:</span></span>

- <span data-ttu-id="9fea9-114">**Las aplicaciones de primer plano** tienen una interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9fea9-114">**Foreground applications** have a UI.</span></span> <span data-ttu-id="9fea9-115">Una de ellas se inicia en el inicio cuando el dispositivo está en modo de cabeza.</span><span class="sxs-lookup"><span data-stu-id="9fea9-115">One of these is launched at startup when the device is in headed mode.</span></span> <span data-ttu-id="9fea9-116">Todas las aplicaciones en primer plano están registradas en el dispositivo y el usuario puede cambiar entre las aplicaciones en primer plano durante el funcionamiento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9fea9-116">All foreground apps are registered on the device and the user can switch between foreground apps during device operation.</span></span>

- <span data-ttu-id="9fea9-117">**Las aplicaciones en segundo plano** no tienen interfaz de usuario y, por tanto, guardan recursos de dispositivo desactivando la pila de IU.</span><span class="sxs-lookup"><span data-stu-id="9fea9-117">**Background applications** have no UI and thus save device resources by turning off the UI stack.</span></span> <span data-ttu-id="9fea9-118">Las aplicaciones en segundo plano se ejecutan a menudo continuamente desde el inicio y a menudo se usan para supervisar el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9fea9-118">Background applications often run continuously from startup and are often used to monitor the device.</span></span>

## <a name="switching-between-apps-with-a-home-app"></a><span data-ttu-id="9fea9-119">Cambiar entre aplicaciones con una aplicación principal</span><span class="sxs-lookup"><span data-stu-id="9fea9-119">Switching between apps with a Home App</span></span>

<span data-ttu-id="9fea9-120">En este momento, la aplicación de inicio le permite crear una aplicación doméstica para Windows 10 IoT Core, que le permite cambiar entre diferentes aplicaciones de primer plano.</span><span class="sxs-lookup"><span data-stu-id="9fea9-120">At the moment, the Startup App allows you to create a home app for Windows 10 IoT Core, which allows you to switch between different foreground applications.</span></span> 

<span data-ttu-id="9fea9-121">La **aplicación de inicio de IOT** ([ejemplo](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) representa una sencilla aplicación de inicio que enumera las aplicaciones instaladas en el dispositivo y, a continuación, inicia una mediante las API de PackageManager.</span><span class="sxs-lookup"><span data-stu-id="9fea9-121">The **IoT Startup App** ([sample](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp) represents a simple startup app that lists the installed apps on your device, then launches one using the PackageManager APIs.</span></span>

## <a name="switching-between-apps-with-hid-injection-keys"></a><span data-ttu-id="9fea9-122">Cambiar entre aplicaciones con claves de inyección de HID</span><span class="sxs-lookup"><span data-stu-id="9fea9-122">Switching between apps with HID Injection Keys</span></span>

<span data-ttu-id="9fea9-123">Las instrucciones siguientes muestran cómo activar la compatibilidad con la tecla de acceso rápido a través de entradas en el registro.</span><span class="sxs-lookup"><span data-stu-id="9fea9-123">The below instructions show you how to turn on Hotkey support through entries to the registry.</span></span> <span data-ttu-id="9fea9-124">Si va a compilar su propia imagen y desea admitir las siguientes teclas de acceso rápido (Inicio, aplicación anterior y aplicación siguiente) sin necesidad de acceder al registro, puede incluir un paquete de características opcional que se ocupe de estos pasos.</span><span class="sxs-lookup"><span data-stu-id="9fea9-124">If you are building your own image and want to support the below hotkeys (Home, previous app, and next app) without needing to access the registry, you can include an optional feature package that handles these steps for you.</span></span>

<span data-ttu-id="9fea9-125">Se llama al paquete de características que se va a buscar: **Microsoft-OneCore-IoTUAP-Shell-hotkeys-Feature-package. cab** y la característica se denomina **IOT_SHELL_HOTKEY_SUPPORT**.</span><span class="sxs-lookup"><span data-stu-id="9fea9-125">The feature package to look for is called: **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** and the feature is called **IOT_SHELL_HOTKEY_SUPPORT**.</span></span> <span data-ttu-id="9fea9-126">Vea el [paquete de ejemplo Settings. Hotkey](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) para obtener un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="9fea9-126">See the [Settings.HotKey sample package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml) for an example.</span></span>

<span data-ttu-id="9fea9-127">En el resto de este documento se explica cómo implementar esta característica de forma manual.</span><span class="sxs-lookup"><span data-stu-id="9fea9-127">The rest of this document covers how to implement this feature manually.</span></span>

### <a name="return-home"></a><span data-ttu-id="9fea9-128">Devolver Inicio</span><span class="sxs-lookup"><span data-stu-id="9fea9-128">Return Home</span></span>

<span data-ttu-id="9fea9-129">Con la actualización de aniversario de Windows 10 IoT (1607), el shell de IoT permite poner la ventana de la aplicación predeterminada en primer plano cuando otra aplicación se está ejecutando presionando la tecla "ir a Inicio", que se establece en la versión del botón de Windows de un teclado.</span><span class="sxs-lookup"><span data-stu-id="9fea9-129">With the Windows 10 IoT Anniversary Update (1607), the IoT Shell supports bringing the default application window to the foreground when another application is running by pressing the "GO HOME" key, which is set to the release of the Windows Button on a keyboard.</span></span> <span data-ttu-id="9fea9-130">Si no tiene un teclado en el dispositivo IoT y necesita insertar eventos de teclado de bajo nivel a través de la [inyección de HID](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), o si solo desea volver a asignar la funcionalidad "ir a la Página principal" a otra clave de la aplicación, puede ajustar el valor de clave en el registro.</span><span class="sxs-lookup"><span data-stu-id="9fea9-130">If you don't have a keyboard on your IoT Device and need to inject low-level keyboard events through [HID Injection](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection), or if you just want to re-map the "GO HOME" functionality to a different key in your app, you can adjust the key value in the registry.</span></span> <span data-ttu-id="9fea9-131">Por ejemplo, para habilitar la tecla ESC (0x1B) en "GO HOME", escriba el siguiente comando en el registro:</span><span class="sxs-lookup"><span data-stu-id="9fea9-131">For example, to enable pressing the ESCAPE key (0x1B) to "GO HOME", enter the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

<span data-ttu-id="9fea9-132">Como archivo REG, tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="9fea9-132">As a REG file, this looks as follows:</span></span>

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a><span data-ttu-id="9fea9-133">Cambiar entre aplicaciones</span><span class="sxs-lookup"><span data-stu-id="9fea9-133">Switch Between Apps</span></span>

<span data-ttu-id="9fea9-134">Como alternativa, si desea cambiar entre las aplicaciones de primer plano, puede configurar la funcionalidad de la pestaña Alt (aplicación siguiente) y Mayús-Alt-Tab (aplicación anterior) en la imagen. para ello, escriba el siguiente comando en el registro:</span><span class="sxs-lookup"><span data-stu-id="9fea9-134">Alternatively, if you want to switch between your foreground apps, you can set up Alt-Tab (next app) and Shift-Alt-Tab (previous app) functionality in your image by entering the following command in the registry:</span></span>

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

<span data-ttu-id="9fea9-135">Como archivo REG, tiene el siguiente aspecto: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span><span class="sxs-lookup"><span data-stu-id="9fea9-135">As a REG file, this looks as follows: ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``</span></span>

### <a name="bit-translation"></a><span data-ttu-id="9fea9-136">Traducción de bits</span><span class="sxs-lookup"><span data-stu-id="9fea9-136">Bit Translation</span></span>

<span data-ttu-id="9fea9-137">Las entradas del archivo REG anteriores descodifican de izquierda a derecha como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="9fea9-137">The above REG file entries decode left to right as follows:</span></span>

- <span data-ttu-id="9fea9-138">Bits 0-15: código de tecla virtual (es decir, 1B, 00 para ESCAPE).</span><span class="sxs-lookup"><span data-stu-id="9fea9-138">Bits 0-15: Virtual Key Code (i.e. 1B,00 for ESCAPE).</span></span> <span data-ttu-id="9fea9-139">Consulte el [código de tecla virtual](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) para ver la lista completa de valores de código clave.</span><span class="sxs-lookup"><span data-stu-id="9fea9-139">See [Virtual Key Code](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx) for the complete list of key code values</span></span>
- <span data-ttu-id="9fea9-140">Bits 16-19: tecla modificadora.</span><span class="sxs-lookup"><span data-stu-id="9fea9-140">Bits 16-19: Modifier Key.</span></span> <span data-ttu-id="9fea9-141">0X0 = sin modificador, 0x1 = ALT, 0X2 = CTRL y 0x4 = Mayús.</span><span class="sxs-lookup"><span data-stu-id="9fea9-141">0x0 = No Modifier, 0x1 = ALT, 0x2 = CTRL, and 0x4 = SHIFT.</span></span> <span data-ttu-id="9fea9-142">La combinación de claves suma los valores (es decir, ALT + MAYÚS es 0X5)</span><span class="sxs-lookup"><span data-stu-id="9fea9-142">Combining keys adds the values together (i.e. ALT+SHIFT is 0x5)</span></span>
- <span data-ttu-id="9fea9-143">Bits 20-47: reservado para uso futuro; debe ser 0</span><span class="sxs-lookup"><span data-stu-id="9fea9-143">Bits 20-47: Reserved for future use; must be 0</span></span>
- <span data-ttu-id="9fea9-144">Bits 48-62: acción</span><span class="sxs-lookup"><span data-stu-id="9fea9-144">Bits 48-62:  Action</span></span>
    - <span data-ttu-id="9fea9-145">0 = Inicio</span><span class="sxs-lookup"><span data-stu-id="9fea9-145">0 = Home</span></span>
    - <span data-ttu-id="9fea9-146">1 = vista anterior (puede que no funcione en versiones futuras)</span><span class="sxs-lookup"><span data-stu-id="9fea9-146">1 = Previous View (may not work in future releases)</span></span>
    - <span data-ttu-id="9fea9-147">2 = vista siguiente (puede que no funcione en versiones futuras)</span><span class="sxs-lookup"><span data-stu-id="9fea9-147">2 = Next View (may not work in future releases)</span></span>
- <span data-ttu-id="9fea9-148">Bit 63: reservado; debe ser 0</span><span class="sxs-lookup"><span data-stu-id="9fea9-148">Bit 63: Reserved; must be 0</span></span>

