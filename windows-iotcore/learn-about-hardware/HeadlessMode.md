---
title: Dispositivos con periféricos y sin ellos
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo configurar Windows IoT Core para dispositivos con o sin cabeza.
keywords: Windows IOT, pantallas, cabeza, interfaz de usuario
ms.openlocfilehash: 2fb41d2981b74436ba88ca573407b0ddbcf35566
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721790"
---
# <a name="headed-and-headless-devices"></a><span data-ttu-id="6e146-104">Dispositivos con cabeza y sin periféricos</span><span class="sxs-lookup"><span data-stu-id="6e146-104">Headed and Headless devices</span></span>

<span data-ttu-id="6e146-105">Windows 10 IoT Core puede configurarse para el *modo de encabezado o sin* *cabeza* .</span><span class="sxs-lookup"><span data-stu-id="6e146-105">Windows 10 IoT Core can be configured for either *headed* or *headless* mode.</span></span> 

## <a name="headed-mode"></a><span data-ttu-id="6e146-106">Modo de punta</span><span class="sxs-lookup"><span data-stu-id="6e146-106">Headed mode</span></span>
<span data-ttu-id="6e146-107">El modo de cabeza se define por la presencia de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6e146-107">Headed mode is defined by the presence of UI.</span></span> <span data-ttu-id="6e146-108">En el modo de *cabeza* , se iniciará una sola aplicación de interfaz de usuario en el arranque del sistema y también puede haber 0 o más "aplicaciones en segundo plano" (StartupTasks).</span><span class="sxs-lookup"><span data-stu-id="6e146-108">In *headed* mode a single UI app will be launched at system boot and there can additionally be 0 or more "Background Apps" (StartupTasks).</span></span> 

## <a name="headless-mode"></a><span data-ttu-id="6e146-109">Modo sin periféricos</span><span class="sxs-lookup"><span data-stu-id="6e146-109">Headless mode</span></span>
<span data-ttu-id="6e146-110">El modo sin periféricos no tiene interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6e146-110">Headless mode has no UI.</span></span>  <span data-ttu-id="6e146-111">Los dispositivos que no necesitan la funcionalidad de la interfaz de usuario se pueden establecer en el modo sin *periféricos* .</span><span class="sxs-lookup"><span data-stu-id="6e146-111">Devices that don't need UI functionality can be set to *headless* mode.</span></span> <span data-ttu-id="6e146-112">La pila de la interfaz de usuario está deshabilitada y las aplicaciones de IU no se iniciarán.</span><span class="sxs-lookup"><span data-stu-id="6e146-112">The UI stack is disabled and UI apps will not launch.</span></span> <span data-ttu-id="6e146-113">Esto reduce la cantidad de recursos del sistema utilizados.</span><span class="sxs-lookup"><span data-stu-id="6e146-113">This reduces the amount of system resources used.</span></span> <span data-ttu-id="6e146-114">Si conecta un monitor al dispositivo, la pantalla será negra.</span><span class="sxs-lookup"><span data-stu-id="6e146-114">If you attach a monitor to your device, the screen will be black.</span></span>

> [!NOTE]
> <span data-ttu-id="6e146-115">Si coloca el dispositivo en el modo sin periféricos, puede usar la aplicación Windows 10 IoT Core Dashboard, que se describe a continuación, para encontrar su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6e146-115">If you put your device into headless mode, then you can use the Windows 10 IoT Core Dashboard application, described below, to find its IP address.</span></span>

## <a name="changing-the-mode"></a><span data-ttu-id="6e146-116">Cambiar el modo</span><span class="sxs-lookup"><span data-stu-id="6e146-116">Changing the mode</span></span>
<span data-ttu-id="6e146-117">Puede modificar el estado de la cabeza o el estado de los dispositivos desde una sesión de Windows PowerShell o una sesión de SSH.</span><span class="sxs-lookup"><span data-stu-id="6e146-117">You can modify the headed/headless state of your device from a Windows PowerShell session or an SSH session.</span></span> <span data-ttu-id="6e146-118">Para obtener más información acerca de PowerShell, consulte la página [PowerShell para IOT Core](../connect-your-device/PowerShell.md) .</span><span class="sxs-lookup"><span data-stu-id="6e146-118">To learn more about PowerShell, see the [PowerShell for IoT Core](../connect-your-device/PowerShell.md) page.</span></span> <span data-ttu-id="6e146-119">Para más información sobre SSH, consulte la página [SSH para IOT Core](../connect-your-device/SSH.md) .</span><span class="sxs-lookup"><span data-stu-id="6e146-119">To learn more about SSH, see the [SSH for IoT Core](../connect-your-device/SSH.md) page.</span></span>

* <span data-ttu-id="6e146-120">Para mostrar el estado actual del dispositivo, use la utilidad `setbootoption`:</span><span class="sxs-lookup"><span data-stu-id="6e146-120">To display the current state of your device, use the `setbootoption` utility:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* <span data-ttu-id="6e146-121">Para modificar el estado del dispositivo para habilitar el modo sin periféricos, use la utilidad `setbootoption` con el `headless` Arg:</span><span class="sxs-lookup"><span data-stu-id="6e146-121">To modify the state of your device to enable headless mode, use the `setbootoption` utility with the `headless` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* <span data-ttu-id="6e146-122">Para modificar el estado del dispositivo para habilitar el modo de cabeza, use la utilidad `setbootoption` con el `headed` Arg:</span><span class="sxs-lookup"><span data-stu-id="6e146-122">To modify the state of your device to enable headed mode, use the `setbootoption` utility with the `headed` arg:</span></span>

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a><span data-ttu-id="6e146-123">Búsqueda de un dispositivo sin periféricos</span><span class="sxs-lookup"><span data-stu-id="6e146-123">Finding your headless device</span></span>

<span data-ttu-id="6e146-124">Un dispositivo de IoT Core que está en modo sin periférico se puede detectar mediante la aplicación **Windows 10 IOT Core Dashboard** .</span><span class="sxs-lookup"><span data-stu-id="6e146-124">An IoT Core device that is in headless mode can be discovered using the **Windows 10 IoT Core Dashboard** application.</span></span>  <span data-ttu-id="6e146-125">Para descargar el panel de IoT, consulte la página de [descargas](https://go.microsoft.com/fwlink/?LinkID=708576) .</span><span class="sxs-lookup"><span data-stu-id="6e146-125">To download the IoT Dashboard, see the [Downloads](https://go.microsoft.com/fwlink/?LinkID=708576) page.</span></span>
<span data-ttu-id="6e146-126">Cuando se ejecuta, la aplicación escucha los pings desde cualquier dispositivo de IoT Core en la red local y muestra información del dispositivo, como el nombre, la dirección IP, etc.</span><span class="sxs-lookup"><span data-stu-id="6e146-126">When running, the application listens for pings from any IoT Core devices on the local network and displays device information such as the name, IP address, and more.</span></span>

![Panel de Windows 10 IoT Core](../media/HeadlessMode/selectDevice.png)
