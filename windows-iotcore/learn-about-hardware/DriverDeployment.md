---
title: Implementación de controladores
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Obtenga información sobre cómo compilar e implementar un controlador con Visual Studio.
keywords: Windows 10 IoT Core, implementación de controladores
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169860"
---
# <a name="driver-deployment"></a>Implementación de controladores

Implemente un controlador en Windows 10 IoT Core con Visual Studio. 

Configure el proyecto de controlador de Visual Studio para que pueda compilar e implementar un controlador para una plataforma específica durante la fase de desarrollo del controlador. 

Para este ejercicio, puede usar el [controlador de ejemplo gpiokmdfdemo](https://github.com/ms-iot/samples/tree/develop/DriverSamples).

Si desea agregar un controlador a una imagen, consulte las instrucciones de nuestra guía de fabricación de [IOT](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).

## <a name="step-1--setup"></a>Paso 1: Programa de instalación 
___

### <a name="on-the-device"></a>En el dispositivo

* Asegúrese de que el dispositivo tiene instalada una imagen de IoTCore siguiendo las [instrucciones de introducción](https://go.microsoft.com/fwlink/?linkid=860461).
* Conéctese a su dispositivo a través de [PowerShell](../connect-your-device/PowerShell.md).

### <a name="on-the-pc"></a>En el equipo

* Asegúrese de que ha instalado Visual Studio 2017.
* Instale el [Kit de controladores de Windows](https://developer.microsoft.com/windows/hardware/windows-driver-kit).  Tendrá que instalar el SDK y WDK.
* Instale los certificados para que el controlador se firme correctamente y se pueda ejecutar en el dispositivo. Desde un símbolo del sistema con privilegios elevados, ejecute los comandos que se enumeran a continuación:

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* Aplicar corrección para habilitar la implementación de F5 desde VS. En el símbolo del sistema con privilegios elevados, ejecute los siguientes comandos:

    1.  `cd %TEMP%`(cambiará el directorio `c:\users\<usernsme>\Appdata\Local\Temp`a)
    2.  `md “WdkTempFiles”`Cree manualmente un directorio "WdkTempFiles". esta es una solución alternativa para un error en las herramientas y debe realizarse una *sola vez* en el equipo.


## <a name="step-2--provision-device-with-visual-studio"></a>Paso 2: Aprovisionamiento de dispositivos con Visual Studio 
___
* Abra Visual Studio y seleccione **Driver > Test > configurar dispositivos > agregar nuevo dispositivo** .
    * Si no se muestra la opción de menú controlador, compruebe si el SDK está instalado.

* En el cuadro de diálogo **configuración del dispositivo** , 
    * Escriba un nombre para mostrar descriptivo para el dispositivo de destino
    * Seleccionar tipo de dispositivo = móvil
    * En la lista que se muestra, ordene por dirección IP y busque la dirección del dispositivo IoT y seleccione. Si hay dos entradas, seleccione la que tenga el GUID distinto de cero.  Asegúrese de que la fila esté seleccionada; debe resaltar azul
    * En la parte inferior del cuadro de diálogo hay dos botones de radio.  Seleccione la que dice **aprovisionar dispositivo y elija Configuración**del depurador.  Seleccionar **siguiente**

* En la **configuración de configurar**el depurador, establezca la configuración adecuada.  Tenga en cuenta lo siguiente:
   * El MinnowBoardMax puede usar la red para la depuración.
       * Usar **red** de tipo de conexión
       * Seleccionar un puerto: se puede usar el valor predeterminado.
       * Seleccionar alguna clave: se puede usar el valor predeterminado.
       * Seleccione la dirección IP del host de la máquina que ejecuta Visual Studio.  No use la dirección de Autonet (169.xxx).
       * Seleccionar **siguiente**
       
  ![Configurar las opciones de depuración](../media/DriverDeployment/confdbgsettings.png)
       
    * Raspberry PI usa serial para la depuración de kernel.
       *  Conectar el cable de depuración serie adecuado a PI y el equipo host
       *  Seleccionar **serie** para el tipo de conexión
       *  Rellene el resto de los parámetros según corresponda para el Raspberry PI.
       *  Seleccionar **siguiente**

* El WDK, a través de VS, aprovisionará ahora el dispositivo de IoT.  TAEF y WDTF se instalarán en el dispositivo y el dispositivo se configurará para la depuración del kernel según la configuración proporcionada anteriormente.

* Cuando haya finalizado, es posible que el dispositivo se reinicie.  La pantalla de progreso de la **configuración del dispositivo** proporcionará el estado y se mostrará cuando el dispositivo de IOT haya completado la instalación. Presione **Finalizar**.

![Configurar el progreso](../media/DriverDeployment/confprogress.png)

* El dispositivo ya está aprovisionado y el estado de la **configuración de prueba del dispositivo** muestra **configurado para las pruebas de controladores**

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a>Paso 3: Configurar proyecto de controlador de Visual Studio
___    
1. Inicie Visual Studio en modo de administrador y abra el proyecto de controlador de Visual Studio.
2. Asegúrese de que la versión de la plataforma de destino coincide con el SDK instalado en el equipo de desarrollo. Seleccione propiedades del proyecto en la ventana Explorador de soluciones.  En propiedades de configuración general, asegúrese de que la versión de la plataforma de destino coincide con el SDK instalado en el equipo de desarrollo.  Puede comprobar la versión del SDK en el panel de **Control > programas > programas y características**.
3. En **proyecto > agregar nuevo elemento > Visual C++ > controlador de Windows**, seleccione **manifiesto del paquete** y, a continuación, haga clic en **Agregar**.

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml`el archivo se agregará al proyecto. En este archivo, especifique las etiquetas de propietario, plataforma, componente y subcomponente. 
 
![Package-pkg-XML](../media/DriverDeployment/Package-pkg-xml.png)
 
4. Establezca el número de versión del paquete en **las propiedades del proyecto > PackageGen > versión**. Tenga en cuenta que cada vez que necesite realizar una instalación o reinstalación del controlador, se debe incrementar este número de versión.

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. En **propiedades del proyecto > firma de controladores > certificado de prueba**, seleccione certificado de prueba (certificado de prueba de OEM de teléfono).

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. Vaya a **instalar controlador** y seleccione **implementación** .

![InstallOptions](../media/DriverDeployment/installOptions.png)

* En el menú desplegable **nombre del dispositivo de destino** , seleccione el destino creado anteriormente en el proceso de aprovisionamiento. Tenga en cuenta las dos opciones de **instalación/reinstalación** y reinstalación **rápida**. Elija una opción y haga clic en **Aceptar**.
* **Instalar/reinstalar** se usa para la instalación inicial de un controlador en el destino.  Esto instala el paquete de controladores mediante la pila de Windows Update y puede tardar varios minutos. Debe usarse cada vez que se cambie el archivo INF. 
    
> [!TIP]
> Cada vez que se usa esta opción para instalar un controlador después de la instalación inicial, se debe incrementar el número de versión del paquete.

* La **reinstalación rápida** se puede usar una vez que se ha instalado un controlador y no hay cambios posteriores en el archivo INF de los controladores que afecten al registro.  Este método omite el proceso de instalación, apaga todos los devnodes asociados al controlador, copia el controlador en y reinicia devnode.  Esto tarda unos pocos (< 20) segundos.

    
> [!WARNING]
> No se garantiza que este método se realice correctamente; si por alguna razón no se puede apagar un devnode para liberar el controlador, se producirá un error en la operación.  Esto puede deberse a un hardware defectuoso o a una implementación defectuosa del controlador.  En este caso, se debe utilizar la opción instalar/reinstalar.


El proyecto de Visual Studio ya está listo para compilar e implementar un controlador en el dispositivo de destino. Si usa el controlador gpiokmdfdemo de ejemplo, debe generar la tabla ACPI y copiarla en el dispositivo de destino. a continuación, siga los pasos de [creación del controlador en Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).


## <a name="step-4--build-and-deploy-driver"></a>Paso 4: Compilar e implementar controlador
___
Esto se puede hacer de dos maneras, mediante la tecla **F5** y el uso de la opción **implementar** . En ambos sentidos, el controlador se compilará e implementará (es decir, lo instala en el dispositivo) y F5 conectará el depurador de kernel de Visual Studio al controlador instalado y cargado. 

Algunos usuarios prefieren usar la funcionalidad de **implementación** y asociar un depurador de kernel diferente, como WinDbg o KD.  Esto puede proporcionar más flexibilidad que usar el depurador de VS.

### <a name="deploy"></a>Implementar
1.  Haga clic con el botón derecho en el proyecto en el explorador de soluciones.
2.  Seleccionar **implementar**

![Implementar](../media/DriverDeployment/deploy.png) 

3.  El proceso de implementación debe continuar.  El dispositivo de IoT se reiniciará después de la implementación y debería mostrar la pantalla "engranajes" mientras se realiza la instalación.

La salida de la compilación está en la ventana de **salida** el estado de implementación también está en la ventana de salida cuando se completa la instalación, el dispositivo se reiniciará de nuevo y la pantalla de salida de vs indicará si se ha realizado correctamente o no.

### <a name="f5"></a>F5

1.  En la ventana compilar, asegúrese de que las configuraciones son correctas: el arco de compilación actual es el mismo que el del dispositivo de destino.  Aquí es donde es útil tener el Arch en el nombre de destino.  El destino se mostrará en el cuadro de vista de la barra de menús en VS en la parte superior derecha.
2.  Presione **F5**.  El destino se compilará, implementará y adjuntará al depurador de kernel de VS.

* Después del reinicio, asegúrese de que PowerShell sigue conectado a él; de lo contrario, vuelva a conectarse al dispositivo de destino mediante `enter-pssession` el comando de PowerShell.


## <a name="known-issues"></a>Problemas conocidos
___

### <a name="provisioning-errors"></a>Errores de aprovisionamiento
Una condición de carrera durante la interacción con MinnowBoardMax puede producir un error detectado durante el aprovisionamiento.  De hecho, lo más probable es que el aprovisionamiento se haya realizado correctamente.

**Lista de errores:**
 
* ERROR: La tarea "registrando WDTF" no se pudo completar correctamente.
* ERROR: La tarea "Configurando la configuración del depurador de kernel (posible reinicio)" no se pudo completar correctamente

**Solución:** Es posible que no se puedan pasar por alto estos errores.

**Indicaciones**

El siguiente error se mostrará en el cuadro de diálogo de progreso de la configuración del **dispositivo** :

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully 
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

Llegados a este punto, puede hacer clic en el **final** con seguridad y, a continuación, en **aplicar** y **Aceptar**.

Se trata de un error benigno formado por una condición de carrera que hace que un registro de resultados tenga un formato incorrecto. Para comprobarlo, examine el archivo de registro en la siguiente área:

1. Abra una conexión FTP con la dirección IP del dispositivo (como se muestra en la pantalla del dispositivo) `Data/test/bin/DriverTest/Run` en el directorio.
ej.`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. Copie el `Configuring_computer_settings_(possible_reboot)_identifier.wtl` archivo en el equipo local.  Tenga en cuenta que el nombre del archivo de registro coincide con el nombre de la tarea con error.
3. Abra el archivo en el Bloc de notas.
4. Desplácese hasta la parte inferior del registro.  El siguiente texto estará presente, lo que indica que el aprovisionamiento se ha realizado correctamente.

```
<PFRollup 
    Total="1" 
    Passed="1" 
    Failed="0" 
    Blocked="0" 
    Warned="0" 
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```

