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
# <a name="develop-an-app-for-your-device"></a>Desarrollo de una aplicación para el dispositivo

> [!NOTE]
> Visual Studio generará un error críptico al realizar la implementación en una imagen de IoT RS5 (o RS4 con OpenSSH habilitado), a menos que haya instalado un SDK de RS4 o superior al que pueda acceder Visual Studio.

Ahora que tiene un dispositivo que funciona con la aplicación predeterminada en ejecución, probablemente querrá mejorarlo desarrollando e implementando una aplicación en el dispositivo. Antes de profundizar en los ejemplos, necesitará descargar [Visual Studio 2017](https://www.visualstudio.com/downloads/) para el desarrollo de aplicaciones.

Si planea usar C++ para los proyectos, al descargar Visual Studio 2017, asegúrese de activar las casillas tal como se muestra en el ejemplo siguiente:

![Elementos básicos para C++ y Windows 10 IoT](../../media/DevelopApp/VS-CPP.jpg)

Si le interesa desarrollar en segundo plano, Arduino, Wiring o aplicaciones de consola en el futuro, le conviene descargar también las plantillas de proyecto de la [Galería de Visual Studio](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15).


Para empezar a trabajar con una aplicación, se recomienda comenzar con uno de los ejemplos de inicio que se sugieren a continuación. Pero si está listo para implementar su propia aplicación, encontrará vínculos útiles en la sección posterior.

## <a name="suggested-starter-samples"></a>Ejemplos de inicio sugeridos

* [Hello Blinky](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloBlinky)
* [Hola mundo](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/HelloWorld)
* [Ejemplo de aplicación de inicio de IoT](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTStartApp)
* [Ejemplo de RPi Cognitive Service](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/RPiCognitiveService) 



Cuando implemente la aplicación, habrá finalizado este inicio rápido. Puede seguir experimentando o, si le está dando vueltas a alguna idea, consulte nuestra documentación sobre la comercialización con Windows 10 IoT. 

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
<td align="left"><p>Obtenga información sobre los diferentes lenguajes que se admiten en Windows 10 IoT Core, así como los tipos de aplicaciones para UWP y no UWP admitidos.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/backgroundapplications.md" data-raw-source="[Developing background applications](../../develop-your-app/backgroundapplications.md)">Desarrollo de aplicaciones en segundo plano</a></p></td>
<td align="left"><p>Obtenga información sobre los diferentes lenguajes que se admiten en Windows 10 IoT Core, así como los tipos de aplicaciones para UWP y no UWP admitidos.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appdeployment.md" data-raw-source="[Deploy an App with Visual Studio](../../develop-your-app/appdeployment.md)">Implementar una aplicación con Visual Studio</a></p></td>
<td align="left"><p>Obtenga información sobre cómo implementar las distintas aplicaciones con Visual Studio en el dispositivo Windows 10 IoT Core.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/remotedebugging.md" data-raw-source="[Debug your app using Remote Console App Debugging](../../develop-your-app/remotedebugging.md)">Depurar la aplicación con la depuración remota de aplicaciones de consola</a></p></td>
<td align="left"><p>Obtenga información sobre cómo depurar las aplicaciones con la depuración remota de aplicaciones de consola en Visual Studio.</p></td>
</tr>

<tr class="odd">
<td align="left"><p><a href="../../develop-your-app/appinstaller.md" data-raw-source="[Install your app on your Windows 10 IoT Core device](../../develop-your-app/appinstaller.md)">Instalar la aplicación en un dispositivo Windows 10 IoT Core</a></p></td>
<td align="left"><p>Obtenga información sobre cómo instalar la aplicación en un dispositivo Windows 10 IoT Core.</p></td>
</tr>

</tbody>
</table>
