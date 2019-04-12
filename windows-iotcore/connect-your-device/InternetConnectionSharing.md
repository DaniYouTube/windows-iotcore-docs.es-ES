---
title: Conexión compartida a Internet
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo habilitar y configurar la conexión a internet de uso compartido en Windows IoT Core.
keywords: Windows iot, conexión compartida a Internet, ICS, Device Portal
ms.openlocfilehash: dcf51d98bc618c1a843c43b2d33fc8f832ef73d4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514587"
---
# <a name="internet-connection-sharing"></a><span data-ttu-id="b75bf-104">Conexión compartida a Internet</span><span class="sxs-lookup"><span data-stu-id="b75bf-104">Internet connection sharing</span></span>

<span data-ttu-id="b75bf-105">Este documento describe cómo se puede habilitar la conexión de internet (ICS) en Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="b75bf-105">This document describes how internet connection sharing (ICS) can be enabled on Windows IoT Core.</span></span> <span data-ttu-id="b75bf-106">Los desarrolladores pueden usar la API NetworkTetheringManager configurar ICS mediante programación.</span><span class="sxs-lookup"><span data-stu-id="b75bf-106">Developers can use the NetworkTetheringManager API to configure ICS programmatically.</span></span> <span data-ttu-id="b75bf-107">La API se describe en el [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) clase.</span><span class="sxs-lookup"><span data-stu-id="b75bf-107">The API is described in the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) class.</span></span>
<span data-ttu-id="b75bf-108">Al utilizar uno de los [imagen de lanzamiento de Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS también pueden configurarse mediante el portal de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b75bf-108">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS can also be configured using the device portal.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b75bf-109">Primero se debe crear un perfil de Wi-Fi y lo siguiente debe agregarse al manifiesto:</span><span class="sxs-lookup"><span data-stu-id="b75bf-109">A WiFi profile must be created first and the following will need to be added to the manifest:</span></span>
`<DeviceCapability Name="wiFiControl" />`

<span data-ttu-id="b75bf-110">Para el Tutorial de uso compartido, ver el [Windows IoT Core versión de noviembre de 2015](InternetConnectionSharingNov2015.md) documento.</span><span class="sxs-lookup"><span data-stu-id="b75bf-110">For the Sharing Tutorial, please view the [Windows IoT Core November 2015 Release](InternetConnectionSharingNov2015.md) document.</span></span>

## <a name="configuring-ics-using-the-device-portal"></a><span data-ttu-id="b75bf-111">Configurar ICS mediante device portal</span><span class="sxs-lookup"><span data-stu-id="b75bf-111">Configuring ICS using the device portal</span></span>
<span data-ttu-id="b75bf-112">Consulte la documentación en [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span><span class="sxs-lookup"><span data-stu-id="b75bf-112">See documentation on [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span></span>

## <a name="ics-code-sample"></a><span data-ttu-id="b75bf-113">Ejemplo de código ICS</span><span class="sxs-lookup"><span data-stu-id="b75bf-113">ICS code sample</span></span>
<span data-ttu-id="b75bf-114">El ejemplo de código siguiente muestra cómo el [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API se usa para empezar a compartir una conexión Ethernet a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="b75bf-114">The code sample below demonstrates how the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API is used to start sharing an Ethernet connection over Wi-Fi.</span></span> <span data-ttu-id="b75bf-115">El método CreateFromConnectionProfile acepta argumentos que especifica la interfaz pública y privada.</span><span class="sxs-lookup"><span data-stu-id="b75bf-115">The CreateFromConnectionProfile method accepts arguments that specifies the public and private interface.</span></span> <span data-ttu-id="b75bf-116">En cualquier caso de una configuración incorrecta, como el radio de Wi-Fi se ha desactivado o Ethernet con una conectividad limitada, el intento de iniciar el uso compartido de internet transmite un código de error correspondiente que pertenecen a este escenario.</span><span class="sxs-lookup"><span data-stu-id="b75bf-116">In any cases of misconfiguration, such as the Wi-Fi radio is turned off, or Ethernet has limited connectivity, then the attempt to start internet sharing conveys an appropriate error code pertaining to this scenario.</span></span>

```
using Windows.Networking.NetworkOperators;
using Windows.Networking.Connectivity; 
 
// Find the Ethernet profile (IANA Type 6)
var connectionProfiles = NetworkInformation.GetConnectionProfiles(); 
var ethernetConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 6); 

// Find an 802.11 wireless network interface (IANA Type 71)
var wirelessConnectionProfile = connectionProfiles.FirstOrDefault(x => x.NetworkAdapter.IanaInterfaceType == 71);
var targetNetworkAdapter = wirelessConnectionProfile.NetworkAdapter;

if (ethernetConnectionProfile != null && targetNetworkAdapter != null)
{
    var tetheringManager = NetworkOperatorTetheringManager.CreateFromConnectionProfile(ethernetConnectionProfile, targetNetworkAdapter); 

    var result = await tetheringManager.StartTetheringAsync(); 
    if (result.Status == TetheringOperationStatus.Success)
    {
        UpdateUI();
    }
    else
    {
        ProcessTetheringError(result);
    }
}
```
