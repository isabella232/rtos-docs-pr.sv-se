---
title: Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-server tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6Server-tjänster
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826028"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Kapitel 4 – Azure återställnings tider NetX Duo DHCPv6-server tjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo DHCPv6Server-tjänster (visas nedan).

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- nx_dhcpv6_server_create *skapa en DHCPv6-serverinstance*
- nx_dhcpv6_server_delete *ta bort ett DHCPv6-serverinstance*
- nx_dhcpv6_server_start *starta aktiviteten DHCPv6-server*
- nx_dhcpv6_server_suspend *pausa aktiviteten DHCPv6-server*
- nx_dhcpv6_server_resume *återuppta DHCPV6-klient bearbetning*
- nx_dhcpv6_server_suspend *pausa DHCPV6-klient bearbetning*
- nx_dhcpv6_create_dns_address *ställa in DNS-servern för Options-begäranden*
- nx_dhcpv6_create_ip_address_range *skapa intervallet av IP-adresser som ska lånas*
- nx_dhcpv6_reserve_ip_address_range *reserv intervall med IP-adresser i Server listan*
- nx_dhcpv6_set_server_duid *ange serverns DUID för DHCPv6-paket*
- nx_dhcpv6_add_ip_address_lease *lägga till en låne post i DHCPv6-server tabellen*
- Nx_dhcpv6_retrieve_ip_address_lease *Hämta en IP-adresslån från Server tabellen*
- nx_dhcpv6_add_client_record *lägga till en DHCPV6-klient post i Server tabellen*
- nx_dhcpv6_retrieve_client_record *Hämta en klient post från Server tabellen*
- nx_dhcpv6_server_interface_set *Ange gränssnitts index för serverns DHCPv6-tjänster*
- nx_dhcpv6_server_option_request_handler_set *Ange hanteraren för Options-begäran*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Ange nätverks-DNS-Server

**Prototyp**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**Beskrivning**

Den här tjänsten läser in DHCPv6-servern med DNS-serveradressen för serverns DHCPv6-nätverks gränssnitt.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **dns_ipv6_address** Pekare till DNS-servern

**Retur värden**

- **NX_SUCCESS** (0X00) DNS-Serversaved till DHCPv6-serverinstansen
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) en ogiltig adress har angetts
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

**Exempel**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>Skapa serverns IP-adress lista

**Prototyp**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Beskrivning**

Den här tjänsten skapar IP-adress listan som anges av start-och slut adresserna för serverns tilldelnings bara adress intervall. Start-och slut adresserna måste överensstämma med adressprefixet för Server gränssnittet (måste finnas på samma länk som serverns DHCPv6-gränssnitt). Antalet adresser som faktiskt har lagts till returneras.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **start_ipv6_address** Början av adresser som ska läggas till
- **end_ipv6_address** Slut på adresser som ska läggas till
- ***addresses_added** Utdata från adresser har lagts till

**Retur värden**

- **NX_SUCCESS** (0X00) IP-adress lista har skapats
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) en ogiltig adress har angetts
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

**Exempel**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>Reservera angivet intervall av IP-adresser

**Prototyp**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Beskrivning**

Den här tjänsten reserverar det IP-adressintervall som anges av start-och slut adresserna. Dessa adresser måste ligga inom det tidigare skapade Server-IP-adressintervallet. Dessa adresser kommer inte att tilldelas till några klienter av DHCPv6-servern. Start-och slut adresserna måste överensstämma med adressprefixet för Server gränssnittet (måste finnas på samma länk som serverns DHCPv6-nätverks gränssnitt). Antalet adresser som faktiskt reserver ATS returneras.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **start_ipv6_address** Början av adresser som ska reserveras
- **end_ipv6_address** Slut på adresser som ska reserveras
- ***addresses_reserved** Antal reserverade adresser

**Retur värden**

- **NX_SUCCESS** (0X00) versions meddelandet har skapats och bearbetats
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) en ogiltig adress har angetts
- Det gick inte att hitta **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) med start adress i server adress listan.
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

**Exempel**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>Skapa DHCPv6-Server instansen 

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

Den här tjänsten skapar DHCPv6-servern med angivna inuppgifter. Återanrops hanterarna är valfria ingångar. Stack pekaren, indatamängden för IP-instansen och Packet-poolen krävs. IP-instansen och Packet-poolen måste redan ha skapats.

Användaren uppmanas att anropa nx_dhcpv6_server_option_request_handler_set för att ställa in option Request handler.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **ip_ptr** Pekare till IP-instansen
- **name_str** Pekare till Server namn
- **packet_pool_ptr** Pekare till Server paketets pool
- **stack_ptr** Pekare till serverns stack minne
- **stack_size** Storlek på serverns stack-minne
- **dhcpv6_address_declined_handler** Pekare till klienten nekar eller frigör meddelande hanterare
- **dhcpv6_option_request_handler** Pekare till alternativ hanteraren för begär ande alternativ

**Retur värden**

- **NX_SUCCESS** (0X00) servern har återupptagits
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare
- NX_DHCPV6_PARAM_ERROR ogiltiga inmatade pekare

**Tillåten från**

Program kod

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

Den här tjänsten tar bort aktiviteten DHCPv6-server och alla begär Anden som servern har bearbetat.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Retur värden**

- **NX_SUCCESS** (0x00)-servern har tagits bort
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Konversation

**Exempel**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>Återuppta DHCPv6-server uppgift 

**Prototyp**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten återupptar DHCPv6-server uppgiften och alla begär Anden som servern har bearbetat.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Retur värden**

- **NX_SUCCESS** (0X00) servern har återupptagits
- **NX_DHCPV6_ALREADY_STARTED** -servern (0xE91) körs redan
- **status** (variabel) ThreadX och netx Duo-fel status
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Konversation

**Exempel**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Pausa DHCPv6-server aktivitet 

**Prototyp**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten gör att DHCPv6-server aktiviteten stoppas och alla begär Anden om att servern har bearbetats.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Retur värden**

- **NX_SUCCESS** (0X00) servern har återupptagits
- **NX_DHCPV6_NOT_STARTED** -servern (0xE92) har inte startats 
- **Status** (variabel) ThreadX och netx Duo-fel status
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Konversation

**Exempel**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>Starta aktiviteten DHCPv6-server 

**Prototyp**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Beskrivning**

Den här tjänsten startar DHCPv6-server aktiviteten och läser servern för att bearbeta program begär Anden för att ta emot DHCPv6-klient meddelanden. Den verifierar att Server instansen har tillräckligt med information (Server-DUID), skapar och binder UDP-socketen för att skicka och ta emot DHCPv6-meddelanden och aktiverar timers för att hålla reda på sessionens tid och förfallo datum för IP-lån.

>[!NOTE] 
> Innan DHCPv6-servern kan köras ansvarar värd programmet för att skapa det IP-adressintervall som servern kan tilldela IP-adresser från. Det är också ansvarigt för att ställa in serverns DUID och DHCPv6-gränssnitt (se *nx_dhcpv6_server_duid_set* respektive *nx_dhcpv6_server_interface_set* .

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Retur värden**

- **NX_SUCCESS** (0X00) servern har startats
- **NX_DHCPV6_ALREADY_STARTED** -servern (0xE91) körs redan
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** -servern (0xEA7) har inga adresser som kan tilldelas till lån
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) inget globalt adress index har angetts
- **NX_DHCPV6_NO_SERVER_DUID** (0XE92) inget Server-DUID har skapats 
- **status** (variabel) ThreadX och netx Duo-fel status
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Konversation

**Exempel**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Hämta ett IP-adresslån från Server tabellen

**Prototyp**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Beskrivning**

Den här tjänsten hämtar en post för IP-adresslån från Server tabellen på den angivna tabell index platsen. Detta kan göras innan eller efter att klient post data har hämtats.

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet. Det innebär ingen skillnad i vilken ordning IP-adresslån data och klient post data sparas till icke-flyktigt minne.

>[!NOTE] 
> Vi rekommenderar inte att du kopierar data till eller från Server tabeller utan att stoppa eller pausa DHCPv6-servern först.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **table_index** Tabell index för att lagra lån på
- **lease_IP_address** Pekare till IP-adress som är lånad till klienten
- **T1** Klient begärd förnyelse tid
- **T2** Klienten begärde OMBINDNINGS tid
- **valid_lifetime** Klient lånet blir föråldrat
- **preferred_lifetime** Klient lånet blir ogiltigt

**Retur värden**

- **NX_SUCCESS** (0X00) servern har startats
- **NX_DHCPV6_PARAMETER_ERROR** (0XE93) ogiltiga indata från IP-adresslån
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

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

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Lägg till ett IP-adresslån till Server tabellen

**Prototyp**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Beskrivning**

Den här tjänsten läser in IP-adresslån från en tidigare DHCPv6-server-session från icke-flyktigt minne till Server leasing tabellen. Detta är inte nödvändigt om servern körs för första gången och inte har några tidigare låne data. Om detta är fallet måste värd programmet skapa ett IP-adressintervall för att tilldela IP-adresser med hjälp av tjänsten *nx_dhcpv6_create_ip_address_range*. Data räcker för att rekonstruera en DHCPv6-låne post. Tabell indexet behöver inte anges. Om värdet är 0xFFFFFFFF (oändlighet) kommer DHCPv6-servern att hitta nästa tillgängliga plats för att kopiera data till.

>[!NOTE] 
> Överföring av IP-adresslån måste göras innan klient poster överförs. båda måste utföras före (åter) start av DHCPv6-servern.

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **table_index** Tabell index för att lagra lån på
- **lease_IP_address** Pekare till IP-adress som är lånad till klienten
- **T1** Klient begärd förnyelse tid
- **T2** Klienten begärde OMBINDNINGS tid
- **valid_lifetime** Klient lånet blir föråldrat
- **preferred_lifetime** Klient lånet blir ogiltigt

**Retur värden**

- **NX_SUCCESS** (0X00) servern har startats
- **NX_DHCPV6_TABLE_FULL** (0XEC4) inget rum för fler låne data * *
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0XE95) låne data visas inte på länk med serverns DHCPv6-gränssnitt
- **NX_DHCPV6_PARAM_ERROR** (0XE93) ogiltiga indata från IP-adresslån
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

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

### <a name="add-a-client-record-to-the-server-table"></a>Lägga till en klient post i Server tabellen

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

Den här tjänsten kopierar klient data från icke-flyktigt minne till Server tabellen en post i taget. Detta är bara nödvändigt om servern startas om och har klient data från en tidigare session som ska återställas från minnet. Om en server saknar tidigare data initierar DHCPv6-servern klient tabellen för att kunna lägga till klient poster.

Du behöver inte ange tabell indexet. Om värdet är 0xFFFFFFFF (oändlighet) kommer DHCPv6-servern att hitta nästa tillgängliga plats. DHCPv6-servern kan rekonstruera en klient post från dessa data.

>[!NOTE] 
> Värd programmet måste ladda upp IP-adresslån innan klienten registrerar data. Detta är så att en intern DHCPv6-server kan korsa länkar tabellerna så att varje klient post är kopplad till motsvarande IP-adresslån i respektive tabell. Se *nx_dhcpv6_add_ip_address_lease* för information om hur du överför IP-adresslån från minnet.

>[!NOTE] 
> Inte alla data måste anges beroende på DUID-typ. Om till exempel en klient har tilldelats en leverantör som har tilldelats typen DUID, kan den skicka i noll för DUID-länk skikts parametrar (MAC-adress, maskin varu typ, DUID-tid).

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Retur värden**

- **NX_SUCCESS** (0X00) servern har startats
- **NX_ INVALID_PARAMETERS** (0X4D) ogiltig information om icke-pekare * *
- **NX_DHCPV6_TABLE_FULL** (0XEC4) inga tomma platser kvar för att lägga till en annan klient post
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0XEA8) kunde inte hitta en klient som har tilldelats adressen i serverns leasing tabell.
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

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

### <a name="retrieve-a-client-record-from-the-server-table"></a>Hämta en klient post från Server tabellen

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

Den här tjänsten kopierar viktiga data från serverns klient post tabell för lagring till beständigt minne. Servern kan konstruera om en lämplig klient post från sådana data i den omvända processen (Ladda upp data till Server tabellen). Oavsett DUID-typ kan ingen av punkterna vara NULL-pekare; data initieras till noll för alla parametrar. Om t. ex. klientens DUID-typ är länk skikt och tid returneras leverantörs numret som noll och det privata ID: t är en tom sträng.

Möjligheten att lagra och hämta data mellan DHCPv6-servern och icke-flyktigt minne är ett krav i DHCPv6-protokollet. Det innebär ingen skillnad i vilken ordning IP-adresslån data och klient post data sparas till icke-flyktigt minne.

>[!NOTE] 
> Vi rekommenderar inte att du kopierar data till eller från Server tabeller utan att stoppa eller pausa DHCPv6-servern först.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **table_index** Index i serverns klient tabell
- **message_xid** Transaktions-ID för klient server
- **client_address** IPv6-adress lånad till klient
- **client_state** Klientens DHCPv6-tillstånd (t. ex. Bound)
- **IP_lease_time_accrued** Tiden upphörde att gälla för lån **dhcpv6_server_ptr** pekare till Dhcpv6-servern
- **dhcpv6_server_ptr** Pekare till DHCPv6-server

**Retur värden**

- **NX_SUCCESS** (0X00) servern har startats
- **NX_DHCPV6_INVALID_DUID** (0XECC) ogiltiga eller inkonsekventa DUID-data
- **NX_PTR_ERROR** (0X16) ogiltigt inmatade pekare
- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

**Tillåten från**

Program kod

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

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Setthe Interface index för Server DHCPv6-gränssnittet

**Prototyp**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Beskrivning**

Den här tjänsten anger det nätverks gränssnitt där DHCPv6-servern hanterar DHCPv6-klient förfrågningar. För versioner av NetX Duo som inte har stöd för multihome är gränssnittets värde standard värdet noll. Det globala adress indexet krävs för att hämta serverns globala adress i DHCPv6-gränssnittet. Detta används av DHCPv6-logiken för att säkerställa att låne adresser och andra DHCPv6-data finns på länken till DHCPv6-servern.

Detta måste anropas innan DHCPv6-servern startas, även för program på enskilda enheter eller utan support för flera hem.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **iface_index** Serverns DHCPv6-server gränssnitt
- **ga_address_index** Index för serverns globala adress i adress tabellen för serverns IP-instans

**Retur värden**

- **NX_SUCCESS** (0X00) servern har startats
- **NX_INVALID_INTERFACE** -gränssnittet (0x4C) finns inte
- NX_NO_INTERFACE_ADDRESS (0x50) globalt index överskrider IP-instansens högsta IPv6-adresser (NX_MAX_IPV6_ADDRESSES)
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

**Exempel**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Ange serverns DUID för DHCPv6-paket

**Prototyp**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Beskrivning**

Den här tjänsten ställer in serverns DUID och måste anropas innan värd programmet startar servern. För länk skikts typer och länk lager tids typer av DUID måste värd programmet ange maskin varu typ och MAC-Datadata. För länk skiktets tids DUIDs måste tids pekaren peka på en giltig tid. Antalet sekunder sedan 1 januari 2000 är ett typiskt Seed-värde. Om serverns DUID-typ är företag, tilldelad typ, skapas DUIDen från användar konfigurerbara alternativ NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID och NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, och värdena för tid och MAC-adress kan anges till NULL.

>[!NOTE] 
> Det är värd programmets ansvar att spara DUID-parametrarna för servern på ett beständigt minne, så att den använder samma DUID i meddelanden till klienter mellan omstarter. Detta är ett krav för DHCPv6-protokollet (RFC 3315).

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **duid_type** DUID-typ för DHCPv6-server
- **hardware_type** Maskin varu typ (t. ex. Ethernet)
- **mac_address_msw** Pekare till DHCPv6-server
- **mac_address_lsw** Pekare till DHCPv6-server
- **tid** Tids värde för DUID

**Retur värden**

- **NX_SUCCESS** (0X00) servern har pausats
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) okänd eller DUID-typ som inte stöds
- **NX_INVALID_PARAMETERS** (0X4D) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

**Exempel**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Ange option Request Handler för DHCPv6-Server instans 

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

Den här tjänsten anger hanterings hanteraren för utökade alternativ för DHCPv6-servern.

**Indataparametrar**

- **dhcpv6_server_ptr** Pekare till DHCPv6-server
- **dhcpv6_option_request_handler_extended** Pekare till begär ande hanterare för utökade alternativ

**Retur värden**

- **NX_SUCCESS** (0X00) servern har återupptagits
- NX_PTR_ERROR (0x16) ogiltigt inmatade pekare

**Tillåten från**

Program kod

**Exempel**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```