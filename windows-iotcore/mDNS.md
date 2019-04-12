---
title: Empezar a trabajar con el origen del ejemplo de servicio de respuesta de MDN
author: saraclay
ms.author: saclayt
ms.date: 02/26/2019
ms.topic: article
description: Obtenga información sobre cómo empezar a trabajar con el origen del ejemplo de servicio de respuesta de MDN.
keywords: Windows 10 IoT Core, origen de ejemplo de servicio de respuesta de MDN
ms.openlocfilehash: eacd22bf4d8a93948706e214fd48262c61c59a08
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514240"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a>Introducción a origen de ejemplo de servicio de respuesta de MDN

## <a name="getting-started"></a>Introducción

1.  Compile el proyecto *mDNSResponder* a mDNSResponder.exe get, que es un servicio. Copie el archivo .exe en el equipo de destino, a continuación, registrar el servicio y ejecute.
2. Run “mDNSResponder.exe /?” Para imprimir el uso
3.  Compile el proyecto *dnssd*, generaría dnssd.dll
4.  Compile el proyecto *mDNSUWP*. Es un agente de UWP que se comunica con dnssd.dll y generará su propio archivo dll y winmd
5.  Compile el proyecto *mDNSTest*, que es un ejemplo de aplicación para UWP para consumir mDNSUWP y finalmente se habla en el servicio mDNSResponder.
6.  Esta aplicación para UWP depende dnssd.dll y el agente UWP (no hay secuencias de comandos configurada para copiar todo el contenido en la carpeta appx UWP)
7.  Implementar inicio/mDNSTest, establecer un identificador y haga clic en Register, el código de respuesta debe ser 0 (correcto)
8.  Si ejecuta cualquier explorador Bonjour al mismo tiempo, debe aparecer el nuevo dispositivo (falso).

![En el registro para MDN](media/mDNS/mDNS1.png)

## <a name="resources"></a>Recursos

* Descargue los MDN Bonjour compatible con servicio de respuesta para Windows IoT (origen del ejemplo) [aquí](https://go.microsoft.com/fwlink/?linkid=2077676).

