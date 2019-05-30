---
title: Modo insertado
author: lilyhou
ms.author: lihou
ms.date: 11/10/2017
ms.topic: article
description: Obtenga información sobre cómo configurar Windows para permitir el modo incrustado, habilitación de aplicaciones en segundo plano y otras capacidades.
keywords: Windows iot, modo incrustado, las aplicaciones en segundo plano
ms.openlocfilehash: ca8124d97a9161a1539eff92c55cf3630cf0a049
ms.sourcegitcommit: b719e66699372e1339c2316cab45df2a474d09a0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2019
ms.locfileid: "66252175"
---
# <a name="embedded-mode"></a>Modo insertado

Modo incrustado se admite en Windows IoT Core y Windows IoT Enterprise. Habilita el modo incrustado:

* [Aplicaciones en segundo plano (más)](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications)
* Uso de la capacidad de lowLevelDevice
* Uso de capacidad systemManagement

Modo incrustado siempre está habilitado en la ventana IoT Core.
Modo incrustado debe habilitarse siguiendo los pasos siguientes en Windows IoT Enterprise.

## <a name="background-applications"></a>Aplicaciones en segundo plano

Aplicaciones en segundo plano se crean mediante la plantilla de aplicación en segundo plano (IoT) de Visual Studio.
Obtenga más información sobre crear [aplicaciones en segundo plano](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications).

En segundo plano de las aplicaciones se ejecutan sin necesidad de detener y sin límites de recursos. Además, si la aplicación en segundo plano se detiene por alguna razón y embedded está habilitado el modo se reiniciará la aplicación en segundo plano por el sistema.

Mientras el sistema reiniciará automáticamente aplicaciones en segundo plano, las características de bloqueo del sistema deben habilitarse para impedir que los usuarios deteniendo o interfieran con el funcionamiento de aplicaciones en segundo plano.

## <a name="lowlevel-device-capability-and-lowleveldevice-capability"></a>dispositivo lowLevel capacidad de capacidad y lowLevelDevice

El **lowLevel** dispositivo capacidad proporciona acceso a las interfaces de hardware de bajo nivel como I2C, SPI y GPIO.

* [Sample(GPIO) llamativa](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)
* [Ejemplo de acelerómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

El **lowLevelDevices** capacidad permite a las aplicaciones tener acceso a dispositivos personalizados cuando se cumple una serie de requisitos adicionales. Esta funcionalidad no debe confundirse con la funcionalidad del dispositivo lowLevel, que permite el acceso a los dispositivos GPIO, I2C, SPI y PWM.

Consulte [declaraciones de funcionalidades de aplicación](https://docs.microsoft.com/en-us/windows/uwp/packaging/app-capability-declarations) para obtener más información.

## <a name="systemmanagment-capability"></a>systemManagment capacidad

Al habilitar las capacidades de systemManagment para la aplicación trata el conjunto de API que desbloquea:  

* [Windows.System.ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System.ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows.Globalization.Language.TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## <a name="debugging-background-applications"></a>Depuración de aplicaciones en segundo plano

Si está depurando en un dispositivo que no se está ejecutando Windows IoT Core y ve alguno de los siguientes mensajes de error debe asegurarse de AllowEmbeddedMode está habilitado en el dispositivo y que se está ejecutando el servicio en modo incrustado:

* No hay no hay más extremos disponibles desde el endpoint mapper.
* Este programa está bloqueado por la directiva de grupo. Para obtener más información, póngase en contacto con el administrador del sistema.

## <a name="changing-the-mode"></a>Cambiar el modo
Para habilitar el modo incrustado que deberá crear un paquete de aprovisionamiento en la creación de imágenes y configuraciones de diseñador (ICD) que establece AllowEmbeddedMode = 1.  Para instalar ICD deberá descargar e instalar Windows ADK para Windows 10.

* [Descargue el Windows ADK para Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=526740)
* [Obtenga información sobre cuáles son las novedades en Windows ADK para Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. Al instalar el ADK, seleccione **creación de imágenes y configuraciones de diseñador (ICD)**
2. Una vez completada la instalación, ejecute Windows Imaging y Diseñador de configuración (WICD).

    ![Icono WICD](../media/EmbeddedMode/WICD_Icon.png)

3. Haz clic en **Aprovisionamiento avanzado**.  Denomine el proyecto **AllowEmbeddedMode** y haga clic en **siguiente**.
    ![Paso 3](../media/EmbeddedMode/Step3.png)

4. Elija **comunes a todas las ediciones de Windows** , a continuación, **siguiente**.
    ![Paso 4](../media/EmbeddedMode/Step4.png)

5. Haga clic en **Finalizar**.

    ![Paso5](../media/EmbeddedMode/Step5.png)

6. En el cuadro Buscar, escriba **EmbeddedMode** y, a continuación, haga clic en **AllowEmbeddedMode**.

    ![Paso6](../media/EmbeddedMode/Step6.png)

7. En el centro de panel de establece el valor de **AllowEmbeddedMode** a **Sí** ![Step7](../media/EmbeddedMode/Step7.png)

8. Haga clic en Exportar > paquete de aprovisionamiento

    ![Step8](../media/EmbeddedMode/Step8.png)

9. Haga clic en Siguiente.

    ![Step9](../media/EmbeddedMode/Step9.png)

10. Haga clic en Siguiente.

    ![Step10](../media/EmbeddedMode/Step10.png)

11. Haga clic en Siguiente.

    ![Step11](../media/EmbeddedMode/Step11.png)

12. Haga clic en generar.

    ![12](../media/EmbeddedMode/Step12.png)

13. Para instalar el modo incrustado. PPKG en Windows IoT Enterprise haga doble clic en el. PPKG.

14. Haz clic en **Sí, agrégalo**.
    Haga clic en Sí en el cuadro de diálogo LUA si aparece y haga clic en **Sí, agregarlo** en el cuadro de diálogo se muestra a continuación.
    ![Step14Standard](../media/EmbeddedMode/Step14Standard.png)


## <a name="configuring-a-background-application-to-run-automatically"></a>Configurar una aplicación en segundo plano para ejecutarse automáticamente
1. Para configurar una aplicación en segundo plano para ejecutar automáticamente, tendrá que seguir las instrucciones para [crear una tarjeta SD de MinnowBoardMax](https://developer.microsoft.com/en-us/windows/iot/getstarted) y copie `D:\windows\system32\iotstartup.exe` (donde D: es la tarjeta SD).

2. Para obtener una lista de tipos de aplicaciones en segundo plano instaladas:

        C:\> iotstartup list BackgroundApplication1

3. La salida debe incluir el nombre completo de cada aplicación instalada en segundo plano, que tendrá un aspecto similar al siguiente:

        Headless : BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee

5. Para configurar esta aplicación se ejecute en el tipo de arranque:

        C:\> iotstartup add headless BackgroundApplication1

6. Si la aplicación en segundo plano se ha agregado correctamente a la lista de inicio verá esto:

        Added Headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpveeplication1

7. Reinicie el dispositivo en modo incrustado:

8. Una vez que se haya reiniciado el dispositivo, se iniciará automáticamente la aplicación en segundo plano.  El servicio de modo incrustado que administra aplicaciones en segundo plano puede tardar unos minutos en iniciarse.  El servicio de modo incrustado supervisar aplicaciones en segundo plano en la lista de inicio y asegúrese de que obtenga reinicia si detiene.  Si una aplicación en segundo plano se detiene varias veces en un breve período de tiempo ya no se reiniciará.

9. Para quitar la aplicación en segundo plano desde el tipo de lista de inicio:

        C:\> iotstartup remove headless BackgroundApplication1

10. Si la aplicación en segundo plano se quita de la lista de inicio la salida tendrá este aspecto:

        Removed headless: BackgroundApplication1-uwp_1.0.0.0_x86__cqewk5knvpvee
