---
title: Visualización remota
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo ver y controlar las aplicaciones de UWP de Windows 10 IoT Core de forma remota.
keywords: Windows IOT, UWP, pantalla remota, aplicaciones de UWP remotas
ms.openlocfilehash: c0e082284e5bceb6f1a7a87723e883ad6e552c4e
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917395"
---
# <a name="remote-display"></a>Visualización remota
Ver y controlar las aplicaciones de UWP de Windows 10 IoT Core de forma remota, desde un equipo de escritorio con Windows 10, tableta o teléfono

> [!WARNING]
> El cliente remoto de IoT de Windows es una característica solo para desarrolladores. No está prevista ni es compatible con dispositivos de producción.

> [!IMPORTANT]
> El cliente remoto de Windows IoT no funciona para Raspberry Pi. Use un panel con gráficos acelerados, como MinnowBoard Max o DragonBoard, o conecte un monitor para la visualización local.

## <a name="overview"></a>Introducción
___
La experiencia de pantalla remota es una herramienta de desarrollo que se usa para controlar de forma remota aplicaciones de UWP que se ejecutan en un dispositivo Windows 10 IoT Core.   

## <a name="setup"></a>Configuración
___
Para empezar, necesitará configurar un dispositivo de Windows 10 IoT Core con la compilación más reciente de Windows 10. [visite la página de introducción para](https://developer.microsoft.com/en-us/windows/iot/getstarted) configurar el panel.

La instalación es rápida y fácil: siga estos tres pasos para usar la tecnología de pantalla remota.

1. Asegúrese de que el dispositivo de IoT Core y el equipo de desarrollo se encuentran en la misma red y en un entorno seguro.

    Un método consiste en conectar el dispositivo directamente al portátil mediante un adaptador Ethernet USB que admita la característica de cruce automático.

1. Active la funcionalidad de pantalla remota en el dispositivo de Windows 10 IoT Core.
  
    Conecte el dispositivo a Internet y conéctese al portal de dispositivos de Windows.
  
    Elija la página "remota" de las opciones de la izquierda y active la casilla "habilitar ventana de IoT Remote Server".  El dispositivo ya está habilitado para la experiencia de visualización remota.
    ![habilitar la experiencia de visualización remota](../media/RemoteDisplay/enable-remote.png)

1. Instale el cliente remoto de Windows IoT en el dispositivo de Windows 10 complementario.
  
    Para permitir que un dispositivo de Windows 10 se conecte a su dispositivo de Windows 10 IoT Core, debe instalar la aplicación de la tienda.  Actualmente, la aplicación cliente remota de Windows IoT está disponible solo mediante vínculos y se puede encontrar [aquí](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).
    
    ![Instalación de la aplicación cliente](../media/RemoteDisplay/store-app.png)


1. Conéctese a su dispositivo Windows 10 IoT Core a través de la aplicación instalada.
  
    Ejecute la aplicación cliente remoto de Windows IoT en el dispositivo complementario de Windows 10.  En la pantalla conectar, escriba la dirección IP del dispositivo. Los dos dispositivos deben conectarse, la experiencia de la interfaz de usuario del dispositivo Windows 10 IoT Core en el dispositivo complementario.
    
    Ahora está conectado. A partir de este punto, se puede usar la función táctil y hacer clic en entrada en el dispositivo de Windows 10 complementario para controlar la aplicación Windows 10 IoT Core UWP.  
    ![Conectar dispositivo](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>Compatibilidad y ámbito
___
Para poder usar el cliente remoto de IoT, debe ejecutar la compilación más reciente de Windows 10 IoT Core en el dispositivo de destino y la aplicación cliente más reciente de la tienda. 
    
  
## <a name="troubleshooting"></a>de solución de problemas
___
El uso de la tecnología de pantalla remota es rápido y sencillo, pero todavía hay algunos problemas que pueden experimentar los usuarios.  Asegúrese de seguir las instrucciones de configuración anteriores de cerca. Si el problema persiste, consulte a continuación.

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>Cuando intento conectar, la aplicación cliente se dirige a una pantalla en blanco.
Las conexiones erróneas pueden deberse a una serie de problemas, pero hemos surgido un par de problemas más comunes:

1. Asegúrese de que está ejecutando la versión más reciente de Insider de Windows 10 IoT Core y la aplicación cliente remota de IoT.
1. En primer lugar, asegúrese de que el dispositivo de IoT se encuentra en la misma red que el dispositivo complementario.
    Compruebe que está ejecutando la última compilación Insider de Windows 10 IoT Core con el servidor remoto de Windows IoT habilitado.
1. Si este no es el problema, intente cambiar la resolución del dispositivo a algo que se garantiza que sea compatible, siga las instrucciones descritas en el paso 1 de la sección de configuración anterior para navegar al servidor Web del dispositivo.  En lugar de seleccionar "remoto" en el menú de la izquierda, permanezca en la página "Inicio" y desplácese hacia abajo hasta encontrar resolución.  Pruebe 800x600.
1. Si esto sigue sin solucionar el problema, puede que tenga un problema que se debe a que nunca se conecta el dispositivo a una pantalla externa.
    Esto hará que el dispositivo se considere como sin periféricos.  Para solucionar este error:
    * Expulse la tarjeta MicroSD y colóquela en el equipo
    * Editar el `<MicroSD card drive>:\config.txt`
    * Agregue las líneas siguientes:
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
