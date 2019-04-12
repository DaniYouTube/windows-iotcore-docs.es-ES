---
title: Implementación de controladores
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: Obtenga información sobre cómo compilar e implementar un controlador mediante Visual Studio.
keywords: Windows 10 IoT Core, implementación de controladores
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514976"
---
# <a name="driver-deployment"></a>Implementación de controladores

Implementar un controlador en Windows 10 IoT Core con Visual Studio. 

Configurar el proyecto de controlador de Visual Studio para que puede compilar e implementar un controlador para una plataforma específica durante la fase de desarrollo de controladores. 

Para este ejercicio puede usar el [controlador de ejemplo gpiokmdfdemo](https://github.com/ms-iot/samples/tree/develop/DriverSamples).

Si desea para agregar un controlador a una imagen, visite las instrucciones de nuestro [IoT fabricación guía](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).

## <a name="step-1--setup"></a>Paso 1: Programa de instalación 
___

### <a name="on-the-device"></a>En el dispositivo

* Asegúrese de que el dispositivo tiene una imagen IoTCore instalada siguiendo el [instrucciones de introducción](https://go.microsoft.com/fwlink/?linkid=860461).
* Conectarse al dispositivo a través de [Powershell](../connect-your-device/PowerShell.md).

### <a name="on-the-pc"></a>En el equipo

* Asegúrese de que ha instalado Visual Studio 2017.
* Instalar el [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).  Deberá instalar el SDK y WDK.
* Instalar los certificados para que el controlador está firmado correctamente y puede ejecutarse en su dispositivo. Desde un símbolo del sistema con privilegios elevados, ejecute los comandos enumerados a continuación:

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* Aplicar corrección para habilitar la implementación de F5 desde Visual Studio. En el símbolo del sistema con privilegios elevados, ejecute los comandos siguientes:

    1.  `cd %TEMP%` (cambie el directorio a `c:\users\<usernsme>\Appdata\Local\Temp`)
    2.  `md “WdkTempFiles”` Crear manualmente un directorio "WdkTempFiles" es una solución a un error en las herramientas y requiere hacerse *sólo una vez* en el equipo.


## <a name="step-2--provision-device-with-visual-studio"></a>Paso 2: Dispositivo de provisión con Visual Studio 
___
* Abra Visual Studio y seleccione **controlador > prueba > configuración de dispositivos > Agregar nuevo dispositivo**
    * Si no se muestra la opción de menú del controlador, compruebe si está instalado el SDK.

* En el **configuración del dispositivo** cuadro de diálogo, 
    * Escriba un usuario de nombre para mostrar descriptivo para el dispositivo de destino
    * Seleccione el tipo de dispositivo = móvil
    * En la lista mostrada, ordenar por dirección IP y busque la dirección para el dispositivo de IoT y seleccione. Si hay dos entradas, seleccione el otro con el GUID distinto de cero.  Asegúrese de que la fila seleccionada: debe resaltar azul
    * En la parte inferior del cuadro de diálogo hay dos botones de radio.  Seleccione la que dice que **aprovisionar el dispositivo y elija la configuración del depurador**.  Seleccione **siguiente**

* En el **configurar el depurador**, establezca la configuración apropiada.  Tenga en cuenta lo siguiente:
   * El MinnowBoardMax puede usar la red para la depuración.
       * Utilice el tipo de conexión **red**
       * Seleccione algún puerto: se puede usar el valor predeterminado
       * Seleccione alguna clave: se puede usar el valor predeterminado
       * Seleccione la dirección IP del host de la máquina que ejecuta visual studio.  No use la dirección autonet (169.xxx).
       * Seleccione **siguiente**
       
  ![Configurar opciones de depuración](../media/DriverDeployment/confdbgsettings.png)
       
    * Raspberry Pi usa serie para la depuración del kernel.
       *  Conecte el cable de la depuración serie adecuado para el PI y el equipo host
       *  Seleccione **serie** para el tipo de conexión
       *  Rellene el resto de los parámetros según corresponda para Raspberry Pi.
       *  Seleccione **siguiente**

* Ahora, el WDK, a través de VS, proporcionará el dispositivo de IoT.  TAEF y WDTF se instalará en el dispositivo y el dispositivo se configurará para depuración por la configuración proporcionada por encima del kernel.

* Cuando haya terminado, puede reiniciar el dispositivo.  La pantalla de progreso en la **configuración del dispositivo** proporcionará el estado y se muestra en completarse cuando se haya completado la instalación del dispositivo de IoT. Presione **finalizar**.

![Configurar el progreso](../media/DriverDeployment/confprogress.png)

* El dispositivo ya está aprovisionado y el **configuración de prueba de dispositivo** estado aparezca **configurado para las pruebas de controladores**

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a>Paso 3: Configurar el proyecto de controlador de Visual Studio
___    
1. Inicie Visual Studio en el modo de administrador y abra el proyecto de controlador de visual studio.
2. Asegúrese de que la versión de la plataforma de destino coincide con el SDK instalado en el equipo de desarrollo. Seleccione las propiedades del proyecto en la ventana Explorador de soluciones.  En Propiedades de configuración General de garantizar que las coincidencias de la versión de la plataforma de destino que el SDK instalado en el equipo de desarrollo.  Puede comprobar la versión del SDK desde la **Panel de Control > Programas > programas y características**.
3. En **proyecto > Agregar nuevo elemento > Visual C++ > Windows Driver**, seleccione **manifiesto del paquete** y presione **agregar**.

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` archivo se agregará al proyecto. En este archivo, especifique las etiquetas de propietario, plataforma, componente y del subcomponente. 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. Establecer el número de versión del paquete en **las propiedades del proyecto > PackageGen > versión**. Tenga en cuenta que cada vez que necesita realizar una instalación o reinstalación del controlador, el número de versión va a incrementar.

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. En **las propiedades del proyecto > firma de controladores > certificado de prueba**, seleccione prueba certificate (certificado de prueba de OEM de teléfono)

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. Vaya a **instalar controlador** y seleccione **implementación**

![InstallOptions](../media/DriverDeployment/installOptions.png)

* Desde el **nombre de dispositivo de destino** lista desplegable, seleccione el destino que creó anteriormente en el proceso de aprovisionamiento. Tenga en cuenta las dos opciones para **instalar o reinstalar** y **rápido volver a instalar**. Elija una opción y haga clic en **Aceptar**.
* **Instalar o reinstalar** se usa para la instalación inicial de un controlador para el destino.  Esto instala el paquete de controladores mediante la pila de Windows update y puede tardar varios minutos. Esto se debe usar cada vez que se modifica el archivo INF. 
    
> [!TIP]
> Cada vez que se utiliza esta opción para instalar a un controlador después de la instalación inicial, se debe incrementar el número de versión del paquete.

* **Rápida Reinstall** puede usarse una vez que se ha instalado un controlador, y no hay ningún cambio posterior en el archivo INF de controladores que afectan al registro.  Este método omite el proceso de instalación, se cierra devnodes todos los asociados con el controlador, copia el controlador a través de y reinicia el devnode.  Este proceso tarda unos pocos (< 20) segundos.

    
> [!WARNING]
> Este método no garantiza que se realice correctamente, si por alguna razón que un devnode no puede estar apagado para liberar el controlador, la operación dará error.  Esto puede ser debido a errores de hardware o una implementación defectuosa inicial del controlador.  La opción de instalar o reinstalar debe usarse en este caso.


El proyecto de Visual Studio ahora está listo para compilar e implementar un controlador para el dispositivo de destino. Si utiliza el controlador de gpiokmdfdemo de ejemplo que necesita para generar la tabla ACPI y copiar en el dispositivo de destino, a continuación, siga los pasos de [generar el controlador en Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).


## <a name="step-4--build-and-deploy-driver"></a>Paso 4: Compilación e implementación de controlador
___
Esto puede hacerse de dos maneras: mediante el **F5** clave y usar el **implementar** opción. En ambos sentidos, se creará e implementará el controlador (es decir, lo instala en el dispositivo) y la F5 asocia el depurador del núcleo de Visual Studio a los controladores instalados y cargados. 

Algunos usuarios prefieren usar la **implementar** funcionalidad y adjuntar un depurador de kernel diferente, como WinDBG, KD.  Esto puede proporcionar más flexibilidad que utilizar al depurador de VS.

### <a name="deploy"></a>Implementar
1.  Haga doble clic en el proyecto en el Explorador de soluciones
2.  Seleccione **implementar**

![Implementar](../media/DriverDeployment/deploy.png) 

3.  Debe continuar el proceso de implementación.  El dispositivo de IoT se reiniciará después de la implementación y debe mostrar la pantalla "Gears" mientras está realizando la instalación.

Generar salida está en el **salida** implementación de la ventana de estado también está en la ventana de salida de instalación cuando se complete, volverán a reiniciar el dispositivo y la pantalla de salida de VS indica éxito o error.

### <a name="f5"></a>F5

1.  En la ventana de compilación, asegúrese de que las configuraciones son correctas, la arquitectura de compilación actual es igual que la arquitectura de dispositivo de destino.  Esto es donde es útil tener el arco en el nombre de destino.  El destino se mostrará en el cuadro de vista en la barra de menú en Visual Studio en la parte central derecha superior.
2.  Presione **F5**.  El destino se creado, implementado y asociado al depurador de Kernel de VS.

* Después del reinicio, asegúrese de que PowerShell todavía está conectado a ella, en caso contrario, vuelva a conectarse al dispositivo de destino mediante el PowerShell `enter-pssession` comando...


## <a name="known-issues"></a>Problemas conocidos
___

### <a name="provisioning-errors"></a>Errores de aprovisionamiento
Una condición de carrera durante la interacción con MinnowBoardMax puede producir un error notificado durante el aprovisionamiento.  De hecho, más probable es que el aprovisionamiento correcto.

**Lista de errores:**
 
* ERROR: Tarea "registrar WDTF" no se pudo completar correctamente.
* ERROR: No se pudo completar correctamente la tarea "Configurar kernel configuración del depurador (reinicio posible)"

**Solución:** Casi seguro que se pueden omitir estos errores.

**Detalles:**

Se mostrará el siguiente error en la **progreso de la configuración de dispositivo configuración** cuadro de diálogo:

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

En este momento puede hacer clic con seguridad en el **finalizar** y, a continuación, el **aplicar** y **Aceptar**.

Se trata de un error inofensivo formado por una condición de carrera que provoca que un registro de resultados tener un formato incorrecto. Esto se puede comprobar examinando el archivo de registro en las áreas siguientes:

1. Abra una conexión FTP a la dirección IP del dispositivo (como se muestra en la pantalla del dispositivo) para el `Data/test/bin/DriverTest/Run` directory.
P. ej.
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. copia el `Configuring_computer_settings_(possible_reboot)_identifier.wtl` archivo en el equipo local.  Tenga en cuenta que el nombre de archivo de registro coincide con el nombre de la tarea con errores.
3. Abra el archivo en el Bloc de notas
4. Desplácese hasta el final del registro.  El siguiente texto estará presente, que indica que el aprovisionamiento sea correcto.

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

