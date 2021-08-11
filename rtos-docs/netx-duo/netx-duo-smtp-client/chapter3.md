---
title: Kapitel 3 – Klientbeskrivning av SMTP-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo SMTP-klienttjänster (anges nedan) i användningsordning i ett typiskt SMTP-klientprogram.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bc54e7763c4a3977ef4d760bc92025b1cda792b979d741fc7b82f8f1a3f2901b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797815"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Kapitel 3 – Klientbeskrivning av SMTP-klienttjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo SMTP-klienttjänster (anges nedan) i användningsordning i ett typiskt SMTP-klientprogram.

> [!NOTE]
> I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **_den NX_DISABLE_ERROR_CHECKING-definition_** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

Skapa en SMTP-klientinstans

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

### <a name="description"></a>Description

Den här tjänsten skapar en SMTP-klientinstans på den angivna IP-instansen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SMTP-klientkontrollblock;
- **ip_ptr** Pekare till IP-instans;
- **packet_pool_ptr** Pekare till klientpaketpoolen;
- **användarnamn** NULL-avslutad** Användarnamn för autentisering
- **lösenord** NULL-avslutat lösenord för autentisering
- **from_address** NULL-avslutad avsändaradress
- **client_domain** NULL-avslutat domännamn
- **authentication_type** Klientautentiseringstyp. Typer som stöds är:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** Pekare till SMTP-serverns IP-adress
- **server_port** TCP-port för SMTP-server

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) SMTP-klienten har skapats. Status för skapande av TCP-socket
- NX_SMTP_INVALID_PARAM (0xA5) Ogiltiga indata som inte pekare
- NX_IP_ADDRESS_ERROR (0x21) Ogiltig IP-adresstyp
- NX_PTR_ERROR (0x07) Ogiltig indata pekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

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

Ta bort en SMTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en tidigare skapad SMTP-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SMTP-klientinstansen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har tagits bort
- NX_PTR_ERROR (0x07) Ogiltig indata pekarparameter

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar och skickar ett SMTP-e-postobjekt. SMTP-klienten upprättar en TCP-anslutning med SMTP-servern och skickar en serie SMTP-kommandon. Om inga fel påträffas överförs e-postmeddelandet till servern. Oavsett om e-postmeddelandet har skickats avslutas TCP-anslutningen och en status returneras som anger resultatet av e-postöverföringen. Programmet kan anropa den här tjänsten för så många e-postmeddelanden som behövs för att skicka utan gräns.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till SMTP-klient
- **recipient_address** NULL-avslutad mottagaradress.
- **ämne** NULL-avslutad ämnesradstext;.
- **prioritet** Prioritetsnivå där e-post levereras
- **mail_body** Pekare till e-postmeddelande
- **mail_body_length** Storleken på e-postmeddelandet

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) E-post har skickats
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP-klientinstansen har inte initierats för SMTP-sessionsstatus Resultatet av SMTP-sessionen
- NX_PTR_ERROR (0x07) Ogiltig pekarparameter
- NX_SMTP_INVALID_PARAM (0xA5) Ogiltiga indata som inte pekare
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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
