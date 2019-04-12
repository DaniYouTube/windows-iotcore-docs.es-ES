---
title: Computer Vision
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar servicios de Microsoft Cognitive y OpenCV para el dispositivo de IoT.
keywords: Windows iot, computer vision o Cognitive Services, OpenCV
ms.openlocfilehash: f6d10024f0f52f7219eb3a63dcefa7fd2b4a6fe3
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514440"
---
# <a name="computer-vision"></a>Computer Vision

Los seres humanos perciben nuestro mundo tridimensional con relativa facilidad. A partir de una edad temprana, nuestro cerebro puede recopilar valiosa incluidos identificación de la característica Prevención obstáculo, coordinación, percepción de profundidad y muchas otras desde estímulos visuales. Visión de equipo es un intento de usar procesadores y cámaras para hacer lo mismo. Tiene un sinfín de aplicaciones para dispositivos de hoy en día. Un DRON puede usar para detectar rápidamente y evitar obstáculos durante el vuelo; una fábrica puede usar para detectar defectos cosméticos en los componentes más pequeños en la línea de ensamblado; y una persona puede usar para detectar su propio ritmo cardíaco sin uso de un monitor o un equipo médico. Nuestro mundo centrados en datos ha realizado el equipo vision un área muy activa de investigación. Las empresas utilizan de maneras que considera improbables incluso hace diez años. Como las cámaras, equipos y los datos se vuelve más están muy arraigadas en nuestra sociedad, herramientas para aprovechar las funcionalidades más emocionantes de la visión equipo deben estar tan fáciles acceder y utilizar como sea posible. Windows 10 IoT Core intenta satisfacer esta necesidad a través de la compatibilidad con dos ofertas: Servicios de Microsoft Cognitive y OpenCV.

## <a name="services"></a>Servicios
___

### <a name="cognitive-services"></a>Cognitive Services

#### <a name="overview"></a>Información general
Cognitivas Services, originalmente un proyecto de Microsoft Research denominado Project Oxford, es una colección de API que realizan "cognitivas tareas de alto nivel". Estas API extraen conocimiento a partir de los datos basados en modelos de años de desarrollo en Microsoft Research y exploración de aprendizaje de automático altamente cualificados.

Cognitivas Services está formado por 5 categorías: Visión, voz, idiomas, conocimiento y búsqueda.

Puede encontrar más información sobre Cognitive Services en los servicios cognitivos [sitio Web](https://www.microsoft.com/cognitive-services).

La categoría de visión, la categoría más valiosa para las aplicaciones de la visión de equipo, contiene cuatro API: Computer Vision, Emotion, cara y vídeo. Estas API ofrecen la funcionalidad siguiente:
- Reconocimiento facial
- Detección de movimiento
- Reconocimiento de emociones
- Estabilización de vídeo
- Análisis de contenido de imagen

Cognitive Services es ideal para trabajar con gran cantidad de datos, obtener acceso a Microsoft Azure y se reduce considerablemente tiempo de comercialización la aplicación, como las API de visión a menudo demostrar a llevar mucho tiempo a desarrollar de forma independiente. El modelo utilizado para estas API es bien preparados y amplias gracias a los esfuerzos de Microsoft Research. Por otro lado, su requisito de conectividad en la nube reduce el rendimiento del sistema y crea el requisito para una conexión a internet.

#### <a name="pricing"></a>Precios
Cada suscripción de la API incluye un conjunto de transacciones gratuita cada mes (300 a 30.000, dependiendo de la API). Después de superar esta cantidad inicial, los servicios vienen con un precio razonable. Por ejemplo, el uso de Emotion API proporciona de forma gratuita las primeros 30 000 transacciones y requiere $0,10 o $0.25 escriba cada transacción 1000 después de eso, dependiendo de la suscripción.

Para obtener más detalles sobre los precios de Cognitive Services se encuentra en sus [sitio Web](https://www.microsoft.com/cognitive-services/en-us/pricing).

#### <a name="get-started"></a>Comenzar
Para permitir el uso de Cognitive Services, los usuarios deben registrarse en el sitio Web de Cognitive Services para recibir las claves de API. Después de proporcionar una clave de API en Cognitive Services, los usuarios pueden llamar a las API dentro de las limitaciones mencionadas en la sección "Precios".

Puede encontrar documentación para cada API en Cognitive Services [sitio Web](https://www.microsoft.com/cognitive-services/en-us/documentation).

Todas las API de Cognitive Services se puede implementar en cualquier plataforma de hardware mediante C#.

¿Desea ejecutar Cognitive Services en el dispositivo de IoT? Visite nuestro [tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices) para empezar a trabajar.

### <a name="opencv"></a>OpenCV

OpenCV es una visión de equipo de código abierto y la biblioteca de software diseñado para aplicaciones en tiempo real y la eficacia de cálculo de aprendizaje automático. Es muy popular entre los desarrolladores y en la industria gracias a su eficacia sin precedentes, versátiles herramientas, soporte técnico para una amplia gama de plataformas y vibrante Comunidad en línea de los desarrolladores. Es, sin duda el más popular herramienta de visión de equipo de código abierto. Bibliotecas de OpenCV están disponibles para C /C++, Java, y C#.

OpenCV [sitio Web](http://opencv.org/) proporciona detalles adicionales.

Características de OpenCV:
- Imagen local y el procesamiento de vídeo y análisis
- Identificación del objeto en tiempo real, coincidencia y seguimiento
- Reconocimiento facial en tiempo real
- Determinación de la distancia desde la imagen y en tiempo real
- Asignación, modelado y reconstrucción 3D
- Edición (por ejemplo, el cambio de color y composición) de la imagen

OpenCV proporciona una serie de ventajas. Es muy eficaz para el procesamiento de datos local debido a la C optimizado /C++ internals y su acceso a la GPU mediante OpenCL (si está habilitado). Contiene más, si no todos, funcionalidad de visión de equipo disponible actualmente. Su duración y la utilidad ha formado una comunidad en línea amplia y experimentada que puede ayudar a los nuevos usuarios con problemas de aplicación o biblioteca. Por otro lado, hay una curva de aprendizaje pronunciada debido a la configuración compleja de código y la biblioteca, así como las incoherencias en los tutoriales y código de ejemplo.

Actualmente, OpenCV con IoT Core solo funciona si los usuarios crear la biblioteca de origen, lo que puede llevar mucho tiempo. Por este motivo, estamos trabajando activamente para que sea más fácil configurar mediante la creación de una colección de paquetes de NuGet para él en IoT Core OpenCV. Un paquete de NuGet, que usa Cognitive Services, permite a los desarrolladores importar una biblioteca previamente generada en su aplicación, que proporciona una funcionalidad completa con unos pocos clics. La aplicación con el paquete NuGet seguirá recibiendo actualizaciones de biblioteca de un servidor dedicado. el usuario no es necesario volver a generar nuevo código fuente cuando hay cambios públicos en el software de código abierto. El paquete también alivia el espacio de almacenamiento en dispositivos con solo partes de la biblioteca.

Esto es actualmente un trabajo en curso, por lo que siga comprobando si hay WindowsOnDevices.com actualizaciones!

Mientras tanto, para compilar la biblioteca de origen para ARM, visite la [repositorio de GitHub](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM).

¿Desea ejecutar OpenCV en el dispositivo de IoT Core? Visite nuestro [tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/opencv) para empezar a trabajar.

## <a name="comparing-opencv-and-cognitive-services"></a>Comparación de OpenCV y Cognitive Services

> |        |Microsoft Cognitive Services|OpenCV|
> |---------------------|--------|------|
> |Fácil de usar en Windows|Sí|No |
> |Compatibilidad con la arquitectura|ARM, x86, x64 | ARM, x86, x64|
> |Seguimiento y el reconocimiento facial| Sí | Sí|
> |Reconocimiento de emociones| Sí | Sí|
> |Asignación y reconstrucción 3D| No | Sí|
> |Detección de contenido| Detecta las funciones generales en lugar de objetos específicos | Sí|
> |Estabilización de vídeo| Sí | Sí|
> |Detección de movimiento| Sí | Sí|
> |Comunidad| Cognitivas Services cuenta con muchos usuarios activos en varios sectores y algunos sitios Web populares, incluidos how-old.net y celebslike.me | OpenCV es un proyecto de código abierto muy popular; miles de personas han contribuido a él y mantenido|
> |Documentación| Cognitivas Services tiene general clara y amplia documentación | Hay muchos ejemplos en línea, pero cada ejemplo está escrito por otra persona y como resultado puede ser una a veces incoherente|
> |Free| Sí, hasta cierto punto (más detalles [aquí](https://azure.microsoft.com/pricing/details/cognitive-services/)) | Sí|
> |Rendimiento| Todas las operaciones y llamadas a API requieren acceso a datos en la nube | Todos los algoritmos están optimizados y local y mediante C++ en lugar de Python aumenta aún más las velocidades|
> |Cámaras/hardware compatible| Cualquier USB o una cámara incrustado | Cualquier USB o una cámara incrustado|
> |Lenguajes y marcos compatibles| C#, UWP | C /C++, Python, Java, C#, UWP|
> |Tiempo de inicio| Los usuarios pueden usar los ejemplos de código junto con una API intuitiva directamente desde la documentación | Eficacia y la flexibilidad de OpenCV significa también requiere una gran cantidad de código para realizar operaciones complejas y la configuración|
> |Vínculos| [Programa de ejemplo](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [Programa de ejemplo](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [Sitio Web de servicios cognitivos](https://azure.microsoft.com/services/cognitive-services/) |  [Sitio Web de OpenCV](http://opencv.org/)


