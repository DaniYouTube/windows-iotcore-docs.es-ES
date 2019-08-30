---
title: Administrar dispositivos Windows con el Azure IoT Hub
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Obtenga información acerca de cómo administrar los dispositivos Windows con el Azure IoT Hub.
keywords: Windows IOT, Azure, DM, administración de dispositivos, Azure IoT Hub, IoT Hub, estado del dispositivo
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169043"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="7d9a1-104">Administrar dispositivos Windows con el Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="7d9a1-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="7d9a1-105">Información general</span><span class="sxs-lookup"><span data-stu-id="7d9a1-105">Overview</span></span>
<span data-ttu-id="7d9a1-106">La administración de dispositivos (DM) permite a los operadores configurar y supervisar de forma remota volúmenes muy altos de dispositivos IoT de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="7d9a1-107">La configuración de los dispositivos se puede insertar en los dispositivos, independientemente de si están en línea o sin conexión.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="7d9a1-108">Si el dispositivo está sin conexión, recogerá la nueva configuración cuando vuelva a conectarse.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="7d9a1-109">Los operadores de dispositivo también pueden recuperar el estado de cada dispositivo, incluso si las actualizaciones de configuración del dispositivo se han aplicado correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="7d9a1-110">Habilitar estas características para dispositivos IoT requiere un mecanismo central, sólido y confiable para almacenar e implementar los datos de configuración en los dispositivos de destino y supervisar el estado del dispositivo a escala.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="7d9a1-111">Una solución completa requiere lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7d9a1-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="7d9a1-112">Un servicio en la nube sólido y escalable para almacenar los Estados deseados e indicados de los distintos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="7d9a1-113">Azure IoT Hub y la administración de dispositivos de Azure ofrecen un servicio en la nube muy escalable y eficaz para administrar millones de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="7d9a1-114">Un cliente que se ejecuta en el dispositivo y puede aplicar la configuración deseada e informar del estado del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="7d9a1-115">El cliente de Windows IoT Azure DM (un SDK + Runtime de código abierto), junto con Azure IoT Hub, puede aplicar e informar sobre un gran conjunto de configuraciones de Windows comunes, en ocasiones críticas.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="7d9a1-116">Un portal o una aplicación que usará el operador para configurar y consultar los dispositivos de forma remota.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="7d9a1-117">Este debe personalizarse para dispositivos por el OEM o el operador del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="7d9a1-118">Como parte de esta solución, también proporcionamos un modelo de datos de código abierto y una implementación de ejemplo para facilitar la interacción con el almacenamiento de IoT Hub y el cliente de Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="7d9a1-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="7d9a1-119">Para obtener más información acerca de la administración de dispositivos para dispositivos Windows, visite el repositorio principal del [cliente de administración de dispositivos](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span><span class="sxs-lookup"><span data-stu-id="7d9a1-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
