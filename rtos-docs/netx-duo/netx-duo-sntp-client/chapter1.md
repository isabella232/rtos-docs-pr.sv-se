---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo SNTP
description: Det Azure RTOS SNTP (NetX Simple Network Time Protocol) är ett protokoll som utformats för att synkronisera klockor via Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a284871d8da9b8d6d220e962de5d27483dafab201b68d64d5c794c1edab50153
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798834"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo SNTP 

Det Azure RTOS SNTP (NetX Simple Network Time Protocol) är ett protokoll som utformats för att synkronisera klockor via Internet. SNTP Version 4 är ett förenklat protokoll som baseras på Network Time Protocol (NTP). Den använder UDP-tjänster (User Datagram Protocol) för att utföra tidsuppdateringar i ett enkelt, tillståndslöst protokoll. Även om SNTP inte är lika komplext som NTP är det mycket tillförlitligt och korrekt. På de flesta platser på Internet i dag ger SNTP en precision på 1–50 millisekunder, beroende på egenskaperna hos synkroniseringskällan och nätverkssökvägarna. SNTP har många alternativ för att ge tillförlitlighet vid mottagning av tidsuppdateringar. Möjligheten att växla till alternativa servrar, tillämpa back off-avsökningsalgoritmer och automatisk identifiering av tidsserver är bara några av de sätt som en SNTP-klient kan använda för att hantera en variabel Internettidstjänstmiljö. Vad den saknar precision utgör enkelt och enkelt att genomföra. SNTP är främst avsett för att tillhandahålla omfattande mekanismer för att få åtkomst till nationella tids- och frekvensfrekvenstjänster (t.ex. NTP-server).

## <a name="netx-duo-sntp-client-requirements"></a>Klientkrav för NetX Duo SNTP

NetX Duo SNTP-klienten kräver att en IP-instans redan har skapats. Dessutom måste UDP vara aktiverat på samma *IP-instans* och ha åtkomst till den välkända port 123 för att skicka tidsdata till en SNTP-server, även om även alternativa portar fungerar. Broadcast-klienter ska binda UDP-porten som deras broadcast-server skickar på, vanligtvis 123. NetX Duo SNTP-klientprogrammet måste ha en eller flera IP SNTP-serveradresser.

## <a name="netx-duo-sntp-client-limitations"></a>Begränsningar för NetX Duo SNTP-klienten 

Precision i lokal tidsrepresentation i NTP-tidsuppdateringar som hanteras av SNTP-klient-API:et är begränsad till en millisekundlösning.

SNTP-klienten har bara en enda SNTP-serveradress när som helst. Om servern inte längre verkar vara giltig måste programmet stoppa SNTP-klientuppgiften och initiera om den med en annan SNTP-serveradress med broadcast- eller unicast SNTP-kommunikation.

SNTP-klienten stöder inte manycast.

NetX Duo SNTP-klienten stöder inte autentiseringsmekanismer för verifiering av mottagna paketdata.

## <a name="netx-duo-sntp-client-operation"></a>NetX Duo SNTP-klientåtgärd

RFC 4330 rekommenderar att SNTP-klienter endast ska fungera på den högsta nivån i det lokala nätverket och helst i konfigurationer där ingen NTP- eller SNTP-klient är beroende av dem för synkronisering. Nivån Stratum visar värdpositionen i NTP-tidshierarkin där stratum 1 är den högsta nivån (en rottidsserver) och 15 är den lägsta tillåtna nivån (t.ex. Klient). SNTP-klientens lägsta stratum är 2.

NetX Duo SNTP-klienten kan användas i ett av två grundläggande lägen, unicast eller broadcast, för att få tid via Internet. I unicast-läge avsöker klienten sin SNTP-server med jämna mellanrum och väntar på att få ett svar från den servern. När ett svar tas emot verifierar klienten att svaret innehåller en giltig tidsuppdatering genom att tillämpa en uppsättning "sanitetskontroller" som rekommenderas av RFC 4330. Klienten tillämpar sedan tidsskillnaden, om någon, med serverklockan på den lokala klockan. I sändningsläge lyssnar klienten bara efter sändning av tidsuppdatering och underhåller sin lokala klocka efter att ha tillämpat en liknande uppsättning sanitetskontroller för att verifiera uppdateringstidsdata. Sanity checks (Sanitetskontroller) beskrivs i detalj i **avsnittet Sanity Checks (Sanitetskontroller för SNTP)** nedan.

Innan klienten kan köras i något av lägena måste den upprätta sina driftsparametrar. Detta görs genom att anropa *antingen nx_sntp_client_initialize_unicast* *eller nx_sntp_client_initialize_broadcast* för unicast- respektive broadcast-lägen. Dessa fungerar för att ange tidsgränser för maximal tid utan en giltig uppdatering, gränsen för efterföljande ogiltiga uppdateringar som tagits emot, ett avsökningsintervall för unicast-läge, driftläge, till exempel unicast eller broadcast och SNTP-server.

Om maximalt antal mottagna uppdateringar eller maximalt antal ogiltiga uppdateringar överskrids fortsätter SNTP-klienten att köras men anger den aktuella SNTP-serverstatusen till ogiltig. Programmet kan avse SNTP-klienten *med hjälp nx_sntp_client_receiving_updates-tjänsten* för att verifiera att SNTP-servern fortfarande skickar giltiga uppdateringar. Annars bör SNTP-klienttråden stoppas med *hjälp av nx_sntp_client_stop-tjänsten* och anropa någon av de två initierar tjänsterna för att ange en annan SNTP-serveradress. För att starta om SNTP-klienten anropar *programmet nx_sntp_client_run_broadcast* eller *nx_sntp_client_run_unicast*. Observera att programmet kan ändra SNTP-klientens driftläge i initiera-anropet för att växla till unicast eller broadcast efter behov.

### <a name="local-clock-operation"></a>Åtgärd för lokal klocka

SNTP-tiden baserat på antalet sekunder på HUVUD-NTP-klockan eller antalet sekunder som förflutit i den första NTP-epoken, t.ex. från 1 januari **1900 00:00:00** till 1 januari **1999 00:00:00**. Signifikansen för 01-01-1999 var när det sista skottet sekund inträffade. Det här värdet definieras på följande sätt:

\#definiera NTP_SECONDS_AT_01011999 0xBA368E80

Innan SNTP-klienten körs kan programmet eventuellt initiera lokal tid för SNTP-klienten som klienten ska använda som baslinjetid. För att göra det  måste den använda nx_sntp_client_set_local_time tjänsten. Detta tar tid i NTP-format, sekunder och bråk, där bråk är millisekunder i NTP-komprimerad tid. Helst kan programmet hämta en SNTP-tid från en oberoende källa. Det finns inget API för konvertering av år, månad, datum och tid till en NTP-tid i NetX Duo SNTP-klienten. En beskrivning av NTP-tidsformat finns i *RFC4330 "Simple Network Time Protocol (SNTP) version 4 för IPv4, IPv6 och OSI".*

Om ingen lokal bastid anges när SNTP-klienten startas accepterar SNTP-klienten SNTP-uppdateringarna utan att jämföra med dess lokala tid i den första uppdateringen. Därefter tillämpar den de högsta och lägsta tidsuppdateringsvärdena för att avgöra om den ska ändra sin lokala tid.

För att hämta lokal tid för SNTP-klienten kan programmet använda *nx_sntp_client_get_local_time_extended tjänsten.*

### <a name="sntp-sanity-checks"></a>Sanity-kontroller för SNTP 

Klienten undersöker det inkommande paketet enligt följande kriterier:

  - Källans IP-adress måste matcha den aktuella serverns IP-adress.

  - Avsändarens källport måste matcha den aktuella serverkällporten.

  - Paketlängden måste vara den minsta längden för ett SNTP-tidsmeddelande.

Därefter extraheras tidsdata från paketbufferten som klienten sedan tillämpar en uppsättning specifika "sanitetskontroller" på:

  - Skottindikatorn inställd på 3 anger att servern inte har synkroniserats. Klienten bör försöka hitta en alternativ server.

  - Ett stratumfält som är inställt på noll kallas för ett Kod-paket (Death of Death). SMTP-klientens KOD-hanterare för den här situationen är ett användardefinierat återanrop. Den lilla exempeldemofilen innehåller en enkel KOD-hanterare för den här situationen. Fältet Referens-ID innehåller eventuellt en kod som anger orsaken till KOD-svaret. KOD-hanteraren måste i alla fall ange hur den ska hantera mottagandet av ett dödsfall från SNTP-servern. Vanligtvis bör SNTP-klienten initieras om med en annan SNTP-server.

  - Server SNTP-version, stratum och driftsläge måste matchas till klienttjänsten.

  - Om klienten är konfigurerad med en maximal spridning av serverklocka kontrollerar klienten serverklocksspridningen endast vid den första uppdateringen som tas emot, och om den överskrider maxvärdet För klienten avvisar klienten servern.

  - Fälten för servertidsstämpel måste också klara specifika kontroller. För unicast-servern måste alla tidsfält vara ifyllda och får inte vara NULL. Tidsstämpeln För ursprung måste vara lika med tidsstämpeln För överföring i klientens begäran om tidsmeddelande för SNTP. Detta skyddar klienten från skadliga intrång och otillåtet serverbeteende. Sändningsservern behöver bara fylla i tidsstämpeln För överföring. Eftersom den inte får något från klienten har den inga fält för mottagning eller ursprung att fylla i.

    En misslyckad sanitetskontroll markerar en tidsuppdatering som en ogiltig tidsuppdatering. Tjänsten SNTP Client Sanity Check spårar antalet på varandra följande ogiltiga tidsuppdateringar som tagits emot från samma server.

När SNTP-klientens trådaktivitet kontrollerar giltigheten för ett SNTP-paket för tillämpning på den lokala SNTP-klientens tid ökar antalet SNTP-klienter. Det returnerar även en felstatus till anroparen, men detta är intern bearbetning så att den inte visas omedelbart för `nx_sntp_client_invalid_time_updates.` programmet. Sättet att identifiera misslyckade tidsuppdateringar är att fråga värdet för SNTP-klienten efter `nx_sntp_client_invalid_time_updates` att ha tagit emot tidsuppdateringar för SNTP-servern.

Om tidsuppdateringen för server klarar hälsokontrollerna försöker klienten bearbeta tidsdata till sin lokala tid. Om klienten har konfigurerats för beräkning av tur och retur, t.ex. tiden från att en uppdateringsbegäran skickades till den tidpunkt då den tas emot, beräknas tur och retur-tiden. Det här värdet halveras och läggs sedan till i serverns tid.

Om det här är den första uppdateringen som togs emot från den aktuella SNTP-servern avgör SNTP-klienten om den ska ignorera skillnaden mellan servern och klientens lokala tid. Därefter utvärderas alla uppdateringar från SNTP-servern för skillnaden med klientens lokala tid.

Skillnaden mellan klient- och servertid jämförs med `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT` . Om den överskrider det här värdet, kommer data att kastas ut. Om skillnaden är mindre än skillnaden `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT` anses vara för liten för att kräva justering.

Genom att skicka alla dessa kontroller tillämpas tidsuppdateringen sedan på SNTP-klienten med vissa korrigeringar för fördröjningar i intern SNTP-klientbearbetning.

### <a name="sntp-asynchronous-unicast-requests"></a>Asynkrona SNTP-unicast-begäranden 

Med SNTP-klienten kan värdprogrammet asynkront skicka en unicast-begäran för aktuell tid från NTP-servern.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

Väntealternativet är förfallotiden för att vänta på ett svar.

Om NTP-servern svarar utsätts paketet för samma bearbetnings- och hälsokontroller enligt beskrivningen i föregående avsnitt innan SNTP-klienten uppdateras lokal tid.

Om anropet returnerar slutförande kan programmet *anropa nx_sntp_client_utility_display_date_time* *eller nx_sntp_client_get_local_time_extended* för den uppdaterade lokala tiden.

Dessa unicast-begäranden stör inte det normala SNTP-klientschemat för att skicka nästa unicast-begäran, eller om de är i sändningsläge, när nästa NTP-sändning ska förväntas.

### <a name="periodic-local-time-updates"></a>Periodiska lokala tidsuppdateringar

Den maximala justeringen av lokal tid anges i NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT (i millisekunder). Avsökningsuppdateringsintervallet för unicast SNTP-klientåtgärder anges i NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL (i sekunder). Om avsökningsintervallet är större än den maximala justeringen avvisas efterföljande serveruppdateringar efter den första serveruppdateringen. För att förhindra detta uppdaterar SNTP-klienten den lokala tid som regelbundet definieras som NX_SNTP_UPDATE_TIMEOUT_INTERVAL. 

Om det finns en tidsskillnad mellan den inkopplade RTC:n och servertiden (som lokal tid för SNTP-klienten ska anges till) ska RTC synkroniseras till SNTP-klientens tid (det visas inte i den här användarhandboken).

Eftersom SNTP-serveruppdateringar inte bör ske oftare än en gång i timmen är det inte användbart att avse SNTP-klienten efter serveruppdateringar eller serverstatus oftare än så. SNTP-klienten bör dock uppdatera sin lokala klocka tillräckligt ofta för att inte gå längre än parametern för maximal tidsjustering NX_SNTP_CLIENT_MAX_TIME_LAPSE.

Alternativt kan den maximala NX_SNTP_CLIENT_MAX_TIME_LAPSE anges till större än unicast-avsökningsuppdateringen (eller förväntade sändningsintervall). Det senare eliminerar behovet av en oberoende realtidsklocka. Avsikten med SNTP-protokollet är dock att undvika total beroende av antingen lokala RTC- eller nätverkstidsuppdateringar. Dessutom är SNTP-serveruppdateringarna avsedda att förhindra drift i den lokala tidsklockan.

## <a name="multiple-network-interfaces"></a>Flera nätverksgränssnitt

NetX Duo SNTP-klienten kan konfigureras att köras på sekundära nätverk så länge dessa nätverk är registrerade med IP-instansen. Mer information om hur du registrerar sekundära nätverk finns i användarhandboken för NetX Duo eller NetX.

I *nx_sntp_client_create* anger du det tredje indatavärdet, iface_index, till indexet för nätverket som SNTP-klienten ska ta emot tidsuppdateringar på. Det primära gränssnittet är alltid vid index 0. NetX Duo SNTP-klienten har inte stöd för tidsuppdateringar samtidigt i flera nätverksgränssnitt.

## <a name="sntp-and-ntp-rfcs"></a>SNTP- och NTP-RFC:er

NetX Duo SNTP-klienten är kompatibel med RFC4330 "Simple Network Time Protocol (SNTP) Version 4 för IPv4, IPv6 och OSI" och relaterade RFC:er.