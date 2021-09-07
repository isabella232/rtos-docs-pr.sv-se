---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo
description: Det här kapitlet innehåller en introduktion till Azure RTOS NetX Duo och en beskrivning av dess program och fördelar.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f45d32afcc2edbd5b851f1b7fb03e7fa2430ebc
ms.sourcegitcommit: 20a136b06a25e31bbde718b4d12a03ddd8db9051
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/07/2021
ms.locfileid: "123552372"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo

Azure RTOS NetX Duo är en högpresterande realtidsimplementering av TCP/IP-standarderna som utformats exklusivt för inbäddade Azure RTOS ThreadX-baserade program. Det här kapitlet innehåller en introduktion till NetX Duo och en beskrivning av dess program och fördelar. 

## <a name="netx-duo-unique-features"></a>Unika funktioner i NetX Duo

Till skillnad från andra TCP/IP-implementeringar är NetX Duo utformat för att vara flexibelt – enkelt att skala från små mikrostyrenhetsbaserade program till de som använder kraftfulla RISC- och DSP-processorer. Detta står i stark kontrast till den offentliga domänen eller andra kommersiella implementeringar som ursprungligen var avsedda för arbetsstationsmiljöer men som sedan samlades ihop till inbäddade designer.

### <a name="piconettrade-architecture"></a>Piconet-arkitektur &trade;

Bakom den överordnade skalbarheten och prestandan i NetX Duo finns <em>Piconet</em>, en programvaruarkitektur som är särskilt utformad för inbäddade system. Piconet-arkitekturen maximerar skalbarheten genom att implementera NetX Duo-tjänster som ett C-bibliotek. På så sätt tas endast de tjänster som används av programmet in i den slutliga körningsavbildningen. Den faktiska storleken på NetX Duo bestäms därför av programmet. För de flesta program varierar instruktionsavbildningskraven för NetX Duo mellan 5 KByte och 30 KByte i storlek. Med IPv6 och ICMPv6 aktiverat för IPv6-adresskonfiguration och grannidentifieringsprotokoll, sträcker sig NetX Duo i storlek från 30 kbyte till 45 kbyte.

NetX Duo uppnår överlägsen nätverksprestanda genom att skikta interna komponentfunktionsanrop endast när det är nödvändigt. Dessutom görs mycket av NetX Duo-bearbetningen direkt i rad, vilket ger utmärkta prestandafördelar jämfört med nätverksprogramvaran för arbetsstationer som använts i inbäddade designer tidigare.

### <a name="zero-copy-implementation"></a>Nollkopieringsimplementering

NetX Duo tillhandahåller en paketbaserad, nollkopieringsimplementering av TCP/IP. Nollkopiering innebär att data i programmets paketbuffert aldrig kopieras i NetX Duo. Detta förbättrar prestanda avsevärt och frigör värdefulla processorcykler för programmet, vilket är viktigt i inbäddade program.

### <a name="udp-fast-pathtrade-technology"></a>UDP-teknik för snabb &trade; sökväg

Med <em>UDP Fast Path Technology</em>ger NetX Duo snabbaste möjliga UDP-bearbetning. På sändningssidan finns UDP-bearbetning , inklusive den valfria <em></em> UDP-kontrollsumman, i nx_udp_socket_send tjänsten. Inga ytterligare funktionsanrop görs förrän paketet är redo att skickas via den interna NETX Duo IP-sändrutinen. Den här rutinen är också plan (det vill säga att funktionsanropens kapsling är minimal) så att paketet snabbt skickas till programmets nätverksdrivrutin. När UDP-paketet tas emot placerar NetX Duo-paket-receivebearbetningen paketet direkt på lämplig UDP-sockets mottagningskö eller ger det till den första tråden som pausas i väntan på ett mottagningspaket från UDP-socketens mottagningskö. Inga ytterligare ThreadX-kontextväxlar krävs.

### <a name="ansi-c-source-code"></a>ANSI C-källkod

NetX Duo är helt skrivet i ANSI C och portabel direkt till praktiskt taget alla processorarkitekturer som har anSI C-kompilator och ThreadX-stöd. 

### <a name="not-a-black-box"></a>Inte en svart låda

De flesta distributioner av NetX Duo innehåller den fullständiga C-källkoden. Detta eliminerar de "black-box"-problem som uppstår med många kommersiella nätverksstackar. Genom att använda NetX Duo kan programutvecklare se exakt vad nätverksstacken gör – det finns inga problem!

Källkoden gör det också möjligt att göra programspecifika ändringar. Även om det inte rekommenderas är det fördelaktigt att ha möjlighet att ändra nätverksstacken om det behövs.

Dessa funktioner är särskilt bekväma för utvecklare som är vana vid att arbeta med lokala eller offentliga domännätverksstackar. De förväntar sig att ha källkod och möjlighet att ändra den. NetX Duo är den ultimata nätverksprogramvaran för sådana utvecklare.

### <a name="bsd-compatible-socket-api"></a>API för BSD-Compatible Socket

För äldre program tillhandahåller NetX Duo också ett BSD-kompatibelt socketgränssnitt som gör anrop till högpresterande NetX Duo API under. Detta hjälper dig att migrera befintlig nätverksprogramkod till NetX Duo.

## <a name="rfcs-supported-by-netx-duo"></a>RFC:er som stöds av NetX Duo

NetX Duo-stöd för RFC:er som beskriver grundläggande nätverksprotokoll omfattar men är inte begränsat till följande nätverksprotokoll. NetX Duo följer alla allmänna rekommendationer och grundläggande krav inom begränsningarna för ett operativsystem i realtid med litet fotavtryck för minne och effektiv körning.

| **RFC**  | **Beskrivning**                                        |
| -------- | ------------------------------------------------------ |
|RFC 1112 | Värdtillägg för IP-multicasting (IGMPv1)           |
|RFC 1122 | Krav för Internetvärdar – kommunikationslager |
|RFC 2236 | Internet Group Management Protocol, version 2          |
|RFC 768  | UDP (User Datagram Protocol)                           |
|RFC 791  | Internet Protocol (IP)                                 |
|RFC 792  | Internet Control Message Protocol (ICMP)               |
|RFC 793  | Transmission Control Protocol (TCP)                    |
|RFC 826  | Ethernet Address Resolution Protocol (ARP) |
|RFC 903  | REVERSE Address Resolution Protocol (RARP) |
|RFC 5681 | TCP-överbelastningskontroll                     |

Nedan visas de IPv6-relaterade RFC:er som stöds av NetX Duo.

|**RFC** |**Beskrivning**|
-------- | ------------------------------------------ |
|RFC 1981 |Sökväg MTU-identifiering för Internet Protocol v6 (IPv6)|
|RFC 2460 | Internet Protocol specifikation för v6 (IPv6)|
|RFC 2464 |Överföring av IPv6-paket via Ethernet-nätverk|
|RFC 4291 |Internet Protocol v6-adresseringsarkitektur (IPv6)|
|RFC 4443 |Internet Control Message Protocol (ICMPv6) för Internet Protocol v6-specifikation (IPv6)|
|RFC 4861 |Grannidentifiering för IP v6|
|RFC 4862 |Automatisk konfiguration av tillståndslös IPv6-adress|

## <a name="embedded-network-applications"></a>Inbäddade nätverksprogram

Inbäddade nätverksprogram är program som behöver nätverksåtkomst och körs på mikroprocessorer som är dolda i produkter som mobiltelefoner, kommunikationsutrustning, bilmotorer, skrivare, medicinska enheter och så vidare. Sådana program har nästan alltid vissa minnes- och prestandabegränsningar. En annan skillnad mellan inbäddade nätverksprogram är att deras programvara och maskinvara har ett särskilt syfte.

Nätverksprogramvara som måste utföra bearbetningen inom en   exakt tidsperiod kallas realtidsnätverksprogramvara och när tidsbegränsningar tillämpas på nätverksprogram klassificeras de som realtidsprogram. Inbäddade nätverksprogram är nästan alltid realtid på grund av deras inbyggda interaktion med den externa världen.

## <a name="netx-duo-benefits"></a>Fördelar med NetX Duo

De främsta fördelarna med att använda NetX Duo för inbäddade program är snabb Internetanslutning och små minneskrav. NetX Duo är också integrerat med operativsystemet ThreadX i realtid med höga prestanda och flera uppgifter.

### <a name="improved-responsiveness"></a>Förbättrad svarstid

Protokollstacken NetX Duo med höga prestanda gör att inbäddade nätverksprogram kan svara snabbare än någonsin tidigare. Detta är särskilt viktigt för inbäddade program som antingen har en betydande mängd nätverkstrafik eller stränga bearbetningskrav på ett enda paket.

### <a name="software-maintenance"></a>Programvaruunderhåll

Med NetX Duo kan utvecklare enkelt partitionera nätverksaspekterna i det inbäddade programmet. Den här partitionering gör hela utvecklingsprocessen enkel och förbättrar avsevärt framtida programvaruunderhåll.

### <a name="increased-throughput"></a>Ökat dataflöde

NetX Duo ger tillgång till nätverk med högsta möjliga prestanda, vilket uppnås med minimala omkostnader för paketbearbetning. Detta möjliggör också ökat dataflöde.

### <a name="processor-isolation"></a>Processorisolering

NetX Duo ger ett robust, processoroberoende gränssnitt mellan programmet och den underliggande processor- och nätverksmaskinvaran. På så sätt kan utvecklare koncentrera sig på nätverksaspekterna i programmet i stället för att ägna extra tid åt att hantera maskinvaruproblem som direkt påverkar nätverket.

### <a name="ease-of-use"></a>Användarvänlighet

NetX Duo är utformat med programutvecklaren i åtanke. NetX Duo-arkitekturen och tjänstanropsgränssnittet är lätta att förstå. Därför kan NetX Duo-utvecklare snabbt använda sina avancerade funktioner.

### <a name="improve-time-to-market"></a>Förbättra tiden till marknad

De kraftfulla funktionerna i NetX Duo påskyndar programutvecklingsprocessen. NetX Duo abstraherar de flesta problem med processor- och nätverksmaskinvara, vilket tar bort dessa problem från de flesta programnätverksspecifika områden. Detta tillsammans med den lättanvända och avancerade funktionsuppsättningen leder till en snabbare tid till marknaden!

### <a name="protecting-the-software-investment"></a>Skydda programvaruinvesteringen

NetX Duo skrivs exklusivt i ANSI C och är helt integrerat med ThreadX-operativsystemet i realtid. Det innebär att NetX Duo-program är direkt portabla till alla ThreadX-processorer som stöds. Ännu bättre är att en ny processorarkitektur kan stödjas med ThreadX på bara några veckor. Därför säkerställer användningen av NetX Duo programmets migreringsväg och skyddar den ursprungliga utvecklingsinvesteringen.

## <a name="ipv6-ready-logo-certification"></a>IPv6-klar logotypcertifiering

NetX Duo-certifieringen "IPv6 Ready" erhölls via paketet "IPv6 Core Protocol (Phase 2) Self Test" som är tillgängligt från IPv6 Ready Organization. Se följande webbplatser IPv6-Ready för mer information om testplattformen och testfallen:[**https://www.ipv6ready.org/**](https://www.ipv6ready.org/)

Fas 2 IPv6 Core Protocol Self Test Suite verifierar att en IPv6-stack uppfyller kraven som anges i följande RFC med omfattande testning:  
Avsnitt 1: RFC 2460  
Avsnitt 2: RFC 4861  
Avsnitt 3: RFC 4862  
Avsnitt 4: RFC 1981  
Avsnitt 5: RFC 4443  

## <a name="ixanvl-test"></a>IxANVL-test

NetX Duo testas med IxANVL från IXIA. IxANVL är branschstandarden för automatiserad nätverks- och protokollvalidering. Mer information om IxANVL finns på: [**https://www.ixiacom.com/products/ixanvl**](https://www.ipv6ready.org/)

I synnerhet testas följande NetX Duo-moduler med IxANVL:

|**Modul** | **Standard** |
| --------- | ------------ |
|IP-adress | RFC791 </br> RFC1122 </br> RFC894|
|ICMP | RFC792 </br> RFC1122 </br> RFC1812|
|UDP | RFC768 </br> RFC1122|
|TCP-Core| RFC793 </br> RFC1122 </br> RFC2460|
|TCP-Advanced| RFC1981</br>RFC2001</br>RFC2385</br>RFC2463</br>RFC813</br>RFC896|
|TCP-Performance| RFC793</br>RFC1323</br>RFC2018|

## <a name="safety-certifications"></a>Säkerhetscertifieringar

### <a name="tv-certification"></a>TÜV-certifiering  

NetX Duo har certifierats av SGS-TÜV Saar för användning i säkerhetskritiska system enligt IEC61508 och IEC-62304. Certifieringen bekräftar att NetX Duo kan användas i utvecklingen av säkerhetsrelaterad programvara för de högsta säkerhetsintegritetsnivåerna i International Electrotechnical Commission (IEC) 61508 och IEC 62304, för "funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade system". SGS-TÜV Saar, som bildas tillsammans med Tysklands SGSGroup och TÜV Saarland, har blivit det ledande auktoriserade, oberoende företaget för testning, granskning, verifiering och certifiering av inbäddad programvara för säkerhetsrelaterade system över hela världen. Den industriella säkerhetsstandarden IEC 61508 och alla standarder som härleds från den, inklusive IEC 62304, används för att garantera funktionell säkerhet för elektriska, elektroniska och programmerbara elektroniska säkerhetsrelaterade medicinska enheter, processkontrollsystem, industriella maskiner och system för kontroll av djur. 

SGS-TÜV Saar har certifierat NetX Duo som ska användas i säkerhetskritiska fordonssystem enligt ISO 26262-standarden. Dessutom är NetX Duo certifierat till Bilsäkerhetsintegritetsnivå (ASIL) D, som representerar den högsta nivån av ISO 26262-certifiering. 

SGS-TÜV Saar har dessutom certifierat NetX Duo som ska användas i säkerhetskritiska program som uppfyller STANDARDEN EN 50128 upp till SW-SIL 4.

![Diagram över SGS-TÜV Saar-certifieringslogotyp.](./media/user-guide/sgs-tuv-saar-logo.png)

IEC 61508 upp till SIL 4  
IEC 62304 upp till SW-säkerhetsklass C ISO 26262 ASIL D EN 50128 SW-SIL 4

> [!IMPORTANT]
> *Kontakta Microsoft om du vill ha mer information om vilka versioner av NetX Duo som har certifierats av TÜV eller om du vill ha tillgång till testrapporter, certifikat och tillhörande dokumentation.*

### <a name="ul-certification"></a>UL-certifiering

NetX Duo har certifierats av UL för kompatibilitet med UL 60730-1 H, CSA E60730-1 Manifest H, IEC 60730-1Lte H, UL 60335-1 Inga R, IEC 60335-1 1 1998- och UL 1998-säkerhetsstandarder för programvara i programmerbara komponenter. Tillsammans med IEC/UL 60730-1, som har krav på "Kontroller med hjälp av programvara" i sin Klass H, beskriver IEC 60335-1-standarden kraven för "Programmerbara elektroniska kretsar" i sin iEC 60730 60330 IEC 60335-1 Vis R tar upp säkerheten för MCU-maskinvara och programvara som används i maskiner som t.ex. maskiner, reglage, torktumlare, kylskåp, skunderar och hjälpmedel.

![Diagram över UL-certifieringslogotyp.](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]  
> *Kontakta Microsoft om du vill ha mer information om vilka versioner av NetX Duo som har certifierats av UL eller för att få tillgång till testrapporter, certifikat och tillhörande dokumentation.*