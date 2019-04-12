---
title: Visualización remota
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo ver y controlar las aplicaciones de Windows 10 IoT Core UWP de forma remota.
keywords: aplicaciones Windows iot, UWP, visualización remota, remotas, UWP
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514787"
---
# <a name="remote-display"></a>Visualización remota
Ver y controlar las aplicaciones de Windows 10 IoT Core UWP de forma remota, desde un equipo de escritorio de Windows 10, tableta o teléfono

> [!WARNING]
> Cliente de Windows IoT remoto es una característica única de desarrollador. No está diseñada ni compatible con dispositivos de producción.

> [!IMPORTANT]
> El cliente de Windows IoT remoto no funciona para Raspberry Pi. Usar un panel con gráficos acelerados como Minnowboard Max o Dragonboard o adjuntar a un monitor para visualización local.

## <a name="overview"></a>Información general
___
La experiencia de pantalla remota es una herramienta de desarrollo que se usa para controlar de forma remota aplicaciones de UWP que se ejecutan en un dispositivo Windows 10 IoT Core.   

## <a name="setup"></a>Programa de instalación
___
Para empezar, deberá configurar un dispositivo Windows 10 IoT Core con la compilación más reciente de Windows 10: visite el [comenzar](https://developer.microsoft.com/en-us/windows/iot/getstarted) página para configurar la placa.

El programa de instalación es rápido y sencillo, siga estos tres pasos para usar la tecnología de pantalla remota.

1. Asegúrese de que el equipo de desarrollo y el dispositivo de IoT Core están en la misma red y n un entorno seguro.

    Es un método conectar el dispositivo directamente a su equipo portátil con un adaptador Ethernet USB que admite cruzado automática.

1. Activar la funcionalidad de visualización remota en el dispositivo Windows 10 IoT Core.
  
    Conecte el dispositivo a Internet y conectarse a Windows Device Portal.
  
    Elija la página "Remoto" en las opciones de la izquierda y marque la casilla "Habilitar ventana IoT Remote Server".  El dispositivo ahora está habilitado para la experiencia de pantalla remota.
    ![Habilitar la experiencia de visualización remota](../media/RemoteDisplay/enable-remote.png)

1. Instale al cliente remoto de Windows IoT en su dispositivo complementario de Windows 10.
  
    Para habilitar un dispositivo Windows 10 para conectarse a su dispositivo Windows 10 IoT Core, deberá instalar la aplicación Store.  La aplicación cliente de Windows IoT remoto está disponible actualmente solo el vínculo y pueden encontrarse [aquí](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz).
    
    ![Instalar la aplicación cliente](../media/RemoteDisplay/store-app.png)


1. Conectarse al dispositivo de Windows 10 IoT Core a través de la aplicación instalada.
  
    Ejecute la aplicación cliente remota de Windows IoT en el dispositivo complementario de Windows 10.  En la pantalla de conexión, escriba la dirección IP del dispositivo. Debe conectar los dos dispositivos, comunicación remota de la experiencia de interfaz de usuario del dispositivo Windows 10 IoT Core para el dispositivo complementario.
    
    Ahora está conectado. Desde este punto reenviar, táctil y haga clic en la entrada en el dispositivo puede usarse para controlar la aplicación de Windows 10 IoT Core UWP de Windows 10 complementario.  
    ![Conexión de dispositivo](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>Compatibilidad y ámbito
___
Para poder usar al cliente remoto de IoT, debe estar ejecutando la última compilación de Windows 10 IoT Core en el dispositivo de destino y la aplicación de cliente más reciente desde el almacén de. 
    
  
## <a name="troubleshooting"></a>Solución de problemas
___
Con la tecnología de pantalla remota es rápido y sencillo, pero todavía hay algunos problemas que pueden experimentar los usuarios.  Asegúrese de seguir la configuración de instrucciones anteriores estrechamente - si el problema persiste, consulte los siguientes.

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>Al intentar conectarse, la aplicación cliente pasa a una pantalla en blanco.
Las conexiones con error pueden deberse a una serie de problemas, pero hemos ejecutado en un par problemas más comunes:

1. Asegúrese de que se están ejecutando a la insider más reciente versión de Windows 10 IoT Core y la aplicación cliente remota de IoT.
1. En primer lugar, asegúrese de que el dispositivo de IoT se encuentra en la misma red que el dispositivo complementario.
    Compruebe que está ejecutando la última compilación de Insider de Windows 10 IoT Core con el servidor remoto de Windows IoT habilitado.
1. Si esto no es el problema, pruebe a cambiar la resolución del dispositivo a algo estamos garantiza la compatibilidad siga las instrucciones que aparecen en el paso 1 de la sección de configuración anterior para desplazarse al servidor web de su dispositivo.  En lugar de seleccionar "Remoto" en el menú de la izquierda, permanecer en la página "Inicio" y desplácese hacia abajo para encontrar la resolución.  Pruebe a 800 x 600.
1. Si todavía no se soluciona el problema, puede que tenga un problema que proviene de nunca conectar su dispositivo a una pantalla externa.
    Esto hará que el dispositivo a pensar en sí mismo como puramente sin periféricos.  Para solucionar este error:
    * Expulse la tarjeta MicroSD y colocan en el equipo
    * Editar el `<MicroSD card drive>:\config.txt`
    * Agregue las siguientes líneas:
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
