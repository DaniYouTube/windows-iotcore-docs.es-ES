---
title: Uso de PowerShell para Windows IoT
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar PowerShell para conectarse al dispositivo, así como para administrar el dispositivo.
keywords: Windows iot, PowerShell, Windows PowerShell, línea de comandos, el shell de línea de comandos
ms.openlocfilehash: 1519fb9dd61a8d6521757fdd97999f03b74afa7d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515066"
---
# <a name="using-powershell-for-windows-iot"></a>Uso de PowerShell para Windows IoT

Configurar y administrar cualquier dispositivo Windows 10 IoT Core con Windows PowerShell de forma remota.
PowerShell es un shell de línea de comandos basado en tareas y lenguaje de scripting diseñado especialmente para la administración del sistema.

Asegúrese de seguir estos pasos para configurar correctamente un dispositivo que ejecuta Windows 10 IoT Core para funcionar bien con Visual Studio 2017.

## <a name="initiating-a-powershell-session"></a>Iniciar una sesión de PowerShell
1. Para iniciar una sesión de PowerShell con el dispositivo Windows 10 IoT Core, primero deberá crear una relación de confianza entre el equipo host y el dispositivo. Después de iniciar el dispositivo Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo.

    ![DefaultApp en Windows 10 IoT Core](../media/PowerShell/DefaultApp.png)

   Puede encontrar la misma información en el panel de Windows 10 IoT Core.

2. Abra una consola de PowerShell del administrador del equipo local. Tipo **powershell** en el **buscar en la web y Windows** cuadro situado en el menú Inicio de Windows. Windows encontrará PowerShell en su PC.

    ![Encontrar PowerShell](../media/PowerShell/start-ps.png)

3. Para iniciar PowerShell como administrador, haga clic en **Windows PowerShell**y, a continuación, seleccione **ejecutar como administrador**.

    ![Ejecute PowerShell como administrador](../media/PowerShell/start-ps2.png)

   Ahora debería ver la consola de PowerShell.

    ![Consola de PowerShell](../media/PowerShell/ps.PNG)

4. Es posible que deba iniciar el servicio WinRM en el escritorio para habilitar conexiones remotas. Para ello, desde la consola de PowerShell, escriba el siguiente comando:

        net start WinRM

5. Desde la consola de PowerShell, escriba lo siguiente, sustituyendo `<machine-name or IP address>` con el valor adecuado (mediante su **nombre-equipo** es más fácil, pero si el dispositivo no tiene un nombre exclusivo en la red, pruebe la dirección IP):

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. Escriba `Y` para confirmar el cambio.

> [!NOTE]
> Si desea conectar varios dispositivos, puede utilizar comas y comillas para separar cada dispositivo.
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
7. Ahora puede iniciar una sesión con su dispositivo Windows IoT Core. Desde PowerShell consola de administrador, escriba:

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. En el cuadro de diálogo de credenciales, escriba la contraseña predeterminada siguiente: `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span> TENGA EN CUENTA </h5>
      <p>El proceso de conexión no es inmediato y puede tardar hasta 30 segundos.</p>
    </div>    
    
    Si se ha conectado correctamente al dispositivo, debería ver la dirección IP del dispositivo antes del símbolo del sistema.

    ![Consola de PowerShell](../media/PowerShell/ps_device.png)

9. Actualizar la contraseña de cuenta. Nos *recomienda* que actualizar la contraseña predeterminada para la cuenta de administrador. Para ello, emita los siguientes comandos en la conexión de PowerShell:

    a. Reemplace `[new password]` con una contraseña segura:
    
            net user Administrator [new password]
            
    b. A continuación, establecer una nueva sesión de PowerShell con `Exit-PSSession` y `Enter-PSSession` con las nuevas credenciales.
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a>Normalmente se usan comandos de PowerShell

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>Solución de problemas con Visual Studio Remote Debugger

Para poder implementar aplicaciones desde Visual Studio 2017, deberá asegurarse de que se está ejecutando Visual Studio Remote Debugger en el dispositivo Windows IoT Core. El depurador remoto debería abrirse automáticamente al iniciar el equipo. Para comprobar la doble, utilice el `tlist` procesa el comando para enumerar todos los de la ejecución de PowerShell. Debe haber dos instancias de msvsmon.exe que se ejecutan en el dispositivo.

Es posible que el depurador remoto de Visual Studio en tiempo de espera tras un largo período de inactividad. Si Visual Studio no puede conectarse a su dispositivo Windows IoT Core, pruebe a reiniciar el dispositivo.

### <a name="configure-your-windows-iot-core-device"></a>Configurar el dispositivo Windows IoT Core

Si lo desea, puede cambiar el nombre del dispositivo. 

1. Para cambiar el nombre del equipo, use el `setcomputername` utilidad:

        setcomputername <new-name>

2. Reinicie el dispositivo para que el cambio surta efecto. Puede usar el `shutdown` comando como sigue:

        shutdown /r /t 0

3. Dado que se ha cambiado el nombre del equipo, después de reiniciar, tendrá que volver a ejecutar este comando para conectarse al dispositivo con el nuevo nombre:

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
El dispositivo Windows IoT Core ahora debería estar configurado y listo para usar correctamente!

### <a name="commonly-used-utilities"></a>Frecuente utilidades

Para obtener una lista de comandos y utilidades que puede usar con PowerShell, vea el [utilidades de línea de comandos](../manage-your-device/CommandLineUtils.md) página.

## <a name="known-issues-and-workarounds"></a>Problemas y soluciones conocidos

**PROBLEMA**: Un problema conocido en las directivas de seguridad de PowerShell hace que los siguientes problemas al manifiesto dentro de la sesión remota:
* Get-Help devuelve a coincidencias inesperadas.
* Get-Command en un módulo especificado devuelve una lista de comandos vacía.
* Ejecución de un cmdlet desde cualquiera de estos módulos genera CommandNotFoundException: AppX, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.
* Import-Module en cualquiera de los módulos anteriores produce la excepción de PSSecurityException con obtener acceso no autorizado. Carga automática de módulos no parece funcionar bien.

**Solución**: Modificar la directiva de ejecución dentro de la sesión remota de PowerShell para **RemoteSigned**. Para obtener más detalles sobre las directivas de ejecución diferente, consulte [mediante el Cmdlet Set-ExecutionPolicy](https://technet.microsoft.com/library/ee176961.aspx).

**PROBLEMA**: Cmdlets de algunos módulos, como NetAdapter a veces no son visibles. Por ejemplo, Get-Module NetAdapter devuelve una lista vacía. 

**Solución**: Use el parámetro - Force con Import-Module. Por ejemplo: `Import-Module NetAdapter -Force`.

**PROBLEMA**: Configuración de directiva de ejecución "AllSigned" interrumpe la comunicación remota de PowerShell. Intenta crear una sesión remota producirá un error con una SecurityException cargando Typesv3.ps1xml. 

**Solución**: Use winrs.exe para restaurar la directiva de ejecución de PowerShell:
* Página de códigos de consola de cambio `Chcp 65001`
* Inicie sesión en un shell de cmd.exe remoto `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* En cmd.exe remoto, modifique la clave del Registro adecuados `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* Salga de sesión remoto cmd.exe `exit`

### <a name="other-known-issues"></a>Otros problemas conocidos

- En los scripts de PowerShell, atributos de enumeración o clase de PowerShell no funcionan. Adición de atribuir los resultados en la siguiente excepción: *Tipo debe ser un objeto de tipo en tiempo de ejecución*.

- No se admite la comunicación remota de PowerShell y CIM saliente. La funcionalidad pertinente en los cmdlets de usuario de confianza no funcionará. Estos incluyen Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command y Copy-Item.

- Comandos de SecureString ConvertFrom-SecureString y ConvertTo-SecureString no funcionan a menos que se crea la sesión mediante la autenticación CredSSP. En caso contrario,-Key debe especificarse el parámetro. Para obtener más información sobre cómo configurar la autenticación CredSSP, vea [el problema de "Salto doble"](http://blogs.msdn.com/b/clustering/archive/2009/06/25/9803001.aspx).


