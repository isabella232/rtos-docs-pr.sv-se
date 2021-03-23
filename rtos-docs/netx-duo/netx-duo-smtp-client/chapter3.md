---
title: Kapitel 3 – klient Beskrivning av SMTP-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SMTP-klienttjänster (visas nedan) i användnings ordning i ett typiskt SMTP-klientcertifikat.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825788"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Kapitel 3 – klient Beskrivning av SMTP-klienttjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo SMTP-klienttjänster (visas nedan) i användnings ordning i ett typiskt SMTP-klientcertifikat.

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **_NX_DISABLE_ERROR_CHECKING_** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

Skapa en SMTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en SMTP-klient instans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SMTP-klientens kontroll block;
- **ip_ptr** Pekare till IP-instans;
- **packet_pool_ptr** Pekare till klient paketets pool;
- **användar namn** NULL-terminerat * * användar namn för autentisering
- **lösen ord** NULL-kopplat lösen ord för autentisering
- **from_address** NULL-avbruten avsändar adress
- **client_domain** NULL-avslutat domän namn
- **authentication_type** Typ av klientautentisering. Typer som stöds:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** Pekare till SMTP-serverns IP-adress
- **SERVER_PORT** TCP-port för SMTP-server

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SMTP-klienten har skapats. Status för generering av TCP-socket
- NX_SMTP_INVALID_PARAM (0xA5) ogiltig inmatad icke-pekare
- NX_IP_ADDRESS_ERROR (0x21) ogiltig IP-adress typ
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

Ta bort en SMTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad SMTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SMTP-klient instans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har tagits bort
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

Skapa och skicka ett SMTP-e-postobjekt

### <a name="prototype"></a>Prototyp

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar och skickar ett SMTP-e-postobjekt. SMTP-klienten upprättar en TCP-anslutning med SMTP-servern och skickar en serie med SMTP-kommandon. Om inga fel uppstår skickas e-postmeddelandet till servern. Oavsett om e-postmeddelandet har skickats avbryts TCP-anslutningen och returnerar en status som anger resultatet av e-postöverföringen. Programmet kan anropa den här tjänsten för så många e-postmeddelanden som det måste skickas utan begränsning.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SMTP-klient
- **recipient_address** NULL-avslutad mottagar adress.
- **ämne** NULL-avslutad ämnes rad text;.
- **prioritet** Prioritets nivå då e-post levereras
- **mail_body** Pekare till e-postmeddelande
- **mail_body_length** Storlek på e-postmeddelande

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) e-post har skickats
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0XB2) SMTP-serverinstans har inte initierats för SMTP-sessionens status resultat för SMTP-session
- NX_PTR_ERROR (0x07) ogiltig pekar parameter
- NX_SMTP_INVALID_PARAM (0xA5) ogiltig inmatad icke-pekare
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
