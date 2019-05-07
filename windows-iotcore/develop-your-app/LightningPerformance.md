---
title: Suma de las pruebas de rendimiento
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre la frecuencia de funcionalidad y activar o desactivar Windows IoT relámpago para diferentes plataformas y lenguajes.
keywords: Windows iot, rendimiento increíblemente, funcionalidad relámpago GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744779"
---
# <a name="windows-iot-lightning-performance-testing"></a><span data-ttu-id="3043e-104">Suma de las pruebas de rendimiento de IoT de Windows</span><span class="sxs-lookup"><span data-stu-id="3043e-104">Windows IoT Lightning Performance Testing</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3043e-105">El equipo de Windows 10 IoT activamente ya no es compatible con Arduino.</span><span class="sxs-lookup"><span data-stu-id="3043e-105">The Windows 10 IoT team is no longer actively supporting Arduino.</span></span>

<span data-ttu-id="3043e-106">Se ha probado el rendimiento de GPIO para la funcionalidad de Windows IoT relámpago mediante una aplicación sencilla de alternancia GPIO, [disponible aquí](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span><span class="sxs-lookup"><span data-stu-id="3043e-106">The GPIO performance was tested for Windows IoT Lightning functionality using a simple GPIO toggle app, [available here](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite).</span></span> <span data-ttu-id="3043e-107">Las pruebas se realizaron alternando GPIO 5 entre 0 y 1 a la mayor velocidad posible.</span><span class="sxs-lookup"><span data-stu-id="3043e-107">The tests were performed by toggling GPIO 5 between 0 and 1 at the fastest possible speed.</span></span> <span data-ttu-id="3043e-108">La frecuencia de alternancia para cada caso se midió mediante un osciloscopio de 2024 Tektronix TPS.</span><span class="sxs-lookup"><span data-stu-id="3043e-108">The toggle frequency for each case was measured using a Tektronix TPS 2024 Oscilloscope.</span></span>

<span data-ttu-id="3043e-109">Los siguientes resultados obtenidos del análisis:</span><span class="sxs-lookup"><span data-stu-id="3043e-109">The following results were obtained from the analysis:</span></span>

> | <span data-ttu-id="3043e-110">Plataforma de prueba</span><span class="sxs-lookup"><span data-stu-id="3043e-110">Platform Tested</span></span>                     | <span data-ttu-id="3043e-111">Lenguaje</span><span class="sxs-lookup"><span data-stu-id="3043e-111">Language</span></span>        | <span data-ttu-id="3043e-112">Frecuencia</span><span class="sxs-lookup"><span data-stu-id="3043e-112">Frequency</span></span>     |
> | ----------------------------------- | --------------- | ------------- |
> | <span data-ttu-id="3043e-113">Arduino Uno</span><span class="sxs-lookup"><span data-stu-id="3043e-113">Arduino Uno</span></span>                         | <span data-ttu-id="3043e-114">Boceto de Arduino</span><span class="sxs-lookup"><span data-stu-id="3043e-114">Arduino Sketch</span></span>  | <span data-ttu-id="3043e-115">75.06 kHz</span><span class="sxs-lookup"><span data-stu-id="3043e-115">75.06 kHz</span></span>     |
> | <span data-ttu-id="3043e-116">Pila nativa de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="3043e-116">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="3043e-117">C#</span><span class="sxs-lookup"><span data-stu-id="3043e-117">C#</span></span>              | <span data-ttu-id="3043e-118">239 KHz</span><span class="sxs-lookup"><span data-stu-id="3043e-118">239 KHz</span></span>       |
> | <span data-ttu-id="3043e-119">Pila nativa de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="3043e-119">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="3043e-120">C++/CX</span><span class="sxs-lookup"><span data-stu-id="3043e-120">C++/CX</span></span>          | <span data-ttu-id="3043e-121">278 kHz</span><span class="sxs-lookup"><span data-stu-id="3043e-121">278 kHz</span></span>       |
> | <span data-ttu-id="3043e-122">Pila nativa de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="3043e-122">Windows 10 IoT Core Native Stack</span></span>    | <span data-ttu-id="3043e-123">WinJS</span><span class="sxs-lookup"><span data-stu-id="3043e-123">WinJS</span></span>           | <span data-ttu-id="3043e-124">34 kHz</span><span class="sxs-lookup"><span data-stu-id="3043e-124">34 kHz</span></span>        |
> | <span data-ttu-id="3043e-125">Conexión de Arduino de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="3043e-125">Windows 10 IoT Core Arduino Wiring</span></span>  | <span data-ttu-id="3043e-126">Conexión de Arduino</span><span class="sxs-lookup"><span data-stu-id="3043e-126">Arduino Wiring</span></span>  | <span data-ttu-id="3043e-127">**7,36 MHz**</span><span class="sxs-lookup"><span data-stu-id="3043e-127">**7.36 MHz**</span></span>  |
> | <span data-ttu-id="3043e-128">Pila de Windows 10 IoT Core DMAP</span><span class="sxs-lookup"><span data-stu-id="3043e-128">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="3043e-129">C#</span><span class="sxs-lookup"><span data-stu-id="3043e-129">C#</span></span>              | <span data-ttu-id="3043e-130">**1.76 MHz**</span><span class="sxs-lookup"><span data-stu-id="3043e-130">**1.76 MHz**</span></span>  |
> | <span data-ttu-id="3043e-131">Pila de Windows 10 IoT Core DMAP</span><span class="sxs-lookup"><span data-stu-id="3043e-131">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="3043e-132">C++/CX</span><span class="sxs-lookup"><span data-stu-id="3043e-132">C++/CX</span></span>          | <span data-ttu-id="3043e-133">**3.78 MHz**</span><span class="sxs-lookup"><span data-stu-id="3043e-133">**3.78 MHz**</span></span>  |
> | <span data-ttu-id="3043e-134">Pila de Windows 10 IoT Core DMAP</span><span class="sxs-lookup"><span data-stu-id="3043e-134">Windows 10 IoT Core DMAP Stack</span></span>      | <span data-ttu-id="3043e-135">WinJS</span><span class="sxs-lookup"><span data-stu-id="3043e-135">WinJS</span></span>           | <span data-ttu-id="3043e-136">42 kHz</span><span class="sxs-lookup"><span data-stu-id="3043e-136">42 kHz</span></span>        |

<span data-ttu-id="3043e-137">Las pruebas de Windows 10 IoT Core estaban ejecutar en un Raspberry Pi 3 con Windows 10 IoT Core Insider Preview compilar 15026 (nombre código piedra rojiza 2) y creadas con Microsoft IoT relámpago SDK 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="3043e-137">Windows 10 IoT Core tests were run on a Raspberry Pi 3 using Windows 10 IoT Core Insider Preview Build 15026 (codename Redstone 2) and built using Microsoft IoT Lightning SDK 1.1.0.</span></span>
