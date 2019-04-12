---
title: Administración de dispositivos de Windows IoT Core
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las diferentes maneras de administrar dispositivos Windows 10 IoT Core.
keywords: Windows iot, administración de dispositivos, windows iot, Azure DM, Hub de Azure, Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514956"
---
# <a name="managing-windows-iot-core-devices"></a>Administración de dispositivos de Windows IoT Core

Dispositivos Windows 10 IoT Core pueden administrarse mediante un servidor OMA DM MDM tradicional que admite la inscripción basada en certificados o con la administración de dispositivos del centro de IoT de Azure.  

 _Obtener más información acerca de MDM y Windows 10 [aquí](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)._  

Para los dispositivos que se administran mediante un servidor OMA DM las directivas de MDM para Windows 10 IoT Core se alinean con las directivas que se admiten en otras ediciones de Windows 10. Para obtener más información sobre directivas, así como lo que pueden administrarse en dispositivos de IoT Core, vea la referencia del proveedor de servicio de configuración para Windows 10 [aquí](https://aka.ms/csplist). La compatibilidad MDM en Windows 10 se basa en la especificación del protocolo 1.2.1 de administración de dispositivos de Open Mobile Alliance (OMA) (DM).

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>¿Cómo se puede inscribir un dispositivo de IoT Core en un MDM?
___
Inscripción de MDM de un dispositivo de IoT Core se logra mediante un paquete de aprovisionamiento. Paquetes de aprovisionamiento pueden crearse mediante la configuración de imagen de Windows y el diseñador (WICD). Vamos a intentar inscribir un dispositivo en un MDM.

### <a name="creating-a-provisioning-package"></a>Creación de un paquete de aprovisionamiento

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (independiente o Intune + SCCM híbrido)

1. Abra la consola de administración de Configuration Manager (consola de Configuration Manager)

2. Vaya a _activos y compatibilidad > configuración de cumplimiento > acceso a los recursos de la compañía > perfiles de certificado_
   ![perfiles de certificado](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. Haga clic en **Crear perfil de certificado**

4. Proporcione un nombre y una descripción para el perfil
   - Nombre: Certificado raíz de confianza de ejemplo de Configuration Manager
     - Tipo de perfil de certificado: Certificado de CA de confianza  
     ![Certificación de confianza](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. Haz clic en **Siguiente**.

6. Importe el archivo de certificado.

7. Seleccione **almacén de certificados de equipo - raíz** para el **Store de destino**.

8. Haz clic en **Siguiente**.

9. Elija **seleccionar todo** para plataformas admitidas ![plataformas compatibles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. Haga clic en **resumen, Next y cerrar** para salir del asistente.

11. Haga doble clic en el perfil que acaba de crear y haga clic en **exportar**.

12. Haga clic en **examinar**, encontrar una ubicación donde se debe exportar el archivo .ppkg y, a continuación, haga clic en **guardar**.

13. Haga clic en **exportar** y haga clic en **Aceptar** para salir del asistente.

#### <a name="other-mdm-servers"></a>Otros servidores MDM

1. Descargue e instale el [Windows Assessment and Deployment Kit (ADK de Windows)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).

2. Abra el Diseñador de configuración (WICD) y creación de imágenes de Windows.
   ![Diseñador de imágenes y configuraciones de Windows](../media/ManagingDevices/WICD-Start-Page.png)

3. Elija **avanzada de aprovisionamiento**

4. Establecer un nombre para el paquete.

5. Elija la configuración de Windows 10 IoT Core.

6. Omitir el paso del paquete de importación.
   ![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. Vaya al área de trabajo -> inscripciones.

8. En el campo UPN, especifique la cuenta que desea inscribir un dispositivo bajo (es decir, trmck@contoso.co) y haga clic en **agregar**.

   ![Rellenado de inscripciones de área de trabajo](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. Para AuthPolicy elija entre usuario y contraseña en función de autenticación (OnPremises) o autenticación basada en certificados.

10. Escriba la dirección URL de servicio de detección para el servidor MDM.

> [!NOTE]
> Dirección URL del servicio de inscripción y la dirección URL del servicio de directiva son opcionales.

11. Para el secreto ENTRAR  
    - OnPremises: La contraseña de la cuenta que se va a inscribir  
    - Certificado: La huella digital del certificado.
    
    ![Relleno OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. Haga clic en la parte superior de la ventana WICD **Exportar > paquete de aprovisionamiento**.

13. Proporcione un nombre y la versión para el paquete y haga clic en **siguiente**. 

> [!NOTE]
> Asegúrese de incrementar el número de versión para asegurarse de que se ejecuta un paquete actualizado.

14. Haga clic en **siguiente** en el **página de detalles de seguridad**.

15. Elija la ubicación donde se pueda exportar en el equipo local y haga clic en el paquete **siguiente**.

16. Haga clic en **compilar** y, a continuación, **finalizar** para salir del asistente.

### <a name="installing-the-provisioning-package"></a>Instalar el paquete de aprovisionamiento

Hay varias maneras en que se puede implementar un paquete de aprovisionamiento en un dispositivo de IoT. Es posible implementar un paquete copiando el paquete en el dispositivo o agregando el paquete a la imagen durante el proceso de creación de imágenes.

#### <a name="copying-package-to-device"></a>Copiar el paquete al dispositivo

Tomar el paquete de aprovisionamiento que se haya exportado desde SCCM o WICD y copie el archivo .ppkg `C:\Windows\Provisioning\Packages` directorio en el dispositivo de IoT. Tras reiniciar el dispositivo se ejecutará el paquete y el dispositivo iniciará el proceso de inscripción.

#### <a name="adding-package-to-image"></a>Agregar paquete de imagen

Consulte [agregar un paquete de aprovisionamiento a una imagen](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image). Tras el primer arranque el dispositivo se ejecute el paquete e iniciar el proceso de inscripción.
