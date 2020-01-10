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
# <a name="headed-and-headless-devices"></a>Dispositivos con cabeza y sin periféricos

Windows 10 IoT Core puede configurarse para el *modo de encabezado o sin* *cabeza* . 

## <a name="headed-mode"></a>Modo de punta
El modo de cabeza se define por la presencia de la interfaz de usuario. En el modo de *cabeza* , se iniciará una sola aplicación de interfaz de usuario en el arranque del sistema y también puede haber 0 o más "aplicaciones en segundo plano" (StartupTasks). 

## <a name="headless-mode"></a>Modo sin periféricos
El modo sin periféricos no tiene interfaz de usuario.  Los dispositivos que no necesitan la funcionalidad de la interfaz de usuario se pueden establecer en el modo sin *periféricos* . La pila de la interfaz de usuario está deshabilitada y las aplicaciones de IU no se iniciarán. Esto reduce la cantidad de recursos del sistema utilizados. Si conecta un monitor al dispositivo, la pantalla será negra.

> [!NOTE]
> Si coloca el dispositivo en el modo sin periféricos, puede usar la aplicación Windows 10 IoT Core Dashboard, que se describe a continuación, para encontrar su dirección IP.

## <a name="changing-the-mode"></a>Cambiar el modo
Puede modificar el estado de la cabeza o el estado de los dispositivos desde una sesión de Windows PowerShell o una sesión de SSH. Para obtener más información acerca de PowerShell, consulte la página [PowerShell para IOT Core](../connect-your-device/PowerShell.md) . Para más información sobre SSH, consulte la página [SSH para IOT Core](../connect-your-device/SSH.md) .

* Para mostrar el estado actual del dispositivo, use la utilidad `setbootoption`:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* Para modificar el estado del dispositivo para habilitar el modo sin periféricos, use la utilidad `setbootoption` con el `headless` Arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* Para modificar el estado del dispositivo para habilitar el modo de cabeza, use la utilidad `setbootoption` con el `headed` Arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>Búsqueda de un dispositivo sin periféricos

Un dispositivo de IoT Core que está en modo sin periférico se puede detectar mediante la aplicación **Windows 10 IOT Core Dashboard** .  Para descargar el panel de IoT, consulte la página de [descargas](https://go.microsoft.com/fwlink/?LinkID=708576) .
Cuando se ejecuta, la aplicación escucha los pings desde cualquier dispositivo de IoT Core en la red local y muestra información del dispositivo, como el nombre, la dirección IP, etc.

![Panel de Windows 10 IoT Core](../media/HeadlessMode/selectDevice.png)
