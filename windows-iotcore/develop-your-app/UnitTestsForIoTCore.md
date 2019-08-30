---
title: Crear pruebas unitarias
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: Obtenga información sobre las pruebas unitarias que admite IoT Core.
keywords: Windows IOT, prueba unitaria, UWP
ms.openlocfilehash: 0a54ad7ffa3065353045f0e2f81306a1a1e0ac13
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169329"
---
# <a name="developing-unit-tests"></a><span data-ttu-id="344ba-104">Desarrollar pruebas unitarias</span><span class="sxs-lookup"><span data-stu-id="344ba-104">Developing unit tests</span></span>
<span data-ttu-id="344ba-105">Obtenga información sobre las pruebas unitarias de UWP compatibles con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="344ba-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="344ba-106">Pruebas unitarias de UWP</span><span class="sxs-lookup"><span data-stu-id="344ba-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="344ba-107">Las pruebas unitarias proporcionan protección y validación vitales para los desarrolladores de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="344ba-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="344ba-108">Visual Studio 15,6 agregó compatibilidad con Windows 10 IoT Core en su nueva plataforma de prueba.</span><span class="sxs-lookup"><span data-stu-id="344ba-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="344ba-109">Con esta nueva compatibilidad, es posible crear pruebas unitarias para la funcionalidad de UWP que se pueden ejecutar como parte de una compilación de integración continua o directamente desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="344ba-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="344ba-110">Crear nuevo proyecto de prueba unitaria</span><span class="sxs-lookup"><span data-stu-id="344ba-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="344ba-111">Abra Visual Studio</span><span class="sxs-lookup"><span data-stu-id="344ba-111">Open Visual Studio</span></span>

2. <span data-ttu-id="344ba-112">Crear una nueva aplicación de instalación ![de proyecto de prueba unitaria](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="344ba-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="344ba-113">Actualización de UnitTest.cs para incluir el código de prueba</span><span class="sxs-lookup"><span data-stu-id="344ba-113">Update UnitTest.cs to include your test code</span></span>
   ```C#
   namespace UnitTestProject1
   {
    [TestClass]
    public class UnitTest1
    {
        [TestMethod]
        public void TestMethod1()
        {
            // test code here
        }
    }
   }
   ```


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="344ba-114">Ejecutar pruebas unitarias de forma remota en un dispositivo de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="344ba-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="344ba-115">Abra el explorador de pruebas de Visual Studio (probar > el explorador de pruebas de Windows >).</span><span class="sxs-lookup"><span data-stu-id="344ba-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 <span data-ttu-id="344ba-116">![Explorador de pruebas](../media/UnitTests/show-test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="344ba-116">![Test Explorer](../media/UnitTests/show-test-explorer.png)</span></span>

1. <span data-ttu-id="344ba-117">Para que la implementación de prueba funcione, el proyecto debe estar configurado de la misma manera que se configuran las aplicaciones para UWP (específicamente mediante la autenticación universal y la máquina remota).</span><span class="sxs-lookup"><span data-stu-id="344ba-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="344ba-118">Consulte [implementación de una aplicación con Visual Studio](../develop-your-app/appdeployment.md) para obtener información específica.</span><span class="sxs-lookup"><span data-stu-id="344ba-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="344ba-119">Para ejecutar una prueba unitaria de forma remota, puede usar el explorador de pruebas y hacer clic con el botón secundario en el TestMethod deseado y ![seleccionar ejecutar o depurar pruebas seleccionadas explorador de pruebas.](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="344ba-119">To remotely run a unit test, you can use the Test Explorer and right clicking the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="344ba-120">Para ejecutar o depurar de forma remota todas las pruebas unitarias, puede usar probar > ejecutar ![o probar](../media/UnitTests/run-tests.png)
 el explorador de pruebas del explorador![de pruebas > Debug.](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="344ba-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="344ba-121">Configurar pruebas unitarias como parte de una compilación de integración continua</span><span class="sxs-lookup"><span data-stu-id="344ba-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="344ba-122">El equipo de Visual Studio ha creado una excelente entrada de blog que muestra cómo incorporar las pruebas unitarias de IoT Core de Windows 10 en una compilación de VSTS: [DevOps para IoT con Win10 IoT Core, UWP y VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="344ba-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

