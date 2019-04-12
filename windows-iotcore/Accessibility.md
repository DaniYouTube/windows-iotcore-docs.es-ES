---
title: Accesibilidad para Windows 10 IoT
author: saraclay
ms.author: saclayt
ms.date: 03/8/2018
ms.topic: article
description: Obtenga información sobre la accesibilidad y cómo aplicar estos conocimientos en la siguiente aplicación o dispositivo.
keywords: Windows 10 IoT Core, Windows 10 IoT Enterprise, accesibilidad, el contraste de color
ms.openlocfilehash: 149c47fc9cae7fb99eb6aa190055c13284c3e197
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514755"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>Información general sobre accesibilidad para Windows IoT 
 
## <a name="introduction"></a>Introducción 
Accesibilidad permite a los usuarios de todas las capacidades de forma intuitiva y eficaz aprovechar todas las funcionalidades que su oferta de aplicaciones o dispositivos, independientemente de una persona interactúa con la aplicación o dispositivo. 
 
Es fundamental que la accesibilidad se considera durante la fase de diseño del producto como esto evitará muchas posibles errores relacionados con la accesibilidad. Por ejemplo, durante la fase de diseño, consideración en torno a los colores usados y el tamaño de texto (y cómo los pueden personalizar, por el usuario) pueden ayudar a un gran muchos clientes. Y para dispositivos con un teclado, durante la fase de diseño, consideraciones acerca de cómo se puede usar el teclado para aprovechar toda la funcionalidad en el producto y también cómo tener acceso a la funcionalidad de acceso más frecuente con el menor número de pulsaciones de teclas.  
 
Para el desarrollador, desde una perspectiva de la implementación la buena noticia es que Windows, como una plataforma hace ya mucho trabajo para proporcionar cierto nivel de accesibilidad de forma predeterminada. Por ejemplo, los controles estándar son accesibles mediante programación a través de la UI Automation (UIA) API de forma predeterminada. Si decide no utilizar un control estándar y compilar en su lugar la interfaz de usuario personalizada, el trabajo necesario para realizar la accesibilidad de interfaz de usuario puede resultar mucho más lento que basta con crear aplicaciones con controles estándares proporcionados por la plataforma. 

## <a name="accessibility-testing"></a>Pruebas de accesibilidad
A continuación se muestran las herramientas que se recomienda para usar al compilar cualquier aplicación. Aunque estas herramientas le ayudarán a cuando se trata de auditoría de sus propios diseños, tenga en cuenta que todavía necesitará tener en cuenta las características como los requisitos de texto y de contraste alto.

### <a name="accscope"></a>AccScope
El [AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) herramienta permite a los desarrolladores y evaluadores evaluar la accesibilidad de su aplicación durante el desarrollo y el diseño, la aplicación potencialmente en fases de prototipo anteriormente, en lugar de en las fases de pruebas en tiempo de ejecución de una aplicación ciclo de desarrollo. Está diseñada especialmente para probar los escenarios de accesibilidad de la característica Narrador con la aplicación.

### <a name="inspect"></a>Inspect
[Inspeccionar](https://msdn.microsoft.com/library/windows/desktop/Dd318521) le permite seleccionar cualquier elemento de interfaz de usuario y ver sus datos de accesibilidad. Puedes ver los modelos de control y las propiedades de Automatización de la interfaz de usuario de Microsoft y probar la estructura de navegación de los elementos de automatización en el árbol de automatización de la interfaz de usuario. Utilice inspeccionar durante el desarrollo de la interfaz de usuario para comprobar cómo se exponen los atributos de accesibilidad en la automatización de interfaz de usuario. En algunos casos, los atributos provienen de la compatibilidad para la automatización de la interfaz de usuario que ya viene implementada en los controles XAML predeterminados. En otros casos los atributos proceden de los valores específicos que se configuraron en el marcado XAML, como AutomationProperties propiedades adjuntas.

¿Desea obtener más información sobre la comprobación de accesibilidad? Leer el [artículo pruebas accesibilidad](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect) para ver la lista completa.
 
 
## <a name="accessibility-in-uwp-apps"></a>Accesibilidad en aplicaciones para UWP 
El equipo UWP de Microsoft ha elaborado a una guía completa sobre la accesibilidad para el desarrollo y diseño de aplicaciones para UWP. Para su comodidad, hemos incluido la siguiente lista, pero también puede aprender más, lea nuestra [información general sobre accesibilidad](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview). 
 
Además, una introducción a la API de automatización de interfaz de usuario y algunas herramientas disponibles para ayudarle a obtener información sobre la representación mediante programación de la interfaz de usuario, está disponible a continuación. 
 
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
| [Automatización del mismo nivel personalizada](https://docs.microsoft.com/windows/uwp/design/accessibility/custom-automation-peers) | Describe el concepto de automatización del mismo nivel para la Automatización de la interfaz de usuario de Microsoft y cómo puedes proporcionar compatibilidad de automatización para tu propia clase de interfaz de usuario personalizada. | 
 
