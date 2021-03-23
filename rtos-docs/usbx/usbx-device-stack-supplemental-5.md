---
title: Kapitel 5 – USBX OTG
description: USBX stöder OTG-funktionerna i USB när en OTG-kompatibel USB-styrenhet är tillgänglig i maskin varu designen.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: da562fd843c6ef0fd17f0d979ca57bd37572748d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827414"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="1dc29-103">Kapitel 5 – USBX OTG</span><span class="sxs-lookup"><span data-stu-id="1dc29-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="1dc29-104">USBX stöder OTG-funktionerna i USB när en OTG-kompatibel USB-styrenhet är tillgänglig i maskin varu designen.</span><span class="sxs-lookup"><span data-stu-id="1dc29-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="1dc29-105">USBX stöder OTG i kärn USB-stacken.</span><span class="sxs-lookup"><span data-stu-id="1dc29-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="1dc29-106">Men för att OTG ska fungera krävs en speciell USB-styrenhet.</span><span class="sxs-lookup"><span data-stu-id="1dc29-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="1dc29-107">USBX OTG Controller-funktioner finns i usbx_otg-katalogen.</span><span class="sxs-lookup"><span data-stu-id="1dc29-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="1dc29-108">Den aktuella USBX-versionen stöder bara NXP-LPC3131 med fullständiga OTG-funktioner.</span><span class="sxs-lookup"><span data-stu-id="1dc29-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="1dc29-109">Driv rutins funktionerna för vanliga kontrollanter (värd eller enhet) finns fortfarande i standard-USBX usbx_device_controllers och usbx_host_controllers, men usbx_otg katalogen innehåller de speciella OTG-funktioner som är associerade med USB-styrenheten.</span><span class="sxs-lookup"><span data-stu-id="1dc29-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="1dc29-110">Det finns fyra funktions kategorier för en OTG-styrenhet Förutom vanliga funktioner för värd/enhet.</span><span class="sxs-lookup"><span data-stu-id="1dc29-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="1dc29-111">VBUS-/regionsspecifika funktioner</span><span class="sxs-lookup"><span data-stu-id="1dc29-111">VBUS specific functions</span></span>
- <span data-ttu-id="1dc29-112">Starta och stoppa styrenheten</span><span class="sxs-lookup"><span data-stu-id="1dc29-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="1dc29-113">USB-roll hanterare</span><span class="sxs-lookup"><span data-stu-id="1dc29-113">USB role manager</span></span>
- <span data-ttu-id="1dc29-114">Avbrotts hanterare</span><span class="sxs-lookup"><span data-stu-id="1dc29-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="1dc29-115">VBUS-funktioner</span><span class="sxs-lookup"><span data-stu-id="1dc29-115">VBUS functions</span></span>

<span data-ttu-id="1dc29-116">Varje kontrollant måste ha en VBUS-ansvarig för att ändra status för VBUS baserat på energispar funktioner.</span><span class="sxs-lookup"><span data-stu-id="1dc29-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="1dc29-117">Den här funktionen utför vanligt vis bara att aktivera eller inaktivera VBUS.</span><span class="sxs-lookup"><span data-stu-id="1dc29-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="1dc29-118">Starta och stoppa styrenheten</span><span class="sxs-lookup"><span data-stu-id="1dc29-118">Start and Stop the controller</span></span>

<span data-ttu-id="1dc29-119">Till skillnad från en vanlig USB-implementering kräver OTG att värden och/eller enhets stacken aktive ras och inaktive ras när rollen ändras.</span><span class="sxs-lookup"><span data-stu-id="1dc29-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="1dc29-120">USB-roll hanterare</span><span class="sxs-lookup"><span data-stu-id="1dc29-120">USB role Manager</span></span>

<span data-ttu-id="1dc29-121">USB-rolltjänsten tar emot kommandon för att ändra status för USB-filen.</span><span class="sxs-lookup"><span data-stu-id="1dc29-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="1dc29-122">Det finns flera tillstånd som behöver över gångar till och från:</span><span class="sxs-lookup"><span data-stu-id="1dc29-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="1dc29-123">Tillstånd</span><span class="sxs-lookup"><span data-stu-id="1dc29-123">State</span></span>                    | <span data-ttu-id="1dc29-124">Värde</span><span class="sxs-lookup"><span data-stu-id="1dc29-124">Value</span></span> | <span data-ttu-id="1dc29-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1dc29-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="1dc29-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="1dc29-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="1dc29-127">0</span><span class="sxs-lookup"><span data-stu-id="1dc29-127">0</span></span>     | <span data-ttu-id="1dc29-128">Enheten är inaktiv.</span><span class="sxs-lookup"><span data-stu-id="1dc29-128">The device is Idle.</span></span> <span data-ttu-id="1dc29-129">Inte ansluten till något</span><span class="sxs-lookup"><span data-stu-id="1dc29-129">Not connected to anything</span></span> |
| <span data-ttu-id="1dc29-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="1dc29-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="1dc29-131">1</span><span class="sxs-lookup"><span data-stu-id="1dc29-131">1</span></span>     | <span data-ttu-id="1dc29-132">Enheten är ansluten med typen anslutning</span><span class="sxs-lookup"><span data-stu-id="1dc29-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="1dc29-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="1dc29-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="1dc29-134">2</span><span class="sxs-lookup"><span data-stu-id="1dc29-134">2</span></span>     | <span data-ttu-id="1dc29-135">Enheten är ansluten med typ B-anslutning</span><span class="sxs-lookup"><span data-stu-id="1dc29-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="1dc29-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="1dc29-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="1dc29-137">3</span><span class="sxs-lookup"><span data-stu-id="1dc29-137">3</span></span>     | <span data-ttu-id="1dc29-138">Värd enheten har kopplats från</span><span class="sxs-lookup"><span data-stu-id="1dc29-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="1dc29-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="1dc29-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="1dc29-140">4</span><span class="sxs-lookup"><span data-stu-id="1dc29-140">4</span></span>     | <span data-ttu-id="1dc29-141">Roll växling från värd till slav</span><span class="sxs-lookup"><span data-stu-id="1dc29-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="1dc29-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="1dc29-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="1dc29-143">5</span><span class="sxs-lookup"><span data-stu-id="1dc29-143">5</span></span>     | <span data-ttu-id="1dc29-144">Slaven het är frånkopplad</span><span class="sxs-lookup"><span data-stu-id="1dc29-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="1dc29-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="1dc29-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="1dc29-146">6</span><span class="sxs-lookup"><span data-stu-id="1dc29-146">6</span></span>     | <span data-ttu-id="1dc29-147">Roll växling från slav till värd</span><span class="sxs-lookup"><span data-stu-id="1dc29-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="1dc29-148">Avbrotts hanterare</span><span class="sxs-lookup"><span data-stu-id="1dc29-148">Interrupt handlers</span></span>

<span data-ttu-id="1dc29-149">Både värd-och enhets styrenhetens driv rutiner för OTG kräver olika avbrotts hanterare för att övervaka signaler bortom traditionella USB-avbrott, särskilt signaler på grund av enhets-och VBUS.</span><span class="sxs-lookup"><span data-stu-id="1dc29-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="1dc29-150">Initiera en USB-OTG kontrollant.</span><span class="sxs-lookup"><span data-stu-id="1dc29-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="1dc29-151">Vi använder NXP-LPC3131 som ett exempel här.</span><span class="sxs-lookup"><span data-stu-id="1dc29-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="1dc29-152">I det här exemplet initierar vi LPC3131 i OTG-läge genom att skicka en VBUS-funktion och en motringning för läges ändring (från värd till slav eller vice versa).</span><span class="sxs-lookup"><span data-stu-id="1dc29-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="1dc29-153">Funktionen motringning ska bara registrera det nya läget och aktivera en väntande tråd för att skapa det nya läget.</span><span class="sxs-lookup"><span data-stu-id="1dc29-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="1dc29-154">Läge svärdet som skickas kan ha följande värden.</span><span class="sxs-lookup"><span data-stu-id="1dc29-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="1dc29-155">**UX_OTG_MODE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="1dc29-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="1dc29-156">**UX_OTG_MODE_SLAVE**</span><span class="sxs-lookup"><span data-stu-id="1dc29-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="1dc29-157">**UX_OTG_MODE_HOST**</span><span class="sxs-lookup"><span data-stu-id="1dc29-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="1dc29-158">Programmet kan alltid kontrol lera vad enheten är genom att titta på variabeln:</span><span class="sxs-lookup"><span data-stu-id="1dc29-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="1dc29-159">Dess värden kan vara något av följande.</span><span class="sxs-lookup"><span data-stu-id="1dc29-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="1dc29-160">**UX_OTG_DEVICE_A**</span><span class="sxs-lookup"><span data-stu-id="1dc29-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="1dc29-161">**UX_OTG_DEVICE_B**</span><span class="sxs-lookup"><span data-stu-id="1dc29-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="1dc29-162">**UX_OTG_DEVICE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="1dc29-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="1dc29-163">En USB-OTG kan alltid fråga efter en roll växling genom att utfärda följande kommando.</span><span class="sxs-lookup"><span data-stu-id="1dc29-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="1dc29-164">För en slav enhet finns det inget kommando att utfärda, men den sekundära enheten kan ange ett tillstånd för att ändra rollen, som kommer att hämtas av värden när den utfärdar en **GET_STATUS** och växlingen initieras.</span><span class="sxs-lookup"><span data-stu-id="1dc29-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
