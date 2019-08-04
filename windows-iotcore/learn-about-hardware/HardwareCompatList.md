---
title: Lista de compatibilidad de hardware
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las interfaces y los protocolos de periféricos que admite Windows 10 IoT Core.
keywords: Windows IOT, periféricos, protocolos, compatibilidad, buses, hardware
ms.openlocfilehash: d1d97c3bff2fe843216410d07530f4866136bc63
ms.sourcegitcommit: c5552007f5456e57512307f51b146406a23fa723
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2019
ms.locfileid: "68739827"
---
# <a name="hardware-compatibility-list"></a>Lista de compatibilidad de hardware

Windows 10 IoT Core admite una variedad de protocolos y interfaces de periféricos, incluida la compatibilidad con buses comunes como I2C, UART, USB, etc. En esta página se enumeran los periféricos compatibles conocidos y se encuentra en el momento de la versión RTM más reciente. Las entradas específicas solo pueden funcionar en las versiones de Insider y se indicarán como tales. Le recomendamos que contribuya en esta lista en GitHub.

> [!IMPORTANT]
> Esta lista no es exhaustiva. Hay muchos otros periféricos que no aparecen en esta página y que son compatibles con Windows 10 IoT Core. Si un dispositivo no aparece en la lista, pero es compatible con la clase, lo que ya se admite en Windows 10 IoT Core, funcionará. 


¿Busca información sobre las plataformas de hardware admitidas? Haga clic [aquí](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) para obtener una lista de los paneles de desarrollo compatibles con Windows.

## <a name="usb-devices"></a>Dispositivos USB

### <a name="wifi-adapters"></a>Adaptadores de WiFi
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | Llave de Wi-Fi oficial de Raspberry PI | ARM32, x64, x86 | El adaptador WiFi de Raspberry PI oficial ofrece el mejor rendimiento de Wi-Fi posible para su tamaño de diminutive. | | &#10004;  |
> | Adaptador USB Airlink Wireless N 150 mini | x64, x86 | Adaptador USB Mini inalámbrico Airlink 101 AWL5077 dorado con WPA2, WPA y WEP mejorado | | &#10004;  
> | Panda PAU06 | x64, x86 |  Adaptador USB de Panda 300 Mbps Inalámbrico N con antena de alta ganancia | |  &#10004;  
> | TP-LINK TL_WN725N |  ARM32, x64, x86 | Adaptador TP-LINK TL-WN725N Wireless N Nano adaptador USB 150 Mbps`(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | Adaptador de red Wi-DIN USB WiFi | MBM | Adaptador USB WiFi NET-DYN | |  &#10004;  
> | Wi-Fi USB inalámbrico Realtek 8191 | ARM32, x64, x86 | Adaptador de tarjeta de red LAN inalámbrica WiFi Realtek 8191 300 g/g/b/USB | | &#10004;  
> | Wi-Fi USB inalámbrico Realtek 8192 | ARM32, x64, x86 | Controlador de WLAN de un solo chip IEEE 802.11 b/g/n 2T2R con la interfaz USB 2,0 | | &#10004; |
> | Wi-Fi USB inalámbrico Realtek 8188EU | ARM32, Mx64, x86BM | Adaptador de red de LAN inalámbrica 802.11 RTL8188EU n/g/b USB 2,0 | | &#10004; |
> | Wi-Fi USB inalámbrico Realtek 8192EU | ARM32, x64, x86 | Adaptador de red de LAN inalámbrica 802.11 RTL8192EU n/g/b USB 2,0 | | &#10004; |
> | CanaKit USB Wireless WiFi | x64, x86 | Chipset Ralink 5370 | | &#10004;
> | D-Link DWA-172 | ARM32 | Adaptador USB de alta ganancia de banda dual inalámbrica AC600 | [Hoja](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>Adaptadores Ethernet
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | Adaptador Ethernet 2,0 Fast Ethernet de ASIX AX88772 | ARM32, x64, x86 | Se trata de un ASIC alto y alto rendimiento integrado con una SRAM de 28 KB insertada para el almacenamiento en búfer de paquetes.  | | &#10004;  |


### <a name="bluetooth-dongles"></a>Llaves Bluetooth
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Adaptador Mini USB Bluetooth V 4,0 de CSR | ARM32, x64, x86 | Adaptador de clase 2 Bluetooth 4,0 Smart Ready, baja energía, energía dual |  | &#10004; 
> | Llave de ORICO BTA-403 Mini Bluetooth 4,0 USB | ARM32, x64, x86 | Llave de adaptador USB 4,0 del adaptador Bluetooth de bajo consumo de energía |  | &#10004; 
> | Adaptador Mini USB Bluetooth V 4,0 de CSR | x64, x86 | Adaptador de clase 2 Bluetooth 4,0 Smart Ready, baja energía, energía dual |  | &#10004;|

### <a name="cameras"></a>Cámaras
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Cámara USB 3000 de Microsoft LifeCam | ARM32, x64, x86 | Cámara web USB | [Proyecto de cámara de seguridad principal](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft LifeCam HD-5000 | ARM32, x64, x86 | Webcam HD de Microsoft LifeCam HD-5000 720p | | &#10004; |
> | ™ De Microsoft® LifeCam Studio | ARM32 | ™ De Microsoft® LifeCam Studio (modelo: Webcam de 1425) 1080p HD | | |
> | Logitech Webcam C210 | ARM32, x64, x86 | Cámara web de USB, 1.3 foto de MP |  |&#10004; |

### <a name="audio"></a>Audio
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Adaptador de sonido estéreo externo USB Sabrent, modelo AU-EMAC1 | ARM32, x64, x86 | Convierte señales de audio y micrófono de USB a 3,5 mm | | &#10004; 

### <a name="miscellaneous"></a>Varios
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Llave de Aeon Labs Z-Wave Z-Wave serie 2 dongle USB DSA02203-ZWUS | ARM32 | Serie 2 Z-Wave USB Z-Wave Controller |  | &#10004; |
> | [Pantalla de pantalla táctil de Chalkboard Electronics 7 "](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [Actualizando el firmware](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32, x64, x86 | Vodafone (Huawei) K5150 150 m. |  | &#10004;  |
> | Vodafone (Huawei) K5160 | ARM32, x64, x86 | Vodafone (Huawei) K5160 150 Mbps GSM/EDGE/3G/HSPA +/LTE-CAT4 módem USB de banda ancha móvil |  | |
> | Luz inalámbrica Sierra (340U de tarjetas de red) | x64, x86 |    Adaptador de banda ancha móvil móvil de sierra (340U) 4G LTE USB |  |&#10004; |
> | Controlador de Microsoft Xbox 360 | ARM32 | Un controlador de juegos USB compatible con HID para Xbox 360 de Microsoft | [Kit de robot](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM, x32 | Un mouse inalámbrico USB compatible con HID, teclado y controlador para juegos |  | &#10004; |

## <a name="other-hardware-peripherals"></a>Otros periféricos de hardware

### <a name="nfcrfidproximity"></a>NFC/RFID/proximidad
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Panel de demostración de NXP OM5577 | ARM32 | Panel de demostración del chip NFC de NXP PN7120. | [Documentación de ProximityDevice](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32, x64, x86 | Chips NFC de NXP admitidos. | | &#10004; |

### <a name="pi-hats"></a>Sombreros PI
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16-Channel PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | Agrega la capacidad de controlar hasta 16 servodirecciones sin ninguna sobrecarga adicional de procesamiento de Raspberry PI. Capacidad de ejecutar PWM hasta 1,6 KHz con una precisión de 12 bits. | [Ejemplo de C# IOT del tutorial de Adafruit](https://github.com/golaat/Adafruit.Pwm) | |
> | [GrovePi de las industrias Dexterity](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | Puede conectar cientos de sensores diferentes sin soldaduras, por lo que puede programarlos para supervisar, controlar y automatizar los dispositivos de su vida. | [Ejemplos de GrovePi](https://github.com/DexterInd/GrovePi/) | |
> | GoPiGo de las industrias Dexterity | ARM, x32 | GoPiGo es un robot agradables y completo de Raspberry PI que convierte su PI en un robot totalmente operativo. GoPiGo es una plataforma robótica móvil para el Raspberry PI desarrollado por las industrias de Dexterity. | [Ejemplos de GoPiGo](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |
> | [SeeedStudio de la base de Olivares para Raspberry PI](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi.html) |ARM| La Hat base Hat para RPI proporciona compatibilidad con el sistema Seeedstudio de los Raspbery PI.| [Biblioteca y ejemplos](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |
> | [SeeedStudio de la base de Olivares para Raspberry PI Zero](https://www.seeedstudio.com/Grove-Base-Hat-for-Raspberry-Pi-Zero-p-3187.html) |ARM| La Hat base Hat para RPI Zero proporciona compatibilidad con el sistema Seeedstudio de los Raspbery PI.| [Biblioteca y ejemplos](https://github.com/KiwiBryn/GroveBaseHatWindows10IoTCore) | |

### <a name="semtech-sx127x-based-lora-pi-hatshttpswwwsemtechcomproductswireless-rflora-transceivers"></a>[Semtech basados en SX127X Lora creada® PI](https://www.semtech.com/products/wireless-rf/lora-transceivers)
La tecnología de comunicaciones de espectro de Semtech de Lora creada® ultra-Long (de 100 a 10KM) tiene una gran inmunidad de interferencias y proporciona una solución de bajo costo para conectar los dispositivos de batería y solar a la infraestructura de red convencional.

> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit Lora creada 433MHz del capó](https://www.adafruit.com/product/4075) | ARM32 | 433MHz Lora creada, 3 botones y OLED. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Adafruit Lora creada 868-915MHz del capó](https://www.adafruit.com/product/4074) | ARM32 | 868/915MHz Lora creada conectividad, 3 botones y pantalla OLED. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Dragino Lora creada GPS Hat for RaspberryPI 433/868/915MHz](http://www.dragino.com/products/lora/item/106-lora-gps-hat.html) | ARM32 | Opciones de conectividad de 433/868/915MHz Lora creada y GPS. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Elecrow Lora creada RFM95 IoT Board for RPI 915MHz](https://www.elecrow.com/lora-rfm95-iot-board-for-rpi.html) | ARM32 | 915MHz Lora creada Connectivity y los sockets. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Trucos electrónicos Lora creada/LoraWan Shield para Raspberry PI Zero y PI3](https://www.tindie.com/products/electronictrik/loralorawan-shield-for-raspberry-pi-zero-and-pi3/) | ARM32 | 868/915MHz conectividad Lora creada y OLED opcional. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Escudo de puerta de enlace de LoRaWan de canal de M2M 1 para Raspberry PI](https://www.tindie.com/products/m2m/1-channel-lorawan-gateway-shield-for-raspberry-pi/) | ARM32 | Opciones de conectividad de 868/915/923MHz Lora creada. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [Placa de expansión uputronics Raspberry PI + Lora creada (TM)](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=68) | ARM32 | Opciones de conectividad de 433/868/915MHz Lora creada. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |
> | [uputronics Raspberry PiZero Lora creada (TM) Expansion Board](https://store.uputronics.com/index.php?route=product/product&path=61&product_id=99) | ARM32 | Opciones de conectividad dual 433/868/915MHz Lora creada. | [Biblioteca y ejemplos](https://github.com/KiwiBryn/RFM9XLoRa-Net) | |


### <a name="nordic-semiconductor-nrf24l01-wireless-pi-hatshttpswwwnordicsemicomproductslow-power-short-range-wirelessnrf24-series"></a>[Sombreros de nRF24L01 inalámbrica PI de Nordic semiconductor](https://www.nordicsemi.com/Products/Low-power-short-range-wireless/nRF24-series)
Nivel de datos de la banda de ISM de 2,5 GHz, 250Kbps, 1 Mbps y 2 Mbps. Los módulos de energía baja 10 de la gama de contadores, de alta potencia, 1KM.

> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Ceech Raspberry PI nRF24l01 + Shield](https://www.tindie.com/products/ceech/new-raspberry-pi-to-nrf24l01-shield/) |ARM| El complemento Raspberry PI NRF24l01 + Shield para el Raspberry PI es compatible con un solo módulo NRF24l01 + más un timbre y un área de prototipo.| [Biblioteca](https://github.com/techfooninja/Radios.RF24), [aplicación de ejemplo](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo), [modificación necesaria](https://blog.devmobile.co.nz/2017/07/31/nrf24-windows-10-iot-core-hardware/) | |
> | [Boros Rf2-dual nRF24L01 pHat](https://www.tindie.com/products/boros/borosrf2-dual-nrf24l01-phathat-rtc-for-pis/) |ARM| Boros RF2 admite hasta dos radios de NRF24L01 + y un RTC opcional.| [Biblioteca](https://github.com/techfooninja/Radios.RF24), [aplicación de ejemplo](https://github.com/KiwiBryn/nRF24L01Windows10IoTCoreDuinoDemo) | |


### <a name="port-expanders"></a>Ampliadores de puertos
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Ampliador de puertos de e/s de 8 bits de MCP23008 | ARM32, x64, x86 | Chip de interfaz I2C, expansor de puertos GPIO. 8 puertos, 18-PDIP paquete | [Ejemplo de explander de Puerto SPI](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | Ampliador de puertos de e/s de 16 bits de MCP23S17 | ARM32, x64, x86 | Chip de interfaz I2C, expansor de puertos GPIO. 16 puertos, 28-SPDIP paquete | [Ejemplo de piano interactivo](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="storage-media"></a>Medios de almacenamiento
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32 GB EVO clase 10 micro SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32, x64, x86 | Una tarjeta SD recomendada para dispositivos que pueden tener Windows 10 IoT Core Flash. | | &#10004;|
> | [SanDisk ultra micro SDHC 16 GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32, x64, x86 | Una tarjeta SD recomendada para dispositivos que pueden tener Windows 10 IoT Core Flash. | | &#10004; |

### <a name="sensors"></a>Sensores
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Temperatura básica de DHT11: sensor de humedad | ARM32, x64, x86 | Un sensor de humedad y temperatura digital básico, ultra de bajo costo. Utiliza un sensor de humedad de capacidad y un thermistor para medir el aire circundante y proporciona una señal digital en el PIN de datos (no se necesitan clavijas de entrada analógicas).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | Temperatura de DHT22: sensor de humedad | ARM32, x64, x86 | Un sensor de humedad y temperatura digital básico, ultra de bajo costo. Utiliza un sensor de humedad de capacidad y un thermistor para medir el aire circundante y proporciona una señal digital en el PIN de datos (no se necesitan clavijas de entrada analógicas).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | SparkFun el acelerómetro del eje triple de ADXL345 | ARM32, x64, x86 | Acelerómetro de MEMS pequeño, fino, de baja energía y de 3 ejes con una medición de alta resolución (13 bits) de hasta ± 16 g. Los datos de salida digital se formatean como complementos de dos bits de 16 bits y son accesibles a través de un SPI (3 o 4 cables) o de una interfaz digital I2C. |[Ejemplo de acelerómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | Temperatura de BMP280 de Adafruit y sensor barométrica | ARM32 | Sensor del entorno de Bosch con temperatura, presión barométrica | |   &#10004; |
> | [Sensor de color de Adafruit TCS34725](http://www.adafruit.com/products/1334) | ARM, x32 | Sensor de color RGB con filtro de INFRARROJOs y LED blanco-TCS34725 | | &#10004; |
> | Sensor de luz ambiente de Rohm BH1750FVI | ARM32 | Sensor I2C pequeño para medición de luz ambiente | [Ejemplos de I2C](https://github.com/mickut/Win10-IoT-Sensors) | |
> | BMP180 de la temperatura y el sensor barométrica de Bosch | ARM, x32 | Sensor del entorno de Bosch con tempreature, presión barométrica | [Ejemplos de I2C](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Sensor de humedad relativa de Dorji DSTH01 | ARM32 | Sensor de humedad relativa de I2C | [Ejemplos de I2C](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L digital 3-AXIS Compass/magnetómetro | ARM32 | Un magnetómetro pequeño de 3 ejes para el uso de brújula digital y las mediciones de campos magnéticos | [Ejemplos de I2C](https://github.com/mickut/Win10-IoT-Sensors) | |

### <a name="touchpanel-solutions"></a>Soluciones Touchpanel
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Keith & Koep i-PAN M7 CoverLens | ARM32 | Equipo Touchpanel de 7,0 pulgadas para uso industrial con Qualcomm Snapdragon 410E CPU, resolución 800x480px, brillo 850cd/QM, USB 2,0, tarjeta SD, POE | [i-PAN información de M7](https://keith-koep.com/en/products/products-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technical-data/) | &#10004; |


### <a name="miscellaneous"></a>Varios
> | Nombre de la parte/no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft verificó | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Presentación de PI oficial | ARM32 | 7 "800x480 Touch display. | [Pantalla táctil de Raspberry PI 7](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | Pantalla gráfica monocromática 1,3 "128x64 OLED |ARM, x32, x64, x86 | 1,3 "pantalla de OLED de alto contraste B/W. 128x64 en blanco OLED píxeles individuales, cada uno está activado o desactivado por el chip del controlador. | [Ejemplo de visualización de SPI](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | SN74HC595N Mayús registrar IC | ARM32, x64, x86 | REGISTRO DE DESPLAZAMIENTO DE 8 BITS IC 16-DIP | [Ejemplo de registro de desplazamiento](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | MicroMCP3002 de ADC de tecnología de microchip-I/P | AARM32, x64, x86 | MCP3002 10 bits analógico al convertidor digital. |  [Ejemplo de sensor potenciómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | MicroMCP3208 de ADC de tecnología de microchip-CI/P | ARM32, x64, x86 | MCP3208 12bit analógico al convertidor digital. | [Ejemplo de sensor potenciómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM, x32, x64, x86 | ADC de 16 bits, ultra pequeño, de baja energía | [Proveedores de bus de ADC](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | Convertidor en serie del módulo CP2102 USB 2,0 a TTL | ARM32, x64, x86 | Convertidor en serie del módulo CP2102 USB 2,0 a TTL | [Ejemplo de puerto serie](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32, x64, x86 | controlador LED de bus de 16 bits de PWM FM + de 16 canales. | [Proveedores de bus de PWM](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


