---
title: Introducción al origen de ejemplo de respondedor de mDNS
ms.date: 02/26/2019
ms.topic: article
description: Obtenga información sobre cómo empezar a usar el origen de ejemplo de respondedor de mDNS.
keywords: Windows 10 IoT Core, origen de ejemplo de respondedor de mDNS
ms.openlocfilehash: ca99a217ade4c55c6d3050134af8d5663d8d1621
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917337"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a><span data-ttu-id="6dee7-104">Introducción al origen de ejemplo de respondedor de mDNS</span><span class="sxs-lookup"><span data-stu-id="6dee7-104">Getting Started with mDNS Responder Sample Source</span></span>

## <a name="getting-started"></a><span data-ttu-id="6dee7-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="6dee7-105">Getting started</span></span>

1.  <span data-ttu-id="6dee7-106">Compile el elemento *mDNSResponder* del proyecto para obtener mDNSResponder.exe, que es un servicio.</span><span class="sxs-lookup"><span data-stu-id="6dee7-106">Compile the project *mDNSResponder* to get mDNSResponder.exe, which is a service.</span></span> <span data-ttu-id="6dee7-107">Copie el archivo .exe en el equipo de destino y, después, registre el servicio y ejecútelo.</span><span class="sxs-lookup"><span data-stu-id="6dee7-107">Copy the .exe to the target machine then register the service and run.</span></span>
2. <span data-ttu-id="6dee7-108">Ejecute "mDNSResponder.exe /?"</span><span class="sxs-lookup"><span data-stu-id="6dee7-108">Run “mDNSResponder.exe /?”</span></span> <span data-ttu-id="6dee7-109">para imprimir el uso.</span><span class="sxs-lookup"><span data-stu-id="6dee7-109">to print the usage</span></span>
3.  <span data-ttu-id="6dee7-110">Compile *dnssd* del proyecto, que generará el archivo dnssd.dll.</span><span class="sxs-lookup"><span data-stu-id="6dee7-110">Compile the project *dnssd*, it would generate dnssd.dll</span></span>
4.  <span data-ttu-id="6dee7-111">Compile *mDNSUWP* del proyecto.</span><span class="sxs-lookup"><span data-stu-id="6dee7-111">Compile the project *mDNSUWP*.</span></span> <span data-ttu-id="6dee7-112">Es un agente de UWP que se comunica con dnssd.dll y que generará sus propios archivos dll y winmd.</span><span class="sxs-lookup"><span data-stu-id="6dee7-112">It’s a UWP broker that talks to dnssd.dll and will generate its own dll and winmd</span></span>
5.  <span data-ttu-id="6dee7-113">Compile *mDNSTest* del proyecto, que es una aplicación para UWP de ejemplo para consumir mDNSUWP y que, en última instancia, se comunica con el servicio mDNSResponder.</span><span class="sxs-lookup"><span data-stu-id="6dee7-113">Compile the project *mDNSTest*, which is a sample UWP app to consume mDNSUWP and eventually talks into mDNSResponder service.</span></span>
6.  <span data-ttu-id="6dee7-114">Esta aplicación para UWP depende de dnssd.dll y del agente de UWP (hay un script configurado para copiar todo el contenido en la carpeta appx de UWP).</span><span class="sxs-lookup"><span data-stu-id="6dee7-114">This UWP app depends on both dnssd.dll and the UWP broker (there is script configured to copy everything into the UWP appx folder)</span></span>
7.  <span data-ttu-id="6dee7-115">Implemente o inicie mDNSTest, establezca un identificador y haga clic en Registrar; el código de respuesta debe ser 0 (CORRECTO).</span><span class="sxs-lookup"><span data-stu-id="6dee7-115">Deploy/launch mDNSTest, set an ID and click Register, the respond code should be 0 (SUCCESS)</span></span>
8.  <span data-ttu-id="6dee7-116">Si ejecuta cualquier explorador Bonjour al mismo tiempo, debería aparecer el nuevo dispositivo (falso).</span><span class="sxs-lookup"><span data-stu-id="6dee7-116">If you run any Bonjour Browser at the same time, the new (fake) device should be listed.</span></span>

![Registro de mDNS](media/mDNS/mDNS1.png)

## <a name="resources"></a><span data-ttu-id="6dee7-118">Recursos</span><span class="sxs-lookup"><span data-stu-id="6dee7-118">Resources</span></span>

* <span data-ttu-id="6dee7-119">Descargue [aquí](https://go.microsoft.com/fwlink/?linkid=2077676) el respondedor de mDNS compatible con Bonjour para Windows IoT (código fuente de ejemplo).</span><span class="sxs-lookup"><span data-stu-id="6dee7-119">Download the Bonjour-compatible mDNS Responder for Windows IoT (sample source) [here](https://go.microsoft.com/fwlink/?linkid=2077676).</span></span>

