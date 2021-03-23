---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SNTP
description: Azure återställnings tider NetX Simple Network Time Protocol (SNTP) är ett protokoll som utformats för att synkronisera klockor via Internet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3e1170197c6c4981060459104da80e354fac5db
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825752"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-sntp"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SNTP 

Azure återställnings tider NetX Simple Network Time Protocol (SNTP) är ett protokoll som utformats för att synkronisera klockor via Internet. SNTP version 4 är ett förenklat protokoll baserat på Network Time Protocol (NTP). Den använder UDP-tjänster (User Datagram Protocol) för att utföra tids uppdateringar i ett enkelt, tillstånds lösa protokoll. Även om det inte är så komplext som NTP är SNTP mycket tillförlitligt och korrekt. I de flesta platser för dagens Internet ger SNTP en noggrannhet på 1-50 millisekunder, beroende på egenskaperna för synkroniseringens källa och nätverks Sök vägar. SNTP har många alternativ för att tillhandahålla tillförlitligheten för att ta emot tid uppdateringar. Möjlighet att växla till alternativa servrar och att tillämpa inaktive ring av avsöknings algoritmer och automatisk tids Server identifiering är bara några av de olika sätten för en SNTP-klient att hantera en variabel Internet tids tjänst miljö. Vad det saknar i precisionen utgör det för enkelhetens skull och under lätta implementeringen. SNTP är främst avsett för att tillhandahålla omfattande mekanismer för att få åtkomst till nationella tids-och frekvens spridnings tjänster (t. ex. NTP-server).

## <a name="netx-duo-sntp-client-requirements"></a>Krav för NetX Duo SNTP-klient

NetX Duo SNTP-klienten kräver att en IP-instans redan har skapats. Dessutom måste UDP vara aktiverat på samma IP-instans och ha till gång till den *välkända* port 123 för att skicka tidsdata till en SNTP-server, även om alternativa portar fungerar också. Broadcast-klienter ska binda UDP-porten deras broadcast-server skickar, vanligt vis 123. Klient programmet NetX Duo SNTP måste ha en eller flera IP-adresser för Server-SNTP.

## <a name="netx-duo-sntp-client-limitations"></a>Begränsningar för NetX Duo SNTP-klienten 

Precision i lokal tids representation i NTP-tidsuppdateringar som hanteras av SNTP-klientens API är begränsat till en upplösning på millisekunder.

SNTP-klienten innehåller bara en enda SNTP-serveradress när som helst. Om servern inte längre är giltig, måste programmet stoppa SNTP-klientens aktivitet och initiera om den med en annan SNTP-serveradress, antingen via broadcast eller unicast SNTP-kommunikation.

SNTP-klienten stöder inte manycast.

NetX Duo SNTP-klienten stöder inte autentiseringsmekanismer för verifiering av mottagna paket data.

## <a name="netx-duo-sntp-client-operation"></a>NetX Duo SNTP-klient åtgärd

RFC 4330 rekommenderar att SNTP-klienter endast ska använda det högsta stratum i sitt lokala nätverk och helst i konfigurationer där ingen NTP-eller SNTP-klient är beroende av dem för synkronisering. Stratum-nivån återspeglar värd positionen i NTP-tidshierarkin där stratum 1 är den högsta nivån (en rot tids Server) och 15 är den lägsta tillåtna nivån (t. ex. klient). SNTP-klientens standardvärde för minsta stratum är 2.

NetX Duo SNTP-klienten kan köras i ett av två grundläggande lägen, unicast eller broadcast, för att få tid via Internet. I unicast-läge avsöker klienten sin SNTP-server med jämna mellanrum och väntar på att få ett svar från den servern. När en tas emot, verifierar klienten att svaret innehåller en giltig tids uppdatering genom att använda en uppsättning "Sanity-kontroller" som rekommenderas av RFC 4330. Klienten använder sedan tids skillnaden, om det finns, med Server klockan på den lokala klockan. I sändnings läge lyssnar klienten bara efter tid för att uppdatera sändningarna och behåller sin lokala klocka efter att ha tillämpat en liknande uppsättning Sanity-kontroller för att kontrol lera uppdaterings tidnas data. Sanity-kontroller beskrivs i detalj i avsnittet om **SNTP-Sanity kontroller** nedan.

Innan klienten kan köras i båda lägena måste den upprätta sina operativa parametrar. Detta görs genom att anropa antingen *nx_sntp_client_initialize_unicast* eller *nx_sntp_client_initialize_broadcast* för unicast-eller sändnings lägen. Detta gör att tids gränsen för maximal tid överskrids utan en giltig uppdatering, att gränsen på på varandra följande ogiltiga uppdateringar togs emot, ett avsöknings intervall för unicast-läge, Operations mode, t. ex. unicast vs. broadcast och SNTP server.

Om den maximala tiden för fördröjning eller högsta antalet mottagna uppdateringar överskrids, fortsätter SNTP-klienten att köras men anger den aktuella statusen för SNTP-servern till ogiltig. Programmet kan avsöka SNTP-klienten med hjälp av *nx_sntp_client_receiving_updates* -tjänsten för att kontrol lera att SNTP-servern fortfarande skickar giltiga uppdateringar. Om inte, bör den stoppa klient tråden för SNTP med hjälp av *nx_sntp_client_stop* tjänsten och anropa någon av de två initierande tjänsterna för att ange en annan SNTP-serveradress. För att starta om SNTP-klienten anropar programmet *nx_sntp_client_run_broadcast* eller *nx_sntp_client_run_unicast*. Observera att programmet kan ändra distributions läget för SNTP-klienten i initierings anropet för att växla till unicast eller broadcast som du vill.

### <a name="local-clock-operation"></a>Lokal klock åtgärd

SNTP-tiden baseras på antalet sekunder på huvud-NTP-klockan eller antalet sekunder som förflutit i den första NTP-klockan, t. ex. från 1 januari **1900 00:00:00 till** 1 januari **1999 00:00:00**. Betydelsen av 01-01-1999 var när den senaste avslags sekunden inträffade. Det här värdet definieras enligt följande:

\#definiera NTP_SECONDS_AT_01011999 0xBA368E80

Innan SNTP-klienten körs kan programmet även initiera lokal tid för SNTP-klienten för klienten som ska användas som en bas linje. För att göra det måste tjänsten *nx_sntp_client_set_local_time* användas. Detta tar tiden i NTP-format, sekunder och del, där bråk är millisekunderna i den komprimerade NTP-tiden. Vi rekommenderar att programmet får en SNTP-tid från en oberoende källa. Det finns inget API för att konvertera år, månad, datum och tid till en NTP-tid i NetX Duo SNTP-klienten. En beskrivning av NTP-tidsformat finns i *RFC4330 "Simple Network Time Protocol (SNTP) version 4 för IPv4, IPv6 och OSI".*

Om ingen bas lokal tid anges när SNTP-klienten startas, accepterar SNTP-klienten SNTP-uppdateringar utan att jämföra med den lokala tiden på den första uppdateringen. Därefter kommer den att tillämpa den högsta och lägsta tids uppdaterings värden för att avgöra om den kommer att ändra den lokala tiden.

Programmet kan använda tjänsten *nx_sntp_client_get_local_time_extended* för att hämta lokal tid för SNTP-klienten.

### <a name="sntp-sanity-checks"></a>Sanity-kontroller för SNTP 

Klienten undersöker det inkommande paketet med följande kriterier:

  - Käll-IP-adressen måste matcha den aktuella serverns IP-adress.

  - Avsändar käll porten måste stämma överens med den aktuella Server käll porten.

  - Paket längden måste vara den minsta längd som ska rymmas ett SNTP-klock meddelande.

Därefter extraheras tids data från den minnesbuffert som klienten sedan tillämpar en uppsättning av vissa "Sanity kontroller":

  - Indikatorn för klivet som anges till 3 anger att servern inte är synkroniserad. Klienten bör försöka hitta en alternativ server.

  - Ett stratum-fält med värdet noll kallas för ett kyss-paket (KOD för dödsfall). SMTP-klienten KOD hanterare för den här situationen är en användardefinierad motringning. Den lilla exempel demonstrations filen innehåller en enkel KOD hanterare för den här situationen. Fältet referens-ID innehåller en kod som anger orsaken till att KOD svaret är uppfyllt. KOD hanteraren måste i vilken takt som helst visa hur de ska hantera att ta emot en kyss från SNTP-servern. Det innebär vanligt vis att du vill initiera om SNTP-klienten med en annan SNTP-server.

  - Serverns SNTP-version, stratum och drift läge måste matchas med klient tjänsten.

  - Om klienten har kon figurer ATS med ett maximalt värde för en server klocka, kontrollerar klienten Server klockans spridning på den första uppdateringen tas emot, och om den överskrider klientens Max värde avvisar klienten servern.

  - Fälten för serverns tidsstämpel måste också klara vissa kontroller. För unicast-servern måste alla tids fält fyllas i och får inte vara NULL. Tidsstämpeln för ursprunget måste vara lika med tids stämplingen för överföring i klientens begäran om SNTP-tidsmeddelande. Detta skyddar klienten från skadlig inkräktare och Server beteende för falsk Server. Sändnings servern behöver bara fylla i tids stämplingen för överföring. Eftersom det inte tar emot något från klienten har det inte några fält för mottagning eller ursprung att fylla i.

    En misslyckad Sanity-kontroll varumärken som en tids uppdatering som en ogiltig tids uppdatering. SNTP-klienten Sanity check service spårar antalet ogiltiga tids uppdateringar som tagits emot från samma server i följd.

När en klient tråds uppgift i SNTP kontrollerar giltigheten för ett SNTP-paket för att tillämpa den lokala SNTP-klientens tid, ökar antalet SNTP-klienter som `nx_sntp_client_invalid_time_updates.` också returnerar en fel status till anroparen, men detta är all intern bearbetning så att den inte visas direkt för programmet. Sättet att identifiera uppdateringar av misslyckade tider är att fråga värdet för SNTP-klienten efter att du har `nx_sntp_client_invalid_time_updates` tagit emot uppdateringar av SNTP-serverns tid.

Om uppdateringen av Server tiden passerar Sanity-kontrollerna försöker klienten att bearbeta tids data till den lokala tiden. Om klienten har kon figurer ATS för beräkning av rund resan, t. ex. När en uppdaterings förfrågan skickas till den tid som tas emot, beräknas tiden för fördröjningen. Värdet är halvt och läggs sedan till serverns tid.

Om det här är den första uppdateringen som tas emot från den aktuella SNTP-servern, fastställer SNTP-klienten om den ska ignorera skillnaden mellan servern och lokal klient tid. Därefter utvärderas alla uppdateringar från SNTP-servern för skillnaden med lokal klient tid.

Skillnaden mellan klient-och server tid jämförs med `NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT` . Om det överskrider det här värdet utlöstes data. Om skillnaden är mindre än `NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT` skillnaden betraktas den som för liten för att kräva justering.

Om du skickar alla dessa kontroller används tid uppdateringen sedan på SNTP-klienten med vissa korrigeringar av fördröjningar i intern bearbetning av SNTP-klienter.

### <a name="sntp-asynchronous-unicast-requests"></a>Asynkrona unicast-begäranden i SNTP 

SNTP-klienten gör att värd programmet kan skicka en unicast-begäran asynkront för den aktuella tiden från NTP-servern.

```C
UINT _nx_sntp_client_request_unicast_time(
NX_SNTP_CLIENT *client_ptr, 
UINT wait_option)
```

Alternativet vänte är förfallo datum för att vänta på ett svar.

Om NTP-servern svarar, omfattas paketet av samma bearbetnings-och Sanity-kontroller enligt beskrivningen i föregående avsnitt innan du uppdaterar lokal tid för SNTP-klienten.

Om anropet returnerar slutförd, kan programmet anropa *nx_sntp_client_utility_display_date_time* eller *nx_sntp_client_get_local_time_extended* för den uppdaterade lokala tiden.

Dessa unicast-begäranden påverkar inte det normala SNTP-klientcertifikatet för att skicka nästa unicast-begäran, eller i sändnings läge, när nästa NTP-sändning förväntas.

### <a name="periodic-local-time-updates"></a>Regelbundna uppdateringar av lokal tid

Den maximala justeringen av den lokala tiden anges i alternativet NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT (i millisekunder). Avsöknings uppdaterings intervallet för unicast SNTP klient åtgärder anges i alternativet NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL (i sekunder). Om avsöknings intervallet är större än den maximala justeringen avvisas efterföljande Server uppdateringar efter den första uppdateringen av servern. För att förhindra detta uppdaterar SNTP-klienten den lokala tiden med jämna mellanrum definierad som NX_SNTP_UPDATE_TIMEOUT_INTERVAL. 

Om det finns en skillnad i tiden mellan on-tavlan och Server tiden (vilken SNTP-klientens lokala tid ska vara inställd på), ska den synkroniseras till SNTP-klientens tid (vi visar inte det i den här användar handboken).

Eftersom uppdatering av SNTP-server inte ska ske oftare än en gång per timme, är det inte praktiskt att avsöka SNTP-klienten för Server uppdateringar eller Server status oftare än. SNTP-klienten bör dock uppdatera sin lokala klocka ofta så att den inte längre överskrider den maximala tids justerings parametern NX_SNTP_CLIENT_MAX_TIME_LAPSE.

Alternativt kan den maximala justerings NX_SNTP_CLIENT_MAX_TIME_LAPSE ställas in på fler än unicast-avsöknings uppdateringen (eller förväntade broadcast-intervall). Detta eliminerar behovet av en oberoende real tids klocka. Avsikten med SNTP-protokollet är dock att undvika det totala beroendet av antingen lokal uppdatering eller uppdateringar av nätverks tid. Vidare är uppdatering av SNTP-servern avsedd för att förhindra drift i den lokala tids klockan.

## <a name="multiple-network-interfaces"></a>Flera nätverks gränssnitt

NetX Duo SNTP-klienten kan konfigureras att köras på sekundära nätverk så länge som dessa nätverk är registrerade med IP-instansen. Mer information om hur du registrerar sekundära nätverk finns i användar handboken för NetX Duo eller NetX.

I *nx_sntp_client_create* -anropet ställer du in den tredje ingången iface_index till indexet för det nätverk som SNTP-klienten ska ta emot tid uppdateringar på. Det primära gränssnittet är alltid vid index 0. NetX Duo SNTP-klienten har inte stöd för tids uppdateringar samtidigt på flera nätverks gränssnitt.

## <a name="sntp-and-ntp-rfcs"></a>SNTP-och NTP-rapporter

NetX Duo SNTP-klienten är kompatibel med RFC4330 "Simple Network Time Protocol (SNTP) version 4 för IPv4, IPv6 och OSI och relaterade RFC: er.