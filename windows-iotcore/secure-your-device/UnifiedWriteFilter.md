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
# <a name="using-the-unified-write-filter-uwf-on-windows-10-iot-core"></a><span data-ttu-id="47107-104">Usar el filtro de escritura unificados (UWF) en Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="47107-104">Using the Unified Write Filter (UWF) on Windows 10 IoT Core</span></span>

> [!WARNING]
> <span data-ttu-id="47107-105">El disco dinámico no se admite para la UWF.</span><span class="sxs-lookup"><span data-stu-id="47107-105">The dynamic disk is not supported for the UWF.</span></span>

<span data-ttu-id="47107-106">El filtro de escritura unificado (UWF) es una característica que protege los medios de almacenamiento físico de escrituras de datos.</span><span class="sxs-lookup"><span data-stu-id="47107-106">The Unified Write Filter (UWF) is a feature that protects physical storage media from data writes.</span></span> <span data-ttu-id="47107-107">UWF intercepta todos los intentos de escritura en un volumen protegido y redirecciona dichos intentos a una superposición virtual.</span><span class="sxs-lookup"><span data-stu-id="47107-107">UWF intercepts all write attempts to a protected volume and redirects those write attempts to a virtual overlay.</span></span> <span data-ttu-id="47107-108">Esto ayuda a mejorar la confiabilidad y la estabilidad del dispositivo y reduce el desgaste en medios sensibles a la escritura como las unidades de unidad de estado sólido de la memoria flash.</span><span class="sxs-lookup"><span data-stu-id="47107-108">This improves the reliability and stability of your device and reduces the wear on write-sensitive media, such as flash memory media like solid-state drives.</span></span>

<span data-ttu-id="47107-109">Lea la documentación en el [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="47107-109">Read our documentation on the [Unified Write Filter](https://docs.microsoft.com/windows-hardware/customize/enterprise/unified-write-filter) for more information.</span></span>

## <a name="how-to-install-uwf-on-a-device-running-windows-10-iot-core"></a><span data-ttu-id="47107-110">Cómo instalar UWF en un dispositivo que ejecuta Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="47107-110">How to Install UWF on a device running Windows 10 IoT Core</span></span>

* <span data-ttu-id="47107-111">Si aún no dispone de la versión actual de los Kits de Windows 10 IoT Core, descargue e instale el [los paquetes de Windows 10 IoT Core](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span><span class="sxs-lookup"><span data-stu-id="47107-111">If you do not have the current version of the Windows 10 IoT Core Kits yet, download and install the [Windows 10 IoT Core Packages](https://www.microsoft.com/en-us/software-download/windows10iotcore).</span></span>
* <span data-ttu-id="47107-112">Según la arquitectura del dispositivo, copie los paquetes UWF ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` y `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) desde su PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) en el dispositivo (por ejemplo, con [uso compartido de archivos de Windows](../manage-your-device/WindowsFileSharing.md)).</span><span class="sxs-lookup"><span data-stu-id="47107-112">Based on your device architecture, copy UWF packages ( `Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab` and `Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab` ) from your PC (`C:\Program Files (x86)\Windows Kits\10\MSPackages\Retail\<arch>\fre\`) to the device (for example, with [Windows file sharing](../manage-your-device/WindowsFileSharing.md)).</span></span>
* <span data-ttu-id="47107-113">Iniciar [SSH](../connect-your-device/SSH.md) o [Powershell](../connect-your-device/PowerShell.md) y tener acceso a un dispositivo que ejecuta Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="47107-113">Launch [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/PowerShell.md) and access your device running Windows 10 IoT Core.</span></span>
* <span data-ttu-id="47107-114">Desde SSH o Powershell, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="47107-114">From SSH or Powershell, do the following:</span></span>
  * <span data-ttu-id="47107-115">Cambie al directorio donde ha copiado los archivos</span><span class="sxs-lookup"><span data-stu-id="47107-115">change to the directory where you have copied your files</span></span>
    * `cd C:\<dir>`
  * <span data-ttu-id="47107-116">Ejecute estos comandos para instalar los paquetes a la imagen de sistema del dispositivo de IoT:</span><span class="sxs-lookup"><span data-stu-id="47107-116">Run these commands to install the packages to your IoT device system image:</span></span>
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package.cab`
    * `applyupdate –stage .\Microsoft-IoTUAP-UnifiedWriteFilter-Package_Lang_en-us.cab`
    * `applyupdate –commit`
* <span data-ttu-id="47107-117">El dispositivo de arranque del sistema operativo de la actualización, instalar las características UWF y para el MainOS reiniciar el equipo.</span><span class="sxs-lookup"><span data-stu-id="47107-117">The device will boot to the Update OS, install UWF features, and reboot to the MainOS.</span></span>
* <span data-ttu-id="47107-118">Una vez que el dispositivo vuelve a la MainOS, la característica UWF está listo y disponible para su uso.</span><span class="sxs-lookup"><span data-stu-id="47107-118">Once the device comes back to the MainOS, the UWF feature is ready and available to use.</span></span> <span data-ttu-id="47107-119">Esto se puede comprobar escribiendo ```uwfmgr.exe``` en la ventana de Powershell o SSH.</span><span class="sxs-lookup"><span data-stu-id="47107-119">This can be verified by typing ```uwfmgr.exe``` into your Powershell or SSH window.</span></span>

  ![uwfmgr.exe en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr.png)


## <a name="how-to-include-uwf-in-your-custom-ffu"></a><span data-ttu-id="47107-121">Cómo incluir UWF en su FFU personalizado</span><span class="sxs-lookup"><span data-stu-id="47107-121">How to include UWF in Your Custom FFU</span></span> 

* <span data-ttu-id="47107-122">Agregar **IOT_UNIFIED_WRITE_FILTER** Id. de característica en el archivo de entrada de OEM</span><span class="sxs-lookup"><span data-stu-id="47107-122">Add **IOT_UNIFIED_WRITE_FILTER** feature id to the OEM Input file</span></span> 
* <span data-ttu-id="47107-123">Cree el image\FFU.</span><span class="sxs-lookup"><span data-stu-id="47107-123">Create the image\FFU.</span></span> <span data-ttu-id="47107-124">Lectura [crear una imagen básica](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="47107-124">Read [Create a basic image](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) for instructions.</span></span>


## <a name="how-to-use-uwf"></a><span data-ttu-id="47107-125">Cómo usar UWF</span><span class="sxs-lookup"><span data-stu-id="47107-125">How to Use UWF</span></span>

<span data-ttu-id="47107-126">UWF puede configurarse mediante la herramienta uwfmgr.exe a través de una sesión de Powershell o SSH.</span><span class="sxs-lookup"><span data-stu-id="47107-126">UWF can be configured using the uwfmgr.exe tool via a Powershell or SSH session.</span></span>
<span data-ttu-id="47107-127">Lectura [ `uwfmgr.exe` herramienta](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) para las opciones disponibles con una excepción de algunos comandos enumerados a continuación y que no son compatibles con IoT Core.</span><span class="sxs-lookup"><span data-stu-id="47107-127">Read [`uwfmgr.exe` tool](https://docs.microsoft.com/windows-hardware/customize/enterprise/uwfmgrexe) for the available options with an exception of some commands listed below that are not supported in IoT Core.</span></span>
<span data-ttu-id="47107-128">Revise la configuración predeterminada de las configuraciones de superposición y adáptelos según sus requisitos.</span><span class="sxs-lookup"><span data-stu-id="47107-128">Review the default settings of the Overlay configurations and adapt them per your requirements.</span></span>

<span data-ttu-id="47107-129">También puede configurarse a través de canal MDM mediante UWF [unificada CSP filtro escribir](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span><span class="sxs-lookup"><span data-stu-id="47107-129">UWF can also be configured via MDM channel using [Unified Write Filter CSP](https://docs.microsoft.com/windows/client-management/mdm/unifiedwritefilter-csp).</span></span>


* <span data-ttu-id="47107-130">Por ejemplo, la siguiente combinación de comandos uwfmgr de habilitar y configurar para proteger la unidad c.</span><span class="sxs-lookup"><span data-stu-id="47107-130">For example, the following combination of commands enable uwfmgr and configure to protect the C drive</span></span>

  `uwfmgr.exe filter enable`      <span data-ttu-id="47107-131">Habilita el filtro de escritura</span><span class="sxs-lookup"><span data-stu-id="47107-131">Enables the write filter</span></span>
  <br>
  `uwfmgr.exe volume protect c:`  <span data-ttu-id="47107-132">Protege el volumen C</span><span class="sxs-lookup"><span data-stu-id="47107-132">Protects the Volume C</span></span>
  <br>
  `shutdown /r /t 0`              <span data-ttu-id="47107-133">Se reinicia el dispositivo para que surta efecto la configuración de filtro de escritura</span><span class="sxs-lookup"><span data-stu-id="47107-133">Restarts the device to make the write filter settings effective</span></span>

<span data-ttu-id="47107-134">*Reiniciar* es necesario para que toda la configuración de uwfmgr surta efecto.</span><span class="sxs-lookup"><span data-stu-id="47107-134">*Reboot* is required to make all the uwfmgr settings effective.</span></span> 


## <a name="protecting-a-data-volume"></a><span data-ttu-id="47107-135">Protege un volumen de datos</span><span class="sxs-lookup"><span data-stu-id="47107-135">Protecting a Data Volume</span></span>

<span data-ttu-id="47107-136">Volumen de datos en IoT Core se puede proteger con el GUID para el volumen.</span><span class="sxs-lookup"><span data-stu-id="47107-136">Data volume in IoT Core can be protected using the GUID for the volume.</span></span> <span data-ttu-id="47107-137">Se puede encontrar el GUID para los volúmenes disponibles en el siguiente comando</span><span class="sxs-lookup"><span data-stu-id="47107-137">The GUID for the available volumes can be found through the following command</span></span>

  `dir /AL`
  <br>
  `uwfmgr.exe volume protect \\?\Volume {GUID}`


  ![Protección de volúmenes en Windows 10 IoT Core](../media/UnifiedWriteFilter/uwfmgr_protect.png)

### <a name="recommended-exclusions"></a><span data-ttu-id="47107-139">Exclusiones recomendadas</span><span class="sxs-lookup"><span data-stu-id="47107-139">Recommended Exclusions</span></span>
<span data-ttu-id="47107-140">Al proteger el volumen de datos, le recomendamos que agregue excepciones para el mantenimiento y las carpetas de registros que se accede mediante servicios de sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="47107-140">When protecting the data volume, we recommend that you add exceptions for the servicing and logging folders that are accessed by Windows OS Services.</span></span>

```
C:\Data\Users\System\AppData\Local\UpdateStagingRoot
C:\Data\SharedData\DuShared
C:\Data\SystemData\temp
C:\Data\users\defaultaccount\appdata\local\temp
C:\Data\Programdata\softwaredistribution
C:\Data\systemdata\nonetwlogs
```

<span data-ttu-id="47107-141">Para agregar las exclusiones:</span><span class="sxs-lookup"><span data-stu-id="47107-141">To add the exclusions:</span></span> `uwfmgr.exe file Add-Exclusion <file/folder name>`



## <a name="servicing-uwf-protected-devices"></a><span data-ttu-id="47107-142">Mantenimiento UWF proteger dispositivos</span><span class="sxs-lookup"><span data-stu-id="47107-142">Servicing UWF protected devices</span></span>

> [!Note]
> <span data-ttu-id="47107-143">A partir de Windows 10 IoT Core versión 1709, versión 16299, el volumen del sistema operativo principal (C:\) pueden proteger con UWF y atiende *automáticamente* sin ningún paso especial.</span><span class="sxs-lookup"><span data-stu-id="47107-143">Starting Windows 10 IoT Core Release 1709, version 16299, the main OS volume (C:\) can be protected with UWF and serviced *automatically* without any special steps.</span></span>

<span data-ttu-id="47107-144">Los siguientes pasos son necesarios para el servicio de dispositivos UWF protegido con volúmenes de datos protegidos.</span><span class="sxs-lookup"><span data-stu-id="47107-144">The following steps are required to service UWF protected devices with protected data volumes.</span></span>

* `uwfmgr.exe filter disable` <span data-ttu-id="47107-145">Deshabilitar UWF</span><span class="sxs-lookup"><span data-stu-id="47107-145">Disable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="47107-146">Reinicie el dispositivo para deshabilitar UWF</span><span class="sxs-lookup"><span data-stu-id="47107-146">Reboot device to disable UWF</span></span>
* <span data-ttu-id="47107-147">Habilitar el servicio (con el paquete de aprovisionamiento o MDM para establecer la directiva de actualización)</span><span class="sxs-lookup"><span data-stu-id="47107-147">Enable Servicing ( using provisioning package or MDM to set Update policy )</span></span>
   * <span data-ttu-id="47107-148">Tenga en cuenta que el dispositivo se reiniciará automáticamente para llevar a cabo el mantenimiento de actualizaciones</span><span class="sxs-lookup"><span data-stu-id="47107-148">Note that the device will automatically reboot to perform the servicing updates</span></span>
* `uwfmgr.exe filter enable` <span data-ttu-id="47107-149">Habilitar UWF</span><span class="sxs-lookup"><span data-stu-id="47107-149">Enable UWF</span></span>
* `shutdown /r /t 0` <span data-ttu-id="47107-150">Reinicie el dispositivo para habilitar UWF</span><span class="sxs-lookup"><span data-stu-id="47107-150">Reboot device to enable UWF</span></span>

## <a name="unsupported-uwfmgrexe-commands"></a><span data-ttu-id="47107-151">Comandos uwfmgr.exe no admitido</span><span class="sxs-lookup"><span data-stu-id="47107-151">Unsupported uwfmgr.exe Commands</span></span>

<span data-ttu-id="47107-152">**Modo de mantenimiento UWF** no se admite en IoT Core.</span><span class="sxs-lookup"><span data-stu-id="47107-152">**UWF Servicing Mode** is not supported in IoT Core.</span></span>

`uwfmgr.exe` <span data-ttu-id="47107-153">en Windows 10 IoT Core no admite los comandos enumerados a continuación.</span><span class="sxs-lookup"><span data-stu-id="47107-153">on Windows 10 IoT Core does not support commands listed below.</span></span>

```
Filter 
    Shutdown 
    Restart 
Servicing 
    Enable 
    Disable 
    Update-Windows
```
