---
title: Productores de AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo crear un productor de AllJoyn aprendiendo y creando XML introspección y sus distintas características.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 014f6f4b4c33f4dbd85963bbddccb948322ccca9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167409"
---
> [!NOTE]
> <span data-ttu-id="cd574-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="cd574-104">You are viewing archived documentation.</span></span> <span data-ttu-id="cd574-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="cd574-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="cd574-106">Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.</span><span class="sxs-lookup"><span data-stu-id="cd574-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-producers"></a><span data-ttu-id="cd574-107">Productores de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="cd574-107">AllJoyn Producers</span></span>

<span data-ttu-id="cd574-108">AllJoyn, creado por [AllSeen Alliance](https://allseenalliance.org/), proporciona un marco de trabajo excelente para la creación de aplicaciones y dispositivos conectados en una red proximal, y Windows proporciona la mejor experiencia para usar AllJoyn con la extensión [Alljoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd574-108">AllJoyn, created by the [AllSeen Alliance](https://allseenalliance.org/), provides a great framework for making connected devices and apps on a proximal network, and Windows provides the best experience for using AllJoyn with the [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286) extension for Visual Studio.</span></span>  <span data-ttu-id="cd574-109">Aunque nuestras herramientas de Excel en la creación de aplicaciones para productores y consumidores, el inicio de un nuevo dispositivo de AllJoyn desde cero puede resultar bastante confuso.</span><span class="sxs-lookup"><span data-stu-id="cd574-109">While our tools excel at creating apps for producers and consumers, starting a new AllJoyn device from scratch can be quite confusing.</span></span>

<span data-ttu-id="cd574-110">Si tiene una idea para el siguiente dispositivo conectado o un nuevo juguete con el que Tinker y explore, es posible que no pueda usar una de las interfaces estándar ofrecidas por AllSeen Alliance.</span><span class="sxs-lookup"><span data-stu-id="cd574-110">If you have an idea for the next great connected device or a new toy with which to tinker and explore, you may not be able to use one of the standard interfaces offered by the AllSeen Alliance.</span></span>  <span data-ttu-id="cd574-111">Si es así, debe crear un productor AllJoyn nuevo.</span><span class="sxs-lookup"><span data-stu-id="cd574-111">If so, then you need to create a brand new AllJoyn producer.</span></span>

<span data-ttu-id="cd574-112">Un desarrollador que desea hacer que un nuevo productor de AllJoyn tenga que crear su propio XML de introspección, pero crear introspección XML requiere conocimientos sobre la materia y tiene una curva de aprendizaje significativa para los nuevos desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="cd574-112">A developer wanting to make a new AllJoyn producer needs to author their own Introspection XML, but creating Introspection XML requires subject matter expertise and has a significant learning curve for new developers.</span></span>  <span data-ttu-id="cd574-113">Este blog reducirá la curva de aprendizaje al desglosar los distintos componentes de introspección XML, describir el propósito y las restricciones de cada componente, y proporcionar buenos ejemplos en términos aproximables.</span><span class="sxs-lookup"><span data-stu-id="cd574-113">This blogpost will lower the learning curve by breaking down the various components of Introspection XML, describing the purpose and restrictions of each component, and providing good examples in approachable terms.</span></span>

## <a name="existing-documentation"></a><span data-ttu-id="cd574-114">Documentación existente</span><span class="sxs-lookup"><span data-stu-id="cd574-114">Existing documentation</span></span>

<span data-ttu-id="cd574-115">Un examen de cursores de los siguientes recursos combinados con este blog debe acelerar la comprensión del desarrollador de introspección XML:</span><span class="sxs-lookup"><span data-stu-id="cd574-115">A cursory examination of the following resources combined with this blogpost should accelerate developer understanding of Introspection XML:</span></span>

1. <span data-ttu-id="cd574-116">[Guía de la API de eventos y acciones de alljoyn](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) : detalles e información general sobre la implementación de alljoyn.</span><span class="sxs-lookup"><span data-stu-id="cd574-116">[AllJoyn Events and Actions API Guide](https://allseenalliance.org/developers/develop/api-guide/events-and-actions) – AllJoyn implementation details and overview.</span></span>
2. <span data-ttu-id="cd574-117">[Directrices de diseño del panel de revisión de la interfaz alljoyn](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) : estructura y especificación rigurosas para ALLJOYN introspección XML.</span><span class="sxs-lookup"><span data-stu-id="cd574-117">[AllJoyn Interface Review Board Design Guidelines](https://wiki.allseenalliance.org/irb/interface_design_guidelines_1.0) - stringent structuring and specification for AllJoyn Introspection XML.</span></span>
3. <span data-ttu-id="cd574-118">[Especificación de bus D](http://dbus.freedesktop.org/doc/dbus-specification.html) : AllJoyn basa introspección XML en esta especificación.</span><span class="sxs-lookup"><span data-stu-id="cd574-118">[D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html) – AllJoyn bases Introspection XML on this specification.</span></span>

<span data-ttu-id="cd574-119">__Los tres tipos de XML de introspección__</span><span class="sxs-lookup"><span data-stu-id="cd574-119">__The three types of Introspection XML__</span></span>

<span data-ttu-id="cd574-120">Al igual que en la documentación de AllJoyn, encontrará tres tipos de introspección XML:</span><span class="sxs-lookup"><span data-stu-id="cd574-120">As you peruse AllJoyn documentation, you will find three types of Introspection XML:</span></span>

1. <span data-ttu-id="cd574-121">XML de especificación de bus D: baja sobrecarga, comunicación entre procesos con un formato de tipo para la representación de datos.</span><span class="sxs-lookup"><span data-stu-id="cd574-121">D-Bus Specification XML: low-overhead, interprocess communication with a type format for data representation.</span></span>
2. <span data-ttu-id="cd574-122">AllJoyn introspección XML: extiende el XML de especificación de bus D con etiquetas XML para almacenar descripciones de texto y aplicar también principios de AllJoyn a la especificación.</span><span class="sxs-lookup"><span data-stu-id="cd574-122">AllJoyn Introspection XML: extends D-Bus Specification XML with XML tags for holding textual descriptions while also applying AllJoyn principles to the specification.</span></span>
3. <span data-ttu-id="cd574-123">Introspección de AllJoyn extendido XML: evolución del XML clásico de introspección introducción de tipos con nombre para estructuras y diccionarios.</span><span class="sxs-lookup"><span data-stu-id="cd574-123">Extended AllJoyn Introspection XML: evolution of classic Introspection XML introducing named types for structures and dictionaries.</span></span>

<span data-ttu-id="cd574-124">AllJoyn Studio admite actualmente la especificación de bus D XML y AllJoyn introspección XML; este blog determinará cómo crear y formar el XML introspección de AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="cd574-124">AllJoyn Studio currently supports D-Bus Specification XML and AllJoyn Introspection XML; this blog will dictate how to create and form AllJoyn Introspection XML.</span></span>  <span data-ttu-id="cd574-125">El panel de revisión de interfaz (IRB) de AllSeen Alliance usa la nueva introspección de AllJoyn extendida como formato para los envíos formales para las revisiones de estandarización, pero está trabajando en un formato XML Unificado de introspección en un futuro próximo.</span><span class="sxs-lookup"><span data-stu-id="cd574-125">The AllSeen Alliance's Interface Review Board (IRB) uses the new Extended AllJoyn Introspection as the format for formal submissions for standardization reviews but is working on a unified introspection XML format for the near future.</span></span>

## <a name="introspection-high-level-overview"></a><span data-ttu-id="cd574-126">Información general de alto nivel de introspección</span><span class="sxs-lookup"><span data-stu-id="cd574-126">Introspection High Level Overview</span></span>

<span data-ttu-id="cd574-127">Cada productor de AllJoyn anuncia públicamente un XML introspección que muestra la funcionalidad admitida por el productor, tal como se describe a través de señales, propiedades y métodos.</span><span class="sxs-lookup"><span data-stu-id="cd574-127">Every AllJoyn producer publicly advertises an Introspection XML that surfaces the producer's supported functionality – interfaces as described via signals, properties and methods.</span></span>  <span data-ttu-id="cd574-128">Las soluciones de generación de código, como la de la extensión AllJoyn Studio, se basan en el XML de introspección para crear el código necesario para acelerar el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="cd574-128">Code Generation solutions, like the one in the AllJoyn Studio extension, rely on Introspection XML to create the necessary code to accelerate development.</span></span>  <span data-ttu-id="cd574-129">El XML introspección describe la funcionalidad de un productor en una manera no ambigua y legible, de modo que dos fabricantes diferentes pueden utilizar el XML para implementar un productor con la misma funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="cd574-129">Introspection XML describes the functionality of a producer in a non-ambiguous, human-readable way such that two different manufacturers can use the XML to implement a producer with the same functionality.</span></span>  <span data-ttu-id="cd574-130">Con el mismo token, los desarrolladores sin ningún conocimiento previo de un productor de AllJoyn deberían ser capaces de desarrollar en ese productor en función de su XML.</span><span class="sxs-lookup"><span data-stu-id="cd574-130">By the same token, developers with no previous knowledge of an AllJoyn producer should be able to develop against that producer based on its XML.</span></span>

<span data-ttu-id="cd574-131">__Interfaces AllJoyn__</span><span class="sxs-lookup"><span data-stu-id="cd574-131">__AllJoyn Interfaces__</span></span>

<span data-ttu-id="cd574-132">AllJoyn consigue esto dividiendo un XML introspección en varias "interfaces" que representan diferentes agrupaciones lógicas de comportamiento y capacidades.</span><span class="sxs-lookup"><span data-stu-id="cd574-132">AllJoyn accomplishes this by breaking an Introspection XML into various "interfaces" that represent different logical groupings of behavior and capabilities.</span></span>  <span data-ttu-id="cd574-133">Las interfaces AllJoyn se denominan mediante una Convención de DNS inverso.</span><span class="sxs-lookup"><span data-stu-id="cd574-133">AllJoyn interfaces are named using a reverse-DNS convention.</span></span> <span data-ttu-id="cd574-134">Por ejemplo, la interfaz "foo" de la interfaz creada por contoso Ltd., que posee el dominio contoso.com, se escribiría como:</span><span class="sxs-lookup"><span data-stu-id="cd574-134">For example, the interface "Foo" interface created by Contoso Ltd., which owns the contoso.com domain, would be written as:</span></span>

    <interface name="com.contoso.Foo">

<span data-ttu-id="cd574-135">Un productor puede implementar cualquier número de interfaces, pero debe implementar todos los componentes de una interfaz que anuncien.</span><span class="sxs-lookup"><span data-stu-id="cd574-135">A producer may implement any number of interfaces, but must implement every component of an interface that they advertise.</span></span>  <span data-ttu-id="cd574-136">Con el fin de diferenciar y extender los comportamientos, AllJoyn admite la creación de nuevas interfaces con respecto a una jerarquía de interfaz existente. es decir, `Foo.Bar` `com.contoso.Foo` define nuevas funcionalidades para las cosas en la categoría, pero no tiene ninguna dependencia explícita en la interfaz. `com.contoso.Foo.Bar`</span><span class="sxs-lookup"><span data-stu-id="cd574-136">In order to differentiate and extend behaviors, AllJoyn supports creating new interfaces with respect to an existing interface hierarchy; i.e. `com.contoso.Foo.Bar` defines new capabilities for things under the `Foo.Bar` category but doesn't have any explicit dependencies on the `com.contoso.Foo` interface.</span></span> 

<span data-ttu-id="cd574-137">Por ejemplo, tenemos dos interfaces: `com.contoso.Sensor` y `com.contoso.Sensor.Humidity` – "humedad" se encuentra lógicamente en la categoría "sensor".</span><span class="sxs-lookup"><span data-stu-id="cd574-137">For an example, we have two interfaces: `com.contoso.Sensor` and `com.contoso.Sensor.Humidity` – "Humidity" logically falls under the "Sensor" category.</span></span>  <span data-ttu-id="cd574-138">Alguien que desarrolle un productor de humedad podría optar `com.contoso.Sensor.Humdity` por admitir solo la interfaz, pero también podría optar por admitir la `com.contoso.Sensor` interfaz.</span><span class="sxs-lookup"><span data-stu-id="cd574-138">Someone developing a Humidity producer could choose to support just the `com.contoso.Sensor.Humdity` interface, but they could also choose to support the `com.contoso.Sensor` interface.</span></span>  <span data-ttu-id="cd574-139">Independientemente de si anuncian una interfaz, los productores deben admitir todas sus funciones.</span><span class="sxs-lookup"><span data-stu-id="cd574-139">Regardless, if they advertise an interface, then producers must support all of its functions.</span></span>

<span data-ttu-id="cd574-140">La `<description>` etiqueta se usa para describir interfaces, funcionalidades y argumentos, y se puede localizar para varios idiomas.</span><span class="sxs-lookup"><span data-stu-id="cd574-140">The `<description>` tag is used to describe interfaces, capabilities and arguments, and can be localized for various languages.</span></span>  <span data-ttu-id="cd574-141">El uso liberal de `<description>` la etiqueta hace que el código XML sea más comprensible y elimine la ambigüedad.</span><span class="sxs-lookup"><span data-stu-id="cd574-141">Liberal use of the `<description>` tag makes the XML more understandable and removes ambiguity.</span></span>

<span data-ttu-id="cd574-142">La práctica estándar dicta el uso de la `org.alljoyn.Bus.Secure` anotación en una interfaz para habilitar la seguridad y la autenticación.</span><span class="sxs-lookup"><span data-stu-id="cd574-142">Standard practice dictates the use of the `org.alljoyn.Bus.Secure` annotation on an interface to enable security and authentication.</span></span>  <span data-ttu-id="cd574-143">Para una autenticación segura, use una clave previamente compartida (PSK) o un intercambio de claves de certificado (ECDSA).</span><span class="sxs-lookup"><span data-stu-id="cd574-143">For strong authentication, use a pre-shared key (PSK) or a certificate key exchange (ECDSA).</span></span>  <span data-ttu-id="cd574-144">De lo contrario, una autenticación "null" se convierte en el comportamiento predeterminado.</span><span class="sxs-lookup"><span data-stu-id="cd574-144">Otherwise, a "null" authentication becomes the default behavior.</span></span>  <span data-ttu-id="cd574-145">**El mecanismo de autenticación real se produce en la implementación, no en la declaración**.</span><span class="sxs-lookup"><span data-stu-id="cd574-145">**The actual authentication mechanism happens in implementation, not the declaration**.</span></span> <span data-ttu-id="cd574-146">Esta anotación habilita la seguridad pero no especifica el tipo de seguridad utilizado o cómo se implementará.</span><span class="sxs-lookup"><span data-stu-id="cd574-146">This annotation enables security but does not specify the type of security used or how it will be implemented.</span></span>

<span data-ttu-id="cd574-147">___Ejemplo___</span><span class="sxs-lookup"><span data-stu-id="cd574-147">___Example___</span></span>

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

<span data-ttu-id="cd574-148">En este ejemplo se muestra una interfaz expuesta por un `com.example.Door.PrivateDoor`dispositivo:.</span><span class="sxs-lookup"><span data-stu-id="cd574-148">This example shows an interface exposed by a device: `com.example.Door.PrivateDoor`.</span></span> <span data-ttu-id="cd574-149">En el ámbito de la interfaz, lo único que nos preocupa es si la comunicación se debe proteger al usar esa interfaz, no qué tipo de mecanismo se está usando.</span><span class="sxs-lookup"><span data-stu-id="cd574-149">In the scope of the interface, the only thing we're concerned about is whether communication should be secured when using that interface, not what type of mechanism is being used.</span></span>

<span data-ttu-id="cd574-150">__Capacidades de interfaz__</span><span class="sxs-lookup"><span data-stu-id="cd574-150">__Interface Capabilities__</span></span>

<span data-ttu-id="cd574-151">Las interfaces declaran sus capacidades con tres miembros de interfaz: métodos, propiedades o señales.</span><span class="sxs-lookup"><span data-stu-id="cd574-151">Interfaces declare their capabilities with three interface members: methods, properties, or signals.</span></span> <span data-ttu-id="cd574-152">Introspección XML también admite anotaciones que describen funcionalidad o restricciones adicionales.</span><span class="sxs-lookup"><span data-stu-id="cd574-152">Introspection XML also supports annotations that describe additional functionality or constraints.</span></span>  <span data-ttu-id="cd574-153">Estas funcionalidades usan la notación UpperCamelCase mientras que los argumentos usan la notación lowerCamelCase.</span><span class="sxs-lookup"><span data-stu-id="cd574-153">These capabilities use UpperCamelCase notation while arguments use lowerCamelCase notation.</span></span>

### <a name="argument-types"></a><span data-ttu-id="cd574-154">Tipos de argumento</span><span class="sxs-lookup"><span data-stu-id="cd574-154">Argument Types</span></span>

<span data-ttu-id="cd574-155">Los miembros de interfaz envían y reciben argumentos indicados por un código de tipo ASCII.</span><span class="sxs-lookup"><span data-stu-id="cd574-155">Interface members send and receive arguments denoted by an ASCII type-code.</span></span>  <span data-ttu-id="cd574-156">Dependiendo del tipo de miembro de interfaz, es posible que los argumentos se hayan enviado al productor desde el consumidor (Direction = "out") o desde el consumidor hasta el productor (Direction = "in").</span><span class="sxs-lookup"><span data-stu-id="cd574-156">Depending on the type of interface member, arguments may have be sent to the producer from the consumer (direction="out") or from the consumer to the producer (direction="in").</span></span>  <span data-ttu-id="cd574-157">En la tabla siguiente se proporciona una breve descripción de los tipos usados comúnmente:</span><span class="sxs-lookup"><span data-stu-id="cd574-157">The following table provides a brief overview of commonly used types:</span></span>

> | <span data-ttu-id="cd574-158">*Nombre convencional*</span><span class="sxs-lookup"><span data-stu-id="cd574-158">*Conventional Name*</span></span> | <span data-ttu-id="cd574-159">*Código de tipo*</span><span class="sxs-lookup"><span data-stu-id="cd574-159">*Type-Code*</span></span> | <span data-ttu-id="cd574-160">*Uso*</span><span class="sxs-lookup"><span data-stu-id="cd574-160">*Use*</span></span> |
> |----------------- |---------| --- |
> |<span data-ttu-id="cd574-161">**BOOLEANO**</span><span class="sxs-lookup"><span data-stu-id="cd574-161">**BOOLEAN**</span></span> | <span data-ttu-id="cd574-162">b</span><span class="sxs-lookup"><span data-stu-id="cd574-162">b</span></span> | <span data-ttu-id="cd574-163">Representa TRUE (1) o FALSE (0).</span><span class="sxs-lookup"><span data-stu-id="cd574-163">Represents TRUE (1) or FALSE (0).</span></span> <span data-ttu-id="cd574-164">Se utiliza para obtener información o Estados binarios simples.</span><span class="sxs-lookup"><span data-stu-id="cd574-164">Used for simple binary information or states.</span></span> |
> |<span data-ttu-id="cd574-165">**BYTES**</span><span class="sxs-lookup"><span data-stu-id="cd574-165">**BYTE**</span></span> | <span data-ttu-id="cd574-166">y</span><span class="sxs-lookup"><span data-stu-id="cd574-166">y</span></span> | <span data-ttu-id="cd574-167">Valor entero comprendido entre 0 y 255.</span><span class="sxs-lookup"><span data-stu-id="cd574-167">Integer value from 0 to 255.</span></span> <span data-ttu-id="cd574-168">Se usa cuando se trabaja con números positivos pequeños.</span><span class="sxs-lookup"><span data-stu-id="cd574-168">Used when dealing with small positive numbers.</span></span> |
> |<span data-ttu-id="cd574-169">**UINT16**</span><span class="sxs-lookup"><span data-stu-id="cd574-169">**UINT16**</span></span> | <span data-ttu-id="cd574-170">q</span><span class="sxs-lookup"><span data-stu-id="cd574-170">q</span></span> | <span data-ttu-id="cd574-171">Valor entero de 0 a 2 ^ 16-1</span><span class="sxs-lookup"><span data-stu-id="cd574-171">Integer value from 0 to 2^16 - 1</span></span> |
> |<span data-ttu-id="cd574-172">**UINT32**</span><span class="sxs-lookup"><span data-stu-id="cd574-172">**UINT32**</span></span> | <span data-ttu-id="cd574-173">5\.50</span><span class="sxs-lookup"><span data-stu-id="cd574-173">u</span></span> | <span data-ttu-id="cd574-174">Valor entero de 0 a 2 ^ 32-1</span><span class="sxs-lookup"><span data-stu-id="cd574-174">Integer value from 0 to 2^32 - 1</span></span> |
> |<span data-ttu-id="cd574-175">**UINT64**</span><span class="sxs-lookup"><span data-stu-id="cd574-175">**UINT64**</span></span> | <span data-ttu-id="cd574-176">t</span><span class="sxs-lookup"><span data-stu-id="cd574-176">t</span></span> | <span data-ttu-id="cd574-177">Valor entero de 0 a 2 ^ 64-1</span><span class="sxs-lookup"><span data-stu-id="cd574-177">Integer value from 0 to 2^64 - 1</span></span> |
> |<span data-ttu-id="cd574-178">**INT16**</span><span class="sxs-lookup"><span data-stu-id="cd574-178">**INT16**</span></span> | <span data-ttu-id="cd574-179">per?</span><span class="sxs-lookup"><span data-stu-id="cd574-179">n</span></span> | <span data-ttu-id="cd574-180">Valor entero de – (2 ^ 15) a 2 ^ 15-1</span><span class="sxs-lookup"><span data-stu-id="cd574-180">Integer value from –(2^15) to 2^15 - 1</span></span> |
> |<span data-ttu-id="cd574-181">**INT32**</span><span class="sxs-lookup"><span data-stu-id="cd574-181">**INT32**</span></span> | <span data-ttu-id="cd574-182">i</span><span class="sxs-lookup"><span data-stu-id="cd574-182">i</span></span> | <span data-ttu-id="cd574-183">Valor entero de – (2 ^ 31) a 2 ^ 31-1</span><span class="sxs-lookup"><span data-stu-id="cd574-183">Integer value from –(2^31) to 2^31 - 1</span></span> |
> |<span data-ttu-id="cd574-184">**INT64**</span><span class="sxs-lookup"><span data-stu-id="cd574-184">**INT64**</span></span> | <span data-ttu-id="cd574-185">x</span><span class="sxs-lookup"><span data-stu-id="cd574-185">x</span></span> | <span data-ttu-id="cd574-186">Valor entero de – (2 ^ 63) a 2 ^ 63-1</span><span class="sxs-lookup"><span data-stu-id="cd574-186">Integer value from –(2^63) to 2^63 - 1</span></span> |
> |<span data-ttu-id="cd574-187">**HACE**</span><span class="sxs-lookup"><span data-stu-id="cd574-187">**DOUBLE**</span></span> | <span data-ttu-id="cd574-188">d</span><span class="sxs-lookup"><span data-stu-id="cd574-188">d</span></span> | <span data-ttu-id="cd574-189">Números de punto flotante de precisión desde – (2 ^ 127) hasta 2 ^ 127-1</span><span class="sxs-lookup"><span data-stu-id="cd574-189">Precision floating point numbers from –(2^127) to 2^127 - 1</span></span> |
> |<span data-ttu-id="cd574-190">**STRING@**</span><span class="sxs-lookup"><span data-stu-id="cd574-190">**STRING**</span></span> | <span data-ttu-id="cd574-191">s</span><span class="sxs-lookup"><span data-stu-id="cd574-191">s</span></span> | <span data-ttu-id="cd574-192">Cadena UTF-8</span><span class="sxs-lookup"><span data-stu-id="cd574-192">UTF-8 string</span></span> |
 
<span data-ttu-id="cd574-193">Para obtener información general más exhaustiva sobre todos los tipos admitidos, consulte [aquí](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span><span class="sxs-lookup"><span data-stu-id="cd574-193">For a more exhaustive overview of all the supported types, see [here](http://dbus.freedesktop.org/doc/dbus-specification.html#idp94392448).</span></span>

<span data-ttu-id="cd574-194">En el punto de redactar este documento, use las unidades SI siempre que sea posible y denote claramente las unidades prepensadas.</span><span class="sxs-lookup"><span data-stu-id="cd574-194">As of this writing, use SI units where possible and clearly denote intended units.</span></span> <span data-ttu-id="cd574-195">Cuando sea posible, elija el código de tipo más restrictivo para su escenario; por ejemplo, si está representando la edad de una persona en años, use BYTE, no UINT16 o INT16, ya que nadie tendrá una edad negativa o más de 255 años.</span><span class="sxs-lookup"><span data-stu-id="cd574-195">When possible, choose the type-code most restrictive to your scenario; e.g., if you are representing a person's age in years, then use BYTE, not UINT16 or INT16, since no one will be a negative age or more than 255 years old.</span></span>  <span data-ttu-id="cd574-196">Siga siempre las instrucciones más recientes del panel de revisión de la [interfaz AllJoyn (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) .</span><span class="sxs-lookup"><span data-stu-id="cd574-196">Always follow the latest [AllJoyn Interface Review Board (IRB)](https://wiki.allseenalliance.org/interfacereviewboard?s%5b%5d=interface&s%5b%5d=review&s%5b%5d=board) guidelines.</span></span>

<span data-ttu-id="cd574-197">En la tabla siguiente se resumen las unidades comunes:</span><span class="sxs-lookup"><span data-stu-id="cd574-197">The following table summarizes common units:</span></span>


> |<span data-ttu-id="cd574-198">*Volumen*</span><span class="sxs-lookup"><span data-stu-id="cd574-198">*Quantity*</span></span> | <span data-ttu-id="cd574-199">*Unidad*</span><span class="sxs-lookup"><span data-stu-id="cd574-199">*Unit*</span></span>|
> |-------- | ---- |
> |<span data-ttu-id="cd574-200">**Tiempo absoluto (fecha & hora)**</span><span class="sxs-lookup"><span data-stu-id="cd574-200">**Absolute time (date & time)**</span></span> | <span data-ttu-id="cd574-201">Segundos desde la época de UNIX (00:00:00 el 1 de enero de 1970)</span><span class="sxs-lookup"><span data-stu-id="cd574-201">Seconds since UNIX Epoch (00:00:00 on January 1, 1970)</span></span> |
> |<span data-ttu-id="cd574-202">**Hora del día**</span><span class="sxs-lookup"><span data-stu-id="cd574-202">**Time of Day**</span></span> | <span data-ttu-id="cd574-203">Segundos desde la medianoche</span><span class="sxs-lookup"><span data-stu-id="cd574-203">Seconds since midnight</span></span> |
> |<span data-ttu-id="cd574-204">**Intervalo de tiempo**</span><span class="sxs-lookup"><span data-stu-id="cd574-204">**Time interval**</span></span> | <span data-ttu-id="cd574-205">Segundos</span><span class="sxs-lookup"><span data-stu-id="cd574-205">Seconds</span></span> |
> |<span data-ttu-id="cd574-206">**Consumo**</span><span class="sxs-lookup"><span data-stu-id="cd574-206">**Bandwidth**</span></span> | <span data-ttu-id="cd574-207">Bits por segundo</span><span class="sxs-lookup"><span data-stu-id="cd574-207">Bits per second</span></span> |
> |<span data-ttu-id="cd574-208">**Tamaño de los datos**</span><span class="sxs-lookup"><span data-stu-id="cd574-208">**Data size**</span></span> | <span data-ttu-id="cd574-209">Bytes</span><span class="sxs-lookup"><span data-stu-id="cd574-209">Bytes</span></span> |
 
### <a name="methods"></a><span data-ttu-id="cd574-210">Métodos</span><span class="sxs-lookup"><span data-stu-id="cd574-210">Methods</span></span>

<span data-ttu-id="cd574-211">Los consumidores llaman a métodos para modificar el estado de un productor y sus nombres deben empezar con un verbo porque representan solicitudes para que el productor realice una acción.</span><span class="sxs-lookup"><span data-stu-id="cd574-211">Consumers call methods to modify the state of a producer, and their names should start with a verb because they represent requests for the producer to perform an action.</span></span>  <span data-ttu-id="cd574-212">Los métodos pueden tener argumentos de entrada y salida; en el caso de que no sea necesario enviar ningún mensaje de retorno, aplique la anotación "org. freedesktop. dBu. Method. noresponse".</span><span class="sxs-lookup"><span data-stu-id="cd574-212">Methods may have input and output arguments; in the case that no return message needs to be sent, apply the annotation "org.freedesktop.DBus.Method.NoReply".</span></span>  <span data-ttu-id="cd574-213">Sin embargo, los métodos AllJoyn normalmente devuelven un SuccessResult o un FailureResult, lo que otorga a los consumidores comentarios sobre la llamada al método.</span><span class="sxs-lookup"><span data-stu-id="cd574-213">However, AllJoyn methods normally return a SuccessResult or a FailureResult, giving consumers feedback about the method call.</span></span>  <span data-ttu-id="cd574-214">El tipo de los argumentos debe cumplir la [especificación de bus D](http://dbus.freedesktop.org/doc/dbus-specification.html).</span><span class="sxs-lookup"><span data-stu-id="cd574-214">The type of the arguments must comply with the [D-Bus Specification](http://dbus.freedesktop.org/doc/dbus-specification.html).</span></span> 

<span data-ttu-id="cd574-215">___Ejemplo (excluir información de interfaz para mayor comodidad)___</span><span class="sxs-lookup"><span data-stu-id="cd574-215">___Example (excluding interface information for convenience)___</span></span>

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

<span data-ttu-id="cd574-216">*Nota: En la mayoría de los casos, se deben usar propiedades en lugar de métodos para tener acceso al estado de un productor (por ejemplo, usar una propiedad de color en lugar de un método GetColor).*</span><span class="sxs-lookup"><span data-stu-id="cd574-216">*Note: In most cases, properties should be used instead of methods to access a producer's state (e.g., use a Color property instead of a GetColor method).*</span></span>

### <a name="properties"></a><span data-ttu-id="cd574-217">Propiedades</span><span class="sxs-lookup"><span data-stu-id="cd574-217">Properties</span></span>

<span data-ttu-id="cd574-218">Las propiedades permiten principalmente el acceso al estado de un productor.</span><span class="sxs-lookup"><span data-stu-id="cd574-218">Properties mainly allow access to a producer's state.</span></span>  <span data-ttu-id="cd574-219">Aunque las propiedades técnicamente tienen los valores de acceso de "lectura", "ReadWrite" o "escritura", la funcionalidad de modificación de Estado suele pertenecer a métodos, como tal, los desarrolladores deben tratar de mantener las propiedades como "lectura" y usar "ReadWrite" solo cuando el estado representado esa propiedad es independiente de todas las demás propiedades.</span><span class="sxs-lookup"><span data-stu-id="cd574-219">While properties technically have access values of "read", "readwrite", or "write", state-modifying functionality generally belongs to methods – as such, developers should strive to keep properties as "read" and use "readwrite" only when the state represented by that property is independent of all other properties.</span></span>  <span data-ttu-id="cd574-220">Las propiedades nunca deben ser simplemente "write": modificar el estado sin observación es el rol de los métodos.</span><span class="sxs-lookup"><span data-stu-id="cd574-220">Properties should never be just "write" – modifying the state without observation is the role of methods.</span></span>

<span data-ttu-id="cd574-221">Las propiedades se deben anotar para avisar a los consumidores cuando cambian sus valores (opcionalmente, las propiedades pueden heredar esta anotación de su interfaz primaria).</span><span class="sxs-lookup"><span data-stu-id="cd574-221">Properties must be annotated to alert consumers when their values change (optionally, properties can inherit this annotation from its parent interface).</span></span>  <span data-ttu-id="cd574-222">La anotación `org.freedesktop.DBus.Property.EmitsChangedSignal` puede tener cuatro valores:</span><span class="sxs-lookup"><span data-stu-id="cd574-222">The annotation `org.freedesktop.DBus.Property.EmitsChangedSignal` can have four values:</span></span>

* <span data-ttu-id="cd574-223">"true": cuando cambia la propiedad, el productor emitirá una señal que denota la propiedad cambiada y el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="cd574-223">"true" – when the property changes, the producer will emit a signal denoting the changed property and the new value.</span></span> <span data-ttu-id="cd574-224">Se utiliza en las propiedades que se usan con frecuencia y requieren supervisión activa, como un "LockState" para una puerta.</span><span class="sxs-lookup"><span data-stu-id="cd574-224">Used in properties that are frequently used and require active oversight, such as a "LockState" for a door.</span></span>
* <span data-ttu-id="cd574-225">"invalidaciones": cuando la propiedad cambia, el productor emitirá una señal que denota la propiedad modificada pero no el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="cd574-225">"invalidates" – when the property changes, the producer will emit a signal denoting the changed property but not the new value.</span></span> <span data-ttu-id="cd574-226">Se usa en las propiedades que no requieren mucha supervisión (por ejemplo, "WashMode" de una secadora de ropa) o que representan una gran cantidad de datos, como un contenedor.</span><span class="sxs-lookup"><span data-stu-id="cd574-226">Used in properties that don't require heavy oversight (such as the "WashMode" of a clothes dryer) or represent a lot of data, such as a container.</span></span>
* <span data-ttu-id="cd574-227">"false": cuando cambia la propiedad, el productor no emite ninguna señal.</span><span class="sxs-lookup"><span data-stu-id="cd574-227">"false" – when the property changes, the producer emits no signal.</span></span> <span data-ttu-id="cd574-228">Se usa en las propiedades que se actualizan rápidamente, como una propiedad "TransitCounter" en un próximo de seguimiento de guión de la próximo.</span><span class="sxs-lookup"><span data-stu-id="cd574-228">Used in properties that update rapidly, such as a "TransitCounter" property on a subway turnstile tracking people boarding the subway.</span></span> <span data-ttu-id="cd574-229">Si no se especifica, las propiedades AllJoyn lo utilizan como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="cd574-229">If unspecified, AllJoyn properties use this as default.</span></span>
* <span data-ttu-id="cd574-230">"const": la propiedad nunca cambiará el valor y nunca emitirá una señal modificada.</span><span class="sxs-lookup"><span data-stu-id="cd574-230">"const" – the property will never change value and never emit a changed signal.</span></span> <span data-ttu-id="cd574-231">Esto se presentará en la versión AllJoyn 16,04; hasta entonces, use "true".</span><span class="sxs-lookup"><span data-stu-id="cd574-231">This will be introduced in the AllJoyn 16.04 release; until then, use "true".</span></span>

<span data-ttu-id="cd574-232">___Ejemplo___</span><span class="sxs-lookup"><span data-stu-id="cd574-232">___Example___</span></span>

<span data-ttu-id="cd574-233">Al expandir el ejemplo anterior, hemos modificado el código XML para incluir las propiedades (excepto los métodos para mayor brevedad).</span><span class="sxs-lookup"><span data-stu-id="cd574-233">Expanding upon the previous example, we have modified the XML to include properties (excluding the methods for brevity).</span></span>

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

### <a name="signals"></a><span data-ttu-id="cd574-234">Simultáneamente</span><span class="sxs-lookup"><span data-stu-id="cd574-234">Signals</span></span>

<span data-ttu-id="cd574-235">Use señales para informar a los consumidores de un evento que no pudieron determinar consultando el productor.</span><span class="sxs-lookup"><span data-stu-id="cd574-235">Use signals to inform consumers of an event that they could not determine by querying the producer.</span></span>  <span data-ttu-id="cd574-236">Una abertura de puerta se transmitiría a través de la propiedad DoorOpen de un productor con una anotación EmitsChangedProperty "true".</span><span class="sxs-lookup"><span data-stu-id="cd574-236">A door opening would be conveyed through a producer's DoorOpen property with a "true" EmitsChangedProperty annotation.</span></span>  <span data-ttu-id="cd574-237">No obstante, alguien que pase a través de la puerta no se puede derivar de cualquier cambio de propiedad, por lo que esto haría una buena señal independiente.</span><span class="sxs-lookup"><span data-stu-id="cd574-237">Someone passing through the door, however, cannot be derived from any property changes, so this would make a good standalone signal.</span></span>  <span data-ttu-id="cd574-238">Hacemos referencia a estos tipos de eventos como "sin estado".</span><span class="sxs-lookup"><span data-stu-id="cd574-238">We refer to these kinds of events as "stateless".</span></span>  <span data-ttu-id="cd574-239">Dado que las señales son unidireccionales desde el productor hasta el consumidor, solo pueden contener argumentos "out".</span><span class="sxs-lookup"><span data-stu-id="cd574-239">Since signals are unidirectional from producer to consumer, they can only contain "out" arguments.</span></span>

<span data-ttu-id="cd574-240">___Example___</span><span class="sxs-lookup"><span data-stu-id="cd574-240">___Examples___</span></span> 

<span data-ttu-id="cd574-241">(sin incluir métodos y propiedades para mayor comodidad):</span><span class="sxs-lookup"><span data-stu-id="cd574-241">(excluding methods and properties for convenience):</span></span>

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

<span data-ttu-id="cd574-242">Dado que las señales tienen un ámbito tan estrecho, normalmente aparecen pocas en el XML de un productor.</span><span class="sxs-lookup"><span data-stu-id="cd574-242">Since signals have such a narrow scope, typically few appear in a producer's XML.</span></span>

### <a name="containers"></a><span data-ttu-id="cd574-243">Contenedores</span><span class="sxs-lookup"><span data-stu-id="cd574-243">Containers</span></span>

<span data-ttu-id="cd574-244">No Combine varios argumentos en una colección compleja como una cadena JSON serializada.</span><span class="sxs-lookup"><span data-stu-id="cd574-244">Do not combine multiple arguments into a complex collection like a serialized JSON string.</span></span> <span data-ttu-id="cd574-245">La especificación de bus D realiza prestaciones para contenedores de datos: STRUCT, ARRAY, VARIANT y DICT_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="cd574-245">The D-Bus specification makes affordances for containers of data – STRUCT, ARRAY, VARIANT, and DICT_ENTRY.</span></span>  <span data-ttu-id="cd574-246">Úselos para pasar argumentos que requieran más de tipos básicos.</span><span class="sxs-lookup"><span data-stu-id="cd574-246">Use these to pass arguments that require more than basic types.</span></span>

<span data-ttu-id="cd574-247">___VARIANTE___</span><span class="sxs-lookup"><span data-stu-id="cd574-247">___VARIANT___</span></span>

<span data-ttu-id="cd574-248">Las variantes se indican mediante el tipo "v" y pueden contener cualquier [tipo completo](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span><span class="sxs-lookup"><span data-stu-id="cd574-248">VARIANTs are denoted by the type "v" and can contain any [single complete type](http://dbus.freedesktop.org/doc/dbus-specification.html#term-single-complete-type).</span></span> <span data-ttu-id="cd574-249">Sin embargo, las variantes deben evitarse siempre que sea posible porque agregan ambigüedad a las definiciones XML.</span><span class="sxs-lookup"><span data-stu-id="cd574-249">However, VARIANTs should be avoided whenever possible because they add ambiguity to XML definitions.</span></span>

<span data-ttu-id="cd574-250">___DESTRUCTOR___</span><span class="sxs-lookup"><span data-stu-id="cd574-250">___STRUCT___</span></span>

<span data-ttu-id="cd574-251">Los STRUCTs usan "(" y ")" para indicar el principio y el final de una estructura de datos, un solo tipo completo.</span><span class="sxs-lookup"><span data-stu-id="cd574-251">STRUCTs use "(" and ")" to denote the beginning and end of a data structure – a single complete type.</span></span>  <span data-ttu-id="cd574-252">Estas estructuras de datos pueden estar anidadas.</span><span class="sxs-lookup"><span data-stu-id="cd574-252">These data structures may be nested.</span></span>

<span data-ttu-id="cd574-253">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="cd574-253">Examples:</span></span>

<span data-ttu-id="cd574-254">Un tipo de "(III)" denota una estructura de tres enteros; "(i (II))" denota una estructura de un entero y una estructura de dos enteros, que es diferente del tipo "((II) i)".</span><span class="sxs-lookup"><span data-stu-id="cd574-254">A type of "(iii)" denotes a structure of three integers; "(i(ii))" denotes a STRUCT of an integer and a STRUCT of two integers, which is distinct from the type "((ii)i)".</span></span>

<span data-ttu-id="cd574-255">___MATRIZ___</span><span class="sxs-lookup"><span data-stu-id="cd574-255">___ARRAY___</span></span>

<span data-ttu-id="cd574-256">Las matrices usan el código de tipo "a" y deben ir seguidos de un único tipo completo.</span><span class="sxs-lookup"><span data-stu-id="cd574-256">ARRAYs use the type code "a" and must be followed by a single complete type.</span></span>  <span data-ttu-id="cd574-257">Las matrices no tienen longitudes fijas, por lo que son similares a una estructura de datos de lista.</span><span class="sxs-lookup"><span data-stu-id="cd574-257">ARRAYs do not have set lengths, so they are similar to a list data structure.</span></span> <span data-ttu-id="cd574-258">Las matrices representan un único tipo completo.</span><span class="sxs-lookup"><span data-stu-id="cd574-258">ARRAYs represent a single complete type.</span></span>

<span data-ttu-id="cd574-259">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="cd574-259">Examples:</span></span>

<span data-ttu-id="cd574-260">Un tipo de "AI" representa una matriz de enteros, mientras que "AAI" representa una matriz de enteros.</span><span class="sxs-lookup"><span data-stu-id="cd574-260">A type of "ai" represents an ARRAY of integers, while "aai" represents an ARRAY of an ARRAY of integers.</span></span>  <span data-ttu-id="cd574-261">También se puede utilizar una matriz con STRUCTs: "a (II)".</span><span class="sxs-lookup"><span data-stu-id="cd574-261">An ARRAY may be used with STRUCTs as well: "a(ii)".</span></span>

<span data-ttu-id="cd574-262">___DICT_ENTRY___</span><span class="sxs-lookup"><span data-stu-id="cd574-262">___DICT_ENTRY___</span></span>

<span data-ttu-id="cd574-263">DICT_ENTRYs función similar a una estructura con restricciones mayores: usan "{" y "}", solo se puede producir como un tipo de elemento de matriz y deben tener exactamente dos tipos completos dentro de las llaves.</span><span class="sxs-lookup"><span data-stu-id="cd574-263">DICT_ENTRYs function similar to a STRUCT with greater restrictions: they use "{" and "}", may only occur as an array element type, and must have exactly two complete types inside the curly braces.</span></span>  <span data-ttu-id="cd574-264">El primer tipo representa una "clave" en una estructura de datos del diccionario y la segunda representa el "valor" en el par clave-valor del diccionario.</span><span class="sxs-lookup"><span data-stu-id="cd574-264">The first type represents a "Key" in a dictionary data structure, and the second represents the "Value" in the dictionary's Key-Value pair.</span></span>  <span data-ttu-id="cd574-265">Una clave debe ser única en un diccionario.</span><span class="sxs-lookup"><span data-stu-id="cd574-265">A Key should be unique in a dictionary.</span></span>

<span data-ttu-id="cd574-266">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="cd574-266">Example:</span></span>

<span data-ttu-id="cd574-267">Un tipo de {SY} denota un diccionario de claves de cadena y valores de byte.</span><span class="sxs-lookup"><span data-stu-id="cd574-267">A type of a{sy} denotes a dictionary of string KEYs and byte VALUEs.</span></span>  <span data-ttu-id="cd574-268">Usar</span><span class="sxs-lookup"><span data-stu-id="cd574-268">Use</span></span> <description> <span data-ttu-id="cd574-269">Etiquetas para describir claves y valores válidos.</span><span class="sxs-lookup"><span data-stu-id="cd574-269">tags to describe valid keys and values.</span></span> 

<span data-ttu-id="cd574-270">__Ejemplo final y ajxmlcop__</span><span class="sxs-lookup"><span data-stu-id="cd574-270">__Final Example and ajxmlcop__</span></span>

<span data-ttu-id="cd574-271">El concepto de contenedores mejora las capacidades del XML existente y proporciona una vía para los nuevos miembros de interfaz útiles.</span><span class="sxs-lookup"><span data-stu-id="cd574-271">The concept of containers improves the capabilities of the existing XML as well as providing an avenue for new useful interface members.</span></span>

<span data-ttu-id="cd574-272">Una vez que haya terminado de escribir el código XML, use la herramienta de línea de comandos ajxmlcop. exe (disponible en el [origen de Git](https://git.allseenalliance.org/cgit/core/alljoyn.git/) de AllJoyn o [aquí](https://github.com/MS-brock/AllJoynToasterDemo)) para validar el XML.</span><span class="sxs-lookup"><span data-stu-id="cd574-272">Once you have finished writing your XML, use the ajxmlcop.exe command line tool (available at the AllJoyn [git source](https://git.allseenalliance.org/cgit/core/alljoyn.git/) or [here](https://github.com/MS-brock/AllJoynToasterDemo)) to validate the XML.</span></span>  <span data-ttu-id="cd574-273">Use ajxmlcop. exe con el archivo XML como argumento de entrada (por ejemplo, `C:\>ajxmlcop.exe doorExample.xml`) para recibir mensajes de error, de advertencia e informativos.</span><span class="sxs-lookup"><span data-stu-id="cd574-273">Use ajxmlcop.exe with your XML file as the input argument (e.g., `C:\>ajxmlcop.exe doorExample.xml`) to receive error, warning, and informational messages.</span></span>  <span data-ttu-id="cd574-274">Esta herramienta proporciona comentarios valiosos sobre la estructura y el formato del XML y el uso de señales, propiedades y métodos.</span><span class="sxs-lookup"><span data-stu-id="cd574-274">This tool provides valuable feedback as to the structure and format of your XML and use of signals, properties, and methods.</span></span>

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

