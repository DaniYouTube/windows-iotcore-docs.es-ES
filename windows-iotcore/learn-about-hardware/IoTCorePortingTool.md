---
title: Herramienta de migración de Windows 10 IoT Core API
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar la herramienta de migración de la API de IoT Core de Windows 10 para calcular los costos de portabilidad.
keywords: Windows IOT, herramienta de portabilidad de API, portabilidad de API, binarios
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169633"
---
# <a name="windows-10-iot-core-api-porting-tool"></a><span data-ttu-id="b1ade-104">Herramienta de migración de Windows 10 IoT Core API</span><span class="sxs-lookup"><span data-stu-id="b1ade-104">Windows 10 IoT Core API Porting Tool</span></span>

<span data-ttu-id="b1ade-105">Windows 10 IoT Core solo admite un subconjunto del área expuesta de la API de Win32 y .net disponible en varias versiones anteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="b1ade-105">Windows 10 IoT Core only supports a subset of the Win32 and .Net API surface area available on various prior versions of Windows.</span></span> <span data-ttu-id="b1ade-106">Esta herramienta examinará los archivos binarios y le proporcionará un informe de las API que usan estos archivos binarios que no están disponibles y ofrecen sugerencias para posibles reemplazos.</span><span class="sxs-lookup"><span data-stu-id="b1ade-106">This tool will scan your binaries and give you a report of the APIs these binaries use that aren't available and give suggestions for possible replacements.</span></span> <span data-ttu-id="b1ade-107">Esto le ayudará a calcular el costo de un puerto a IoT Core, así como a ayudarle durante el proceso.</span><span class="sxs-lookup"><span data-stu-id="b1ade-107">This will both help with estimating the cost of a port to IoT Core as well as help you along the way.</span></span>


## <a name="usage"></a><span data-ttu-id="b1ade-108">Uso</span><span class="sxs-lookup"><span data-stu-id="b1ade-108">Usage</span></span>

<span data-ttu-id="b1ade-109">La herramienta de portabilidad de la API de IoT Core de Windows 10 se puede encontrar en el repositorio de github [MS-IOT/IOT-Utilities](https://github.com/ms-iot/iot-utilities) .</span><span class="sxs-lookup"><span data-stu-id="b1ade-109">The Windows 10 IoT Core API Porting Tool can be found in the [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github repository.</span></span>  <span data-ttu-id="b1ade-110">Descargue el archivo [zip del repositorio](https://github.com/ms-iot/iot-utilities/archive/master.zip) y copie la carpeta IoTAPIPortingTool en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="b1ade-110">Download the [repository zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) and copy the IoTAPIPortingTool folder to your local machine.</span></span>  <span data-ttu-id="b1ade-111">Abra **IoTAPIPortingTool. sln** en Visual Studio 2017 y compile el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b1ade-111">Open **IoTAPIPortingTool.sln** in Visual Studio 2017 and build the project.</span></span>  <span data-ttu-id="b1ade-112">Se generará `IotAPIPortingTool.exe`.</span><span class="sxs-lookup"><span data-stu-id="b1ade-112">This will generate `IotAPIPortingTool.exe`.</span></span>

<span data-ttu-id="b1ade-113">Puede usar la herramienta ejecutando `IoTAPIPortingTool.exe <Application path> [-os]`.</span><span class="sxs-lookup"><span data-stu-id="b1ade-113">You can use the tool by running `IoTAPIPortingTool.exe <Application path> [-os]`.</span></span>

*  <span data-ttu-id="b1ade-114">`<Application path>`exe de la aplicación para la que se usa la herramienta de migración</span><span class="sxs-lookup"><span data-stu-id="b1ade-114">`<Application path>` exe of application that porting tool is used for</span></span>

*  <span data-ttu-id="b1ade-115">`-os`debe especificarse si no tiene previsto usar UWP.</span><span class="sxs-lookup"><span data-stu-id="b1ade-115">`-os` should be specified if you are not planning to use UWP.</span></span>  <span data-ttu-id="b1ade-116">De forma predeterminada, la herramienta valida los archivos binarios con la plataforma UWP de Windows.</span><span class="sxs-lookup"><span data-stu-id="b1ade-116">By default, the tool validates your binaries against the Windows UWP platform.</span></span>

> [!NOTE] 
> <span data-ttu-id="b1ade-117">IoTAPIPortingTool. exe se debe ejecutar desde un Símbolo del sistema para desarrolladores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1ade-117">IoTAPIPortingTool.exe must be run from a Visual Studio Developer Command Prompt.</span></span> <span data-ttu-id="b1ade-118">Debe navegar hasta la carpeta que contiene IotAPIPortingTool. exe.</span><span class="sxs-lookup"><span data-stu-id="b1ade-118">You need to navigate to the folder that contains the IotAPIPortingTool.exe.</span></span> 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a><span data-ttu-id="b1ade-119">Salida</span><span class="sxs-lookup"><span data-stu-id="b1ade-119">Output</span></span>

<span data-ttu-id="b1ade-120">La herramienta generará un archivo de valores separados por comas (CSV) en la misma `IotAPIPortingTool.exe`carpeta que contiene el.</span><span class="sxs-lookup"><span data-stu-id="b1ade-120">The tool will generate a comma separated values (csv) file in same folder that contains the `IotAPIPortingTool.exe`.</span></span> <span data-ttu-id="b1ade-121">El archivo se denomina `IoTAPIPortingTool.csv` (o, `IoTAPIPortingToolOS.csv` si se especifica-os) y se mostrará un resumen en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="b1ade-121">The file is named `IoTAPIPortingTool.csv` (or, `IoTAPIPortingToolOS.csv` if -os is specified) and a summary will be on the command line.</span></span> <span data-ttu-id="b1ade-122">Abra el `.csv` archivo en Excel para analizar la salida completa.</span><span class="sxs-lookup"><span data-stu-id="b1ade-122">Open the `.csv` file in Excel to analyze the complete output.</span></span>
