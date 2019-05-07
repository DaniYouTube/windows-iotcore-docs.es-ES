---
title: Lista de compatibilidad de hardware
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre las interfaces periféricas y los protocolos que admite Windows 10 IoT Core mejor.
keywords: Windows iot, periféricos, protocolos, compatibilidad, buses, hardware
ms.openlocfilehash: 54ca0f706033a8a3eef0704534805d0d6b379083
ms.sourcegitcommit: 77caab0cfa47c74c66777c3cf5eeaa0ec9ac5784
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/01/2019
ms.locfileid: "64981936"
---
# <a name="hardware-compatibility-list"></a>Lista de compatibilidad de hardware

Windows 10 IoT Core es compatible con una variedad de interfaces de periféricos y protocolos, incluida la compatibilidad con buses comunes como I2C, UART, USB y mucho más. Esta página enumera los periféricos compatibles conocidos y es actual a partir de la última versión RTM. Entradas específicas pueden no funcionan en las versiones Insider y se anotará como tal. Animamos a colaborar en esta lista en GitHub.

> [!IMPORTANT]
> Esta lista no es exhaustiva. Hay muchos otros dispositivos periféricos no aparece en esta página que son compatibles con Windows 10 IoT Core. Si un dispositivo que no ve muestran, pero es compatible para la clase con lo que ya se admite en Windows 10 IoT Core, a continuación, funcionará. 


¿Busca información sobre las plataformas de hardware compatible? Haga clic en [aquí](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards) para obtener una lista de placas de desarrollo compatibles con Windows.

## <a name="usb-devices"></a>Dispositivos USB

### <a name="wifi-adapters"></a>Adaptadores de red Wi-Fi
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | Oficial llave Wi-Fi de Raspberry Pi | ARM32, x64, x86 | El adaptador Wi-Fi de Raspberry Pi oficial ofrece el mejor rendimiento posible de Wi-Fi para su tamaño diminuto. | | &#10004;  |
> | Adaptador USB Mini 150 Airlink Wireless N | x64, x86 | Airlink 101 AWL5077 Golden adaptador USB de Mini inalámbrica de 150 Mbps con WEP, WPA y WPA2 ha mejorado la seguridad inalámbrica | | &#10004;  
> | Panda PAU06 | x64, x86 |  Adaptador de USB N inalámbrica Panda 300 Mbps con antena ganancia alta | |  &#10004;  
> | TP-LINK TL_WN725N |  ARM32, x64, x86 | VÍNCULO de TP TL WN725N Wireless N Nano USB adaptador 150 Mbps `(USB/VID_0BDA&PID_8179)` |  | &#10004;  
> | Adaptador USB de DYN de la red Wi-Fi | MBM | Adaptador de USB de Wi-Fi NET-DYN | |  &#10004;  
> | Wi-Fi de Realtek 8191 USB inalámbrico | ARM32, x64, x86 | Adaptador tarjeta de red LAN inalámbrica Wi-Fi de Realtek 8191 300 Mbps 802.11n/g/b/ USB | | &#10004;  
> | Wi-Fi de Realtek 8192 USB inalámbrico | ARM32, x64, x86 | Interfaz de controlador WLAN 2T2R con USB 2.0 802.11b/g/n Realtek único Chip IEEE | | &#10004; |
> | Realtek 8188EU USB inalámbrica Wi-Fi | ARM32, Mx64, x86BM | Adaptador de red 2.0 de Realtek RTL8188EU LAN inalámbrica 802.11n/g/b USB | | &#10004; |
> | Realtek 8192EU USB inalámbrica Wi-Fi | ARM32, x64, x86 | Adaptador de red 2.0 de Realtek RTL8192EU LAN inalámbrica 802.11n/g/b USB | | &#10004; |
> | WiFi inalámbrica USB CanaKit | x64, x86 | Conjunto de chips Ralink 5370 | | &#10004;
> | Vínculo de D DWA-172 | ARM32 | Adaptador USB de gran aumento de banda Dual AC600 inalámbrica | [Hoja de datos](ftp://ftp.dlink.de/dwa/dwa-172/documentation/DWA-172_ds_en_Datasheet.pdf) |

### <a name="ethernet-adapters"></a>Adaptadores Ethernet
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|---------------|------------------------------|
> | Adaptador ASIX AX88772 USB 2.0 Fast Ethernet | ARM32, x64, x86 | Se trata de un alto rendimiento y alta integrado ASIC con 28 KB incrustado SRAM paquete el almacenamiento en búfer.  | | &#10004;  |


### <a name="bluetooth-dongles"></a>Llaves de Bluetooth
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Adaptador Bluetooth V 4.0 de CSR USB Mini | ARM32, x64, x86 | Clase 2 Bluetooth 4.0 de adaptador lista inteligente, baja energía, alimentación doble |  | &#10004; 
> | Adaptador USB ORICO BTA 403 Mini Bluetooth 4.0 | ARM32, x64, x86 | Adaptador Bluetooth 4.0 de baja energía llave de adaptador de USB Micro |  | &#10004; 
> | Adaptador Bluetooth V 4.0 de CSR USB Mini | x64, x86 | Clase 2 Bluetooth 4.0 de adaptador lista inteligente, baja energía, alimentación doble |  | &#10004;|

### <a name="cameras"></a>Cámaras
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Cámara USB de cámara Microsoft 3000 | ARM32, x64, x86 | Cámara Web USB | [Proyecto de cámaras de seguridad principal](https://developer.microsoft.com/en-us/windows/iot/samples/webcamapp)|&#10004;|
> | Microsoft Lifecam HD-5000 | ARM32, x64, x86 | Cámara Web HD de 5000 de HD 720p de cámara de Microsoft | | &#10004; |
> | Microsoft® LifeCam Studio™ | ARM32 | Microsoft® cámara Studio™ (modelo: Webcam de HD 1080p 1425) | | |
> | Logitech Webcam C210 | ARM32, x64, x86 | Cámara Web USB, 1,3 MP foto |  |&#10004; |

### <a name="audio"></a>Audio
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Adaptador de sonido estéreo de sabrent USB externo, modelo AU-EMAC1 | ARM32, x64, x86 | Convierte las señales de audio y micrófono de 3,5 mm USB | | &#10004; 

### <a name="miscellaneous"></a>Varios
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Aeon Labs Z-Wave Z Stick serie 2 USB llave DSA02203-ZWUS | ARM32 | Controlador de Z-Stick USB de serie 2 Z-Wave |  | &#10004; |
> | [Pizarra electrónica 7" LCD capacitativa pantalla táctil](https://www.chalk-elec.com/?page_id=1280#!/7-black-frame-universal-HDMI-LCD-with-capacitive-multi-touch/p/21750201/category=3094861) | ARM32 | | [Actualización del firmware](https://www.chalk-elec.com/?p=1826) | &#10004; |
> | Vodafone (Huawei) K5150 | ARM32, x64, x86 | Vodafone (Huawei) K5150 150 Mbps 4G LTE FDD USB móvil módem de banda ancha |  | &#10004;  |
> | Vodafone (Huawei) K5160 | ARM32, x64, x86 | Vodafone (Huawei) K5160 150 Mbps GSM/EDGE / 3G/HSPA c++ / módem de banda ancha móvil LTE CAT4 USB |  | |
> | Sierra inalámbrica carretera (AirCard 340U) | x64, x86 |    Sierra carretera inalámbrica (AirCard 340U) 4G LTE USB móvil módem de banda ancha |  |&#10004; |
> | Controlador de Microsoft Xbox 360 | ARM32 | Un controlador para juegos USB HID compatible para Microsoft Xbox 360 | [Kit robótico](https://microsoft.hackster.io/en-US/windowsiot/robot-kit-6dd474) |  &#10004; |
> | [MyTeletouch](http://www.myteletouch.com/) | ARM, x32 | Un mouse inalámbrico USB HID conforme, el teclado y el controlador para juegos |  | &#10004; |

## <a name="other-hardware-peripherals"></a>Otros dispositivos periféricos de Hardware

### <a name="nfcrfidproximity"></a>NFC/RFID/proximidad
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified |
> |----------------|-------------------|-------------|--------|------------------------------|
> | Panel de demostración NXP OM5577 | ARM32 | Placa de demostración para el chip NXP PN7120 NFC. | [Documentación de ProximityDevice](https://docs.microsoft.com/uwp/api/Windows.Networking.Proximity.ProximityDevice) | &#10004; |
> | NXP PN547/PN548/PN7120 | ARM32, x64, x86 | Admite los chips NXP NFC. | | &#10004; |

### <a name="pi-hats"></a>Sombreros PI
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Adafruit 16 canales PWM](https://www.adafruit.com/product/2327#description-anchor) | ARM32 | Agrega la capacidad para controlar un máximo de 16 servodirecciones sin ninguna sobrecarga adicional de procesamiento de Raspberry Pi. Capaz de hacer PWM con una precisión de 12 bits hasta 1,6 KHz. | [Tutorial de Adafruit C# ejemplo de IoT](https://github.com/golaat/Adafruit.Pwm) | |
> | [Dexter Industries GrovePi](https://www.dexterindustries.com/shop/grovepi-board/) | ARM32 | Puede conectarse a cientos de diferentes sensores sin soldadura, por lo que se puede programar para supervisar, control y automatizar los dispositivos de su vida. | [Ejemplos de GrovePi](https://github.com/DexterInd/GrovePi/) | |
> | Dexter Industries GoPiGo | ARM, x32 | El GoPiGo es un robot agradable y completado para Raspberry Pi que Pi se convierte en un robot completamente operativo. GoPiGo es una plataforma robótica móvil para Raspberry Pi desarrollado por Dexter sectores. | [Ejemplos de GoPiGo](https://github.com/DexterInd/GoPiGo/tree/master/Software/CSharp) | |

### <a name="port-expanders"></a>Ampliadores de puertos
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Botón de expansión de puerto de E/S de 8 bits MCP23008 | ARM32, x64, x86 | Chip de interfaz i2c, puerto GPIO expansor. 8 puertos, el paquete de 18 PDIP | [Ejemplo de puerto SPI Explander](https://www.hackster.io/4803/i2c-port-expander-sample-0a6d4f) | &#10004; |
> | Botón de expansión de puerto de E/S de 16 bits MCP23S17 | ARM32, x64, x86 | Chip de interfaz i2c, puerto GPIO expansor. paquete de 28 SPDIP de 16 puertos | [Ejemplo de Piano interactivo](https://www.hackster.io/windowsiot/build-2014-piano-3b449c) | &#10004; |

### <a name="storage-media"></a>Medios de almacenamiento
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | [Samsung 32GB EVO Class 10 Micro SDHC](https://www.amazon.com/gp/product/B00IVPU786) | AARM32, x64, x86 | Una tarjeta SD recomendada para los dispositivos que pueden tener Windows 10 IoT Core se vacían. | | &#10004;|
> | [SanDisk Ultra Micro SDHC 16GB](https://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445) | ARM32, x64, x86 | Una tarjeta SD recomendada para los dispositivos que pueden tener Windows 10 IoT Core se vacían. | | &#10004; |

### <a name="sensors"></a>Sensores
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified  | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Sensor de temperatura y humedad básica DHT11 | ARM32, x64, x86 | Un básico, ultra bajo costo temperatura y humedad sensor digital. Se usa un sensor de humedad de las capacidades y un termistor para medir el aire circundante y arroja una señal digital en el pin de datos (no es necesitados ningún PIN entrados analógicos).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire)| &#10004; |
> | Sensor de humedad y temperatura DHT22 | ARM32, x64, x86 | Un básico, ultra bajo costo temperatura y humedad sensor digital. Se usa un sensor de humedad de las capacidades y un termistor para medir el aire circundante y arroja una señal digital en el pin de datos (no es necesitados ningún PIN entrados analógicos).  | [GpioOneWireSample (DHT11)](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/GpioOneWire) | &#10004; |
> | Desglose de acelerómetro de eje SparkFun Triple - ADXL345 | ARM32, x64, x86 | Pequeño, ligero, de baja potencia, 3 ejes acelerómetro MEMS con mediciones de alta resolución (13 bits) con hasta ±16 g. Datos de salida digital con el formato de complemento a dos de 16 bits y son accesibles a través de una interfaz digital I2C o SPI (3 o 4 cables). |[Ejemplo de acelerómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer) | &#10004; |
> | Sensor barométrica y temperatura Adafruit BMP280 | ARM32 | Sensor de medioambientales Bosch con la temperatura, presión barométrica | |   &#10004; |
> | [Sensor de Adafruit TCS34725 de Color](http://www.adafruit.com/products/1334) | ARM, x32 | Sensor de Color RGB con filtro IR y LED blanco - TCS34725 | | &#10004; |
> | Sensor de luz ambiente ROHM BH1750FVI | ARM32 | Sensor de I2C pequeño para la medición de luz ambiente | [Ejemplos de i2c](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Sensor barométrica y temperatura Bosch BMP180 | ARM, x32 | Sensor de medioambientales Bosch con tempreature, presión barométrica | [Ejemplos de i2c](https://github.com/mickut/Win10-IoT-Sensors) | |
> | Sensor de humedad relativa Dorji DSTH01 | ARM32 | Sensor de humedad relativa i2c | [Ejemplos de i2c](https://github.com/mickut/Win10-IoT-Sensors)| |
> | Honeywell HMC5883L brújula 3 ejes digital/magnetómetro | ARM32 | Un pequeño magnetómetro 3 ejes de mediciones de uso y el campo magnético brújula digitales | [Ejemplos de i2c](https://github.com/mickut/Win10-IoT-Sensors) | |

### <a name="touchpanel-solutions"></a>Soluciones TouchPanel
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Keith & Koep CoverLens de M7 i-panorámica | ARM32 | 7.0 pulgadas equipo Touchpanel para su uso industrial con CPU de Qualcomm Snapdragon 410E, resolución 800x480px, brillo 850cd/qm, USB 2.0, tarjeta SD, POE | [información de i-panorámica M7](https://keith-koep.com/en/products/products-hmi/i-pan-m7-coverlens-arm-touch-panel-computer-technical-data/) | &#10004; |

### <a name="miscellaneous"></a>Varios
> | Nombre de elemento o no. | Arquitectura compatible | Descripción | Vínculos relevantes | Microsoft Verified | 
> |----------------|-------------------|-------------|--------|------------------------------|
> | Mostrar oficial de Pi | ARM32 | 800 x 480 de 7" tocar la pantalla. | [Pantalla táctil de raspberry Pi 7"](https://www.raspberrypi.org/products/raspberry-pi-touch-display/) | &#10004; |
> | Presentación gráfica OLED de monocromático de 1,3" 128 x 64 |ARM, x32, x64, x86 | 1,3" diagonal, de alto contraste para mostrar en blanco y negro OLED. 128 x 64 blanco OLED píxeles individuales, cada uno de ellos es activar o desactivar por el chip del controlador. | [Ejemplo de presentación SPI](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SPIDisplay) | &#10004; |
> | Registro de desplazamiento SN74HC595N IC | ARM32, x64, x86 | REGISTRO DE DESPLAZAMIENTO DE 8 BITS DE IC 16 DIP | [Ejemplo de registro de desplazamiento](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/ShiftRegister) | &#10004; |
> | Microchip tecnología ADC MCP3002-/ P | AARM32, x64, x86 | MCP3002 10 bits analógico al convertidor Digital. |  [Ejemplo de Sensor potenciómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | Tecnología microchip ADC MCP3208-CI/P | ARM32, x64, x86 | MCP3208 12 bits analógico al convertidor Digital. | [Ejemplo de Sensor potenciómetro](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/PotentiometerSensor) | &#10004; |
> | ADS1115 | ARM, x32, x64, x86 | ADC extremadamente pequeño, de bajo consumo de energía, 16 bits | [Proveedores de Bus de ADC](https://github.com/ms-iot/BusProviders/tree/develop/ADC) | &#10004; |
> | CP2102 Convertidor de USB 2.0 a TTL módulo serie | ARM32, x64, x86 | CP2102 Convertidor de USB 2.0 a TTL módulo serie | [Ejemplo de puertos serie](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/SerialUART) | &#10004; |
> | PCA9685 | ARM32, x64, x86 | controlador de bus I2C Fm + PWM LED 16 canales, 12 bits. | [Proveedores de Bus PWM](https://github.com/ms-iot/BusProviders/tree/develop/PWM) | &#10004; |


