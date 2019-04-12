---
title: Dispositivos sin periféricos y puntas
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo configurar Windows IoT Core para el modo con cabezal o sin periféricos de los dispositivos.
keywords: Windows iot, pantallas, puntas sin periféricos, la interfaz de usuario
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514751"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="4df19-104">Dispositivos sin periféricos y puntas</span><span class="sxs-lookup"><span data-stu-id="4df19-104">Headed and Headless devices</span></span>

<span data-ttu-id="4df19-105">Windows 10 IoT Core se pueden configurar para cualquiera *puntas* o *sin periféricos* modo.</span><span class="sxs-lookup"><span data-stu-id="4df19-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="4df19-106">Modo con cabezal</span><span class="sxs-lookup"><span data-stu-id="4df19-106">Headed mode</span></span>
<span data-ttu-id="4df19-107">Modo con cabezal está definido por la presencia de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="4df19-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="4df19-108">En *puntas* modo de una sola aplicación de interfaz de usuario se iniciará al arrancar el sistema y además puede ser 0 o más "aplicaciones en segundo plano" (StartupTasks).</span><span class="sxs-lookup"><span data-stu-id="4df19-108">In *headed* mode a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="4df19-109">Modo "desatendido"</span><span class="sxs-lookup"><span data-stu-id="4df19-109">Headless mode</span></span>
<span data-ttu-id="4df19-110">Modo "desatendido" no tiene ninguna interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="4df19-110">Headless mode has no UI.</span></span>  <span data-ttu-id="4df19-111">Los dispositivos que no necesitan la funcionalidad de la interfaz de usuario se pueden establecer en *sin periféricos* modo.</span><span class="sxs-lookup"><span data-stu-id="4df19-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="4df19-112">La pila de la interfaz de usuario está deshabilitada y no se iniciarán las aplicaciones de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="4df19-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="4df19-113">Esto reduce la cantidad de recursos del sistema utilizados.</span><span class="sxs-lookup"><span data-stu-id="4df19-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="4df19-114">Si conecta a un monitor a su dispositivo, la pantalla será negra.</span><span class="sxs-lookup"><span data-stu-id="4df19-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="4df19-115">Si coloca el dispositivo en modo "desatendido", a continuación, puede usar la aplicación de escritorio de Windows 10 IoT Core, descrita a continuación, para encontrar su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="4df19-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="4df19-116">Cambiar el modo</span><span class="sxs-lookup"><span data-stu-id="4df19-116">Changing the mode</span></span>
<span data-ttu-id="4df19-117">Puede modificar el estado del dispositivo desde una sesión de Windows PowerShell o una sesión de SSH sin puntas periféricos.</span><span class="sxs-lookup"><span data-stu-id="4df19-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="4df19-118">Para obtener más información acerca de PowerShell, vea el [PowerShell para IoT Core](../connect-your-device/PowerShell.md) página.</span><span class="sxs-lookup"><span data-stu-id="4df19-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="4df19-119">Para obtener más información acerca de SSH, consulte el [SSH para IoT Core](../connect-your-device/SSH.md) página.</span><span class="sxs-lookup"><span data-stu-id="4df19-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="4df19-120">Para mostrar el estado actual del dispositivo, use el `setbootoption` utilidad:</span><span class="sxs-lookup"><span data-stu-id="4df19-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="4df19-121">Para modificar el estado del dispositivo para habilitar el modo "desatendido", utilice el `setbootoption` utilidad con el `headless` arg:</span><span class="sxs-lookup"><span data-stu-id="4df19-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="4df19-122">Para modificar el estado del dispositivo al modo de habilitar puntas, use el `setbootoption` utilidad con el `headed` arg:</span><span class="sxs-lookup"><span data-stu-id="4df19-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="4df19-123">Buscar el dispositivo sin periféricos</span><span class="sxs-lookup"><span data-stu-id="4df19-123">Finding your headless device</span></span>

<span data-ttu-id="4df19-124">Se puede detectar un dispositivo de IoT Core que esté en modo "desatendido" mediante la **panel de Windows 10 IoT Core** aplicación.</span><span class="sxs-lookup"><span data-stu-id="4df19-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="4df19-125">Para descargar el panel de IoT, consulte el [descargas](http://go.microsoft.com/fwlink/?LinkID=708576) página.</span><span class="sxs-lookup"><span data-stu-id="4df19-125">To download the IoT Dashboard, see the [Downloads](http://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="4df19-126">Cuando se ejecuta, la aplicación escucha pings desde los dispositivos de IoT Core en la red local y muestra información de dispositivo como el nombre, dirección IP y mucho más.</span><span class="sxs-lookup"><span data-stu-id="4df19-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Panel de Windows 10 IoT Core](../media/HeadlessMode/selectDevice.png)
