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
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="04462-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo DNS Client Services</span><span class="sxs-lookup"><span data-stu-id="04462-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="04462-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DNS-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="04462-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="04462-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="04462-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="04462-106">**nx_dns_authority_zone_start_get** *Leta upp starten av en zon för auktoritet som är associerad med det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="04462-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="04462-107">**nx_dns_cache_initialize** *initiera en DNS-cache.*</span><span class="sxs-lookup"><span data-stu-id="04462-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="04462-108">**nx_dns_cache_notify_clear** *Rensa cache-funktionen fullständig notify.*</span><span class="sxs-lookup"><span data-stu-id="04462-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="04462-109">**nx_dns_cache_notify_set** *Ange fullständig meddelande funktion för cachen.*</span><span class="sxs-lookup"><span data-stu-id="04462-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="04462-110">**nx_dns_cname_get** *Leta upp det kanoniska domän namnet för aliaset för den inmatade domänen*</span><span class="sxs-lookup"><span data-stu-id="04462-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="04462-111">**nx_dns_create** *skapa en DNS-klient instans*</span><span class="sxs-lookup"><span data-stu-id="04462-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="04462-112">**nx_dns_delete** *ta bort en DNS-klient instans*</span><span class="sxs-lookup"><span data-stu-id="04462-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="04462-113">**nx_dns_domain_name_server_get** *Leta upp auktoritativa namnservrar för den angivna domän zonen*</span><span class="sxs-lookup"><span data-stu-id="04462-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="04462-114">**nx_dns_domain_mail_exchange_get** *slå upp e-postmeddelandet som är kopplat till det angivna värd namnet.*</span><span class="sxs-lookup"><span data-stu-id="04462-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="04462-115">**nx_dns_domain_service_get** *Leta upp de tjänster som är associerade med det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="04462-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="04462-116">**nx_dns_get_serverlist_size** att *returnera storleken på listan över DNS-klientinställningar*</span><span class="sxs-lookup"><span data-stu-id="04462-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="04462-117">**nx_dns_info_by_name_get** *returnera IP-adress, Port fråga på indata-värdnamn*</span><span class="sxs-lookup"><span data-stu-id="04462-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="04462-118">**nx_dns_ipv4_address_by_name_get** *Leta upp IPv4-adressen från det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="04462-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="04462-119">**nxd_dns_ipv6_address_by_name_get** *Leta upp IPv6-adressen från det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="04462-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="04462-120">**nx_dns_host_by_address_get** *wrapper-funktionen för nxd_dns_host_by_address_get för att leta upp ett värdnamn från en angiven IP-adress (stöder endast IPv4-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="04462-121">**nxd_dns_host_by_address_get** *Leta upp en IP-adress från det angivna värd namnet (stöder både IPv4-och IPv6-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="04462-122">**nx_dns_host_by_name_get** *wrapper-funktionen för nxd_dns_host_by_address_get för att leta upp ett värdnamn från den angivna adressen (stöder endast IPv4-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="04462-123">**nxd_dns_host_by_name_get** *Leta upp en IP-adress från det angivna värd namnet (stöder både IPv4-och IPv6-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="04462-124">**nx_dns_host_text_get** *söka efter text data för det angivna domän namnet*</span><span class="sxs-lookup"><span data-stu-id="04462-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="04462-125">**nx_dns_packet_pool_set** *Ange pool för DNS-klient*</span><span class="sxs-lookup"><span data-stu-id="04462-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="04462-126">**nx_dns_server_add** *wrapper-funktionen för* nxd_dns_server_add för *att lägga till en DNS-server på den angivna adressen i klient listan (stöder endast IPv4)*</span><span class="sxs-lookup"><span data-stu-id="04462-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="04462-127">**nxd_dns_server_add** *lägga till en DNS-server med den angivna IP-adressen i klient server listan (stöder både IPv4-eller IPv6-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="04462-128">**nx_dns_server_get** *returnera DNS-servern i klient listan (stöder endast IPv4-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="04462-129">**nxd_dns_server_get** *returnera DNS-servern i klient listan (stöder både IPv4-och IPv6-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="04462-130">**nx_dns_server_remove** *wrapper-funktionen för nxd_dns_server_remove ta bort en DNS-server från klient listan*</span><span class="sxs-lookup"><span data-stu-id="04462-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="04462-131">**nxd_dns_server_remove** *ta bort en DNS-server med den angivna IP-adressen från klient listan (stöder både IPv4-och IPv6-adresser)*</span><span class="sxs-lookup"><span data-stu-id="04462-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="04462-132">**nx_dns_server_remove_all** *ta bort alla DNS-servrar från klient listan*</span><span class="sxs-lookup"><span data-stu-id="04462-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="04462-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="04462-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="04462-134">Leta upp starten av auktoritets zonen för den angivna värden</span><span class="sxs-lookup"><span data-stu-id="04462-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-135">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="04462-136">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-136">Description</span></span>

<span data-ttu-id="04462-137">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SOA med det angivna domän namnet för att hämta start zonen för auktoriteten för det angivna domän namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="04462-138">DNS-klienten kopierar de SOA-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="04462-139">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="04462-140">I NetX Duo DNS-klienten sparas SOA-posttypen NX_DNS_SOA_ENTRY, som 7 4 byte-parametrar, totalt 28 byte:</span><span class="sxs-lookup"><span data-stu-id="04462-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="04462-141">**nx_dns_soa_host_mname_ptr** Pekare till den primära data källan för den här zonen.</span><span class="sxs-lookup"><span data-stu-id="04462-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="04462-142">**nx_dns_soa_host_rname_ptr** Pekare till den post låda som ansvarar för den här zonen</span><span class="sxs-lookup"><span data-stu-id="04462-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="04462-143">**nx_dns_soa_serial** Versions nummer för zon</span><span class="sxs-lookup"><span data-stu-id="04462-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="04462-144">**nx_dns_soa_refresh** Uppdaterings intervall</span><span class="sxs-lookup"><span data-stu-id="04462-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="04462-145">**nx_dns_soa_retry** Intervall mellan försök med SOA-frågor</span><span class="sxs-lookup"><span data-stu-id="04462-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="04462-146">**nx_dns_soa_expire** Tids varaktighet när SOA upphör att gälla</span><span class="sxs-lookup"><span data-stu-id="04462-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="04462-147">**nx_dns_soa_minmum** Minsta TTL-fält i SOA hostname DNS-svarsmeddelanden</span><span class="sxs-lookup"><span data-stu-id="04462-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="04462-148">Lagringen av två SOA-poster visas nedan.</span><span class="sxs-lookup"><span data-stu-id="04462-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="04462-149">De SOA-poster som innehåller fasta längd data anges med början överst i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="04462-150">Pekarna MNAME och RNAME pekar på variabla längd data (värd namn) som lagras längst ned i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="04462-151">Ytterligare SOA-poster anges efter den första posten ("ytterligare SOA-poster...") och deras variabla längd data lagras ovanför den sista postens variabla längd data ("ytterligare data för SOA-variabel längd"):</span><span class="sxs-lookup"><span data-stu-id="04462-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Lagring av två SOA-poster](media/image4.png)

<span data-ttu-id="04462-153">Om indata- *record_buffer* inte rymmer alla SOA-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="04462-154">Med antalet SOA-poster som returneras i \**record_count* kan programmet parsa data från *record_buffer* och extrahera start av värd namn strängar för zon utfärdare.</span><span class="sxs-lookup"><span data-stu-id="04462-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-155">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-155">Input Parameters</span></span>

- <span data-ttu-id="04462-156">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-157">**host_name** Pekare till värd namnet för att hämta SOA-data för</span><span class="sxs-lookup"><span data-stu-id="04462-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="04462-158">**record_buffer** Pekare till platsen där SOA-data ska extraheras till</span><span class="sxs-lookup"><span data-stu-id="04462-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="04462-159">**buffer_size** Buffertstorleken för att lagra SOA-data</span><span class="sxs-lookup"><span data-stu-id="04462-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="04462-160">**record_count** Pekare till antalet SOA-poster som hämtats</span><span class="sxs-lookup"><span data-stu-id="04462-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="04462-161">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-162">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-162">Return Values</span></span>

- <span data-ttu-id="04462-163">**NX_SUCCESS** (0X00) har hämtat SOA-data</span><span class="sxs-lookup"><span data-stu-id="04462-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="04462-164">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-165">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-166">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-167">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-168">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-169">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-169">Allowed From</span></span>

<span data-ttu-id="04462-170">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-171">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-171">Example</span></span>
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

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="04462-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="04462-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="04462-173">Initiera DNS-cachen</span><span class="sxs-lookup"><span data-stu-id="04462-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-174">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="04462-175">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-175">Description</span></span>

<span data-ttu-id="04462-176">Den här tjänsten skapar och initierar en DNS-cache.</span><span class="sxs-lookup"><span data-stu-id="04462-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-177">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-177">Input Parameters</span></span>

- <span data-ttu-id="04462-178">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="04462-179">**cache_ptr** Pekare till DNS-cache.</span><span class="sxs-lookup"><span data-stu-id="04462-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="04462-180">**cache_size** Storlek på DNS-cache, i byte.</span><span class="sxs-lookup"><span data-stu-id="04462-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-181">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-181">Return Values</span></span>

- <span data-ttu-id="04462-182">**NX_SUCCESS** (0X00) DNS-cache har initierats</span><span class="sxs-lookup"><span data-stu-id="04462-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="04462-183">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="04462-184">NX_DNS_CACHE_ERROR (0xB7) ogiltig cache-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="04462-185">NX_PTR_ERROR (0x07) ogiltig DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="04462-186">NX_DNS_ERROR-cachen (0xA0) är inte 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="04462-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-187">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-187">Allowed From</span></span>

<span data-ttu-id="04462-188">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-189">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="04462-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="04462-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="04462-191">Rensa DNS-cachens fullständiga meddelande funktion</span><span class="sxs-lookup"><span data-stu-id="04462-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-192">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="04462-193">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-193">Description</span></span>

<span data-ttu-id="04462-194">Den här tjänsten rensar cachen fullständig aviserings funktion.</span><span class="sxs-lookup"><span data-stu-id="04462-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-195">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-195">Input Parameters</span></span>

- <span data-ttu-id="04462-196">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-197">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-197">Return Values</span></span>

- <span data-ttu-id="04462-198">**NX_SUCCESS** (0X00) DNS-cache-avisering har angetts</span><span class="sxs-lookup"><span data-stu-id="04462-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="04462-199">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="04462-200">NX_PTR_ERROR (0x07) ogiltig DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-201">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-201">Allowed From</span></span>

<span data-ttu-id="04462-202">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-203">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="04462-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="04462-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="04462-205">Ange fullständig meddelande funktion för DNS-cache</span><span class="sxs-lookup"><span data-stu-id="04462-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-206">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="04462-207">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-207">Description</span></span>

<span data-ttu-id="04462-208">Den här tjänsten anger den fullständiga aviserings funktionen cache.</span><span class="sxs-lookup"><span data-stu-id="04462-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-209">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-209">Input Parameters</span></span>

- <span data-ttu-id="04462-210">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="04462-211">**cache_full_notify_cb** Motringningsfunktionen som anropas när cachen blir full.</span><span class="sxs-lookup"><span data-stu-id="04462-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-212">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-212">Return Values</span></span>

- <span data-ttu-id="04462-213">**NX_SUCCESS** (0X00) DNS-cache-avisering har angetts</span><span class="sxs-lookup"><span data-stu-id="04462-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="04462-214">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="04462-215">NX_PTR_ERROR (0x07) ogiltig DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-216">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-216">Allowed From</span></span>

<span data-ttu-id="04462-217">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-218">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="04462-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="04462-219">nx_dns_cname_get</span></span>

<span data-ttu-id="04462-220">Leta upp det kanoniska namnet för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-221">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-222">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-222">Description</span></span>

<span data-ttu-id="04462-223">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES definieras i *nxd_dns. h* skickar den här tjänsten en fråga av typen CNAME med det angivna domän namnet för att hämta det kanoniska domän namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="04462-224">DNS-klienten kopierar den CNAME-sträng som returnerades i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-225">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-225">Input Parameters</span></span>

- <span data-ttu-id="04462-226">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-227">**host_name** Pekare till värd namnet för att hämta CNAME-data för</span><span class="sxs-lookup"><span data-stu-id="04462-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="04462-228">**record_buffer** Pekare till platsen där du vill extrahera CNAME-data till</span><span class="sxs-lookup"><span data-stu-id="04462-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="04462-229">**buffer_size** Buffertstorleken för att lagra CNAME-data</span><span class="sxs-lookup"><span data-stu-id="04462-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="04462-230">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-231">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-231">Return Values</span></span>

- <span data-ttu-id="04462-232">**NX_SUCCESS** (0x00) hämtade CNAME-data</span><span class="sxs-lookup"><span data-stu-id="04462-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="04462-233">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-234">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-235">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-236">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-237">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-238">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-238">Allowed From</span></span>

<span data-ttu-id="04462-239">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-240">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-240">Example</span></span>
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

##  <a name="nx_dns_create"></a><span data-ttu-id="04462-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="04462-241">nx_dns_create</span></span>

<span data-ttu-id="04462-242">Skapa en DNS-klient instans</span><span class="sxs-lookup"><span data-stu-id="04462-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-243">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="04462-244">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-244">Description</span></span>

<span data-ttu-id="04462-245">Den här tjänsten skapar en DNS-klient instans för den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="04462-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04462-246">Programmet måste se till att paket nytto lasten för den modempool som används av DNS-klienten är tillräckligt stor för maximalt 512 byte DNS-meddelande, plus UDP-, IP-och Ethernet-rubriker.</span><span class="sxs-lookup"><span data-stu-id="04462-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="04462-247">Om DNS-klienten skapar en egen modempool, definieras detta av NX_DNS_PACKET_PAYLOAD och NX_DNS_PACKET_POOL_SIZE.</span><span class="sxs-lookup"><span data-stu-id="04462-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="04462-248">Om DNS-klientprogrammet föredrar att tillhandahålla en tidigare skapad modempool ska nytto lasten för IPv4 DNS-klienten vara 512 byte för maximalt antal DNS plus 20 byte för IP-huvudet, 8 byte för UDP-huvudet och 14 byte för Ethernet-huvudet.</span><span class="sxs-lookup"><span data-stu-id="04462-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="04462-249">För IPv6 är den enda skillnaden att IP-huvudet är 40 byte, och paketet måste därför hantera IPv6-huvudet på 40 byte.</span><span class="sxs-lookup"><span data-stu-id="04462-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-250">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-250">Input Parameters</span></span>

- <span data-ttu-id="04462-251">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-252">**ip_ptr** Pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="04462-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="04462-253">**domain_name** Pekare till domän namn för DNS-instans.</span><span class="sxs-lookup"><span data-stu-id="04462-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-254">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-254">Return Values</span></span>

- <span data-ttu-id="04462-255">**NX_SUCCESS** (0X00) DNS-skapande har genomförts</span><span class="sxs-lookup"><span data-stu-id="04462-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="04462-256">**NX_DNS_ERROR** (0XA0) DNS-skapande fel</span><span class="sxs-lookup"><span data-stu-id="04462-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="04462-257">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-258">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-259">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-259">Allowed From</span></span>

<span data-ttu-id="04462-260">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-261">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="04462-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="04462-262">nx_dns_delete</span></span>

<span data-ttu-id="04462-263">Ta bort en DNS-klient instans</span><span class="sxs-lookup"><span data-stu-id="04462-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-264">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="04462-265">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-265">Description</span></span>

<span data-ttu-id="04462-266">Den här tjänsten tar bort en tidigare skapad DNS-klient instans och frigör sina resurser.</span><span class="sxs-lookup"><span data-stu-id="04462-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-267">Om NX_DNS_CLIENT_USER_CREATE_PACKET_POOL har definierats och DNS-klienten tilldelats en användardefinierad modempool, är det upp till programmet att ta bort DNS-klientcachen om den inte längre behöver den.</span><span class="sxs-lookup"><span data-stu-id="04462-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-268">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-268">Input Parameters</span></span>

- <span data-ttu-id="04462-269">**dns_ptr** Pekare till en tidigare skapad DNS-klient instans.</span><span class="sxs-lookup"><span data-stu-id="04462-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-270">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-270">Return Values</span></span>

- <span data-ttu-id="04462-271">**NX_SUCCESS** (0X00) DNS-klientbegäran har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="04462-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="04462-272">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="04462-273">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="04462-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-274">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-274">Allowed From</span></span>

<span data-ttu-id="04462-275">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-276">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="04462-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="04462-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="04462-278">Leta upp auktoritativa namnservrar för den inmatade domän zonen</span><span class="sxs-lookup"><span data-stu-id="04462-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-279">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-280">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-280">Description</span></span>

<span data-ttu-id="04462-281">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen NS med det angivna domän namnet för att hämta namnservrarna för det inmatade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="04462-282">DNS-klienten kopierar den eller de NS-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="04462-283">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="04462-284">I NetX Duo DNS-klient har data typen NS, NX_DNS_NS_ENTRY, sparats som 2 4 byte-parametrar:</span><span class="sxs-lookup"><span data-stu-id="04462-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="04462-285">**nx_dns_ns_ipv4_address** Namnserverns IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="04462-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="04462-286">**nx_dns_ns_hostname_ptr** Pekare till namn serverns värdnamn</span><span class="sxs-lookup"><span data-stu-id="04462-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="04462-287">Den buffert som visas nedan innehåller fyra NX_DNS_NS_ENTRY poster.</span><span class="sxs-lookup"><span data-stu-id="04462-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="04462-288">Pekaren som är värd för namn sträng i varje post pekar mot motsvarande värd namn sträng i den nedre halvan av bufferten:</span><span class="sxs-lookup"><span data-stu-id="04462-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Innehåller fyra NX_DNS_NS_ENTRY poster](media/image5.png)

<span data-ttu-id="04462-290">Om indata- *record_buffer* inte rymmer alla ns-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="04462-291">Med antalet NS-poster som returneras i \**record_count* kan programmet parsa IP-adressen och värd namnet för varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="04462-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-292">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-292">Input Parameters</span></span>

- <span data-ttu-id="04462-293">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-294">**host_name** Pekare till värd namnet för att hämta NS-data för</span><span class="sxs-lookup"><span data-stu-id="04462-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="04462-295">**record_buffer** Pekare till platsen för att extrahera NS-data till</span><span class="sxs-lookup"><span data-stu-id="04462-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="04462-296">**buffer_size** Buffertstorleken för att lagra NS-data</span><span class="sxs-lookup"><span data-stu-id="04462-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="04462-297">**record_count** Pekare till antalet hämtade NS-poster</span><span class="sxs-lookup"><span data-stu-id="04462-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="04462-298">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-299">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-299">Return Values</span></span>

- <span data-ttu-id="04462-300">**NX_SUCCESS** (0X00) har hämtat ns-data</span><span class="sxs-lookup"><span data-stu-id="04462-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="04462-301">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-302">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-303">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="04462-304">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-305">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-306">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-306">Allowed From</span></span>

<span data-ttu-id="04462-307">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-308">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-308">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="04462-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="04462-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="04462-310">Slå upp e-post Exchange (s) för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-311">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-312">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-312">Description</span></span>

<span data-ttu-id="04462-313">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen MX med det angivna domän namnet för att hämta e-postadressen för det inmatade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="04462-314">DNS-klienten kopierar MX-post (er) som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-315">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="04462-316">I NetX Duo DNS-klienten sparas post typen post Exchange, NX_DNS_MAIL_EXCHANGE_ENTRY, som fyra parametrar, totalt 12 byte:</span><span class="sxs-lookup"><span data-stu-id="04462-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="04462-317">**nx_dns_mx_ipv4_address** E-post Exchange IPv4-adress 4 byte</span><span class="sxs-lookup"><span data-stu-id="04462-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="04462-318">**nx_dns_mx_preference** Alternativ 2 byte</span><span class="sxs-lookup"><span data-stu-id="04462-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="04462-319">**nx_dns_mx_reserved0** Reserverade 2 byte</span><span class="sxs-lookup"><span data-stu-id="04462-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="04462-320">**nx_dns_mx_hostname_ptr** Pekare till e-post för Exchange Server-värdnamn 4 byte</span><span class="sxs-lookup"><span data-stu-id="04462-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="04462-321">En buffert som innehåller fyra MX-poster visas nedan.</span><span class="sxs-lookup"><span data-stu-id="04462-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="04462-322">Varje post innehåller data för fast längd från listan ovan.</span><span class="sxs-lookup"><span data-stu-id="04462-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="04462-323">Pekaren till e-postadressen till Exchange-servern pekar på motsvarande värdnamn längst ned i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![En buffert som innehåller fyra MX-poster](media/image6.png)

<span data-ttu-id="04462-325">Om indata- *record_buffer* inte rymmer alla MX-data i svaret på servern så innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="04462-326">Med antalet MX-poster som returneras i \**record_count* kan programmet parsa MX-parametrarna, inklusive e-postvärdnamnet för varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="04462-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-327">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-327">Input Parameters</span></span>

- <span data-ttu-id="04462-328">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-329">**host_name** Pekare till värdnamn för att hämta MX-data för</span><span class="sxs-lookup"><span data-stu-id="04462-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="04462-330">**record_buffer** Pekare till platsen där du vill extrahera MX-data till</span><span class="sxs-lookup"><span data-stu-id="04462-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="04462-331">**buffer_size** Buffertstorleken för att lagra MX-data</span><span class="sxs-lookup"><span data-stu-id="04462-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="04462-332">**record_count** Pekare till antalet MX-poster som hämtats</span><span class="sxs-lookup"><span data-stu-id="04462-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="04462-333">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-334">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-334">Return Values</span></span>

- <span data-ttu-id="04462-335">**NX_SUCCESS** (0X00) har hämtat MX-data</span><span class="sxs-lookup"><span data-stu-id="04462-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="04462-336">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-337">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-338">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="04462-339">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-340">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-341">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-341">Allowed From</span></span>

<span data-ttu-id="04462-342">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-343">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-343">Example</span></span>
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

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="04462-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="04462-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="04462-345">Leta upp de tjänster som tillhandahålls av det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-346">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-347">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-347">Description</span></span>

<span data-ttu-id="04462-348">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SRV med det angivna domän namnet för att leta upp de tjänster och deras port nummer som är associerade med den angivna domänen.</span><span class="sxs-lookup"><span data-stu-id="04462-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="04462-349">DNS-klienten kopierar de SRV-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-350">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="04462-351">I NetX Duo DNS-klienten sparas tjänst post typen NX_DNS_SRV_ post som sex parametrar, med en total summa på 16 byte.</span><span class="sxs-lookup"><span data-stu-id="04462-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="04462-352">Detta gör att SRV-data för variabel längd lagras på ett minnes effektivt sätt:</span><span class="sxs-lookup"><span data-stu-id="04462-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="04462-353">**Serverns IPv4-adress** nx_dns_srv_ipv4_address 4 byte</span><span class="sxs-lookup"><span data-stu-id="04462-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="04462-354">**Server prioritet** nx_dns_srv_priority 2 byte</span><span class="sxs-lookup"><span data-stu-id="04462-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="04462-355">**Server vikt** nx_dns_srv_weight 2 byte</span><span class="sxs-lookup"><span data-stu-id="04462-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="04462-356">**Tjänst port nummer** nx_dns_srv_port_number 2 byte</span><span class="sxs-lookup"><span data-stu-id="04462-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="04462-357">**Reserverad för 4-byte-justering** nx_dns_srv_reserved0 2 byte</span><span class="sxs-lookup"><span data-stu-id="04462-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="04462-358">**Pekare till serverns värdnamn** \* nx_dns_srv_hostname_ptr 4 byte</span><span class="sxs-lookup"><span data-stu-id="04462-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="04462-359">Fyra SRV-poster lagras i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="04462-360">Varje NX_DNS_SRV_ENTRY post innehåller en pekare, *nx_dns_srv_hostname_ptr*, som pekar på motsvarande värd namn sträng längst ned i bufferten för poster:</span><span class="sxs-lookup"><span data-stu-id="04462-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Fyra SRV-poster](media/image7.png)

<span data-ttu-id="04462-362">Om indata- *record_buffer* inte rymmer alla SRV-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="04462-363">Med antalet SRV-poster som returneras i \**record_count* kan programmet parsa SRV-parametrarna, inklusive Server värd namnet för varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="04462-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-364">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-364">Input Parameters</span></span>

- <span data-ttu-id="04462-365">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-366">**host_name** Pekare till värd namnet för att hämta SRV-data för</span><span class="sxs-lookup"><span data-stu-id="04462-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="04462-367">**record_buffer** Pekare till platsen där du kan extrahera SRV-data till</span><span class="sxs-lookup"><span data-stu-id="04462-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="04462-368">**buffer_size** Buffertstorleken för att lagra SRV-data</span><span class="sxs-lookup"><span data-stu-id="04462-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="04462-369">**record_count** Pekare till antalet SRV-poster som hämtats</span><span class="sxs-lookup"><span data-stu-id="04462-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="04462-370">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-371">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-371">Return Values</span></span>

- <span data-ttu-id="04462-372">**NX_SUCCESS** (0x00) hämtade SRV-data</span><span class="sxs-lookup"><span data-stu-id="04462-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="04462-373">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-374">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-375">NX_DNS_PARAM_ERROR (0xA8) ogiltig icke-pekarpost-parameter.</span><span class="sxs-lookup"><span data-stu-id="04462-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="04462-376">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-377">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-378">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-378">Allowed From</span></span>

<span data-ttu-id="04462-379">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-380">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-380">Example</span></span>
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="04462-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="04462-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="04462-382">Returnera storleken på DNS-klientens server lista</span><span class="sxs-lookup"><span data-stu-id="04462-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-383">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="04462-384">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-384">Description</span></span>

<span data-ttu-id="04462-385">Den här tjänsten returnerar antalet giltiga DNS-servrar (både IPv4 och IPv6) i klient listan.</span><span class="sxs-lookup"><span data-stu-id="04462-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-386">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-386">Input Parameters</span></span>

- <span data-ttu-id="04462-387">**dns_ptr** Pekare till DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="04462-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="04462-388">**storlek** Returnerar antalet servrar i listan</span><span class="sxs-lookup"><span data-stu-id="04462-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-389">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-389">Return Values</span></span>

- <span data-ttu-id="04462-390">**NX_SUCCESS** (0X00) DNS-serverns lista storlek har returnerats</span><span class="sxs-lookup"><span data-stu-id="04462-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="04462-391">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="04462-392">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-393">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-393">Allowed From</span></span>

<span data-ttu-id="04462-394">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-395">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="04462-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="04462-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="04462-397">Returnera IP-adress och port för DNS-servern efter värdnamn</span><span class="sxs-lookup"><span data-stu-id="04462-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-398">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-399">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-399">Description</span></span>

<span data-ttu-id="04462-400">Den här tjänsten returnerar serverns IP-adress och port (tjänst post) baserat på det angivna värd namnet av DNS-frågan.</span><span class="sxs-lookup"><span data-stu-id="04462-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="04462-401">Om en tjänst post inte hittas returnerar den här rutinen en noll-IP-adress i indata-adress pekaren och en fel status som inte är noll returneras för att signalera ett fel.</span><span class="sxs-lookup"><span data-stu-id="04462-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-402">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-402">Input Parameters</span></span>

- <span data-ttu-id="04462-403">**dns_ptr** Pekare till DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="04462-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="04462-404">**host_name** Pekare till värd namnets buffert</span><span class="sxs-lookup"><span data-stu-id="04462-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="04462-405">**host_address_ptr** Pekare som ska användas för att returnera</span><span class="sxs-lookup"><span data-stu-id="04462-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="04462-406">**host_port_ptr** Pekare till port att returnera</span><span class="sxs-lookup"><span data-stu-id="04462-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="04462-407">**wait_option** Vänte alternativ för DNS-svar</span><span class="sxs-lookup"><span data-stu-id="04462-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-408">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-408">Return Values</span></span>

- <span data-ttu-id="04462-409">**NX_SUCCESS** (0X00) DNS-serveradress har returnerats</span><span class="sxs-lookup"><span data-stu-id="04462-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="04462-410">**NX_DNS_NO_SERVER** (0XA1) ingen DNS-Server registrerad med klienten för att skicka fråga på värdnamn</span><span class="sxs-lookup"><span data-stu-id="04462-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="04462-411">**NX_DNS_QUERY_FAILED** (0XA3) DNS-fråga misslyckades, Inga svar från några DNS-servrar i klient listan eller ingen tjänst post är tillgängliga för det angivna värd namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="04462-412">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-413">NX_CALLER_ERROR (0x11) ogiltig anropare</span><span class="sxs-lookup"><span data-stu-id="04462-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-414">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-414">Allowed From</span></span>

<span data-ttu-id="04462-415">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-416">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="04462-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="04462-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="04462-418">Leta upp IPv4-adressen för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-419">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-420">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-420">Description</span></span>

<span data-ttu-id="04462-421">Den här tjänsten skickar en fråga av typen A med det angivna värd namnet för att hämta IP-adresserna för det angivna värd namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="04462-422">DNS-klienten kopierar IPv4-adressen från en eller flera poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="04462-423">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="04462-424">Flera IPv4-adresser lagras i den 4-byte-justerade bufferten som visas nedan:</span><span class="sxs-lookup"><span data-stu-id="04462-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![adress, 4-byte, anpassad buffert](media/image8.png)

<span data-ttu-id="04462-426">Om den angivna bufferten inte kan innehålla alla IP-Datadata, lagras inte de återstående posterna i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="04462-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="04462-427">Detta gör att programmet kan hämta ett, några eller alla tillgängliga IP-Datadata i svaret från servern.</span><span class="sxs-lookup"><span data-stu-id="04462-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="04462-428">Med antalet returnerade poster i \**record_count* kan programmet parsa IPv4-adress data från *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="04462-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-429">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-429">Input Parameters</span></span>

- <span data-ttu-id="04462-430">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-431">**host_name_ptr** Pekare till värd namn för att hämta IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="04462-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="04462-432">**buffert** Pekare till platsen där du vill extrahera IPv4-data till</span><span class="sxs-lookup"><span data-stu-id="04462-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="04462-433">**buffer_size** Buffertstorleken för att lagra IPv4-data</span><span class="sxs-lookup"><span data-stu-id="04462-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="04462-434">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-435">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-435">Return Values</span></span>

- <span data-ttu-id="04462-436">**NX_SUCCESS** (0x00) hämtade IPv4-data</span><span class="sxs-lookup"><span data-stu-id="04462-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="04462-437">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-438">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-439">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-440">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-441">NX_DNS_PARAM_ERROR (0xA8) ogiltig icke-pekarpost-parameter.</span><span class="sxs-lookup"><span data-stu-id="04462-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-442">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-442">Allowed From</span></span>

<span data-ttu-id="04462-443">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-444">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-444">Example</span></span>
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

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="04462-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="04462-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="04462-446">Leta upp IPv6-adressen för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-447">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-448">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-448">Description</span></span>

<span data-ttu-id="04462-449">Den här tjänsten skickar en fråga av typen AAAA med det angivna domän namnet för att hämta IP-adresserna för det inmatade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="04462-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="04462-450">DNS-klienten kopierar IPv6-adressen från AAAA-post (er) som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-451">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="04462-452">Formatet för IPv6-adresser som lagras i den 4-byte-justerade bufferten visas nedan:</span><span class="sxs-lookup"><span data-stu-id="04462-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![IPv6-format 4-bytes-justerad buffert](media/image9.png)

<span data-ttu-id="04462-454">Om indata- *record_buffer* inte rymmer alla AAAA-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="04462-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="04462-455">Med antalet AAAA-poster som returneras i \**record_count* kan programmet parsa IPv6-adresserna från varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="04462-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-456">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-456">Input Parameters</span></span>

- <span data-ttu-id="04462-457">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-458">**host_name_ptr** Pekare till värd namnet för att hämta IPv6-adress</span><span class="sxs-lookup"><span data-stu-id="04462-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="04462-459">**buffert** Pekare till platsen där du vill extrahera IPv6-data till</span><span class="sxs-lookup"><span data-stu-id="04462-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="04462-460">**buffer_size** Buffertstorleken för att lagra IPv6-data</span><span class="sxs-lookup"><span data-stu-id="04462-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="04462-461">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-462">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-462">Return Values</span></span>

- <span data-ttu-id="04462-463">**NX_SUCCESS** (0x00) hämtade IPv6-data</span><span class="sxs-lookup"><span data-stu-id="04462-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="04462-464">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-465">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-466">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-467">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-468">NX_DNS_PARAM_ERROR (0xA8) ogiltig icke-pekarpost-parameter.</span><span class="sxs-lookup"><span data-stu-id="04462-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-469">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-469">Allowed From</span></span>

<span data-ttu-id="04462-470">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-471">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-471">Example</span></span>
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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="04462-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="04462-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="04462-473">Leta upp ett värdnamn från en IP-adress</span><span class="sxs-lookup"><span data-stu-id="04462-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-474">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-475">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-475">Description</span></span>

<span data-ttu-id="04462-476">Den här tjänsten begär namn matchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="04462-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="04462-477">Om det lyckas returneras det NULL-avslutade värd namnet i strängen som anges av *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="04462-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="04462-478">Detta är en wrapper-funktion för *nxd_dns_host_by_address_get* tjänst och accepterar inte IPv6-adresser.</span><span class="sxs-lookup"><span data-stu-id="04462-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-479">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-479">Input Parameters</span></span>

- <span data-ttu-id="04462-480">**dns_ptr** Pekare till den tidigare skapade DNS-instansen.</span><span class="sxs-lookup"><span data-stu-id="04462-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="04462-481">**ip_address** IP-adress att matcha i ett namn</span><span class="sxs-lookup"><span data-stu-id="04462-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="04462-482">**host_name_ptr** Pekare till mål arean för värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="04462-483">**max_host_name_size** Storlek på mål arean för värdnamn</span><span class="sxs-lookup"><span data-stu-id="04462-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="04462-484">**wait_option** Definierar hur länge tjänsten väntar på timer-Tick för ett DNS-Server svar efter varje DNS-fråga och fråga om försök igen.</span><span class="sxs-lookup"><span data-stu-id="04462-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="04462-485">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04462-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="04462-486">timeout-värde (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="04462-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="04462-487">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="04462-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="04462-488">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="04462-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-489">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-489">Return Values</span></span>

- <span data-ttu-id="04462-490">**NX_SUCCESS** (0X00) DNS-matchning har genomförts</span><span class="sxs-lookup"><span data-stu-id="04462-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="04462-491">Tids gränsen nåddes för **NX_DNS_TIMEOUT** (0xA2) vid hämtning av DNS-mutex</span><span class="sxs-lookup"><span data-stu-id="04462-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="04462-492">**NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts</span><span class="sxs-lookup"><span data-stu-id="04462-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="04462-493">**NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan</span><span class="sxs-lookup"><span data-stu-id="04462-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="04462-494">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata adress</span><span class="sxs-lookup"><span data-stu-id="04462-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="04462-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)</span><span class="sxs-lookup"><span data-stu-id="04462-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="04462-496">**NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="04462-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-498">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="04462-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="04462-499">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-500">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-500">Allowed From</span></span>

<span data-ttu-id="04462-501">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-501">Threads</span></span>

<span data-ttu-id="04462-502">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="04462-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="04462-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="04462-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="04462-504">Leta upp ett värdnamn från IP-adressen</span><span class="sxs-lookup"><span data-stu-id="04462-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-505">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-506">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-506">Description</span></span>

<span data-ttu-id="04462-507">Den här tjänsten begär namn matchning av IPv6-eller IPv4-adressen i *ip_address* indataargumentet från en eller flera DNS-servrar som tidigare angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="04462-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="04462-508">Om det lyckas returneras det NULL-avslutade värd namnet i strängen som anges av *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="04462-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-509">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-509">Input Parameters</span></span>

- <span data-ttu-id="04462-510">**dns_ptr** Pekare till den tidigare skapade DNS-instansen.</span><span class="sxs-lookup"><span data-stu-id="04462-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="04462-511">**ip_address** IP-adress att matcha i ett namn</span><span class="sxs-lookup"><span data-stu-id="04462-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="04462-512">**host_name_ptr** Pekare till mål arean för värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="04462-513">**max_host_name_size** Storlek på mål arean för värdnamn</span><span class="sxs-lookup"><span data-stu-id="04462-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="04462-514">**wait_option** Definierar hur länge tjänsten väntar på timer-Tick för ett DNS-Server svar efter varje DNS-fråga och fråga om försök igen.</span><span class="sxs-lookup"><span data-stu-id="04462-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="04462-515">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04462-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="04462-516">timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="04462-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="04462-517">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="04462-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="04462-518">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="04462-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-519">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-519">Return Values</span></span>

- <span data-ttu-id="04462-520">**NX_SUCCESS** (0X00) DNS-matchning har genomförts</span><span class="sxs-lookup"><span data-stu-id="04462-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="04462-521">Tids gränsen nåddes för **NX_DNS_TIMEOUT** (0xA2) vid hämtning av DNS-mutex</span><span class="sxs-lookup"><span data-stu-id="04462-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="04462-522">**NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts</span><span class="sxs-lookup"><span data-stu-id="04462-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="04462-523">**NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan</span><span class="sxs-lookup"><span data-stu-id="04462-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="04462-524">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata adress</span><span class="sxs-lookup"><span data-stu-id="04462-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="04462-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-526">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="04462-527">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-528">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-529">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-529">Allowed From</span></span>

<span data-ttu-id="04462-530">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-530">Threads</span></span>

<span data-ttu-id="04462-531">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="04462-531">**Example**</span></span>
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

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="04462-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="04462-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="04462-533">Leta upp en IP-adress från värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-534">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-535">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-535">Description</span></span>

<span data-ttu-id="04462-536">Den här tjänsten begär namn matchning för det angivna namnet från en eller flera DNS-servrar som tidigare angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="04462-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="04462-537">Om det lyckas returneras den associerade IP-adressen i målet som host_address_ptr.</span><span class="sxs-lookup"><span data-stu-id="04462-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="04462-538">Detta är en wrapper-funktion för tjänsten *nxd_dns_host_by_name_get* och är begränsad till IPv4-adress indata.</span><span class="sxs-lookup"><span data-stu-id="04462-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-539">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-539">Input Parameters</span></span>

- <span data-ttu-id="04462-540">**dns_ptr** Pekare till den tidigare skapade DNS-instansen.</span><span class="sxs-lookup"><span data-stu-id="04462-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="04462-541">**host_name** Pekare till värdnamn</span><span class="sxs-lookup"><span data-stu-id="04462-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="04462-542">**host_address_ptr** DNS-serverns IP-adress returnerades</span><span class="sxs-lookup"><span data-stu-id="04462-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="04462-543">**wait_option** Definierar hur länge tjänsten ska vänta på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="04462-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="04462-544">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04462-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="04462-545">timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="04462-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="04462-546">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="04462-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="04462-547">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="04462-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-548">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-548">Return Values</span></span>

- <span data-ttu-id="04462-549">**NX_SUCCESS** (0X00) DNS-matchning har genomförts.</span><span class="sxs-lookup"><span data-stu-id="04462-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="04462-550">**NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts</span><span class="sxs-lookup"><span data-stu-id="04462-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="04462-551">**NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan</span><span class="sxs-lookup"><span data-stu-id="04462-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="04462-552">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="04462-553">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="04462-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="04462-554">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-555">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-555">Allowed From</span></span>

<span data-ttu-id="04462-556">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-556">Threads</span></span>

<span data-ttu-id="04462-557">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="04462-557">**Example**</span></span>
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

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="04462-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="04462-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="04462-559">Sök efter en IP-adress från värd namnet</span><span class="sxs-lookup"><span data-stu-id="04462-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-560">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="04462-561">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-561">Description</span></span>

<span data-ttu-id="04462-562">Den här tjänsten begär namn matchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="04462-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="04462-563">Om det lyckas returneras den associerade IP-adressen i ett NXD_ADDRESS som pekas av *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="04462-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="04462-564">Om anroparen specifikt anger lookup_type indata till NX_IP_VERSION_V6 skickas frågan för en IPv6-adress (AAAA-post) för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="04462-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="04462-565">Om anroparen specifikt anger lookup_type indata till NX_IP_VERSION_V4 skickas en fråga för en IPv4-adress för värden (en post).</span><span class="sxs-lookup"><span data-stu-id="04462-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-566">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-566">Input Parameters</span></span>

- <span data-ttu-id="04462-567">**dns_ptr** Pekare till en tidigare skapad DNS-klient instans.</span><span class="sxs-lookup"><span data-stu-id="04462-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="04462-568">**host_name** Pekare till värd namnet för att hitta en IP-adress för</span><span class="sxs-lookup"><span data-stu-id="04462-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="04462-569">**host_address_ptr** Pekare till målet för NXD_ADDRESS som innehåller IP-adressen</span><span class="sxs-lookup"><span data-stu-id="04462-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="04462-570">**wait_option** Definierar hur länge tjänsten väntar på timer-Tick för DNS-serverns svar för varje frågans överföring och återöverföring.</span><span class="sxs-lookup"><span data-stu-id="04462-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="04462-571">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04462-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="04462-572">timeout-värde (0x00000001 till 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="04462-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="04462-573">Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden oändligt tills en DNS-Server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="04462-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="04462-574">Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="04462-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="04462-575">**lookup_type** Ange typ av sökning (A vs AAAA).</span><span class="sxs-lookup"><span data-stu-id="04462-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-576">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-576">Return Values</span></span>

- <span data-ttu-id="04462-577">**NX_SUCCESS** (0X00) DNS-matchning har genomförts.</span><span class="sxs-lookup"><span data-stu-id="04462-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="04462-578">**NX_DNS_NO_SERVER** (0XA1) ingen DNS-serveradress har angetts</span><span class="sxs-lookup"><span data-stu-id="04462-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="04462-579">**NX_DNS_QUERY_FAILED** (0XA3) fick inget svar på frågan</span><span class="sxs-lookup"><span data-stu-id="04462-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="04462-580">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata adress</span><span class="sxs-lookup"><span data-stu-id="04462-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="04462-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-582">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="04462-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="04462-583">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-584">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-585">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-585">Allowed From</span></span>

<span data-ttu-id="04462-586">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-586">Threads</span></span>

<span data-ttu-id="04462-587">**Exempel**</span><span class="sxs-lookup"><span data-stu-id="04462-587">**Example**</span></span>
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

<span data-ttu-id="04462-588">Ett annat exempel på att använda den här tids tjänsten, den här gången med IPv4-adresser och en post typer visas nedan:</span><span class="sxs-lookup"><span data-stu-id="04462-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="04462-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="04462-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="04462-590">Leta upp text strängen för det angivna domän namnet</span><span class="sxs-lookup"><span data-stu-id="04462-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-591">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="04462-592">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-592">Description</span></span>

<span data-ttu-id="04462-593">Den här tjänsten skickar en fråga av typen TXT med det angivna domän namnet och bufferten för att hämta godtyckliga sträng data.</span><span class="sxs-lookup"><span data-stu-id="04462-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="04462-594">DNS-klienten kopierar text strängen i TXT-posten i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="04462-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-595">Record_buffer behöver inte vara 4 byte-justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="04462-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-596">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-596">Input Parameters</span></span>

- <span data-ttu-id="04462-597">**dns_ptr** Pekare till DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="04462-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="04462-598">**host_name** Pekare till namnet på värden att söka på</span><span class="sxs-lookup"><span data-stu-id="04462-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="04462-599">**record_buffer** Pekare till platsen där du vill extrahera TXT-data till</span><span class="sxs-lookup"><span data-stu-id="04462-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="04462-600">**buffer_size** Buffertstorleken för att lagra TXT-data</span><span class="sxs-lookup"><span data-stu-id="04462-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="04462-601">**wait_option** Vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="04462-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-602">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-602">Return Values</span></span>

- <span data-ttu-id="04462-603">**NX_SUCCESS** (0x00) en returnerad txt-sträng</span><span class="sxs-lookup"><span data-stu-id="04462-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="04462-604">**NX_DNS_NO_SERVER** (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="04462-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="04462-605">**NX_DNS_QUERY_FAILED** (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="04462-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="04462-606">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="04462-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="04462-607">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-608">NX_DNS_PARAM_ERROR (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-609">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-609">Allowed From</span></span>

<span data-ttu-id="04462-610">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-610">Threads</span></span>

######   
<span data-ttu-id="04462-611">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-611">Example</span></span>
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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="04462-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="04462-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="04462-613">Ange pool för DNS-klient</span><span class="sxs-lookup"><span data-stu-id="04462-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-614">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="04462-615">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-615">Description</span></span>

<span data-ttu-id="04462-616">Den här tjänsten anger en tidigare skapad modempool som DNS-klientens adresspool.</span><span class="sxs-lookup"><span data-stu-id="04462-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="04462-617">DNS-klienten kommer att använda den här poolen för att skicka DNS-frågor, så paketets nytto Last bör inte vara mindre än NX_DNS_PACKET_PAYLOAD som inkluderar Ethernet-, IP-och UDP-huvudena och definieras i *nxd_dns. h.*</span><span class="sxs-lookup"><span data-stu-id="04462-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-618">Om DNS-klienten är borttagen tas inte poolen bort med den och det är programmets ansvar att ta bort modempoolen när den inte längre behöver den.</span><span class="sxs-lookup"><span data-stu-id="04462-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="04462-619">Den här tjänsten är bara tillgänglig om konfigurations alternativet NX_DNS_CLIENT_USER_CREATE_PACKET_POOL definierats i *nxd_dns. h*</span><span class="sxs-lookup"><span data-stu-id="04462-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-620">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-620">Input Parameters</span></span>

- <span data-ttu-id="04462-621">**dns_ptr** Pekare till en tidigare skapad DNS-klient instans.</span><span class="sxs-lookup"><span data-stu-id="04462-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="04462-622">**pool_ptr** Pekare till tidigare skapade paket pool</span><span class="sxs-lookup"><span data-stu-id="04462-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-623">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-623">Return Values</span></span>

- <span data-ttu-id="04462-624">**NX_SUCCESS** (0x00) slutfördes.</span><span class="sxs-lookup"><span data-stu-id="04462-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="04462-625">**NX_NOT_ENABLED** -klienten (0x14) har inte kon figurer ATS för det här alternativet</span><span class="sxs-lookup"><span data-stu-id="04462-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="04462-626">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="04462-627">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="04462-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-628">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-628">Allowed From</span></span>

<span data-ttu-id="04462-629">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-630">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-630">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="04462-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="04462-631">nx_dns_server_add</span></span>

<span data-ttu-id="04462-632">Lägg till DNS-serverns IP-adress</span><span class="sxs-lookup"><span data-stu-id="04462-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-633">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="04462-634">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-634">Description</span></span>

<span data-ttu-id="04462-635">Den här tjänsten lägger till en IPv4 DNS-server i Server listan.</span><span class="sxs-lookup"><span data-stu-id="04462-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-636">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-636">Input Parameters</span></span>

- <span data-ttu-id="04462-637">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="04462-638">**server_address** IP-adress för DNS-Server</span><span class="sxs-lookup"><span data-stu-id="04462-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-639">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-639">Return Values</span></span>

- <span data-ttu-id="04462-640">**NX_SUCCESS** (0x00)-servern har lagts till</span><span class="sxs-lookup"><span data-stu-id="04462-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="04462-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="04462-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="04462-642">**NX_NO_MORE_ENTRIES** (0X17) inga fler DNS-servrar tillåts (listan är full)</span><span class="sxs-lookup"><span data-stu-id="04462-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="04462-643">**NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="04462-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-645">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="04462-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="04462-646">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) null-indata för server adress</span><span class="sxs-lookup"><span data-stu-id="04462-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-648">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-648">Allowed From</span></span>

<span data-ttu-id="04462-649">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-650">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="04462-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="04462-651">nxd_dns_server_add</span></span>

<span data-ttu-id="04462-652">Lägg till DNS-server i klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-653">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="04462-654">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-654">Description</span></span>

<span data-ttu-id="04462-655">Den här tjänsten lägger till IP-adressen för en DNS-server i listan DNS-klientkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="04462-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="04462-656">Server_address kan vara antingen en IPv4-eller IPv6-adress.</span><span class="sxs-lookup"><span data-stu-id="04462-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="04462-657">Om klienten vill kunna komma åt samma server med en IPv4-adress eller IPv6-adress ska den lägga till båda IP-adresserna som poster i Server listan.</span><span class="sxs-lookup"><span data-stu-id="04462-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-658">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-658">Input Parameters</span></span>

- <span data-ttu-id="04462-659">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="04462-660">**server_address** Pekar till den NXD_ADDRESS som innehåller serverns IP-adress för DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="04462-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-661">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-661">Return Values</span></span>

- <span data-ttu-id="04462-662">**NX_SUCCESS** (0x00)-servern har lagts till</span><span class="sxs-lookup"><span data-stu-id="04462-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="04462-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="04462-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="04462-664">**NX_NO_MORE_ENTRIES** (0X17) inga fler DNS-servrar tillåts (listan är full)</span><span class="sxs-lookup"><span data-stu-id="04462-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="04462-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-666">**NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="04462-667">NX_PTR_ERROR (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="04462-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="04462-668">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) null-indata för server adress</span><span class="sxs-lookup"><span data-stu-id="04462-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="04462-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) index pekar på ogiltig adress typ (t. ex. IPv6)</span><span class="sxs-lookup"><span data-stu-id="04462-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-671">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-671">Allowed From</span></span>

<span data-ttu-id="04462-672">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-673">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-673">Example</span></span>
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

## <a name="nx_dns_server_get"></a><span data-ttu-id="04462-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="04462-674">nx_dns_server_get</span></span>

<span data-ttu-id="04462-675">Returnera en IPv4 DNS-server från klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-676">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="04462-677">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-677">Description</span></span>

<span data-ttu-id="04462-678">Den här tjänsten returnerar IPv4 DNS-serveradressen från server listan vid det angivna indexet.</span><span class="sxs-lookup"><span data-stu-id="04462-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-679">Indexet är noll baserat.</span><span class="sxs-lookup"><span data-stu-id="04462-679">The index is zero based.</span></span> <span data-ttu-id="04462-680">Om indata-indexet överskrider storleken på listan över DNS-klienter, finns det en IPv6-adress i indexet eller en null-adress som finns i det angivna indexet. ett fel returneras.</span><span class="sxs-lookup"><span data-stu-id="04462-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="04462-681">Den *nx_dns_get_serverlist_size* tjänsten kan anropas först hämta antalet DNS-servrar i klient listan.</span><span class="sxs-lookup"><span data-stu-id="04462-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="04462-682">Den här tjänsten stöder endast IPv4-adresser.</span><span class="sxs-lookup"><span data-stu-id="04462-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="04462-683">Den anropar tjänsten *nxd_dns_server_get* som stöder både IPv4-och IPv6-adresser.</span><span class="sxs-lookup"><span data-stu-id="04462-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-684">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-684">Input Parameters</span></span>

- <span data-ttu-id="04462-685">**dns_ptr** Pekare till DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="04462-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="04462-686">**index** Indexera till DNS-klientens lista över servrar</span><span class="sxs-lookup"><span data-stu-id="04462-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="04462-687">**dns_server_address** Pekare till IP-adressen för DNS-servern</span><span class="sxs-lookup"><span data-stu-id="04462-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-688">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-688">Return Values</span></span>

- <span data-ttu-id="04462-689">**NX_SUCCESS** (0x00) returnerad Server</span><span class="sxs-lookup"><span data-stu-id="04462-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="04462-690">**NX_DNS_SERVER_NOT_FOUND** (0XA9) index pekar på tom plats</span><span class="sxs-lookup"><span data-stu-id="04462-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="04462-691">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) index pekar på null-adress</span><span class="sxs-lookup"><span data-stu-id="04462-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="04462-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)</span><span class="sxs-lookup"><span data-stu-id="04462-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="04462-693">**NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="04462-694">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="04462-695">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-696">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-696">Allowed From</span></span>

<span data-ttu-id="04462-697">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-698">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="04462-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="04462-699">nxd_dns_server_get</span></span>

<span data-ttu-id="04462-700">Returnera en DNS-server från klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-701">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="04462-702">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-702">Description</span></span>

<span data-ttu-id="04462-703">Den här tjänsten returnerar DNS-serverns IP-adress från server listan vid det angivna indexet.</span><span class="sxs-lookup"><span data-stu-id="04462-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="04462-704">Indexet är noll baserat.</span><span class="sxs-lookup"><span data-stu-id="04462-704">The index is zero based.</span></span> <span data-ttu-id="04462-705">Om indata-indexet överskrider storleken på listan över DNS-klienter, eller om en null-adress hittas vid det angivna indexet, returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="04462-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="04462-706">Den *nx_dns_get_serverlist_size* tjänsten kan anropas först för att erhålla antalet DNS-servrar i Server listan.</span><span class="sxs-lookup"><span data-stu-id="04462-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="04462-707">Den här tjänsten har stöd för IPv4-och IPv6-adresser.</span><span class="sxs-lookup"><span data-stu-id="04462-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-708">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-708">Input Parameters</span></span>

- <span data-ttu-id="04462-709">**dns_ptr** Pekare till DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="04462-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="04462-710">**index** Indexera till DNS-klientens lista över servrar</span><span class="sxs-lookup"><span data-stu-id="04462-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="04462-711">**dns_server_address** Pekare till IP-adressen för DNS-servern</span><span class="sxs-lookup"><span data-stu-id="04462-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-712">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-712">Return Values</span></span>

- <span data-ttu-id="04462-713">**NX_SUCCESS** (0x00) returnerade SERVERNS IP-adress</span><span class="sxs-lookup"><span data-stu-id="04462-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="04462-714">**NX_DNS_SERVER_NOT_FOUND** (0XA9) index pekar på tom plats</span><span class="sxs-lookup"><span data-stu-id="04462-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="04462-715">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) index pekar på en null-serveradress</span><span class="sxs-lookup"><span data-stu-id="04462-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="04462-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)</span><span class="sxs-lookup"><span data-stu-id="04462-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="04462-717">**NX_DNS_PARAM_ERROR** (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="04462-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="04462-718">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="04462-719">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-720">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-720">Allowed From</span></span>

<span data-ttu-id="04462-721">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-722">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="04462-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="04462-723">nx_dns_server_remove</span></span>

<span data-ttu-id="04462-724">Ta bort en IPv4 DNS-server från klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-725">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="04462-726">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-726">Description</span></span>

<span data-ttu-id="04462-727">Den här tjänsten tar bort en IPv4 DNS-server från klient listan.</span><span class="sxs-lookup"><span data-stu-id="04462-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="04462-728">Det är en wrapper-funktion för *nxd_dns_server_remove*.</span><span class="sxs-lookup"><span data-stu-id="04462-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-729">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-729">Input Parameters</span></span>

- <span data-ttu-id="04462-730">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="04462-731">**server_address** IP-adressen för DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="04462-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-732">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-732">Return Values</span></span>

- <span data-ttu-id="04462-733">**NX_SUCCESS** (0X00) DNS-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="04462-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="04462-734">**NX_DNS_SERVER_NOT_FOUND** -servern (0xA9) inte i klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="04462-735">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata för server adress</span><span class="sxs-lookup"><span data-stu-id="04462-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="04462-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-737">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="04462-738">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-739">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-739">Allowed From</span></span>

<span data-ttu-id="04462-740">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-741">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="04462-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="04462-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="04462-743">Ta bort en DNS-server från klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-744">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="04462-745">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-745">Description</span></span>

<span data-ttu-id="04462-746">Den här tjänsten tar bort en DNS-server med den angivna IP-adressen från klient listan.</span><span class="sxs-lookup"><span data-stu-id="04462-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="04462-747">IP-adressen för indata accepterar både IPv4-och IPv6-adresser.</span><span class="sxs-lookup"><span data-stu-id="04462-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="04462-748">När servern har tagits bort flyttas de återstående servrarna nedåt ett index i listan för att fylla vacated-facket.</span><span class="sxs-lookup"><span data-stu-id="04462-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-749">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-749">Input Parameters</span></span>

- <span data-ttu-id="04462-750">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="04462-751">**server_address** Pekare till DNS-Server NXD_ADDRESS data som innehåller Server-IP-adress.</span><span class="sxs-lookup"><span data-stu-id="04462-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-752">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-752">Return Values</span></span>

- <span data-ttu-id="04462-753">**NX_SUCCESS** (0X00) DNS-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="04462-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="04462-754">**NX_DNS_SERVER_NOT_FOUND** -servern (0xA9) inte i klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="04462-755">**NX_DNS_BAD_ADDRESS_ERROR** (0XA4) null-indata för server adress</span><span class="sxs-lookup"><span data-stu-id="04462-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="04462-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0XB3) kan inte bearbeta posten med IPv6 inaktiverat</span><span class="sxs-lookup"><span data-stu-id="04462-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="04462-757">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="04462-758">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="04462-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) index pekar på ogiltig adress typ (t. ex. IPv6)</span><span class="sxs-lookup"><span data-stu-id="04462-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-760">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-760">Allowed From</span></span>

<span data-ttu-id="04462-761">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-762">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-762">Example</span></span>
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

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="04462-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="04462-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="04462-764">Ta bort alla DNS-servrar från klient listan</span><span class="sxs-lookup"><span data-stu-id="04462-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="04462-765">Prototyp</span><span class="sxs-lookup"><span data-stu-id="04462-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="04462-766">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="04462-766">Description</span></span>

<span data-ttu-id="04462-767">Den här tjänsten tar bort alla DNS-servrar från klient listan.</span><span class="sxs-lookup"><span data-stu-id="04462-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="04462-768">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="04462-768">Input Parameters</span></span>

- <span data-ttu-id="04462-769">**dns_ptr** Pekare till DNS-Control-Block.</span><span class="sxs-lookup"><span data-stu-id="04462-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="04462-770">Retur värden</span><span class="sxs-lookup"><span data-stu-id="04462-770">Return Values</span></span>

- <span data-ttu-id="04462-771">**NX_SUCCESS** (0X00) DNS-servrar har tagits bort</span><span class="sxs-lookup"><span data-stu-id="04462-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="04462-772">**NX_DNS_ERROR** (0XA0) Det gick inte att hämta skydds-mutex</span><span class="sxs-lookup"><span data-stu-id="04462-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="04462-773">NX_PTR_ERROR (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="04462-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="04462-774">NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="04462-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="04462-775">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="04462-775">Allowed From</span></span>

<span data-ttu-id="04462-776">Konversation</span><span class="sxs-lookup"><span data-stu-id="04462-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="04462-777">Exempel</span><span class="sxs-lookup"><span data-stu-id="04462-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```