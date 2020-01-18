---
title: Activación táctil
author: jordanrh1
ms.author: jordanrh
ms.date: 09/17/2018
ms.topic: article
description: Configuración del dispositivo para la reactivación táctil
keywords: Windows IOT, pantalla, suspensión, Wake, Touch, Standby, Power
ms.custom: RS5
ms.openlocfilehash: 11aaaeed721ff3df7d4b78a29ddb3d0f1b4aa732
ms.sourcegitcommit: 0fa10fafb13788496674d13e0ae810a6d93e3483
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2020
ms.locfileid: "76258536"
---
# <a name="configure-your-device-to-wake-on-touch"></a><span data-ttu-id="42744-104">Configuración del dispositivo para la reactivación táctil</span><span class="sxs-lookup"><span data-stu-id="42744-104">Configure your device to wake on touch</span></span>

<span data-ttu-id="42744-105">En algunos escenarios, quiere que la pantalla del dispositivo se apague mientras no esté en uso y se active rápidamente cuando un usuario toca la pantalla táctil.</span><span class="sxs-lookup"><span data-stu-id="42744-105">In some scenarios, you want your device's screen to turn off while not in use and to turn on quickly when a user touches the touchscreen.</span></span> <span data-ttu-id="42744-106">En este documento se describe cómo configurar el dispositivo para lograr este escenario.</span><span class="sxs-lookup"><span data-stu-id="42744-106">This document describes how to configure your device to achieve this scenario.</span></span>

## <a name="setting-a-video-idle-timeout"></a><span data-ttu-id="42744-107">Establecer un tiempo de espera de inactividad de vídeo</span><span class="sxs-lookup"><span data-stu-id="42744-107">Setting a video idle timeout</span></span>

<span data-ttu-id="42744-108">Puede configurar la pantalla para que se apague después de un período de inactividad mediante la configuración de un tiempo de espera de inactividad de vídeo.</span><span class="sxs-lookup"><span data-stu-id="42744-108">You can configure the screen to turn off after a period of inactivity by setting a video idle timeout.</span></span> <span data-ttu-id="42744-109">Cuando el usuario no ha interactuado con el dispositivo durante un período de tiempo especificado, la pantalla se apagará.</span><span class="sxs-lookup"><span data-stu-id="42744-109">When the user has not interacted with the device for a specified length of time, the screen will turn off.</span></span> <span data-ttu-id="42744-110">Esto permitirá que el dispositivo entre en un estado de energía baja apagando los componentes relacionados con la pantalla.</span><span class="sxs-lookup"><span data-stu-id="42744-110">This will enable the device to enter a low power state by powering down components related to the display.</span></span>

```powershell
    powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setdcvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 10
    powercfg.exe /setactive SCHEME_CURRENT
```

<span data-ttu-id="42744-111">Para obtener más información, vea Mostrar el tiempo de [espera de inactividad](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) y [Mostrar, suspender e hibernar temporizadores de inactividad](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span><span class="sxs-lookup"><span data-stu-id="42744-111">For more information, see [Display Idle Timeout](/windows-hardware/customize/power-settings/display-settings-display-idle-timeout) and [Display, sleep, and hibernate idle timers](/windows-hardware/design/device-experiences/display--sleep--and-hibernate-idle-timers).</span></span>

## <a name="disabling-modern-standby"></a><span data-ttu-id="42744-112">Deshabilitar el modo de espera moderno</span><span class="sxs-lookup"><span data-stu-id="42744-112">Disabling modern standby</span></span>

<span data-ttu-id="42744-113">En los sistemas AoAC (que incluyen todos los sistemas ARM), el sistema entrará automáticamente en [modo de espera moderno](/windows-hardware/design/device-experiences/modern-standby) cuando la pantalla se desactive.</span><span class="sxs-lookup"><span data-stu-id="42744-113">On AoAC systems (which includes all ARM systems), the system will automatically enter [modern standby](/windows-hardware/design/device-experiences/modern-standby) when the display goes off.</span></span> <span data-ttu-id="42744-114">Cuando un sistema se encuentra en modo de espera moderno, solo se puede reactivarán mediante ciertas entradas.</span><span class="sxs-lookup"><span data-stu-id="42744-114">When a system is in modern standby, it can only be woken by certain inputs.</span></span> <span data-ttu-id="42744-115">Esta no es una lista exhaustiva, pero estas entradas incluyen presionar el botón de encendido, abrir la tapa de un portátil o hacer clic con el mouse.</span><span class="sxs-lookup"><span data-stu-id="42744-115">This is not an exhaustive list, but these inputs include pressing the power button, opening the lid on a laptop, or clicking the mouse.</span></span> <span data-ttu-id="42744-116">Al tocar la pantalla no se reactivará el dispositivo desde el modo de espera moderno.</span><span class="sxs-lookup"><span data-stu-id="42744-116">Touching the screen will not wake up the device from modern standby.</span></span> <span data-ttu-id="42744-117">Si desea que el dispositivo se reactive mediante la función táctil, tiene que configurar el dispositivo para que no entre en modo de espera moderno.</span><span class="sxs-lookup"><span data-stu-id="42744-117">If you want your device to wake up by touch, you have to configure the device not to enter modern standby.</span></span> <span data-ttu-id="42744-118">Para deshabilitar el modo de espera moderno, establezca la siguiente clave del registro y reinicie el sistema.</span><span class="sxs-lookup"><span data-stu-id="42744-118">To disable modern standby, set the following registry key and reboot.</span></span>

```powershell
    reg add HKLM\System\CurrentControlSet\Control\Power /v PlatformAoAcOverride /t REG_DWORD /d 0
```
    
<span data-ttu-id="42744-119">Deshabilitar el modo de espera moderno puede afectar al consumo de energía cuando el sistema está inactivo.</span><span class="sxs-lookup"><span data-stu-id="42744-119">Disabling modern standby can impact power consumption when the system is idle.</span></span> <span data-ttu-id="42744-120">Debe medir el consumo de energía del sistema con el modo de espera moderno habilitado y deshabilitado antes de tomar la decisión de deshabilitar el modo de espera moderno.</span><span class="sxs-lookup"><span data-stu-id="42744-120">You should measure your system's power consumption with modern standby enabled and disabled before making the decision to disable modern standby.</span></span>

<span data-ttu-id="42744-121">El modo de espera moderno es un mecanismo de software que intenta deshacer la actividad del sistema lo máximo posible, lo que permite que el hardware entre en un estado de baja energía.</span><span class="sxs-lookup"><span data-stu-id="42744-121">Modern standby is a software mechanism that attempts to quiet system activity as much as possible, thereby allowing hardware to enter a low power state.</span></span> <span data-ttu-id="42744-122">En teoría, un dispositivo suficientemente silencioso con el modo de espera moderno deshabilitado puede lograr el mismo consumo de energía bajo que un dispositivo en el modo de espera moderno.</span><span class="sxs-lookup"><span data-stu-id="42744-122">In theory, a sufficiently quiet device with modern standby disabled can achieve the same low power consumption as a device in modern standby.</span></span> <span data-ttu-id="42744-123">Es importante minimizar la actividad en segundo plano, incluidos los temporizadores de software y las tareas periódicas, si está deshabilitado el modo de espera moderno.</span><span class="sxs-lookup"><span data-stu-id="42744-123">It is important to minimize background activity including software timers and periodic tasks if modern standby is disabled.</span></span>
