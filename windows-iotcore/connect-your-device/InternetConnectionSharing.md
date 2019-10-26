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
# <a name="internet-connection-sharing"></a>Conexión compartida a Internet

En este documento se describe cómo se puede habilitar la conexión compartida a Internet (ICS) en Windows IoT Core. Los desarrolladores pueden usar la API NetworkTetheringManager para configurar ICS mediante programación. La API se describe en la clase [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) .
Cuando se usa una de las imágenes de la [versión de IOT Core de Windows 10](https://developer.microsoft.com/en-us/windows/iot/downloads) , ICS también puede configurarse mediante el portal de dispositivos.

> [!IMPORTANT]
> Primero se debe crear un perfil de Wi-Fi y se deben agregar los siguientes elementos al manifiesto: `<DeviceCapability Name="wiFiControl" />`

Para ver el tutorial de uso compartido, consulte el documento de la [versión de Windows IOT Core de noviembre 2015](InternetConnectionSharingNov2015.md) .

## <a name="configuring-ics-using-the-device-portal"></a>Configuración de ICS mediante el portal de dispositivos
Consulte la documentación sobre [Windows Device portal](../manage-your-device/deviceportal.md) (WDP).

## <a name="ics-code-sample"></a>Ejemplo de código ICS
En el ejemplo de código siguiente se muestra cómo se usa la API de [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) para empezar a compartir una conexión Ethernet a través de Wi-Fi. El método CreateFromConnectionProfile acepta argumentos que especifican la interfaz pública y la privada. En cualquier caso de error de configuración, como el radio Wi-Fi está desactivado o Ethernet tiene una conectividad limitada, el intento de iniciar el uso compartido de Internet transmite un código de error adecuado relacionado con este escenario.

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
