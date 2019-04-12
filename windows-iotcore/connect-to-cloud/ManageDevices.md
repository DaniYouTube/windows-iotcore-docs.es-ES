---
title: Administrar dispositivos Windows con Azure IoT Hub
author: saraclay
ms.author: saclayt
ms.date: 01/08/2018
ms.topic: article
description: Obtenga información sobre cómo administrar los dispositivos de Windows con Azure IoT Hub.
keywords: Windows iot, Azure, DM, administración de dispositivos Azure IoT Hub, IoT Hub, el estado del dispositivo
ms.openlocfilehash: f3018007c262112374fd39439bf2306675fddafe
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/11/2019
ms.locfileid: "59514679"
---
# <a name="manage-your-windows-devices-with-the-azure-iot-hub"></a><span data-ttu-id="3e63b-104">Administrar dispositivos Windows con Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="3e63b-104">Manage your Windows devices with the Azure IoT Hub</span></span>

## <a name="overview"></a><span data-ttu-id="3e63b-105">Información general</span><span class="sxs-lookup"><span data-stu-id="3e63b-105">Overview</span></span>
<span data-ttu-id="3e63b-106">Administración de dispositivos (DM) permite a los operadores configurar y supervisar simultáneamente muy grandes volúmenes de dispositivos IoT de forma remota.</span><span class="sxs-lookup"><span data-stu-id="3e63b-106">Device Management (DM) allows operators to remotely configure and monitor very high volumes of IoT devices simultaneously.</span></span>

<span data-ttu-id="3e63b-107">Configuración de los dispositivos se puede insertar en los dispositivos, si los dispositivos de destino están en línea o sin conexión.</span><span class="sxs-lookup"><span data-stu-id="3e63b-107">Configuration for the devices can be pushed to devices, whether the target devices are online or offline.</span></span> <span data-ttu-id="3e63b-108">Si el dispositivo está desconectado recogerá la nueva configuración cuando se vuelve a conectar.</span><span class="sxs-lookup"><span data-stu-id="3e63b-108">If the device is offline it will pick up the new configuration when it reconnects.</span></span> <span data-ttu-id="3e63b-109">Operadores de dispositivo también pueden recuperar el estado de cada dispositivo, incluso si las actualizaciones de configuración de dispositivo se han aplicado correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="3e63b-109">Device operators can also retrieve the status of each device, including whether device configuration updates have been successfully applied or not.</span></span>

<span data-ttu-id="3e63b-110">Habilitar estas características para los dispositivos de IoT requiere una central, sólida y confiable mecanismo para almacenar e implementar los datos de configuración para los dispositivos de destino y supervisar el estado de dispositivo, a escala.</span><span class="sxs-lookup"><span data-stu-id="3e63b-110">Enabling these features for IoT devices requires a central, robust, and reliable mechanism to store and to deploy the configuration data to the target devices, and monitor device status - at scale.</span></span>

<span data-ttu-id="3e63b-111">Una solución completa requiere lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3e63b-111">A complete solution requires the following:</span></span>

* <span data-ttu-id="3e63b-112">Un servicio de nube sólida y escalable para almacenar los Estados deseados y notificados de los diversos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3e63b-112">A Robust/Scalable Cloud Service to store the desired and reported states of the various devices.</span></span>
  * <span data-ttu-id="3e63b-113">Azure IoT Hub y administración de dispositivos de Azure ofrecen un servicio en la nube altamente escalable y eficaz para administrar millones de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3e63b-113">Azure IoT Hub and Azure Device Management offer a highly scalable and efficient cloud service for managing millions of devices.</span></span>

* <span data-ttu-id="3e63b-114">Un cliente que se ejecuta en el dispositivo y puede aplicar la configuración deseada y notificar el estado del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3e63b-114">A Client that runs on the device and can apply the desired configuration and report the state of the device.</span></span>
  * <span data-ttu-id="3e63b-115">El cliente de minería de datos Windows Azure de IoT (un código abierto SDK + en tiempo de ejecución), junto con Azure IoT Hub, puede aplicar y notificar un gran conjunto de común, en ocasiones, crítico, las configuraciones de Windows.</span><span class="sxs-lookup"><span data-stu-id="3e63b-115">The Windows IoT Azure DM Client (an open source SDK + runtime), in conjunction with Azure IoT Hub, can apply and report on a large set of common, sometimes critical, Windows configurations.</span></span>

* <span data-ttu-id="3e63b-116">Un Portal o una aplicación que se utilizará el operador para configurar y consultar los dispositivos de forma remota.</span><span class="sxs-lookup"><span data-stu-id="3e63b-116">A Portal or an Application that will be used by the operator to configure and query the devices remotely.</span></span>
  * <span data-ttu-id="3e63b-117">Esto debe personalizarse para dispositivos con el dispositivo de OEM u operador.</span><span class="sxs-lookup"><span data-stu-id="3e63b-117">This must be customized for devices by the device OEM or operator.</span></span> <span data-ttu-id="3e63b-118">Como parte de esta solución, también proporcionamos un modelo de datos de código abierto y ejemplo de implementación para la interacción sea más fácil con el almacenamiento de IoT Hub y el cliente de Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="3e63b-118">As part of this solution, we also provide an open source data model and sample implementation for easier interaction with the IoT Hub storage and the Windows IoT client.</span></span>

<span data-ttu-id="3e63b-119">Para obtener más información sobre la administración de dispositivos para dispositivos de Windows, visite principal [repositorio de administración de cliente de dispositivo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span><span class="sxs-lookup"><span data-stu-id="3e63b-119">To learn more about device management for Windows devices, visit the main [Device Management Client repo](https://github.com/ms-iot/iot-core-azure-dm-client/tree/master).</span></span>
