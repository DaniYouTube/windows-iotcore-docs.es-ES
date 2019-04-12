---
title: Inscripción de dispositivos de IoT Core de Windows en Intune
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos con administración de dispositivos de Microsoft Intune y Windows IoT.
keywords: Windows iot, IoT de Azure, administración de dispositivos de Intune, administración de dispositivos
ms.openlocfilehash: 5d75c64813a3e61f60630abd87185949b63e178b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514280"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>Inscripción de dispositivos de Windows IoT Core en Microsoft Intune

Su empresa puede administrar dispositivos de IoT Core junto con todos los demás dispositivos administrados. Esto le ofrece una manera coherente para administrar IoT Core, IoT empresarial y otros dispositivos de Windows con Intune.

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>¿Cómo se puede inscribir un dispositivo de IoT Core en Intune?

Inscripción de Intune de un dispositivo de IoT Core se logra mediante el panel de Windows IoT Core para preparar el dispositivo y, a continuación, mediante el Diseñador de configuración de Windows para crear un paquete de aprovisionamiento.

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>Cambiar el ámbito de usuario de MDM de Intune en Azure AD

1. Inicie sesión en el [portal Azure](https://portal.azure.com)y, a continuación, seleccione **Azure Active Directory**.
2. Seleccione **movilidad (MDM y MAM)**.


~~~
 ![Selecting Mobility and Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)
~~~
1. Seleccione **Microsoft Intune**. En el **configurar Microsoft Intune** página, junto a **el ámbito de usuario MDM**, seleccione **todas**. Esto permitirá que su IoT Core usuario del dispositivo se inscriba en Intune después de unirse a Azure AD.

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>Crear una tarjeta SD de programa de instalación para el dispositivo de IoT Core
1. Inserte una tarjeta microSD en el lector de tarjeta en su PC. 
     > [!NOTE]
     > La tarjeta microSD se formateará durante este proceso, por lo que se eliminarán todos los datos de la tarjeta.
2. Vaya a [Windows IoT Core panel](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) para descargar e instalar el panel.
3. Una vez instalado el panel, ábrala y seleccione **configurar un nuevo dispositivo**.

     ![Panel de Windows IoT Core](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. Escriba un **nombre de dispositivo**.
5. Escriba una nueva contraseña de administrador. 
6. Si desea habilitar Wi-Fi para el dispositivo, seleccione el **conexión de red Wi-Fi** casilla de verificación. Omita este paso si el dispositivo usará sólo una conexión de red ethernet.

     ![Casilla de verificación de Wi-Fi en el panel de IoT](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. Seleccione el **acepto los términos de licencia del software** casilla de verificación y, a continuación, seleccione **descargue e instale**.
8. Cuando aparezca el mensaje de confirmación, seleccione la opción de **formato** la tarjeta SD. 
     > [!NOTE]
     > Esté atento a la **formato** mensaje de confirmación durante la instalación. El mensaje podría estar oculto por otra aplicación abierto, pero es importante seleccionar la opción de formato. Si la unidad no tiene el formato correcto, se producirá un error de arranque.
9. El mensaje **tarjeta SD Your está lista** aparece.

     ![Mensaje listo de la tarjeta SD](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. Minimizar esta página.  Deberá volver a él más adelante.

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>Crear un paquete de aprovisionamiento para la inscripción de Intune
1. Instale la aplicación de diseño de la configuración de Windows siguiendo los pasos descritos en [instalar Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).

2. Abra el **creación de imágenes de Windows y el Diseñador de configuración**.
3. Elija **aprovisionar dispositivos de escritorio** para crear un proyecto 

     ![Elección de servicios de escritorio de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. Escriba el **Project Details** como se desee. A continuación, seleccione **finalizar**.
5. Vaya a la **administración de cuentas** página y seleccione **inscribir en Azure AD**.
      > [!NOTE]
     > Instalación de la aplicación desde la Microsoft Store o el Windows Assessment y Deployment Kit (ADK) está bien.

     ![Elegir inscribir en Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. Junto a **expiración del Token masiva**, escriba una fecha de expiración del token de forma masiva.
7. Seleccione **Get Bulk Token**. Aparece un mensaje de inicio de sesión para conectarse a Azure AD.

     ![Página de inicio de sesión de AD Azure](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. Escriba el nombre de usuario del inquilino (por ejemplo, john@mycompany.onmicrosoft.com) y la contraseña.   
9. Acepta que la aplicación de diseño de la configuración de Windows tener acceso a la información de Azure AD. 
10. Un mensaje en la página se muestra que el token de AAD de forma masiva se capturó correctamente.

     ![Mensaje correcta del token de forma masiva](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. Seleccione **cambie al editor avanzado**y, a continuación, seleccione *Sí*.

     ![Cambie a la página de confirmación del editor avanzado](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. En **personalizaciones seleccionadas**, deje el **cuenta** configuración, quitar, pero las demás opciones:
13. Seleccione **OOBE**y, a continuación, seleccione **quitar**.
14. Si **SharedPC** está en la lista, selecciónelo y, a continuación, seleccione **quitar**.

     ![Eliminación de las personalizaciones](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. Seleccione **exportar**y, a continuación, elija **paquete de aprovisionamiento**.

     ![Elegir el paquete de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. En la página siguiente, acepte la configuración predeterminada y seleccione **siguiente**.
17. De nuevo, en la página siguiente, acepte la configuración predeterminada y seleccione siguiente.
18. Cambiar el **paquete de aprovisionamiento** destino o dejar la ruta de acceso predeterminada y, a continuación, seleccione **siguiente**.
19. Seleccione **compilar**.
20. Seleccione el **ubicación de salida** vincular para que puedan encontrar el archivo .ppkg cuando esté listo.

     ![Vínculos de la ubicación de salida](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. Seleccione **finalizar**.
22. Vaya al explorador de archivos y copie el paquete de aprovisionamiento en el dispositivo de IoT Core. Guárdelo en la tarjeta microSD en la **MainOS** unidad en la **c:\windows\provisioning\packages** carpeta.  Debe conceder permisos para guardar el archivo en esta carpeta.

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>Aprovisione e inscribir el dispositivo de IoT Core en Intune
1. Inserte la tarjeta microSD en el dispositivo de IoT Core.
2. Encienda el dispositivo de IoT Core y deje tiempo para que pueda iniciarse y muestra la pantalla estándar. 
3. Volver a la consola de Microsoft Intune en Azure portal. El dispositivo debe aparecer en la lista de dispositivos.
     > [!NOTE]
     > La inscripción puede tardar 15 minutos o más en completarse.

     ![Lista de dispositivos de Intune](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>Pasos siguientes
- [Consulte los detalles del dispositivo en Intune](https://docs.microsoft.com/intune/device-inventory).
- [Sincronizar el dispositivo para obtener las últimas directivas y acciones con Intune](https://docs.microsoft.com/intune/device-sync).
- [Reiniciar de forma remota el dispositivo con Intune](https://docs.microsoft.com/intune/device-restart).
