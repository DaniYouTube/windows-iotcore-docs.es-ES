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
# <a name="install-your-app-on-an-iot-core-device"></a>Instalar la aplicación en un dispositivo de IoT Core
Puede instalar la aplicación mediante uno de los dos métodos que se enumeran a continuación.

> [!NOTE]
> El método mediante el Windows Device Portal es sólo para escenarios de desarrollo. Los otros dos métodos son para escenarios de producción.

## <a name="using-windows-device-portal"></a>Uso de Windows Device Portal

Para este método, deberá asegurarse de que está conectado a internet. Si no tiene acceso a internet, también puede tener una conexión ethernet de punto a punto entre el dispositivo y un equipo cliente que no incluye la ruta de acceso a la internet abierta. Sin embargo, llegar a la última forma instalará la aplicación pero iniciará si la aplicación está firmado por el almacén.

Para instalar la aplicación en el dispositivo, realice lo siguiente:

1. Abra el [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) para el dispositivo de IoT.

2. En el *aplicaciones* menú, instalar la aplicación mediante la carga del paquete de aplicación.
 ![Instalar aplicación](../media/AppInstaller/install-app.gif)

3. Implementar la aplicación.

4. La aplicación ahora estará visible en la lista de aplicaciones en el dispositivo.
 ![Lista de aplicaciones](../media/AppInstaller/AppList.png)


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


## <a name="add-to-the-iot-core-imageffu"></a>Agregar a la image(.ffu) de IoT core   
Puede agregar la aplicación para formar parte de la propia imagen IoT Core. Este es el mecanismo usado para los OEM. 

Vea cómo [agregar una aplicación a la imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) y un [paquete de aplicación de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).
