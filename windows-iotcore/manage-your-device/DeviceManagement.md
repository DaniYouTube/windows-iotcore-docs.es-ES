---
title: Administración de dispositivos Windows IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las distintas formas de administrar dispositivos de Windows 10 IoT Core.
keywords: Windows IOT, administración de dispositivos, Windows IOT, Azure DM, centro de Azure, Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170920"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="01d4e-104">Administración de dispositivos Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="01d4e-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="01d4e-105">Los dispositivos de Windows 10 IoT Core pueden administrarse mediante un servidor MDM DM DM tradicional que admita la inscripción basada en certificados o el uso de la administración de dispositivos de Azure IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="01d4e-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 <span data-ttu-id="01d4e-106">_[Aquí](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)encontrará más información sobre MDM y Windows 10._</span><span class="sxs-lookup"><span data-stu-id="01d4e-106">_Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)._</span></span>  

<span data-ttu-id="01d4e-107">En el caso de los dispositivos que se administran mediante un servidor OMA DM, las directivas MDM para Windows 10 IoT Core se alinean con las directivas admitidas en otras ediciones de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="01d4e-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="01d4e-108">Para más información sobre las directivas, así como sobre lo que se puede administrar en los dispositivos IoT Core, consulte referencia del proveedor de servicios de configuración para Windows 10 [aquí](https://aka.ms/csplist).</span><span class="sxs-lookup"><span data-stu-id="01d4e-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="01d4e-109">La compatibilidad de MDM en Windows 10 se basa en la especificación del Protocolo de administración de dispositivos (DM) de Open Mobile Alliance (OMA).</span><span class="sxs-lookup"><span data-stu-id="01d4e-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="01d4e-110">Cómo inscribir un dispositivo IoT Core en una MDM</span><span class="sxs-lookup"><span data-stu-id="01d4e-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="01d4e-111">La inscripción de MDM de un dispositivo de IoT Core se realiza mediante un paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="01d4e-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="01d4e-112">Los paquetes de aprovisionamiento se pueden crear mediante el diseñador y la configuración de imágenes de Windows (WICD).</span><span class="sxs-lookup"><span data-stu-id="01d4e-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="01d4e-113">Vamos a intentar inscribir un dispositivo en una MDM.</span><span class="sxs-lookup"><span data-stu-id="01d4e-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="01d4e-114">Creación de un paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="01d4e-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="01d4e-115">Microsoft System Center Configuration Manager (independiente o SCCM + Intune híbrido)</span><span class="sxs-lookup"><span data-stu-id="01d4e-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="01d4e-116">Abra la consola de administración de Configuration Manager (consola de ConfigMgr)</span><span class="sxs-lookup"><span data-stu-id="01d4e-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="01d4e-117">Vaya a _activos y compatibilidad > configuración de cumplimiento > acceso a recursos de la empresa >_ 
   ![perfiles de certificado perfiles de certificado](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="01d4e-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="01d4e-118">Haga clic en **crear Perfil de certificado** .</span><span class="sxs-lookup"><span data-stu-id="01d4e-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="01d4e-119">Proporcionar un nombre y una descripción para el perfil</span><span class="sxs-lookup"><span data-stu-id="01d4e-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="01d4e-120">Nombre: Ejemplo de Configuration Manager certificado raíz de confianza</span><span class="sxs-lookup"><span data-stu-id="01d4e-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="01d4e-121">Tipo de Perfil de certificado: Certificado de CA de confianza</span><span class="sxs-lookup"><span data-stu-id="01d4e-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![Certificación de confianza](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="01d4e-123">Haga clic en **Next**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-123">Click **Next**.</span></span>

6. <span data-ttu-id="01d4e-124">Importe el archivo de certificado.</span><span class="sxs-lookup"><span data-stu-id="01d4e-124">Import the certificate file.</span></span>

7. <span data-ttu-id="01d4e-125">Seleccione **almacén de certificados del equipo-raíz** para el **almacén de destino**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="01d4e-126">Haga clic en **Next**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-126">Click **Next**.</span></span>

9. <span data-ttu-id="01d4e-127">Elegir **seleccionar todo** para plataformas compatibles ![plataformas admitidas](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="01d4e-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="01d4e-128">Haga clic en **Resumen, siguiente y cerrar** para salir del asistente.</span><span class="sxs-lookup"><span data-stu-id="01d4e-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="01d4e-129">Haga clic con el botón derecho en el perfil que acaba de crear y haga clic en **exportar**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="01d4e-130">Haga clic en **examinar**, busque una ubicación donde se debe exportar el archivo. ppkg y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="01d4e-131">Haga clic en **exportar** y en **Aceptar** para salir del asistente.</span><span class="sxs-lookup"><span data-stu-id="01d4e-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="01d4e-132">Otros servidores MDM</span><span class="sxs-lookup"><span data-stu-id="01d4e-132">Other MDM Servers</span></span>

1. <span data-ttu-id="01d4e-133">Descargue e instale [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span><span class="sxs-lookup"><span data-stu-id="01d4e-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="01d4e-134">Abra el diseñador de imágenes y configuraciones de Windows (WICD).</span><span class="sxs-lookup"><span data-stu-id="01d4e-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   <span data-ttu-id="01d4e-135">![Diseñador de imágenes y configuraciones de Windows](../media/ManagingDevices/WICD-Start-Page.png)</span><span class="sxs-lookup"><span data-stu-id="01d4e-135">![Windows Imaging and Configuration Designer](../media/ManagingDevices/WICD-Start-Page.png)</span></span>

3. <span data-ttu-id="01d4e-136">Elección del **aprovisionamiento avanzado**</span><span class="sxs-lookup"><span data-stu-id="01d4e-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="01d4e-137">Establezca un nombre para el paquete.</span><span class="sxs-lookup"><span data-stu-id="01d4e-137">Set a name for your package.</span></span>

5. <span data-ttu-id="01d4e-138">Elija la configuración común para Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="01d4e-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="01d4e-139">Omitir el paso importar paquete.</span><span class="sxs-lookup"><span data-stu-id="01d4e-139">Skip the Import Package step.</span></span>
   <span data-ttu-id="01d4e-140">![WICD-New-](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   Project-details![wicd-New-Project](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   -Editions![wicd-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)</span><span class="sxs-lookup"><span data-stu-id="01d4e-140">![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)</span></span>

7. <span data-ttu-id="01d4e-141">Vaya a Workplace-> inscripciones.</span><span class="sxs-lookup"><span data-stu-id="01d4e-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="01d4e-142">En el campo UPN, escriba la cuenta en la que desea inscribir el dispositivo (es trmck@contoso.codecir,) y haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![Inscripciones de área de trabajo llenas](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="01d4e-144">Para AuthPolicy, elija entre el nombre de usuario autenticación basada en contraseña (local) o la autenticación basada en certificados.</span><span class="sxs-lookup"><span data-stu-id="01d4e-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="01d4e-145">Escriba la dirección URL del servicio de detección para el servidor MDM.</span><span class="sxs-lookup"><span data-stu-id="01d4e-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="01d4e-146">La dirección URL del servicio de inscripción y la dirección URL del servicio de directivas son opcionales.</span><span class="sxs-lookup"><span data-stu-id="01d4e-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="01d4e-147">Para el secreto, escriba</span><span class="sxs-lookup"><span data-stu-id="01d4e-147">For the Secret enter</span></span>  
    - <span data-ttu-id="01d4e-148">OnPremises La contraseña de la cuenta con la que está realizando la inscripción.</span><span class="sxs-lookup"><span data-stu-id="01d4e-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="01d4e-149">Certificado La huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="01d4e-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![En su entorno local](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="01d4e-151">En la parte superior de la ventana de WICD, haga clic en **exportar > paquete de aprovisionamiento**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="01d4e-152">Proporcione un nombre y una versión para el paquete y haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="01d4e-153">Asegúrese de incrementar el número de versión para asegurarse de que se ejecuta un paquete actualizado.</span><span class="sxs-lookup"><span data-stu-id="01d4e-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="01d4e-154">Haga clic en **siguiente** en la **página Detalles de seguridad**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="01d4e-155">Elija la ubicación donde se exportará el paquete en el equipo local y haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="01d4e-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="01d4e-156">Haga clic en **generar** y, a continuación, en **Finalizar** para salir del asistente.</span><span class="sxs-lookup"><span data-stu-id="01d4e-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="01d4e-157">Instalación del paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="01d4e-157">Installing the Provisioning package</span></span>

<span data-ttu-id="01d4e-158">Hay varias maneras en las que se puede implementar un paquete de aprovisionamiento en un dispositivo IoT.</span><span class="sxs-lookup"><span data-stu-id="01d4e-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="01d4e-159">Es posible implementar un paquete copiando el paquete en el dispositivo o agregando el paquete a la imagen durante el proceso de creación de imágenes.</span><span class="sxs-lookup"><span data-stu-id="01d4e-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="01d4e-160">Copiando el paquete en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="01d4e-160">Copying package to device</span></span>

<span data-ttu-id="01d4e-161">Tome el paquete de aprovisionamiento que se exportó desde SCCM o wicd y copie el archivo. ppkg `C:\Windows\Provisioning\Packages` en el directorio del dispositivo iot.</span><span class="sxs-lookup"><span data-stu-id="01d4e-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="01d4e-162">Tras reiniciar el dispositivo, se ejecutará el paquete y el dispositivo iniciará el proceso de inscripción.</span><span class="sxs-lookup"><span data-stu-id="01d4e-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="01d4e-163">Agregando paquete a la imagen</span><span class="sxs-lookup"><span data-stu-id="01d4e-163">Adding package to image</span></span>

<span data-ttu-id="01d4e-164">Consulte [Agregar un paquete de aprovisionamiento a una imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span><span class="sxs-lookup"><span data-stu-id="01d4e-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="01d4e-165">Al iniciarse por primera vez, el dispositivo ejecutará el paquete e iniciará el proceso de inscripción.</span><span class="sxs-lookup"><span data-stu-id="01d4e-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
