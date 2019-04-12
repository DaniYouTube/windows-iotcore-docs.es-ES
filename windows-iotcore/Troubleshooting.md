---
author: saraclay
Description: Solución de problemas de diferentes problemas relacionados con el desarrollo.
title: Solución de problemas
ms.author: saclayt
ms.date: 08/28/18
ms.topic: article
ms.openlocfilehash: 00c748e4ce06e960dbc2a4250fb3cb279f4d092a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514747"
---
# <a name="troubleshooting"></a><span data-ttu-id="e43e3-103">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="e43e3-103">Troubleshooting</span></span>
<span data-ttu-id="e43e3-104">Se trata de un artículo que contiene los problemas más comunes que las personas han llegado a través.</span><span class="sxs-lookup"><span data-stu-id="e43e3-104">This is an article that contains common troubleshooting issues that people have come across.</span></span> <span data-ttu-id="e43e3-105">Para buscar un elemento específico, use Ctrl + F para buscar una palabra o frase.</span><span class="sxs-lookup"><span data-stu-id="e43e3-105">To find something specific, use Ctrl+F to find a word or phrase.</span></span> <span data-ttu-id="e43e3-106">¿Tendría ninguna idea de que desea agregar?</span><span class="sxs-lookup"><span data-stu-id="e43e3-106">Have any insight you want to add?</span></span> <span data-ttu-id="e43e3-107">Crear una solicitud para esta documentación o previsión comentarios sobre el contenido siguiente.</span><span class="sxs-lookup"><span data-stu-id="e43e3-107">Create a PR for this documentation or provident content feedback below.</span></span>

> [!TIP]
> <span data-ttu-id="e43e3-108">Para solucionar problemas relacionados con la fabricación, lea el [documento de solución de problemas](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) en nuestra guía de fabricación.</span><span class="sxs-lookup"><span data-stu-id="e43e3-108">For troubleshooting issues related to manufacturing, please read the [Troubleshooting doc](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) in our manufacturing guide.</span></span>

## <a name="asus-tinkerboard-and-rockchip-support"></a><span data-ttu-id="e43e3-109">Compatibilidad con ASUS Tinkerboard y Rockchip</span><span class="sxs-lookup"><span data-stu-id="e43e3-109">ASUS Tinkerboard and Rockchip support</span></span>

<span data-ttu-id="e43e3-110">Aunque el ASUS Tinkerboard y Rockchip no se admiten oficialmente por nuestra parte, hay casos donde Rockchip ha trabajado con terceras partes obtener SoC trabajando en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e43e3-110">While the ASUS Tinkerboard and Rockchip are not officially supported by us, there are cases where Rockchip has worked with other third parties to get SoC working on Windows 10 IoT Core.</span></span>

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a><span data-ttu-id="e43e3-111">Problema al conectar un dispositivo MBM itinerancia</span><span class="sxs-lookup"><span data-stu-id="e43e3-111">Issue when connecting a MBM device when roaming</span></span>

<span data-ttu-id="e43e3-112">Hay dos cosas a tener en cuenta al habilitar la itinerancia:</span><span class="sxs-lookup"><span data-stu-id="e43e3-112">There are two things to consider when enabling roaming:</span></span>

1. <span data-ttu-id="e43e3-113">El profile.xml configura itinerancia y establece el comportamiento para establecer automáticamente una conexión a la red de telefonía móvil.</span><span class="sxs-lookup"><span data-stu-id="e43e3-113">The profile.xml configures roaming and sets the behavior to automatically establish a connection to the cellular network.</span></span>
<span data-ttu-id="e43e3-114">Para establecer un perfil para móviles, consulte [en este artículo](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span><span class="sxs-lookup"><span data-stu-id="e43e3-114">To set a profile for roaming please refer to [this article](https://docs.microsoft.com/windows/desktop/mbn/schema-root).</span></span>

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

<span data-ttu-id="e43e3-115">Para establecer un perfil de conexión automática, seleccione "auto":</span><span class="sxs-lookup"><span data-stu-id="e43e3-115">To set a profile for automatic connection, select "auto":</span></span>

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

2. <span data-ttu-id="e43e3-116">Otro factor es que debe cumplirse la directiva de movilidad por interfaz.</span><span class="sxs-lookup"><span data-stu-id="e43e3-116">Another factor is that the per-interface roaming policy must be satisfied.</span></span> <span data-ttu-id="e43e3-117">De forma predeterminada, esa directiva se establece en FALSE ("home transportista solo").</span><span class="sxs-lookup"><span data-stu-id="e43e3-117">By default, that policy is set to FALSE ("home carrier only").</span></span> <span data-ttu-id="e43e3-118">Esto se puede consultar y cambiar en la línea de comandos a través de</span><span class="sxs-lookup"><span data-stu-id="e43e3-118">This can be queried and changed in command line via</span></span> `netsh mbn get/set dataroamcontrol.`

<span data-ttu-id="e43e3-119">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e43e3-119">Example:</span></span>

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

<span data-ttu-id="e43e3-120">Puede obtener error **0x139f (ERROR_INVALID_STATE)** en el caso cuando el dispositivo está en itinerancia, pero la directiva de movilidad no permite la itinerancia de datos - error en una solicitud de conexión enviado a wwansvc.</span><span class="sxs-lookup"><span data-stu-id="e43e3-120">You may get error **0x139f (ERROR_INVALID_STATE)** in the case when the device is roaming but the roaming policy disallows data roaming - error on a connect request sent to wwansvc.</span></span>

## <a name="raspberry-pi-3b-booting-issues"></a><span data-ttu-id="e43e3-121">Raspberry Pi 3B + arranque problemas</span><span class="sxs-lookup"><span data-stu-id="e43e3-121">Raspberry Pi 3B+ booting issues</span></span>

> [!NOTE]
> <span data-ttu-id="e43e3-122">Esta versión para el dispositivo Raspberry Pi 3B + es una versión preliminar técnica no admitida.</span><span class="sxs-lookup"><span data-stu-id="e43e3-122">This release for the Raspberry Pi 3B+ is an unsupported technical preview.</span></span> <span data-ttu-id="e43e3-123">Se ha completado la habilitación y la validación limitada.</span><span class="sxs-lookup"><span data-stu-id="e43e3-123">Limited validation and enablement has been completed.</span></span> <span data-ttu-id="e43e3-124">Para obtener una mejor evaluación experimentar y para los productos comerciales, use el 3B Raspberry Pi u otros dispositivos con Intel, Qualcomm o NXP Qualcomm admitidos.</span><span class="sxs-lookup"><span data-stu-id="e43e3-124">For a better evaluation experience and for any commercial products, please use the Raspberry Pi 3B or other devices with supported Intel, Qualcomm, or NXP SoCs.</span></span> <span data-ttu-id="e43e3-125">Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B +, consulte nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span><span class="sxs-lookup"><span data-stu-id="e43e3-125">For troubleshooting issues with the Raspberry Pi 3B+, please see our Troubleshooting Guide, [here](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues).</span></span> 

<span data-ttu-id="e43e3-126">El dispositivo Raspberry Pi 3 modelo B + es el producto más reciente en el intervalo de Raspberry Pi 3, haciendo alarde de un procesador quad core de 64 bits a 1,4 GHz, doble banda 2,4 GHz y 5 GHz redes LAN inalámbricas, Ethernet 4.2/BLE, más rápido de Bluetooth y PoE capacidad a través de una independiente PoE alta disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="e43e3-126">The Raspberry Pi 3 Model B+ is the latest product in the Raspberry Pi 3 range, boasting a 64-bit quad core processor running at 1.4GHz, dual-band 2.4GHz and 5GHz wireless LAN, Bluetooth 4.2/BLE, faster Ethernet, and PoE capability via a separate PoE HA.</span></span>

<span data-ttu-id="e43e3-127">Recientemente, muchos clientes que están interesados en Windows 10 IoT Core encontró un problema donde el dispositivo no pudo iniciar normalmente después de vaciar Windows 10 IoT Core, pero la Raspbian funciona bien en él.</span><span class="sxs-lookup"><span data-stu-id="e43e3-127">Recently, many customers who are interested in Windows 10 IoT Core encountered a problem where the device could not boot normally after flushing Windows 10 IoT Core, but the Raspbian works fine on it.</span></span> <span data-ttu-id="e43e3-128">Las siguientes son algunas sugerencias sobre cómo solucionar el problema de inicio.</span><span class="sxs-lookup"><span data-stu-id="e43e3-128">The following are some suggestions on how to troubleshoot the boot problem.</span></span>

<span data-ttu-id="e43e3-129">Hay algunos problemas conocidos en esta imagen de vista previa de Insider.</span><span class="sxs-lookup"><span data-stu-id="e43e3-129">There are some known issues in this Insider Preview image.</span></span> <span data-ttu-id="e43e3-130">Tenga en cuenta:</span><span class="sxs-lookup"><span data-stu-id="e43e3-130">Please note that:</span></span>
* <span data-ttu-id="e43e3-131">Esta imagen solo está pensada para el dispositivo Raspberry Pi 3B + y no se iniciará en el Pi Raspbierry 2.</span><span class="sxs-lookup"><span data-stu-id="e43e3-131">This image is only meant for the Raspberry Pi 3B+ and will not boot on the Raspbierry Pi 2.</span></span>
* <span data-ttu-id="e43e3-132">Implementación de controladores de F5 desde Visual Studio no funciona en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e43e3-132">F5 driver deployment from Visual Studio does not work on Windows 10 IoT Core.</span></span>
* <span data-ttu-id="e43e3-133">Incorporación de Wi-Fi y Bluetooth no funcionan en el Raspberry Pi 3B +.</span><span class="sxs-lookup"><span data-stu-id="e43e3-133">Onboard Wi-Fi and Bluetooth do not work on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="e43e3-134">Controlador de pantalla táctil Ft5406 está deshabilitado en el Raspberry Pi 3B +.</span><span class="sxs-lookup"><span data-stu-id="e43e3-134">Ft5406 touch screen driver is disabled on the Raspberry Pi 3B+.</span></span>
* <span data-ttu-id="e43e3-135">Está deshabilitado el LED de actividad de tarjeta SD.</span><span class="sxs-lookup"><span data-stu-id="e43e3-135">SD card activity LED is disabled.</span></span>

<span data-ttu-id="e43e3-136">Hay solo dos requisitos al elegir qué tarjetas SD para usar con Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e43e3-136">There are only two requirements when choosing which SD cards to use with Windows 10 IoT Core.</span></span> <span data-ttu-id="e43e3-137">Deberá usar una tarjeta SD de clase 10 y asegúrese de que la tarjeta tiene suficiente espacio - al menos 8 GB de espacio.</span><span class="sxs-lookup"><span data-stu-id="e43e3-137">You need to use a class 10 SD card and make sure the card has enough space - at least 8 GB of space.</span></span> <span data-ttu-id="e43e3-138">Hay un par de tarjetas SD que se han comprobado por Microsoft para que sean compatibles con Windows 10 IoT Core:</span><span class="sxs-lookup"><span data-stu-id="e43e3-138">There are a couple of SD cards that have been verified by Microsoft to be compatible with Windows 10 IoT Core:</span></span>
* <span data-ttu-id="e43e3-139">Tarjeta de SDHC con Micros clase 10 Samsung EVO 32 GB</span><span class="sxs-lookup"><span data-stu-id="e43e3-139">Samsung EVO 32 GB class 10 Micros SDHC card</span></span>
* <span data-ttu-id="e43e3-140">SanDisk Ultra Micro SDHC con, tarjeta de 16 GB</span><span class="sxs-lookup"><span data-stu-id="e43e3-140">SanDisk Ultra Micro SDHC, 16 GB card</span></span>

<span data-ttu-id="e43e3-141">Por lo general, deberá comprobar si la tarjeta SD es falsa, o si está dañado.</span><span class="sxs-lookup"><span data-stu-id="e43e3-141">Generally, you need to check if the SD card is fake or if it is damaged or corrupt.</span></span> <span data-ttu-id="e43e3-142">La tarjeta SD es igualmente proclives a daños debido a una variedad de factores como la escasez de energía o eliminación incorrecta.</span><span class="sxs-lookup"><span data-stu-id="e43e3-142">The SD card is equally prone to corruption due to a variety of factors such as power shortage or improper removal.</span></span> <span data-ttu-id="e43e3-143">Es importante proteger su tarjeta de memoria de daños.</span><span class="sxs-lookup"><span data-stu-id="e43e3-143">It is important to safeguard your memroy card from damage.</span></span>

<span data-ttu-id="e43e3-144">Para actualizar la imagen en una tarjeta SD, puede usar el [panel de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span><span class="sxs-lookup"><span data-stu-id="e43e3-144">To flash your image to a SD card, you can use the [Windows 10 IoT Core Dashboard](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard).</span></span> <span data-ttu-id="e43e3-145">Deberá elegir "Custom" en el campo de la compilación del sistema operativo y luego seleccione el archivo FFU a flash.</span><span class="sxs-lookup"><span data-stu-id="e43e3-145">You will need to choose "Custom" in the OS Build field, then select the FFU file to flash.</span></span> 

<span data-ttu-id="e43e3-146">Compruebe si hay cualquier error de hardware en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e43e3-146">Check to see if there are any hardware failure in the device.</span></span> <span data-ttu-id="e43e3-147">Hay dos LED en la placa de Raspberry Pi 3B + igual que el 3B.</span><span class="sxs-lookup"><span data-stu-id="e43e3-147">There are two LEDs on the Raspberry Pi 3B+ board, same as the 3B.</span></span> <span data-ttu-id="e43e3-148">Uno es potencia mientras hay otra para ACT.</span><span class="sxs-lookup"><span data-stu-id="e43e3-148">One is for PWR while another is for ACT.</span></span> <span data-ttu-id="e43e3-149">El número de parpadeos hace que la ley de luz determinará si se está iniciando la placa.</span><span class="sxs-lookup"><span data-stu-id="e43e3-149">The number of blinks the ACT light makes will determine whether or not your board is booting.</span></span> <span data-ttu-id="e43e3-150">El LED de actividad de tarjeta SD no parpadeará durante algunas partes de arranque en el Raspberry Pi 3B +.</span><span class="sxs-lookup"><span data-stu-id="e43e3-150">The SD card activity LED will not flash during some portions of booting on the Raspberry Pi 3B+.</span></span>

<span data-ttu-id="e43e3-151">Cuando se arranca el dispositivo y el dispositivo muestra la página de espera, espere pacientemente.</span><span class="sxs-lookup"><span data-stu-id="e43e3-151">When the device is booting and the device shows the waiting page, please wait patiently.</span></span> <span data-ttu-id="e43e3-152">Por lo general, esto estará en vigor hasta un minuto.</span><span class="sxs-lookup"><span data-stu-id="e43e3-152">Generally, this will last up to a minute.</span></span> <span data-ttu-id="e43e3-153">Pero en ocasiones, debido a la velocidad de lectura y escritura de tarjeta SD, es posible que tarde más tiempo.</span><span class="sxs-lookup"><span data-stu-id="e43e3-153">But sometimes, due to the SD card read-write speed, it may take longer.</span></span>

<span data-ttu-id="e43e3-154">Si el dispositivo no puede arrancar normalmente con Windows 10 IoT Core, puede intentar flash un sistema operativo Linux (por ejemplo, Raspbian) en la tarjeta SD para concretar si el problema está causado por hardware.</span><span class="sxs-lookup"><span data-stu-id="e43e3-154">If the device can't boot normally with Windows 10 IoT Core, you can try to flash a Linux OS (such as Raspbian) to the SD card to narrow down whether the issue is caused by hardware.</span></span> 

<span data-ttu-id="e43e3-155">Si encuentra que está obteniendo una "pantalla de arco iris", compruebe para asegurarse de que se vacían la 3B + versión de lanzamiento, disponible [aquí](https://www.microsoft.com/en-us/software-download/windowsiot).</span><span class="sxs-lookup"><span data-stu-id="e43e3-155">If you find that you're getting a "rainbow screen", please check to make sure that you flashed the 3B+ release version, available [here](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="e43e3-156">Puede comprobar el proceso con un 3B Comunidad + parpadeando tutorial [aquí](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span><span class="sxs-lookup"><span data-stu-id="e43e3-156">You can verify your process with a community-submitted 3B+ flashing tutorial [here](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).</span></span>

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a><span data-ttu-id="e43e3-157">Comunicación de puerto serie en Windows 10 IoT Core para Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="e43e3-157">Serial Port communication on Windows 10 IoT Core for Raspberry Pi</span></span> 

<span data-ttu-id="e43e3-158">En el dispositivo Raspberry Pi, hardware UART USB UART adaptadores y ambos son utilizables para su aplicación con la comunicación serie.</span><span class="sxs-lookup"><span data-stu-id="e43e3-158">On the Raspberry Pi, hardware UART and USB UART adapters both are usable for your application with serial communicaiton.</span></span> <span data-ttu-id="e43e3-159">Forma predeterminada, la transmisión UART y recibir los PIN son los pines 8 y 10 en el encabezado GPIO.</span><span class="sxs-lookup"><span data-stu-id="e43e3-159">By default, the UART transmit and receive pins are pins 8 and 10 on teh GPIO header.</span></span>

![UART y USB UART adaptadores](media/Troubleshooting/adapters.png)

<span data-ttu-id="e43e3-161">Puede leer [en este artículo](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) para obtener más información sobre cómo inicializar UART0 y realizar una operación de escritura seguido de una lectura.</span><span class="sxs-lookup"><span data-stu-id="e43e3-161">You can read [this article](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) to learn more about how to initialize UART0 and perform a write followed by a read.</span></span>

<span data-ttu-id="e43e3-162">Además, la comunicación por radiofrecuencia (RFCOMM) es las comunicaciones en serie subyacentes Bluetooth clásico.</span><span class="sxs-lookup"><span data-stu-id="e43e3-162">In addition, Radio Frequency Communication (RFCOMM) is the underlying serial communications for classic Bluetooth.</span></span> <span data-ttu-id="e43e3-163">Consulte [en este ejemplo de GitHub](https://github.com/djaus2/iotbluetoothserial) para obtener información sobre cómo ejecutar las aplicaciones para UWP en Windows 10 IoT Core a conectado a través de un dispositivo de IoT con el número de serie de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="e43e3-163">Refer to [this GitHub sample](https://github.com/djaus2/iotbluetoothserial) to learn about running UWP apps on Windows 10 IoT Core to connected over an IoT device with Bluetooth Serial.</span></span>

<span data-ttu-id="e43e3-164">Si encuentra que el dispositivo no puede leer o escribir datos a través del puerto serie, siga estos pasos para solucionar problemas:</span><span class="sxs-lookup"><span data-stu-id="e43e3-164">If you encounter that the device cannot read/write data through the serial port, follow the steps below to troubleshoot:</span></span>

1. <span data-ttu-id="e43e3-165">Conectar TX RX con puentes - se muestra a continuación: después de ejecutar el código de ejemplo para comprobar si la aplicación puede leer o escribir datos.</span><span class="sxs-lookup"><span data-stu-id="e43e3-165">Connect the TX to RX with Jumper - shown below - then run the sample code to check if the app can read/write data.</span></span> <span data-ttu-id="e43e3-166">Si esto no funciona, el IC en el panel pueden dejar de funcionar.</span><span class="sxs-lookup"><span data-stu-id="e43e3-166">If this does not work, the IC on the board may be broken.</span></span>

![TX a RX en Raspberry Pi](media/Troubleshooting/txrx.png)

2. <span data-ttu-id="e43e3-168">Asegúrese de que la velocidad en baudios, el protocolo de enlace y StopBits están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="e43e3-168">Make sure the BaudRate, Handshaking and StopBits are configured correctly.</span></span> <span data-ttu-id="e43e3-169">Si el puerto serie que va a probarse tiene una interfaz RS232 completa (por ejemplo, DB9), use un enchufe de la base de datos con los cables de entrecruzamiento RxTx conectados con los crossovers típico de protocolo de enlace.</span><span class="sxs-lookup"><span data-stu-id="e43e3-169">If the serial port to be tested has a complete RS232 interface (e.g. DB9), use a DB plug with the RxTx crossover wires connected with the typical handshaking crossovers.</span></span> <span data-ttu-id="e43e3-170">Algunos puertos RS232 (o adaptadores USB) requieren las señales, como portadora detectar (DCD) y DCE preparado (DSR) imponerse antes de que funcionen correctamente.</span><span class="sxs-lookup"><span data-stu-id="e43e3-170">Some RS232 ports (or USB adapters) require signals such as Carrier Detect (DCD) and DCE Ready (DSR) to be asserted before they function properly.</span></span>

3. <span data-ttu-id="e43e3-171">Si desea usar adaptadores USB UART en Windows 10 IoT Core, se admite lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e43e3-171">If you want to use USB UART adapters on Windows 10 IoT Core, the following are supported:</span></span>

* <span data-ttu-id="e43e3-172">CP2102 USB 2.0</span><span class="sxs-lookup"><span data-stu-id="e43e3-172">CP2102 USB 2.0</span></span>
* <span data-ttu-id="e43e3-173">Convertidor serie del módulo TTL</span><span class="sxs-lookup"><span data-stu-id="e43e3-173">TTL Module Serial Converter</span></span>
* <span data-ttu-id="e43e3-174">FTDI</span><span class="sxs-lookup"><span data-stu-id="e43e3-174">FTDI</span></span>
* <span data-ttu-id="e43e3-175">Usbser.sys genérico</span><span class="sxs-lookup"><span data-stu-id="e43e3-175">Generic usbser.sys</span></span>

<span data-ttu-id="e43e3-176">También puede usar la pila devcon.exe \* y devcon.exe estado \* cmdlet para comprobar la pila de controladores esperado y el estado de los controladores en Windows 10 IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e43e3-176">You can also use the devcon.exe stack \* and devcon.exe status\* cmdlet to check the expected drivers stack and drivers status on Windows 10 IoT Core.</span></span>

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
<span data-ttu-id="e43e3-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) es otra herramienta útil para solucionar problemas de puerto serie.</span><span class="sxs-lookup"><span data-stu-id="e43e3-177">[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) is another helpful tool to troubleshoot serial port issues.</span></span> <span data-ttu-id="e43e3-178">Esta herramienta puede enumerar los puertos, proporcionarle su nombre descriptivo y el Id. de dispositivo, abra los puertos, configuración (es decir, velocidad en baudios, bits de parada, etc.) y enviar y recibir datos.</span><span class="sxs-lookup"><span data-stu-id="e43e3-178">This tool can enumerate ports, give you their friendly name and Device ID, open ports, configure settings (i.e. baud rate, stop bits, etc.) and send and receive data.</span></span> 

## <a name="sirep-test-service"></a><span data-ttu-id="e43e3-179">Servicio de prueba Sirep</span><span class="sxs-lookup"><span data-stu-id="e43e3-179">Sirep Test service</span></span>
<span data-ttu-id="e43e3-180">Aunque el servicio de prueba Sirep no está habilitado de forma predeterminada en las imágenes de venta directa, en caso de que desea deshabilitar el servicio Sirep en Inicio, puede iniciar sesión y deshabilitar Sirep de inicio automático.</span><span class="sxs-lookup"><span data-stu-id="e43e3-180">Even though the Sirep Test service is not enabled by default in retail images, in case you still want to disable the Sirep service on startup, you can login and disable Sirep from autostart.</span></span> 

<span data-ttu-id="e43e3-181">Puede usar los siguientes comandos de PowerShell para hacerlo, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="e43e3-181">You can use the following PowerShell commands to do so, as shown below:</span></span>

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

## <a name="tablet-mode"></a><span data-ttu-id="e43e3-182">Modo tableta</span><span class="sxs-lookup"><span data-stu-id="e43e3-182">Tablet mode</span></span>

<span data-ttu-id="e43e3-183">"Modo de Tablet PC" es un concepto que solo existen en el shell de escritorio y no se aplica a IoT Core.</span><span class="sxs-lookup"><span data-stu-id="e43e3-183">"Tablet Mode" is a concept that only exist on Desktop shell and doesn’t apply to IoT Core.</span></span> 

<span data-ttu-id="e43e3-184">Si el dispositivo tiene hardware (ya sea a través de I2C o USB HID touch) compatible, toque debería funcionar automáticamente con los controladores de clase de la Bandeja de entrada.</span><span class="sxs-lookup"><span data-stu-id="e43e3-184">If the device have supported hardware (either through I2C or USB HID touch), touch should function automatically using the inbox class drivers.</span></span> <span data-ttu-id="e43e3-185">Puede leer más sobre esto [aquí](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span><span class="sxs-lookup"><span data-stu-id="e43e3-185">You can read more about this [here](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).</span></span>


## <a name="yubikey-support"></a><span data-ttu-id="e43e3-186">Compatibilidad con Yubikey</span><span class="sxs-lookup"><span data-stu-id="e43e3-186">Yubikey support</span></span>

<span data-ttu-id="e43e3-187">Windows 10 IoT Core no tiene compatibilidad con tarjetas inteligentes.</span><span class="sxs-lookup"><span data-stu-id="e43e3-187">Windows 10 IoT Core does not have smart card support.</span></span> <span data-ttu-id="e43e3-188">Sin embargo, las tarjetas inteligentes suelen ser dispositivos usados para la identidad del usuario y la identidad del dispositivo no porque están protegidas con clavijas y, en el caso de lo Yubikey, presione un botón.</span><span class="sxs-lookup"><span data-stu-id="e43e3-188">However, smart cards are usually devices used for user identity and not device identity because they are secured with PINs and, in the case of the Yubikey, a button to press.</span></span> <span data-ttu-id="e43e3-189">Esto no armonizar con un dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="e43e3-189">This does not harmonize with an IoT device.</span></span> <span data-ttu-id="e43e3-190">Si está buscando una alternativa, un TPM 2.0 en el dispositivo puede servir mejor que un Yubikey o una tarjeta inteligente.</span><span class="sxs-lookup"><span data-stu-id="e43e3-190">If you're looking for an alternative, a TPM 2.0 on the device may serve better than a Yubikey or smart card.</span></span> <span data-ttu-id="e43e3-191">Contamos con compatibilidad de certificados completa para TPM y están diseñadas para almacenar los dispositivos, así como los certificados de usuario y credenciales de acceso de Azure IoT (Limpets).</span><span class="sxs-lookup"><span data-stu-id="e43e3-191">We have full certificate support for TPMs and they are meant to store devices as well as user certificates and Azure IoT access credentials (Limpets).</span></span>
