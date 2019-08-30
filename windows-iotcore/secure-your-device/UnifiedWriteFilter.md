---
title: Usar el filtro de escritura unificado
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información acerca de cómo usar el filtro de escritura unificado para proteger los medios de almacenamiento físico de las escrituras de datos.
keywords: Windows IOT, filtro de escritura unificado, seguridad, memoria, medios de almacenamiento
ms.openlocfilehash: d1d6927fe19b5888ef0393d0b101065096cd9f63
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167562"
---
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="2ec55-104">Uso del filtro de escritura unificado (UWF) en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="2ec55-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="2ec55-105">El disco dinámico no es compatible con el UWF.</span><span class="sxs-lookup"><span data-stu-id="2ec55-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="2ec55-106">El filtro de escritura unificado (UWF) es una característica que protege los medios de almacenamiento físico de las escrituras de datos.</span><span class="sxs-lookup"><span data-stu-id="2ec55-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="2ec55-107">UWF intercepta todos los intentos de escritura en un volumen protegido y redirecciona dichos intentos a una superposición virtual.</span><span class="sxs-lookup"><span data-stu-id="2ec55-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="2ec55-108">Esto ayuda a mejorar la confiabilidad y la estabilidad del dispositivo y reduce el desgaste en medios sensibles a la escritura como las unidades de unidad de estado sólido de la memoria flash.</span><span class="sxs-lookup"><span data-stu-id="2ec55-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="2ec55-109">Lea nuestra documentación sobre el [filtro de escritura unificado](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="2ec55-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="2ec55-110">Instalación de UWF en un dispositivo que ejecuta Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="2ec55-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="2ec55-111">Si aún no tiene la versión actual de los kits de IoT Core de Windows 10, descargue e instale los [paquetes de Windows 10 IOT Core](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span><span class="sxs-lookup"><span data-stu-id="2ec55-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="2ec55-112">En función de la arquitectura del dispositivo, copie los `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` paquetes `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` de UWF (y)`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`del equipo () en el dispositivo (por ejemplo, con el [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md)).</span><span class="sxs-lookup"><span data-stu-id="2ec55-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="2ec55-113">Inicie [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/PowerShell.md) y acceda a su dispositivo con Windows 10 IOT Core.</span><span class="sxs-lookup"><span data-stu-id="2ec55-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="2ec55-114">Desde SSH o PowerShell, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2ec55-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="2ec55-115">Cambie al directorio en el que ha copiado los archivos</span><span class="sxs-lookup"><span data-stu-id="2ec55-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="2ec55-116">Ejecute estos comandos para instalar los paquetes en la imagen de sistema del dispositivo IoT:</span><span class="sxs-lookup"><span data-stu-id="2ec55-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="2ec55-117">El dispositivo arrancará en el sistema operativo de actualización, instalará las características de UWF y se reiniciará en los principales.</span><span class="sxs-lookup"><span data-stu-id="2ec55-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="2ec55-118">Una vez que el dispositivo vuelve a los principales, la característica UWF está lista y disponible para su uso.</span><span class="sxs-lookup"><span data-stu-id="2ec55-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="2ec55-119">Para comprobarlo, escriba ```uwfmgr.exe``` en la ventana de PowerShell o SSH.</span><span class="sxs-lookup"><span data-stu-id="2ec55-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![uwfmgr. exe en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="2ec55-121">Cómo incluir UWF en el FFU personalizado</span><span class="sxs-lookup"><span data-stu-id="2ec55-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="2ec55-122">Agregar el identificador de la característica **IOT_UNIFIED_WRITE_FILTER** al archivo de entrada OEM</span><span class="sxs-lookup"><span data-stu-id="2ec55-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="2ec55-123">Crear image\FFU.</span><span class="sxs-lookup"><span data-stu-id="2ec55-123">Create the image\FFU.</span></span> <span data-ttu-id="2ec55-124">Lea [creación de una imagen básica](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="2ec55-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="2ec55-125">Cómo usar UWF</span><span class="sxs-lookup"><span data-stu-id="2ec55-125">How to Use UWF</span></span>

<span data-ttu-id="2ec55-126">UWF se puede configurar mediante la herramienta uwfmgr. exe a través de una sesión de PowerShell o SSH.</span><span class="sxs-lookup"><span data-stu-id="2ec55-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="2ec55-127">Lea la herramienta para las opciones disponibles con una excepción de algunos comandos que se enumeran a continuación y que no se admiten en IOT Core. [ `uwfmgr.exe` ](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe)</span><span class="sxs-lookup"><span data-stu-id="2ec55-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="2ec55-128">Revise la configuración predeterminada de las configuraciones de superposición y adaptarlas según sus necesidades.</span><span class="sxs-lookup"><span data-stu-id="2ec55-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="2ec55-129">UWF también puede configurarse a través del canal de MDM mediante el [CSP de filtro de escritura unificado](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span><span class="sxs-lookup"><span data-stu-id="2ec55-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="2ec55-130">Por ejemplo, la siguiente combinación de comandos habilita uwfmgr y configure para proteger la unidad C</span><span class="sxs-lookup"><span data-stu-id="2ec55-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  <span data-ttu-id="2ec55-131">`uwfmgr.exe filter enable`Habilita el filtro de escritura</span><span class="sxs-lookup"><span data-stu-id="2ec55-131">`uwfmgr.exe filter enable`      Enables the write filter</span></span>
  <br>
  <span data-ttu-id="2ec55-132">`uwfmgr.exe volume protect c:`Protege el volumen C</span><span class="sxs-lookup"><span data-stu-id="2ec55-132">`uwfmgr.exe volume protect c:`  Protects the Volume C</span></span>
  <br>
  <span data-ttu-id="2ec55-133">`shutdown /r /t 0`Reinicia el dispositivo para que la configuración del filtro de escritura sea efectiva.</span><span class="sxs-lookup"><span data-stu-id="2ec55-133">`shutdown /r /t 0`              Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="2ec55-134">Es necesario *reiniciar* para que toda la configuración de uwfmgr sea efectiva.</span><span class="sxs-lookup"><span data-stu-id="2ec55-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="2ec55-135">Protección de un volumen de datos</span><span class="sxs-lookup"><span data-stu-id="2ec55-135">Protecting a Data Volume</span></span>

<span data-ttu-id="2ec55-136">El volumen de datos en IoT Core se puede proteger con el GUID del volumen.</span><span class="sxs-lookup"><span data-stu-id="2ec55-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="2ec55-137">El GUID de los volúmenes disponibles se puede encontrar con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="2ec55-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Proteger el volumen en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="2ec55-139">Exclusiones recomendadas</span><span class="sxs-lookup"><span data-stu-id="2ec55-139">Recommended Exclusions</span></span>
<span data-ttu-id="2ec55-140">Al proteger el volumen de datos, se recomienda agregar excepciones para las carpetas de mantenimiento y registro a las que tienen acceso los servicios de sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="2ec55-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="2ec55-141">Para agregar las exclusiones:`uwfmgr.exe file Add-Exclusion <file/folder name>`</span><span class="sxs-lookup"><span data-stu-id="2ec55-141">To add the exclusions: `uwfmgr.exe file Add-Exclusion <file/folder name>`</span></span>



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="2ec55-142">Mantenimiento de dispositivos protegidos de UWF</span><span class="sxs-lookup"><span data-stu-id="2ec55-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="2ec55-143">A partir de la versión 1709 de IOT Core de Windows 10, la versión 16299, el\) volumen del sistema operativo principal (C: se puede proteger con el UWF y con servicio *automáticamente* sin ningún paso especial).</span><span class="sxs-lookup"><span data-stu-id="2ec55-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="2ec55-144">Los siguientes pasos son necesarios para el servicio de los dispositivos protegidos de UWF con volúmenes de datos protegidos.</span><span class="sxs-lookup"><span data-stu-id="2ec55-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* <span data-ttu-id="2ec55-145">`uwfmgr.exe filter disable`Deshabilitar UWF</span><span class="sxs-lookup"><span data-stu-id="2ec55-145">`uwfmgr.exe filter disable` Disable UWF</span></span>
* <span data-ttu-id="2ec55-146">`shutdown /r /t 0`Reinicio del dispositivo para deshabilitar UWF</span><span class="sxs-lookup"><span data-stu-id="2ec55-146">`shutdown /r /t 0` Reboot device to disable UWF</span></span>
* <span data-ttu-id="2ec55-147">Habilitar el servicio (mediante el paquete de aprovisionamiento o MDM para establecer la Directiva de actualización)</span><span class="sxs-lookup"><span data-stu-id="2ec55-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="2ec55-148">Tenga en cuenta que el dispositivo se reiniciará automáticamente para realizar las actualizaciones de servicio.</span><span class="sxs-lookup"><span data-stu-id="2ec55-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* <span data-ttu-id="2ec55-149">`uwfmgr.exe filter enable`Habilitar UWF</span><span class="sxs-lookup"><span data-stu-id="2ec55-149">`uwfmgr.exe filter enable` Enable UWF</span></span>
* <span data-ttu-id="2ec55-150">`shutdown /r /t 0`Reiniciar el dispositivo para habilitar el UWF</span><span class="sxs-lookup"><span data-stu-id="2ec55-150">`shutdown /r /t 0` Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="2ec55-151">Comandos uwfmgr. exe no admitidos</span><span class="sxs-lookup"><span data-stu-id="2ec55-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="2ec55-152">El **modo de servicio de UWF** no es compatible con IOT Core.</span><span class="sxs-lookup"><span data-stu-id="2ec55-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

<span data-ttu-id="2ec55-153">`uwfmgr.exe`en Windows 10 IoT Core no es compatible con los comandos que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="2ec55-153">`uwfmgr.exe` on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
