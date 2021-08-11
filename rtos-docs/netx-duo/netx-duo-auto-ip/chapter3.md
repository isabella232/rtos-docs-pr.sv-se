---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX Duo AutoIP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo AutoIP-tjänster (anges nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82a186505104983dbe6964f92e89c8e775d545eedb6495e27f21542d7660bf42
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791201"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX Duo AutoIP-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo AutoIP-tjänster (anges nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- **nx_auto_ip_create:** Skapa *en AutoIP-instans*
- **nx_auto_ip_delete:** Ta *bort AutoIP-instans*
- **nx_auto_ip_get_address:** Hämta *aktuell AutoIP-adress*
- **nx_auto_ip_set_interface:** Ange *IP-gränssnitt som behöver en AutoIP-adress*
- **nx_auto_ip_start:** Starta *automatiskIP-bearbetning*
- **nx_auto_ip_stop:** Stoppa *automatiskIP-bearbetning*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Skapa En AutoIP-instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a>Description

Den här tjänsten skapar en AutoIP-instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr:** Pekare till AutoIP-kontrollblock.
- **name**: Namnet på AutoIP-instansen.
- **ip_ptr:** Pekare till IP-instans.
- **stack_ptr:** Pekare till Området AutoIP-trådstack.
- **stack_size:** Storleken på området för AutoIP-trådstacken.
- **prioritet:** Prioritet för AutoIP-tråden.

> [!NOTE]
> Om DHCP används måste DHCP-tråden ha högre prioritet än IP-instanstråden och AutoIP-tråden.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Skapa automatiskt.
- **NX_AUTO_IP_ERROR:**(0xA00) Fel vid automatiskIP- skapas.
- NX_PTR_ERROR: (0x16) Ogiltig AutoIP, ip_ptr eller stackpekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad AutoIP-instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr:** Pekare till AutoIP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS:**(0x00) Lyckad autoIP-borttagning.
- **NX_AUTO_IP_ERROR:**(0xA00) AutoIP-borttagningsfel.
- NX_PTR_ERROR: (0x16) Ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten hämtar den autoIP-adress som är konfigurerad för tillfället. Om det inte finns någon returneras IP-adressen 0.0.0.0.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr:** Pekare till AutoIP-kontrollblock.
- **local_ip_address:** Mål för avsändar-IP-adress.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad AutoIP-adress hämta.
- **NX_AUTO_IP_NO_LOCAL**: (0xA01) Ingen giltig AutoIP-adress.
- NX_PTR_ERROR: (0x16) Ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, timers, trådar, ISR

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

Ange nätverksgränssnitt för AutoIP

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten anger indexet för nätverksgränssnittet som AutoIP kommer att söka efter en IP-adress för nätverket. Standardvärdet är noll (det primära nätverksgränssnittet). Gäller endast för enheter med flera startenheter.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr:** Pekare till AutoIP-kontrollblock.
- **interface_index: Gränssnitt** för avsökning av IP-adress för

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad AutoIP-gränssnittsuppsättning
- **NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Ogiltig NX_PTR_ERROR (0x16) Ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Initiering, timers, trådar, ISR

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

Starta automatiskIP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Description

Den här tjänsten startar AutoIP-protokollet på en tidigare skapad AutoIP-instans.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr:** Pekare till AutoIP-kontrollblock.
- **starting_local_address:** Valfri Startadress för AutoIP. Värdet IP_ADDRESS(0,0,0,0) anger att en slumpmässig AutoIP-adress ska härledas. Annars försöker NetX AutoIP tilldela den adressen om en giltig AutoIP-adress anges.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckad AutoIP-start.
- **NX_AUTO_IP_ERROR:**(0xA00) AutoIP-startfel.
- NX_PTR_ERROR: (0x16) Ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

Stoppa automatiskIP-bearbetning

### <a name="prototype"></a>Prototyp

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar AutoIP-protokollet på en tidigare skapad och startad AutoIP-instans. Den här tjänsten används vanligtvis när IP-adressen ändras via DHCP eller manuellt till en icke-AutoIP-adress.

### <a name="input-parameters"></a>Indataparametrar

- **auto_ip_ptr:** Pekare till AutoIP-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**: (0x00) Lyckat autoIP-stopp.
- **NX_AUTO_IP_ERROR:**(0xA00) AutoIP-stoppfel.
- NX_PTR_ERROR: (0x16) Ogiltig AutoIP-pekare.
- NX_CALLER_ERROR: (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>Se även

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start