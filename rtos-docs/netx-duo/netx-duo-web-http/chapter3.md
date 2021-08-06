---
title: Kapitel 3 – Beskrivning av HTTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Web HTTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0357afe7f997c84a5d031ca71dc524e381734b4a
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178195"
---
# <a name="chapter-3---description-of-http-services"></a>Kapitel 3 – Beskrivning av HTTP-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX Web HTTP-tjänster (visas nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

## <a name="http-and-https-client-api"></a>HTTP- och HTTPS-klient-API

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

Öppna en socket i klartext till en HTTP-server för anpassade begäranden

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten öppnar en TCP-socket i klartext till en HTTP-server men skickar inga begäranden. Begäranden skapas med n *x_web_http_client_request_initialize() och* skickas med *hjälp av nx_web_http_client_request_send().* Anpassade HTTP-huvuden kan läggas till i begäran med *hjälp av nx_web_http_client_request_header_add()*.

Användning av den här tjänsten gör det möjligt för ett program att lägga till val annat antal anpassade huvuden i begäran. **Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.**

> [!NOTE]
> Metoderna nx_web_http_client_*_start tillhandahålls för enkelhetens skull (t.ex. *nx_web_http_client_get_start*()) och hanterar genereringen av förfrågningar och socketanslutningen. Du kan använda dessa tjänster *i stället för nx_web_http_client_connect()* och relaterade rutiner om du inte behöver anpassade HTTP-huvuden i dina begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **server_ip** IP-adress för fjärransluten HTTP-server.
- **server_port** Port på http-fjärrserver (t.ex. 80 för HTTP).
- **wait_option** Definierar hur länge tjänsten ska vänta på underliggande nätverksåtgärder. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad anslutning av TCP-socket.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_WEB_HTTP_NOT_READY (0x3000A) En annan begäran pågår redan.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
    "https://192.168.1.150/test.txt ", "host.com",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

Skapa en HTTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en HTTP-klientinstans på den angivna IP-instansen. Klientinstansen kan användas för HTTP eller HTTPS. Se tjänsterna *nx_web_http_client_connect() och* *nx_web_http_client_secure_connect()* för mer information om hur du startar en HTTP- eller HTTPS-instans. Se även API:et för *nx_web_http_client_get_**, *nx_web_http_client_put_**, *nx_web_http_client_post_** för enkla anrop av GET-, PUT- och POST-metoder.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **client_name** Namnet på HTTP-klientinstansen.
- **ip_ptr** Pekare till IP-instans.
- **pool_ptr** Pekare till standardpaketpoolen. Observera att paketen i den här poolen måste ha en nyttolast som är tillräckligt stor för att hantera hela svarshuvudet. Detta definieras av *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* i *nx_web_http_client.h*.
- **window_size** Storleken på klientens TCP-socket-mottagningsfönster.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad HTTP-klient skapas
- NX_PTR_ERROR (0x16) Ogiltig HTTP-, ip_ptr- eller paketpoolspekare
- NX_WEB_HTTP_POOL_ERROR (0x30009) Ogiltig nyttolaststorlek i paketpoolen

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

Ta bort en HTTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en http-klientinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av HTTP-klient
- NX_PTR_ERROR (0x16) Ogiltig HTTP-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Det här API:et är inaktuellt. Utvecklare uppmanas att använda *nx_web_http_client_delete_start_extended()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) har skickat meddelandet HTTP-klientens DELETE-begäran
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_delete_start* (). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Meddelandet HTTP-klientens DELETE-begäran har skickats
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_delete_secure_start_extended()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen. -resursen måste vara NULL-avslutad.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Meddelandet HTTP-klientens DELETE-begäran har skickats
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker skicka en DELETE-begäran för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_delete_secure_start*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen. -resursen måste vara NULL-avslutad.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) har skickat meddelandet HTTP-klientens DELETE-begäran
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.


### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_get_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Skickade HTTP-klientens GET-startmeddelande
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Strängarna för resursen, värden, användarnamnet och lösenordet måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_get_start*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Skickade HTTP-klientens GET-startmeddelande
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_get_secure_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) STARTmeddelande för HTTP-klienten
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker hämta resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop *till nx_web_http_client_response_body_get()* för att hämta datapaket som motsvarar det begärda resursinnehållet.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_secure_start*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) STARTmeddelande för HTTP-klienten
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta en HTTP HEAD-begäran i klartext

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om rutinen returnerar NX_SUCCESS kan programmet sedan anropa *nx_web_http_client_response_body_get()* för att hämta svaret.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_head_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta en HTTP HEAD-begäran i klartext

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen NX_SUCCESS kan programmet sedan anropa *nx_web_http_client_response_body_get()* för att hämta svaret.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_head_start*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar som motsvarar det begärda resursinnehållet.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_head_secure_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker hämta HEAD-metadata för resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen returnerar NX_SUCCESS kan programmet anropa *nx_web_http_client_response_body_get()* för att hämta serverns svar som motsvarar det begärda resursinnehållet.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` GET-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_head_secure_start*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** Port på fjärransluten HTTP-server.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) skickade ETT MEDDELANDE om HTTP-klientens HEAD-begäran
- **NX_WEB_HTTP_ERROR** (0x30000) Internt HTTP-klientfel
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP-klientfel som kommunicerar med HTTP-servern.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Allokera ett HTTP(S)-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker allokera ett paket för klientens HTTP(S).

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **packet_ptr** Pekare till allokerat paket.
- **wait_option** Definierar väntetiden i tick om det inte finns några paket tillgängliga i paketpoolen. Väntealternativen definieras på följande sätt:
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **timeout i tick** (0x00000001 via 0xFFFFFFFE)

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Allokera ett lyckat paket
- **NX_NO_PACKET** (0x01) Inget paket tillgängligt
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D) Paketstorleken stöder inte protokoll.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas ska programkoden göra efterföljande anrop *nx_web_http_client_put_packet* rutinen för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_post_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng som resursen ska skicka till servern.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Post-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas ska programkoden göra efterföljande anrop *nx_web_http_client_put_packet* rutinen för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_post_start* (). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Post-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas ska programkoden göra efterföljande anrop *till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_post_secure_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng som resursen ska skicka till servern.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Post-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker skicka en POST-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas ska programkoden göra efterföljande anrop *till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_post_secure_start* (). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för begärd resurs.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Post-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta en HTTP PUT-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_put_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng som resursen ska skicka till servern.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **total_bytes** Totalt antal byte för resursen som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Put-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta en HTTP PUT-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Den här metoden är **för KLARTEXT** HTTP.

Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_put_start* (). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **total_bytes** Totalt antal byte för resursen som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Put-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta en krypterad HTTPS PUT-begäran

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_put_secure_start_extended()*.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng som resursen ska skicka till servern.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **total_bytes** Totalt antal byte för resursen som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Put-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Starta en krypterad HTTPS PUT-begäran

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

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTPS-servern på den angivna IP-adressen och porten. Om den här rutinen lyckas bör programkoden göra efterföljande *anrop till nx_web_http_client_put_packet()-rutinen* för att skicka resursinnehållet till HTTP-servern.

Observera att resurssträngen kan referera till en lokal fil, t.ex. "/index.htm" eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade `http://abc.website.com/index.htm` PUT-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_put_secure_start*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **ip_address** HTTP-serverns IP-adress.
- **server_port** TCP-port på den fjärranslutna HTTP-servern.
- **resurs** Pekare till URL-sträng för den begärda resursen.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **total_bytes** Totalt antal byte för resursen som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_web_http_client_put_packet() måste* vara lika med det här värdet.
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Put-begäran har skickats
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Användarnamnet är för stort för buffert
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skicka nästa resursdatapaket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skicka nästa paket med resursinnehåll till HTTP-servern för både PUT- och POST-åtgärder. Observera att den här rutinen bör anropas repetitivt tills den kombinerade längden på de paket som skickas är lika med "total_bytes" som angavs i det tidigare *nx_web_http_client_put_start() eller* *nx_web_http_client_post_start()-anropet* (eller deras motsvarande säkra versioner).

Den här tjänsten söker också efter svar från servern om det uppstod ett problem med att upprätta HTTP-anslutningen (eller HTTPS).

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **packet_ptr** Pekar till nästa innehåll i resursen som skickas till HTTP-servern.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) SKICKADE HTTP-klientpaket.
- **HTTP-klienten** NX_WEB_HTTP_NOT_READY (0x3000A) inte klar
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Felkod för mottagen server**
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Ogiltig paketlängd
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Ogiltigt namn och/eller lösenord
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Servern svarar innan PUT har slutförts
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_INVALID_PACKET (0x12) Paket för litet för TCP-huvud
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

Ange segmenterad överföring för HTTP(S)-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten använder chunked transfer-kodning för att skicka en anpassad HTTP(S)-begäran till servern som anges i *anropet nx_web_http_client_connect()* eller *nx_web_http_client_secure_connect(),* som tidigare har upprättat socketanslutningen till fjärrvärden.

> [!NOTE]
> Om programmet använder segmenterad överföringskod för att skicka ett datapaket för begäran måste det anropa den här tjänsten efter *anropet nx_web_http_client_request_packet_allocate*() och *innan anropet nx_web_http_client_reqeust_packet_send* ().

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **chunk_size** Storleken på segmentdata i oktett.
- **packet_ptr** Pekare för HTTP(S)-begärandedatapaket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har angetts segmenterat.
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
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

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

Lägga till ett anpassat huvud i en anpassad HTTP-begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Description

Den här tjänsten lägger till ett anpassat huvud (i form av ett fältnamn och värde) i en anpassad HTTP-begäran som skapats med n *x_web_http_client_request_initialize()*.

Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran. **Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.**

> [!NOTE]
> De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull. Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize()) för* att skapa och skicka HTTP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **field_name** Fältnamnssträng (t.ex. "Innehållstyp").
- **name_length** Längden på fältnamnssträngen i byte.
- **field_value** Fältvärdessträng (t.ex. "program/oktettström").
- **value_length** Längden på värdesträngen i byte.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tillägg av rubrik i begäran.
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
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
    until the entire response is retrieved. */

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

### <a name="description"></a>Description

Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klientinstansen. Till skillnad *från de enklare nx_web_http_client_get_start()* (tillsammans med metoderna för PUT, POST och de associerade säkra versionerna av dessa API) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send()* anropas.

Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran med ***hjälp av nx_web_http_client_request_header_add()-tjänsten.*** Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.

> [!NOTE]
> De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull. Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_send()) för* att skapa och skicka HTTP-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_client_request_initialize_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **metod** Http-förfrågningsmetoden som ska användas. Alternativen definieras på följande sätt:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resurs** Namnet på den resurs som överförs.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **input_size** Storleken på indata för PUT och POST. Skicka 0 för andra åtgärder.
- **transfer_encoding_trunked** Reserverad parameter för stöd för framtida trunkerad överföring.
- **användarnamn** Användarnamn för skyddade resurser.
- **lösenord** Lösenord för skyddade resurser.
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av begäran.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_WEB_HTTP_METHOD_ERROR (0x30014) Viss nödvändig information saknades (t.ex. input_size put eller POST).

### <a name="allowed-from"></a>Tillåts från

Trådar

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
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
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skapar en anpassad HTTP-begäran och associerar den med HTTP-klientinstansen. Till skillnad *från de enklare nx_web_http_client_get_start()* (tillsammans med metoderna för PUT, POST och de associerade säkra versionerna av dessa API) skickas inte den anpassade begäran förrän tjänsten *nx_web_http_client_request_send()* anropas.

Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran med ***hjälp av nx_web_http_client_request_header_add()-tjänsten.*** Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.

> [!NOTE]
> De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull. Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_send()) för* att skapa och skicka HTTP-begäranden.

Strängarna för resurs, värd, användarnamn och lösenord måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_client_request_initialize*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **metod** Http-förfrågningsmetoden som ska användas. Alternativen definieras på följande sätt:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resurs** Namnet på den resurs som överförs.
- **resource_length** Stränglängd för den begärda resursen.
- **värd** Null-avslutad sträng för serverns domännamn. Den här strängen överförs i fältet HTTP-värdrubrik. Värdsträngen får inte vara NULL.
- **host_length** Stränglängd för värden.
- **input_size** Storlek på indata för PUT och POST. Skicka 0 för andra åtgärder.
- **transfer_encoding_trunked** Reserverad parameter för stöd för framtida trunkerad överföring.
- **användarnamn** Pekare till valfritt användarnamn för autentisering.
- **username_length** Stränglängd för användarnamn för autentisering.
- **lösenord** Pekare till valfritt lösenord för autentisering.
- **password_length** Stränglängd för lösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av begäran.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_WEB_HTTP_METHOD_ERROR (0x30014) Viss nödvändig information saknades (t.ex. input_size put eller POST).

### <a name="allowed-from"></a>Tillåts från

Trådar

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

Skicka HTTP(S)-begärandedatapaket till fjärrserver

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett anpassat HTTP(S)-begärandedatapaket som skapats med *nx_web_http_client_request_packet_allocate* () till den server som anges i *anropet nx_web_http_client_connect()* eller *nx_web_http_client_secure_connect(*) som tidigare har upprättat socketanslutningen till fjärrvärden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **packet_ptr** Pekare för HTTP(S)-begärandedatapaket.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades skicka datapaket för begäran.
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
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

/* At this point, user can fill the data into my_packet. */
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

### <a name="description"></a>Description

Den här tjänsten skickar en anpassad HTTP-begäran som skapats med *nx_web_http_client_request_initialize()* till den server som anges i *nx_web_http_client_connect()* eller *nx_web_http_client_secure_connect()* som båda tidigare har upprättat socketanslutningen till fjärrvärden.

Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran med ***hjälp av nx_web_http_client_request_header_add()-tjänsten.*** Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.

> [!NOTE]
> De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull. Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize()) för* att skapa och skicka HTTP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckades skicka begäran.
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

Hämta nästa resursdatapaket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>Description

Den här tjänsten hämtar nästa paket med innehåll i resursen som begärdes i föregående begäran. Efterföljande anrop till den här rutinen ska göras tills returstatusen för NX_WEB_HTTP_GET_DONE tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **packet_ptr** Mål för paket pekare som innehåller partiellt resursinnehåll.
- **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Hämta HTTP-klientpaket.
- **NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP-klienten hämta paket är klar
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP-klienten är inte i get-läge.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Ogiltig paketlängd
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP-statuskod 100 Fortsätt
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP-statuskod 101 Växla protokoll
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP-statuskod 201 har skapats
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP-statuskod 202 Accepterad
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP-statuskod 203 Icke-auktoritativ information
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP-statuskod 204 Inget innehåll
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP-statuskod 205 Återställ innehåll
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP-statuskod 206 Partiellt innehåll
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP-statuskod 300 Flera alternativ
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP-statuskod 301 flyttades permanent
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP-statuskod 302 Hittades
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP-statuskod 303 Se övrigt
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP-statuskod 304 Har inte ändrats
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP-statuskod 305 Använd proxy
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP-statuskod 307 Tillfällig omdirigering
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP-statuskod 400 Felaktig begäran
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP-statuskod 401 – Obehörig
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP-statuskod 402 Betalning krävs
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP-statuskod 403 Förbjuden
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP-statuskod 404 Hittades inte
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP-statuskod 405 Metoden tillåts inte
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP-statuskod 406 Inte acceptabel
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP-statuskod 407 Proxyautentisering krävs
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP-statuskod 408 Time-out för begäran
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP-statuskod 409 Konflikt
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP-statuskod 410 borta
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP-statuskod 411 Längd krävs
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP-statuskod 412 Förhandsvillkor misslyckades
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP-statuskod 413 Begärandeentiteten är för stor
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP-statuskod 414 För stor begärande-URL
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP-statuskod 415 Medietyp stöds inte
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP-statuskod 416 Det begärda intervallet är inte tillåtna
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP-statuskod 417 Förväntan misslyckades
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP-statuskod 500 Internt serverfel
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP-statuskod 501 Inte implementerad
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP-statuskod 502 Felaktig gateway
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP-statuskod 503 Tjänsten är inte tillgänglig
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP-statuskod 504 Gateway Time-out
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP-statuskod 505 HTTP-versionen stöds inte
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ställ in återanrop för att anropa vid bearbetning av HTTP-huvuden

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Description

Den här tjänsten tilldelar ett återanrop som anropas när NetX Web HTTP Client bearbetar ett HTTP-huvud i ett inkommande svar från en fjärransluten HTTP-server. Motringning anropas en gång för varje huvud i svaret när det bearbetas. Motringning gör att ett HTTP-klientprogram kan komma åt vart och ett av huvudena i HTTP-serversvaret för att vidta önskade åtgärder utöver den grundläggande bearbetning som NetX Web HTTP-klienten gör.

### <a name="input-parameters"></a>Indataparametrar

**client_ptr** Pekare till HTTP-klientkontrollblock.

**callback_function** Motringning anropas vid bearbetning av svarshuvud. Motringning anropas med fältnamnet och värdet som strängar (och deras längder). Till exempel skulle rubriken "Content-Length: 100" göra så att funktionen anropas med "Content-Length" för *field_name* och strängen "100" *för field_value*.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad tilldelning av återanrop.
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Öppna en TLS-session till en HTTPS-server för anpassade begäranden

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här metoden är för **TLS-skyddad** HTTPS.

Den här tjänsten öppnar en skyddad TLS-session till en HTTPS-server men skickar inga begäranden. Begäranden skapas med n *x_web_http_client_request_initialize() och* skickas med *hjälp av nx_web_http_client_request_send().* Anpassade HTTP-huvuden kan läggas till i begäran med *hjälp av nx_web_http_client_request_header_add()*.

Användning av den här tjänsten gör att ett program kan lägga till val annat antal anpassade huvuden i begäran. **Detta möjliggör anpassade HTTP-begäranden som är avsedda för specifika program.**

> [!NOTE]
> De nx_web_http_client_ \* _start metoderna tillhandahålls för enkelhetens skull. Alla dessa funktioner använder den här rutinen internt (tillsammans med *nx_web_http_client_request_initialize()) för* att skapa och skicka HTTP-begäranden.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **server_ip** IP-adress för fjärransluten HTTPS-server.
- **server_port** Port på https-fjärrserver (t.ex. 443 för HTTPS).
- **tls_setup** Återanrop som används för att konfigurera TLS-konfiguration. Programmet definierar det här återanropet för att initiera TLS-kryptografi och autentiseringsuppgifter (t.ex. certifikat).
- **wait_option** Definierar hur länge tjänsten ska vänta på att HTTP-klienten hämtar startbegäran. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till och med 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på HTTP-serversvaret.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad anslutning av TLS-session.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_WEB_HTTP_NOT_READY (0x3000A) En annan begäran pågår redan.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
    "https://192.168.1.150/test.txt ", "host.com",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>API för HTTP- och HTTPS-server

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

Ange återanropet för att hämta URL:ens maximala ålder och datum

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Description

Den här tjänsten anger återanropstjänsten som anropas för att hämta den högsta ålder och senaste ändringsdatum för den angivna resursen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **cache_info_get** Pekare till motringning
- **max_age** Pekare till högsta ålder för en resurs
- **data** Pekare till senaste ändringsdatum som returnerades.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ange återanropet
- **NX_PTR_ERROR** (0x07) Ogiltig pekarindata

### <a name="allowed-from"></a>Tillåts från

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

Skicka data från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Description

Den här tjänsten skickar data i det angivna paketet från programmets återanropsrutin. Detta används vanligtvis för att skicka dynamiska data som är associerade med GET/POST-begäranden. Observera att om den här funktionen används ansvarar motringningsfunktionen för att skicka hela svaret i rätt format. Dessutom måste återanropsrutinen returnera statusen för NX_WEB_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **data_ptr** Pekare till de data som ska skickas.
- **data_length** Antal byte som ska skickas.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Serverdata har skickats
- **NX_PTR_ERROR** (0x07) Ogiltig pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa ett svarshuvud i en återanropsfunktion

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Description

Den här tjänsten används i HTTP(S)-serverns återanropsrutin (definieras av programmet) för att generera ett HTTP-svarshuvud. Serverns återanropsrutin anropas när HTTP-servern svarar på klientens GET-, PUT- och DELETE-begäranden som kräver ett HTTP-svar. Den här funktionen tar svarsinformationen från programmet och genererar lämpligt svarshuvud. Mer information om *rutinerna för återanrop av* serverbegäran finns i service nx_web_http_server_create().

Det här API:et är inaktuellt. Utvecklare uppmanas att använda *nx_web_http_server_callback_generate_response_header_extended()*.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **packet_pptr** Pekare en paket pekare som allokerats för meddelande
- **status_code** Ange status för resursen. Exempel:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** Storlek på innehåll i byte
- **content_type** Typ av HTTP, t.ex. "text/oformaterad"
- **additional_header** Pekare till ytterligare rubriktext

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) HTML-rubriken har skapats
- **NX_PTR_ERROR** (0x07) Ogiltig pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa ett svarshuvud i en återanropsfunktion

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

### <a name="description"></a>Description

Den här tjänsten används i HTTP(S)-serverns återanropsrutin (definieras av programmet) för att generera ett HTTP-svarshuvud. Serverns återanropsrutin anropas när HTTP-servern svarar på klientens GET-, PUT- och DELETE-begäranden som kräver ett HTTP-svar. Den här funktionen tar svarsinformationen från programmet och genererar lämpligt svarshuvud. Mer information om *rutinerna för återanrop av* serverbegäran finns i service nx_web_http_server_create().

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **packet_pptr** Pekare en paket pekare som allokerats för meddelande
- **status_code** Ange status för resursen. Exempel:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** Stränglängd för statuskod
- **content_length** Storlek på innehåll i byte
- **content_type** Typ av HTTP, t.ex. "text/oformaterad"
- **content_type_length** Stränglängd för innehållstyp
- **additional_header** Pekare till ytterligare rubriktext
- **additional_header_length** Längden på ytterligare rubriktext

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) HTML-rubriken har skapats
- **NX_PTR_ERROR** (0x07) Ogiltig pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skicka ett HTTP-paket från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett fullständigt HTTP-serversvar från ett HTTP-återanrop. HTTP-servern skickar paketet med NX_WEB_HTTP_SERVER _TIMEOUT_SEND. HTTP-huvudet och data måste läggas till i paketet. Om returstatusen indikerar ett fel måste HTTP-programmet släppa paketet.

Motringning ska returnera NX_WEB_HTTP_CALLBACK_COMPLETED.

I *nx_web_http_server_callback_generate_response_header()* finns ett mer detaljerat exempel.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock
- **packet_ptr** Pekare till paketet som ska skickas

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) HTTP-serverpaket har skickats
- **NX_PTR_ERROR** (0x07) Ogiltig pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skicka svar från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Description

Den här tjänsten skickar den angivna svarsinformationen från programmets återanropsrutin. Detta används vanligtvis för att skicka anpassade svar som är associerade med GET/POST-begäranden. Observera att om den här funktionen används måste återanropsrutinen returnera statusen för NX_WEB_HTTP_CALLBACK_COMPLETED.

Den här tjänsten är inaktuell. Utvecklare uppmanas att använda *nx_web_http_server_callback_response_send_extended().*

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **rubrik** Pekare till svarshuvudsträngen.
- **information** Pekare till informationssträngen.
- **additional_info** Pekare till den ytterligare informationssträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) HTTP-serversvaret har skickats

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skicka svar från återanropsfunktionen

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

### <a name="description"></a>Description

Den här tjänsten skickar den angivna svarsinformationen från programmets återanropsrutin. Detta används vanligtvis för att skicka anpassade svar som är associerade med GET/POST-begäranden. Observera att om den här funktionen används måste återanropsrutinen returnera statusen för NX_WEB_HTTP_CALLBACK_COMPLETED.

Strängarna i rubrik, information och additional_info måste vara NULL-avslutade och längden på varje sträng matchar längden som anges i argumentlistan.

Den här tjänsten *ersätter nx_web_http_server_callback_response_send*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **sidhuvud** Pekare till svarshuvudsträngen.
- **header_length** Längden på svarshuvudsträngen.
- **information** Pekare till informationssträngen.
- **Information_length** Längden på informationssträngen.
- **additional_info** Pekare till den ytterligare informationssträngen.
- **additional_info_length** Längden på den ytterligare informationssträngen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) HTTP-serversvaret har skickats

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten försöker hämta den angivna mängden innehåll från POST- eller PUT HTTP-klientbegäran. Den ska anropas från programmets begäran för att meddela återanropet som angavs när HTTP-servern skapades (*nx_web_http_server_create()*).

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.
- **byte_offset** Antal byte som ska förskjutas till innehållsområdet.
- **destination_ptr** Pekare till målområdet för innehållet.
- **destination_size** Maximalt antal byte som är tillgängliga i målområdet.
- **actual_size** Pekare till målvariabeln som ställs in på den faktiska storleken på det kopierade innehållet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Hämta http-serverinnehåll
- **NX_WEB_HTTP_ERROR** (0x30000) Internt fel för HTTP-server
- **NX_WEB_HTTP_DATA_END** (0x30007) Slut på begärandeinnehåll
- **NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP-server-timeout för att hämta nästa paket med innehåll
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämta innehåll från begäran/stöder ingen innehållslängd

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

### <a name="description"></a>Description

Den här tjänsten är nästan identisk *med nx_web_http_server_content_get()*; Den försöker hämta den angivna mängden innehåll från POST- eller PUT HTTP-klientbegäran. Den hanterar dock begäranden med innehållslängd på noll värde (tom begäran) som en giltig begäran. Den ska anropas från programmets begäran för att meddela återanropet som angavs när HTTP-servern skapades (*nx_web_http_server_create()*).

Den här tjänsten *ersätter nx_web_http_server_content_get*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.
- **byte_offset** Antal byte som ska förskjutas till innehållsområdet.
- **destination_ptr** Pekare till målområdet för innehållet.
- **destination_size** Maximalt antal byte som är tillgängliga i målområdet.
- **actual_size** Pekare till målvariabeln som ställs in på den faktiska storleken på det kopierade innehållet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Http-innehåll hämta
- **NX_WEB_HTTP_ERROR** (0x30000) Internt fel för HTTP-server
- **NX_WEB_HTTP_DATA_END** (0x30007) Slut på begärandeinnehåll
- **NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP-server-timeout för att hämta nästa paket
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämta längden på innehållet i begäran/stöder innehållslängd på noll värde

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Description

Den här tjänsten försöker hämta HTTP-innehållslängden i det angivna paketet. Returvärdet anger slutförandestatus och det faktiska längdvärdet returneras i indatapekaren content_length. Om det inte finns något HTTP-innehåll/innehållslängd = 0 returnerar den här rutinen fortfarande statusen slutförd och content_length pekar på en giltig längd (noll). Den ska anropas från programmets begäran för att meddela återanropet som angavs när HTTP-servern skapades (*nx_web_http_server_create()*).

### <a name="input-parameters"></a>Indataparametrar

- **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.
- **content_length** Pekare till värde som hämtats från fältet Innehållslängd

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Hämta lyckad HTTP-serverinnehållslängd
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Felaktigt HTTP-huvudformat
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd. De *valfria authentication_check* *och request_notify* för programanrop ger programkontroll över de grundläggande åtgärderna för HTTP-servern.

Den här tjänsten används för att skapa HTTP-servrar i klartext och TLS-skyddade HTTPS-servrar. Information om hur du aktiverar HTTPS med TLS finns *i nx_web_http_server_secure_configure()*.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverkontrollblock.
- **http_server_name** Pekar på HTTP-serverns namn.
- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **server_port** TCP-lyssningsport för serverinstans.
- **media_ptr** Pekare till tidigare skapade FileX-medieinstanser.
- **stack_ptr** Pekare till http-serverns trådstackområde.
- **stack_size** Pekare till http-serverns trådstackstorlek.
- **authentication_check** Funktions pekare till programmets autentiseringskontrollrutin. Om detta anges anropas den här rutinen för varje HTTP-klientbegäran. Om den här parametern är NULL utförs ingen autentisering. Den här parametern är inaktuell. Anropa *nx_web_http_server_authenticate_check_set*() i stället.
- **request_notify** Funktionspekare till programmets avvisningsrutin för begäran. Om detta anges anropas den här rutinen före HTTP-serverbearbetningen av begäran. På så sätt kan resursnamnet omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad HTTP-server för att skapa.
- NX_PTR_ERROR (0x07) Ogiltig HTTP-server, IP-adress, media, stack eller paketpoolspekare.
- NX_WEB_HTTP_POOL_ERROR (0x30009) Paketnyttolasten för poolen är inte tillräckligt stor för att innehålla en fullständig HTTP-begäran.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

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

### <a name="description"></a>Description

Den här tjänsten tar bort en http-serverinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP-serverkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av HTTP-server
- NX_PTR_ERROR (0x07) Ogiltig HTTP-server-pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

Hämta plats och längd för entitetsdata

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Description

Den här tjänsten avgör platsen för datastarten i den aktuella multipart-entiteten i de mottagna klientmeddelandena och längden på data som inte inkluderar gränssträngen. Internt uppdaterar HTTP-servern sina egna förskjutningar så att den här funktionen kan anropas igen på samma klientdatagram för meddelanden med flera entiteter. Paketpekaren uppdateras till nästa paket där klientmeddelandet är ett datagram med flera paket.

Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten. Observera också att programmet inte ska släppa paketet som det packet_pptr. Detta görs internt av HTTP-servern.

Se *nx_web_http_server_get_entity_header()* för mer information.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-server
- **packet_pptr** Pekare till platsen för paket pekaren. Observera att programmet inte får släppa det här paketet
- **available_offset** Pekare till förskjutning av entitetsdata från pekaren för paketförberedelser
- **available_length** Pekare till längden på entitetsdata

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Storleken och platsen för entitetsinnehåll har hämtats
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Innehåll för interna multipart-markörer för HTTP-servern finns redan
- NX_WEB_HTTP_ERROR (0x30000) internt HTTP-serverfel
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämta innehållet i entitetsrubriken

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar entitetsrubriken till den angivna bufferten. Internt uppdaterar HTTP Server sina egna pekare för att hitta nästa entitet med flera delar i ett klientdatagram med flera entitetsrubriker. Paketpekaren uppdateras till nästa paket där klientmeddelandet är ett datagram med flera paket.

Observera att NX_WEB_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten. Observera också att programmet inte ska släppa det paket som det packet_pptr.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-server
- **packet_pptr** Pekare till platsen för paket pekaren. Observera att programmet inte får släppa det här paketet
- **entity_header_buffer** Pekare till plats för att lagra entitetsrubrik
- **buffer_size** Storleken på indatabufferten

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Entitetsrubrik har hämtats
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Det går inte att hitta entitetsrubrikfältet
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiden har gått ut för att ta emot nästa paket för multipacket-klientmeddelande
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten
- NX_WEB_HTTP_ERROR (0x30000) Internt HTTP-fel

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ställ in återanropet för att hämta GMT-datum och tid

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Description

Den här tjänsten ställer in återanrop för att hämta GMT-datum och -tid med en tidigare skapad HTTP-server. Den här tjänsten anropas med HTTP-servern skapar ett huvud i HTTP-serversvar till klienten.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-server
- **gmt_get** Pekare till GMT-återanrop
- **datum** Pekare till det datum som hämtades

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har ställt in återanropet
- NX_PTR_ERROR (0x07) Ogiltig paket- eller parameterpekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange återanrop för att hantera ogiltig användare/lösenord

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Description

Den här tjänsten anger återanropet som anropas när ett ogiltigt användarnamn och lösenord tas emot i en klient få, placera eller ta bort begäran, antingen genom sammanfattad eller grundläggande autentisering. HTTP-servern måste ha skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-server
- **invalid_username_password_callback** Pekare till ogiltig användare/skicka återanrop
- **resurs** Pekare till den resurs som anges av klienten
- **client_address** Klientadress
- **request_type** Anger typ av klientbegäran. Kanske:
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har ställt in återanropet
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange ytterligare MIME-kartor för HTML

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Description

Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från de MIME-standardtyper som tillhandahålls av NetX Web HTTP Server. Se *nx_web_http_server_get_type() för* en lista över definierade typer.

När en klientbegäran tas emot, t.ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med hjälp av den ytterligare MIME-mappningsuppsättningen och om ingen matchning hittas letar den efter en matchning i STANDARD-MIME-kartan för HTTP-servern. Om ingen matchning hittas får MIME-typen som standard "text/oformaterad".

Om request notify-funktionen är registrerad på HTTP-servern kan återanropet av begäran meddela *nx_web_http_server_type_get_extended()* för att parsa filtypen.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP Server-instans
- **mime_maps** Pekare till en MIME-kartmatris
- **mime_map_num** Antal MIME-kartor i matris

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad MIME-kartuppsättning för HTTP-server
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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

Allokera ett HTTP(S)-paket

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker allokera ett paket för HTTP(S)-servern.

Observera att om ett efterföljande NetX- eller HTTP Server-API som använder det här paketet som indata **misslyckas,** till exempel nx_packet_data_append eller **nx_web_http_server_callback_packet_send, ansvarar programmet för att släppa paketet. **

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverkontrollblock.
- **packet_ptr** Pekare till allokerat paket.
- **wait_option** Definierar väntetiden i tick om det inte finns några paket tillgängliga i paketpoolen. Väntealternativen definieras på följande sätt:
  - **NX_NO_WAIT** (0x00000000) Om du NX_NO_WAIT här alternativet returneras den anropande tråden omedelbart om begäran inte kan uppfyllas.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Om du NX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Allokera ett lyckat paket
- **NX_NO_PACKET** (0x01) Inget paket tillgängligt
- **NX_WAIT_ABORTED** (0x1A) Den begärda instängningen avbröts av ett anrop *till tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D) Paketstorleken stöder inte protokoll.
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

Extrahera innehållslängd och ange pekare till början av data

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Description

Den här tjänsten extraherar innehållslängden från HTTP-huvudet. Det uppdaterar även det angivna paketet på följande sätt: pekaren för paketförberedelser (början på platsen för paketbufferten att skriva till) är inställd på HTTP-innehållet (data) som precis skickade HTTP-huvudet.

Om början av innehållet inte hittas i det aktuella paketet väntar funktionen på att nästa paket tas emot med hjälp av NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE väntealternativet.

Observera att detta inte ska anropas innan *du anropar nx_web_http_server_get_entity_header()* eftersom det ändrar pekaren för paketförberedelserna förbi entitetsrubriken.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverinstans
- **packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad förberedelse pekare
- **content_length** Pekare till extraherade content_length

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) HTTP-innehållslängd hittades och paketet har uppdaterats
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiden har gått ut och väntar på nästa paket
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten returnerar nästa paket som tas emot på HTTP-serversocketen. Väntealternativet för att ta emot ett paket NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Observera att om det lyckas ansvarar programmet för att släppa paketet.

### <a name="input-parameters"></a>Indataparametrar

- **server_ptr** Pekare till HTTP-serverinstans
- **packet_ptr** Pekare till mottaget paket

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Tog emot nästa HTTP-paket
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiden har gått ut och väntar på nästa paket
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

Hämta parametern från begäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Description

Den här tjänsten försöker hämta den angivna HTTP-URL-parametern i det angivna begärandepaketet. Om den begärda HTTP-parametern inte finns returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND. Den här rutinen ska anropas från programmets begäran meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).

### <a name="input-parameters"></a>Indataparametrar

- **packet_ptr** Pekare till HTTP-klientbegärandepaket. Observera att programmet inte får släppa det här paketet.
- **param_number** Logiskt nummer för parametern med början vid noll, från vänster till höger i parameterlistan.
- **param_ptr** Målområde för att kopiera parametern.
- **param_size** Returnera den totala parameterdatalängden (i byte).
- **max_param_size** Maximal storlek för parameterns målområde.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad HTTP-serverparameter get
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Det gick inte att hitta den angivna parametern
- **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Parametern för begäran avslutades inte korrekt
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten försöker hämta den angivna HTTP-URL-frågan i det angivna begärandepaketet. Om den begärda HTTP-frågan inte finns returnerar den här rutinen statusen NX_WEB_HTTP_NOT_FOUND. Den här rutinen ska anropas från programmets begäran meddela återanrop som anges när HTTP-servern skapas (*nx_web_http_server_create()*).

### <a name="input-parameters"></a>Indataparametrar

- **packet_ptr** Pekare till HTTP-klientbegärandepaket. Observera att programmet inte får släppa det här paketet.
- **query_number** Logiskt nummer för parametern med början vid noll, från vänster till höger i frågelistan.
- **query_ptr** Målområde för att kopiera frågan.
- **query_size** Returnera frågedatastorlek (i byte).
- **max_query_size** Maximal storlek på frågemålet

Området.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad HTTP-serverfråga hämta
- **NX_WEB_HTTP_FAILED** (0x30002) Frågestorlek för liten.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Det gick inte att hitta den angivna frågan
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) Ingen fråga i Klientbegäran
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ange segmenterad överföring för HTTP(S)-svar

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten använder segmenterad överföringskodning för att skicka ett anpassat HTTP(S)-svarsdatapaket *som skapats med nx_web_http_server_response_packet_allocate*() till klienten.

> [!NOTE]
> Om programmet använder segmenterad överföringskodning för att skicka ett svarsdatapaket måste det anropa den här tjänsten efter *anropet nx_web_http_server_response_packet_allocate*() och innan *det anropar nx_web_http_server_callback_packet_send*().

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till HTTP-klientkontrollblock.
- **chunk_size** Storleken på segmentdata i oktett.
- **packet_ptr** Pekare för HTTP(S)-begärandedatapaket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad uppsättning segmenterad.
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

/* At this point, user can fill the data into my_packet. */
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

### <a name="description"></a>Description

Den här tjänsten konfigurerar en tidigare skapad NetX Web HTTP-serverinstans för att använda TLS för säker HTTPS-kommunikation. Parametrarna används för att konfigurera alla möjliga TLS-sessioner med identiskt tillstånd så att varje inkommande HTTPS-klient har konsekvent beteende. Antalet TLS-sessioner styrs med hjälp av NX_WEB_HTTP_SESSION_MAX.

Den kryptografiska rutintabellen (chiffertabell) delas mellan alla TLS-sessioner eftersom den bara innehåller funktionspekare.

Metadata och paket som åter sätts ihop med buffertar fördelas jämnt mellan alla TLS-sessioner. Om buffertstorleken inte är jämnt delbar med antalet sessioner kommer resten att vara oanvänd.

Det skickade identitetscertifikatet används av alla sessioner. Under TLS-åtgärden läses serveridentitetscertifikatet endast från, så kopior behövs inte för varje session.

De betrodda certifikaten läggs till i varje TLS-session på HTTPS-servern. Dessa används för autentisering med klientcertifikat som aktiveras automatiskt när fjärranslutet certifikatutrymme anges.

Fjärrcertifikatmatrisen och bufferten delas som standard mellan alla TLS-sessioner. Fjärrcertifikaten används för klientcertifikatautentisering som aktiveras automatiskt när antalet fjärrcertifikat inte är noll. På grund av att bufferten delas kan vissa sessioner blockeras under certifikatverifieringen.

Om du vill inaktivera klientcertifikatautentisering skickar NX_NULL för remote_certificates-parametern och värdet 0 för remote_certs_num parametern.

Returvärden innehåller eventuella TLS-felkoder som är resultatet av problem i konfigurationen av TLS-sessionerna.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans.
- **crypto_table** Pekare till TLS-chiffertabell.
- **metadata_buffer** Pekare till kryptografisk metadatabuffert.
- **metadata_size** Storlek på buffert för kryptografiska metadata.
- **packet_buffer** TLS-paket sätts ihop på ett åter sätt.
- **packet_buffer** Storleken på TLS-paketbufferten – ska vara lika med (<önskad TLS-buffertstorlek* NX_WEB_HTTP_SESSION_MAX).
- **identity_certificate** TLS-serveridentitetscertifikat – används för alla HTTPS-serversessioner.
- **trusted_certificates** Pekare till matris NX_SECURE_X509_CERT objekt, som används för att verifiera inkommande klientcertifikat om klientcertifikatautentisering är aktiverat genom att skicka ett värde som *inte är noll för remote_certs_num-parametern.*
- **trusted_certs_num** Antal betrodda certifikat i *trusted_certificates* matrisen.
- **remote_certificates** Pekare till matris med NX_SECURE_X509_CERT objekt som används för inkommande klientcertifikat.
- **remote_certs_num** Antal fjärrcertifikat. Bör vara det maximala antalet förväntade certifikat från klienter. Autentisering med klientcertifikat aktiveras automatiskt när detta inte är noll.
- **remote_certificate_buffer** Buffert som ska innehålla inkommande fjärrcertifikat från klienter om autentisering med klientcertifikat är aktiverat. remote_cert_buffer_size storleken på bufferten för fjärrcertifikat. Ska vara lika med (<maximal förväntad \* certifikatstorlek remote_certs_num).


### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad initiering av TLS-sessionen.
- **NX_NOT_CONNECTED** (0x38) Den underliggande TCP-socketen är inte längre ansluten.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) En mottagen TLS-meddelandetyp är felaktig.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Chiffer som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Meddelandebearbetningen under TLS-handskakningen misslyckades.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Ett inkommande meddelande misslyckades med en hash-MAC-kontroll.
- **NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Det gick inte att skicka underliggande TCP-socket.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Ett inkommande meddelande hade ett fält med ogiltig längd.
- **NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) Ett inkommande ChangeCipherSpec-meddelande var felaktigt.
- **NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) Ett inkommande TLS-certifikat kan inte användas för att identifiera TLS-fjärrservern.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Chiffer med offentlig nyckel som tillhandahålls av fjärrvärden stöds inte.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Fjärrvärden har inte angett några chiffer som stöds av NetX Secure TLS-stacken.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Ett mottaget TLS-meddelande hade en okänd TLS-version i huvudet.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Ett mottaget TLS-meddelande hade en känd TLS-version som inte stöds i rubriken.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) En intern TLS-paketallokering misslyckades.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Fjärrvärden angav ett ogiltigt certifikat.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Fjärrvärden skickade en avisering som anger ett fel och avslutar TLS-sessionen.
- **NX_PTR_ERROR** (0x07) Försökte använda en ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

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

### <a name="description"></a>Description

Den här tjänsten startar en http- eller HTTPS-serverinstans som skapats tidigare.

HTTPS-servrar delar samma API som HTTP. Information om hur du aktiverar HTTPS med TLS på en HTTP-server finns *i nx_web_http_server_secure_configure().*

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad HTTP-serverstart
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

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

### <a name="description"></a>Description

Den här tjänsten stoppar den http-serverinstans som du skapade tidigare. Den här rutinen bör anropas innan du tar bort en HTTP Server-instans.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckat HTTP-serverstopp
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

Extrahera filtyp från HTTP-klientbegäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Description

> [!NOTE]
> Den här tjänsten är inaktuell. Användarna uppmanas att använda tjänsten *nx_web_http_server_type_get_extended().*

Den här tjänsten extraherar HTTP-begärandetypen *i bufferten http_type_string* och dess längd *i string_size* från namnet på indatabufferten , vanligtvis URL:en.  Om ingen MIME-karta hittas används som standard typen "text/oformaterad". Annars jämförs den extraherade typen med HTTP-serverns standard-MIME-mappning för en matchning. MIME-standardmappningar i NetX Web HTTP Server är:

- html-text/html
- htm text/html
- txt text/plain
- gif-bild/gif
- jpg-bild/jpeg
- ico-bild/x-ikon

Om det anges söker den även efter en användardefinierad uppsättning ytterligare MIME-kartor. Se *nx_web_http_server_mime_maps_addtional_set() för* mer information om användardefinierade kartor.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans
- **namn** Pekare till buffert för sökning
- **http_type_string** Pekare till extraherad HTML-typsträng
- **string_size** Pekare för att returnera stränglängden för extraherad HTML-typ.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad extrahering av typen
- NX_PTR_ERROR (0x07) Ogiltig pekare
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Standardvärdet "text/oformaterad" returneras.

### <a name="allowed-from"></a>Tillåts från

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

Extrahera filtyp från HTTP-klientbegäran

### <a name="prototype"></a>Prototyp

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Description

Den här tjänsten extraherar HTTP-begärandetypen *i bufferten http_type_string* och dess längd *i string_size* från namnet på indatabufferten , vanligtvis URL:en.  Om ingen MIME-karta hittas används som standard typen "text/oformaterad". Annars jämförs den extraherade typen med HTTP-serverns standard-MIME-mappning för en matchning. Mime-standardkartorna i NetX Web HTTP Server är:

- html-text/html
- htm text/html
- txt text/plain
- gif-bild/gif
- jpg-bild/jpeg
- ico-bild/x-ikon

Om det anges söker den även i en användardefinierad uppsättning ytterligare MIME-kartor. Se *nx_web_http_server_mime_maps_addtional_set() för* mer information om användardefinierade kartor.

Den här tjänsten *ersätter nx_web_http_server_type_get*(). Den här versionen kräver att anropare tillhandahåller längdinformation till funktionen.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans
- **namn** Pekare till buffert för sökning
- **name_length** Namnlängd
- **http_type_string** Pekare till extraherad HTML-typsträng
- **http_type_string_max_size** Storlek på http_type_string buffertstorlek
- **string_size** Pekare för att returnera extraherad HTML-typsträng

Längd.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad extrahering av typen
- NX_PTR_ERROR (0x07) Ogiltig pekare
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Standardvärdet "text/oformaterad" returneras.

### <a name="allowed-from"></a>Tillåts från

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

Ange sammanfattad funktion för att autentisera motringning

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

### <a name="description"></a>Description

Den här tjänsten anger återanropet som anropas när sammanfattad autentisering utförs.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans
- **digest_authenticate_callback** Pekare för att sammanfatta autentisera återanrop

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har ställt in återanropet
- NX_PTR_ERROR (0x07) Ogiltig pekare
- NX_NOT_SUPPORTED (0x4B) Sammanfattad autentisering är inte aktiverat

### <a name="allowed-from"></a>Tillåts från

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

Ange sammanfattad funktion för att autentisera motringning

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

### <a name="description"></a>Description

Den här tjänsten anger återanropet som anropas när autentiseringskontrollen utförs.

### <a name="input-parameters"></a>Indataparametrar

- **http_server_ptr** Pekare till HTTP Server-instans
- **authenticate_check_externded** Pekare för att autentisera check motringning

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Har ställt in återanropet
- NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

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
