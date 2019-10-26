---
title: Conectar el dispositivo a la nube
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar el dispositivo a la nube.
keywords: Windows IOT, Azure, seguridad, Módulo de plataforma segura, SoC
ms.openlocfilehash: 6bce16b45175c4c19156f30f35f6d3502f675930
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918397"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="b10d5-104">Conectar el dispositivo a la nube</span><span class="sxs-lookup"><span data-stu-id="b10d5-104">Connect your device to the cloud</span></span>

<span data-ttu-id="b10d5-105">Almacenar información segura, como una contraseña o un certificado en un dispositivo, puede hacer que un dispositivo sea vulnerable a la exposición.</span><span class="sxs-lookup"><span data-stu-id="b10d5-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="b10d5-106">Una contraseña filtrada es una forma SureFire de poner en peligro la seguridad de un dispositivo o de un sistema completo.</span><span class="sxs-lookup"><span data-stu-id="b10d5-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="b10d5-107">En la familia de Windows, la tecnología que admite la seguridad del sistema operativo es la Módulo de plataforma segura.</span><span class="sxs-lookup"><span data-stu-id="b10d5-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="b10d5-108">Un dispositivo [módulo de plataforma segura](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) es un microcontrolador que puede almacenar datos y realizar cálculos.</span><span class="sxs-lookup"><span data-stu-id="b10d5-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="b10d5-109">Puede ser un chip discreto soldado a la placa base de un equipo o un módulo integrado en el sistema en un chip (SoC) por el fabricante.</span><span class="sxs-lookup"><span data-stu-id="b10d5-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="b10d5-110">Dentro de TPM</span><span class="sxs-lookup"><span data-stu-id="b10d5-110">Inside the TPM</span></span> 

<span data-ttu-id="b10d5-111">Una funcionalidad clave de TPM es la memoria de solo escritura.</span><span class="sxs-lookup"><span data-stu-id="b10d5-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="b10d5-112">En función de los datos que contenga, TPM también puede calcular un hash criptográfico (como [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), basado en esos datos.</span><span class="sxs-lookup"><span data-stu-id="b10d5-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="b10d5-113">No es posible descubrir el secreto dado el hash, pero si ambas partes de la comunicación conocen el secreto, es posible determinar si el hash recibido de otra entidad se produjo a partir de ese secreto.</span><span class="sxs-lookup"><span data-stu-id="b10d5-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="b10d5-114">La idea básica detrás del uso de claves criptográficas: el secreto (también denominado clave de acceso compartido) se establece y comparte entre el dispositivo IoT y la nube durante el proceso de aprovisionamiento de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b10d5-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="b10d5-115">A partir de ese momento, se usará un HMAC derivado del secreto para autenticar el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="b10d5-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="b10d5-116">Aprovisionamiento de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b10d5-116">Device Provisioning</span></span> 

<span data-ttu-id="b10d5-117">La herramienta que aprovisiona dispositivos Windows 10 IoT Core se denomina panel de IoT Core y se puede descargar desde [la página de descargas](http://go.microsoft.com/fwlink/?LinkID=708576).</span><span class="sxs-lookup"><span data-stu-id="b10d5-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="b10d5-118">El panel genera una imagen del sistema operativo y conecta de forma segura el dispositivo a Azure.</span><span class="sxs-lookup"><span data-stu-id="b10d5-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="b10d5-119">Esto se realiza asociando el dispositivo físico con el identificador del dispositivo en el Azure IoT Hub e imprime la clave de acceso compartida específica del dispositivo en el TPM del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b10d5-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="b10d5-120">En el caso de los dispositivos que no tienen un chip de TPM, la herramienta puede instalar un TPM emulado por software.</span><span class="sxs-lookup"><span data-stu-id="b10d5-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="b10d5-121">Esto no proporciona seguridad, pero permite desarrollar la aplicación mediante un dispositivo de creador (como Raspberry pi 2 o 3) y hacer que la seguridad "se ilumine" en un dispositivo con el TPM de hardware sin tener que cambiar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b10d5-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="b10d5-122">Para conectar el dispositivo a Azure, haga clic en la pestaña "conectar con Azure":</span><span class="sxs-lookup"><span data-stu-id="b10d5-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![Abra la pestaña conectar a Azure.](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="b10d5-124">Se le pedirá que inicie sesión en su cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="b10d5-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="b10d5-125">Seleccione la instancia deseada de Azure IoT Hub y asocie el dispositivo físico con ella.</span><span class="sxs-lookup"><span data-stu-id="b10d5-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="b10d5-126">Si no tiene ninguna instancia de IoT Hub en su suscripción de Azure, la herramienta le permitirá crear una instancia gratuita.</span><span class="sxs-lookup"><span data-stu-id="b10d5-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="b10d5-127">Una vez que haya seleccionado el IoT Hub y el ID. de dispositivo con el que asociar el dispositivo, puede incluir la clave de acceso compartido de dicho dispositivo en el TPM:</span><span class="sxs-lookup"><span data-stu-id="b10d5-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![Aprovisionar dispositivo](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="b10d5-129">El dispositivo ya está listo para conectarse a Azure de forma segura.</span><span class="sxs-lookup"><span data-stu-id="b10d5-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="b10d5-130">También puede usar el portal de dispositivos de Windows para adquirir dinámicamente una cadena de conexión de IoT Hub cuando se conecta por primera vez a Internet después de aprovisionarse.</span><span class="sxs-lookup"><span data-stu-id="b10d5-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="b10d5-131">Esto puede realizarse desde la pestaña "clientes de Azure" en el portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b10d5-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Pestaña clientes de Azure](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="b10d5-133">Recursos útiles:</span><span class="sxs-lookup"><span data-stu-id="b10d5-133">Helpful resources:</span></span>
* [<span data-ttu-id="b10d5-134">Conexión de la aplicación a Azure</span><span class="sxs-lookup"><span data-stu-id="b10d5-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="b10d5-135">Compilación de aplicaciones seguras para IoT Core</span><span class="sxs-lookup"><span data-stu-id="b10d5-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
