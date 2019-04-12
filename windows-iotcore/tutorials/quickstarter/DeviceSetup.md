---
title: Configuración del dispositivo
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo con Windows 10 IoT Core con una tarjeta SD.
keywords: Windows 10 IoT Core, una tarjeta SD, panel de Windows 10 IoT Core
ms.custom: RS5
ms.openlocfilehash: ece83dcc7f6961a4614db2ee0c6a1331b009bb47
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514303"
---
# <a name="setting-up-your-device"></a>Configuración del dispositivo

A continuación encontrará cuatro maneras diferentes para actualizar el dispositivo con Windows 10 IoT Core. Basándose en el gráfico que se incluye en el [lista de paneles sugeridos para la creación de prototipos](PrototypeBoards.md), siga las instrucciones adecuadas. Use la columna derecha para desplazarse entre estos dos métodos diferentes de parpadeo.

> [!IMPORTANT]
> No use maker imágenes para la comercialización. Si se commercializing un dispositivo, debe usar un FFU personalizado para una seguridad óptima. Obtenga más información [aquí](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

> [!IMPORTANT]
> Cuando el "dar formato al disco" pop hasta, hacer _no_ formatear el disco. Estamos trabajando en una solución para este problema.

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a>Mediante el panel de IoT (Raspberry Pi, MinnowBoard, NXP)

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> El firmware más reciente de 64 bits para MinnowBoard Turbot puede encontrarse en el [sitio Web de MinnowBoard](https://minnowboard.org/tutorials/updating-the-firmware) (omita el paso 4 en las instrucciones de la carpeta del sitio MinnowBoard).

> [!IMPORTANT]
> NXP sólo admite imágenes personalizadas. Si lo que busca una imagen personalizada de flash, seleccione "Custom" en la lista desplegable de la compilación del sistema operativo, siga las instrucciones [aquí](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para crear una imagen básica y siga el resto de las siguientes instrucciones para finalizar.

> [!NOTE]
> No se puede utilizar el panel usado para configurar el dispositivo Raspberry Pi 3B +. Si tiene un dispositivo 3B +, debe usar el [vista previa técnica de 3B +](https://www.microsoft.com/en-us/software-download/windowsiot). Consulte la [limitaciones conocidas](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) de technical preview para determinar si esto es adecuado para el desarrollo.

> [!TIP]
> Se recomienda mediante una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk, para mayor estabilidad, así como conectar el dispositivo en una pantalla externa para ver la aplicación predeterminada de arranque.


1. Descargar el panel de Windows 10 IoT Core [aquí](https://docs.microsoft.com/windows/iot-core/downloads).
2. Una vez descargado, abra el panel y haga clic en _configurar un nuevo dispositivo_ e inserte una tarjeta SD en el equipo.
3. Rellene todos los campos como se indica.
4. Acepte los términos de licencia de software y haga clic en _descargue e instale_. Verá que ahora es Windows 10 IoT Core intermitencia en la tarjeta SD.


![Captura de pantalla de panel](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a>Mediante el panel de IoT (DragonBoard 410c)

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> Se recomienda conectar el dispositivo en una pantalla externa para ver la aplicación predeterminada de arranque.

> [!IMPORTANT]
> Si lo que busca una imagen personalizada de flash, seleccione "Custom" en la lista desplegable de la compilación del sistema operativo, siga las instrucciones [aquí](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para crear una imagen básica y siga el resto de las siguientes instrucciones para finalizar.

> [!IMPORTANT]
> Cuando está trabajando con un nuevo Dragonboard, acompañada de Android instalado. Deberá borrar y cargar el dispositivo mediante el método eMMC parpadeante.

> [!NOTE]
> Si experimenta problemas relacionados con el audio con su DragonBoard, le recomendamos que lea manual de Qualcomm [aquí](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf). 

1. Descargar el panel de Windows 10 IoT Core [aquí](https://docs.microsoft.com/windows/iot-core/downloads).
2. Una vez descargado, abra el panel y seleccione "Qualcomm DragonBoard 410c". A continuación, _inicie sesión como un Insider de Windows_. Debe haber iniciado sesión como una persona interna con el fin de flash DragonBoard 410 c. 
3. Conectar la placa de Qualcomm a la máquina de desarrollador mediante un cable microUSB.
4. Encender su Dragonboard mediante un 12V (> 1A) alimentación mientras mantiene presionada (+) para Subir volumen botón. El dispositivo - cuando se conecta a una pantalla - debe aparecer la imagen de un martillo, un rayo y un engranaje. 
5. Ahora, el dispositivo debe estar visible en el panel, como se muestra a continuación. Seleccione el dispositivo adecuado.
6. Acepte los términos de licencia de software y haga clic en _descargue e instale_. Verá que ahora parpadea en su dispositivo Windows 10 IoT Core.


![DragonBoard en modo de flash](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a>La intermitencia con eMMC (para DragonBoard 410c, otros dispositivos de Qualcomm)

1. Descargue e instale la herramienta de actualización DragonBoard para su [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) o [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) máquina.
2. Descargue el [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).
3. Haga doble clic en el archivo ISO descargado y busque la montado Virtual-unidad de CD. Esta unidad contendrá un archivo de instalador (.msi); Haga doble clic en él. Esto crea un nuevo directorio en su equipo bajo `C:\Program Files (x86)\Microsoft IoT\FFU\` en lo que debería ver un archivo de imagen, "flash.ffu".
4. Asegúrese de que su DragonBoard está en modo de descarga estableciendo el primer arranque cambie en el panel a USB de arranque, como se muestra a continuación. Conectar el equipo host a través de un cable microUSB DragonBoard, a continuación, conecte el DragonBoard a un 12V (> 1A) fuente de alimentación.
5. Inicie la herramienta de actualización DragonBoard, que debe detectar que el DragonBoard se conecte al equipo con un círculo verde. "Examinar" para el DragonBoard FFU que ha descargado, a continuación, haga clic en el _programa_ botón.
6. Haga clic en "Examinar" nuevo y seleccione "rawprogram0.xml" que se generó en el paso 5. A continuación, haga clic en el botón "Programa".
7. Una vez completada la descarga, desconecte el cable de alimentación de suministro y microUSB desde el panel y alternar el modificador de arranque USB al _OFF_. Conectar una pantalla HDMI, un mouse y teclado al DragonBoard y rec-onectar la fuente de alimentación. Después de unos minutos, debería ver la aplicación predeterminada de Windows 10 IoT Core. 

![DragonBoard en modo de descarga](../../media/DeviceSetup/db1.png)

> [!NOTE]
> Asegúrese de que el dispositivo ahora consiste en arrancar desde la memoria eMMC volver a escribir la configuración del BIOS y cambiando el orden de la unidad de arranque cargar de la unidad en lugar de desde la unidad USB.


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a>La intermitencia con eMMC (para la seguridad al cuadrado, otros dispositivos de Intel)

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

> [!NOTE]
> Asegúrese de que el dispositivo ahora consiste en arrancar desde la memoria eMMC volver a escribir la configuración del BIOS y cambiando el orden de la unidad de arranque cargar de la unidad en lugar de desde la unidad USB.


## <a name="connecting-to-a-network"></a>Conectarse a una red

#### <a name="wired-connection"></a>Conexión con cable
Si el dispositivo viene con un puerto Ethernet o la compatibilidad del adaptador Ethernet USB para habilitar una conexión con cable, conectar un cable Ethernet para conectarse a la red.

#### <a name="wireless-connection"></a>Conexión inalámbrica
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

## <a name="connecting-to-windows-device-portal"></a>Conectarse a Windows Device Portal

Use la [Windows Device Portal](../../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece configuración valioso y capacidades de administración de dispositivos. 

