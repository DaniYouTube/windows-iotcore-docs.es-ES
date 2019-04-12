---
title: Instalar la aplicación en un dispositivo de IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo instalar la aplicación mediante el Windows Device Portal o como parte del IoT core la imagen.
keywords: Windows iot, los dispositivos de instalación, Windows Device Portal, aplicación
ms.openlocfilehash: 6e188eaef6551548c6c71ac50859516d4cbe7e9c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514616"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="2275f-104">Instalar la aplicación en un dispositivo de IoT Core</span><span class="sxs-lookup"><span data-stu-id="2275f-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="2275f-105">Puede instalar la aplicación mediante uno de los dos métodos que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="2275f-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="2275f-106">El método mediante el Windows Device Portal es sólo para escenarios de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="2275f-106">The method using the Windows Device Portal is only for developer scenarios.</span></span> <span data-ttu-id="2275f-107">Los otros dos métodos son para escenarios de producción.</span><span class="sxs-lookup"><span data-stu-id="2275f-107">The other two methods are for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="2275f-108">Uso de Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="2275f-108">Using Windows Device Portal</span></span>

<span data-ttu-id="2275f-109">Para este método, deberá asegurarse de que está conectado a internet.</span><span class="sxs-lookup"><span data-stu-id="2275f-109">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="2275f-110">Si no tiene acceso a internet, también puede tener una conexión ethernet de punto a punto entre el dispositivo y un equipo cliente que no incluye la ruta de acceso a la internet abierta.</span><span class="sxs-lookup"><span data-stu-id="2275f-110">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="2275f-111">Sin embargo, llegar a la última forma instalará la aplicación pero iniciará si la aplicación está firmado por el almacén.</span><span class="sxs-lookup"><span data-stu-id="2275f-111">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="2275f-112">Para instalar la aplicación en el dispositivo, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2275f-112">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="2275f-113">Abra el [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) para el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="2275f-113">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="2275f-114">En el *aplicaciones* menú, instalar la aplicación mediante la carga del paquete de aplicación.</span><span class="sxs-lookup"><span data-stu-id="2275f-114">In the *Apps* menu, install your app by uploading the app package.</span></span>
 ![Instalar aplicación](../media/AppInstaller/install-app.gif)

3. <span data-ttu-id="2275f-116">Implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2275f-116">Deploy the app.</span></span>

4. <span data-ttu-id="2275f-117">La aplicación ahora estará visible en la lista de aplicaciones en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2275f-117">The application will now be visible on the list of applications on your device.</span></span>
 ![Lista de aplicaciones](../media/AppInstaller/AppList.png)


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="2275f-119">Usar el paquete de aprovisionamiento de WCD</span><span class="sxs-lookup"><span data-stu-id="2275f-119">Using provisioning package from WCD</span></span>
<span data-ttu-id="2275f-120">Puede crear un paquete de aprovisionamiento con la aplicación e instalar el paquete de aprovisionamiento en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2275f-120">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="2275f-121">Este método funciona incluso en dispositivos que no tienen conexión a internet y es el método preferido para instalar el archivo de licencia del almacén.</span><span class="sxs-lookup"><span data-stu-id="2275f-121">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="2275f-122">Por ejemplo, esto habilita escenarios de fábrica en el dispositivo no está conectado a internet pero la aplicación principal es una aplicación UWP firmado por el almacén.</span><span class="sxs-lookup"><span data-stu-id="2275f-122">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="2275f-123">El nombre de familia de paquete (PFN) puede encontrarse en el centro de desarrollo de Windows en **administración de aplicaciones > identidad de aplicación**</span><span class="sxs-lookup"><span data-stu-id="2275f-123">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="2275f-124">Abra [Diseñador de configuración de Windows (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="2275f-124">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="2275f-125">Seleccione **avanzada aprovisionamiento**, escriba el nombre del proyecto y una descripción</span><span class="sxs-lookup"><span data-stu-id="2275f-125">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="2275f-126">Elija Windows 10 IoT Core para la configuración del proyecto y omitir la importación del paquete de aprovisionamiento</span><span class="sxs-lookup"><span data-stu-id="2275f-126">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="2275f-127">En el lado izquierdo, expanda **en tiempo de ejecución** y haga clic en **de instalación de aplicaciones Universal > aplicación de contexto de usuario**</span><span class="sxs-lookup"><span data-stu-id="2275f-127">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="2275f-128">Escriba el nombre de familia de paquete de la aplicación y haga clic en **agregar**</span><span class="sxs-lookup"><span data-stu-id="2275f-128">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="2275f-129">En el PFN recién agregado</span><span class="sxs-lookup"><span data-stu-id="2275f-129">Under the newly added PFN</span></span>
    - <span data-ttu-id="2275f-130">agregar el Appx y sus dependencias</span><span class="sxs-lookup"><span data-stu-id="2275f-130">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="2275f-131">establecer el DeploymentOptions "Cierre de aplicación de destino Force"</span><span class="sxs-lookup"><span data-stu-id="2275f-131">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="2275f-132">Store firmados de aplicaciones deberá especificar la licencia.</span><span class="sxs-lookup"><span data-stu-id="2275f-132">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="2275f-133">En UserContextAppLicense,</span><span class="sxs-lookup"><span data-stu-id="2275f-133">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="2275f-134">Agregar LicenseProductID (disponible como LicenseID en el archivo de licencia XML)</span><span class="sxs-lookup"><span data-stu-id="2275f-134">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="2275f-135">Cambie la extensión de licencia xml a *.ms-windows-store-licencia*.</span><span class="sxs-lookup"><span data-stu-id="2275f-135">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="2275f-136">Seleccione el identificador de producto de licencia en el lado izquierdo y busque el archivo de licencia para asignar el campo LicenseInstall</span><span class="sxs-lookup"><span data-stu-id="2275f-136">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="2275f-137">Para las aplicaciones firmadas no-store, deberá agregar el archivo app.cer bajo **certificados > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="2275f-137">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="2275f-138">Exportar el paquete</span><span class="sxs-lookup"><span data-stu-id="2275f-138">Export the package</span></span>

10. <span data-ttu-id="2275f-139">Copie el archivo .ppkg exportado en _C:\Windows\Provisioning\Packages_ en el dispositivo de IoT mediante [SSH](../connect-your-device/SSH.md) o [Powershell](../connect-your-device/powershell.md)) y reinicie el equipo.</span><span class="sxs-lookup"><span data-stu-id="2275f-139">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="2275f-140">Cuando el dispositivo se reinicia, se procesa el paquete de aprovisionamiento y la aplicación está instalada.</span><span class="sxs-lookup"><span data-stu-id="2275f-140">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-to-the-iot-core-imageffu"></a><span data-ttu-id="2275f-141">Agregar a la image(.ffu) de IoT core</span><span class="sxs-lookup"><span data-stu-id="2275f-141">Add to the IoT core image(.ffu)</span></span>   
<span data-ttu-id="2275f-142">Puede agregar la aplicación para formar parte de la propia imagen IoT Core.</span><span class="sxs-lookup"><span data-stu-id="2275f-142">You can add the app to be part of the IoT Core image itself.</span></span> <span data-ttu-id="2275f-143">Este es el mecanismo usado para los OEM.</span><span class="sxs-lookup"><span data-stu-id="2275f-143">This is the widely used mechanism for OEMs.</span></span> 

<span data-ttu-id="2275f-144">Vea cómo [agregar una aplicación a la imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) y un [paquete de aplicación de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span><span class="sxs-lookup"><span data-stu-id="2275f-144">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
