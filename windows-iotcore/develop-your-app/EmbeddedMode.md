---
title: Modo insertado
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Obtenga información acerca de cómo configurar Windows para permitir el modo incrustado, habilitar aplicaciones en segundo plano y otras funcionalidades.
keywords: Windows IOT, modo incrustado, aplicaciones en segundo plano
ms.openlocfilehash: 7305853515b5bd1ca53c9b8be34c2449752c4897
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721675"
---
# <a name="embedded-mode"></a>Modo insertado

El modo incrustado se admite en Windows IoT Core y Windows IoT Enterprise. El modo incrustado habilita:

* [Aplicaciones en segundo plano (más información)](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* Uso de la funcionalidad lowLevelDevice
* Uso de la funcionalidad systemManagement

El modo incrustado siempre está habilitado en la ventana IoT Core.
El modo incrustado debe estar habilitado siguiendo los pasos que se indican a continuación en Windows IoT Enterprise.

## <a name="background-applications"></a>Aplicaciones en segundo plano

Las aplicaciones en segundo plano se crean mediante la plantilla aplicación en segundo plano (IoT) de Visual Studio.
Obtenga más información sobre la creación de [aplicaciones en segundo plano](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).

Las aplicaciones en segundo plano se ejecutan sin detenerse y sin límites de recursos. Además, si la aplicación en segundo plano se detiene por alguna razón y el modo incrustado está habilitado, el sistema reiniciará la aplicación en segundo plano.

Aunque el sistema reiniciará automáticamente las aplicaciones en segundo plano, las características de bloqueo del sistema deben estar habilitadas para impedir que los usuarios se detengan o interfieran con el funcionamiento de las aplicaciones en segundo plano.

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a>funcionalidad del dispositivo lowLevel y capacidad de lowLevelDevice

La funcionalidad del dispositivo **lowLevel** proporciona acceso a interfaces de hardware de bajo nivel como GPIO, SPI y I2C.

* [Ejemplo de parpadeo (GPIO)](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [Ejemplo de acelerómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

La funcionalidad **lowLevelDevices** permite a las aplicaciones tener acceso a dispositivos personalizados cuando se cumplen varios requisitos adicionales. Esta funcionalidad no se debe confundir con la funcionalidad de dispositivo lowLevel, que permite el acceso a dispositivos GPIO, I2C, SPI y PWM.

Consulte [declaraciones de funcionalidades de aplicación](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) para obtener más información.

## <a name="systemmanagment-capability"></a>Funcionalidad de systemManagment

Cuando se habilitan las capacidades de systemManagment para la aplicación, este es el conjunto de API que se desbloquea:  

* [Windows. System. ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows. System. TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows. System. ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows. Globalization. Language. TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>Depurar aplicaciones en segundo plano

Si está depurando en un dispositivo que no ejecuta Windows IoT Core y ve alguno de los siguientes mensajes de error, debe asegurarse de que AllowEmbeddedMode está habilitado en el dispositivo y de que el servicio de modo incrustado se está ejecutando:

* No hay más extremos disponibles desde el Endpoint Mapper.
* Este programa está bloqueado por la Directiva de grupo. Para obtener más información, póngase en contacto con el administrador del sistema.

## <a name="changing-the-mode"></a>Cambiar el modo
Para habilitar el modo incrustado, debe crear un paquete de aprovisionamiento en el diseñador de imágenes y configuraciones (ICD) que establece AllowEmbeddedMode = 1.  Para instalar ICD, debe descargar e instalar Windows ADK para Windows 10.

* [Descargar Windows ADK para Windows 10](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* [Obtener información sobre las novedades de Windows ADK para Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. Al instalar el ADK, seleccione **Imaging and Configuration Designer (ICD)**
2. Una vez completada la instalación, ejecute el diseñador de imágenes y configuraciones de Windows (WICD).

    ![Icono de WICD](../media/EmbeddedMode/WICD_Icon.png)

3. Haz clic en **Aprovisionamiento avanzado**.  Asigne al proyecto el nombre **AllowEmbeddedMode** y haga clic en **siguiente**.
    ![Step3](../media/EmbeddedMode/Step3.png)

4. Elija **común a todas las ediciones de Windows** y, a continuación, haga clic en **siguiente**.
    ![Paso4](../media/EmbeddedMode/Step4.png)

5. Haz clic en **Finalizar**.

    ![Paso5](../media/EmbeddedMode/Step5.png)

6. En el cuadro de búsqueda, escriba **EmbeddedMode** y, a continuación, haga clic en **AllowEmbeddedMode**.

    ![Paso6](../media/EmbeddedMode/Step6.png)

7. En el panel central, establezca el valor de **AllowEmbeddedMode** en **sí** ![STEP7](../media/EmbeddedMode/Step7.png)

8. Haga clic en Exportar > paquete de aprovisionamiento

    ![Step8](../media/EmbeddedMode/Step8.png)

9. Haga clic en Siguiente.

    ![Step9](../media/EmbeddedMode/Step9.png)

10. Haga clic en Siguiente.

    ![Step10](../media/EmbeddedMode/Step10.png)

11. Haga clic en Siguiente.

    ![Step11](../media/EmbeddedMode/Step11.png)

12. Haga clic en Generar.

    ![Step12](../media/EmbeddedMode/Step12.png)

13. Para instalar el modo incrustado. PPKG en Windows IoT Enterprise haga doble clic en el. PPKG.

14. Haz clic en **Sí, agrégalo**.
    Haga clic en sí en el cuadro de diálogo LUA, si aparece, y en **sí, agréguelo** en el cuadro de diálogo que se muestra a continuación.
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>Configurar una aplicación en segundo plano para que se ejecute automáticamente
1. Para configurar una aplicación en segundo plano para que se ejecute automáticamente, deberá seguir las instrucciones para [crear una tarjeta SD MinnowBoardMax](https://developer.microsoft.com/en-us/windows/iot/getstarted) y copiar `D:\windows\system32\iotstartup.exe` (donde D: es la tarjeta SD).

2. Para obtener una lista de las aplicaciones en segundo plano instaladas, escriba:

        C:\> iotstartup list BackgroundApplication1

3. La salida debe incluir el nombre completo de cada aplicación en segundo plano instalada, que tendrá el siguiente aspecto:

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. Para configurar esta aplicación de forma que se ejecute en el tipo de arranque:

        C:\> iotstartup add headless BackgroundApplication1

6. Si la aplicación en segundo plano se ha agregado correctamente a la lista de inicio, debería ver lo siguiente:

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. Reinicie el dispositivo en modo incrustado:

8. Una vez que se haya reiniciado el dispositivo, la aplicación en segundo plano se iniciará automáticamente.  El servicio de modo incrustado que administra las aplicaciones en segundo plano puede tardar unos minutos en iniciarse.  El servicio de modo incrustado supervisará las aplicaciones en segundo plano en la lista de inicio y se asegurará de que se reinicien si se detienen.  Si una aplicación en segundo plano se detiene varias veces en un breve período de tiempo, ya no se reiniciará.

9. Para quitar la aplicación en segundo plano del tipo de lista de Inicio:

        C:\> iotstartup remove headless BackgroundApplication1

10. Si la aplicación en segundo plano se quita de la lista de inicio, la salida tendrá el siguiente aspecto:

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
