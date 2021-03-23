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
# <a name="chapter-5---usbx-otg"></a>Kapitel 5 – USBX OTG

USBX stöder OTG-funktionerna i USB när en OTG-kompatibel USB-styrenhet är tillgänglig i maskin varu designen.

USBX stöder OTG i kärn USB-stacken. Men för att OTG ska fungera krävs en speciell USB-styrenhet. USBX OTG Controller-funktioner finns i usbx_otg-katalogen. Den aktuella USBX-versionen stöder bara NXP-LPC3131 med fullständiga OTG-funktioner.

Driv rutins funktionerna för vanliga kontrollanter (värd eller enhet) finns fortfarande i standard-USBX usbx_device_controllers och usbx_host_controllers, men usbx_otg katalogen innehåller de speciella OTG-funktioner som är associerade med USB-styrenheten.

Det finns fyra funktions kategorier för en OTG-styrenhet Förutom vanliga funktioner för värd/enhet.

- VBUS-/regionsspecifika funktioner
- Starta och stoppa styrenheten
- USB-roll hanterare
- Avbrotts hanterare

## <a name="vbus-functions"></a>VBUS-funktioner

Varje kontrollant måste ha en VBUS-ansvarig för att ändra status för VBUS baserat på energispar funktioner. Den här funktionen utför vanligt vis bara att aktivera eller inaktivera VBUS.

## <a name="start-and-stop-the-controller"></a>Starta och stoppa styrenheten

Till skillnad från en vanlig USB-implementering kräver OTG att värden och/eller enhets stacken aktive ras och inaktive ras när rollen ändras.

## <a name="usb-role-manager"></a>USB-roll hanterare

USB-rolltjänsten tar emot kommandon för att ändra status för USB-filen. Det finns flera tillstånd som behöver över gångar till och från:

| Tillstånd                    | Värde | Beskrivning                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | Enheten är inaktiv. Inte ansluten till något |
| UX_OTG_IDLE_TO_HOST  | 1     | Enheten är ansluten med typen anslutning             |
| UX_OTG_IDLE_TO_SLAVE | 2     | Enheten är ansluten med typ B-anslutning             |
| UX_OTG_HOST_TO_IDLE  | 3     | Värd enheten har kopplats från                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Roll växling från värd till slav                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | Slaven het är frånkopplad                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Roll växling från slav till värd                          |

## <a name="interrupt-handlers"></a>Avbrotts hanterare

Både värd-och enhets styrenhetens driv rutiner för OTG kräver olika avbrotts hanterare för att övervaka signaler bortom traditionella USB-avbrott, särskilt signaler på grund av enhets-och VBUS.

Initiera en USB-OTG kontrollant. Vi använder NXP-LPC3131 som ett exempel här.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

I det här exemplet initierar vi LPC3131 i OTG-läge genom att skicka en VBUS-funktion och en motringning för läges ändring (från värd till slav eller vice versa).

Funktionen motringning ska bara registrera det nya läget och aktivera en väntande tråd för att skapa det nya läget.

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

Läge svärdet som skickas kan ha följande värden.

- **UX_OTG_MODE_IDLE**
- **UX_OTG_MODE_SLAVE**
- **UX_OTG_MODE_HOST**

Programmet kan alltid kontrol lera vad enheten är genom att titta på variabeln:

```C
_ux_system_otg -> ux_system_otg_device_type
```

Dess värden kan vara något av följande.

- **UX_OTG_DEVICE_A**
- **UX_OTG_DEVICE_B**
- **UX_OTG_DEVICE_IDLE**

En USB-OTG kan alltid fråga efter en roll växling genom att utfärda följande kommando.

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

För en slav enhet finns det inget kommando att utfärda, men den sekundära enheten kan ange ett tillstånd för att ändra rollen, som kommer att hämtas av värden när den utfärdar en **GET_STATUS** och växlingen initieras.

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
