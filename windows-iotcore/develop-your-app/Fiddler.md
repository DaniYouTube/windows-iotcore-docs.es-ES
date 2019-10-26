---
title: Capturar seguimientos de Fiddler
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar Fiddler para capturar seguimientos de Fiddler en Windows IoT Core.
keywords: Windows IOT, Fiddler, seguimientos, PuTTy, seguimientos de Fiddler
ms.openlocfilehash: 0539365ed4727866d816ad129cef0e904f22b1df
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918254"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>Captura de seguimientos de Fiddler en Windows IoT Core

Fiddler es una herramienta para depurar el tráfico web. Es especialmente útil porque se puede personalizar para las necesidades específicas mediante extensiones y complementos, y la herramienta proporciona una gran cantidad de información útil específica para el tráfico web.

## <a name="assumptions"></a>Suposiciones 

* Tiene [Putty](http://www.putty.org/) en el cuadro de desarrollador o una alternativa para ssh
* Las instrucciones siguientes suponen la suposición de una máquina virtual de IoT Core, pero funcionarán en *cualquier* dispositivo de IOT Core.

## <a name="initial-setup"></a>Configuración inicial

1. Descargue e instale la versión más reciente de [Fiddler](http://www.telerik.com/fiddler/) en el cuadro de desarrollador si todavía no lo ha hecho.
2. Inicie Fiddler y realice las siguientes actualizaciones de configuración en _herramientas-> Telerik Fiddler Options-> pestaña https_ .
    * Comprobar la _captura de conexiones https_
    * Comprobar _el descifrado del tráfico https: > de todos los procesos_
    * Haga clic en el vínculo "certificados generados por" y seleccione el _motor Makecert_ (recomendación: reiniciar Fiddler para que este cambio surta efecto)
    * A continuación, exporte el archivo FiddlerRoot. cer a través _de Actions-> exportar el certificado raíz al escritorio_ .
3. Realice las siguientes actualizaciones de configuración en _herramientas-> opciones de Telerik Fiddler: pestaña > conexiones_ :
    * Configure Fiddler para que actúe como proxy del sistema; para ello, active la casilla _permitir que los equipos remotos se conecten_
    * _Fiddler escucha en el puerto_ debe establecerse en _8888_
  
Nota: debe reiniciar Fiddler después de este y aceptar cualquier solicitud de UAC.

## <a name="transfer-and-import-fiddler-root-certificate"></a>Transferencia e importación de un certificado raíz de Fiddler
Debe importar el certificado raíz de Fiddler en la imagen o el dispositivo de IoT para depurar el enrutamiento de tráfico HTTPS a través de su equipo.  Para ello:

1. Monte el archivo VHD (haga clic con el botón derecho en el disco duro virtual y elija _montar_) o conéctese a su dispositivo de IOT mediante Putty (o cliente SSH alternativo).
2. Vaya a la partición principal de y cree una carpeta de _prueba_ en la raíz (a través de SSH, use _MD c:\test_).
3. Copie FiddlerRoot. cer que generó anteriormente (debe estar en el escritorio de forma predeterminada) en la ubicación de la carpeta de prueba.
4. Si usa un disco duro virtual, desmonte los discos montados y, a continuación, inicie la máquina virtual de IoT Core a través de HyperV.
5. Inicio de una [sesión de ssh](../connect-your-device/ssh.md) e inicio de sesión como administrador 
6. Navegue al directorio c:\test en la sesión de SSH.
7. Importar certificado raíz de Fiddler mediante el comando:
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. Cerrar sesión SSH


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>Configuración del proxy en la máquina virtual o en un dispositivo de IoT Core
Los pasos siguientes permitirán que la máquina virtual o el dispositivo de IoT enruten el tráfico a través de su equipo para que Fiddler pueda capturar el tráfico de red para el análisis:

1. Determinar la dirección IP de la máquina de desarrollo mediante una consola CMD mediante _ipconfig_
2. Inicie una nueva sesión de SSH y esta vez, inicie sesión como defaultUser (nombredeusuario: _DefaultAccount_ PWD: _[Blank]_ )
3. Establezca el proxy mediante los siguientes comandos:
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

Si aún no se está ejecutando, inicie Fiddler en el equipo, reinicie la máquina virtual o el dispositivo de IoT Core y el tráfico ahora debe enrutarse a través de Fiddler. 

Nota: Si ve https CONNECT en Fiddler pero no tiene datos, es probable que el certificado no se haya instalado correctamente. Asegúrese de que no perdió los pasos de la _transferencia e importación del certificado raíz de Fiddler_ anterior.

Adicionalmente, si desea volver a desactivar el proxy, tenga en cuenta que las claves de registro anteriores se almacenan en caché en un BLOB binario en otra clave. por lo tanto, además de quitar las claves que se acaban de agregar en el paso 3 anterior, también debe hacer lo siguiente:

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
