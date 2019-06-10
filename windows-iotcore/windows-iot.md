---
title: Descripción general de Windows 10 IoT
author: saraclay
ms.author: saclayt
ms.date: 01/30/2018
ms.topic: article
description: Obtenga información sobre las novedades de Windows 10 IoT y lo que puede hacer con él.
keywords: Windows 10 IoT Enterprise, Windows 10 IoT Core, sin periféricos, voz, características, edición binaria, las ediciones
ms.openlocfilehash: 1e1d2769513005a705c48522d4dc7dc034f5d7b9
ms.sourcegitcommit: dcaeaa6c5e84dd6a4974a56098f3bab151209e41
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66760392"
---
# <a name="an-overview-of-windows-10-iot"></a>Información general de Windows 10 IoT 

> [!NOTE]
> Contenedores de Windows 10 solo pueden usarse con Windows IoT Core y Windows IoT Enterprise para las implementaciones comerciales de uso de Microsoft Azure IoT Edge.

## <a name="what-is-windows-10-iot"></a>¿Qué es Windows 10 IoT?
Windows 10 IoT es un miembro de la familia de Windows 10 que aporta la potencia de clase empresarial, seguridad y facilidad de uso a Internet de las cosas.  Aprovecha de Windows embedded experiencia, ecosistema y en la nube conectividad, lo que permite a las organizaciones crear su Internet de las cosas con dispositivos seguros que se pueden aprovisionar rápidamente, fáciles de administrar y conectados a la perfección a una estrategia de nube global.  

## <a name="windows-10-iot-editions"></a>Ediciones de Windows 10 IoT
Windows 10 IoT está disponible en dos ediciones.  Windows 10 IoT Core es el miembro más pequeño de la familia de sistemas operativos Windows 10.  Aunque solo ejecuta una sola aplicación, aún tiene la capacidad de administración y seguridad que se esperan de Windows 10.  En cambio, Windows 10 IoT Enterprise es una versión completa de Windows 10 con características especializadas para crear dispositivos dedicados bloqueados hasta un conjunto específico de aplicaciones y dispositivos periféricos. 

## <a name="differences-between-windows-10-iot-core-and-windows-10-iot-enterprise"></a>Diferencias entre Windows 10 IoT Enterprise y Windows 10 IoT Core

Aunque Windows 10 IoT Core y Windows 10 IoT Enterprise son similares en nombre, hay diferencias en lo que ofrecen, así como lo admiten. A continuación es una lista de características que se resalta las diferencias de edición.

> |             | Windows 10 IoT Core  |  Windows 10 IoT Enterprise  |
> |-------------|----------|---------|
> | Experiencia del usuario | Una aplicación para UWP en primer plano a la vez (consulte [documentación del Shell de IoT](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoreshell) para el control de aplicación backstack) con compatibilidad con servicios y aplicaciones en segundo plano. | Shell de Windows tradicional con características avanzadas de bloqueo |
> | Sin periféricos compatibles | Sí | Sí |
> | Arquitectura de aplicaciones compatibles | UWP UI sólo | Soporte completo de la interfaz de usuario de Windows (por ejemplo, UWP, WinForms, etcetera) |
> | Cortana | [*SDK de Cortana*](https://developer.microsoft.com/en-us/cortana/devices) | Sí |
> | Unión a un dominio | Sólo AAD | AAD y dominio tradicionales |
> | Management | MDM | MDM |
> | Tecnologías de seguridad del dispositivo | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [Secure Boot, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker)y atestación de estado de dispositivo | [TPM](https://docs.microsoft.com/windows/iot-core/secure-your-device/tpm), [Secure Boot, BitLocker, Device Guard](https://docs.microsoft.com/windows/iot-core/secure-your-device/securebootandbitlocker) y atestación de estado de dispositivo |
> | Compatibilidad con la arquitectura de CPU | x86 x64 y ARM | x86 y x64 |
> | Concesión de licencias | En línea licencias de contrato y acuerdos de OEM incrustado, libre de regalías | Contratos directos e indirectos OEM incrustado |
> | Escenarios de uso | [Señalización digital](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), edificio inteligente, puerta de enlace de IoT, HMI, Home, Smart ponibles | Tabletas del sector, Retail Point of Service, quioscos multimedia, [señalización Digital](https://www.microsoft.com/en-us/windowsforbusiness/digital-signage), ATM, los dispositivos médicos, fabricación, los dispositivos de cliente ligero |

Para obtener detalles de requisitos mínimos, visite [el sitio de Windows Hardware](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview).

Si está interesado en aprender más sobre el punto de servicio, visite la [los documentos de UWP en este tema](https://aka.ms/pointofservice).

## <a name="differences-between-windows-10-desktop-and-windows-10-iot-core"></a>Diferencias entre el escritorio de Windows 10 y Windows 10 IoT Core

### <a name="different-features-available-on-desktop-and-iot-core"></a>Distintas características disponibles en el escritorio y IoT Core

* Inbox Cortana ya no está disponible en Windows 10 IoT Core desde la versión 1809 (17763). Si desea para poner un dispositivo habilitado por voz al mercado rápidamente, puede integrar el soporte técnico de Cortana en el dispositivo mediante el [preview del SDK de dispositivos de Cortana](https://developer.microsoft.com/en-us/cortana/devices).
* El [FileOpenPicker API](https://docs.microsoft.com/en-us/uwp/api/windows.storage.pickers.fileopenpicker) no se admite en Windows 10 IoT Core. Para obtener acceso a las unidades locales o almacenamiento extraíble, puede implementar en su propia aplicación.
* El dispositivo Windows 10 IoT Core arrancará en el [aplicación predeterminada](https://docs.microsoft.com/en-us/windows/iot-core/develop-your-app/iotcoredefaultapp) en lugar de un PC de sobremesa. El propósito de esta aplicación no es solo para proporcionarle un shell descriptivo para interactuar con tras el primer arranque, pero que también le permite usar el [código abierto](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) para esta aplicación para que se pueden usar estas características para de plug and play sus propias aplicaciones personalizadas.

### <a name="differences-in-driver-supported-areas"></a>Diferencias en las áreas compatibles con el controlador

* Windows 10 escritorio más ha admitido controladores de Windows 10 IoT Core. Para que el mismo dispositivos funcionan en Windows 10 IoT Core, como en el escritorio, es posible que necesite compilar un controlador de origen para un dispositivo Windows 10 IoT Core o buscar otra solución alternativa, especialmente para la arquitectura ARM.
* No hay ningún controlador de fábrica para libusb para Windows 10 IoT Core (ARM) - deberá compilar del origen al destino de la arquitectura ARM.

### <a name="differences-in-available-registry-set"></a>Diferencias en el conjunto disponible en el registro

* En el escritorio, hay una opción para "Automáticamente ocultar las barras de desplazamiento en Windows" que se pueden establecer en off. Se controla mediante la entrada del registro siguiente: 

```
HKEY_CURRENTUSER\Control Panel\Accessibility
```

* No hay ningún registro de este tipo en los dispositivos Windows 10 IoT Core de forma predeterminada. Deberá agregar un registro de "Barras de desplazamiento dinámico" Si lo desea.
* Para habilitar las barras de desplazamiento de ocultar automáticamente en una aplicación de UWP, puede agregar el "DynamicScrollbars" registrar y establecer el valor en "1" similar al siguiente:

```
REG ADD "HKCU\Control Panel\Accessibility" /v DynamicScrollbars /t REG_DWORD \d "1"
```

* Debe establecer la clave del registro de la cuenta predeterminada. Si la configuración de XAML de ScrollViewer es "Visible", el valor del registro 0 forzará la barra de desplazamiento aparezcan regardlss si no hay suficiente contenido para que el desplazamiento aparezca en la interfaz de usuario. El valor del registro 1 mantendrá la barra de desplazamiento oculta hasta que no hay suficiente contenido.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Visible" Text="..."/>
```

* Por último, si la configuración de ScrollViewer XAML es "Auto", a continuación, el valor del registro 0 sólo mostrará la barra de desplazamiento completo cuando no hay suficiente contenido para mostrar la barra de desplazamiento. Cuando la configuración del registro es 1, aparecerá la barra de desplazamiento, a continuación, cuando no hay suficiente contenido u oculta si no hay ningún contenido.

```
<TextBox Height="200" Width="100" IsEnabled="True" FontSize="50" TextWrapping="Wrap" ScrollViewer.VerticalScrollBarVisibility="Auto" Text="..."/>
```

### <a name="different-commands-supported"></a>Diferentes comandos admitidos

* El comando Remove-AppxPackage de PowerShell funciona en el escritorio, pero no en Windows 10 IoT Core.
* No todas las carpetas en el dispositivo son accesibles para las aplicaciones universales de Windows. Puede usar la herramienta FolderPermissions para crear una carpeta accesibles para una aplicación para UWP en Windows 10 IoT Core. Por ejemplo, ejecute FolderPermissions c:\test -e para dar acceso de aplicaciones UWP a la carpeta c:\test. Sin embargo, esto no está disponible en el escritorio.

Comandos que aparecen en esta publicación pueden cambiar mientras pasa el tiempo desde que se actualiza continuamente Windows 10 IoT Core.

## <a name="iot-edge-support-for-windows-10-iot"></a>Compatibilidad de IoT Edge para Windows 10 IoT
Para más información acerca de IoT Edge soporte técnico para Windows 10 IoT, por favor, puede obtener más información sobre "Sistemas operativos" en el artículo de Azure IoT Edge [aquí](https://docs.microsoft.com/en-us/azure/iot-edge/support#operating-systems).


## <a name="helpful-resources"></a>Recursos útiles
* [Windows 10 IoT Enterprise](windows-iot-enterprise.md)
* [Windows 10 IoT Core](windows-iot-core.md)
