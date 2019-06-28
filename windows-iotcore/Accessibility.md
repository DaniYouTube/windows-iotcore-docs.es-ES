---
title: Accesibilidad de Windows 10 IoT
author: saraclay
ms.author: saclayt
ms.date: 03/8/2018
ms.topic: article
description: Obtenga información sobre la accesibilidad y aprenda a aplicar los conocimientos adquiridos en su próxima aplicación o dispositivo.
keywords: Windows 10 IoT Core, Windows 10 IoT Enterprise, accesibilidad, contraste de color
ms.openlocfilehash: 149c47fc9cae7fb99eb6aa190055c13284c3e197
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2019
ms.locfileid: "60167354"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>Información general sobre la accesibilidad en Windows IoT 
 
## <a name="introduction"></a>Introducción 
La accesibilidad permite a usuarios con diferentes capacidades aprovechar de forma intuitiva y eficaz todas las funcionalidades que ofrecen las aplicaciones o los dispositivos, independientemente de si la persona interactúa con estos. 
 
Es fundamental tener en cuenta la accesibilidad durante la fase de diseño del producto, ya que esto evitará muchos posibles errores relacionados con la accesibilidad. Por ejemplo, durante la fase de diseño, se puede ayudar a numerosos clientes si se tienen en cuenta los colores usados y el tamaño de texto (y cómo el usuario puede personalizar estas opciones). En cuanto a los dispositivos con teclado, conviene considerar durante la fase de diseño cómo se puede usar el teclado para aprovechar toda la funcionalidad del producto y cómo se puede acceder a las funcionalidades usadas con más frecuencia con el menor número posible de pulsaciones de teclas.  
 
Afortunadamente para el desarrollador, desde el punto de vista de la implementación, Windows es una plataforma que por su parte ya proporciona cierto grado de accesibilidad de forma predeterminada. Por ejemplo, se puede acceder a los controles estándar mediante programación de forma predeterminada a través de la API de Automatización de la interfaz de usuario (UIA). Si decide no usar un control estándar y, en su lugar, compilar una interfaz de usuario personalizada, el trabajo necesario para garantizar la accesibilidad de la interfaz de usuario puede llevar mucho más tiempo que simplemente crear las aplicaciones con los controles estándar que proporciona la plataforma. 

## <a name="accessibility-testing"></a>Pruebas de accesibilidad
A continuación se muestran las herramientas recomendadas durante la compilación de la aplicación. Aunque le resultarán de gran ayuda para llevar a cabo una auditoría de sus propios diseños, tendrá que tener en cuenta igualmente características como los requisitos de texto y de contraste alto.

### <a name="accscope"></a>AccScope
La herramienta [AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) permite que los desarrolladores y los evaluadores evalúen la accesibilidad de la aplicación durante la fase de desarrollo y diseño de la aplicación, y posiblemente en fases anteriores del prototipo, en lugar de hacerlo en las fases de prueba más avanzadas del ciclo de desarrollo de la aplicación. Está diseñada especialmente para probar los escenarios de accesibilidad de la característica Narrador con la aplicación.

### <a name="inspect"></a>Inspect
[Inspect](https://msdn.microsoft.com/library/windows/desktop/Dd318521) permite seleccionar cualquier elemento de la interfaz de usuario y ver sus datos de accesibilidad. Puedes ver los modelos de control y las propiedades de Automatización de la interfaz de usuario de Microsoft y probar la estructura de navegación de los elementos de automatización en el árbol de automatización de la interfaz de usuario. Use Inspect mientras desarrolla la interfaz de usuario para comprobar cómo se exponen los atributos de accesibilidad en la automatización de la interfaz de usuario. En algunos casos, los atributos provienen de la compatibilidad para la automatización de la interfaz de usuario que ya viene implementada en los controles XAML predeterminados. En otros casos, los atributos provienen de valores específicos que ha definido en el marcado XAML, como propiedades adjuntas AutomationProperties.

¿Le interesa obtener más información sobre las pruebas de accesibilidad? En el artículo [Pruebas de accesibilidad](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect) encontrará una lista completa.
 
 
## <a name="accessibility-in-uwp-apps"></a>Accesibilidad en aplicaciones para UWP 
El equipo de UWP de Microsoft ha elaborado una guía completa sobre la accesibilidad en el desarrollo y el diseño de aplicaciones para UWP. Para mayor comodidad hemos incluido una lista más abajo, pero también puede profundizar en los detalles en el artículo [Información general sobre accesibilidad](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview). 
 
Además, a continuación encontrará una introducción a la API de Automatización de la interfaz de usuario y algunas herramientas que le ayudarán a obtener información sobre la representación mediante programación de la interfaz de usuario. 
 
> [!VIDEO https://www.youtube.com/embed/6b0K2883rXA]

 
| Artículo | Descripción | 
|---------|-------------| 
| [Diseño de software inclusivo](https://docs.microsoft.com/windows/uwp/design/accessibility/designing-inclusive-software) | Aprende sobre la evolución del diseño inclusivo con aplicaciones para UWP para Windows 10.  Diseña y crea software inclusivo teniendo en cuenta la accesibilidad. | 
| [Desarrollo de aplicaciones inclusivas de Windows](https://docs.microsoft.com/windows/uwp/design/accessibility/developing-inclusive-windows-apps) | Este artículo es una guía básica para desarrollar aplicaciones para UWP accesibles. | 
| [Lista de comprobación de accesibilidad](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-checklist) | Proporciona una lista de comprobación que te ayudará a garantizar que tu aplicación para UWP sea accesible. | 
| [Exponer información básica de accesibilidad](https://docs.microsoft.com/windows/uwp/design/accessibility/basic-accessibility-information) | La información de accesibilidad básica se suele clasificar en nombre, rol y valor. En este tema se describe el código para ayudar a que tu aplicación exponga la información básica requerida por las tecnologías de asistencia. | 
| [Accesibilidad de teclado](https://docs.microsoft.com/windows/uwp/design/accessibility/keyboard-accessibility) | Si tu aplicación no proporciona un buen acceso de teclado, los usuarios invidentes o con problemas de motricidad pueden llegar a tener dificultades para usar tu aplicación o, probablemente, no puedan usarla. | 
| [Temas de contraste alto](https://docs.microsoft.com/windows/uwp/design/accessibility/high-contrast-themes) | Describe los pasos necesarios para asegurarte de que tu aplicación para UWP pueda usarse cuando esté activo un tema de contraste alto. | 
| [Requisitos de texto accesible](https://docs.microsoft.com/windows/uwp/design/accessibility/accessible-text-requirements) | En este tema se describen los procedimientos recomendados sobre accesibilidad de texto en una aplicación mediante la configuración de los colores de texto y fondo, de forma que cumplan con la relación de contraste necesaria. También se analizan los roles de Automatización de la interfaz de usuario de Microsoft que pueden tener los elementos de texto en una aplicación para UWP y los procedimientos recomendados para texto en elementos gráficos. | 
| [Procedimientos de accesibilidad que deben evitarse](https://docs.microsoft.com/windows/uwp/design/accessibility/practices-to-avoid) | Enumera los procedimientos que se deben evitar si quieres crear una aplicación accesible para UWP. | 
| [Automatización del mismo nivel personalizado](https://docs.microsoft.com/windows/uwp/design/accessibility/custom-automation-peers) | Describe el concepto de automatización del mismo nivel para la Automatización de la interfaz de usuario de Microsoft y cómo puedes proporcionar compatibilidad de automatización para tu propia clase de interfaz de usuario personalizada. | 
 
