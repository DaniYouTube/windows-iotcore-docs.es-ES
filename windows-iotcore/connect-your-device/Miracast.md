---
title: Miracast en IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: Obtenga información sobre cómo incluir Miracast capacidades del dispositivo
keywords: Windows iot, miracast, conectividad
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515240"
---
# <a name="miracast-on-iot-core"></a>Miracast en IoT Core

Este documento le mostrará cómo incluir la funcionalidad de Miracast en el dispositivo de IoT Core.

> [!IMPORTANT]
> Esta característica solo está disponible en 17093 de compilación de Insider y versiones posteriores

## <a name="miracast-overview"></a>Información general de Miracast

Una conexión de Miracast está formada por dos componentes: el origen y el receptor. El **Miracast origen** envía el contenido a la **Miracast receptor**, que muestra el contenido. Para crear la conexión, el receptor se anuncia a la red Wi-Fi conectada. El origen usa la **selector de dispositivo** para seleccionar el receptor y solicita una conexión. Una vez que se solicita la conexión, un usuario en el receptor recibe una alerta que está intentando realizar una conexión y que debe comprobar que la conexión debe tener lugar. Una vez que esto sucede, el origen comienza conversión al receptor hasta que la conexión cancela el origen o el receptor deja de publicidad.

## <a name="hardware-requirements"></a>Requisitos de hardware

Tanto de origen y receptor dispositivos requieren Miracast-compatible con controladores Wi-Fi y los gráficos y conjuntos de chips funcione correctamente. Para averiguar si el dispositivo tiene hardware compatible con Miracast, ejecute: 
```
netsh wlan show driver
```
en la línea de comandos del dispositivo.

Si el dispositivo es compatible con Miracast, debería ver la salida siguiente:

![Salida de un dispositivo compatible](../media/Miracast/CompatibleDevice.png)

La tabla siguiente muestra la compatibilidad de Miracast para las plataformas de referencia de IoT Core:

| Panel | SoC | Presentan controladores Wi-Fi | Presentan los controladores de gráficos | Compatible con Miracast |
|-------|-----|----------------------|--------------------------|---------------------|
| QUALCOMM Dragonboard 410c | Snapdragon 410 | Sí | Sí | Sí |
| Raspberry Pi 2/3 | Broadcom BCM283x | Sí | No | No |
| Minnowboard máx. | Intel Atom E3825 | Sí | No | No |
| HASTA al cuadrado | Intel Celeron N3350 | Sí | Sí | Sí |


### <a name="wi-fi"></a>Wi-Fi

El controlador de Wi-Fi y el conjunto de chips para el dispositivo deben admitir Wi-Fi Direct, entre otras funciones, para admitir Miracast. Si el dispositivo no tiene estas características, puede usar una llave USB Wi-Fi en su lugar. Se recomienda la [300 M inalámbrica USB adaptador](http://a.co/fdhEhV9).

### <a name="graphics"></a>Gráficos

El controlador de gráficos y el conjunto de chips deben admitir h.264 codificación y descodificación para admitir Miracast. Si el dispositivo no tiene un controlador de gráficos compatible o un conjunto de chips, tendrá que elegir un nuevo dispositivo. Consulte la matriz anterior al elegir un dispositivo compatible con Miracast.

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT como un receptor de Miracast

Para habilitar el dispositivo como un receptor de Miracast, deberá habilitar la aplicación conectar en el dispositivo y vuelva a habilitarla Miracast en el registro.

### <a name="enable-the-connect-app"></a>Habilitar la conexión de aplicación

Para habilitar la aplicación conectar, deberá incluir el **IOT_MIRACAST_RX_APP** característica a la imagen. También deberá incluir **Microsoft-conectarse-Package.cab** y **Package_Lang_XXXX.cab conectar Microsoft** en la imagen (donde XXXX es un lenguaje, es decir, "enUS"). 

Consulte [esta página](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) para obtener más información acerca de cómo agregar características y paquetes a la imagen. Se pueden también transferir localmente el paquete y las características de las imágenes existentes siguiendo [estas instrucciones](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage). Tenga en cuenta que esta característica de instalación de prueba impedirá que pueda recibir actualizaciones.


### <a name="enable-miracast"></a>Habilitar Miracast

Conectarse al dispositivo a través de [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) o [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) y ejecute los siguientes comandos:
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
Esto le permitirá Miracast sin una notificación de consentimiento, solo en redes seguras y solo mientras esté conectado a la potencia de aire acondicionado. Se trata de la manera recomendada para ejecutar un receptor de Miracast en IoT Core.

## <a name="windows-iot-as-a-miracast-source"></a>Windows IoT como un origen de Miracast

> [!IMPORTANT]
> Antes de intentar usar el dispositivo como un origen de Miracast, desactive la aplicación IoTOnboardingTask desde el [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) tal como se muestra a continuación, que solo necesitará hacer una vez: ![Desactivar aplicación IoTOnboardingTask](../media/Miracast/IoTOnboardingOff.gif)
>
> Después, reinicie el dispositivo

Puede configurar Miracast conversión en el dispositivo compatible a través de las API públicas desde la `Windows.Media.Casting` espacio de nombres en la aplicación.

Para ver estas API en acción, descargue el [ejemplo BasicMediaCasting UWP](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) y ejecutarlo en el dispositivo. Las API en el ejemplo abarcan los escenarios siguientes, todos se ejecutan en dispositivos IoT compatible con Miracast Core:
1. Conversión de medios básica, que usa la conversión integrada para enviar contenido a los dispositivos Bluetooth, Miracast y DLNA
2. Realiza la conversión mediante el selector de conversión, que le permite personalizar aún más el selector de dispositivos
3. Realiza la conversión mediante un selector personalizado, que muestra cómo crear la experiencia de usuario personalizada para seleccionar los dispositivos

> [!NOTE]
> Algunos receptores Miracast (Surface Laptop, Surface Hub, PC con un adaptador de pantalla inalámbrica) no son compatibles con dispositivos de IoT Core la conversión. Se recomienda usar la [adaptador de pantalla de Microsoft Wireless](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) con un monitor compatible como receptor Miracast.
