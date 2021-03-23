---
title: Kapitel 1 – Introduktion till HTTP och HTTPS
description: I det här kapitlet introduceras Azure återställnings tider NetX Duo HTTP/HTTPS för Web-modulen.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c784843e4d3f11ee306e866223c0a19bfcba3b85
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826994"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>Kapitel 1 – Introduktion till HTTP och HTTPS

Hypertext Transfer Protocol (HTTP) är ett protokoll som har utformats för att överföra innehåll på webben. HTTP är ett enkelt protokoll som använder Reliable Transmission Control Protocol (TCP)-tjänster för att utföra sin innehålls överförings funktion. Därför är HTTP ett mycket tillförlitligt innehålls överförings protokoll. HTTP är ett av de mest använda program protokollen. Alla åtgärder på webben använder HTTP-protokollet.

HTTPS är en säker version av HTTP-protokollet, som implementerar HTTP med hjälp av Transport Layer Security (TLS) för att skydda den underliggande TCP-anslutningen. Förutom den ytterligare konfiguration som krävs för att konfigurera TLS, är HTTPS i princip identiskt med HTTP som används.

## <a name="general-http-requirements"></a>Allmänna HTTP-krav

För att kunna fungera korrekt kräver NetX-webbhttp-paketet att NetX Duo (version 5,10 eller senare) är installerat. Dessutom måste en IP-instans skapas och TCP måste vara aktiverat på samma IP-instans. För HTTPS-stöd måste NetX Secure TLS (version 5,11 eller senare) också installeras (se nästa avsnitt). Demo filen i avsnittet "litet exempel system" i **kapitel 2** visar hur detta görs.

HTTP-klient delen av NetX-webb-HTTP-paketet har inga ytterligare krav.

HTTP-server delen av NetX-webb-HTTP-paketet har flera ytterligare krav. Först måste du ha fullständig åtkomst till den *välkända TCP-porten 80* för att hantera alla klient-HTTP-begäranden (detta kan ändras av programmet till någon annan giltig TCP-port). HTTP-servern är också avsedd att användas med det inbäddade fil systemet FileX. Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö. Detta beskrivs i senare avsnitt i den här hand boken.

## <a name="https-requirements"></a>HTTPS-krav

För att HTTPS ska fungera korrekt kräver NetX webb-HTTP-paketet att NetX Duo (version 5,10 eller senare) och NetX Secure TLS (version 5,11 eller senare) båda är installerade. Dessutom måste en IP-instans skapas och TCP måste vara aktiverat på samma IP-instans för användning med TLS. TLS-sessionen måste initieras med lämpliga kryptografiska rutiner, ett certifikat för betrodd certifikat utfärdare och utrymme måste allokeras för certifikat som kommer att tillhandahållas av fjärrserverns värdar under TLS-handskakningen. Demo filen i avsnittet "litet exempel HTTPS system" i **kapitel 2** visar hur detta görs.

HTTPS-klient delen av NetX-webb-HTTP-paketet har inga ytterligare krav.

HTTPS-server delen av NetX-webb-HTTP-paketet har flera ytterligare krav. Först måste du ha fullständig åtkomst till den TCP *-välkända porten 443* för att hantera alla KLIENTERs HTTPS-begäranden (som med http med oformaterad text, den här porten kan ändras av programmet). Därefter måste TLS-sessionen initieras med rätt kryptografiska rutiner och ett Server identitets certifikat (eller i förväg delad nyckel). HTTPS-servern är också avsedd att användas med det inbäddade fil systemet FileX. Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö. Användningen av FileX beskrivs i senare avsnitt i den här hand boken.

Mer information om konfigurations alternativen för TLS hittar du i NetX Secure Documentation.

Om inget annat anges gäller alla HTTP-funktioner som beskrivs i det här dokumentet också för HTTPS.

## <a name="http-and-https-constraints"></a>HTTP-och HTTPS-begränsningar

NetX webb-HTTP implementerar HTTP 1,1-standarden. Följande begränsningar gäller dock:

1. Pipelining för begäran stöds inte
1. HTTP-servern stöder både Basic-och MD5 Digest-autentisering, men inte MD5-sess. HTTP-klienten har nu bara stöd för grundläggande autentisering. När du använder TLS för HTTPS kan HTTP-autentisering fortfarande användas.
1. Det finns inte stöd för innehålls komprimering.
1. SPÅRNINGs-, alternativ-och ANSLUTNINGS begär Anden stöds inte.
1. Den modempool som är kopplad till HTTP-servern eller-klienten måste vara tillräckligt stor för att rymma det fullständiga HTTP-huvudet.
1. HTTP-klienttjänster är endast för innehålls överföring – det finns inga visnings verktyg i det här paketet.

## <a name="http-url-resource-names"></a>HTTP-URL (resurs namn)

HTTP-protokollet är utformat för att överföra innehåll på webben. Det begärda innehållet anges av URL: en (Universal Resource Locator). Detta är den primära komponenten i varje HTTP-begäran. URL: er börjar alltid med ett "/"-Character och motsvarar vanligt vis filer på HTTP-servern. Vanliga HTTP-filtillägg visas nedan:

- **. htm** (eller **. html**) Hypertext Markup Language (HTML)
- **. txt** Oformaterad ASCII-text
- **. gif** Binär GIF-bild
- **. XBM** Binär Xbitmap-avbildning

## <a name="http-client-requests"></a>HTTP-klient begär Anden

HTTP har en enkel mekanism för att begära webb innehåll. Det finns en uppsättning standard-HTTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den välkända TCP *-porten 80 (port 443 för https)*. Nedan visas några av de grundläggande HTTP-kommandona:

- **Hämta *resurs* -http/1.1** Hämta den angivna resursen
- **Publicera *resurs* -http/1.1** Hämta den angivna resursen och skicka kopplade inmatade till HTTP-servern
- **Head- *resurs* http/1.1** Behandlas som en GET men inte innehåll returneras av HTTP-servern
- **Lägg till *resurs* http/1.1** Placera resurs på HTTP-Server
- **Ta bort *resurs* http/1.1** Ta bort resurs på servern

Dessa ASCII-kommandon genereras internt av webbläsare och NetX-webb-HTTP-klient tjänsterna för att utföra HTTP-åtgärder med en HTTP-server.

Observera att HTTP-klientprogrammet ska använda port 80 eller port 443 om HTTPS används. Både klient-och Server-HTTP-API: erna tar porten som en parameter – makron NX_WEB_HTTP_SERVER_PORT (port 80) och NX_WEB_HTTPS_SERVER_PORT (port 443) definieras för bekvämligheten. HTTP-Server porten kan också ändras vid körning med hjälp av tjänsten *nx_web_http_client_set_connect_port ()* . Mer information om den här tjänsten finns i kapitel 4.

## <a name="http-server-responses"></a>Svar på HTTP-Server

HTTP-servern använder samma *välkända TCP-port 80 (443 för https)* för att skicka klient kommando svar. När HTTP-servern bearbetar klient kommandot returneras en ASCII-svarskod som innehåller en tresiffrig numerisk status kod. Det numeriska svaret används av HTTP-klientens program vara för att avgöra om åtgärden lyckades eller misslyckades. Nedan visas en lista över olika HTTP-server svar på klient kommandon:

- **200** begäran har slutförts
- **400** -begäran har inte formaterats korrekt
- **401** obehörig begäran, klienten måste skicka autentisering
- Det gick inte att hitta den angivna resursen i **404**
- **500** internt http-server fel
- **501** -begäran har inte implementerats av HTTP-servern
- **502** -tjänsten är inte tillgänglig

Till exempel är en lyckad klientbegäran att skicka filen "test.htm" svars med meddelandet "HTTP/1.1 200 OK".

## <a name="http-communication"></a>HTTP-kommunikation

Som tidigare nämnts använder HTTP-servern den *välkända TCP-porten 80 (443 för https)* till fält klient begär Anden. HTTP-klienter kan använda alla tillgängliga TCP-portar för utgående anslutningar. Den allmänna sekvensen av HTTP-händelser är följande:

**Http GET-begäran**:

1. Klient problem TCP Connect to server port 80 (eller 443 för HTTPS).
1. Om HTTPS används följs TCP-anslutningen av en TLS-handskakning för att autentisera servern och upprätta en säker kanal.
1. Klienten skickar begäran om att **få *resurs* -http/1.1**(tillsammans med annan rubrik information).
1. Servern skapar ett "**http/1.1 200 OK"-** meddelande med ytterligare information som omedelbart följs av resurs innehållet (om det finns några).
1. Servern kopplar från klienten (TLS stängs av om HTTPS används).
1. Klienten kopplar från socketen (TLS stängs av efter från kopplings aviseringen från servern).

**Http-begäran**:

1. Klient problem TCP Connect to server port 80 (eller 443).
1. Om HTTPS används följs TCP-anslutningen av en TLS-handskakning för att autentisera servern och upprätta en säker kanal.
1. Klienten skickar begäran "placera resurs HTTP/1.1", tillsammans med annan rubrik information och följt av resurs innehållet.
1. Servern skapar ett "HTTP/1.1 200 OK"-meddelande med ytterligare information som direkt åtföljs av resurs innehållet.
1. Servern utför en från koppling.
1. Klienten utför en från koppling.

> [!NOTE]
> Som tidigare nämnts kan HTTP-servern ändra standard anslutnings porten (80 eller 443) vid körning till en annan port med hjälp av *nx_web_http_client_set_connect_port ()* för webb servrar som använder alternativa portar för att ansluta till klienter.

## <a name="http-authentication"></a>HTTP-autentisering

HTTP-autentisering är valfritt och krävs inte för alla webb förfrågningar. Det finns två varianter-autentisering, nämligen *Basic* och *Digest*. Grundläggande autentisering motsvarar autentisering med *namn* och *lösen ord* som finns i många protokoll. I HTTP Basic-autentisering sammanfogas namn och lösen ord och kodas i base64-format. Den största nack delen med grundläggande autentisering är att namnet och lösen ordet skickas på ett öppet sätt i begäran. Detta gör det något enkelt för namn och lösen ord att bli stulen. Digest-autentisering löser problemet genom att aldrig skicka namnet och lösen ordet i begäran. I stället används en algoritm för att härleda en 128-bitars Digest från namnet, lösen ordet och annan information. NetX webb-HTTP-Server stöder standardalgoritmen för MD5-sammandrag.

När krävs autentisering? HTTP-servern bestämmer om en begärd resurs kräver autentisering. Om autentisering krävs och klientbegäran inte inkluderade rätt autentisering, skickas "HTTP/1.1 401 oauktoriserad" svar med den typ av autentisering som krävs skickas till klienten. Klienten förväntas sedan skapa en ny begäran med korrekt autentisering.

När HTTPS används kan HTTPS-servern fortfarande använda HTTP-autentisering. I det här fallet används TLS för att kryptera all HTTP-trafik så att användningen av *grundläggande* http-autentisering inte utgör en säkerhets risk. *Sammanfattad* autentisering tillåts också, men ger ingen betydande säkerhets förbättring för grundläggande autentisering över TLS.

## <a name="http-authentication-callback"></a>Motanrop för HTTP-autentisering

Som tidigare nämnts är HTTP-autentisering valfritt och krävs inte för alla webb överföringar. Dessutom är autentiseringen vanligt vis resurs beroende. Åtkomst till vissa resurser på servern kräver autentisering, medan andra inte gör det. NetX Web HTTP server-paketet gör att programmet kan ange (via ***nx_web_http_server_create*** -anrop) en rutin för autentisering av motringning som anropas i början av hantering av varje http-klientbegäran.

Återanrops rutinen tillhandahåller NetX webb-HTTP-server med användar namn, lösen ord och sfär-strängar som är associerade med resursen och returnerar den typ av autentisering som krävs. Om ingen autentisering krävs för resursen ska återanropet av autentiseringen returnera värdet för **NX_WEB_HTTP_DONT_AUTHENTICATE**. Annars, om grundläggande autentisering krävs för den angivna resursen, bör rutinen returnera **NX_WEB_HTTP_BASIC_AUTHENTICATE**. Slutligen, om MD5 Digest-autentisering krävs, bör återanrops rutinen returnera **NX_WEB_HTTP_DIGEST_AUTHENTICATE**. Om ingen autentisering krävs för någon resurs som tillhandahålls av HTTP-servern behövs inte återanropet och en NULL-pekare kan ges till HTTP-servern för att skapa samtal.

Formatet på appen för att autentisera återanrop är mycket enkelt och definieras nedan:

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

Indataparametrarna definieras enligt följande:

- **request_type** Anger HTTP-klientbegäran, giltiga begär Anden definieras som:
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **resurs** Angiven resurs har begärts.
- **namn** Mål för pekaren till det begärda användar namnet.
- **lösen ord** Destination för pekaren till det lösen ord som krävs.
- **sfär** Mål för pekaren till sfären för den här autentiseringen.

Returvärdet för autentiseringsmetoden anger om autentisering krävs. namn, lösen ord och domän pekare används inte om **NX_WEB_HTTP_DONT_AUTHENTICATE** returneras av rutinen för återanrop av autentisering. Annars måste HTTP-serverns utvecklare se till att **NX_WEB_HTTP_MAX_USERNAME** och **NX_WEB_HTTP_MAX_PASSWORD** som definieras i *nx_web_http_server. h* är tillräckligt stora för det användar namn och lösen ord som anges i återanropet för autentisering. Båda har en standard storlek på 20 tecken.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP ogiltigt användar namn/lösen ord för motringning

Det valfria ogiltigt lösen ord för användar namn/lösen ord i NetX webb-HTTP-server anropas om HTTP-servern får en ogiltig kombination av användar namn och lösen ord i en klientbegäran. Om HTTP-serverprogrammet registrerar ett återanrop med HTTP-servern, anropas det om antingen Basic-eller Digest-autentisering Miss lyckas *i nx_web_http_server_get_process ()*, i *nx_web_http_server_put_process ()* eller *i nx_web_http_server_delete_process ().*

För att registrera ett återanrop med HTTP-servern definieras följande tjänst för NetX-webb-HTTP-servern.

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

Förfrågnings typerna definieras enligt följande:

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP-infoga GMT-datum huvud återanrop

Det finns ett valfritt motanrop i NetX webb-HTTP-server för att infoga en datum rubrik i dess svarsmeddelanden. Detta motanrop anropas när HTTP-servern svarar på en skicka-eller GET-begäran

För att registrera ett GMT-datum återanrop med HTTP-servern definieras följande tjänst.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

Data typen NX_WEB_HTTP_SERVER_DATE definieras enligt följande:

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

## <a name="http-cache-info-get-callback"></a>HTTP cache-information Hämta motringning

HTTP-servern har ett återanrop för att begära högsta ålder och datum från HTTP-programmet för en specifik resurs. Den här informationen används för att avgöra om HTTP-servern skickar en hel sida som svar på en klient GET-begäran. Om den "om det har ändrats sedan" i klientbegäran inte hittas eller inte matchar datumet "senast ändrad" som returnerades av Get cache-återanropet, skickas hela sidan.

Följande tjänst definieras för att registrera återanropet med HTTP-servern:

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>Stöd för kodning av HTTP-segmenterad överföring

När den totala längden för HTTP-meddelanden inte kan fastställas innan du skickar den, kan du använda funktionen för Chunked Transfer-kodning för att skicka meddelanden som en serie segment utan rubrik fältet Content-Length. Den här funktionen stöds i alla HTTP-begäranden och svarsmeddelanden. Som mottagare stöds den här funktionen och segment huvudet bearbetas transparent med intern logik. Som avsändare måste API- *nx_web_http_client_request_chunked_set* och *nx_web_http_server_response_chunked_set* anropas av klienten respektive servern.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

Mer information om dessa tjänster finns i beskrivningarna i kapitel 3 "Beskrivning av HTTP-tjänster".

## <a name="http-multipart-support"></a>Stöd för HTTP-multipart

Multipurpose Internet Mail Extensions (MIME) ursprungligen avsåg SMTP-protokollet, men dess användning har spridit till HTTP. MIME tillåter meddelanden som innehåller blandade meddelande typer (t. ex. image/jpg och text/plain) i samma meddelande. NetX-webb-HTTP-servern har tjänster för att fastställa innehålls typ i HTTP-meddelanden som innehåller MIME från klienten. Om du vill aktivera stöd för HTTP-multipart och använda dessa tjänster måste konfigurations alternativet **NX_WEB_HTTP_MULTIPART_ENABLE** definieras.

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

Mer information om hur du använder dessa tjänster finns i beskrivningen i kapitel 3 "Beskrivning av HTTP-tjänster".

## <a name="http-multi-thread-support"></a>Stöd för HTTP multi-threading

NetX webb-HTTP-klienttjänster kan anropas från flera trådar samtidigt. Läs-eller Skriv begär Anden för en viss HTTP-klient måste dock göras i följd från samma tråd.

Om du använder HTTPS kan NetX webb-HTTP-klienter anropas från flera trådar, men på grund av ökad komplexitet för de underliggande TLS-funktionerna bör varje tråd ha en enda, oberoende HTTP-klient instans (NX_WEB_HTTP_CLIENT kontroll struktur).

## <a name="http-rfcs"></a>HTTP-RFC

NetX webb-HTTP är kompatibel med RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2616 "Hypertext Transfer Protocol-HTTP/1.1", RFC 2581 "TCP överbelastnings kontroll", RFC 1122 "krav för Internet värdar" och relaterade RFC: er.

NetX webb-HTTP är kompatibel med RFC 2818 "HTTP över TLS" för HTTPS.
