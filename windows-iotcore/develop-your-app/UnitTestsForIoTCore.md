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
# <a name="developing-unit-tests"></a>Desarrollar pruebas unitarias
Obtenga información sobre las pruebas unitarias de UWP compatibles con Windows 10 IoT Core.

## <a name="uwp-unit-tests"></a>Pruebas unitarias de UWP
___

Las pruebas unitarias proporcionan protección y validación vitales para los desarrolladores de aplicaciones.  Visual Studio 15,6 agregó compatibilidad con Windows 10 IoT Core en su nueva plataforma de prueba.  Con esta nueva compatibilidad, es posible crear pruebas unitarias para la funcionalidad de UWP que se pueden ejecutar como parte de una compilación de integración continua o directamente desde Visual Studio.


### <a name="create-new-unit-test-project"></a>Crear nuevo proyecto de prueba unitaria
___

1. Abra Visual Studio

2. Crear una nueva aplicación de instalación ![de proyecto de prueba unitaria](../media/UnitTests/newproject.png)

3. Actualización de UnitTest.cs para incluir el código de prueba
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


### <a name="remotely-run-unit-test-on-windows-10-iot-core-device"></a>Ejecutar pruebas unitarias de forma remota en un dispositivo de Windows 10 IoT Core
___

1. Abra el explorador de pruebas de Visual Studio (probar > el explorador de pruebas de Windows >).
 ![Explorador de pruebas](../media/UnitTests/show-test-explorer.png)

1. Para que la implementación de prueba funcione, el proyecto debe estar configurado de la misma manera que se configuran las aplicaciones para UWP (específicamente mediante la autenticación universal y la máquina remota).  Consulte [implementación de una aplicación con Visual Studio](../develop-your-app/appdeployment.md) para obtener información específica.

1. Para ejecutar una prueba unitaria de forma remota, puede usar el explorador de pruebas y hacer clic con el botón secundario en el TestMethod deseado y ![seleccionar ejecutar o depurar pruebas seleccionadas explorador de pruebas.](../media/UnitTests/test-explorer.png)

1. Para ejecutar o depurar de forma remota todas las pruebas unitarias, puede usar probar > ejecutar ![o probar](../media/UnitTests/run-tests.png)
 el explorador de pruebas del explorador![de pruebas > Debug.](../media/UnitTests/debug-tests.png)
   

### <a name="configure-unit-tests-as-part-of-a-continuous-integration-build"></a>Configurar pruebas unitarias como parte de una compilación de integración continua
___

El equipo de Visual Studio ha creado una excelente entrada de blog que muestra cómo incorporar las pruebas unitarias de IoT Core de Windows 10 en una compilación de VSTS: [DevOps para IoT con Win10 IoT Core, UWP y VSTS](https://blogs.msdn.microsoft.com/devops/2018/03/07/devops-for-iot-with-win10-iot-core-uwp-and-vsts/)

