---
title: Seguimiento de eventos para Windows IoT Core
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar el seguimiento de eventos para escribir eventos y consumir eventos para Windows IoT Core.
keywords: Windows IOT, seguimiento de eventos, ETW, seguimiento de eventos para Windows, dispositivos
ms.openlocfilehash: e5d017c28640f78011ef0b7d82071a51524b2185
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721578"
---
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="aa796-104">Seguimiento de eventos para Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="aa796-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="aa796-105">Seguimiento de eventos para Windows (ETW) proporciona a los desarrolladores la capacidad de iniciar y detener sesiones de seguimiento de eventos, instrumentar una aplicación para proporcionar eventos de seguimiento y consumir eventos de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="aa796-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="aa796-106">ETW en dispositivos Windows IoT Core es compatible con eventos clásicos y basados en manifiestos, y no es diferente de otros dispositivos Windows 10.</span><span class="sxs-lookup"><span data-stu-id="aa796-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="aa796-107">En esta sección se proporcionan vínculos útiles sobre los aspectos básicos de la escritura y el consumo de eventos.</span><span class="sxs-lookup"><span data-stu-id="aa796-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="aa796-108">Busque información más detallada en la [Página de seguimiento de eventos de Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="aa796-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="aa796-109">Escribir eventos</span><span class="sxs-lookup"><span data-stu-id="aa796-109">Writing Events</span></span>

<span data-ttu-id="aa796-110">Busque un ejemplo de UWP que implemente los distintos métodos para escribir eventos como parte de los [ejemplos de Windows universal de github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span><span class="sxs-lookup"><span data-stu-id="aa796-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="aa796-111">Esto se ejecutará en dispositivos Windows IoT Core y también es una excelente referencia de código.</span><span class="sxs-lookup"><span data-stu-id="aa796-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="aa796-112">Puede encontrar una guía detallada sobre la escritura de eventos y la obtención de GUID [aquí](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="aa796-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="aa796-113">Consumir eventos</span><span class="sxs-lookup"><span data-stu-id="aa796-113">Consuming Events</span></span>

<span data-ttu-id="aa796-114">Los eventos se guardan en un archivo ETL o se capturan en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="aa796-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="aa796-115">Use [FTP](../connect-your-device/FTP.md) o el [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md) para recuperar archivos ETL desde dispositivos Windows IOT Core.</span><span class="sxs-lookup"><span data-stu-id="aa796-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="aa796-116">Usar herramientas en Windows Assessment and Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="aa796-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="aa796-117">Windows Assessment and Deployment Kit incluye 3 herramientas para ayudar a capturar y analizar eventos.</span><span class="sxs-lookup"><span data-stu-id="aa796-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="aa796-118">Haga clic aquí para descargar</span><span class="sxs-lookup"><span data-stu-id="aa796-118">Click here to download</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="aa796-119">El **analizador de rendimiento de Windows** visualiza archivos ETL en el escritorio, con una guía paso a paso [aquí](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="aa796-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="aa796-120">La **herramienta de línea de comandos Xperf** captura eventos en tiempo real y los escribe en un archivo ETL.</span><span class="sxs-lookup"><span data-stu-id="aa796-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="aa796-121">Esta herramienta ya está instalada en los dispositivos Windows IoT Core, solo tiene que ejecutar los siguientes comandos en los dispositivos:</span><span class="sxs-lookup"><span data-stu-id="aa796-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="aa796-122">**Tracerpt la herramienta de línea de comandos** convierte los archivos ETL en archivos XML.</span><span class="sxs-lookup"><span data-stu-id="aa796-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="aa796-123">Uso del portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="aa796-123">Use Device Portal</span></span>

<span data-ttu-id="aa796-124">El portal de dispositivos puede capturar eventos en tiempo real, con instrucciones [aquí](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span><span class="sxs-lookup"><span data-stu-id="aa796-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="aa796-125">Este método no genera un archivo ETL para su posterior análisis, pero requiere una configuración mínima.</span><span class="sxs-lookup"><span data-stu-id="aa796-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="aa796-126">Usar llamadas a función</span><span class="sxs-lookup"><span data-stu-id="aa796-126">Use Function Calls</span></span>

<span data-ttu-id="aa796-127">Permite que una aplicación consuma eventos de un archivo ETL o en tiempo real mediante llamadas a funciones.</span><span class="sxs-lookup"><span data-stu-id="aa796-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="aa796-128">Aprenda a usar estas funciones [aquí](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="aa796-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
