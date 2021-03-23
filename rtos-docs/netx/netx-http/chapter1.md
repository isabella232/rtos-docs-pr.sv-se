---
title: Kapitel 1 – Introduktion till NetX HTTP
description: I det här dokumentet beskrivs hur HTTP är ett protokoll som har utformats för att överföra innehåll på webben.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826718"
---
# <a name="chapter-1---introduction-to-netx-http"></a>Kapitel 1 – Introduktion till NetX HTTP

Hypertext Transfer Protocol (HTTP) är ett protokoll som har utformats för att överföra innehåll på webben. HTTP är ett enkelt protokoll som använder Reliable Transmission Control Protocol (TCP)-tjänster för att utföra sin innehålls överförings funktion. Därför är HTTP ett mycket tillförlitligt innehålls överförings protokoll. HTTP är ett av de mest använda program protokollen. Alla åtgärder på webben använder HTTP-protokollet.

## <a name="http-requirements"></a>HTTP-krav

För att kunna fungera korrekt kräver HTTP-paketet NetX att en NetX (version 5,2 eller senare) är installerad. Dessutom måste en IP-instans redan skapas och TCP måste vara aktiverat på samma IP-instans. Demo filen i avsnittet "litet exempel system" i **kapitel 2** visar hur detta görs.

HTTP-klient delen av NetX HTTP-paketet har inga ytterligare krav.

HTTP-server delen av NetX HTTP-paketet har flera ytterligare krav. Först måste du ha fullständig åtkomst till den *välkända TCP-porten 80* för att hantera alla klient-HTTP-begäranden. HTTP-servern är också avsedd att användas med det inbäddade fil systemet FileX. Om FileX inte är tillgängligt kan användaren hamna i de delar av FileX som används i sin egen miljö. Detta beskrivs i senare avsnitt i den här hand boken.

## <a name="http-constraints"></a>HTTP-begränsningar 

NetX HTTP-protokollet implementerar HTTP 1,0-standarden. Det finns dock följande begränsningar:

1.  Beständiga anslutningar stöds inte

2.  Pipelining för begäran stöds inte

3.  HTTP-servern stöder både Basic-och MD5 Digest-autentisering, men inte MD5-sess. HTTP-klienten har nu bara stöd för grundläggande autentisering.

4.  Det finns inte stöd för innehålls komprimering.

5.  SPÅRNINGs-, alternativ-och ANSLUTNINGS begär Anden stöds inte.

6.  Den modempool som är kopplad till HTTP-servern eller-klienten måste vara tillräckligt stor för att rymma det fullständiga HTTP-huvudet.

7.  HTTP-klienttjänster är endast för innehålls överföring – det finns inga visnings verktyg i det här paketet.

## <a name="http-url-resource-names"></a>HTTP-URL (resurs namn)

HTTP-protokollet är utformat för att överföra innehåll på webben. Det begärda innehållet anges av URL: en (Universal Resource Locator). Detta är den primära komponenten i varje HTTP-begäran. URL: er börjar alltid med ett "/"-Character och motsvarar vanligt vis filer på HTTP-servern. Vanliga HTTP-filtillägg visas nedan:

- **. htm (eller. html)** Hypertext Markup Language (HTML)
- **. txt** Oformaterad ASCII-text
- **. gif** Binär GIF-bild
- **. XBM** Binär Xbitmap-avbildning

## <a name="http-client-requests"></a>HTTP-klient begär Anden

HTTP har en enkel mekanism för att begära webb innehåll. Det finns i princip en uppsättning standard-HTTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den *välkända TCP-porten 80*. Nedan visas några av de grundläggande HTTP-kommandona:

- Hämta resurs HTTP/1.0 *Hämta den angivna resursen*
- PUBLICERA resurs HTTP/1.0 *Hämta den angivna resursen och skicka kopplade indata till HTTP-servern*
- HUVUD resurs-HTTP/1.0, *som behandlas som en get men inte innehåll, returneras av HTTP-servern*
- Placera resurs-HTTP/1.0-resurs *på HTTP-server*
- TA bort resurs HTTP/1.0 *ta bort resurs på servern*

Dessa ASCII-kommandon genereras internt av webbläsare och NetX HTTP-klienttjänster för att utföra HTTP-åtgärder med en HTTP-server.

>[!NOTE] 
> HTTP-klientens program som standard till Connect-porten 80. Det kan dock ändra anslutnings porten till HTTP-servern vid körning med hjälp av tjänsten *nx_http_client_set_connect_port* . Mer information om den här tjänsten finns i kapitel 4. Detta är att hantera webb servrar som ibland använder alternativa portar för klient anslutningar.

## <a name="http-server-responses"></a>Svar på HTTP-Server

HTTP-servern använder samma *välkända TCP-port 80* för att skicka svar på klient kommandon. När HTTP-servern bearbetar klient kommandot returneras en ASCII-svarskod som innehåller en tresiffrig numerisk status kod. Det numeriska svaret används av HTTP-klientens program vara för att avgöra om åtgärden lyckades eller misslyckades. Nedan visas en lista över olika HTTP-server svar på klient kommandon:

- 200 *begäran har slutförts*
- 400- *begäran har inte formaterats korrekt*
- 401 *obehörig begäran, klienten måste skicka autentisering*
- det *gick inte att hitta den angivna resursen i* 404
- 500 *internt HTTP-server fel*
- 501 *-begäran har inte implementerats av HTTP-servern*
- 502 *-tjänsten är inte tillgänglig*

Till exempel är en lyckad klientbegäran att skicka filen "test.htm" svars med meddelandet "HTTP/1.0 200 OK".

## <a name="http-communication"></a>HTTP-kommunikation

Som tidigare nämnts använder HTTP-servern den *välkända TCP-port 80* för fält klient begär Anden. HTTP-klienter kan använda alla tillgängliga TCP-portar. Den allmänna sekvensen av HTTP-händelser är följande:

**Http GET-begäran**:

1.  Klient problem TCP Anslut till server port 80.

2.  Klienten skickar begäran om att **få resurs-http/1.0**(tillsammans med annan rubrik information).

3.  Servern skapar ett "**http/1.0 200 OK"-** meddelande med ytterligare information som omedelbart följs av resurs innehållet (om det finns några).

4.  Servern utför en från koppling.

5.  Klienten utför en från koppling.

**Http-begäran**:

1. Klient problem TCP Anslut till server port 80.

2. Klienten skickar begäran "**Placera resurs http/1.0**", tillsammans med annan rubrik information och följt av resurs innehållet.

3. Servern skapar ett "**http/1.0 200 OK"-** meddelande med ytterligare information som direkt åtföljs av resurs innehållet.

4. Servern utför en från koppling.

5. Klienten utför en från koppling.

>[!NOTE] 
> Som tidigare nämnts kan HTTP-klienten ändra standard anslutnings porten från 80 till en annan port med hjälp av *nx_http_client_set_connect_port* för webb servrar som använder alternativa portar för att ansluta till klienter.

## <a name="http-authentication"></a>HTTP-autentisering

HTTP-autentisering är valfritt och krävs inte för alla webb förfrågningar. Det finns två varianter-autentisering, nämligen *Basic* och *Digest*. Grundläggande autentisering motsvarar autentisering med *namn* och *lösen ord* som finns i många protokoll. I HTTP Basic-autentisering sammanfogas namn och lösen ord och kodas i base64-format. Den största nack delen med grundläggande autentisering är att namnet och lösen ordet skickas på ett öppet sätt i begäran. Detta gör det något enkelt för namn och lösen ord att bli stulen. Digest-autentisering löser problemet genom att aldrig skicka namnet och lösen ordet i begäran. I stället används en algoritm för att härleda en 128-bitars nyckel eller sammanfattad från namnet, lösen ordet och annan information. NetX HTTP-Server stöder standardalgoritmen för MD5-sammandrag.

När krävs autentisering? I princip avgör HTTP-servern om en begärd resurs kräver autentisering. Om autentisering krävs och klientbegäran inte inkluderade rätt autentisering, skickas svars tiden "HTTP/1.0 401" med den typ av autentisering som krävs skickas till klienten. Klienten förväntas sedan skapa en ny begäran med korrekt autentisering.

## <a name="http-authentication-callback"></a>Motanrop för HTTP-autentisering

Som tidigare nämnts är HTTP-autentisering valfritt och krävs inte för alla webb överföringar. Dessutom är autentiseringen vanligt vis resurs beroende. Åtkomst till vissa resurser på servern kräver autentisering, medan andra inte gör det. HTTP-NetX gör det möjligt för programmet att ange (via ***nx_http_server_create*** -anrop) en rutin för motringning av autentisering som anropas i början av hantering av varje http-klientbegäran.

Återanrops rutinen tillhandahåller NetX HTTP-servern med användar namnet, lösen ordet och sfär strängarna som är kopplade till resursen och returnerar den typ av autentisering som krävs. Om ingen autentisering krävs för resursen ska återanropet av autentiseringen returnera värdet för **NX_HTTP_DONT_AUTHENTICATE**. Annars, om grundläggande autentisering krävs för den angivna resursen, bör rutinen returnera **NX_HTTP_BASIC_AUTHENTICATE**. Slutligen, om MD5 Digest-autentisering krävs, bör återanrops rutinen returnera **NX_HTTP_DIGEST_AUTHENTICATE**. Om ingen autentisering krävs för någon resurs som tillhandahålls av HTTP-servern behövs inte återanropet och en NULL-pekare kan anges för HTTP-servern skapa samtal.

Formatet på appen för att autentisera återanrop är mycket enkelt och definieras nedan:

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

Indataparametrarna definieras enligt följande:

- *request_type* Anger HTTP-klientbegäran, giltiga begär Anden definieras som:
  - **NX_HTTP_SERVER_GET_REQUEST**
  - **NX_HTTP_SERVER_POST_REQUEST**
  - **NX_HTTP_SERVER_HEAD_REQUEST**
  - **NX_HTTP_SERVER_PUT_REQUEST**
  - **NX_HTTP_SERVER_DELETE_REQUEST**
- *resurs* Angiven resurs har begärts.
- *namn* Mål för pekaren till det begärda användar namnet.
- *lösen ord* Destination för pekaren till det lösen ord som krävs.
- *sfär* Mål för pekaren till sfären för den här autentiseringen.

Returvärdet för autentiseringsmetoden anger om autentisering krävs. namn, lösen ord och domän pekare används inte om **NX_HTTP_DONT_AUTHENTICATE** returneras av rutinen för återanrop av autentisering. Annars måste HTTP-serverns utvecklare se till att **NX_HTTP_MAX_USERNAME** och **NX_HTTP_MAX_PASSWORD** som definieras i *nx_http_server. h* är tillräckligt stora för det användar namn och lösen ord som anges i återanropet för autentisering. Dessa är båda standardvärdena för storlek 20 tecken.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP ogiltigt användar namn/lösen ord för motringning

Det valfria ogiltigt användar namn/lösen ord för motringning i NetX HTTP-server anropas om HTTP-servern får en ogiltig kombination av användar namn och lösen ord i en klientbegäran. Om HTTP-serverprogrammet registrerar ett återanrop med HTTP-servern anropas det om antingen grundläggande eller sammanfattad autentisering Miss lyckas *i nx_http_server_get_process*, i *nx_http_server_put_process* eller *i nx_http_server_delete_process.*

För att registrera ett återanrop med HTTP-servern definieras följande tjänst i NetX HTTP-server.

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
Förfrågnings typerna definieras enligt följande:

- **NX_HTTP_SERVER_GET_REQUEST**
- **NX_HTTP_SERVER_POST_REQUEST**
- **NX_HTTP_SERVER_HEAD_REQUEST**
- **NX_HTTP_SERVER_PUT_REQUEST**
- **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP-infoga GMT-datum huvud återanrop

Det finns ett valfritt motanrop i NetX HTTP-server för att infoga en datum rubrik i dess svarsmeddelanden. Detta motanrop anropas när HTTP-servern svarar på en skicka-eller GET-begäran

För att registrera ett GMT-datum återanrop med HTTP-servern definieras följande tjänst i NetX HTTP-server.

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

Data typen NX_HTTP_SERVER_DATE definieras enligt följande:

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP cache-information Hämta motringning

HTTP-servern har ett återanrop för att begära högsta ålder och datum från HTTP-programmet för en specifik resurs. Den här informationen används för att avgöra om HTTP-servern skickar hela sidan som svar på en klient GET-begäran. Om den "om det har ändrats sedan" i klientbegäran inte hittas eller inte matchar datumet "senast ändrad" som returnerades av Get cache-återanropet, skickas hela sidan.

Följande tjänst definieras för att registrera återanropet med HTTP-servern:

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a>Stöd för HTTP-multipart

Multipurpose Internet Mail Extensions (MIME) ursprungligen avsåg SMTP-protokollet, men dess användning har spridit till HTTP. MIME tillåter meddelanden som innehåller blandade meddelande typer (t. ex. image/jpg och text/plain) i samma meddelande. NetX HTTP-server har lagt till tjänster för att fastställa innehålls typ i HTTP-meddelanden som innehåller MIME från klienten. Om du vill aktivera stöd för HTTP-multipart och använda dessa tjänster måste konfigurations alternativet **NX_HTTP_MULTIPART_ENABLE** definieras.

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

Mer information om hur du använder dessa tjänster finns i beskrivningen i kapitel 3 "Beskrivning av HTTP-tjänster".

## <a name="http-multi-thread-support"></a>Stöd för HTTP multi-threading

NetX HTTP-klienttjänster kan anropas från flera trådar samtidigt. Läs-eller Skriv begär Anden för en viss HTTP-klient måste dock göras i följd från samma tråd.

## <a name="http-rfcs"></a>HTTP-RFC

NetX HTTP är kompatibelt med RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2581 "TCP överbelastnings kontroll", RFC 1122 "krav för Internet-värdar" och relaterade RFC: er.