---
title: Conexión de banda ancha móvil
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Obtenga información sobre cómo usar la conexión de banda ancha móvil para Windows 10 IoT Core.
keywords: Windows IOT, MBB, conexión de banda ancha móvil
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168053"
---
## <a name="mobile-broadband-connection"></a><span data-ttu-id="8dc40-104">Conexión de banda ancha móvil</span><span class="sxs-lookup"><span data-stu-id="8dc40-104">Mobile Broadband Connection</span></span>

<span data-ttu-id="8dc40-105">La conexión de banda ancha móvil es compatible con [Windows 10 IOT Core](http://windowsondevices.com).</span><span class="sxs-lookup"><span data-stu-id="8dc40-105">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="8dc40-106">Si la puerta de enlace de IOT es compatible con el módulo de módem de `MBBConnect` banda ancha móvil, puede usar la herramienta para ayudar a configurar las configuraciones de conexión de banda ancha móvil en IOT Core.</span><span class="sxs-lookup"><span data-stu-id="8dc40-106">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help setup configurations for mobile broadband connection in IoT Core.</span></span>

<span data-ttu-id="8dc40-107">`MBBConnect`Recupera la información relevante para la conexión, como el identificador del suscriptor, el identificador de ICC de SIM, el nombre de la interfaz y el nombre del proveedor de inicio, etc. A continuación, crea el perfil de conexión.</span><span class="sxs-lookup"><span data-stu-id="8dc40-107">`MBBConnect` retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="8dc40-108">Lo único que debe hacer es proporcionar el APN y el programa de instalación de la conexión automáticamente.</span><span class="sxs-lookup"><span data-stu-id="8dc40-108">The only thing you’ll need to do is to provide APN, and it’ll setup connection automatically.</span></span>

<span data-ttu-id="8dc40-109">`MBBConnect`se desarrolla y prueba con la puerta de enlace de IoT basada en MinnowBoard Max que ejecuta IoT Core versión 16299 y el módulo de módem de banda ancha móvil con la tarjeta SIM del proveedor de telecomunicaciones principal en Taiwán.</span><span class="sxs-lookup"><span data-stu-id="8dc40-109">`MBBConnect` is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="8dc40-110">Uso</span><span class="sxs-lookup"><span data-stu-id="8dc40-110">Usage</span></span>

1. <span data-ttu-id="8dc40-111">Copiar `MBBConnect.exe` a la puerta de enlace de IOT.</span><span class="sxs-lookup"><span data-stu-id="8dc40-111">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="8dc40-112">FTP</span><span class="sxs-lookup"><span data-stu-id="8dc40-112">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="8dc40-113">Conecte la puerta de enlace mediante PowerShell o SSH.</span><span class="sxs-lookup"><span data-stu-id="8dc40-113">Connect gateway by Powershell or SSH.</span></span>

   * [<span data-ttu-id="8dc40-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8dc40-114">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="8dc40-115">SSH</span><span class="sxs-lookup"><span data-stu-id="8dc40-115">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="8dc40-116">Cambie a la carpeta donde `MBBConnect.exe` se encuentra.</span><span class="sxs-lookup"><span data-stu-id="8dc40-116">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="8dc40-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8dc40-117">Example</span></span>
<span data-ttu-id="8dc40-118">En el ejemplo siguiente se usa MBBConnect. exe en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8dc40-118">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="8dc40-119">Por ejemplo, si el APN de la tarjeta SIM es "Internet", use `MBBConnect.exe Internet` para conectarse.</span><span class="sxs-lookup"><span data-stu-id="8dc40-119">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="8dc40-120">El mensaje de salida mostrará el flujo:</span><span class="sxs-lookup"><span data-stu-id="8dc40-120">The output message will show the flow:</span></span>

* <span data-ttu-id="8dc40-121">El estado cambia de no conectado a conectado.</span><span class="sxs-lookup"><span data-stu-id="8dc40-121">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="8dc40-122">La red WWAN está configurada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8dc40-122">WWAN network is configured successfully.</span></span>

<span data-ttu-id="8dc40-123">Pruebe el ejemplo de conexión de banda ancha móvil [aquí](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span><span class="sxs-lookup"><span data-stu-id="8dc40-123">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
