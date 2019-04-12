---
title: Inscripción de dispositivos de IoT Core de Windows en Intune
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos con administración de dispositivos de Microsoft Intune y Windows IoT.
keywords: Windows iot, IoT de Azure, administración de dispositivos de Intune, administración de dispositivos
ms.openlocfilehash: 5d75c64813a3e61f60630abd87185949b63e178b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514280"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="5d825-104">Inscripción de dispositivos de Windows IoT Core en Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="5d825-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="5d825-105">Su empresa puede administrar dispositivos de IoT Core junto con todos los demás dispositivos administrados.</span><span class="sxs-lookup"><span data-stu-id="5d825-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="5d825-106">Esto le ofrece una manera coherente para administrar IoT Core, IoT empresarial y otros dispositivos de Windows con Intune.</span><span class="sxs-lookup"><span data-stu-id="5d825-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="5d825-107">¿Cómo se puede inscribir un dispositivo de IoT Core en Intune?</span><span class="sxs-lookup"><span data-stu-id="5d825-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="5d825-108">Inscripción de Intune de un dispositivo de IoT Core se logra mediante el panel de Windows IoT Core para preparar el dispositivo y, a continuación, mediante el Diseñador de configuración de Windows para crear un paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="5d825-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="5d825-109">Cambiar el ámbito de usuario de MDM de Intune en Azure AD</span><span class="sxs-lookup"><span data-stu-id="5d825-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="5d825-110">Inicie sesión en el [portal Azure](https://portal.azure.com)y, a continuación, seleccione **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="5d825-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="5d825-111">Seleccione **movilidad (MDM y MAM)**.</span><span class="sxs-lookup"><span data-stu-id="5d825-111">Select **Mobility (MDM and MAM)**.</span></span>


~~~
 ![Selecting Mobility and Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)
~~~
1. <span data-ttu-id="5d825-112">Seleccione **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="5d825-112">Select **Microsoft Intune**.</span></span> <span data-ttu-id="5d825-113">En el **configurar Microsoft Intune** página, junto a **el ámbito de usuario MDM**, seleccione **todas**.</span><span class="sxs-lookup"><span data-stu-id="5d825-113">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="5d825-114">Esto permitirá que su IoT Core usuario del dispositivo se inscriba en Intune después de unirse a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5d825-114">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="5d825-115">Crear una tarjeta SD de programa de instalación para el dispositivo de IoT Core</span><span class="sxs-lookup"><span data-stu-id="5d825-115">Create a setup SD card for the IoT Core device</span></span>
1. <span data-ttu-id="5d825-116">Inserte una tarjeta microSD en el lector de tarjeta en su PC.</span><span class="sxs-lookup"><span data-stu-id="5d825-116">Insert a microSD card into the card reader on your PC.</span></span> 
     > [!NOTE]
     > <span data-ttu-id="5d825-117">La tarjeta microSD se formateará durante este proceso, por lo que se eliminarán todos los datos de la tarjeta.</span><span class="sxs-lookup"><span data-stu-id="5d825-117">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="5d825-118">Vaya a [Windows IoT Core panel](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) para descargar e instalar el panel.</span><span class="sxs-lookup"><span data-stu-id="5d825-118">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="5d825-119">Una vez instalado el panel, ábrala y seleccione **configurar un nuevo dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="5d825-119">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Panel de Windows IoT Core](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="5d825-121">Escriba un **nombre de dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="5d825-121">Type a **Device name**.</span></span>
5. <span data-ttu-id="5d825-122">Escriba una nueva contraseña de administrador.</span><span class="sxs-lookup"><span data-stu-id="5d825-122">Enter a new administrator password.</span></span> 
6. <span data-ttu-id="5d825-123">Si desea habilitar Wi-Fi para el dispositivo, seleccione el **conexión de red Wi-Fi** casilla de verificación.</span><span class="sxs-lookup"><span data-stu-id="5d825-123">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="5d825-124">Omita este paso si el dispositivo usará sólo una conexión de red ethernet.</span><span class="sxs-lookup"><span data-stu-id="5d825-124">Skip this if the device will use an ethernet network connection only.</span></span>

     ![Casilla de verificación de Wi-Fi en el panel de IoT](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="5d825-126">Seleccione el **acepto los términos de licencia del software** casilla de verificación y, a continuación, seleccione **descargue e instale**.</span><span class="sxs-lookup"><span data-stu-id="5d825-126">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="5d825-127">Cuando aparezca el mensaje de confirmación, seleccione la opción de **formato** la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="5d825-127">When the confirmation message appears, select the option to **Format** the SD Card.</span></span> 
     > [!NOTE]
     > <span data-ttu-id="5d825-128">Esté atento a la **formato** mensaje de confirmación durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="5d825-128">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="5d825-129">El mensaje podría estar oculto por otra aplicación abierto, pero es importante seleccionar la opción de formato.</span><span class="sxs-lookup"><span data-stu-id="5d825-129">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="5d825-130">Si la unidad no tiene el formato correcto, se producirá un error de arranque.</span><span class="sxs-lookup"><span data-stu-id="5d825-130">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="5d825-131">El mensaje **tarjeta SD Your está lista** aparece.</span><span class="sxs-lookup"><span data-stu-id="5d825-131">The message **Your SD card is ready** appears.</span></span>

     ![Mensaje listo de la tarjeta SD](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="5d825-133">Minimizar esta página.</span><span class="sxs-lookup"><span data-stu-id="5d825-133">Minimize this page.</span></span>  <span data-ttu-id="5d825-134">Deberá volver a él más adelante.</span><span class="sxs-lookup"><span data-stu-id="5d825-134">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="5d825-135">Crear un paquete de aprovisionamiento para la inscripción de Intune</span><span class="sxs-lookup"><span data-stu-id="5d825-135">Create a provisioning package for Intune enrollment</span></span>
1. <span data-ttu-id="5d825-136">Instale la aplicación de diseño de la configuración de Windows siguiendo los pasos descritos en [instalar Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span><span class="sxs-lookup"><span data-stu-id="5d825-136">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="5d825-137">Abra el **creación de imágenes de Windows y el Diseñador de configuración**.</span><span class="sxs-lookup"><span data-stu-id="5d825-137">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="5d825-138">Elija **aprovisionar dispositivos de escritorio** para crear un proyecto</span><span class="sxs-lookup"><span data-stu-id="5d825-138">Choose **Provision desktop devices** to create a project</span></span> 

     ![Elección de servicios de escritorio de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="5d825-140">Escriba el **Project Details** como se desee.</span><span class="sxs-lookup"><span data-stu-id="5d825-140">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="5d825-141">A continuación, seleccione **finalizar**.</span><span class="sxs-lookup"><span data-stu-id="5d825-141">Then select **Finish**.</span></span>
5. <span data-ttu-id="5d825-142">Vaya a la **administración de cuentas** página y seleccione **inscribir en Azure AD**.</span><span class="sxs-lookup"><span data-stu-id="5d825-142">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
      > [!NOTE]
     > <span data-ttu-id="5d825-143">Instalación de la aplicación desde la Microsoft Store o el Windows Assessment y Deployment Kit (ADK) está bien.</span><span class="sxs-lookup"><span data-stu-id="5d825-143">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![Elegir inscribir en Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="5d825-145">Junto a **expiración del Token masiva**, escriba una fecha de expiración del token de forma masiva.</span><span class="sxs-lookup"><span data-stu-id="5d825-145">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="5d825-146">Seleccione **Get Bulk Token**.</span><span class="sxs-lookup"><span data-stu-id="5d825-146">Select **Get Bulk Token**.</span></span> <span data-ttu-id="5d825-147">Aparece un mensaje de inicio de sesión para conectarse a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5d825-147">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Página de inicio de sesión de AD Azure](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="5d825-149">Escriba el nombre de usuario del inquilino (por ejemplo, john@mycompany.onmicrosoft.com) y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="5d825-149">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>   
9. <span data-ttu-id="5d825-150">Acepta que la aplicación de diseño de la configuración de Windows tener acceso a la información de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5d825-150">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span> 
10. <span data-ttu-id="5d825-151">Un mensaje en la página se muestra que el token de AAD de forma masiva se capturó correctamente.</span><span class="sxs-lookup"><span data-stu-id="5d825-151">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![Mensaje correcta del token de forma masiva](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="5d825-153">Seleccione **cambie al editor avanzado**y, a continuación, seleccione *Sí*.</span><span class="sxs-lookup"><span data-stu-id="5d825-153">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![Cambie a la página de confirmación del editor avanzado](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="5d825-155">En **personalizaciones seleccionadas**, deje el **cuenta** configuración, quitar, pero las demás opciones:</span><span class="sxs-lookup"><span data-stu-id="5d825-155">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="5d825-156">Seleccione **OOBE**y, a continuación, seleccione **quitar**.</span><span class="sxs-lookup"><span data-stu-id="5d825-156">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="5d825-157">Si **SharedPC** está en la lista, selecciónelo y, a continuación, seleccione **quitar**.</span><span class="sxs-lookup"><span data-stu-id="5d825-157">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![Eliminación de las personalizaciones](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="5d825-159">Seleccione **exportar**y, a continuación, elija **paquete de aprovisionamiento**.</span><span class="sxs-lookup"><span data-stu-id="5d825-159">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![Elegir el paquete de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="5d825-161">En la página siguiente, acepte la configuración predeterminada y seleccione **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="5d825-161">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="5d825-162">De nuevo, en la página siguiente, acepte la configuración predeterminada y seleccione siguiente.</span><span class="sxs-lookup"><span data-stu-id="5d825-162">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="5d825-163">Cambiar el **paquete de aprovisionamiento** destino o dejar la ruta de acceso predeterminada y, a continuación, seleccione **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="5d825-163">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="5d825-164">Seleccione **compilar**.</span><span class="sxs-lookup"><span data-stu-id="5d825-164">Select **Build**.</span></span>
20. <span data-ttu-id="5d825-165">Seleccione el **ubicación de salida** vincular para que puedan encontrar el archivo .ppkg cuando esté listo.</span><span class="sxs-lookup"><span data-stu-id="5d825-165">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![Vínculos de la ubicación de salida](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="5d825-167">Seleccione **finalizar**.</span><span class="sxs-lookup"><span data-stu-id="5d825-167">Select **Finish**.</span></span>
22. <span data-ttu-id="5d825-168">Vaya al explorador de archivos y copie el paquete de aprovisionamiento en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5d825-168">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="5d825-169">Guárdelo en la tarjeta microSD en la **MainOS** unidad en la **c:\windows\provisioning\packages** carpeta.</span><span class="sxs-lookup"><span data-stu-id="5d825-169">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="5d825-170">Debe conceder permisos para guardar el archivo en esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="5d825-170">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="5d825-171">Aprovisione e inscribir el dispositivo de IoT Core en Intune</span><span class="sxs-lookup"><span data-stu-id="5d825-171">Provision and enroll the IoT Core device in Intune</span></span>
1. <span data-ttu-id="5d825-172">Inserte la tarjeta microSD en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="5d825-172">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="5d825-173">Encienda el dispositivo de IoT Core y deje tiempo para que pueda iniciarse y muestra la pantalla estándar.</span><span class="sxs-lookup"><span data-stu-id="5d825-173">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span> 
3. <span data-ttu-id="5d825-174">Volver a la consola de Microsoft Intune en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="5d825-174">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="5d825-175">El dispositivo debe aparecer en la lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5d825-175">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="5d825-176">La inscripción puede tardar 15 minutos o más en completarse.</span><span class="sxs-lookup"><span data-stu-id="5d825-176">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Lista de dispositivos de Intune](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="5d825-178">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="5d825-178">Next steps</span></span>
- <span data-ttu-id="5d825-179">[Consulte los detalles del dispositivo en Intune](https://docs.microsoft.com/intune/device-inventory).</span><span class="sxs-lookup"><span data-stu-id="5d825-179">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="5d825-180">[Sincronizar el dispositivo para obtener las últimas directivas y acciones con Intune](https://docs.microsoft.com/intune/device-sync).</span><span class="sxs-lookup"><span data-stu-id="5d825-180">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="5d825-181">[Reiniciar de forma remota el dispositivo con Intune](https://docs.microsoft.com/intune/device-restart).</span><span class="sxs-lookup"><span data-stu-id="5d825-181">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
