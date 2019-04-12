---
title: Crear pruebas unitarias
author: bfjelds
ms.author: bfjelds
ms.date: 10/08/2018
ms.topic: article
description: Obtenga información sobre las pruebas unitarias que son compatibles con IoT Core.
keywords: Windows iot, pruebas unitarias, UWP
ms.openlocfilehash: 0a54ad7ffa3065353045f0e2f81306a1a1e0ac13
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514775"
---
# <a name="developing-unit-tests"></a><span data-ttu-id="79bbf-104">Desarrollo de pruebas unitarias</span><span class="sxs-lookup"><span data-stu-id="79bbf-104">Developing unit tests</span></span>
<span data-ttu-id="79bbf-105">Obtenga información acerca de la unidad UWP pruebas admitidas en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="79bbf-105">Learn about UWP unit testing supported on Windows 10 IoT Core.</span></span>

## <a name="uwp-unit-tests"></a><span data-ttu-id="79bbf-106">Pruebas unitarias UWP</span><span class="sxs-lookup"><span data-stu-id="79bbf-106">UWP Unit Tests</span></span>
___

<span data-ttu-id="79bbf-107">Las pruebas unitarias proporcionan protección vital y validación para los desarrolladores de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="79bbf-107">Unit tests provide vital protection and validation for app developers.</span></span>  <span data-ttu-id="79bbf-108">Visual Studio 15.6 había agregado compatibilidad para Windows 10 IoT Core en su nueva plataforma de prueba.</span><span class="sxs-lookup"><span data-stu-id="79bbf-108">Visual Studio 15.6 added support for Windows 10 IoT Core in its new test platform.</span></span>  <span data-ttu-id="79bbf-109">Con esta nueva compatibilidad, es posible crear pruebas unitarias para la funcionalidad UWP que se pueden ejecutar como parte de una compilación de integración continua o directamente desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79bbf-109">With this new support, it is possible to create unit tests for UWP functionality that can execute as part of a Continuous Integration build or directly from Visual Studio.</span></span>


### <a name="create-new-unit-test-project"></a><span data-ttu-id="79bbf-110">Crear nuevo proyecto de prueba unitaria</span><span class="sxs-lookup"><span data-stu-id="79bbf-110">Create new unit test project</span></span>
___

1. <span data-ttu-id="79bbf-111">Abra Visual Studio</span><span class="sxs-lookup"><span data-stu-id="79bbf-111">Open Visual Studio</span></span>

2. <span data-ttu-id="79bbf-112">Crear un nuevo proyecto de prueba unitaria ![instalar aplicación](../media/UnitTests/newproject.png)</span><span class="sxs-lookup"><span data-stu-id="79bbf-112">Create a new unit test project ![Install App](../media/UnitTests/newproject.png)</span></span>

3. <span data-ttu-id="79bbf-113">Actualizar UnitTest.cs para incluir el código de prueba</span><span class="sxs-lookup"><span data-stu-id="79bbf-113">Update UnitTest.cs to include your test code</span></span>
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a><span data-ttu-id="79bbf-114">Ejecutar pruebas unitarias de forma remota en dispositivos Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="79bbf-114">Remotely run unit test on Windows 10 IoT Core device</span></span>
___

1. <span data-ttu-id="79bbf-115">Abra el Explorador de pruebas de Visual Studio (prueba > Windows > Explorador de pruebas).</span><span class="sxs-lookup"><span data-stu-id="79bbf-115">Open the Visual Studio Test Explorer (Test > Windows > Test Explorer).</span></span>
 ![Explorador de pruebas](../media/UnitTests/show-test-explorer.png)

1. <span data-ttu-id="79bbf-117">Implementación de prueba para que funcione, debe configurarse el proyecto de la misma manera que se configuran las aplicaciones para UWP (específicamente con autenticación Universal y el equipo remoto).</span><span class="sxs-lookup"><span data-stu-id="79bbf-117">For test deployment to work, your project must be configured in the same way UWP apps are configured (specifically using Universal Authentication and Remote Machine).</span></span>  <span data-ttu-id="79bbf-118">Consulte [implementar una aplicación con Visual Studio](../develop-your-app/appdeployment.md) para obtener información específica.</span><span class="sxs-lookup"><span data-stu-id="79bbf-118">See [Deploy an App with Visual Studio](../develop-your-app/appdeployment.md) for specifics.</span></span>

1. <span data-ttu-id="79bbf-119">Para ejecutar una prueba unitaria de forma remota, puede usar el Explorador de pruebas haciendo el TestMethod deseada y seleccione Ejecutar o depurar las pruebas seleccionadas ![Explorador de pruebas](../media/UnitTests/test-explorer.png)</span><span class="sxs-lookup"><span data-stu-id="79bbf-119">To remotely run a unit test, you can use the Test Explorer and right clicking the desired TestMethod and selecting Run/Debug Selected Tests ![Test Explorer](../media/UnitTests/test-explorer.png)</span></span>

1. <span data-ttu-id="79bbf-120">Para ejecutar o depurar todas las pruebas unitarias de forma remota, puede usar prueba > ejecutar o comprobar > depurar ![Explorador de pruebas](../media/UnitTests/run-tests.png)
 ![Explorador de pruebas](../media/UnitTests/debug-tests.png)</span><span class="sxs-lookup"><span data-stu-id="79bbf-120">To remotely run or debug all unit tests, you can use Test > Run or Test > Debug ![Test Explorer](../media/UnitTests/run-tests.png)
 ![Test Explorer](../media/UnitTests/debug-tests.png)</span></span>
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a><span data-ttu-id="79bbf-121">Configuración de pruebas unitarias como parte de una compilación de integración continua</span><span class="sxs-lookup"><span data-stu-id="79bbf-121">Configure unit tests as part of a Continuous Integration build</span></span>
___

<span data-ttu-id="79bbf-122">El equipo de Visual Studio ha creado una entrada de blog excelentes que muestra cómo incorporar pruebas unitarias de Windows 10 IoT Core en una compilación VSTS: [DevOps para IoT con Win10 IoT Core, UWP y VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span><span class="sxs-lookup"><span data-stu-id="79bbf-122">The Visual Studio team has created a great blog post showing how to incorporate Windows 10 IoT Core unit tests into a VSTS build: [DevOps for IoT with Win10 IoT Core, UWP, and VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)</span></span>

