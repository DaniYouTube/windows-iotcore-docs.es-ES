---
title: Empezar a trabajar con el origen del ejemplo de servicio de respuesta de MDN
author: saraclay
ms.author: saclayt
ms.date: 02/26/2019
ms.topic: article
description: Obtenga información sobre cómo empezar a trabajar con el origen del ejemplo de servicio de respuesta de MDN.
keywords: Windows 10 IoT Core, origen de ejemplo de servicio de respuesta de MDN
ms.openlocfilehash: eacd22bf4d8a93948706e214fd48262c61c59a08
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514240"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="ffcda-104">Introducción a origen de ejemplo de servicio de respuesta de MDN</span><span class="sxs-lookup"><span data-stu-id="ffcda-104">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="ffcda-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="ffcda-105">Getting started</span></span>

1.  <span data-ttu-id="ffcda-106">Compile el proyecto *mDNSResponder* a mDNSResponder.exe get, que es un servicio.</span><span class="sxs-lookup"><span data-stu-id="ffcda-106">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="ffcda-107">Copie el archivo .exe en el equipo de destino, a continuación, registrar el servicio y ejecute.</span><span class="sxs-lookup"><span data-stu-id="ffcda-107">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="ffcda-108">Run “mDNSResponder.exe /?”</span><span class="sxs-lookup"><span data-stu-id="ffcda-108">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="ffcda-109">Para imprimir el uso</span><span class="sxs-lookup"><span data-stu-id="ffcda-109">to print the usage</span></span>
3.  <span data-ttu-id="ffcda-110">Compile el proyecto *dnssd*, generaría dnssd.dll</span><span class="sxs-lookup"><span data-stu-id="ffcda-110">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="ffcda-111">Compile el proyecto *mDNSUWP*.</span><span class="sxs-lookup"><span data-stu-id="ffcda-111">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="ffcda-112">Es un agente de UWP que se comunica con dnssd.dll y generará su propio archivo dll y winmd</span><span class="sxs-lookup"><span data-stu-id="ffcda-112">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="ffcda-113">Compile el proyecto *mDNSTest*, que es un ejemplo de aplicación para UWP para consumir mDNSUWP y finalmente se habla en el servicio mDNSResponder.</span><span class="sxs-lookup"><span data-stu-id="ffcda-113">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="ffcda-114">Esta aplicación para UWP depende dnssd.dll y el agente UWP (no hay secuencias de comandos configurada para copiar todo el contenido en la carpeta appx UWP)</span><span class="sxs-lookup"><span data-stu-id="ffcda-114">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="ffcda-115">Implementar inicio/mDNSTest, establecer un identificador y haga clic en Register, el código de respuesta debe ser 0 (correcto)</span><span class="sxs-lookup"><span data-stu-id="ffcda-115">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="ffcda-116">Si ejecuta cualquier explorador Bonjour al mismo tiempo, debe aparecer el nuevo dispositivo (falso).</span><span class="sxs-lookup"><span data-stu-id="ffcda-116">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![En el registro para MDN](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="ffcda-118">Recursos</span><span class="sxs-lookup"><span data-stu-id="ffcda-118">Resources</span></span>

* <span data-ttu-id="ffcda-119">Descargue los MDN Bonjour compatible con servicio de respuesta para Windows IoT (origen del ejemplo) [aquí](https://go.microsoft.com/fwlink/?linkid=2077676).</span><span class="sxs-lookup"><span data-stu-id="ffcda-119">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

