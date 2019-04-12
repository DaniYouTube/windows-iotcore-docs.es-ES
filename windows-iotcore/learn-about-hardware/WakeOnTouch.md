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
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="b4540-104">Configurar el dispositivo a reactivarse en táctil</span><span class="sxs-lookup"><span data-stu-id="b4540-104">Configure your device to wake on touch</span></span>

<span data-ttu-id="b4540-105">En algunos escenarios, que desea que la pantalla de su dispositivo para desactivar mientras no esté en uso y para activar rápidamente si un usuario toca la pantalla táctil.</span><span class="sxs-lookup"><span data-stu-id="b4540-105">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="b4540-106">Este documento describe cómo configurar el dispositivo para lograr este escenario.</span><span class="sxs-lookup"><span data-stu-id="b4540-106">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="b4540-107">Establecer un tiempo de espera de inactividad vídeo</span><span class="sxs-lookup"><span data-stu-id="b4540-107">Setting a video idle timeout</span></span>

<span data-ttu-id="b4540-108">Puede configurar la pantalla para desactivar estableciendo un tiempo de espera de inactividad vídeo tras un período de inactividad.</span><span class="sxs-lookup"><span data-stu-id="b4540-108">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="b4540-109">Cuando el usuario no ha interactuado con el dispositivo durante un período de tiempo especificado, se desactivará la pantalla.</span><span class="sxs-lookup"><span data-stu-id="b4540-109">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="b4540-110">Esto permitirá que el dispositivo entrar en un estado de bajo consumo de energía al apagar los componentes relacionados con la presentación.</span><span class="sxs-lookup"><span data-stu-id="b4540-110">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="b4540-111">Para obtener más información, consulte [Mostrar tiempo de espera inactivo](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) y [Display, suspensión e hibernación de los temporizadores de inactividad](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span><span class="sxs-lookup"><span data-stu-id="b4540-111">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="b4540-112">Deshabilitar standby moderna</span><span class="sxs-lookup"><span data-stu-id="b4540-112">Disabling modern standby</span></span>

<span data-ttu-id="b4540-113">En los sistemas AoAC (que incluye todos los sistemas ARM), especificará automáticamente el sistema [standby modernas](/windows-hardware/design/device-experiences/modern-standby) cuando sale de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="b4540-113">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="b4540-114">Cuando un sistema está en modo de espera moderna, solo se active ciertas entradas.</span><span class="sxs-lookup"><span data-stu-id="b4540-114">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="b4540-115">Esto no es una lista exhaustiva, pero estas entradas incluyen al presionar el botón de encendido, abriendo la tapa de un equipo portátil o hacer clic con el mouse.</span><span class="sxs-lookup"><span data-stu-id="b4540-115">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="b4540-116">Tocar la pantalla no se activará el dispositivo del modo de suspensión modernas.</span><span class="sxs-lookup"><span data-stu-id="b4540-116">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="b4540-117">Si desea que el dispositivo de reactivación con el tacto, tendrá que configurar el dispositivo para que no entra en suspensión modernas.</span><span class="sxs-lookup"><span data-stu-id="b4540-117">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="b4540-118">Para deshabilitar la suspensión modernos, establezca la siguiente clave del registro y reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="b4540-118">To disable modern standby, set the following registry key and reboot.</span></span>

```
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="b4540-119">Deshabilitar standby moderno puede afectar al consumo de energía cuando el sistema está inactivo.</span><span class="sxs-lookup"><span data-stu-id="b4540-119">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="b4540-120">Debe medir el consumo de energía del sistema con modernas espera habilitados y deshabilitados antes de tomar la decisión de deshabilitar standby modernas.</span><span class="sxs-lookup"><span data-stu-id="b4540-120">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="b4540-121">Standby moderna es un mecanismo de software que intenta la actividad del sistema silencioso tanto como sea posible, lo que permite que el hardware entrar en un estado de bajo consumo de energía.</span><span class="sxs-lookup"><span data-stu-id="b4540-121">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="b4540-122">En teoría, un dispositivo lo suficientemente silencioso con modernas deshabilitado en espera puede lograr el mismo bajo consumo de energía como un dispositivo en modo de espera modernas.</span><span class="sxs-lookup"><span data-stu-id="b4540-122">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="b4540-123">Es importante minimizar la actividad en segundo plano incluidos los temporizadores de software y las tareas periódicas si espera moderna está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="b4540-123">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
