---
title: Conexión compartida a Internet
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo habilitar y configurar la conexión compartida a Internet en Windows IoT Core.
keywords: Windows IOT, conexión compartida a Internet, ICS, portal de dispositivos
ms.openlocfilehash: 6392ef8b6216b9e622e308f8e1988655ebebee53
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918579"
---
# <a name="internet-connection-sharing"></a><span data-ttu-id="58f5d-104">Conexión compartida a Internet</span><span class="sxs-lookup"><span data-stu-id="58f5d-104">Internet connection sharing</span></span>

<span data-ttu-id="58f5d-105">En este documento se describe cómo se puede habilitar la conexión compartida a Internet (ICS) en Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="58f5d-105">This document describes how internet connection sharing (ICS) can be enabled on Windows IoT Core.</span></span> <span data-ttu-id="58f5d-106">Los desarrolladores pueden usar la API NetworkTetheringManager para configurar ICS mediante programación.</span><span class="sxs-lookup"><span data-stu-id="58f5d-106">Developers can use the NetworkTetheringManager API to configure ICS programmatically.</span></span> <span data-ttu-id="58f5d-107">La API se describe en la clase [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) .</span><span class="sxs-lookup"><span data-stu-id="58f5d-107">The API is described in the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) class.</span></span>
<span data-ttu-id="58f5d-108">Cuando se usa una de las imágenes de la [versión de IOT Core de Windows 10](https://developer.microsoft.com/en-us/windows/iot/downloads) , ICS también puede configurarse mediante el portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="58f5d-108">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS can also be configured using the device portal.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58f5d-109">Primero se debe crear un perfil de Wi-Fi y se deben agregar los siguientes elementos al manifiesto: `<DeviceCapability Name="wiFiControl" />`</span><span class="sxs-lookup"><span data-stu-id="58f5d-109">A WiFi profile must be created first and the following will need to be added to the manifest: `<DeviceCapability Name="wiFiControl" />`</span></span>

<span data-ttu-id="58f5d-110">Para ver el tutorial de uso compartido, consulte el documento de la [versión de Windows IOT Core de noviembre 2015](InternetConnectionSharingNov2015.md) .</span><span class="sxs-lookup"><span data-stu-id="58f5d-110">For the Sharing Tutorial, please view the [Windows IoT Core November 2015 Release](InternetConnectionSharingNov2015.md) document.</span></span>

## <a name="configuring-ics-using-the-device-portal"></a><span data-ttu-id="58f5d-111">Configuración de ICS mediante el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="58f5d-111">Configuring ICS using the device portal</span></span>
<span data-ttu-id="58f5d-112">Consulte la documentación sobre [Windows Device portal](../manage-your-device/deviceportal.md) (WDP).</span><span class="sxs-lookup"><span data-stu-id="58f5d-112">See documentation on [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).</span></span>

## <a name="ics-code-sample"></a><span data-ttu-id="58f5d-113">Ejemplo de código ICS</span><span class="sxs-lookup"><span data-stu-id="58f5d-113">ICS code sample</span></span>
<span data-ttu-id="58f5d-114">En el ejemplo de código siguiente se muestra cómo se usa la API de [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) para empezar a compartir una conexión Ethernet a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="58f5d-114">The code sample below demonstrates how the [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API is used to start sharing an Ethernet connection over Wi-Fi.</span></span> <span data-ttu-id="58f5d-115">El método CreateFromConnectionProfile acepta argumentos que especifican la interfaz pública y la privada.</span><span class="sxs-lookup"><span data-stu-id="58f5d-115">The CreateFromConnectionProfile method accepts arguments that specifies the public and private interface.</span></span> <span data-ttu-id="58f5d-116">En cualquier caso de error de configuración, como el radio Wi-Fi está desactivado o Ethernet tiene una conectividad limitada, el intento de iniciar el uso compartido de Internet transmite un código de error adecuado relacionado con este escenario.</span><span class="sxs-lookup"><span data-stu-id="58f5d-116">In any cases of misconfiguration, such as the Wi-Fi radio is turned off, or Ethernet has limited connectivity, then the attempt to start internet sharing conveys an appropriate error code pertaining to this scenario.</span></span>

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
