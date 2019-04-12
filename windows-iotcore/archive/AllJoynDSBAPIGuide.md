---
title: Puente de sistema de dispositivo Alljoyn - Guía de la API
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo asignar objetos de la interfaz de puente para AllJoyn con un IAdapter, que representa el controlador para un sistema de uno o varios dispositivos que se asignan al bus AllJoyn.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 7c928ee0359ba705a4255d309339c48aa8d000a4
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515077"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="mapping-bridge-interface-objects-to-alljoyn"></a>Objetos de interfaz de puente de asignación para AllJoyn

### <a name="i-iadapter"></a>I. IAdapter

Desde la perspectiva del puente, un IAdapter representa el controlador para un sistema de uno o varios dispositivos que se asignan al bus AllJoyn.  IAdapter declara las interfaces necesarias para compatibilidad con enumeración de dispositivos, configuración general y administración del ciclo de vida.  También declara los métodos que interactúan con un dispositivo o propiedades de dispositivos, los métodos y las señales. 

Para exponer los dispositivos como un servicio de AllJoyn, es necesario implementar una clase concreta que se hereda de IAdapter.  Cómo se implementa cada interfaz depende de la naturaleza de los dispositivos que se va a adaptar para AllJoyn. 

El adaptador aparecerá en el bus AllJoyn como un AllJoyn anuncia el servicio con el siguiente nombre: 

```
<ExposedAdapterPrefix>.DeviceSystemBridge.<AdapterName> 
```

Cada adaptador expone dos `com.microsoft.alljoynmanagement.config` interfaces esa configuración de puente y el adaptador de soporte técnico: 

```
/AdapterConfig 

/BusConfig
```
La interfaz de IAdapter declara ciertas propiedades que deben implementarse.  En la tabla siguiente se describe las propiedades y cómo se asignan a AllJoyn:

>  Propiedad IAdapter | Descripción | Asignación de puente |
> | :---------------- | :---------- | :------------- |
> | AdapterName       | Modelo de este adaptador.  También es el sufijo utilizado para nombre anunciados de este adaptador. (Consulte ExposedAdapterPrefix). | AllJoyn sobre el número de modelo de datos |
> | ExposedAdapterPrefix |Prefijo que se usa al crear el nombre de este puente anunciado en el bus de AllJoyn.  El adaptador se verá expuesto con el siguiente nombre: {ExposedAdapterPrefix}. DeviceSystemBridge. {AdapterName}. | Datos adjuntos de Bus AllJoyn anuncian nombre |
> | ExposedApplciationGUID | Un GUID proporcionado por el adaptador, que identifica este adaptador.  Este GUID también se aplica a los datos para todos los dispositivos administrados por este adaptador.|AllJoyn sobre datos de Id. de aplicación para este adaptador y todos los dispositivos que están expuestos por este adaptador. |
> | ExposedApplicationName | Un nombre descriptivo de aplicación expuestos por este adaptador.  Este nombre también se aplica a todos los dispositivos administrados por este adaptador. | AllJoyn sobre datos nombre de la aplicación para este adaptador y todos los dispositivos que están expuestos por este adaptador. |
> | proveedor | Nombre del proveedor de este adaptador | AllJoyn sobre datos fabricante |
> | Versión | Versión de software de este adaptador | AllJoyn acerca de la versión de SO de datos |

#### <a name="iadapterinitialize"></a>IAdapter::Initialize

Inicializa el adaptador. Esto se puede usar igualmente necesita.  Por ejemplo, se pudo iniciar un subproceso en segundo plano para iniciar la detección de dispositivos.  Normalmente, esto se utiliza para crear una inserción de dispositivo y las señales de eliminación del dispositivo. 

#### <a name="iadaptergetsetconfig"></a>IAdapter::Get/SetConfig

Este par de métodos se usan para tener acceso a datos de configuración de su adaptador.  Por lo general, constan de estas opciones de configuración de comunicación que el adaptador necesita para la enumeración de dispositivos, pero no se limitan a ese fin.  

El puente expone los datos de configuración del adaptador para AllJoyn a través de la interfaz "com.microsoft.alljoynmanagement.config".  Desde la perspectiva del puente, los valores de datos de configuración de adaptador son completamente arbitrarios y se intercambian con el adaptador como una matriz de bytes simple.  Internamente, el adaptador, puede almacenar esta configuración según sea necesario.   

#### <a name="iadapterenumdevices"></a>IAdapter::EnumDevices

Este método proporciona el puente con información acerca de los dispositivos disponibles en el bus.  La lista de dispositivos que se devuelven al puente se agregan al bus AllJoyn como AllJoyn los servicios individuales. 

Se debe devolver una lista a través de este método, pero si la enumeración no ha completado una IAdapterIoRequest también puede aparecer aquí.  El puente esperará en esto hasta que el adaptador señala el IAdapterIoRequest para completar la enumeración de dispositivos.   
### <a name="ii-iadapterdevice"></a>II. IAdapterDevice

Desde la perspectiva del puente un dispositivo representa un dispositivo que, el implementador de adaptador, desea exponer en el bus AllJoyn como un AllJoyn Service.  ¿Qué propiedades, métodos y las señales que expone el dispositivo en el bus son depende de usted como implementador de la, pero normalmente sería una asignación directa de las propiedades, métodos y las señales de que el dispositivo o dispositivos intrínsecamente se exponen a través de su red de comunicaciones nativo . 

Cada IAdapterDevice se anuncia a alljoyn con el siguiente nombre: 

    {ExposedAdapterPrefix}.{AdapterName}.{Name} 

Cada dispositivo expone una interfaz de único alljoyn para exponer todas las propiedades, método y las señales encapsuladas por el dispositivo.  Es el nombre de la interfaz de alljoyn: 

    {ExposedAdapterPrefix}.{AdapterName}.{Name}.MainInterface 

Al igual que un IAdapter, cada IAdapterDevice es necesario para implementar propiedades que usa el puente para exponer el dispositivo para AllJoyn.  La tabla siguiente describe cada propiedad y cómo el puente lo asigna a AllJoyn. 

> | Propiedad IAdapterDevice | Descripción | Asignación de puente |
> | :---------------------- | :---------- | :------------- |
> | ControlPanelHandler     | Un panel de control que puede operar a este dispositivo. | Expone como un org.alljoyn.ControlPanel.ControlPanel en un objeto de bus /ControlPanel |
> | Descripción             | Una descripción de este dispositivo. | AllJoyn acerca de la descripción de datos |
> | FirmwareVersion         | Versión de software de este dispositivo | AllJoyn acerca de la versión de Firmware de datos |
> | Icon                    | Icono de gráfico que expone este dispositivo para alljoyn. Esto puede ser null si no hay ningún icono. |     Expone como un icono de sobre AllJoyn estándar |
> | Métodos                 | Este es el conjunto de todos los métodos que expone el dispositivo para AllJoyn. | Esto puede estar vacío si no hay ningún método. Se exponen como métodos en la MainInterface con el nombre de cada método. Los nombres que no son únicos se anexan con un identificador único. |
> | Modelo                   | Modelo de este dispositivo | Número de modelo de datos de Bus de AllJoyn |
> | Nombre                      | Nombre de este nombre de dispositivo de AllJoyn sobre datos del dispositivo. | Esto también se usa para el sufijo de nombre anunciados del dispositivo: {ExposedAdapterPrefix}. {AdapterName}. {Name} |
> | Propiedades              | Este es el conjunto de todas las propiedades que expone el dispositivo para AllJoyn. Esto puede estar vacío si no hay ninguna propiedad, pero si no está vacío, a continuación, al menos una señal, también se debe admitir la señal del cambio de valor. | Consulte IProperty |
> | SerialNumber            | Número de serie de este dispositivo | AllJoyn sobre el número de serie de datos |
> | Señales                 | Este es el conjunto de todas las señales que expone este dispositivo para AllJoyn. | Expuesto como señales de AllJoyn |
> | proveedor                  | Nombre del proveedor de este dispositivo | AllJoyn sobre datos fabricante |
> | Versión                 | Versión de software de este dispositivo | AllJoyn acerca de la versión de SO de datos |


### <a name="iii-iadapterproperty"></a>III. IAdapterProperty

Desde la perspectiva del puente un IAdapterProperty representa una colección de valores de datos relacionados, el implementador de adaptador, desea exponer en el bus de AllJoyn para un dispositivo específico.  Cada propiedad contiene un conjunto de uno o más IAdapterValues.  Cada IAdapterValue representa una unidad de datos que pueden tener acceso a un cliente AllJoyn individual.     

Cada IAdapterProperty se anuncia a Alljoyn como un objeto de bus con un nombre de interfaz como sigue: 

    /{PropertyName} 

    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName} 

Como alternativa, el nombre de la interfaz puede reemplazarse por la propiedad para asignar a un tipo de interfaz específica.  En ese caso, el nombre IAdapterProperty se anuncia como un objeto de bus con un nombre de interfaz como sigue: 

    /{PropertyName} 

    {InterfaceHint} 

> | Propiedades de IAdapterProperty |   Descripción                        | Asignación de puente |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Atributos                |Colección de IAdapterAttributes    | Conjunto de propiedades de AllJoyn (consulte IAdapterValue) |
> | InterfaceHint | Una invalidación para esta propiedad, que puede usarse para asignar esta propiedad a algún otro tipo de interfaz conocida.  Devuelve null para usar el comportamiento predeterminado | Nombre de la interfaz de AllJoyn para esta propiedad (si se especifica) |
> | Nombre | Nombre de propiedad | Propiedad AllJoyn |

### <a name="v-iadaptervalue"></a>V. IAdapterValue

Cada IAdapterValue se expone como un elemento secundario de una propiedad de AllJoyn con el siguiente nombre de objeto y la interfaz de bus:

    /{PropertyName}/{ValueName}
    
    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName}.{ValueName}

> | Propiedades de IAdapterValue    | Descripción                        | Asignación de puente                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Datos                          | El valor de los datos reales de una propiedad en un dispositivo con puente.| Una propiedad AllJoyn|
> | Name                        | Nombre del valor                      | Nombre de una propiedad AllJoyn|

### <a name="iv-iadaptersignal"></a>IV. IAdapterSignal

Desde la perspectiva del puente un ISignal representa un evento que el dispositivo puede generar cuando se produzca algún cambio.  Todos los dispositivos suelen tengan una señal de cambio de valor.  Esta señal alertas AllJoyn los clientes que han cambiado una o varias propiedades en un dispositivo. También pueden admitirse señales adicionales.

Cada ISignal se anuncia a AllJoyn como una señal de sesión hospedada para un dispositivo con el nombre de señales.  
Las siguientes propiedades deben implementarse para una ISignal

> | Propiedades de ISignal          | Descripción                        | Asignación de puente                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Nombre                          |Nombre de señal                      | AllJoyn Signal |
> | params | Un conjunto de objetos que ha cambiado y los nuevos valores o null si se trata de una señal pura. | Se asigna a una matriz de argumentos de la señal de alljoyn pasa a la señal. |
