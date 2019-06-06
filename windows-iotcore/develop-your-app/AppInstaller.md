---
title: Instalar la aplicación en un dispositivo de IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo instalar la aplicación mediante el Windows Device Portal o como parte del IoT core la imagen.
keywords: Windows iot, los dispositivos de instalación, Windows Device Portal, aplicación
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694156"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="09aa9-104">Instalar la aplicación en un dispositivo de IoT Core</span><span class="sxs-lookup"><span data-stu-id="09aa9-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="09aa9-105">Puede instalar la aplicación mediante uno de los dos métodos que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="09aa9-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="09aa9-106">Instalación de aplicaciones con el de Windows Device Portal es sólo para escenarios de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="09aa9-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="09aa9-107">Cree un paquete de aprovisionamiento o agregar la aplicación a la imagen de Windows IoT Core para escenarios de producción.</span><span class="sxs-lookup"><span data-stu-id="09aa9-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="09aa9-108">Uso de Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="09aa9-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="09aa9-109">Un .appx o .appxbundle es necesario para Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="09aa9-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="09aa9-110">Desde la versión 17763 del SDK y herramientas si la mínima versión del proyecto de aplicación de destino > es mayor o 17763 crearán las herramientas de un [.msix o .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span><span class="sxs-lookup"><span data-stu-id="09aa9-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="09aa9-111">Para crear un conjunto de .appx o .appxbundle la versión mínima para una versión inferior a 17763 o [ejecutar directamente makeappx.exe](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span><span class="sxs-lookup"><span data-stu-id="09aa9-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="09aa9-112">Es también posible cambiar el nombre de la .msix .appx o .msixbundle a appxbundle.</span><span class="sxs-lookup"><span data-stu-id="09aa9-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="09aa9-113">Para este método, deberá asegurarse de que está conectado a internet.</span><span class="sxs-lookup"><span data-stu-id="09aa9-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="09aa9-114">Si no tiene acceso a internet, también puede tener una conexión ethernet de punto a punto entre el dispositivo y un equipo cliente que no incluye la ruta de acceso a la internet abierta.</span><span class="sxs-lookup"><span data-stu-id="09aa9-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="09aa9-115">Sin embargo, llegar a la última forma instalará la aplicación pero iniciará si la aplicación está firmado por el almacén.</span><span class="sxs-lookup"><span data-stu-id="09aa9-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="09aa9-116">Para instalar la aplicación en el dispositivo, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="09aa9-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="09aa9-117">Abra el [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) para el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="09aa9-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="09aa9-118">En el **aplicaciones** menú, instalar la aplicación, seleccione los archivos de aplicación y haciendo clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="09aa9-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="09aa9-119">Haga clic en **Seleccionar archivo**</span><span class="sxs-lookup"><span data-stu-id="09aa9-119">Click **Select File**</span></span>

4. <span data-ttu-id="09aa9-120">Seleccione el archivo .appx y haga clic en **abierto**</span><span class="sxs-lookup"><span data-stu-id="09aa9-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="09aa9-121">Comprobar **permitirme seleccionar los paquetes de framework**</span><span class="sxs-lookup"><span data-stu-id="09aa9-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="09aa9-122">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="09aa9-122">Click **Next**</span></span>

7. <span data-ttu-id="09aa9-123">Para cada elemento de la **dependencias** carpeta para el paso de AppX repetición 7.1 y 7.2</span><span class="sxs-lookup"><span data-stu-id="09aa9-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="09aa9-124">7.1 haga clic en **Elegir archivo**</span><span class="sxs-lookup"><span data-stu-id="09aa9-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="09aa9-125">7.2 Seleccione archivo .appx depenency y haga clic en **abierto**</span><span class="sxs-lookup"><span data-stu-id="09aa9-125">7.2 Select the depenency .appx and click **Open**</span></span>

8. <span data-ttu-id="09aa9-126">Cuando todas las dependencias se agregan clic **instalar**</span><span class="sxs-lookup"><span data-stu-id="09aa9-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="09aa9-127">Espera para la instalación se complete y haga clic en **listo**</span><span class="sxs-lookup"><span data-stu-id="09aa9-127">Wait for the install is completed and click **Done**</span></span>

 ![Instalar aplicación](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="09aa9-129">La aplicación ahora estará visible en la lista de aplicaciones en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="09aa9-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="09aa9-130">![Instalar aplicación](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="09aa9-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="09aa9-131">Usar el paquete de aprovisionamiento de WCD</span><span class="sxs-lookup"><span data-stu-id="09aa9-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="09aa9-132">Puede crear un paquete de aprovisionamiento con la aplicación e instalar el paquete de aprovisionamiento en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="09aa9-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="09aa9-133">Este método funciona incluso en dispositivos que no tienen conexión a internet y es el método preferido para instalar el archivo de licencia del almacén.</span><span class="sxs-lookup"><span data-stu-id="09aa9-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="09aa9-134">Por ejemplo, esto habilita escenarios de fábrica en el dispositivo no está conectado a internet pero la aplicación principal es una aplicación UWP firmado por el almacén.</span><span class="sxs-lookup"><span data-stu-id="09aa9-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="09aa9-135">El nombre de familia de paquete (PFN) puede encontrarse en el centro de desarrollo de Windows en **administración de aplicaciones > identidad de aplicación**</span><span class="sxs-lookup"><span data-stu-id="09aa9-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="09aa9-136">Abra [Diseñador de configuración de Windows (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="09aa9-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="09aa9-137">Seleccione **avanzada aprovisionamiento**, escriba el nombre del proyecto y una descripción</span><span class="sxs-lookup"><span data-stu-id="09aa9-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="09aa9-138">Elija Windows 10 IoT Core para la configuración del proyecto y omitir la importación del paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="09aa9-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="09aa9-139">En el lado izquierdo, expanda **en tiempo de ejecución** y haga clic en **de instalación de aplicaciones Universal > aplicación de contexto de usuario**</span><span class="sxs-lookup"><span data-stu-id="09aa9-139">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="09aa9-140">Escriba el nombre de familia de paquete de la aplicación y haga clic en **agregar**</span><span class="sxs-lookup"><span data-stu-id="09aa9-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="09aa9-141">En el PFN recién agregado</span><span class="sxs-lookup"><span data-stu-id="09aa9-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="09aa9-142">agregar el Appx y sus dependencias</span><span class="sxs-lookup"><span data-stu-id="09aa9-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="09aa9-143">establecer el DeploymentOptions "Cierre de aplicación de destino Force"</span><span class="sxs-lookup"><span data-stu-id="09aa9-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="09aa9-144">Store firmados de aplicaciones deberá especificar la licencia.</span><span class="sxs-lookup"><span data-stu-id="09aa9-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="09aa9-145">En UserContextAppLicense,</span><span class="sxs-lookup"><span data-stu-id="09aa9-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="09aa9-146">Agregar LicenseProductID (disponible como LicenseID en el archivo de licencia XML)</span><span class="sxs-lookup"><span data-stu-id="09aa9-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="09aa9-147">Cambie la extensión de licencia xml a *.ms-windows-store-licencia*.</span><span class="sxs-lookup"><span data-stu-id="09aa9-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="09aa9-148">Seleccione el identificador de producto de licencia en el lado izquierdo y busque el archivo de licencia para asignar el campo LicenseInstall</span><span class="sxs-lookup"><span data-stu-id="09aa9-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="09aa9-149">Para las aplicaciones firmadas no-store, deberá agregar el archivo app.cer bajo **certificados > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="09aa9-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="09aa9-150">Exportar el paquete</span><span class="sxs-lookup"><span data-stu-id="09aa9-150">Export the package</span></span>

10. <span data-ttu-id="09aa9-151">Copie el archivo .ppkg exportado en _C:\Windows\Provisioning\Packages_ en el dispositivo de IoT mediante [SSH](../connect-your-device/SSH.md) o [Powershell](../connect-your-device/powershell.md)) y reinicie el equipo.</span><span class="sxs-lookup"><span data-stu-id="09aa9-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="09aa9-152">Cuando el dispositivo se reinicia, se procesa el paquete de aprovisionamiento y la aplicación está instalada.</span><span class="sxs-lookup"><span data-stu-id="09aa9-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="09aa9-153">Agregar la aplicación a la image(.ffu) Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="09aa9-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="09aa9-154">Puede agregar la aplicación para formar parte de la propia imagen de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="09aa9-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="09aa9-155">Este es el método preferido para que los OEM instalen las aplicaciones en sus dispositivos.</span><span class="sxs-lookup"><span data-stu-id="09aa9-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="09aa9-156">Vea cómo [agregar una aplicación a la imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) y un [paquete de aplicación de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="09aa9-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
