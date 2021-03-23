---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX DNS Client Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DNS-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826751"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="328f4-103">Kapitel 3 – Beskrivning av Azure återställnings tider NetX DNS Client Services</span><span class="sxs-lookup"><span data-stu-id="328f4-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="328f4-104">Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX DNS-tjänster (visas nedan) i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="328f4-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="328f4-105">I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="328f4-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="328f4-106">**nx_dns_authority_zone_start_get**: *Leta upp starten av en zon för auktoritet som är associerad med det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="328f4-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="328f4-107">**nx_dns_cache_initialize**: *initiera en DNS-cache.*</span><span class="sxs-lookup"><span data-stu-id="328f4-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="328f4-108">**nx_dns_cache_notify_clear**: *Rensa cachen fullständig aviserings funktion.*</span><span class="sxs-lookup"><span data-stu-id="328f4-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="328f4-109">**nx_dns_cache_notify_set**: *Ange fullständig meddelande funktion för cachen.*</span><span class="sxs-lookup"><span data-stu-id="328f4-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="328f4-110">**nx_dns_cname_get**: *Leta upp det kanoniska domän namnet för aliaset för den inmatade domänen*</span><span class="sxs-lookup"><span data-stu-id="328f4-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="328f4-111">**nx_dns_create**: *skapa en DNS-klient instans*</span><span class="sxs-lookup"><span data-stu-id="328f4-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="328f4-112">**nx_dns_delete**: *ta bort en DNS-klient instans*</span><span class="sxs-lookup"><span data-stu-id="328f4-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="328f4-113">**nx_dns_domain_name_server_get**: *Leta upp auktoritativa namnservrar för zonen för inmatade domäner*</span><span class="sxs-lookup"><span data-stu-id="328f4-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="328f4-114">**nx_dns_domain_mail_exchange_get**: *slå upp e-postmeddelandet som är kopplat till det angivna värd namnet.*</span><span class="sxs-lookup"><span data-stu-id="328f4-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="328f4-115">**nx_dns_domain_service_get**: *slå upp de tjänster som är associerade med det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="328f4-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="328f4-116">**nx_dns_get_serverlist_size**: *returnera storleken på listan över DNS-klientinställningar*</span><span class="sxs-lookup"><span data-stu-id="328f4-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="328f4-117">**nx_dns_info_by_name_get**: *returnera IP-adress, Port fråga på indata-värdnamn*</span><span class="sxs-lookup"><span data-stu-id="328f4-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="328f4-118">**nx_dns_ipv4_address_by_name_get**: *Leta upp IPv4-adressen från det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="328f4-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="328f4-119">**nx_dns_host_by_address_get**: *Leta upp ett värdnamn från en angiven IP-adress*</span><span class="sxs-lookup"><span data-stu-id="328f4-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="328f4-120">**nx_dns_host_by_name_get**: *Leta upp IPv4-adressen från det angivna värd namnet*</span><span class="sxs-lookup"><span data-stu-id="328f4-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="328f4-121">**nx_dns_host_text_get**: *Leta upp text data för det angivna domän namnet*</span><span class="sxs-lookup"><span data-stu-id="328f4-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="328f4-122">**nx_dns_packet_pool_set**: *Ange DNS-anslutningspoolen för klienter*</span><span class="sxs-lookup"><span data-stu-id="328f4-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="328f4-123">**nx_dns_server_add**: *Lägg till en DNS-server på den angivna adressen i klient listan*</span><span class="sxs-lookup"><span data-stu-id="328f4-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="328f4-124">**nx_dns_server_get**: *returnera DNS-servern i klient listan*</span><span class="sxs-lookup"><span data-stu-id="328f4-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="328f4-125">**nx_dns_server_remove**: *ta bort en DNS-server från klient listan*</span><span class="sxs-lookup"><span data-stu-id="328f4-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="328f4-126">**nx_dns_server_remove_all**: *ta bort alla DNS-servrar från klient listan*</span><span class="sxs-lookup"><span data-stu-id="328f4-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="328f4-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="328f4-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="328f4-128">Leta upp starten av auktoritets zonen för den angivna värden</span><span class="sxs-lookup"><span data-stu-id="328f4-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-129">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="328f4-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-130">Description</span></span>

<span data-ttu-id="328f4-131">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SOA med det angivna domän namnet för att hämta start zonen för auktoriteten för det angivna domän namnet.</span><span class="sxs-lookup"><span data-stu-id="328f4-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="328f4-132">DNS-klienten kopierar de SOA-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="328f4-133">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="328f4-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="328f4-134">I NetX DNS-klient sparas SOA-posttypen NX_DNS_SOA_ENTRY, som 7 4 byte-parametrar, totalt 28 byte:</span><span class="sxs-lookup"><span data-stu-id="328f4-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="328f4-135">**nx_dns_soa_host_mname_ptr**: pekar mot primär data källa för den här zonen</span><span class="sxs-lookup"><span data-stu-id="328f4-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="328f4-136">**nx_dns_soa_host_rname_ptr**: pekar mot post lådan som ansvarar för zonen</span><span class="sxs-lookup"><span data-stu-id="328f4-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="328f4-137">**nx_dns_soa_serial**: zon versions nummer</span><span class="sxs-lookup"><span data-stu-id="328f4-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="328f4-138">**nx_dns_soa_refresh**: uppdaterings intervall</span><span class="sxs-lookup"><span data-stu-id="328f4-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="328f4-139">**nx_dns_soa_retry**: intervall mellan SOA-frågekörning försök</span><span class="sxs-lookup"><span data-stu-id="328f4-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="328f4-140">**nx_dns_soa_expire**: tids period när SOA upphör att gälla</span><span class="sxs-lookup"><span data-stu-id="328f4-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="328f4-141">**nx_dns_soa_minmum**: minsta TTL-fält i SOA värdnamn DNS-svarsmeddelanden</span><span class="sxs-lookup"><span data-stu-id="328f4-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="328f4-142">Lagringen av två SOA-poster visas nedan.</span><span class="sxs-lookup"><span data-stu-id="328f4-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="328f4-143">De SOA-poster som innehåller fasta längd data anges med början överst i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="328f4-144">Pekarna MNAME och RNAME pekar på variabla längd data (värd namn) som lagras längst ned i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="328f4-145">Ytterligare SOA-poster anges efter den första posten ("ytterligare SOA-poster...") och deras variabla längd data lagras ovanför den sista postens variabla längd data ("ytterligare data för SOA-variabel längd"):</span><span class="sxs-lookup"><span data-stu-id="328f4-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Diagram som representerar lagringen av två S O A-poster](media/image2.png)

<span data-ttu-id="328f4-147">Om indata- *record_buffer* inte rymmer alla SOA-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="328f4-148">Med antalet SOA-poster som returneras i \**record_count* kan programmet parsa data från *record_buffer* och extrahera start av värd namn strängar för zon utfärdare.</span><span class="sxs-lookup"><span data-stu-id="328f4-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-149">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-149">Input Parameters</span></span>

- <span data-ttu-id="328f4-150">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-151">**host_name**: pekare till värd namnet för att hämta SOA-data för</span><span class="sxs-lookup"><span data-stu-id="328f4-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="328f4-152">**record_buffer**: pekare till plats att extrahera SOA-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="328f4-153">**buffer_size**: storleken på bufferten som ska innehålla SOA-data</span><span class="sxs-lookup"><span data-stu-id="328f4-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="328f4-154">**record_count**: pekar mot antalet SOA-poster som hämtats</span><span class="sxs-lookup"><span data-stu-id="328f4-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="328f4-155">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-156">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-156">Return Values</span></span>

- <span data-ttu-id="328f4-157">**NX_SUCCESS**: (0X00) har hämtat SOA-data</span><span class="sxs-lookup"><span data-stu-id="328f4-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="328f4-158">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-159">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-160">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-161">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="328f4-162">NX_DNS_PARAM_ERROR: (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-163">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-163">Allowed From</span></span>

<span data-ttu-id="328f4-164">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-165">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-165">Example</span></span>
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

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

```

```Output
Test SOA:
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="328f4-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="328f4-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="328f4-167">Initiera DNS-cachen</span><span class="sxs-lookup"><span data-stu-id="328f4-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-168">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="328f4-169">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-169">Description</span></span>

<span data-ttu-id="328f4-170">Den här tjänsten skapar och initierar en DNS-cache.</span><span class="sxs-lookup"><span data-stu-id="328f4-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-171">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-171">Input Parameters</span></span>

- <span data-ttu-id="328f4-172">**dns_ptr**: pekar mot DNS-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="328f4-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="328f4-173">**cache_ptr**: pekar mot DNS-cache.</span><span class="sxs-lookup"><span data-stu-id="328f4-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="328f4-174">**cache_size**: DNS-cachens storlek, i byte.</span><span class="sxs-lookup"><span data-stu-id="328f4-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-175">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-175">Return Values</span></span>

- <span data-ttu-id="328f4-176">**NX_SUCCESS**: (0X00) DNS-cache har initierats</span><span class="sxs-lookup"><span data-stu-id="328f4-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="328f4-177">NX_DNS_ERROR: (0xA0) cache är inte 4-byte-justerad.</span><span class="sxs-lookup"><span data-stu-id="328f4-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="328f4-178">NX_DNS_PARAM_ERROR: (0xA8) ogiltigt DNS-ID.</span><span class="sxs-lookup"><span data-stu-id="328f4-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="328f4-179">NX_PTR_ERROR: (0x07) ogiltig DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="328f4-180">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-181">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-181">Allowed From</span></span>

<span data-ttu-id="328f4-182">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-183">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="328f4-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="328f4-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="328f4-185">Rensa DNS-cachens fullständiga meddelande funktion</span><span class="sxs-lookup"><span data-stu-id="328f4-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-186">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="328f4-187">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-187">Description</span></span>

<span data-ttu-id="328f4-188">Den här tjänsten rensar cachen fullständig aviserings funktion.</span><span class="sxs-lookup"><span data-stu-id="328f4-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-189">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-189">Input Parameters</span></span>

- <span data-ttu-id="328f4-190">**dns_ptr**: pekar mot DNS-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="328f4-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-191">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-191">Return Values</span></span>

- <span data-ttu-id="328f4-192">**NX_SUCCESS**: (0X00) DNS-cache-avisering har angetts</span><span class="sxs-lookup"><span data-stu-id="328f4-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="328f4-193">NX_DNS_PARAM_ERROR: (0xA8) ogiltigt DNS-ID.</span><span class="sxs-lookup"><span data-stu-id="328f4-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="328f4-194">NX_PTR_ERROR: (0x07) ogiltig DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-195">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-195">Allowed From</span></span>

<span data-ttu-id="328f4-196">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-197">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="328f4-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="328f4-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="328f4-199">Ange fullständig meddelande funktion för DNS-cache</span><span class="sxs-lookup"><span data-stu-id="328f4-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-200">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="328f4-201">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-201">Description</span></span>

<span data-ttu-id="328f4-202">Den här tjänsten anger den fullständiga aviserings funktionen cache.</span><span class="sxs-lookup"><span data-stu-id="328f4-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-203">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-203">Input Parameters</span></span>

- <span data-ttu-id="328f4-204">**dns_ptr**: pekar mot DNS-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="328f4-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="328f4-205">**cache_full_notify_cb**: motringningsfunktionen som anropas när cachen blir full.</span><span class="sxs-lookup"><span data-stu-id="328f4-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-206">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-206">Return Values</span></span>

- <span data-ttu-id="328f4-207">**NX_SUCCESS**: (0X00) DNS-cache-avisering har angetts</span><span class="sxs-lookup"><span data-stu-id="328f4-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="328f4-208">NX_DNS_PARAM_ERROR: (0xA8) ogiltigt DNS-ID.</span><span class="sxs-lookup"><span data-stu-id="328f4-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="328f4-209">NX_PTR_ERROR: (0x07) ogiltig DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-210">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-210">Allowed From</span></span>

<span data-ttu-id="328f4-211">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-212">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="328f4-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="328f4-213">nx_dns_cname_get</span></span>

<span data-ttu-id="328f4-214">Leta upp det kanoniska namnet för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-215">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-216">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-216">Description</span></span>

<span data-ttu-id="328f4-217">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES definieras i *nx_dns. h* skickar den här tjänsten en fråga av typen CNAME med det angivna domän namnet för att hämta det kanoniska domän namnet.</span><span class="sxs-lookup"><span data-stu-id="328f4-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="328f4-218">DNS-klienten kopierar den CNAME-sträng som returnerades i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-219">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-219">Input Parameters</span></span>

- <span data-ttu-id="328f4-220">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-221">**host_name**: pekare till värd namn för att hämta CNAME-data för</span><span class="sxs-lookup"><span data-stu-id="328f4-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="328f4-222">**record_buffer**: pekare till platsen där du vill extrahera CNAME-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="328f4-223">**buffer_size**: buffertstorleken för att lagra CNAME-data</span><span class="sxs-lookup"><span data-stu-id="328f4-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="328f4-224">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-225">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-225">Return Values</span></span>

- <span data-ttu-id="328f4-226">**NX_SUCCESS**: (0x00) hämtade CNAME-data</span><span class="sxs-lookup"><span data-stu-id="328f4-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="328f4-227">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-228">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-229">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-230">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="328f4-231">NX_DNS_PARAM_ERROR: (0xA8) ogiltig Indatatyp för icke-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-232">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-232">Allowed From</span></span>

<span data-ttu-id="328f4-233">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-234">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-234">Example</span></span>

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a><span data-ttu-id="328f4-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="328f4-235">nx_dns_create</span></span>

<span data-ttu-id="328f4-236">Skapa en DNS-klient instans</span><span class="sxs-lookup"><span data-stu-id="328f4-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-237">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="328f4-238">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-238">Description</span></span>

<span data-ttu-id="328f4-239">Den här tjänsten skapar en DNS-klient instans för den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="328f4-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="328f4-240">Programmet måste se till att paket nytto lasten för den modempool som används av DNS-klienten är tillräckligt stor för maximalt 512 byte DNS-meddelande, plus UDP-, IP-och Ethernet-rubriker.</span><span class="sxs-lookup"><span data-stu-id="328f4-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="328f4-241">Om DNS-klienten skapar en egen modempool, definieras detta av NX_DNS_PACKET_POOL_SIZE och NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="328f4-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="328f4-242">Om DNS-klientprogrammet föredrar att tillhandahålla en tidigare skapad modempool ska nytto lasten för IPv4 DNS-klienten vara 512 byte för maximalt antal DNS plus 20 byte för IP-huvudet, 8 byte för UDP-huvudet och 14 byte för Ethernet-huvudet.</span><span class="sxs-lookup"><span data-stu-id="328f4-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-243">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-243">Input Parameters</span></span>

- <span data-ttu-id="328f4-244">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-245">**ip_ptr**: pekare till den tidigare skapade IP-instansen.</span><span class="sxs-lookup"><span data-stu-id="328f4-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="328f4-246">**domain_name**: pekar på domän namn för DNS-instans.</span><span class="sxs-lookup"><span data-stu-id="328f4-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-247">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-247">Return Values</span></span>

- <span data-ttu-id="328f4-248">**NX_SUCCESS**: (0X00) lyckad DNS-skapande</span><span class="sxs-lookup"><span data-stu-id="328f4-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="328f4-249">**NX_DNS_ERROR**: (0XA0) DNS-skapande fel</span><span class="sxs-lookup"><span data-stu-id="328f4-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="328f4-250">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-251">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-252">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-252">Allowed From</span></span>

<span data-ttu-id="328f4-253">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-254">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="328f4-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="328f4-255">nx_dns_delete</span></span>

<span data-ttu-id="328f4-256">Ta bort en DNS-klient instans</span><span class="sxs-lookup"><span data-stu-id="328f4-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-257">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="328f4-258">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-258">Description</span></span>

<span data-ttu-id="328f4-259">Den här tjänsten tar bort en tidigare skapad DNS-klient instans och frigör sina resurser.</span><span class="sxs-lookup"><span data-stu-id="328f4-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="328f4-260">Om **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** har definierats och DNS-klienten tilldelats en användardefinierad modempool, är det upp till programmet att ta bort DNS-klientcachen om den inte längre behöver den.</span><span class="sxs-lookup"><span data-stu-id="328f4-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-261">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-261">Input Parameters</span></span>

- <span data-ttu-id="328f4-262">**dns_ptr**: pekar mot en tidigare skapad DNS- **klient** instans.</span><span class="sxs-lookup"><span data-stu-id="328f4-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-263">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-263">Return Values</span></span>

- <span data-ttu-id="328f4-264">**NX_SUCCESS**: (0X00) lyckade DNS-klient borttagningar.</span><span class="sxs-lookup"><span data-stu-id="328f4-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="328f4-265">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-klient pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="328f4-266">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="328f4-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-267">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-267">Allowed From</span></span>

<span data-ttu-id="328f4-268">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-269">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="328f4-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="328f4-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="328f4-271">Leta upp auktoritativa namnservrar för den inmatade domän zonen</span><span class="sxs-lookup"><span data-stu-id="328f4-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-272">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-273">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-273">Description</span></span>

<span data-ttu-id="328f4-274">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen NS med det angivna domän namnet för att hämta namnservrarna för det inmatade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="328f4-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="328f4-275">DNS-klienten kopierar den eller de NS-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="328f4-276">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="328f4-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="328f4-277">I NetX DNS-klient har data typen NS, NX_DNS_NS_ENTRY, sparats som 2 4 byte-parametrar:</span><span class="sxs-lookup"><span data-stu-id="328f4-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="328f4-278">**nx_dns_ns_ipv4_address**: namn serverns IPv4-adress</span><span class="sxs-lookup"><span data-stu-id="328f4-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="328f4-279">**nx_dns_ns_hostname_ptr**: pekar mot namn serverns värdnamn</span><span class="sxs-lookup"><span data-stu-id="328f4-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="328f4-280">Den buffert som visas nedan innehåller fyra NX_DNS_NS_ENTRY poster.</span><span class="sxs-lookup"><span data-stu-id="328f4-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="328f4-281">Pekaren som är värd för namn sträng i varje post pekar mot motsvarande värd namn sträng i den nedre halvan av bufferten:</span><span class="sxs-lookup"><span data-stu-id="328f4-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Diagram över bufferten som innehåller fyra N X D N s post poster.](media/image3.png)

<span data-ttu-id="328f4-283">Om indata- *record_buffer* inte rymmer alla ns-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="328f4-284">Med antalet NS-poster som returneras i \**record_count* kan programmet parsa IP-adressen och värd namnet för varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="328f4-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-285">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-285">Input Parameters</span></span>

- <span data-ttu-id="328f4-286">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-287">**host_name**: pekare till värdnamn för att hämta ns-data för</span><span class="sxs-lookup"><span data-stu-id="328f4-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="328f4-288">**record_buffer**: pekare till platsen för att extrahera ns-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="328f4-289">**buffer_size**: storleken på bufferten som ska innehålla ns-data</span><span class="sxs-lookup"><span data-stu-id="328f4-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="328f4-290">**record_count**: pekar mot antalet hämtade NS-poster</span><span class="sxs-lookup"><span data-stu-id="328f4-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="328f4-291">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-292">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-292">Return Values</span></span>

- <span data-ttu-id="328f4-293">**NX_SUCCESS**: (0x00) hämtade ns-data</span><span class="sxs-lookup"><span data-stu-id="328f4-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="328f4-294">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-295">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-296">NX_DNS_PARAM_ERROR: (0xA8) ogiltigt DNS-ID.</span><span class="sxs-lookup"><span data-stu-id="328f4-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="328f4-297">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-298">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-299">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-299">Allowed From</span></span>

<span data-ttu-id="328f4-300">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-301">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-301">Example</span></span>
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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
```

```Output
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="328f4-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="328f4-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="328f4-303">Slå upp e-post Exchange (s) för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-304">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="328f4-305">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-305">Description</span></span>

<span data-ttu-id="328f4-306">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen MX med det angivna domän namnet för att hämta e-postadressen för det inmatade domän namnet.</span><span class="sxs-lookup"><span data-stu-id="328f4-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="328f4-307">DNS-klienten kopierar MX-post (er) som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="328f4-308">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="328f4-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="328f4-309">I NetX DNS-klient sparas post typen post Exchange, NX_DNS_MAIL_EXCHANGE_ENTRY, som fyra parametrar, med summering av 12 byte:</span><span class="sxs-lookup"><span data-stu-id="328f4-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="328f4-310">**nx_dns_mx_ipv4_address**: e-post Exchange IPv4-adress 4 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="328f4-311">**nx_dns_mx_preference**: Preference 2 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="328f4-312">**nx_dns_mx_reserved0**: reserverade 2 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="328f4-313">**nx_dns_mx_hostname_ptr**: pekare till e-post Exchange Server-värdnamn 4 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="328f4-314">En buffert som innehåller fyra MX-poster visas nedan.</span><span class="sxs-lookup"><span data-stu-id="328f4-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="328f4-315">Varje post innehåller data för fast längd från listan ovan.</span><span class="sxs-lookup"><span data-stu-id="328f4-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="328f4-316">Pekaren till e-postadressen till Exchange-servern pekar på motsvarande värdnamn längst ned i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Diagram som visar bufferten som innehåller fyra M X-poster.](media/image4.png)

<span data-ttu-id="328f4-318">Om indata- *record_buffer* inte rymmer alla MX-data i svaret på servern så innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="328f4-319">Med antalet MX-poster som returneras i \**record_count* kan programmet parsa MX-parametrarna, inklusive e-postvärdnamnet för varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="328f4-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-320">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-320">Input Parameters</span></span>

- <span data-ttu-id="328f4-321">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-322">**host_name**: pekare till värdnamn för att hämta MX-data för</span><span class="sxs-lookup"><span data-stu-id="328f4-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="328f4-323">**record_buffer**: pekare till plats att extrahera MX-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="328f4-324">**buffer_size**: storleken på bufferten som ska innehålla MX-data</span><span class="sxs-lookup"><span data-stu-id="328f4-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="328f4-325">**record_count**: pekar mot antalet MX-poster som hämtats</span><span class="sxs-lookup"><span data-stu-id="328f4-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="328f4-326">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-327">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-327">Return Values</span></span>

- <span data-ttu-id="328f4-328">**NX_SUCCESS**: (0X00) har hämtat MX-data</span><span class="sxs-lookup"><span data-stu-id="328f4-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="328f4-329">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-330">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-331">NX_DNS_PARAM_ERROR: (0xA8) ogiltigt DNS-ID.</span><span class="sxs-lookup"><span data-stu-id="328f4-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="328f4-332">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-333">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-334">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-334">Allowed From</span></span>

<span data-ttu-id="328f4-335">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-336">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-336">Example</span></span>
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
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


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="328f4-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="328f4-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="328f4-338">Leta upp de tjänster som tillhandahålls av det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-339">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-340">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-340">Description</span></span>

<span data-ttu-id="328f4-341">Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har definierats skickar den här tjänsten en fråga av typen SRV med det angivna domän namnet för att leta upp de tjänster och deras port nummer som är associerade med den angivna domänen.</span><span class="sxs-lookup"><span data-stu-id="328f4-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="328f4-342">DNS-klienten kopierar de SRV-poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="328f4-343">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="328f4-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="328f4-344">I NetX DNS-klient sparas tjänst post typen NX_DNS_SRV_ post som sex parametrar, vilket innebär att 16 byte summeras.</span><span class="sxs-lookup"><span data-stu-id="328f4-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="328f4-345">Detta gör att SRV-data för variabel längd lagras på ett minnes effektivt sätt:</span><span class="sxs-lookup"><span data-stu-id="328f4-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="328f4-346">**Serverns IPv4-adress**: nx_dns_srv_ipv4_address 4 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="328f4-347">**Server prioritet**: nx_dns_srv_priority 2 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="328f4-348">**Server vikt**: nx_dns_srv_weight 2 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="328f4-349">**Tjänst port nummer**: nx_dns_srv_port_number 2 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="328f4-350">**Reserverad för 4-byte-justering**: nx_dns_srv_reserved0 2 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="328f4-351">**Pekare till serverns värdnamn**: \* nx_dns_srv_hostname_ptr 4 byte</span><span class="sxs-lookup"><span data-stu-id="328f4-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="328f4-352">Fyra SRV-poster lagras i den angivna bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="328f4-353">Varje NX_DNS_SRV_ENTRY post innehåller en pekare, *nx_dns_srv_hostname_ptr*, som pekar på motsvarande värd namn sträng längst ned i bufferten för poster:</span><span class="sxs-lookup"><span data-stu-id="328f4-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Diagram över fyra S R V-poster som lagras i den angivna bufferten.](media/image5.png)

<span data-ttu-id="328f4-355">Om indata- *record_buffer* inte rymmer alla SRV-data i Server svaret innehåller *record_buffer* så många poster som får plats och returnerar antalet poster i bufferten.</span><span class="sxs-lookup"><span data-stu-id="328f4-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="328f4-356">Med antalet SRV-poster som returneras i \**record_count* kan programmet parsa SRV-parametrarna, inklusive Server värd namnet för varje post i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="328f4-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-357">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-357">Input Parameters</span></span>

- <span data-ttu-id="328f4-358">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-359">**host_name**: pekare till värdnamn för att hämta SRV-data för</span><span class="sxs-lookup"><span data-stu-id="328f4-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="328f4-360">**record_buffer**: pekare till plats för att extrahera SRV-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="328f4-361">**buffer_size**: storleken på bufferten som ska innehålla SRV-data</span><span class="sxs-lookup"><span data-stu-id="328f4-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="328f4-362">**record_count**: pekar mot antalet SRV-poster som hämtats</span><span class="sxs-lookup"><span data-stu-id="328f4-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="328f4-363">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-364">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-364">Return Values</span></span>

- <span data-ttu-id="328f4-365">**NX_SUCCESS**: (0x00) hämtade SRV-data</span><span class="sxs-lookup"><span data-stu-id="328f4-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="328f4-366">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-367">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-368">NX_DNS_PARAM_ERROR: (0xA8) ogiltigt DNS-ID.</span><span class="sxs-lookup"><span data-stu-id="328f4-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="328f4-369">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-370">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-371">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-371">Allowed From</span></span>

<span data-ttu-id="328f4-372">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-373">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-373">Example</span></span>

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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
```

```Output
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="328f4-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="328f4-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="328f4-375">Returnera storleken på DNS-klientens server lista</span><span class="sxs-lookup"><span data-stu-id="328f4-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-376">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="328f4-377">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-377">Description</span></span>

<span data-ttu-id="328f4-378">Den här tjänsten returnerar antalet giltiga DNS-servrar i klient listan.</span><span class="sxs-lookup"><span data-stu-id="328f4-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-379">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-379">Input Parameters</span></span>

- <span data-ttu-id="328f4-380">**dns_ptr**: pekar mot DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="328f4-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="328f4-381">**storlek**: returnerar antalet servrar i listan</span><span class="sxs-lookup"><span data-stu-id="328f4-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-382">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-382">Return Values</span></span>

- <span data-ttu-id="328f4-383">**NX_SUCCESS**: (0X00) DNS-serverns lista storlek har returnerats</span><span class="sxs-lookup"><span data-stu-id="328f4-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="328f4-384">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="328f4-385">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-386">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-386">Allowed From</span></span>

<span data-ttu-id="328f4-387">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-388">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="328f4-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="328f4-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="328f4-390">Returnera IP-adress och port för DNS-servern efter värdnamn</span><span class="sxs-lookup"><span data-stu-id="328f4-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-391">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-392">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-392">Description</span></span>

<span data-ttu-id="328f4-393">Den här tjänsten returnerar serverns IP-adress och port (tjänst post) baserat på det angivna värd namnet av DNS-frågan.</span><span class="sxs-lookup"><span data-stu-id="328f4-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="328f4-394">Om en tjänst post inte hittas returnerar den här rutinen en noll-IP-adress i indata-adress pekaren och en fel status som inte är noll returneras för att signalera ett fel.</span><span class="sxs-lookup"><span data-stu-id="328f4-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-395">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-395">Input Parameters</span></span>

- <span data-ttu-id="328f4-396">**dns_ptr**: pekar mot DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="328f4-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="328f4-397">**host_name**: pekare till värd namnets buffert</span><span class="sxs-lookup"><span data-stu-id="328f4-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="328f4-398">**host_address_ptr**: pekare till adress som ska returneras</span><span class="sxs-lookup"><span data-stu-id="328f4-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="328f4-399">**host_port_ptr**: pekare till port för att returnera wait_option vänte alternativ för DNS-svaret</span><span class="sxs-lookup"><span data-stu-id="328f4-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-400">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-400">Return Values</span></span>

- <span data-ttu-id="328f4-401">**NX_SUCCESS**: (0X00) DNS-Server posten har returnerats</span><span class="sxs-lookup"><span data-stu-id="328f4-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="328f4-402">**NX_DNS_NO_SERVER**: (0XA1) ingen DNS-server har registrerats med klienten för att skicka fråga på hostname</span><span class="sxs-lookup"><span data-stu-id="328f4-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="328f4-403">**NX_DNS_QUERY_FAILED**: (0XA3) DNS-fråga misslyckades; Inga svar från några DNS-servrar i klient listan eller ingen tjänst post är tillgängliga för det angivna värd namnet.</span><span class="sxs-lookup"><span data-stu-id="328f4-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="328f4-404">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-405">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-406">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-406">Allowed From</span></span>

<span data-ttu-id="328f4-407">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-408">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="328f4-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="328f4-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="328f4-410">Leta upp IPv4-adressen för det angivna värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-411">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-412">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-412">Description</span></span>

<span data-ttu-id="328f4-413">Den här tjänsten skickar en fråga av typen A med det angivna värd namnet för att hämta IP-adresserna för det angivna värd namnet.</span><span class="sxs-lookup"><span data-stu-id="328f4-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="328f4-414">DNS-klienten kopierar IPv4-adressen från en eller flera poster som returneras i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="328f4-415">*Record_buffer* måste vara 4 bytes justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="328f4-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="328f4-416">Flera IPv4-adresser lagras i den 4-byte-justerade bufferten som visas nedan:</span><span class="sxs-lookup"><span data-stu-id="328f4-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Diagram över multipla I P v 4-adresser som lagras i den justerade bufferten på 4 byte.](media/image6.png)

<span data-ttu-id="328f4-418">Om den angivna bufferten inte kan innehålla alla IP-Datadata, lagras inte de återstående posterna i *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="328f4-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="328f4-419">Detta gör att programmet kan hämta ett, några eller alla tillgängliga IP-Datadata i svaret från servern.</span><span class="sxs-lookup"><span data-stu-id="328f4-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="328f4-420">Med antalet returnerade poster i \**record_count* kan programmet parsa IPv4-adress data från *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="328f4-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-421">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-421">Input Parameters</span></span>

- <span data-ttu-id="328f4-422">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-423">**host_name_ptr**: pekar på värd namn för att hämta IPv4-adressens buffert pekare till platsen där du kan extrahera IPv4-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="328f4-424">**buffer_size**: storleken på bufferten för att lagra IPv4-data</span><span class="sxs-lookup"><span data-stu-id="328f4-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="328f4-425">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-426">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-426">Return Values</span></span>

- <span data-ttu-id="328f4-427">**NX_SUCCESS**: (0x00) hämtade IPv4-data</span><span class="sxs-lookup"><span data-stu-id="328f4-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="328f4-428">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-429">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-430">NX_DNS_PARAM_ERROR: (0xA8) ogiltig indataparameter.</span><span class="sxs-lookup"><span data-stu-id="328f4-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="328f4-431">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="328f4-432">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-433">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-433">Allowed From</span></span>

<span data-ttu-id="328f4-434">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-435">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-435">Example</span></span>

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
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
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="328f4-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="328f4-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="328f4-437">Leta upp ett värdnamn från en IP-adress</span><span class="sxs-lookup"><span data-stu-id="328f4-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-438">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-439">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-439">Description</span></span>

<span data-ttu-id="328f4-440">Den här tjänsten begär namn matchning av den angivna IP-adressen från en eller flera DNS-servrar som tidigare angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="328f4-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="328f4-441">Om det lyckas returneras det NULL-avslutade värd namnet i strängen som anges av *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="328f4-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-442">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-442">Input Parameters</span></span>

- <span data-ttu-id="328f4-443">**dns_ptr**: pekare till en tidigare skapad DNS-instans.</span><span class="sxs-lookup"><span data-stu-id="328f4-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="328f4-444">**ip_address**: IP-adress att matcha i ett namn</span><span class="sxs-lookup"><span data-stu-id="328f4-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="328f4-445">**host_name_ptr**: pekare till mål arean för värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="328f4-446">**max_host_name_size**: storleken på mål arean för värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="328f4-447">**wait_option**: definierar hur länge tjänsten väntar på timer-Tick för ett DNS-servernamn efter varje DNS-fråga och frågans försök att göra om vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="328f4-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="328f4-448">**timeout-värde**: (0X00000001-0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="328f4-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="328f4-449">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills en DNS-Server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="328f4-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-450">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-450">Return Values</span></span>

- <span data-ttu-id="328f4-451">**NX_SUCCESS**: (0X00) DNS-matchning har genomförts</span><span class="sxs-lookup"><span data-stu-id="328f4-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="328f4-452">**NX_DNS_TIMEOUT**: (0xA2) uppnådde tids gränsen vid hämtning av DNS-mutex</span><span class="sxs-lookup"><span data-stu-id="328f4-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="328f4-453">**NX_DNS_NO_SERVER**: (0XA1) ingen DNS-serveradress har angetts</span><span class="sxs-lookup"><span data-stu-id="328f4-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="328f4-454">**NX_DNS_QUERY_FAILED**: (0XA3) fick inget svar på frågan</span><span class="sxs-lookup"><span data-stu-id="328f4-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="328f4-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) null-indata adress</span><span class="sxs-lookup"><span data-stu-id="328f4-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="328f4-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0XB2) index pekar på ogiltig adress typ (t. ex. IPv6)</span><span class="sxs-lookup"><span data-stu-id="328f4-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="328f4-457">**NX_DNS_PARAM_ERROR**: (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="328f4-458">NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="328f4-459">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-460">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-460">Allowed From</span></span>

<span data-ttu-id="328f4-461">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-462">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="328f4-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="328f4-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="328f4-464">Leta upp en IP-adress från värd namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-465">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-466">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-466">Description</span></span>

<span data-ttu-id="328f4-467">Den här tjänsten begär namn matchning för det angivna namnet, som pekas efter *host_name*, från en eller flera DNS-servrar som tidigare angavs av programmet.</span><span class="sxs-lookup"><span data-stu-id="328f4-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="328f4-468">Om det lyckas returneras den associerade IP-adressen i målet som *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="328f4-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-469">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-469">Input Parameters</span></span>

- <span data-ttu-id="328f4-470">**dns_ptr**: pekare till en tidigare skapad DNS-instans.</span><span class="sxs-lookup"><span data-stu-id="328f4-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="328f4-471">**host_name**: pekare till värdnamn</span><span class="sxs-lookup"><span data-stu-id="328f4-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="328f4-472">**host_address_ptr**: pekar mot DNS-VÄRDEns IP-adress</span><span class="sxs-lookup"><span data-stu-id="328f4-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="328f4-473">**wait_option**: definierar hur länge tjänsten ska vänta på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="328f4-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="328f4-474">Vänte alternativen definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="328f4-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="328f4-475">**timeout-värde**: (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska pausas i väntan på DNS-matchningen.</span><span class="sxs-lookup"><span data-stu-id="328f4-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="328f4-476">**TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills en DNS-Server svarar på begäran.</span><span class="sxs-lookup"><span data-stu-id="328f4-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-477">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-477">Return Values</span></span>

- <span data-ttu-id="328f4-478">**NX_SUCCESS**: (0X00) DNS-matchning har genomförts.</span><span class="sxs-lookup"><span data-stu-id="328f4-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="328f4-479">**NX_DNS_NO_SERVER**: (0XA1) ingen DNS-serveradress har angetts</span><span class="sxs-lookup"><span data-stu-id="328f4-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="328f4-480">**NX_DNS_QUERY_FAILED**: (0XA3) fick inget svar på frågan</span><span class="sxs-lookup"><span data-stu-id="328f4-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="328f4-481">NX_DNS_PARAM_ERROR: (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="328f4-482">NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="328f4-483">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-484">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-484">Allowed From</span></span>

<span data-ttu-id="328f4-485">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-486">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-486">Example</span></span>
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="328f4-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="328f4-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="328f4-488">Leta upp text strängen för det angivna domän namnet</span><span class="sxs-lookup"><span data-stu-id="328f4-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-489">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="328f4-490">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-490">Description</span></span>

<span data-ttu-id="328f4-491">Den här tjänsten skickar en fråga av typen TXT med det angivna domän namnet och bufferten för att hämta godtyckliga sträng data.</span><span class="sxs-lookup"><span data-stu-id="328f4-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="328f4-492">DNS-klienten kopierar text strängen i TXT-posten i DNS-serverns svar till *record_buffer* minnes plats.</span><span class="sxs-lookup"><span data-stu-id="328f4-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="328f4-493">*Record_buffer* behöver inte vara 4 byte-justerad för att ta emot data.</span><span class="sxs-lookup"><span data-stu-id="328f4-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-494">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-494">Input Parameters</span></span>

- <span data-ttu-id="328f4-495">**dns_ptr**: pekar mot DNS-klient.</span><span class="sxs-lookup"><span data-stu-id="328f4-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="328f4-496">**host_name**: pekare till namnet på värden att söka på</span><span class="sxs-lookup"><span data-stu-id="328f4-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="328f4-497">**record_buffer**: pekare till plats att extrahera txt-data till</span><span class="sxs-lookup"><span data-stu-id="328f4-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="328f4-498">**buffer_size**: storleken på bufferten som ska innehålla txt-data</span><span class="sxs-lookup"><span data-stu-id="328f4-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="328f4-499">**wait_option**: vänte alternativ för att ta emot DNS-serverns svar</span><span class="sxs-lookup"><span data-stu-id="328f4-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-500">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-500">Return Values</span></span>

- <span data-ttu-id="328f4-501">**NX_SUCCESS**: (0x00) en returnerad txt-sträng</span><span class="sxs-lookup"><span data-stu-id="328f4-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="328f4-502">**NX_DNS_NO_SERVER**: (0XA1) klient server listan är tom</span><span class="sxs-lookup"><span data-stu-id="328f4-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="328f4-503">**NX_DNS_QUERY_FAILED**: (0XA3) inget giltigt DNS-svar togs emot</span><span class="sxs-lookup"><span data-stu-id="328f4-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="328f4-504">NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="328f4-505">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="328f4-506">NX_DNS_PARAM_ERROR: (0xA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-507">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-507">Allowed From</span></span>

<span data-ttu-id="328f4-508">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-509">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-509">Example</span></span>

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="328f4-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="328f4-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="328f4-511">Ange pool för DNS-klient</span><span class="sxs-lookup"><span data-stu-id="328f4-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-512">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="328f4-513">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-513">Description</span></span>

<span data-ttu-id="328f4-514">Den här tjänsten anger en tidigare skapad modempool som DNS- **klientens** adresspool.</span><span class="sxs-lookup"><span data-stu-id="328f4-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="328f4-515">DNS-klienten kommer att använda den här poolen för att skicka DNS-frågor, så paketets nytto Last bör inte vara mindre än NX_DNS_PACKET_PAYLOAD_UNALIGNED som innehåller Ethernet-fönstret, IP-och UDP-huvuden och definieras i *nx_dns. h*.</span><span class="sxs-lookup"><span data-stu-id="328f4-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="328f4-516">När DNS-klienten tas bort tas inte poolen bort med den och det är programmets ansvar att ta bort modempoolen när den inte längre behöver den.</span><span class="sxs-lookup"><span data-stu-id="328f4-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="328f4-517">Den här tjänsten är bara tillgänglig om konfigurations alternativet NX_DNS_CLIENT_USER_CREATE_PACKET_POOL definierats i *nx_dns. h*</span><span class="sxs-lookup"><span data-stu-id="328f4-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-518">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-518">Input Parameters</span></span>

- <span data-ttu-id="328f4-519">**dns_ptr**: pekar mot en tidigare skapad DNS- **klient** instans.</span><span class="sxs-lookup"><span data-stu-id="328f4-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="328f4-520">**pool_ptr**: pekare till tidigare skapade paketets pool</span><span class="sxs-lookup"><span data-stu-id="328f4-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-521">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-521">Return Values</span></span>

- <span data-ttu-id="328f4-522">**NX_SUCCESS**: (0X00) slutfördes.</span><span class="sxs-lookup"><span data-stu-id="328f4-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="328f4-523">**NX_NOT_ENABLED**: (0X14) klienten är inte konfigurerad för det här alternativet</span><span class="sxs-lookup"><span data-stu-id="328f4-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="328f4-524">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS- **klient** pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="328f4-525">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.</span><span class="sxs-lookup"><span data-stu-id="328f4-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-526">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-526">Allowed From</span></span>

<span data-ttu-id="328f4-527">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-528">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-528">Example</span></span>
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a><span data-ttu-id="328f4-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="328f4-529">nx_dns_server_add</span></span>

<span data-ttu-id="328f4-530">Lägg till DNS-serverns IP-adress</span><span class="sxs-lookup"><span data-stu-id="328f4-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-531">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="328f4-532">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-532">Description</span></span>

<span data-ttu-id="328f4-533">Den här tjänsten lägger till en IPv4 DNS-server i Server listan.</span><span class="sxs-lookup"><span data-stu-id="328f4-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-534">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-534">Input Parameters</span></span>

- <span data-ttu-id="328f4-535">**dns_ptr**: pekar mot DNS-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="328f4-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="328f4-536">**server_address**: IP-adress för DNS-Server</span><span class="sxs-lookup"><span data-stu-id="328f4-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-537">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-537">Return Values</span></span>

- <span data-ttu-id="328f4-538">**NX_SUCCESS**: (0X00) servern har lagts till</span><span class="sxs-lookup"><span data-stu-id="328f4-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="328f4-539">**NX_DNS_DUPLICATE_ENTRY** eller **NX_NO_MORE_ENTRIES**: (0X17) inga fler DNS-servrar tillåts (listan är full)</span><span class="sxs-lookup"><span data-stu-id="328f4-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="328f4-540">**NX_DNS_PARAM_ERROR**: (0XA8) ogiltig inmatad icke-pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="328f4-541">NX_PTR_ERROR: (0x07) ogiltigt inmatade pekare</span><span class="sxs-lookup"><span data-stu-id="328f4-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="328f4-542">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="328f4-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) null-indata för server adress</span><span class="sxs-lookup"><span data-stu-id="328f4-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-544">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-544">Allowed From</span></span>

<span data-ttu-id="328f4-545">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-546">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="328f4-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="328f4-547">nx_dns_server_get</span></span>

<span data-ttu-id="328f4-548">Returnera en IPv4 DNS-server från klient listan</span><span class="sxs-lookup"><span data-stu-id="328f4-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-549">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="328f4-550">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-550">Description</span></span>

<span data-ttu-id="328f4-551">Den här tjänsten returnerar IPv4 DNS-serveradressen från server listan vid det angivna indexet.</span><span class="sxs-lookup"><span data-stu-id="328f4-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="328f4-552">Observera att indexet är noll baserat.</span><span class="sxs-lookup"><span data-stu-id="328f4-552">Note that the index is zero based.</span></span> <span data-ttu-id="328f4-553">Om inindexet överskrider storleken på listan över DNS-klienter returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="328f4-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="328f4-554">Den *nx_dns_get_serverlist_size* tjänsten kan anropas först hämta antalet DNS-servrar i klient listan.</span><span class="sxs-lookup"><span data-stu-id="328f4-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-555">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-555">Input Parameters</span></span>

- <span data-ttu-id="328f4-556">**dns_ptr**: pekar mot DNS-kontroll-block</span><span class="sxs-lookup"><span data-stu-id="328f4-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="328f4-557">**index**: index i DNS-klientens lista över servrar</span><span class="sxs-lookup"><span data-stu-id="328f4-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="328f4-558">**dns_server_address**: pekare till IP-adressen för DNS-servern</span><span class="sxs-lookup"><span data-stu-id="328f4-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-559">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-559">Return Values</span></span>

- <span data-ttu-id="328f4-560">**NX_SUCCESS**: (0X00) lyckad Server returnerades</span><span class="sxs-lookup"><span data-stu-id="328f4-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="328f4-561">**NX_DNS_SERVER_NOT_FOUND**: (0XA9) index pekar på tom plats</span><span class="sxs-lookup"><span data-stu-id="328f4-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="328f4-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) index pekar på null-adress</span><span class="sxs-lookup"><span data-stu-id="328f4-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="328f4-563">**NX_DNS_PARAM_ERROR**: (0XA8) indexet överskrider storleken på listan</span><span class="sxs-lookup"><span data-stu-id="328f4-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="328f4-564">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="328f4-565">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-566">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-566">Allowed From</span></span>

<span data-ttu-id="328f4-567">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-568">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="328f4-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="328f4-569">nx_dns_server_remove</span></span>

<span data-ttu-id="328f4-570">Ta bort en IPv4 DNS-server från klient listan</span><span class="sxs-lookup"><span data-stu-id="328f4-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-571">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="328f4-572">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-572">Description</span></span>

<span data-ttu-id="328f4-573">Den här tjänsten tar bort en IPv4 DNS-server från klient listan.</span><span class="sxs-lookup"><span data-stu-id="328f4-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-574">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-574">Input Parameters</span></span>

- <span data-ttu-id="328f4-575">**dns_ptr**: pekar mot DNS-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="328f4-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="328f4-576">**server_address**: IP-adressen för DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="328f4-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-577">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-577">Return Values</span></span>

- <span data-ttu-id="328f4-578">**NX_SUCCESS**: (0X00) DNS-servern har tagits bort</span><span class="sxs-lookup"><span data-stu-id="328f4-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="328f4-579">**NX_DNS_SERVER_NOT_FOUND**: (0XA9) Server inte i klient listan</span><span class="sxs-lookup"><span data-stu-id="328f4-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="328f4-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0XA4) null-indata för server adress</span><span class="sxs-lookup"><span data-stu-id="328f4-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="328f4-581">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="328f4-582">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-583">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-583">Allowed From</span></span>

<span data-ttu-id="328f4-584">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-585">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="328f4-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="328f4-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="328f4-587">Ta bort alla DNS-servrar från klient listan</span><span class="sxs-lookup"><span data-stu-id="328f4-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="328f4-588">Prototyp</span><span class="sxs-lookup"><span data-stu-id="328f4-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="328f4-589">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="328f4-589">Description</span></span>

<span data-ttu-id="328f4-590">Den här tjänsten tar bort alla DNS-servrar från klient listan.</span><span class="sxs-lookup"><span data-stu-id="328f4-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="328f4-591">Indataparametrar</span><span class="sxs-lookup"><span data-stu-id="328f4-591">Input Parameters</span></span>

- <span data-ttu-id="328f4-592">**dns_ptr**: pekar mot DNS-kontroll-block.</span><span class="sxs-lookup"><span data-stu-id="328f4-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="328f4-593">Retur värden</span><span class="sxs-lookup"><span data-stu-id="328f4-593">Return Values</span></span>

- <span data-ttu-id="328f4-594">**NX_SUCCESS**: (0X00) DNS-servrar har tagits bort</span><span class="sxs-lookup"><span data-stu-id="328f4-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="328f4-595">**NX_DNS_ERROR**: (0XA0) Det gick inte att hämta skydds-mutex</span><span class="sxs-lookup"><span data-stu-id="328f4-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="328f4-596">NX_PTR_ERROR: (0x07) ogiltig IP-eller DNS-pekare.</span><span class="sxs-lookup"><span data-stu-id="328f4-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="328f4-597">NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten</span><span class="sxs-lookup"><span data-stu-id="328f4-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="328f4-598">Tillåten från</span><span class="sxs-lookup"><span data-stu-id="328f4-598">Allowed From</span></span>

<span data-ttu-id="328f4-599">Konversation</span><span class="sxs-lookup"><span data-stu-id="328f4-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="328f4-600">Exempel</span><span class="sxs-lookup"><span data-stu-id="328f4-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```