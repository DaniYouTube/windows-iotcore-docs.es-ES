---
title: Desarrollar una aplicación para el dispositivo
author: saraclay
ms.author: saclayt
ms.date: 04/17/2018
ms.topic: article
description: Obtenga información sobre cómo agregar y desarrollar aplicaciones para el dispositivo
keywords: Windows 10 IoT Core, antes de empezar, desarrolle aplicaciones, aplicaciones
ms.openlocfilehash: f5ee15c2115d6e10a2a8ade1522c7b66cf788bee
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515101"
---
# <a name="develop-an-app-for-your-device"></a><span data-ttu-id="5c474-104">Desarrollar una aplicación para el dispositivo</span><span class="sxs-lookup"><span data-stu-id="5c474-104">Develop an app for your device</span></span>

> [!NOTE]
> <span data-ttu-id="5c474-105">Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.</span><span class="sxs-lookup"><span data-stu-id="5c474-105">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

<span data-ttu-id="5c474-106">Ahora que tiene un dispositivo que funcione con la aplicación predeterminada que se ejecuta, conviene aprovechar el dispositivo al siguiente nivel al desarrollar e implementar una aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5c474-106">Now that you have a working device with the default app running, you'll want to take your device to the next level by developing and deploying an app on your device.</span></span> <span data-ttu-id="5c474-107">Antes de profundizar en los ejemplos, necesitará descargar [Visual Studio 2017](https://www.visualstudio.com/downloads/) para el desarrollo de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="5c474-107">Before diving into samples, you'll need to download [Visual Studio 2017](https://www.visualstudio.com/downloads/) for application development.</span></span>

<span data-ttu-id="5c474-108">Si está planeando usar C++ para sus proyectos, al descargar Visual Studio 2017, asegúrese de Active las casillas de la misma manera que estén en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5c474-108">If you're planning to use C++ for your projects, when downloading Visual Studio 2017, make sure to check the boxes the same way as they are in the example below:</span></span>

![Essentials para C++ y Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

<span data-ttu-id="5c474-110">Si está interesado en desarrollar en segundo plano, el cableado de Arduino o aplicaciones de consola en el futuro, también conviene descargar las plantillas de proyecto desde el [Galería de Visual Studio](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span><span class="sxs-lookup"><span data-stu-id="5c474-110">If you're interested in developing background, Arduino Wiring or console applications in the future, you'll also want to download project templates from the [Visual Studio Gallery](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).</span></span>


<span data-ttu-id="5c474-111">Para empezar a trabajar con una aplicación, se recomienda comenzar con un ejemplo de inicio sugeridos a continuación.</span><span class="sxs-lookup"><span data-stu-id="5c474-111">To get up and running with an app, we recommend starting with a suggested starter sample below.</span></span> <span data-ttu-id="5c474-112">Pero si está listo para implementar su propia aplicación, también hemos proporcionado vínculos útiles en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="5c474-112">But if you're ready to deploy your own app, we've also provided helpful links in the section after.</span></span>

## <a name="suggested-starter-samples"></a><span data-ttu-id="5c474-113">Ejemplos de inicio sugerido</span><span class="sxs-lookup"><span data-stu-id="5c474-113">Suggested starter samples</span></span>

* [<span data-ttu-id="5c474-114">Hola llamativa</span><span class="sxs-lookup"><span data-stu-id="5c474-114">Hello Blinky</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [<span data-ttu-id="5c474-115">Hello World</span><span class="sxs-lookup"><span data-stu-id="5c474-115">Hello World</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [<span data-ttu-id="5c474-116">Ejemplo de aplicación de inicio de IoT</span><span class="sxs-lookup"><span data-stu-id="5c474-116">IoT Startup App sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [<span data-ttu-id="5c474-117">Ejemplo de RPi Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="5c474-117">RPi Cognitive Service sample</span></span>](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



<span data-ttu-id="5c474-118">Cuando se haya implementado la aplicación - Enhorabuena, ha terminado este quickstarter!</span><span class="sxs-lookup"><span data-stu-id="5c474-118">Once you've deployed your app - congratulations, you've finished this quickstarter!</span></span> <span data-ttu-id="5c474-119">Seguir practique o, si tiene algunas ideas que rebota alrededor de la cabeza, consulte nuestra documentación sobre commercializing con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="5c474-119">Continue to play around or, if you have a few ideas bouncing around in your head, check out our documentation on commercializing with Windows 10 IoT.</span></span> 

## <a name="app-development-resources"></a><span data-ttu-id="5c474-120">Recursos de desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="5c474-120">App development resources</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5c474-121">Tema</span><span class="sxs-lookup"><span data-stu-id="5c474-121">Topic</span></span></th>
<th align="left"><span data-ttu-id="5c474-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="5c474-122">Description</span></span></th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)"><span data-ttu-id="5c474-123">Desarrollo de aplicaciones de primer plano</span><span class="sxs-lookup"><span data-stu-id="5c474-123">Developing foreground applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5c474-124">Obtenga información sobre los diferentes idiomas que se admiten en Windows 10 IoT Core, así como la UWP y tipos de aplicaciones no de UWP que se admiten.</span><span class="sxs-lookup"><span data-stu-id="5c474-124">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)"><span data-ttu-id="5c474-125">Desarrollo de aplicaciones en segundo plano</span><span class="sxs-lookup"><span data-stu-id="5c474-125">Developing background applications</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5c474-126">Obtenga información sobre los diferentes idiomas que se admiten en Windows 10 IoT Core, así como la UWP y tipos de aplicaciones no de UWP que se admiten.</span><span class="sxs-lookup"><span data-stu-id="5c474-126">Learn about the different languages that are supported on Windows 10 IoT Core as well as the UWP and non-UWP app types that are supported.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)"><span data-ttu-id="5c474-127">Implementar una aplicación con Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5c474-127">Deploy an App with Visual Studio</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5c474-128">Obtenga información sobre cómo implementar las distintas aplicaciones con Visual Studio en el dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5c474-128">Learn how to deploy your different apps with Visual Studio to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)"><span data-ttu-id="5c474-129">Depurar la aplicación con la depuración remota de aplicaciones de consola</span><span class="sxs-lookup"><span data-stu-id="5c474-129">Debug your app using Remote Console App Debugging</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5c474-130">Obtenga información sobre cómo depurar las aplicaciones con la depuración remota de aplicaciones de consola en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c474-130">Learn how to debug your apps using Remote Console App Debugging in Visual Studio.</span></span></p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)"><span data-ttu-id="5c474-131">Instalar la aplicación en el dispositivo Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="5c474-131">Install your app on your Windows 10 IoT Core device</span></span></a></p></td>
<td align="left"><p><span data-ttu-id="5c474-132">Obtenga información sobre cómo instalar la aplicación en el dispositivo Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5c474-132">Learn how to install your app to your Windows 10 IoT Core device.</span></span></p></td>
</tr>

</tbody>
</table>
