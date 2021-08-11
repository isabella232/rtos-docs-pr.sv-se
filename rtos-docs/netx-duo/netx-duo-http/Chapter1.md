---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo HTTP
description: I det här kapitlet introduceras Azure RTOS HTTP-modulen för NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45f35f2c1bec142e10d29eedb6e5a88a8eb74771e5d4adf1d85b04a87ad59ab7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796216"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-http"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo HTTP

Http Hypertext Transfer Protocol (Http) är ett protokoll som utformats för att överföra innehåll på webben. HTTP är ett enkelt protokoll som använder tillförlitliga Transmission Control Protocol tjänster (TCP) för att utföra sin innehållsöverföringsfunktion. På grund av detta är HTTP ett mycket tillförlitligt protokoll för innehållsöverföring. HTTP är ett av de mest använda programprotokollen. Alla åtgärder på webben använder HTTP-protokollet. Azure RTOS NetX Duo HTTP kan hantera både IPv4- och IPv6-nätverk. IPv6 ändrar inte HTTP-protokollet direkt, även om vissa ändringar i den ursprungliga Azure RTOS NetX HTTP API krävs för att hantera IPv6 och beskrivs i det här dokumentet.

## <a name="http-requirements"></a>HTTP-krav

För att fungera korrekt kräver NetX Duo HTTP-paketet att en NetX Duo (version 5.2 eller senare) är installerad. Dessutom måste en IP-instans redan skapas och TCP måste aktiveras på samma IP-instans. Ett IPv6-värdprogram måste ange sin länk till en lokal och global IPv6-adress med hjälp av IPv6-API:et och/eller DHCPv6. Demofilen i avsnittet "Small Example System" i **kapitel 2** visar hur detta görs.

HTTP-klientdelen av NETX Duo HTTP-paketet har inga ytterligare krav.

HTTP Server-delen av NetX Duo HTTP-paketet har flera ytterligare krav. För det första krävs fullständig åtkomst till DEN välkända TCP-porten 80 för hantering av alla HTTP-klientbegäranden. HTTP-servern är också utformad för användning med filbäddat filsystem. Om FileX inte är tillgängligt kan användaren porta de delar av FileX som används i deras egen miljö. Detta beskrivs i senare avsnitt i den här guiden.

## <a name="http-constraints"></a>HTTP-begränsningar

HTTP-protokollet NetX Duo implementerar HTTP 1.0-standarden. Det finns dock följande begränsningar:

1.  Beständiga anslutningar stöds inte
2.  Pipelining för förfrågningar stöds inte
3.  HTTP-servern stöder både grundläggande och MD5-sammanfattad autentisering, men inte MD5-sess. För närvarande stöder HTTP-klienten endast grundläggande autentisering.
4.  Ingen innehållskomprimering stöds.
5.  SPÅRNINGS-, OPTIONS- och CONNECT-begäranden stöds inte.
6.  Paketpoolen som är associerad med HTTP-servern eller klienten måste vara tillräckligt stor för att innehålla det fullständiga HTTP-huvudet.
7.  HTTP-klienttjänster är endast för innehållsöverföring – det finns inga visningsverktyg i det här paketet.

## <a name="http-url-resource-names"></a>HTTP-URL (resursnamn)

HTTP-protokollet är utformat för att överföra innehåll på webben. Det begärda innehållet anges av Universal Resource Locator (URL). Det här är den primära komponenten i varje HTTP-begäran. URL:er börjar alltid med *ett "/"-tecken* och motsvarar vanligtvis filer på HTTP-servern. Vanliga HTTP-filnamnstillägg visas nedan:

| Anknytning | Innebörd |
| --------- | ------- |
| .htm (eller .html) | HTML (HyperText Markup Language) |
| .txt | Oformaterad ASCII-text |
| .gif | Binär GIF-bild |
| .xbm | Bild av binär Xbitmap |

## <a name="http-client-requests"></a>HTTP-klientbegäranden

HTTP har en enkel mekanism för att begära webbinnehåll. Det finns i princip en uppsättning standard-HTTP-kommandon som utfärdas av klienten när en anslutning har upprättats på den välkända *TCP-porten 80.* Nedan visas några av de grundläggande HTTP-kommandona:

| HTTP-kommando | Innebörd |
| ------------ | ------- |
| GET resource HTTP/1.0 | *Hämta den angivna resursen* |
| POST-resurs HTTP/1.0 | *Hämta den angivna resursen och skicka anslutna indata till HTTP-server* |
| HEAD-resursen HTTP/1.0 | *Behandlas som en GET men inte innehåll returneras av HTTP-servern* |
| PUT-resursen HTTP/1.0 | *Placera resurs på HTTP-server* |
| DELETE resource HTTP/1.0 | *Ta bort resurs på servern* |

Dessa ASCII-kommandon genereras internt av webbläsare och NetX HTTP-klienttjänster för att utföra HTTP-åtgärder med en HTTP-server.

> [!NOTE]
> HTTP-klientprogrammet använder som standard anslutningsporten 80. Den kan dock ändra anslutningsporten till HTTP-servern vid körning med hjälp av nx_http_client_set_connect_port tjänsten. Mer information om den här tjänsten finns i kapitel 4. Detta är för att hantera webbservrar som ibland använder alternativa portar för klientanslutningar.

## <a name="http-server-responses"></a>HTTP-serversvar

HTTP-servern använder samma välkända *TCP-port 80 för att* skicka klientkommandosvar. När HTTP-servern bearbetar klientkommandot returneras en ASCII-svarssträng som innehåller en 3-siffrig numerisk statuskod. Det numeriska svaret används av HTTP-klientprogrammet för att avgöra om åtgärden lyckades eller misslyckades. Här följer en lista över olika HTTP-serversvar på klientkommandon:

| Numeriskt fält | Innebörd |
| ------------- | ------- |
| *200* | *Begäran lyckades* |
| *400* |   *Begäran skapades inte korrekt* |
| *401* | *Obehörig begäran, klienten måste skicka autentisering* |
| *404* | *Den angivna resursen i begäran hittades inte* |
| *500* | *Internt HTTP-serverfel* |
| *501* | *Begäran implementeras inte av HTTP Server* |
| *502* | *Tjänsten är inte tillgänglig* |

En lyckad klientbegäran till PUT-filen "test.htm" besvaras till exempel med meddelandet "HTTP/1.0 200 OK".

## <a name="http-communication"></a>HTTP-kommunikation

Som tidigare nämnts använder HTTP-servern den välkända TCP-port 80 för att ange klientbegäranden. HTTP-klienter kan använda alla tillgängliga TCP-portar. Den allmänna sekvensen för HTTP-händelser är följande:

### <a name="http-get-request"></a>HTTP GET-begäran:

1.  Klientproblem TCP-anslutning till serverport 80.
2.  Klienten skickar EN **HTTP/1.0-begäran** för GET-resursen (tillsammans med annan huvudinformation).
3.  Servern skapar ett **"HTTP/1.0 200** OK"-meddelande med ytterligare information följt av resursinnehållet (om sådant finns).
4.  Servern utför en frånkoppling.
5.  Klienten utför en frånkoppling.

### <a name="http-put-request"></a>HTTP PUT-begäran:

1.  Klientproblem TCP-anslutning till serverport 80.
2.  Klienten skickar **PUT-resursens HTTP/1.0-begäran,** tillsammans med annan rubrikinformation och därefter resursinnehållet.
3.  Servern skapar ett **"HTTP/1.0 200** OK"-meddelande med ytterligare information följt av resursinnehållet.
4.  Servern utför en frånkoppling.
5.  Klienten utför en frånkoppling.

> [!NOTE]
>Som tidigare nämnts kan HTTP-klienten ändra standardporten för anslutning från 80 till en annan port med *hjälp av nx_http_client_set_connect_port* för webbservrar som använder alternativa portar för att ansluta till klienter.

## <a name="http-authentication"></a>HTTP-autentisering

HTTP-autentisering är valfritt och krävs inte för alla webbförfrågningar. Det finns två varianter av autentisering, nämligen grundläggande och sammanfattad. Grundläggande autentisering motsvarar namn- och lösenordsautentisering som finns i många protokoll. I grundläggande HTTP-autentisering sammanfogas namn och lösenord och kodas i base64-format. Den största nackdelen med grundläggande autentisering är att namn och lösenord överförs öppet i begäran. Det gör det lite enkelt att stjäla namn och lösenord. Sammanfattad autentisering löser det här problemet genom att aldrig överföra namn och lösenord i begäran. I stället används en algoritm för att härleda en 128-bitars nyckel eller sammanfatta från namn, lösenord och annan information. NetX HTTP-servern har stöd för standard-MD5-sammanfattande algoritm.

När krävs autentisering? HTTP-servern avgör i princip om en begärd resurs kräver autentisering. Om autentisering krävs och klientbegäran inte innehåller rätt autentisering skickas svaret "HTTP/1.0 401 Unauthorized" med den typ av autentisering som krävs till klienten. Klienten förväntas sedan skapa en ny begäran med rätt autentisering.

## <a name="http-authentication-callback"></a>Återanrop för HTTP-autentisering

Som tidigare nämnts är HTTP-autentisering valfritt och krävs inte för alla weböverföringar. Dessutom är autentisering vanligtvis resursberoende. Åtkomst till vissa resurser på servern kräver autentisering, medan andra inte gör det. Med NetX HTTP Server-paketet kan programmet  (via nx_http_server_create-anropet) ange en rutin för autentiseringsanrop som anropas i början av hanteringen av varje HTTP-klientbegäran.

Motringningsmetoden ger NetX HTTP-servern användarnamn, lösenord och sfärsträngar som är associerade med resursen och returnerar den typ av autentisering som krävs. Om ingen autentisering krävs för resursen ska återanropet av autentisering returnera värdet för **NX_HTTP_DONT_AUTHENTICATE**. Annars, om grundläggande autentisering krävs för den angivna resursen, ska rutinen returnera **NX_HTTP_BASIC_AUTHENTICATE**. Och slutligen, om sammanfattad MD5-autentisering krävs ska återanropsrutinen returnera **NX_HTTP_DIGEST_AUTHENTICATE**. Om ingen autentisering krävs för en resurs som tillhandahålls av HTTP-servern behövs inte motringning och en NULL-pekare kan anges för HTTP-serverns skapa-anrop.

Formatet för programmet autentiserar motringning är mycket enkelt och definieras nedan:

```c
UINT nx_http_server_authentication_check(NX_HTTP_SERVER *server_ptr,
                                          UINT request_type, CHAR *resource,
                                          CHAR **name, CHAR **password,
                                          CHAR **realm);
```
Indataparametrarna definieras på följande sätt:

| Parameter | Innebörd |
| --------- | --------|
| *request_type* | Anger HTTP-klientbegäran, giltiga begäranden definieras som: <br/> **NX_HTTP_SERVER_GET_REQUEST**<br/>**NX_HTTP_SERVER_POST_REQUEST**<br/>**NX_HTTP_SERVER_HEAD_REQUEST**<br/>**NX_HTTP_SERVER_PUT_REQUEST**<br/>**NX_HTTP_SERVER_DELETE_REQUEST** |
| *resource* | Specifik resurs som begärdes. |
| *Namn* | Mål för pekaren till det användarnamn som krävs. |
| *lösenord* | Mål för pekaren till det lösenord som krävs. |
| *Sfären* | Mål för pekaren till sfären för den här autentiseringen. |

Returvärdet för autentiseringsrutinen anger om autentisering krävs. ```name, password, and realm``` pekare används inte om NX_HTTP_DONT_AUTHENTICATE **returneras** av autentiseringsrutinen för återanrop. Annars måste HTTP-serverutvecklaren se **till att NX_HTTP_MAX_USERNAME** och **NX_HTTP_MAX_PASSWORD** som definierats *i nxd_http_server.h* är tillräckligt stora för användarnamnet och lösenordet som anges i autentiseringsanropet. Båda har storleken 20 tecken som standard.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP ogiltigt användarnamn/återanrop av lösenord

Det valfria ogiltiga återanropet av användarnamn/lösenord i NetX HTTP Server anropas om HTTP-servern får en ogiltig kombination av användarnamn och lösenord i en klientbegäran. Om HTTP-serverprogrammet registrerar ett återanrop med HTTP-servern anropas det om antingen grundläggande eller sammanfattad autentisering misslyckas i *nx_http_server_get_process*, *i nx_http_server_put_process* eller i *nx_http_server_delete_process*.

För att registrera ett återanrop med HTTP-servern definieras följande tjänst i NetX Duo HTTP Server.

```c
UINT nx_http_server_invalid_userpassword_notify_set(
                   NX_HTTP_SERVER *http_server_ptr,
                   UINT *invalid_username_password_callback)
                            (CHAR *resource,
                             NXD_ADDRESS *client_nxd_address,
                             UINT request_type))
```

Begärandetyperna definieras på följande sätt:
 - **NX_HTTP_SERVER_GET_REQUEST**
 - **NX_HTTP_SERVER_POST_REQUEST**
 - **NX_HTTP_SERVER_HEAD_REQUEST**
 - **NX_HTTP_SERVER_PUT_REQUEST**
 - **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP Insert GMT Date Header Callback

Det finns ett valfritt återanrop i NetX Duo HTTP Server för att infoga en datumrubrik i svarsmeddelandena. Det här återanropet anropas när HTTP-servern svarar på en put- eller get-begäran

Det finns ett valfritt återanrop i NetX Duo HTTP Server för att infoga en datumrubrik i svarsmeddelandena. Det här återanropet anropas när HTTP-servern svarar på en put- eller get-begäran

För att registrera ett GMT-datumanrop med HTTP-servern definieras följande tjänst i NetX Duo HTTP-servern.

```c
UINT  _nx_http_server_gmt_callback_set(
                    NX_HTTP_SERVER *server_ptr,
                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date)
```

Datatypen NX_HTTP_SERVER_DATE definieras på följande sätt:

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT          nx_http_server_year;           /* Year                 */
    UCHAR           nx_http_server_month;          /* Month                */
    UCHAR           nx_http_server_day;            /* Day                  */
    UCHAR           nx_http_server_hour;           /* Hour              */
    UCHAR           nx_http_server_minute;         /* Minute               */
    UCHAR           nx_http_server_second;         /* Second               */
    UCHAR           nx_http_server_weekday;        /* Weekday              */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP Cache Info Get Callback

HTTP-servern har ett återanrop för att begära högsta ålder och datum från HTTP-programmet för en specifik resurs. Den här informationen används för att avgöra om HTTP-servern skickar hela sidan som svar på en Client Get-begäran. Om "if modified since" i klientbegäran inte hittas eller inte matchar datumet för senaste ändring som returnerades av get cache-återanropet, skickas hela sidan.

För att registrera motringning med HTTP-servern definieras följande tjänst:

```c
UINT  _nx_http_server_cache_info_callback_set(
                              NX_HTTP_SERVER *server_ptr,
                              UINT (*cache_info_get)
                                    (CHAR *, UINT *, NX_HTTP_SERVER_DATE *))
```

## <a name="http-multipart-support"></a>HTTP-stöd för flera delar

Multipurpose Internet Mail Extensions (MIME) var ursprungligen avsett för SMTP-protokollet, men dess användning har spridits till HTTP. MIME gör att meddelanden kan innehålla blandade meddelandetyper (t.ex. bild/jpg och text/oformaterad) i samma meddelande. NetX Duo HTTP Server har lagt till tjänster för att fastställa innehållstyp i HTTP-meddelanden som innehåller MIME från klienten. Om du vill aktivera stöd för HTTP med flera delar och använda dessa **tjänster NX_HTTP_MULTIPART_ENABLE** konfigurationsalternativet definieras.

```c
UINT  nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       UCHAR *entity_header_buffer,
                                       ULONG buffer_size);

UINT  nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_pptr,
                                        ULONG *available_offset,
                                        ULONG *available_length)
```

Mer information om användningen av dessa tjänster finns i beskrivningen i kapitel 3 "Beskrivning av HTTP-tjänster".

## <a name="http-multi-thread-support"></a>HTTP-stöd för flera trådar

NetX HTTP-klienttjänsterna kan anropas från flera trådar samtidigt. Läs- eller skrivbegäranden för en viss HTTP-klientinstans bör dock göras i följd från samma tråd.

## <a name="http-rfcs"></a>HTTP-RFC

NetX HTTP är kompatibel med RFC1945 "Hypertext Transfer Protocol/1.0, RFC 2581 "TCP Congestion Control", RFC 1122 "Krav för Internetvärdar" och relaterade RFC: er.
