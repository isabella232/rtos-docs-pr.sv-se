---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX Duo DNS-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX Duo DNS-tjänster (anges nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 10368edf3cdf15d32bddbd5bd943681b3ff3dd1aa1a7042d1b9bb2bf0e71699f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791914"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX Duo DNS-klienttjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS NetX DNS-tjänster (anges nedan) i alfabetisk ordning.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nx_dns_authority_zone_start_get** *Leta upp starten av en auktoritetszon som är associerad med det angivna värdnamnet*

- **nx_dns_cache_initialize** *initiera en DNS-cache.*

- **nx_dns_cache_notify_clear rensa** *cachen med fullständig notify-funktion.*

- **nx_dns_cache_notify_set** *Ange cachen för fullständig notify-funktion.*

- **nx_dns_cname_get** *Leta upp det kanoniska domännamnet för det inmatade domännamnsaliaset*

- **nx_dns_create Skapa** *en DNS-klientinstans*

- **nx_dns_delete Ta** *bort en DNS-klientinstans*

- **nx_dns_domain_name_server_get** *leta upp auktoritativa namnservrar för indatadomänzonen*

- **nx_dns_domain_mail_exchange_get leta** *upp det e-postutbyte som är associerat med det angivna värdnamnet.*

- **nx_dns_domain_service_get** *leta upp de tjänster som är associerade med det angivna värdnamnet*

- **nx_dns_get_serverlist_size** *returnera storleken på listan över DNS-klientservrar*

- **nx_dns_info_by_name_get** *returnera IP-adress, portfrågor på indatavärdnamn*

- **nx_dns_ipv4_address_by_name_get** *leta upp IPv4-adressen från det angivna värdnamnet*

- **nxd_dns_ipv6_address_by_name_get** *leta upp IPv6-adressen från det angivna värdnamnet*

- **nx_dns_host_by_address_get** för att nxd_dns_host_by_address_get ett värdnamn från en angiven *IP-adress (stöder endast IPv4-adresser)*

- **nxd_dns_host_by_address_get** *Upp en IP-adress från indatavärdnamnet (stöder både IPv4- och IPv6-adresser)*

- **nx_dns_host_by_name_get** för att nxd_dns_host_by_address_get söka efter ett värdnamn från den angivna adressen *(stöder endast IPv4-adresser)*

- **nxd_dns_host_by_name_get** *Upp en IP-adress från indatavärdnamnet (stöder både IPv4- och IPv6-adresser)*

- **nx_dns_host_text_get** *Leta upp textdata för domännamnet för indata*

- **nx_dns_packet_pool_set ange** *DNS-klientens paketpool*

- **nx_dns_server_add** *för att lägga nxd_dns_server_add* DNS-server på den angivna adressen i klientlistan *(stöder endast IPv4)*

- **nxd_dns_server_add Lägg** till en DNS-server för den angivna IP-adressen i klientserverlistan (stöder både *IPv4- eller IPv6-adresser)*

- **nx_dns_server_get** *returnera DNS-servern i klientlistan (stöder endast IPv4-adresser)*

- **nxd_dns_server_get** *returnera DNS-servern i klientlistan (stöder både IPv4- och IPv6-adresser)*

- **nx_dns_server_remove** *för att nxd_dns_server_remove ta bort en DNS-server från klientlistan*

- **nxd_dns_server_remove** Ta bort en DNS-server för den angivna *IP-adressen från klientlistan (stöder både IPv4- och IPv6-adresser)*

- **nx_dns_server_remove_all** *Ta bort alla DNS-servrar från klientlistan*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Leta upp indatavärdens startzon

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a>Description

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SOA med det angivna domännamnet för att få början av auktoritetszonen för indatadomännamnet. DNS-klienten kopierar de SOA-poster som returneras i DNS-serversvaret *till den record_buffer* minnesplatsen.

> [!NOTE]
> Den *record_buffer* måste vara 4 byte justerad för att ta emot data.

I NETX Duo DNS-klienten sparas SOA-posttypen, NX_DNS_SOA_ENTRY, som sju 4 byte-parametrar, totalt 28 byte:

- **nx_dns_soa_host_mname_ptr** Pekare till den primära datakällan för den här zonen.
- **nx_dns_soa_host_rname_ptr** Pekare till postlådan som ansvarar för den här zonen
- **nx_dns_soa_serial** Zonversionsnummer
- **nx_dns_soa_refresh** Uppdateringsintervall
- **nx_dns_soa_retry** Intervall mellan återförsök för SOA-fråga
- **nx_dns_soa_expire** Tidslängd när SOA upphör att gälla
- **nx_dns_soa_minmum** Minsta TTL-fält i SOA-värdnamnets DNS-svarsmeddelanden

Lagringen av två SOA-poster visas nedan. SOA-posterna som innehåller data med fast längd anges med början överst i bufferten. Pekarna MNAME och RNAME pekar på variabellängdsdata (värdnamn) som lagras längst ned i bufferten. Ytterligare SOA-poster anges efter den första posten ("ytterligare SOA-poster...") och deras variabellängdsdata lagras ovanför den sista postens variabellängdsdata ("ytterligare data för SOA-variabellängd"):

![Lagring av två SOA-poster](media/image4.png)

Om *indataservern record_buffer* inte kan lagra alla SOA-data i serverns *svar,* innehåller record_buffer så många poster som passar och returnerar antalet poster i bufferten.

Med antalet SOA-poster som returneras i **record_count kan* programmet parsa data från *record_buffer* och extrahera början av zonutfärdares värdnamnssträngar.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värdnamn för att hämta SOA-data för
- **record_buffer** Pekare till plats för att extrahera SOA-data till
- **buffer_size** Storleken på bufferten som ska innehålla SOA-data
- **record_count** Pekare till antalet soa-poster som hämtats
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Soa-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Klientserverlistan är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar och initierar en DNS-cache.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.
- **cache_ptr** Pekare till DNS Cache.
- **cache_size** Storleken på DNS-cache i byte.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS Cache har initierats
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga icke-pekarindata
- NX_DNS_CACHE_ERROR (0xB7) Ogiltig cache-pekare.
- NX_PTR_ERROR (0x07) Ogiltig DNS-pekare. 
- NX_DNS_ERROR (0xA0) Cacheminnet är inte justerat med 4 byte.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Rensa den fullständiga av meddela-funktionen för DNS Cache

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar den fullständiga av meddela-funktionen för cachen.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) AV DNS-cache har angetts
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga indata som inte pekare
- NX_PTR_ERROR (0x07) Ogiltig DNS-pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Ange den fullständiga av meddela-funktionen för DNS Cache

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Description

Den här tjänsten anger cachen fullständig notify-funktion.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.
- **cache_full_notify_cb** Återanropsfunktionen som ska anropas när cachen blir full.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) AV DNS-cache har angetts
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga indata som inte pekare
- NX_PTR_ERROR (0x07) Ogiltig DNS-pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Leta upp det kanoniska namnet för värdnamnet för indata

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a>Description

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES definieras *i nxd_dns.h* skickar den här tjänsten en fråga av typen CNAME med det angivna domännamnet för att hämta det kanoniska domännamnet. DNS-klienten kopierar CNAME-strängen som returneras i DNS-serversvaret *till record_buffer* minnesplatsen.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värdnamn för att hämta CNAME-data för
- **record_buffer** Pekare till plats för att extrahera CNAME-data till
- **buffer_size** Storleken på bufferten som ska innehålla CNAME-data
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) CNAME-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Klientserverlistan är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga indata som inte pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa en DNS-klientinstans

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a>Description

Den här tjänsten skapar en DNS-klientinstans för den tidigare skapade IP-instansen.

> [!IMPORTANT]
> Programmet måste se till att paketnyttolasten för paketpoolen som används av DNS-klienten är tillräckligt stor för det maximala DNS-meddelandet på 512 byte, plus UDP-, IP- och Ethernet-huvuden. Om DNS-klienten skapar en egen paketpool definieras detta av NX_DNS_PACKET_PAYLOAD och NX_DNS_PACKET_POOL_SIZE.

Om DNS-klientprogrammet föredrar att ange en tidigare skapad paketpool bör nyttolasten för IPv4 DNS-klienten vara 512 byte för det maximala DNS-värdet plus 20 byte för IP-huvudet, 8 byte för UDP-huvudet och 14 byte för Ethernet-huvudet. För IPv6 är den enda skillnaden att IP-huvudet är 40 byte, vilket innebär att paketet måste hantera IPv6-huvudet på 40 byte.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **ip_ptr** Pekare till ip-instans som skapats tidigare.  
- **domain_name** Pekare till domännamn för DNS-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DNS-skapa
- **NX_DNS_ERROR** (0xA0) DNS-skapa
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a>nx_dns_delete

Ta bort en DNS-klientinstans

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a>Description

Den här tjänsten tar bort en DNS-klientinstans som skapats tidigare och frigör dess resurser. 

> [!NOTE]
> Om NX_DNS_CLIENT_USER_CREATE_PACKET_POOL har definierats och DNS-klienten har tilldelats en användardefinierad paketpool är det upp till programmet att ta bort DNS-klientens paketpool om den inte längre behöver den.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till dns-klientinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Borttagning av DNS-klient.
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-klient pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Leta upp auktoritativa namnservrar för indatadomänzonen

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Description

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen NS med det angivna domännamnet för att hämta namnservrarna för indatadomännamnet. DNS-klienten kopierar NS-posterna som returneras i DNS-serversvaret *till record_buffer* minnesplatsen.

> [!NOTE]
> Den *record_buffer* måste vara 4 byte justerad för att ta emot data.

I NetX Duo DNS-klienten sparas NS-datatypen, NX_DNS_NS_ENTRY, som två 4 byte-parametrar:

- **nx_dns_ns_ipv4_address** Namnserverns IPv4-adress
- **nx_dns_ns_hostname_ptr** Pekare till namnserverns värdnamn

Bufferten som visas nedan innehåller fyra NX_DNS_NS_ENTRY poster. Pekaren till värdnamnssträngen i varje startpunkt pekar på motsvarande värdnamnssträng i den nedre halvan av bufferten:

![Innehåller fyra NX_DNS_NS_ENTRY poster](media/image5.png)

Om *indataservern record_buffer* inte kan lagra alla NS-data i serverns *svar,* innehåller record_buffer så många poster som passar och returnerar antalet poster i bufferten.

Med antalet NS-poster som returneras i **record_count kan* programmet parsa IP-adressen och värdnamnet för varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värdnamn för att hämta NS-data för
- **record_buffer** Pekare till plats för att extrahera NS-data till
- **buffer_size** Storlek på buffert för att lagra NS-data
- **record_count** Pekare till antalet NS-poster som hämtats
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) NS-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Klientserverlistan är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga indata som inte pekare
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Leta upp e-postutbytena efter indatavärdnamnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a>Description

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen MX med det angivna domännamnet för att hämta e-postutbytet för indatadomännamnet. DNS-klienten kopierar MX-posterna som returneras i DNS-serversvaret *till den record_buffer* minnesplatsen. 

> [!NOTE]
> Den *record_buffer* måste vara 4 byte justerad för att ta emot data.

I NetX Duo DNS-klienten sparas posttypen för e-postutbyte, NX_DNS_MAIL_EXCHANGE_ENTRY, som fyra parametrar, totalt 12 byte:

- **nx_dns_mx_ipv4_address** E-postutbyte, IPv4-adress, 4 byte
- **nx_dns_mx_preference** Inställning 2 byte
- **nx_dns_mx_reserved0** Reserverade 2 byte
- **nx_dns_mx_hostname_ptr** Pekare till e-post exchange-serverns värdnamn 4 byte

En buffert som innehåller fyra MX-poster visas nedan. Varje post innehåller data med fast längd från listan ovan. Pekaren till värdnamnet för e-postutbytesservern pekar på motsvarande värdnamn längst ned i bufferten.

![En buffert som innehåller fyra MX-poster](media/image6.png)

Om *indataservern record_buffer* inte kan lagra alla MX-data i serverns *svar,* innehåller record_buffer så många poster som passar och returnerar antalet poster i bufferten.

Med antalet MX-poster som returneras i **record_count kan* programmet parsa MX-parametrarna, inklusive e-postvärdnamnet för varje post *i record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värdnamn för att hämta MX-data för
- **record_buffer** Pekare till plats för att extrahera MX-data till
- **buffer_size** Storleken på bufferten som ska innehålla MX-data
- **record_count** Pekare till antalet MX-poster som hämtats
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) MX-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Klientserverlistan är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga indata som inte pekare
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Leta upp de tjänster som tillhandahålls av indatavärdnamnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Description

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SRV med det angivna domännamnet för att leta upp de tjänster och deras portnummer som är associerade med den angivna domänen. DNS-klienten kopierar de SRV-poster som returneras i DNS-serversvaret till *record_buffer* minnesplatsen. 

> [!NOTE]
> Den *record_buffer* måste vara 4 byte justerad för att ta emot data.

I NetX Duo DNS-klienten sparas tjänstposttypen, NX_DNS_SRV_ ENTRY, som sex parametrar, totalt 16 byte. Detta gör att SRV-data med variabel längd kan lagras på ett minneseffektivt sätt:

- **Serverns IPv4-nx_dns_srv_ipv4_address** 4 byte
- **Serverprioritet** nx_dns_srv_priority 2 byte
- **Servervikt** nx_dns_srv_weight 2 byte
- **Tjänstportnummer** nx_dns_srv_port_number 2 byte
- **Reserverad för justering på 4 byte** nx_dns_srv_reserved0 2 byte
- **Pekare till serverns värdnamn** *nx_dns_srv_hostname_ptr 4 byte

Fyra SRV-poster lagras i den angivna bufferten. Varje NX_DNS_SRV_ENTRY innehåller en *pekare, nx_dns_srv_hostname_ptr*, som pekar på motsvarande värdnamnssträng längst ned i postbufferten:

![Fyra SRV-poster](media/image7.png)

Om *indataservern record_buffer* inte kan lagra alla SRV-data i serverns *svar,* innehåller record_buffer så många poster som passar och returnerar antalet poster i bufferten.

Med antalet SRV-poster som returneras i **record_count kan* programmet parsa SRV-parametrarna, inklusive servervärdnamnet för varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till värdnamn för att hämta SRV-data för
- **record_buffer** Pekare till plats för att extrahera SRV-data till
- **buffer_size** Storlek på buffert för att lagra SRV-data
- **record_count** Pekare till antalet SRV-poster som hämtats
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) SRV-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Klientserverlistan är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_DNS_PARAM_ERROR (0xA8) Ogiltig icke-pekarparameter.
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Returnera storleken på DNS-klientens serverlista

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a>Description

Den här tjänsten returnerar antalet giltiga DNS-servrar (både IPv4 och IPv6) i klientlistan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock  
- **storlek** Returnerar antalet servrar i listan

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS-serverlistans storlek har returnerats
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Returnera IP-adress och port för DNS-server efter värdnamn

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten returnerar server-IP och port (tjänstpost) baserat på indatavärdnamnet efter DNS-fråga. Om en tjänstpost inte hittas returnerar den här rutinen en noll-IP-adress i pekaren för indataadressen och statusen för ett fel som inte är noll returneras för att signalera ett fel.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock  
- **host_name** Pekare till värdnamnsbuffert
- **host_address_ptr** Pekare till adress som ska returneras
- **host_port_ptr** Pekare till port som ska returneras
- **wait_option** Väntealternativ för DNS-svaret

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS-serverposten returnerades
- **NX_DNS_NO_SERVER** (0xA1) Ingen DNS-server registrerad med Klienten för att skicka fråga på värdnamnet
- **NX_DNS_QUERY_FAILED** (0xA3) DNS-fråga misslyckades; inget svar från några DNS-servrar i klientlistan eller ingen tjänstpost är tillgänglig för indatavärdnamnet.
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Leta upp IPv4-adressen för värdnamnet för indata

### <a name="prototype"></a>Prototyp
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar en fråga av typen A med det angivna värdnamnet för att hämta IP-adresserna för indatavärdnamnet. DNS-klienten kopierar IPv4-adressen från A-posterna som returneras i DNS-serversvaret till *den* record_buffer minnesplatsen.

> [!NOTE]
> Den *record_buffer* måste vara 4 byte justerad för att ta emot data.

Flera IPv4-adresser lagras i den 4 byte-justerade bufferten enligt nedan:

![4 byte-justerad buffert med flera adresser](media/image8.png)

Om den angivna bufferten inte kan innehålla alla IP-adressdata lagras inte de återstående A-posterna i *record_buffer*. Detta gör att programmet kan hämta en eller flera av de tillgängliga IP-adressdata i serverns svar.

Med antalet A-poster som returneras i **record_count* kan programmet parsa IPv4-adressdata från *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name_ptr** Pekare till värdnamn för att hämta IPv4-adress
- **buffert** Pekare till plats för att extrahera IPv4-data till
- **buffer_size** Storlek på buffert för att lagra IPv4-data
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IPv4-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Listan över klientservrar är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltig icke-pekarparameter.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Leta upp IPv6-adressen för värdnamnet för indata

### <a name="prototype"></a>Prototyp
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar en fråga av typen AAAA med det angivna domännamnet för att hämta IP-adresserna för indatadomännamnet. DNS-klienten kopierar IPv6-adressen från DE AAAA-poster som returneras i DNS-serversvaret till *record_buffer* minnesplatsen. 

> [!NOTE]
> Den *record_buffer* måste vara 4 byte justerad för att ta emot data.

Formatet för IPv6-adresser som lagras i den 4 byte justerade bufferten visas nedan:

![4 byte-justerad buffert i IPv6-format](media/image9.png)

Om *indataservern record_buffer* kan innehålla alla AAAA-data i serverns svar, innehåller *record_buffer* så många poster som passar och returnerar antalet poster i bufferten.

Med antalet AAAA-poster som returneras i **record_count kan* programmet parsa IPv6-adresserna från varje post i *record_buffer*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name_ptr** Pekare till värdnamn för att hämta IPv6-adress
- **buffert** Pekare till plats för att extrahera IPv6-data till
- **buffer_size** Storlek på buffert för att lagra IPv6-data
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) IPv6-data har erhållits
- **NX_DNS_NO_SERVER** (0xA1) Listan över klientservrar är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltig icke-pekarparameter.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten begär namnmatchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angetts av programmet. Om det lyckas returneras det NULL-avslutade värdnamnet i strängen som anges av *host_name_ptr*. Det här är en omserfunktion *nxd_dns_host_by_address_get* tjänst och accepterar inte IPv6-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till dns-instans som skapats tidigare.
- **ip_address** IP-adress som ska matchas mot ett namn
- **host_name_ptr** Pekare till målområdet för värdnamnet
- **max_host_name_size** Storleken på målområdet för värdnamnet
- **wait_option** Definierar hur länge tjänsten ska vänta i timern för ett DNS-serversvar efter varje DNS-fråga och återförsök av frågor. Väntealternativen definieras på följande sätt:

  timeout-värde (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en DNS-server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på DNS-upplösningen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DNS-upplösning  
- **NX_DNS_TIMEOUT** (0xA2) Time out när DNS mutex erhölls
- **NX_DNS_NO_SERVER** (0xA1) Ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0xA3) Tog inte emot något svar på frågan
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null-indataadress
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) pekar på ogiltig adresstyp (t.ex. IPv6)
- **NX_DNS_PARAM_ERROR** (0xA8) Ogiltig icke-pekarindata
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten begär namnmatchning av IPv6- eller IPv4-adressen *i ip_address* från en eller flera DNS-servrar som tidigare angetts av programmet. Om det lyckas returneras det NULL-avslutade värdnamnet i strängen som anges av *host_name_ptr*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till dns-instans som skapats tidigare.
- **ip_address** IP-adress som ska matchas mot ett namn
- **host_name_ptr** Pekare till målområdet för värdnamnet
- **max_host_name_size** Storleken på målområdet för värdnamnet
- **wait_option** Definierar hur länge tjänsten ska vänta i timern för ett DNS-serversvar efter varje DNS-fråga och återförsök av frågor. Väntealternativen definieras på följande sätt:

  timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en DNS-server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på DNS-upplösningen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DNS-upplösning  
- **NX_DNS_TIMEOUT** (0xA2) Time out när DNS mutex erhölls
- **NX_DNS_NO_SERVER** (0xA1) Ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0xA3) Tog inte emot något svar på frågan
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null-indataadress
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Leta upp en IP-adress från värdnamnet

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten begär namnmatchning av det angivna namnet från en eller flera DNS-servrar som tidigare angetts av programmet. Om det lyckas returneras den associerade IP-adressen i det mål som host_address_ptr. Det här är en wrapper-funktion *för nxd_dns_host_by_name_get tjänsten* och är begränsad till IPv4-adressinmatning.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till dns-instans som skapats tidigare.
- **host_name** Pekare till värdnamn
- **host_address_ptr** DNS-serverns IP-adress returnerades
- **wait_option** Definierar hur länge tjänsten ska vänta på DNS-upplösningen. Väntealternativen definieras på följande sätt:

  timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en DNS-server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på DNS-upplösningen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DNS-upplösning.
- **NX_DNS_NO_SERVER** (0xA1) Ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0xA3) Tog inte emot något svar på frågan
- NX_DNS_PARAM_ERROR (0xA8) Ogiltig icke-pekarindata
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Leta upp en IP-adress från värdnamnet

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a>Description

Den här tjänsten begär namnmatchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angetts av programmet. Om det lyckas returneras den associerade IP-adressen i en NXD_ADDRESS pekar på *av host_address_ptr*. Om anroparen specifikt anger lookup_type indata till NX_IP_VERSION_V6 skickar den här tjänsten ut frågan för en värd-IPv6-adress (AAAA-post). Om anroparen specifikt anger lookup_type indata till NX_IP_VERSION_V4 skickar den här tjänsten ut frågan för en IPv4-värdadress (A-post).

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till dns-klientinstans som skapats tidigare.
- **host_name** Pekare till värdnamnet för att hitta IP-adressen
- **host_address_ptr** Pekare till mål för NXD_ADDRESS som innehåller IP-adressen
- **wait_option** Definierar hur länge tjänsten ska vänta i timern för DNS-serversvaret för varje frågeöverföring och återöverföring. Väntealternativen definieras på följande sätt:

  timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en DNS-server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på DNS-upplösningen.

- **lookup_type** Ange typ av sökning (A kontra AAAA).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad DNS-upplösning.
- **NX_DNS_NO_SERVER** (0xA1) Ingen DNS-serveradress har angetts
- **NX_DNS_QUERY_FAILED** (0xA3) Tog inte emot något svar på frågan
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null-indataadress
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ett annat exempel på hur du använder den här tidstjänsten, den här gången med IPv4-adresser och A-posttyper, visas nedan:
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

Leta upp textsträngen för domännamnet för indata

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar en fråga av typen TXT med det angivna domännamnet och bufferten för att hämta godtyckliga strängdata.

DNS-klienten kopierar textsträngen i TXT-posten i DNS-serversvaret till *record_buffer* minnesplatsen. 

> [!NOTE]
> Den record_buffer behöver inte vara 4 byte justerad för att ta emot data.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-klient.  
- **host_name** Pekare till namnet på värden som sökningen ska sökas på
- **record_buffer** Pekare till plats för att extrahera TXT-data till
- **buffer_size** Storlek på buffert för att lagra TXT-data
- **wait_option** Väntealternativ för att ta emot DNS-serversvar

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) TXT-strängen har hämtats
- **NX_DNS_NO_SERVER** (0xA1) Klientserverlistan är tom
- **NX_DNS_QUERY_FAILED** (0xA3) Inget giltigt DNS-svar togs emot
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_PARAM_ERROR (0xA8) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange DNS-klientens paketpool

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Description

Den här tjänsten anger en tidigare skapad paketpool som DNS-klientpaketpool. DNS-klienten använder den här paketpoolen för att skicka DNS-frågor, så paketnyttolasten bör inte vara mindre än NX_DNS_PACKET_PAYLOAD som innehåller Ethernet-, IP- och UDP-huvuden och definieras *i nxd_dns.h.* 

> [!NOTE]
> *Dns-klienten* tas bort, paketpoolen tas inte bort med den och det är programmets ansvar att ta bort paketpoolen när den inte längre behövs.
>
> Den här tjänsten är bara tillgänglig om konfigurationsalternativet NX_DNS_CLIENT_USER_CREATE_PACKET_POOL har definierats i *nxd_dns.h*

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till dns-klientinstans som skapats tidigare.
- **pool_ptr** Pekare till paketpool som skapats tidigare

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Slutförande.
- **NX_NOT_ENABLED** (0x14) Klienten har inte konfigurerats för det här alternativet
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-klient pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Lägga till IP-adress för DNS-server

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Description

Den här tjänsten lägger till en IPv4 DNS-server i serverlistan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.  
- **server_address** IP-adress för DNS-server

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Server har lagts till
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) Inga fler DNS-servrar tillåts (listan är full)
- **NX_DNS_PARAM_ERROR** (0xA8) Ogiltiga icke-pekarindata
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null-serveradressindata

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a>nxd_dns_server_add

Lägg till DNS-server i klientlistan

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Description

Den här tjänsten lägger till IP-adressen för en DNS-server i listan över DNS-klientservrar. Den server_address kan vara antingen en IPv4- eller IPv6-adress. Om klienten vill kunna komma åt samma server via antingen sin IPv4-adress eller IPv6-adress bör båda IP-adresserna läggas till som poster i serverlistan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.
- **server_address** Pekare till den NXD_ADDRESS som innehåller serverns IP-adress för DNS-servern.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Server har lagts till
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) Inga fler DNS-servrar tillåts (listan är full) 
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- **NX_DNS_PARAM_ERROR** (0xA8) Ogiltiga icke-pekarindata
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null-serveradressindata
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Pekar på ogiltig adresstyp (t.ex. IPv6)

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Returnera en IPv4 DNS-server från klientlistan

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a>Description

Den här tjänsten returnerar IPv4 DNS-serveradressen från serverlistan för det angivna indexet. 

> [!NOTE]
> Indexet är nollbaserat. Om indataindexet överskrider storleken på DNS-klientlistan hittas en IPv6-adress i indexet eller en null-adress hittas i det angivna indexet. Ett fel returneras. Tjänsten *nx_dns_get_serverlist_size* anropas först hämta antalet DNS-servrar i klientlistan.

Den här tjänsten stöder endast IPv4-adresser. Den anropar *nxd_dns_server_get* som stöder både IPv4- och IPv6-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock  
- **index** Indexera till DNS-klientens lista över servrar
- **dns_server_address** Pekare till IP-adress för DNS-server

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Servern har returnerats
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Index pekar på ett tomt fack
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index pekar på Null-adress
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) pekar på ogiltig adresstyp (t.ex. IPv6)
- **NX_DNS_PARAM_ERROR** (0xA8) Ogiltiga indata som inte pekare
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a>nxd_dns_server_get

Returnera en DNS-server från klientlistan

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a>Description

Den här tjänsten returnerar DNS-serverns IP-adress från serverlistan i det angivna indexet. 

> [!NOTE]
> Indexet är nollbaserat. Om indataindexet överskrider storleken på DNS-klientlistan, eller om en null-adress hittas i det angivna indexet, returneras ett fel. Tjänsten *nx_dns_get_serverlist_size* anropas först för att hämta antalet DNS-servrar i serverlistan.

Den här tjänsten stöder IPv4- och IPv6-adresser.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock  
- **index** Indexera till DNS-klientens lista över servrar
- **dns_server_address** Pekare till IP-adress för DNS-server

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Serverns IP-adress har returnerats
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Index pekar på en tom plats
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index pekar på null-serveradress
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) pekar på ogiltig adresstyp (t.ex. IPv6)
- **NX_DNS_PARAM_ERROR** (0xA8) Ogiltiga icke-pekarindata
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Ta bort en IPv4 DNS-server från klientlistan

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Description

Den här tjänsten tar bort en IPv4 DNS-server från klientlistan. Det är en omslutningsfunktion för *nxd_dns_server_remove*.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.
- **server_address** IP-adress för DNS-server.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS-servern har tagits bort
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Server inte i klientlistan
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null-serveradressinmatning
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a>nxd_dns_server_remove

Ta bort en DNS-server från klientlistan

### <a name="prototype"></a>Prototyp
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Description

Den här tjänsten tar bort en DNS-server för den angivna IP-adressen från klientlistan. Den inkommande IP-adressen accepterar både IPv4- och IPv6-adresser. När servern har tagits bort flyttas de återstående servrarna ned ett index i listan för att fylla det lediga facket.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.
- **server_address** Pekare till DNS Server NXD_ADDRESS data som innehåller serverns IP-adress.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS-servern har tagits bort
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) Server inte i klientlistan
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null-serveradressinmatning
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Det går inte att bearbeta poster med IPv6 inaktiverat
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Pekar på ogiltig adresstyp (t.ex. IPv6)

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ta bort alla DNS-servrar från klientlistan

### <a name="prototype"></a>Prototyp
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a>Description

Den här tjänsten tar bort alla DNS-servrar från klientlistan.

### <a name="input-parameters"></a>Indataparametrar

- **dns_ptr** Pekare till DNS-kontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) DNS-servrar har tagits bort
- **NX_DNS_ERROR** (0xA0) Det går inte att hämta skyddet mutex
- NX_PTR_ERROR (0x07) Ogiltig IP- eller DNS-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```