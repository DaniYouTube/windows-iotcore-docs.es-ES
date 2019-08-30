---
title: Comunicación con localhost
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear una conexión TCP/IP con dos procesos habilitando el bucle invertido localhost.
keywords: Windows IOT, localhost, loopback, UWP, Visual Studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170673"
---
# <a name="communicating-with-localhost-loopback"></a><span data-ttu-id="49eb6-104">Comunicación con localhost (bucle invertido)</span><span class="sxs-lookup"><span data-stu-id="49eb6-104">Communicating with localhost (loopback)</span></span>

<span data-ttu-id="49eb6-105">En Windows IoT Core, si desea crear una conexión TCP/IP entre 2 procesos que se ejecutan en el mismo dispositivo y uno de ellos es una aplicación para UWP, debe habilitar el bucle invertido localhost.</span><span class="sxs-lookup"><span data-stu-id="49eb6-105">On Windows IoT Core, if you want to create a TCP/IP connection between 2 processes running on the same device and one of them is a UWP app you must enable localhost loopback.</span></span>

## <a name="loopback-and-the-debugger"></a><span data-ttu-id="49eb6-106">Bucle invertido y el depurador</span><span class="sxs-lookup"><span data-stu-id="49eb6-106">Loopback and the debugger</span></span> 
<span data-ttu-id="49eb6-107">De forma predeterminada, la ejecución en el depurador de Visual Studio solo habilita el bucle invertido de salida automáticamente para esa sesión de depuración.</span><span class="sxs-lookup"><span data-stu-id="49eb6-107">By default, running under the Visual Studio debugger enables outbound loopback automatically for that debug session only.</span></span><span data-ttu-id="49eb6-108">  No debe hacer nada, siempre y cuando la casilla de bucle invertido esté activada en la configuración del depurador del proyecto de inicio.</span><span class="sxs-lookup"><span data-stu-id="49eb6-108">  You shouldn’t have to do anything as long as the loopback checkbox is checked in the debugger settings for your startup project.</span></span> <span data-ttu-id="49eb6-109"> Si desea implementar un agente de escucha de socket, debe habilitar el bucle invertido localhost para las conexiones entrantes (consulte a continuación).</span><span class="sxs-lookup"><span data-stu-id="49eb6-109"> If you want to implement a socket listener the you must enable localhost loopback for inbound connections (see below).</span></span>
 
## <a name="enabling-the-inbound-loopback-policy"></a><span data-ttu-id="49eb6-110">Habilitar la Directiva de bucle invertido entrante</span><span class="sxs-lookup"><span data-stu-id="49eb6-110">Enabling the inbound loopback policy</span></span>
<span data-ttu-id="49eb6-111">La Directiva de bucle invertido de entrada localhost para **Windows IOT Core** debe estar habilitada para las aplicaciones UWP que implementan servidores.</span><span class="sxs-lookup"><span data-stu-id="49eb6-111">The localhost inbound loopback policy for **Windows IoT Core** must be enabled for UWP apps that implement servers.</span></span>  <span data-ttu-id="49eb6-112">Esta directiva está controlada por la siguiente clave del registro:</span><span class="sxs-lookup"><span data-stu-id="49eb6-112">This policy is controlled by the following registry key:</span></span>

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

<span data-ttu-id="49eb6-113">Este valor de clave del registro IoTInboundLoopbackPolicy debe establecerse en DWORD: 00000001 para habilitar.</span><span class="sxs-lookup"><span data-stu-id="49eb6-113">This IoTInboundLoopbackPolicy registry key value must be set to dword:00000001 to enable.</span></span> <span data-ttu-id="49eb6-114">Si cambia el valor del registro IoTInboundLoopbackPolicy, debe reiniciar para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="49eb6-114">If you change the IoTInboundLoopbackPolicy registry value you must reboot for the change to take effect.</span></span><span data-ttu-id="49eb6-115">  La directiva de bucle invertido localhost debe estar habilitada de forma predeterminada en **Windows IoT Core**</span><span class="sxs-lookup"><span data-stu-id="49eb6-115">  The localhost loopback policy should be enabled by default on **Windows IoT Core**</span></span>

<span data-ttu-id="49eb6-116">Para comprobar que el valor está establecido, ejecute el siguiente comando en el dispositivo **Windows IOT Core** :</span><span class="sxs-lookup"><span data-stu-id="49eb6-116">To verify that the value is set execute the following command on the **Windows IoT Core** device:</span></span>

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

<span data-ttu-id="49eb6-117">Para habilitar la Directiva, ejecute el siguiente comando en el dispositivo **Windows IOT Core** :</span><span class="sxs-lookup"><span data-stu-id="49eb6-117">To enable the policy execute the following command on the **Windows IoT Core** device:</span></span>

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a><span data-ttu-id="49eb6-118">Habilitación de bucle invertido para una aplicación de UWP</span><span class="sxs-lookup"><span data-stu-id="49eb6-118">Enabling loopback for a UWP application</span></span>
<span data-ttu-id="49eb6-119">Antes de poder habilitar el bucle invertido para una aplicación, necesitará el nombre de familia del paquete.</span><span class="sxs-lookup"><span data-stu-id="49eb6-119">Before you can enable loopback for an application you will need the package family name.</span></span>  <span data-ttu-id="49eb6-120">Para encontrar el nombre de familia de paquete de una aplicación instalada, ejecute la **lista iotstartup**.</span><span class="sxs-lookup"><span data-stu-id="49eb6-120">You can find the package family name for an installed application by running **iotstartup list**.</span></span>  <span data-ttu-id="49eb6-121">Si la entrada de la **lista de iotstartup** para la\_aplicación es IoTCoreDefaultApp 1w720vyc4ccym! Aplicación, el nombre de familia del paquete\_es IoTCoreDefaultApp 1w720vyc4ccym</span><span class="sxs-lookup"><span data-stu-id="49eb6-121">If the **iotstartup list** entry for the application is IoTCoreDefaultApp\_1w720vyc4ccym!App then the package family name is IoTCoreDefaultApp\_1w720vyc4ccym</span></span>

<span data-ttu-id="49eb6-122">Para habilitar el bucle invertido para las `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`conexiones de cliente, use.</span><span class="sxs-lookup"><span data-stu-id="49eb6-122">To enable loopback for client connections use `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span></span>  <span data-ttu-id="49eb6-123">CheckNetIsolation. exe configurará el bucle invertido para la aplicación y se cerrará.</span><span class="sxs-lookup"><span data-stu-id="49eb6-123">CheckNetIsolation.exe will configure loopback for the application and exit.</span></span> <span data-ttu-id="49eb6-124">Esto permitirá que la aplicación realice conexiones salientes a un servidor.</span><span class="sxs-lookup"><span data-stu-id="49eb6-124">This will enable the application to make outbound connections to a server.</span></span>

<span data-ttu-id="49eb6-125">Ejemplo: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`</span><span class="sxs-lookup"><span data-stu-id="49eb6-125">Example: `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`</span></span>

<span data-ttu-id="49eb6-126">Para permitir que una aplicación de servidor reciba conexiones de entrada `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`, use.</span><span class="sxs-lookup"><span data-stu-id="49eb6-126">To enable a server application to receive inbound connections use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span></span> <span data-ttu-id="49eb6-127">A diferencia de la configuración de la conexión de salida, las conexiones entrantes requieren que CheckNetIsolation. exe se ejecute continuamente mientras la aplicación de servidor recibe conexiones.</span><span class="sxs-lookup"><span data-stu-id="49eb6-127">Unlike outbound connection configuration, inbound connections require CheckNetIsolation.exe to run continuously while the server application is receiving connections.</span></span><span data-ttu-id="49eb6-128">  Esto requiere una compilación de sistema operativo más reciente que 10.0.14393.</span><span class="sxs-lookup"><span data-stu-id="49eb6-128">  This requires an OS build newer than 10.0.14393.</span></span>

<span data-ttu-id="49eb6-129">Ejemplo: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`</span><span class="sxs-lookup"><span data-stu-id="49eb6-129">Example: `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`</span></span>

<span data-ttu-id="49eb6-130">La mejor manera de ejecutar CheckNetIsolation. exe automáticamente al iniciar es usar SchTasks. exe:`schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`</span><span class="sxs-lookup"><span data-stu-id="49eb6-130">The best way to run CheckNetIsolation.exe automatically on startup is to use schtasks.exe: `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`</span></span>

<span data-ttu-id="49eb6-131">Tras el reinicio, debería poder comprobar que checknetisolation. exe se está ejecutando mediante Tlist. exe o el [portal de dispositivos de Windows](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal) .</span><span class="sxs-lookup"><span data-stu-id="49eb6-131">Upon rebooting you should be able to verify that checknetisolation.exe is running by using tlist.exe or [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span></span>
