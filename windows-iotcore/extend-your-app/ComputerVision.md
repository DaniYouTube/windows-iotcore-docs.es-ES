---
title: Computer Vision
ms.date: 08/28/2017
ms.topic: article
description: Aprenda a usar Webstore Cognitive Services y OpenCV para el dispositivo de IoT.
keywords: Windows IOT, Computer Vision, Cognitive Services, OpenCV
ms.openlocfilehash: 74e4ee1303a9c59461f12b59f141c0f7b97d26db
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918190"
---
# <a name="computer-vision"></a>Computer Vision

Los seres humanos perciben nuestro mundo tridimensional con relativa facilidad. A partir de una edad temprana, nuestro cerebro puede recopilar información valiosa, como la identificación de características, la prevención de obstáculos, la coordinación, la percepción de profundidad y muchas otras personas de estímulo visual. Computer Vision es un intento de usar procesadores y cámaras para hacer lo mismo. Tiene innumerables aplicaciones para los dispositivos de hoy en día. Un Dron puede utilizarlo para detectar rápidamente y evitar obstáculos durante el vuelo; un generador puede utilizarlo para detectar defectos cosméticos en los componentes más pequeños de la línea de montaje; Además, una persona puede utilizarla para detectar su tarifa cardíaca sin usar el equipo de un monitor o médico. Nuestro mundo centrado en datos ha hecho que el equipo de Vision sea un área de investigación increíblemente activa. Las compañías lo están usando de maneras consideradas improbables, incluso hace diez años. A medida que los equipos, las cámaras y los datos se hacen más innecesarios en nuestra sociedad, las herramientas necesarias para aprovechar las capacidades más emocionantes de Computer Vision deben ser más fáciles de acceder y usar como sea posible. Windows 10 IoT Core intenta satisfacer esta necesidad a través de la compatibilidad con dos ofertas: Microsoft Cognitive Services y OpenCV.

## <a name="services"></a>Servicios
___

### <a name="cognitive-services"></a>Cognitive Services

#### <a name="overview"></a>Introducción
Cognitive Services, originalmente un proyecto de Microsoft Research denominado Project Oxford, es una colección de API que realizan "tareas cognitivas" de alto nivel. Estas API extraen información de sus datos en función de los modelos de aprendizaje automático muy entrenados de años de exploración y desarrollo en Microsoft Research.

Cognitive Services se compone de 5 categorías: visión, voz, lenguajes, conocimiento y búsqueda.

Puede encontrar más información sobre Cognitive Services en el [sitio web](https://www.microsoft.com/cognitive-services)de Cognitive Services.

La categoría visión, la categoría más valiosa de Computer Vision Applications, contiene cuatro API: Computer Vision, emoción, facial y vídeo. Estas API proporcionan la siguiente funcionalidad:
- Reconocimiento facial
- Detección de movimiento
- Reconocimiento de emociones
- Estabilización de vídeo
- Análisis del contenido de la imagen

Cognitive Services es excelente para trabajar con una gran cantidad de datos, tener acceso a Microsoft Azure y reducir considerablemente el tiempo de comercialización de la aplicación, ya que las API de visión a menudo demuestran que tardan mucho en desarrollarse de forma independiente. El modelo usado para estas API es bien entrenado y extensivo gracias a los esfuerzos de Microsoft Research. Por otro lado, su requisito de conectividad en la nube reduce el rendimiento del sistema y crea el requisito de una conexión a Internet.

#### <a name="pricing"></a>Precios
Cada suscripción de API incluye un conjunto de transacciones gratuitas cada mes (de 300 a 30.000, en función de la API). Después de superar esta cantidad inicial, los servicios tienen un precio razonable. Por ejemplo, el Emotion API proporciona las primeras 30.000 transacciones gratis y requiere $0,10 o $0,25 cada 1000 transacción, según el tipo de suscripción.

Encontrará más información sobre los precios de Cognitive Services en su [sitio web](https://www.microsoft.com/cognitive-services/en-us/pricing).

#### <a name="get-started"></a>Comenzar
Para usar Cognitive Services, los usuarios deben registrarse en el sitio web de Congitive Services para recibir claves de API. Después de proporcionar una clave de API para Cognitive Services, los usuarios pueden llamar a las API dentro de las limitaciones mencionadas en la sección "precios".

La documentación de cada API puede encontrarse en el [sitio web](https://www.microsoft.com/cognitive-services/en-us/documentation)de Cognitive Services.

Todos los Cognitive Services APIs se pueden implementar en cualquier plataforma de C#hardware mediante.

¿Quiere ejecutar Cognitive Services en el dispositivo IoT? Visite nuestro [tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/cognitiveservices) para comenzar.

### <a name="opencv"></a>OpenCV

OpenCV es una biblioteca de software de código abierto y de aprendizaje automático diseñado para la eficacia computacional y aplicaciones en tiempo real. Es muy popular entre desarrolladores y en el sector debido a su eficiencia sin precedentes, herramientas versátiles, soporte técnico para una amplia gama de plataformas y una comunidad en línea en línea de los desarrolladores. Es la herramienta informática de código abierto más conocida. Las bibliotecas de OpenCV están disponibles paraC++C/, Java C#y.

El [sitio web](http://opencv.org/) de OpenCV proporciona detalles adicionales.

Características de OpenCV:
- Procesamiento y análisis de imágenes locales y vídeo
- Identificación, coincidencia y seguimiento de objetos en tiempo real
- Reconocimiento facial en tiempo real
- Determinación de la distancia a partir de la imagen y en tiempo real
- asignación/modelado/reconstrucción 3D
- Edición de imágenes (como composición y cambio de color)

OpenCV ofrece una serie de ventajas. Es muy eficaz para el procesamiento de datos locales debido a las e/C++ s optimizadas y el acceso a la GPU mediante OpenCL (si está habilitado). Contiene la mayoría de las funciones de Computer Vision, si no todas, disponibles actualmente. Su longevidad y utilidad han formado una comunidad en línea amplia y experimentada que puede ayudar a los nuevos usuarios a solucionar problemas de aplicaciones o bibliotecas. Por otro lado, hay una curva de aprendizaje pronunciada debida al código complejo y a la configuración de la biblioteca, así como a las incoherencias en los tutoriales y el código de ejemplo.

Actualmente, OpenCV con IoT Core solo funciona si los usuarios compilan la biblioteca desde el origen, lo que puede llevar mucho tiempo. Por esta razón, estamos trabajando activamente para que OpenCV resulte más fácil de configurar en IoT Core mediante la creación de una colección de paquetes de NuGet. Un paquete de NuGet, que Cognitive Services usa, permite a los desarrolladores importar una biblioteca precompilada en su aplicación, lo que proporciona una funcionalidad completa con unos pocos clics. La aplicación que usa el paquete NuGet seguirá recibiendo actualizaciones de biblioteca desde un servidor dedicado. el usuario no necesita volver a generar el código fuente nuevo cuando haya cambios públicos en el software de código abierto. El paquete también libera espacio de almacenamiento en los dispositivos que solo usan partes de la biblioteca.

Actualmente se trata de un trabajo en curso, por lo que debe seguir comprobando si hay actualizaciones de WindowsOnDevices.com.

Mientras tanto, para compilar la biblioteca desde el origen para ARM, visite el [repositorio de github](https://github.com/Microsoft/opencv/tree/vs2015-samples-ARM).

¿Quiere ejecutar OpenCV en el dispositivo de IoT Core? Visite nuestro [tutorial](https://developer.microsoft.com/en-us/windows/iot/samples/opencv) para comenzar.

## <a name="comparing-opencv-and-cognitive-services"></a>Comparar OpenCV y Cognitive Services

> |        |Microsoft Cognitive Services|OpenCV|
> |---------------------|--------|------|
> |Fácil de usar en Windows|Sí|No |
> |Compatibilidad con la arquitectura|ARM, x86, x64 | ARM, x86, x64|
> |Reconocimiento facial y seguimiento| Sí | Sí|
> |Reconocimiento de emociones| Sí | Sí|
> |reconstrucción y asignación 3D| No | Sí|
> |Detección de contenido| Detecta características generales en lugar de objetos específicos | Sí|
> |Estabilización de vídeo| Sí | Sí|
> |Detección de movimiento| Sí | Sí|
> |Comunidad| Cognitive Services tiene muchos usuarios activos en varios sectores y algunos sitios web populares, como how-old.net y celebslike.me | OpenCV es un proyecto de código abierto muy popular; miles de personas han contribuido a ti y lo mantuvieron|
> |Documentación| Cognitive Services tiene una documentación global y clara | Hay muchos ejemplos disponibles en línea, pero cada ejemplo está escrito por otra persona y, como resultado, puede ser incoherente a veces|
> |Free| Sí, hasta una extensión (más detalles [aquí](https://azure.microsoft.com/pricing/details/cognitive-services/)) | Sí|
> |Rendimiento| Todas las operaciones y llamadas API requieren el acceso a los datos en la nube | Todos los algoritmos están optimizados y son locales C++ , y el uso en lugar de Python aumenta aún más la velocidad|
> |Cámaras y hardware compatibles| Cualquier cámara USB o incrustada | Cualquier cámara USB o incrustada|
> |Lenguajes o marcos de trabajo admitidos| C#, UWP | C/C++, Python, Java, C#, UWP|
> |Hora de inicio| Los usuarios pueden usar ejemplos de código junto con las API intuitivas directamente desde la documentación | La potencia y la flexibilidad de OpenCV significa que también requiere una gran cantidad de configuración y código para realizar operaciones complejas|
> |Vínculos| [Programa de ejemplo](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/CognitiveServicesExample) | [Programa de ejemplo](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/OpenCVExample) |
> |    |   [Sitio web Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) |  [Sitio web de OpenCV](http://opencv.org/)


