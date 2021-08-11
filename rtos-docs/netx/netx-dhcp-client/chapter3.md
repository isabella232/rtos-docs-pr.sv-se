---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX DHCP-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX DHCP-tjänster (anges nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50902d37f823302910b1b219658dcbf1a41406f480c14795ffceea6e733a0848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799548"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX DHCP-klienttjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX DHCP-tjänster (anges nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- **nx_dhcp_create:** *Skapa en DHCP-instans*

- **nx_dhcp_clear_broadcast_flag:** Rensa broadcast-flaggan för klientmeddelanden

- **nx_dhcp_delete:** Ta *bort en DHCP-instans*

- **nx_dhcp_decline:** Skicka *avböj-meddelande till server*

- **nx_dhcp_force_renew:** Skicka *meddelande om force renew*

- **nx_dhcp_packet_pool_set:** *Ange DHCP-klientens paketpool*

- **nx_dhcp_release:** Skicka *release-meddelande till servern*

- **nx_dhcp_reinitialize: Rensa** *nätverksparametrar för DHCP-klienter*

- **nx_dhcp_request_client_ip:** Ange *en specifik IP-adress*

- **nx_dhcp_send_request:** Skicka *DHCP-meddelande till servern*

- **nx_dhcp_server_address_get:** Hämta *DHCP-klientens DHCP-serveradress*

- **nx_dhcp_set_interface_index:** Ange *klientnätverksgränssnittet*

- **nx_dhcp_start:** *Starta DHCP-bearbetning*

- **nx_dhcp_state_change_notify:** Meddela *tillämpningen av DHCP-tillståndsändring*

- **nx_dhcp_stop:** Stoppa *DHCP-bearbetning*

- **nx_dhcp_user_option_retrieve:** Alternativet *Hämta DHCP*

- **nx_dhcp_user_option_convert:** Konvertera *fyra byte till ULONG*

Gränssnittsspecifika DHCP-klienttjänster:

- **nx_dhcp_interface_clear_broadcast_flag:** Rensa *broadcast-flaggan på klientmeddelanden i angivet gränssnitt*

- **nx_dhcp_interface_enable:** Aktivera *gränssnittet för att köra DHCP på det angivna gränssnittet*

- **nx_dhcp_interface_disable:** Inaktivera *gränssnittet för att köra DHCP på det angivna gränssnittet*

- **nx_dhcp_interface_decline:** *Skicka avböj-meddelande till servern i det angivna gränssnittet*

- **nx_dhcp_interface_force_renew:** Skicka *ett meddelande om force renew i det angivna gränssnittet*

- **nx_dhcp_interface_reinitialize:** Rensa *DHCP-klientnätverksparametrar i det angivna gränssnittet*

- **nx_dhcp_interface_release:** *Skicka release-meddelande till servern i det angivna gränssnittet*

- **nx_dhcp_interface_request_client_ip:** Ange *en specifik IP-adress i det angivna gränssnittet*

- **nx_dhcp_interface_send_request:** *Skicka DHCP-meddelande till servern i det angivna gränssnittet*

- **nx_dhcp_interface_server_address_get:** Hämta *DHCP-serverns IP-adress i det angivna gränssnittet*

- **nx_dhcp_interface_start:** Starta *DHCP-klientbearbetningen på det angivna gränssnittet*

- **nx_dhcp_interface_stop:** *Stoppa bearbetningen av DHCP-klienten i det angivna gränssnittet*

- **nx_dhcp_interface_state_change_notify:** *Ange återanropsfunktionen när DHCP-tillståndet ändras i det angivna gränssnittet*

- **nx_dhcp_interface_user_option_retrieve:** *Hämta det angivna DHCP-alternativet på det angivna gränssnittet*

DHCP-klienttjänster om NX_DHCP_CLIENT_RESORE_STATE har definierats:

- **nx_dhcp_resume:** Återuppta *tidigare etablerat DHCP-klienttillstånd*

- **nx_dhcp_suspend:** *Pausa bearbetningen av DHCP-klienttillståndet*

- **nx_dhcp_client_get_record:** Skapa *en post för DHCP-klienttillståndet*

- **nx_dhcp_client_restore_record:** Återställa *en tidigare sparad post till DHCP-klienten*

- **nx_dhcp_client_update_time_remaining:** *Uppdatera den återstående tiden i det aktuella DHCP-tillståndet*

Gränssnittsspecifika DHCP-klienttjänster om NX_DHCP_CLIENT_RESORE_STATE har definierats:

- **nx_dhcp_client_interface_get_record:** Skapa *en post för DHCP-klienttillståndet på det angivna gränssnittet*

- **nx_dhcp_client_interface_restore_record:** Återställa *en tidigare sparad post till DHCP-klienten i det angivna gränssnittet*

- **nx_dhcp_client_interface_update_time_remaining:** Uppdatera *tiden som återstår i det aktuella DHCP-tillståndet på det angivna gränssnittet*

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Skapa en DHCP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skapar en DHCP-instans för den TIDIGARE skapade IP-instansen. Som standard är det primära gränssnittet aktiverat för att köra DHCP. Namnindata, som inte används i NetX-implementeringen av DHCP-klienten, måste följa RFC 1035-kriterier för värdnamn. Den totala längden får inte överskrida 255 tecken, etiketterna avgränsade med punkter måste börja med en bokstav och sluta med en bokstav eller siffra och får innehålla bindestreck men inga andra icke-alfanumeriska tecken.

Om programmet vill köra DHCP ett annat gränssnitt som är registrerat med IP-instansen (med *nx_ip_interface_attach*) kan programmet anropa *nx_dhcp_set_interface_index* för att köra DHCP på bara det gränssnittet, eller *nx_dhcp_interface_enable* för att köra DHCP på det gränssnittet också. Mer information finns i beskrivningen av dessa tjänster.

> [!NOTE]
> Programmet måste se till att DHCP-klientens paketpoolsnyttolast har stöd för den minsta DHCP-meddelandestorlek som anges av RFC 2131 avsnitt 2 (548 byte DHCP-meddelandedata plus UDP, IP och fysiska ramrubriker för nätverk).

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  
- **ip_ptr** Pekare till IP-instans som skapats tidigare.  
- **name_ptr** Pekare till värdnamnet för DHCP-instansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Dhcp-skapa

- **NX_DHCP_INVALID_NAME** (0xA8) Ogiltigt värdnamn

- **NX_DHCP_INVALID_PAYLOAD** (0x9C) Nyttolasten är för liten för DHCP-meddelande

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

### <a name="allowed-from"></a>Tillåts från

**Trådar,** Initiering

### <a name="example"></a>Exempel

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

Aktivera det angivna gränssnittet för att köra DHCP 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar det angivna gränssnittet för att köra DHCP. Som standard är det primära gränssnittet aktiverat för DHCP-klienten. I det här läget kan DHCP startas på det här gränssnittet antingen genom *att anropa nx_dhcp_interface_start* eller starta DHCP på alla aktiverade gränssnitt *nx_dhcp_start*.

Observera att programmet först måste registrera det här gränssnittet med IP-instansen med *hjälp av nx_ip_interface_attach.*

Dessutom måste det finnas en tillgänglig "post" för DHCP-klientgränssnittet för att lägga till det här gränssnittet i listan över aktiverade gränssnitt. Som standard NX_DHCP_CLIENT_MAX_RECORDS definieras till 1. Ange det här alternativet till det maximala antalet gränssnitt som förväntas köra DHCP-klienten samtidigt. Vanligtvis NX_DHCP_CLIENT_MAX_RECORDS lika med NX_MAX_PHYSICAL_INTERFACES; Men om en enhet har fler fysiska gränssnitt än den förväntar sig att köra DHCP-klienten kan den spara minne genom att ange NX_DHCP_CLIENT_MAX_RECORDS till mindre än det antalet. Det finns ingen en-till-en-mappning av fysiska gränssnitt med DHCP-klientgränssnittsposter.

Skillnaden mellan den här tjänsten *och nx_dhcp_set_interface_index* är att det senare endast anger ett enda gränssnitt för att köra DHCP, medan den här tjänsten helt enkelt lägger till det angivna gränssnittet i listan över klientgränssnitt som är aktiverade för DHCP.

Om du vill inaktivera ett gränssnitt  för DHCP kan programmet anropa nx_dhcp_interface_disable tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  

- **interface_index** Gränssnittsindex för att aktivera DHCP på

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Dhcp-aktiverad

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) Ingen post tillgänglig för ett annat gränssnitt som ska aktiveras för DHCP

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

Inaktivera det angivna gränssnittet för att köra DHCP 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten inaktiverar det angivna gränssnittet för att köra DHCP. Den initierar om DHCP-klienten i det här gränssnittet.

Om du vill starta om DHCP-klienten måste programmet återaktivera gränssnittet med hjälp *nx_dhcp_interface_enable* starta om DHCP genom att *anropa nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  

- **interface_index** Index för gränssnitt för att inaktivera DHCP på

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP-skapa

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

Ange FLAGGAN FÖR DHCP-sändning

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Description

Den här tjänsten anger eller rensar broadcast-flaggan DHCP-meddelandehuvudet för alla gränssnitt som är aktiverade för DHCP. För vissa DHCP-meddelanden (t.ex. DISCOVER) är broadcast-flaggan inställd på broadcast eftersom klienten inte har någon IP-adress.

__clear_flag__


- **NX_TRUE** broadcast-flaggan rensas (unicast-svar för begäran)

- **NX_FALSE** broadcast-flaggan har angetts (begäran om broadcast-svar)

Den här tjänsten är avsedd för DHCP-klienter som måste gå via en router för att komma till DHCP-servern, där routern avvisar vidarebefordran av broadcast-meddelanden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock  

- **clear_flag** Värde för att ange broadcast-flaggan till

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Sändningsflaggan har uppdaterats

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Ange eller rensa broadcast-flaggan i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Description

Med den här tjänsten kan DHCP-klientens värdprogram ange eller rensa broadcast-flaggan i DHCP-klientmeddelanden till DHCP-servern på det angivna gränssnittet. Mer information finns **i nx_dhcp_clear_broadcast_flag**

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock

- **interface_index** Index för gränssnitt för att ange broadcast-flaggan  

- **clear_flag** Värde för att ange broadcast-flaggan till

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Sändningsflaggan har uppdaterats

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

Ta bort en DHCP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad DHCP-instans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DHCP-borttagning.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Skicka ett meddelande om force renew 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Med den här tjänsten kan värdprogrammet skicka ett force renew-meddelande för alla gränssnitt som är aktiverade för DHCP. DHCP-klienten måste vara i ETT BOUND-tillstånd. Den här funktionen anger tillståndet RENEW så att DHCP-klienten försöker förnya innan T1-tidsgränsen går ut.

Om du vill skicka en force renew på ett specifikt gränssnitt när flera gränssnitt är DHCP-aktiverade använder *du nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Force renew har skickats.  

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

Skicka ett meddelande om tvingad förnyelse i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Description

Med den här tjänsten kan värdprogrammet skicka ett meddelande om force renew i indatagränssnittet så länge som gränssnittet har aktiverats för DHCP (se *nx_dhcp_interface_enable*). DHCP-klienten på det angivna gränssnittet måste vara i ETT BOUND-tillstånd. Den här funktionen anger tillståndet RENEW så att DHCP-klienten försöker förnya innan T1-tidsgränsen går ut.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Force renew har skickats.  

- **NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

Ange DHCP-klientens paketpool

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Description

Med den här tjänsten kan programmet skapa DHCP-klientens paketpool genom att skicka en pekare till en tidigare skapad paketpool i det här tjänstsamtalet. Om du vill använda den här funktionen måste värdprogrammet definiera NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. När den *definieras nx_dhcp_create* tjänsten inte klientens paketpool. Observera att programmet rekommenderas att använda standardvärdena för DHCP-klientens paketpoolsnyttolast, som definieras som NX_DHCP_PACKET_PAYLOAD i *nx_dhcp.h när* paketpoolen skapas.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  

- **packet_pool_ptr** Pekare till paketpool som skapats tidigare

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP-klientpaketpool har angetts

- **NX_NOT_ENABLED** (0x14)-tjänsten är inte aktiverad

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_DHCP_INVALID_PAYLOAD (0x9C) Nyttolasten är för liten

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

Ange begärd IP-adress för DHCP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Description

Den här tjänsten anger IP-adressen för DHCP-klienten att begära från DHCP-servern på det första gränssnittet som är aktiverat för DHCP i DHCP-klientposten. Om *skip_discover_message* har angetts hoppar DHCP-klienten över meddelandet Identifiera och skickar ett meddelande om begäran.

Om du vill ange begäran för en specifik IP-adress för DHCP-meddelanden i ett visst *gränssnitt* använder nx_dhcp_interface_request_client_ip tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  

- **client_ip_address** IP-adress att begära från DHCP-server

- **skip_discover_message** Om sant skickar DHCP-klienten ett meddelande om begäran  
Om det är falskt skickas meddelandet Identifiera.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Begärd IP-adress har angetts.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt
 
### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

Ange begärd IP-adress för DHCP-instans på angivet gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Description

Den här tjänsten anger IP-adressen för DHCP-klienten att begära från DHCP-servern på det angivna gränssnittet, om det gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*). Om *skip_discover_message* har angetts hoppar DHCP-klienten över meddelandet Identifiera och skickar ett meddelande om begäran.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.

- **Interface_index** Index för gränssnitt för att begära IP-adress på

- **client_ip_address** IP-adress att begära från DHCP-server

- **skip_discover_message** Om sant skickar DHCP-klienten ett meddelande om begäran. annars skickas meddelandet Identifiera.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Begärd IP-adress har angetts.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig IP- eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt


### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

Rensa nätverksparametrarna för DHCP-klienten 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar värdprogrammets nätverksparametrar (IP-adress, nätverksadress och nätverksmask) och rensar DHCP-klienttillståndet på alla gränssnitt som är aktiverade för DHCP. Det används i kombination med *nx_dhcp_stop* och nx_dhcp_start *för att* "starta om" DHCP-tillståndsdatorn: 

nx_dhcp_stop(&my_dhcp);  
nx_dhcp_reinitialize(&my_dhcp);  
nx_dhcp_start(&my_dhcp);


Om du vill initiera om DHCP-klienten på ett visst gränssnitt när  flera gränssnitt är aktiverade för DHCP använder du nx_dhcp_interface_reinitialize tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP initieras om 

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

Rensa NÄTVERKSparametrarna för DHCP-klienten i det angivna gränssnittet 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten rensar nätverksparametrarna (IP-adress, nätverksadress och nätverksmask) på det angivna gränssnittet om det gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*). Se *nx_dhcp_reinitialize* för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till dhcp-instans som skapats tidigare

- **interface_index** Index för gränssnitt som ska initieras om.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** -gränssnittet (0x00) har initierats om

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

Frigöra hyrd IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten släpper IP-adressen som hämtas från en DHCP-server genom att skicka RELEASE-meddelandet till den servern. Den initierar sedan om DHCP-klienten. Den här tjänsten tillämpas på alla gränssnitt som är aktiverade för DHCP.

Programmet kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.

Om du vill frigöra en adress tillbaka till DHCP-servern i ett visst gränssnitt använder *du nx_dhcp_interface_release tjänsten*

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DHCP-version.  

- **NX_DHCP_NOT_BOUND** (0x94) IP-adressen har inte hyrts så att den inte kan släppas.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

Frigöra IP-adress i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten släpper IP-adressen som hämtas från en DHCP-server i det angivna gränssnittet och initierar om DHCP-klienten. DHCP-klienten kan startas om genom att anropa *nx_dhcp_start*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DHCP-version.

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- **NX_DHCP_NOT_BOUND** (0x94) IP-adressen har inte hyrts så att den inte kan släppas.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

Neka IP-adress från DHCP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten nekar en IP-adress som leasas från DHCP-servern på alla gränssnitt som är aktiverade för DHCP. Om NX_DHCP_CLIENT_ SEND_ ARP_PROBE har definierats skickar DHCP-klienten ett NEKA-meddelande om den upptäcker att IP-adressen redan används. Se **ARP-avsökningar i** kapitel ett för mer information om konfiguration av ARP-avsökning i NetX DHCP-klienten.

Programmet kan använda den här tjänsten för att neka sin IP-adress om det upptäcker att adressen används på annat sätt.

Den här tjänsten initierar om DHCP-klienten så att den kan startas om genom att anropa *nx_dhcp_start*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Avböj har skickats  

- **NX_DHCP_NOT_STARTED** (0x96) DHCP-instansen startades inte

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

Neka IP-adress från DHCP-server i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten skickar AVBÖJ-meddelandet till servern för att neka en IP-adress som tilldelats av DHCP-servern. Den initierar även om DHCP-klienten. Mer *nx_dhcp_decline* finns i nx_dhcp_decline.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

- **Interface_index** Index för gränssnitt för att neka IP-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP-avböjning skickas  

- **NX_DHCP_NOT_BOUND** (0x94) DHCP-klient som inte är bunden

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

Skicka DHCP-meddelande till server

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Description

Den här tjänsten skickar det angivna DHCP-meddelandet till DHCP-servern i det första gränssnittet som är aktiverat för DHCP som finns i DHCP-klientposten. Om du vill skicka ett RELEASE- eller *DECLINE-meddelande måste programmet använda nx_dhcp-tjänsterna [_interface]_release*() respektive *nx_dhcp_interface_decline().*

DHCP-klienten måste startas för att använda den här tjänsten förutom för att skicka INFORM_REQUEST-meddelandetypen.

> [!NOTE] 
> Den här tjänsten är inte avsedd för värdprogrammet att "köra" DHCP-klienttillståndsdatorn.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  

- **dhcp_message_type** Meddelandebegäran (definieras *i nx_dhcp.h*)

### <a name="return-values"></a>Returvärden

- **DHCP NX_SUCCESS meddelande** (0x00) skickas  

- **NX_DHCP_NOT_STARTED** (0x96) Ogiltigt gränssnittsindex

- **NX_DHCP_INVALID_MESSAGE** (0x9B) Ogiltig meddelandetyp att skicka

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Skicka DHCP-meddelande till server i ett specifikt gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett meddelande till DHCP-servern på det angivna gränssnittet om gränssnittet är aktiverat för DHCP. Om du vill skicka ett RELEASE- eller *DECLINE-meddelande måste programmet använda nx_dhcp-tjänsterna [_interface]_release*() respektive *nx_dhcp_interface_decline().*

DHCP-klienten måste startas för att använda den här tjänsten förutom för att skicka meddelandetypen DHCP INFORM REQUEST.

Den här tjänsten är inte avsedd för värdprogrammet att "köra" DHCP-klienttillståndsdatorn.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.

- **Interface_index** Index för gränssnitt för att skicka meddelande på  

- **dhcp_message_type** Meddelandebegäran (definieras *i nx_dhcp.h*)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP-meddelande som skickats  

- **NX_DHCP_NOT_STARTED** (0x96) Ogiltigt gränssnittsindex

- **NX_DHCP_INVALID_MESSAGE** (0x9B) Ogiltig meddelandetyp att skicka

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Gränssnitt inte aktiverat för DHCP

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

Hämta DHCP-klientens IP-adress för DHCP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Description

Den här tjänsten hämtar DHCP-klientens DHCP-serverns IP-adress i det första gränssnittet som är aktiverat för DHCP som finns i DHCP-klientposten. Anroparen kan bara använda den här tjänsten när DHCP-klienten är bunden till en IP-adress som tilldelats av DHCP-servern. Värdprogrammet kan använda *tjänsten nx_ip_status_check* för att verifiera att IP-adressen  har angetts, eller så kan det använda nx_dhcp_state_change_notify och fråga DHCP-klienttillståndet är NX_DHCP_STATE_BOUND. Se *nx_dhcp_state_change_notify* mer information om hur du ställer in återanropsfunktionen för tillståndsändring.

Om du vill hitta DHCP-servern på ett specifikt gränssnitt när flera gränssnitt är aktiverade för DHCP-klienten använder *du nx_dhcp_interface_server_address_get tjänsten*

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.

- **server_address** Pekare till serverns IP-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP-serveradress returnerad

- NX_PTR_ERROR (0x16) Ogiltig pekare för indata

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

Hämta DHCP-klientens DHCP-serverns IP-adress i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Description

Den här tjänsten hämtar DHCP-klientens DHCP-serverns IP-adress i det angivna gränssnittet om gränssnittet är aktiverat för DHCP. DHCP-klienten måste vara i bunden tillstånd. När du har börjat DHCP-klienten i det gränssnittet kan värdprogrammet antingen använda *nx_ip_status_check-tjänsten* för att verifiera att IP-adressen har angetts, eller så kan det använda DHCP-klienttillståndet för att ändra återanrop och fråga DHCP-klienttillståndet NX_DHCP_STATE_BOUND. Se *nx_dhcp_state_change_notify* mer information om hur du ställer in återanropsfunktionen för tillståndsändring.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.

- **Interface_index** Index för gränssnitt för att hämta IP-adress  

- **server_address** Pekare till serverns IP-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DHCP-serveradress returnerad

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Inga gränssnitt har aktiverats för DHCP

- **NX_DHCP_NOT_BOUND** (0x94) DHCP-klient som inte är bunden

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

Ange nätverksgränssnitt för DHCP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Description

Den här tjänsten anger nätverksgränssnittet för DHCP-instansen att ansluta till DHCP-servern när DHCP-klienten körs som konfigurerats för ett enda nätverksgränssnitt.

Som standard körs DHCP-klienten i det primära gränssnittet. Om du vill köra DHCP på en sekundär tjänst använder du den här tjänsten för att ange det sekundära gränssnittet som DHCP-klientgränssnitt. Programmet måste tidigare registrera det angivna gränssnittet  till IP-instansen med hjälp av nx_ip_interface_attach tjänsten.

Observera att den här tjänsten är avsedd för program som avser att köra DHCP-klienten på endast ett gränssnitt. Om du vill köra DHCP på flera gränssnitt *nx_dhcp_interface_enable* mer information.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontrollblock.  

- **index** Index för enhetens nätverksgränssnitt

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) har angetts.

- **NX_INVALID_INTERFACE** (0x4C) Ogiltigt nätverksgränssnitt

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) aktiverat för DHCP

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) Ingen post tillgänglig för en annan

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

Starta DHCP-bearbetning

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar DHCP-bearbetning på alla gränssnitt som är aktiverade för DHCP. Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*

Om du vill kontrollera när IP-instansen är bunden till en *IP-adress* i DHCP-klientgränssnittet använder du nx_ip_status_check för att se om IP-adressen är giltig.

Om det finns andra gränssnitt som redan kör DHCP påverkar inte den här tjänsten dem.

Om du vill starta DHCP på ett visst gränssnitt när flera gränssnitt är aktiverade använder *du nx_dhcp_interface_start tjänsten.*

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till dhcp-instans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DHCP-start.  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP har redan startats.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

Starta DHCP-bearbetning på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten startar DHCP-bearbetning på det angivna gränssnittet om det gränssnittet är aktiverat för DHCP. Se *nx_dhcp_interface_enable*() för mer information om hur du aktiverar ett gränssnitt för DHCP. Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*

Om det inte finns några andra gränssnitt som kör DHCP-klienten startar/återupptar tjänsten DHCP-klienttråden och (åter)aktiverar DHCP-klientens timer.  
  
Programmet bör använda nx_ip_status_check *för* att kontrollera om en IP-adress hämtas.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

- **Interface_index** Index som DHCP-klienten ska startas på

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DHCP-start.  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP-instansen har redan startats.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

Ange funktionen för återanrop i DHCP-tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Description

Den här tjänsten registrerar den angivna återanropsfunktionen dhcp_state_change_notify för att meddela en tillämpning av DHCP-tillståndsändringar. Återanropsfunktionen tillhandahåller det tillstånd som DHCP-klienten har övergåt till.

Här följer värden som är associerade med de olika DHCP-tillstånden:

| Tillstånd                             | Värde |
|-----------------------------------|-------|
| NX \_ \_ DHCP-TILLSTÅNDSSTART \_             | 1     |
| NX \_ \_ DHCP-TILLSTÅND \_ INIT             | 2     |
| VÄLJ NX \_ \_ \_ DHCP-TILLSTÅND        | 3     |
| BEGÄRAN OM NX \_ \_ \_ DHCP-TILLSTÅND       | 4     |
| NX \_ \_ DHCP-TILLSTÅNDSBUNDEN \_            | 5     |
| FÖRNYA NX \_ \_ \_ DHCP-TILLSTÅND         | 6     |
| NX \_ \_ DHCP-TILLSTÅNDSREBINDING \_        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| AVSÖKNING \_ AV NX \_ \_ \_ DHCP-TILLSTÅNDSADRESS | 9     |


### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

- **dhcp_state_change_notify** Pekare för återanropsfunktionen för tillståndsändring

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad motringning.  

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

Ange funktionen för återanrop av DHCP-tillstånd i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>Description

Den här tjänsten registrerar den angivna återanropsfunktionen för att meddela en tillämpning av DHCP-tillståndsändringar. Motringningsargumenten för funciton är gränssnittsindexet och det tillstånd som DHCP-klienten har övergåt till i det gränssnittet.

Mer information om tillståndsändringsfunktioner finns i *nx_dhcp_state_change_notify*().

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

- **dhcp_interface_state_change_notify** Funktions pekare för återanrop av program

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad motringning.  

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

Stoppar DHCP-bearbetning

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar DHCP-bearbetning på alla gränssnitt som har startat DHCP-bearbetning. Om det inte finns några gränssnitt som bearbetar DHCP inaktiverar den här tjänsten DHCP-klienttråden och inaktiverar TIMERN för DHCP-klienten.

Om du vill stoppa DHCP på ett specifikt gränssnitt  om flera gränssnitt är aktiverade för DHCP använder du nx_dhcp_interface_stop tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Dhcp-stopp

- **NX_DHCP_NOT_STARTED** (0x96) DHCP-instansen startades inte.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Stoppa DHCP-bearbetning i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Description

Den här tjänsten stoppar DHCP-bearbetningen på det angivna gränssnittet om DHCP redan har startats. Om det inte finns några andra gränssnitt som kör DHCP inaktiveras DHCP-tråden och timern.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till en TIDIGARE skapad DHCP-instans.

- **Interface_index** Gränssnitt som DHCP-bearbetningen ska stoppas på

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Dhcp-stopp

- **NX_DHCP_NOT_STARTED** (0x96) DHCP har inte startats.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

Hämta ett DHCP-alternativ från senaste serversvar

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det angivna DHCP-alternativet från DHCP-alternativbufferten i det första gränssnittet som är aktiverat för DHCP som finns på DHCP-klientposten. Om det lyckas kopieras alternativdata till den angivna bufferten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till dhcp-instans som skapats tidigare.  

- **request_option** DHCP-alternativet, enligt vad som anges av RFC:erna. Se NX_DHCP_OPTION i *nx_dhcp.h*.

- **destination_ptr** Pekare till målet för svarssträngen.  

- **destination_size** Pekare till storleken på målet och vid retur, målet för att placera det antal byte som returneras.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad alternativhämtning.  

- **NX_DHCP_NOT_BOUND** (0x94) DHCP-klient som inte är bunden.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Inga gränssnitt har aktiverats för DHCP

- **NX_DHCP_DEST_TO_SMALL** (0x95) Målet är för litet för att innehålla svar.

- **NX_DHCP_PARSE_ERROR** (0x97) DHCP-alternativet hittades inte i serversvaret.

- NX_PTR_ERROR (0x16) Ogiltig indatapekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

Hämta ett DHCP-alternativ från det senaste serversvaret på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det angivna DHCP-alternativet från DHCP-alternativbufferten i det angivna gränssnittet, om gränssnittet är aktiverat för DHCP. Om det lyckas kopieras alternativdata till den angivna bufferten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till dhcp-instans som skapats tidigare.

- **Interface_index** Index som du vill hämta det angivna alternativet för  

- **request_option** DHCP-alternativet, enligt vad som anges av RFC:erna. Se NX_DHCP_OPTION i *nx_dhcp.h*.  

- **destination_ptr** Pekare till målet för svarssträngen.  

- **destination_size** Pekare till storleken på målet och vid retur, målet för att placera det antal byte som returneras.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad alternativhämtning.  

- **NX_DHCP_NOT_BOUND** (0x94) IP-adress som inte har tilldelats

- **NX_DHCP_DEST_TO_SMALL** (0x95) bufferten är för liten

- **NX_DHCP_PARSE_ERROR** (0x97) DHCP-alternativet hittades inte i serversvaret.

- NX_PTR_ERROR (0x16) Ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare av tjänsten.

- NX_INVALID_INTERFACE (0x4C) Ogiltigt nätverksgränssnitt

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

Konvertera fyra byte till ULONG

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>Description

Den här tjänsten konverterar de fyra tecken som "option_string_ptr" pekar på till ett osignerat långt värde. Det är särskilt användbart när det finns IP-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **option_string_ptr** Pekare till tidigare hämtad alternativsträng.

### <a name="return-values"></a>Returvärden

- **Värde** Värdet för de första fyra byteen.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

Ange återanropsfunktion för att lägga till alternativ som användaren anger

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>Description

Den här tjänsten registrerar den angivna återanropsfunktionen för att lägga till alternativ som användaren anger.

Om återanropsfunktionen anges kan programmen lägga till alternativ som användaren anger i paketet genom att iface_index och message_type.

> [!NOTE]
> I användarens rutin. Program måste följa FORMATET DHCP-alternativ när du lägger till alternativ som användaren har angett. Den totala storleken på användaralternativen måste vara mindre eller lika med user_option_length och uppdatera user_option_length som verklig alternativlängd. Returnera NX_TRUE lägg till alternativ, annars returneras NX_FALSE.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till dhcp-instans som skapats tidigare.

- **dhcp_user_option_add** Pekare till användaralternativet Lägg till funktion.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad motringning.

- NX_PTR_ERROR (0x16) Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
