---
title: Kapitel 1 – Introduktion till DNS-klienten för Azure återställnings tider NetX Duo
description: DNS tillhandahåller en distribuerad databas som innehåller mappning mellan domän namn och fysiska IP-adresser.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4c07d6e3183d421c637874dcdeff3767554fca78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826025"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dns-client"></a>Kapitel 1 – Introduktion till DNS-klienten för Azure återställnings tider NetX Duo

DNS tillhandahåller en distribuerad databas som innehåller mappning mellan domän namn och fysiska IP-adresser. Databasen kallas *distribuerad* eftersom det inte finns någon enskild entitet på Internet som innehåller den fullständiga mappningen. En entitet som underhåller en del av mappningen kallas för en DNS-server. Internet består av flera DNS-servrar, som var och en innehåller en delmängd av databasen. DNS-servrar svarar också på DNS-klientcertifikat för mappnings information för domän namn, endast om servern har den begärda mappningen.

DNS-klientens protokoll för NetX Duo tillhandahåller programmet med tjänster för att begära mappnings information från en eller flera DNS-servrar.

## <a name="dns-client-setup"></a>DNS-klient installation

För att kunna fungera korrekt kräver DNS-klientprogrammet att en NetX Duo-instans redan har skapats.

När du har skapat DNS-klienten måste programmet lägga till en eller flera DNS-servrar i Server listan som underhålls av DNS-klienten. Om du vill lägga till DNS-servrar använder programmet tjänsten *nxd_dns_server_add* . NetX Duo DNS-klienttjänsten *nx_dns_server_add* kan också användas för att lägga till servrar. Det accepterar dock bara IPv4-adresser och vi rekommenderar att utvecklarna använder tjänsten *nxd_dns_server_add* i stället.

Om alternativet NX_DNS_IP_GATEWAY_SERVER är aktiverat och gateway-adressen för IP-instansen inte är noll läggs gatewayen för IP-instansen automatiskt till som den primära DNS-servern. Om DNS-serverns information inte är statiskt känd kan den också härledas via Dynamic Host Configuration Protocol (DHCP) för NetX Duo. Mer information finns i användar handboken för NetX Duo DHCP.

DNS-klienten kräver en modempool för överföring av DNS-meddelanden. Som standard skapar DNS-klienten den här poolen när tjänsten *nx_dns_create* anropas. Konfigurations alternativen NX_DNS_PACKET_PAYLOAD_UNALIGNED och NX_DNS_PACKET_POOL_SIZE tillåter att programmet fastställer paketets nytto last och paketets pool storlek (t. ex. antalet paket) för den här poolen. De här alternativen beskrivs i avsnittet "konfigurations alternativ" i kapitel två.

Ett alternativ till DNS-klienten som skapar en egen modempool är för att programmet ska skapa poolen och ange den som DNS-klientens modempool med hjälp av tjänsten *nx_dns_packet_pool_set* . För att göra det måste NX_DNS_CLIENT_USER_CREATE_PACKET_POOL alternativet definieras. Det här alternativet kräver också en tidigare skapad modempool som använder *nx_packet_pool_create* som paketets pool pekare in på *nx_dns_packet_pool_set* . När DNS-klienttjänsten tas bort ansvarar programmet för att ta bort poolen för DNS-klienter om NX_DNS_CLIENT_USER_CREATE_PACKET_POOL är aktive rad om den inte längre behövs.

> [!NOTE] 
> För program som väljer att tillhandahålla en egen modempool med hjälp av alternativet NX_DNS_CLIENT_USER_CREATE_PACKET_POOL måste paket storleken kunna innehålla den maximala storleken för DNS-massage (512 byte) plus rum för UDP-huvud, IPv4-eller IPv6-huvud och MAC-huvudet.

## <a name="dns-messages"></a>DNS-meddelanden

DNS har en mycket enkel mekanism för att hämta mappning mellan värdnamn och IP-adresser. För att hämta en mappning förbereder DNS-klienten ett DNS-frågemeddelanden som innehåller namnet eller IP-adressen som måste matchas. Meddelandet skickas sedan till den första DNS-servern i Server listan. Om servern har en sådan mappning svarar den på DNS-klienten med ett DNS-svarsmeddelande som innehåller den begärda mappnings informationen. Om servern inte svarar frågar DNS-klienten nästa server i listan tills alla DNS-servrar har frågats. Om inget svar från alla DNS-servrar tas emot har DNS-klienten återförsök för att överföra DNS-meddelandet igen. Vid återsändning av en DNS-fråga dubbleras tids gränsen för återöverföring. Den här processen fortsätter tills Max gränsen för överföring (definieras som NX_DNS_MAX_RETRANS_TIMEOUT i *nxd_dns. h*) har nåtts eller tills ett lyckat svar tas emot från servern.

NetX Duo DNS-klienten kan utföra både IPv6-adresss ökningar (typ AAAA) och IPv4-adresss ökningar (Skriv A) genom att ange versionen för IP-adressen i *nxd_dns_host_by_name_get* -anropet. DNS-klienten kan utföra omvänd sökning av IP-adresser (Skriv PTR-frågor) för att hämta webb värd namn med hjälp av *nxd_dns_host_by_address_get*. NetX Duo DNS-klienten stöder fortfarande *nx_dns_host_by_name_get* och *nx_dns_host_by_address_get* som är motsvarande tjänster, men som är begränsade till IPv4-nätverkskommunikation. Utvecklare uppmanas dock att Porta befintliga DNS-klientprogram till *nxd_dns_host_by_name_get* -och *nxd_dns_host_by_address_get* -tjänsterna.

DNS-meddelanden använder UDP-protokollet för att skicka begär Anden och fält svar. En DNS-Server lyssnar på port nummer 53 för frågor från klienter. Därför måste UDP-tjänsterna vara aktiverade i NetX Duo med ***nx_udp_enable** _-tjänsten på en tidigare skapad IP-instans (_ *_nx_ip_create_* *).

I det här läget är DNS-klienten redo att ta emot begär Anden från programmet och skicka DNS-frågor.

## <a name="extended-dns-resource-record-types"></a>Utökade DNS-resurs post typer

Om NX_DNS_ENABLE_EXTENDED_RR_TYPES är aktive rad stöder NetX Duo DNS-klienten även följande frågor för post typer:

- CNAME: innehåller det kanoniska namnet för ett alias
- TXT: innehåller en text sträng
- NS: innehåller en auktoritativ namnserver
- SOA: innehåller start för en zon för auktoritet
- MX: används för e-postutbyte
- SRV: innehåller information om den tjänst som erbjuds av domänen

Med undantag för CNAME-och TXT-posttyper måste programmet tillhandahålla en 4-byte-justerad buffert för att ta emot DNS-dataposten.

I NetX Duo DNS-klient lagras post data på ett sådant sätt för att effektivt utnyttja buffertutrymme.

Ett exempel på en post buffert med fast längd (typ AAAA-post) visas nedan:

![Registrera bufferten med fast längd](media/image2.png)

För de frågor vars post typer har variabel data längd, till exempel NS-poster vars värdnamn är varierande längd, sparar NetX Duo DNS-klienten data på följande sätt. Bufferten som anges i DNS-klientens fråga är ordnad i ett området med fasta längd data och ett del av ostrukturerat minne. Den övre delen av minnesbufferten är indelad i 4 bytes justerade post poster. Varje post post innehåller IP-adressen och en pekare till data för variabel längd för den IP-adressen. Variabla längd data för varje IP-adress lagras i det ostrukturerade områdets minne som börjar i slutet av minnesbufferten. Variabla längd data för varje post i följd sparas i nästa områdes minne intill variabel data för föregående post poster. Därmed växer variabeln data mot det strukturerade minnes området som innehåller post posterna tills det inte finns tillräckligt med minne för att lagra ytterligare post-och variabel data.

Detta visas i bilden nedan:

![Bild 2](media/image3.png)

Exemplet på DNS-datalagringen (NS) för DNS-domännamn visas ovan.

NetX Duo DNS-klientfrågor med post Storage-formatet returnerar antalet poster som sparats till postbufferten. Med den här informationen kan programmet extrahera NS-poster från bufferten för poster.

Ett exempel på en DNS-klient fråga som lagrar DNS-data för variabel längd med det här post lagrings formatet visas nedan:

```C
UINT  _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, 
                    UCHAR *host_name, VOID *record_buffer, 
                    UINT buffer_size, UINT *record_count, 
                    ULONG wait_option);
```


Mer information finns i kapitel 3, "Beskrivning av DNS-klienttjänster".

## <a name="dns-cache"></a>DNS-cache

Om NX_DNS_CACHE_ENABLE är aktive rad stöder NetX Duo DNS-klienten funktionen DNS-cache. När du har skapat DNS-klienten kan programmet anropa API *-nx_dns_cache_initialize ()* för att ange det särskilda DNS-cacheminnet. Om Aktivera DNS-cache-funktion hittar DNS-klienten det tillgängliga svaret från DNS-cachen innan den börjar skicka DNS-fråga, om du hittar det tillgängliga svaret, returnerar svaret till programmet, annars skickas ett meddelande till DNS-servern i DNS-klienten och väntar på svar. När DNS-klienten hämtar svarsmeddelandet och det finns ledigt cache tillgängligt, returnerar DNS-klienten svaret till programmet och lägger även till svaret som resurs post i DNS-cachen.

Varje svar är en data struktur *NX_DNS_RR* (resurs post) i cacheminnet. Strängar (resurs post namn och data) i poster är variabel längd och lagras därför inte i NX_DNS_RRs strukturen. Posten innehåller pekare till den faktiska minnes platsen där strängarna lagras. Sträng tabellen och posterna delar cacheminnet. Poster lagras från cachens början och växer mot slutet av cacheminnet. Sträng tabellen börjar från slutet av cacheminnet och växer till början av cachen. Varje sträng i sträng tabellen har fältet längd och ett räknar fält. När en sträng läggs till i sträng tabellen, och om samma sträng redan finns i tabellen, ökar räknarvärdet och inget minne allokeras för strängen. Cachen anses vara full om inga fler resurs poster eller nya strängar kan läggas till i cachen.

## <a name="dns-client-limitations"></a>Begränsningar för DNS-klient

DNS-klienten har stöd för en DNS-begäran åt gången. Trådar som försöker göra en annan DNS-begäran blockeras tillfälligt tills den tidigare DNS-begäran har slutförts.

NetX Duo DNS-klienten använder inte data från auktoritativa svar för att vidarebefordra ytterligare DNS-frågor till andra DNS-servrar.

## <a name="dns-rfcs"></a>DNS-RFC

NetX Duo DNS är kompatibelt med följande RFC: er:

- RFC1034 DOMÄN NAMN – KONCEPT OCH ANLÄGGNINGAR
- RFC1035 DOMÄN NAMN – IMPLEMENTERING OCH SPECIFIKATION
- RFC1480 USA-domänen
- RFC 2782 A DNS RR för att ange plats för tjänster (DNS SRV)
- RFC 3596 DNS-tillägg som stöder IP version 6