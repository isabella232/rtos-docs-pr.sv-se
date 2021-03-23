---
title: Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DHCPv6-klient tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826073"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-klient tjänster

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DHCPv6-klient tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_dhcpv6_client_create:** *skapa en DHCPV6-klient instans* 

- **nx_dhcpv6_client_delete:** *ta bort en DHCPV6-klient instans* 

- **nx_dhcpv6_create_ client_duid:** *skapa ett DUID för DHCPv6-klienten* 

- **nx_dhcpv6 _add_client_ia:** *Lägg till en Dhcpv6-klient identitets adress (IA)* 

- **nx_dhcpv6 _create_client_ia:** (*äldre Lägg till en DHCPv6-klients identitets adress (IA))* 

- **nx_dhcpv6_create_client_iana:** *skapa en Dhcpv6-klient identitets Association för icke-temporära adresser (IANA)* 

- **nx_dhcpv6_get_client_duid_time_id:** *Hämta tid-ID: t från DHCPv6-klientens DUID* 

- **nx_dhcpv6_client_set_interface:** *Ange klient nätverks gränssnittet för kommunikation med DHCPv6-servern* 

- **nx_dhcpv6_get_IP_address:** *Hämta den globala IPv6-adress som tilldelats till DHCPv6-klienten* 

- **nx_dhcpv6_get_lease_time_data:** *Hämta T1, T2, giltiga och önskade livs längder för den globala klientens globala IPv6-adress*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *Hämta T1, T2, giltiga och önskade livs längder för DHCPv6-klientens IPv6-adress med adress index* 

- **nx_dhcpv6_get_iana_lease_time:** *Hämta T1 och T2 i identitets associeringen (IANA) som är lånad till DHCPv6-klienten* 

- **nx_dhcpv6_get_other_option_data:** *Hämta de angivna alternativ data, t. ex. domän namn eller tids zons Server* 

- **nx_dhcpv6_get_DNS_server_address:** *Hämta DNS-serveradress vid angivet index till DHCPv6-klientens DNS-server lista* 

- **nx_dhcpv6_get_time_accrued:** *Hämta den uppskjutna tiden som det globala IPv6-adresslån har bundits till DHCPv6-klienten* 

- **nx_dhcpv6_get_time_server_address:** *Hämta tids server adress vid angivet index i DHCPv6-klientens tids server lista*

- **nx_dhcpv6_get_valid_ip_address_count:** *Hämta antalet IPv6-adresser som har tilldelats DHCPv6-klienten* 

- **nx_dhcpv6_reinitialize:** *initiera om DHCPv6 för att starta om DHCPv6-klientens tillstånds dator och köra DHCPv6-protokollet igen* 

- **nx_dhcpv6_request_confirm:** *skicka en Confirm-begäran till servern* 

- **nx_dhcpv6_request_inform_request:** S *Avsluta ett meddelande om begäran till servern* 

- **nx_dhcpv6_request_release:** *skicka en release-begäran till servern* 

- **nx_dhcpv6_request_option_DNS_server:** *Lägg till alternativet DNS-server i klient alternativ begär ande data i begär ande meddelanden till servern* 

- **nx_dhcpv6_request_option_FQDN:** *Lägg till alternativet FQDN i klient alternativ begär ande data i begär ande meddelanden till servern* 

- **nx_dhcpv6_request_option_domain_name:** *Lägg till alternativet domän namn i klient alternativ begär ande data i begär ande meddelanden till servern* 

- **nx_dhcpv6_request_option_time_server:** *Lägg till alternativet för tids server i klient alternativ begär ande data i begär ande meddelanden till servern* 

- **nx_dhcpv6_request_option_timezone:** *Lägg till alternativet tidszon i begär ande data för klient alternativ i begär ande meddelanden till servern* 

- **nx_dhcpv6_request_solicit:** *skicka en begäran om DHCPv6-begäran till valfri server i klient nätverket (sändning)* 

- **nx_dhcpv6_request_solicit_rapid:** *skicka en begäran om DHCPv6-begäran till valfri server på klient nätverket (sändning) med alternativ uppsättningen för snabb incheckning* 

- **nx_dhcpv6_resume:** *återuppta DHCPV6-klient bearbetning* 

- **nx_dhcpv6_start:** *starta aktiviteten dhcpv6 client Thread. OBS! detta motsvarar inte start av DHCPv6-tillstånds datorn och skickar ingen begär ande förfrågan* 

- **nx_dhcpv6_stop:** *Stoppa aktiviteten DHCPV6 klient tråd* 

- **nx_dhcpv6_suspend:** *inaktivera aktiviteten för DHCPv6-klient tråd* 

- **nx_dhcpv6_set_time_accrued:** *Ange den tid som ska periodiseras på det globala klientens IPv6-adresslån i klient posten.*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

Skapa en DHCPv6-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en DHCPv6-klient instans inklusive återanrops funktioner.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-kontroll block  

- **ip_ptr** Pekare till klientens IP-instans  

- **name_ptr** Pekare till namn på DHCPv6-instans

- **packet_pool_ptr** Pekare till klient paketets pool

- **stack_ptr** Pekare till klientens stack minne

- **stack_size** Storlek på klientens stack minne

- **dhcpv6_state_change_notify** Pekare till callback-funktionen anropas när klienten initierar en ny DHCPv6-begäran till servern

- **dhcpv6_server_error_handler** Pekare till callback-funktionen anropas när klienten får en fel status från servern

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient skapande

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

Ta bort en DHCPv6-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad DHCPv6-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckade DHCPv6-borttagning

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

Anger klientens nätverks gränssnitt för DHCPv6

### <a name="prototype"></a>Prototyp

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger klientens nätverks gränssnitt för att kommunicera med DHCPv6-servrarna till det angivna indexet för indataport.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **interface_index** Index indikerar nätverks gränssnitt

### <a name="return-values"></a>Retur värden

- Gränssnittet för **NX_SUCCESS** (0x00) har angetts

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_INVALID_INTERFACE (0x4C) ogiltigt inmatade gränssnitts index

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

Anger mål adressen där DHCPv6-meddelande ska skickas till

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger mål adressen där DHCPv6-meddelandet ska skickas. Som standard är ALL_DHCP_Relay_Agents_and_Servers (FF02:: 1:2).

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **destination_address** Mål adress

### <a name="return-values"></a>Retur värden

- Gränssnittet för **NX_SUCCESS** (0x00) har angetts

- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) stycke fel

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

Skapa DUID-objekt för klient

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar klienten DUID med indataparametrarna. Om tiden inte anges och DUID-typen indikerar länk lager med tid, kommer den här funktionen att tillhandahålla en tid som innehåller en slumpmässig faktor för unikhet. Leverantörs tilldelning (Enterprise) DUID-typer stöds inte.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **duid_type** Typ av DUID (maskin vara, företag osv.)

- **hardware_type** Nätverks maskin vara, t. ex. IEEE 802

- **tid** Värde som används för att skapa unik identifierare

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) ett lyckat klient-DUID skapades

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID-typen är okänd eller stöds inte 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID-maskin varu typen är okänd eller stöds inte

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

Lägg till en identitets koppling till klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är identisk med *nx_dhcpv6_add_client_ia* -tjänsten. Den lägger till en klient identitets Association genom att fylla i klient posten med de angivna parametrarna. Ange de här parametrarna till oändlighet för att begära maximalt antal prioriterade och giltiga livstider. Om du vill lägga till mer än ett IA i en DHCPv6-klient anger du NX_DHCPV6_MAX_IA_ADDRESS till ett värde som är högre än standardvärdet 1.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **ipv6_address** Pekare till NetX Duo IP-adressblock

- **preferred_lifetime** Tids längd innan IP-adressen är föråldrad

- **valid_lifetime** Tids längd innan IP-adressen har gått ut

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient-IA har lagts till

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) DUBBLETT av IA-adress 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA överskrider den högsta antalet IAS-klienter som kan lagra

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) ogiltig (t. ex. null) IA-adress i IA

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

Skapa en identitets Association (icke-tillfällig) för klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en klient som inte har en tillfällig identitets Association (IANA) från de angivna parametrarna. Om du vill ställa in T1-och T2-tiderna till maximum (oändlighet) i DHCPv6-klient förfrågningarna ställer du in dessa parametrar på NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> En klient har bara en IANA.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **IA_ident** Unikt ID för identitets Association

- **T1** När klienten måste starta förnyelsen av IPv6-adressen

- **T2** När klienten måste starta theIPv6 Address binding

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skapade IANA

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

Lägg till en identitets koppling till klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en klient identitets Association genom att fylla i klient posten med de angivna parametrarna. Ange de här parametrarna till oändlighet för att begära maximalt antal prioriterade och giltiga livstider. Om du vill lägga till mer än ett IA i en DHCPv6-klient anger du NX_DHCPV6_MAX_IA_ADDRESS till ett värde som är högre än standardvärdet 1.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **ipv6_address** Pekare till NetX Duo IP-adressblock

- **preferred_lifetime** Tids längd innan IP-adressen är föråldrad

- **valid_lifetime** Tids längd innan IP-adressen har gått ut 

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient-IA har lagts till

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0XEAF) DUBBLETT av IA-adress 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA överskrider den högsta antalet IAS-klienter som kan lagra

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) ogiltig (t. ex. null) IA-adress i IA

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare

 
### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

Hämtar tid-ID från klientens DUID

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar fältet tid-ID från klientens DUID. Om programmet först måste anropa *nx_dhcpv6_create_client_duid*, för att fylla i klientens DUID i Dhcpv6-klient instansen, eller så har det ett null-värde för det här fältet. Avsikten är att programmet ska kunna spara dessa data och presentera samma klient-DUID på servern, inklusive fältet Time, i omstarter.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **TIME_ID** Pekare till datum fältet för klientens DUID

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) IP-adresslån har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

Hämtar klientens globala IPv6-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar klientens globala IPv6-adress. Om klienten inte har en giltig adress returneras en fel status. Om en klient har fler än en global IPv6-adress returneras den primära IPv6-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **ip_address** Pekare till IPv6-adress

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IPv6-adress har tilldelats

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0XEAD) IPv6-adressen är inte giltig

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

Hämtar information om låne tid för klientens IA-adress

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar klientens globala data för IA-adress. Om status för klientens IA-adress är ogiltig anges tids data till noll och statusen för lyckad slut för ande har returnerats. Om en klient har fler än en global IPv6-adress returneras data för primär data källor.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **T1** Pekare till IA-adress förnyelse tid

- **T2** Pekare till tid i IA-adress OMBINDNING

- **preferred_lifetime** Pekare till tid när IA-adressen är föråldrad

- **valid_lifetime** Pekare till tid när IA-adressen har upphört att gälla

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IA låne data har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana lease_time

Hämta klientens information om låne tid för IANA

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar klientens globala IA-NA-data (T1 och T2). Om ingen av klientens IA-NA-adresser har en giltig adress status anges tids data till noll, och statusen för lyckad slut för ande har returnerats. Om en klient har fler än en global IPv6-adress returneras data för primär data källor.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **T1** Pekare till tid för att påbörja låne förnyelse

- **T2** Pekare till tid för att starta låne OMBINDNING

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IANA-adresslån har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

Hämta antalet klientens giltiga IA-adresser

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Beskrivning

Tjänsten hämtar antalet giltiga IPv6-adresser för klienten. En giltig IPv6-adress är kopplad till klienten och är registrerad hos IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **address_count** Pekare till adress antal att returnera

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IANA-adresslån har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

Hämta klientens IA-data med adress index

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar klientens IA-adress och låne data efter adress index. Om ett ogiltigt index anges eller IPv6-adressen i det indexet inte är giltig, returnerar tjänsten en NX_DHCPV6_IA_ADDRESS_NOT_VALID fel status.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **address_index** Index i DHCPv6 IA-tabell

- **ip_address** Pekare till IPv6-adress att hämta

- **preferred_lifetime** Pekare till tid när IA-adressen är föråldrad

- **valid_lifetime** Pekare till tid när IA-adressen har upphört att gälla

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) IANA-data har hämtats

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0XEAD) ett ogiltigt index eller ingen giltig IPv6-adress med det angivna indexet 

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

Hämtar DNS-serveradress 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar DNS-serverns IPv6-Datadata med det angivna indexet i klient listan. Om listan inte innehåller någon server adress vid indexet returneras ett fel. Indexet får inte överskrida storleken på listan över DNS-servrar som anges av alternativet för att konfigurera användare NX_DHCPV6_NUM_DNS_SERVERS.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **index** Index i listan DNS-Server

- **server_address** Pekare till server adress buffer

### <a name="return-values"></a>Retur värden

- **NX_SUCCESSs** adress (0x00) har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

Hämtar DHCPv6-alternativ data 

### <a name="prototype"></a>Prototyp

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar DHCPv6-alternativ data från ett DHCPv6-meddelande för den angivna alternativ koden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **alternativ** kod för alternativ kod för vilka data som ska hämtas

- **buffert** Pekare till buffert för att kopiera data till 

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) alternativ data har hämtats

- **NX_DHCPV6_UNKNOWN_OPTION** (0XEAB) Okänd/alternativ kod som inte stöds

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) ogiltig inmatad icke-pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

Hämtar den tid som periodiseras på klientens IP-adresslån

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den tid som periodiseras på klientens IPv6-adresslån. Funktionen kontrollerar alla IPv6-adresser som tilldelats klienten för den första giltiga adressen. Om inga giltiga adresser hittas returneras ett nollvärde för den uppskjutna tiden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **time_accrued** Pekare till tid som periodiseras i IP-adresslån

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) upplupen tid har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

Hämtar tids server adress 

### <a name="prototype"></a>Prototyp

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar Time servers IPv6-Datadata vid det angivna indexet i klient listan. Om listan inte innehåller någon server adress vid indexet returneras ett fel. Indexet får inte överskrida storleken på tids server listan som anges av alternativet för att konfigurera användare NX_DHCPV6_NUM_TIME_SERVERS.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **index** Index i tids server listan

- **server_address** Pekare till server adress buffer

### <a name="return-values"></a>Retur värden

- **NX_SUCCESSs** adress (0x00) har hämtats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

Ta bort klientens IP-adress från IP-tabellen

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar om klienten för att starta om DHCPv6-tillstånds datorn och köra DHCPv6-protokollet igen. Detta är inte nödvändigt om klienten inte tidigare har startat DHPCv6-tillstånds datorn eller tilldelats några IPv6-adresser. Adresserna som sparas i DHCPv6-klienten samt registrerade med IP-instansen är båda rensade.

> [!NOTE]
> Programmet måste fortfarande starta DHCPv6-klienten med hjälp av *nx_dhcpv6_start tjänsten* och påbörja begäran om IPv6-adress tilldelning genom att anropa *nx_dhcpv6_request_solicit*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESSs** adress (0x00) har tagits bort

- **NX_DHCPV6_ALREADY_STARTED** (0XE91) DHCPv6-klienten körs redan

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

Bearbeta klientens bekräftelse tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en bekräftelse förfrågan. Om ett svar tas emot från servern uppdaterar DHCPv6-klienten dess låne parametrar med mottagna data.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) bekräfta att meddelandet har skickats och bearbetats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

Behandla klientens tillstånd för att meddela begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett meddelande om meddelande om begäran. Om ett svar tas emot bearbetas svaret för att fastställa att det är giltigt och servern beviljar begäran. Klient instansen uppdateras sedan med Server informationen vid behov.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) meddela att begär ande meddelandet har skapats och bearbetats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

Lägg till DNS-server i DHCPv6 option-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till alternativet för att begära DNS-Server information till DHCPv6-alternativ förfrågan. Om servern svarar inkluderar DNS-Datadata kommer klienten att lagra DNS-servern om den har utrymme att göra det. Antalet DNS-servrar som klienten kan lagra bestäms av det konfigurerbara alternativet NX_DHCPV6_NUM_DNS_SERVERS vars standardvärde är 2.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- Alternativet DNS-server för **NX_SUCCESS** (0x00) ingår

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

Lägg till fullständigt kvalificerat domän namns alternativ i option Request List

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till alternativet för att lägga till klientens fullständigt kvalificerade domän namn i DHCPv6 option-begäran. Det finns tre alternativ för alternativet FQDN:

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 uppdatera FQDN-till-IPv6-adress mappningen för FQDN och adress (er) som används av klienten.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 uppdatera adress mappningen för FQDN-till-IPv6 för FQDN och adress (er) som används av klienten till servern.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 begär att servern inte utför DNS-uppdateringar på klientens vägnar.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **domain_name** Sträng som innehåller domän namnet

- **op** Typ av FQDN-alternativ som ska användas (se listan ovan)

### <a name="return-values"></a>Retur värden

- Alternativet för **NX_SUCCESS** (0X00) FQDN ingår

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

Lägg till domän namns alternativ i DHCPv6 option-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till alternativet domän namn i option-begäran i klient begär ande meddelanden. Om Server svaret inkluderar domän namns data kommer klienten att lagra domän namns informationen om domän namnets storlek ligger inom buffertstorleken för att hålla domän namnet. Buffertstorleken är ett konfigurerbart alternativ (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) med ett standardvärde på 30 byte.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) alternativ uppsättning för domän namn

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

Ange tids Server data som valfri begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till alternativet för Time Server-information i option-begäran om klient begär ande meddelanden. Om Server svaret innehåller Tim Server data kommer klienten att lagra tids servern om den har utrymme att göra det. Antalet tids servrar som klienten kan lagra bestäms av det konfigurerbara alternativet

NX_DHCPV6_NUM_TIME _SERVERS vars standardvärde är 1.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) tids Server alternativ har lagts till

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

Ange tids zons data som valfri begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till alternativet för att begära tids zons information till klient Options förfrågan. Om Server svaret innehåller tids zons data, kommer klienten att lagra tids zons informationen om tids zonens storlek ligger inom buffertstorleken för att hålla tids zonen. Buffertstorleken är ett konfigurerbart alternativ (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) med ett standardvärde på 10 byte.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) tids zons alternativ har lagts till

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

Skicka ett DHCPv6-RELEASE-meddelande

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett RELEASE-meddelande i klient nätverket. Om meddelandet har skickats returneras en lyckad status. En lyckad slut för ande innebär inte att klienten tog emot ett svar eller har beviljats en IPv6-adress ännu. Aktiviteten DHCPv6 klient tråd väntar på ett svar från en DHCPv6-server. Om ett tas emot, kontrollerar det att svaret är giltigt och lagrar data till klient posten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) versions meddelandet har skickats

- **NX_DHCPV6_NOT_STARTED** (0XE92) DHCPV6-klient aktiviteten har inte startats

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** -adressen (0xEAD) är inte kopplad till klienten

- Det gick inte att hitta **NX_INVALID_INTERFACE** (0x4C) i IP-adress tabellen

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

Skicka ett INBJUDNINGs meddelande

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett INBJUDNINGs meddelande ut från nätverket. Om meddelandet har skickats returneras en lyckad status. En lyckad slut för ande innebär inte att klienten tog emot ett svar eller har beviljats en IPv6-adress ännu. Aktiviteten DHCPv6 klient tråd väntar på ett svar (ett ANNONSERINGs meddelande) från en DHCPv6-server. Om en tas emot, kontrol leras att svaret är giltigt, lagrar data i klient posten och befordrar klienten till status för begäran.

> [!NOTE] 
> Om alternativet för snabb incheckning är inställt, går DHCPv6-klienten direkt till det begränsade tillstånd om den får ett giltigt meddelande om Server annonsering. Mer information finns i tjänst beskrivningen för *nx_dhcpv6_request_solicit_rapid* .

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SOLICIT-meddelande har skickats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Skicka ett INBJUDNINGs meddelande med alternativet för snabb incheckning

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett VÄRVNINGs meddelande i nätverket med alternativet för snabb incheckning. Om meddelandet har skickats returneras en lyckad status. En lyckad slut för ande innebär inte att klienten tog emot ett svar eller har beviljats en IPv6-adress ännu. Aktiviteten DHCPv6 klient tråd väntar på ett svar (ett ANNONSERINGs meddelande) från en DHCPv6-server. Om en tas emot, kontrollerar det att svaret är giltigt, lagrar data till klient posten och befordrar klienten till ett begränsat tillstånd.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SOLICIT-meddelande har skickats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

Återuppta DHCPv6-klient aktivitet 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återupptar aktiviteten för DHCPv6 client-tråden. Aktuellt DHCPv6-klient tillstånd kommer att bearbetas (t. ex. bounds, solicit)

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har återupptagits

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_ time_accrued

Anger den tid som periodiseras på klientens IP-adresslån

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den tid som ska periodiseras på klientens globala IP-adress sedan den tilldelades av servern. Detta bör endast användas om en klient för närvarande är kopplad till en tilldelad IPv6-adress.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

- **time_accrued** Tid som periodiseras i IP-adresslån

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) som har angetts

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

Starta aktiviteten DHCPv6-klient 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar DHCPv6-klient aktiviteten och förbereder klienten för att köra DHCPv6-protokollet. Den verifierar att klient instansen har tillräckligt med information (till exempel en klient-DUID), skapar och binder UDP-socketen för att skicka och ta emot DHCPv6-meddelanden och aktiverar timers för att hålla reda på sessionens tid och när det aktuella IPv6-lånet upphör att gälla.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har startats

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** -klienten (0xEA9) saknar nödvändiga alternativ

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

Stoppa aktiviteten DHCPv6-klient 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar DHCPv6-klientens aktivitet och rensar återöverförings antal, högsta antal återöverförings intervall, inaktive ring av sessionens och lånets förfallo tider och avbinder DHCPv6-klientens socket-port. Om du vill starta om klienten måste du först stoppa och eventuellt initiera klienten igen innan du påbörjar en annan session med en DHCPv6-server. Mer information finns i avsnittet om litet exempel.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har stoppats

- **NX_DHCPV6_NOT_STARTED** (0XE92) klient tråden har inte startats

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

Pausa aktiviteten DHCPv6-klient 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten pausar DHCPv6-klient aktiviteten och alla begär Anden som den var i mitten av bearbetningen. Timers har inaktiverats och klientens tillstånd är inställt på att inte köras.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klient instans

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har pausats

- **NX_DHCPV6_NOT_STARTED** -klienten (0XE92) körs inte och kan inte pausas

- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

- NX_CALLER_ERROR (0x11) måste anropas från tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>Se även

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
