---
title: Conexión de banda ancha móvil
author: saraclay
ms.author: saclayt
ms.date: 06/12/18
ms.topic: article
description: Obtenga información sobre cómo usar Mobile Broadband conexión para Windows 10 IoT Core.
keywords: conexión de banda ancha móvil de Windows iot, MBB,
ms.openlocfilehash: 3afa48e049e38f7e26308434ba6f7349ac0be050
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514888"
---
## <a name="mobile-broadband-connection"></a><span data-ttu-id="0f987-104">Conexión de banda ancha móvil</span><span class="sxs-lookup"><span data-stu-id="0f987-104">Mobile Broadband Connection</span></span>

<span data-ttu-id="0f987-105">Conexión de banda ancha móvil es compatible con [Windows 10 IoT Core](http://windowsondevices.com).</span><span class="sxs-lookup"><span data-stu-id="0f987-105">Mobile Broadband Connection is supported on [Windows 10 IoT Core](http://windowsondevices.com).</span></span> <span data-ttu-id="0f987-106">Si la puerta de enlace de IoT es compatible con el módulo de módem de banda ancha móvil, puede usar el `MBBConnect` herramienta para ayudar a configuraciones de instalación para la conexión de banda ancha móvil en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="0f987-106">If your IoT gateway supports the mobile broadband modem module, you can use the `MBBConnect` tool to help setup configurations for mobile broadband connection in IoT Core.</span></span>

`MBBConnect` <span data-ttu-id="0f987-107">Recupera la información relevante para conectar, por ejemplo, Id. de suscriptor, Id. de ICC SIM, nombre de la interfaz y nombre del proveedor de inicio, etcetera. A continuación, crea el perfil de conexión.</span><span class="sxs-lookup"><span data-stu-id="0f987-107">retrieves the relevant information for connect, such as subscriber ID, SIM ICC ID, interface name, and home provider name, etc. Then, it creates the connection profile.</span></span> <span data-ttu-id="0f987-108">Lo único que necesita hacer es proporcionar APN y podrá configurar la conexión automáticamente.</span><span class="sxs-lookup"><span data-stu-id="0f987-108">The only thing you’ll need to do is to provide APN, and it’ll setup connection automatically.</span></span>

`MBBConnect` <span data-ttu-id="0f987-109">está desarrollado y probado con MinnowBoard máximo en función de puerta de enlace de IoT con IoT Core versión 16299 y el módulo de módem de banda ancha móvil con la tarjeta SIM de proveedor de telecomunicaciones principales de Taiwán.</span><span class="sxs-lookup"><span data-stu-id="0f987-109">is developed and tested with MinnowBoard Max based IoT gateway running IoT Core version 16299 and the mobile broadband modem module with the SIM card from major telecom provider in Taiwan.</span></span>

### <a name="usage"></a><span data-ttu-id="0f987-110">Uso</span><span class="sxs-lookup"><span data-stu-id="0f987-110">Usage</span></span>

1. <span data-ttu-id="0f987-111">Copia `MBBConnect.exe` a puerta de enlace de IoT.</span><span class="sxs-lookup"><span data-stu-id="0f987-111">Copy `MBBConnect.exe` to IoT gateway.</span></span>

   * [<span data-ttu-id="0f987-112">FTP</span><span class="sxs-lookup"><span data-stu-id="0f987-112">FTP</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/ftp)

2. <span data-ttu-id="0f987-113">Conectar la puerta de enlace mediante Powershell o SSH.</span><span class="sxs-lookup"><span data-stu-id="0f987-113">Connect gateway by Powershell or SSH.</span></span>

   * [<span data-ttu-id="0f987-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f987-114">PowerShell</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell)

   * [<span data-ttu-id="0f987-115">SSH</span><span class="sxs-lookup"><span data-stu-id="0f987-115">SSH</span></span>](https://docs.microsoft.com/windows/iot-core/connect-your-device/SSH)

3. <span data-ttu-id="0f987-116">Cambie a la carpeta donde `MBBConnect.exe` se encuentra.</span><span class="sxs-lookup"><span data-stu-id="0f987-116">Switch to the folder where `MBBConnect.exe` is located.</span></span> 
   ```
   Command: MBBConnect.exe <APN name>
   <APN name>: It depends on your SIM card’s provider. 
   ```

### <a name="example"></a><span data-ttu-id="0f987-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0f987-117">Example</span></span>
<span data-ttu-id="0f987-118">El ejemplo siguiente utiliza MBBConnect.exe en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f987-118">The example below uses MBBConnect.exe in PowerShell.</span></span> <span data-ttu-id="0f987-119">Por ejemplo, si el APN de la tarjeta SIM es "Internet", use `MBBConnect.exe Internet` para conectarse.</span><span class="sxs-lookup"><span data-stu-id="0f987-119">For example, if the APN of the SIM card is “Internet”, use `MBBConnect.exe Internet` to connect.</span></span>
 
<span data-ttu-id="0f987-120">El mensaje de salida muestra el flujo:</span><span class="sxs-lookup"><span data-stu-id="0f987-120">The output message will show the flow:</span></span>

* <span data-ttu-id="0f987-121">Se cambia el estado de no conectado a conectado.</span><span class="sxs-lookup"><span data-stu-id="0f987-121">The state is changed from Not Connected to Connected.</span></span> 

* <span data-ttu-id="0f987-122">Red WWAN está configurado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0f987-122">WWAN network is configured successfully.</span></span>

<span data-ttu-id="0f987-123">Pruebe el ejemplo para la conexión de banda ancha móvil [aquí](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span><span class="sxs-lookup"><span data-stu-id="0f987-123">Try the sample for Mobile Broadband Connection [here](https://github.com/ms-iot/iot-utilities/tree/master/MBBConnect).</span></span>
