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
> Está viendo la documentación archivada. AllJoyn ya no es compatible con Windows 10 IoT. Si tiene preguntas, abra una incidencia en GitHub o enviarnos sus comentarios en los comentarios a continuación.

# <a name="alljoyn-troubleshooting"></a>Solución de problemas de AllJoyn

[AllJoyn](https://allseenalliance.org/developers/learn) es una tecnología que permite a los dispositivos de IoT y aplicaciones para detectar e interactuar entre sí. Puesto que AllJoyn está integrada en Windows 10 y el SDK de Windows 10, es fácil aprovechar las ventajas de AllJoyn con la plataforma Universal de Windows (UWP).

![AJ_Troubleshooting_intro](../media/AllJoyn/AJ_Troubleshooting_intro.jpg)

Esta entrada de blog le ayudará a configurar la red de AllJoyn y dispositivos y también proporcionan los pasos de solución de problemas cuando algo no funcione según lo previsto. El objetivo principal de este artículo se habilitará la comunicación entre aplicaciones de cliente de AllJoyn de UWP (AllJoyn consumidores) y dispositivos de AllJoyn (AllJoyn productores). Muchos de los mismos pasos de configuración son necesarios para habilitar la comunicación con aplicaciones de UWP AllJoyn productor, pero aún más los detalles se quedará en futuras en blogs y artículos.

### <a name="app-development-checklist"></a>Lista de comprobación de desarrollo de aplicaciones

Si está escribiendo aplicaciones para UWP para Windows 10, primero debe asegurarse:

1. Se ha declarado la función 'allJoyn' en el manifiesto de la aplicación (tenga en cuenta mayúsculas y minúsculas).
2. Ha seleccionado la arquitectura específica que se va a dirigir. (Necesario en algunos casos porque no se pueden compilar los componentes de Windows en tiempo de ejecución mediante "Any CPU", un problema conocido con algunas Visual Studio 2017 se basa).

Si está escribiendo una aplicación o software de dispositivo que no es una aplicación basada en UWP para Windows 10, debe revisar la siguiente lista de comprobación para garantizar la compatibilidad con AllJoyn en Windows 10:

1. Si implementa un productor, asegúrese de que acerca de la interfaz y el anuncio y detección basada en About se usan. Es la interfaz About [documentada en el sitio Web de AllSeen Alliance](https://allseenalliance.org/developers/learn/core/about-announcement/interface).
2. Para obtener mejores resultados, use la base de código AllJoyn 15.04, disponible en el [sección de descargas](https://allseenalliance.org/developers/download) del sitio Web AllSeen Alliance.

### <a name="network-setup-and-troubleshooting"></a>Configuración de red y la solución de problemas

Para que los dispositivos AllJoyn ser capaz de descubrir e interactuar entre sí, la configuración de red y la configuración para cada dispositivo debe cumplir lo siguiente:

1. Todos los dispositivos de AllJoyn están conectados a la misma red y en la misma subred.
2. Windows 10 PC: "Buscar dispositivos y el contenido" está habilitada para la red en uso con AllJoyn (no es aplicable para Phone).

En un equipo puede usar el comando de la ruta de seguimiento desde una ventana CMD o PowerShell para comprobar si otro máquina/el dispositivo está en la misma subred como sigue:

    PS C:\Users\user> tracert WIN10PC1
     
    Tracing route to WIN10PC1 [fe80::657d:d8bf:176f:d0b2%24]
     
    over a maximum of 30 hops:
     
    1       1 ms     1 ms     1 ms   WIN10PC1 [fe80::657d:d8bf:176f:d0b2]
     
    Trace complete.

Aquí la primera salida número es el número de saltos, y dado que ese valor es "1" significa que ambos equipos están en la misma subred.

A continuación es un ejemplo de una configuración de red AllJoyn típica. En este ejemplo, todos los dispositivos que se muestran sería capaz de descubrir e interactuar entre sí mediante AllJoyn suponiendo que estuvieran en la misma subred.

![AJ_Troubleshooting_Devices](../media/AllJoyn/AJ_Troubleshooting_Devices.jpg)

Cuando se conecta el equipo con Windows 10 a la red con dispositivos AllJoyn, deberá si se muestra un cuadro de diálogo con respecto a los equipos y dispositivos de la búsqueda en la red, haga clic en "Sí". (Tenga en cuenta: Esto no es aplicable al unirse a redes de teléfonos con Windows 10, porque no hay ningún cuadro de diálogo tal).

También puede administrar esta configuración en la página "Configuración avanzada" en la configuración de Wi-Fi como se muestra aquí: (esta página puede ser ligeramente diferente dependiendo de la compilación de Windows 10 Insider usa)

![AJ_Troubleshooting_Settings](../media/AllJoyn/AJ_Troubleshooting_Settings.jpg)

El botón de alternancia para "Buscar dispositivos y el contenido" debe estar en la posición "On" para habilitar la funcionalidad de AllJoyn.

Para las conexiones de red existentes, puede validar fácilmente si esta opción está configurada correctamente, ejecute el cmdlet de Powershell "Get-NetConnectionProfile". (Tenga en cuenta que esto no es aplicable para teléfonos con Windows 10).

Ejemplo de salida de Get-NetConnectionProfile:

    PS C:\Users\user> Get-NetConnectionProfile
     
    Name             : myWirelessNetwork
    InterfaceAlias   : vEthernet (Intel(R) Dual Band Wireless-AC 7260 Virtual Switch)
    InterfaceIndex   : 24
    NetworkCategory : Private
    IPv4Connectivity : Internet
    IPv6Connectivity : LocalNetwork


Si el valor de "NetworkCategory" es "Private" (como se muestra arriba), esto indica que ha configurado correctamente la conexión de red para AllJoyn.

### <a name="about-advertisement-and-troubleshooting-discovery-with-getajxmlexe"></a>Acerca de la publicidad y la solución de problemas de detección con Getajxml.exe

Para que los dispositivos de productor de AllJoyn o las aplicaciones para que sea reconocible por las aplicaciones de Windows 10 UWP AllJoyn, detección basada en sobre debe implementarse correctamente. Esto se puede comprobar fácilmente con la herramienta GetAjXml.exe. Para obtener información de descarga y uso relacionados con GetAjXml.exe, consulte [AllJoyn Studio](https://visualstudiogallery.msdn.microsoft.com/064e58a7-fb56-464b-bed5-f85914c89286).

A continuación muestra la salida GetAjXml.exe para un dispositivo de ejemplo que admite la detección basada en sobre:

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


En el ejemplo anterior, puesto que `Discovery   : About Announcement` se incluyó en esta salida, este productor AllJoyn podrán detectar aplicaciones AllJoyn de Windows 10 UWP. Si no ve esta salida para un productor AllJoyn determinado, deberá investigar la implementación de detección en el lado del dispositivo (productor).

### <a name="advanced-troubleshooting-with-etw-log-output"></a>Solución avanzada de problemas con la salida del registro ETW

Seguimiento de eventos para Windows (ETW) puede ayudarle a obtener información de depuración para muchas de las distintas características de Windows avanzada. Afortunadamente AllJoyn es una de las características con registro de soporte técnico, por lo que en esta sección mostraré cómo habilitar el registro para AllJoyn ETW y cómo tener acceso a los registros ETW.

1. Inicie el Visor de eventos escribiendo "Registros de eventos" en el cuadro de texto de búsqueda del menú Inicio, seleccione "ver registros de eventos".
2. En el menú "Ver", asegúrese de que se activa "Mostrar registros analíticos y de depuración".
3. Vaya a la vista de árbol en el panel de navegación izquierdo para "Aplicaciones y servicios registros > Microsoft > Windows > AllJoyn" en la vista de carpetas y habilite el canal de depuración y el canal operativo. (vea un cuadro rojo en la siguiente captura de pantalla).
4. Reproduzca el problema que está experimentando con AllJoyn.
5. Haga clic en "Actualización" en la barra de la derecha "acciones", a continuación, compruebe los canales operativos y de depuración en la barra de navegación izquierdo debajo de la carpeta "AllJoyn".

![AJ_Troubleshooting_ETW](../media/AllJoyn/AJ_Troubleshooting_ETW.jpg)

Los seguimientos de ETW AllJoyn se dividen en particiones como sigue:

- Canal de depuración: Seguimientos detallados, no-error/informativo
- Canal operativo: Seguimientos de errores, errores son sólo de salida en el canal operativo

Con el fin de extraer información de las entradas ETW, puede hacer doble clic en una entrada en la vista de lista para un canal determinado y, a continuación, seleccione "Copiar" y, a continuación, en "Copiar detalles como texto". Si, a continuación, pegar el texto correspondiente en un editor de texto, tendrá los detalles, como en el ejemplo siguiente:


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


Esta información puede ayudar a localizar problemas de AllJoyn o ayudar a proporcionar detalles al notificar problemas a Microsoft o a otros asociados. Puede obtener más información acerca de [ETW seguimientos y el Visor de eventos en MSDN](https://msdn.microsoft.com/library/windows/desktop/bb968803.aspx).

### <a name="known-issues-and-limitations"></a>Problemas y limitaciones conocidos

Limitaciones de diseño para AllJoyn de Windows 10:

- El nodo de AllJoyn Router no es iniciado automáticamente por AllJoyn dispositivos o aplicaciones en la red cuando no hay aplicaciones se ejecutan en el equipo con Windows 10. El nodo de enrutador de Windows 10 se puede iniciar desde un símbolo del sistema con privilegios elevados o una sesión de Powershell ejecutando el comando "net start ajrouter".
- Aplicaciones AllJoyn UWP no pueden detectar ni interactuar con otras aplicaciones de AllJoyn UWP o aplicaciones de escritorio de AllJoyn que se ejecutan en el mismo equipo. Esta es una parte de la promesa de aislamiento de aplicación se implementa en Windows 10 para aplicaciones UWP. 
  - Si implementa una aplicación de AllJoyn UWP desde Visual Studio, el aislamiento de aplicación de aislamiento de aplicaciones se omite para esa aplicación (Esto se denomina una exención de bucle invertido""). Cada aplicación para UWP que se implemente desde Visual Studio podrá descubrir e interactuar con otras aplicaciones de escritorio y aplicaciones UWP de exención de bucle invertido, siempre y cuando esas aplicaciones usan anuncio/detección basada en sobre. Si está ejecutando Windows 10 IoT Core en "Modo incrustado", automáticamente se aplica esta excepción de bucle invertido, no es algo que deba configurar. Puede leer más sobre las excepciones de bucle invertido [en MSDN](https://msdn.microsoft.com/library/windows/apps/Hh780593.aspx).

