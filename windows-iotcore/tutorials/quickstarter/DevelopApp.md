---
title: Desarrollo de una aplicación para el dispositivo
ms.date: 04/17/2018
ms.topic: article
description: Obtenga información sobre cómo agregar y desarrollar aplicaciones para el dispositivo.
keywords: Windows 10 IoT Core, introducción, desarrollo de aplicaciones, aplicaciones
ms.openlocfilehash: 7c047e2bba686705db19b12ea3b31350f0240688
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "72918484"
---
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="a4311-104">Desarrollo de una aplicación para el dispositivo</span><span class="sxs-lookup"><span data-stu-id="a4311-104">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="a4311-105">Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4311-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="a4311-106">Ahora que tiene un dispositivo que funciona con la aplicación predeterminada en ejecución, probablemente querrá mejorarlo desarrollando e implementando una aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4311-106">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="a4311-107">Antes de profundizar en los ejemplos, necesitará descargar [Visual Studio 2017](https://www.visualstudio.com/downloads/) para el desarrollo de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a4311-107">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="a4311-108">Si planea usar C++ para los proyectos, al descargar Visual Studio 2017, asegúrese de activar las casillas tal como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a4311-108">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![Elementos básicos para C++ y Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="a4311-110">Si le interesa desarrollar en segundo plano, Arduino, Wiring o aplicaciones de consola en el futuro, le conviene descargar también las plantillas de proyecto de la [Galería de Visual Studio](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span><span class="sxs-lookup"><span data-stu-id="a4311-110">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="a4311-111">Para empezar a trabajar con una aplicación, se recomienda comenzar con uno de los ejemplos de inicio que se sugieren a continuación.</span><span class="sxs-lookup"><span data-stu-id="a4311-111">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="a4311-112">Pero si está listo para implementar su propia aplicación, encontrará vínculos útiles en la sección posterior.</span><span class="sxs-lookup"><span data-stu-id="a4311-112">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="a4311-113">Ejemplos de inicio sugeridos</span><span class="sxs-lookup"><span data-stu-id="a4311-113">Suggested starter samples</span></span>

* [<span data-ttu-id="a4311-114">Hello Blinky</span><span class="sxs-lookup"><span data-stu-id="a4311-114">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="a4311-115">Hola mundo</span><span class="sxs-lookup"><span data-stu-id="a4311-115">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="a4311-116">Ejemplo de aplicación de inicio de IoT</span><span class="sxs-lookup"><span data-stu-id="a4311-116">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="a4311-117">Ejemplo de RPi Cognitive Service</span><span class="sxs-lookup"><span data-stu-id="a4311-117">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="a4311-118">Cuando implemente la aplicación, habrá finalizado este inicio rápido.</span><span class="sxs-lookup"><span data-stu-id="a4311-118">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="a4311-119">Puede seguir experimentando o, si le está dando vueltas a alguna idea, consulte nuestra documentación sobre la comercialización con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="a4311-119">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="a4311-120">Recursos de desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="a4311-120">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="a4311-121">Tema</span><span class="sxs-lookup"><span data-stu-id="a4311-121">Topic</span></span></th>
<th align="left"><span data-ttu-id="a4311-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="a4311-122">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><span data-ttu-id="a4311-123"><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">Desarrollo de aplicaciones de primer plano</a></span><span class="sxs-lookup"><span data-stu-id="a4311-123"><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">Developing foreground applications</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="a4311-124">Obtenga información sobre los diferentes lenguajes que se admiten en Windows 10 IoT Core, así como los tipos de aplicaciones para UWP y no UWP admitidos.</span><span class="sxs-lookup"><span data-stu-id="a4311-124">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="a4311-125"><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Desarrollo de aplicaciones en segundo plano</a></span><span class="sxs-lookup"><span data-stu-id="a4311-125"><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Developing background applications</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="a4311-126">Obtenga información sobre los diferentes lenguajes que se admiten en Windows 10 IoT Core, así como los tipos de aplicaciones para UWP y no UWP admitidos.</span><span class="sxs-lookup"><span data-stu-id="a4311-126">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="a4311-127"><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Implementar una aplicación con Visual Studio</a></span><span class="sxs-lookup"><span data-stu-id="a4311-127"><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Deploy an App with Visual Studio</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="a4311-128">Obtenga información sobre cómo implementar las distintas aplicaciones con Visual Studio en el dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="a4311-128">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="a4311-129"><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Depurar la aplicación con la depuración remota de aplicaciones de consola</a></span><span class="sxs-lookup"><span data-stu-id="a4311-129"><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Debug your app using Remote Console App Debugging</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="a4311-130">Obtenga información sobre cómo depurar las aplicaciones con la depuración remota de aplicaciones de consola en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4311-130">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><span data-ttu-id="a4311-131"><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Instalar la aplicación en un dispositivo Windows 10 IoT Core</a></span><span class="sxs-lookup"><span data-stu-id="a4311-131"><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Install your app on your Windows 10 IoT Core device</a></span></span></p></td>
<td align="left"><p><span data-ttu-id="a4311-132">Obtenga información sobre cómo instalar la aplicación en un dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="a4311-132">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
