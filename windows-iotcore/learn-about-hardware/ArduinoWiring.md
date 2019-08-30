---
title: Cableado Arduino para dispositivos Windows IoT Core
author: msalehmsft
ms.author: msaleh
ms.date: 09/06/17
ms.topic: article
description: Obtenga información sobre cómo crear, implementar y depurar bocetos de cableado de Arduino en dispositivos Windows IoT Core compatibles.
keywords: Windows IOT, Arduino, Arduino de conexión, plantilla, IoT Core, UWP
ms.openlocfilehash: ee6c64bdfd01e79d26bfa0a6c5f88f7735150393
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744797"
---
# <a name="arduino-wiring-for-windows-iot-core-devices"></a><span data-ttu-id="3226c-104">Cableado Arduino para dispositivos Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="3226c-104">Arduino Wiring for Windows IoT Core Devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3226c-105">El equipo de IoT de Windows 10 ya no mantiene de forma activa Arduino.</span><span class="sxs-lookup"><span data-stu-id="3226c-105">The Windows 10 IoT team is no longer actively maintaining Arduino.</span></span>

<span data-ttu-id="3226c-106">Para permitir el desarrollo y reutilización de los bocetos de [cableado de Arduino](https://www.arduino.cc/en/Reference/HomePage) conocidos en los dispositivos IOT Core, se proporciona una plantilla de proyecto de Visual Studio para el cableado Arduino como parte de la extensión de plantillas de [proyecto de Windows IOT Core](https://go.microsoft.com/fwlink/?linkid=847472).</span><span class="sxs-lookup"><span data-stu-id="3226c-106">To enable the development and reuse of the familiar [Arduino Wiring](https://www.arduino.cc/en/Reference/HomePage) sketches on IoT Core devices, a Visual Studio project template for Arduino Wiring is provided as part of the [Windows IoT Core Project Templates extension](https://go.microsoft.com/fwlink/?linkid=847472).</span></span>

<span data-ttu-id="3226c-107">La plantilla de proyecto de cableado de Arduino permite a los desarrolladores y a los desarrolladores crear, implementar y depurar bocetos de cableado de Arduino en dispositivos IoT Core compatibles con la misma semántica de lenguaje de cableado Arduino y construcciones disponibles en plataformas Arduino.</span><span class="sxs-lookup"><span data-stu-id="3226c-107">The Arduino Wiring project template enables developers and makers to create, deploy and debug Arduino Wiring sketches on supported IoT Core devices using the same Arduino Wiring language semantics and constructs available on Arduino platforms.</span></span> <span data-ttu-id="3226c-108">No solo esto puede ayudarle a migrar bocetos de Arduino existentes a IoT Core con muy poco costo, pero los bocetos de cableado de Arduino que se ejecutan en IoT Core son aplicaciones completas de Windows 10 que pueden hacer uso de la API de la plataforma universal de Windows (UWP).</span><span class="sxs-lookup"><span data-stu-id="3226c-108">Not only this can help port existing Arduino sketches to IoT Core with very little cost, but Arduino Wiring sketches running on IoT Core are full Windows 10 apps that can make use of the Univeral Windows Platform (UWP) API.</span></span> <span data-ttu-id="3226c-109">Por lo tanto, los bocetos de cableado de Arduino tienen acceso total a las API como la comunicación, el acceso a datos, las redes, los gráficos, entre muchos otros, que se pueden usar para crear escenarios de un extremo a otro que se ejecuten en dispositivos de IoT Core de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3226c-109">So, Arduino Wiring sketches have full access to APIs such as communication, data access, networking, graphics, among many others, which can be used to create end to end scenarios running on Windows 10 IoT Core devices.</span></span> <span data-ttu-id="3226c-110">Para obtener más información sobre el desarrollo de aplicaciones Plataforma universal de Windows (UWP), consulte [creación de aplicaciones para Windows 10 IOT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span><span class="sxs-lookup"><span data-stu-id="3226c-110">For more information on developing Universal Windows Platform (UWP) Apps, please refer to [Building Applications for Windows 10 IoT Core](../develop-your-app/BuildingAppsForIoTCore.md).</span></span>

<span data-ttu-id="3226c-111">Además, los bocetos de cableado de Arduino hacen uso de un controlador asignado a memoria directo que ofrece un alto rendimiento en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="3226c-111">Additionally, Arduino Wiring sketches make use of a direct memory mapped driver that offers high performance on supported devices.</span></span> <span data-ttu-id="3226c-112">Para obtener más información sobre los detalles de rendimiento, consulte el informe de [pruebas de rendimiento de Windows IOT Lightning](../develop-your-app/LightningPerformance.md) .</span><span class="sxs-lookup"><span data-stu-id="3226c-112">For more details on performance details, please refer to the [Windows IoT Lightning Performance Testing](../develop-your-app/LightningPerformance.md) report.</span></span>

<span data-ttu-id="3226c-113">Para empezar a crear proyectos de cableado de Arduino para Raspberry pi2, Pi3 o Minnowboard Max, consulte la [Guía de proyecto de cableado de Arduino](ArduinoWiringProjectGuide.md).</span><span class="sxs-lookup"><span data-stu-id="3226c-113">To start building Arduino Wiring projects for Raspberry Pi2, Pi3 or Minnowboard Max, please refer to the [Arduino Wiring project guide](ArduinoWiringProjectGuide.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3226c-114">El cableado Arduino *no* se admite actualmente en DragonBoard 410C.</span><span class="sxs-lookup"><span data-stu-id="3226c-114">Arduino Wiring is *not* currently supported on DragonBoard 410c.</span></span>
