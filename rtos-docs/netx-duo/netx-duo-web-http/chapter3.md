---
title: Kapitel 3 – Beskrivning av HTTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX-webb-HTTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30168ad5a564b0f4c0a8c999046c5103385f4f90
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826985"
---
# <a name="chapter-3---description-of-http-services"></a>Kapitel 3 – Beskrivning av HTTP-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX-webb-HTTP-tjänster (visas nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

## <a name="http-and-https-client-api"></a>API för HTTP-och HTTPS-klient

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

Öppna en klartext-socket till en HTTP-server för anpassade begär Anden

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten öppnar en TCP-socket i klartext till en HTTP-server, men skickar inga förfrågningar. Begär Anden skapas med n *x_web_http_client_request_initialize ()* och skickas med *nx_web_http_client_request_send ()*. Anpassade HTTP-huvuden kan läggas till i begäran med hjälp av *nx_web_http_client_request_header_add ()*.

Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran. **Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.**

> [!NOTE]
> Nx_web_http_client_ * _start metoder tillhandahålls för bekvämlighet (t. ex. *nx_web_http_client_get_start*()) och hanterar genereringen av förfrågningar och socketanslutningar. Du kan använda dessa tjänster i stället för *nx_web_http_client_connect ()* och de relaterade rutinerna om du inte behöver anpassade HTTP-huvuden i dina begär Anden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **server_ip** IP-adress för fjärr-HTTP-server.
- **SERVER_PORT** Port på fjärr-HTTP-server (t. ex. 80 för HTTP).
- **wait_option** Definierar hur länge tjänsten ska vänta på underliggande nätverks åtgärder. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) anslutning av TCP-socket.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_WEB_HTTP_NOT_READY (0x3000A) en annan begäran pågår redan.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

Skapa en HTTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en HTTP-klient instans på den angivna IP-instansen. Klient instansen kan användas för antingen HTTP eller HTTPS. Se tjänsterna *nx_web_http_client_connect ()* och *nx_web_http_client_secure_connect ()* för mer information om hur du startar en HTTP-eller https-instans. Se även API: et för * nx_web_http_client_get_ * *, *nx_web_http_client_put_ * *, *nx_web_http_client_post_** för enkla anrop av get-, get-och post-metoder.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **client_name** Namn på HTTP-klient instans.
- **ip_ptr** Pekare till IP-instans.
- **pool_ptr** Pekare till standard paketets pool. Observera att paketen i den här poolen måste ha en nytto last som är tillräckligt stor för att hantera hela svars huvudet. Detta definieras av *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* i *nx_web_http_client. h*.
- **window_size** Storlek på klientens mottagnings fönster för TCP-socket.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-klienten har skapats
- NX_PTR_ERROR (0x16) ogiltig pekare för HTTP, ip_ptr eller Packet pool
- NX_WEB_HTTP_POOL_ERROR (0x30009) ogiltig nytto Last storlek i Packet bassäng

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

Ta bort en HTTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad HTTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-klientbegäran har tagits bort
- NX_PTR_ERROR (0x16) ogiltig HTTP-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

Starta en HTTP DELETE-begäran i klartext

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Detta API är föråldrat. Utvecklare uppmanas att använda *nx_web_http_client_delete_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

Starta en HTTP DELETE-begäran i klartext

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-terminerade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_delete_start* (). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

Starta en krypterad HTTPS DELETE-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_delete_secure_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen. resursen måste vara NULL-terminerad.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

Starta en krypterad HTTPS DELETE-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker skicka en begäran om borttagning av resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_delete_secure_start*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen. resursen måste vara NULL-terminerad.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat meddelande om http-klient borttagnings förfrågan
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

Starta en HTTP GET-begäran i klartext

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_get_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

Starta en HTTP GET-begäran i klartext

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-terminerade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_get_start*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

Starta en krypterad HTTPS GET-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_get_secure_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

Starta en krypterad HTTPS GET-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker hämta resursen som anges av resurs pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop till *nx_web_http_client_response_body_get ()* för att hämta data paket som motsvarar det begärda resurs innehållet.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-terminerade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_secure_start*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande om att http-klient får Start meddelande har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

Starta en HTTP HEAD-begäran med oformaterad text

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta svaret.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_head_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

Starta en HTTP HEAD-begäran med oformaterad text

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta svaret.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_head_start*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

Starta en krypterad HTTPS HEAD-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar som motsvarar det begärda resurs innehållet.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_head_secure_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

Starta en krypterad HTTPS HEAD-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "Resource"-pekaren på den tidigare skapade HTTP-serverinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get ()* för att hämta serverns svar som motsvarar det begärda resurs innehållet.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder get-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_head_secure_start*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** Port på fjärr-HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) meddelande meddelande om http-klient huvud har skickats
- **NX_WEB_HTTP_ERROR** (0X30000) internt http-klient fel
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_FAILED** (0X30002) http-klient fel vid kommunikation med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

Allokera ett HTTP (S)-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker allokera ett paket för klient-HTTP (S).

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **packet_ptr** Pekare till allokerat paket.
- **wait_option** Definierar vänte tiden i Tick om det inte finns några tillgängliga paket i modempoolen. Vänte alternativen definieras enligt följande:
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **timeout i Tick** (0X00000001 till 0xFFFFFFFE)

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket tilldelningen lyckades
- **NX_NO_PACKET** (0X01) inget tillgängligt paket
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

Starta en HTTP POST-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet* rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_post_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för resurs som ska skickas till servern.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat post-begäran
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

Starta en HTTP POST-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet* rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_post_start* (). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat post-begäran
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

Starta en krypterad HTTPS POST-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_post_secure_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för resurs som ska skickas till servern.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat post-begäran
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_post_secure_start_extended

Starta en krypterad HTTPS POST-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_post_secure_start* (). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat post-begäran
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

Starta en HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_put_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för resurs som ska skickas till servern.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat begäran om att skicka
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_put_start_extended

Starta en HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för http med **oformaterad text** .

Tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_put_start* (). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat begäran om att skicka
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

Starta en krypterad HTTPS-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_put_secure_start_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för resurs som ska skickas till servern.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat begäran om att skicka
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

Starta en krypterad HTTPS-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten försöker skicka en begäran om att skicka en begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör program koden göra efterföljande anrop till *nx_web_http_client_put_packet ()* -rutinen för att skicka resurs innehållet till http-servern.

Observera att resurs strängen kan referera till en lokal fil, t. ex. "/index.htm" eller så kan den referera till en annan URL, t. ex. `http://abc.website.com/index.htm` om HTTP-servern anger att den stöder refererande begär Anden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_put_secure_start*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **ip_address** IP-adressen för HTTP-servern.
- **SERVER_PORT** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **total_bytes** Totalt antal byte som skickas av resursen. Observera att den sammanlagda längden för alla paket som skickas via efterföljande anrop till *nx_web_http_client_put_packet ()* måste vara lika med det här värdet.
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat begäran om att skicka
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0X30012) användar namnet är för stort för bufferten
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_SIZE_ERROR (0x09) ogiltig total resurs storlek
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

Skicka nästa resurs data paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker skicka nästa paket med resurs innehåll till HTTP-servern för både åtgärderna placera och publicera. Observera att den här rutinen ska anropas upprepade gånger tills den kombinerade längden på de paket som skickas är lika med "total_bytes" som anges i föregående *nx_web_http_client_put_start ()* eller *nx_web_http_client_post_start ()* -anrop (eller motsvarande säkra versioner).

Tjänsten söker också efter ett svar från servern om det uppstod ett problem med att upprätta en HTTP-anslutning (eller HTTPS).

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **packet_ptr** Pekare till nästa innehåll i resursen som ska skickas till HTTP-servern.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skickade http-klient paketet.
- **NX_WEB_HTTP_NOT_READY** (0X3000A) http-klienten är inte klar
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0X3000E) tog emot Server fel kod * *
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) ogiltig paket längd
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0X3000B) ogiltigt namn och/eller lösen ord
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** -servern (0x3000F) svarar innan den har slutförts
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_INVALID_PACKET-paketet (0x12) är för litet för TCP-huvud
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

Ange segmenterad överföring för HTTP (S)-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten använder Chunked Transfer-kodning för att skicka en anpassad HTTP (S)-begäran till den server som anges i det *nx_web_http_client_connect ()* eller *nx_web_http_client_secure_connect ()* -anropet som tidigare har upprättat socket-anslutningen till fjärrvärden.

> [!NOTE]
> Om programmet använder Chunked Transfer-kodning för att skicka ett data paket för begäran, måste det anropa tjänsten efter att ha anropat *nx_web_http_client_request_packet_allocate*() och innan anrop *nx_web_http_client_reqeust_packet_send* ().

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **chunk_size** Storlek på segment data i oktetter.
- **packet_ptr** HTTP (a) begär data pakets pekare.

### <a name="return-values"></a>Retur värden

- Ett segment har angetts för **NX_SUCCESS** (0x00).
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT, "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

Lägg till en anpassad rubrik i en anpassad HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten lägger till en anpassad rubrik (i form av ett fält namn och värde) till en anpassad HTTP-begäran som skapats med n *x_web_http_client_request_initialize ()*.

Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran. **Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.**

> [!NOTE]
> Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull. Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize ())* för att skapa och skicka HTTP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **field_name** Fält namn sträng (t. ex. "innehålls typ").
- **name_length** Längd på fält namn sträng i byte.
- **field_value** Fält värde sträng (t. ex. "Application/oktett-Stream").
- **value_length** Värde strängens längd i byte.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) addition av sidhuvud att begära.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

Initiera en anpassad HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klient instansen. Till skillnad från de enklare *nx_web_http_client_get_start ()* (tillsammans med metoderna för att skicka, publicera och associerade säkra versioner av dessa API: er) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send ()* har anropats.

Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran med hjälp av tjänsten ***nx_web_http_client_request_header_add ()*** . Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.

> [!NOTE]
> Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull. Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_send ())* för att skapa och skicka HTTP-begäranden.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_client_request_initialize_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **metod** Den HTTP-metod för begäran som ska användas. Alternativen definieras enligt följande:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resurs** Namnet på den resurs som överförs.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **input_size** Storlek på indata för skicka och publicera. Pass 0 för andra åtgärder.
- **transfer_encoding_trunked** Reserverad parameter för framtida Trunked transfer-stöd.
- **användar namn** Användar namn för skyddade resurser.
- **lösen ord** Lösen ord för skyddade resurser.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförde initieringen av begäran.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_WEB_HTTP_METHOD_ERROR (0x30014) viss nödvändig information saknades (t. ex. input_size för placering eller POST).

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

Initiera en anpassad HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klient instansen. Till skillnad från de enklare *nx_web_http_client_get_start ()* (tillsammans med metoderna för att skicka, publicera och associerade säkra versioner av dessa API: er) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send ()* har anropats.

Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran med hjälp av tjänsten ***nx_web_http_client_request_header_add ()*** . Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.

> [!NOTE]
> Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull. Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_send ())* för att skapa och skicka HTTP-begäranden.

Strängarna för resurs, värd, användar namn och lösen ord måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_client_request_initialize*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **metod** Den HTTP-metod för begäran som ska användas. Alternativen definieras enligt följande:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resurs** Namnet på den resurs som överförs.
- **resource_length** Sträng längd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domän namn. Den här strängen överförs i fältet HTTP-värd huvud. Värd strängen får inte vara NULL.
- **host_length** Värdens sträng längd.
- **input_size** Storlek på indata för skicka och publicera. Pass 0 för andra åtgärder.
- **transfer_encoding_trunked** Reserverad parameter för framtida Trunked transfer-stöd.
- **användar namn** Pekare till valfritt användar namn för autentisering.
- **username_length** Sträng längd för användar namn för autentisering.
- **lösen ord** Pekare till valfritt lösen ord för autentisering.
- **password_length** Sträng längden för lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförde initieringen av begäran.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_WEB_HTTP_METHOD_ERROR (0x30014) viss nödvändig information saknades (t. ex. input_size för placering eller POST).

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

Skicka HTTP (S)-begäran om data paket till fjärrservern

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett anpassat HTTP (S)-begär ande data paket som skapats med *nx_web_http_client_request_packet_allocate* () till den server som anges i *nx_web_http_client_connect ()* eller *nx_web_http_client_secure_connect (*)-anropet som tidigare har upprättat socket-anslutningen till fjärrvärden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **packet_ptr** HTTP (a) begär data pakets pekare.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) skickade data paket för begäran.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

Skicka en anpassad HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar en anpassad HTTP-begäran som skapats med *nx_web_http_client_request_initialize ()* till den server som anges i *nx_web_http_client_connect ()* eller *nx_web_http_client_secure_connect ()* som tidigare har upprättat socket-anslutningen till fjärrvärden.

Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran med hjälp av tjänsten ***nx_web_http_client_request_header_add ()*** . Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.

> [!NOTE]
> Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull. Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize ())* för att skapa och skicka HTTP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades skicka begäran.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

Hämta nästa resurs data paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar nästa innehålls paket av resursen som begärdes av föregående *nx_web_http_client_get_start ()* eller *nx_web_http_client_get_secure_start ()-* anropet. Efterföljande anrop till den här rutinen bör göras tills retur statusen för NX_WEB_HTTP_GET_DONE tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **packet_ptr** Mål för paket pekare som innehåller partiellt resurs innehåll.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades Hämta http-klient paket.
- **NX_WEB_HTTP_GET_DONE** (0X3000C) http-klient hämta paket har slutförts
- **NX_WEB_HTTP_NOT_READY** (0x3000A) http-klienten är inte i get-läge.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0X3000D) ogiltig paket längd
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0X3001A) HTTP-statuskod 100 Fortsätt
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0X3001B) HTTP-statuskod 101 växlings protokoll
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0X3001C) HTTP-statuskod 201 skapades
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0X3001D) HTTP-statuskod 202 accepterades
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0X3001E) HTTP-statuskod 203 icke-auktoritativ information
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0X3001F) HTTP-statuskod 204 inget innehåll
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0X30020) HTTP-statuskod 205 Återställ innehåll
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0X30021) HTTP-statuskod 206 del av innehåll
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0X30022) HTTP-statuskod 300 flera alternativ
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0X30023) HTTP-statuskod 301 flyttades permanent
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0X30024) HTTP-statuskod 302 hittades
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0X30025) HTTP-statuskod 303 Se andra
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0X30026) HTTP-statuskod 304 har inte ändrats
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0X30027) HTTP-statuskod 305 Använd proxy
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0X30028) HTTP-statuskod 307 tillfällig omdirigering
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0X30029) HTTP-statuskod 400 Felaktig begäran
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0X3002A) HTTP-statuskod 401 obehörig
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0X3002B) HTTP-statuskod 402 betalning krävs
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0X3002C) HTTP-statuskod 403 förbjuden
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0X3002D) HTTP-statuskod 404 hittades inte
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0X3002E) HTTP-statuskod 405 metoden är inte tillåten
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0X3002F) HTTP-statuskod 406 är inte acceptabel
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP-statuskod 407 proxy-autentisering krävs
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0X30031) HTTP-statuskod 408 begäran om timeout
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0X30032) http STATUS kod 409 konflikt
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0X30033) HTTP-statuskod 410 borta
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0X30034) HTTP-statuskod 411 längd krävs
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0X30035) HTTP-statuskod 412 förhands villkor misslyckades
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0X30036) HTTP-statuskod 413 den begärda enheten är för stor
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP-statuskod 414 förfrågnings-URL: en är för stor
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0X30038) HTTP-statuskod 415 medie typen stöds inte
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0X30039) HTTP-statuskod 416 begärt intervall uppfyller inte kraven
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0X3003A) HTTP-statuskod 417 förväntades inte
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0X3003B) http STATUS kod 500 internt Server fel
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0X3003C) HTTP-statuskod 501 inte implementerad
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0X3003D) HTTP-statuskod 502 Felaktig gateway
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0X3003E) HTTP-statuskod 503 tjänsten är inte tillgänglig
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0X3003F) http STATUS kod 504 Gateway-timeout
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0X30040) HTTP-statuskod 505 http-version stöds inte
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

Ange motringning för att anropa vid bearbetning av HTTP-huvuden

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Beskrivning

Den här tjänsten tilldelar ett återanrop som ska anropas när NetX webb-HTTP-klient bearbetar ett HTTP-huvud i ett inkommande svar från en fjärr-HTTP-server. Återanropet anropas en gång för varje huvud i svaret som det bearbetas. Återanropet gör att ett HTTP-klientprogram kan komma åt vart och ett av huvudena i svaret på HTTP-servern för att vidta önskade åtgärder utöver den grundläggande bearbetning som NetX webb-HTTP-klient gör.

### <a name="input-parameters"></a>Indataparametrar

**client_ptr** Pekare till HTTP-klientens kontroll block.

**callback_function** Motringning anropades under bearbetning av svars huvud. Återanropet anropas med fält namnet och värdet som strängar (och deras längd). Huvudet "Content-Length: 100" skulle till exempel orsaka att funktionen anropas med "Content-Length" för *field_name* och strängen "100" för *field_value*.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) återanrops tilldelningen lyckades.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

Öppna en TLS-session till en HTTPS-server för anpassade begär Anden

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här metoden är för **TLS-säkrad** https.

Den här tjänsten öppnar en säker TLS-session till en HTTPS-server men skickar inga förfrågningar. Begär Anden skapas med n *x_web_http_client_request_initialize ()* och skickas med *nx_web_http_client_request_send ()*. Anpassade HTTP-huvuden kan läggas till i begäran med hjälp av *nx_web_http_client_request_header_add ()*.

Användningen av den här tjänsten gör det möjligt för ett program att lägga till valfritt antal anpassade huvuden i begäran. **Detta möjliggör anpassade HTTP-begäranden som är avsedda för vissa program.**

> [!NOTE]
> Nx_web_http_client_ \* _start metoder tillhandahålls för enkelhetens skull. Dessa funktioner använder all den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize ())* för att skapa och skicka HTTP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **server_ip** IP-adress för fjärr-HTTPS-server.
- **SERVER_PORT** Port på fjärr-HTTPS-server (t. ex. 443 för HTTPS).
- **tls_setup** Motringning används för att konfigurera TLS-konfiguration. Programmet definierar denna motringning för att initiera TLS-kryptografi och autentiseringsuppgifter (t. ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten får start förfrågan. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) anslutning av TLS-session.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_WEB_HTTP_NOT_READY (0x3000A) en annan begäran pågår redan.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>API för HTTP och HTTPS-server

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

Ange återanropet för att hämta URL-högsta ålder och datum

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den callback-tjänst som anropas för att hämta den maximala ålder och senaste ändrings datum för den angivna resursen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **cache_info_get** Pekare till motringning
- **max_age** Pekare till högsta ålder för en resurs
- **data** Pekare till senaste ändrings datum som returnerades.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett återanropet
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Initiering

### <a name="example"></a>Exempel

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

Skicka data från callback-funktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar data i det angivna paketet från programmets callback-rutin. Detta används vanligt vis för att skicka dynamiska data som är kopplade till GET/POST-förfrågningar. Observera att om den här funktionen används ansvarar återanrops rutinen för att skicka hela svaret i rätt format. Dessutom måste återanrops rutinen returnera status för NX_WEB_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **data_ptr** Pekare till de data som ska skickas.
- **data_length** Antal byte som ska skickas.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat Server data
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

Skapa ett svars huvud i en callback-funktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används i HTTP (S)-återanrops rutinen för servern (definieras av programmet) för att generera ett HTTP-svarshuvuden. Återkallnings rutinen för servern anropas när HTTP-servern svarar på GET-, Delete-och DELETE-begäranden som kräver HTTP-svar. Den här funktionen tar svars information från programmet och genererar lämpligt svars huvud. Se tjänst *nx_web_http_server_create ()* om du vill ha mer information om återanrops rutinen för serverbegäran.

Detta API är föråldrat. Utvecklare uppmanas att använda *nx_web_http_server_callback_generate_response_header_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **packet_pptr** Pekar en paket pekare som har allokerats för meddelande
- **status_code** Indikerar resurs status. Exempel:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **CONTENT_LENGTH** Storlek på innehåll i byte
- **content_type** Typ av HTTP, t. ex. "text/plain"
- **additional_header** Pekare till ytterligare sidhuvud text

### <a name="return-values"></a>Retur värden

- Ett HTML-huvud har skapats för **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

Skapa ett svars huvud i en callback-funktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten används i HTTP (S)-återanrops rutinen för servern (definieras av programmet) för att generera ett HTTP-svarshuvuden. Återkallnings rutinen för servern anropas när HTTP-servern svarar på GET-, Delete-och DELETE-begäranden som kräver HTTP-svar. Den här funktionen tar svars information från programmet och genererar lämpligt svars huvud. Se tjänst *nx_web_http_server_create ()* om du vill ha mer information om återanrops rutinen för serverbegäran.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **packet_pptr** Pekar en paket pekare som har allokerats för meddelande
- **status_code** Indikerar resurs status. Exempel:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** Sträng längd för status kod
- **CONTENT_LENGTH** Storlek på innehåll i byte
- **content_type** Typ av HTTP, t. ex. "text/plain"
- **content_type_length** Innehålls typ sträng längd
- **additional_header** Pekare till ytterligare sidhuvud text
- **additional_header_length** Längd på ytterligare rubrik text

### <a name="return-values"></a>Retur värden

- Ett HTML-huvud har skapats för **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

Skicka ett HTTP-paket från callback-funktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar ett fullständigt HTTP-servernamn från ett HTTP-motanrop. HTTP-servern skickar paketet med NX_WEB_HTTP_SERVER _TIMEOUT_SEND. HTTP-huvudet och data måste läggas till i paketet. Om retur statusen indikerar ett fel, måste HTTP-programmet släppa paketet.

Återanropet ska returnera NX_WEB_HTTP_CALLBACK_COMPLETED.

Se *nx_web_http_server_callback_generate_response_header ()* för ett mer detaljerat exempel.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block
- **packet_ptr** Pekare till det paket som ska skickas

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) tog emot http-server paket
- **NX_PTR_ERROR** (0X07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

Skicka svar från callback-funktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar den levererade svars informationen från appens callback-rutin. Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar. Observera att om den här funktionen används måste återanrops rutinen returnera status för NX_WEB_HTTP_CALLBACK_COMPLETED.

Den här tjänsten är föråldrad. Utvecklare uppmanas att använda *nx_web_http_server_callback_response_send_extended ()*.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **sidhuvud** Pekar mot svars huvud strängen.
- **information** Pekar mot informations strängen.
- **additional_info** Pekare till den ytterligare informations strängen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat http-serverns svar

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

Skicka svar från callback-funktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skickar den levererade svars informationen från appens callback-rutin. Detta används vanligt vis för att skicka anpassade svar som är kopplade till GET/POST-förfrågningar. Observera att om den här funktionen används måste återanrops rutinen returnera status för NX_WEB_HTTP_CALLBACK_COMPLETED.

Strängarna för rubrik, information och additional_info måste vara NULL-avslutade och längden på varje sträng matchar den längd som anges i argument listan.

Den här tjänsten ersätter *nx_web_http_server_callback_response_send*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **sidhuvud** Pekar mot svars huvud strängen.
- **header_length** Längd på svars huvud strängen.
- **information** Pekar mot informations strängen.
- **Information_length** Längden på informations strängen.
- **additional_info** Pekare till den ytterligare informations strängen.
- **additional_info_length** Den ytterligare informations strängens längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har skickat http-serverns svar

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

Hämta innehåll från begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hämta den angivna mängden innehåll från begäran eller skicka HTTP-klientbegäran. Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **packet_ptr** Pekar mot HTTP-klientens begär ande paket. Observera att det här paketet inte får släppas av begäran om att meddela motringning.
- **byte_offset** Antal byte som ska förskjutas i innehålls ytan.
- **destination_ptr** Pekar till mål avsnittet för innehållet.
- **destination_size** Maximalt antal byte som är tillgängliga i mål arean.
- **actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-serverns innehåll Hämta
- Internt fel för **NX_WEB_HTTP_ERROR** (0X30000) http-server
- **NX_WEB_HTTP_DATA_END** (0X30007) slut på innehåll i begäran
- **NX_WEB_HTTP_TIMEOUT** (0x30001) timeout för http-server i Hämta nästa paket med innehåll
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

Hämta innehåll från begäran/har stöd för längd för längd innehåll

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är nästan identisk med *nx_web_http_server_content_get ()*; det försöker hämta den angivna mängden innehåll från POST-eller klient förfrågan. Den hanterar dock begär Anden med innehålls längd noll (' Empty Request ') som en giltig begäran. Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).

Den här tjänsten ersätter *nx_web_http_server_content_get*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **packet_ptr** Pekar mot HTTP-klientens begär ande paket. Observera att det här paketet inte får släppas av begäran om att meddela motringning.
- **byte_offset** Antal byte som ska förskjutas i innehålls ytan.
- **destination_ptr** Pekar till mål avsnittet för innehållet.
- **destination_size** Maximalt antal byte som är tillgängliga i mål arean.
- **actual_size** Pekar på den mål variabel som ska anges till den faktiska storleken på innehållet som kopieras.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-innehållet Hämta
- Internt fel för **NX_WEB_HTTP_ERROR** (0X30000) http-server
- **NX_WEB_HTTP_DATA_END** (0X30007) slut på innehåll i begäran
- **NX_WEB_HTTP_TIMEOUT** (0x30001) timeout för http-server i Hämta nästa paket
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

Hämta längden på innehållet i begäran/stöder innehålls längden noll värde

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hämta HTTP-innehållets längd i det angivna paketet. Returvärdet visar att slut för ande status har slutförts och det faktiska värdet för längd returneras i indatamängden content_length. Om det inte finns något HTTP-innehåll/innehålls längd = 0, returnerar den här rutinen fortfarande statusen slutförd och content_length inmatare pekar på en giltig längd (noll). Den ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Indataparametrar

- **packet_ptr** Pekar mot HTTP-klientens begär ande paket. Observera att det här paketet inte får släppas av begäran om att meddela motringning.
- **CONTENT_LENGTH** Pekare till värde som hämtats från fältet innehålls längd

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-serverns innehålls längd Hämta
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0X3000F) felaktigt http-huvudformat
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

Skapa en HTTP-serverinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd. De valfria rutinerna för *authentication_check* och *request_notify* programbegäran ger program kontroll över den grundläggande driften av HTTP-servern.

Den här tjänsten används för att skapa både oformaterade HTTP-servrar och TLS-säkra HTTPS-servrar. Information om hur du aktiverar HTTPS med TLS finns i tjänst *nx_web_http_server_secure_configure ()*.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server Control-Block.
- **http_server_name** Pekare till HTTP-serverns namn.
- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **SERVER_PORT** TCP-lyssnings port för Server instans.
- **media_ptr** Pekare till den tidigare skapade FileX Media-instansen.
- **stack_ptr** Pekar på ett stack-fält för HTTP-serverns tråd.
- **stack_size** Pekare till HTTP-server trådens stack storlek.
- **authentication_check** Funktions pekare till programmets verifierings kontroll rutin. Den här rutinen anropas för varje HTTP-klientbegäran. Om den här parametern är NULL utförs ingen autentisering. Den här parametern är föråldrad. Anropa *nx_web_http_server_authenticate_check_set*() i stället.
- **request_notify** Funktions pekare till program begär ande aviserings rutin. Den här rutinen anropas före HTTP-serverns bearbetning av begäran. Detta gör att resurs namnet kan omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-servern har skapats.
- NX_PTR_ERROR (0x07) ogiltig pekare för HTTP-server, IP, media, stack eller Packet-pool.
- NX_WEB_HTTP_POOL_ERROR (0x30009) paket nytto lasten för poolen är inte tillräckligt stor för att rymma fullständig HTTP-begäran.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

Ta bort en HTTP-serverinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad HTTP-serverinstans.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server Control-Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-servern har tagits bort
- NX_PTR_ERROR (0x07) ogiltig HTTP-server pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

Hämta plats och längd för enhets data

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten bestämmer platsen för starten av data i den aktuella flerdelade entiteten i mottagna klient meddelanden och längden på data som inte inkluderar begränsnings strängen. Internt uppdaterar HTTP-servern sina egna förskjutningar så att den här funktionen kan anropas igen på samma klient-datagram för meddelanden med flera entiteter. Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.

Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten. Observera också att programmet inte bör släppa paketet som packet_pptr. Detta görs internt av HTTP-servern.

Se *nx_web_http_server_get_entity_header ()* för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-Server
- **packet_pptr** Pekare till platsen för paket pekaren. Observera att programmet inte ska frigöra det här paketet
- **available_offset** Pekare för förskjutning av enhets data från paketets lägga-pekare
- **available_length** Pekare till längd på enhets data

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har hämtat storlek och plats för enhetens innehåll
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) för HTTP-serverns interna flerdelade markörer finns redan
- Internt fel för NX_WEB_HTTP_ERROR (0x30000) HTTP-Server
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

Hämta innehållet i enhets huvudet

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar enhets rubriken till den angivna bufferten. Internt HTTP-Server uppdaterar sin egen pekare för att hitta nästa flerdelade entitet i ett klient-datagram med flera entitets-rubriker. Paket pekaren uppdateras till nästa paket där klient meddelandet är ett datagram med flera paket.

Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten. Observera också att programmet inte bör släppa paketet som packet_pptr.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-Server
- **packet_pptr** Pekare till platsen för paket pekaren. Observera att programmet inte ska frigöra det här paketet
- **entity_header_buffer** Pekare till plats för lagring av enhets huvud
- **buffer_size** Storlek på indatabufferten

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har hämtat enhets huvudet
- Det gick inte att hitta **NX_WEB_HTTP_NOT_FOUND** (0X30006) entitets huvud fält
- **NX_WEB_HTTP_TIMEOUT** (0X30001) tid för att ta emot nästa paket för klient meddelande med multipaket
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten
- Internt HTTP-fel NX_WEB_HTTP_ERROR (0x30000)

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

Ange återanropet för att få GMT-datum och-tid

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger återanropet för att hämta GMT-datum och-tid med en tidigare skapad HTTP-server. Den här tjänsten anropas med HTTP-servern för att skapa en rubrik i HTTP-server svar på klienten.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-Server
- **gmt_get** Pekare till GMT-motanrop
- **datum** Pekare till det datum som hämtades

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett återanropet
- NX_PTR_ERROR (0x07) ogiltig paket-eller parameter pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

Ange återanropet för att hantera Ogiltig användare/lösen ord

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger återanropet som anropas när ett ogiltigt användar namn och lösen ord tas emot i en klient get-,-eller Delete-begäran, antingen av Digest eller grundläggande autentisering. HTTP-servern måste ha skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-Server
- **invalid_username_password_callback** Pekare till Ogiltig användare/pass motringning
- **resurs** Pekare till resursen som anges av klienten
- **client_address** Klient adress
- **request_type** Anger typ av klient förfrågan. Kanske:
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett återanropet
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

Ange ytterligare MIME-mappningar för HTML

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Beskrivning

Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från de standard-MIME-typer som anges av NetX-webb-HTTP-servern. Se *nx_web_http_server_get_type ()* för lista över definierade typer.

När en klientbegäran tas emot, t. ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med en prioriterad uppsättning av ytterligare MIME-mappningar och om ingen matchning hittas söker den efter en matchning i standard-MIME-mappningen för HTTP-servern. Om ingen matchning hittas är MIME-typen Standard text/plain.

Om begär ande aviserings funktionen har registrerats med HTTP-servern kan aviseringen meddela motringning anropa *nx_web_http_server_type_get_extended ()* för att parsa filtypen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverinstansen
- **mime_maps** Pekare till en MIME-kart mat ris
- **mime_map_num** Antal MIME-mappningar i matrisen

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-SERVERNS MIME-mappning har angetts
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

Allokera ett HTTP (S)-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker allokera ett paket för HTTP (S)-servern.

Observera att om ett efterföljande NetX-eller HTTP-server-API som använder det här paketet **Miss lyckas**, t. ex. nx_packet_data_append eller * * nx_web_http_server_callback_packet_send, är programmet ansvarigt för att släppa paketet. **

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server Control-Block.
- **packet_ptr** Pekare till allokerat paket.
- **wait_option** Definierar vänte tiden i Tick om det inte finns några tillgängliga paket i modempoolen. Vänte alternativen definieras enligt följande:
  - **NX_NO_WAIT** (0X00000000) väljer NX_NO_WAIT gör att anrops tråden returneras omedelbart om begäran inte kan uppfyllas.
  - **NX_WAIT_FOREVER** (0Xffffffff) väljer NX_WAIT_FOREVER gör att anrops tråden inaktive ras oändligt tills http-servern svarar på begäran.
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (0X1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på http-server svaret.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket tilldelningen lyckades
- **NX_NO_PACKET** (0X01) inget tillgängligt paket
- **NX_WAIT_ABORTED** (0x1a) den begärda Avstängningen avbröts av ett anrop till *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERSs** paket storlek (0X4D) stöder inte protokollet.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

Extrahera innehålls längd och ange pekare till början av data

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten extraherar innehålls längden från HTTP-huvudet. Den uppdaterar också det tillhandahållna paketet enligt följande: paketets lägga-pekare (start på platsen för den pakettyp som ska skrivas till) har angetts till HTTP-innehållet (data) precis skickade HTTP-huvudet.

Om början av innehållet inte hittas i det aktuella paketet väntar funktionen på nästa paket som ska tas emot med alternativet NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE vänta.

Observera att detta inte ska anropas innan du anropar *nx_web_http_server_get_entity_header ()* eftersom den ändrar paketets lägga-pekare förbi enhets huvudet.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverinstansen
- **packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad lägga-pekare
- **CONTENT_LENGTH** Pekare som extraheras content_length

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-innehålls längd hittades och paketet har uppdaterats
- **NX_WEB_HTTP_TIMEOUT** (0X30001) tid för att vänta på nästa paket
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

Ta emot nästa HTTP-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar nästa paket som tas emot på HTTP-serverns socket. Alternativet vänte för att ta emot ett paket är NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Observera att om programmet har ansvar för att släppa paketet.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverinstansen
- **packet_ptr** Pekare till mottaget paket

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har tagit emot nästa http-paket
- **NX_WEB_HTTP_TIMEOUT** (0X30001) tid för att vänta på nästa paket
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

Hämta parameter från begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hämta angiven HTTP URL-parameter i det angivna paketet för begäran. Om den begärda HTTP-parametern inte finns, returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND. Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Indataparametrar

- **packet_ptr** Pekare till HTTP-klientens begär ande paket. Observera att programmet inte ska frigöra det här paketet.
- **param_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i parameter listan.
- **param_ptr** Mål arean för att kopiera parametern.
- **param_size** Returnera total parameter data längd (i byte).
- **max_param_size** Maximal storlek för parameter mål arean.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-server parametern get har slutförts
- Det gick inte att hitta den angivna parametern **NX_WEB_HTTP_NOT_FOUND** (0x30006)
- Parametern för **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) är inte korrekt avslutad
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

Hämta fråga från begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker hämta angiven HTTP URL-fråga i det angivna paketet för begäran. Om begärd HTTP-fråga inte finns, returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND. Den här rutinen ska anropas från programmets begär ande meddela motringning som anges när HTTP-servern skapas (*nx_web_http_server_create ()*).

### <a name="input-parameters"></a>Indataparametrar

- **packet_ptr** Pekare till HTTP-klientens begär ande paket. Observera att programmet inte ska frigöra det här paketet.
- **query_number** Logiskt nummer för parametern som börjar vid noll, från vänster till höger i listan över frågor.
- **query_ptr** Mål områden för att kopiera frågan.
- **query_size** Returnera frågans data storlek (i byte).
- **max_query_size** Maximal storlek på målet

Skriv.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad http-server fråga Hämta
- **NX_WEB_HTTP_FAILED** (0X30002) frågan är för liten.
- Det gick inte att hitta den angivna frågan för **NX_WEB_HTTP_NOT_FOUND** (0x30006)
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0X30013) ingen fråga i klient förfrågan
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

Ange segmenterad överföring för HTTP (S)-svar

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten använder Chunked Transfer-kodning för att skicka ett anpassat HTTP (S)-svars data paket som skapats med *nx_web_http_server_response_packet_allocate*() till klienten.

> [!NOTE]
> Om programmet använder Chunked Transfer-kodning för att skicka ett svars data paket, måste det anropa den här tjänsten när du anropar *nx_web_http_server_response_packet_allocate*() och innan du anropar *nx_web_http_server_callback_packet_send*().

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientens kontroll block.
- **chunk_size** Storlek på segment data i oktetter.
- **packet_ptr** HTTP (a) begär data pakets pekare.

### <a name="return-values"></a>Retur värden

- Den **NX_SUCCESS** (0x00) har en segment.
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

Konfigurera en HTTP-server för att använda TLS för säker HTTPS

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar en tidigare skapad NetX-webbinstans för HTTP-server för att använda TLS för säker HTTPS-kommunikation. Parametrarna används för att konfigurera alla möjliga TLS-sessioner med identiskt tillstånd så att varje inkommande HTTPS-klient upplever konsekvent beteende. Antalet TLS-sessioner styrs med hjälp av makro NX_WEB_HTTP_SESSION_MAX.

Den kryptografiska rutin tabellen (ciphersuite-tabellen) delas mellan alla TLS-sessioner eftersom den bara innehåller funktions pekare.

Buffertarna för metadata och paket ommontering är var och en uppdelad jämnt mellan alla TLS-sessioner. Om buffertstorleken inte är jämnt delbar med antalet sessioner används resten.

Det skickade identitets certifikatet används av alla sessioner. Under TLS-åtgärd läses Server identitets certifikatet bara från så att kopior inte behövs för varje session.

De betrodda certifikaten läggs till i varje TLS-session i HTTPS-servern. Dessa används för autentisering av klient certifikat som aktive ras automatiskt när Fjärrcertifikatet har angetts.

Fjärrcertifikatets matris och buffert delas som standard mellan alla TLS-sessioner. Fjärrcertifikaten används för autentisering av klient certifikat som aktive ras automatiskt när antalet fjärrcertifikat är noll. På grund av att bufferten som delas är en del sessioner kan blockeras under certifikat valideringen.

Om du vill inaktivera autentisering av klient certifikat, pass NX_NULL för remote_certificates-parametern och värdet 0 för remote_certs_num-parametern.

Retur värden tar med alla TLS-felkoder som uppstår på grund av problem med konfigurationen av TLS-sessionerna.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen.
- **crypto_table** Pekare till TLS ciphersuite-tabell.
- **metadata_buffer** Pekare till buffert för kryptografisk metadata.
- **metadata_size** Storlek på buffert för kryptografisk metadata.
- **packet_buffer** Omassembly-buffert för TLS-paket.
- **packet_buffer** Storleken på TLS-paketets buffert – bör vara lika med (<önskad TLS-buffertstorlek * NX_WEB_HTTP_SESSION_MAX).
- **identity_certificate** TLS-serverns identitets certifikat – kommer att användas för alla HTTPS-serversessioner.
- **trusted_certificates** Pekar mot matrisen med NX_SECURE_X509_CERT objekt som används för att verifiera inkommande klient certifikat om autentisering av klient certifikat är aktiverat genom att skicka ett värde som inte är noll för parametern *remote_certs_num* .
- **trusted_certs_num** Antal betrodda certifikat i *trusted_certificates* matrisen.
- **remote_certificates** Pekare till matrisen med NX_SECURE_X509_CERT objekt som används för inkommande klient certifikat.
- **remote_certs_num** Antal fjärrcertifikat. Ska vara det maximala antalet certifikat som förväntas från klienter. Autentisering av klient certifikat aktive ras automatiskt när detta inte är noll.
- **remote_certificate_buffer** Buffert som innehåller inkommande fjärrcertifikat från klienter om autentisering av klient certifikat är aktiverat. remote_cert_buffer_size storleken på bufferten för fjärrcertifikat. Måste vara lika med (<maximala förväntad certifikat storlek \* remote_certs_num).


### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckades initiera TLS-sessionen.
- **NX_NOT_CONNECTED** (0X38) den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) en mottagen TLS-meddelande typ är felaktig.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0X106) ett chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Det gick inte att bearbeta meddelande bearbetningen under TLS-handskakningen.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108) ett inkommande meddelande misslyckades med en hash Mac-kontroll.
- **NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Det gick inte att skicka en underliggande TCP-socket.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) ett inkommande meddelande hade ett ogiltigt längd fält.
- **NX_SECURE_TLS_BAD_CIPHERSPE** (0X10B) ett inkommande ChangeCipherSpec-meddelande var felaktigt.
- **NX_SECURE_TLS_INVALID_SERVER_CER** (0X10C) ett inkommande TLS-certifikat kan inte användas för att identifiera fjärr-TLS-servern.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0X10D) den offentliga nyckel chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) fjärrvärden har angett Inga krypteringssviter som stöds av netx Secure TLS-stacken.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) ett MOTTAGet TLS-meddelande hade en okänd TLS-version i huvudet.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) ett MOTTAGet TLS-meddelande hade en känd men TLS-version som inte stöds i huvudet.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Det gick inte att tilldela en intern TLS-paket.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) fjärrvärden tillhandahöll ett ogiltigt certifikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) den fjärranslutna värden skickade en avisering som indikerar ett fel och att TLS-sessionen avslutas.
- **NX_PTR_ERROR** (0X07) försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

Starta HTTP-servern

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en tidigare skapad HTTP-eller HTTPS-serverinstans.

HTTPS-servrar delar samma API som HTTP. Information om hur du aktiverar HTTPS med TLS på en HTTP-Server finns i tjänst *nx_web_http_server_secure_configure ().*

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-servern har startats
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

Stoppa HTTP-servern

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar den tidigare skapade HTTP-serverinstansen. Den här rutinen ska anropas innan en HTTP-serverinstans tas bort.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) http-servern stoppades
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

Extrahera filtypen från klientens HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Beskrivning

> [!NOTE]
> Den här tjänsten är föråldrad. Användarna uppmanas att använda tjänsten *nx_web_http_server_type_get_extended ()*.

Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd *string_size* från indatabufferten *, vanligt vis URL: en*. Om det inte går att hitta någon MIME-mappning används standard typen text/plain. Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning. Standard-MIME-mappningarna i NetX webb-HTTP-server är:

- HTML-text/html
- htm-text/html
- txt-text/plain
- GIF-bild/gif
- jpg-bild/JPEG
- ico-bild/x-ikon

Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar. Se *nx_web_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen
- **namn** Pekare för att söka
- **http_type_string** Pekare till extraherad HTML-typ sträng
- **string_size** Pekare för att returnera extraherad HTML-typ sträng längd.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) extrahering av typ
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) standard "text/plain" returnerades.

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

Extrahera filtypen från klientens HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten extraherar typen av HTTP-begäran i bufferten *http_type_string* och dess längd *string_size* från indatabufferten *, vanligt vis URL: en*. Om det inte går att hitta någon MIME-mappning används standard typen text/plain. Annars jämförs den extraherade typen mot standard-MIME-mappningarna i HTTP-servern för en matchning. Standard-MIME-mappningarna i NetX webb-HTTP-server är:

- HTML-text/html
- htm-text/html
- txt-text/plain
- GIF-bild/gif
- jpg-bild/JPEG
- ico-bild/x-ikon

Om den anges söker den också efter en användardefinierad uppsättning ytterligare MIME-mappningar. Se *nx_web_http_server_mime_maps_addtional_set ()* för mer information om användardefinierade mappningar.

Den här tjänsten ersätter *nx_web_http_server_type_get*(). Den här versionen kräver att anropare anger längd information för funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen
- **namn** Pekare för att söka
- **name_length** Längd på namn
- **http_type_string** Pekare till extraherad HTML-typ sträng
- **http_type_string_max_size** Storlek på storleken på http_type_string-buffertstorleken
- **string_size** Pekare som returnerar extraherad HTML-typ sträng

krävande.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) extrahering av typ
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0X30019) standard "text/plain" returnerades.

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

Ange funktionen Digest-autentisering

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger återanropet som anropas när Digest-autentisering utförs.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen
- **digest_authenticate_callback** Pekare till sammanfattad autentisering av motringning

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett återanropet
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare
- NX_NOT_SUPPORTED (0x4B) Digest-autentisering är inte aktiverat

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

Ange funktionen Digest-autentisering

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger det motanrop som anropades när autentiserings kontroll utförs.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverinstansen
- **authenticate_check_externded** Pekare för att autentisera check motringning

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har angett återanropet
- NX_PTR_ERROR (0x07) ogiltigt inmatade pekare

### <a name="allowed-from"></a>Tillåten från

Program

### <a name="example"></a>Exempel

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
