---
title: 'Puente de sistema de dispositivos Alljoyn: Guía de API'
author: saraclay
ms.author: saclayt
ms.date: 09/06/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo asignar objetos de interfaz de puente a AllJoyn mediante IAdapter, que representa el controlador de un sistema de uno o más dispositivos que se asignan al bus AllJoyn.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 7c928ee0359ba705a4255d309339c48aa8d000a4
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169013"
---
> [!NOTE]
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="mapping-bridge-interface-objects-to-alljoyn"></a>Asignación de objetos de interfaz de puente a AllJoyn

### <a name="i-iadapter"></a>CONFIGUR. IAdapter

Desde la perspectiva del puente, IAdapter representa el controlador de un sistema de uno o más dispositivos que se asignan al bus AllJoyn.  IAdapter declara las interfaces necesarias para admitir la enumeración de dispositivos, la configuración general y la administración del ciclo de vida.  También declara métodos que interactúan con las propiedades, los métodos y las señales de un dispositivo o dispositivo. 

Para exponer los dispositivos como un servicio AllJoyn, es necesario implementar una clase concreta que herede de IAdapter.  La forma en que se implementa cada interfaz depende de la naturaleza de los dispositivos que se están adaptando a AllJoyn. 

El adaptador aparecerá en el bus AllJoyn como un servicio AllJoyn anunciado con el siguiente nombre: 

```
<ExposedAdapterPrefix>.DeviceSystemBridge.<AdapterName> 
```

Cada adaptador expone dos `com.microsoft.alljoynmanagement.config` interfaces que admiten la configuración de puente y adaptador: 

```
/AdapterConfig 

/BusConfig
```
La interfaz IAdapter declara ciertas propiedades que se deben implementar.  En la tabla siguiente se describen esas propiedades y cómo se asignan a AllJoyn:

>  Propiedad IAdapter | Descripción | Asignación de puente |
> | :---------------- | :---------- | :------------- |
> | AdapterName       | Modelo de este adaptador.  También es el sufijo utilizado para el nombre anunciado de este adaptador. (Consulte ExposedAdapterPrefix). | AllJoyn acerca del número de modelo de datos |
> | ExposedAdapterPrefix |Prefijo que se usa al crear el nombre anunciado de este puente en el bus AllJoyn.  El adaptador se expondrá con el siguiente nombre: {ExposedAdapterPrefix}. DeviceSystemBridge. {AdapterName}. | Nombre anunciado de datos adjuntos de bus AllJoyn |
> | ExposedApplciationGUID | Un GUID, proporcionado por el adaptador, que identifica de forma única este adaptador.  Este GUID también se aplica a la información acerca de los datos de todos los dispositivos administrados por este adaptador.|AllJoyn acerca del ID. de la aplicación de datos para este adaptador y todos los dispositivos expuestos por este adaptador. |
> | ExposedApplicationName | Nombre descriptivo de la aplicación expuesto por este adaptador.  Este nombre también se aplica a todos los dispositivos administrados por este adaptador. | AllJoyn acerca del nombre de la aplicación de datos para este adaptador y todos los dispositivos expuestos por este adaptador. |
> | Proveedor | Nombre del proveedor de este adaptador | AllJoyn acerca del fabricante de datos |
> | `Version` | Versión de software de este adaptador | AllJoyn acerca de la versión de Data SW |

#### <a name="iadapterinitialize"></a>IAdapter:: Initialize

Inicializa el adaptador. Se puede usar de todos modos.  Por ejemplo, se puede iniciar un subproceso en segundo plano para iniciar la detección de dispositivos.  Normalmente, también se usa para crear una inserción de dispositivo y señales de eliminación de dispositivos. 

#### <a name="iadaptergetsetconfig"></a>IAdapter:: get/SetConfig

Este par de métodos se utiliza para tener acceso a los datos de configuración del adaptador.  Normalmente, estas opciones de configuración se componen de la configuración de comunicación que necesita el adaptador para la enumeración de dispositivos, pero no se limitan a ese propósito.  

El puente expone los datos de configuración del adaptador a AllJoyn a través de la interfaz "com. Microsoft. alljoynmanagement. config".  Desde la perspectiva del puente, los valores de los datos de configuración del adaptador son completamente arbitrarios y se intercambian con el adaptador como una matriz de bytes simple.  Internamente en el adaptador, puede almacenar estos valores como desee.   

#### <a name="iadapterenumdevices"></a>IAdapter:: EnumDevices

Este método proporciona al puente información acerca de los dispositivos disponibles en el bus.  La lista de dispositivos que se devuelven al puente se agregan al bus AllJoyn como servicios de AllJoyn individuales. 

Se debe devolver una lista a través de este método, pero si la enumeración no ha completado un IAdapterIoRequest, también se puede devolver aquí.  El puente esperará hasta que el adaptador señale a IAdapterIoRequest para completar la enumeración del dispositivo.   
### <a name="ii-iadapterdevice"></a>II. IAdapterDevice

Desde la perspectiva del puente un dispositivo representa un dispositivo que usted, el implementador del adaptador, desea exponer al bus de AllJoyn como un servicio AllJoyn.  ¿Qué propiedades, métodos y señales expone el dispositivo al bus como implementador, pero normalmente esto sería una asignación directa de propiedades, métodos y señales que el dispositivo o los dispositivos exponen de forma inherente a su red de comunicaciones nativas? . 

Cada IAdapterDevice se anuncia a alljoyn con el siguiente nombre: 

    {ExposedAdapterPrefix}.{AdapterName}.{Name} 

Cada dispositivo expone una única interfaz alljoyn para exponer todas las propiedades, el método y las señales encapsuladas por el dispositivo.  El nombre de la interfaz alljoyn es: 

    {ExposedAdapterPrefix}.{AdapterName}.{Name}.MainInterface 

De forma similar a IAdapter, cada IAdapterDevice es necesario para implementar propiedades que el puente usa para exponer el dispositivo a AllJoyn.  En la tabla siguiente se describe cada propiedad y cómo la asigna el puente a AllJoyn. 

> | Propiedad IAdapterDevice | Descripción | Asignación de puente |
> | :---------------------- | :---------- | :------------- |
> | ControlPanelHandler     | Un panel de control que puede usar este dispositivo. | Se expone como org. alljoyn. ControlPanel. ControlPanel en un objeto de bus/ControlPanel |
> | Descripción             | Descripción de este dispositivo. | Información general acerca de la descripción de datos |
> | FirmwareVersion         | Versión de software de este dispositivo | AllJoyn acerca de la versión de firmware de datos |
> | Icon                    | Icono gráfico que expone este dispositivo a alljoyn. Puede ser null si no hay ningún icono. |     Se expone como un icono de información de AllJoyn estándar |
> | Métodos                 | Este es el conjunto de todos los métodos que expone el dispositivo a AllJoyn. | Puede estar vacío si no hay métodos. Se expone como métodos en MainInterface con el nombre de cada método. Los nombres no únicos se anexan con un identificador único. |
> | Modelo                   | Modelo de este dispositivo | Número de modelo de datos de bus AllJoyn |
> | NOMBRE                      | Nombre de este dispositivo AllJoyn sobre el nombre del dispositivo de datos. | También se usa para el sufijo del nombre anunciado de este dispositivo: {ExposedAdapterPrefix}. {AdapterName}. Name |
> | Propiedades              | Este es el conjunto de todas las propiedades que expone el dispositivo a AllJoyn. Puede estar vacío si no hay ninguna propiedad, pero si no está vacía, debe admitirse también al menos una señal, el cambio de la señal de valor. | Consulte IProperty |
> | SerialNumber            | Número de serie de este dispositivo | AllJoyn acerca del número de serie de datos |
> | Simultáneamente                 | Este es el conjunto de todas las señales que expone este dispositivo a AllJoyn. | Expuesto como señales AllJoyn |
> | Proveedor                  | Nombre del proveedor de este dispositivo | AllJoyn acerca del fabricante de datos |
> | `Version`                 | Versión de software de este dispositivo | AllJoyn acerca de la versión de Data SW |


### <a name="iii-iadapterproperty"></a>ORDEN. IAdapterProperty

Desde la perspectiva del puente, un IAdapterProperty representa una colección de valores de datos relacionados que usted, el implementador del adaptador, desea exponer al bus AllJoyn para un dispositivo específico.  Cada propiedad contiene un conjunto de uno o varios IAdapterValues.  Cada IAdapterValue representa una unidad de datos individual a la que puede tener acceso un cliente AllJoyn.     

Cada IAdapterProperty se anuncia a Alljoyn como un objeto de bus con un nombre de interfaz como se indica a continuación: 

    /{PropertyName} 

    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName} 

Como alternativa, el nombre de la interfaz puede reemplazarse por la propiedad para asignarse a un tipo de interfaz específico.  En ese caso, el nombre de IAdapterProperty se anuncia como un objeto de bus con un nombre de interfaz como se indica a continuación: 

    /{PropertyName} 

    {InterfaceHint} 

> | Propiedades de IAdapterProperty |   Descripción                        | Asignación de puente |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Atributos                |Colección de IAdapterAttributes    | Conjunto de propiedades de AllJoyn (vea IAdapterValue) |
> | InterfaceHint | Una invalidación para esta propiedad que se puede usar para asignar esta propiedad a algún otro tipo de interfaz muy conocido.  Devolver null para usar el comportamiento predeterminado | Nombre de la interfaz AllJoyn para esta propiedad (si se especifica) |
> | NOMBRE | Nombre de la propiedad | AllJoyn (propiedad) |

### <a name="v-iadaptervalue"></a>V. IAdapterValue

Cada IAdapterValue se expone como un elemento secundario de una propiedad AllJoyn con el siguiente objeto de bus y el nombre de interfaz:

    /{PropertyName}/{ValueName}
    
    {ExposedAdapterPrefix}.{AdapterName}.{PropertyName}.{ValueName}

> | Propiedades de IAdapterValue    | Descripción                        | Asignación de puente                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | Datos                          | Valor de datos real de una propiedad en un dispositivo puente.| Propiedad AllJoyn|
> | NOMBRE                        | Nombre del valor                      | Nombre de una propiedad AllJoyn|

### <a name="iv-iadaptersignal"></a>CUARTA. IAdapterSignal

Desde la perspectiva del puente, un ISignal representa un evento que el dispositivo puede generar cuando se produce algún cambio.  Todos los dispositivos suelen tener un cambio de señal de valor.  Esta señal alerta a los clientes de AllJoyn de que una o más propiedades han cambiado en un dispositivo. También pueden admitirse señales adicionales.

Cada ISignal se anuncia a AllJoyn como una señal de sesión hospedada para un dispositivo con el nombre de señales.  
Las siguientes propiedades se deben implementar para un ISignal

> | Propiedades de ISignal          | Descripción                        | Asignación de puente                                |
> | :-------------------------- | :--------------------------------- | :-------------------------------------------- |
> | NOMBRE                          |Nombre de la señal                      | Señal AllJoyn |
> | Params | Un conjunto de objetos que han cambiado y sus nuevos valores, o null si se trata de una señal pura. | Asigna a una matriz de argumentos de señal alljoyn pasados a la señal. |
