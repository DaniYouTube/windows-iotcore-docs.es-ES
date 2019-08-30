---
title: Miracast en IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/30/2017
ms.topic: article
description: Obtenga información sobre cómo incluir funcionalidades de Miracast en el dispositivo
keywords: Windows IOT, miracast, conectividad
ms.openlocfilehash: c58def4b218d35c78532f54df4a74fb572c8549e
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168112"
---
# <a name="miracast-on-iot-core"></a>Miracast en IoT Core

Este documento le mostrará cómo incluir la funcionalidad de Miracast en el dispositivo de IoT Core.

> [!IMPORTANT]
> Esta característica solo está disponible en la compilación Insider 17093 y versiones posteriores.

## <a name="miracast-overview"></a>Información general de Miracast

Una conexión Miracast se compone de dos componentes: el origen y el receptor. El **origen de miracast** envía contenido al **receptor de miracast**, que muestra el contenido. Para crear la conexión, el receptor se anuncia a la red Wi-Fi conectada. El origen usa el **selector de dispositivos** para seleccionar el receptor y solicitar una conexión. Una vez solicitada la conexión, un usuario del receptor recibe una alerta que indica que el origen está intentando establecer una conexión y debe comprobar que la conexión debe realizarse. Cuando esto ocurre, el origen comienza la conversión al receptor hasta que el origen cancela la conexión o el receptor detiene la publicidad.

## <a name="hardware-requirements"></a>Requisitos de hardware

Los dispositivos de origen y receptor requieren controladores y chipsets de Wi-Fi y gráficos compatibles con Miracast para funcionar correctamente. Para averiguar si el dispositivo tiene hardware compatible con Miracast, ejecute: 
```
netsh wlan show driver
```
en el símbolo del sistema del dispositivo.

Si el dispositivo admite Miracast, debería ver el siguiente resultado:

![Salida de dispositivo compatible](../media/Miracast/CompatibleDevice.png)

En la tabla siguiente se muestra la compatibilidad de Miracast con las plataformas de referencia de IoT Core:

| Panel | Seg | Controladores de WiFi presentes | Controladores de gráficos presentes | Compatible con Miracast |
|-------|-----|----------------------|--------------------------|---------------------|
| Qualcomm Dragonboard 410C | Snapdragon 410 | Sí | Sí | Sí |
| Raspberry pi 2/3 | Broadcom BCM283x | Sí | No | Sin |
| Minnowboard Max | E3825 de Intel Atom | Sí | No | Sin |
| ARRIBA cuadrada | N3350 de Intel Celeron | Sí | Sí | Sí |


### <a name="wi-fi"></a>Wi-Fi

El controlador de Wi-Fi y el chipset del dispositivo deben ser compatibles con Wi-Fi Direct, entre otras funcionalidades, para admitir Miracast. Si el dispositivo no tiene estas características, puede usar una llave Wi-Fi USB en su lugar. Se recomienda el [adaptador USB inalámbrico de 300 m](http://a.co/fdhEhV9).

### <a name="graphics"></a>Gráficos

El controlador de gráficos y el chipset deben admitir la codificación y descodificación de h. 264 para admitir Miracast. Si el dispositivo no tiene un controlador de gráficos compatible o un chipset, tendrá que elegir un dispositivo nuevo. Consulte la matriz anterior al elegir un dispositivo compatible con Miracast.

## <a name="windows-iot-as-a-miracast-sink"></a>Windows IoT como receptor de Miracast

Para habilitar el dispositivo como un receptor de Miracast, deberá habilitar la aplicación Connect en el dispositivo y, a continuación, habilitar Miracast en el registro.

### <a name="enable-the-connect-app"></a>Habilitación de la aplicación Connect

Para habilitar la aplicación de conexión, debe incluir la característica **IOT_MIRACAST_RX_APP** en la imagen. También deberá incluir **Microsoft-Connect-package. cab** y **Microsoft-Connect-Package_Lang_XXXX. cab** en la imagen (donde XXXX es un idioma, es decir, "Enus"). 

Consulte [esta página](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board#update-the-feature-manifest) para obtener más detalles sobre cómo agregar características y paquetes a la imagen. También puede cargar el paquete y las características en las imágenes existentes siguiendo [estas instrucciones](https://docs.microsoft.com/windows/iot-core/build-your-image/createinstallpackage). Tenga en cuenta que esta característica impedirá que se reciban actualizaciones en la instalación en paralelo.


### <a name="enable-miracast"></a>Habilitar Miracast

Conéctese al dispositivo a través de [PowerShell](https://docs.microsoft.com/windows/iot-core/connect-your-device/powershell) o el [portal de dispositivos de Windows](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) y ejecute los siguientes comandos:
```
reg add HKLM\Software\Microsoft\PlayToReceiver /v AutoEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v  ConsentToast /t REG_DWORD /d 0  
reg add HKLM\Software\Microsoft\MiracastReceiver /v NetworkQualificationEnabled /t REG_DWORD /d 1  
reg add HKLM\Software\Microsoft\MiracastReceiver /v EnabledOnACOnly /t REG_DWORD /d 1  
```
Esto habilitará Miracast sin ninguna notificación de consentimiento, solo en redes seguras y solo mientras esté conectado a la corriente a/C. Esta es la manera recomendada de ejecutar un receptor de Miracast en IoT Core.

## <a name="windows-iot-as-a-miracast-source"></a>Windows IoT como origen de Miracast

> [!IMPORTANT]
> Antes de intentar usar el dispositivo como origen de Miracast, desactive la aplicación IoTOnboardingTask del portal de [dispositivos de Windows](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) como se muestra a continuación, que solo necesitará hacer una vez: ![Desactivar la aplicación IoTOnboardingTask](../media/Miracast/IoTOnboardingOff.gif)
>
> Después, reinicie el dispositivo.

Puede configurar la conversión de Miracast en el dispositivo compatible a través de las API `Windows.Media.Casting` públicas desde el espacio de nombres de la aplicación.

Para ver estas API en acción, descargue el [ejemplo de UWP de BasicMediaCasting](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicMediaCasting) y ejecútelo en el dispositivo. Las API del ejemplo cubren los escenarios siguientes, que se ejecutan en dispositivos IoT Core compatibles con Miracast:
1. Conversión de multimedia básica, que usa la conversión integrada para enviar contenido a dispositivos Miracast, DLNA y Bluetooth
2. Conversión mediante el selector de conversión, que permite personalizar aún más el selector de dispositivos
3. Conversión mediante un selector personalizado, que muestra cómo crear una experiencia de usuario personalizada para seleccionar dispositivos

> [!NOTE]
> Algunos receptores de Miracast (Surface Laptop, Surface Hub, PC con un adaptador de pantalla inalámbrico) no son compatibles con los dispositivos de conversión de IoT Core. Se recomienda usar el [adaptador de pantalla inalámbrica de Microsoft](https://www.microsoft.com/accessories/en-us/products/adapters/wireless-display-adapter-2/p3q-00001) con un monitor compatible como receptor de Miracast.
