---
title: Usar el filtro de escritura unificado
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo usar el filtro de escritura unificado para proteger los medios de almacenamiento físico de las escrituras de datos.
keywords: Windows IOT, filtro de escritura unificado, seguridad, memoria, medios de almacenamiento
ms.openlocfilehash: 7c8632cf12d391d458861ef22e2c3a9fc77a3a08
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918680"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a>Uso del filtro de escritura unificado (UWF) en Windows 10 IoT Core

> [!WARNING]
> El disco dinámico no es compatible con el UWF.

El filtro de escritura unificado (UWF) es una característica que protege los medios de almacenamiento físico de las escrituras de datos. UWF intercepta todos los intentos de escritura en un volumen protegido y redirecciona dichos intentos a una superposición virtual. Esto ayuda a mejorar la confiabilidad y la estabilidad del dispositivo y reduce el desgaste en medios sensibles a la escritura como las unidades de unidad de estado sólido de la memoria flash.

Lea nuestra documentación sobre el [filtro de escritura unificado](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) para obtener más información.

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a>Instalación de UWF en un dispositivo que ejecuta Windows 10 IoT Core

* Si aún no tiene la versión actual de los kits de IoT Core de Windows 10, descargue e instale los [paquetes de Windows 10 IOT Core](https://www.microsoft.com/en-us/software-download/windows10iotcore).
* En función de la arquitectura del dispositivo, copie los paquetes de UWF (`Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` y `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`) del equipo (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) en el dispositivo (por ejemplo, con el [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md)).
* Inicie [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) y acceda a su dispositivo con Windows 10 IOT Core.
* Desde SSH o PowerShell, haga lo siguiente:
  * Cambie al directorio en el que ha copiado los archivos
    * `cd C:\<dir>`
  * Ejecute estos comandos para instalar los paquetes en la imagen de sistema del dispositivo IoT:
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* El dispositivo arrancará en el sistema operativo de actualización, instalará las características de UWF y se reiniciará en los principales.
* Una vez que el dispositivo vuelve a los principales, la característica UWF está lista y disponible para su uso. Para comprobarlo, escriba ```uwfmgr.exe``` en la ventana de PowerShell o SSH.

  ![uwfmgr. exe en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a>Cómo incluir UWF en el FFU personalizado 

* Agregar el identificador de la característica **IOT_UNIFIED_WRITE_FILTER** al archivo de entrada OEM 
* Crear image\FFU. Lea [creación de una imagen básica](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para obtener instrucciones.


## <a name="how-to-use-uwf"></a>Cómo usar UWF

UWF se puede configurar mediante la herramienta uwfmgr. exe a través de una sesión de PowerShell o SSH.
Lea [`uwfmgr.exe` herramienta](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) para las opciones disponibles con una excepción de algunos comandos que se enumeran a continuación y que no se admiten en IOT Core.
Revise la configuración predeterminada de las configuraciones de superposición y adaptarlas según sus necesidades.

UWF también puede configurarse a través del canal de MDM mediante el [CSP de filtro de escritura unificado](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).


* Por ejemplo, la siguiente combinación de comandos habilita uwfmgr y configure para proteger la unidad C

  `uwfmgr.exe filter enable` habilita el filtro de escritura
  <br>
  `uwfmgr.exe volume protect c:` protege el volumen C
  <br>
  `shutdown /r /t 0` reinicia el dispositivo para que la configuración del filtro de escritura sea efectiva

Es necesario *reiniciar* para que toda la configuración de uwfmgr sea efectiva. 


## <a name="protecting-a-data-volume"></a>Protección de un volumen de datos

El volumen de datos en IoT Core se puede proteger con el GUID del volumen. El GUID de los volúmenes disponibles se puede encontrar con el siguiente comando:

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Proteger el volumen en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a>Exclusiones recomendadas
Al proteger el volumen de datos, se recomienda agregar excepciones para las carpetas de mantenimiento y registro a las que tienen acceso los servicios de sistema operativo Windows.

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

Para agregar las exclusiones: `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a>Mantenimiento de dispositivos protegidos de UWF

> [!Note]
> A partir de la versión 1709 de IoT Core de Windows 10, versión 16299, el volumen principal del sistema operativo (C:\) se puede proteger con el UWF y con servicio *automáticamente* sin ningún paso especial.

Los siguientes pasos son necesarios para el servicio de los dispositivos protegidos de UWF con volúmenes de datos protegidos.

* `uwfmgr.exe filter disable` deshabilitar UWF
* `shutdown /r /t 0` reiniciar el dispositivo para deshabilitar el UWF
* Habilitar el servicio (mediante el paquete de aprovisionamiento o MDM para establecer la Directiva de actualización)
   * Tenga en cuenta que el dispositivo se reiniciará automáticamente para realizar las actualizaciones de servicio.
* `uwfmgr.exe filter enable` habilitar UWF
* `shutdown /r /t 0` reiniciar el dispositivo para habilitar el UWF

## <a name="unsupported-uwfmgrexe-commands"></a>Comandos uwfmgr. exe no admitidos

El **modo de servicio de UWF** no es compatible con IOT Core.

`uwfmgr.exe` en Windows 10 IoT Core no es compatible con los comandos que se enumeran a continuación.

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
