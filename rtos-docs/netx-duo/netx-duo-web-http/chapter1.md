---
title: Kapitel 1 – Introduktion till HTTP och HTTPS
description: I det här kapitlet introduceras Azure RTOS NetX Duo HTTP/HTTPS för webbmodulen.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5f50419be3171d3df8544d1b34d603822f339785923f8a8199dc5b5ddcac281
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801766"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>Kapitel 1 – Introduktion till HTTP och HTTPS

Den Hypertext Transfer Protocol (HTTP) är ett protokoll som utformats för att överföra innehåll på webben. HTTP är ett enkelt protokoll som använder tillförlitliga Transmission Control Protocol (TCP)-tjänster för att utföra sin innehållsöverföringsfunktion. Därför är HTTP ett mycket tillförlitligt protokoll för innehållsöverföring. HTTP är ett av de mest använda programprotokollen. Alla åtgärder på webben använder HTTP-protokollet.

HTTPS är den säkra versionen av HTTP-protokollet, som implementerar HTTP med hjälp Transport Layer Security (TLS) för att skydda den underliggande TCP-anslutningen. Förutom den ytterligare konfiguration som krävs för att konfigurera TLS är HTTPS i princip identiskt med HTTP som används.

## <a name="general-http-requirements"></a>Allmänna HTTP-krav

För att NetX Web HTTP-paketet ska fungera korrekt måste NetX Duo (version 5.10 eller senare) vara installerat. Dessutom måste en IP-instans skapas och TCP måste aktiveras på samma IP-instans. För HTTPS-stöd måste även NetX Secure TLS (version 5.11 eller senare) installeras (se nästa avsnitt). Demofilen i avsnittet "Litet exempelsystem" i **kapitel 2** visar hur detta görs.

HTTP-klientdelen av NetX Web HTTP-paketet har inga ytterligare krav.

HTTP Server-delen av NetX Web HTTP-paketet har flera ytterligare krav. För det första krävs fullständig åtkomst till TCP *välkänd port 80* för hantering av alla HTTP-klientbegäranden (detta kan ändras av programmet till en annan giltig TCP-port). HTTP-servern är också utformad för användning med filex-inbäddat filsystem. Om FileX inte är tillgängligt kan användaren porta de delar av FileX som används i deras egen miljö. Detta beskrivs i senare avsnitt i den här guiden.

## <a name="https-requirements"></a>HTTPS-krav

För att HTTPS ska fungera korrekt kräver NetX Web HTTP-paketet att Både NetX Duo (version 5.10 eller senare) och NetX Secure TLS (version 5.11 eller senare) är installerade. Dessutom måste en IP-instans skapas och TCP måste aktiveras på samma IP-instans för användning med TLS. TLS-sessionen måste initieras med lämpliga kryptografiska rutiner, ett betrott CA-certifikat och utrymme måste allokeras för certifikat som kommer att tillhandahållas av fjärrservervärdar under TLS-handskakningen. Demofilen i avsnittet "Small Example HTTPS System" i **kapitel 2** visar hur detta görs.

HTTPS-klientdelen av NetX Web HTTP-paketet har inga ytterligare krav.

HTTPS-serverdelen av NetX Web HTTP-paketet har flera ytterligare krav. För det första krävs fullständig åtkomst till DEN välkända *TCP-porten 443* för hantering av alla KLIENT-HTTPS-begäranden (precis som med HTTP i klartext kan den här porten ändras av programmet). För det andra måste TLS-sessionen initieras med rätt kryptografiska rutiner och ett serveridentitetscertifikat (eller i förväg delad nyckel). HTTPS-servern är också utformad för användning med filex-inbäddat filsystem. Om FileX inte är tillgängligt kan användaren porta de delar av FileX som används i deras egen miljö. Användningen av FileX beskrivs i senare avsnitt i den här guiden.

Mer information om konfigurationsalternativ för TLS finns i NetX Secure-dokumentationen.

Om inget annat anges gäller alla HTTP-funktioner som beskrivs i det här dokumentet även HTTPS.

## <a name="http-and-https-constraints"></a>HTTP- och HTTPS-begränsningar

NetX Web HTTP implementerar HTTP 1.1-standarden. Här är dock följande begränsningar:

1. Pipelining för begäran stöds inte
1. HTTP-servern stöder både grundläggande och MD5-sammanfattad autentisering, men inte MD5-sess. HTTP-klienten stöder för närvarande endast grundläggande autentisering. När du använder TLS för HTTPS kan HTTP-autentisering fortfarande användas.
1. Ingen innehållskomprimering stöds.
1. TRACE-, OPTIONS- och CONNECT-begäranden stöds inte.
1. Paketpoolen som är associerad med HTTP-servern eller klienten måste vara tillräckligt stor för att rymma hela HTTP-huvudet.
1. HTTP-klienttjänster är endast till för innehållsöverföring – det finns inga visningsverktyg i det här paketet.

## <a name="http-url-resource-names"></a>HTTP-URL (resursnamn)

HTTP-protokollet är utformat för att överföra innehåll på webben. Det begärda innehållet anges av Universal Resource Locator (URL). Det här är den primära komponenten i varje HTTP-begäran. URL:er börjar alltid med ett "/"-tecken och motsvarar vanligtvis filer på HTTP-servern. Vanliga HTTP-filnamnstillägg visas nedan:

- **.htm** (eller **.html**) Hypertext Markup Language (HTML)
- **.txt** Oformaterad ASCII-text
- **.gif** Binär GIF-bild
- **.xbm** Bild av binär Xbitmap

## <a name="http-client-requests"></a>HTTP-klientbegäranden

HTTP har en enkel mekanism för att begära webbinnehåll. Det finns en uppsättning http-standardkommandon som utfärdas av klienten när en anslutning har upprättats på den välkända *TCP-porten 80 (port 443 för HTTPS).* Nedan visas några av de grundläggande HTTP-kommandona:

- **GET *resource* HTTP/1.1** Hämta den angivna resursen
- ***POST-resursen* HTTP/1.1** Hämta den angivna resursen och skicka anslutna indata till HTTP-servern
- ***HEAD-resursen* HTTP/1.1** Behandlas som en GET men inte innehåll returneras av HTTP-servern
- ***PUT-resursen* HTTP/1.1** Placera resurs på HTTP-server
- **DELETE *resource* HTTP/1.1** Ta bort resurs på servern

Dessa ASCII-kommandon genereras internt av webbläsare och NetX Web HTTP-klienttjänster för att utföra HTTP-åtgärder med en HTTP-server.

Observera att HTTP-klientprogrammet ska använda port 80 eller port 443 om HTTPS används. Både KLIENT- och server-HTTP-API:er tar porten som en parameter – makrona NX_WEB_HTTP_SERVER_PORT (port 80) och NX_WEB_HTTPS_SERVER_PORT (port 443) har definierats för enkelhetens skull. HTTP-serverporten kan också ändras vid körning med hjälp *av nx_web_http_client_set_connect_port()-tjänsten.* Mer information om den här tjänsten finns i kapitel 4.

## <a name="http-server-responses"></a>HTTP-serversvar

HTTP-servern använder samma välkända *TCP-port 80 (443 för HTTPS)* för att skicka klientkommandosvar. När HTTP-servern bearbetar klientkommandot returneras en ASCII-svarssträng som innehåller en 3-siffrig numerisk statuskod. Det numeriska svaret används av HTTP-klientprogrammet för att avgöra om åtgärden lyckades eller misslyckades. Följande är en lista över olika HTTP-serversvar på klientkommandon:

- **200-begäran** lyckades
- **400-begäran** har inte formats korrekt
- **401** Obehörig begäran, klienten måste skicka autentisering
- **404 Angiven** resurs i begäran hittades inte
- **500 Internt** HTTP-serverfel
- **501-begäran** implementeras inte av HTTP Server
- **502-tjänsten** är inte tillgänglig

Till exempel besvaras en lyckad klientbegäran om att PLACERA filen "test.htm" med meddelandet "HTTP/1.1 200 OK".

## <a name="http-communication"></a>HTTP-kommunikation

Som tidigare nämnts använder HTTP-servern den välkända *TCP-port 80 (443 för HTTPS)* för att ange klientbegäranden. HTTP-klienter kan använda alla tillgängliga TCP-portar för utgående anslutningar. Den allmänna sekvensen med HTTP-händelser är följande:

**HTTP GET-begäran:**

1. Klientproblem TCP-anslutning till serverport 80 (eller 443 för HTTPS).
1. Om HTTPS används följs TCP-anslutningen av en TLS-handskakning för att autentisera servern och upprätta en säker kanal.
1. Klienten skickar en **HTTP/1.1-begäran** för GET-resursen (tillsammans med annan rubrikinformation).
1. Servern skapar ett **"HTTP/1.1 200** OK"-meddelande med ytterligare information följt av resursinnehållet (om sådant finns).
1. Servern kopplar från klienten (TLS stängs av om HTTPS används).
1. Klienten kopplar från socketen (TLS stängs av efter aviseringen om frånkoppling från servern).

**HTTP PUT-begäran:**

1. Klientproblem TCP-anslutning till serverport 80 (eller 443).
1. Om HTTPS används följs TCP-anslutningen av en TLS-handskakning för att autentisera servern och upprätta en säker kanal.
1. Klienten skickar en HTTP/1.1-begäran för PUT-resursen tillsammans med annan rubrikinformation, följt av resursinnehållet.
1. Servern skapar ett "HTTP/1.1 200 OK"-meddelande med ytterligare information följt av resursinnehållet direkt.
1. Servern utför en frånkoppling.
1. Klienten utför en frånkoppling.

> [!NOTE]
> Som tidigare nämnts kan HTTP-servern ändra standardporten för anslutning (80 eller 443) vid körning med hjälp av *nx_web_http_client_set_connect_port()* för webbservrar som använder alternativa portar för att ansluta till klienter.

## <a name="http-authentication"></a>HTTP-autentisering

HTTP-autentisering är valfritt och krävs inte för alla webbförfrågningar. Det finns två varianter av autentisering, *nämligen grundläggande* och *sammanfattande*. Grundläggande autentisering motsvarar namn- och *lösenordsautentisering* som finns i många protokoll.  I grundläggande HTTP-autentisering sammanfogas namn och lösenord och kodas i base64-format. Den största nackdelen med grundläggande autentisering är att namn och lösenord överförs öppet i begäran. Det gör det lite enkelt att stjäla namn och lösenord. Sammanfattad autentisering löser det här problemet genom att aldrig överföra namn och lösenord i begäran. I stället används en algoritm för att härleda en 128-bitars sammanfattning från namn, lösenord och annan information. NetX Web HTTP Server stöder standardalgoritmen för MD5-sammanfattning.

När krävs autentisering? HTTP-servern avgör om en begärd resurs kräver autentisering. Om autentisering krävs och klientbegäran inte innehåller rätt autentisering, skickas svaret "HTTP/1.1 401 Unauthorized" med den typ av autentisering som krävs till klienten. Klienten förväntas sedan skapa en ny begäran med rätt autentisering.

När HTTPS används kan HTTPS-servern fortfarande använda HTTP-autentisering. I det här fallet används TLS för  att kryptera all HTTP-trafik så att grundläggande HTTP-autentisering inte utgör en säkerhetsrisk. *Sammanfattad* autentisering tillåts också, men ger ingen betydande säkerhetsförbättring jämfört med grundläggande autentisering över TLS.

## <a name="http-authentication-callback"></a>Återanrop för HTTP-autentisering

Som tidigare nämnts är HTTP-autentisering valfritt och krävs inte för alla weböverföringar. Dessutom är autentisering vanligtvis resursberoende. Åtkomst till vissa resurser på servern kräver autentisering, medan andra inte gör det. Med NetX Web HTTP Server-paketet kan  programmet (via nx_web_http_server_create-anropet) ange en rutin för autentiseringsanrop som anropas i början av hanteringen av varje HTTP-klientbegäran.

Återanropsrutinen förser NetX Web HTTP Server med användarnamn, lösenord och sfärsträngar som är associerade med resursen och returnerar den typ av autentisering som krävs. Om ingen autentisering krävs för resursen ska återanropet av autentisering returnera värdet för **NX_WEB_HTTP_DONT_AUTHENTICATE**. Annars, om grundläggande autentisering krävs för den angivna resursen, ska rutinen returnera **NX_WEB_HTTP_BASIC_AUTHENTICATE**. Och slutligen, om sammanfattad MD5-autentisering krävs ska återanropsrutinen returnera **NX_WEB_HTTP_DIGEST_AUTHENTICATE**. Om ingen autentisering krävs för en resurs som tillhandahålls av HTTP-servern behövs inte motringning och en NULL-pekare kan anges för HTTP-serverns skapa-anrop.

Formatet för programmet autentiserar motringning är mycket enkelt och definieras nedan:

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

Indataparametrarna definieras på följande sätt:

- **request_type** Anger HTTP-klientbegäran, giltiga begäranden definieras som:
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **resurs** Specifik resurs som begärdes.
- **namn** Mål för pekaren till det användarnamn som krävs.
- **lösenord** Mål för pekaren till det lösenord som krävs.
- **sfär** Mål för pekaren till sfären för den här autentiseringen.

Returvärdet för autentiseringsrutinen anger om autentisering krävs. pekare för namn, lösenord och sfär används inte **om NX_WEB_HTTP_DONT_AUTHENTICATE** returneras av autentiseringsrutinen för återanrop. Annars måste HTTP-serverutvecklaren se **till att NX_WEB_HTTP_MAX_USERNAME** och **NX_WEB_HTTP_MAX_PASSWORD** som definierats *i nx_web_http_server.h* är tillräckligt stora för användarnamnet och lösenordet som anges i autentiseringsanropet. Båda dessa har en standardstorlek på 20 tecken.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP ogiltigt användarnamn/återanrop av lösenord

Det valfria ogiltiga återanropet av användarnamn/lösenord i NetX-webb-HTTP-servern anropas om HTTP-servern får en ogiltig kombination av användarnamn och lösenord i en klientbegäran. Om HTTP-serverprogrammet registrerar ett återanrop med HTTP-servern anropas det om antingen grundläggande eller sammanfattad autentisering misslyckas i *nx_web_http_server_get_process()*, *i nx_web_http_server_put_process()* eller *i nx_web_http_server_delete_process().*

För att registrera ett återanrop med HTTP-servern definieras följande tjänst för NetX-webb-HTTP-servern.

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

Begärandetyperna definieras på följande sätt:

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP Insert GMT Date Header Callback

Det finns ett valfritt återanrop i NetX Web HTTP Server för att infoga en datumrubrik i svarsmeddelandena. Det här återanropet anropas när HTTP-servern svarar på en put- eller get-begäran

Följande tjänst definieras för att registrera ett GMT-datumanrop med HTTP-servern.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

Datatypen NX_WEB_HTTP_SERVER_DATE definieras på följande sätt:

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP Cache Info Get Callback

HTTP-servern har ett återanrop för att begära högsta ålder och datum från HTTP-programmet för en specifik resurs. Den här informationen används för att avgöra om HTTP-servern skickar en hel sida som svar på en Client Get-begäran. Om "if modified since" i klientbegäran inte hittas eller inte matchar datumet för senaste ändring som returnerades av get cache-återanropet, skickas hela sidan.

För att registrera motringning med HTTP-servern definieras följande tjänst:

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>Kodningsstöd för HTTP-segmenterad överföring

När den totala längden på HTTP-meddelanden inte kan fastställas innan det skickas kan funktionen Chunked Transfer Coding användas för att skicka meddelanden som en serie med segment utan rubrikfältet "Content-Length". Den här funktionen stöds i alla HTTP-begäran- och svarsmeddelanden. Som mottagare stöds den här funktionen och segmentrubriken bearbetas transparent av intern logik. Som avsändare måste *API-nx_web_http_client_request_chunked_set* *nx_web_http_server_response_chunked_set* anropas av klienten respektive servern.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

Mer information om dessa tjänster finns i beskrivningarna i kapitel 3 "Beskrivning av HTTP-tjänster".

## <a name="http-multipart-support"></a>HTTP-stöd för flera delar

Multipurpose Internet Mail Extensions (MIME) var ursprungligen avsett för SMTP-protokollet, men dess användning har spridits till HTTP. MIME gör att meddelanden kan innehålla blandade meddelandetyper (t.ex. bild/jpg och text/oformaterad) i samma meddelande. NetX-webb-HTTP-servern har tjänster för att fastställa innehållstyp i HTTP-meddelanden som innehåller MIME från klienten. Om du vill aktivera stöd för HTTP med flera delar och använda dessa **tjänster NX_WEB_HTTP_MULTIPART_ENABLE** konfigurationsalternativet definieras.

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

Mer information om användningen av dessa tjänster finns i beskrivningen i kapitel 3 "Beskrivning av HTTP-tjänster".

## <a name="http-multi-thread-support"></a>HTTP-stöd för flera trådar

NetX Web HTTP-klienttjänsterna kan anropas från flera trådar samtidigt. Läs- eller skrivbegäranden för en viss HTTP-klientinstans bör dock göras i följd från samma tråd.

Om du använder HTTPS kan NetX Web HTTP-klienttjänster anropas från flera trådar, men på grund av den ytterligare komplexiteten i de underliggande TLS-funktionerna bör varje tråd ha en enda, oberoende HTTP-klientinstans (NX_WEB_HTTP_CLIENT-kontrollstruktur).

## <a name="http-rfcs"></a>HTTP-RFC

NetX Web HTTP är kompatibel med RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2616 "Hypertext Transfer Protocol – HTTP/1.1", RFC 2581 "TCP Congestion Control", RFC 1122 "Krav för Internetvärdar" och relaterade RFC: er.

För HTTPS är NetX Web HTTP kompatibelt med RFC 2818 "HTTP över TLS".
