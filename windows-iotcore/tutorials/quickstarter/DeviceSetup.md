---
title: Configuración del dispositivo
ms.date: 04/10/2018
ms.topic: article
description: Obtenga información sobre cómo configurar el dispositivo con Windows 10 IoT Core mediante una tarjeta SD.
keywords: Windows 10 IoT Core, tarjeta SD, Panel de Windows 10 IoT Core
ms.custom: RS5
ms.openlocfilehash: 7575889b94cf7a69550c5c4128ab5ff8a82dde9c
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721840"
---
# <a name="setting-up-your-device"></a>Configuración del dispositivo

Debajo encontrará cuatro maneras diferentes para instalar una imagen en el dispositivo con Windows 10 IoT Core. Basándose en el gráfico incluido en la [lista de placas sugeridas para la creación de prototipos](PrototypeBoards.md), siga las instrucciones adecuadas. Use la columna derecha para navegar entre estos dos métodos diferentes de instalación de imágenes.

> [!IMPORTANT]
> No use las imágenes del creador con fines comerciales. Si se comercializa un dispositivo, debe usar una FFU personalizada para una seguridad óptima. Obtenga más información [aquí](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).

> [!IMPORTANT]
> Cuando aparezca el mensaje emergente "formatear el disco", _no_ lo formatee. Estamos trabajando en una solución para este problema.

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a>Mediante el Panel de IoT (Raspberry Pi, MinnowBoard, NXP)

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> El firmware de 64 bits más reciente para MinnowBoard Turbot se puede encontrar en el [sitio web de MinnowBoard](https://minnowboard.org/tutorials/updating-the-firmware) (omita el paso 4 en las instrucciones del sitio de MinnowBoard).

> [!IMPORTANT]
> NXP solo admite imágenes personalizadas. Si lo que busca es instalar una imagen personalizada, seleccione "Personalizada" en la lista desplegable de la compilación del sistema operativo, siga las instrucciones [aquí](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para crear una imagen básica y siga el resto de las siguientes instrucciones para finalizar.

> [!NOTE]
> El panel de información no se puede utilizar para configurar Raspberry Pi 3B+. Si tiene un dispositivo 3B+, debe usar la [versión preliminar técnica de 3B+](https://www.microsoft.com/software-download/windowsiot). Consulte las [limitaciones conocidas](https://docs.microsoft.com/windows/iot-core/troubleshooting) de la versión preliminar técnica para determinar si esto es adecuado para el desarrollo.

> [!TIP]
> Se recomienda usar una tarjeta SD de alto rendimiento, como una tarjeta SD SanDisk, para una mayor estabilidad, así como conectar el dispositivo en una pantalla externa para ver cómo arranca la aplicación predeterminada.


1. Descargue el Panel de Windows 10 IoT Core [aquí](https://docs.microsoft.com/windows/iot-core/downloads).
2. Una vez descargado, abra el panel y haga clic en _configurar un nuevo dispositivo_ y luego inserte una tarjeta SD en el equipo.
3. Rellene todos los campos como se indica.
4. Acepte los términos de licencia y, después, haga clic en _Descargar e instalar_. Verá que Windows 10 IoT Core instala una imagen en la tarjeta SD.


![Captura de pantalla del panel.](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a>Mediante el Panel de IoT (DragonBoard 410c)

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> Se recomienda conectar el dispositivo en una pantalla externa para ver cómo arranca la aplicación predeterminada.

> [!IMPORTANT]
> Si lo que busca es instalar una imagen personalizada, seleccione "Personalizada" en la lista desplegable de la compilación del sistema operativo, siga las instrucciones [aquí](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) para crear una imagen básica y siga el resto de las siguientes instrucciones para finalizar.

> [!IMPORTANT]
> Cuando trabaja con un nuevo dispositivo DragonBoard, viene con Android instalado. Deberá borrar y cargar el dispositivo mediante el método de instalación de imagen eMMC.

> [!NOTE]
> Si experimenta problemas relacionados con el audio con DragonBoard, le recomendamos que consulte el manual de Qualcomm [aquí](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf). 

1. Descargue el Panel de Windows 10 IoT Core [aquí](https://docs.microsoft.com/windows/iot-core/downloads).
2. Una vez descargado, abra el panel y seleccione "Qualcomm DragonBoard 410c". Luego, _inicie sesión como Windows Insider_. Debe haber iniciado sesión como una persona interna con el fin de instalar una imagen en DragonBoard 410c. 
3. Conecte la placa de Qualcomm a la máquina del desarrollador mediante un cable microUSB.
4. Encienda el dispositivo DragonBoard con una fuente de alimentación de 12 V (> 1 A) mientras mantiene presionado el botón de subir volumen (+). El dispositivo, cuando se conecta a una pantalla, debe mostrar la imagen de un martillo, un rayo y un engranaje. 
5. Ahora, el dispositivo debe estar visible en el panel, como se muestra debajo. Seleccione el dispositivo correspondiente.
6. Acepte los términos de licencia de software y, después, haga clic en _Descargar e instalar_. Verá que Windows 10 IoT Core instala una imagen en el dispositivo.


![DragonBoard en modo sobrescribir](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a>Instalación de una imagen con eMMC (para DragonBoard 410c y otros dispositivos de Qualcomm)

1. Descargue e instale la herramienta de actualización de DragonBoard para la máquina [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) o [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip).
2. Descargue la [FFU de DragonBoard de Windows 10 IoT Core](https://developer.microsoft.com/windows/iot/Downloads).
3. Haga doble clic en el archivo ISO descargado y busque la unidad de Virtual CD montada. Esta unidad contendrá un archivo de instalador (.msi); haga doble clic en él. Esto crea un directorio en el equipo en  `C:\Program Files (x86)\Microsoft IoT\FFU\` donde debería ver un archivo de imagen, "flash.ffu".
4. Asegúrese de que DragonBoard está en modo de descarga estableciendo que el primer arranque cambie en la placa a arranque de USB, como se muestra debajo. Luego, conecte DragonBoard al equipo host a través de un cable microUSB y, después, conecte DragonBoard a una fuente de alimentación de 12 V (> 1 A).
5. Inicie la herramienta de actualización de DragonBoard, que debe detectar que DragonBoard se conecta al equipo con un círculo verde. Haga clic en "Examinar" en la FFU del DragonBoard que ha descargado y, después, haga clic en el botón _Programa_.
6. Haga clic otra vez en "Examinar" y seleccione "rawprogram0.xml", que se ha generado en el paso 5. Luego haga clic en el botón "Programa".
7. Una vez completada la descarga, desconecte la fuente de alimentación y el cable microUSB de la placa y cambie el conmutador de arranque USB a _OFF_. Conecta una pantalla HDMI, un ratón y un teclado a DragonBoard y vuelve a conectar la fuente de alimentación. Pasados unos minutos, debería ver la aplicación predeterminada Windows 10 IoT Core. 

![DragonBoard en modo de descarga](../../media/DeviceSetup/db1.png)

> [!NOTE]
> Para asegurarse de que el dispositivo ahora arranca desde la memoria eMMC, escriba de nuevo la configuración del BIOS y cambie el orden de la unidad de arranque para que se cargue desde el disco duro en lugar de la unidad USB.


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a>Instalación de una imagen con eMMC (para UP Squared y otros dispositivos de Intel)

#### <a name="download-and-install-tools"></a>Descarga e instalación de herramientas

1. Descargue e instale el [kit de evaluación e implementación de Windows](https://docs.microsoft.com/windows-hardware/get-started/adk-install) (Windows ADK) con la versión de correlación de Windows 10 que se está ejecutando en su equipo.
2. Descargue e instale el [complemento de Windows PE para el ADK](https://go.microsoft.com/fwlink/?linkid=2087112).

#### <a name="create-a-usb-bootable-windows-pehttpsdocsmicrosoftcomwindows-hardwaremanufacturedesktopwinpe-intro-image"></a>Creación de una imagen de [Windows PE](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) con arranque USB

3. Inserte una unidad USB en el equipo.
4. Inicie el entorno de herramientas de implementación y creación de imágenes como un administrador. La ruta de instalación predeterminada es `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools\DandISetEnv.bat`.
5. Use [`Copype`](https://docs.microsoft.com/windows-hardware/manufacture/desktop/copype-command-line-options) para crear una copia de trabajo de los archivos de Windows PE. Debe especificar arquitecturas x86, AMD64 o ARM (por ejemplo, `Copype amd64 C:\WINPE_amd64`).
6. Instale Windows PE en la unidad flash USB con [`MakeWinPEMedia`](https://docs.microsoft.com/windows-hardware/manufacture/desktop/makewinpemedia-command-line-options). Debe especificar la unidad USB de destino (por ejemplo, `MakeWinPEMedia /UFD C:\WinPE_amd64 P:`).
7. Para descargar la [imagen de Windows 10 IoT Core](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) haga doble clic en el archivo ISO descargado y localice la unidad de Virtual CD montada.
8. Esta unidad contendrá un archivo de instalación (.msi); haga doble clic en él. Esto creará un directorio en el equipo en `C:\Program Files (x86)\Microsoft IoT\FFU\` donde debería ver un archivo de imagen, `flash.ffu`.
9. Descargue, descomprima y copie el [script de instalador eMMC](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) al directorio raíz del dispositivo USB, junto con la FFU del dispositivo.
10. Conecte la unidad USB, el ratón y el teclado al concentrador USB. Conecte la pantalla HDMI al dispositivo, el dispositivo al concentrador USB y el cable de alimentación al dispositivo.
11. Si fuera necesario, vaya a la configuración del BIOS del dispositivo. Seleccione *Windows* como el sistema operativo y establezca el dispositivo para que arranque desde la unidad USB. Cuando se reinicie el sistema, verá el símbolo del sistema de WinPE. Cambie el símbolo del sistema de WinPE a la unidad USB. Suele ser C: o D:, pero puede que necesite probar otras letras de unidad.
12. Ejecute el script del instalador de eMMC, que instalará la imagen de Windows 10 IoT Core en la memoria eMMC del dispositivo. Cuando haya terminado, presione cualquier tecla y ejecute `wpeutil reboot`. El sistema debe arrancar en Windows 10 IoT Core, iniciar el proceso de configuración y cargar la aplicación predeterminada.

> [!NOTE]
> Para asegurarse de que el dispositivo ahora arranca desde la memoria eMMC, escriba de nuevo la configuración del BIOS y cambie el orden de la unidad de arranque para que se cargue desde el disco duro en lugar de la unidad USB.


## <a name="connecting-to-a-network"></a>Conexión a una red

#### <a name="wired-connection"></a>Conexión por cable
Si el dispositivo viene con un puerto Ethernet o con compatibilidad de adaptador Ethernet USB para habilitar una conexión por cable, conecte un cable Ethernet para conectarse a la red.

#### <a name="wireless-connection"></a>Conexión inalámbrica
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
> En el equipo la Wi-Fi debe estar activada para poder buscar otras redes.

## <a name="connecting-to-windows-device-portal"></a>Conexión a Portal de dispositivos Windows

Use el [Portal de dispositivos Windows](../../manage-your-device/DevicePortal.md) para conectar el dispositivo mediante un explorador web. El portal de dispositivos ofrece funciones de configuración y administración de dispositivos muy útiles. 

