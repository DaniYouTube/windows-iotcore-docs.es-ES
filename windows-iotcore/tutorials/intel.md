---
title: Configuración de dispositivos Intel
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo Intel con Windows 10 IoT Core.
keywords: Windows 10 IoT Core, Intel
ms.custom: RS5
ms.openlocfilehash: a42771d82ffbebee9a45a72c5256479f5f611388
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182187"
---
# <a name="setting-up-an-intel-device"></a>Cómo configurar un dispositivo Intel

Si busca para fabricar con un dispositivo de Qualcomm, consulte el [IoT Core fabricación guía](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide). No puede usar imágenes de creador de fabricación.

> [!NOTE]
> Asegúrese de que el dispositivo ahora consiste en arrancar desde la memoria eMMC volver a escribir la configuración del BIOS y cambiando el orden de la unidad de arranque cargar de la unidad en lugar de desde la unidad USB.

## <a name="using-emmc"></a>Uso de eMMC

1. Descargue e instale el [kit de evaluación de Windows y la implementación](https://docs.microsoft.com/windows-hardware/get-started/adk-install) con la versión de correlación de Windows 10 que se está ejecutando.
2. Inserte una unidad USB en el equipo.
3. Crear una imagen de WinPE de arranque USB:
4. Iniciar la implementación y el entorno de herramientas de creación de imágenes `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` como administrador.
5. Crear una copia de trabajo de los archivos de Windows PE. Especifique cualquier x86, amd64 o ARM: `Copype amd64 C:\WINPE_amd64`
6. Instale Windows PE en la unidad flash USB, especificando la siguiente letra de unidad de WinPE. Puede encontrar más información [aquí](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive). `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. Descargue el [imagen de Windows 10 IoT Core](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) haciendo doble clic en el archivo ISO descargado y localizar la montado Virtual-unidad de CD.
8. Esta unidad contendrá un archivo de instalación (.msi); Haga doble clic en él. Esto creará un nuevo directorio en su equipo bajo \Microsoft IoT\FFU\ C:\Program Files (x86) en el que se shoul d. ver un archivo de imagen "flash.ffu".
9. Descargar, descomprima y copie el [eMMC script del instalador](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) al directorio raíz del dispositivo USB, junto con FFU del dispositivo.
10. Conecte la unidad USB, mouse y teclado para el concentrador USB. Adjunte la presentación HDMI al dispositivo, el dispositivo al concentrador USB y el cable de alimentación al dispositivo.
11. Vaya a la configuración del BIOS del dispositivo. Seleccione *Windows* como el sistema operativo y establezca el dispositivo para que arranque desde la unidad uSB. Cuando se reinicia el sistema, verá el símbolo del sistema de WinPE. Cambiar el indicador de WinPE en la unidad USB. Esto suele ser C: o D:, pero puede que necesite probar otras letras de unidad.
12. Ejecute el script del instalador, que se instalará la imagen de Windows 10 IoT Core en la memoria del dispositivo eMMC eMMC. Cuando haya terminado, presione cualquier tecla y ejecute `wpeutil reboot`. El sistema debe arrancar en Windows 10 IoT Core, inicie el proceso de configuración y cargar la aplicación predeterminada.

## <a name="connect-to-a-network"></a>Conectarse a una red

### <a name="wired-connection"></a>Conexión con cable
Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.

### <a name="wireless-connection"></a>Conexión inalámbrica
Si el dispositivo admite la conectividad mediante Wi-Fi y ha conectado una pantalla a él, deberá:

1. Vaya a la aplicación de forma predeterminada y haga clic en el botón Configuración situado junto al reloj.
2. En la página de configuración, seleccione _red y Wi-Fi_.
3. El dispositivo realizará un examen para redes inalámbricas.
4. Una vez que la red aparece en esta lista, selecciónelo y haga clic en _Connect_.

Si aún no lo ha conectado a una pantalla y le gustaría conectarse a través de Wi-Fi, deberá:

1. Vaya al panel de IoT y haga clic en _Mis dispositivos_.
2. Encuentre la placa no configurada en la lista. Su nombre comienza con "AJ_"... (por ejemplo, AJ_58EA6C68). Si no ve la placa aparecen después de unos minutos, intente reiniciar la placa.
3. Haga clic en _Configurar dispositivo_ y escriba sus credenciales de red. La placa de esto conectará a la red.

> [!NOTE]
> Wi-Fi en el equipo debe estar activada para poder buscar otras redes.

## <a name="connect-to-windows-device-portal"></a>Conectarse a Windows Device Portal

Use la [Windows Device Portal](../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos. 


