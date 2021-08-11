---
title: Kapitel 4 – Azure RTOS NetX Duo DHCPv6-servertjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6Server-tjänster
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf6b43f70a7159af6c24496ec2ae2276d5e271af2ad3af99687181df3bf6be6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792034"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Kapitel 4 – Azure RTOS NetX Duo DHCPv6-servertjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6Server-tjänster (anges nedan).

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

- nx_dhcpv6_server_create skapa *en DHCPv6-serverinance*
- nx_dhcpv6_server_delete Ta *bort en DHCPv6-server*
- nx_dhcpv6_server_start starta *DHCPv6-serveraktiviteten*
- nx_dhcpv6_server_suspend *pausa DHCPv6-serveraktiviteten*
- nx_dhcpv6_server_resume återuppta *DHCPv6-klientbearbetning*
- nx_dhcpv6_server_suspend *pausa DHCPv6-klientbearbetning*
- nx_dhcpv6_create_dns_address Ange *DNS-servern för alternativbegäranden*
- nx_dhcpv6_create_ip_address_range Skapa *det IP-adressintervall som ska lånas ut*
- nx_dhcpv6_reserve_ip_address_range *reservera ip-adressintervall i serverlistan*
- nx_dhcpv6_set_server_duid *Ange Server DUID för DHCPv6-paket*
- nx_dhcpv6_add_ip_address_lease Lägga *till en lånepost i DHCPv6-servertabellen*
- Nx_dhcpv6_retrieve_ip_address_lease Hämta *en IP-lånepost från servertabellen*
- nx_dhcpv6_add_client_record lägga *till en DHCPv6-klientpost i servertabellen*
- nx_dhcpv6_retrieve_client_record Hämta *en klientpost från servertabellen*
- nx_dhcpv6_server_interface_set Ange *gränssnittsindex för Server DHCPv6-tjänster*
- nx_dhcpv6_server_option_request_handler_set *Ange hanteraren för alternativbegäran*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Ange nätverkets DNS-server

**Prototyp**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**Beskrivning**

Den här tjänsten läser in DHCPv6-servern med DNS-serveradressen för server-DHCPv6-nätverksgränssnittet.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **dns_ipv6_address** Pekare till DNS-servern

**Returvärden**

- **NX_SUCCESS** (0x00) DNS-servrar som sparats till DHCPv6-serverinstansen
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) En ogiltig adress har angetts
- NX_PTR_ERROR (0x16) Ogiltig pekarindata

**Tillåts från**

Programkod

**Exempel**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>Skapa listan med SERVER-IP-adresser

**Prototyp**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Beskrivning**

Den här tjänsten skapar ip-adresslistan som anges av start- och slutadresserna för serverns tilldelningsbara adressintervall. Start- och slutadresserna måste matcha servergränssnittets adressprefix (måste finnas på samma länk som server-DHCPv6-gränssnittet). Det antal adresser som faktiskt har lagts till returneras.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **start_ipv6_address** Start för adresser som ska läggas till
- **end_ipv6_address** Slut på adresser som ska läggas till
- ***addresses_added** Utdata från tillagda adresser

**Returvärden**

- **IP-NX_SUCCESS** (0x00) har skapats
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) En ogiltig adress har angetts
- NX_PTR_ERROR (0x16) Ogiltig pekarindata

**Tillåts från**

Programkod

**Exempel**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>Reservera angivet intervall med IP-adresser

**Prototyp**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Beskrivning**

Den här tjänsten reserverar det IP-adressintervall som anges av start- och slutadresserna. De här adresserna måste finnas inom det tidigare skapade server-IP-adressintervallet. Dessa adresser tilldelas inte till några klienter av DHCPv6-servern. Start- och slutadresserna måste matcha servergränssnittets adressprefix (måste finnas på samma länk som server-DHCPv6-nätverksgränssnittet). Antalet adresser som faktiskt är reserverade returneras.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **start_ipv6_address** Start för adresser som ska reserveras
- **end_ipv6_address** Slut på adresser som ska reserveras
- ***addresses_reserved** Antal reserverade adresser

**Returvärden**

- **NX_SUCCESS** (0x00) RELEASE-meddelandet har skapats och bearbetats
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) En ogiltig adress har angetts
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Startadressen hittades inte i listan Serveradress.
- NX_PTR_ERROR (0x16) Ogiltig pekarindata

**Tillåts från**

Programkod

**Exempel**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>Skapa DHCPv6-serverinstansen 

**Prototyp**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**Beskrivning**

Den här tjänsten skapar DHCPv6-serveruppgiften med angivna indata. Motringningarna är valfria indata. Stackpekaren, IP-instansen och indata för paketpoolen krävs. IP-instansen och paketpoolen måste redan skapas.

Användaren uppmanas att anropa nx_dhcpv6_server_option_request_handler_set för att ange hanteraren för alternativbegäran.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **ip_ptr** Pekare till IP-instansen
- **name_str** Pekare till servernamn
- **packet_pool_ptr** Pekare till serverpaketpool
- **stack_ptr** Pekare till serverstackens minne
- **stack_size** Storleken på serverstackens minne
- **dhcpv6_address_declined_handler** Pekare till klientens nekande eller meddelandehanterare för version
- **dhcpv6_option_request_handler** Pekare till alternativ hanteraren för begärandealternativ

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har återupptagits
- NX_PTR_ERROR (0x16) Ogiltig pekarindata
- NX_DHCPV6_PARAM_ERROR Ogiltiga indata som inte pekare

**Tillåts från**

Programkod

**Exempel**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>Ta bort DHCPv6-servern

**Prototyp**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten tar bort DHCPv6-serveruppgiften och alla förfrågningar som servern bearbetar.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har tagits bort
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Trådar

**Exempel**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>Återuppta DHCPv6-serveruppgiften 

**Prototyp**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten återupptar DHCPv6-serveruppgiften och alla förfrågningar som servern bearbetar.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har återupptagits
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) Servern körs redan
- **status** (variabel) Felstatus för ThreadX och NetX Duo
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Trådar

**Exempel**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Pausa DHCPv6-serveraktivitet 

**Prototyp**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten pausar DHCPv6-serveruppgiften och alla förfrågningar som servern bearbetar.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har återupptagits
- **NX_DHCPV6_NOT_STARTED** (0xE92) Servern har inte startats 
- **Status** (variabel) Felstatus för ThreadX och NetX Duo
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Trådar

**Exempel**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>Starta DHCPv6-serveruppgiften 

**Prototyp**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten startar DHCPv6-serveruppgiften och läser servern för att bearbeta programbegäranden för att ta emot DHCPv6-klientmeddelanden. Den verifierar att serverinstansen har tillräckligt med information (Server DUID), skapar och binder UDP-socketen för att skicka och ta emot DHCPv6-meddelanden och aktiverar timers för att hålla reda på sessionstid och IP-lånetid.

>[!NOTE] 
> Innan DHCPv6-servern kan köras ansvarar värdprogrammet för att skapa IP-adressintervallet som servern kan tilldela IP-adresser från. Det ansvarar också för att ställa in server-DUID- och DHCPv6-gränssnittet *(se nx_dhcpv6_server_duid_set* *respektive nx_dhcpv6_server_interface_set).*

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har startats
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) Servern körs redan
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server har inga tilldelningsbara adresser att låna ut
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Globalt adressindex har inte angetts
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) Ingen SERVER DUID har skapats 
- **status** (variabel) Felstatus för ThreadX och NetX Duo
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Trådar

**Exempel**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Hämta ett IP-adresslån från servertabellen

**Prototyp**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Beskrivning**

Den här tjänsten hämtar en IP-adresslånpost från servertabellen på den angivna tabellens indexplats. Detta kan göras före eller efter hämtning av klientpostdata.

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-beständigt minne är ett krav i DHCPv6-protokollet. Det spelar ingen roll i vilken ordning IP-lånedata och klientpostdata sparas i icke-volatilt minne.

>[!NOTE] 
> Vi rekommenderar inte att du kopierar data till eller från servertabeller utan att stoppa eller pausa DHCPv6-servern först.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **table_index** Tabellindex för lagring av lån på
- **lease_IP_address** Pekare till IP-adress som lånats ut till klienten
- **T1** Klienten begärde förnyelsetid
- **T2** Klienten begärde bindningstid
- **valid_lifetime** Klientlånet blir inaktuellt
- **preferred_lifetime** Klientlånet blir ogiltigt

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har startats
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) Ogiltiga indata för IP-lån
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Programkod

**Exempel**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Lägga till ett IP-adresslån i servertabellen

**Prototyp**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Beskrivning**

Den här tjänsten läser in IP-lånedata från en tidigare DHCPv6-serversession från icke-beständigt minne till tabellen För serverlån. Detta är inte nödvändigt om servern körs för första gången och inte har några tidigare lånedata. Om så är fallet måste värdprogrammet skapa ett IP-adressintervall för att tilldela IP-adresser med hjälp *av nx_dhcpv6_create_ip_address_range tjänsten.* Data räcker för att rekonstruera en DHCPv6-lånepost. Tabellindexet behöver inte anges. Om det är 0xFFFFFFFF (oändlighet) hittar DHCPv6-servern nästa tillgängliga plats att kopiera data till.

>[!NOTE] 
> Överföring av IP-lånedata MÅSTE göras innan klientposter laddas upp. båda MÅSTE göras innan (åter)startar DHCPv6-servern.

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-beständigt minne är ett krav i DHCPv6-protokollet.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **table_index** Tabellindex för lagring av lån på
- **lease_IP_address** Pekare till IP-adress som lånats ut till klienten
- **T1** Klienten begärde förnyelsetid
- **T2** Klienten begärde bindningstid
- **valid_lifetime** Klientlånet blir inaktuellt
- **preferred_lifetime** Klientlånet blir ogiltigt

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har startats
- **NX_DHCPV6_TABLE_FULL** (0xEC4) Inget utrymme för mer lånedata**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lånedata verkar inte finnas på länken med server-DHCPv6-gränssnittet
- **NX_DHCPV6_PARAM_ERROR** (0xE93) Ogiltig indata för IP-lån
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Programkod

**Exempel**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>Lägga till en klientpost i servertabellen

**Prototyp**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**Beskrivning**

Den här tjänsten kopierar klientdata från icke-beständigt minne till servertabellen en post i taget. Detta är bara nödvändigt om servern startas om och har klientdata från en tidigare session för att återställa från minnet. Om en server inte har några tidigare data initierar DHCPv6-servern klienttabellen för att kunna lägga till klientposter.

Du behöver inte ange tabellindexet. Om det är 0xFFFFFFFF (oändlighet) letar DHCPv6-servern upp nästa tillgängliga plats. DHCPv6-servern kan rekonstruera en klientpost från dessa data.

>[!NOTE] 
> Värdprogrammet MÅSTE ladda upp IP-lånedata före klientpostdata. Detta är så att DHCPv6-servern internt kan korslänka tabellerna så att varje klientpost är ansluten med motsvarande IP-lånepost i sina respektive tabeller. Se *nx_dhcpv6_add_ip_address_lease* information om hur du laddar upp IP-lånedata från minnet.

>[!NOTE] 
> Beroende på DUID-typ måste inte alla data anges. Om en klient till exempel har en leverantör tilldelad DUID-typ kan den skicka in noll för PARAMETRAR för DUID-länkskikt (MAC-adress, maskinvarutyp, DUID-tid).

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-beständigt minne är ett krav i DHCPv6-protokollet.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har startats
- **NX_ INVALID_PARAMETERS** (0x4D) Ogiltiga indata som inte pekare**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) Inga tomma platser kvar för att lägga till en annan klientpost
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Klientadressen hittades inte i tabellen Serverlån.
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Programkod

**Exempel**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>Hämta en klientpost från servertabellen

**Prototyp**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**Beskrivning**

Den här tjänsten kopierar viktiga data från serverns klientposttabell för lagring till icke-beständigt minne. Servern kan rekonstruera en lämplig klientpost från sådana data i omvänd process (ladda upp data till servertabellen). Oavsett DUID-typ kan ingen av pekarna vara NULL-pekare. data initieras till noll för alla parametrar. Om client DUID-typen till exempel är Link Layer Plus Time returneras leverantörsnumret som noll och det privata ID:t är en tom sträng.

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-beständigt minne är ett krav i DHCPv6-protokollet. Det spelar ingen roll i vilken ordning IP-lånedata och klientpostdata sparas i icke-volatilt minne.

>[!NOTE] 
> Vi rekommenderar inte att du kopierar data till eller från servertabeller utan att stoppa eller pausa DHCPv6-servern först.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **table_index** Indexera till serverns klienttabell
- **message_xid** Transaktions-ID för klientserver
- **client_address** IPv6-adress som lånats ut till klienten
- **client_state** Klientens DHCPv6-tillstånd (t.ex. bunden)
- **IP_lease_time_accrued** Tiden har gått ut när lånet redan **dhcpv6_server_ptr** pekaren till DHCPv6-servern
- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har startats
- **NX_DHCPV6_INVALID_DUID** (0xECC) Ogiltiga eller inkonsekventa DUID-data
- **NX_PTR_ERROR** (0x16) Ogiltig pekare
- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata

**Tillåts från**

Programkod

**Exempel**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Ange gränssnittsindexet för server-DHCPv6-gränssnittet

**Prototyp**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Beskrivning**

Den här tjänsten anger nätverksgränssnittet där DHCPv6-servern hanterar DHCPv6-klientbegäranden. Inte för versioner av NetX Duo som inte stöder multihome, är gränssnittsvärdet noll som standard. Det globala adressindexet är nödvändigt för att hämta serverns globala adress i dess DHCPv6-gränssnitt. Detta används av DHCPv6-logiken för att säkerställa att lånadresser och andra DHCPv6-data finns på länken till DHCPv6-servern.

Detta måste anropas innan DHCPv6-servern startas, även för program på enskilda homed-enheter eller utan multihome-stöd.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **iface_index** Server-DHCPv6-servergränssnitt
- **ga_address_index** Index för serverns globala adress i tabellen Server-IP-instansadress

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har startats
- **NX_INVALID_INTERFACE** (0x4C) Gränssnittet finns inte
- NX_NO_INTERFACE_ADDRESS (0x50) Globalt index överskrider ip-instansens maximala IPv6-adresser (NX_MAX_IPV6_ADDRESSES)
- NX_PTR_ERROR (0x16) Ogiltig pekare

**Tillåts från**

Programkod

**Exempel**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Ange Server DUID för DHCPv6-paket

**Prototyp**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Beskrivning**

Den här tjänsten anger Server DUID och måste anropas innan värdprogrammet startar servern. För DUID-typer för länkskikt och länkskikt måste värdprogrammet ange maskinvarutyp och MAC-adressdata. För duID:er för länklagertid måste tidspekaren peka på en giltig tid. Antalet sekunder sedan den 1 januari 2000 är ett typiskt startvärde. Om DuID-typen för server är företaget, leverantörs tilldelad typ, skapas DUID från de användarkonfigurerbara alternativen NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID och NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, och värdena för tid och MAC-adress kan anges till NULL.

>[!NOTE] 
> Det är värdprogrammets ansvar att spara server-DUID-parametrarna till icke-volatilt minne så att samma DUID används i meddelanden till klienter mellan omstarter. Detta är ett krav för DHCPv6-protokollet (RFC 3315).

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **duid_type** DHCPv6 Server DUID-typ
- **hardware_type** Maskinvarutyp (t.ex. Ethernet)
- **mac_address_msw** Pekare till DHCPv6-server
- **mac_address_lsw** Pekare till DHCPv6-server
- **tid** Tidsvärde för DUID

**Returvärden**

- **NX_SUCCESS** (0x00) Har pausat servern
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) DUID-typ som inte stöds
- **NX_INVALID_PARAMETERS** (0x4D) Ogiltiga icke-pekarindata
- NX_PTR_ERROR (0x16) Ogiltig pekarindata

**Tillåts från**

Programkod

**Exempel**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Ange hanteraren för alternativbegäran för DHCPv6-serverinstansen 

**Prototyp**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**Beskrivning**

Den här tjänsten anger DHCPv6-serverns hanterare för utökade alternativbegäran.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **dhcpv6_option_request_handler_extended** Pekare till begärandehanteraren för utökade alternativ

**Returvärden**

- **NX_SUCCESS** (0x00) Servern har återupptagits
- NX_PTR_ERROR (0x16) Ogiltig pekarindata

**Tillåts från**

Programkod

**Exempel**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```