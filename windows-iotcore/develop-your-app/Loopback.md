---
title: Comunicación con Localhost
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear una conexión TCP/IP con dos procesos al habilitar bucle invertido localhost.
keywords: Windows iot, localhost, bucle invertido, UWP, visual studio
ms.openlocfilehash: 498db8321babad890606e9e4589c9a6407f3ea6e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514247"
---
# <a name="communicating-with-localhost-loopback"></a><span data-ttu-id="d3d92-104">Comunicación con el host local (bucle invertido)</span><span class="sxs-lookup"><span data-stu-id="d3d92-104">Communicating with localhost (loopback)</span></span>

<span data-ttu-id="d3d92-105">En Windows IoT Core, si desea crear una conexión TCP/IP entre 2 procesos que se ejecutan en el mismo dispositivo y una de ellas es una aplicación para UWP debe habilitar bucle invertido localhost.</span><span class="sxs-lookup"><span data-stu-id="d3d92-105">On Windows IoT Core, if you want to create a TCP/IP connection between 2 processes running on the same device and one of them is a UWP app you must enable localhost loopback.</span></span>

## <a name="loopback-and-the-debugger"></a><span data-ttu-id="d3d92-106">El depurador y en bucle</span><span class="sxs-lookup"><span data-stu-id="d3d92-106">Loopback and the debugger</span></span> 
<span data-ttu-id="d3d92-107">De forma predeterminada, que se ejecuta en el depurador de Visual Studio permite bucle invertido de salida automáticamente para esa sesión de depuración solo.</span><span class="sxs-lookup"><span data-stu-id="d3d92-107">By default, running under the Visual Studio debugger enables outbound loopback automatically for that debug session only.</span></span><span data-ttu-id="d3d92-108">  No debería tener que hacer nada, siempre y cuando se activa la casilla de bucle invertido en la configuración del depurador para su proyecto de inicio.</span><span class="sxs-lookup"><span data-stu-id="d3d92-108">  You shouldn’t have to do anything as long as the loopback checkbox is checked in the debugger settings for your startup project.</span></span> <span data-ttu-id="d3d92-109"> Si desea implementar un agente de escucha de socket se debe habilitar bucle invertido localhost para las conexiones entrantes (ver abajo).</span><span class="sxs-lookup"><span data-stu-id="d3d92-109"> If you want to implement a socket listener the you must enable localhost loopback for inbound connections (see below).</span></span>
 
## <a name="enabling-the-inbound-loopback-policy"></a><span data-ttu-id="d3d92-110">Habilitación de la directiva de bucle invertido de entrada</span><span class="sxs-lookup"><span data-stu-id="d3d92-110">Enabling the inbound loopback policy</span></span>
<span data-ttu-id="d3d92-111">El host local de entrada directiva de bucle invertido para **Windows IoT Core** debe habilitarse para las que implementar servidores de aplicaciones para UWP.</span><span class="sxs-lookup"><span data-stu-id="d3d92-111">The localhost inbound loopback policy for **Windows IoT Core** must be enabled for UWP apps that implement servers.</span></span>  <span data-ttu-id="d3d92-112">Esta directiva se controla mediante la clave del registro siguiente:</span><span class="sxs-lookup"><span data-stu-id="d3d92-112">This policy is controlled by the following registry key:</span></span>

        [HKEY_LOCAL_MACHINE\system\currentcontrolset\services\mpssvc\parameters]
            "IoTInboundLoopbackPolicy"=dword:00000001

<span data-ttu-id="d3d92-113">Este valor de clave del registro IoTInboundLoopbackPolicy debe establecerse en DWORD: 00000001 para habilitar.</span><span class="sxs-lookup"><span data-stu-id="d3d92-113">This IoTInboundLoopbackPolicy registry key value must be set to dword:00000001 to enable.</span></span> <span data-ttu-id="d3d92-114">Si cambia el valor del registro de IoTInboundLoopbackPolicy que debe reiniciarse para que el cambio surta efecto.</span><span class="sxs-lookup"><span data-stu-id="d3d92-114">If you change the IoTInboundLoopbackPolicy registry value you must reboot for the change to take effect.</span></span><span data-ttu-id="d3d92-115">  La directiva de bucle invertido localhost debe estar habilitada de forma predeterminada en \*\*Windows IoT Core**</span><span class="sxs-lookup"><span data-stu-id="d3d92-115">  The localhost loopback policy should be enabled by default on \*\*Windows IoT Core**</span></span>

<span data-ttu-id="d3d92-116">Para comprobar que el valor es el conjunto ejecute el siguiente comando en el **Windows IoT Core** dispositivo:</span><span class="sxs-lookup"><span data-stu-id="d3d92-116">To verify that the value is set execute the following command on the **Windows IoT Core** device:</span></span>

        reg query hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy

<span data-ttu-id="d3d92-117">Para habilitar la directiva de ejecutar el comando siguiente en el **Windows IoT Core** dispositivo:</span><span class="sxs-lookup"><span data-stu-id="d3d92-117">To enable the policy execute the following command on the **Windows IoT Core** device:</span></span>

        reg add hklm\system\currentcontrolset\services\mpssvc\parameters /v IoTInboundLoopbackPolicy /t REG_DWORD /d 1
 

## <a name="enabling-loopback-for-a-uwp-application"></a><span data-ttu-id="d3d92-118">Habilitación de bucle invertido para una aplicación de UWP</span><span class="sxs-lookup"><span data-stu-id="d3d92-118">Enabling loopback for a UWP application</span></span>
<span data-ttu-id="d3d92-119">Antes de poder habilitar bucle invertido para una aplicación necesita el nombre de familia de paquete.</span><span class="sxs-lookup"><span data-stu-id="d3d92-119">Before you can enable loopback for an application you will need the package family name.</span></span>  <span data-ttu-id="d3d92-120">Puede encontrar el nombre de familia de paquete para una aplicación instalada mediante la ejecución de **iotstartup lista**.</span><span class="sxs-lookup"><span data-stu-id="d3d92-120">You can find the package family name for an installed application by running **iotstartup list**.</span></span>  <span data-ttu-id="d3d92-121">Si el **iotstartup lista** entrada para la aplicación es IoTCoreDefaultApp\_1w720vyc4ccym! A continuación, el nombre de familia de paquete de aplicación es IoTCoreDefaultApp\_1w720vyc4ccym</span><span class="sxs-lookup"><span data-stu-id="d3d92-121">If the **iotstartup list** entry for the application is IoTCoreDefaultApp\_1w720vyc4ccym!App then the package family name is IoTCoreDefaultApp\_1w720vyc4ccym</span></span>

<span data-ttu-id="d3d92-122">Para permitir bucle invertido para su uso de conexiones de cliente `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span><span class="sxs-lookup"><span data-stu-id="d3d92-122">To enable loopback for client connections use `CheckNetIsolation.exe LoopbackExempt -a -n=<AppContainer or Package Family>`.</span></span>  <span data-ttu-id="d3d92-123">CheckNetIsolation.exe configurará bucle invertido para la aplicación y salir.</span><span class="sxs-lookup"><span data-stu-id="d3d92-123">CheckNetIsolation.exe will configure loopback for the application and exit.</span></span> <span data-ttu-id="d3d92-124">Esto permitirá que la aplicación realizar conexiones salientes a un servidor.</span><span class="sxs-lookup"><span data-stu-id="d3d92-124">This will enable the application to make outbound connections to a server.</span></span>

<span data-ttu-id="d3d92-125">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d3d92-125">Example:</span></span> `CheckNetIsolation.exe LoopbackExempt -a -n=IoTCoreDefaultApp_1w720vyc4ccym`

<span data-ttu-id="d3d92-126">Para habilitar una aplicación de servidor recibir conexiones entrantes, use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span><span class="sxs-lookup"><span data-stu-id="d3d92-126">To enable a server application to receive inbound connections use `CheckNetIsolation.exe LoopbackExempt -is -n=<AppContainer or Package Family>`.</span></span> <span data-ttu-id="d3d92-127">A diferencia de la configuración de conexiones salientes, las conexiones entrantes requieren CheckNetIsolation.exe ejecutar continuamente mientras la aplicación de servidor está recibiendo las conexiones.</span><span class="sxs-lookup"><span data-stu-id="d3d92-127">Unlike outbound connection configuration, inbound connections require CheckNetIsolation.exe to run continuously while the server application is receiving connections.</span></span><span data-ttu-id="d3d92-128">  Esto requiere una compilación del sistema operativo más reciente que 10.0.14393.</span><span class="sxs-lookup"><span data-stu-id="d3d92-128">  This requires an OS build newer than 10.0.14393.</span></span>

<span data-ttu-id="d3d92-129">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d3d92-129">Example:</span></span> `CheckNetIsolation.exe LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym`

<span data-ttu-id="d3d92-130">La mejor manera de ejecutar CheckNetIsolation.exe automáticamente durante el inicio es usar schtasks.exe:</span><span class="sxs-lookup"><span data-stu-id="d3d92-130">The best way to run CheckNetIsolation.exe automatically on startup is to use schtasks.exe:</span></span> `schtasks /create /tn MyTask /f /sc onstart /ru system /tr "checknetisolation LoopbackExempt -is -n=IoTCoreDefaultApp_1w720vyc4ccym"`

<span data-ttu-id="d3d92-131">Tras reiniciar el sistema debe ser capaz de comprobar que se está ejecutando ese checknetisolation.exe utilizando tlist.exe o [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span><span class="sxs-lookup"><span data-stu-id="d3d92-131">Upon rebooting you should be able to verify that checknetisolation.exe is running by using tlist.exe or [Windows Device Portal](https://developer.microsoft.com/en-us/windows/iot/docs/deviceportal)</span></span>
