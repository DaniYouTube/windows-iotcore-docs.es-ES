---
title: Instalación de la aplicación en un dispositivo de IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo instalar la aplicación mediante el portal de dispositivos de Windows o como parte de la imagen de IoT Core.
keywords: Windows IOT, instalación de aplicaciones, portal de dispositivos de Windows, dispositivos
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694156"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="55734-104">Instalación de la aplicación en un dispositivo de IoT Core</span><span class="sxs-lookup"><span data-stu-id="55734-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="55734-105">Puede instalar la aplicación mediante uno de los dos métodos que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="55734-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="55734-106">La instalación de aplicaciones mediante el portal de dispositivos de Windows solo es para escenarios de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="55734-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="55734-107">Cree un paquete de aprovisionamiento o agregue la aplicación a la imagen de Windows IoT Core para escenarios de producción.</span><span class="sxs-lookup"><span data-stu-id="55734-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="55734-108">Uso del portal de dispositivos de Windows</span><span class="sxs-lookup"><span data-stu-id="55734-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="55734-109">Se requiere un. appx o. appxbundle para el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="55734-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="55734-110">A partir de la versión 17763 del SDK y las herramientas si la versión de destino mínima del proyecto de aplicación > es 17763 o superior, las herramientas crearán un [. msix o. msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span><span class="sxs-lookup"><span data-stu-id="55734-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="55734-111">Para crear un archivo. appx o. appxbundle, establezca la versión mínima en una versión inferior a 17763 o [ejecute makeappx. exe directamente](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span><span class="sxs-lookup"><span data-stu-id="55734-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="55734-112">También es posible cambiar el nombre de. msix a. appx o. msixbundle a. appxbundle.</span><span class="sxs-lookup"><span data-stu-id="55734-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="55734-113">Para este método, deberá asegurarse de que está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="55734-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="55734-114">Si no tiene acceso a Internet, también puede tener una conexión Ethernet punto a punto entre el dispositivo y un equipo cliente que no incluya una ruta de acceso para acceder a Internet abierto.</span><span class="sxs-lookup"><span data-stu-id="55734-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="55734-115">Sin embargo, si se trata de la última manera, se instalará la aplicación, pero no se iniciará si la aplicación está firmada en la tienda.</span><span class="sxs-lookup"><span data-stu-id="55734-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="55734-116">Para instalar la aplicación en el dispositivo, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="55734-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="55734-117">Abra el [portal de dispositivos de Windows](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) para el dispositivo de IOT.</span><span class="sxs-lookup"><span data-stu-id="55734-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="55734-118">En el menú **aplicaciones** , seleccione los archivos de la aplicación y haga clic en **instalar**para instalar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="55734-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="55734-119">Haga clic en **Seleccionar archivo** .</span><span class="sxs-lookup"><span data-stu-id="55734-119">Click **Select File**</span></span>

4. <span data-ttu-id="55734-120">Seleccione el archivo. appx y haga clic en **abrir** .</span><span class="sxs-lookup"><span data-stu-id="55734-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="55734-121">Active **la casilla permitirme seleccionar paquetes de Framework**</span><span class="sxs-lookup"><span data-stu-id="55734-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="55734-122">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="55734-122">Click **Next**</span></span>

7. <span data-ttu-id="55734-123">Para cada elemento de la carpeta **dependencies** del. appx, repita el paso 7,1 y 7,2</span><span class="sxs-lookup"><span data-stu-id="55734-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="55734-124">7,1 Haga clic en **elegir archivo**</span><span class="sxs-lookup"><span data-stu-id="55734-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="55734-125">7,2 Seleccione depenency. appx y haga clic en **abrir** .</span><span class="sxs-lookup"><span data-stu-id="55734-125">7.2 Select the depenency .appx and click **Open**</span></span>

8. <span data-ttu-id="55734-126">Cuando se hayan agregado todas las dependencias, haga clic en **instalar** .</span><span class="sxs-lookup"><span data-stu-id="55734-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="55734-127">Espere a que se complete la instalación y haga clic en **listo** .</span><span class="sxs-lookup"><span data-stu-id="55734-127">Wait for the install is completed and click **Done**</span></span>

 ![Instalar aplicación](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="55734-129">La aplicación ahora estará visible en la lista de aplicaciones del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="55734-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="55734-130">![Instalar aplicación](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="55734-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="55734-131">Usar el paquete de aprovisionamiento de WCD</span><span class="sxs-lookup"><span data-stu-id="55734-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="55734-132">Puede crear un paquete de aprovisionamiento con la aplicación e instalar el paquete de aprovisionamiento en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="55734-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="55734-133">Este método funciona incluso en dispositivos que no tienen conexión a Internet y es el método preferido para instalar el archivo de licencia de almacén.</span><span class="sxs-lookup"><span data-stu-id="55734-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="55734-134">Por ejemplo, esto habilita escenarios de fábrica en los que el dispositivo no está conectado a Internet, pero la aplicación principal es una aplicación de UWP firmada por el almacén.</span><span class="sxs-lookup"><span data-stu-id="55734-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="55734-135">El nombre de familia de paquete (PFN) se puede encontrar en el centro de desarrollo de Windows en **App Management > identidad** de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="55734-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="55734-136">Abrir el [Diseñador de configuración de Windows (wicd)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="55734-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="55734-137">Seleccione **aprovisionamiento avanzado**, escriba el nombre del proyecto y una descripción.</span><span class="sxs-lookup"><span data-stu-id="55734-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="55734-138">Elija Windows 10 IoT Core para la configuración del proyecto y omita la importación del paquete de aprovisionamiento.</span><span class="sxs-lookup"><span data-stu-id="55734-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="55734-139">En el lado izquierdo, expanda **configuración de tiempo de ejecución** y haga clic en instalación de **aplicación universal > aplicación de contexto de usuario** .</span><span class="sxs-lookup"><span data-stu-id="55734-139">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="55734-140">Escriba el nombre de familia de paquete de la aplicación y haga clic en **Agregar** .</span><span class="sxs-lookup"><span data-stu-id="55734-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="55734-141">En el PFN recién agregado</span><span class="sxs-lookup"><span data-stu-id="55734-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="55734-142">agregar el appx y sus dependencias</span><span class="sxs-lookup"><span data-stu-id="55734-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="55734-143">establecer archivo deploymentoptions en "forzar el cierre de la aplicación de destino"</span><span class="sxs-lookup"><span data-stu-id="55734-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="55734-144">En el caso de las aplicaciones firmadas en el almacén, debe especificar la licencia.</span><span class="sxs-lookup"><span data-stu-id="55734-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="55734-145">En UserContextAppLicense,</span><span class="sxs-lookup"><span data-stu-id="55734-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="55734-146">Agregar LicenseProductID (disponible como LicenseID en el archivo de licencia XML)</span><span class="sxs-lookup"><span data-stu-id="55734-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="55734-147">cambie la extensión de XML de licencia a *. MS-Windows-Store-License*.</span><span class="sxs-lookup"><span data-stu-id="55734-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="55734-148">Seleccione el ID. de producto de licencia en el lado izquierdo y examine el archivo de licencia para asignar el campo LicenseInstall</span><span class="sxs-lookup"><span data-stu-id="55734-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="55734-149">En el caso de las aplicaciones no almacenadas en el almacén, tendrá que agregar el archivo app. cer en **certificados > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="55734-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="55734-150">Exportar el paquete</span><span class="sxs-lookup"><span data-stu-id="55734-150">Export the package</span></span>

10. <span data-ttu-id="55734-151">Copie el archivo. ppkg exportado en _C:\Windows\Provisioning\Packages_ en el dispositivo IOT mediante [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/powershell.md)) y reinicie.</span><span class="sxs-lookup"><span data-stu-id="55734-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="55734-152">Cuando el dispositivo se reinicia, se procesa el paquete de aprovisionamiento y se instala la aplicación.</span><span class="sxs-lookup"><span data-stu-id="55734-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="55734-153">Agregar la aplicación a la imagen de Windows IoT Core (. FFU)</span><span class="sxs-lookup"><span data-stu-id="55734-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="55734-154">Puede Agregar la aplicación para que forme parte de la propia imagen de Windows IoT Core.</span><span class="sxs-lookup"><span data-stu-id="55734-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="55734-155">Este es el método preferido para que los OEM instalen aplicaciones en sus dispositivos.</span><span class="sxs-lookup"><span data-stu-id="55734-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="55734-156">Vea cómo [Agregar una aplicación a la imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) y un [paquete de aplicación de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="55734-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
