---
title: Creación de dispositivos segura con Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo crear dispositivos seguros al habilitar el arranque seguro, la implementación de TPM y mucho más.
keywords: Windows iot, seguridad, firmware, el arranque seguro, TPM, Bitlocker, cifrado
ms.openlocfilehash: e9d9bc476455bfbd653a7923c729880dbfad0891
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515108"
---
# <a name="building-secure-devices-with-windows-10-iot-core"></a>Creación de dispositivos segura con Windows 10 IoT Core

## <a name="introduction"></a>Introducción  
Con la introducción de Windows 10 IoT Core, Microsoft ofrece enterprise seguro las características de seguridad de nivel que se pueden aprovechar en las clases de restricción de recursos más pequeñas, de dispositivos IoT.  Para estas características de seguridad ofrecer beneficios tangibles, la plataforma de hardware debe proporcionar también un medio para fijarlos. Este documento proporciona orientación a los generadores de dispositivo de OEM y la seguridad de alto nivel conscientes 'creadores' que desean seleccionar el hardware apropiado y generar, configurar y enviar un dispositivo de IoT seguro a sus clientes. 

## <a name="firmware"></a>Firmware  
En dispositivos que están "abiertos", por ejemplo, los equipos informáticos de uso general, los usuarios tener acceso a configuración de firmware durante el arranque del dispositivo a través de diversas combinaciones de teclas (p. ej., F2 entra en el programa de instalación UEFI en la mayoría de los equipos hoy en día). Esto puede permitir que los usuarios realicen cambios en la forma en que la plataforma arranca, así como habilitar y deshabilitar los distintos puertos de dispositivo, funciones y otras características de seguridad potenciales disponibles en el dispositivo.  

Dada la naturaleza confidencial de estas modificaciones, IoT, los dispositivos no deben funcionar como "Abra dispositivos" y debería funcionar más como dispositivos "bloqueada", similar a los teléfonos móviles, donde firmware es por lo general no permite el acceso a.  Normalmente esto se consigue asegurándose de que utilizas firmware bloqueado en el dispositivo de producción. Bloqueado firmware debe estar disponible a través del proveedor de firmware.  Como mínimo, en los dispositivos donde bloqueado firmware no está disponible o potencialmente no son adecuados, como para su uso por los creadores, considere la posibilidad de proteger el acceso de configuración de firmware a través de una contraseña de administrador segura.

## <a name="enabling-secure-boot"></a>Habilitar el arranque seguro
Windows 10 IoT Core arrancará en dispositivos que implementan Unified Extensible Firmware Interface (UEFI).  El estándar de UEFI implementa una característica de seguridad que se conoce como arranque seguro. Esto permite que un dispositivo de arranque sólo software de confianza mediante la restricción del sistema para solo permitir la ejecución de archivos binarios firmados por una entidad determinada.  Cuando un dispositivo está encendido, arranque seguro de UEFI comprueba la firma de cada parte del software de arranque, incluidos los controladores de firmware y el sistema operativo.  Si las firmas no coinciden (por ejemplo, si un atacante fuera a reemplazar la imagen original con un sistema operativo en peligro) no se iniciará la plataforma. Si las firmas son buenos y comprobado, el dispositivo continúa el arranque y, a continuación, proporciona control para el sistema operativo.  Tenga en cuenta que mientras la limitación de un conjunto definido de la publicación de autoridades excluye todo el código desconocido, que no necesariamente impide código incorrecto conocido que se está ejecutando (por ejemplo, ataques de reversión).  Se recomienda encarecidamente habilitar el arranque seguro si el firmware lo admite. 

Los fabricantes de dispositivos debe almacenar las bases de datos de arranque seguro en sus dispositivos.  Esto incluye la firma base de datos (db), las firmas revocados (dbx) y la base de datos de inscripción de clave (KEK).  Estas bases de datos normalmente se almacenan en la memoria RAM (NV-RAM) permanente de firmware en el momento de la fabricación. La base de datos de firma (db) y la base de datos de firmas revocadas (dbx) mostrar los firmantes o códigos hash de las aplicaciones de UEFI, cargadores del sistema operativo (por ejemplo, el cargador del sistema operativo de Microsoft o el Administrador de arranque), la imagen y controladores UEFI que se pueden cargar en el dispositivo, así como las imágenes revocadas para elementos que ya no son de confianza y no se pueden cargar. La base de datos de inscripción de clave (KEK) es una base de datos independiente de las claves que pueden usarse para actualizar la base de datos de firma y revocados firmas de firma. Microsoft requiere una clave especificada que se incluirán en la base de datos KEK para que en el futuro Microsoft puede agregar nuevos sistemas operativos a la base de datos de la firma o agregar imágenes incorrectas conocidas a la base de datos de firmas revocados.

Después de han agregado estas bases de datos y después de pruebas y validación de firmware final, firmware está bloqueado de edición y se puede generar y agregar una clave de la plataforma (PK). La clave principal puede usarse posteriormente para firmar las actualizaciones de la KEK o realizar los cambios deseados a las variables de seguras. 

Los generadores de dispositivo deben ponerse en contacto con su fabricante de firmware para herramientas y ayuda para crear estas bases de datos. Visite este [artículo de TechNet](https://technet.microsoft.com/library/dn747883.aspx) para obtener más información sobre el arranque seguro creación y administración de clave.

## <a name="implementing-tpms"></a>Implementación de TPM  
Una plataforma segura Module (TPM), es un coprocesador criptográfico que incluye capacidades de generación de números aleatorios, generación segura de claves criptográficas y la limitación de su uso. También incluye capacidades como la autorización remota y almacenamiento sealed. Especificación técnica del TPM está disponible públicamente y está controlado por un organismo legislativo llamado el Trusted Computing Group (TCG).  TPM 2.0 está disponible como un componente discreto (de diversos fabricantes), así como dentro de algunos Qualcomm, implementado en el firmware.

Los dispositivos que incorporan un TPM pueden crear claves criptográficas y cifrarlas para que solo puede descifrar el TPM. Este proceso, a menudo denominado "encapsular" o "enlazar" una clave, puede ayudar a proteger la clave de la divulgación. Cada TPM tiene una clave de "encapsulado" maestra, llama a la clave raíz de almacenamiento (SRK), que se almacena dentro del propio TPM. La parte privada de una clave creada en un TPM nunca se expone a cualquier otro componente, software, proceso o persona. Además, los dispositivos que incorporan un TPM también pueden crear una clave que no sólo se haya encapsulado, sino también esté ligada a ciertas medidas de la plataforma. Este tipo de clave solo puede ser sin ajustar cuando esas mediciones de plataforma tienen los mismos valores que tenían cuando se creó la clave. Este proceso se denomina "sellar" la clave en el TPM mientras que descifrar la clave se denomina "quitar el sello". TPM también puede sellar y quitar el sello de datos generados fuera de TPM. Con esta clave sellada y software como cifrado de unidad BitLocker, puede bloquear los datos hasta que se cumplan las condiciones de software o hardware específico. 

Con un TPM, las partes privadas de los pares de claves se mantienen separadas de la memoria controlada por el sistema operativo. Las claves se pueden sellar en TPM y comprobar determinadas garantías sobre el estado de un sistema (controles que definen el "nivel de confianza" de un sistema) pueden realizarse antes de que las claves son y liberarlas para su uso. Dado que el TPM usa su propio firmare interno y circuitos de lógica para las instrucciones de procesamiento, no se basa en el sistema operativo y no se expone a las vulnerabilidades que puedan existir en el sistema operativo o el software de aplicación.

> [!NOTE] 
> Aunque algunos dispositivos pueden incorporar un chip de TPM 1.2 anterior, Windows 10 IoT Core solo admite TPM 2.0.

## <a name="enabling-bitlocker-encryption"></a>Habilitar el cifrado de BitLocker  
Con el fin de proteger los datos en reposo (es decir, la fecha almacenada en un dispositivo), Microsoft pone su tecnología de cifrado de unidad BitLocker de nivel empresarial para dispositivos de IoT en Windows 10 IoT Core.  BitLocker garantiza que los datos almacenados en un dispositivo permanecen cifrados, incluso si el dispositivo ha sido alterado mientras el sistema operativo no se está ejecutando.  Esto ayuda a protegerse de "ataques sin conexión," los ataques que se realizan al deshabilitar o burlar el sistema operativo instalado, o bien separar físicamente los medios de almacenamiento desde el dispositivo con el fin de atacar los datos por separado. 

BitLocker usa un módulo de plataforma segura (TPM) para proporcionar una protección mejorada para los datos y para garantizar la integridad de componentes de arranque inicial. Esto ayuda a proteger los datos de robos o de visualización no autorizada al cifrar todo el volumen de Windows y las particiones de datos que pueden estar presentes en el dispositivo.

Para obtener instrucciones adicionales sobre cómo habilitar BitLocker en Windows 10 IoT Core, siga los pasos descritos [aquí](../secure-your-device/SecureBootandBitLocker.md).

## <a name="onboard-storage-options"></a>Opciones de almacenamiento incorporado
Paneles de desarrollo, como la Raspberry Pi 3 populares, proporcionan flexibilidad y permiten a los desarrolladores arrancar fácilmente cualquier plataforma mediante una tarjeta SD extraíble.  La mayoría de los dispositivos de IoT del sector, dicha flexibilidad no es deseable y puede realizar un objetivo fácil para los ataques de dichos dispositivos. En su lugar, al diseñar el hardware, considere el uso de un almacenamiento eMMC para los dispositivos de IoT más pequeños y de bajo costos.  Almacenamiento incrustado facilita mucho más difícil separar el contenido desde el dispositivo y a su vez, reduce el riesgo de introducir código malintencionado en el robo de datos o el dispositivo. 

## <a name="developer-tools"></a>Herramientas de desarrollo  
Al compilar Windows 10 IoT Core imagen final trasvase de registros dispositivo con ICD (Diseñador de configuración de la imagen), no Asegúrese de que ningún desarrollador herramientas están incluidas en la imagen de venta directa.  Herramientas que permite a los desarrolladores obtener acceso remoto y depurar los dispositivos de IoT Core no deben estar presentes en los sistemas de producción como estos potencialmente pueden abrir el dispositivo a los ataques.  Asegúrese de que si utiliza nuestras herramientas de desarrollo, como Windows Device Portal, servidor ftp, PowerShell o SSH en las imágenes durante el desarrollo, probar y validar los escenarios en retail que IOT Core imágenes que no incluyen estas herramientas.

## <a name="user-accounts"></a>Cuentas de usuario  
La mayoría de los usuarios están familiarizados con la noción de toma de "propiedad" de dispositivos como equipos y teléfonos - la idea de personalizar el dispositivo cuando la conversión unboxing y configurar las credenciales para acceder al dispositivo. A diferencia de consumidor de los equipos y teléfonos, dispositivos de IoT no pretenden servir como dispositivos informáticos de uso general. En su lugar, son dispositivos de aplicación normalmente solo para fines fijo. Aunque Windows admite la noción de administradores de dispositivos que puede conectarse de forma remota a los dispositivos durante un ciclo de desarrollo, dicha compatibilidad en dispositivos de IoT del sector puede suponer una amenaza, especialmente cuando se usan contraseñas poco seguras.  En general, Microsoft recomienda que no se deben crear ninguna cuenta de "default" o las contraseñas en los dispositivos Windows 10 IoT Core.

