---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo DNS-klient
description: DNS tillhandahåller en distribuerad databas som innehåller mappning mellan domännamn och fysiska IP-adresser.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e878d32d6bcf514bb75a76b51e66c4d267b1a5b34f6c4b2df6ab231e5814ffc5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792066"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dns-client"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo DNS-klient

DNS tillhandahåller en distribuerad databas som innehåller mappning mellan domännamn och fysiska IP-adresser. Databasen kallas distribuerad eftersom *det inte* finns någon enskild entitet på Internet som innehåller den fullständiga mappningen. En entitet som underhåller en del av mappningen kallas för en DNS-server. Internet består av flera DNS-servrar som var och en innehåller en delmängd av databasen. DNS-servrar svarar också på DNS-klientbegäranden om domännamnsmappningsinformation, endast om servern har den begärda mappningen.

DNS-klientprotokollet för NetX Duo ger programmet tjänster för att begära mappningsinformation från en eller flera DNS-servrar.

## <a name="dns-client-setup"></a>Konfiguration av DNS-klient

För att fungera korrekt kräver DNS-klientpaketet att en NetX Duo IP-instans redan har skapats.

När du har skapat DNS-klienten måste programmet lägga till en eller flera DNS-servrar i serverlistan som underhålls av DNS-klienten. För att lägga till DNS-servrar använder programmet *nxd_dns_server_add tjänsten.* NetX Duo DNS-klienttjänsttjänsten *nx_dns_server_add* också användas för att lägga till servrar. Men den accepterar bara IPv4-adresser och vi rekommenderar att utvecklare använder *nxd_dns_server_add tjänsten* i stället.

Om alternativet NX_DNS_IP_GATEWAY_SERVER aktiverat och IP-instansens gatewayadress inte är noll läggs IP-instansgatewayen automatiskt till som den primära DNS-servern. Om DNS-serverinformationen inte är statiskt känd kan den också härleds via Dynamic Host Configuration Protocol (DHCP) för NetX Duo. Mer information finns i användarhandboken för NetX Duo DHCP.

DNS-klienten kräver en paketpool för överföring av DNS-meddelanden. Som standard skapar DNS-klienten den här paketpoolen *när nx_dns_create tjänsten* anropas. Konfigurationsalternativen NX_DNS_PACKET_PAYLOAD_UNALIGNED och NX_DNS_PACKET_POOL_SIZE att programmet kan fastställa paketnyttolasten och paketpoolens storlek (t.ex. antalet paket) för den här paketpoolen. Dessa alternativ beskrivs i avsnittet "Konfigurationsalternativ" i kapitel två.

Ett alternativ till att DNS-klienten skapar en egen paketpool är att programmet skapar paketpoolen och anger den som DNS-klientens paketpool med *hjälp av nx_dns_packet_pool_set tjänsten.* För att göra det måste NX_DNS_CLIENT_USER_CREATE_PACKET_POOL här alternativet definieras. Det här alternativet kräver också en tidigare skapad paketpool *med nx_packet_pool_create* som indata från paketpoolens pekare *till nx_dns_packet_pool_set* . När DNS-klientinstansen tas bort ansvarar programmet för att ta bort DNS-klientens paketpool om NX_DNS_CLIENT_USER_CREATE_PACKET_POOL är aktiverad om den inte längre behövs.

> [!NOTE] 
> För program som väljer att tillhandahålla en egen paketpool med hjälp av NX_DNS_CLIENT_USER_CREATE_PACKET_POOL-alternativet måste paketstorleken kunna innehålla DNS-maximal storlek (512 byte) plus rum för UDP-huvud, IPv4- eller IPv6-huvud och MAC-huvudet.

## <a name="dns-messages"></a>DNS-meddelanden

DNS har en mycket enkel metod för att hämta mappning mellan värdnamn och IP-adresser. För att hämta en mappning förbereder DNS-klienten ett DNS-frågemeddelande som innehåller det namn eller den IP-adress som måste matchas. Meddelandet skickas sedan till den första DNS-servern i serverlistan. Om servern har en sådan mappning svarar den DNS-klienten med hjälp av ett DNS-svarsmeddelande som innehåller den begärda mappningsinformationen. Om servern inte svarar frågar DNS-klienten nästa server i listan tills alla dess DNS-servrar har frågats. Om inget svar från alla dess DNS-servrar tas emot, har DNS-klienten logik för omförsök för att skicka DNS-meddelandet igen. Vid återsändning av en DNS-fråga fördubblas tidsgränsen för återöverföring. Den här processen fortsätter tills den maximala tidsgränsen för överföring (definieras som *NX_DNS_MAX_RETRANS_TIMEOUT i nxd_dns.h*) har nåtts eller tills ett lyckat svar tas emot från den servern.

NetX Duo DNS-klienten kan utföra både IPv6-adressuppslag (typ AAAA) och IPv4-adressuppslag (typ  A) genom att ange versionen av IP-adressen i nxd_dns_host_by_name_get-anropet. DNS-klienten kan utföra omvända sökningar av IP-adresser (typ PTR-frågor) för att hämta webbvärdnamn med *hjälp av nxd_dns_host_by_address_get*. NetX Duo DNS-klienten stöder *fortfarande nx_dns_host_by_name_get* och *nx_dns_host_by_address_get* som är motsvarande tjänster men som är begränsade till IPv4-nätverkskommunikation. Utvecklare uppmanas dock att porta befintliga DNS-klientprogram till *nxd_dns_host_by_name_get* och *nxd_dns_host_by_address_get* tjänster.

DNS-meddelanden använder UDP-protokollet för att skicka begäranden och fältsvar. En DNS-server lyssnar på portnummer 53 efter frågor från klienter. Därför måste UDP-tjänster aktiveras i NetX Duo med hjälp av tjänsten ***nx_udp_enable** _ på en tidigare skapad IP-instans (_*_nx_ip_create_**).

I det här läget är DNS-klienten redo att acceptera begäranden från programmet och skicka ut DNS-frågor.

## <a name="extended-dns-resource-record-types"></a>Utökade DNS-resursposttyper

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES har aktiverats stöder NetX Duo DNS-klienten även följande posttypsfrågor:

- CNAME: innehåller det kanoniska namnet för ett alias
- TXT: innehåller en textsträng
- NS: innehåller en auktoritativ namnserver
- SOA: innehåller början av en auktoritetszon
- MX: används för e-postutbyte
- SRV: innehåller information om den tjänst som erbjuds av domänen

Med undantag för posttyperna CNAME och TXT måste programmet ange en 4 byte-justerad buffert för att ta emot DNS-dataposten.

I NetX Duo DNS-klienten lagras postdata på ett sådant sätt att du kan använda buffertutrymmet på bästa sätt.

Ett exempel på en postbuffert med fast längd (typen AAAA-post) visas nedan:

![Postbuffert med fast längd](media/image2.png)

För de frågor vars posttyper har variabel datalängd, till exempel NS-poster vars värdnamn har variabel längd, sparar NetX Duo DNS-klienten data på följande sätt. Bufferten som anges i DNS-klientfrågan är ordnad i ett område med data med fast längd och ett område med ostrukturerat minne. Överst i minnesbufferten är indelade i postposter som är justerade med 4 byte. Varje postpost innehåller IP-adressen och en pekare till variabellängdsdata för den IP-adressen. Variabellängdsdata för varje IP-adress lagras i det ostrukturerade områdets minne med början i slutet av minnesbufferten. Variabellängdsdata för varje efterföljande postpost sparas i nästa områdesminne bredvid tidigare poster för variabeldata. Därför "växer" variabeldata mot det strukturerade området i minnet som innehåller postposterna tills det inte finns tillräckligt med minne för att lagra en annan postpost och variabeldata.

Detta visas i bilden nedan:

![Bild 2](media/image3.png)

Exemplet på datalagring för DNS-domännamn (NS) visas ovan.

NetX Duo DNS-klientfrågor med postlagringsformatet returnerar antalet poster som sparats i postbufferten. Den här informationen gör att programmet kan extrahera NS-poster från postbufferten.

Ett exempel på en DNS-klientfråga som lagrar DNS-data med variabel längd med det här postlagringsformatet visas nedan:

```C
UINT  _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, 
                    UCHAR *host_name, VOID *record_buffer, 
                    UINT buffer_size, UINT *record_count, 
                    ULONG wait_option);
```


Mer information finns i kapitel 3, "Beskrivning av DNS-klienttjänster".

## <a name="dns-cache"></a>DNS-cache

Om NX_DNS_CACHE_ENABLE är aktiverat stöder NetX Duo DNS-klienten DNS Cache-funktionen. När du har skapat DNS-klienten kan programmet anropa *API:et nx_dns_cache_initialize() för* att ange den särskilda DNS-cachen. Om du aktiverar funktionen DNS Cache hittar DNS-klienten det tillgängliga svaret från DNS Cache innan börjar skicka DNS-fråga. Om du hittar det tillgängliga svaret returnerar den svaret direkt till programmet. Annars skickar DNS-klienten frågemeddelandet till DNS-servern och väntar på svaret. När DNS-klienten får svarsmeddelandet och det finns ledigt cacheminne tillgängligt returnerar DNS-klienten svaret till programmet och lägger även till svaret som resurspost i DNS-cachen.

Varje svarar på en *datastruktur NX_DNS_RR* (Resurspost) i cacheminnet. Strängar (resurspostnamn och data) i Poster är variabel längd och lagras därför inte i NX_DNS_RR struktur. Posten innehåller pekare till den faktiska minnesplatsen där strängarna lagras. Strängtabellen och posterna delar cachen. Poster lagras från början av cachen och växer mot slutet av cachen. Strängtabellen startar från slutet av cachen och växer mot början av cachen. Varje sträng i strängtabellen har ett längdfält och ett räknarfält. Om samma sträng redan finns i tabellen när en sträng läggs till i strängtabellen ökas räknarvärdet och inget minne allokeras för strängen. Cachen anses vara full om inga fler resursposter eller nya strängar kan läggas till i cacheminnet.

## <a name="dns-client-limitations"></a>Begränsningar för DNS-klienter

DNS-klienten stöder en DNS-begäran i taget. Trådar som försöker göra en annan DNS-begäran blockeras tillfälligt tills den tidigare DNS-begäran har slutförts.

NetX Duo DNS-klienten använder inte data från auktoritativa svar för att vidarebefordra ytterligare DNS-frågor till andra DNS-servrar.

## <a name="dns-rfcs"></a>DNS-RFC:er

NetX Duo DNS är kompatibelt med följande RFC:er:

- RFC1034-DOMÄNNAMN – BEGREPP OCH ANLÄGGNINGAR
- RFC1035-DOMÄNNAMN – IMPLEMENTERING OCH SPECIFIKATION
- RFC1480– domänen USA
- RFC 2782 En DNS-RR för att ange platsen för tjänster (DNS SRV)
- RFC 3596 DNS-tillägg som stöder IP-version 6