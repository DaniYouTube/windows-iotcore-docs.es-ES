---
title: Productores AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo hacer que un productor AllJoyn por aprender y creación introspección XML y sus características diferentes.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514512"
---
> [!NOTE]
> <span data-ttu-id="da35a-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="da35a-104">You are viewing archived documentation.</span></span> <span data-ttu-id="da35a-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="da35a-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="da35a-106">Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.</span><span class="sxs-lookup"><span data-stu-id="da35a-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="da35a-107">Productores AllJoyn</span><span class="sxs-lookup"><span data-stu-id="da35a-107">AllJoyn Producers</span></span>

<span data-ttu-id="da35a-108">AllJoyn, creado por el [AllSeen Alliance](https://allseenalliance.org/), proporciona un marco excelente para hacer que los dispositivos conectados y aplicaciones en una red articulaciones próximas y Windows proporciona la mejor experiencia para el uso de AllJoyn con las [AllJoyn Studio ](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extensión para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da35a-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="da35a-109">Mientras que sobresale con nuestras herramientas de creación de aplicaciones para los productores y consumidores, puede resultar muy confuso a partir de un nuevo dispositivo AllJoyn desde cero.</span><span class="sxs-lookup"><span data-stu-id="da35a-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="da35a-110">Si tiene alguna idea para el dispositivo conectado excelente siguiente o un juguete nuevo con la que se va a realizar ajustes y explore, es posible que no pueda usar una de las interfaces estándares que ofrece la alianza AllSeen.</span><span class="sxs-lookup"><span data-stu-id="da35a-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="da35a-111">Si es así, deberá crear un productor AllJoyn completamente nuevo.</span><span class="sxs-lookup"><span data-stu-id="da35a-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="da35a-112">Un desarrollador que desean realizar un productor AllJoyn nuevo debe crear su propio XML introspección, pero crear XML de introspección requiere experiencia en la materia y tiene una considerable curva de aprendizaje para desarrolladores nuevo.</span><span class="sxs-lookup"><span data-stu-id="da35a-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="da35a-113">Esta entrada de blog, reduce la curva de aprendizaje desglosando los distintos componentes de introspección XML, que describe el propósito y las restricciones de cada componente, y proporcionando buenos ejemplos en términos asequible.</span><span class="sxs-lookup"><span data-stu-id="da35a-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="da35a-114">Documentación existente</span><span class="sxs-lookup"><span data-stu-id="da35a-114">Existing documentation</span></span>

<span data-ttu-id="da35a-115">Un examen de los siguientes recursos que se combina con esta entrada de blog debe acelerar developer comprensión de introspección XML:</span><span class="sxs-lookup"><span data-stu-id="da35a-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="da35a-116">[Guía de la API de acciones y eventos de AllJoyn](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn información general y detalles de implementación.</span><span class="sxs-lookup"><span data-stu-id="da35a-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="da35a-117">[Instrucciones de diseño de AllJoyn interfaz Review Board](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) -estructurar estrictos y la especificación para AllJoyn introspección XML.</span><span class="sxs-lookup"><span data-stu-id="da35a-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="da35a-118">[Especificación de Bus de D](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn basa introspección XML en esta especificación.</span><span class="sxs-lookup"><span data-stu-id="da35a-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

__<span data-ttu-id="da35a-119">Los tres tipos de introspección XML</span><span class="sxs-lookup"><span data-stu-id="da35a-119">The three types of Introspection XML</span></span>__

<span data-ttu-id="da35a-120">Como leer detenidamente la documentación de AllJoyn, encontrará tres tipos de introspección XML:</span><span class="sxs-lookup"><span data-stu-id="da35a-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="da35a-121">XML de especificación de Bus de D: comunicación entre procesos, de baja sobrecarga con un formato de tipo para la representación de datos.</span><span class="sxs-lookup"><span data-stu-id="da35a-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="da35a-122">Introspección AllJoyn XML: amplía XML de especificación de Bus de D con las etiquetas XML que contiene descripciones textuales al aplicar también AllJoyn principios para la especificación.</span><span class="sxs-lookup"><span data-stu-id="da35a-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="da35a-123">Había extendido AllJoyn introspección XML: evolución de la introducción de introspección XML clásico había denominado tipos para las estructuras y diccionarios.</span><span class="sxs-lookup"><span data-stu-id="da35a-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="da35a-124">AllJoyn Studio actualmente es compatible con XML de especificación de Bus de D y AllJoyn introspección XML; este blog determinará cómo crear y formulario AllJoyn introspección XML.</span><span class="sxs-lookup"><span data-stu-id="da35a-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="da35a-125">Interfaz Review Board (IRB de la alianza AllSeen) usa el nuevo introspección de AllJoyn extendido como el formato para envíos formales para las revisiones de estandarización, pero está trabajando en un formato XML de introspección unificada para el futuro próximo.</span><span class="sxs-lookup"><span data-stu-id="da35a-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="da35a-126">Introducción de alto nivel introspección</span><span class="sxs-lookup"><span data-stu-id="da35a-126">Introspection High Level Overview</span></span>

<span data-ttu-id="da35a-127">Cada productor AllJoyn anuncia públicamente un archivo XML de introspección presenta funcionalidad admitida del productor: interfaces como se describe a través de las señales, propiedades y métodos.</span><span class="sxs-lookup"><span data-stu-id="da35a-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="da35a-128">Soluciones de generación de código, como el de la extensión AllJoyn Studio, dependen de introspección XML para crear el código necesario para acelerar el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="da35a-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="da35a-129">Introspección XML describe la funcionalidad de un productor de forma no ambigua y legible que dos distintos fabricantes pueden usar el código XML para implementar un productor con la misma funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="da35a-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="da35a-130">Con el mismo token, los desarrolladores con ningún conocimiento anterior de un productor AllJoyn deberían poder desarrollar en que el productor según su XML.</span><span class="sxs-lookup"><span data-stu-id="da35a-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

__<span data-ttu-id="da35a-131">Interfaces de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="da35a-131">AllJoyn Interfaces</span></span>__

<span data-ttu-id="da35a-132">Para hacerlo, AllJoyn dividir un archivo XML de introspección en diversas "interfaces" que representan diferentes agrupaciones lógicas de comportamiento y las funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="da35a-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="da35a-133">Interfaces de AllJoyn se denominan utilizando una convención de DNS inversa.</span><span class="sxs-lookup"><span data-stu-id="da35a-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="da35a-134">Por ejemplo, la interfaz de "Foo" creada por Contoso Ltd., que posee el dominio contoso.com, se escribiría como:</span><span class="sxs-lookup"><span data-stu-id="da35a-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="da35a-135">Un productor puede implementar cualquier número de interfaces, pero debe implementar todos los componentes de una interfaz que anuncie.</span><span class="sxs-lookup"><span data-stu-id="da35a-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="da35a-136">Con el fin de diferenciar y extender el comportamiento, AllJoyn admite crear interfaces nuevas con respecto a una jerarquía de interfaz existente; es decir, `com.contoso.Foo.Bar` define nuevas capacidades de las cosas en el `Foo.Bar` categoría, pero no tiene ninguna dependencia explícita en el `com.contoso.Foo` interfaz.</span><span class="sxs-lookup"><span data-stu-id="da35a-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="da35a-137">Por ejemplo, tenemos dos interfaces: `com.contoso.Sensor` y `com.contoso.Sensor.Humidity` : "Humedad" lógicamente cae por debajo de la categoría "Sensor".</span><span class="sxs-lookup"><span data-stu-id="da35a-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="da35a-138">Alguien desarrollar un productor de humedad podría optar por admitir solamente el `com.contoso.Sensor.Humdity` interfaz, pero también podría optar por admitir la `com.contoso.Sensor` interfaz.</span><span class="sxs-lookup"><span data-stu-id="da35a-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="da35a-139">En cualquier caso, si anuncia una interfaz, a continuación, los productores deben admitir todas sus funciones.</span><span class="sxs-lookup"><span data-stu-id="da35a-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="da35a-140">El `<description>` etiqueta se utiliza para describir interfaces, capacidades y los argumentos y se pueden localizar para varios idiomas.</span><span class="sxs-lookup"><span data-stu-id="da35a-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="da35a-141">El uso racional de la `<description>` etiqueta a la que hace que el código XML sea más comprensible y elimina la ambigüedad.</span><span class="sxs-lookup"><span data-stu-id="da35a-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="da35a-142">Una práctica estándar dicta el uso de la `org.alljoyn.Bus.Secure` anotación en una interfaz para habilitar la autenticación y seguridad.</span><span class="sxs-lookup"><span data-stu-id="da35a-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="da35a-143">Para una autenticación segura, utilice una clave precompartida (PSK) o un intercambio de claves de certificado (ECDSA).</span><span class="sxs-lookup"><span data-stu-id="da35a-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="da35a-144">En caso contrario, una autenticación de "null" se convierte en el comportamiento predeterminado.</span><span class="sxs-lookup"><span data-stu-id="da35a-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="da35a-145">**El mecanismo de autenticación real se produce en la implementación, no la declaración**.</span><span class="sxs-lookup"><span data-stu-id="da35a-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="da35a-146">Esta anotación habilita la seguridad pero no especifica el tipo de seguridad que utilizan o cómo se implementarán.</span><span class="sxs-lookup"><span data-stu-id="da35a-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

___<span data-ttu-id="da35a-147">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="da35a-147">Example</span></span>___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <annotation name="org.allJoyn.Bus.Secure" value="true" />
 
    <description language="en">
 
      Private interface for a Door the consumer owns. 
 
    </description>
 
  </interface>
 
</node>
```

<span data-ttu-id="da35a-148">En este ejemplo se muestra una interfaz expuesta por un dispositivo: `com.example.Door.PrivateDoor`.</span><span class="sxs-lookup"><span data-stu-id="da35a-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="da35a-149">En el ámbito de la interfaz, lo único que nos preocupa es si debe protegerse comunicación cuando se usa esa interfaz, no se está usando el tipo de mecanismo.</span><span class="sxs-lookup"><span data-stu-id="da35a-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

__<span data-ttu-id="da35a-150">Capacidades de interfaz</span><span class="sxs-lookup"><span data-stu-id="da35a-150">Interface Capabilities</span></span>__

<span data-ttu-id="da35a-151">Las interfaces declarar sus capacidades con tres miembros de interfaz: métodos, propiedades o señales.</span><span class="sxs-lookup"><span data-stu-id="da35a-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="da35a-152">Introspección XML también admite las anotaciones que describan una funcionalidad adicional o restricciones.</span><span class="sxs-lookup"><span data-stu-id="da35a-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="da35a-153">Estas funcionalidades con notación UpperCamelCase mientras lowerCamelCase con argumentos de notación.</span><span class="sxs-lookup"><span data-stu-id="da35a-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="da35a-154">Tipos de argumento</span><span class="sxs-lookup"><span data-stu-id="da35a-154">Argument Types</span></span>

<span data-ttu-id="da35a-155">Los miembros de interfaz enviar y reciben los argumentos que se indica con un código de tipo ASCII.</span><span class="sxs-lookup"><span data-stu-id="da35a-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="da35a-156">Según el tipo de miembro de interfaz, argumentos han se pueden enviar al productor del consumidor (dirección = "out") o desde el productor al consumidor (dirección = "in").</span><span class="sxs-lookup"><span data-stu-id="da35a-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="da35a-157">En la tabla siguiente proporciona una breve descripción de los tipos más comunes:</span><span class="sxs-lookup"><span data-stu-id="da35a-157">The following table provides a brief overview of commonly used types:</span></span>

> | *<span data-ttu-id="da35a-158">Nombre convencional</span><span class="sxs-lookup"><span data-stu-id="da35a-158">Conventional Name</span></span>* | *<span data-ttu-id="da35a-159">Tipo de código</span><span class="sxs-lookup"><span data-stu-id="da35a-159">Type-Code</span></span>* | *<span data-ttu-id="da35a-160">Usar</span><span class="sxs-lookup"><span data-stu-id="da35a-160">Use</span></span>* |
> |----------------- |---------| --- |
> |**<span data-ttu-id="da35a-161">BOOLEANO</span><span class="sxs-lookup"><span data-stu-id="da35a-161">BOOLEAN</span></span>** | <span data-ttu-id="da35a-162">b</span><span class="sxs-lookup"><span data-stu-id="da35a-162">b</span></span> | <span data-ttu-id="da35a-163">Representa TRUE (1) o FALSE (0).</span><span class="sxs-lookup"><span data-stu-id="da35a-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="da35a-164">Se usa para información binaria simple o Estados.</span><span class="sxs-lookup"><span data-stu-id="da35a-164">Used for simple binary information or states.</span></span> |
> |**<span data-ttu-id="da35a-165">BYTES</span><span class="sxs-lookup"><span data-stu-id="da35a-165">BYTE</span></span>** | <span data-ttu-id="da35a-166">y</span><span class="sxs-lookup"><span data-stu-id="da35a-166">y</span></span> | <span data-ttu-id="da35a-167">Valor entero comprendido entre 0 y 255.</span><span class="sxs-lookup"><span data-stu-id="da35a-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="da35a-168">Se utiliza cuando se trabaja con un número positivo pequeño.</span><span class="sxs-lookup"><span data-stu-id="da35a-168">Used when dealing with small positive numbers.</span></span> |
> |**<span data-ttu-id="da35a-169">UINT16</span><span class="sxs-lookup"><span data-stu-id="da35a-169">UINT16</span></span>** | <span data-ttu-id="da35a-170">q</span><span class="sxs-lookup"><span data-stu-id="da35a-170">q</span></span> | <span data-ttu-id="da35a-171">Valor entero entre 0 y 2 ^ 16-1</span><span class="sxs-lookup"><span data-stu-id="da35a-171">Integer value from 0 to 2^16 - 1</span></span> |
> |**<span data-ttu-id="da35a-172">UINT32</span><span class="sxs-lookup"><span data-stu-id="da35a-172">UINT32</span></span>** | <span data-ttu-id="da35a-173">u</span><span class="sxs-lookup"><span data-stu-id="da35a-173">u</span></span> | <span data-ttu-id="da35a-174">Valor entero entre 0 y 2 ^ 32-1</span><span class="sxs-lookup"><span data-stu-id="da35a-174">Integer value from 0 to 2^32 - 1</span></span> |
> |**<span data-ttu-id="da35a-175">UINT64</span><span class="sxs-lookup"><span data-stu-id="da35a-175">UINT64</span></span>** | <span data-ttu-id="da35a-176">tar</span><span class="sxs-lookup"><span data-stu-id="da35a-176">t</span></span> | <span data-ttu-id="da35a-177">Valor entero entre 0 y 2 ^ 64-1</span><span class="sxs-lookup"><span data-stu-id="da35a-177">Integer value from 0 to 2^64 - 1</span></span> |
> |**<span data-ttu-id="da35a-178">INT16</span><span class="sxs-lookup"><span data-stu-id="da35a-178">INT16</span></span>** | <span data-ttu-id="da35a-179">per?</span><span class="sxs-lookup"><span data-stu-id="da35a-179">n</span></span> | <span data-ttu-id="da35a-180">Valor entero entre –(2^15) y 2 ^ 15-1</span><span class="sxs-lookup"><span data-stu-id="da35a-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |**<span data-ttu-id="da35a-181">INT32</span><span class="sxs-lookup"><span data-stu-id="da35a-181">INT32</span></span>** | <span data-ttu-id="da35a-182">i</span><span class="sxs-lookup"><span data-stu-id="da35a-182">i</span></span> | <span data-ttu-id="da35a-183">Valor entero entre –(2^31) y 2 ^ 31-1</span><span class="sxs-lookup"><span data-stu-id="da35a-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |**<span data-ttu-id="da35a-184">INT64</span><span class="sxs-lookup"><span data-stu-id="da35a-184">INT64</span></span>** | <span data-ttu-id="da35a-185">x</span><span class="sxs-lookup"><span data-stu-id="da35a-185">x</span></span> | <span data-ttu-id="da35a-186">Valor entero entre –(2^63) y 2 ^ 63-1</span><span class="sxs-lookup"><span data-stu-id="da35a-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |**<span data-ttu-id="da35a-187">DOBLE</span><span class="sxs-lookup"><span data-stu-id="da35a-187">DOUBLE</span></span>** | <span data-ttu-id="da35a-188">d</span><span class="sxs-lookup"><span data-stu-id="da35a-188">d</span></span> | <span data-ttu-id="da35a-189">Precisión de números decimales de –(2^127) a 2 ^ 127-1</span><span class="sxs-lookup"><span data-stu-id="da35a-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |**<span data-ttu-id="da35a-190">CADENA</span><span class="sxs-lookup"><span data-stu-id="da35a-190">STRING</span></span>** | <span data-ttu-id="da35a-191">s</span><span class="sxs-lookup"><span data-stu-id="da35a-191">s</span></span> | <span data-ttu-id="da35a-192">Cadena UTF-8</span><span class="sxs-lookup"><span data-stu-id="da35a-192">UTF-8 string</span></span> |
 
<span data-ttu-id="da35a-193">Para obtener una descripción más exhaustiva de todos los tipos admitidos, consulte [aquí](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span><span class="sxs-lookup"><span data-stu-id="da35a-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="da35a-194">Cuando se redactó este documento, use las unidades que sea posible y denotar claramente unidades deseadas.</span><span class="sxs-lookup"><span data-stu-id="da35a-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="da35a-195">Cuando sea posible, elija el tipo de código más restrictivo para su escenario; Por ejemplo, si va a representar la edad de una persona en años, a continuación, utilizar BYTE, no UINT16 o INT16, ya que nadie será una negativo edad o más de 255 años de antigüedad.</span><span class="sxs-lookup"><span data-stu-id="da35a-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="da35a-196">Siga siempre la versión más reciente [AllJoyn interfaz Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) directrices.</span><span class="sxs-lookup"><span data-stu-id="da35a-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="da35a-197">La tabla siguiente resume las unidades comunes:</span><span class="sxs-lookup"><span data-stu-id="da35a-197">The following table summarizes common units:</span></span>


> |*<span data-ttu-id="da35a-198">Cantidad</span><span class="sxs-lookup"><span data-stu-id="da35a-198">Quantity</span></span>* | *<span data-ttu-id="da35a-199">Unidad</span><span class="sxs-lookup"><span data-stu-id="da35a-199">Unit</span></span>*|
> |-------- | ---- |
> |**<span data-ttu-id="da35a-200">Tiempo absoluto (fecha y hora)</span><span class="sxs-lookup"><span data-stu-id="da35a-200">Absolute time (date & time)</span></span>** | <span data-ttu-id="da35a-201">Segundos transcurridos desde la época de UNIX (00: 00:00 en 1 de enero de 1970)</span><span class="sxs-lookup"><span data-stu-id="da35a-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |**<span data-ttu-id="da35a-202">Hora del día</span><span class="sxs-lookup"><span data-stu-id="da35a-202">Time of Day</span></span>** | <span data-ttu-id="da35a-203">Segundos transcurridos desde medianoche</span><span class="sxs-lookup"><span data-stu-id="da35a-203">Seconds since midnight</span></span> |
> |**<span data-ttu-id="da35a-204">Intervalo de tiempo</span><span class="sxs-lookup"><span data-stu-id="da35a-204">Time interval</span></span>** | <span data-ttu-id="da35a-205">Segundos</span><span class="sxs-lookup"><span data-stu-id="da35a-205">Seconds</span></span> |
> |**<span data-ttu-id="da35a-206">Ancho de banda</span><span class="sxs-lookup"><span data-stu-id="da35a-206">Bandwidth</span></span>** | <span data-ttu-id="da35a-207">Bits por segundo</span><span class="sxs-lookup"><span data-stu-id="da35a-207">Bits per second</span></span> |
> |**<span data-ttu-id="da35a-208">Tamaño de los datos</span><span class="sxs-lookup"><span data-stu-id="da35a-208">Data size</span></span>** | <span data-ttu-id="da35a-209">Bytes</span><span class="sxs-lookup"><span data-stu-id="da35a-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="da35a-210">Métodos</span><span class="sxs-lookup"><span data-stu-id="da35a-210">Methods</span></span>

<span data-ttu-id="da35a-211">Los consumidores de llamar a métodos para modificar el estado de un productor y sus nombres deben empezar con un verbo, ya que representan las solicitudes para el productor realizar una acción.</span><span class="sxs-lookup"><span data-stu-id="da35a-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="da35a-212">Los métodos pueden tener de entrada y salida argumentos; en el caso de que no hay que enviar ningún mensaje de retorno, se aplica la anotación "org.freedesktop.DBus.Method.NoReply".</span><span class="sxs-lookup"><span data-stu-id="da35a-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="da35a-213">Sin embargo, métodos de AllJoyn normalmente devuelven un SuccessResult o un FailureResult, ofreciendo a comentarios de los consumidores acerca de la llamada al método.</span><span class="sxs-lookup"><span data-stu-id="da35a-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="da35a-214">El tipo de los argumentos debe cumplir el [D Bus especificación](http://dbus.freedesktop.org/doc/dbus-specification.html).</span><span class="sxs-lookup"><span data-stu-id="da35a-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

___<span data-ttu-id="da35a-215">Ejemplo (excepto la información de la interfaz para su comodidad)</span><span class="sxs-lookup"><span data-stu-id="da35a-215">Example (excluding interface information for convenience)</span></span>___

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!-- Method showing arguments with only directions in -->
 
    <method name="SetPasscode">
 
      <description language="en">
 
        Allows owner of the door to change the code needed to unlock it.
 
      </description>
 
      <argument name="currentPasscode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="newPasscode" type="u" direction="in">
 
        <description language="en">
 
          New code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!-- Method showing both arguments in and out -->
 
    <method name="UnlockDoor">
 
      <description language="en">
 
        Allows guests with the code to unlock the door.
 
      </description>
 
      <argument name="passcode" type="u" direction="in">
 
        <description language="en">
 
          Current code (00000000 to 99999999) needed to unlock door
 
        </description>
 
      </argument>
 
      <argument name="welcomeMessage" type="s" direction="out">
 
        <description language="en">
 
          Message from the owner of the door.
 
        </description>
 
      </argument>
 
    </method>
 
  </interface>
 
</node>
```

*<span data-ttu-id="da35a-216">Nota: En la mayoría de los casos, las propiedades deben usarse en lugar de métodos para tener acceso a estado del productor (por ejemplo, usar una propiedad de Color en lugar de un método GetColor).</span><span class="sxs-lookup"><span data-stu-id="da35a-216">Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).</span></span>*

### <a name="properties"></a><span data-ttu-id="da35a-217">Propiedades</span><span class="sxs-lookup"><span data-stu-id="da35a-217">Properties</span></span>

<span data-ttu-id="da35a-218">Propiedades principalmente permiten el acceso al estado del productor.</span><span class="sxs-lookup"><span data-stu-id="da35a-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="da35a-219">Aunque técnicamente, las propiedades tienen valores de acceso de "lectura", "readwrite" o "escritura", funcionalidad de modificación de estado generalmente pertenece a los métodos, por lo tanto, los desarrolladores deben esforzarse por mantener propiedades como "lectura" y use "readwrite" solo cuando el estado representado por esa propiedad es independiente de todas las demás propiedades.</span><span class="sxs-lookup"><span data-stu-id="da35a-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="da35a-220">Las propiedades nunca deben ser simplemente "escritura": modificar el estado sin observación es la función de los métodos.</span><span class="sxs-lookup"><span data-stu-id="da35a-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="da35a-221">Se deben anotar propiedades a los consumidores alertas cuando cambian sus valores (si lo desea, las propiedades pueden heredar esta anotación de su interfaz primaria).</span><span class="sxs-lookup"><span data-stu-id="da35a-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="da35a-222">La anotación `org.freedesktop.DBus.Property.EmitsChangedSignal` puede tener cuatro valores:</span><span class="sxs-lookup"><span data-stu-id="da35a-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="da35a-223">"true": cuando se cambia la propiedad, el productor emitirá una señal que indica la propiedad que ha cambiado y el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="da35a-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="da35a-224">Se utiliza en las propiedades que se utilizan con frecuencia y que requieren una supervisión activa, como "LockState" para una puerta.</span><span class="sxs-lookup"><span data-stu-id="da35a-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="da35a-225">"invalida": cuando cambia la propiedad, el productor emitirá una señal que indica la propiedad que ha cambiado, pero no el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="da35a-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="da35a-226">Se utiliza en las propiedades que no requieren supervisión pesada (por ejemplo, el "WashMode" un secador de ropas) o representan una gran cantidad de datos, como un contenedor.</span><span class="sxs-lookup"><span data-stu-id="da35a-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="da35a-227">"false": cuando se cambia la propiedad, el productor no emite ninguna señal.</span><span class="sxs-lookup"><span data-stu-id="da35a-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="da35a-228">Se utiliza en las propiedades que actualizan rápidamente, por ejemplo, una propiedad "TransitCounter" en un torniquete metro seguimiento de personas que realiza el metro.</span><span class="sxs-lookup"><span data-stu-id="da35a-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="da35a-229">Si no se especifica, las propiedades de AllJoyn Úselo como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="da35a-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="da35a-230">"const": la propiedad nunca cambiará valor y nunca emitir una señal modificada.</span><span class="sxs-lookup"><span data-stu-id="da35a-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="da35a-231">Se trata de introducidas en la versión 16.04 AllJoyn; hasta entonces, utilice "true".</span><span class="sxs-lookup"><span data-stu-id="da35a-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

___<span data-ttu-id="da35a-232">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="da35a-232">Example</span></span>___

<span data-ttu-id="da35a-233">Ampliar el ejemplo anterior, hemos modificado el código XML para incluir propiedades (excepto los métodos por razones de brevedad).</span><span class="sxs-lookup"><span data-stu-id="da35a-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Read property that sends a signal when the value changes -->
 
    <property name="IsLocked" type="b" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door may freely lock and unlock the door.
 
      </description>
 
    </property>  
 
  </interface>
 
  <interface name="com.example.Door.PublicDoor">
 
    <!—- Read-only property that never sends a signal and never changes -->
 
    <property name="Owner" type="s" access="read">
 
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
 
      <description language="en">
 
        Owner of the door is public knowledge.
 
      </description>
 
    </property>
 
  </interface>
 
</node>
```

### <a name="signals"></a><span data-ttu-id="da35a-234">Señales</span><span class="sxs-lookup"><span data-stu-id="da35a-234">Signals</span></span>

<span data-ttu-id="da35a-235">Señales de uso para informar a los consumidores de un evento que no puede determinar consultando el productor.</span><span class="sxs-lookup"><span data-stu-id="da35a-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="da35a-236">Apertura de una puerta se podría transmitir a través de propiedad de un productor DoorOpen con una anotación EmitsChangedProperty "true".</span><span class="sxs-lookup"><span data-stu-id="da35a-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="da35a-237">Alguien pasa a través de la puerta, sin embargo, no puede derivar de los cambios de propiedades, por lo que esto provocaría una señal de buena independiente.</span><span class="sxs-lookup"><span data-stu-id="da35a-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="da35a-238">Nos referimos a estos tipos de eventos como "sin estado".</span><span class="sxs-lookup"><span data-stu-id="da35a-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="da35a-239">Puesto que las señales son unidireccionales del productor al consumidor, solo puede contener "argumentos out".</span><span class="sxs-lookup"><span data-stu-id="da35a-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

___<span data-ttu-id="da35a-240">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="da35a-240">Examples</span></span>___ 

<span data-ttu-id="da35a-241">(excepto los métodos y propiedades para su comodidad):</span><span class="sxs-lookup"><span data-stu-id="da35a-241">(excluding methods and properties for convenience):</span></span>

``` xml
<node>
 
  <interface name="com.example.Door.PrivateDoor">
 
    <!—- Signals may contain arguments about non-state information -->
 
    <signal name="ThresholdCrossed" sessioncast="true">
 
      <description>
 
        Signal to notify owner whenever anyone passes through the door.
 
      </description>
 
      <argument name="crossedInward" type="b" direction="out">
 
        If true, someone entered; if false, someone left.
 
      </argument>
 
    </signal>
 
  </interface>
 
</node>
```

<span data-ttu-id="da35a-242">Normalmente puesto que las señales tienen este tipo de un ámbito restringido, pocos aparecen en el XML del productor.</span><span class="sxs-lookup"><span data-stu-id="da35a-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="da35a-243">Contenedores</span><span class="sxs-lookup"><span data-stu-id="da35a-243">Containers</span></span>

<span data-ttu-id="da35a-244">No combine varios argumentos en una colección compleja como una cadena JSON serializada.</span><span class="sxs-lookup"><span data-stu-id="da35a-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="da35a-245">La especificación de Bus de D hace prestaciones para los contenedores de datos, STRUCT, matriz, variante y DICT_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="da35a-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="da35a-246">Úselas para pasar argumentos que requieren más de los tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="da35a-246">Use these to pass arguments that require more than basic types.</span></span>

___<span data-ttu-id="da35a-247">VARIANT</span><span class="sxs-lookup"><span data-stu-id="da35a-247">VARIANT</span></span>___

<span data-ttu-id="da35a-248">Las variantes se denotan mediante el tipo "v" y puede contener ninguno [único de tipo completo](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span><span class="sxs-lookup"><span data-stu-id="da35a-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="da35a-249">Sin embargo, las variantes deben evitarse siempre que sea posible porque agregan ambigüedad definiciones XML.</span><span class="sxs-lookup"><span data-stu-id="da35a-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

___<span data-ttu-id="da35a-250">STRUCT</span><span class="sxs-lookup"><span data-stu-id="da35a-250">STRUCT</span></span>___

<span data-ttu-id="da35a-251">Uso de STRUCTs "(" y ")" para denotar el principio y al final de una estructura de datos: un único tipo completo.</span><span class="sxs-lookup"><span data-stu-id="da35a-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="da35a-252">Estas estructuras de datos pueden estar anidadas.</span><span class="sxs-lookup"><span data-stu-id="da35a-252">These data structures may be nested.</span></span>

<span data-ttu-id="da35a-253">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="da35a-253">Examples:</span></span>

<span data-ttu-id="da35a-254">Un tipo de "(iii)" denota una estructura de tres enteros; "(i(ii))" denota una estructura de un entero y una estructura de dos enteros, que es distinta del tipo "((ii))".</span><span class="sxs-lookup"><span data-stu-id="da35a-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

___<span data-ttu-id="da35a-255">MATRIZ</span><span class="sxs-lookup"><span data-stu-id="da35a-255">ARRAY</span></span>___

<span data-ttu-id="da35a-256">Las matrices de usar el código de tipo "a" y debe ir seguido por un único tipo completo.</span><span class="sxs-lookup"><span data-stu-id="da35a-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="da35a-257">Las matrices no tienen longitudes de conjunto, por lo que son similares a una estructura de datos de lista.</span><span class="sxs-lookup"><span data-stu-id="da35a-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="da35a-258">Matrices representan un único tipo completo.</span><span class="sxs-lookup"><span data-stu-id="da35a-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="da35a-259">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="da35a-259">Examples:</span></span>

<span data-ttu-id="da35a-260">Un tipo de "ai" representa una matriz de enteros, mientras que "aai" representa una matriz de una matriz de enteros.</span><span class="sxs-lookup"><span data-stu-id="da35a-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="da35a-261">Una matriz se puede utilizar con las estructuras también: "a(ii)".</span><span class="sxs-lookup"><span data-stu-id="da35a-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

___<span data-ttu-id="da35a-262">DICT_ENTRY</span><span class="sxs-lookup"><span data-stu-id="da35a-262">DICT_ENTRY</span></span>___

<span data-ttu-id="da35a-263">Función DICT_ENTRYs similar a un STRUCT con mayores restricciones: usan "{" y "}", solo se puede producir como un tipo de elemento de matriz y debe tener exactamente dos tipos entre las llaves completos.</span><span class="sxs-lookup"><span data-stu-id="da35a-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="da35a-264">El primer tipo representa una "clave" en una estructura de datos de diccionario y la segunda representa el "valor" par de clave-valor del diccionario.</span><span class="sxs-lookup"><span data-stu-id="da35a-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="da35a-265">Una clave debe ser única en un diccionario.</span><span class="sxs-lookup"><span data-stu-id="da35a-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="da35a-266">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="da35a-266">Example:</span></span>

<span data-ttu-id="da35a-267">Un tipo de una {sy} denota un diccionario de claves de cadena y valores de tipo byte.</span><span class="sxs-lookup"><span data-stu-id="da35a-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="da35a-268">Usar</span><span class="sxs-lookup"><span data-stu-id="da35a-268">Use</span></span> <description> <span data-ttu-id="da35a-269">etiquetas para describir los valores y claves válidas.</span><span class="sxs-lookup"><span data-stu-id="da35a-269">tags to describe valid keys and values.</span></span> 

__<span data-ttu-id="da35a-270">Final ejemplo y ajxmlcop</span><span class="sxs-lookup"><span data-stu-id="da35a-270">Final Example and ajxmlcop</span></span>__

<span data-ttu-id="da35a-271">El concepto de contenedores mejora las capacidades de XML existente, además de proporcionar una vía para nuevos miembros de interfaz útil.</span><span class="sxs-lookup"><span data-stu-id="da35a-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="da35a-272">Cuando haya terminado de escribir el código XML, utilice la herramienta de línea de comandos ajxmlcop.exe (disponible en el AllJoyn [git origen](https://git.allseenalliance.org/cgit/core/alljoyn.git/) o [aquí](https://github.com/MS-brock/AllJoynToasterDemo)) para validar el XML.</span><span class="sxs-lookup"><span data-stu-id="da35a-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="da35a-273">Use ajxmlcop.exe con el archivo XML como el argumento de entrada (por ejemplo, `C:\>ajxmlcop.exe doorExample.xml`) para recibir el error, advertencia y mensajes informativos.</span><span class="sxs-lookup"><span data-stu-id="da35a-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="da35a-274">Esta herramienta proporciona valiosos comentarios sobre la estructura y el formato de XML y el uso de las señales, propiedades y métodos.</span><span class="sxs-lookup"><span data-stu-id="da35a-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

``` xml
<node>
  <interface name="com.example.Door.PrivateDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door.  Private interface that can only be used by the producer’s owner.
    </description>
    <method name="SetPasscode">
      <description language="en">
        Change the code needed to unlock the door.
      </description>
      <argument name="currentPasscode" type="u" direction="in">
        <description language="en">
          Current code needed to unlock door
        </description>
      </argument>
      <argument name="newPasscode" type="u" direction="in">
        <description language="en">
          New code needed to unlock door
        </description>
      </argument>
    </method>
    <method name="UpdateGuestRatings">
      <description language="en">
        Update the list of guests and their personality scores.
      </description>
      <annotation name="org.freedesktop.DBus.Method.NoReply" value="true" />
      <argument name="guestName" type="s">
        <description language="en">
          The name of the guest being entered.
        </description>
      </argument>
      <argument name="qualityScores" type="a{sy}">
        <description language="en">
          DICTIONARY[Key:(string)guestQuality, Value:(byte)score]
          KEYs: "Friendly", "Social", "Punctual" 
          VALUEs: [0-10]
          The qualities of the guest, scored appropriately. If the guestName matches an existing entry, this updates that entry.
        </description>
      </argument>
    </method>
    <method name="SetDoorSecurity">
      <description language="en">
        Close and lock the door or unlock the door.
      </description>
      <argument name="secured" type="b" direction="in">
        <description language="en">
          If TRUE, shut and lock the door.
          If FALSE, unlock the door.
        </description>
      </argument>
    </method>
    <property name="MessageBook" type="a(ss)" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="invalidates"/>
      <description language="en">
        (struct)[(string)guestName, (string)message]
        A list of names of people and the messages they have left.
      </description>
    </property>
    <property name="GuestRatings" type="a(sa{sy})" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        ARRAY[(string)guestName, DICTIONARY(Key:(string)guestQuality, Value:(byte)score)]
        KEYs: "Friendly", "Social", "Punctual"
        VALUEs: [0-10]
        A collection of the previous guests and their scored qualities.
      </description>
    </property>
    <property name="IsLocked" type="b" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="true"/>
      <description language="en">
        Owner of the door may freely lock and unlock the door.
      </description>
    </property>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <signal name="ThresholdCrossed" sessioncast="true">
      <description>
        Signal to notify owner whenever anyone passes through the door.
      </description>
      <argument name="crossedInwards" type="b" direction="out">
        If true, someone entered; if false, someone left.
      </argument>    
    </signal>
  </interface>
  <interface name="com.example.Door.PublicDoor">
    <annotation name="org.alljoyn.Bus.Secure" value="true" />
    <description language="en">
      Examples for an AllJoyn-enabled door. Public interface that can be used by any consumer.
    </description>
    <method name="UnlockDoor">
      <description language="en">
        Allows guests with the code to unlock the door.
      </description>
      <argument name="passcode" type="u" direction="in">
        <description language="en">
          Current code (00000000 to 99999999) needed to unlock door
        </description>
      </argument>
      <argument name="welcomeMessage" type="s" direction="out">
        <description language="en">
          Message from the owner of the door.
        </description>
      </argument>
    </method>
    <method name="LeaveMessage">
      <description language="en">
        Leave a message for the owner of the door.
      </description>
      <argument name="guestName" type="s" direction="in">
        <description language="en">
          Name of guest leaving a message
        </description>
      </argument>
      <argument name="message" type="s" direction="in">
        <description language="en">
          Message left for owner of the door
        </description>
      </argument>
    </method>
    <method name="AnnouncePresence">
      <description language="en">
        Send a message to the owner of the door.
      </description>
      <argument name="announcingGuest" type="s" direction="in">
        <description language="en">
          Name of the guest announcing their presence.
        </description>
      </argument>
      <argument name="forcefulnessOfAnnouncment" type="y" direction="in">
        <description language="en">
          Degree to which the guest attempts to make their presence known, on bounds [1:10], where 1 is softly and 10 is aggressively.
        </description>
      </argument>
    </method>
    <property name="Version" type="q" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Version of the implementation being used.
      </description>
    </property>
    <property name="Owner" type="s" access="read">
      <annotation name="org.freedesktop.DBus.Property.EmitsChangedSignal" value="false"/>
      <description language="en">
        Owner of the door is public knowledge.
      </description>
    </property>
  </interface>
</node>
```

