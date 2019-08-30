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
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra un problema en GitHub o envíenos sus comentarios en los comentarios siguientes.

# <a name="alljoyn-troubleshooting"></a>Solución de problemas de AllJoyn

[AllJoyn](https://allseenalliance.org/developers/learn) es una tecnología que permite a los dispositivos y aplicaciones IOT detectar e interactuar entre sí. Como AllJoyn está integrado en Windows 10 y el SDK de Windows 10, es fácil aprovechar AllJoyn con el Plataforma universal de Windows (UWP).

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

Esta entrada de blog le ayudará a configurar la red y los dispositivos de AllJoyn, así como los pasos de solución de problemas que deben seguirse cuando las cosas no funcionan según lo esperado. El objetivo principal de este artículo será habilitar la comunicación entre las aplicaciones cliente de AllJoyn de UWP (consumidores AllJoyn) y los dispositivos AllJoyn (productores AllJoyn). Muchos de los mismos pasos de configuración son necesarios para habilitar la comunicación con las aplicaciones de productores AllJoyn de UWP, pero se dejarán más detalles en las próximas entradas y artículos de blog.

### <a name="app-development-checklist"></a>Lista de comprobación de desarrollo de aplicaciones

Si va a escribir aplicaciones para UWP para Windows 10, debe asegurarse de que:

1. Ha declarado la funcionalidad ' allJoyn ' en el manifiesto de la aplicación (con mayúsculas y minúsculas).
2. Ha seleccionado la arquitectura específica de destino. (Se requiere en algunos casos porque Windows Runtime componentes no se pueden compilar con ' any CPU ', un problema conocido con algunas compilaciones de Visual Studio 2017).

Si va a escribir una aplicación o software de dispositivo que no es una aplicación basada en UWP para Windows 10, debe revisar la siguiente lista de comprobación para garantizar la compatibilidad con AllJoyn en Windows 10:

1. Si va a implementar un productor, asegúrese de que se están usando la interfaz about y la detección de anuncios basados en. La interfaz about se [documenta en el sitio web de AllSeen Alliance](https://allseenalliance.org/developers/learn/core/about-announcement/interface).
2. Para obtener los mejores resultados, use la base de código AllJoyn 15,04, disponible en la [sección de descargas](https://allseenalliance.org/developers/download) del sitio web de AllSeen Alliance.

### <a name="network-setup-and-troubleshooting"></a>Configuración y solución de problemas de red

Para que los dispositivos AllJoyn puedan detectar e interactuar entre sí, la configuración de red y la configuración de cada dispositivo deben cumplir lo siguiente:

1. Todos los dispositivos AllJoyn están conectados a la misma red y se encuentran en la misma subred.
2. PC con Windows 10: "Buscar dispositivos y contenido" está habilitado para la red en uso con AllJoyn (no se aplica al teléfono).

En un equipo, puede usar el comando seguimiento de ruta desde una ventana de CMD o PowerShell para comprobar si otro equipo o dispositivo está en la misma subred de la manera siguiente:

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

La salida del primer número aquí es el número de saltos, y dado que ese valor es "1", significa que ambos equipos están en la misma subred.

A continuación se muestra un ejemplo de una configuración de red de AllJoyn típica. En este ejemplo, todos los dispositivos mostrados podrían detectarse e interactuar entre sí mediante AllJoyn suponiendo que estuvieran en la misma subred.

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

Al conectar su equipo con Windows 10 a la red con dispositivos AllJoyn, deberá hacer clic en "sí" si se muestra un cuadro de diálogo con respecto a la búsqueda de dispositivos y equipos en la red. Tenga en cuenta Esto no se aplica al unir redes desde Windows 10 Phone, ya que no hay ningún cuadro de diálogo de este tipo.

También puede administrar esta opción en la página "configuración avanzada" en configuración de Wi-Fi, como se muestra aquí: (esta página puede tener un aspecto ligeramente diferente en función de la compilación de Windows 10 Insider que esté usando)

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

La alternancia de "buscar dispositivos y contenido" debe estar en la posición "activado" para habilitar la funcionalidad AllJoyn.

En el caso de las conexiones de red existentes, puede validar fácilmente si esta opción está configurada correctamente mediante la ejecución del cmdlet de PowerShell "Get-NetConnectionProfile". (Tenga en cuenta que esto no se aplica a Windows 10 Phone).

Ejemplo de salida Get-NetConnectionProfile:

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


Si el valor "NetworkCategory" es "Private" (como se mostró anteriormente), significa que ha configurado correctamente la conexión de red para AllJoyn.

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a>Acerca de la detección de anuncios y solución de problemas con Getajxml. exe

Para que las aplicaciones de AllJoyn de Windows 10 UWP puedan detectar aplicaciones o dispositivos productores de AllJoyn, la detección basada en se debe implementar correctamente. Esto puede comprobarse fácilmente con la herramienta GetAjXml. exe. Para buscar información de uso y descarga relacionada con GetAjXml. exe, consulte [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).

A continuación se muestra la salida de GetAjXml. exe para un dispositivo de ejemplo que admite la detección basada en about:

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


En el ejemplo anterior, como `Discovery   : About Announcement` se incluyó en esta salida, las aplicaciones de UWP de alljoyn de Windows 10 detectarán este productor alljoyn. Si no ve esta salida para un productor AllJoyn determinado, deberá investigar la implementación de la detección en el lado del dispositivo (productor).

### <a name="advanced-troubleshooting-with-etw-log-output"></a>Solución avanzada de problemas con la salida del registro de ETW

Seguimiento de eventos para Windows (ETW) puede ayudarle a obtener información de depuración avanzada para muchas características diferentes de Windows. Afortunadamente, AllJoyn es una de las características de compatibilidad con el registro de ETW, por lo que en esta sección le mostraré cómo habilitar el registro de ETW para AllJoyn y cómo obtener acceso a los registros.

1. Inicie el Visor de eventos escribiendo "registros de eventos" en el cuadro de texto de búsqueda del menú Inicio y seleccione "Ver registros de eventos".
2. En el menú "ver", asegúrese de que está activada la casilla "Mostrar registros analíticos y de depuración".
3. Navegue por la vista de árbol en el panel de navegación izquierdo hasta "registros de aplicaciones y servicios > Microsoft > Windows > AllJoyn" en la vista de carpetas y habilite el canal de depuración y el canal operativo. (vea el cuadro rojo en la captura de pantalla siguiente).
4. Reproduzca el problema que está experimentando con AllJoyn.
5. Haga clic en "actualizar" en la barra derecha "acciones" y, a continuación, compruebe los canales operativos y de depuración en la barra de navegación izquierda bajo la carpeta "AllJoyn".

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

Los seguimientos de ETW de AllJoyn tienen particiones como se indica a continuación:

- Canal de depuración: Seguimientos detallados, no erróneos o informativos
- Canal operativo: Seguimientos de errores, los errores solo se muestran en el canal operativo

Para extraer información de las entradas ETW, puede hacer clic con el botón secundario en una entrada de la vista de lista para un canal determinado y, a continuación, seleccionar "copiar" y, a continuación, "copiar detalles como texto". Si después pega el texto correspondiente en un editor de texto, tendrá detalles como el ejemplo siguiente:


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


Esta información puede ayudar a realizar un seguimiento de los problemas de AllJoyn o ayudar a proporcionar detalles al informar de problemas a Microsoft o a otros asociados. Puede obtener más información acerca de [los seguimientos de ETW y el visor de eventos en MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).

### <a name="known-issues-and-limitations"></a>Problemas y limitaciones conocidos

Limitaciones de diseño de AllJoyn en Windows 10:

- Los dispositivos o aplicaciones de AllJoyn no inician automáticamente el nodo del enrutador AllJoyn en la red cuando no se ejecuta ninguna aplicación en el equipo con Windows 10. El nodo del enrutador de Windows 10 se puede iniciar desde un símbolo del sistema con privilegios elevados o desde una sesión de PowerShell mediante la ejecución del comando "net start ajrouter".
- Las aplicaciones para UWP de AllJoyn no pueden detectar ni interactuar con otras aplicaciones de UWP de AllJoyn ni con aplicaciones de escritorio AllJoyn que se ejecuten en el mismo equipo. Esta es una parte de la promesa de aislamiento de aplicaciones que se implementa en Windows 10 para aplicaciones para UWP. 
  - Si implementa una aplicación de UWP de AllJoyn desde Visual Studio, se omite el aislamiento de aplicaciones de aislamiento de aplicaciones para esa aplicación (esto se denomina "exención de bucle invertido"). Cada aplicación de UWP que se implemente desde Visual Studio podrá detectar e interactuar con otras aplicaciones UWP de exención de bucle invertido y aplicaciones de escritorio, siempre y cuando esas aplicaciones usen la detección y el anuncio basados en. Si está ejecutando Windows 10 IoT Core en "modo incrustado", esta excepción de bucle invertido se aplica automáticamente, no es algo que deba configurar. Puede obtener más información sobre las excepciones [de bucle invertido en MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).

