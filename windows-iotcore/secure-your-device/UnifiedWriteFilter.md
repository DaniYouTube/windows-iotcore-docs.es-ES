---
title: Con el filtro de escritura unificados
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar el filtro de escritura unificado para proteger los medios de almacenamiento físico de escrituras de datos.
keywords: seguridad de iot, Unified Write Filter, Windows, memoria, medios de almacenamiento
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515258"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>Usar el filtro de escritura unificados (UWF) en Windows 10 IoT Core

> [!WARNING]
> El disco dinámico no se admite para la UWF.

El filtro de escritura unificado (UWF) es una característica que protege los medios de almacenamiento físico de escrituras de datos. UWF intercepta todos los intentos de escritura en un volumen protegido y redirecciona dichos intentos a una superposición virtual. Esto ayuda a mejorar la confiabilidad y la estabilidad del dispositivo y reduce el desgaste en medios sensibles a la escritura como las unidades de unidad de estado sólido de la memoria flash.

Lea la documentación en el [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) para obtener más información.

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>Cómo instalar UWF en un dispositivo que ejecuta Windows 10 IoT Core

* Si aún no dispone de la versión actual de los Kits de Windows 10 IoT Core, descargue e instale el [los paquetes de Windows 10 IoT Core](https://www.microsoft.com/en-us/software-download/windows10iotcore).
* Según la arquitectura del dispositivo, copie los paquetes UWF ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` y `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) desde su PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) en el dispositivo (por ejemplo, con [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md)).
* Iniciar [SSH](../connect-your-device/SSH.md) o [Powershell](../connect-your-device/PowerShell.md) y tener acceso a un dispositivo que ejecuta Windows 10 IoT Core.
* Desde SSH o Powershell, realice lo siguiente:
  * Cambie al directorio donde ha copiado los archivos
    * `cd C:\<dir>`
  * Ejecute estos comandos para instalar los paquetes a la imagen de sistema del dispositivo de IoT:
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* El dispositivo de arranque del sistema operativo de la actualización, instalar las características UWF y para el MainOS reiniciar el equipo.
* Una vez que el dispositivo vuelve a la MainOS, la característica UWF está listo y disponible para su uso. Esto se puede comprobar escribiendo ```uwfmgr.exe``` en la ventana de Powershell o SSH.

  ![uwfmgr.exe en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>Cómo incluir UWF en su FFU personalizado 

* Agregar **IOT_UNIFIED_WRITE_FILTER** Id. de característica en el archivo de entrada de OEM 
* Cree el image\FFU. Lectura [crear una imagen básica](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para obtener instrucciones.


## <a name="how-to-use-uwf"></a>Cómo usar UWF

UWF puede configurarse mediante la herramienta uwfmgr.exe a través de una sesión de Powershell o SSH.
Lectura [ `uwfmgr.exe` herramienta](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) para las opciones disponibles con una excepción de algunos comandos enumerados a continuación y que no son compatibles con IoT Core.
Revise la configuración predeterminada de las configuraciones de superposición y adáptelos según sus requisitos.

También puede configurarse a través de canal MDM mediante UWF [unificada CSP filtro escribir](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).


* Por ejemplo, la siguiente combinación de comandos uwfmgr de habilitar y configurar para proteger la unidad c.

  `uwfmgr.exe filter enable`      Habilita el filtro de escritura
  <br>
  `uwfmgr.exe volume protect c:`  Protege el volumen C
  <br>
  `shutdown /r /t 0`              Se reinicia el dispositivo para que surta efecto la configuración de filtro de escritura

*Reiniciar* es necesario para que toda la configuración de uwfmgr surta efecto. 


## <a name="protecting-a-data-volume"></a>Protege un volumen de datos

Volumen de datos en IoT Core se puede proteger con el GUID para el volumen. Se puede encontrar el GUID para los volúmenes disponibles en el siguiente comando

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Protección de volúmenes en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>Exclusiones recomendadas
Al proteger el volumen de datos, le recomendamos que agregue excepciones para el mantenimiento y las carpetas de registros que se accede mediante servicios de sistema operativo Windows.

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

Para agregar las exclusiones: `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>Mantenimiento UWF proteger dispositivos

> [!Note]
> A partir de Windows 10 IoT Core versión 1709, versión 16299, el volumen del sistema operativo principal (C:\) pueden proteger con UWF y atiende *automáticamente* sin ningún paso especial.

Los siguientes pasos son necesarios para el servicio de dispositivos UWF protegido con volúmenes de datos protegidos.

* `uwfmgr.exe filter disable` Deshabilitar UWF
* `shutdown /r /t 0` Reinicie el dispositivo para deshabilitar UWF
* Habilitar el servicio (con el paquete de aprovisionamiento o MDM para establecer la directiva de actualización)
   * Tenga en cuenta que el dispositivo se reiniciará automáticamente para llevar a cabo el mantenimiento de actualizaciones
* `uwfmgr.exe filter enable` Habilitar UWF
* `shutdown /r /t 0` Reinicie el dispositivo para habilitar UWF

## <a name="unsupported-uwfmgrexe-commands"></a>Comandos uwfmgr.exe no admitido

**Modo de mantenimiento UWF** no se admite en IoT Core.

`uwfmgr.exe` en Windows 10 IoT Core no admite los comandos enumerados a continuación.

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
