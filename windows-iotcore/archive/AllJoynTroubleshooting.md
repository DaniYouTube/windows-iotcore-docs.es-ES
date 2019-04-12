---
title: Solución de problemas de AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo solucionar problemas de tecnología de AllJoyn con esta completa guía que cubren los problemas conocidos y solución de problemas de configuración.
keywords: Windows iot, AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514340"
---
> [!NOTE]
> <span data-ttu-id="b5885-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="b5885-104">You are viewing archived documentation.</span></span> <span data-ttu-id="b5885-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="b5885-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="b5885-106">Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.</span><span class="sxs-lookup"><span data-stu-id="b5885-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-troubleshooting"></a><span data-ttu-id="b5885-107">Solución de problemas de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="b5885-107">AllJoyn Troubleshooting</span></span>

<span data-ttu-id="b5885-108">[AllJoyn](https://allseenalliance.org/developers/learn) es una tecnología que permite a los dispositivos de IoT y aplicaciones para detectar e interactuar entre sí.</span><span class="sxs-lookup"><span data-stu-id="b5885-108">[AllJoyn](https://allseenalliance.org/developers/learn) is a technology that enables IoT devices and applications to discover and interact with each other.</span></span> <span data-ttu-id="b5885-109">Puesto que AllJoyn está integrada en Windows 10 y el SDK de Windows 10, es fácil aprovechar las ventajas de AllJoyn con la plataforma Universal de Windows (UWP).</span><span class="sxs-lookup"><span data-stu-id="b5885-109">Since AllJoyn is built into Windows 10 and the Windows 10 SDK, it's easy to take advantage of AllJoyn using the Universal Windows Platform (UWP).</span></span>

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

<span data-ttu-id="b5885-111">Esta entrada de blog le ayudará a configurar la red de AllJoyn y dispositivos y también proporcionan los pasos de solución de problemas cuando algo no funcione según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="b5885-111">This blog post will help you configure your AllJoyn network and devices, and also provide troubleshooting steps to follow when things don't work as expected.</span></span> <span data-ttu-id="b5885-112">El objetivo principal de este artículo se habilitará la comunicación entre aplicaciones de cliente de AllJoyn de UWP (AllJoyn consumidores) y dispositivos de AllJoyn (AllJoyn productores).</span><span class="sxs-lookup"><span data-stu-id="b5885-112">The primary focus of this article will be enabling communication between UWP AllJoyn client apps (AllJoyn consumers) and AllJoyn devices (AllJoyn producers).</span></span> <span data-ttu-id="b5885-113">Muchos de los mismos pasos de configuración son necesarios para habilitar la comunicación con aplicaciones de UWP AllJoyn productor, pero aún más los detalles se quedará en futuras en blogs y artículos.</span><span class="sxs-lookup"><span data-stu-id="b5885-113">Many of the same configuration steps are required to enable communication with UWP AllJoyn Producer apps, but further details will be left to future blog posts and articles.</span></span>

### <a name="app-development-checklist"></a><span data-ttu-id="b5885-114">Lista de comprobación de desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="b5885-114">App Development Checklist</span></span>

<span data-ttu-id="b5885-115">Si está escribiendo aplicaciones para UWP para Windows 10, primero debe asegurarse:</span><span class="sxs-lookup"><span data-stu-id="b5885-115">If you are writing UWP apps for Windows 10, you should make sure that:</span></span>

1. <span data-ttu-id="b5885-116">Se ha declarado la función 'allJoyn' en el manifiesto de la aplicación (tenga en cuenta mayúsculas y minúsculas).</span><span class="sxs-lookup"><span data-stu-id="b5885-116">You've declared the 'allJoyn' capability in your app's manifest (note casing).</span></span>
2. <span data-ttu-id="b5885-117">Ha seleccionado la arquitectura específica que se va a dirigir.</span><span class="sxs-lookup"><span data-stu-id="b5885-117">You've selected the specific architecture that you'll be targeting.</span></span> <span data-ttu-id="b5885-118">(Necesario en algunos casos porque no se pueden compilar los componentes de Windows en tiempo de ejecución mediante "Any CPU", un problema conocido con algunas Visual Studio 2017 se basa).</span><span class="sxs-lookup"><span data-stu-id="b5885-118">(Required in some cases because Windows Runtime Components cannot be built using 'Any CPU', a known issue with some Visual Studio 2017 builds).</span></span>

<span data-ttu-id="b5885-119">Si está escribiendo una aplicación o software de dispositivo que no es una aplicación basada en UWP para Windows 10, debe revisar la siguiente lista de comprobación para garantizar la compatibilidad con AllJoyn en Windows 10:</span><span class="sxs-lookup"><span data-stu-id="b5885-119">If you are writing an app or device software that is not a UWP-based application for Windows 10, you should review the following checklist to ensure compatibility with AllJoyn in Windows 10:</span></span>

1. <span data-ttu-id="b5885-120">Si implementa un productor, asegúrese de que acerca de la interfaz y el anuncio y detección basada en About se usan.</span><span class="sxs-lookup"><span data-stu-id="b5885-120">If implementing a Producer, ensure that the About interface and About-based advertisement/discovery are being used.</span></span> <span data-ttu-id="b5885-121">Es la interfaz About [documentada en el sitio Web de AllSeen Alliance](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span><span class="sxs-lookup"><span data-stu-id="b5885-121">The About interface is [documented at the AllSeen Alliance website](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span></span>
2. <span data-ttu-id="b5885-122">Para obtener mejores resultados, use la base de código AllJoyn 15.04, disponible en el [sección de descargas](https://allseenalliance.org/developers/download) del sitio Web AllSeen Alliance.</span><span class="sxs-lookup"><span data-stu-id="b5885-122">For best results, use the 15.04 AllJoyn code base, available in the [downloads section](https://allseenalliance.org/developers/download) of the AllSeen Alliance website.</span></span>

### <a name="network-setup-and-troubleshooting"></a><span data-ttu-id="b5885-123">Configuración de red y la solución de problemas</span><span class="sxs-lookup"><span data-stu-id="b5885-123">Network Setup and Troubleshooting</span></span>

<span data-ttu-id="b5885-124">Para que los dispositivos AllJoyn ser capaz de descubrir e interactuar entre sí, la configuración de red y la configuración para cada dispositivo debe cumplir lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b5885-124">For AllJoyn devices to be able to discover and interact with each other, the network configuration and settings for each device must satisfy the following:</span></span>

1. <span data-ttu-id="b5885-125">Todos los dispositivos de AllJoyn están conectados a la misma red y en la misma subred.</span><span class="sxs-lookup"><span data-stu-id="b5885-125">All AllJoyn devices are connected to the same network, and are on the same subnet.</span></span>
2. <span data-ttu-id="b5885-126">Windows 10 PC: "Buscar dispositivos y el contenido" está habilitada para la red en uso con AllJoyn (no es aplicable para Phone).</span><span class="sxs-lookup"><span data-stu-id="b5885-126">Windows 10 PC: "Find devices and content" is enabled for the network in use with AllJoyn (does not apply for Phone).</span></span>

<span data-ttu-id="b5885-127">En un equipo puede usar el comando de la ruta de seguimiento desde una ventana CMD o PowerShell para comprobar si otro máquina/el dispositivo está en la misma subred como sigue:</span><span class="sxs-lookup"><span data-stu-id="b5885-127">On a PC you can use the trace route command from a CMD or PowerShell window to check if another machine/device is on the same subnet as follows:</span></span>

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

<span data-ttu-id="b5885-128">Aquí la primera salida número es el número de saltos, y dado que ese valor es "1" significa que ambos equipos están en la misma subred.</span><span class="sxs-lookup"><span data-stu-id="b5885-128">The first number output here is the number of hops, and since that value is "1" it means that both machines are on the same subnet.</span></span>

<span data-ttu-id="b5885-129">A continuación es un ejemplo de una configuración de red AllJoyn típica.</span><span class="sxs-lookup"><span data-stu-id="b5885-129">Below is an example of a typical AllJoyn network setup.</span></span> <span data-ttu-id="b5885-130">En este ejemplo, todos los dispositivos que se muestran sería capaz de descubrir e interactuar entre sí mediante AllJoyn suponiendo que estuvieran en la misma subred.</span><span class="sxs-lookup"><span data-stu-id="b5885-130">In this example, all of the devices shown would be able to discover and interact with each other using AllJoyn assuming they were on the same subnet.</span></span>

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

<span data-ttu-id="b5885-132">Cuando se conecta el equipo con Windows 10 a la red con dispositivos AllJoyn, deberá si se muestra un cuadro de diálogo con respecto a los equipos y dispositivos de la búsqueda en la red, haga clic en "Sí".</span><span class="sxs-lookup"><span data-stu-id="b5885-132">When you connect your Windows 10 PC to the network with AllJoyn devices, you'll need to click "Yes" if a dialog is displayed regarding finding devices and PCs on the network.</span></span> <span data-ttu-id="b5885-133">(Tenga en cuenta: Esto no es aplicable al unirse a redes de teléfonos con Windows 10, porque no hay ningún cuadro de diálogo tal).</span><span class="sxs-lookup"><span data-stu-id="b5885-133">(Note: This does not apply when joining networks from Windows 10 Phone as there is no such dialog).</span></span>

<span data-ttu-id="b5885-134">También puede administrar esta configuración en la página "Configuración avanzada" en la configuración de Wi-Fi como se muestra aquí: (esta página puede ser ligeramente diferente dependiendo de la compilación de Windows 10 Insider usa)</span><span class="sxs-lookup"><span data-stu-id="b5885-134">You can also manage this setting in the "Advanced Settings" page in Wi-Fi settings as shown here: (this page may look slightly different depending on which Windows 10 Insider build you are using)</span></span>

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

<span data-ttu-id="b5885-136">El botón de alternancia para "Buscar dispositivos y el contenido" debe estar en la posición "On" para habilitar la funcionalidad de AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="b5885-136">The toggle for "Find devices and content" should be in the "On" position in order to enable AllJoyn functionality.</span></span>

<span data-ttu-id="b5885-137">Para las conexiones de red existentes, puede validar fácilmente si esta opción está configurada correctamente, ejecute el cmdlet de Powershell "Get-NetConnectionProfile".</span><span class="sxs-lookup"><span data-stu-id="b5885-137">For existing network connections, you can easily validate whether this option is configured properly by running the "Get-NetConnectionProfile" Powershell cmdlet .</span></span> <span data-ttu-id="b5885-138">(Tenga en cuenta que esto no es aplicable para teléfonos con Windows 10).</span><span class="sxs-lookup"><span data-stu-id="b5885-138">(Note that this does not apply for Windows 10 Phone).</span></span>

<span data-ttu-id="b5885-139">Ejemplo de salida de Get-NetConnectionProfile:</span><span class="sxs-lookup"><span data-stu-id="b5885-139">Example Get-NetConnectionProfile output:</span></span>

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


<span data-ttu-id="b5885-140">Si el valor de "NetworkCategory" es "Private" (como se muestra arriba), esto indica que ha configurado correctamente la conexión de red para AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="b5885-140">If the "NetworkCategory" value is "Private" (as shown above), this indicates that you have a properly configured your network connection for AllJoyn.</span></span>

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a><span data-ttu-id="b5885-141">Acerca de la publicidad y la solución de problemas de detección con Getajxml.exe</span><span class="sxs-lookup"><span data-stu-id="b5885-141">About Advertisement and Troubleshooting Discovery with Getajxml.exe</span></span>

<span data-ttu-id="b5885-142">Para que los dispositivos de productor de AllJoyn o las aplicaciones para que sea reconocible por las aplicaciones de Windows 10 UWP AllJoyn, detección basada en sobre debe implementarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="b5885-142">For AllJoyn producer devices or apps to be discoverable by Windows 10 UWP AllJoyn apps, About-based discovery must be properly implemented.</span></span> <span data-ttu-id="b5885-143">Esto se puede comprobar fácilmente con la herramienta GetAjXml.exe.</span><span class="sxs-lookup"><span data-stu-id="b5885-143">This can be easily verified with the GetAjXml.exe tool.</span></span> <span data-ttu-id="b5885-144">Para obtener información de descarga y uso relacionados con GetAjXml.exe, consulte [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span><span class="sxs-lookup"><span data-stu-id="b5885-144">To find download and usage information related to GetAjXml.exe, check out [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span></span>

<span data-ttu-id="b5885-145">A continuación muestra la salida GetAjXml.exe para un dispositivo de ejemplo que admite la detección basada en sobre:</span><span class="sxs-lookup"><span data-stu-id="b5885-145">The following shows GetAjXml.exe output for an example device that supports About-based discovery:</span></span>

    ----------------------------------------------------------------------
    Discovery   : About Announcement
    Manufacturer: Microsoft
    Model #     : 070773
    Device Name : Raspberry Pi Toaster
    Device ID   : 41d9a124-6913-40c5-a20a-9d1b20f8121b
    App Name   : Toaster Producer
          Bus Name                       Port Object Path
          ============================== ===== ===============================
          :3yZG_wu1.2                       25 /emergency
          :3yZG_wu1.2                       25 /info
          :3yZG_wu1.2                       25 /notificationDismisser
          :3yZG_wu1.2                       25 /notificationProducer
          :3yZG_wu1.2                       25 /toaster
          :3yZG_wu1.2                       25 /warning


<span data-ttu-id="b5885-146">En el ejemplo anterior, puesto que `Discovery   : About Announcement` se incluyó en esta salida, este productor AllJoyn podrán detectar aplicaciones AllJoyn de Windows 10 UWP.</span><span class="sxs-lookup"><span data-stu-id="b5885-146">In the above example, since `Discovery   : About Announcement` was included in this output, this AllJoyn producer will be discoverable by Windows 10 AllJoyn UWP apps.</span></span> <span data-ttu-id="b5885-147">Si no ve esta salida para un productor AllJoyn determinado, deberá investigar la implementación de detección en el lado del dispositivo (productor).</span><span class="sxs-lookup"><span data-stu-id="b5885-147">If you don't see this output for a particular AllJoyn producer, you will need to investigate the discovery implementation on the device (Producer) side.</span></span>

### <a name="advanced-troubleshooting-with-etw-log-output"></a><span data-ttu-id="b5885-148">Solución avanzada de problemas con la salida del registro ETW</span><span class="sxs-lookup"><span data-stu-id="b5885-148">Advanced Troubleshooting with ETW Log Output</span></span>

<span data-ttu-id="b5885-149">Seguimiento de eventos para Windows (ETW) puede ayudarle a obtener información de depuración para muchas de las distintas características de Windows avanzada.</span><span class="sxs-lookup"><span data-stu-id="b5885-149">Event Tracing for Windows (ETW) can help you get advanced debugging information for many different features in Windows.</span></span> <span data-ttu-id="b5885-150">Afortunadamente AllJoyn es una de las características con registro de soporte técnico, por lo que en esta sección mostraré cómo habilitar el registro para AllJoyn ETW y cómo tener acceso a los registros ETW.</span><span class="sxs-lookup"><span data-stu-id="b5885-150">Fortunately AllJoyn is one of the features with ETW logging support, so in this section I'll show you how to enable ETW logging for AllJoyn, and how to access logs.</span></span>

1. <span data-ttu-id="b5885-151">Inicie el Visor de eventos escribiendo "Registros de eventos" en el cuadro de texto de búsqueda del menú Inicio, seleccione "ver registros de eventos".</span><span class="sxs-lookup"><span data-stu-id="b5885-151">Launch the Event Viewer by typing "Event Logs" into the Start Menu search textbox, select "View Event Logs".</span></span>
2. <span data-ttu-id="b5885-152">En el menú "Ver", asegúrese de que se activa "Mostrar registros analíticos y de depuración".</span><span class="sxs-lookup"><span data-stu-id="b5885-152">In the "View" menu, ensure that "Show Analytic and Debug Logs" is checked.</span></span>
3. <span data-ttu-id="b5885-153">Vaya a la vista de árbol en el panel de navegación izquierdo para "Aplicaciones y servicios registros > Microsoft > Windows > AllJoyn" en la vista de carpetas y habilite el canal de depuración y el canal operativo.</span><span class="sxs-lookup"><span data-stu-id="b5885-153">Navigate the tree view in the left navigation to "Applications and Services Logs > Microsoft > Windows > AllJoyn" in the folder view, and enable both the Debug channel and the Operational channel.</span></span> <span data-ttu-id="b5885-154">(vea un cuadro rojo en la siguiente captura de pantalla).</span><span class="sxs-lookup"><span data-stu-id="b5885-154">(see red box in screenshot below).</span></span>
4. <span data-ttu-id="b5885-155">Reproduzca el problema que está experimentando con AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="b5885-155">Reproduce the problem that you are experiencing with AllJoyn.</span></span>
5. <span data-ttu-id="b5885-156">Haga clic en "Actualización" en la barra de la derecha "acciones", a continuación, compruebe los canales operativos y de depuración en la barra de navegación izquierdo debajo de la carpeta "AllJoyn".</span><span class="sxs-lookup"><span data-stu-id="b5885-156">Click on "Refresh" in the right "Actions" bar, then check the Operational and Debug channels from the left navigation bar under the "AllJoyn" folder.</span></span>

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

<span data-ttu-id="b5885-158">Los seguimientos de ETW AllJoyn se dividen en particiones como sigue:</span><span class="sxs-lookup"><span data-stu-id="b5885-158">AllJoyn ETW traces are partitioned as follows:</span></span>

- <span data-ttu-id="b5885-159">Canal de depuración: Seguimientos detallados, no-error/informativo</span><span class="sxs-lookup"><span data-stu-id="b5885-159">Debug channel: Verbose, non-error/informational traces</span></span>
- <span data-ttu-id="b5885-160">Canal operativo: Seguimientos de errores, errores son sólo de salida en el canal operativo</span><span class="sxs-lookup"><span data-stu-id="b5885-160">Operational channel: Error traces, errors are only output on the operational channel</span></span>

<span data-ttu-id="b5885-161">Con el fin de extraer información de las entradas ETW, puede hacer doble clic en una entrada en la vista de lista para un canal determinado y, a continuación, seleccione "Copiar" y, a continuación, en "Copiar detalles como texto".</span><span class="sxs-lookup"><span data-stu-id="b5885-161">In order to extract information from ETW entries, you can right-click on an entry in the list view for a given channel, and then select "Copy" and then "Copy Details as Text".</span></span> <span data-ttu-id="b5885-162">Si, a continuación, pegar el texto correspondiente en un editor de texto, tendrá los detalles, como en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b5885-162">If you then paste the corresponding text into a text editor, you'll have detail like the example below:</span></span>


    Log Name:       Microsoft-Windows-AllJoyn/Operational
    Source:         Microsoft-Windows-AllJoyn
    Date:           6/1/2015 3:57:45 PM
    Event ID:     2
    Task Category: AJ
    Level:         Error
    Keywords:      (70368744177664),AJ
    User:         LOCAL SERVICE
    Computer:       <computer name>
     
    Description:
    AllJoyn encountered an error 0x902D in module UDP, file ..\udptransport.cc, at line number 10809. See the event user data for more information.
    Event Xml:
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
    <System>
       <Provider Name="Microsoft-Windows-AllJoyn" Guid="{2ED299D2-2F6B-411D-8D15-F4CC6FDE0C70}" />
        <EventID>2</EventID>
        <Version>0</Version>
        <Level>2</Level>
        <Task>1</Task>
        <Opcode>10</Opcode>
        <Keywords>0x8000400000000001</Keywords>
       <TimeCreated SystemTime="2015-06-01T22:57:45.626729500Z" />
        <EventRecordID>16</EventRecordID>
       <Correlation />
       <Execution ProcessID="1392" ThreadID="5768" />
       <Channel>Microsoft-Windows-AllJoyn/Operational</Channel>
        <Computer>computer name</Computer>
       <Security UserID="SID" />
    </System>
    <UserData>
       <AJErrorData xmlns="http://manifests.microsoft.com/win/2005/08/windows/alljoyn/events">
           <QStatus>0x902d</QStatus>
           <Message>UDPTransport::DisbleDiscovery(): Not running or stopping; exiting</Message>
           <Module>UDP</Module>
           <File>..\udptransport.cc</File>
           <Line>10809</Line>
        </AJErrorData>
    </UserData>
    </Event>


<span data-ttu-id="b5885-163">Esta información puede ayudar a localizar problemas de AllJoyn o ayudar a proporcionar detalles al notificar problemas a Microsoft o a otros asociados.</span><span class="sxs-lookup"><span data-stu-id="b5885-163">This information can help track down AllJoyn issues, or assist in providing detail when reporting issues to Microsoft or other partners.</span></span> <span data-ttu-id="b5885-164">Puede obtener más información acerca de [ETW seguimientos y el Visor de eventos en MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span><span class="sxs-lookup"><span data-stu-id="b5885-164">You can learn more about [ETW traces and the Event Viewer on MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span></span>

### <a name="known-issues-and-limitations"></a><span data-ttu-id="b5885-165">Problemas y limitaciones conocidos</span><span class="sxs-lookup"><span data-stu-id="b5885-165">Known Issues and Limitations</span></span>

<span data-ttu-id="b5885-166">Limitaciones de diseño para AllJoyn de Windows 10:</span><span class="sxs-lookup"><span data-stu-id="b5885-166">By-Design limitations for AllJoyn in Windows 10:</span></span>

- <span data-ttu-id="b5885-167">El nodo de AllJoyn Router no es iniciado automáticamente por AllJoyn dispositivos o aplicaciones en la red cuando no hay aplicaciones se ejecutan en el equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b5885-167">The AllJoyn Router Node is not auto-started by AllJoyn devices or apps on the network when no apps are running on the Windows 10 PC.</span></span> <span data-ttu-id="b5885-168">El nodo de enrutador de Windows 10 se puede iniciar desde un símbolo del sistema con privilegios elevados o una sesión de Powershell ejecutando el comando "net start ajrouter".</span><span class="sxs-lookup"><span data-stu-id="b5885-168">The Windows 10 Router Node can be started from an elevated command prompt or Powershell session by running the command "net start ajrouter".</span></span>
- <span data-ttu-id="b5885-169">Aplicaciones AllJoyn UWP no pueden detectar ni interactuar con otras aplicaciones de AllJoyn UWP o aplicaciones de escritorio de AllJoyn que se ejecutan en el mismo equipo.</span><span class="sxs-lookup"><span data-stu-id="b5885-169">AllJoyn UWP apps can't discover or interact with other AllJoyn UWP apps or AllJoyn desktop apps running on the same machine.</span></span> <span data-ttu-id="b5885-170">Esta es una parte de la promesa de aislamiento de aplicación se implementa en Windows 10 para aplicaciones UWP.</span><span class="sxs-lookup"><span data-stu-id="b5885-170">This is a part of the app isolation promise that is implemented in Windows 10 for UWP apps.</span></span> 
  - <span data-ttu-id="b5885-171">Si implementa una aplicación de AllJoyn UWP desde Visual Studio, el aislamiento de aplicación de aislamiento de aplicaciones se omite para esa aplicación (Esto se denomina una exención de bucle invertido"").</span><span class="sxs-lookup"><span data-stu-id="b5885-171">If you deploy an AllJoyn UWP app from Visual Studio, app isolation app isolation is bypassed for that app (this is called a "loopback exemption ").</span></span> <span data-ttu-id="b5885-172">Cada aplicación para UWP que se implemente desde Visual Studio podrá descubrir e interactuar con otras aplicaciones de escritorio y aplicaciones UWP de exención de bucle invertido, siempre y cuando esas aplicaciones usan anuncio/detección basada en sobre.</span><span class="sxs-lookup"><span data-stu-id="b5885-172">Each UWP app that is deployed from Visual Studio will be able to discover and interact with other loopback-exempt UWP apps and desktop apps as long as those apps use About-based advertisement/discovery.</span></span> <span data-ttu-id="b5885-173">Si está ejecutando Windows 10 IoT Core en "Modo incrustado", automáticamente se aplica esta excepción de bucle invertido, no es algo que deba configurar.</span><span class="sxs-lookup"><span data-stu-id="b5885-173">If you are running Windows 10 IoT Core in "Embedded Mode", this loopback exception is automatically applied, it's not something that you need to configure.</span></span> <span data-ttu-id="b5885-174">Puede leer más sobre las excepciones de bucle invertido [en MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span><span class="sxs-lookup"><span data-stu-id="b5885-174">You can read more about loopback exceptions [on MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>

