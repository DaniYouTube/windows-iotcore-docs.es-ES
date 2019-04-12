---
title: Herramienta de migración de Windows 10 IoT Core API
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar la herramienta de migración de Windows 10 IoT Core API para calcular los costos de migración.
keywords: Windows iot, API de migración de la herramienta, la portabilidad de API, los archivos binarios
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514604"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="672c9-104">Herramienta de migración de Windows 10 IoT Core API</span><span class="sxs-lookup"><span data-stu-id="672c9-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="672c9-105">Windows 10 IoT Core solo admite un subconjunto de la de Win32 y .net área expuesta de API disponible en diferentes versiones anteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="672c9-105">Windows 10 IoT Core only supports a subset of the Win32 and .Net API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="672c9-106">Esta herramienta examinará los archivos binarios y le entregará un informe de las API que use estos archivos binarios que no están disponibles y se ofrecen sugerencias para los reemplazos posibles.</span><span class="sxs-lookup"><span data-stu-id="672c9-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="672c9-107">Esto se ambos ayudar a estimar el costo de un puerto de IoT Core así como ayudarle a lo largo de la forma.</span><span class="sxs-lookup"><span data-stu-id="672c9-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="672c9-108">Uso</span><span class="sxs-lookup"><span data-stu-id="672c9-108">Usage</span></span>

<span data-ttu-id="672c9-109">La herramienta de migración de Windows 10 IoT Core API puede encontrarse en el [ms: iot/iot-utilidades](https://github.com/ms-iot/iot-utilities) repositorio de github.</span><span class="sxs-lookup"><span data-stu-id="672c9-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github repository.</span></span>  <span data-ttu-id="672c9-110">Descargue el [zip del repositorio](https://github.com/ms-iot/iot-utilities/archive/master.zip) y copie la carpeta IoTAPIPortingTool en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="672c9-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="672c9-111">Abra **IoTAPIPortingTool.sln** en Visual Studio 2017 y compile el proyecto.</span><span class="sxs-lookup"><span data-stu-id="672c9-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="672c9-112">Esto generará `IotAPIPortingTool.exe`.</span><span class="sxs-lookup"><span data-stu-id="672c9-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="672c9-113">Puede usar la herramienta mediante la ejecución de `IoTAPIPortingTool.exe <Application path> [-os]`.</span><span class="sxs-lookup"><span data-stu-id="672c9-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  `<Application path>` <span data-ttu-id="672c9-114">exe de la aplicación que se usa la herramienta de migración para</span><span class="sxs-lookup"><span data-stu-id="672c9-114">exe of application that porting tool is used for</span></span>

*  `-os` <span data-ttu-id="672c9-115">debe especificarse si no planea usar UWP.</span><span class="sxs-lookup"><span data-stu-id="672c9-115">should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="672c9-116">De forma predeterminada, la herramienta valida los archivos binarios en la plataforma UWP de Windows.</span><span class="sxs-lookup"><span data-stu-id="672c9-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE] 
> <span data-ttu-id="672c9-117">IoTAPIPortingTool.exe se debe ejecutar desde un símbolo del sistema de Visual Studio para desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="672c9-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="672c9-118">Necesita navegar hasta la carpeta que contiene el IotAPIPortingTool.exe.</span><span class="sxs-lookup"><span data-stu-id="672c9-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span> 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a><span data-ttu-id="672c9-119">Salida</span><span class="sxs-lookup"><span data-stu-id="672c9-119">Output</span></span>

<span data-ttu-id="672c9-120">La herramienta generará un archivo de archivo (csv) de valores separados por comas en la misma carpeta que contiene el `IotAPIPortingTool.exe`.</span><span class="sxs-lookup"><span data-stu-id="672c9-120">The tool will generate a comma separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="672c9-121">El archivo se denomina `IoTAPIPortingTool.csv` (o bien, `IoTAPIPortingToolOS.csv` si se especifica - sistema operativo) y será un resumen en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="672c9-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="672c9-122">Abra el `.csv` archivo en Excel para analizar la salida completa.</span><span class="sxs-lookup"><span data-stu-id="672c9-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
