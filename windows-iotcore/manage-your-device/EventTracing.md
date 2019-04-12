---
title: Seguimiento de eventos para Windows IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo utilizar el seguimiento de eventos para escribir los eventos y consumir eventos de Windows IoT Core.
keywords: Windows iot, seguimiento de eventos de seguimiento, ETW, event para dispositivos windows
ms.openlocfilehash: 7e01681e2af2ed8913614ba23bd12dfd36bcd76e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515192"
---
# <a name="event-tracing-for-windows-iot-core"></a><span data-ttu-id="1db7b-104">Seguimiento de eventos para Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="1db7b-104">Event Tracing for Windows IoT Core</span></span>

<span data-ttu-id="1db7b-105">Seguimiento de eventos para Windows (ETW) proporciona a los desarrolladores la capacidad de iniciar y detener las sesiones de seguimiento de eventos, instrumentar una aplicación para proporcionar eventos de seguimiento y consumir eventos de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="1db7b-105">Event Tracing for Windows (ETW) provides developers the ability to start and stop event tracing sessions, instrument an application to provide trace events, and consume trace events.</span></span>
<span data-ttu-id="1db7b-106">ETW en dispositivos de Windows IoT Core admite eventos basada en manifiestos y clásicos y no es diferente a otros dispositivos Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1db7b-106">ETW on Windows IoT Core devices supports both manifest-based and classic events, and is no different than other Windows 10 devices.</span></span>

<span data-ttu-id="1db7b-107">Esta sección proporciona vínculos útiles sobre los conceptos básicos de escritura y consumo de eventos.</span><span class="sxs-lookup"><span data-stu-id="1db7b-107">This section will provide useful links on the basics of writing and consuming events.</span></span> <span data-ttu-id="1db7b-108">Buscar la información más detallada de la [página seguimiento de eventos de Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1db7b-108">Find more detailed information from the [Windows Event Tracing page](https://msdn.microsoft.com/library/windows/desktop/bb968803(v=vs.85).aspx).</span></span>

## <a name="writing-events"></a><span data-ttu-id="1db7b-109">Eventos de escritura</span><span class="sxs-lookup"><span data-stu-id="1db7b-109">Writing Events</span></span>

<span data-ttu-id="1db7b-110">Buscar una UWP de ejemplo que implementa los distintos métodos de escritura de eventos como parte de la [Github de Windows Universal Samples](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span><span class="sxs-lookup"><span data-stu-id="1db7b-110">Find a UWP sample that implements the different methods of writing events as part of the [Windows Universal Samples Github](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Logging).</span></span>
<span data-ttu-id="1db7b-111">Esto se ejecutará en dispositivos de Windows IoT Core y también es una referencia de código de gran calidad.</span><span class="sxs-lookup"><span data-stu-id="1db7b-111">This will run on Windows IoT Core devices and is also a great code reference.</span></span>

<span data-ttu-id="1db7b-112">Guía detallada sobre la escritura de eventos y obtener el GUID puede encontrarse [aquí](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1db7b-112">Detailed guide on writing events and obtaining GUIDs can be found [here](https://msdn.microsoft.com/library/windows/desktop/aa364161(v=vs.85).aspx).</span></span>

## <a name="consuming-events"></a><span data-ttu-id="1db7b-113">Consumo de eventos</span><span class="sxs-lookup"><span data-stu-id="1db7b-113">Consuming Events</span></span>

<span data-ttu-id="1db7b-114">Los eventos se guardan en un archivo ETL o capturados en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="1db7b-114">Events are either saved to an ETL file or captured in real-time.</span></span>
<span data-ttu-id="1db7b-115">Use [FTP](../connect-your-device/FTP.md) o [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md) para recuperar los archivos ETL de dispositivos de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="1db7b-115">Use [FTP](../connect-your-device/FTP.md) or [Windows File Sharing](../manage-your-device/WindowsFileSharing.md) to retrieve ETL files from Windows IoT Core devices.</span></span>

## <a name="use-tools-in-windows-assessment-and-deployment-kit"></a><span data-ttu-id="1db7b-116">Usar herramientas en Windows Assessment and Deployment Kit</span><span class="sxs-lookup"><span data-stu-id="1db7b-116">Use Tools in Windows Assessment and Deployment Kit</span></span>

<span data-ttu-id="1db7b-117">Windows Assessment and Deployment Kit incluye 3 herramientas para ayudar a capturar y analizar eventos.</span><span class="sxs-lookup"><span data-stu-id="1db7b-117">Windows Assessment and Deployment Kit includes 3 tools to help capture and analyze events.</span></span> [<span data-ttu-id="1db7b-118">Haga clic aquí para descargar</span><span class="sxs-lookup"><span data-stu-id="1db7b-118">Click here to download</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=526740)


1. <span data-ttu-id="1db7b-119">**Windows Performance Analyzer** visualiza los archivos ETL en escritorio, con una guía paso a paso [aquí](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1db7b-119">**Windows Performance Analyzer** visualizes ETL files on desktop, with a step by step guide [here](https://msdn.microsoft.com/library/windows/hardware/dn927319(v=vs.85).aspx).</span></span>

2. <span data-ttu-id="1db7b-120">**Herramienta de línea de comandos Xperf** captura los eventos en tiempo real y los escribe en un archivo ETL.</span><span class="sxs-lookup"><span data-stu-id="1db7b-120">**Xperf command line tool** captures real-time events and writes them to an ETL file.</span></span> <span data-ttu-id="1db7b-121">Esta herramienta ya está instalada en los dispositivos de Windows IoT Core, simplemente ejecute los siguientes comandos en los dispositivos:</span><span class="sxs-lookup"><span data-stu-id="1db7b-121">This tool is already installed on Windows IoT Core devices, just run the following commands on the devices:</span></span>

        // Start capturing events from specific GUID and save them to an ETL file
        xperf -start <Session Name> -f <ETL File> -on <GUID>

        // Stop capturing events with the specified session name
        xperf -stop <Session Name>


3. <span data-ttu-id="1db7b-122">**Herramienta de línea de comandos tracerpt** convierte los archivos ETL en archivos xml.</span><span class="sxs-lookup"><span data-stu-id="1db7b-122">**Tracerpt command line tool** converts ETL files into xml files.</span></span>

        // Generate dumpfile.xml from ETL file
        tracerpt <ETL File>


## <a name="use-device-portal"></a><span data-ttu-id="1db7b-123">Use el Portal de dispositivo</span><span class="sxs-lookup"><span data-stu-id="1db7b-123">Use Device Portal</span></span>

<span data-ttu-id="1db7b-124">Portal de dispositivos puede capturar los eventos en tiempo real, con instrucciones [aquí](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span><span class="sxs-lookup"><span data-stu-id="1db7b-124">Device portal can capture events in real-time, with instructions [here](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal).</span></span>

> [!NOTE]
> <span data-ttu-id="1db7b-125">Este método no genera un archivo ETL para su posterior análisis, pero requiere una configuración mínima.</span><span class="sxs-lookup"><span data-stu-id="1db7b-125">This method does not produce an ETL file for further analysis, but requires minimal setup.</span></span>

## <a name="use-function-calls"></a><span data-ttu-id="1db7b-126">Usar llamadas de función</span><span class="sxs-lookup"><span data-stu-id="1db7b-126">Use Function Calls</span></span>

<span data-ttu-id="1db7b-127">Habilita una aplicación para consumir eventos desde un archivo ETL o en tiempo real mediante llamadas a la función.</span><span class="sxs-lookup"><span data-stu-id="1db7b-127">Enable an application to consume events from an ETL file or in real-time using function calls.</span></span>
<span data-ttu-id="1db7b-128">Aprenda a usar estas funciones [aquí](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="1db7b-128">Learn how to use these functions [here](https://msdn.microsoft.com/library/windows/desktop/aa363692(v=vs.85).aspx).</span></span>
