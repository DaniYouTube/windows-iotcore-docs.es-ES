---
title: Uso de PowerShell para Windows IoT
author: paulmon
ms.author: paulmon
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo usar PowerShell para conectarse al dispositivo, así como para administrar el dispositivo.
keywords: Windows IOT, PowerShell, Windows PowerShell, línea de comandos, Shell de línea de comandos
ms.openlocfilehash: f12fd88ee7c53937d92f163ae5acedc4197dbc8a
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080566"
---
# <a name="using-powershell-for-windows-iot"></a>Uso de PowerShell para Windows IoT

Configure y administre de forma remota cualquier dispositivo de Windows 10 IoT Core mediante Windows PowerShell.
PowerShell es un shell de línea de comandos basado en tareas y un lenguaje de scripting diseñado especialmente para la administración del sistema.

Asegúrese de seguir estos pasos para configurar correctamente el dispositivo que ejecuta Windows 10 IoT Core para que funcione bien con Visual Studio 2017.

## <a name="initiating-a-powershell-session"></a>Iniciar una sesión de PowerShell
1. Para iniciar una sesión de PowerShell con el dispositivo de Windows 10 IoT Core, primero deberá crear una relación de confianza entre el equipo host y el dispositivo. Después de iniciar el dispositivo de Windows IoT Core, se mostrará una dirección IP en la pantalla conectada al dispositivo.

    ![DefaultApp en Windows 10 IoT Core](../media/PowerShell/DefaultApp.png)

   Puede encontrar la misma información en el panel de Windows 10 IoT Core.

2. Abra una consola de administrador de PowerShell en el equipo local. Escriba **PowerShell** en el cuadro **Buscar en la web y Windows** cerca del menú Inicio de Windows. Windows buscará PowerShell en su equipo.

    ![Búsqueda de PowerShell](../media/PowerShell/start-ps.png)

3. Para iniciar PowerShell como administrador, haga clic con el botón derecho en **Windows PowerShell**y, a continuación, seleccione **Ejecutar como administrador**.

    ![Ejecutar PowerShell como administrador](../media/PowerShell/start-ps2.png)

   Ahora debería ver la consola de PowerShell.

    ![Consola de PowerShell](../media/PowerShell/ps.PNG)

4. Es posible que tenga que iniciar el servicio WinRM en el escritorio para habilitar las conexiones remotas. Para ello, en la consola de PowerShell, escriba el siguiente comando:

        net start WinRM

5. En la consola de PowerShell, escriba lo siguiente, sustituyendo `<machine-name or IP address>` por el valor adecuado (con el **nombre del equipo** es el más sencillo, pero si el dispositivo no tiene un nombre único en la red, pruebe la dirección IP):

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <machine-name or IP Address>

6. Escriba `Y` para confirmar el cambio.
        
        Set-Item WSMan:\localhost\Client\TrustedHosts -Value "<machine1-name or IP Address>,<machine2-name or IP Address>"
    
> [!NOTE]
> Si desea conectar varios dispositivos, puede usar comas y comillas para separar cada dispositivo.

7. Ahora puede iniciar una sesión con el dispositivo de Windows IoT Core. En la consola de PowerShell del administrador, escriba:

        Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

8. En el cuadro de diálogo de credenciales, escriba la siguiente contraseña predeterminada: `p@ssw0rd`
    
    <div class="alert alert-note">
      <h5><span class="win-icon win-icon-Page"></span>Tenga en cuenta </h5>
      <p>El proceso de conexión no es inmediato y puede tardar hasta 30 segundos.</p>
    </div>    
    
    Si se conectó correctamente al dispositivo, debería ver la dirección IP del dispositivo antes de la solicitud.

    ![Consola de PowerShell](../media/PowerShell/ps_device.png)

9. Actualice la contraseña de la cuenta. Se *recomienda encarecidamente* que actualice la contraseña predeterminada para la cuenta de administrador. Para ello, emita los siguientes comandos en la conexión de PowerShell:

    a. Reemplace `[new password]` por una contraseña segura:
    
            net user Administrator [new password]
            
    b. A continuación, establezca una nueva sesión de PowerShell con `Exit-PSSession` y `Enter-PSSession` con las nuevas credenciales.
    
            Exit-PSSession
            
            Enter-PSSession -ComputerName <machine-name or IP Address> -Credential <machine-name or IP Address or localhost>\Administrator

## <a name="commonly-used-powershell-commands"></a>Comandos de PowerShell de uso frecuente

### <a name="troubleshooting-with-visual-studio-remote-debugger"></a>Solución de problemas con Visual Studio Remote Debugger

Para poder implementar aplicaciones desde Visual Studio 2017, tendrá que asegurarse de que el Visual Studio Remote Debugger se está ejecutando en el dispositivo de Windows IoT Core. El depurador remoto debe abrirse automáticamente al iniciar el equipo. Para realizar una doble comprobación, use el comando `tlist` para mostrar todos los procesos en ejecución de PowerShell. Debe haber dos instancias de msvsmon. exe en ejecución en el dispositivo.

Es posible que el Visual Studio Remote Debugger agote el tiempo de espera después de largos períodos de inactividad. Si Visual Studio no se puede conectar al dispositivo de Windows IoT Core, intente reiniciar el dispositivo.

### <a name="configure-your-windows-iot-core-device"></a>Configuración del dispositivo de Windows IoT Core

Si lo desea, puede cambiar el nombre del dispositivo. 

1. Para cambiar el nombre del equipo, use la utilidad `setcomputername`:

        setcomputername <new-name>

2. Reinicie el dispositivo para que el cambio surta efecto. Puede usar el comando `shutdown` como se indica a continuación:

        shutdown /r /t 0

3. Dado que se ha cambiado el nombre del equipo, después de reiniciar deberá volver a ejecutar este comando para conectarse a su dispositivo con el nuevo nombre:

        Set-Item WSMan:\localhost\Client\TrustedHosts -Value <new-name>
        
El dispositivo Windows IoT Core ahora debe estar configurado correctamente y listo para usarse.

### <a name="commonly-used-utilities"></a>Utilidades usadas comúnmente

Para obtener una lista de comandos y utilidades que puede usar con PowerShell, consulte la página de utilidades de la [línea de comandos](../manage-your-device/CommandLineUtils.md) .

## <a name="known-issues-and-workarounds"></a>Problemas conocidos y soluciones

**Problema**: un error conocido en las directivas de seguridad de PowerShell provoca el manifiesto de los siguientes problemas en la sesión remota:
* Get-Help devuelve coincidencias inesperadas.
* Get-command en un módulo especificado devuelve una lista de comandos vacía.
* La ejecución de un cmdlet desde cualquiera de estos módulos produce CommandNotFoundException: Appx, NetAdapter, NetSecurity, NetTCPIP, PnpDevice.
* Import-Module en cualquiera de los módulos anteriores produce una excepción PSSecurityException con UnauthorizedAccess. La carga automática de módulos no parece funcionar.

**Solución alternativa**: modifique la Directiva de ejecución en la sesión remota de PowerShell a **RemoteSigned**. Para obtener más información sobre las diferentes directivas de ejecución, consulte [uso del cmdlet Set-ExecutionPolicy](https://technet.microsoft.com/library/ee176961.aspx).

**Problema**: a veces, los cmdlets de algunos módulos, como NetAdapter, no son visibles. Por ejemplo, Get-Module NetAdapter devuelve una lista vacía. 

**Solución alternativa**: Use el parámetro-Force con Import-Module. Por ejemplo, `Import-Module NetAdapter -Force`.

**Problema**: establecer la Directiva de ejecución en "AllSigned" interrumpe la comunicación remota de PowerShell. Los intentos posteriores de crear una sesión remota producirán un error con una excepción de carga Typesv3. ps1xml. 

**Solución alternativa**: Use Winrs. exe para restaurar la Directiva de ejecución de PowerShell:
* Cambiar la página de códigos de la consola `Chcp 65001`
* Inicie sesión en un shell de cmd. exe remoto `Winrs.exe -r:<target> -u:<username> -p:<password> cmd.exe`
* En cmd. exe remoto, modifique la clave del registro adecuada `reg add HKLM\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell /v ExecutionPolicy /d RemoteSigned /f`
* Salga de la sesión remota de cmd. exe `exit`

### <a name="other-known-issues"></a>Otros problemas conocidos

- En los scripts de PowerShell, los atributos de la clase o enumeración de PowerShell no funcionan. Agregando resultados con atributos en la siguiente excepción: el *tipo debe ser un objeto de tipo en tiempo de ejecución*.

- No se admite CIM saliente y la comunicación remota de PowerShell. La funcionalidad relevante en los cmdlets de confianza no funcionará. Entre ellas se incluyen Enter-PSSession, Get-Job, Receive-Job, Import-Module, Invoke-Command y Copy-Item.

- Los comandos SecureString ConvertFrom-SecureString y ConvertTo-SecureString no funcionan a menos que la sesión se cree mediante la autenticación CredSSP. De lo contrario, debe especificarse el parámetro-Key. Para más información sobre la configuración de la autenticación CredSSP, consulte [habilitación de la funcionalidad de segundo salto de PowerShell con CredSSP](https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/).


