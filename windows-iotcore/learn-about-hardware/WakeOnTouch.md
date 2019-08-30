---
title: Activación táctil
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: Configuración del dispositivo para la reactivación táctil
keywords: Windows IOT, pantalla, suspensión, Wake, Touch, Standby, Power
ms.custom: RS5
ms.openlocfilehash: 7c0fc9613f1b1ed45fb8d69a18d82b034eb366fb
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167643"
---
# <a name="configure-your-device-to-wake-on-touch"></a>Configuración del dispositivo para la reactivación táctil

En algunos escenarios, quiere que la pantalla del dispositivo se apague mientras no esté en uso y se active rápidamente cuando un usuario toca la pantalla táctil. En este documento se describe cómo configurar el dispositivo para lograr este escenario.

## <a name="setting-a-video-idle-timeout"></a>Establecer un tiempo de espera de inactividad de vídeo

Puede configurar la pantalla para que se apague después de un período de inactividad mediante la configuración de un tiempo de espera de inactividad de vídeo. Cuando el usuario no ha interactuado con el dispositivo durante un período de tiempo especificado, la pantalla se apagará. Esto permitirá que el dispositivo entre en un estado de energía baja apagando los componentes relacionados con la pantalla.

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

Para obtener más información, vea Mostrar el tiempo de [espera](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) de inactividad y [Mostrar, suspender e hibernar temporizadores](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers)de inactividad.

## <a name="disabling-modern-standby"></a>Deshabilitar el modo de espera moderno

En los sistemas AoAC (que incluyen todos los sistemas ARM), el sistema entrará automáticamente en [modo de espera moderno](/windows-hardware/design/device-experiences/modern-standby) cuando la pantalla se desactive. Cuando un sistema se encuentra en modo de espera moderno, solo se puede reactivarán mediante ciertas entradas. Esta no es una lista exhaustiva, pero estas entradas incluyen presionar el botón de encendido, abrir la tapa de un portátil o hacer clic con el mouse. Al tocar la pantalla no se reactivará el dispositivo desde el modo de espera moderno. Si desea que el dispositivo se reactive mediante la función táctil, tiene que configurar el dispositivo para que no entre en modo de espera moderno. Para deshabilitar el modo de espera moderno, establezca la siguiente clave del registro y reinicie el sistema.

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
Deshabilitar el modo de espera moderno puede afectar al consumo de energía cuando el sistema está inactivo. Debe medir el consumo de energía del sistema con el modo de espera moderno habilitado y deshabilitado antes de tomar la decisión de deshabilitar el modo de espera moderno.

El modo de espera moderno es un mecanismo de software que intenta deshacer la actividad del sistema lo máximo posible, lo que permite que el hardware entre en un estado de baja energía. En teoría, un dispositivo suficientemente silencioso con el modo de espera moderno deshabilitado puede lograr el mismo consumo de energía bajo que un dispositivo en el modo de espera moderno. Es importante minimizar la actividad en segundo plano, incluidos los temporizadores de software y las tareas periódicas, si está deshabilitado el modo de espera moderno.
