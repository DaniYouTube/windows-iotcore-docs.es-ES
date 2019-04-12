---
title: Wake on táctil
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: Configurar el dispositivo a reactivarse en táctil
keywords: Windows iot, pantalla, suspensión, wake, toque, en espera, energía
ms.custom: RS5
ms.openlocfilehash: 7c0fc9613f1b1ed45fb8d69a18d82b034eb366fb
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514612"
---
# <a name="configure-your-device-to-wake-on-touch"></a>Configurar el dispositivo a reactivarse en táctil

En algunos escenarios, que desea que la pantalla de su dispositivo para desactivar mientras no esté en uso y para activar rápidamente si un usuario toca la pantalla táctil. Este documento describe cómo configurar el dispositivo para lograr este escenario.

## <a name="setting-a-video-idle-timeout"></a>Establecer un tiempo de espera de inactividad vídeo

Puede configurar la pantalla para desactivar estableciendo un tiempo de espera de inactividad vídeo tras un período de inactividad. Cuando el usuario no ha interactuado con el dispositivo durante un período de tiempo especificado, se desactivará la pantalla. Esto permitirá que el dispositivo entrar en un estado de bajo consumo de energía al apagar los componentes relacionados con la presentación.

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

Para obtener más información, consulte [Mostrar tiempo de espera inactivo](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) y [Display, suspensión e hibernación de los temporizadores de inactividad](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).

## <a name="disabling-modern-standby"></a>Deshabilitar standby moderna

En los sistemas AoAC (que incluye todos los sistemas ARM), especificará automáticamente el sistema [standby modernas](/windows-hardware/design/device-experiences/modern-standby) cuando sale de la pantalla. Cuando un sistema está en modo de espera moderna, solo se active ciertas entradas. Esto no es una lista exhaustiva, pero estas entradas incluyen al presionar el botón de encendido, abriendo la tapa de un equipo portátil o hacer clic con el mouse. Tocar la pantalla no se activará el dispositivo del modo de suspensión modernas. Si desea que el dispositivo de reactivación con el tacto, tendrá que configurar el dispositivo para que no entra en suspensión modernas. Para deshabilitar la suspensión modernos, establezca la siguiente clave del registro y reiniciar el equipo.

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
Deshabilitar standby moderno puede afectar al consumo de energía cuando el sistema está inactivo. Debe medir el consumo de energía del sistema con modernas espera habilitados y deshabilitados antes de tomar la decisión de deshabilitar standby modernas.

Standby moderna es un mecanismo de software que intenta la actividad del sistema silencioso tanto como sea posible, lo que permite que el hardware entrar en un estado de bajo consumo de energía. En teoría, un dispositivo lo suficientemente silencioso con modernas deshabilitado en espera puede lograr el mismo bajo consumo de energía como un dispositivo en modo de espera modernas. Es importante minimizar la actividad en segundo plano incluidos los temporizadores de software y las tareas periódicas si espera moderna está deshabilitado.
