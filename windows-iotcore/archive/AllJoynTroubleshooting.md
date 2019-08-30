---
title: Solución de problemas de AllJoyn
author: saraclay
ms.author: saclayt
ms.date: 09/07/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: Obtenga información sobre cómo solucionar problemas de la tecnología AllJoyn con esta guía completa que trata los problemas conocidos y la configuración de solución de problemas.
keywords: Windows IOT, AllJoyn
ms.openlocfilehash: 8b93242c8f583199ee5890c6d0d15985f9025175
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169973"
---
> [!NOTE]
> <span data-ttu-id="72194-104">Está viendo la documentación archivada.</span><span class="sxs-lookup"><span data-stu-id="72194-104">You are viewing archived documentation.</span></span> <span data-ttu-id="72194-105">AllJoyn ya no es compatible con Windows 10 IoT.</span><span class="sxs-lookup"><span data-stu-id="72194-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="72194-106">Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.</span><span class="sxs-lookup"><span data-stu-id="72194-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="alljoyn-troubleshooting"></a><span data-ttu-id="72194-107">Solución de problemas de AllJoyn</span><span class="sxs-lookup"><span data-stu-id="72194-107">AllJoyn Troubleshooting</span></span>

<span data-ttu-id="72194-108">[AllJoyn](https://allseenalliance.org/developers/learn) es una tecnología que permite a los dispositivos y aplicaciones IOT detectar e interactuar entre sí.</span><span class="sxs-lookup"><span data-stu-id="72194-108">[AllJoyn](https://allseenalliance.org/developers/learn) is a technology that enables IoT devices and applications to discover and interact with each other.</span></span> <span data-ttu-id="72194-109">Como AllJoyn está integrado en Windows 10 y el SDK de Windows 10, es fácil aprovechar AllJoyn con el Plataforma universal de Windows (UWP).</span><span class="sxs-lookup"><span data-stu-id="72194-109">Since AllJoyn is built into Windows 10 and the Windows 10 SDK, it's easy to take advantage of AllJoyn using the Universal Windows Platform (UWP).</span></span>

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

<span data-ttu-id="72194-111">Esta entrada de blog le ayudará a configurar la red y los dispositivos de AllJoyn, así como los pasos de solución de problemas que deben seguirse cuando las cosas no funcionan según lo esperado.</span><span class="sxs-lookup"><span data-stu-id="72194-111">This blog post will help you configure your AllJoyn network and devices, and also provide troubleshooting steps to follow when things don't work as expected.</span></span> <span data-ttu-id="72194-112">El objetivo principal de este artículo será habilitar la comunicación entre las aplicaciones cliente de AllJoyn de UWP (consumidores AllJoyn) y los dispositivos AllJoyn (productores AllJoyn).</span><span class="sxs-lookup"><span data-stu-id="72194-112">The primary focus of this article will be enabling communication between UWP AllJoyn client apps (AllJoyn consumers) and AllJoyn devices (AllJoyn producers).</span></span> <span data-ttu-id="72194-113">Muchos de los mismos pasos de configuración son necesarios para habilitar la comunicación con las aplicaciones de productores AllJoyn de UWP, pero se dejarán más detalles en las próximas entradas y artículos de blog.</span><span class="sxs-lookup"><span data-stu-id="72194-113">Many of the same configuration steps are required to enable communication with UWP AllJoyn Producer apps, but further details will be left to future blog posts and articles.</span></span>

### <a name="app-development-checklist"></a><span data-ttu-id="72194-114">Lista de comprobación de desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="72194-114">App Development Checklist</span></span>

<span data-ttu-id="72194-115">Si va a escribir aplicaciones para UWP para Windows 10, debe asegurarse de que:</span><span class="sxs-lookup"><span data-stu-id="72194-115">If you are writing UWP apps for Windows 10, you should make sure that:</span></span>

1. <span data-ttu-id="72194-116">Ha declarado la funcionalidad ' allJoyn ' en el manifiesto de la aplicación (con mayúsculas y minúsculas).</span><span class="sxs-lookup"><span data-stu-id="72194-116">You've declared the 'allJoyn' capability in your app's manifest (note casing).</span></span>
2. <span data-ttu-id="72194-117">Ha seleccionado la arquitectura específica de destino.</span><span class="sxs-lookup"><span data-stu-id="72194-117">You've selected the specific architecture that you'll be targeting.</span></span> <span data-ttu-id="72194-118">(Se requiere en algunos casos porque Windows Runtime componentes no se pueden compilar con ' any CPU ', un problema conocido con algunas compilaciones de Visual Studio 2017).</span><span class="sxs-lookup"><span data-stu-id="72194-118">(Required in some cases because Windows Runtime Components cannot be built using 'Any CPU', a known issue with some Visual Studio 2017 builds).</span></span>

<span data-ttu-id="72194-119">Si va a escribir una aplicación o software de dispositivo que no es una aplicación basada en UWP para Windows 10, debe revisar la siguiente lista de comprobación para garantizar la compatibilidad con AllJoyn en Windows 10:</span><span class="sxs-lookup"><span data-stu-id="72194-119">If you are writing an app or device software that is not a UWP-based application for Windows 10, you should review the following checklist to ensure compatibility with AllJoyn in Windows 10:</span></span>

1. <span data-ttu-id="72194-120">Si va a implementar un productor, asegúrese de que se están usando la interfaz about y la detección de anuncios basados en.</span><span class="sxs-lookup"><span data-stu-id="72194-120">If implementing a Producer, ensure that the About interface and About-based advertisement/discovery are being used.</span></span> <span data-ttu-id="72194-121">La interfaz about se [documenta en el sitio web de AllSeen Alliance](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span><span class="sxs-lookup"><span data-stu-id="72194-121">The About interface is [documented at the AllSeen Alliance website](https://allseenalliance.org/developers/learn/core/about-announcement/interface).</span></span>
2. <span data-ttu-id="72194-122">Para obtener los mejores resultados, use la base de código AllJoyn 15,04, disponible en la [sección de descargas](https://allseenalliance.org/developers/download) del sitio web de AllSeen Alliance.</span><span class="sxs-lookup"><span data-stu-id="72194-122">For best results, use the 15.04 AllJoyn code base, available in the [downloads section](https://allseenalliance.org/developers/download) of the AllSeen Alliance website.</span></span>

### <a name="network-setup-and-troubleshooting"></a><span data-ttu-id="72194-123">Configuración y solución de problemas de red</span><span class="sxs-lookup"><span data-stu-id="72194-123">Network Setup and Troubleshooting</span></span>

<span data-ttu-id="72194-124">Para que los dispositivos AllJoyn puedan detectar e interactuar entre sí, la configuración de red y la configuración de cada dispositivo deben cumplir lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="72194-124">For AllJoyn devices to be able to discover and interact with each other, the network configuration and settings for each device must satisfy the following:</span></span>

1. <span data-ttu-id="72194-125">Todos los dispositivos AllJoyn están conectados a la misma red y se encuentran en la misma subred.</span><span class="sxs-lookup"><span data-stu-id="72194-125">All AllJoyn devices are connected to the same network, and are on the same subnet.</span></span>
2. <span data-ttu-id="72194-126">PC con Windows 10: "Buscar dispositivos y contenido" está habilitado para la red en uso con AllJoyn (no se aplica al teléfono).</span><span class="sxs-lookup"><span data-stu-id="72194-126">Windows 10 PC: "Find devices and content" is enabled for the network in use with AllJoyn (does not apply for Phone).</span></span>

<span data-ttu-id="72194-127">En un equipo, puede usar el comando seguimiento de ruta desde una ventana de CMD o PowerShell para comprobar si otro equipo o dispositivo está en la misma subred de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="72194-127">On a PC you can use the trace route command from a CMD or PowerShell window to check if another machine/device is on the same subnet as follows:</span></span>

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

<span data-ttu-id="72194-128">La salida del primer número aquí es el número de saltos, y dado que ese valor es "1", significa que ambos equipos están en la misma subred.</span><span class="sxs-lookup"><span data-stu-id="72194-128">The first number output here is the number of hops, and since that value is "1" it means that both machines are on the same subnet.</span></span>

<span data-ttu-id="72194-129">A continuación se muestra un ejemplo de una configuración de red de AllJoyn típica.</span><span class="sxs-lookup"><span data-stu-id="72194-129">Below is an example of a typical AllJoyn network setup.</span></span> <span data-ttu-id="72194-130">En este ejemplo, todos los dispositivos mostrados podrían detectarse e interactuar entre sí mediante AllJoyn suponiendo que estuvieran en la misma subred.</span><span class="sxs-lookup"><span data-stu-id="72194-130">In this example, all of the devices shown would be able to discover and interact with each other using AllJoyn assuming they were on the same subnet.</span></span>

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

<span data-ttu-id="72194-132">Al conectar su equipo con Windows 10 a la red con dispositivos AllJoyn, deberá hacer clic en "sí" si se muestra un cuadro de diálogo con respecto a la búsqueda de dispositivos y equipos en la red.</span><span class="sxs-lookup"><span data-stu-id="72194-132">When you connect your Windows 10 PC to the network with AllJoyn devices, you'll need to click "Yes" if a dialog is displayed regarding finding devices and PCs on the network.</span></span> <span data-ttu-id="72194-133">Tenga en cuenta Esto no se aplica al unir redes desde Windows 10 Phone, ya que no hay ningún cuadro de diálogo de este tipo.</span><span class="sxs-lookup"><span data-stu-id="72194-133">(Note: This does not apply when joining networks from Windows 10 Phone as there is no such dialog).</span></span>

<span data-ttu-id="72194-134">También puede administrar esta opción en la página "configuración avanzada" en configuración de Wi-Fi, como se muestra aquí: (esta página puede tener un aspecto ligeramente diferente en función de la compilación de Windows 10 Insider que esté usando)</span><span class="sxs-lookup"><span data-stu-id="72194-134">You can also manage this setting in the "Advanced Settings" page in Wi-Fi settings as shown here: (this page may look slightly different depending on which Windows 10 Insider build you are using)</span></span>

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

<span data-ttu-id="72194-136">La alternancia de "buscar dispositivos y contenido" debe estar en la posición "activado" para habilitar la funcionalidad AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="72194-136">The toggle for "Find devices and content" should be in the "On" position in order to enable AllJoyn functionality.</span></span>

<span data-ttu-id="72194-137">En el caso de las conexiones de red existentes, puede validar fácilmente si esta opción está configurada correctamente mediante la ejecución del cmdlet de PowerShell "Get-NetConnectionProfile".</span><span class="sxs-lookup"><span data-stu-id="72194-137">For existing network connections, you can easily validate whether this option is configured properly by running the "Get-NetConnectionProfile" Powershell cmdlet .</span></span> <span data-ttu-id="72194-138">(Tenga en cuenta que esto no se aplica a Windows 10 Phone).</span><span class="sxs-lookup"><span data-stu-id="72194-138">(Note that this does not apply for Windows 10 Phone).</span></span>

<span data-ttu-id="72194-139">Ejemplo de salida Get-NetConnectionProfile:</span><span class="sxs-lookup"><span data-stu-id="72194-139">Example Get-NetConnectionProfile output:</span></span>

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


<span data-ttu-id="72194-140">Si el valor "NetworkCategory" es "Private" (como se mostró anteriormente), significa que ha configurado correctamente la conexión de red para AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="72194-140">If the "NetworkCategory" value is "Private" (as shown above), this indicates that you have a properly configured your network connection for AllJoyn.</span></span>

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a><span data-ttu-id="72194-141">Acerca de la detección de anuncios y solución de problemas con Getajxml. exe</span><span class="sxs-lookup"><span data-stu-id="72194-141">About Advertisement and Troubleshooting Discovery with Getajxml.exe</span></span>

<span data-ttu-id="72194-142">Para que las aplicaciones de AllJoyn de Windows 10 UWP puedan detectar aplicaciones o dispositivos productores de AllJoyn, la detección basada en se debe implementar correctamente.</span><span class="sxs-lookup"><span data-stu-id="72194-142">For AllJoyn producer devices or apps to be discoverable by Windows 10 UWP AllJoyn apps, About-based discovery must be properly implemented.</span></span> <span data-ttu-id="72194-143">Esto puede comprobarse fácilmente con la herramienta GetAjXml. exe.</span><span class="sxs-lookup"><span data-stu-id="72194-143">This can be easily verified with the GetAjXml.exe tool.</span></span> <span data-ttu-id="72194-144">Para buscar información de uso y descarga relacionada con GetAjXml. exe, consulte [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span><span class="sxs-lookup"><span data-stu-id="72194-144">To find download and usage information related to GetAjXml.exe, check out [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).</span></span>

<span data-ttu-id="72194-145">A continuación se muestra la salida de GetAjXml. exe para un dispositivo de ejemplo que admite la detección basada en about:</span><span class="sxs-lookup"><span data-stu-id="72194-145">The following shows GetAjXml.exe output for an example device that supports About-based discovery:</span></span>

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


<span data-ttu-id="72194-146">En el ejemplo anterior, como `Discovery   : About Announcement` se incluyó en esta salida, las aplicaciones de UWP de alljoyn de Windows 10 detectarán este productor alljoyn.</span><span class="sxs-lookup"><span data-stu-id="72194-146">In the above example, since `Discovery   : About Announcement` was included in this output, this AllJoyn producer will be discoverable by Windows 10 AllJoyn UWP apps.</span></span> <span data-ttu-id="72194-147">Si no ve esta salida para un productor AllJoyn determinado, deberá investigar la implementación de la detección en el lado del dispositivo (productor).</span><span class="sxs-lookup"><span data-stu-id="72194-147">If you don't see this output for a particular AllJoyn producer, you will need to investigate the discovery implementation on the device (Producer) side.</span></span>

### <a name="advanced-troubleshooting-with-etw-log-output"></a><span data-ttu-id="72194-148">Solución avanzada de problemas con la salida del registro de ETW</span><span class="sxs-lookup"><span data-stu-id="72194-148">Advanced Troubleshooting with ETW Log Output</span></span>

<span data-ttu-id="72194-149">Seguimiento de eventos para Windows (ETW) puede ayudarle a obtener información de depuración avanzada para muchas características diferentes de Windows.</span><span class="sxs-lookup"><span data-stu-id="72194-149">Event Tracing for Windows (ETW) can help you get advanced debugging information for many different features in Windows.</span></span> <span data-ttu-id="72194-150">Afortunadamente, AllJoyn es una de las características de compatibilidad con el registro de ETW, por lo que en esta sección le mostraré cómo habilitar el registro de ETW para AllJoyn y cómo obtener acceso a los registros.</span><span class="sxs-lookup"><span data-stu-id="72194-150">Fortunately AllJoyn is one of the features with ETW logging support, so in this section I'll show you how to enable ETW logging for AllJoyn, and how to access logs.</span></span>

1. <span data-ttu-id="72194-151">Inicie el Visor de eventos escribiendo "registros de eventos" en el cuadro de texto de búsqueda del menú Inicio y seleccione "Ver registros de eventos".</span><span class="sxs-lookup"><span data-stu-id="72194-151">Launch the Event Viewer by typing "Event Logs" into the Start Menu search textbox, select "View Event Logs".</span></span>
2. <span data-ttu-id="72194-152">En el menú "ver", asegúrese de que está activada la casilla "Mostrar registros analíticos y de depuración".</span><span class="sxs-lookup"><span data-stu-id="72194-152">In the "View" menu, ensure that "Show Analytic and Debug Logs" is checked.</span></span>
3. <span data-ttu-id="72194-153">Navegue por la vista de árbol en el panel de navegación izquierdo hasta "registros de aplicaciones y servicios > Microsoft > Windows > AllJoyn" en la vista de carpetas y habilite el canal de depuración y el canal operativo.</span><span class="sxs-lookup"><span data-stu-id="72194-153">Navigate the tree view in the left navigation to "Applications and Services Logs > Microsoft > Windows > AllJoyn" in the folder view, and enable both the Debug channel and the Operational channel.</span></span> <span data-ttu-id="72194-154">(vea el cuadro rojo en la captura de pantalla siguiente).</span><span class="sxs-lookup"><span data-stu-id="72194-154">(see red box in screenshot below).</span></span>
4. <span data-ttu-id="72194-155">Reproduzca el problema que está experimentando con AllJoyn.</span><span class="sxs-lookup"><span data-stu-id="72194-155">Reproduce the problem that you are experiencing with AllJoyn.</span></span>
5. <span data-ttu-id="72194-156">Haga clic en "actualizar" en la barra derecha "acciones" y, a continuación, compruebe los canales operativos y de depuración en la barra de navegación izquierda bajo la carpeta "AllJoyn".</span><span class="sxs-lookup"><span data-stu-id="72194-156">Click on "Refresh" in the right "Actions" bar, then check the Operational and Debug channels from the left navigation bar under the "AllJoyn" folder.</span></span>

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

<span data-ttu-id="72194-158">Los seguimientos de ETW de AllJoyn tienen particiones como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="72194-158">AllJoyn ETW traces are partitioned as follows:</span></span>

- <span data-ttu-id="72194-159">Canal de depuración: Seguimientos detallados, no erróneos o informativos</span><span class="sxs-lookup"><span data-stu-id="72194-159">Debug channel: Verbose, non-error/informational traces</span></span>
- <span data-ttu-id="72194-160">Canal operativo: Seguimientos de errores, los errores solo se muestran en el canal operativo</span><span class="sxs-lookup"><span data-stu-id="72194-160">Operational channel: Error traces, errors are only output on the operational channel</span></span>

<span data-ttu-id="72194-161">Para extraer información de las entradas ETW, puede hacer clic con el botón secundario en una entrada de la vista de lista para un canal determinado y, a continuación, seleccionar "copiar" y, a continuación, "copiar detalles como texto".</span><span class="sxs-lookup"><span data-stu-id="72194-161">In order to extract information from ETW entries, you can right-click on an entry in the list view for a given channel, and then select "Copy" and then "Copy Details as Text".</span></span> <span data-ttu-id="72194-162">Si después pega el texto correspondiente en un editor de texto, tendrá detalles como el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="72194-162">If you then paste the corresponding text into a text editor, you'll have detail like the example below:</span></span>


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


<span data-ttu-id="72194-163">Esta información puede ayudar a realizar un seguimiento de los problemas de AllJoyn o ayudar a proporcionar detalles al informar de problemas a Microsoft o a otros asociados.</span><span class="sxs-lookup"><span data-stu-id="72194-163">This information can help track down AllJoyn issues, or assist in providing detail when reporting issues to Microsoft or other partners.</span></span> <span data-ttu-id="72194-164">Puede obtener más información acerca de [los seguimientos de ETW y el visor de eventos en MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span><span class="sxs-lookup"><span data-stu-id="72194-164">You can learn more about [ETW traces and the Event Viewer on MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).</span></span>

### <a name="known-issues-and-limitations"></a><span data-ttu-id="72194-165">Problemas y limitaciones conocidos</span><span class="sxs-lookup"><span data-stu-id="72194-165">Known Issues and Limitations</span></span>

<span data-ttu-id="72194-166">Limitaciones de diseño de AllJoyn en Windows 10:</span><span class="sxs-lookup"><span data-stu-id="72194-166">By-Design limitations for AllJoyn in Windows 10:</span></span>

- <span data-ttu-id="72194-167">Los dispositivos o aplicaciones de AllJoyn no inician automáticamente el nodo del enrutador AllJoyn en la red cuando no se ejecuta ninguna aplicación en el equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="72194-167">The AllJoyn Router Node is not auto-started by AllJoyn devices or apps on the network when no apps are running on the Windows 10 PC.</span></span> <span data-ttu-id="72194-168">El nodo del enrutador de Windows 10 se puede iniciar desde un símbolo del sistema con privilegios elevados o desde una sesión de PowerShell mediante la ejecución del comando "net start ajrouter".</span><span class="sxs-lookup"><span data-stu-id="72194-168">The Windows 10 Router Node can be started from an elevated command prompt or Powershell session by running the command "net start ajrouter".</span></span>
- <span data-ttu-id="72194-169">Las aplicaciones para UWP de AllJoyn no pueden detectar ni interactuar con otras aplicaciones de UWP de AllJoyn ni con aplicaciones de escritorio AllJoyn que se ejecuten en el mismo equipo.</span><span class="sxs-lookup"><span data-stu-id="72194-169">AllJoyn UWP apps can't discover or interact with other AllJoyn UWP apps or AllJoyn desktop apps running on the same machine.</span></span> <span data-ttu-id="72194-170">Esta es una parte de la promesa de aislamiento de aplicaciones que se implementa en Windows 10 para aplicaciones para UWP.</span><span class="sxs-lookup"><span data-stu-id="72194-170">This is a part of the app isolation promise that is implemented in Windows 10 for UWP apps.</span></span> 
  - <span data-ttu-id="72194-171">Si implementa una aplicación de UWP de AllJoyn desde Visual Studio, se omite el aislamiento de aplicaciones de aislamiento de aplicaciones para esa aplicación (esto se denomina "exención de bucle invertido").</span><span class="sxs-lookup"><span data-stu-id="72194-171">If you deploy an AllJoyn UWP app from Visual Studio, app isolation app isolation is bypassed for that app (this is called a "loopback exemption ").</span></span> <span data-ttu-id="72194-172">Cada aplicación de UWP que se implemente desde Visual Studio podrá detectar e interactuar con otras aplicaciones UWP de exención de bucle invertido y aplicaciones de escritorio, siempre y cuando esas aplicaciones usen la detección y el anuncio basados en.</span><span class="sxs-lookup"><span data-stu-id="72194-172">Each UWP app that is deployed from Visual Studio will be able to discover and interact with other loopback-exempt UWP apps and desktop apps as long as those apps use About-based advertisement/discovery.</span></span> <span data-ttu-id="72194-173">Si está ejecutando Windows 10 IoT Core en "modo incrustado", esta excepción de bucle invertido se aplica automáticamente, no es algo que deba configurar.</span><span class="sxs-lookup"><span data-stu-id="72194-173">If you are running Windows 10 IoT Core in "Embedded Mode", this loopback exception is automatically applied, it's not something that you need to configure.</span></span> <span data-ttu-id="72194-174">Puede obtener más información sobre las excepciones [de bucle invertido en MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span><span class="sxs-lookup"><span data-stu-id="72194-174">You can read more about loopback exceptions [on MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).</span></span>

