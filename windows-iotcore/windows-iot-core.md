---
title: Información general de Windows 10 IoT Core
ms.date: 01/18/2018
ms.topic: article
description: Obtenga información sobre qué es Windows 10 IoT Core y lo que puede hacer con él.
keywords: Windows 10 IoT Core, superficie pequeña, equipo sin periféricos
ms.openlocfilehash: 270d2e2491514a1b5b0c0fefb7c16da326512355
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080533"
---
# <a name="an-overview-of-windows-10-iot-core"></a><span data-ttu-id="ab142-104">Información general de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="ab142-104">An overview of Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="ab142-105">Se admiten contenedores Windows para implementaciones comerciales en Windows Server, Windows IoT Server, Windows IoT Enterprise y Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab142-105">Windows Containers are supported for commercial deployments on Windows Server, Windows IoT Server, Windows IoT Enterprise and Windows IoT Core.</span></span>  <span data-ttu-id="ab142-106">A partir de la actualización de octubre de 2018 de Windows (compilación 17763), los contenedores Windows solo se pueden usar con Windows Enterprise y Professional para fines de desarrollo y pruebas.</span><span class="sxs-lookup"><span data-stu-id="ab142-106">As of Windows October Update 2018 (Build 17763), Windows Containers can only be used with Windows Enterprise and Professional for dev/test purposes.</span></span>

## <a name="what-is-windows-10-iot-core"></a><span data-ttu-id="ab142-107">¿Qué es Windows 10 IoT Core?</span><span class="sxs-lookup"><span data-stu-id="ab142-107">What is Windows 10 IoT Core?</span></span>
<span data-ttu-id="ab142-108">Windows 10 IoT Core es una versión de Windows 10 optimizada para dispositivos más pequeños con o sin pantalla, y que se ejecutan en dispositivos ARM y x86 o x64.</span><span class="sxs-lookup"><span data-stu-id="ab142-108">Windows 10 IoT Core is a version of Windows 10 that is optimized for smaller devices with or without a display that run on both ARM and x86/x64 devices.</span></span> <span data-ttu-id="ab142-109">La documentación de Windows IoT Core, proporciona información sobre la conexión, administración, actualización y protección de los dispositivos, y mucho más.</span><span class="sxs-lookup"><span data-stu-id="ab142-109">The Windows IoT Core documentation provides information on connecting, managing, updating, securing your devices, and more.</span></span> 

<span data-ttu-id="ab142-110">Si está listo para pasar al siguiente nivel y empezar a comercializar la solución, puede aprender a fabricar con Windows 10 IoT Core con nuestra [Guía de fabricación de Windows 10 IoT Core](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span><span class="sxs-lookup"><span data-stu-id="ab142-110">If you're ready to go to the next level and start commercializing your solution, you can learn how to manufacture with Windows 10 IoT Core with our [Windows 10 IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> 

## <a name="getting-started"></a><span data-ttu-id="ab142-111">Introducción</span><span class="sxs-lookup"><span data-stu-id="ab142-111">Getting started</span></span>

<span data-ttu-id="ab142-112">Antes de intentar fabricar un dispositivo, primero es recomendable probar y diseñar un prototipo de un dispositivo con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab142-112">Before attempting to manufacture a device, it's best to first try and prototype a device with Windows 10 IoT Core.</span></span> <span data-ttu-id="ab142-113">De este modo, puede comprender las características que va a necesitar y las configuraciones que le interesarán cuando llegue el momento de la fabricación.</span><span class="sxs-lookup"><span data-stu-id="ab142-113">That way, you can understand what features you'll need and what configurations you'll want when it's time to manufacture.</span></span>

<table>  
<span data-ttu-id="ab142-114"><colgroup> <col width="50%" /> <col width="50%" /> </colgroup>  
</span><span class="sxs-lookup"><span data-stu-id="ab142-114"><colgroup> <col width="50%" /> <col width="50%" /> </colgroup>  
</span></span><thead>  
<tr class="header">  
<th align="left"><span data-ttu-id="ab142-115">Tema</span><span class="sxs-lookup"><span data-stu-id="ab142-115">Topic</span></span></th>
<th align="left"><span data-ttu-id="ab142-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="ab142-116">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="ab142-117"><a href="https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. Selección de una placa de prototipo</a></span><span class="sxs-lookup"><span data-stu-id="ab142-117"><a href="https://docs.microsoft.com/windows/iot-core/tutorials/quickstarter/PrototypeBoards"
>1. Pick a prototype board</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="ab142-118">Examine placas de prototipo comunes y elija una con la que empezar a crear prototipos.</span><span class="sxs-lookup"><span data-stu-id="ab142-118">Take a look at common prototype boards and choose one to start prototyping with.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="ab142-119">2. Instalación de una imagen de prototipo</span><span class="sxs-lookup"><span data-stu-id="ab142-119">2. Flash a prototype image</span></span></p></td>
<td align="left"><p><span data-ttu-id="ab142-120">Vaya a las secciones de los tutoriales para obtener información sobre cómo instalar imágenes de prototipo en los dispositivos seleccionados.</span><span class="sxs-lookup"><span data-stu-id="ab142-120">Go to our tutorial sections to learn how to flash prototype images onto your selected device(s).</span></span> </p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="ab142-121"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller">3. Instalación de la aplicación</a></span><span class="sxs-lookup"><span data-stu-id="ab142-121"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appinstaller">3. Install your app</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="ab142-122">Obtenga información sobre cómo instalar la aplicación mediante distintas herramientas.</span><span class="sxs-lookup"><span data-stu-id="ab142-122">Learn how to install your app using different tools.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="ab142-123"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appdeployment">4. Implementación de la aplicación</a></span><span class="sxs-lookup"><span data-stu-id="ab142-123"><a href="https://docs.microsoft.com/windows/iot-core/develop-your-app/appdeployment">4. Deploy your app</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="ab142-124">Obtenga información sobre cómo implementar una aplicación mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab142-124">Learn how to deploy an app using Visual Studio.</span></span></p></td>
</tr>

</tbody>
</table>

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a><span data-ttu-id="ab142-125">Diferencias entre Windows 10 Desktop y Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="ab142-125">Differences between Windows 10 Desktop and Windows 10 IoT Core</span></span>

### <a name="different-features-available-on-desktop-and-iot-core"></a><span data-ttu-id="ab142-126">Distintas características disponibles en Desktop e IoT Core</span><span class="sxs-lookup"><span data-stu-id="ab142-126">Different features available on Desktop and IoT Core</span></span>

* <span data-ttu-id="ab142-127">Inbox Cortana ya no está disponible en Windows 10 IoT Core desde la versión 1809 (17763).</span><span class="sxs-lookup"><span data-stu-id="ab142-127">Inbox Cortana is no longer available on Windows 10 IoT Core since version 1809 (17763).</span></span> <span data-ttu-id="ab142-128">Si lo que busca es comercializar rápidamente un dispositivo habilitado para voz, puede integrar la compatibilidad con Cortana en el dispositivo mediante la [versión preliminar del SDK de dispositivos de Cortana](https://developer.microsoft.com/cortana/devices).</span><span class="sxs-lookup"><span data-stu-id="ab142-128">If you are looking to bring a voice-enabled device to market quickly, you can integrate Cortana support into the device using the [preview of the Cortana Devices SDK](https://developer.microsoft.com/cortana/devices).</span></span>
* <span data-ttu-id="ab142-129">[FileOpenPicker API](https://docs.microsoft.com/uwp/api/windows.storage.pickers.fileopenpicker) no se admite en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab142-129">The [FileOpenPicker API](https://docs.microsoft.com/uwp/api/windows.storage.pickers.fileopenpicker) is not supported in Windows 10 IoT Core.</span></span> <span data-ttu-id="ab142-130">Para acceder a unidades locales o almacenamiento extraíble, puede implementar esto en una aplicación propia.</span><span class="sxs-lookup"><span data-stu-id="ab142-130">To access local drives or removable storage, you can implement this in your own application.</span></span>
* <span data-ttu-id="ab142-131">De fábrica, el dispositivo Windows 10 IoT Core arrancará en la [aplicación predeterminada](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) en lugar de un PC de estilo escritorio.</span><span class="sxs-lookup"><span data-stu-id="ab142-131">Out of the box, The Windows 10 IoT Core device will boot to the [default app](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) instead of a desktop-like PC.</span></span> <span data-ttu-id="ab142-132">Pero para la comercialización, **es obligatorio** reemplazar esta aplicación predeterminada por una personalizada o una aplicación predeterminada que se pueda modificar.</span><span class="sxs-lookup"><span data-stu-id="ab142-132">However, for commercialization, this default app **must** be replaced by either a custom app or a default app that can be modified.</span></span> <span data-ttu-id="ab142-133">El propósito de esta aplicación no es solo proporcionar un shell descriptivo con el que interactuar tras el primer arranque, sino también permitir el uso del [código abierto](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para esta aplicación con el fin de poder utilizar estas características para conectar aplicaciones personalizadas propias.</span><span class="sxs-lookup"><span data-stu-id="ab142-133">The purpose of this application is not only to provide you with a friendly shell to interact with upon first boot, but to also allow you to use the [open-sourced code](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) for this application so that you can use these features to plug and play your own custom application(s).</span></span>

### <a name="differences-in-driver-supported-areas"></a><span data-ttu-id="ab142-134">Diferencias en las áreas compatibles con el controlador</span><span class="sxs-lookup"><span data-stu-id="ab142-134">Differences in driver-supported areas</span></span>

* <span data-ttu-id="ab142-135">Windows 10 Desktop tiene más controladores compatibles que Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab142-135">Windows 10 Desktop has more supported drivers than Windows 10 IoT Core.</span></span> <span data-ttu-id="ab142-136">Para hacer que los mismos dispositivos funcionen en Windows 10 IoT Core y en Desktop, es posible que tenga que compilar un controlador a partir de código fuente para un dispositivo Windows 10 IoT Core, o bien buscar otra solución alternativa, especialmente para la arquitectura ARM.</span><span class="sxs-lookup"><span data-stu-id="ab142-136">To make the same device(s) work on Windows 10 IoT Core as on Desktop, you may need to build a driver from source for a Windows 10 IoT Core device or find another workaround, especially for ARM architecture.</span></span>
* <span data-ttu-id="ab142-137">No hay ningún controlador de fábrica para libusb para Windows 10 IoT Core (ARM); tendrá que compilar a partir del código fuente para seleccionar la arquitectura ARM como destino.</span><span class="sxs-lookup"><span data-stu-id="ab142-137">There is no out-of-the-box driver for libusb for Windows 10 IoT Core (ARM) - you will need to build from source to target the ARM architecture.</span></span>

### <a name="differences-in-available-registry-set"></a><span data-ttu-id="ab142-138">Diferencias en el conjunto de registros disponibles</span><span class="sxs-lookup"><span data-stu-id="ab142-138">Differences in available registry set</span></span>

* <span data-ttu-id="ab142-139">En Desktop, hay una opción para "ocultar automáticamente las barras de desplazamiento en Windows" que se puede desactivar.</span><span class="sxs-lookup"><span data-stu-id="ab142-139">On desktop, there is an option to "Automatically hide scroll bars in Windows" that can be set to off.</span></span> <span data-ttu-id="ab142-140">Se controla mediante la entrada del Registro siguiente:</span><span class="sxs-lookup"><span data-stu-id="ab142-140">It is controlled by the following registry entry:</span></span> 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* <span data-ttu-id="ab142-141">De forma predeterminada, en los dispositivos Windows 10 IoT Core no hay ningún Registro de este tipo.</span><span class="sxs-lookup"><span data-stu-id="ab142-141">There is no such registry on Windows 10 IoT Core devices by default.</span></span> <span data-ttu-id="ab142-142">Tendrá que agregar una entrada del Registro "DynamicScrollbars" si lo quiere.</span><span class="sxs-lookup"><span data-stu-id="ab142-142">You will need to add a "Dynamic Scrollbars" register if you want.</span></span>
* <span data-ttu-id="ab142-143">Para permitir que las barras de desplazamiento se oculten de forma automática en una aplicación de UWP, puede agregar la entrada del Registro "DynamicScrollbars" y establecer el valor en "1" de esta forma:</span><span class="sxs-lookup"><span data-stu-id="ab142-143">To enable hide scroll bars automatically in a UWP application, you can add the "DynamicScrollbars" register and set the value to "1" like this:</span></span>

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* <span data-ttu-id="ab142-144">La clave del Registro se debe establecer desde la cuenta predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ab142-144">The registry key must be set from the Default Account.</span></span> <span data-ttu-id="ab142-145">Si el valor XAML ScrollViewer es "Visible", el valor del Registro de 0 forzará la aparición de la barra de desplazamiento, con independencia de que haya contenido suficiente para que se muestre en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="ab142-145">If the ScrollViewer's XAML setting is "Visible", the nthe registry setting of 0 will force the scroll bar to appear regardlss of whether there is sufficient content to have the scroll appear in the UI.</span></span> <span data-ttu-id="ab142-146">Un valor del Registro de 1 mantendrá oculta la barra de desplazamiento hasta que haya contenido suficiente.</span><span class="sxs-lookup"><span data-stu-id="ab142-146">A registry setting of 1 will keep the scroll bar hidden until there is sufficient content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* <span data-ttu-id="ab142-147">Por último, si el valor de XAML ScrollViewer es "Auto", el valor del Registro de 0 solo mostrará la barra de desplazamiento completa cuando haya contenido suficiente para mostrarla.</span><span class="sxs-lookup"><span data-stu-id="ab142-147">Lastly, if the ScrollViewer XAML's setting is "Auto" then the registry setting of 0 will only show the full scroll bar when there is enough content to display the scroll bar.</span></span> <span data-ttu-id="ab142-148">Cuando el valor del Registro es 1, la barra de desplazamiento aparecerá cuando haya contenido suficiente, o bien se ocultará si no lo hay.</span><span class="sxs-lookup"><span data-stu-id="ab142-148">When the registry setting is 1, the scroll bar will appear then when there is enough content or hidden if there is no content.</span></span>

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a><span data-ttu-id="ab142-149">Diferentes comandos admitidos</span><span class="sxs-lookup"><span data-stu-id="ab142-149">Different commands supported</span></span>

* <span data-ttu-id="ab142-150">El comando Remove-AppxPackage de PowerShell funciona en Desktop pero no en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab142-150">The PowerShell Remove-AppxPackage command works on Desktop but not on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="ab142-151">No todas las carpetas del dispositivo son accesibles para las aplicaciones universales de Windows.</span><span class="sxs-lookup"><span data-stu-id="ab142-151">Not all folders on your device are accessible by Universal Windows Apps.</span></span> <span data-ttu-id="ab142-152">En Windows 10 IoT Core puede usar la herramienta FolderPermissions para hacer que una carpeta sea accesible para una aplicación para UWP.</span><span class="sxs-lookup"><span data-stu-id="ab142-152">On Windows 10 IoT Core you can use the FolderPermissions tool to make a folder accessible to a UWP app.</span></span> <span data-ttu-id="ab142-153">Por ejemplo, ejecute FolderPermissions c:\test -e para conceder a las aplicaciones para UWP acceso a la carpeta c:\test.</span><span class="sxs-lookup"><span data-stu-id="ab142-153">For example, run FolderPermissions c:\test -e to give UWP apps access to c:\test folder.</span></span> <span data-ttu-id="ab142-154">Pero esto no está disponible en Desktop.</span><span class="sxs-lookup"><span data-stu-id="ab142-154">However, this is not available on Desktop.</span></span>

<span data-ttu-id="ab142-155">Todas las diferencias que se describen en esta publicación pueden no ser válidas en el futuro, ya que Windows 10 IoT Core se actualiza constantemente.</span><span class="sxs-lookup"><span data-stu-id="ab142-155">All differences described in this post may not be valid in the future because Windows 10 IoT Core is constantly being updated.</span></span>

## <a name="helpful-resources"></a><span data-ttu-id="ab142-156">Recursos útiles</span><span class="sxs-lookup"><span data-stu-id="ab142-156">Helpful resources</span></span>
<span data-ttu-id="ab142-157">[Lea nuestra documentación](https://docs.microsoft.com/windows/iot-core/) para obtener más información sobre Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="ab142-157">[Read our documentation](https://docs.microsoft.com/windows/iot-core/) to learn more about Windows 10 IoT Core.</span></span>
