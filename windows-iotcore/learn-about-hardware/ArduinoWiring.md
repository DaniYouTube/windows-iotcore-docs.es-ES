---
title: Conexión de Arduino para dispositivos de Windows IoT Core
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: Aprenda a crear, implementar y depurar el cableado Arduino dibujos en los dispositivos compatibles de Windows IoT Core.
keywords: Windows iot, Arduino, Arduino cableado, plantilla, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744797"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a><span data-ttu-id="99444-104">Conexión de Arduino para dispositivos de Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="99444-104">Arduino Wiring for Windows IoT Core Devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99444-105">El equipo de Windows 10 IoT activamente ya no es mantener Arduino.</span><span class="sxs-lookup"><span data-stu-id="99444-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="99444-106">Para habilitar el desarrollo y la reutilización de la conocida [Arduino cableado](https://www.arduino.cc/en/Reference/HomePage) dibujos en los dispositivos de IoT Core, una plantilla de proyecto de Visual Studio para la conexión de Arduino se proporciona como parte de la [plantillas de proyecto de Windows IoT Core extensión](https://go.microsoft.com/fwlink/?linkid=847472).</span><span class="sxs-lookup"><span data-stu-id="99444-106">To enable the development and reuse of the familiar [Arduino Wiring](https://www.arduino.cc/en/Reference/HomePage) sketches on IoT Core devices, a Visual Studio project template for Arduino Wiring is provided as part of the [Windows IoT Core Project Templates extension](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>

<span data-ttu-id="99444-107">La plantilla de proyecto de cableado Arduino permite a los desarrolladores y responsables de crear, implementar y depurar bocetos de conexión de Arduino en dispositivos IoT Core compatibles con la misma semántica de lenguaje de conexión de Arduino y construye disponible en las plataformas de Arduino.</span><span class="sxs-lookup"><span data-stu-id="99444-107">The Arduino Wiring project template enables developers and makers to create, deploy and debug Arduino Wiring sketches on supported IoT Core devices using the same Arduino Wiring language semantics and constructs available on Arduino platforms.</span></span> <span data-ttu-id="99444-108">No solo Esto puede ayudar bocetos de puerto existentes Arduino a IoT Core con un costo muy pequeño, pero bocetos de Arduino de cableado que se ejecutan en IoT Core son aplicaciones de Windows 10 completas que pueden hacer uso de la API de plataforma de Windows de universal (UWP).</span><span class="sxs-lookup"><span data-stu-id="99444-108">Not only this can help port existing Arduino sketches to IoT Core with very little cost, but Arduino Wiring sketches running on IoT Core are full Windows 10 apps that can make use of the Univeral Windows Platform (UWP) API.</span></span> <span data-ttu-id="99444-109">Por lo tanto, Arduino cableado bocetos tienen acceso total a las API, como la comunicación, acceso a datos, redes, gráficos, entre muchas otras cosas, que se puede usar para crear escenarios de extremo a extremo que se ejecutan en dispositivos Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="99444-109">So, Arduino Wiring sketches have full access to APIs such as communication, data access, networking, graphics, among many others, which can be used to create end to end scenarios running on Windows 10 IoT Core devices.</span></span> <span data-ttu-id="99444-110">Para obtener más información sobre el desarrollo de aplicaciones de Universal Windows Platform (UWP), consulte [compilar aplicaciones para Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span><span class="sxs-lookup"><span data-stu-id="99444-110">For more information on developing Universal Windows Platform (UWP) Apps, please refer to [Building Applications for Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span></span>

<span data-ttu-id="99444-111">Además, usar Arduino cableado hacer bocetos de controlador asignado memoria directa que ofrece un alto rendimiento en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="99444-111">Additionally, Arduino Wiring sketches make use of a direct memory mapped driver that offers high performance on supported devices.</span></span> <span data-ttu-id="99444-112">Para obtener más detalles sobre los detalles de rendimiento, consulte el [pruebas de rendimiento de Windows IoT relámpago](../develop-your-app/LightningPerformance.md) informes.</span><span class="sxs-lookup"><span data-stu-id="99444-112">For more details on performance details, please refer to the [Windows IoT Lightning Performance Testing](../develop-your-app/LightningPerformance.md) report.</span></span>

<span data-ttu-id="99444-113">Para empezar a crear proyectos de conexión de Arduino para Raspberry Pi2, Pi3 o Minnowboard Max, consulte el [Guía de proyecto de cableado Arduino](ArduinoWiringProjectGuide.md).</span><span class="sxs-lookup"><span data-stu-id="99444-113">To start building Arduino Wiring projects for Raspberry Pi2, Pi3 or Minnowboard Max, please refer to the [Arduino Wiring project guide](ArduinoWiringProjectGuide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="99444-114">Conexión de Arduino es *no* admite actualmente en DragonBoard 410 c.</span><span class="sxs-lookup"><span data-stu-id="99444-114">Arduino Wiring is *not* currently supported on DragonBoard 410c.</span></span>
