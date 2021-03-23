---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo AutoIP Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo AutoIP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826166"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo AutoIP Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo AutoIP-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_auto_ip_create**: *skapa AutoIP-instans*
- **nx_auto_ip_delete**: *ta bort AutoIP-instans*
- **nx_auto_ip_get_address**: *Hämta aktuell AutoIP-adress*
- **nx_auto_ip_set_interface**: *Ange IP-gränssnitt som behöver en AutoIP-adress*
- **nx_auto_ip_start**: *Starta AutoIP-bearbetning*
- **nx_auto_ip_stop**: *stoppa AutoIP-bearbetning*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Skapa AutoIP-instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en AutoIP-instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr**: pekare till AutoIP Control Block.
- **namn**: namnet på AutoIP-instansen.
- **ip_ptr**: pekare till IP-instans.
- **stack_ptr**: pekar på AutoIP tråds tack yta.
- **stack_size**: storleken på AutoIP trådens stack Area.
- **prioritet**: prioriteten för AutoIP-tråden.

> [!NOTE]
> Om DHCP används måste DHCP-tråden ha högre prioritet än IP-instansen och AutoIP-tråden.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades skapa AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP skapa fel.
- NX_PTR_ERROR: (0x16) ogiltig AutoIP, ip_ptr eller stack pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>Se även

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

Ta bort AutoIP-instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad AutoIP-instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr**: pekare till AutoIP Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad AutoIP-borttagning.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP Delete-fel.
- NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>Se även

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

Hämta aktuell AutoIP-adress

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den aktuella AutoIP-adressen. Om det inte finns någon returneras en IP-adress 0.0.0.0.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr**: pekare till AutoIP Control Block.
- **local_ip_address**: målet för retur-IP-adressen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad AutoIP-adress Hämta.
- **NX_AUTO_IP_NO_LOCAL**: (0XA01) ingen giltig AutoIP-adress.
- NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, timers, trådar, ISR: er

### <a name="example"></a>Exempel

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>Se även

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

Ange nätverks gränssnitt för AutoIP

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger index för nätverks gränssnittets AutoIP som avsöker en IP-adress för nätverket. Standardvärdet är noll (det primära nätverks gränssnittet). Gäller endast för multihomed-enheter.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr**: pekare till AutoIP Control Block.
- **interface_index**: gränssnitt till avsökning av IP-adress för

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad AutoIP-gränssnitts uppsättning
- **NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0XA02) ogiltigt nätverks gränssnitt NX_PTR_ERROR (0X16) ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, timers, trådar, ISR: er

### <a name="example"></a>Exempel

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a>Se även

nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

Starta AutoIP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar AutoIP-protokollet på en tidigare skapad AutoIP-instans.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr**: pekare till AutoIP Control Block.
- **starting_local_address**: valfri start adress för AutoIP. Värdet IP_ADDRESS (0, 0, 0) anger att en slumpmässig AutoIP-adress ska härledas. Annars, om en giltig AutoIP-adress har angetts försöker NetX AutoIP tilldela adressen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades AutoIP-start.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP start fel.
- NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>Se även

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

Stoppa AutoIP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar AutoIP-protokollet på en tidigare skapad och startad AutoIP-instans. Den här tjänsten används vanligt vis när IP-adressen ändras via DHCP eller manuellt till en icke-AutoIP adress.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr**: pekare till AutoIP Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades AutoIP-stopp.
- **NX_AUTO_IP_ERROR**: (0XA00) AutoIP Stop-fel.
- NX_PTR_ERROR: (0x16) ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>Se även

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start