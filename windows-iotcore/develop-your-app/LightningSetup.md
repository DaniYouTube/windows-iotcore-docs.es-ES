---
title: Guía de instalación de rayo
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo cambiar el controlador del controlador predeterminado del controlador relámpago DMAP en un dispositivo.
keywords: Windows iot, relámpago, el programa de instalación, el programa de instalación de rayos, Windows Device Portal
ms.openlocfilehash: 0997638b50f89fd42262df437623bd55380fbb5b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514700"
---
# <a name="lightning-setup-guide"></a><span data-ttu-id="6cecc-104">Guía de instalación de rayo</span><span class="sxs-lookup"><span data-stu-id="6cecc-104">Lightning Setup Guide</span></span>

<span data-ttu-id="6cecc-105">Esta guía le guiará por los pasos necesarios para cambiar el controlador del controlador predeterminado para el controlador de acceso asignado (DMAP) de memoria directa relámpago en un dispositivo Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="6cecc-105">This guide will walk you through the steps needed to change the default controller driver to the Lightning direct memory access mapped (DMAP) driver on a Windows IoT Core device.</span></span> <span data-ttu-id="6cecc-106">Esto permitirá que el uso de las aplicaciones habilitadas por el rayo en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6cecc-106">This will allow the use of Lightning-enabled applications on that device.</span></span>

## <a name="change-the-default-controller-driver"></a><span data-ttu-id="6cecc-107">Cambiar el controlador del controlador predeterminado</span><span class="sxs-lookup"><span data-stu-id="6cecc-107">Change the Default Controller Driver</span></span>

<span data-ttu-id="6cecc-108">Queremos abrir la Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="6cecc-108">We will want to open the Windows Device Portal.</span></span>

1. <span data-ttu-id="6cecc-109">Busque la dirección IP del dispositivo, ya sea mediante la aplicación de panel de Windows 10 IoT Core o la placa a un monitor de enlace.</span><span class="sxs-lookup"><span data-stu-id="6cecc-109">Locate the IP address of your device, either by using the Windows 10 IoT Core Dashboard application or hooking up your board to a monitor.</span></span>

2. <span data-ttu-id="6cecc-110">Desde el equipo local, abra la página web de Portal de dispositivos de Windows escribiendo esta http://{BoardIPAddress}:8080/ dirección en el explorador web.</span><span class="sxs-lookup"><span data-stu-id="6cecc-110">From your local machine, open the Windows Devices Portal web page by entering this address http://{BoardIPAddress}:8080/ in your web browser.</span></span>
   ![Portal de dispositivos de Windows](../media/LightningSetup/dmap1.png)

3. <span data-ttu-id="6cecc-112">La página de Portal de dispositivos de Windows debe pedir las credenciales.</span><span class="sxs-lookup"><span data-stu-id="6cecc-112">The Windows Devices Portal Page should ask you for your credentials.</span></span> <span data-ttu-id="6cecc-113">El nombre de usuario predeterminado es `Administrator` y la contraseña es `p@ssw0rd` tenga en cuenta que después de escribir el nombre de usuario y la contraseña, el Portal le preguntará si debe cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="6cecc-113">The default username is `Administrator` and password is `p@ssw0rd` Note, after entering the username and password, the Portal will ask you if you need to change the password.</span></span> <span data-ttu-id="6cecc-114">Siempre es una buena práctica para cambiarlo.</span><span class="sxs-lookup"><span data-stu-id="6cecc-114">It's always a good practice to change it.</span></span>
   ![Credenciales de Portal de dispositivos de Windows](../media/LightningSetup/dmap2.png)

4. <span data-ttu-id="6cecc-116">Haga clic en los dispositivos en el menú de navegación para abrir la página dispositivos ![página dispositivos](../media/LightningSetup/dmap3.png)</span><span class="sxs-lookup"><span data-stu-id="6cecc-116">Click on Devices in the navigation menu to open the Devices page ![Devices Page](../media/LightningSetup/dmap3.png)</span></span>

5. <span data-ttu-id="6cecc-117">La página de dispositivos enumera los controladores disponibles.</span><span class="sxs-lookup"><span data-stu-id="6cecc-117">The Devices page lists the available Controller drivers.</span></span> <span data-ttu-id="6cecc-118">De forma predeterminada, el controlador de bandeja de entrada se establece al actual.</span><span class="sxs-lookup"><span data-stu-id="6cecc-118">By default, the Inbox Driver is set to current.</span></span>

6. <span data-ttu-id="6cecc-119">Cambiar al controlador relámpago eligiendo el controlador de asignar memoria directa desde el menú desplegable y haga clic en el botón Actualizar controlador</span><span class="sxs-lookup"><span data-stu-id="6cecc-119">Switch to the Lightning driver by choosing the Direct Memory Mapped Driver from the drop down menu and click the Update Driver Button</span></span><br/>
   ![Seleccione el controlador asignado memoria directa](../media/LightningSetup/dmap4.png)

7. <span data-ttu-id="6cecc-121">Espere hasta que la página le permite saber cuando se completa la instalación del controlador.</span><span class="sxs-lookup"><span data-stu-id="6cecc-121">Please wait until the page lets you know when the driver installation is complete.</span></span>
   ![Instalación del controlador completa](../media/LightningSetup/dmap5.png)

8. <span data-ttu-id="6cecc-123">Si se requiere un reinicio, la página le permitirá saber también.</span><span class="sxs-lookup"><span data-stu-id="6cecc-123">If a reboot is required, the page will let you know as well.</span></span> <span data-ttu-id="6cecc-124">Puede reiniciar mediante el botón de reinicio en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="6cecc-124">You can reboot by using the Reboot button at the top of the page.</span></span>

9. <span data-ttu-id="6cecc-125">Ahora está listo para crear y usar aplicaciones hacen uso del controlador asignado en memoria directa relámpago.</span><span class="sxs-lookup"><span data-stu-id="6cecc-125">Now you're ready to create and use applications that make use of the Lightning Direct Memory Mapped driver.</span></span>
