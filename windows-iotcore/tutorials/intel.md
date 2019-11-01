---
title: Configuración de dispositivos Intel
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo Intel con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Intel
ms.custom: RS5
ms.openlocfilehash: 3f92f9af4ddb492b1f465ee00b55e88e16b3a67f
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918508"
---
# <a name="setting-up-an-intel-device"></a>Configuración de un dispositivo Intel

Si lo que quiere es fabricar con un dispositivo Qualcomm, consulte la [guía de fabricación de IoT Core](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No se pueden usar imágenes del creador para la fabricación.

> [!NOTE]
> Para asegurarse de que el dispositivo ahora arranca desde la memoria eMMC, escriba de nuevo la configuración del BIOS y cambie el orden de la unidad de arranque para que se cargue desde el disco duro en lugar de la unidad USB.

## <a name="using-emmc"></a>Uso de eMMC

1. Descargue e instale el [kit de evaluación e implementación de Windows](https://docs.microsoft.com/windows-hardware/get-started/adk-install) con la versión de correlación de Windows 10 que se está ejecutando.
2. Inserte una unidad USB en el equipo.
3. Cree una imagen de WinPE con arranque USB:
4. Inicie el entorno de herramientas de implementación y creación de imágenes `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` como un administrador.
5. Cree una copia de trabajo de los archivos de Windows PE. Especifique x86, amd64 o ARM: `Copype amd64 C:\WINPE_amd64`
6. Instale Windows PE en la unidad flash USB, especificando la siguiente letra de unidad de WinPE. Puede encontrar más información [aquí](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive). `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. Para descargar la [imagen de Windows 10 IoT Core](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) haga doble clic en el archivo ISO descargado y localice la unidad de Virtual CD montada.
8. Esta unidad contendrá un archivo de instalación (.msi); haga doble clic en él. Esto creará un directorio en el equipo en C:\Archivos de programa (x86)\Microsoft IoT\FFU\ en el que debería ver un archivo de imagen, "flash.ffu".
9. Descargue, descomprima y copie el [script de instalador eMMC](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) al directorio raíz del dispositivo USB, junto con la FFU del dispositivo.
10. Conecte la unidad USB, el ratón y el teclado al concentrador USB. Conecte la pantalla HDMI al dispositivo, el dispositivo al concentrador USB y el cable de alimentación al dispositivo.
11. Vaya a la configuración del BIOS del dispositivo. Seleccione *Windows* como el sistema operativo y establezca el dispositivo para que arranque desde la unidad USB. Cuando se reinicie el sistema, verá el símbolo del sistema de WinPE. Cambie el símbolo del sistema de WinPE a la unidad USB. Suele ser C: o D:, pero puede que necesite probar otras letras de unidad.
12. Ejecute el script del instalador de eMMC, que instalará la imagen de Windows 10 IoT Core en la memoria eMMC del dispositivo. Cuando haya terminado, presione cualquier tecla y ejecute `wpeutil reboot`. El sistema debe arrancar en Windows 10 IoT Core, iniciar el proceso de configuración y cargar la aplicación predeterminada.

## <a name="connect-to-a-network"></a>Conexión a una red

### <a name="wired-connection"></a>Conexión por cable
Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.

### <a name="wireless-connection"></a>Conexión inalámbrica
Si el dispositivo admite la conectividad Wi-Fi y le ha conectado una pantalla, deberá hacer lo siguiente:

1. Vaya a la aplicación predeterminada y haga clic en el botón de configuración situado junto al reloj.
2. En la página de configuración, seleccione _Network and Wi-Fi_ (Redes y Wi-Fi).
3. El dispositivo realizará una exploración de redes inalámbricas.
4. Una vez que la red aparezca en esta lista, selecciónela y haga clic en _Conectar_.

Si no se ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá hacer lo siguiente:

1. Vaya al Panel de IoT y haga clic en _Mis dispositivos_.
2. Busque la placa no configurada en la lista. El nombre empieza por "AJ_"… (por ejemplo, AJ_58EA6C68). Si la placa no aparece después de unos minutos, intente reiniciarla.
3. Haga clic en _Configurar dispositivo_ y escriba las credenciales de red. Esto conectará la placa a la red.

> [!NOTE]
> La Wi-Fi debe estar activada en el equipo para poder buscar otras redes.

## <a name="connect-to-windows-device-portal"></a>Conexión al Portal de dispositivos Windows

Use el [Portal de dispositivos Windows](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles. 


