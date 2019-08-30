---
title: Pruebas de rendimiento de Lightning
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de la funcionalidad de Windows IoT Lightning y la frecuencia de alternancia para diferentes plataformas y lenguajes.
keywords: Windows IOT, Lightning rendimiento, funcionalidad de Lightning, GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744779"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="7916b-104">Pruebas de rendimiento de Windows IoT Lightning</span><span class="sxs-lookup"><span data-stu-id="7916b-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7916b-105">El equipo de IoT de Windows 10 ya no admite activamente Arduino.</span><span class="sxs-lookup"><span data-stu-id="7916b-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="7916b-106">El rendimiento de GPIO se probó para la funcionalidad de Windows IoT Lightning mediante una sencilla aplicación de alternancia de GPIO, [disponible aquí](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span><span class="sxs-lookup"><span data-stu-id="7916b-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="7916b-107">Las pruebas se realizaron alternando el GPIO 5 entre 0 y 1 a la velocidad más rápida posible.</span><span class="sxs-lookup"><span data-stu-id="7916b-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="7916b-108">La frecuencia de alternancia para cada caso se midió con un osciloscopio de Tektronix TPS 2024.</span><span class="sxs-lookup"><span data-stu-id="7916b-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="7916b-109">Los siguientes resultados se obtuvieron del análisis:</span><span class="sxs-lookup"><span data-stu-id="7916b-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="7916b-110">Plataforma probada</span><span class="sxs-lookup"><span data-stu-id="7916b-110">Platform Tested</span></span>                     | <span data-ttu-id="7916b-111">Lenguaje</span><span class="sxs-lookup"><span data-stu-id="7916b-111">Language</span></span>        | <span data-ttu-id="7916b-112">Frecuencia</span><span class="sxs-lookup"><span data-stu-id="7916b-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="7916b-113">Arduino uno</span><span class="sxs-lookup"><span data-stu-id="7916b-113">Arduino Uno</span></span>                         | <span data-ttu-id="7916b-114">Boceto de Arduino</span><span class="sxs-lookup"><span data-stu-id="7916b-114">Arduino Sketch</span></span>  | <span data-ttu-id="7916b-115">75,06 kHz</span><span class="sxs-lookup"><span data-stu-id="7916b-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="7916b-116">Pila nativa de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7916b-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="7916b-117">C#</span><span class="sxs-lookup"><span data-stu-id="7916b-117">C#</span></span>              | <span data-ttu-id="7916b-118">239 KHz</span><span class="sxs-lookup"><span data-stu-id="7916b-118">239 KHz</span></span>       |
> | <span data-ttu-id="7916b-119">Pila nativa de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7916b-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="7916b-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="7916b-120">C++/CX</span></span>          | <span data-ttu-id="7916b-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="7916b-121">278 kHz</span></span>       |
> | <span data-ttu-id="7916b-122">Pila nativa de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7916b-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="7916b-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="7916b-123">WinJS</span></span>           | <span data-ttu-id="7916b-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="7916b-124">34 kHz</span></span>        |
> | <span data-ttu-id="7916b-125">Cableado de Windows 10 IoT Core Arduino</span><span class="sxs-lookup"><span data-stu-id="7916b-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="7916b-126">Cableado de Arduino</span><span class="sxs-lookup"><span data-stu-id="7916b-126">Arduino Wiring</span></span>  | <span data-ttu-id="7916b-127">**7,36 MHz**</span><span class="sxs-lookup"><span data-stu-id="7916b-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="7916b-128">Pila DMAP de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7916b-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="7916b-129">C#</span><span class="sxs-lookup"><span data-stu-id="7916b-129">C#</span></span>              | <span data-ttu-id="7916b-130">**1,76 MHz**</span><span class="sxs-lookup"><span data-stu-id="7916b-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="7916b-131">Pila DMAP de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7916b-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="7916b-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="7916b-132">C++/CX</span></span>          | <span data-ttu-id="7916b-133">**3,78 MHz**</span><span class="sxs-lookup"><span data-stu-id="7916b-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="7916b-134">Pila DMAP de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="7916b-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="7916b-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="7916b-135">WinJS</span></span>           | <span data-ttu-id="7916b-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="7916b-136">42 kHz</span></span>        |

<span data-ttu-id="7916b-137">Las pruebas de Windows 10 IoT Core se ejecutaban en un Raspberry PI 3 con Windows 10 IoT Core Insider versión preliminar 15026 (nombre del código Redstone 2) y se crearon con Microsoft IoT Lightning SDK 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="7916b-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
