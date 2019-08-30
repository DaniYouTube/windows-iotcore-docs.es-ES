---
title: Inscripción de dispositivos Windows IoT Core en Intune
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos mediante Microsoft Intune la administración de dispositivos y Windows IoT.
keywords: Windows IOT, Azure IoT, administración de dispositivos de Intune, administración de dispositivos
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277812"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="8e563-104">Inscripción de dispositivos Windows IoT Core en Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="8e563-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="8e563-105">Su empresa puede administrar dispositivos IoT Core junto con todos los demás dispositivos administrados.</span><span class="sxs-lookup"><span data-stu-id="8e563-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="8e563-106">Esto le ofrece una manera coherente de administrar IoT Core, IoT Enterprise y otros dispositivos Windows con Intune.</span><span class="sxs-lookup"><span data-stu-id="8e563-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="8e563-107">Cómo inscribir un dispositivo IoT Core en Intune</span><span class="sxs-lookup"><span data-stu-id="8e563-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="8e563-108">La inscripción de Intune de un dispositivo de IoT Core se realiza mediante el panel de Windows IoT Core para preparar el dispositivo y, a continuación, mediante el diseñador de configuración de Windows para crear un paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="8e563-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="8e563-109">Cambiar el ámbito de usuario de MDM de Intune en Azure AD</span><span class="sxs-lookup"><span data-stu-id="8e563-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="8e563-110">Inicie sesión en el [Azure portal](https://portal.azure.com)y, a continuación, seleccione **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="8e563-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="8e563-111">Seleccione **movilidad (MDM y MAM)** .</span><span class="sxs-lookup"><span data-stu-id="8e563-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![Selección de movilidad y Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="8e563-113">Seleccione **Microsoft Intune**.</span><span class="sxs-lookup"><span data-stu-id="8e563-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="8e563-114">En la página **configurar Microsoft Intune** , junto a **ámbito de usuario de MDM**, seleccione **todo**.</span><span class="sxs-lookup"><span data-stu-id="8e563-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="8e563-115">Esto permitirá que el usuario del dispositivo de IoT Core se inscriba en Intune después de unirse Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8e563-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="8e563-116">Creación de una tarjeta SD de instalación para el dispositivo IoT Core</span><span class="sxs-lookup"><span data-stu-id="8e563-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="8e563-117">Inserte una tarjeta de microSD en el lector de tarjetas del equipo.</span><span class="sxs-lookup"><span data-stu-id="8e563-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="8e563-118">Durante este proceso se formateará la tarjeta microSD, por lo que se eliminarán todos los datos de la tarjeta.</span><span class="sxs-lookup"><span data-stu-id="8e563-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="8e563-119">Vaya al [Panel de Windows IOT Core](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) para descargar e instalar el panel.</span><span class="sxs-lookup"><span data-stu-id="8e563-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="8e563-120">Una vez instalado el panel, ábralo y seleccione **configurar un nuevo dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="8e563-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Panel de Windows IoT Core](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="8e563-122">Escriba un **nombre de dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="8e563-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="8e563-123">Escriba una nueva contraseña de administrador.</span><span class="sxs-lookup"><span data-stu-id="8e563-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="8e563-124">Si desea habilitar Wi-Fi para el dispositivo, seleccione la casilla **conexión de red Wi-Fi** .</span><span class="sxs-lookup"><span data-stu-id="8e563-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="8e563-125">Omitir esta información si el dispositivo va a usar solo una conexión de red Ethernet.</span><span class="sxs-lookup"><span data-stu-id="8e563-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![Casilla Wi-Fi en el panel de IoT](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="8e563-127">Active la casilla acepto **los términos de licencia de software** y, a continuación, seleccione **Descargar e instalar**.</span><span class="sxs-lookup"><span data-stu-id="8e563-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="8e563-128">Cuando aparezca el mensaje de confirmación, seleccione la opción para **dar formato** a la tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="8e563-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="8e563-129">Vea el mensaje de confirmación de **formato** durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="8e563-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="8e563-130">El mensaje puede estar oculto por otra aplicación abierta, pero es importante seleccionar la opción Format.</span><span class="sxs-lookup"><span data-stu-id="8e563-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="8e563-131">Si la unidad no tiene el formato correcto, se producirá un error de arranque.</span><span class="sxs-lookup"><span data-stu-id="8e563-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="8e563-132">Aparece el mensaje **la tarjeta SD está lista** .</span><span class="sxs-lookup"><span data-stu-id="8e563-132">The message **Your SD card is ready** appears.</span></span>

     ![Mensaje listo para tarjeta SD](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="8e563-134">Minimice esta página.</span><span class="sxs-lookup"><span data-stu-id="8e563-134">Minimize this page.</span></span>  <span data-ttu-id="8e563-135">Volverá a ella más adelante.</span><span class="sxs-lookup"><span data-stu-id="8e563-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="8e563-136">Creación de un paquete de aprovisionamiento para la inscripción de Intune</span><span class="sxs-lookup"><span data-stu-id="8e563-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="8e563-137">Instale la aplicación de diseño de configuración de Windows siguiendo los pasos descritos en [instalar el diseñador de configuración de Windows](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span><span class="sxs-lookup"><span data-stu-id="8e563-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="8e563-138">Abra el **Diseñador de imágenes y configuraciones de Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e563-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="8e563-139">Elija **aprovisionar dispositivos de escritorio** para crear un proyecto.</span><span class="sxs-lookup"><span data-stu-id="8e563-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![Elección del aprovisionamiento de servicios de escritorio](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="8e563-141">Escriba los **detalles del proyecto** como desee.</span><span class="sxs-lookup"><span data-stu-id="8e563-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="8e563-142">Después, seleccione **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="8e563-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="8e563-143">Vaya a la página de **Administración de cuentas** y seleccione **inscribirse en Azure ad**.</span><span class="sxs-lookup"><span data-stu-id="8e563-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="8e563-144">La instalación de la aplicación desde el Microsoft Store o Windows Assessment and Deployment Kit (ADK) es correcta.</span><span class="sxs-lookup"><span data-stu-id="8e563-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![Elección de la inscripción en Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="8e563-146">Junto a expiración de tokens en **masa**, especifique una fecha de expiración de tokens en masa.</span><span class="sxs-lookup"><span data-stu-id="8e563-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="8e563-147">Seleccione **obtener token en masa**.</span><span class="sxs-lookup"><span data-stu-id="8e563-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="8e563-148">Aparece un mensaje de inicio de sesión para conectarse a Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8e563-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD página de inicio de sesión](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="8e563-150">Escriba el nombre de usuario del inquilino ( john@mycompany.onmicrosoft.compor ejemplo,) y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="8e563-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="8e563-151">Acepte que la aplicación de diseño de configuración de Windows pueda acceder a la información de Azure AD.</span><span class="sxs-lookup"><span data-stu-id="8e563-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="8e563-152">Un mensaje en la página muestra que el token de AAD en masa se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8e563-152">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![Mensaje de token en masa correcto](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="8e563-154">Seleccione **cambiar a editor avanzado**y, a continuación, seleccione *sí*.</span><span class="sxs-lookup"><span data-stu-id="8e563-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![Cambiar a la página de confirmación del editor avanzado](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="8e563-156">En **personalizaciones seleccionadas**, deje la configuración de la **cuenta** , pero Quite todas las demás configuraciones:</span><span class="sxs-lookup"><span data-stu-id="8e563-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="8e563-157">Seleccione **Oobe**y, a continuación, seleccione **quitar**.</span><span class="sxs-lookup"><span data-stu-id="8e563-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="8e563-158">Si aparece **SharedPC** , selecciónelo y, a continuación, seleccione **quitar**.</span><span class="sxs-lookup"><span data-stu-id="8e563-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![Quitar personalizaciones](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="8e563-160">Seleccione **exportar**y, a continuación, elija **paquete de aprovisionamiento**.</span><span class="sxs-lookup"><span data-stu-id="8e563-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![Elegir el paquete de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="8e563-162">En la página siguiente, acepte la configuración predeterminada y seleccione **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8e563-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="8e563-163">De nuevo, en la página siguiente, acepte la configuración predeterminada y seleccione siguiente.</span><span class="sxs-lookup"><span data-stu-id="8e563-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="8e563-164">Cambie el destino del **paquete de aprovisionamiento** o deje la ruta de acceso predeterminada y, a continuación, seleccione **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="8e563-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="8e563-165">Seleccionecompilar.</span><span class="sxs-lookup"><span data-stu-id="8e563-165">Select **Build**.</span></span>
20. <span data-ttu-id="8e563-166">Seleccione el vínculo **Ubicación de salida** para que pueda localizar el archivo. ppkg cuando esté listo.</span><span class="sxs-lookup"><span data-stu-id="8e563-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![Vínculos de ubicación de salida](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="8e563-168">Seleccione **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="8e563-168">Select **Finish**.</span></span>
22. <span data-ttu-id="8e563-169">Vaya al explorador de archivos y copie el paquete de aprovisionamiento en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="8e563-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="8e563-170">Guárdelo en la tarjeta microSD en la unidad **principal** de la carpeta **c:\windows\provisioning\packages** .</span><span class="sxs-lookup"><span data-stu-id="8e563-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="8e563-171">Tendrá que conceder permisos para guardar el archivo en esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="8e563-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="8e563-172">Aprovisionamiento e inscripción del dispositivo IoT Core en Intune</span><span class="sxs-lookup"><span data-stu-id="8e563-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="8e563-173">Inserte la tarjeta microSD en el dispositivo de IoT Core.</span><span class="sxs-lookup"><span data-stu-id="8e563-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="8e563-174">Encienda el dispositivo de IoT Core y deje tiempo para que se inicie y muestre la pantalla estándar.</span><span class="sxs-lookup"><span data-stu-id="8e563-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="8e563-175">Vuelva a la consola de Microsoft Intune en el Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="8e563-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="8e563-176">El dispositivo debe aparecer en la lista de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8e563-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="8e563-177">La inscripción podría tardar 15 minutos o más en completarse.</span><span class="sxs-lookup"><span data-stu-id="8e563-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Lista de dispositivos de Intune](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="8e563-179">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="8e563-179">Next steps</span></span>

- <span data-ttu-id="8e563-180">[Vea los detalles del dispositivo en Intune](https://docs.microsoft.com/intune/device-inventory).</span><span class="sxs-lookup"><span data-stu-id="8e563-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="8e563-181">[Sincronizar el dispositivo para obtener las directivas y las acciones más recientes con Intune](https://docs.microsoft.com/intune/device-sync).</span><span class="sxs-lookup"><span data-stu-id="8e563-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="8e563-182">[Reiniciar el dispositivo de forma remota con Intune](https://docs.microsoft.com/intune/device-restart).</span><span class="sxs-lookup"><span data-stu-id="8e563-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
