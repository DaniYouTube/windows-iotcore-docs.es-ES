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
# <a name="internet-connection-sharing"></a>Conexión compartida a Internet

Este documento describe cómo se puede habilitar la conexión de internet (ICS) en Windows IoT Core. Los desarrolladores pueden usar la API NetworkTetheringManager configurar ICS mediante programación. La API se describe en el [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) clase.
Al utilizar uno de los [imagen de lanzamiento de Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot/downloads) ICS también pueden configurarse mediante el portal de dispositivo.

> [!IMPORTANT]
> Primero se debe crear un perfil de Wi-Fi y lo siguiente debe agregarse al manifiesto:
`<DeviceCapability Name="wiFiControl" />`

Para el Tutorial de uso compartido, ver el [Windows IoT Core versión de noviembre de 2015](InternetConnectionSharingNov2015.md) documento.

## <a name="configuring-ics-using-the-device-portal"></a>Configurar ICS mediante device portal
Consulte la documentación en [Windows Device Portal](../manage-your-device/deviceportal.md) (WDP).

## <a name="ics-code-sample"></a>Ejemplo de código ICS
El ejemplo de código siguiente muestra cómo el [NetworkOperatorTetheringManager](https://msdn.microsoft.com/library/windows/apps/windows.networking.networkoperators.networkoperatortetheringmanager.aspx) API se usa para empezar a compartir una conexión Ethernet a través de Wi-Fi. El método CreateFromConnectionProfile acepta argumentos que especifica la interfaz pública y privada. En cualquier caso de una configuración incorrecta, como el radio de Wi-Fi se ha desactivado o Ethernet con una conectividad limitada, el intento de iniciar el uso compartido de internet transmite un código de error correspondiente que pertenecen a este escenario.

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
