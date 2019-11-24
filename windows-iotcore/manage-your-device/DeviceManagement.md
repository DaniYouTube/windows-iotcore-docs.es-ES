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
# <a name="managing-windows-iot-core-devices"></a>Administración de dispositivos Windows IoT Core

Los dispositivos de Windows 10 IoT Core pueden administrarse mediante un servidor MDM DM DM tradicional que admita la inscripción basada en certificados o el uso de la administración de dispositivos de Azure IoT Hub.  

 _[Aquí](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)encontrará más información sobre MDM y Windows 10._  

En el caso de los dispositivos que se administran mediante un servidor OMA DM, las directivas MDM para Windows 10 IoT Core se alinean con las directivas admitidas en otras ediciones de Windows 10. Para más información sobre las directivas, así como sobre lo que se puede administrar en los dispositivos IoT Core, consulte referencia del proveedor de servicios de configuración para Windows 10 [aquí](https://aka.ms/csplist). La compatibilidad de MDM en Windows 10 se basa en la especificación del Protocolo de administración de dispositivos (DM) de Open Mobile Alliance (OMA).

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>Cómo inscribir un dispositivo IoT Core en una MDM
___
La inscripción de MDM de un dispositivo de IoT Core se realiza mediante un paquete de aprovisionamiento. Los paquetes de aprovisionamiento se pueden crear mediante el diseñador y la configuración de imágenes de Windows (WICD). Vamos a intentar inscribir un dispositivo en una MDM.

### <a name="creating-a-provisioning-package"></a>Creación de un paquete de aprovisionamiento

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (independiente o SCCM + Intune híbrido)

1. Abra la consola de administración de Configuration Manager (consola de ConfigMgr)

2. Vaya a _activos y compatibilidad > configuración de cumplimiento > perfiles de acceso de recursos de la compañía > perfiles_ de certificado
   ![perfiles de certificado](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. Haga clic en **crear Perfil de certificado** .

4. Proporcionar un nombre y una descripción para el perfil
   - Nombre: ejemplo de Configuration Manager certificado raíz de confianza
     - Tipo de Perfil de certificado: certificado de CA de confianza  
     ![Certificación de confianza](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. Haz clic en **Siguiente**.

6. Importe el archivo de certificado.

7. Seleccione **almacén de certificados del equipo-raíz** para el **almacén de destino**.

8. Haz clic en **Siguiente**.

9. Elija **seleccionar todo para las** plataformas compatibles ![plataformas admitidas](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. Haga clic en **Resumen, siguiente y cerrar** para salir del asistente.

11. Haga clic con el botón derecho en el perfil que acaba de crear y haga clic en **exportar**.

12. Haga clic en **examinar**, busque una ubicación donde se debe exportar el archivo. ppkg y, a continuación, haga clic en **Guardar**.

13. Haga clic en **exportar** y en **Aceptar** para salir del asistente.

#### <a name="other-mdm-servers"></a>Otros servidores MDM

1. Descargue e instale [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).

2. Abra el diseñador de imágenes y configuraciones de Windows (WICD).
   ![el diseñador de imágenes y configuraciones de Windows](../media/ManagingDevices/WICD-Start-Page.png)

3. Elección del **aprovisionamiento avanzado**

4. Establezca un nombre para el paquete.

5. Elija la configuración común para Windows 10 IoT Core.

6. Omitir el paso importar paquete.
   ![WICD-New-Project-details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. Vaya a Workplace-> inscripciones.

8. En el campo UPN, escriba la cuenta en la que desea inscribir el dispositivo (es decir, trmck@contoso.co) y haga clic en **Agregar**.

   ![Inscripciones de área de trabajo llenas](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. Para AuthPolicy, elija entre el nombre de usuario autenticación basada en contraseña (local) o la autenticación basada en certificados.

10. Escriba la dirección URL del servicio de detección para el servidor MDM.

> [!NOTE]
> La dirección URL del servicio de inscripción y la dirección URL del servicio de directivas son opcionales.

11. Para el secreto, escriba  
    - Local: la contraseña de la cuenta con la que está realizando la inscripción.  
    - Certificado: la huella digital del certificado
    
    ![En su entorno local](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. En la parte superior de la ventana de WICD, haga clic en **exportar > paquete de aprovisionamiento**.

13. Proporcione un nombre y una versión para el paquete y haga clic en **siguiente**. 

> [!NOTE]
> Asegúrese de incrementar el número de versión para asegurarse de que se ejecuta un paquete actualizado.

14. Haga clic en **siguiente** en la **página Detalles de seguridad**.

15. Elija la ubicación donde se exportará el paquete en el equipo local y haga clic en **siguiente**.

16. Haga clic en **generar** y, a continuación, en **Finalizar** para salir del asistente.

### <a name="installing-the-provisioning-package"></a>Instalación del paquete de aprovisionamiento

Hay varias maneras en las que se puede implementar un paquete de aprovisionamiento en un dispositivo IoT. Es posible implementar un paquete copiando el paquete en el dispositivo o agregando el paquete a la imagen durante el proceso de creación de imágenes.

#### <a name="copying-package-to-device"></a>Copiando el paquete en el dispositivo

Tome el paquete de aprovisionamiento que se exportó desde SCCM o WICD y copie el archivo. ppkg en `C:\Windows\Provisioning\Packages` directorio del dispositivo IoT. Tras reiniciar el dispositivo, se ejecutará el paquete y el dispositivo iniciará el proceso de inscripción.

#### <a name="adding-package-to-image"></a>Agregando paquete a la imagen

Consulte [Agregar un paquete de aprovisionamiento a una imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image). Al iniciarse por primera vez, el dispositivo ejecutará el paquete e iniciará el proceso de inscripción.
