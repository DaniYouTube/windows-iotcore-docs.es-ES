---
title: Introducción al origen de ejemplo de respondedor de mDNS
ms.date: 02/26/2019
ms.topic: article
description: Obtenga información sobre cómo empezar a usar el origen de ejemplo de respondedor de mDNS.
keywords: Windows 10 IoT Core, origen de ejemplo de respondedor de mDNS
ms.openlocfilehash: ca99a217ade4c55c6d3050134af8d5663d8d1621
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917337"
---
# <a name="getting-started-with-mdns-responder-sample-source"></a>Introducción al origen de ejemplo de respondedor de mDNS

## <a name="getting-started"></a>Introducción

1.  Compile el elemento *mDNSResponder* del proyecto para obtener mDNSResponder.exe, que es un servicio. Copie el archivo .exe en el equipo de destino y, después, registre el servicio y ejecútelo.
2. Ejecute "mDNSResponder.exe /?" para imprimir el uso.
3.  Compile *dnssd* del proyecto, que generará el archivo dnssd.dll.
4.  Compile *mDNSUWP* del proyecto. Es un agente de UWP que se comunica con dnssd.dll y que generará sus propios archivos dll y winmd.
5.  Compile *mDNSTest* del proyecto, que es una aplicación para UWP de ejemplo para consumir mDNSUWP y que, en última instancia, se comunica con el servicio mDNSResponder.
6.  Esta aplicación para UWP depende de dnssd.dll y del agente de UWP (hay un script configurado para copiar todo el contenido en la carpeta appx de UWP).
7.  Implemente o inicie mDNSTest, establezca un identificador y haga clic en Registrar; el código de respuesta debe ser 0 (CORRECTO).
8.  Si ejecuta cualquier explorador Bonjour al mismo tiempo, debería aparecer el nuevo dispositivo (falso).

![Registro de mDNS](media/mDNS/mDNS1.png)

## <a name="resources"></a>Recursos

* Descargue [aquí](https://go.microsoft.com/fwlink/?linkid=2077676) el respondedor de mDNS compatible con Bonjour para Windows IoT (código fuente de ejemplo).

