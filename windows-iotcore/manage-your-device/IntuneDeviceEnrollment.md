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
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>Inscripción de dispositivos Windows IoT Core en Microsoft Intune

Su empresa puede administrar dispositivos IoT Core junto con todos los demás dispositivos administrados. Esto le ofrece una manera coherente de administrar IoT Core, IoT Enterprise y otros dispositivos Windows con Intune.

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>Cómo inscribir un dispositivo IoT Core en Intune

La inscripción de Intune de un dispositivo de IoT Core se realiza mediante el panel de Windows IoT Core para preparar el dispositivo y, a continuación, mediante el diseñador de configuración de Windows para crear un paquete de aprovisionamiento.

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>Cambiar el ámbito de usuario de MDM de Intune en Azure AD

1. Inicie sesión en el [Azure portal](https://portal.azure.com)y, a continuación, seleccione **Azure Active Directory**.
2. Seleccione **movilidad (MDM y MAM)** .

     ![Selección de movilidad y Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. Seleccione **Microsoft Intune**. En la página **configurar Microsoft Intune** , junto a **ámbito de usuario de MDM**, seleccione **todo**. Esto permitirá que el usuario del dispositivo de IoT Core se inscriba en Intune después de unirse Azure AD.

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>Creación de una tarjeta SD de instalación para el dispositivo IoT Core

1. Inserte una tarjeta de microSD en el lector de tarjetas del equipo.
     > [!NOTE]
     > Durante este proceso se formateará la tarjeta microSD, por lo que se eliminarán todos los datos de la tarjeta.
2. Vaya al [Panel de Windows IOT Core](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) para descargar e instalar el panel.
3. Una vez instalado el panel, ábralo y seleccione **configurar un nuevo dispositivo**.

     ![Panel de Windows IoT Core](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. Escriba un **nombre de dispositivo**.
5. Escriba una nueva contraseña de administrador.
6. Si desea habilitar Wi-Fi para el dispositivo, seleccione la casilla **conexión de red Wi-Fi** . Omitir esta información si el dispositivo va a usar solo una conexión de red Ethernet.

     ![Casilla Wi-Fi en el panel de IoT](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. Active la casilla acepto **los términos de licencia de software** y, a continuación, seleccione **Descargar e instalar**.
8. Cuando aparezca el mensaje de confirmación, seleccione la opción para **dar formato** a la tarjeta SD.
     > [!NOTE]
     > Vea el mensaje de confirmación de **formato** durante la instalación. El mensaje puede estar oculto por otra aplicación abierta, pero es importante seleccionar la opción Format. Si la unidad no tiene el formato correcto, se producirá un error de arranque.
9. Aparece el mensaje **la tarjeta SD está lista** .

     ![Mensaje listo para tarjeta SD](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. Minimice esta página.  Volverá a ella más adelante.

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>Creación de un paquete de aprovisionamiento para la inscripción de Intune

1. Instale la aplicación de diseño de configuración de Windows siguiendo los pasos descritos en [instalar el diseñador de configuración de Windows](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).

2. Abra el **Diseñador de imágenes y configuraciones de Windows**.
3. Elija **aprovisionar dispositivos de escritorio** para crear un proyecto.

     ![Elección del aprovisionamiento de servicios de escritorio](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. Escriba los **detalles del proyecto** como desee. Después, seleccione **Finalizar**.
5. Vaya a la página de **Administración de cuentas** y seleccione **inscribirse en Azure ad**.
     > [!NOTE]
     > La instalación de la aplicación desde el Microsoft Store o Windows Assessment and Deployment Kit (ADK) es correcta.

     ![Elección de la inscripción en Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. Junto a expiración de tokens en **masa**, especifique una fecha de expiración de tokens en masa.
7. Seleccione **obtener token en masa**. Aparece un mensaje de inicio de sesión para conectarse a Azure AD.

     ![Azure AD página de inicio de sesión](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. Escriba el nombre de usuario del inquilino ( john@mycompany.onmicrosoft.compor ejemplo,) y la contraseña.
9. Acepte que la aplicación de diseño de configuración de Windows pueda acceder a la información de Azure AD.
10. Un mensaje en la página muestra que el token de AAD en masa se ha recuperado correctamente.

     ![Mensaje de token en masa correcto](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. Seleccione **cambiar a editor avanzado**y, a continuación, seleccione *sí*.

     ![Cambiar a la página de confirmación del editor avanzado](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. En **personalizaciones seleccionadas**, deje la configuración de la **cuenta** , pero Quite todas las demás configuraciones:
13. Seleccione **Oobe**y, a continuación, seleccione **quitar**.
14. Si aparece **SharedPC** , selecciónelo y, a continuación, seleccione **quitar**.

     ![Quitar personalizaciones](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. Seleccione **exportar**y, a continuación, elija **paquete de aprovisionamiento**.

     ![Elegir el paquete de aprovisionamiento](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. En la página siguiente, acepte la configuración predeterminada y seleccione **siguiente**.
17. De nuevo, en la página siguiente, acepte la configuración predeterminada y seleccione siguiente.
18. Cambie el destino del **paquete de aprovisionamiento** o deje la ruta de acceso predeterminada y, a continuación, seleccione **siguiente**.
19. Seleccionecompilar.
20. Seleccione el vínculo **Ubicación de salida** para que pueda localizar el archivo. ppkg cuando esté listo.

     ![Vínculos de ubicación de salida](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. Seleccione **Finalizar**.
22. Vaya al explorador de archivos y copie el paquete de aprovisionamiento en el dispositivo de IoT Core. Guárdelo en la tarjeta microSD en la unidad **principal** de la carpeta **c:\windows\provisioning\packages** .  Tendrá que conceder permisos para guardar el archivo en esta carpeta.

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>Aprovisionamiento e inscripción del dispositivo IoT Core en Intune

1. Inserte la tarjeta microSD en el dispositivo de IoT Core.
2. Encienda el dispositivo de IoT Core y deje tiempo para que se inicie y muestre la pantalla estándar.
3. Vuelva a la consola de Microsoft Intune en el Azure Portal. El dispositivo debe aparecer en la lista de dispositivos.
     > [!NOTE]
     > La inscripción podría tardar 15 minutos o más en completarse.

     ![Lista de dispositivos de Intune](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>Pasos siguientes

- [Vea los detalles del dispositivo en Intune](https://docs.microsoft.com/intune/device-inventory).
- [Sincronizar el dispositivo para obtener las directivas y las acciones más recientes con Intune](https://docs.microsoft.com/intune/device-sync).
- [Reiniciar el dispositivo de forma remota con Intune](https://docs.microsoft.com/intune/device-restart).
