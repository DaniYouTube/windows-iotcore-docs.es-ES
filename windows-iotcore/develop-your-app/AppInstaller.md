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
# <a name="install-your-app-on-an-iot-core-device"></a>Instalar la aplicación en un dispositivo de IoT Core
Puede instalar la aplicación mediante uno de los dos métodos que se enumeran a continuación.

> [!NOTE]
> Instalación de aplicaciones con el de Windows Device Portal es sólo para escenarios de desarrollo.
> Cree un paquete de aprovisionamiento o agregar la aplicación a la imagen de Windows IoT Core para escenarios de producción.

## <a name="using-windows-device-portal"></a>Uso de Windows Device Portal

> [!NOTE]
> Un .appx o .appxbundle es necesario para Windows Device Portal. Desde la versión 17763 del SDK y herramientas si la mínima versión del proyecto de aplicación de destino > es mayor o 17763 crearán las herramientas de un [.msix o .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).
> Para crear un conjunto de .appx o .appxbundle la versión mínima para una versión inferior a 17763 o [ejecutar directamente makeappx.exe](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax). Es también posible cambiar el nombre de la .msix .appx o .msixbundle a appxbundle.

Para este método, deberá asegurarse de que está conectado a internet. Si no tiene acceso a internet, también puede tener una conexión ethernet de punto a punto entre el dispositivo y un equipo cliente que no incluye la ruta de acceso a la internet abierta. Sin embargo, llegar a la última forma instalará la aplicación pero iniciará si la aplicación está firmado por el almacén.

Para instalar la aplicación en el dispositivo, realice lo siguiente:

1. Abra el [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) para el dispositivo de IoT.

2. En el **aplicaciones** menú, instalar la aplicación, seleccione los archivos de aplicación y haciendo clic en **instalar**.

3. Haga clic en **Seleccionar archivo**

4. Seleccione el archivo .appx y haga clic en **abierto**

5. Comprobar **permitirme seleccionar los paquetes de framework**

6. Haga clic en **Siguiente**.

7. Para cada elemento de la **dependencias** carpeta para el paso de AppX repetición 7.1 y 7.2

    7.1 haga clic en **Elegir archivo**

    7.2 Seleccione archivo .appx depenency y haga clic en **abierto**

8. Cuando todas las dependencias se agregan clic **instalar**

9. Espera para la instalación se complete y haga clic en **listo**

 ![Instalar aplicación](../media/AppInstaller/install-app.gif)

10. La aplicación ahora estará visible en la lista de aplicaciones en el dispositivo.
 ![Instalar aplicación](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>Usar el paquete de aprovisionamiento de WCD
Puede crear un paquete de aprovisionamiento con la aplicación e instalar el paquete de aprovisionamiento en el dispositivo. Este método funciona incluso en dispositivos que no tienen conexión a internet y es el método preferido para instalar el archivo de licencia del almacén. Por ejemplo, esto habilita escenarios de fábrica en el dispositivo no está conectado a internet pero la aplicación principal es una aplicación UWP firmado por el almacén.

> [!NOTE]
> El nombre de familia de paquete (PFN) puede encontrarse en el centro de desarrollo de Windows en **administración de aplicaciones > identidad de aplicación**

1. Abra [Diseñador de configuración de Windows (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. Seleccione **avanzada aprovisionamiento**, escriba el nombre del proyecto y una descripción

3. Elija Windows 10 IoT Core para la configuración del proyecto y omitir la importación del paquete de aprovisionamiento

4. En el lado izquierdo, expanda **en tiempo de ejecución** y haga clic en **de instalación de aplicaciones Universal > aplicación de contexto de usuario**

5. Escriba el nombre de familia de paquete de la aplicación y haga clic en **agregar**

6. En el PFN recién agregado
    - agregar el Appx y sus dependencias
    - establecer el DeploymentOptions "Cierre de aplicación de destino Force"

7. Store firmados de aplicaciones deberá especificar la licencia. En UserContextAppLicense,
    - Agregar LicenseProductID (disponible como LicenseID en el archivo de licencia XML)
    - Cambie la extensión de licencia xml a *.ms-windows-store-licencia*.
    - Seleccione el identificador de producto de licencia en el lado izquierdo y busque el archivo de licencia para asignar el campo LicenseInstall

8. Para las aplicaciones firmadas no-store, deberá agregar el archivo app.cer bajo **certificados > RootCertificates** 

9. Exportar el paquete

10. Copie el archivo .ppkg exportado en _C:\Windows\Provisioning\Packages_ en el dispositivo de IoT mediante [SSH](../connect-your-device/SSH.md) o [Powershell](../connect-your-device/powershell.md)) y reinicie el equipo. Cuando el dispositivo se reinicia, se procesa el paquete de aprovisionamiento y la aplicación está instalada.


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>Agregar la aplicación a la image(.ffu) Windows IoT Core
Puede agregar la aplicación para formar parte de la propia imagen de Windows IoT Core.
Este es el método preferido para que los OEM instalen las aplicaciones en sus dispositivos.

Vea cómo [agregar una aplicación a la imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) y un [paquete de aplicación de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).
