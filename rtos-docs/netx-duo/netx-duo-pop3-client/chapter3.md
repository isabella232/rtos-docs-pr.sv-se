---
title: Kapitel 3 – Beskrivning av POP3-klienttjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo POP3-klienttjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c8608f3894eba4db557f0c67b1042f2c88362cb0ca4bf6034bff9ae591fe26bc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797185"
---
# <a name="chapter-3---description-of-pop3-client-services"></a>Kapitel 3 – Beskrivning av POP3-klienttjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo POP3-klienttjänster (visas nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

Skapa en POP3-klientinstans för IPv4

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Description

Den här tjänsten skapar en instans av POP3-klienten. Den stöder endast IPv4 POP3-serveradresser.

Observera att enhetsprogrammet först måste skapa en IP-instans och en paketpool för att POP3-klienten ska kunna överföra paket. Den här paketpoolen som skapats för användning exklusivt av POP3-klienten eller samma paketpool som användes när IP-instansen skapades. Paketpoolen kan också delas med Ethernet-drivrutinspaketpoolen, men det har nackdelen att använda stora paketpooler vars nyttolast är avsedd för att ta emot potentiellt stora paketnyttolast för ATT POP3-klienten ska skicka relativt små POP3-meddelandepaket till servern.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient att skapa
- **APOP_authentication** Aktivera APOP-autentisering
- **ip_ptr pekare till** IP-instans
- **packet_pool_ptr** Pekare till klientpaketpool
- **server_ip_address** POP3-serverns IPv4-adress
- **server_port** POP3-serverport
- **client_name** Pekare till klientnamn
- **client_password** Pekare till klientlösenord

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** -klienten (0x00) har skapats
- **status** Status slutförande av NetX Duo- och ThreadX-tjänstanrop
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
- NX_POP3_PARAM_ERROR (0xB1) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a>nxd_pop3_client_create

Skapa en POP3-klientinstans för IPv4 eller IPv6

### <a name="prototype"></a>Prototyp

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Description

Den här tjänsten skapar en instans av POP3-klienten. Den stöder både IPv4- och IPv6 POP3-serveradresser. Se den tidigare *beskrivna nx_pop3_client_create tjänsten* för mer information om processen för att skapa POP3-klient.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient att skapa
- **APOP_authentication** Aktivera APOP-autentisering
- **ip_ptr** Pekare till IP-instans
- **packet_pool_ptr** Pekare till klientpaketpool
- **server_ip_address** POP3-serverns IPv6- eller IPv4-adress
- **server_port** POP3-serverport
- **client_name**  Pekare till klientnamn
- **client_password** Pekare till klientlösenord

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** -klienten (0x00) har skapats
- **status** Status slutförande av NetX Duo- och ThreadX-tjänstanrop
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter
- NX_POP3_PARAM_ERROR (0xB1) Ogiltig icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

Ta bort en POP3-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en POP3-klient som skapats tidigare. Inte för att den här tjänsten inte tar bort POP3-klientens paketpool. Enhetsprogrammet måste ta bort den här resursen separat om den inte längre har användning för paketpoolen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klienten som ska tas bort

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Klienten har tagits bort
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Ta bort ett angivet e-postobjekt från client maildrop

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a>Description

Den här tjänsten tar bort det angivna e-postobjektet från Client maildrop. Den är avsedd efter nedladdning av e-postobjektet, även om vissa POP3-servrar automatiskt kan ta bort e-postobjekt efter att ha begärts av klienten.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klientinstans
- **mail_index** Indexera till klientens e-postlyssnare

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Borttagningsbegäran lyckades
- **NX_POP3_INVALID_MAIL_ITEM**(0xB2) Ogiltigt e-postobjektsindex
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Nyttolasten för klientpaket är för liten för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server svarar med felstatus
- NX_POP3_CLIENT_INVALID_INDEX(0xB8) Ogiltiga e-postindexindata
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

Hämta ett angivet e-postobjekt

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a>Description

Den här tjänsten skickar en RETR-begäran om att hämta ett e-postobjekt från den Klient-e-postdroppe som anges av indexets mail_item. När du har gjort en RETR-begäran och fått ett positivt svar från servern kan klienten börja ladda ned e-postmeddelandet med *hjälp nx_pop3_client_mail_item_message_get* tjänsten. Observera att tjänsten även tillhandahåller storleken på det begärda e-postobjektet som extraheras från serversvaret.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klientinstans
- **mail_item** Indexera till klientens e-postlyssnare
- **item_size** Pekare till storleken på e-postmeddelandet

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) E-postobjektet har hämtats
- **NX_POP3_INVALID_MAIL_ITEM** (0xB2) Ogiltigt e-postobjektsindex
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Nyttolasten för klientpaket är för liten för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server svarar med felstatus
- NX_POP3_CLIENT_INVALID_INDEX (0xB8) Ogiltiga indata för e-postindex
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

Hämta antalet e-postobjekt i maildrop

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a>Description

Den här tjänsten skickar en STAT-begäran om att hämta antalet e-postobjekt och den totala storleken på e-postmeddelandedata från klientens e-postlyssnare.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klientinstans
- **number_mail_item** Antal e-postmeddelanden i klientens e-postlyssning
- **maildrop_total_size** Pekare till storleken på alla e-postmeddelanden

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) E-postobjektet har hämtats
- **NX_POP3_INVALID_MAIL_ITEM** (0xB2) Ogiltigt e-postobjektsindex
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Nyttolasten för klientpaket är för liten för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server svarar med felstatus
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

Hämta det angivna e-postobjektets meddelande

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a>Description

Den här tjänsten hämtar e-postmeddelandet, storleken på e-postmeddelandet och om det är det sista paketet i e-postmeddelandet. Om final_packet är NX_TRUE det paket som recv_packet_ptr på är det sista paketet i e-postmeddelandet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klientinstans
- **recv_packet_ptr** Mottaget paket med meddelandedata
- **number_mail_item** Antal e-postmeddelanden i klientens e-postlyssning
- **maildrop_total_size** Pekare till storleken på alla e-postmeddelanden

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) E-postobjektet har hämtats
- **NX_POP3_CLIENT_INVALID_STATE** (0xB7) Nyttolasten för klientpaket är för liten för POP3-begäran.
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

Hämta storleken på det angivna e-postobjektet

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a>Description

Den här tjänsten gör en LIST-begäran för att hämta storleken på det angivna e-postobjektet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klientinstans
- **mail_item** Indexera till klientens e-postlyssnare
- **storlek** Pekare till storleken på e-postmeddelandet

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) E-postobjektet har hämtats
- **NX_POP3_INVALID_MAIL_ITEM** (0xB2) Ogiltigt e-postobjektsindex
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Nyttolasten för klientpaket är för liten för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server svarar med felstatus
- NX_POP3_CLIENT_INVALID_INDEX (0xB8) Ogiltiga indata för e-postindex
- NX_PTR_ERROR (0x07) Ogiltig indatapekarparameter

### <a name="allowed-from"></a>Tillåts från

Programkod

### <a name="example"></a>Exempel

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
