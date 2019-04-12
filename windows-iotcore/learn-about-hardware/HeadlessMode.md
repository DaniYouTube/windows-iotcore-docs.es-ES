---
title: Dispositivos sin periféricos y puntas
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo configurar Windows IoT Core para el modo con cabezal o sin periféricos de los dispositivos.
keywords: Windows iot, pantallas, puntas sin periféricos, la interfaz de usuario
ms.openlocfilehash: 8ac0d7e06477836aa080af1b7556b054957d0cac
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514751"
---
# <a name="headed-and-headless-devices"></a>Dispositivos sin periféricos y puntas

Windows 10 IoT Core se pueden configurar para cualquiera *puntas* o *sin periféricos* modo. 

## <a name="headed-mode"></a>Modo con cabezal
Modo con cabezal está definido por la presencia de la interfaz de usuario. En *puntas* modo de una sola aplicación de interfaz de usuario se iniciará al arrancar el sistema y además puede ser 0 o más "aplicaciones en segundo plano" (StartupTasks). 

## <a name="headless-mode"></a>Modo "desatendido"
Modo "desatendido" no tiene ninguna interfaz de usuario.  Los dispositivos que no necesitan la funcionalidad de la interfaz de usuario se pueden establecer en *sin periféricos* modo. La pila de la interfaz de usuario está deshabilitada y no se iniciarán las aplicaciones de interfaz de usuario. Esto reduce la cantidad de recursos del sistema utilizados. Si conecta a un monitor a su dispositivo, la pantalla será negra.

> [!NOTE]
> Si coloca el dispositivo en modo "desatendido", a continuación, puede usar la aplicación de escritorio de Windows 10 IoT Core, descrita a continuación, para encontrar su dirección IP.

## <a name="changing-the-mode"></a>Cambiar el modo
Puede modificar el estado del dispositivo desde una sesión de Windows PowerShell o una sesión de SSH sin puntas periféricos. Para obtener más información acerca de PowerShell, vea el [PowerShell para IoT Core](../connect-your-device/PowerShell.md) página. Para obtener más información acerca de SSH, consulte el [SSH para IoT Core](../connect-your-device/SSH.md) página.

* Para mostrar el estado actual del dispositivo, use el `setbootoption` utilidad:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe
~~~

* Para modificar el estado del dispositivo para habilitar el modo "desatendido", utilice el `setbootoption` utilidad con el `headless` arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headless
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

* Para modificar el estado del dispositivo al modo de habilitar puntas, use el `setbootoption` utilidad con el `headed` arg:

~~~
    [192.168.0.243]: PS C:\> setbootoption.exe headed
    [192.168.0.243]: PS C:\> shutdown /r /t 0
~~~

## <a name="finding-your-headless-device"></a>Buscar el dispositivo sin periféricos

Se puede detectar un dispositivo de IoT Core que esté en modo "desatendido" mediante la **panel de Windows 10 IoT Core** aplicación.  Para descargar el panel de IoT, consulte el [descargas](http://go.microsoft.com/fwlink/?LinkID=708576) página.
Cuando se ejecuta, la aplicación escucha pings desde los dispositivos de IoT Core en la red local y muestra información de dispositivo como el nombre, dirección IP y mucho más.

![Panel de Windows 10 IoT Core](../media/HeadlessMode/selectDevice.png)
