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
# <a name="troubleshooting"></a>Solución de problemas
Se trata de un artículo que contiene los problemas más comunes que las personas han llegado a través. Para buscar un elemento específico, use Ctrl + F para buscar una palabra o frase. ¿Tendría ninguna idea de que desea agregar? Crear una solicitud para esta documentación o previsión comentarios sobre el contenido siguiente.

> [!TIP]
> Para solucionar problemas relacionados con la fabricación, lea el [documento de solución de problemas](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/troubleshooting) en nuestra guía de fabricación.

## <a name="asus-tinkerboard-and-rockchip-support"></a>Compatibilidad con ASUS Tinkerboard y Rockchip

Aunque el ASUS Tinkerboard y Rockchip no se admiten oficialmente por nuestra parte, hay casos donde Rockchip ha trabajado con terceras partes obtener SoC trabajando en Windows 10 IoT Core.

## <a name="issue-when-connecting-a-mbm-device-when-roaming"></a>Problema al conectar un dispositivo MBM itinerancia

Hay dos cosas a tener en cuenta al habilitar la itinerancia:

1. El profile.xml configura itinerancia y establece el comportamiento para establecer automáticamente una conexión a la red de telefonía móvil.
Para establecer un perfil para móviles, consulte [en este artículo](https://docs.microsoft.com/windows/desktop/mbn/schema-root).

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

2. Otro factor es que debe cumplirse la directiva de movilidad por interfaz. De forma predeterminada, esa directiva se establece en FALSE ("home transportista solo"). Esto se puede consultar y cambiar en la línea de comandos a través de `netsh mbn get/set dataroamcontrol.`

Por ejemplo:

```
    netsh mbn show dataroamcontrol int=*
    netsh mbn set dataroamcontrol interface=Cellular profileset=all state=all
    netsh mbn set dataroamcontrol help
```

Puede obtener error **0x139f (ERROR_INVALID_STATE)** en el caso cuando el dispositivo está en itinerancia, pero la directiva de movilidad no permite la itinerancia de datos - error en una solicitud de conexión enviado a wwansvc.

## <a name="raspberry-pi-3b-booting-issues"></a>Raspberry Pi 3B + arranque problemas

> [!NOTE]
> Esta versión para el dispositivo Raspberry Pi 3B + es una versión preliminar técnica no admitida. Se ha completado la habilitación y la validación limitada. Para obtener una mejor evaluación experimentar y para los productos comerciales, use el 3B Raspberry Pi u otros dispositivos con Intel, Qualcomm o NXP Qualcomm admitidos. Para solucionar problemas relacionados con el dispositivo Raspberry Pi 3B +, consulte nuestra guía de solución de problemas, [aquí](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting?branch=master#raspberry-pi-3b-booting-issues). 

El dispositivo Raspberry Pi 3 modelo B + es el producto más reciente en el intervalo de Raspberry Pi 3, haciendo alarde de un procesador quad core de 64 bits a 1,4 GHz, doble banda 2,4 GHz y 5 GHz redes LAN inalámbricas, Ethernet 4.2/BLE, más rápido de Bluetooth y PoE capacidad a través de una independiente PoE alta disponibilidad.

Recientemente, muchos clientes que están interesados en Windows 10 IoT Core encontró un problema donde el dispositivo no pudo iniciar normalmente después de vaciar Windows 10 IoT Core, pero la Raspbian funciona bien en él. Las siguientes son algunas sugerencias sobre cómo solucionar el problema de inicio.

Hay algunos problemas conocidos en esta imagen de vista previa de Insider. Tenga en cuenta:
* Esta imagen solo está pensada para el dispositivo Raspberry Pi 3B + y no se iniciará en el Pi Raspbierry 2.
* Implementación de controladores de F5 desde Visual Studio no funciona en Windows 10 IoT Core.
* Incorporación de Wi-Fi y Bluetooth no funcionan en el Raspberry Pi 3B +.
* Controlador de pantalla táctil Ft5406 está deshabilitado en el Raspberry Pi 3B +.
* Está deshabilitado el LED de actividad de tarjeta SD.

Hay solo dos requisitos al elegir qué tarjetas SD para usar con Windows 10 IoT Core. Deberá usar una tarjeta SD de clase 10 y asegúrese de que la tarjeta tiene suficiente espacio - al menos 8 GB de espacio. Hay un par de tarjetas SD que se han comprobado por Microsoft para que sean compatibles con Windows 10 IoT Core:
* Tarjeta de SDHC con Micros clase 10 Samsung EVO 32 GB
* SanDisk Ultra Micro SDHC con, tarjeta de 16 GB

Por lo general, deberá comprobar si la tarjeta SD es falsa, o si está dañado. La tarjeta SD es igualmente proclives a daños debido a una variedad de factores como la escasez de energía o eliminación incorrecta. Es importante proteger su tarjeta de memoria de daños.

Para actualizar la imagen en una tarjeta SD, puede usar el [panel de Windows 10 IoT Core](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard). Deberá elegir "Custom" en el campo de la compilación del sistema operativo y luego seleccione el archivo FFU a flash. 

Compruebe si hay cualquier error de hardware en el dispositivo. Hay dos LED en la placa de Raspberry Pi 3B + igual que el 3B. Uno es potencia mientras hay otra para ACT. El número de parpadeos hace que la ley de luz determinará si se está iniciando la placa. El LED de actividad de tarjeta SD no parpadeará durante algunas partes de arranque en el Raspberry Pi 3B +.

Cuando se arranca el dispositivo y el dispositivo muestra la página de espera, espere pacientemente. Por lo general, esto estará en vigor hasta un minuto. Pero en ocasiones, debido a la velocidad de lectura y escritura de tarjeta SD, es posible que tarde más tiempo.

Si el dispositivo no puede arrancar normalmente con Windows 10 IoT Core, puede intentar flash un sistema operativo Linux (por ejemplo, Raspbian) en la tarjeta SD para concretar si el problema está causado por hardware. 

Si encuentra que está obteniendo una "pantalla de arco iris", compruebe para asegurarse de que se vacían la 3B + versión de lanzamiento, disponible [aquí](https://www.microsoft.com/en-us/software-download/windowsiot). Puede comprobar el proceso con un 3B Comunidad + parpadeando tutorial [aquí](https://www.hackster.io/JiongShi/windows-10-iot-core-for-raspberry-pi-3-model-b-92b1a3).

## <a name="serial-port-communication-on-windows-10-iot-core-for-raspberry-pi"></a>Comunicación de puerto serie en Windows 10 IoT Core para Raspberry Pi 

En el dispositivo Raspberry Pi, hardware UART USB UART adaptadores y ambos son utilizables para su aplicación con la comunicación serie. Forma predeterminada, la transmisión UART y recibir los PIN son los pines 8 y 10 en el encabezado GPIO.

![UART y USB UART adaptadores](media/Troubleshooting/adapters.png)

Puede leer [en este artículo](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/pinmappings/pinmappingsrpi#serial-uart) para obtener más información sobre cómo inicializar UART0 y realizar una operación de escritura seguido de una lectura.

Además, la comunicación por radiofrecuencia (RFCOMM) es las comunicaciones en serie subyacentes Bluetooth clásico. Consulte [en este ejemplo de GitHub](https://github.com/djaus2/iotbluetoothserial) para obtener información sobre cómo ejecutar las aplicaciones para UWP en Windows 10 IoT Core a conectado a través de un dispositivo de IoT con el número de serie de Bluetooth.

Si encuentra que el dispositivo no puede leer o escribir datos a través del puerto serie, siga estos pasos para solucionar problemas:

1. Conectar TX RX con puentes - se muestra a continuación: después de ejecutar el código de ejemplo para comprobar si la aplicación puede leer o escribir datos. Si esto no funciona, el IC en el panel pueden dejar de funcionar.

![TX a RX en Raspberry Pi](media/Troubleshooting/txrx.png)

2. Asegúrese de que la velocidad en baudios, el protocolo de enlace y StopBits están configurados correctamente. Si el puerto serie que va a probarse tiene una interfaz RS232 completa (por ejemplo, DB9), use un enchufe de la base de datos con los cables de entrecruzamiento RxTx conectados con los crossovers típico de protocolo de enlace. Algunos puertos RS232 (o adaptadores USB) requieren las señales, como portadora detectar (DCD) y DCE preparado (DSR) imponerse antes de que funcionen correctamente.

3. Si desea usar adaptadores USB UART en Windows 10 IoT Core, se admite lo siguiente:

* CP2102 USB 2.0
* Convertidor serie del módulo TTL
* FTDI
* Usbser.sys genérico

También puede usar la pila devcon.exe * y devcon.exe estado * cmdlet para comprobar la pila de controladores esperado y el estado de los controladores en Windows 10 IoT Core.

```
USB\VID_10C4&PID_EA60\0001
    Name: Silicon Labs CP210x USB to UART Bridge
    Setup Class: {4d36e978-e325-11ce-bfc1-08002be10318} Ports
    Controlling service:
        silabser
```
[Mincomm](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools/MinComm) es otra herramienta útil para solucionar problemas de puerto serie. Esta herramienta puede enumerar los puertos, proporcionarle su nombre descriptivo y el Id. de dispositivo, abra los puertos, configuración (es decir, velocidad en baudios, bits de parada, etc.) y enviar y recibir datos. 

## <a name="sirep-test-service"></a>Servicio de prueba Sirep
Aunque el servicio de prueba Sirep no está habilitado de forma predeterminada en las imágenes de venta directa, en caso de que desea deshabilitar el servicio Sirep en Inicio, puede iniciar sesión y deshabilitar Sirep de inicio automático. 

Puede usar los siguientes comandos de PowerShell para hacerlo, como se muestra a continuación:

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

"Modo de Tablet PC" es un concepto que solo existen en el shell de escritorio y no se aplica a IoT Core. 

Si el dispositivo tiene hardware (ya sea a través de I2C o USB HID touch) compatible, toque debería funcionar automáticamente con los controladores de clase de la Bandeja de entrada. Puede leer más sobre esto [aquí](https://docs.microsoft.com/en-us/windows-hardware/design/component-guidelines/touchscreen-device-bus-connectivity).


## <a name="yubikey-support"></a>Compatibilidad con Yubikey

Windows 10 IoT Core no tiene compatibilidad con tarjetas inteligentes. Sin embargo, las tarjetas inteligentes suelen ser dispositivos usados para la identidad del usuario y la identidad del dispositivo no porque están protegidas con clavijas y, en el caso de lo Yubikey, presione un botón. Esto no armonizar con un dispositivo de IoT. Si está buscando una alternativa, un TPM 2.0 en el dispositivo puede servir mejor que un Yubikey o una tarjeta inteligente. Contamos con compatibilidad de certificados completa para TPM y están diseñadas para almacenar los dispositivos, así como los certificados de usuario y credenciales de acceso de Azure IoT (Limpets).
