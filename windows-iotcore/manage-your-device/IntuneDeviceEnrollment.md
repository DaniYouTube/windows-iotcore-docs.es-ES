---
title: Inscripción de dispositivos de IoT Core de Windows en Intune
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos con administración de dispositivos de Microsoft Intune y Windows IoT.
keywords: Windows iot, IoT de Azure, administración de dispositivos de Intune, administración de dispositivos
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277812"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="e3a53-104">Inscripción de dispositivos de Windows IoT Core en Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="e3a53-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="e3a53-105">Su empresa puede administrar dispositivos de IoT Core junto con todos los demás dispositivos administrados.</span><span class="sxs-lookup"><span data-stu-id="e3a53-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="e3a53-106">Esto le ofrece una manera coherente para administrar IoT Core, IoT empresarial y otros dispositivos de Windows con Intune.</span><span class="sxs-lookup"><span data-stu-id="e3a53-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="e3a53-107">¿Cómo se puede inscribir un dispositivo de IoT Core en Intune?</span><span class="sxs-lookup"><span data-stu-id="e3a53-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="e3a53-108">Inscripción de Intune de un dispositivo de IoT Core se logra mediante el panel de Windows IoT Core para preparar el dispositivo y, a continuación, mediante el Diseñador de configuración de Windows para crear un paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="e3a53-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="e3a53-109">Cambiar el ámbito de usuario de MDM de Intune en Azure AD</span><span class="sxs-lookup"><span data-stu-id="e3a53-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="e3a53-110">Inicie sesión en el [portal Azure](https://portal.azure.com)y, a continuación, seleccione **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="e3a53-111">Seleccione **movilidad (MDM y MAM)** .</span><span class="sxs-lookup"><span data-stu-id="e3a53-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![Selección de movilidad y Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="e3a53-113">Seleccione **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="e3a53-114">En el **configurar Microsoft Intune** página, junto a **el ámbito de usuario MDM**, seleccione **todas**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="e3a53-115">Esto permitirá que su IoT Core usuario del dispositivo se inscriba en Intune después de unirse a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e3a53-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="e3a53-116">Crear una tarjeta SD de programa de instalación para el dispositivo de IoT Core</span><span class="sxs-lookup"><span data-stu-id="e3a53-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="e3a53-117">Inserte una tarjeta microSD en el lector de tarjeta en su PC.</span><span class="sxs-lookup"><span data-stu-id="e3a53-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e3a53-118">La tarjeta microSD se formateará durante este proceso, por lo que se eliminarán todos los datos de la tarjeta.</span><span class="sxs-lookup"><span data-stu-id="e3a53-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="e3a53-119">Vaya a [Windows IoT Core panel](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) para descargar e instalar el panel.</span><span class="sxs-lookup"><span data-stu-id="e3a53-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="e3a53-120">Una vez instalado el panel, ábrala y seleccione **configurar un nuevo dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Panel de Windows IoT Core](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="e3a53-122">Escriba un **nombre de dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="e3a53-123">Escriba una nueva contraseña de administrador.</span><span class="sxs-lookup"><span data-stu-id="e3a53-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="e3a53-124">Si desea habilitar Wi-Fi para el dispositivo, seleccione el **conexión de red Wi-Fi** casilla de verificación.</span><span class="sxs-lookup"><span data-stu-id="e3a53-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="e3a53-125">Omita este paso si el dispositivo usará sólo una conexión de red ethernet.</span><span class="sxs-lookup"><span data-stu-id="e3a53-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![Casilla de verificación de Wi-Fi en el panel de IoT](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="e3a53-127">Seleccione el **acepto los términos de licencia del software** casilla de verificación y, a continuación, seleccione **descargue e instale**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="e3a53-128">Cuando aparezca el mensaje de confirmación, seleccione la opción de **formato** la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="e3a53-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e3a53-129">Esté atento a la **formato** mensaje de confirmación durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="e3a53-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="e3a53-130">El mensaje podría estar oculto por otra aplicación abierto, pero es importante seleccionar la opción de formato.</span><span class="sxs-lookup"><span data-stu-id="e3a53-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="e3a53-131">Si la unidad no tiene el formato correcto, se producirá un error de arranque.</span><span class="sxs-lookup"><span data-stu-id="e3a53-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="e3a53-132">El mensaje **tarjeta SD Your está lista** aparece.</span><span class="sxs-lookup"><span data-stu-id="e3a53-132">The message **Your SD card is ready** appears.</span></span>

     ![Mensaje listo de la tarjeta SD](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="e3a53-134">Minimizar esta página.</span><span class="sxs-lookup"><span data-stu-id="e3a53-134">Minimize this page.</span></span>  <span data-ttu-id="e3a53-135">Deberá volver a él más adelante.</span><span class="sxs-lookup"><span data-stu-id="e3a53-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="e3a53-136">Crear un paquete de aprovisionamiento para la inscripción de Intune</span><span class="sxs-lookup"><span data-stu-id="e3a53-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="e3a53-137">Instale la aplicación de diseño de la configuración de Windows siguiendo los pasos descritos en [instalar Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span><span class="sxs-lookup"><span data-stu-id="e3a53-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="e3a53-138">Abra el **creación de imágenes de Windows y el Diseñador de configuración**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="e3a53-139">Elija **aprovisionar dispositivos de escritorio** para crear un proyecto.</span><span class="sxs-lookup"><span data-stu-id="e3a53-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![Elección de servicios de escritorio de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="e3a53-141">Escriba el **Project Details** como se desee.</span><span class="sxs-lookup"><span data-stu-id="e3a53-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="e3a53-142">A continuación, seleccione **finalizar**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="e3a53-143">Vaya a la **administración de cuentas** página y seleccione **inscribir en Azure AD**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e3a53-144">Instalación de la aplicación desde la Microsoft Store o el Windows Assessment y Deployment Kit (ADK) está bien.</span><span class="sxs-lookup"><span data-stu-id="e3a53-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![Elegir inscribir en Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="e3a53-146">Junto a **expiración del Token masiva**, escriba una fecha de expiración del token de forma masiva.</span><span class="sxs-lookup"><span data-stu-id="e3a53-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="e3a53-147">Seleccione **Get Bulk Token**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="e3a53-148">Aparece un mensaje de inicio de sesión para conectarse a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e3a53-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Página de inicio de sesión de AD Azure](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="e3a53-150">Escriba el nombre de usuario del inquilino (por ejemplo, john@mycompany.onmicrosoft.com) y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="e3a53-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="e3a53-151">Acepta que la aplicación de diseño de la configuración de Windows tener acceso a la información de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e3a53-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="e3a53-152">Un mensaje en la página se muestra que el token de AAD de forma masiva se capturó correctamente.</span><span class="sxs-lookup"><span data-stu-id="e3a53-152">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![Mensaje correcta del token de forma masiva](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="e3a53-154">Seleccione **cambie al editor avanzado**y, a continuación, seleccione *Sí*.</span><span class="sxs-lookup"><span data-stu-id="e3a53-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![Cambie a la página de confirmación del editor avanzado](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="e3a53-156">En **personalizaciones seleccionadas**, deje el **cuenta** configuración, quitar, pero las demás opciones:</span><span class="sxs-lookup"><span data-stu-id="e3a53-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="e3a53-157">Seleccione **OOBE**y, a continuación, seleccione **quitar**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="e3a53-158">Si **SharedPC** está en la lista, selecciónelo y, a continuación, seleccione **quitar**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![Eliminación de las personalizaciones](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="e3a53-160">Seleccione **exportar**y, a continuación, elija **paquete de aprovisionamiento**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![Elegir el paquete de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="e3a53-162">En la página siguiente, acepte la configuración predeterminada y seleccione **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="e3a53-163">De nuevo, en la página siguiente, acepte la configuración predeterminada y seleccione siguiente.</span><span class="sxs-lookup"><span data-stu-id="e3a53-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="e3a53-164">Cambiar el **paquete de aprovisionamiento** destino o dejar la ruta de acceso predeterminada y, a continuación, seleccione **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="e3a53-165">Seleccione **compilar**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-165">Select **Build**.</span></span>
20. <span data-ttu-id="e3a53-166">Seleccione el **ubicación de salida** vincular para que puedan encontrar el archivo .ppkg cuando esté listo.</span><span class="sxs-lookup"><span data-stu-id="e3a53-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![Vínculos de la ubicación de salida](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="e3a53-168">Seleccione **finalizar**.</span><span class="sxs-lookup"><span data-stu-id="e3a53-168">Select **Finish**.</span></span>
22. <span data-ttu-id="e3a53-169">Vaya al explorador de archivos y copie el paquete de aprovisionamiento en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e3a53-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="e3a53-170">Guárdelo en la tarjeta microSD en la **MainOS** unidad en la **c:\windows\provisioning\packages** carpeta.</span><span class="sxs-lookup"><span data-stu-id="e3a53-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="e3a53-171">Debe conceder permisos para guardar el archivo en esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="e3a53-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="e3a53-172">Aprovisione e inscribir el dispositivo de IoT Core en Intune</span><span class="sxs-lookup"><span data-stu-id="e3a53-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="e3a53-173">Inserte la tarjeta microSD en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e3a53-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="e3a53-174">Encienda el dispositivo de IoT Core y deje tiempo para que pueda iniciarse y muestra la pantalla estándar.</span><span class="sxs-lookup"><span data-stu-id="e3a53-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="e3a53-175">Volver a la consola de Microsoft Intune en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="e3a53-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="e3a53-176">El dispositivo debe aparecer en la lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e3a53-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e3a53-177">La inscripción puede tardar 15 minutos o más en completarse.</span><span class="sxs-lookup"><span data-stu-id="e3a53-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Lista de dispositivos de Intune](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="e3a53-179">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="e3a53-179">Next steps</span></span>

- <span data-ttu-id="e3a53-180">[Consulte los detalles del dispositivo en Intune](https://docs.microsoft.com/intune/device-inventory).</span><span class="sxs-lookup"><span data-stu-id="e3a53-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="e3a53-181">[Sincronizar el dispositivo para obtener las últimas directivas y acciones con Intune](https://docs.microsoft.com/intune/device-sync).</span><span class="sxs-lookup"><span data-stu-id="e3a53-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="e3a53-182">[Reiniciar de forma remota el dispositivo con Intune](https://docs.microsoft.com/intune/device-restart).</span><span class="sxs-lookup"><span data-stu-id="e3a53-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
