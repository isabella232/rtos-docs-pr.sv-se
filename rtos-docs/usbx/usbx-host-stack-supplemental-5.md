---
title: USBX OTG
description: USBX stöder OTG-funktionerna i USB när en OTG-kompatibel USB-styrenhet är tillgänglig i maskinvarudesignen.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bb9a0b98ed3f843ee690dfe419a3684562f1255e6839ddb06ded9d8f6023adcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798273"
---
# <a name="chapter-5-usbx-otg"></a>Kapitel 5: USBX OTG

USBX stöder OTG-funktionerna i USB när en OTG-kompatibel USB-styrenhet är tillgänglig i maskinvarudesignen.

USBX stöder OTG i USB-kärnstacken. Men för att OTG ska fungera krävs en specifik USB-styrenhet. USBX OTG-styrenhetsfunktioner finns  i usbx_otg katalogen. Den aktuella USBX-versionen stöder endast NXP LPC3131 med fullständiga OTG-funktioner.

De vanliga styrenhetsdrivrutinsfunktionerna (värd eller enhet) finns fortfarande i STANDARD USBX-usbx_device_controllers och usbx_host_controllers, men ***usbx_otg-katalogen*** innehåller de specifika OTG-funktioner som är associerade med USB-styrenheten.

Det finns fyra kategorier av funktioner för en OTG-styrenhet utöver de vanliga värd-/enhetsfunktioner.

- VBUS-specifika funktioner
- Start och stopp av kontrollanten
- USB-rollhanterare
- Avbrottshanterare

## <a name="vbus-functions"></a>VBUS-funktioner

Varje styrenhet måste ha en VBUS-hanterare för att ändra tillståndet för VBUS baserat på energisparkrav. Den här funktionen utför vanligtvis bara att aktivera eller inaktivera VBUS

## <a name="start-and-stop-the-controller"></a>Starta och stoppa kontrollanten

Till skillnad från en vanlig USB-implementering kräver OTG att värden och/eller enhetsstacken aktiveras och inaktiveras när rollen ändras.

## <a name="usb-role-manager"></a>USB-rollhanterare

USB-rollhanteraren tar emot kommandon för att ändra USB-tillståndet. Det finns flera tillstånd som behöver övergångar till och från de som anges i tabellen nedan.

| Tillstånd                    | Värde | Beskrivning                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | Enheten är inaktiv. Inte ansluten till något |
| UX_OTG_IDLE_TO_HOST  | 1     | Enheten är ansluten med typ A-anslutning             |
| UX_OTG_IDLE_TO_SLAVE | 2     | Enheten är ansluten med typ B-anslutning             |
| UX_OTG_HOST_TO_IDLE  | 3     | Värdenheten kopplades från                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Rollbyte från värd till undernod                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | Den underkopplade enheten är frånkopplad                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Rollbyte från slave till värd                          |

## <a name="interrupt-handlers"></a>Avbrottshanterare

Både värd- och enhetsstyrenhetsdrivrutiner för OTG behöver olika avbrottshanterare för att övervaka signaler utöver traditionella USB-avbrott, särskilt signaler som beror på SRP och VBUS.

Så här initierar du en USB OTG-styrenhet. Vi använder NXP LPC3131 som exempel här.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

I det här exemplet initierar vi LPC3131 i OTG-läge genom att skicka en VBUS-funktion och ett återanrop för lägesändring (från värd till undergående eller vice versa).

Återanropsfunktionen bör helt enkelt registrera det nya läget och väcka en väntande tråd för att aktivera det nya tillståndet.

```C
void tx_demo_change_mode_callback(ULONG mode)
{
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

Det lägesvärde som skickas kan ha följande värden.

- UX_OTG_MODE_IDLE
- UX_OTG_MODE_SLAVE
- UX_OTG_MODE_HOST

Programmet kan alltid kontrollera vad enheten är genom att titta på variabeln .

```C
ux_system_otg ->ux_system_otg_device_type
```

Dess värden kan vara något av följande.

- UX_OTG_DEVICE_A
- UX_OTG_DEVICE_B
- UX_OTG_DEVICE_IDLE

En USB OTG-värdenhet kan alltid fråga efter ett rollbyte genom att utfärda kommandot .

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */

ux_host_stack_role_swap(storage ->ux_host_class_storage_device);
```

För en underställt enhet finns det inget kommando att utfärda, men den underrede enheten kan ange ett tillstånd för att ändra rollen, som hämtas av värden när den utfärdar en GET_STATUS och växlingen initieras sedan.

```C
/* We are a B device, ask for role swap. The next GET_STATUS from the host will get the status change and do the HNP. */

ux_system_otg ->ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
