---
title: Guía de instalación de Lightning
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo cambiar el controlador de controlador predeterminado para el controlador Lightning DMAP en un dispositivo.
keywords: Windows IOT, Lightning, instalación, Lightning, Windows Device portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167869"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="c37fc-104">Guía de instalación de Lightning</span><span class="sxs-lookup"><span data-stu-id="c37fc-104">Lightning Setup Guide</span></span>

<span data-ttu-id="c37fc-105">Esta guía le guiará a través de los pasos necesarios para cambiar el controlador de controlador predeterminado por el controlador de acceso directo a memoria asignado (DMAP) en un dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="c37fc-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="c37fc-106">Esto permitirá el uso de aplicaciones con un relámpago en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c37fc-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="c37fc-107">Cambiar el controlador de controlador predeterminado</span><span class="sxs-lookup"><span data-stu-id="c37fc-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="c37fc-108">Le interesaremos abrir el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="c37fc-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="c37fc-109">Busque la dirección IP del dispositivo, ya sea mediante el uso de la aplicación Windows 10 IoT Core Dashboard o enlazando el panel a un monitor.</span><span class="sxs-lookup"><span data-stu-id="c37fc-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="c37fc-110">En el equipo local, abra la página web del portal de dispositivos de Windows. para ello, escriba esta dirección http://{BoardIPAddress}: 8080/en el explorador Web.</span><span class="sxs-lookup"><span data-stu-id="c37fc-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   <span data-ttu-id="c37fc-111">![Portal de dispositivos Windows](../media/LightningSetup/dmap1.png)</span><span class="sxs-lookup"><span data-stu-id="c37fc-111">![Windows Devices Portal](../media/LightningSetup/dmap1.png)</span></span>

3. <span data-ttu-id="c37fc-112">La página del portal de dispositivos de Windows debe solicitar sus credenciales.</span><span class="sxs-lookup"><span data-stu-id="c37fc-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="c37fc-113">El nombre de usuario `Administrator` predeterminado es y `p@ssw0rd` la contraseña es Nota, después de escribir el nombre de usuario y la contraseña, el portal le preguntará si necesita cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="c37fc-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="c37fc-114">Siempre es una buena práctica cambiarla.</span><span class="sxs-lookup"><span data-stu-id="c37fc-114">It's always a good practice to change it.</span></span>
   <span data-ttu-id="c37fc-115">![Credenciales del portal de dispositivos Windows](../media/LightningSetup/dmap2.png)</span><span class="sxs-lookup"><span data-stu-id="c37fc-115">![Windows Devices Portal Credentials](../media/LightningSetup/dmap2.png)</span></span>

4. <span data-ttu-id="c37fc-116">Haga clic en dispositivos en el menú de navegación para abrir la ![página dispositivos página dispositivos.](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="c37fc-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="c37fc-117">La página dispositivos muestra los controladores de controlador disponibles.</span><span class="sxs-lookup"><span data-stu-id="c37fc-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="c37fc-118">De forma predeterminada, el controlador de bandeja de entrada se establece en actual.</span><span class="sxs-lookup"><span data-stu-id="c37fc-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="c37fc-119">Cambie al controlador de Lightning; para ello, elija el controlador asignación de memoria directa en el menú desplegable y haga clic en el botón Actualizar controlador.</span><span class="sxs-lookup"><span data-stu-id="c37fc-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   <span data-ttu-id="c37fc-120">![Seleccionar controlador asignado a memoria directa](../media/LightningSetup/dmap4.png)</span><span class="sxs-lookup"><span data-stu-id="c37fc-120">![Select Direct Memory Mapped Driver](../media/LightningSetup/dmap4.png)</span></span>

7. <span data-ttu-id="c37fc-121">Espere hasta que la página le permita saber cuándo se ha completado la instalación del controlador.</span><span class="sxs-lookup"><span data-stu-id="c37fc-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   <span data-ttu-id="c37fc-122">![Instalación de controladores completada](../media/LightningSetup/dmap5.png)</span><span class="sxs-lookup"><span data-stu-id="c37fc-122">![Driver Installation Complete](../media/LightningSetup/dmap5.png)</span></span>

8. <span data-ttu-id="c37fc-123">Si se requiere un reinicio, la página le indicará también.</span><span class="sxs-lookup"><span data-stu-id="c37fc-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="c37fc-124">Puede reiniciar con el botón reiniciar en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="c37fc-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="c37fc-125">Ahora está listo para crear y usar aplicaciones que usan el controlador asignado a la memoria de Lightning Direct.</span><span class="sxs-lookup"><span data-stu-id="c37fc-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
