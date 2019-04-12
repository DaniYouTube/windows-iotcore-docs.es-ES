---
title: Administración de dispositivos de Windows IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las diferentes maneras de administrar dispositivos Windows 10 IoT Core.
keywords: Windows iot, administración de dispositivos, windows iot, Azure DM, Hub de Azure, Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514956"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="68db7-104">Administración de dispositivos de Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="68db7-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="68db7-105">Dispositivos Windows 10 IoT Core pueden administrarse mediante un servidor OMA DM MDM tradicional que admite la inscripción basada en certificados o con la administración de dispositivos del centro de IoT de Azure.</span><span class="sxs-lookup"><span data-stu-id="68db7-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 _<span data-ttu-id="68db7-106">Obtener más información acerca de MDM y Windows 10 [aquí](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="68db7-106">Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx).</span></span>_  

<span data-ttu-id="68db7-107">Para los dispositivos que se administran mediante un servidor OMA DM las directivas de MDM para Windows 10 IoT Core se alinean con las directivas que se admiten en otras ediciones de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="68db7-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="68db7-108">Para obtener más información sobre directivas, así como lo que pueden administrarse en dispositivos de IoT Core, vea la referencia del proveedor de servicio de configuración para Windows 10 [aquí](https://aka.ms/csplist).</span><span class="sxs-lookup"><span data-stu-id="68db7-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="68db7-109">La compatibilidad MDM en Windows 10 se basa en la especificación del protocolo 1.2.1 de administración de dispositivos de Open Mobile Alliance (OMA) (DM).</span><span class="sxs-lookup"><span data-stu-id="68db7-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="68db7-110">¿Cómo se puede inscribir un dispositivo de IoT Core en un MDM?</span><span class="sxs-lookup"><span data-stu-id="68db7-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="68db7-111">Inscripción de MDM de un dispositivo de IoT Core se logra mediante un paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="68db7-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="68db7-112">Paquetes de aprovisionamiento pueden crearse mediante la configuración de imagen de Windows y el diseñador (WICD).</span><span class="sxs-lookup"><span data-stu-id="68db7-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="68db7-113">Vamos a intentar inscribir un dispositivo en un MDM.</span><span class="sxs-lookup"><span data-stu-id="68db7-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="68db7-114">Creación de un paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="68db7-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="68db7-115">Microsoft System Center Configuration Manager (independiente o Intune + SCCM híbrido)</span><span class="sxs-lookup"><span data-stu-id="68db7-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="68db7-116">Abra la consola de administración de Configuration Manager (consola de Configuration Manager)</span><span class="sxs-lookup"><span data-stu-id="68db7-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="68db7-117">Vaya a _activos y compatibilidad > configuración de cumplimiento > acceso a los recursos de la compañía > perfiles de certificado_
   ![perfiles de certificado](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="68db7-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="68db7-118">Haga clic en **Crear perfil de certificado**</span><span class="sxs-lookup"><span data-stu-id="68db7-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="68db7-119">Proporcione un nombre y una descripción para el perfil</span><span class="sxs-lookup"><span data-stu-id="68db7-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="68db7-120">Nombre: Certificado raíz de confianza de ejemplo de Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="68db7-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="68db7-121">Tipo de perfil de certificado: Certificado de CA de confianza</span><span class="sxs-lookup"><span data-stu-id="68db7-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![Certificación de confianza](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="68db7-123">Haz clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="68db7-123">Click **Next**.</span></span>

6. <span data-ttu-id="68db7-124">Importe el archivo de certificado.</span><span class="sxs-lookup"><span data-stu-id="68db7-124">Import the certificate file.</span></span>

7. <span data-ttu-id="68db7-125">Seleccione **almacén de certificados de equipo - raíz** para el **Store de destino**.</span><span class="sxs-lookup"><span data-stu-id="68db7-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="68db7-126">Haz clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="68db7-126">Click **Next**.</span></span>

9. <span data-ttu-id="68db7-127">Elija **seleccionar todo** para plataformas admitidas ![plataformas compatibles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="68db7-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="68db7-128">Haga clic en **resumen, Next y cerrar** para salir del asistente.</span><span class="sxs-lookup"><span data-stu-id="68db7-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="68db7-129">Haga doble clic en el perfil que acaba de crear y haga clic en **exportar**.</span><span class="sxs-lookup"><span data-stu-id="68db7-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="68db7-130">Haga clic en **examinar**, encontrar una ubicación donde se debe exportar el archivo .ppkg y, a continuación, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="68db7-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="68db7-131">Haga clic en **exportar** y haga clic en **Aceptar** para salir del asistente.</span><span class="sxs-lookup"><span data-stu-id="68db7-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="68db7-132">Otros servidores MDM</span><span class="sxs-lookup"><span data-stu-id="68db7-132">Other MDM Servers</span></span>

1. <span data-ttu-id="68db7-133">Descargue e instale el [Windows Assessment and Deployment Kit (ADK de Windows)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span><span class="sxs-lookup"><span data-stu-id="68db7-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="68db7-134">Abra el Diseñador de configuración (WICD) y creación de imágenes de Windows.</span><span class="sxs-lookup"><span data-stu-id="68db7-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   ![Diseñador de imágenes y configuraciones de Windows](../media/ManagingDevices/WICD-Start-Page.png)

3. <span data-ttu-id="68db7-136">Elija **avanzada de aprovisionamiento**</span><span class="sxs-lookup"><span data-stu-id="68db7-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="68db7-137">Establecer un nombre para el paquete.</span><span class="sxs-lookup"><span data-stu-id="68db7-137">Set a name for your package.</span></span>

5. <span data-ttu-id="68db7-138">Elija la configuración de Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="68db7-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="68db7-139">Omitir el paso del paquete de importación.</span><span class="sxs-lookup"><span data-stu-id="68db7-139">Skip the Import Package step.</span></span>
   ![<span data-ttu-id="68db7-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import</span><span class="sxs-lookup"><span data-stu-id="68db7-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import</span></span>](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. <span data-ttu-id="68db7-141">Vaya al área de trabajo -> inscripciones.</span><span class="sxs-lookup"><span data-stu-id="68db7-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="68db7-142">En el campo UPN, especifique la cuenta que desea inscribir un dispositivo bajo (es decir, trmck@contoso.co) y haga clic en **agregar**.</span><span class="sxs-lookup"><span data-stu-id="68db7-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![Rellenado de inscripciones de área de trabajo](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="68db7-144">Para AuthPolicy elija entre usuario y contraseña en función de autenticación (OnPremises) o autenticación basada en certificados.</span><span class="sxs-lookup"><span data-stu-id="68db7-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="68db7-145">Escriba la dirección URL de servicio de detección para el servidor MDM.</span><span class="sxs-lookup"><span data-stu-id="68db7-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="68db7-146">Dirección URL del servicio de inscripción y la dirección URL del servicio de directiva son opcionales.</span><span class="sxs-lookup"><span data-stu-id="68db7-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="68db7-147">Para el secreto ENTRAR</span><span class="sxs-lookup"><span data-stu-id="68db7-147">For the Secret enter</span></span>  
    - <span data-ttu-id="68db7-148">OnPremises: La contraseña de la cuenta que se va a inscribir</span><span class="sxs-lookup"><span data-stu-id="68db7-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="68db7-149">Certificado: La huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="68db7-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![Relleno OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="68db7-151">Haga clic en la parte superior de la ventana WICD **Exportar > paquete de aprovisionamiento**.</span><span class="sxs-lookup"><span data-stu-id="68db7-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="68db7-152">Proporcione un nombre y la versión para el paquete y haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="68db7-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="68db7-153">Asegúrese de incrementar el número de versión para asegurarse de que se ejecuta un paquete actualizado.</span><span class="sxs-lookup"><span data-stu-id="68db7-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="68db7-154">Haga clic en **siguiente** en el **página de detalles de seguridad**.</span><span class="sxs-lookup"><span data-stu-id="68db7-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="68db7-155">Elija la ubicación donde se pueda exportar en el equipo local y haga clic en el paquete **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="68db7-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="68db7-156">Haga clic en **compilar** y, a continuación, **finalizar** para salir del asistente.</span><span class="sxs-lookup"><span data-stu-id="68db7-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="68db7-157">Instalar el paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="68db7-157">Installing the Provisioning package</span></span>

<span data-ttu-id="68db7-158">Hay varias maneras en que se puede implementar un paquete de aprovisionamiento en un dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="68db7-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="68db7-159">Es posible implementar un paquete copiando el paquete en el dispositivo o agregando el paquete a la imagen durante el proceso de creación de imágenes.</span><span class="sxs-lookup"><span data-stu-id="68db7-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="68db7-160">Copiar el paquete al dispositivo</span><span class="sxs-lookup"><span data-stu-id="68db7-160">Copying package to device</span></span>

<span data-ttu-id="68db7-161">Tomar el paquete de aprovisionamiento que se haya exportado desde SCCM o WICD y copie el archivo .ppkg `C:\Windows\Provisioning\Packages` directorio en el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="68db7-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="68db7-162">Tras reiniciar el dispositivo se ejecutará el paquete y el dispositivo iniciará el proceso de inscripción.</span><span class="sxs-lookup"><span data-stu-id="68db7-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="68db7-163">Agregar paquete de imagen</span><span class="sxs-lookup"><span data-stu-id="68db7-163">Adding package to image</span></span>

<span data-ttu-id="68db7-164">Consulte [agregar un paquete de aprovisionamiento a una imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span><span class="sxs-lookup"><span data-stu-id="68db7-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="68db7-165">Tras el primer arranque el dispositivo se ejecute el paquete e iniciar el proceso de inscripción.</span><span class="sxs-lookup"><span data-stu-id="68db7-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
