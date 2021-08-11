---
title: Kapitel 4 – Azure RTOS NetX Duo DHCPv6-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo DHCPv6-klienttjänster (listas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6caf943f990f8fe5cbd2cd6139a1253fcaf47dc207141963e31a9e31864ef839
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791745"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Kapitel 4 – Azure RTOS NetX Duo DHCPv6-klienttjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo DHCPv6-klienttjänster (listas nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- **nx_dhcpv6_client_create: Skapa** *en DHCPv6-klientinstans* 

- **nx_dhcpv6_client_delete: Ta** *bort en DHCPv6-klientinstans* 

- **nx_dhcpv6_create_ client_duid: Skapa** *ett DHCPv6-klient-DUID* 

- **nx_dhcpv6 _add_client_ia: Lägg** *till en DHCPv6-klientidentitetsadress (IA)* 

- **nx_dhcpv6 _create_client_ia:** (*Lägg till en DHCPv6-klientidentitetsadress (IA)* 

- **nx_dhcpv6_create_client_iana: Skapa** *en DHCPv6-klientidentitetsassociation för icke-tillfälliga adresser (IANA)* 

- **nx_dhcpv6_get_client_duid_time_id: Hämta** *tids-ID från DHCPv6-klientens DUID* 

- **nx_dhcpv6_client_set_interface:** *Ange klientnätverksgränssnittet för kommunikation med DHCPv6-servern* 

- **nx_dhcpv6_get_IP_address: Hämta** *den globala IPv6-adressen som tilldelats DHCPv6-klienten* 

- **nx_dhcpv6_get_lease_time_data:** *Hämta T1, T2, giltig och önskad livslängd för klientens globala IPv6-adress*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** Hämta T1, T2, giltig och önskad livslängd för *DHCPv6-klientens IPv6-adress efter adressindex* 

- **nx_dhcpv6_get_iana_lease_time:** Hämta T1 och T2 i *Identity Association (IANA) som leasas till DHCPv6-klienten* 

- **nx_dhcpv6_get_other_option_data:** *Hämta angivna alternativdata, t.ex. domännamn eller tidszonsserver* 

- **nx_dhcpv6_get_DNS_server_address: Hämta** *DNS-serveradressen vid det angivna indexet till listan över DHCPv6-klient-DNS-servrar* 

- **nx_dhcpv6_get_time_accrued: Hämta** den tid som ackumuleras det globala IPv6-adresslånet har varit bundet *till DHCPv6-klienten* 

- **nx_dhcpv6_get_time_server_address: Hämta** *tidsserverns adress vid det angivna indexet till listan DHCPv6-klienttidsserver*

- **nx_dhcpv6_get_valid_ip_address_count:** *Hämta antalet IPv6-adresser som tilldelats DHCPv6-klienten* 

- **nx_dhcpv6_reinitialize:** Initiera om DHCPv6 för att starta om DHCPv6-klienttillståndsdatorn och köra *DHCPv6-protokollet igen* 

- **nx_dhcpv6_request_confirm:** *Skicka en CONFIRM-begäran till servern* 

- **nx_dhcpv6_request_inform_request:** Avsluta *ett INFORM REQUEST-meddelande till servern* 

- **nx_dhcpv6_request_release:** *Skicka en RELEASE-begäran till servern* 

- **nx_dhcpv6_request_option_DNS_server:** *Lägg till ALTERNATIVET DNS-server i alternativet Klient för att begära data i begärandemeddelanden till servern* 

- **nx_dhcpv6_request_option_FQDN:** *Lägg till alternativet FQDN i alternativet Klient för att begära data i begärandemeddelanden till servern* 

- **nx_dhcpv6_request_option_domain_name:** *Lägg till domännamnsalternativet i alternativet Klient för att begära data i begärandemeddelanden till servern* 

- **nx_dhcpv6_request_option_time_server:** *Lägg till tidsserveralternativet i alternativet Klient för att begära data i begärandemeddelanden till servern* 

- **nx_dhcpv6_request_option_timezone:** *Lägg till tidszonsalternativet i alternativet Klient för att begära data i begärandemeddelanden till servern* 

- **nx_dhcpv6_request_solicit:** *Skicka en DHCPv6 REQUEST-begäran till valfri server i klientnätverket (broadcast)* 

- **nx_dhcpv6_request_solicit_rapid:** Skicka en DHCPv6 REQUEST-begäran till en server i klientnätverket *(broadcast) med alternativuppsättningen Snabb genomföring* 

- **nx_dhcpv6_resume: Återuppta** *DHCPv6-klientbearbetning* 

- **nx_dhcpv6_start:** *Starta tråduppgiften DHCPv6-klient. Observera att detta inte motsvarar att starta DHCPv6-tillståndsdatorn och inte skickar en REQUEST-begäran* 

- **nx_dhcpv6_stop:** *Stoppa DHCPv6-klientens tråduppgift* 

- **nx_dhcpv6_suspend: Pausa** *DHCPv6-klientens tråduppgift* 

- **nx_dhcpv6_set_time_accrued: Ange** *den tid som påförs på det globala klient-IPv6-adresslånet i klientposten.*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

Skapa en DHCPv6-klientinstans

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

### <a name="description"></a>Description

Den här tjänsten skapar en DHCPv6-klientinstans, inklusive återanropsfunktioner.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-kontrollblock  

- **ip_ptr** Pekare till klientens IP-instans  

- **name_ptr** Pekare till namn för DHCPv6-instans

- **packet_pool_ptr** Pekare till klientpaketpool

- **stack_ptr** Pekare till minne för klientstack

- **stack_size** Storleken på klientens stackminne

- **dhcpv6_state_change_notify** Pekare till återanropsfunktionen som anropas när klienten initierar en ny DHCPv6-begäran till servern

- **dhcpv6_server_error_handler** Pekare till återanropsfunktionen som anropas när klienten får en felstatus från servern

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Skapa en klient

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ta bort en DHCPv6-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad DHCPv6-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DHCPv6-borttagning

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger klientens nätverksgränssnitt för DHCPv6

### <a name="prototype"></a>Prototyp

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Description

Den här tjänsten anger klientens nätverksgränssnitt för kommunikation med DHCPv6-servrarna till det angivna indatagränssnittsindexet.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

- **interface_index** Index som anger nätverksgränssnitt

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) har angetts

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_INVALID_INTERFACE (0x4C) Ogiltiga gränssnittsindexindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger måladressen som DHCPv6-meddelandet ska skickas till

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Description

Den här tjänsten anger måladressen som DHCPv6-meddelandet ska skickas till. Som standard är ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **destination_address** Måladress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har angetts

- NX_PTR_ERROR (0x07) Ogiltig pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) Parameterfel

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa klientens DUID-objekt

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Description

Den här tjänsten skapar Klient-DUID med indataparametrarna. Om tidsinmatningen inte anges och duid-typen anger länkskikt med tid, anger den här funktionen en tid som innehåller en slumpmässig faktor för unikhet. Leverantörs tilldelade (företags)duid-typer stöds inte.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **duid_type** Typ av DUID (maskinvara, företag osv.)

- **hardware_type** Nätverksmaskinvara, t.ex. IEEE 802

- **tid** Värde som används för att skapa unik identifierare

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klient-DUID har skapats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltiga icke-pekarindata

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID-typ okänd eller stöds inte 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID-maskinvarutyp okänd eller stöds inte

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Lägga till en identitetsassociat till klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Description

Den här tjänsten är identisk med *den nx_dhcpv6_add_client_ia* tjänsten. Den lägger till en klientidentitetsassociaty genom att fylla i klientposten med de angivna parametrarna. Om du vill begära maximal önskad och giltig livslängd anger du dessa parametrar till oändlighet. Om du vill lägga till fler än en IA till en DHCPv6-klient anger du NX_DHCPV6_MAX_IA_ADDRESS till ett värde som är högre än standardvärdet 1.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **ipv6_address** Pekare till NETX Duo IP-adressblock

- **preferred_lifetime** Hur lång tid det tar innan IP-adressen blir inaktuell

- **valid_lifetime** Hur lång tid det tar innan IP-adressen upphör att gälla

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klient-IA har lagts till

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicerad IA-adress 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA överskrider det högsta antal IAs-klienter som kan lagras

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Ogiltig (t.ex. null) IA-adress i IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltiga icke-pekarindata


### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa en identitetsassociaty (icke-tillfällig) för klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Description

Den här tjänsten skapar en IANA (Client Non Temporary Identity Association) från de angivna parametrarna. Om du vill ange T1- och T2-gångerna till maximum (oändlighet) i DHCPv6-klientbegäranden anger du dessa parametrar till NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> En klient har bara en IANA.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **IA_ident** Unik identifierare för identitetsassociaty

- **T1** När klienten måste starta förnyelsen av IPv6-adressen

- **T2** När klienten måste starta omkopplingen avIPv6-adressen

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IANA har skapats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Lägga till en identitetsassociat till klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Description

Den här tjänsten lägger till en klientidentitetsassociaty genom att fylla i klientposten med de angivna parametrarna. Om du vill begära maximal önskad och giltig livslängd anger du dessa parametrar till oändlighet. Om du vill lägga till fler än en IA till en DHCPv6-klient anger du NX_DHCPV6_MAX_IA_ADDRESS till ett värde som är högre än standardvärdet 1.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **ipv6_address** Pekare till NETX Duo IP-adressblock

- **preferred_lifetime** Hur lång tid det tar innan IP-adressen blir inaktuell

- **valid_lifetime** Hur lång tid det tar innan IP-adressen upphör att gälla 

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klient-IA har lagts till

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicerad IA-adress 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA överskrider det högsta antal IAs-klienter som kan lagras

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Ogiltig (t.ex. null) IA-adress i IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltiga icke-pekarindata

 
### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar tids-ID från Klientens DUID

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Description

Den här tjänsten hämtar tids-ID-fältet från Klientens DUID. Om programmet först måste anropa *nx_dhcpv6_create_client_duid*, för att fylla i Client DUID i DHCPv6-klientinstansen, eller om det har ett null-värde för det här fältet. Avsikten är att programmet ska spara dessa data och presentera samma Klient-DUID för servern, inklusive tidsfältet, vid omstarter.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **time_id** Pekare till fältet Klientens DUID-tid

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IP-låndata har hämtats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten hämtar klientens globala IPv6-adress. Om klienten inte har en giltig adress returneras en felstatus. Om en klient har fler än en global IPv6-adress returneras den primära IPv6-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **ip_address** Pekare till IPv6-adress

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IPv6-adress har tilldelats

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6-adressen är inte giltig

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar klientens tidsdata för IA-adresslån

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Description

Den här tjänsten hämtar klientens globala IA-adresstidsdata. Om klientens IA-adressstatus är ogiltig anges tidsdata till noll och slutförandestatusen returneras. Om en klient har fler än en global IPv6-adress returneras primära IA-adressdata.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **T1** Pekare till förnyelsetid för IA-adress

- **T2** Pekare till tid för ombindning av IA-adress

- **preferred_lifetime** Pekare till tidpunkt när IA-adressen är inaktuell

- **valid_lifetime** Pekare till tidpunkt när IA-adressen har upphört att gälla

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IA-låndata har hämtats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämta klientens IANA-lånetidsdata

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Description

Den här tjänsten hämtar klientens globala IA-NA-lånetidsdata (T1 och T2). Om ingen av klienternas IA-NA-adresser har en giltig adressstatus anges tiden till noll och slutförandestatusen returneras. Om en klient har fler än en global IPv6-adress returneras primära IA-adressdata.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **T1** Pekare till tid för att starta låneförnyelse

- **T2** Pekare till tid för att starta återbindning av lån

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IANA-lånedata hämtades

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten hämtar antalet klientens giltiga IPv6-adresser. En giltig IPv6-adress är bunden (tilldelad) till klienten och registreras med IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **address_count** Pekare till antalet adresser som ska returneras

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IANA-lånedata hämtades

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

Hämta klientens IA-data efter adressindex

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Description

Den här tjänsten hämtar klientens IA-adress och lånar data efter adressindex. Om ett ogiltigt index anges, eller om IPv6-adressen vid det indexet inte är giltig, returnerar tjänsten en NX_DHCPV6_IA_ADDRESS_NOT_VALID felstatus.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **address_index** Indexera till DHCPv6 IA-tabell

- **ip_address** Pekare till IPv6-adress som ska hämtas

- **preferred_lifetime** Pekare till tidpunkt när IA-adressen är inaktuell

- **valid_lifetime** Pekare till tidpunkt när IA-adressen har upphört att gälla

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IANA-data har hämtats

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Ett ogiltigt index eller ingen giltig IPv6-adress för det angivna indexet 

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar DNS-serveradressen 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Description

Den här tjänsten hämtar DNS-serverns IPv6-adressdata vid det angivna indexet i klientlistan. Om listan inte innehåller en serveradress i indexet returneras ett fel. Indexet får inte överskrida storleken på DNS-serverlistan som anges av det användarkonfigurerbara alternativet NX_DHCPV6_NUM_DNS_SERVERS.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **index** Indexera till DNS-serverlistan

- **server_address** Pekare till serveradressbuffert

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Adressen har hämtats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar DHCPv6-alternativdata 

### <a name="prototype"></a>Prototyp

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Description

Den här tjänsten hämtar DHCPv6-alternativdata från ett DHCPv6-meddelande för den angivna alternativkoden.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **alternativkod** Alternativkod som data ska hämtas för

- **buffert** Pekare till buffert för att kopiera data till 

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Alternativdata har hämtats

- **NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Alternativkod som inte stöds

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_DHCPV6_PARAM_ERROR (0xE93) Ogiltiga icke-pekarindata

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar tid som ackumuleras på klientens IP-adresslån

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den tid som påförs på klientens IPv6-adresslån. Funktionen kontrollerar den första giltiga adressen för alla IPv6-adresser som tilldelats klienten. Om inga giltiga adresser hittas returneras ett nollvärde för upplupen tid.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

- **time_accrued** Pekare till tid som ackumuleras i IP-lån

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Upplupen tid har hämtats

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar tidsserveradress 

### <a name="prototype"></a>Prototyp

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Description

Den här tjänsten hämtar tidsserverns IPv6-adressdata vid det angivna indexet i klientlistan. Om listan inte innehåller en serveradress i indexet returneras ett fel. Indexet får inte överskrida storleken på listan Tidsserver anges av det användarkonfigurerbara alternativet NX_DHCPV6_NUM_TIME_SERVERS.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

- **index** Indexera till tidsserverlistan

- **server_address** Pekare till serveradressbuffert

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** -adress (0x00) har hämtats

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten initierar om klienten för att starta om DHCPv6-tillståndsdatorn och köra DHCPv6-protokollet igen. Detta är inte nödvändigt om klienten inte tidigare har startat DHPCv6-tillståndsdatorn eller har tilldelats några IPv6-adresser. Adresserna som sparats till DHCPv6-klienten och som registrerats med IP-instansen rensas båda.

> [!NOTE]
> Programmet måste fortfarande starta DHCPv6-klienten med hjälp *nx_dhcpv6_start-tjänsten* och påbörja begäran om IPv6-adresstilldelning genom att *anropa nx_dhcpv6_request_solicit*.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00)-adressen har tagits bort

- **NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6-klienten körs redan

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Bearbeta klientens CONFIRM-tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar en CONFIRM-begäran. Om ett svar tas emot från servern uppdaterar DHCPv6-klienten sina låneparametrar med mottagna data.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) CONFIRM-meddelandet har skickats och bearbetats

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Bearbeta klientens INFORM REQUEST-tillstånd

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett meddelande om inform-begäran. Om ett svar tas emot bearbetas svaret när det tas emot för att fastställa att det är giltigt och servern har beviljat begäran. Klientinstansen uppdateras sedan med serverinformationen efter behov.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstansen

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) INFORM REQUEST-meddelandet har skapats och bearbetats

- NX_PTR_ERROR (0x16) Ogiltig pekarindata

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Lägg till DNS-server till DHCPv6-alternativbegäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till alternativet för att begära DNS-serverinformation till DHCPv6-alternativbegäran. Om serversvaret innehåller DNS-serverdata lagrar klienten DNS-servern om den har utrymme att göra det. Antalet DNS-servrar som klienten kan lagra bestäms av det konfigurerbara alternativet NX_DHCPV6_NUM_DNS_SERVERS vars standardvärde är 2.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS-server ingår

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Alternativet Lägg till fullständigt domännamn i listan Alternativbegäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Description

Den här tjänsten lägger till alternativet för att lägga till det fullständiga domännamnet för klienten i DHCPv6-alternativbegäran. Det finns tre alternativ för FQDN-alternativet:

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Uppdatera FQDN-till-IPv6-adressmappningen för det FQDN och de adresser som används av klienten.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Uppdatera FQDN-till-IPv6-adressmappningen för FQDN och adresser som används av klienten till servern.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Begär att servern inte utför några DNS-uppdateringar för klientens räkning.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **domain_name** Sträng som innehar domännamnet

- **op** Typ av FQDN-alternativ som ska användas (se listan ovan)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) FQDN ingår

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Alternativ för att lägga till domännamn i DHCPv6-alternativbegäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till alternativet domännamn i alternativbegäran i meddelanden om klientbegäran. Om serversvaret innehåller domännamnsdata lagrar klienten domännamnsinformationen om storleken på domännamnet ligger inom buffertstorleken för att lagra domännamnet. Den här buffertstorleken är ett konfigurerbart alternativ (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) med ett standardvärde på 30 byte.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Alternativuppsättning för domännamn

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange tidsserverdata som valfri begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till alternativet för tidsserverinformation i alternativbegäran för meddelanden om klientbegäran. Om serversvaret innehåller tim-serverdata lagrar klienten tidsservern om den har utrymme att göra det. Antalet tidsservrar som klienten kan lagra bestäms av det konfigurerbara alternativet

NX_DHCPV6_NUM_TIME _SERVERS vars standardvärde är 1.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Tidsserveralternativet har lagts till

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange tidszonsdata som valfri begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten lägger till alternativet för att begära tidszonsinformation till begäran om klientalternativ. Om serversvaret innehåller tidszonsdata lagrar klienten tidszonsinformationen om tidszonens storlek ligger inom buffertstorleken för tidszonen. Den här buffertstorleken är ett konfigurerbart alternativ (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) med ett standardvärde på 10 byte.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Alternativet Tidszon har lagts till

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skicka ett DHCPv6 RELEASE-meddelande

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett RELEASE-meddelande i klientnätverket. Om meddelandet har skickats returneras en lyckad status. Ett lyckat slutförande innebär inte att klienten har fått ett svar eller har beviljats en IPv6-adress ännu. DHCPv6-klientens tråduppgift väntar på svar från en DHCPv6-server. Om ett tas emot kontrollerar det att svaret är giltigt och lagrar data till klientposten.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) VERSION har skickats

- **NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6-klientuppgiften startades inte

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Adress som inte är bunden till klienten

- **NX_INVALID_INTERFACE** (0x4C) Hittades inte i IP-adresstabellen

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skicka ett MEDDELANDE OM begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar ut ett MEDDELANDE OM begäran i nätverket. Om meddelandet har skickats returneras en lyckad status. Ett lyckat slutförande innebär inte att klienten har fått ett svar eller har beviljats en IPv6-adress ännu. DHCPv6-klientens tråduppgift väntar på ett svar (ett ADVERTISE-meddelande) från en DHCPv6-server. Om ett tas emot kontrollerar det att svaret är giltigt, lagrar data till klientposten och befordrar klienten till tillståndet REQUEST.

> [!NOTE] 
> Om alternativet Snabb genomförande har angetts, kommer DHCPv6-klienten att gå direkt till det bundna tillståndet om den tar emot ett giltigt meddelande server ANNONSERa. Mer information finns i *nx_dhcpv6_request_solicit_rapid* tjänstbeskrivning.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) BEGÄRD meddelande har skickats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Skicka ett MEDDELANDE OM begäran med alternativet Snabb genomförande

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar ut ett MEDDELANDE OM begäran i nätverket med alternativet Snabb genomförande inställt. Om meddelandet har skickats returneras en lyckad status. Ett lyckat slutförande innebär inte att klienten har fått ett svar eller har beviljats en IPv6-adress ännu. DHCPv6-klientens tråduppgift väntar på ett svar (ett ADVERTISE-meddelande) från en DHCPv6-server. Om ett tas emot kontrollerar det att svaret är giltigt, lagrar data till klientposten och befordrar klienten till BOUND-tillståndet.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) BEGÄRD meddelande har skickats

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Återuppta DHCPv6-klientuppgiften 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten återupptar DHCPv6-klienttrådaktiviteten. Det aktuella DHCPv6-klienttillståndet bearbetas (t.ex. bound, solicit)

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har återupptagits

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger den tid som påförs på klientens IP-adresslån

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Description

Den här tjänsten anger den tid som påförs klientens globala IP-adress sedan den tilldelades av servern. Detta bör endast användas om en klient för närvarande är bunden till en tilldelad IPv6-adress.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

- **time_accrued** Tid som påförs i IP-lån

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Tid som ackumulerats har angetts

- NX_PTR_ERROR (0x16) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta DHCPv6-klientuppgiften 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar DHCPv6-klientuppgiften och förbereder klienten för att köra DHCPv6-protokollet. Den verifierar att klientinstansen har tillräckligt med information (till exempel ett klient-DUID), skapar och binder UDP-socketen för att skicka och ta emot DHCPv6-meddelanden och aktiverar timers för att hålla reda på sessionstid och när det aktuella IPv6-lånet går ut.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har startats

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Klienten saknar nödvändiga alternativ

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Stoppa DHCPv6-klientuppgiften 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar DHCPv6-klientaktiviteten och rensar antal återöverföringar, maximalt återöverföringsintervall, inaktiverar timers för sessions- och låneförfallotid och tar bort bindningar för DHCPv6-klientens socketport. Om du vill starta om klienten måste du först stoppa och eventuellt initiera om klienten innan du startar en till session med en DHCPv6-server. Mer information finns i avsnittet Litet exempel.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har stoppats

- **NX_DHCPV6_NOT_STARTED** (0xE92) Klienttråden startades inte

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden


### <a name="allowed-from"></a>Tillåts från

Trådar

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

Pausa DHCPv6-klientuppgiften 

### <a name="prototype"></a>Prototyp

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Description

Den här tjänsten pausar DHCPv6-klientuppgiften och eventuella förfrågningar som gjordes mitt under bearbetningen. Timers inaktiveras och klienttillståndet är inställt på icke-körs.

### <a name="input-parameters"></a>Indataparametrar

- **dhcpv6_ptr** Pekare till DHCPv6-klientinstans

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har inaktiverats

- **NX_DHCPV6_NOT_STARTED** (0XE92) Klienten körs inte så kan inte pausas

- NX_PTR_ERROR (0x16) Ogiltig pekare

- NX_CALLER_ERROR (0x11) Måste anropas från tråden

### <a name="allowed-from"></a>Tillåts från

Trådar

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
