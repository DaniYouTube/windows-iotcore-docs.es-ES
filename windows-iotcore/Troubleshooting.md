---
Description: Solución de diferentes problemas relacionados con el desarrollo.
title: Solución de problemas
ms.date: 08/28/2018
ms.topic: article
ms.openlocfilehash: 8d2e326dae01157931e5d1d1c3d6eb858a1268b1
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918587"
---
# <a name="troubleshooting"></a><span data-ttu-id="d2285-103">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="d2285-103">Troubleshooting</span></span>
<span data-ttu-id="d2285-104">Se trata de un artículo que contiene los problemas más comunes que se han encontrado los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d2285-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="d2285-105">Para encontrar un elemento específico, presione Ctrl+F para buscar una palabra o frase.</span><span class="sxs-lookup"><span data-stu-id="d2285-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="d2285-106">¿Tiene alguna idea que quiera agregar?</span><span class="sxs-lookup"><span data-stu-id="d2285-106">Have any insight you want to add?</span></span> <span data-ttu-id="d2285-107">Cree una solicitud de incorporación de cambios para esta documentación o proporcione comentarios sobre el contenido a continuación.</span><span class="sxs-lookup"><span data-stu-id="d2285-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="d2285-108">Para solucionar problemas relacionados con la fabricación, lea el [documento sobre solución de problemas](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) de nuestra guía de fabricación.</span><span class="sxs-lookup"><span data-stu-id="d2285-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="d2285-109">Compatibilidad con ASUS Tinkerboard y Rockchip</span><span class="sxs-lookup"><span data-stu-id="d2285-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="d2285-110">Aunque no admitamos ASUS Tinkerboard y Rockchip de forma oficial, hay casos en los que Rockchip ha colaborado con terceras partes para conseguir que SoC funcionara en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d2285-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="d2285-111">Problema al conectar un dispositivo MBM en itinerancia</span><span class="sxs-lookup"><span data-stu-id="d2285-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="d2285-112">Hay dos aspecto que tener en cuenta al habilitar la itinerancia:</span><span class="sxs-lookup"><span data-stu-id="d2285-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="d2285-113">profile.xml configura la itinerancia y define el comportamiento para establecer de forma automática una conexión a la red de telefonía móvil.</span><span class="sxs-lookup"><span data-stu-id="d2285-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="d2285-114">Para establecer un perfil para móviles, consulte [este artículo](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span><span class="sxs-lookup"><span data-stu-id="d2285-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

```
  <!-- applicability to any combination of home carrier, partner MOs and non-partner MOs, except for HomeAndNonPartner -->
  <xs:simpleType name="roamApplicabilityType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="NonPartnerOnly"/>
       <xs:enumeration value="PartnerOnly"/>
       <xs:enumeration value="HomeOnly"/>
       <xs:enumeration value="HomeAndPartner"/>
       <xs:enumeration value="PartnerAndNonpartner"/>
       <xs:enumeration value="AllRoaming"/>
    </xs:restriction>
  </xs:simpleType>
  
  <xs:simpleType name="roamControlType">
    <xs:restriction base="xs:token">
       <xs:enumeration value="AllRoamAllowed"/>
       <xs:enumeration value="PartnerRoamAllowed"/>
       <xs:enumeration value="NoRoamAllowed"/>
    </xs:restriction>
  </xs:simpleType>
``` 

<span data-ttu-id="d2285-115">Para establecer un perfil de conexión automática, seleccione "auto":</span><span class="sxs-lookup"><span data-stu-id="d2285-115">To set a profile for automatic connection, select "auto":</span></span>

```  
<!-- Connection Mode, default is "manual" -->
    <xs:element name="ConnectionMode" minOccurs="0">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <!-- manual connect always -->
          <xs:enumeration value="manual" />
          <!-- auto connect always -->
          <xs:enumeration value="auto" />
          <!-- auto connect when not roaming -->
          <xs:enumeration value="auto-home"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:element>
```

2. <span data-ttu-id="d2285-116">Otro factor es que se debe cumplir la directiva de itinerancia por cada interfaz.</span><span class="sxs-lookup"><span data-stu-id="d2285-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="d2285-117">De forma predeterminada, esa directiva se establece en FALSE ("solo operador local").</span><span class="sxs-lookup"><span data-stu-id="d2285-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="d2285-118">Esto se puede consultar y cambiar en la línea de comandos a través de `netsh mbn get/set dataroamcontrol.`</span><span class="sxs-lookup"><span data-stu-id="d2285-118">This can be queried and changed in command line via `netsh mbn get/set dataroamcontrol.`</span></span>

<span data-ttu-id="d2285-119">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d2285-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="d2285-120">Puede obtener el error **0x139f (ERROR_INVALID_STATE)** cuando el dispositivo está en itinerancia pero la directiva de itinerancia no permite la itinerancia de datos; error en una solicitud de conexión enviada a wwansvc.</span><span class="sxs-lookup"><span data-stu-id="d2285-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="d2285-121">Problemas de arranque de Raspberry Pi 3B+</span><span class="sxs-lookup"><span data-stu-id="d2285-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="d2285-122">Esta versión para Raspberry Pi 3B+ es una versión preliminar técnica no admitida.</span><span class="sxs-lookup"><span data-stu-id="d2285-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="d2285-123">Se ha completado la habilitación y la validación limitadas.</span><span class="sxs-lookup"><span data-stu-id="d2285-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="d2285-124">Para obtener una mejor experiencia de evaluación y para cualquier producto comercial, use Raspberry Pi 3B u otros dispositivos con SoC de Intel, Qualcomm o NXP admitidos.</span><span class="sxs-lookup"><span data-stu-id="d2285-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="d2285-125">Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B+, vea nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="d2285-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="d2285-126">El dispositivo Raspberry Pi 3 modelo B+ es el producto más reciente de la gama Raspberry Pi 3, con un procesador de cuatro núcleos de 64 bits a 1,4 GHz, LAN inalámbrica de banda dual a 2,4 GHz y 5 GHz, Bluetooth 4.2/BLE, Ethernet más rápido y funciones PoE a través de alta disponibilidad de PoE independiente.</span><span class="sxs-lookup"><span data-stu-id="d2285-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="d2285-127">Recientemente, muchos clientes interesados en Windows 10 IoT Core han encontrado un problema que hacía que el dispositivo no se pudiera iniciar con normalidad después de instalar la imagen de Windows 10 IoT Core, pero el dispositivo Raspbian funciona bien en él.</span><span class="sxs-lookup"><span data-stu-id="d2285-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flashing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="d2285-128">A continuación se indican algunas sugerencias sobre cómo solucionar el problema de inicio.</span><span class="sxs-lookup"><span data-stu-id="d2285-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="d2285-129">Hay algunos problemas conocidos en esta imagen de Insider Preview.</span><span class="sxs-lookup"><span data-stu-id="d2285-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="d2285-130">Tenga en cuenta que:</span><span class="sxs-lookup"><span data-stu-id="d2285-130">Please note that:</span></span>
* <span data-ttu-id="d2285-131">Esta imagen solo está pensada para el dispositivo Raspberry Pi 3B+ y no arrancará en Raspberry Pi 2.</span><span class="sxs-lookup"><span data-stu-id="d2285-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="d2285-132">La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d2285-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="d2285-133">Wi-Fi y Bluetooth en la placa no funcionan en el dispositivo Raspberry Pi 3B+.</span><span class="sxs-lookup"><span data-stu-id="d2285-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="d2285-134">El controlador de pantalla táctil Ft5406 está deshabilitado en Raspberry Pi 3B+.</span><span class="sxs-lookup"><span data-stu-id="d2285-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="d2285-135">El LED de actividad de tarjeta SD está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="d2285-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="d2285-136">Solo hay dos requisitos al elegir las tarjetas SD que se van a usar con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d2285-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="d2285-137">Tendrá que usar una tarjeta SD de clase 10 y asegurarse de que tenga espacio suficiente, al menos 8 GB.</span><span class="sxs-lookup"><span data-stu-id="d2285-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="d2285-138">Microsoft ha comprobado la compatibilidad de un par de tarjetas SD con Windows 10 IoT Core:</span><span class="sxs-lookup"><span data-stu-id="d2285-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="d2285-139">Tarjeta Micros SDHC de clase 10 Samsung EVO de 32 GB</span><span class="sxs-lookup"><span data-stu-id="d2285-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="d2285-140">SanDisk Ultra Micro SDHC, de 16 GB</span><span class="sxs-lookup"><span data-stu-id="d2285-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="d2285-141">Por lo general, tendrá que comprobar si la tarjeta SD es falsa o si está dañada.</span><span class="sxs-lookup"><span data-stu-id="d2285-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="d2285-142">Igualmente la tarjeta SD puede sufrir daños debido a diversos factores, como la escasez de alimentación o una extracción incorrecta.</span><span class="sxs-lookup"><span data-stu-id="d2285-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="d2285-143">Es importante proteger la tarjeta de memoria de posibles daños.</span><span class="sxs-lookup"><span data-stu-id="d2285-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="d2285-144">Para instalar la imagen en una tarjeta SD, puede usar el [Panel de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span><span class="sxs-lookup"><span data-stu-id="d2285-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="d2285-145">Tendrá que elegir "Personalizada" en el campo de la compilación del sistema operativo y luego seleccionar el archivo FFU para instalar.</span><span class="sxs-lookup"><span data-stu-id="d2285-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="d2285-146">Compruebe si hay algún error de hardware en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d2285-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="d2285-147">Hay dos LED en la placa Raspberry Pi 3B+, como en el modelo 3B.</span><span class="sxs-lookup"><span data-stu-id="d2285-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="d2285-148">Uno es para PWR y el otro para ACT.</span><span class="sxs-lookup"><span data-stu-id="d2285-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="d2285-149">El número de parpadeos que emite la luz ACT determinará si la placa arranca o no.</span><span class="sxs-lookup"><span data-stu-id="d2285-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="d2285-150">En el modelo Raspberry Pi 3B+, el LED de actividad de la tarjeta SD no parpadeará durante algunas fases del arranque.</span><span class="sxs-lookup"><span data-stu-id="d2285-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="d2285-151">Cuando el dispositivo está arrancando y muestra la página de espera, espere pacientemente.</span><span class="sxs-lookup"><span data-stu-id="d2285-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="d2285-152">Por lo general, esto suele durar hasta un minuto.</span><span class="sxs-lookup"><span data-stu-id="d2285-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="d2285-153">Pero en ocasiones, debido a la velocidad de lectura y escritura de la tarjeta SD, es posible que tarde más tiempo.</span><span class="sxs-lookup"><span data-stu-id="d2285-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="d2285-154">Si el dispositivo no puede arrancar normalmente con Windows 10 IoT Core, puede intentar instalar un sistema operativo Linux (como Raspbian) en la tarjeta SD para concretar si el problema se debe al hardware.</span><span class="sxs-lookup"><span data-stu-id="d2285-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="d2285-155">Si recibe una "pantalla arco iris", asegúrese de que ha instalado la versión de lanzamiento 3B+, disponible [aquí](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="d2285-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="d2285-156">[Aquí](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3) puede comprobar el proceso con un tutorial sobre instalación de imágenes de 3B+ enviado por la comunidad.</span><span class="sxs-lookup"><span data-stu-id="d2285-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="d2285-157">Comunicación de puerto serie en Windows 10 IoT Core para Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="d2285-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="d2285-158">En el dispositivo Raspberry Pi, la aplicación puede usar los adaptadores hardware UART y UART USB con la comunicación de serie.</span><span class="sxs-lookup"><span data-stu-id="d2285-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="d2285-159">De forma predeterminada, los pines de transmisión y recepción de UART en el adaptador GPIO son el 8 y el 10.</span><span class="sxs-lookup"><span data-stu-id="d2285-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![Adaptadores UART y UART USB](media/Troubleshooting/adapters.png)

<span data-ttu-id="d2285-161">Puede leer [este artículo](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) para obtener más información sobre cómo inicializar UART0 y realizar una operación de escritura seguida de una de lectura.</span><span class="sxs-lookup"><span data-stu-id="d2285-161">You can read [this article](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="d2285-162">Además, la comunicación por radiofrecuencia (RFCOMM) es la comunicación de serie subyacente para Bluetooth clásico.</span><span class="sxs-lookup"><span data-stu-id="d2285-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="d2285-163">Consulte [este ejemplo de GitHub](https://github.com/djaus2/iotbluetoothserial) para obtener información sobre la ejecución de aplicaciones para UWP en Windows 10 IoT Core conectadas a través de un dispositivo de IoT con Bluetooth de serie.</span><span class="sxs-lookup"><span data-stu-id="d2285-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="d2285-164">Si comprueba que el dispositivo no puede leer o escribir datos a través del puerto serie, siga estos pasos para solucionar problemas:</span><span class="sxs-lookup"><span data-stu-id="d2285-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="d2285-165">Conecte la transmisión (TX) a la recepción (RX) mediante el puente (mostrado a continuación) y después ejecute el código de ejemplo para comprobar si la aplicación puede leer o escribir datos.</span><span class="sxs-lookup"><span data-stu-id="d2285-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="d2285-166">Si esto no funciona, es posible que el circuito integrado de la placa esté dañado.</span><span class="sxs-lookup"><span data-stu-id="d2285-166">If this does not work, the IC on the board may be broken.</span></span>

![TX a RX en Raspberry Pi](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="d2285-168">Asegúrese de que la velocidad en baudios, el enlace y los bits de parada están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="d2285-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="d2285-169">Si el puerto serie que se va a probar tiene una interfaz RS232 completa (por ejemplo, DB9), use un conector DB con los cables cruzados RxTx conectados con los cables cruzados de enlace típicos.</span><span class="sxs-lookup"><span data-stu-id="d2285-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="d2285-170">Algunos puertos RS232 (o adaptadores USB) requieren que se confirmen señales como las de detección de operador (DCD) y DCE listo (DSR) antes de funcionar correctamente.</span><span class="sxs-lookup"><span data-stu-id="d2285-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="d2285-171">Si quiere usar adaptadores UART USB en Windows 10 IoT Core, se admiten los siguientes:</span><span class="sxs-lookup"><span data-stu-id="d2285-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="d2285-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="d2285-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="d2285-173">Convertidor serie del módulo TTL</span><span class="sxs-lookup"><span data-stu-id="d2285-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="d2285-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="d2285-174">FTDI</span></span>
* <span data-ttu-id="d2285-175">usbser.sys genérico</span><span class="sxs-lookup"><span data-stu-id="d2285-175">Generic usbser.sys</span></span>

<span data-ttu-id="d2285-176">También puede usar la pila devcon.exe \* y el cmdlet devcon.exe status\* para comprobar la pila de controladores esperada y el estado de los controladores en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d2285-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="d2285-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) es otra herramienta útil para solucionar problemas de puerto serie.</span><span class="sxs-lookup"><span data-stu-id="d2285-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="d2285-178">Esta herramienta puede enumerar puertos, proporcionar sus nombres descriptivos y los identificadores de dispositivo, abrir puertos, configurar ajustes (como la velocidad en baudios, los bits de parada, etc.) y enviar y recibir datos.</span><span class="sxs-lookup"><span data-stu-id="d2285-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="d2285-179">Servicio de prueba Sirep</span><span class="sxs-lookup"><span data-stu-id="d2285-179">Sirep Test service</span></span>
<span data-ttu-id="d2285-180">Aunque el servicio de prueba Sirep no está habilitado de manera predeterminada en las imágenes comerciales, si todavía quiere deshabilitarlo al inicio, puede iniciar sesión y deshabilitar el inicio automático de Sirep.</span><span class="sxs-lookup"><span data-stu-id="d2285-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="d2285-181">Puede usar los comandos de PowerShell siguientes para hacerlo, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="d2285-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

```
administrator@MINWINPC C:\Data\Users\administrator>sc stop TestSirepSvc

SERVICE_NAME: TestSirepSvc
       TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 3  STOP_PENDING
                                (STOPPABLE, NOT_PAUSABLE, ACCEPTS_PRESHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x4
        WAIT_HINT          : 0x1770

administrator@MINWINPC C:\Data\Users\administrator>sc query TestSirepSvc

SERVICE_NAME: TestSirepSvc
        TYPE               : 20  WIN32_SHARE_PROCESS
        STATE              : 1  STOPPED
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        CHECKPOINT         : 0x0
        WAIT_HINT          : 0x0

administrator@MINWINPC C:\Data\Users\administrator>sc config TestSirepSvc start=disabled
[SC] ChangeServiceConfig SUCCESS
```

## <a name="tablet-mode"></a><span data-ttu-id="d2285-182">Modo tableta</span><span class="sxs-lookup"><span data-stu-id="d2285-182">Tablet mode</span></span>

<span data-ttu-id="d2285-183">El "modo tableta" es un concepto que solo existe en el shell de Desktop y no se aplica a IoT Core.</span><span class="sxs-lookup"><span data-stu-id="d2285-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="d2285-184">Si el dispositivo tiene hardware compatible (ya sea a través de I2C o USB HID Touch), la función táctil debería funcionar de forma automática con los controladores de clase de bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="d2285-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="d2285-185">Puedes leer más sobre esto [aquí](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span><span class="sxs-lookup"><span data-stu-id="d2285-185">You can read more about this [here](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="d2285-186">Compatibilidad con Yubikey</span><span class="sxs-lookup"><span data-stu-id="d2285-186">Yubikey support</span></span>

<span data-ttu-id="d2285-187">Windows 10 IoT Core no es compatible con tarjetas inteligentes.</span><span class="sxs-lookup"><span data-stu-id="d2285-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="d2285-188">Pero las tarjetas inteligentes suelen ser dispositivos que se usan para la identidad del usuario y no la del dispositivo, ya que están protegidas mediante PIN y, en el caso de Yubikey, un botón que hay que presionar.</span><span class="sxs-lookup"><span data-stu-id="d2285-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="d2285-189">Esto no concuerda con un dispositivo IoT.</span><span class="sxs-lookup"><span data-stu-id="d2285-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="d2285-190">Si busca una alternativa, un TPM 2.0 en el dispositivo puede ser más indicado que Yubikey o una tarjeta inteligente.</span><span class="sxs-lookup"><span data-stu-id="d2285-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="d2285-191">Contamos con soporte para certificados completo para TPM y están diseñados para almacenar dispositivos, así como certificados de usuario y credenciales de acceso de Azure IoT (Limpets).</span><span class="sxs-lookup"><span data-stu-id="d2285-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
