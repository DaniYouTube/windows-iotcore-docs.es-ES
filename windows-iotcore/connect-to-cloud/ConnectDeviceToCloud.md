---
title: Conectar el dispositivo a la nube
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: Obtenga información sobre cómo conectar el dispositivo a la nube.
keywords: seguridad de Azure, de iot, Windows, el módulo de plataforma segura, SoC
ms.openlocfilehash: ff54bbfa1aaf30d08107fac72ba59ae5a04aa247
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59515023"
---
# <a name="connect-your-device-to-the-cloud"></a><span data-ttu-id="707b5-104">Conectar el dispositivo a la nube</span><span class="sxs-lookup"><span data-stu-id="707b5-104">Connect your device to the cloud</span></span>

<span data-ttu-id="707b5-105">Almacenar información segura, como una contraseña o un certificado en un dispositivo podría hacer que un dispositivo sea vulnerable a la exposición.</span><span class="sxs-lookup"><span data-stu-id="707b5-105">Storing secure information such as a password or a certificate on a device could make a device vulnerable to exposure.</span></span> <span data-ttu-id="707b5-106">Una contraseña filtrada es una manera reír para poner en peligro la seguridad de un dispositivo o un sistema completo.</span><span class="sxs-lookup"><span data-stu-id="707b5-106">A leaked password is a surefire way to compromise the security of a device or an entire system.</span></span> <span data-ttu-id="707b5-107">En la familia Windows, la tecnología que admite la seguridad del sistema operativo es el módulo de plataforma segura.</span><span class="sxs-lookup"><span data-stu-id="707b5-107">In the Windows family, the technology that supports the security of the OS is the Trusted Platform Module.</span></span>

<span data-ttu-id="707b5-108">Un [módulo de plataforma segura](https://en.wikipedia.org/wiki/Trusted_Platform_Module) dispositivo (TPM) es un microcontrolador que puede almacenar datos y realizar cálculos.</span><span class="sxs-lookup"><span data-stu-id="707b5-108">A [Trusted Platform Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module) (TPM) device is a microcontroller that can store data and perform computations.</span></span> <span data-ttu-id="707b5-109">Puede ser un chip discreto soldado a la placa base de un equipo o un módulo integrado en el sistema en un chip (SoC) por el fabricante.</span><span class="sxs-lookup"><span data-stu-id="707b5-109">It can be either a discrete chip soldered to a computer's motherboard or a module integrated into the system on a chip (SoC) by the manufacturer.</span></span> 

## <a name="inside-the-tpm"></a><span data-ttu-id="707b5-110">Dentro de TPM</span><span class="sxs-lookup"><span data-stu-id="707b5-110">Inside the TPM</span></span> 

<span data-ttu-id="707b5-111">Una capacidad clave de TPM es su memoria de solo escritura.</span><span class="sxs-lookup"><span data-stu-id="707b5-111">A key capability of the TPM is its write-only memory.</span></span> <span data-ttu-id="707b5-112">En función de los datos en ella, TPM también puede calcular un hash criptográfico (como el [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), en función de esos datos.</span><span class="sxs-lookup"><span data-stu-id="707b5-112">Based on the data in it, TPM can also compute a cryptographic hash (such as the [HMAC](https://en.wikipedia.org/wiki/Hash-based_message_authentication_code)), based on that data.</span></span>
<span data-ttu-id="707b5-113">No es posible descubrir el secreto dado el hash, pero si se conoce el secreto para ambas partes de comunicación, es posible determinar si se ha generado el hash recibido de otra entidad desde ese secreto.</span><span class="sxs-lookup"><span data-stu-id="707b5-113">It’s impossible to uncover the secret given the hash, but if the secret is known to both parties of communication, it is possible to determine whether the hash received from another party was produced from that secret.</span></span>

<span data-ttu-id="707b5-114">La idea básica mediante claves criptográficas: se establece el secreto (también denominado clave de acceso compartido) y se comparte entre el dispositivo de IoT y la nube durante el proceso de aprovisionamiento de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="707b5-114">The basic idea behind using cryptographic keys: the secret (also called the shared access key) is established and shared between the IoT device and the cloud during the device provisioning process.</span></span> <span data-ttu-id="707b5-115">Desde ese momento, un HMAC que se deriva el secreto se usarán para autenticar el dispositivo de IoT.</span><span class="sxs-lookup"><span data-stu-id="707b5-115">From that point on, an HMAC derived from the secret will be used to authenticate the IoT device.</span></span>

## <a name="device-provisioning"></a><span data-ttu-id="707b5-116">Aprovisionamiento de dispositivos</span><span class="sxs-lookup"><span data-stu-id="707b5-116">Device Provisioning</span></span> 

<span data-ttu-id="707b5-117">La herramienta que aprovisiona los dispositivos Windows 10 IoT Core se denomina el panel de IoT Core y puede descargarse desde [la página de descargas](http://go.microsoft.com/fwlink/?LinkID=708576).</span><span class="sxs-lookup"><span data-stu-id="707b5-117">The tool that provisions Windows 10 IoT Core devices is called the IoT Core Dashboard and can be downloaded from [the downloads page](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

<span data-ttu-id="707b5-118">El panel genera una imagen del sistema operativo y conecta el dispositivo con seguridad en Azure.</span><span class="sxs-lookup"><span data-stu-id="707b5-118">The dashboard produces an image of the OS and securely connects your device to Azure.</span></span> <span data-ttu-id="707b5-119">Esto se hace mediante la asociación del dispositivo físico con el identificador de dispositivo en IoT Hub de Azure e impresiones de la clave específica del dispositivo de acceso compartido en TPM del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="707b5-119">This is done by associating the physical device with the device ID in the Azure IoT Hub and imprinting the device-specific shared access key to the device's TPM.</span></span> 

<span data-ttu-id="707b5-120">Para los dispositivos que no tienen un chip de TPM, la herramienta puede instalar un TPM de software emulados.</span><span class="sxs-lookup"><span data-stu-id="707b5-120">For devices that don’t have a TPM chip, the tool can install a software-emulated TPM.</span></span> <span data-ttu-id="707b5-121">Esto no proporciona seguridad, pero le permite desarrollar aplicaciones mediante un dispositivo maker (como Raspberry Pi 2 o 3) y tiene seguridad "iluminada" en un dispositivo con el hardware TPM sin tener que cambiar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="707b5-121">This does not provide security but allows you to develop your app using a maker device (such as Raspberry Pi 2 or 3) and have security "light up" on a device with the hardware TPM without having to change the app.</span></span> 

<span data-ttu-id="707b5-122">Para conectar el dispositivo a Azure, haga clic en la pestaña "Conectar a Azure":</span><span class="sxs-lookup"><span data-stu-id="707b5-122">To connect your device to Azure, click on the "Connect to Azure" tab:</span></span>

![Abrir conectarse a la pestaña de Azure](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen01.png)

<span data-ttu-id="707b5-124">Se le pedirá que inicie sesión en su cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="707b5-124">You will be asked to log in to your Azure account.</span></span> <span data-ttu-id="707b5-125">Seleccione la instancia de Azure IoT Hub deseada y asociar el dispositivo físico.</span><span class="sxs-lookup"><span data-stu-id="707b5-125">Pick the desired instance of Azure IoT Hub and associate your physical device with it.</span></span> <span data-ttu-id="707b5-126">Si no tiene ninguna instancia de IoT Hub en su suscripción de Azure, la herramienta permitirá crear una instancia gratuita.</span><span class="sxs-lookup"><span data-stu-id="707b5-126">If you don’t have any IoT Hub instances in your Azure subscription, the tool will let you create a free instance.</span></span> 

<span data-ttu-id="707b5-127">Una vez haya seleccionado el centro de IoT y el identificador de dispositivo para asociar el dispositivo con, puede transmitir la clave de acceso compartido de ese dispositivo en el TPM:</span><span class="sxs-lookup"><span data-stu-id="707b5-127">Once you have selected the IoT Hub and the device ID to associate your device with, you can imprint the shared access key of that device on your TPM:</span></span>

![Dispositivo de provisión](../media/ConnectDeviceToCloud/Building_Secure_Apps_for_IoT_Core_Screen02.png)

<span data-ttu-id="707b5-129">El dispositivo ahora está listo para conectarse a Azure de forma segura.</span><span class="sxs-lookup"><span data-stu-id="707b5-129">Your device is now ready to connect to Azure in a secure way.</span></span> 

<span data-ttu-id="707b5-130">También puede usar el Windows Device Portal para adquirir una cadena de conexión de IoT Hub de forma dinámica cuando primero se conecta a internet después de que se está aprovisionando.</span><span class="sxs-lookup"><span data-stu-id="707b5-130">You can also use the Windows Device Portal to dynamically acquire an IoT Hub connection string when it first connects to the internet after being provisioned.</span></span> <span data-ttu-id="707b5-131">Esto puede hacerse desde la pestaña "Clientes de Azure" en el Portal de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="707b5-131">This can be done from the "Azure Clients" tab in the Device Portal.</span></span>

![Pestaña de clientes de Azure](../media/ConnectDeviceToCloud/azure-clients.png)

## <a name="helpful-resources"></a><span data-ttu-id="707b5-133">Recursos útiles:</span><span class="sxs-lookup"><span data-stu-id="707b5-133">Helpful resources:</span></span>
* [<span data-ttu-id="707b5-134">Conectar la aplicación a Azure</span><span class="sxs-lookup"><span data-stu-id="707b5-134">Connecting your app to Azure</span></span>](../connect-to-cloud/ConnectAppToCloud.md)
* [<span data-ttu-id="707b5-135">Creación de aplicaciones seguras para IoT Core</span><span class="sxs-lookup"><span data-stu-id="707b5-135">Building secure apps for IoT Core</span></span>](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core/#oqFLXiWIL1iCF8j9.97)
