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
# <a name="troubleshooting"></a>Solución de problemas
Se trata de un artículo que contiene los problemas más comunes que se han encontrado los usuarios. Para encontrar un elemento específico, presione Ctrl+F para buscar una palabra o frase. ¿Tiene alguna idea que quiera agregar? Cree una solicitud de incorporación de cambios para esta documentación o proporcione comentarios sobre el contenido a continuación.

> [!TIP]
> Para solucionar problemas relacionados con la fabricación, lea el [documento sobre solución de problemas](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) de nuestra guía de fabricación.

## <a name="asus-tinkerboard-and-rockchip-support"></a>Compatibilidad con ASUS Tinkerboard y Rockchip

Aunque no admitamos ASUS Tinkerboard y Rockchip de forma oficial, hay casos en los que Rockchip ha colaborado con terceras partes para conseguir que SoC funcionara en Windows 10 IoT Core.

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a>Problema al conectar un dispositivo MBM en itinerancia

Hay dos aspecto que tener en cuenta al habilitar la itinerancia:

1. profile.xml configura la itinerancia y define el comportamiento para establecer de forma automática una conexión a la red de telefonía móvil.
Para establecer un perfil para móviles, consulte [este artículo](https://docs.microsoft.com/windows/desktop/mbn/schema-root).

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

Para establecer un perfil de conexión automática, seleccione "auto":

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

2. Otro factor es que se debe cumplir la directiva de itinerancia por cada interfaz. De forma predeterminada, esa directiva se establece en FALSE ("solo operador local"). Esto se puede consultar y cambiar en la línea de comandos a través de `netsh mbn get/set dataroamcontrol.`

Por ejemplo:

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

Puede obtener el error **0x139f (ERROR_INVALID_STATE)** cuando el dispositivo está en itinerancia pero la directiva de itinerancia no permite la itinerancia de datos; error en una solicitud de conexión enviada a wwansvc.

## <a name="raspberry-pi-3b-booting-issues"></a>Problemas de arranque de Raspberry Pi 3B+

> [!NOTE]
> Esta versión para Raspberry Pi 3B+ es una versión preliminar técnica no admitida. Se ha completado la habilitación y la validación limitadas. Para obtener una mejor experiencia de evaluación y para cualquier producto comercial, use Raspberry Pi 3B u otros dispositivos con SoC de Intel, Qualcomm o NXP admitidos. Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B+, vea nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues). 

El dispositivo Raspberry Pi 3 modelo B+ es el producto más reciente de la gama Raspberry Pi 3, con un procesador de cuatro núcleos de 64 bits a 1,4 GHz, LAN inalámbrica de banda dual a 2,4 GHz y 5 GHz, Bluetooth 4.2/BLE, Ethernet más rápido y funciones PoE a través de alta disponibilidad de PoE independiente.

Recientemente, muchos clientes interesados en Windows 10 IoT Core han encontrado un problema que hacía que el dispositivo no se pudiera iniciar con normalidad después de instalar la imagen de Windows 10 IoT Core, pero el dispositivo Raspbian funciona bien en él. A continuación se indican algunas sugerencias sobre cómo solucionar el problema de inicio.

Hay algunos problemas conocidos en esta imagen de Insider Preview. Tenga en cuenta que:
* Esta imagen solo está pensada para el dispositivo Raspberry Pi 3B+ y no arrancará en Raspberry Pi 2.
* La implementación de controlador F5 desde Visual Studio no funciona en Windows 10 IoT Core.
* Wi-Fi y Bluetooth en la placa no funcionan en el dispositivo Raspberry Pi 3B+.
* El controlador de pantalla táctil Ft5406 está deshabilitado en Raspberry Pi 3B+.
* El LED de actividad de tarjeta SD está deshabilitado.

Solo hay dos requisitos al elegir las tarjetas SD que se van a usar con Windows 10 IoT Core. Tendrá que usar una tarjeta SD de clase 10 y asegurarse de que tenga espacio suficiente, al menos 8 GB. Microsoft ha comprobado la compatibilidad de un par de tarjetas SD con Windows 10 IoT Core:
* Tarjeta Micros SDHC de clase 10 Samsung EVO de 32 GB
* SanDisk Ultra Micro SDHC, de 16 GB

Por lo general, tendrá que comprobar si la tarjeta SD es falsa o si está dañada. Igualmente la tarjeta SD puede sufrir daños debido a diversos factores, como la escasez de alimentación o una extracción incorrecta. Es importante proteger la tarjeta de memoria de posibles daños.

Para instalar la imagen en una tarjeta SD, puede usar el [Panel de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard). Tendrá que elegir "Personalizada" en el campo de la compilación del sistema operativo y luego seleccionar el archivo FFU para instalar. 

Compruebe si hay algún error de hardware en el dispositivo. Hay dos LED en la placa Raspberry Pi 3B+, como en el modelo 3B. Uno es para PWR y el otro para ACT. El número de parpadeos que emite la luz ACT determinará si la placa arranca o no. En el modelo Raspberry Pi 3B+, el LED de actividad de la tarjeta SD no parpadeará durante algunas fases del arranque.

Cuando el dispositivo está arrancando y muestra la página de espera, espere pacientemente. Por lo general, esto suele durar hasta un minuto. Pero en ocasiones, debido a la velocidad de lectura y escritura de la tarjeta SD, es posible que tarde más tiempo.

Si el dispositivo no puede arrancar normalmente con Windows 10 IoT Core, puede intentar instalar un sistema operativo Linux (como Raspbian) en la tarjeta SD para concretar si el problema se debe al hardware. 

Si recibe una "pantalla arco iris", asegúrese de que ha instalado la versión de lanzamiento 3B+, disponible [aquí](https://www.microsoft.com/en-us/software-download/windowsiot). [Aquí](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3) puede comprobar el proceso con un tutorial sobre instalación de imágenes de 3B+ enviado por la comunidad.

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a>Comunicación de puerto serie en Windows 10 IoT Core para Raspberry Pi 

En el dispositivo Raspberry Pi, la aplicación puede usar los adaptadores hardware UART y UART USB con la comunicación de serie. De forma predeterminada, los pines de transmisión y recepción de UART en el adaptador GPIO son el 8 y el 10.

![Adaptadores UART y UART USB](media/Troubleshooting/adapters.png)

Puede leer [este artículo](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) para obtener más información sobre cómo inicializar UART0 y realizar una operación de escritura seguida de una de lectura.

Además, la comunicación por radiofrecuencia (RFCOMM) es la comunicación de serie subyacente para Bluetooth clásico. Consulte [este ejemplo de GitHub](https://github.com/djaus2/iotbluetoothserial) para obtener información sobre la ejecución de aplicaciones para UWP en Windows 10 IoT Core conectadas a través de un dispositivo de IoT con Bluetooth de serie.

Si comprueba que el dispositivo no puede leer o escribir datos a través del puerto serie, siga estos pasos para solucionar problemas:

1. Conecte la transmisión (TX) a la recepción (RX) mediante el puente (mostrado a continuación) y después ejecute el código de ejemplo para comprobar si la aplicación puede leer o escribir datos. Si esto no funciona, es posible que el circuito integrado de la placa esté dañado.

![TX a RX en Raspberry Pi](media/Troubleshooting/txrx.png)

2. Asegúrese de que la velocidad en baudios, el enlace y los bits de parada están configurados correctamente. Si el puerto serie que se va a probar tiene una interfaz RS232 completa (por ejemplo, DB9), use un conector DB con los cables cruzados RxTx conectados con los cables cruzados de enlace típicos. Algunos puertos RS232 (o adaptadores USB) requieren que se confirmen señales como las de detección de operador (DCD) y DCE listo (DSR) antes de funcionar correctamente.

3. Si quiere usar adaptadores UART USB en Windows 10 IoT Core, se admiten los siguientes:

* CP2102 USB 2.0
* Convertidor serie del módulo TTL
* FTDI
* usbser.sys genérico

También puede usar la pila devcon.exe * y el cmdlet devcon.exe status* para comprobar la pila de controladores esperada y el estado de los controladores en Windows 10 IoT Core.

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) es otra herramienta útil para solucionar problemas de puerto serie. Esta herramienta puede enumerar puertos, proporcionar sus nombres descriptivos y los identificadores de dispositivo, abrir puertos, configurar ajustes (como la velocidad en baudios, los bits de parada, etc.) y enviar y recibir datos. 

## <a name="sirep-test-service"></a>Servicio de prueba Sirep
Aunque el servicio de prueba Sirep no está habilitado de manera predeterminada en las imágenes comerciales, si todavía quiere deshabilitarlo al inicio, puede iniciar sesión y deshabilitar el inicio automático de Sirep. 

Puede usar los comandos de PowerShell siguientes para hacerlo, como se muestra a continuación:

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

## <a name="tablet-mode"></a>Modo tableta

El "modo tableta" es un concepto que solo existe en el shell de Desktop y no se aplica a IoT Core. 

Si el dispositivo tiene hardware compatible (ya sea a través de I2C o USB HID Touch), la función táctil debería funcionar de forma automática con los controladores de clase de bandeja de entrada. Puedes leer más sobre esto [aquí](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).


## <a name="yubikey-support"></a>Compatibilidad con Yubikey

Windows 10 IoT Core no es compatible con tarjetas inteligentes. Pero las tarjetas inteligentes suelen ser dispositivos que se usan para la identidad del usuario y no la del dispositivo, ya que están protegidas mediante PIN y, en el caso de Yubikey, un botón que hay que presionar. Esto no concuerda con un dispositivo IoT. Si busca una alternativa, un TPM 2.0 en el dispositivo puede ser más indicado que Yubikey o una tarjeta inteligente. Contamos con soporte para certificados completo para TPM y están diseñados para almacenar dispositivos, así como certificados de usuario y credenciales de acceso de Azure IoT (Limpets).
