---
title: Python
author: paulmon
ms.author: paulmon
ms.date: 08/13/2019
ms.topic: article
description: Aprende a instalar Python en un dispositivo ejecutando Windows 10 IoT Core
keywords: windows iot, python
ms.openlocfilehash: e76fdeaafe4b3b2b80b75a1fc22bd8a58769e1e5
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721638"
---
# <a name="python"></a><span data-ttu-id="041f1-104">Python</span><span class="sxs-lookup"><span data-stu-id="041f1-104">Python</span></span>
<span data-ttu-id="041f1-105">Python es un lenguaje de scripting que es popular para la automatización del sistema y el aprendizaje automático (ML).</span><span class="sxs-lookup"><span data-stu-id="041f1-105">Python is a scripting language that is popular for system automation and machine learning (ML).</span></span>
<span data-ttu-id="041f1-106">Puedes obtener más información acerca de Python en [python.org](https://www.python.org/).</span><span class="sxs-lookup"><span data-stu-id="041f1-106">You can learn more about Python at [python.org](https://www.python.org/).</span></span>

## <a name="using-python-on-x64-or-x86"></a><span data-ttu-id="041f1-107">Uso de Python en x64 o x86</span><span class="sxs-lookup"><span data-stu-id="041f1-107">Using Python on x64 or x86</span></span>
<span data-ttu-id="041f1-108">Para instalar Python en Windows IoT Core:</span><span class="sxs-lookup"><span data-stu-id="041f1-108">To install Python on Windows IoT Core:</span></span>
1. <span data-ttu-id="041f1-109">Descarga el paquete NuGet de Python y, a continuación, instala los archivos con [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="041f1-109">Download the Python nuget package, and then install the files using [PowerShell](../connect-your-device/PowerShell.md).</span></span>

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

2. <span data-ttu-id="041f1-110">Agrega Python a la ruta de acceso del sistema.</span><span class="sxs-lookup"><span data-stu-id="041f1-110">Add Python to the system path.</span></span>

    ```powershell
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

3. <span data-ttu-id="041f1-111">Asegúrate de que está instalada la versión actual de PIP.</span><span class="sxs-lookup"><span data-stu-id="041f1-111">Ensure that the current version of pip is installed</span></span>

    ```powershell
    python -m pip install --upgrade pip
    ```

## <a name="using-python-on-windows-iot-core-arm32"></a><span data-ttu-id="041f1-112">Uso de Python en Windows IoT Core ARM32</span><span class="sxs-lookup"><span data-stu-id="041f1-112">Using Python on Windows IoT Core ARM32</span></span>

<span data-ttu-id="041f1-113">Para obtener Python para Windows, deberás compilar los archivos binarios por ti mismo.</span><span class="sxs-lookup"><span data-stu-id="041f1-113">To get Python for Windows you will need to build the binaries yourself.</span></span>

1. <span data-ttu-id="041f1-114">Compila Python para ARM32.</span><span class="sxs-lookup"><span data-stu-id="041f1-114">Build Python for ARM32.</span></span>  <span data-ttu-id="041f1-115">La versión debe ser 3.8 o superior.</span><span class="sxs-lookup"><span data-stu-id="041f1-115">The branch must be 3.8 or greater.</span></span>

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\build.bat -p ARM --no-tkinter
    ```

2. <span data-ttu-id="041f1-116">Compila el archivo .zip de Python para Windows IoT Core ARM32.</span><span class="sxs-lookup"><span data-stu-id="041f1-116">Build Python .zip file for for Windows IoT Core ARM32.</span></span>  <span data-ttu-id="041f1-117">Se debe usar la misma versión de Python para ejecutar el equipo o el diseño.</span><span class="sxs-lookup"><span data-stu-id="041f1-117">The same version of Python must be used to run PC/layout.</span></span> <span data-ttu-id="041f1-118">Este paso permite compilar Python para x86 y lo usa para compilar los archivos .zip.</span><span class="sxs-lookup"><span data-stu-id="041f1-118">This step builds Python for x86 and uses it to build the .zip file(s).</span></span>  <span data-ttu-id="041f1-119">Si quieres las pruebas de la biblioteca estándar en el archivo .zip, agrega el parámetro `--include-tests`.</span><span class="sxs-lookup"><span data-stu-id="041f1-119">If you want the standard library tests in your .zip file add the `--include-tests` parameter.</span></span>

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm32" -t ".\PCBuild\temp" --preset-iot --include-venv --zip ".\PCBuild\arm32\zip\python.zip"

    net use P: \\[ip address]\c$ /user:administrator

    copy .\PCBuild\arm32\zip\python.zip P:\data
    ```

3. <span data-ttu-id="041f1-120">Usa [PowerShell](../connect-your-device/PowerShell.md) para extraer el archivo .zip en el dispositivo y agrega Python a la ruta de acceso del sistema.</span><span class="sxs-lookup"><span data-stu-id="041f1-120">Use [PowerShell](../connect-your-device/PowerShell.md) to extract the .zip file on the device and add Python to the system path.</span></span>

    ```powershell
    Expand-Archive C:\data\python.zip -DestinationPath c:\python
    cmd /c 'setx PATH "%PATH%";c:\python;c:\python\scripts /M'
    $env:Path += ";c:\python;c:\python\scripts"
    ```

4. <span data-ttu-id="041f1-121">Comprueba que `print('Hello World')` funciona.</span><span class="sxs-lookup"><span data-stu-id="041f1-121">Verify that `print('Hello World')` works.</span></span>

    ```powershell
    python -c "print('Hello World!');quit()"
    ```

## <a name="using-python-on-windows-iot-core-arm64"></a><span data-ttu-id="041f1-122">Uso de Python en Windows IoT Core ARM64</span><span class="sxs-lookup"><span data-stu-id="041f1-122">Using Python on Windows IoT Core ARM64</span></span>

<span data-ttu-id="041f1-123">Para obtener Python para Windows, deberás compilar los archivos binarios por ti mismo.</span><span class="sxs-lookup"><span data-stu-id="041f1-123">To get Python for Windows you will need to build the binaries yourself.</span></span>

1. <span data-ttu-id="041f1-124">Clona Python para ARM32 y ejecuta `get_externals`.</span><span class="sxs-lookup"><span data-stu-id="041f1-124">Clone Python for ARM32 and run `get_externals`.</span></span>  <span data-ttu-id="041f1-125">La versión debe ser 3.8 o superior.</span><span class="sxs-lookup"><span data-stu-id="041f1-125">The branch must be 3.8 or greater.</span></span>

    ```cmd
    git clone https://github.com/python/cpython
    cd cpython
    git checkout 3.8
    pcbuild\get_externals.bat
    cd ..
    ```

2. <span data-ttu-id="041f1-126">Clona y compila libffi.</span><span class="sxs-lookup"><span data-stu-id="041f1-126">Clone and build libffi.</span></span>

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

3. <span data-ttu-id="041f1-127">Compila Python para ARM64.</span><span class="sxs-lookup"><span data-stu-id="041f1-127">Build Python for ARM64.</span></span>

    ```cmd
    pcbuild\build.bat -p ARM64 --no-tkinter
    ```

4. <span data-ttu-id="041f1-128">Compila el archivo .zip de Python para Windows IoT Core ARM64.</span><span class="sxs-lookup"><span data-stu-id="041f1-128">Build Python .zip file for for Windows IoT Core ARM64.</span></span>  <span data-ttu-id="041f1-129">Se debe usar la misma versión de Python para ejecutar el equipo o el diseño.</span><span class="sxs-lookup"><span data-stu-id="041f1-129">The same version of Python must be used to run PC/layout.</span></span> <span data-ttu-id="041f1-130">Este paso permite compilar Python para x86 y lo usa para compilar los archivos .zip.</span><span class="sxs-lookup"><span data-stu-id="041f1-130">This step builds Python for x86 and uses it to build the .zip file(s).</span></span>  <span data-ttu-id="041f1-131">Si quieres las pruebas de la biblioteca estándar en el archivo .zip, agrega el parámetro `--include-tests`.</span><span class="sxs-lookup"><span data-stu-id="041f1-131">If you want the standard library tests in your .zip file add the `--include-tests` parameter.</span></span>

    ```cmd
    REM Build Python for x86 to use for building the .zip file.
    pcbuild\build.bat

    REM Map drive to device and copy files using PC/layout
    net use P: \\[ip address]\c$ /user:administrator
    pcbuild\win32\python.exe PC/layout -vv -s "." -b ".\PCBuild\arm64" -t ".\PCBuild\temp" --preset-iot --include-venv --copy P:\python
    ```

3. <span data-ttu-id="041f1-132">Agrega Python a la ruta de acceso del sistema.</span><span class="sxs-lookup"><span data-stu-id="041f1-132">Add Python to the system path.</span></span>

    ```cmd
    setx PATH "%PATH%";c:\python;c:\python\scripts /M
    set PATH=%PATH%;c:\python;c:\python\scripts
    ```

4. <span data-ttu-id="041f1-133">Comprueba que `print('Hello World')` funciona.</span><span class="sxs-lookup"><span data-stu-id="041f1-133">Verify that `print('Hello World')` works.</span></span>

    ```cmd
    python -c "print('Hello World!');quit()"
    ```

## <a name="try-out-azure-iot-hub-python-sdks-v2---previewhttpsgithubcomazureazure-iot-sdk-python-preview"></a><span data-ttu-id="041f1-134">Prueba los [SDK de Python para Azure IoT Hub v2 (versión preliminar)](https://github.com/Azure/azure-iot-sdk-python-preview)</span><span class="sxs-lookup"><span data-stu-id="041f1-134">Try out [Azure IoT Hub Python SDKs v2 - PREVIEW](https://github.com/Azure/azure-iot-sdk-python-preview)</span></span>

1. <span data-ttu-id="041f1-135">Primero, instala el SDK.</span><span class="sxs-lookup"><span data-stu-id="041f1-135">First install the SDK.</span></span>

    ```cmd
    python -m pip install azure-iot-device
    ```

<span data-ttu-id="041f1-136">En la salida de `pip install` se pueden producir errores: `Download error on https://pypi.org/simple/pbr/`.</span><span class="sxs-lookup"><span data-stu-id="041f1-136">In the output for the `pip install` there may be errors: `Download error on https://pypi.org/simple/pbr/`.</span></span> <span data-ttu-id="041f1-137">Si ves esto, en caso contrario, ve a `Set up an IoT Hub and create a Device Identity`:</span><span class="sxs-lookup"><span data-stu-id="041f1-137">If you see this then, otherwise skip to `Set up an IoT Hub and create a Device Identity`:</span></span>

2. <span data-ttu-id="041f1-138">Ve a `https://pypi.org/simple/pbr/` con tu explorador favorito.</span><span class="sxs-lookup"><span data-stu-id="041f1-138">Navigate to `https://pypi.org/simple/pbr/` in your favorite browser.</span></span> <span data-ttu-id="041f1-139">Inspecciona el certificado del sitio web y observa que lo emitió `DigiCert`.</span><span class="sxs-lookup"><span data-stu-id="041f1-139">Inspect the web site's certificate and noticed that it issued by `DigiCert`.</span></span>

3. <span data-ttu-id="041f1-140">Cree un directorio denominado `c:\test`.</span><span class="sxs-lookup"><span data-stu-id="041f1-140">Create a directory named `c:\test`.</span></span>

4. <span data-ttu-id="041f1-141">Ejecuta `certmgr.msc` desde un símbolo del sistema en una máquina Windows de escritorio.</span><span class="sxs-lookup"><span data-stu-id="041f1-141">Run `certmgr.msc` from a command prompt on a desktop Windows machine.</span></span>  

5. <span data-ttu-id="041f1-142">Ve a `Trusted Root Certification Authorities` en la vista de árbol.</span><span class="sxs-lookup"><span data-stu-id="041f1-142">Navigate to `Trusted Root Certification Authorities` in the treeview.</span></span>  <span data-ttu-id="041f1-143">Expande el nodo y elige `Certificates`.</span><span class="sxs-lookup"><span data-stu-id="041f1-143">Expand the node and choose `Certificates`.</span></span>

6. <span data-ttu-id="041f1-144">En el panel derecho, busca `DigiCert High Assurance EV Root`, haz clic con el botón derecho y selecciona `All Tasks` > `Export`.</span><span class="sxs-lookup"><span data-stu-id="041f1-144">In the right pane find the `DigiCert High Assurance EV Root`, right-click and select `All Tasks` > `Export`.</span></span>  <span data-ttu-id="041f1-145">Ten en cuenta que hay varios certificados `DigiCert` y yo identifiqué este probándolos todos, uno cada vez.</span><span class="sxs-lookup"><span data-stu-id="041f1-145">Note that there are multiple `DigiCert` certs and I identified this one by trying each one, one at a time.</span></span>

7. <span data-ttu-id="041f1-146">En el cuadro de diálogo que aparece, haz clic en `Next`.</span><span class="sxs-lookup"><span data-stu-id="041f1-146">In the dialog that pops up click `Next`.</span></span>

8. <span data-ttu-id="041f1-147">Selecciona `DER encoded binary X.509 (.CER)` (este debe ser el valor predeterminado) y haz clic en `Next`.</span><span class="sxs-lookup"><span data-stu-id="041f1-147">Select `DER encoded binary X.509 (.CER)` (this should be the default) and click `Next`.</span></span>

9. <span data-ttu-id="041f1-148">En el cuadro de edición `File name:` escribe `c:\test\DigiCert High Assurance EV Root.cer`.</span><span class="sxs-lookup"><span data-stu-id="041f1-148">In the `File name:` edit box type `c:\test\DigiCert High Assurance EV Root.cer`</span></span>

![Asistente para la exportación de certificado](../media/Python/global_sign_cert.png)

10. <span data-ttu-id="041f1-150">Haga clic en `Next`.</span><span class="sxs-lookup"><span data-stu-id="041f1-150">Click `Next`.</span></span>

11. <span data-ttu-id="041f1-151">Haga clic en `Finish`.</span><span class="sxs-lookup"><span data-stu-id="041f1-151">Click `Finish`.</span></span>

12. <span data-ttu-id="041f1-152">Copia `c:\test\DigiCert High Assurance EV Root.cer` en el dispositivo ejecutando el comando siguiente en la máquina de escritorio:</span><span class="sxs-lookup"><span data-stu-id="041f1-152">Copy `c:\test\DigiCert High Assurance EV Root.cer` to the device by running the following command on your desktop machine:</span></span>

    ```cmd
    net use X: \\host\c$ /user:host\administrator
    md X:\test
    copy "c:\test\GlobalSign Root CA.cer" X:\test
    ```

13. <span data-ttu-id="041f1-153">En el dispositivo, importa el certificado en el almacén raíz mediante [PowerShell](../connect-your-device/PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="041f1-153">On the device import the certificate into the root store using [PowerShell](../connect-your-device/PowerShell.md).</span></span>

    ```cmd
    certmgr -add "c:\test\DigiCert High Assurance EV Root.cer" -s root -r localMachine -c
    certmgr -add "c:\test\GlobalSign Root CA.cer" -s root -r localMachine -c
    ```

14. <span data-ttu-id="041f1-154">Intenta instalar `azure-iot-device` de nuevo.</span><span class="sxs-lookup"><span data-stu-id="041f1-154">Try to install the `azure-iot-device` again</span></span>

    ``` cmd
    python -m pip install azure-iot-device --no-color
    ```

15.  <span data-ttu-id="041f1-155">En la salida de `pip install` se pueden producir errores: `Download error for https://files.pythonhosted.org/`.</span><span class="sxs-lookup"><span data-stu-id="041f1-155">In the output for the `pip install` there may be errors: `Download error for https://files.pythonhosted.org/`.</span></span>  <span data-ttu-id="041f1-156">Si no se producen, ve a `Set up an IoT Hub and create a Device Identity`</span><span class="sxs-lookup"><span data-stu-id="041f1-156">If you don't see this then skip to `Set up an IoT Hub and create a Device Identity`</span></span>

16. <span data-ttu-id="041f1-157">Ve a `https://files.pythonhosted.org/` con tu explorador favorito.</span><span class="sxs-lookup"><span data-stu-id="041f1-157">Navigate to `https://files.pythonhosted.org/` in your favorite browser.</span></span> <span data-ttu-id="041f1-158">Inspecciona el certificado del sitio web y observa que lo emitió `GlobalSign`.</span><span class="sxs-lookup"><span data-stu-id="041f1-158">Inspect the web site's certificate and noticed that it issued by `GlobalSign`.</span></span>

17. <span data-ttu-id="041f1-159">Repite los pasos para exportar el certificado `GlobalSign Root CA` de la máquina de escritorio e importarlo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="041f1-159">Repeat the steps to export the `GlobalSign Root CA` certificate from your desktop machine and import it on the device.</span></span>

18. <span data-ttu-id="041f1-160">Intenta instalar `azure-iot-device` de nuevo.</span><span class="sxs-lookup"><span data-stu-id="041f1-160">Try to install the `azure-iot-device` again.</span></span>

### <a name="set-up-an-iot-hub-and-create-a-device-identity"></a><span data-ttu-id="041f1-161">Configuración de una instancia de IoT Hub y creación de una identidad de dispositivo</span><span class="sxs-lookup"><span data-stu-id="041f1-161">Set up an IoT Hub and create a Device Identity</span></span>

19. <span data-ttu-id="041f1-162">Instala la [CLI de Azure](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) (o usa [Azure Cloud Shell](https://shell.azure.com/)) y úsala para [crear una instancia de Azure IOT Hub](https://docs.microsoft.com/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).</span><span class="sxs-lookup"><span data-stu-id="041f1-162">Install the [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) (or use the [Azure Cloud Shell](https://shell.azure.com/)) and use it to [create an Azure IoT Hub](https://docs.microsoft.com/cli/azure/iot/hub?view=azure-cli-latest#az-iot-hub-create).</span></span>

    ```powershell
    az iot hub create --resource-group <your resource group> --name <your IoT Hub name>
    ```
    * <span data-ttu-id="041f1-163">Ten en cuenta que esta operación tarda unos minutos.</span><span class="sxs-lookup"><span data-stu-id="041f1-163">Note that this operation make take a few minutes.</span></span>

20. <span data-ttu-id="041f1-164">Agrega la extensión de IOT a la CLI de Azure y, a continuación, [registra una identidad de dispositivo](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create).</span><span class="sxs-lookup"><span data-stu-id="041f1-164">Add the IoT Extension to the Azure CLI, and then [register a device identity](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-create)</span></span>

    ```powershell
    az extension add --name azure-cli-iot-ext
    az iot hub device-identity create --hub-name <your IoT Hub name> --device-id <your device id>
    ```

21. <span data-ttu-id="041f1-165">[Recupera la cadena de conexión del dispositivo](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string) mediante la CLI de Azure</span><span class="sxs-lookup"><span data-stu-id="041f1-165">[Retrieve your Device Connection String](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub/device-identity?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-device-identity-show-connection-string) using the Azure CLI</span></span>

    ```powershell
    az iot hub device-identity show-connection-string --device-id <your device id> --hub-name <your IoT Hub name>
    ```

    <span data-ttu-id="041f1-166">Debe tener el formato:</span><span class="sxs-lookup"><span data-stu-id="041f1-166">It should be in the format:</span></span>
    ```
    HostName=<your IoT Hub name>.azure-devices.net;DeviceId=<your device id>;SharedAccessKey=<some value>
    ```

### <a name="send-a-simple-telemetry-message"></a><span data-ttu-id="041f1-167">Envío de un mensaje de telemetría simple</span><span class="sxs-lookup"><span data-stu-id="041f1-167">Send a simple telemetry message</span></span>

22. <span data-ttu-id="041f1-168">[Comienza la supervisión de la telemetría](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events) en la instancia de IOT Hub mediante la CLI de Azure</span><span class="sxs-lookup"><span data-stu-id="041f1-168">[Begin monitoring for telemetry](https://docs.microsoft.com/cli/azure/ext/azure-cli-iot-ext/iot/hub?view=azure-cli-latest#ext-azure-cli-iot-ext-az-iot-hub-monitor-events) on your IoT Hub using the Azure CLI</span></span>

    ```powershell
    az iot hub monitor-events --hub-name <your IoT Hub name> --output table
    ```

23. <span data-ttu-id="041f1-169">En el dispositivo, establece la cadena de conexión del dispositivo como una variable de entorno denominada `IOTHUB_DEVICE_CONNECTION_STRING`.</span><span class="sxs-lookup"><span data-stu-id="041f1-169">On your device, set the Device Connection String as an enviornment variable called `IOTHUB_DEVICE_CONNECTION_STRING`.</span></span>

    ```cmd
    REM NOTE: there are no quotes
    set IOTHUB_DEVICE_CONNECTION_STRING=<your connection string here>
    ```

24. <span data-ttu-id="041f1-170">Copia simple_send_d2c_message.py y ejecútalo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="041f1-170">Copy simple_send_d2c_message.py and run it on the device.</span></span>

    ```cmd
    cmd /c "if not exist c:\test md c:\test"
    REM copy simple_send_d2c_message.py from https://github.com/Azure/azure-iot-sdk-python-preview/blob/master/azure-iot-device/samples/simple_send_d2c_message.py to c:\test on the device
    python c:\test\simple_send_d2c_message.py
    ```

## <a name="using-python-in-an-x64-docker-container-on-windows-iot-core"></a><span data-ttu-id="041f1-171">Uso de Python en un contenedor de Docker x64 en Windows IoT Core</span><span class="sxs-lookup"><span data-stu-id="041f1-171">Using Python in an x64 docker container on Windows IoT Core</span></span>

1. <span data-ttu-id="041f1-172">Descarga los archivos más recientes de Docker e instálalos.</span><span class="sxs-lookup"><span data-stu-id="041f1-172">Download the newest docker, and install files.</span></span>

    ```powershell
    Invoke-WebRequest https://master.dockerproject.org/windows/x86_64/docker.zip -OutFile c:\data\docker.zip
    Expand-Archive c:\data\docker.zip -DestinationPath c:\data
    move c:\data\docker\docker*exe c:\windows\system32
    Remove-Item c:\data\docker -Recurse -Force
    dockerd --register-service
    net start docker
    ```

2.  <span data-ttu-id="041f1-173">Crea un archivo Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="041f1-173">Create Dockerfile</span></span>
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

3. <span data-ttu-id="041f1-174">Copia el archivo Dockerfile en c:\docker en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="041f1-174">Copy Dockerfile to c:\docker on device.</span></span> <span data-ttu-id="041f1-175">Copia también todos los certificados en P:\docker\test.</span><span class="sxs-lookup"><span data-stu-id="041f1-175">Also copy any certificates to P:\docker\test.</span></span>  <span data-ttu-id="041f1-176">1.txt es un archivo con el número 1 y un retorno de carro.</span><span class="sxs-lookup"><span data-stu-id="041f1-176">1.txt is a file with the number 1 and a carraige return.</span></span>

    ```cmd
    net use P: \\[device IP address]\c$ /user:administrator
    md P:\docker\test
    copy Dockerfile P:\docker
    copy AppCertificates\*.cer P:\docker\test
    copy 1.txt P:\docker\test
    ```

4.  <span data-ttu-id="041f1-177">Conéctate al dispositivo mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="041f1-177">Connect to the device using SSH.</span></span>  <span data-ttu-id="041f1-178">PowerShell remoto no funcionará en una sesión de Docker interactiva.</span><span class="sxs-lookup"><span data-stu-id="041f1-178">Remote powershell will not work for an interactive docker session.</span></span>

    ```powershell
    docker build --isolation==process . -t python
    docker run --isolation==process python
    ```

5. <span data-ttu-id="041f1-179">Imprime Hola mundo.</span><span class="sxs-lookup"><span data-stu-id="041f1-179">Print hello world</span></span>

    ```
    python -c "print('Hello Python in Containers!')"
    ```

6. <span data-ttu-id="041f1-180">Consulta las instrucciones anteriores sobre SDK de Azure IoT para probar los mensajes de nube a dispositivo.</span><span class="sxs-lookup"><span data-stu-id="041f1-180">See Azure IoT SDK directions above to test cloud to device messages.</span></span>

## <a name="additional-python-developer-resources"></a><span data-ttu-id="041f1-181">Recursos adicionales para desarrolladores de Python</span><span class="sxs-lookup"><span data-stu-id="041f1-181">Additional Python Developer Resources</span></span>
- [<span data-ttu-id="041f1-182">Guía para desarrolladores de Python</span><span class="sxs-lookup"><span data-stu-id="041f1-182">Python Developer's Guide</span></span>](https://devguide.python.org/setup/#setup)
- [<span data-ttu-id="041f1-183">Compilación de CPython en Windows</span><span class="sxs-lookup"><span data-stu-id="041f1-183">Build CPython on Windows</span></span>](https://cpython-core-tutorial.readthedocs.io/en/latest/build_cpython_windows.html)

