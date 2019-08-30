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
# <a name="install-your-app-on-an-iot-core-device"></a>Instalación de la aplicación en un dispositivo de IoT Core
Puede instalar la aplicación mediante uno de los dos métodos que se enumeran a continuación.

> [!NOTE]
> La instalación de aplicaciones mediante el portal de dispositivos de Windows solo es para escenarios de desarrollador.
> Cree un paquete de aprovisionamiento o agregue la aplicación a la imagen de Windows IoT Core para escenarios de producción.

## <a name="using-windows-device-portal"></a>Uso del portal de dispositivos de Windows

> [!NOTE]
> Se requiere un. appx o. appxbundle para el portal de dispositivos de Windows. A partir de la versión 17763 del SDK y las herramientas si la versión de destino mínima del proyecto de aplicación > es 17763 o superior, las herramientas crearán un [. msix o. msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).
> Para crear un archivo. appx o. appxbundle, establezca la versión mínima en una versión inferior a 17763 o [ejecute makeappx. exe directamente](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax). También es posible cambiar el nombre de. msix a. appx o. msixbundle a. appxbundle.

Para este método, deberá asegurarse de que está conectado a Internet. Si no tiene acceso a Internet, también puede tener una conexión Ethernet punto a punto entre el dispositivo y un equipo cliente que no incluya una ruta de acceso para acceder a Internet abierto. Sin embargo, si se trata de la última manera, se instalará la aplicación, pero no se iniciará si la aplicación está firmada en la tienda.

Para instalar la aplicación en el dispositivo, haga lo siguiente:

1. Abra el [portal de dispositivos de Windows](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) para el dispositivo de IOT.

2. En el menú **aplicaciones** , seleccione los archivos de la aplicación y haga clic en **instalar**para instalar la aplicación.

3. Haga clic en **Seleccionar archivo** .

4. Seleccione el archivo. appx y haga clic en **abrir** .

5. Active **la casilla permitirme seleccionar paquetes de Framework**

6. Haga clic en **Siguiente**.

7. Para cada elemento de la carpeta **dependencies** del. appx, repita el paso 7,1 y 7,2

    7,1 Haga clic en **elegir archivo**

    7,2 Seleccione depenency. appx y haga clic en **abrir** .

8. Cuando se hayan agregado todas las dependencias, haga clic en **instalar** .

9. Espere a que se complete la instalación y haga clic en **listo** .

 ![Instalar aplicación](../media/AppInstaller/install-app.gif)

10. La aplicación ahora estará visible en la lista de aplicaciones del dispositivo.
 ![Instalar aplicación](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>Usar el paquete de aprovisionamiento de WCD
Puede crear un paquete de aprovisionamiento con la aplicación e instalar el paquete de aprovisionamiento en el dispositivo. Este método funciona incluso en dispositivos que no tienen conexión a Internet y es el método preferido para instalar el archivo de licencia de almacén. Por ejemplo, esto habilita escenarios de fábrica en los que el dispositivo no está conectado a Internet, pero la aplicación principal es una aplicación de UWP firmada por el almacén.

> [!NOTE]
> El nombre de familia de paquete (PFN) se puede encontrar en el centro de desarrollo de Windows en **App Management > identidad** de la aplicación.

1. Abrir el [Diseñador de configuración de Windows (wicd)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. Seleccione **aprovisionamiento avanzado**, escriba el nombre del proyecto y una descripción.

3. Elija Windows 10 IoT Core para la configuración del proyecto y omita la importación del paquete de aprovisionamiento.

4. En el lado izquierdo, expanda **configuración de tiempo de ejecución** y haga clic en instalación de **aplicación universal > aplicación de contexto de usuario** .

5. Escriba el nombre de familia de paquete de la aplicación y haga clic en **Agregar** .

6. En el PFN recién agregado
    - agregar el appx y sus dependencias
    - establecer archivo deploymentoptions en "forzar el cierre de la aplicación de destino"

7. En el caso de las aplicaciones firmadas en el almacén, debe especificar la licencia. En UserContextAppLicense,
    - Agregar LicenseProductID (disponible como LicenseID en el archivo de licencia XML)
    - cambie la extensión de XML de licencia a *. MS-Windows-Store-License*.
    - Seleccione el ID. de producto de licencia en el lado izquierdo y examine el archivo de licencia para asignar el campo LicenseInstall

8. En el caso de las aplicaciones no almacenadas en el almacén, tendrá que agregar el archivo app. cer en **certificados > RootCertificates** 

9. Exportar el paquete

10. Copie el archivo. ppkg exportado en _C:\Windows\Provisioning\Packages_ en el dispositivo IOT mediante [ssh](../connect-your-device/SSH.md) o [PowerShell](../connect-your-device/powershell.md)) y reinicie. Cuando el dispositivo se reinicia, se procesa el paquete de aprovisionamiento y se instala la aplicación.


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>Agregar la aplicación a la imagen de Windows IoT Core (. FFU)
Puede Agregar la aplicación para que forme parte de la propia imagen de Windows IoT Core.
Este es el método preferido para que los OEM instalen aplicaciones en sus dispositivos.

Vea cómo [Agregar una aplicación a la imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) y un [paquete de aplicación de ejemplo](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).
