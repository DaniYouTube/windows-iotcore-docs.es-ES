---
title: Python
author: paulmon
ms.author: paulmon
ms.date: 08/13/2019
ms.topic: article
description: Aprende a instalar Python en un dispositivo ejecutando Windows 10 IoT Core
keywords: windows iot, python
ms.openlocfilehash: 26063863e5fdf7539e3159d4a4809bab3a38fb71
ms.sourcegitcommit: 4272081b5186dada1e61974193e41fcc1c42a1b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69629380"
---
# <a name="python"></a>Python
Python es un lenguaje de scripting que es popular para la automatización del sistema y el aprendizaje automático (ML).
Puedes obtener más información acerca de Python en [python.org](https://www.python.org/).

## <a name="using-python-on-x64-or-x86"></a>Uso de Python en x64 o x86
Para instalar Python en Windows IoT Core:
1. Descarga el paquete NuGet de Python y, a continuación, instala los archivos con [PowerShell](../connect-your-device/PowerShell.md).

    ```powershell
    $python_zip = "https://globalcdn.nuget.org/packages/python.3.7.4.nupkg"
    if($env:PROCESSOR_ARCHITECTURE -ieq "x86") {
        $python_zip = "https://www.nuget.org/api/v2/package/pythonx86/3.7.4"
    }
    Invoke-WebRequest $python_zip -OutFile c:\data\python.zip
    Expand-Archive C:\data\python.zip -DestinationPath c:\python_temp
    move C:\python_temp\tools c:\python
    rd C:\python_temp -Recurse -Force
    del C:\data\python.zip
    ```

2. Agrega Python a la ruta de acceso del sistema.

    ```powershell
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

3. Asegúrate de que está instalada la versión actual de PIP.

    ```powershell
    python -m pip install --upgrade pip
    ```

## <a name="using-python-on-windows-iot-core-arm32"></a>Uso de Python en Windows IoT Core ARM32

Para obtener Python para Windows, deberás compilar los archivos binarios por ti mismo.

1. Compila Python para ARM32.  La versión debe ser 3.8 o superior.

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\build.bat -p ARM --no-tkinter
    ```

2. Compila el archivo .zip de Python para Windows IoT Core ARM32.  Se debe usar la misma versión de Python para ejecutar el equipo o el diseño. Este paso permite compilar Python para x86 y lo usa para compilar los archivos .zip.  Si quieres las pruebas de la biblioteca estándar en el archivo .zip, agrega el parámetro `--include-tests`.

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm32" -t ".\PCBuild\temp" --preset-iot --include-venv --zip ".\PCBuild\arm32\zip\python.zip"

    net use P: \\[ip address]\c$ /user:administrator

    copy .\PCBuild\arm32\zip\python.zip P:\data
    ```

3. Usa [PowerShell](../connect-your-device/PowerShell.md) para extraer el archivo .zip en el dispositivo y agrega Python a la ruta de acceso del sistema.

    ```powershell
    Expand-Archive C:\data\python.zip -DestinationPath c:\python
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

4. Comprueba que `print('Hello World')` funciona.

    ```powershell
    python -c "print('Hello World!');quit()"
    ```

## <a name="using-python-on-windows-iot-core-arm64"></a>Uso de Python en Windows IoT Core ARM64

Para obtener Python para Windows, deberás compilar los archivos binarios por ti mismo.

1. Clona Python para ARM32 y ejecuta `get_externals`.  La versión debe ser 3.8 o superior.

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\get_externals.bat
    cd ..
    ```

2. Clona y compila libffi.

    ```cmd
    git clone https://github.com/libffi/libffi
    set LIBFFI_SOURCE=%CD%\libffi

    REM Visual Studio 2015 or greater with ARM64 tools installed is required to build Python
    REM the location of VCVARSALL may differ on your machine
    set VCVARSALL="C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\VC\Auxiliary\Build\vcvarsall.bat"

    cd cpython
    if exist c:\cygwin\bin\sh.exe (
        call pcbuild\prepare_libffi.bat -arm64
    ) else (
        call pcbuild\prepare_libffi.bat -arm64 --install-cygwin
    )
    if not exist externals\libffi\arm64\libffi-7.dll echo ERROR: libffi not built! & exit /b 1
    ```

3. Compila Python para ARM64.

    ```cmd
    pcbuild\build.bat -p ARM64 --no-tkinter
    ```

4. Compila el archivo .zip de Python para Windows IoT Core ARM64.  Se debe usar la misma versión de Python para ejecutar el equipo o el diseño. Este paso permite compilar Python para x86 y lo usa para compilar los archivos .zip.  Si quieres las pruebas de la biblioteca estándar en el archivo .zip, agrega el parámetro `--include-tests`.

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat

    REM Map drive to device and copy files using PC/layout
    net use P: \\[ip address]\c$ /user:administrator
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm64" -t ".\PCBuild\temp" --preset-iot --include-venv --copy P:\python
    ```

3. Agrega Python a la ruta de acceso del sistema.

    ```cmd
    setx PATH "%PATH%";c:\python;c:\python\scripts /M
    set PATH=%PATH%;c:\python;c:\python\scripts
    ```

4. Comprueba que `print('Hello World')` funciona.

    ```cmd
    python -c "print('Hello World!');quit()"
    ```

## <a name="try-out-azure-iot-hub-python-sdks-v2---previewhttpsgithubcomazureazure-iot-sdk-python-preview"></a>Prueba los [SDK de Python para Azure IoT Hub v2 (versión preliminar)](https://github.com/Azure/azure-iot-sdk-python-preview)

1. Primero, instala el SDK.

    ```cmd
    python -m pip install azure-iot-device
    ```

En la salida de `pip install` se pueden producir errores: `Download error on https://pypi.org/simple/pbr/`. Si ves esto, en caso contrario, ve a `Set up an IoT Hub and create a Device Identity`:

2. Ve a `https://pypi.org/simple/pbr/` con tu explorador favorito. Inspecciona el certificado del sitio web y observa que lo emitió `DigiCert`.

3. Cree un directorio denominado `c:\test`.

4. Ejecuta `certmgr.msc` desde un símbolo del sistema en una máquina Windows de escritorio.  

5. Ve a `Trusted Root Certification Authorities` en la vista de árbol.  Expande el nodo y elige `Certificates`.

6. En el panel derecho, busca `DigiCert High Assurance EV Root`, haz clic con el botón derecho y selecciona `All Tasks` > `Export`.  Ten en cuenta que hay varios certificados `DigiCert` y yo identifiqué este probándolos todos, uno cada vez.

7. En el cuadro de diálogo que aparece, haz clic en `Next`.

8. Selecciona `DER encoded binary X.509 (.CER)` (este debe ser el valor predeterminado) y haz clic en `Next`.

9. En el cuadro de edición `File name:` escribe `c:\test\DigiCert High Assurance EV Root.cer`.

![Asistente para la exportación de certificado](../media/Python/global_sign_cert.png)

10. Haga clic en `Next`.

11. Haga clic en `Finish`.

12. Copia `c:\test\DigiCert High Assurance EV Root.cer` en el dispositivo ejecutando el comando siguiente en la máquina de escritorio:

    ```cmd
    net use X: \\host\c$ /user:host\administrator
    md X:\test
    copy "c:\test\GlobalSign Root CA.cer" X:\test
    ```

13. En el dispositivo, importa el certificado en el almacén raíz mediante [PowerShell](../connect-your-device/PowerShell.md).

    ```cmd
    certmgr -add "c:\test\DigiCert High Assurance EV Root.cer" -s root -r localMachine -c
    certmgr -add "c:\test\GlobalSign Root CA.cer" -s root -r localMachine -c
    ```

14. Intenta instalar `azure-iot-device` de nuevo.

    ``` cmd
    python -m pip install azure-iot-device --no-color
    ```

15.  En la salida de `pip install` se pueden producir errores: `Download error for https://files.pythonhosted.org/`.  Si no se producen, ve a `Set up an IoT Hub and create a Device Identity`

16. Ve a `https://files.pythonhosted.org/` con tu explorador favorito. Inspecciona el certificado del sitio web y observa que lo emitió `GlobalSign`.

17. Repite los pasos para exportar el certificado `GlobalSign Root CA` de la máquina de escritorio e importarlo en el dispositivo.

18. Intenta instalar `azure-iot-device` de nuevo.

### <a name="set-up-an-iot-hub-and-create-a-device-identity"></a>Configuración de una instancia de IoT Hub y creación de una identidad de dispositivo

19. Instala la [CLI de Azure](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) (o usa [Azure Cloud Shell](https://shell.azure.com/)) y úsala para [crear una instancia de Azure IOT Hub](https://docs.microsoft.com/en-us/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).

    ```powershell
    az iot hub create --resource-group <your resource group> --name <your IoT Hub name>
    ```
    * Ten en cuenta que esta operación tarda unos minutos.

20. Agrega la extensión de IOT a la CLI de Azure y, a continuación, [registra una identidad de dispositivo](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create).

    ```powershell
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name <your IoT Hub name> --device-id <your device id>
    ```

21. [Recupera la cadena de conexión del dispositivo](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string) mediante la CLI de Azure

    ```powershell
    az iot hub device-identity show-connection-string --device-id <your device id> --hub-name <your IoT Hub name>
    ```

    Debe tener el formato:
    ```
    HostName=<your IoT Hub name>.azure-devices.net;DeviceId=<your device id>;SharedAccessKey=<some value>
    ```

### <a name="send-a-simple-telemetry-message"></a>Envío de un mensaje de telemetría simple

22. [Comienza la supervisión de la telemetría](https://docs.microsoft.com/en-us/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events) en la instancia de IOT Hub mediante la CLI de Azure

    ```powershell
    az iot hub monitor-events --hub-name <your IoT Hub name> --output table
    ```

23. En el dispositivo, establece la cadena de conexión del dispositivo como una variable de entorno denominada `IOTHUB_DEVICE_CONNECTION_STRING`.

    ```cmd
    REM NOTE: there are no quotes
    set IOTHUB_DEVICE_CONNECTION_STRING=<your connection string here>
    ```

24. Copia simple_send_d2c_message.py y ejecútalo en el dispositivo.

    ```cmd
    cmd /c "if not exist c:\test md c:\test"
    REM copy simple_send_d2c_message.py from https://github.com/Azure/azure-iot-sdk-python-preview/blob/master/azure-iot-device/samples/simple_send_d2c_message.py to c:\test on the device
    python c:\test\simple_send_d2c_message.py
    ```

## <a name="using-python-in-an-x64-docker-container-on-windows-iot-core"></a>Uso de Python en un contenedor de Docker x64 en Windows IoT Core

1. Descarga los archivos más recientes de Docker e instálalos.

    ```powershell
    Invoke-WebRequest https://master.dockerproject.org/windows/x86_64/docker.zip -OutFile c:\data\docker.zip
    Expand-Archive c:\data\docker.zip -DestinationPath c:\data
    move c:\data\docker\docker*exe c:\windows\system32
    Remove-Item c:\data\docker -Recurse -Force
    dockerd --register-service
    net start docker
    ```

2.  Crea un archivo Dockerfile.
    ```
    # escape = `
    FROM mcr.microsoft.com/windows/nanoserver:1809-amd64

    # Get Python
    ADD "https://globalcdn.nuget.org/packages/python.3.7.4.nupkg" .\temp\py.zip

    COPY test test
    COPY certmgr.exe c:\windows\system32

    # need admin for setx and certmgr
    USER ContainerAdministrator

    # Extract Python
    RUN tar -xf c:\temp\py.zip -C c:\temp && `
        move c:\temp\tools c:\ && `
        ren tools python && `
        RD c:\temp /s/q && `
        setx PATH "%PATH%";c:\python;c:\python\scripts /M

    RUN dir c:\test\*.cer /s/b > c:\test\certs.txt && `
        for /f "delims==" %i in (c:\test\certs.txt) do certmgr -add "%i" -s root -r localMachine -c < c:\test\1.txt

    USER ContainerUser

    RUN python -m pip install --upgrade pip && `
        python -m pip install azure-iot-device

    CMD cmd /k c:\test\start.cmd
    ```

3. Copia el archivo Dockerfile en c:\docker en el dispositivo. Copia también todos los certificados en P:\docker\test.  1.txt es un archivo con el número 1 y un retorno de carro.

    ```cmd
    net use P: \\[device IP address]\c$ /user:administrator
    md P:\docker\test
    copy Dockerfile P:\docker
    copy AppCertificates\*.cer P:\docker\test
    copy 1.txt P:\docker\test
    ```

4.  Conéctate al dispositivo mediante SSH.  PowerShell remoto no funcionará en una sesión de Docker interactiva.

    ```powershell
    docker build --isolation==process . -t python
    docker run --isolation==process python
    ```

5. Imprime Hola mundo.

    ```
    python -c "print('Hello Python in Containers!')"
    ```

6. Consulta las instrucciones anteriores sobre SDK de Azure IoT para probar los mensajes de nube a dispositivo.

## <a name="additional-python-developer-resources"></a>Recursos adicionales para desarrolladores de Python
- [Guía para desarrolladores de Python](https://devguide.python.org/setup/#setup)
- [Compilación de CPython en Windows](https://cpython-core-tutorial.readthedocs.io/en/latest/build_cpython_windows.html)

