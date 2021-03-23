---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DNS Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX Duo DNS-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9634adab3944c29f64d26dd688b5053dc1bd9bcb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826016"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DNS Client Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DNS-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_dns_authority_zone_start_get** *Leta upp starten av en zon för auktoritet som är associerad med det angivna värd namnet*

- **nx_dns_cache_initialize** *initiera en DNS-cache.*

- **nx_dns_cache_notify_clear** *Rensa cache-funktionen fullständig notify.*

- **nx_dns_cache_notify_set** *Ange fullständig meddelande funktion för cachen.*

- **nx_dns_cname_get** *Leta upp det kanoniska domän namnet för aliaset för den inmatade domänen*

- **nx_dns_create** *skapa en DNS-klient instans*

- **nx_dns_delete** *ta bort en DNS-klient instans*

- **nx_dns_domain_name_server_get** *Leta upp auktoritativa namnservrar för den angivna domän zonen*

- **nx_dns_domain_mail_exchange_get** *slå upp e-postmeddelandet som är kopplat till det angivna värd namnet.*

- **nx_dns_domain_service_get** *Leta upp de tjänster som är associerade med det angivna värd namnet*

- **nx_dns_get_serverlist_size** att *returnera storleken på listan över DNS-klientinställningar*

- **nx_dns_info_by_name_get** *returnera IP-adress, Port fråga på indata-värdnamn*

- **nx_dns_ipv4_address_by_name_get** *Leta upp IPv4-adressen från det angivna värd namnet*

- **nxd_dns_ipv6_address_by_name_get** *Leta upp IPv6-adressen från det angivna värd namnet*

- **nx_dns_host_by_address_get** *wrapper-funktionen för nxd_dns_host_by_address_get för att leta upp ett värdnamn från en angiven IP-adress (stöder endast IPv4-adresser)*

- **nxd_dns_host_by_address_get** *Leta upp en IP-adress från det angivna värd namnet (stöder både IPv4-och IPv6-adresser)*

- **nx_dns_host_by_name_get** *wrapper-funktionen för nxd_dns_host_by_address_get för att leta upp ett värdnamn från den angivna adressen (stöder endast IPv4-adresser)*

- **nxd_dns_host_by_name_get** *Leta upp en IP-adress från det angivna värd namnet (stöder både IPv4-och IPv6-adresser)*

- **nx_dns_host_text_get** *söka efter text data för det angivna domän namnet*

- **nx_dns_packet_pool_set** *Ange pool för DNS-klient*

- **nx_dns_server_add** *wrapper-funktionen för* nxd_dns_server_add för *att lägga till en DNS-server på den angivna adressen i klient listan (stöder endast IPv4)*

- **nxd_dns_server_add** *lägga till en DNS-server med den angivna IP-adressen i klient server listan (stöder både IPv4-eller IPv6-adresser)*

- **nx_dns_server_get** *returnera DNS-servern i klient listan (stöder endast IPv4-adresser)*

- **nxd_dns_server_get** *returnera DNS-servern i klient listan (stöder både IPv4-och IPv6-adresser)*

- **nx_dns_server_remove** *wrapper-funktionen för nxd_dns_server_remove ta bort en DNS-server från klient listan*

- **nxd_dns_server_remove** *ta bort en DNS-server med den angivna IP-adressen från klient listan (stöder både IPv4-och IPv6-adresser)*

- **nx_dns_server_remove_all** *ta bort alla DNS-servrar från klient listan*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Leta upp starten av auktoritets zonen för den angivna värden

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a>Beskrivning

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SOA med det angivna domän namnet för att hämta start zonen för auktoriteten för det angivna domän namnet. DNS-klienten kopierar de SOA-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.

> [!NOTE]
> *Record_buffer* måste vara 4 bytes justerad för att ta emot data.

I NetX Duo DNS-klienten sparas SOA-posttypen NX_DNS_SOA_ENTRY, som 7 4 byte-parametrar, totalt 28 byte:

- **nx_dns_soa_host_mname_ptr** Pekare till den primära data källan för den här zonen.
- **nx_dns_soa_host_rname_ptr** Pekare till den post låda som ansvarar för den här zonen
- **nx_dns_soa_serial** Versions nummer för zon
- **nx_dns_soa_refresh** Uppdaterings intervall
- **nx_dns_soa_retry** Intervall mellan försök med SOA-frågor
- **nx_dns_soa_expire** Tids varaktighet när SOA upphör att gälla
- **nx_dns_soa_minmum** Minsta TTL-fält i SOA hostname DNS-svarsmeddelanden

Lagringen av två SOA-poster visas nedan. De SOA-poster som innehåller fasta längd data anges med början överst i bufferten. Pekarna MNAME och RNAME pekar på variabla längd data (värd namn) som lagras längst ned i bufferten. Ytterligare SOA-poster anges efter den första posten ("ytterligare SOA-poster...") och deras variabla längd data lagras ovanför den sista postens variabla längd data ("ytterligare data för SOA-variabel längd"):

![Lagring av två SOA-poster](media/image4.png)

Om indata- *record_buffer* inte rymmer alla SOA-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.

Med antalet SOA-poster som returneras i **record_count* kan programmet parsa data från *record_buffer* och extrahera start av värd namn strängar för zon utfärdare.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värd namnet för att hämta SOA-data för
- **record_buffer** Pekare till platsen där SOA-data ska extraheras till
- **buffer_size** Buffertstorleken för att lagra SOA-data
- **record_count** Pekare till antalet SOA-poster som hämtats
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har hämtat SOA-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

    /* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;

    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );

    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }

    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

[Output]
----------------------------------------------------
Test SOA: 
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```

## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

Initiera DNS-cachen

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar och initierar en DNS-cache.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.
- **cache_ptr** Pekare till DNS-cache.
- **cache_size** Storlek på DNS-cache, i byte.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-cache har initierats
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare
- NX_DNS_CACHE_ERROR (0xB7) ogiltig cache-pekare.
- NX_PTR_ERROR (0x07) ogiltig DNS-pekare. 
- NX_DNS_ERROR-cachen (0xA0) är inte 4-byte-justerad.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Rensa DNS-cachens fullständiga meddelande funktion

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar cachen fullständig aviserings funktion.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-cache-avisering har angetts
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltig DNS-pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Ange fullständig meddelande funktion för DNS-cache

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den fullständiga aviserings funktionen cache.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.
- **cache_full_notify_cb** Motringningsfunktionen som anropas när cachen blir full.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-cache-avisering har angetts
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltig DNS-pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Leta upp det kanoniska namnet för det angivna värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES definieras i *nxd_dns. h* skickar den här tjänsten en fråga av typen CNAME med det angivna domän namnet för att hämta det kanoniska domän namnet. DNS-klienten kopierar den CNAME-sträng som returnerades i DNS-serverns svar till *record_buffer* minnes plats.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värd namnet för att hämta CNAME-data för
- **record_buffer** Pekare till platsen där du vill extrahera CNAME-data till
- **buffer_size** Buffertstorleken för att lagra CNAME-data
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtade CNAME-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a>nx_dns_create

Skapa en DNS-klient instans

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en DNS-klient instans för den tidigare skapade IP-instansen.

> [!IMPORTANT]
> Programmet måste se till att paket nytto lasten för den modempool som används av DNS-klienten är tillräckligt stor för maximalt 512 byte DNS-meddelande, plus UDP-, IP-och Ethernet-rubriker. Om DNS-klienten skapar en egen modempool, definieras detta av NX_DNS_PACKET_PAYLOAD och NX_DNS_PACKET_POOL_SIZE.

Om DNS-klientprogrammet föredrar att tillhandahålla en tidigare skapad modempool ska nytto lasten för IPv4 DNS-klienten vara 512 byte för maximalt antal DNS plus 20 byte för IP-huvudet, 8 byte för UDP-huvudet och 14 byte för Ethernet-huvudet. För IPv6 är den enda skillnaden att IP-huvudet är 40 byte, och paketet måste därför hantera IPv6-huvudet på 40 byte.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **ip_ptr** Pekare till den tidigare skapade IP-instansen.  
- **domain_name** Pekare till domän namn för DNS-instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-skapande har genomförts
- **NX_DNS_ERROR** (0XA0) DNS-skapande fel
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a>nx_dns_delete

Ta bort en DNS-klient instans

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad DNS-klient instans och frigör sina resurser. 

> [!NOTE]
> Om NX_DNS_CLIENT_USER_CREATE_PACKET_POOL har definierats och DNS-klienten tilldelats en användardefinierad modempool, är det upp till programmet att ta bort DNS-klientcachen om den inte längre behöver den.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till en tidigare skapad DNS-klient instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-klientbegäran har tagits bort.
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-klient pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Leta upp auktoritativa namnservrar för den inmatade domän zonen

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen NS med det angivna domän namnet för att hämta namnservrarna för det inmatade domän namnet. DNS-klienten kopierar den eller de NS-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.

> [!NOTE]
> *Record_buffer* måste vara 4 bytes justerad för att ta emot data.

I NetX Duo DNS-klient har data typen NS, NX_DNS_NS_ENTRY, sparats som 2 4 byte-parametrar:

- **nx_dns_ns_ipv4_address** Namnserverns IPv4-adress
- **nx_dns_ns_hostname_ptr** Pekare till namn serverns värdnamn

Den buffert som visas nedan innehåller fyra NX_DNS_NS_ENTRY poster. Pekaren som är värd för namn sträng i varje post pekar mot motsvarande värd namn sträng i den nedre halvan av bufferten:

![Innehåller fyra NX_DNS_NS_ENTRY poster](media/image5.png)

Om indata- *record_buffer* inte rymmer alla ns-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.

Med antalet NS-poster som returneras i **record_count* kan programmet parsa IP-adressen och värd namnet för varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värd namnet för att hämta NS-data för
- **record_buffer** Pekare till platsen för att extrahera NS-data till
- **buffer_size** Buffertstorleken för att lagra NS-data
- **record_count** Pekare till antalet hämtade NS-poster
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har hämtat ns-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                     nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
                }
        else
            printf("hostname is not set\n");
    }
}

[Output]
------------------------------------------------------
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

Slå upp e-post Exchange (s) för det angivna värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen MX med det angivna domän namnet för att hämta e-postadressen för det inmatade domän namnet. DNS-klienten kopierar MX-post (er) som returneras i DNS-serverns svar till *record_buffer* minnes plats. 

> [!NOTE]
> *Record_buffer* måste vara 4 bytes justerad för att ta emot data.

I NetX Duo DNS-klienten sparas post typen post Exchange, NX_DNS_MAIL_EXCHANGE_ENTRY, som fyra parametrar, totalt 12 byte:

- **nx_dns_mx_ipv4_address** E-post Exchange IPv4-adress 4 byte
- **nx_dns_mx_preference** Alternativ 2 byte
- **nx_dns_mx_reserved0** Reserverade 2 byte
- **nx_dns_mx_hostname_ptr** Pekare till e-post för Exchange Server-värdnamn 4 byte

En buffert som innehåller fyra MX-poster visas nedan. Varje post innehåller data för fast längd från listan ovan. Pekaren till e-postadressen till Exchange-servern pekar på motsvarande värdnamn längst ned i bufferten.

![En buffert som innehåller fyra MX-poster](media/image6.png)

Om indata- *record_buffer* inte rymmer alla MX-data i svaret på servern så innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.

Med antalet MX-poster som returneras i **record_count* kan programmet parsa MX-parametrarna, inklusive e-postvärdnamnet för varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värdnamn för att hämta MX-data för
- **record_buffer** Pekare till platsen där du vill extrahera MX-data till
- **buffer_size** Buffertstorleken för att lagra MX-data
- **record_count** Pekare till antalet MX-poster som hämtats
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har hämtat MX-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```

## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

Leta upp de tjänster som tillhandahålls av det angivna värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SRV med det angivna domän namnet för att leta upp de tjänster och deras port nummer som är associerade med den angivna domänen. DNS-klienten kopierar de SRV-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats. 

> [!NOTE]
> *Record_buffer* måste vara 4 bytes justerad för att ta emot data.

I NetX Duo DNS-klienten sparas tjänst post typen NX_DNS_SRV_ post som sex parametrar, med en total summa på 16 byte. Detta gör att SRV-data för variabel längd lagras på ett minnes effektivt sätt:

- **Serverns IPv4-adress** nx_dns_srv_ipv4_address 4 byte
- **Server prioritet** nx_dns_srv_priority 2 byte
- **Server vikt** nx_dns_srv_weight 2 byte
- **Tjänst port nummer** nx_dns_srv_port_number 2 byte
- **Reserverad för 4-byte-justering** nx_dns_srv_reserved0 2 byte
- **Pekare till serverns värdnamn** * nx_dns_srv_hostname_ptr 4 byte

Fyra SRV-poster lagras i den angivna bufferten. Varje NX_DNS_SRV_ENTRY post innehåller en pekare, *nx_dns_srv_hostname_ptr*, som pekar på motsvarande värd namn sträng längst ned i bufferten för poster:

![Fyra SRV-poster](media/image7.png)

Om indata- *record_buffer* inte rymmer alla SRV-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.

Med antalet SRV-poster som returneras i **record_count* kan programmet parsa SRV-parametrarna, inklusive Server värd namnet för varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värd namnet för att hämta SRV-data för
- **record_buffer** Pekare till platsen där du kan extrahera SRV-data till
- **buffer_size** Buffertstorleken för att lagra SRV-data
- **record_count** Pekare till antalet SRV-poster som hämtats
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtade SRV-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_DNS_PARAM_ERROR (0xA8) ogiltig icke-pekarpost-parameter.
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

            printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

           printf("port number = %d\n", 
                   nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
           printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
           printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

           if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
           {
                printf("hostname = %s\n", 
                        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
            }
           else
                printf("hostname is not set\n");
        }
}

[Output]
----------------------------------------------------
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

Returnera storleken på DNS-klientens server lista

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar antalet giltiga DNS-servrar (både IPv4 och IPv6) i klient listan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontroll-block  
- **storlek** Returnerar antalet servrar i listan

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-serverns lista storlek har returnerats
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Returnera IP-adress och port för DNS-servern efter värdnamn

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar serverns IP-adress och port (tjänst post) baserat på det angivna värd namnet av DNS-frågan. Om en tjänst post inte hittas returnerar den här rutinen en noll-IP-adress i indata-adress pekaren och en fel status som inte är noll returneras för att signalera ett fel.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontroll-block  
- **host_name** Pekare till värd namnets buffert
- **host_address_ptr** Pekare som ska användas för att returnera
- **host_port_ptr** Pekare till port att returnera
- **wait_option** Vänte alternativ för DNS-svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-serveradress har returnerats
- **NX_DNS_NO_SERVER** (0XA1) ingen DNS-Server registrerad med klienten för att skicka fråga på värdnamn
- **NX_DNS_QUERY_FAILED** (0XA3) DNS-fråga misslyckades, Inga svar från några DNS-servrar i klient listan eller ingen tjänst post är tillgängliga för det angivna värd namnet.
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Leta upp IPv4-adressen för det angivna värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en fråga av typen A med det angivna värd namnet för att hämta IP-adresserna för det angivna värd namnet. DNS-klienten kopierar IPv4-adressen från en eller flera poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.

> [!NOTE]
> *Record_buffer* måste vara 4 bytes justerad för att ta emot data.

Flera IPv4-adresser lagras i den 4-byte-justerade bufferten som visas nedan:

![adress, 4-byte, anpassad buffert](media/image8.png)

Om den angivna bufferten inte kan innehålla alla IP-Datadata, lagras inte de återstående posterna i *record_buffer*. Detta gör att programmet kan hämta ett, några eller alla tillgängliga IP-Datadata i svaret från servern.

Med antalet returnerade poster i **record_count* kan programmet parsa IPv4-adress data från *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name_ptr** Pekare till värd namn för att hämta IPv4-adress
- **buffert** Pekare till platsen där du vill extrahera IPv4-data till
- **buffer_size** Buffertstorleken för att lagra IPv4-data
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtade IPv4-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig icke-pekarpost-parameter.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
           for(i =0; i< record_count; i++)
           {
                ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
                printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                    *ipv4_address_ptr[i] >> 24,
                    *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                    *ipv4_address_ptr[i] >> 8 & 0xFF,
                    *ipv4_address_ptr[i] & 0xFF);
            }

}

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a>nxd_dns_ipv6_address_by_name_get

Leta upp IPv6-adressen för det angivna värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en fråga av typen AAAA med det angivna domän namnet för att hämta IP-adresserna för det inmatade domän namnet. DNS-klienten kopierar IPv6-adressen från AAAA-post (er) som returneras i DNS-serverns svar till *record_buffer* minnes plats. 

> [!NOTE]
> *Record_buffer* måste vara 4 bytes justerad för att ta emot data.

Formatet för IPv6-adresser som lagras i den 4-byte-justerade bufferten visas nedan:

![IPv6-format 4-bytes-justerad buffert](media/image9.png)

Om indata- *record_buffer* inte rymmer alla AAAA-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.

Med antalet AAAA-poster som returneras i **record_count* kan programmet parsa IPv6-adresserna från varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name_ptr** Pekare till värd namnet för att hämta IPv6-adress
- **buffert** Pekare till platsen där du vill extrahera IPv6-data till
- **buffer_size** Buffertstorleken för att lagra IPv6-data
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) hämtade IPv6-data
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig icke-pekarpost-parameter.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Leta upp ett värdnamn från en IP-adress

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten begär namn matchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angavs av programmet. Om det lyckas returneras det NULL-avslutade värd namnet i strängen som anges av *host_name_ptr*. Detta är en wrapper-funktion för *nxd_dns_host_by_address_get* tjänst och accepterar inte IPv6-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till den tidigare skapade DNS-instansen.
- **ip_address** IP-adress att matcha i ett namn
- **host_name_ptr** Pekare till mål arean för värd namnet
- **max_host_name_size** Storlek på mål arean för värdnamn
- **wait_option** Definierar hur länge tjänsten väntar på timer-Tick för ett DNS-Server svar efter varje DNS-fråga och fråga om försök igen. Vänte alternativen definieras enligt följande:

  timeout-värde (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-matchning har genomförts  
- Tids gränsen nåddes för **NX_DNS_TIMEOUT** (0xA2) vid hämtning av DNS-mutex
- **NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata adress
- **NX_DNS_INVALID_ADDRESS_TYPE** (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)
- **NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

**Exempel**
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a>nxd_dns_host_by_address_get

Leta upp ett värdnamn från IP-adressen

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten begär namn matchning av IPv6-eller IPv4-adressen i *ip_address* indataargumentet från en eller flera DNS-servrar som tidigare angavs av programmet. Om det lyckas returneras det NULL-avslutade värd namnet i strängen som anges av *host_name_ptr*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till den tidigare skapade DNS-instansen.
- **ip_address** IP-adress att matcha i ett namn
- **host_name_ptr** Pekare till mål arean för värd namnet
- **max_host_name_size** Storlek på mål arean för värdnamn
- **wait_option** Definierar hur länge tjänsten väntar på timer-Tick för ett DNS-Server svar efter varje DNS-fråga och fråga om försök igen. Vänte alternativen definieras enligt följande:

  timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-matchning har genomförts  
- Tids gränsen nåddes för **NX_DNS_TIMEOUT** (0xA2) vid hämtning av DNS-mutex
- **NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata adress
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

**Exempel**
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Leta upp en IP-adress från värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten begär namn matchning för det angivna namnet från en eller flera DNS-servrar som tidigare angavs av programmet. Om det lyckas returneras den associerade IP-adressen i målet som host_address_ptr. Detta är en wrapper-funktion för tjänsten *nxd_dns_host_by_name_get* och är begränsad till IPv4-adress indata.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till den tidigare skapade DNS-instansen.
- **host_name** Pekare till värdnamn
- **host_address_ptr** DNS-serverns IP-adress returnerades
- **wait_option** Definierar hur länge tjänsten ska vänta på DNS-matchningen. Vänte alternativen definieras enligt följande:

  timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-matchning har genomförts.
- **NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

**Exempel**
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a>nxd_dns_host_by_name_get

Sök efter en IP-adress från värd namnet

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten begär namn matchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angavs av programmet. Om det lyckas returneras den associerade IP-adressen i ett NXD_ADDRESS som pekas av *host_address_ptr*. Om anroparen specifikt anger lookup_type indata till NX_IP_VERSION_V6 skickas frågan för en IPv6-adress (AAAA-post) för den här tjänsten. Om anroparen specifikt anger lookup_type indata till NX_IP_VERSION_V4 skickas en fråga för en IPv4-adress för värden (en post).

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till en tidigare skapad DNS-klient instans.
- **host_name** Pekare till värd namnet för att hitta en IP-adress för
- **host_address_ptr** Pekare till målet för NXD_ADDRESS som innehåller IP-adressen
- **wait_option** Definierar hur länge tjänsten väntar på timer-Tick för DNS-serverns svar för varje frågans överföring och återöverföring. Vänte alternativen definieras enligt följande:

  timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.

- **lookup_type** Ange typ av sökning (A vs AAAA).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-matchning har genomförts.
- **NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata adress
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

**Exempel**
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

Ett annat exempel på att använda den här tids tjänsten, den här gången med IPv4-adresser och en post typer visas nedan:
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Leta upp text strängen för det angivna domän namnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en fråga av typen TXT med det angivna domän namnet och bufferten för att hämta godtyckliga sträng data.

DNS-klienten kopierar text strängen i TXT-posten i DNS-serverns svar till *record_buffer* minnes plats. 

> [!NOTE]
> Record_buffer behöver inte vara 4 byte-justerad för att ta emot data.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till namnet på värden att söka på
- **record_buffer** Pekare till platsen där du vill extrahera TXT-data till
- **buffer_size** Buffertstorleken för att lagra TXT-data
- **wait_option** Vänte alternativ för att ta emot DNS-serverns svar

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en returnerad txt-sträng
- **NX_DNS_NO_SERVER** (0XA1) klient server listan är tom
- **NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

######   
Exempel
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Ange pool för DNS-klient

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger en tidigare skapad modempool som DNS-klientens adresspool. DNS-klienten kommer att använda den här poolen för att skicka DNS-frågor, så paketets nytto Last bör inte vara mindre än NX_DNS_PACKET_PAYLOAD som inkluderar Ethernet-, IP-och UDP-huvudena och definieras i *nxd_dns. h.* 

> [!NOTE]
> Om DNS-klienten är borttagen tas inte poolen bort med den och det är programmets ansvar att ta bort modempoolen när den inte längre behöver den.
>
> Den här tjänsten är bara tillgänglig om konfigurations alternativet NX_DNS_CLIENT_USER_CREATE_PACKET_POOL definierats i *nxd_dns. h*

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till en tidigare skapad DNS-klient instans.
- **pool_ptr** Pekare till tidigare skapade paket pool

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) slutfördes.
- **NX_NOT_ENABLED** -klienten (0x14) har inte kon figurer ATS för det här alternativet
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-klient pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Lägg till DNS-serverns IP-adress

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en IPv4 DNS-server i Server listan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.  
- **server_address** IP-adress för DNS-Server

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00)-servern har lagts till
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0X17) inga fler DNS-servrar tillåts (listan är full)
- **NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) null-indata för server adress

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a>nxd_dns_server_add

Lägg till DNS-server i klient listan

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Beskrivning

Den här tjänsten lägger till IP-adressen för en DNS-server i listan DNS-klientkonfiguration. Server_address kan vara antingen en IPv4-eller IPv6-adress. Om klienten vill kunna komma åt samma server med en IPv4-adress eller IPv6-adress ska den lägga till båda IP-adresserna som poster i Server listan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.
- **server_address** Pekar till den NXD_ADDRESS som innehåller serverns IP-adress för DNS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00)-servern har lagts till
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0X17) inga fler DNS-servrar tillåts (listan är full) 
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- **NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) null-indata för server adress
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) index pekar på ogiltig adress typ (t. ex. IPv6)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Returnera en IPv4 DNS-server från klient listan

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar IPv4 DNS-serveradressen från server listan vid det angivna indexet. 

> [!NOTE]
> Indexet är noll baserat. Om indata-indexet överskrider storleken på listan över DNS-klienter, finns det en IPv6-adress i indexet eller en null-adress som finns i det angivna indexet. ett fel returneras. Den *nx_dns_get_serverlist_size* tjänsten kan anropas först hämta antalet DNS-servrar i klient listan.

Den här tjänsten stöder endast IPv4-adresser. Den anropar tjänsten *nxd_dns_server_get* som stöder både IPv4-och IPv6-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontroll-block  
- **index** Indexera till DNS-klientens lista över servrar
- **dns_server_address** Pekare till IP-adressen för DNS-servern

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) returnerad Server
- **NX_DNS_SERVER_NOT_FOUND** (0XA9) index pekar på tom plats
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) index pekar på null-adress
- **NX_DNS_INVALID_ADDRESS_TYPE** (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)
- **NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a>nxd_dns_server_get

Returnera en DNS-server från klient listan

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar DNS-serverns IP-adress från server listan vid det angivna indexet. 

> [!NOTE]
> Indexet är noll baserat. Om indata-indexet överskrider storleken på listan över DNS-klienter, eller om en null-adress hittas vid det angivna indexet, returneras ett fel. Den *nx_dns_get_serverlist_size* tjänsten kan anropas först för att erhålla antalet DNS-servrar i Server listan.

Den här tjänsten har stöd för IPv4-och IPv6-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontroll-block  
- **index** Indexera till DNS-klientens lista över servrar
- **dns_server_address** Pekare till IP-adressen för DNS-servern

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) returnerade SERVERNS IP-adress
- **NX_DNS_SERVER_NOT_FOUND** (0XA9) index pekar på tom plats
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) index pekar på en null-serveradress
- **NX_DNS_INVALID_ADDRESS_TYPE** (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)
- **NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Ta bort en IPv4 DNS-server från klient listan

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en IPv4 DNS-server från klient listan. Det är en wrapper-funktion för *nxd_dns_server_remove*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.
- **server_address** IP-adressen för DNS-servern.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-servern har tagits bort
- **NX_DNS_SERVER_NOT_FOUND** -servern (0xA9) inte i klient listan
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata för server adress
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a>nxd_dns_server_remove

Ta bort en DNS-server från klient listan

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en DNS-server med den angivna IP-adressen från klient listan. IP-adressen för indata accepterar både IPv4-och IPv6-adresser. När servern har tagits bort flyttas de återstående servrarna nedåt ett index i listan för att fylla vacated-facket.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.
- **server_address** Pekare till DNS-Server NXD_ADDRESS data som innehåller Server-IP-adress.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-servern har tagits bort
- **NX_DNS_SERVER_NOT_FOUND** -servern (0xA9) inte i klient listan
- **NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata för server adress
- **NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) index pekar på ogiltig adress typ (t. ex. IPv6)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Ta bort alla DNS-servrar från klient listan

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort alla DNS-servrar från klient listan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-Control-Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) DNS-servrar har tagits bort
- **NX_DNS_ERROR** (0XA0) Det gick inte att hämta skydds-mutex
- NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```