---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DHCP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826796"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX DHCP Client Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DHCP-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_dhcp_create**: *skapa en DHCP-instans*

- **nx_dhcp_clear_broadcast_flag**: Rensa sändnings flagga på klient meddelanden

- **nx_dhcp_delete**: *ta bort en DHCP-instans*

- **nx_dhcp_decline**: skicka *neka meddelande till Server*

- **nx_dhcp_force_renew**: *Skicka framtvinga förnyelse av meddelande*

- **nx_dhcp_packet_pool_set**: *ange DHCP-klient paketets adresspool*

- **nx_dhcp_release**: Skicka ett *release-meddelande till servern*

- **nx_dhcp_reinitialize**: *ta bort nätverks parametrar för DHCP-klienter*

- **nx_dhcp_request_client_ip**: *Ange en speciell IP-adress*

- **nx_dhcp_send_request**: *Skicka DHCP-meddelande till Server*

- **nx_dhcp_server_address_get**: *Hämta DHCP-klientens DHCP-serveradress*

- **nx_dhcp_set_interface_index**: *Ange klient nätverks gränssnittet*

- **nx_dhcp_start**: *Starta DHCP-bearbetning*

- **nx_dhcp_state_change_notify**: *meddela programmet om ändring av DHCP-tillstånd*

- **nx_dhcp_stop**: *stoppa DHCP-bearbetning*

- **nx_dhcp_user_option_retrieve**: *Hämta DHCP-alternativ*

- **nx_dhcp_user_option_convert**: *konvertera fyra byte till ulong*

Gränssnitt för vissa DHCP-klient tjänster:

- **nx_dhcp_interface_clear_broadcast_flag**: *Rensa sändnings flagga på klient meddelanden i angivet gränssnitt*

- **nx_dhcp_interface_enable**: *Aktivera gränssnitt för att köra DHCP på det angivna gränssnittet*

- **nx_dhcp_interface_disable**: *inaktivera gränssnittet för att köra DHCP på det angivna gränssnittet*

- **nx_dhcp_interface_decline**: *Skicka neka meddelande till server på det angivna gränssnittet*

- **nx_dhcp_interface_force_renew**: *Skicka ett Force renew-meddelande på det angivna gränssnittet*

- **nx_dhcp_interface_reinitialize**: *ta bort nätverks parametrar för DHCP-klienter på det angivna gränssnittet*

- **nx_dhcp_interface_release**: *Skicka ett release-meddelande till servern på det angivna gränssnittet*

- **nx_dhcp_interface_request_client_ip**: *Ange en specifik IP-adress för det angivna gränssnittet*

- **nx_dhcp_interface_send_request**: *Skicka DHCP-meddelande till servern på det angivna gränssnittet*

- **nx_dhcp_interface_server_address_get**: *Hämta IP-adressen för DHCP-servern på det angivna gränssnittet*

- **nx_dhcp_interface_start**: *Starta DHCP-klient bearbetningen på det angivna gränssnittet*

- **nx_dhcp_interface_stop**: *stoppa DHCP-klientens bearbetning på det angivna gränssnittet*

- **nx_dhcp_interface_state_change_notify**: *Ange callback-funktionen när DHCP-tillstånd ändras på det angivna gränssnittet*

- **nx_dhcp_interface_user_option_retrieve**: *Hämta det angivna DHCP-alternativet på det angivna gränssnittet*

DHCP-klienttjänster om NX_DHCP_CLIENT_RESORE_STATE definieras:

- **nx_dhcp_resume**: *återuppta tidigare upprättat DHCP-klient tillstånd*

- **nx_dhcp_suspend**: *pausa bearbetningen av DHCP-klientens tillstånd*

- **nx_dhcp_client_get_record**: *skapa en post för DHCP-klientens tillstånd*

- **nx_dhcp_client_restore_record**: *återställa en tidigare sparad post till DHCP-klienten*

- **nx_dhcp_client_update_time_remaining**: *Uppdatera tiden som återstår i det aktuella DHCP-läget*

Gränssnitt för klient tjänster för DHCP om NX_DHCP_CLIENT_RESORE_STATE definieras:

- **nx_dhcp_client_interface_get_record**: *skapa en post av DHCP-klientens tillstånd på det angivna gränssnittet*

- **nx_dhcp_client_interface_restore_record**: *Återställ en tidigare sparad post till DHCP-klienten på det angivna gränssnittet*

- **nx_dhcp_client_interface_update_time_remaining**: *Uppdatera tiden som återstår i det aktuella DHCP-läget på det angivna gränssnittet*

## <a name="nx_dhcp_create"></a>nx_dhcp_create

Skapa en DHCP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en DHCP-instans för den tidigare skapade IP-instansen. Som standard är det primära gränssnittet aktiverat för att köra DHCP. Inmatade namn, men som inte används i NetX-implementeringen av DHCP-klienten, måste följa RFC 1035-kriterier för värdnamn. Den totala längden får inte överskrida 255 tecken, etiketter åtskilda av punkter måste börja med en bokstav och sluta med en bokstav eller siffra och får innehålla bindestreck, men inte andra icke-alfanumeriska tecken.

Om programmet vill köra ett annat gränssnitt som registrerats med IP-instansen (med *nx_ip_interface_attach*) kan programmet anropa *nx_dhcp_set_interface_index* för att köra DHCP på bara det gränssnittet, eller *nx_dhcp_interface_enable* för att köra DHCP på det gränssnittet också. Mer information finns i Beskrivning av dessa tjänster.

> [!NOTE]
> Programmet måste se till att nytto lasten i DHCP-adresspoolen har stöd för den minsta storleken för DHCP-meddelanden som anges i RFC 2131 avsnitt 2 (548 byte av DHCP-meddelande data samt UDP, IP och fysiska nätverks ram rubriker).

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  
- **ip_ptr** Pekare till den tidigare skapade IP-instansen.  
- **name_ptr** Pekare till värd namnet för DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-skapande har slutförts

- **NX_DHCP_INVALID_NAME** (0XA8) ogiltigt värdnamn

- **NX_DHCP_INVALID_PAYLOAD** (0X9C) nytto lasten är för liten för DHCP-meddelande

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

### <a name="allowed-from"></a>Tillåten från

**Trådar,** Initialisering

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

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar det angivna gränssnittet för att köra DHCP. Som standard är det primära gränssnittet aktiverat för DHCP-klienten. I det här läget kan du starta DHCP på det här gränssnittet antingen genom att anropa *nx_dhcp_interface_start* eller starta DHCP på alla aktiverade gränssnitt *nx_dhcp_start*.

Obs! programmet måste först registrera det här gränssnittet med IP-instansen med hjälp av *nx_ip_interface_attach.*

Vidare måste det finnas ett tillgängligt DHCP-klient gränssnitt för att lägga till det här gränssnittet i listan över aktiverade gränssnitt. Som standard har NX_DHCP_CLIENT_MAX_RECORDS definierats till 1. Ange det här alternativet till det maximala antalet gränssnitt som förväntas köra DHCP-klienten samtidigt. Vanligt vis är NX_DHCP_CLIENT_MAX_RECORDS samma NX_MAX_PHYSICAL_INTERFACES; men om en enhet har fler fysiska gränssnitt än det förväntar sig att köra DHCP-klienten, kan du spara minne genom att ange NX_DHCP_CLIENT_MAX_RECORDS till mindre än det numret. Det finns inte någon till en mappning av fysiska gränssnitt med DHCP-klientens gränssnitts poster.

Skillnaden mellan den här tjänsten och *nx_dhcp_set_interface_index* är att de senare bara anger ett enda gränssnitt för att köra DHCP, medan denna tjänst bara lägger till det angivna gränssnittet i listan över klient gränssnitt som är aktiverade för DHCP.

Om du vill inaktivera ett gränssnitt för DHCP kan programmet anropa tjänsten *nx_dhcp_interface_disable* .

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  

- **interface_index** Index för gränssnitt för att aktivera DHCP

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) genomförde DHCP-aktivering

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) ingen post är tillgänglig för ett annat gränssnitt att aktive ras för DHCP

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** -gränssnitt (0xA3) aktiverat för DHCP

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten inaktiverar det angivna gränssnittet för att köra DHCP. Den initierar DHCP-klienten på det här gränssnittet.

För att starta om DHCP-klienten måste programmet återaktivera gränssnittet med *nx_dhcp_interface_enable* och starta om DHCP genom att anropa *nx_dhcp_interface_start*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  

- **interface_index** Index för gränssnitt att inaktivera DHCP på

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-skapande har slutförts

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

Ange DHCP-sändnings flagga

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger eller rensar sändnings flaggan för DHCP-meddelandets huvud för alla gränssnitt som är aktiverade för DHCP. För vissa DHCP-meddelanden (t. ex. identifiering) är sändnings flaggan inställd på sändning eftersom klienten inte har någon IP-adress.

__clear_flag__


- Flaggan för **NX_TRUE** sändning rensas (begär unicast-svar)

- **NX_FALSE** broadcast-flaggan har angetts (begär sändnings svar)

Den här tjänsten är avsedd för DHCP-klienter som måste gå via en router för att komma till DHCP-servern, där routern avvisar broadcast-meddelanden vidarebefordras.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block  

- **clear_flag** Värde att ange sändnings flaggan till

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har uppdaterat sändnings flaggan

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Trådar, initiering

### <a name="example"></a>Exempel

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

Ange eller rensa sändnings flaggan för det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör det möjligt för DHCP-klientens värd program att ange eller rensa sändnings flaggan i DHCP-klientens meddelanden till DHCP-servern på det angivna gränssnittet. Mer information finns i **nx_dhcp_clear_broadcast_flag**

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block

- **interface_index** Index för gränssnitt för att ange sändnings flagga  

- **clear_flag** Värde att ange sändnings flaggan till

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har uppdaterat sändnings flaggan

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad DHCP-instans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-borttagning har slutförts.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_ force_renew

Skicka ett meddelande om Force-förnyelse 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör det möjligt för värd programmet att skicka ett Force renew-meddelande på alla gränssnitt som är aktiverade för DHCP. DHCP-klienten måste vara i ett begränsat tillstånd. Den här funktionen ställer in statusen så att den FÖRNYAs så att DHCP-klienten kan försöka förnya innan T1-timeouten går ut.

Om du vill skicka en tvingande förnyelse av ett speciellt gränssnitt när flera gränssnitt är DHCP-aktiverade använder du *nx_dhcp_interface_force_renew*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat en framtvinga förnyelse.  

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

Skicka ett meddelande om Force-förnyelse på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten gör det möjligt för värd programmet att skicka ett Force renew-meddelande i Indataporten så länge gränssnittet har Aktiver ATS för DHCP (se *nx_dhcp_interface_enable*). DHCP-klienten på det angivna gränssnittet måste vara i ett begränsat tillstånd. Den här funktionen ställer in statusen så att den FÖRNYAs så att DHCP-klienten kan försöka förnya innan T1-timeouten går ut.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat en framtvinga förnyelse.  

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

Ange DHCP-klient paketets adresspool

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Beskrivning

Med den här tjänsten kan programmet skapa en DHCP-modempool genom att skicka en pekare till en tidigare skapad modempool i det här tjänst anropet. Om du vill använda den här funktionen måste värd programmet definiera NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL. När den har definierats skapas inte klientens modempool i *nx_dhcp_creates* tjänsten. Observera att programmet rekommenderas att använda standardvärden för DHCP-poolens paket nytto Last, definierad som NX_DHCP_PACKET_PAYLOAD i *nx_dhcp. h* när du skapar poolen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  

- **packet_pool_ptr** Pekare till tidigare skapade paket pool

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) DHCP-pool för DHCP-klient har angetts

- Tjänsten **NX_NOT_ENABLED** (0x14) är inte aktive rad

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_DHCP_INVALID_PAYLOAD (0x9C) nytto lasten är för liten

### <a name="allowed-from"></a>Tillåten från

Program kod

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

Ange den begärda IP-adressen för DHCP-instansen

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-adressen för DHCP-klienten som ska begäras från DHCP-servern på det första gränssnittet som är aktiverat för DHCP i DHCP-postposten. Om *skip_discover_message* -flaggan har angetts hoppar DHCP-klienten över identifierings meddelandet och skickar ett meddelande om begäran.

Om du vill ange en begäran för en speciell IP-adress för DHCP-meddelanden i ett gränssnitt använder du tjänsten *nx_dhcp_interface_request_client_ip* .

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  

- **client_ip_address** IP-adress att begära från DHCP-server

- **skip_discover_message** Om värdet är true skickar DHCP-klienten begär ande meddelande  
Om det här värdet är falskt skickas identifierings meddelandet.

### <a name="return-values"></a>Retur värden

- Den begärda IP-adressen för **NX_SUCCESS** (0x00) har angetts.

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt
 
### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

Ange den begärda IP-adressen för DHCP-instansen på angivet gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger IP-adressen för DHCP-klienten som ska begäras från DHCP-servern på det angivna gränssnittet, om gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*). Om *skip_discover_message* -flaggan har angetts hoppar DHCP-klienten över identifierings meddelandet och skickar ett meddelande om begäran.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.

- **Interface_index** Index för gränssnitt att begära IP-adress på

- **client_ip_address** IP-adress att begära från DHCP-server

- **skip_discover_message** Om värdet är true skickar DHCP-klienten begär ande meddelande. annars skickas identifierings meddelandet.

### <a name="return-values"></a>Retur värden

- Den begärda IP-adressen för **NX_SUCCESS** (0x00) har angetts.

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig IP-eller DHCP-pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

Rensa nätverks parametrarna för DHCP-klienten 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar nätverks parametrarna för värd programmet (IP-adress, nätverks adress och nätverks mask) och tar bort statusen för DHCP-klienten på alla gränssnitt som är aktiverade för DHCP. Den används i kombination med *nx_dhcp_stop* och *nx_dhcp_start* att starta om DHCP-tillstånds datorn: 

nx_dhcp_stop (&my_dhcp);  
nx_dhcp_reinitialize (&my_dhcp);  
nx_dhcp_start (&my_dhcp);


Använd tjänsten *nx_dhcp_interface_reinitialize* om du vill initiera DHCP-klienten på ett speciellt gränssnitt när flera gränssnitt är aktiverade för DHCP.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP har initierats om 

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

Rensa nätverks parametrarna för DHCP-klienten på det angivna gränssnittet 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar nätverks parametrarna (IP-adress, nätverks adress och nätverks mask) på det angivna gränssnittet om gränssnittet är aktiverat för DHCP (se *nx_dhcp_interface_enable*). Se *nx_dhcp_reinitialize* för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till tidigare skapad DHCP-instans

- **interface_index** Index för gränssnitt att initiera om.

### <a name="return-values"></a>Retur värden

- Gränssnittet för **NX_SUCCESS** (0x00) har initierats om

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

Frisläpp IP-adress för lån

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör IP-adressen som hämtades från en DHCP-server genom att skicka RELEASE-meddelandet till den servern. Sedan initierar den om DHCP-klienten. Den här tjänsten används för alla gränssnitt som är aktiverade för DHCP.

Programmet kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.

Om du vill släppa en adress tillbaka till DHCP-servern i ett gränssnitt använder du tjänsten *nx_dhcp_interface_release*

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-version.  

- **NX_DHCP_NOT_BOUND** (0X94) IP-adressen har inte lånats så den kan inte släppas.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

Frigör IP-adress på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten frigör IP-adressen som hämtades från en DHCP-server på det angivna gränssnittet och initierar om DHCP-klienten. Du kan starta om DHCP-klienten genom att anropa *nx_dhcp_start*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-version.

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- **NX_DHCP_NOT_BOUND** (0X94) IP-adressen har inte lånats så den kan inte släppas.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten avböjer en IP-adress som är lånad från DHCP-servern på alla gränssnitt som är aktiverade för DHCP. Om NX_DHCP_CLIENT_ SEND_ ARP_PROBE har definierats skickar DHCP-klienten ett neka-meddelande om den identifierar att IP-adressen redan används. Se **ARP-avsökningar** i kapitel ett för mer information om ARP PROBE-konfiguration i netx DHCP-klienten.

Programmet kan använda den här tjänsten för att neka sin IP-adress om den identifierar adressen används på annat sätt.

Den här tjänsten initierar om DHCP-klienten så att den kan startas om genom att anropa *nx_dhcp_start*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) nekad har skickats  

- **NX_DHCP_NOT_STARTED** (0X96) DHCP-instansen startades inte

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

Neka IP-adress från DHCP-server på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar meddelandet neka till servern för att neka en IP-adress som tilldelats av DHCP-servern. Den initierar också om DHCP-klienten. Se *nx_dhcp_decline* för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **Interface_index** Index för gränssnittet för att neka IP-adress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-neka meddelande har skickats  

- **NX_DHCP_NOT_BOUND** (0X94) DHCP-klienten är inte kopplad

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

Skicka DHCP-meddelande till Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar det angivna DHCP-meddelandet till DHCP-servern i det första gränssnitt som är aktiverat för DHCP som finns i DHCP-postposten. Om du vill skicka en version eller avvisa ett meddelande måste programmet använda tjänsterna *nx_dhcp [_interface] _release*() eller *nx_dhcp_interface_decline ()* .

DHCP-klienten måste startas för att använda den här tjänsten, förutom för att skicka INFORM_REQUEST meddelande typen.

> [!NOTE] 
> Den här tjänsten är inte avsedd för värd programmet till enhetens klient tillstånds dator.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  

- **dhcp_message_type** Meddelandebegäran (definieras i *nx_dhcp. h*)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-meddelande har skickats  

- **NX_DHCP_NOT_STARTED** (0X96) ogiltigt gränssnitts index

- **NX_DHCP_INVALID_MESSAGE** (0X9B) ogiltig meddelande typ som ska skickas

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

Skicka DHCP-meddelande till server på ett speciellt gränssnitt

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett meddelande till DHCP-servern på det angivna gränssnittet om gränssnittet är aktiverat för DHCP. Om du vill skicka en version eller avvisa ett meddelande måste programmet använda tjänsterna *nx_dhcp [_interface] _release*() eller *nx_dhcp_interface_decline ()* .

DHCP-klienten måste ha startats för att använda den här tjänsten, förutom för meddelande typen DHCP-meddelande begär Ande.

Den här tjänsten är inte avsedd för värd programmet till enhetens klient tillstånds dator.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.

- **Interface_index** Index för gränssnitt att skicka meddelande på  

- **dhcp_message_type** Meddelandebegäran (definieras i *nx_dhcp. h*)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-meddelande har skickats  

- **NX_DHCP_NOT_STARTED** (0X96) ogiltigt gränssnitts index

- **NX_DHCP_INVALID_MESSAGE** (0X9B) ogiltig meddelande typ som ska skickas

- Gränssnitt för **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) har inte Aktiver ATS för DHCP

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

Hämta DHCP-klientens DHCP-servers IP-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar DHCP-klientens DHCP-servers IP-adress i det första gränssnittet som är aktiverat för DHCP som finns i DHCP-postposten. Anroparen kan bara använda den här tjänsten när DHCP-klienten har bundits till en IP-adress som tilldelats av DHCP-servern. Värd programmet kan använda tjänsten *nx_ip_status_check* för att kontrol lera att IP-adressen har angetts, eller så kan den använda *nx_dhcp_state_change_notify* och fråga DHCP-klientens tillstånd NX_DHCP_STATE_BOUND. Mer information om hur du anger motringnings funktionen för tillstånds ändringar finns i *nx_dhcp_state_change_notify* .

Om du vill hitta DHCP-servern på ett speciellt gränssnitt när flera gränssnitt är aktiverade för DHCP-klienten, använder du tjänsten *nx_dhcp_interface_server_address_get*

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.

- **server_address** Pekare till serverns IP-adress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-serveradress returnerades

- NX_PTR_ERROR (0x16) ogiltig inmatare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hämta DHCP-klientens DHCP-servers IP-adress på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar DHCP-klientens DHCP-servers IP-adress på det angivna gränssnittet om gränssnittet är aktiverat för DHCP. DHCP-klienten måste vara i begränsat tillstånd. När du har startat DHCP-klienten på det här gränssnittet kan värd programmet antingen använda *nx_ip_status_check* tjänsten för att kontrol lera att IP-adressen har angetts, eller så kan den använda DHCP-klientens tillstånd för att ändra motringning och fråga DHCP-klientens tillstånd att NX_DHCP_STATE_BOUND. Mer information om hur du anger motringnings funktionen för tillstånds ändringar finns i *nx_dhcp_state_change_notify* .

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.

- **Interface_index** Index för gränssnitt för att hämta IP-adress  

- **server_address** Pekare till serverns IP-adress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-serveradress returnerades

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt har Aktiver ATS för DHCP

- **NX_DHCP_NOT_BOUND** (0X94) DHCP-klienten är inte kopplad

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ange nätverks gränssnitt för DHCP-instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger nätverks gränssnittet för DHCP-instansen att ansluta till DHCP-servern vid körning av DHCP-klienten som kon figurer ATS för ett enda nätverks gränssnitt.

Som standard körs DHCP-klienten på det primära gränssnittet. Om du vill köra DHCP på en sekundär tjänst använder du den här tjänsten för att ange det sekundära gränssnittet som DHCP-klient gränssnitt. Programmet måste tidigare registrera det angivna gränssnittet för IP-instansen med hjälp av tjänsten *nx_ip_interface_attach* .

Observera att den här tjänsten är avsedd för program som endast avser att köra DHCP-klienten på ett gränssnitt. Om du vill köra DHCP på flera gränssnitt kan du se *nx_dhcp_interface_enable* för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till DHCP-kontroll block.  

- **index** Index för enhetens nätverks gränssnitt

### <a name="return-values"></a>Retur värden

- Gränssnittet för **NX_SUCCESS** (0x00) har angetts.

- **NX_INVALID_INTERFACE** (0X4C) ogiltigt nätverks gränssnitt

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** -gränssnitt (0xA3) aktiverat för DHCP

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0XA7) ingen post tillgänglig för en annan

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten startar DHCP-bearbetning på alla gränssnitt som är aktiverade för DHCP. Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*

Om du vill kontrol lera att IP-instansen är kopplad till en IP-adress i DHCP-klientens gränssnitt använder du *nx_ip_status_check* för att se bekräfta att IP-adressen är giltig.

Om det finns andra gränssnitt som redan kör DHCP, kommer den här tjänsten inte att påverka dem.

Använd tjänsten *nx_dhcp_interface_start* för att starta DHCP på ett speciellt gränssnitt när flera gränssnitt är aktiverade.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-start har slutförts.  

- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP har redan startats.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten startar DHCP-bearbetning på det angivna gränssnittet om gränssnittet är aktiverat för DHCP. Se *nx_dhcp_interface_enable*() om du vill ha mer information om hur du aktiverar ett gränssnitt för DHCP. Som standard är det primära gränssnittet aktiverat för DHCP när programmet anropar *nx_dhcp_create.*

Om det inte finns några andra gränssnitt som kör DHCP-klienten, kommer tjänsten att starta/återuppta DHCP-klientens tråd och (åter) Aktivera DHCP-klientens timer.  
  
Programmet bör använda *nx_ip_status_check* för att kontrol lera om en IP-adress hämtas.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **Interface_index** Index för att starta DHCP-klienten

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-start har slutförts.  

- **NX_DHCP_ALREADY_STARTED** (0X93) DHCP-instansen har redan startats.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

Ange funktion för att ändra motringning för DHCP-tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar den angivna återanrops funktionen dhcp_state_change_notify för att meddela ett program om DHCP-tillstånds ändringar. Funktionen motringning tillhandahåller det tillstånd som DHCP-klienten har övergått till.

Följande är värden som är associerade med de olika DHCP-tillstånden:

| Tillstånd                             | Värde |
|-----------------------------------|-------|
| start av NX \_ DHCP- \_ tillstånd \_             | 1     |
| initiering av NX \_ DHCP- \_ tillstånd \_             | 2     |
| Val av NX \_ DHCP- \_ tillstånd \_        | 3     |
| \_begär ande av NX DHCP- \_ tillstånd \_       | 4     |
| \_giltiga NX DHCP- \_ tillstånd \_            | 5     |
| NX \_ DHCP- \_ tillstånd \_ förnyar         | 6     |
| OMBINDNING av NX \_ DHCP- \_ tillstånd \_        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| NX \_ DHCP- \_ tillstånd \_ adress för \_ avsökning | 9     |


### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **dhcp_state_change_notify** Funktions pekare för motringning av tillstånds ändring

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) motringning har angetts.  

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

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

Ange funktionen motringning av DHCP-tillstånd i det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar den angivna callback-funktionen för att meddela ett program om DHCP-tillstånds ändringar. Funciton för motringning är gränssnitts index och det tillstånd som DHCP-klienten har övergått till på det gränssnittet.

Mer information om tillstånds ändrings funktioner finns i *nx_dhcp_state_change_notify*().

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **dhcp_interface_state_change_notify** Funktions pekare för program återanrop

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) motringning har angetts.  

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

### <a name="allowed-from"></a>Tillåten från

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

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar DHCP-bearbetning på alla gränssnitt som har börjat DHCP-bearbetning. Om det inte finns några gränssnitt som bearbetar DHCP kommer den här tjänsten att pausa DHCP-klientens tråd och inaktivera DHCP-klientens timer.

Använd tjänsten *nx_dhcp_interface_stop* för att stoppa DHCP på ett speciellt gränssnitt om flera gränssnitt är aktiverade för DHCP.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-stopp

- **NX_DHCP_NOT_STARTED** (0X96) DHCP-instansen startades inte.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

Stoppa DHCP-bearbetning på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar DHCP-bearbetning på det angivna gränssnittet om DHCP redan har startats. Om det inte finns några andra gränssnitt som kör DHCP så pausas DHCP-tråden och timern.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **Interface_index** Gränssnitt där DHCP-bearbetningen ska stoppas

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DHCP-stopp

- **NX_DHCP_NOT_STARTED** (0X96) DHCP har inte startats.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

Hämta ett DHCP-alternativ från senaste Server svar

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det angivna DHCP-alternativet från bufferten för DHCP-alternativ i det första gränssnitt som är aktiverat för DHCP som finns på DHCP-klienttjänsten. Om det lyckas kopieras alternativ data till den angivna bufferten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.  

- **request_option** DHCP-alternativet, enligt vad som anges i RFC: erna. Se alternativet NX_DHCP_OPTION i *nx_dhcp. h*.

- **destination_ptr** Pekar till målet för svars strängen.  

- **destination_size** Pekar till målets storlek och vid retur, där antalet byte som returneras visas.

### <a name="return-values"></a>Retur värden

- Hämtning av **NX_SUCCESS** (0X00) lyckades.  

- **NX_DHCP_NOT_BOUND** (0X94) DHCP-klienten är inte kopplad.

- **NX_DHCP_NO_INTERFACES_ENABLED** (0XA5) inga gränssnitt har Aktiver ATS för DHCP

- **NX_DHCP_DEST_TO_SMALL** -destinationen (0x95) är för liten för att rymma svar.

- Det gick inte att hitta **NX_DHCP_PARSE_ERROR** (0X97) DHCP-alternativet i Server svaret.

- NX_PTR_ERROR (0x16) ogiltig inmatad pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Hämta ett DHCP-alternativ från senaste Server svar på det angivna gränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det angivna DHCP-alternativet från bufferten för DHCP-alternativ på det angivna gränssnittet, om gränssnittet är aktiverat för DHCP. Om det lyckas kopieras alternativ data till den angivna bufferten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **Interface_index** Index som det angivna alternativet ska hämtas till  

- **request_option** DHCP-alternativet, enligt vad som anges i RFC: erna. Se alternativet NX_DHCP_OPTION i *nx_dhcp. h*.  

- **destination_ptr** Pekar till målet för svars strängen.  

- **destination_size** Pekar till målets storlek och vid retur, där antalet byte som returneras visas.

### <a name="return-values"></a>Retur värden

- Hämtning av **NX_SUCCESS** (0X00) lyckades.  

- **NX_DHCP_NOT_BOUND** (0X94) IP-adress inte tilldelad

- **NX_DHCP_DEST_TO_SMALL** -bufferten (0x95) är för liten

- Det gick inte att hitta **NX_DHCP_PARSE_ERROR** (0X97) DHCP-alternativet i Server svaret.

- NX_PTR_ERROR (0x16) ogiltig DHCP-pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropar tjänst.

- NX_INVALID_INTERFACE (0x4C) ogiltigt nätverks gränssnitt

### <a name="allowed-from"></a>Tillåten från

Konversation

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

### <a name="description"></a>Beskrivning

Den här tjänsten konverterar de fyra tecknen till "option_string_ptr" till ett osignerat långt värde. Det är särskilt användbart när det finns IP-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **option_string_ptr** Pekare till den tidigare hämtade alternativ strängen.

### <a name="return-values"></a>Retur värden

- **Värde** Värdet för de första fyra bytena.

### <a name="allowed-from"></a>Tillåten från

Konversation

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

Ange callback-funktionen för att lägga till användar alternativ som har angetts

### <a name="prototype"></a>Prototyp

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>Beskrivning

Den här tjänsten registrerar den angivna callback-funktionen för att lägga till användar alternativ.

Om funktionen motringning har angetts kan programmen lägga till användar alternativ i paketet genom iface_index och message_type.

> [!NOTE]
> I användarens rutin. Program måste följa alternativen för DHCP-alternativ när du lägger till användar alternativ. Den totala storleken för användar alternativ måste vara mindre än eller lika med user_option_length och uppdatera user_option_length som en verklig längd. Returnera NX_TRUE om alternativet har lagts till, annars returnerar NX_FALSE.

### <a name="input-parameters"></a>Indataparametrar

- **dhcp_ptr** Pekare till den tidigare skapade DHCP-instansen.

- **dhcp_user_option_add** Pekare till funktionen Lägg till användar alternativ.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) motringning har angetts.

- NX_PTR_ERROR (0x16) ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
