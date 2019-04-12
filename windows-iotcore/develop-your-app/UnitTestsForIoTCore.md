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
# <a name="developing-unit-tests"></a>Desarrollo de pruebas unitarias
Obtenga información acerca de la unidad UWP pruebas admitidas en Windows 10 IoT Core.

## <a name="uwp-unit-tests"></a>Pruebas unitarias UWP
___

Las pruebas unitarias proporcionan protección vital y validación para los desarrolladores de aplicaciones.  Visual Studio 15.6 había agregado compatibilidad para Windows 10 IoT Core en su nueva plataforma de prueba.  Con esta nueva compatibilidad, es posible crear pruebas unitarias para la funcionalidad UWP que se pueden ejecutar como parte de una compilación de integración continua o directamente desde Visual Studio.


### <a name="create-new-unit-test-project"></a>Crear nuevo proyecto de prueba unitaria
___

1. Abra Visual Studio

2. Crear un nuevo proyecto de prueba unitaria ![instalar aplicación](../media/UnitTests/newproject.png)

3. Actualizar UnitTest.cs para incluir el código de prueba
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a>Ejecutar pruebas unitarias de forma remota en dispositivos Windows 10 IoT Core
___

1. Abra el Explorador de pruebas de Visual Studio (prueba > Windows > Explorador de pruebas).
 ![Explorador de pruebas](../media/UnitTests/show-test-explorer.png)

1. Implementación de prueba para que funcione, debe configurarse el proyecto de la misma manera que se configuran las aplicaciones para UWP (específicamente con autenticación Universal y el equipo remoto).  Consulte [implementar una aplicación con Visual Studio](../develop-your-app/appdeployment.md) para obtener información específica.

1. Para ejecutar una prueba unitaria de forma remota, puede usar el Explorador de pruebas haciendo el TestMethod deseada y seleccione Ejecutar o depurar las pruebas seleccionadas ![Explorador de pruebas](../media/UnitTests/test-explorer.png)

1. Para ejecutar o depurar todas las pruebas unitarias de forma remota, puede usar prueba > ejecutar o comprobar > depurar ![Explorador de pruebas](../media/UnitTests/run-tests.png)
 ![Explorador de pruebas](../media/UnitTests/debug-tests.png)
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a>Configuración de pruebas unitarias como parte de una compilación de integración continua
___

El equipo de Visual Studio ha creado una entrada de blog excelentes que muestra cómo incorporar pruebas unitarias de Windows 10 IoT Core en una compilación VSTS: [DevOps para IoT con Win10 IoT Core, UWP y VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)

