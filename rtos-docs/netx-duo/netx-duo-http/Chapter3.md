---
title: Kapitel 3 – Beskrivning av Azure RTOS NETX Duo HTTP Services
description: Det här kapitlet innehåller en beskrivning av alla http-tjänster för Azure RTOS NetX Duo (anges nedan) i alfabetisk ordning förutom att motsvarigheten "NetX" (endast IPv4) för samma tjänst är sammankopplad).
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 09add7bb20a8e104ba41583c0dbf4d574b8e6c9e6b3a3deed71d8fa8c8942ce2
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796488"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NETX Duo HTTP Services

Det här kapitlet innehåller en beskrivning av alla http-tjänster för Azure RTOS NetX Duo (anges nedan) i alfabetisk ordning förutom att motsvarigheten "NetX" (endast IPv4) för samma tjänst är sammankopplad).

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i BOLD av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

**HTTP-klienttjänster:**

- **nx_http_client_create Skapa** *en HTTP-klientinstans*
- **nx_http_client_delete Ta** *bort en HTTP-klientinstans*
- **nx_http_client_get_start** *Starta en HTTP GET-begäran (endast IPv4)*
- **nx_http_client_get_start_extended** *Starta en HTTP GET-begäran (endast IPv4)*
- **nxd_http_client_get_start** *Starta en HTTP GET-begäran (IPv4 eller IPv6)*
- **nxd_http_client_get_start_extended** *Starta en HTTP GET-begäran (IPv4 eller IPv6)*
- **nx_http_client_get_packet** *Hämta nästa resursdatapaket*
- **nx_http_client_put_start** *Starta en HTTP PUT-begäran (endast IPv4)*
- **nx_http_client_put_start_extended** *Starta en HTTP PUT-begäran (endast IPv4)*
- **nxd_http_client_put_start** *Starta en HTTP PUT-begäran (IPv4 eller IPv6)*
- **nxd_http_client_put_start_extended** *Starta en HTTP PUT-begäran (IPv4 eller IPv6)*
- **nx_http_client_put_packet Skicka** *nästa resursdatapaket*
- **nx_http_client_set_connect_port** *Ändra porten för att ansluta till HTTP-servern*

**HTTP-servertjänster:**

- **nx_http_server_cache_info_callback_set Ange** *återanrop för att hämta ålder och senaste ändringsdatum för angiven URL*
- **nx_http_server_callback_data_send skicka** *HTTP-data från återanropsfunktionen*
- **nx_http_server_callback_generate_response_header Skapa** *svarshuvud i återanropsfunktioner*
- **nx_http_server_callback_generate_response_header_extended Skapa** *svarshuvud i återanropsfunktioner*
- **nx_http_server_callback_packet_send Skicka** *ett HTTP-paket från ett HTTP-återanrop*
- **nx_http_server_callback_response_send skicka** *svar från återanropsfunktionen*
- **nx_http_server_callback_response_send_extended skicka** *svar från återanropsfunktionen*
- **nx_http_server_content_get** *Hämta innehåll från begäran*
- **nx_http_server_content_get_extended** *Hämta innehåll från begäran; stöder tomma begäranden (ingen innehållslängd)*
- **nx_http_server_content_length_get** *Hämta längden på innehållet i begäran*
- **nx_http_server_content_length_get_extended** *Hämta längden på innehållet i begäran. stöder tomma begäranden (ingen innehållslängd)*
- **nx_http_server_create Skapa** *en HTTP-serverinstans*
- **nx_http_server_delete** * Ta bort en HTTP Server-instans*
- **nx_http_server_get_entity_content returnera** *storlek och plats för entitetsinnehåll i URL*
- **nx_http_server_get_entity_header extrahera** *URL-entitetsrubrik till angiven buffert*
- **nx_http_server_gmt_callback_set Ställ in** *återanrop för att hämta DATUM och tid för GMT*
- **nx_http_server_invalid_userpassword_notify_set Ange** *återanrop för när ogiltigt användarnamn och lösenord tas emot i en klientbegäran*
- **nx_http_server_mime_maps_additional_set** *Definiera ytterligare mime-kartor för HTML*
- **nx_http_server_packet_content_find Extrahera** *innehållslängd i HTTP-huvud och ange pekare till början av innehållsdata*
- **nx_http_server_packet_get ta** *emot klientpaket direkt*
- **nx_http_server_param_get** *hämta parametern från begäran*
- **nx_http_server_query_get** *Hämta fråga från begäran*
- **nx_http_server_start** *starta HTTP-servern*
- **nx_http_server_stop** *stoppa HTTP-servern*
- **nx_http_server_type_get (inaktuell) Extrahera** *HTTP-typ, t.ex. text/oformaterad från rubrik*
- **nx_http_server_type_get_extended** *HTTP-typ, t.ex. text/oformaterad från sidhuvud*
- **nx_http_server_digest_authenticate_notify_set Ange** *sammanfattad funktion för att autentisera motringning*
- **nx_http_server_authentication_check_set Ange** *återanropsfunktion för autentiseringskontroll*

## <a name="nx_http_client_create"></a>nx_http_client_create

Skapa en PPPoE-klientinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a>Description

Den här tjänsten skapar en HTTP-klientinstans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **client_name** Namnet på HTTP-klientinstansen.
 - **ip_ptr** Pekare till IP-instans.
 - **pool_ptr** Pekare till standardpaketpoolen. Observera att paketen i den här poolen måste ha en nyttolast som är tillräckligt stor för att hantera hela svarshuvudet. Detta definieras av NX_HTTP_CLIENT_MIN_PACKET_SIZE i *nx_http.h*.
 - **window_size** Storleken på klientens TCP-socket-mottagningsfönster.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad HTTP-klient skapas
 - NX_PTR_ERROR (0x07) Ogiltig HTTP-, ip_ptr- eller paketpoolspekare
 - NX_HTTP_POOL_ERROR (0xE9) Ogiltig nyttolaststorlek i paketpoolen

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

Ta bort en HTTP-klientinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en http-klientinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av HTTP-klient
 - NX_PTR_ERROR (0x07) Ogiltig HTTP-pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

Starta en HTTP GET-begäran via IPv4

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen NX_SUCCESS kan programmet göra flera anrop *för att nx_http_client_get_packet* hämta datapaket som motsvarar det begärda resursinnehållet.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` GET-begäranden.

Den här tjänsten fungerar endast över IPv4-nätverk. För program som behöver ansluta till IPv6-nätverk *nxd_http_client_get_start_extended()* användas.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera *till nx_http_client_get_start_extended()* *eller nxd_http_client_get_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **ip_address** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng för begärd resurs.
 - **input_ptr** Pekare till ytterligare data för GET-begäran. Detta är valfritt. Om det är giltigt placeras angivna indata i meddelandets innehållsområde och en POST används i stället för en GET-åtgärd.
 - **input_size** Antal byte i valfria ytterligare indata som pekar på ```input_ptr``` .
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:

    - **time out-värde** (0x00000001 via 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) har skickat HTTP-klienten. GET-startmeddelande.
 - **NX_HTTP_ERROR** (0xE0) Internt HTTP-klientfel
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klient inte klar
 - **NX_HTTP_FAILED** (0xE2) HTTP-klientfel som kommunicerar med HTTP-servern.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Ogiltigt namn och/eller lösenord.
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

Starta en HTTP GET-begäran via IPv4

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Om den här rutinen NX_SUCCESS kan programmet göra flera anrop *för att nx_http_client_get_packet* hämta datapaket som motsvarar det begärda resursinnehållet.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` GET-begäranden.

Den här tjänsten fungerar endast över IPv4-nätverk. För program som behöver ansluta till IPv6-nätverk *nxd_http_client_get_start_extended()* användas.

Den här tjänsten *ersätter nx_http_client_get_start()*. Det kräver att anroparen anger längden på resursen, användarnamnet och lösenordet.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **ip_address** HTTP-serverns IP-adress.
 - **resurs pekare** till URL-sträng för begärd resurs.
 - **resource_length** Längden på URL-strängen för den begärda resursen.
 - **input_ptr** Pekare till ytterligare data för GET-begäran. Detta är valfritt. Om det är giltigt placeras angivna indata i meddelandets innehållsområde och en POST används i stället för en GET-åtgärd.
 - **input_size** Antal byte i valfria ytterligare indata som pekar på ```input_ptr``` .
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **username_length** Längden på det valfria användarnamnet för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **password_length** Längden på valfritt lösenord för autentisering.
 - **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 via 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) har skickat HTTP-klienten. GET-startmeddelande
 - **NX_HTTP_ERROR** (0xE0) Internt HTTP-klientfel
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klient inte klar
 - **NX_HTTP_FAILED** (0xE2) HTTP-klientfel som kommunicerar med HTTP-servern.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Ogiltigt namn och/eller lösenord.
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a>nxd_http_client_get_start

Skicka en HTTP GET-begäran (IPv4 eller IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Den kan användas för att ansluta till IPv4- eller IPv6-nätverk. Om den här rutinen NX_SUCCESS kan programmet göra flera anrop *för att nx_http_client_get_packet* hämta datapaket som motsvarar det begärda resursinnehållet.

> [!NOTE]
>Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` GET-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nxd_http_client_get_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **Server_ip** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng för den begärda resursen.
 - **input_ptr** Pekare till ytterligare data för GET-begäran. Detta är valfritt. Om det är giltigt placeras angivna indata i meddelandets innehållsområde och en POST används i stället för en GET-åtgärd.
 - **input_size** Antal byte i valfria ytterligare indata som pekar på ```input_ptr``` .
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **username_length** Längden på det valfria användarnamnet för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **password_length** Längden på valfritt lösenord för autentisering.
 - **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens startbegäran. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 via 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Get-begäran har skickats
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Lösenordet överskrider buffertstorleken
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klient inte klar
 - **NX_HTTP_FAILED** (0xE2) Ogiltiga paketparametrar.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Ogiltigt namn eller lösenord
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a>nxd_http_client_get_start_extended

Skicka en HTTP GET-begäran (IPv4 eller IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skapa och skicka en GET-begäran med resursen som anges av "resurs"-pekaren på den tidigare skapade HTTP-klientinstansen. Den kan användas för att ansluta till IPv4- eller IPv6-nätverk. Om rutinen returnerar NX_SUCCESS kan programmet sedan göra flera anrop *till nx_http_client_get_packet* för att hämta datapaket som motsvarar det begärda resursinnehållet.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` GET-begäranden.

Den här tjänsten *ersätter nxd_http_client_get_start()*. Det kräver att anroparen anger längden på resursen, användarnamnet och lösenordet.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **Server_ip** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng för den begärda resursen.
 - **resource_length** Längden på URL-strängen för den begärda resursen.
 - **input_ptr** Pekare till ytterligare data för GET-begäran. Detta är valfritt. Om det är giltigt placeras angivna indata i meddelandets innehållsområde och en POST används i stället för en GET-åtgärd.
 - **input_size** Antalet byte i valfria ytterligare indata som pekar på ```input_ptr``` .
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **username_length** Längden på ett valfritt användarnamn för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **password_length** Längden på ett valfritt lösenord för autentisering.
 - **wait_option** Definierar hur länge tjänsten ska vänta internt för att bearbeta HTTP-klientens start. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 till 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick för att förbli pausat medan du väntar på HTTP-serversvaret.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Get-begäran har skickats
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Lösenordet överskrider buffertstorleken
 - **HTTP-klienten** NX_HTTP_NOT_READY (0xEA) inte klar
 - **NX_HTTP_FAILED** (0xE2) Ogiltiga paketparametrar.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Ogiltigt namn eller lösenord
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

Hämta nästa resursdatapaket

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a>Description

Den här tjänsten hämtar nästa paket med innehåll för resursen som begärdes av det tidigare *nx_http_client_get_start anropet.* Efterföljande anrop till den här rutinen ska göras tills returstatusen för NX_HTTP_GET_DONE tas emot.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **packet_ptr** Mål för paket pekare som innehåller partiellt resursinnehåll.
 - **wait_option** Definierar hur länge tjänsten ska vänta på HTTP-klientens get-paket. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 till 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick för att förbli pausat medan du väntar på HTTP-serversvaret.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad HTTP-klient får paket.
 - **NX_HTTP_GET_DONE** (0xEC) HTTP-klienten får paket är klar
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klienten är inte i get-läge.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Ogiltig paketlängd
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

Starta en HTTP PUT-begäran via IPv4

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen. Om den här rutinen lyckas bör programkoden göra efterföljande anrop *till nx_http_client_put_packet()-rutinen* för att faktiskt skicka resursinnehållet till HTTP-servern.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` PUT-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nxd_http_client_put_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **ip_address** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng för den begärda resursen.
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **total_bytes** Totalt antal byte för resursen som skickas. Observera att den kombinerade längden för alla paket som skickas via efterföljande anrop *till nx_http_client_put_packet* måste vara lika med det här värdet.
 - **wait_option** Definierar hur länge tjänsten ska vänta tills HTTP-klientens PUT startar. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 till 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick för att förbli pausat medan du väntar på HTTP-serversvaret

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Put-begäran har skickats
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) Användarnamnet är för stort för buffert
 - **HTTP-klienten** NX_HTTP_NOT_READY (0xEA) inte klar
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

Starta en HTTP PUT-begäran via IPv4

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skicka en PUT-begäran med den angivna resursen till HTTP-servern på den angivna IP-adressen. Om den här rutinen lyckas ska programkoden göra efterföljande *anrop till nx_http_client_put_packet()-rutinen* för att faktiskt skicka resursinnehållet till HTTP-servern.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` PUT-begäranden.

Den här tjänsten *ersätter nx_http_client_put_start()*. Det kräver att anroparen anger längden på resursen, användarnamnet och lösenordet.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **ip_address** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng för den begärda resursen.
 - **resource_length** Längden på URL-strängen som resursen ska skicka till servern.
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **username_length** Längden på det valfria användarnamnet för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **password_length** Längden på valfritt lösenord för autentisering.
 - **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden på alla paket som skickas via efterföljande anrop *till nx_http_client_put_packet* måste vara lika med det här värdet.
 - **wait_option** Definierar hur länge tjänsten ska vänta tills HTTP-klientens PUT startar. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 via 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Put-begäran har skickats
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) Användarnamnet är för stort för buffert
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klient inte klar
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a>nxd_http_client_put_start

Starta en HTTP PUT-begäran (IPv4 eller IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker PLACERA (skicka) den angivna resursen på HTTP-servern på den angivna IP-adressen via IPv6. Om den här rutinen lyckas ska programkoden göra efterföljande *anrop till nx_http_client_put_packet()-rutinen* för att faktiskt skicka resursinnehållet till HTTP-servern.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` PUT-begäranden.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nxd_http_client_put_start_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **server_ip** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng som resursen ska skicka till servern.
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden på alla paket som skickas via efterföljande anrop *till nx_http_client_put_packet* måste vara lika med det här värdet.
 - **wait_option** Definierar hur länge tjänsten ska vänta tills HTTP-klientens PUT startar. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 via 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) SKICKADE HTTP-klientens PUT-begäran
 - **NX_HTTP_ERROR** (0xE0) internt fel för HTTP-klienten
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klient inte klar
 - **NX_HTTP_FAILED** (0xE2) HTTP-klientfel som kommunicerar med HTTP-servern
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a>nxd_http_client_put_start_extended

Starta en HTTP PUT-begäran (IPv4 eller IPv6)

### <a name="prototype"></a>Prototyp

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker PLACERA (skicka) den angivna resursen på HTTP-servern på den angivna IP-adressen via IPv6. Om den här rutinen lyckas ska programkoden göra efterföljande *anrop till nx_http_client_put_packet()-rutinen* för att faktiskt skicka resursinnehållet till HTTP-servern.

> [!NOTE]
> Resurssträngen kan referera till en lokal fil, t.ex. eller referera till en annan URL, t.ex. om HTTP-servern anger att den stöder refererade ``` “/index.htm” ``` ```http://abc.website.com/index.htm``` PUT-begäranden.

Den här tjänsten *ersätter nxd_http_client_put_start()*. Det kräver att anroparen anger längden på resursen, användarnamnet och lösenordet.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **ip_address** HTTP-serverns IP-adress.
 - **resurs** Pekare till URL-sträng för den begärda resursen.
 - **resource_length** Längden på URL-strängen som resursen ska skicka till servern.
 - **användarnamn** Pekare till valfritt användarnamn för autentisering.
 - **username_length** Längden på det valfria användarnamnet för autentisering.
 - **lösenord** Pekare till valfritt lösenord för autentisering.
 - **password_length** Längden på valfritt lösenord för autentisering.
 - **total_bytes** Totalt antal byte av resurs som skickas. Observera att den kombinerade längden på alla paket som skickas via efterföljande anrop *till nx_http_client_put_packet* måste vara lika med det här värdet.
 - **wait_option** Definierar hur länge tjänsten ska vänta tills HTTP-klientens PUT startar. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 via 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan HTTP-serversvaret väntar.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) SKICKADE HTTP-klientens PUT-begäran
 - **NX_HTTP_ERROR** (0xE0) internt fel för HTTP-klienten
 - **NX_HTTP_NOT_READY** (0xEA) HTTP-klient inte klar
 - NX_HTTP_FAILED (0xE2) HTTP-klientfel vid kommunikation med HTTP-servern
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_SIZE_ERROR (0x09) Ogiltig total storlek på resursen
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

Skicka nästa resursdatapaket

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker skicka nästa paket med resursinnehåll till HTTP-servern.

> [!NOTE]
> Den här rutinen bör anropas repetitivt tills den kombinerade längden på de skickade paketen är lika med den "total_bytes" som angavs i *föregående nx_http_client_put_start anrop.*

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **packet_ptr** Pekar till nästa innehåll i resursen som skickas till HTTP-servern.
 - **wait_option** Definierar hur länge tjänsten ska vänta internt för att bearbeta HTTP-klientens PUT-paket. Väntealternativen definieras på följande sätt:
    - **time out-värde** (0x00000001 till 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills HTTP-servern svarar på begäran.

    Om du väljer ett numeriskt värde (0x1-0xFFFFFFFE) anges det maximala antalet timer tick för att förbli pausat medan du väntar på HTTP-serversvaret.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) SKICKADE HTTP-klientpaket.
 - **HTTP-klienten** NX_HTTP_NOT_READY (0xEA) inte klar
 - **felkod NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) mottagen server
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Ogiltig paketlängd
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Ogiltigt namn och/eller lösenord
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Servern svarar innan PUT är klar
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_INVALID_PACKET (0x12) Paket för litet för TCP-huvud
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

Ange anslutningsporten till servern

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a>Description

Den här tjänsten ändrar anslutningsporten vid anslutning till HTTP-servern till den angivna porten vid körning. Annars är standardinställningen för anslutningsporten 80. Detta måste anropas innan *nx_http_client_get_start()* *och nx_http_client_put_start()* t.ex. när HTTP-klienten ansluter till servern.

### <a name="input-parameters"></a>Indataparametrar

 - **client_ptr** Pekare till HTTP-klientkontrollblock.
 - **port** Port för att ansluta till servern.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Ändra port
 - NX_INVALID_PORT (0x46) Porten överskrider maxvärdet (0xFFFF) eller är noll
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar, initiering

### <a name="example"></a>Exempel

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

Ange återanropet för att hämta URL:ens maximala ålder och datum

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a>Description

Den här tjänsten anger återanropstjänsten som anropas för att hämta den högsta ålder och senaste ändringsdatum för den angivna resursen.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **cache_info_get** Pekare till motringning
 - **max_age** Pekare till högsta ålder för en resurs
 - **data** Pekare till senaste ändringsdatum som returnerades.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Konfigurera motringning
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering

### <a name="example"></a>Exempel

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a>nx_http_server_callback_data_send

Skicka data från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a>Description

Den här tjänsten skickar data i det angivna paketet från programmets återanropsrutin. Detta används vanligtvis för att skicka dynamiska data som är associerade med GET/POST-begäranden.

> [!NOTE]
> Om den här funktionen används ansvarar motringningsfunktionen för att skicka hela svaret i rätt format. Dessutom måste återanropsrutinen returnera statusen för NX_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **data_ptr** Pekare till de data som ska skickas.
 - **data_length**  Antal byte som ska skickas.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Serverdata har skickats
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

Skapa ett svarshuvud i en återanropsfunktion

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Description

Den här tjänsten anropar den *interna _nx_http_server_generate_response_header* när HTTP-servern svarar på begäranden om att hämta, placera och ta bort klienten. Den är avsedd att användas i återanropsfunktioner för HTTP-server när HTTP-serverprogrammet utformar sitt svar till klienten.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nxd_http_server_callback_generate_response_header_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **packet_pptr** Pekare en paket pekare som allokerats för meddelande
 - **status_code** Ange status för resursen. Exempel:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **content_length** Storleken på innehåll i byte
 - **content_type** Typ av HTTP, t.ex. "text/oformaterad"
 - **additional_header** Pekare till ytterligare rubriktext

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Har skapats
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a>nx_http_server_callback_generate_response_header_extended

Skapa ett svarshuvud i en återanropsfunktion

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a>Description

Den här tjänsten anropar den *interna funktionen _nx_http_server_generate_response_header()* när HTTP-servern svarar på klientens begäranden om att hämta, placera och ta bort. Den är avsedd att användas i återanropsfunktioner för HTTP-server när HTTP-serverprogrammet utformar sitt svar till klienten.

Den här tjänsten *ersätter nx_http_server_callback_generate_response_header()*. Den här versionen tillhandahåller ytterligare längdinformation till återanropsfunktionen.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **packet_pptr** Pekare en paket pekare som allokerats för meddelande
 - **status_code** Ange status för resursen. Exempel:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **status_code** Längden på statuskoden
 - **content_length** Storleken på innehåll i byte
 - **content_type** Typ av HTTP, t.ex. "text/oformaterad"
 - **content_type_length** Längden på HTTP-typen
 - **additional_header** Pekare till ytterligare rubriktext
 - **additional_header_length** Längden på ytterligare rubriktext

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Har skapats
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a>nx_http_server_callback_packet_send

Skicka ett HTTP-paket från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skickar ett fullständigt HTTP-serversvar från ett HTTP-återanrop. HTTP-servern skickar paketet med NX_HTTP_SERVER _TIMEOUT_SEND. HTTP-huvudet och data måste läggas till i paketet. Om returstatusen indikerar ett fel måste HTTP-programmet släppa paketet.

Motringning ska returnera NX_HTTP_CALLBACK_COMPLETED.

I *nx_http_server_callback_generate_response_header() finns* ett mer detaljerat exempel.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **packet_ptr** Pekare till det paket som ska skickas

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Serverpaket har skickats
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

Skicka svar från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a>Description

Den här tjänsten skickar den angivna svarsinformationen från programmets återanropsrutin. Detta används vanligtvis för att skicka anpassade svar som är associerade med GET/POST-begäranden.

> [!NOTE]
> Om den här funktionen används måste återanropsrutinen returnera statusen för NX_HTTP_CALLBACK_COMPLETED.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nxd_http_server_callback_response_send_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **rubrik** Pekare till svarshuvudsträngen.
 - **information** Pekare till informationssträngen.
 - **additional_info** Pekare till den ytterligare informationssträngen.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Serversvaret har skickats

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a>nx_http_server_callback_response_send_extended

Skicka svar från återanropsfunktionen

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a>Description

Den här tjänsten skickar den angivna svarsinformationen från programmets återanropsrutin. Detta används vanligtvis för att skicka anpassade svar som är associerade med GET/POST-begäranden.

> [!NOTE]
> Om den här funktionen används måste återanropsrutinen returnera statusen för NX_HTTP_CALLBACK_COMPLETED.

Den här tjänsten *ersätter nx_http_server_callback_response_send()*. Den här versionen tar ytterligare längdinformation som argument.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **rubrik** Pekare till svarshuvudsträngen.
 - **header_length** Längden på svarshuvudsträngen.
 - **information** Pekare till informationssträngen.
 - **information_length** Längden på informationssträngen.
 - **additional_info** Pekare till den ytterligare informationssträngen.
 - **additional_info_length** Längden på den ytterligare informationssträngen.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Serversvaret har skickats

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a>nx_http_server_content_get

Hämta innehåll från begäran

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a>Description

Den här tjänsten försöker hämta den angivna mängden innehåll från POST- eller PUT HTTP-klientbegäran. Den ska anropas från programmets begäran för att meddela återanrop som angavs när HTTP-servern skapades (*nx_http_server_create*).

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_http_server_content_get_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.
 - **byte_offset** Antal byte som ska förskjutas till innehållsområdet.
 - **destination_ptr** Pekare till målområdet för innehållet.
 - **destination_size** Maximalt antal byte som är tillgängliga i målområdet.
 - **actual_size** Pekare till målvariabeln som ställs in på den faktiska storleken på det kopierade innehållet.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Http-serverinnehåll hämta
 - **NX_HTTP_ERROR** (0xE0) internt HTTP-serverfel
 - **NX_HTTP_DATA_END** (0xE7) Slut på begärandeinnehåll
 - **NX_HTTP_TIMEOUT** (0xE1) HTTP-server-timeout för att hämta nästa paket med innehåll
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

Hämta innehåll från begäran/stöder ingen innehållslängd

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a>Description

Den här tjänsten är nästan *identisk med nx_http_server_content_get().* Den försöker hämta den angivna mängden innehåll från POST- eller PUT HTTP-klientbegäran. Den hanterar dock begäranden med innehållslängd på noll värde (tom begäran) som en giltig begäran. Den ska anropas från programmets begäran för att meddela återanrop som angavs när HTTP-servern skapades (*nx_http_server_create()*).

Den här tjänsten *ersätter nx_http_server_content_get()*. Den här versionen kräver att anroparen tillhandahåller ytterligare längdinformation.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverkontrollblock.
 - **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.
 - **byte_offset** Antal byte som ska förskjutas till innehållsområdet.
 - **destination_ptr** Pekare till målområdet för innehållet.
 - **destination_size** Maximalt antal byte som är tillgängliga i målområdet.
 - **actual_size** Pekare till målvariabeln som ställs in på den faktiska storleken på det kopierade innehållet.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Http-innehåll hämta
 - **NX_HTTP_ERROR** (0xE0) internt HTTP-serverfel
 - **NX_HTTP_DATA_END** (0xE7) Slut på begärandeinnehåll
 - **NX_HTTP_TIMEOUT** (0xE1) HTTP-server-timeout för att hämta nästa paket
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

Hämta längden på innehållet i begäran

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten försöker hämta HTTP-innehållslängden i det angivna paketet. Om det inte finns något HTTP-innehåll returnerar den här rutinen värdet noll. Den ska anropas från programmets begäran för att meddela återanrop som angavs när HTTP-servern skapades (*nx_http_server_create()*).

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_http_server_content_length_get_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.

### <a name="return-values"></a>Returvärden

 - **innehållslängd** Vid fel returneras värdet noll  

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

Hämta längden på innehållet i begäran/stöder innehållslängd på noll värde

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a>Description

Den här tjänsten liknar *nx_http_server_content_length_get, försöker* hämta HTTP-innehållslängden i det angivna paketet. Returvärdet anger dock slutförandestatusen och det faktiska längdvärdet returneras i indata pekaren ```content_length``` . Om det inte finns något HTTP-innehåll/innehållslängd = 0 returnerar den här rutinen fortfarande statusen slutförd och content_length pekar på en giltig längd (noll). Den ska anropas från programmets begäran för att meddela återanrop som angavs när HTTP-servern skapades (*nx_http_server_create*).

Den här tjänsten *ersätter nx_http_server_content_length_get()*.

### <a name="input-parameters"></a>Indataparametrar

 - **packet_ptr** Pekare till HTTP-klientens begärandepaket. Observera att det här paketet inte får släppas av begäran för att meddela återanrop.
 - **content_length** Pekare till värde som hämtats från fältet Innehållslängd

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Hämta innehåll för lyckad server
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Felaktigt HTTP-huvudformat
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

Skapa en HTTP-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

Den här tjänsten skapar en HTTP-serverinstans som körs i kontexten för en egen ThreadX-tråd. De *valfria authentication_check* och request_notify för programanrop ger programkontroll över HTTP-serverns grundläggande åtgärder.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP-serverkontrollblock.
 - **http_server_name** Pekare till HTTP-serverns namn.
 - **ip_ptr** Pekare till ip-instans som skapats tidigare.
 - **media_ptr** Pekare till tidigare skapad FileX-medieinstans.
 - **stack_ptr** Pekare till http-serverns trådstackområde.
 - **stack_size** Pekare till http-serverns trådstackstorlek.
 - **authentication_check** Funktions pekare till programmets autentiseringskontrollrutin. Om detta anges anropas den här rutinen för varje HTTP-klientbegäran. Om den här parametern är NULL utförs ingen autentisering.
 - **request_notify** Funktions pekare till programmets avvisningsrutin för begäran. Om detta anges anropas den här rutinen före HTTP-serverbearbetningen av begäran. På så sätt kan resursnamnet omdirigeras eller fält i en resurs uppdateras innan HTTP-klientbegäran slutförs.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad HTTP-server skapas.
 - NX_PTR_ERROR (0x07) Ogiltig HTTP-server, IP-adress, media, stack eller paketpoolspekare.
 - NX_HTTP_POOL_ERROR (0xE9) Paketnyttolasten för poolen är inte tillräckligt stor för att innehålla fullständig HTTP-begäran.

### <a name="allowed-from"></a>Tillåts från

Initiering, trådar

### <a name="example"></a>Exempel

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

Ta bort en HTTP-serverinstans

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en http-serverinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP-serverkontrollblock.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av HTTP-server
 - NX_PTR_ERROR (0x07) Ogiltig HTTP-server pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

Hämta plats och längd för entitetsdata

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a>Description

Den här tjänsten bestämmer platsen för datastarten i den aktuella entiteten med flera delar i de mottagna klientmeddelandena och längden på data som inte inkluderar gränssträngen. Internt uppdaterar HTTP-servern sina egna förskjutningar så att den här funktionen kan anropas igen på samma klientdatagram för meddelanden med flera entiteter. Paket pekaren uppdateras till nästa paket där klientmeddelandet är ett datagram med flera paket.

> [!NOTE]
> NX_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.

Mer [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) finns i nx_http_server_get_entity_header mer information.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-server
 - **packet_pptr** Pekare till platsen för paket pekaren. Observera att programmet inte ska släppa det här paketet.
 - **available_offset** Pekare till förskjutning av entitetsdata från pekaren för paketförberedelser
 - **available_length** Pekare till längden på entitetsdata

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Hämtad storlek och plats för entitetsinnehåll
 - **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Innehåll för interna multipartmarkörer för HTTP-servern finns redan
 - NX_HTTP_ERROR (0xE0) Internt HTTP-fel
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

Hämta innehållet i entitetsrubriken

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a>Description

Den här tjänsten hämtar entitetsrubriken till den angivna bufferten. Internt uppdaterar HTTP-servern sina egna pekare för att hitta nästa entitet med flera delar i ett klientdatagram med flera entitetsrubriker. Paket pekaren uppdateras till nästa paket där klientmeddelandet är ett datagram med flera paket.

> [!NOTE]
> NX_HTTP_MULTIPART_ENABLE måste vara aktiverat för att använda den här tjänsten.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-server
 - **packet_pptr** Pekare till platsen för paket pekaren. Observera att programmet inte ska släppa det här paketet.
 - **entity_header_buffer** Pekare till plats för att lagra entitetsrubrik
 - **buffer_size** Storleken på indatabufferten

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Entitets heade har hämtats
 - **NX_HTTP_NOT_FOUND** **(0xE6) Det går** inte att hitta entitetsrubrikfältet
 - **NX_HTTP_TIMEOUT** **(0xE1) Tiden** har gått ut för att ta emot nästa paket för multipacket-klientmeddelande
 - NX_HTTP_ERROR (0xE0) Internt HTTP-fel
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

Ställ in återanropet för att hämta datum och tid för GMT

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Description

Den här tjänsten ställer in återanrop för att hämta DATUM och tid för GMT med en http-server som skapats tidigare. Den här tjänsten anropas med HTTP-servern skapar ett -huvud i HTTP-serversvar till klienten.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-server
 - **gmt_getv** Pekare till GMT-återanrop
 - **datev** Pekare till det datum som hämtades

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Har ställt in återanropet
 - NX_PTR_ERROR (0x07) Ogiltig paket- eller parameterpekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

Ange motringning till för att hantera ogiltig användare/lösenord

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a>Description

Den här tjänsten anger återanropet som anropas när ett ogiltigt användarnamn och lösenord tas emot i en klient få, placera eller ta bort begäran, antingen genom sammanfattad eller grundläggande autentisering. HTTP-servern måste ha skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-server
 - **invalid_username_password_callback** Pekare till ogiltig användare/skicka återanrop
 - **resurs** Pekare till den resurs som anges av klienten
 - **client_address** Pekare till klientadress. Kan vara IPv4 eller IPv6
 - **request_type** Anger typ av klientbegäran. Kanske:
    - NX_HTTP_SERVER_GET_REQUEST
    - NX_HTTP_SERVER_POST_REQUEST
    - NX_HTTP_SERVER_HEAD_REQUEST
    - NX_HTTP_SERVER_PUT_REQUEST
    - NX_HTTP_SERVER_DELETE_REQUEST

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Har angett återanropet
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

Ange ytterligare MIME-kartor för HTML

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a>Description

Med den här tjänsten kan HTTP-programutvecklaren lägga till ytterligare MIME-typer från  de mime-standardtyper som tillhandahålls av NetX Duo HTTP Server (se nx_http_server_get_type lista över definierade typer).

När en klientbegäran tas emot, t.ex. en GET-begäran, parsar HTTP-servern den begärda filtypen från HTTP-huvudet med hjälp av den ytterligare MIME-mappningsuppsättningen och om ingen matchning hittas letar den efter en matchning i STANDARD-MIME-kartan för HTTP-servern. Om ingen matchning hittas får MIME-typen som standard "text/oformaterad".

Om funktionen request notify är registrerad på HTTP-servern kan återanropet av begäran meddela *om nx_http_server_type_retrieve()* för att parsa filtypen.

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

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

Extrahera innehållslängd och ange pekare till början av data

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a>Description

Den här tjänsten extraherar innehållslängden från HTTP-huvudet. Det uppdaterar även det angivna paketet på följande sätt: pekaren för paketförberedelser (början på platsen för paketbufferten att skriva till) är inställd på HTTP-innehållet (data) som precis skickade HTTP-huvudet.

Om början av innehållet inte hittas i det aktuella paketet väntar funktionen på att nästa paket tas emot med hjälp av NX_HTTP_SERVER_TIMEOUT_RECEIVE väntealternativet.

> [!NOTE]
> Detta bör inte anropas innan du *anropar nx_http_server_get_entity_header* eftersom den ändrar prepend-pekaren förbi entitetsrubriken.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverinstans
 - **packet_ptr** Pekare till paket pekare för att returnera paketet med uppdaterad förberedelse pekare
 - **content_length** Pekare till extraherad ```content_length```

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) HTTP-innehållslängd hittades och paketet har uppdaterats
 - **NX_HTTP_TIMEOUT** (0xE1) Tiden har gått ut och väntar på nästa paket
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

Ta emot nästa HTTP-paket

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar nästa paket som tas emot på HTTP-serversocketen. Väntealternativet för att ta emot ett paket NX_HTTP_SERVER_TIMEOUT_RECEIVE.

### <a name="input-parameters"></a>Indataparametrar

 - **server_ptr** Pekare till HTTP-serverinstans
 - **packet_ptr** Pekare till mottaget paket

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckades ta emot nästa paket
 - **NX_HTTP_TIMEOUT** (0xE1) Tiden har gått ut och väntar på nästa paket
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

Hämta parametern från begäran

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a>Description

Den här tjänsten försöker hämta den angivna HTTP-URL-parametern i det angivna begärandepaketet. Om den begärda HTTP-parametern inte finns returnerar den här rutinen statusen NX_HTTP_NOT_FOUND. Den här rutinen ska anropas från programmets begäran för att meddela återanrop som angavs när HTTP-servern skapades (*nx_http_server_create*).

### <a name="input-parameters"></a>Indataparametrar

 - **packet_ptr** Pekare till HTTP-klientbegärandepaket. Observera att programmet inte ska släppa det här paketet.
 - **param_number** Logiskt nummer för parametern med början vid noll, från vänster till höger i parameterlistan.
 - **param_ptr** Målområde för att kopiera parametern.
 - **max_param_size** Maximal storlek för parameterns målområde.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad HTTP-serverparameter get
 - **NX_HTTP_NOT_FOUND** (0xE6) Det gick inte att hitta den angivna parametern
 - **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parametern för begäran avslutades inte korrekt
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

Hämta fråga från begäran

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a>Description

Den här tjänsten försöker hämta den angivna HTTP-URL-frågan i det angivna begärandepaketet. Om den begärda HTTP-frågan inte finns returnerar den här rutinen statusen NX_HTTP_NOT_FOUND. Den här rutinen ska anropas från programmets begäran för att meddela återanrop som angavs när HTTP-servern skapades (*nx_http_server_create*).

### <a name="input-parameters"></a>Indataparametrar

 - **packet_ptr** Pekare till HTTP-klientbegärandepaket. Observera att programmet inte får släppa det här paketet.
 - **query_number** Logiskt nummer för parametern med början vid noll, från vänster till höger i frågelistan.
 - **query_ptr** Målområde för att kopiera frågan.
 - **max_query_size** Maximal storlek för frågans målområde.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad HTTP-serverfråga hämta
 - **NX_HTTP_FAILED** (0xE2) Frågestorlek för liten.
 - **NX_HTTP_NOT_FOUND** (0xE6) Det gick inte att hitta den angivna frågan
 - **NX_HTTP_NO_QUERY_PARSED** (0xF2) Ingen fråga i klientbegäran
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a>nx_http_server_start

Starta HTTP-servern

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar den http-serverinstans som du skapade tidigare.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP Server-instans.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad serverstart
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Initiering, Trådar

### <a name="example"></a>Exempel

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

Stoppa HTTP-servern

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar den http-serverinstans som du skapade tidigare. Den här rutinen bör anropas innan du tar bort en HTTP Server-instans.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP Server-instans.

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Lyckad serverstopp
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

Extrahera filtyp från HTTP-klientbegäran

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a>Description

> [!NOTE]
> Den här tjänsten är inaktuell. Användarna uppmanas att använda tjänsten *nx_http_server_type_retrieve()*.

Den här tjänsten extraherar HTTP-begärandetypen i bufferten http_type_string och dess längd i returvärdet från namnet på indatabufferten, vanligtvis URL:en. Om ingen MIME-karta hittas används som standard typen "text/oformaterad". Annars jämförs den extraherade typen med HTTP-serverns standard-MIME-mappning för en matchning. MIME-standardmappningar i NetX Duo HTTP Server är:

 -  html-text/html
 - **htm** text/html
 - **txt** text/plain
 - **gif-bild/gif**
 -  jpg-bild/jpeg
 -  ico-bild/x-ikon

Om det anges söker den även efter en användardefinierad uppsättning ytterligare MIME-kartor. Se *nx_http_server_mime_maps_addtional_set() för* mer information om användardefinierade kartor.

Den här tjänsten är inaktuell. Utvecklare uppmanas att migrera till *nx_http_server_type_get_extended().*

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP Server-instans
 - name Pointer to buffer to search **(namn pekare** till buffert för sökning)
 - **http_type_string** (Pekare till extraherad HTML-typ)

### <a name="return-values"></a>Returvärden

 - **Längden på strängen i byte** Värdet inte noll är lyckades. Noll indikerar fel.

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

Extrahera filtyp från HTTP-klientbegäran

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a>Description

Den här tjänsten extraherar HTTP-begärandetypen *i bufferten http_type_string* och dess längd i returvärdet från namnet på indatabufferten , vanligtvis URL:en.  Om ingen MIME-karta hittas används som standard typen "text/oformaterad". Annars jämförs den extraherade typen med HTTP-serverns standard-MIME-mappning för en matchning. MIME-standardmappningar i NetX Duo HTTP Server är:

 -  html-text/html
 - **htm** text/html
 - **txt** text/plain
 - **gif-bild/gif**
 -  jpg-bild/jpeg
 -  ico-bild/x-ikon

Om det anges söker den även efter en användardefinierad uppsättning ytterligare MIME-kartor. Se *nx_http_server_mime_maps_addtional_set() för* mer information om användardefinierade kartor.

Den här tjänsten *ersätter nx_http_server_type_get()*. Den här versionen innehåller ytterligare längdinformation.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP Server-instans
 - **namn** Pekare till buffert för sökning
 - **name_length** Längden på bufferten som ska genomsöks
 - **http_type_string** (Pekare till extraherad HTML-typ)
 - **http_type_string_max_size** Storleken på http_type_string bufferten

### <a name="return-values"></a>Returvärden

 - **Längden på strängen i byte** Värdet inte noll är lyckades. Noll indikerar fel.

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

Ett mer detaljerat exempel finns i beskrivningen för [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

Ange sammanfattad funktion för att autentisera motringning

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
```

### <a name="description"></a>Description

Den här tjänsten anger återanropet som anropas när sammanfattad autentisering utförs.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP Server-instans
 - **digest_authenticate_callback** Pekare för att sammanfatta autentisera återanrop

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Har angett återanropet
 - NX_PTR_ERROR (0x07) Ogiltig pekare
 - NX_NOT_SUPPORTED (0x4B) Sammanfattad autentisering är inte aktiverat

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

Ange återanropsfunktion för autentiseringskontroll

### <a name="prototype"></a>Prototyp

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a>Description

Den här tjänsten anger återanropsfunktionen för autentiseringskontroll.

### <a name="input-parameters"></a>Indataparametrar

 - **http_server_ptr** Pekare till HTTP Server-instans
 - **authentication_check_extended** Pekare till programmets autentiseringskontroll

### <a name="return-values"></a>Returvärden

 - **NX_SUCCESS** (0x00) Har angett återanropet
 - NX_PTR_ERROR (0x07) Ogiltig pekare

### <a name="allowed-from"></a>Tillåts från

Program

### <a name="example"></a>Exempel

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
