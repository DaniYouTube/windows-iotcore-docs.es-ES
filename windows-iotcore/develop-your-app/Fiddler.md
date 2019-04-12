---
title: Capturar seguimientos de Fiddler
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar Fiddler para capturar seguimientos de Fiddler en Windows IoT Core.
keywords: seguimientos de Fiddler PuTTY, de Windows iot, Fiddler, seguimientos,
ms.openlocfilehash: b8bf4fa6390aad9640ad9139a8a164a9c83fcff5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514744"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>Capturar seguimientos de Fiddler en Windows IoT Core

Fiddler es una herramienta para depurar el tráfico web. Es especialmente útil porque puede personalizarlo para necesidades específicas mediante extensiones y complementos, y la herramienta proporciona mucha información útil específico para el tráfico web.

## <a name="assumptions"></a>Suposiciones 

* Tiene [PuTTY](http://www.putty.org/) en el cuadro de desarrollo o una alternativa de SSH
* Las instrucciones siguientes dan por hecho de una máquina virtual principal de IoT, pero funcionará en *cualquier* dispositivo de IoT Core

## <a name="initial-setup"></a>Instalación inicial

1. Descargue e instale la versión más reciente de [Fiddler](http://www.telerik.com/fiddler/) en el cuadro de desarrollo si todavía no
2. Inicie Fiddler y realice las siguientes actualizaciones de configuración en _Herramientas -> Opciones de Telerik Fiddler -> HTTPS_ ficha
    * Comprobar _Capture HTTPS CONNECTs_
    * Comprobar _descifrar tráfico HTTPS -> de todos los procesos_
    * Haga clic en el vínculo 'Certificados generan por' y seleccione _MakeCert motor_ (recomendación: Reiniciar Fiddler para que este cambio surta efecto)
    * A continuación, exporte el archivo FiddlerRoot.cer a través de _acciones -> Exportar certificado raíz para escritorio_
3. Realice las siguientes actualizaciones de configuración en _Herramientas -> Opciones de Telerik Fiddler -> conexiones_ pestaña:
    * Configurar Fiddler para que actúe como un proxy del sistema activando _permitir que los equipos remotos a Connect_
    * _Fiddler escucha en el puerto_ debe establecerse en _8888_
  
Nota: Debe reiniciar Fiddler después de esto y acepta cualquier solicitud de UAC.

## <a name="transfer-and-import-fiddler-root-certificate"></a>Transferir e importar el certificado raíz de Fiddler
Deberá importar el certificado de raíz de Fiddler para su dispositivo o una imagen de IoT con el fin de depurar el enrutamiento del tráfico https a través de su PC.  Para ello:

1. Monte el archivo de disco duro virtual (haga clic con el botón derecho en el disco duro virtual y elija _montar_) o conectarse al dispositivo de IoT mediante PuTTY (o cliente SSH alternativo)
2. Vaya a la partición mainOS y crear un _probar_ carpeta raíz (a través de SSH, use _md c:\test_)
3. Copiar FiddlerRoot.cer ha generado anteriormente (debe estar en el escritorio de forma predeterminada) en la ubicación de carpeta de prueba
4. Si usa un disco duro virtual, desmontarla por cualquiera de las unidades montadas expulsar y, a continuación, iniciar la máquina virtual principal de IoT a través de Hyper-v
5. Iniciar un [sesión SSH](../connect-your-device/ssh.md) e inicie sesión como administrador 
6. Navegue al directorio c:\test en la sesión SSH
7. Importar el certificado de raíz de Fiddler a través del comando:
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. Cerrar sesión SSH


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>Configuración de Proxy en la máquina virtual o el dispositivo de IoT Core
Los pasos siguientes permitirá a su dispositivo para enrutar el tráfico a través de su PC o IoT VM para que Fiddler puede capturar el tráfico de red para el análisis:

1. Determinar la dirección IP de la máquina de desarrollo mediante una consola CMD mediante _ipconfig_
2. Iniciar una nueva sesión SSH y esta vez, inicie sesión como defaultUser (nombre de usuario: _DefaultAccount_ Pwd: _[en blanco]_ )
3. Establecer al proxy a través de los siguientes comandos:
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

Si no se está ejecutando, inicie Fiddler en su PC, reinicie el dispositivo de la máquina virtual o IoT Core y ahora se debería enrutar el tráfico a través de Fiddler. 

Nota: Si ve CONNECT en Fiddler, pero ningún dato de https, el certificado era probable que no está instalado correctamente. Asegúrese de que no se haya olvidado el _transferencia y el certificado raíz de importación Fiddler_ pasos anteriores.

Adicionalmente, si desea activar al proxy tenga en cuenta que se almacene en caché las claves del registro anterior en un blob binario de otra clave de interrupción. por lo tanto, además de quitar las claves que acaba de agregar en el paso 3 anterior, también deben hacer:

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
