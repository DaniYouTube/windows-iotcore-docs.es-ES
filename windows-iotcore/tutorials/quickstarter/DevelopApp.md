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
# <a name="develop-an-app-for-your-device"></a>Desarrollar una aplicación para el dispositivo

> [!NOTE]
> Visual Studio generará un error críptico al implementar en un RS5 (o RS4 con OpenSSH habilitado) IoT a menos que se instala un SDK de RS4 o mayor que Visual Studio puede tener acceso a la imagen.

Ahora que tiene un dispositivo que funcione con la aplicación predeterminada que se ejecuta, conviene aprovechar el dispositivo al siguiente nivel al desarrollar e implementar una aplicación en el dispositivo. Antes de profundizar en los ejemplos, necesitará descargar [Visual Studio 2017](https://www.visualstudio.com/downloads/) para el desarrollo de aplicaciones.

Si está planeando usar C++ para sus proyectos, al descargar Visual Studio 2017, asegúrese de Active las casillas de la misma manera que estén en el ejemplo siguiente:

![Essentials para C++ y Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

Si está interesado en desarrollar en segundo plano, el cableado de Arduino o aplicaciones de consola en el futuro, también conviene descargar las plantillas de proyecto desde el [Galería de Visual Studio](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).


Para empezar a trabajar con una aplicación, se recomienda comenzar con un ejemplo de inicio sugeridos a continuación. Pero si está listo para implementar su propia aplicación, también hemos proporcionado vínculos útiles en la siguiente sección.

## <a name="suggested-starter-samples"></a>Ejemplos de inicio sugerido

* [Hola llamativa](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hello World](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [Ejemplo de aplicación de inicio de IoT](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [Ejemplo de RPi Cognitive Services](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



Cuando se haya implementado la aplicación - Enhorabuena, ha terminado este quickstarter! Seguir practique o, si tiene algunas ideas que rebota alrededor de la cabeza, consulte nuestra documentación sobre commercializing con Windows 10 IoT. 

## <a name="app-development-resources"></a>Recursos de desarrollo de aplicaciones

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Tema</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/buildingappsforiotcore.md" data-raw-source="[Developing foreground applications](../../develop-your-app/buildingappsforiotcore.md)">Desarrollo de aplicaciones de primer plano</a></p></td>
<td align="left"><p>Obtenga información sobre los diferentes idiomas que se admiten en Windows 10 IoT Core, así como la UWP y tipos de aplicaciones no de UWP que se admiten.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Desarrollo de aplicaciones en segundo plano</a></p></td>
<td align="left"><p>Obtenga información sobre los diferentes idiomas que se admiten en Windows 10 IoT Core, así como la UWP y tipos de aplicaciones no de UWP que se admiten.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Implementar una aplicación con Visual Studio</a></p></td>
<td align="left"><p>Obtenga información sobre cómo implementar las distintas aplicaciones con Visual Studio en el dispositivo Windows 10 IoT Core.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Depurar la aplicación con la depuración remota de aplicaciones de consola</a></p></td>
<td align="left"><p>Obtenga información sobre cómo depurar las aplicaciones con la depuración remota de aplicaciones de consola en Visual Studio.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Instalar la aplicación en el dispositivo Windows 10 IoT Core</a></p></td>
<td align="left"><p>Obtenga información sobre cómo instalar la aplicación en el dispositivo Windows 10 IoT Core.</p></td>
</tr>

</tbody>
</table>
