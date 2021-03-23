---
title: Kapitel 3 – Beskrivning av POP3-klient tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo POP3-klient tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825842"
---
# <a name="chapter-3---description-of-pop3-client-services"></a>Kapitel 3 – Beskrivning av POP3-klient tjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo POP3-klient tjänster (visas nedan) i alfabetisk ordning.

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

Skapa en POP3-klient instans för IPv4

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en instans av POP3-klienten. Det stöder endast IPv4 POP3-server adresser.

Observera att enhets programmet först måste skapa en IP-instans och en modempool för att POP3-klienten ska kunna överföra paket. Den här poolen skapas för användning exklusivt av POP3-klient aktiviteten eller samma modempool som används i skapandet av IP-instansen. Packet-poolen kan också delas med Ethernet-drivrutinen, men detta har en nackdel med att använda stora paket pooler vars nytto Last är avsedd för att ta emot potentiellt stora paket nytto laster för POP3-klienten för att skicka relativt små POP3-meddelande paket till servern.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klienten för att skapa
- **APOP_authentication** Aktivera APOP-autentisering
- **Ip_ptr pekare** till IP-instans
- **packet_pool_ptr** Pekare till klient paketets pool
- **server_ip_address** IPv4-adress för POP3-server
- **SERVER_PORT** POP3-server port
- **client_name** Pekare till klient namn
- **client_password** Pekare till klient lösen ord

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00)-klienten har skapats
- **status** Status för slut för ande av NetX Duo-och ThreadX service-anrop
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
- NX_POP3_PARAM_ERROR (0xB1) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

Skapa en POP3-klient instans för IPv4 eller IPv6

### <a name="prototype"></a>Prototyp

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en instans av POP3-klienten. Det stöder både IPv4-och IPv6 POP3-server adresser. Se den tidigare beskrivna *nx_pop3_client_create* tjänsten för mer information om POP3-klienten skapa process.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klienten för att skapa
- **APOP_authentication** Aktivera APOP-autentisering
- **ip_ptr** Pekare till IP-instans
- **packet_pool_ptr** Pekare till klient paketets pool
- **server_ip_address** POP3-serverns IPv6-eller IPv4-adress
- **SERVER_PORT** POP3-server port
- **client_name**  Pekare till klient namn
- **client_password** Pekare till klient lösen ord

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00)-klienten har skapats
- **status** Status för slut för ande av NetX Duo-och ThreadX service-anrop
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare
- NX_POP3_PARAM_ERROR (0xB1) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

Ta bort en POP3-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad POP3-klient. Inte att den här tjänsten inte tar bort POP3-klientens adresspool. Enhets programmet måste ta bort den här resursen separat om den inte längre har använt för poolen.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klienten som ska tas bort

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klienten har tagits bort
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Ta bort ett angivet e-postobjekt från klientens maildrop

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort det angivna e-postobjektet från klientens maildrop. Den är avsedd för när du har laddat ned e-postobjektet, även om vissa POP3-servrar kan ta bort e-postobjekten automatiskt efter att klienten har begärt

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient instans
- **mail_index** Index i klientens maildrop

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) borttagnings förfrågan lyckades
- **NX_POP3_INVALID_MAIL_ITEM**(0XB2) ogiltigt e-postobjekts index
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) av klient paketets nytto Last är för litet för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS**-Server (0xB4) svarar med fel status
- NX_POP3_CLIENT_INVALID_INDEX (0xB8) ogiltigt inmatade e-postindex
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

### <a name="description"></a>Beskrivning

Den här tjänsten gör en RETR-begäran för att hämta ett e-postobjekt från den klient maildrop som anges av index mail_item. När du har gjort en RETR-begäran och fått ett positivt svar från servern kan klienten börja hämta e-postmeddelandet med hjälp av tjänsten *nx_pop3_client_mail_item_message_get* . Observera att tjänsten också tillhandahåller storleken på det begärda e-postobjektet som extraherats från Server svaret.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient instans
- **mail_item** Index i klientens maildrop
- **item_size** Pekare till storlek på e-postmeddelande

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) e-postobjektet har hämtats
- **NX_POP3_INVALID_MAIL_ITEM** (0XB2) ogiltigt e-postobjekts index
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) av klient paketets nytto Last är för litet för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS** -Server (0xB4) svarar med fel status
- NX_POP3_CLIENT_INVALID_INDEX (0xB8) ogiltigt inmatade e-postindex
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

### <a name="description"></a>Beskrivning

Den här tjänsten gör en STAT-begäran för att hämta antalet e-postobjekt och den totala storleken på e-postmeddelandets data från klientens maildrop.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient instans
- **number_mail_item** Antal e-postmeddelanden i klient maildrop
- **maildrop_total_size** Pekare till storlek på alla e-postmeddelanden

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) e-postobjektet har hämtats
- **NX_POP3_INVALID_MAIL_ITEM** (0XB2) ogiltigt e-postobjekts index
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) av klient paketets nytto Last är för litet för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS** -Server (0xB4) svarar med fel status
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

Hämta det angivna meddelandet om e-postobjektet

### <a name="prototype"></a>Prototyp

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar e-postmeddelandets meddelande, storleken på e-postmeddelandet och om det är det sista paketet i e-postmeddelandet. Om final_packet NX_TRUE paketet som pekas av recv_packet_ptr är det sista paketet i e-postmeddelandet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient instans
- **recv_packet_ptr** Tog emot paket med meddelande data
- **number_mail_item** Antal e-postmeddelanden i klient maildrop
- **maildrop_total_size** Pekare till storlek på alla e-postmeddelanden

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) e-postobjektet har hämtats
- **NX_POP3_CLIENT_INVALID_STATE** (0xB7) av klient paketets nytto Last är för litet för POP3-begäran.
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

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

### <a name="description"></a>Beskrivning

Den här tjänsten gör en LIST förfrågan för att hämta storleken på det angivna e-postobjektet.

### <a name="input-parameters"></a>Indataparametrar

- **client_ptr** Pekare till klient instans
- **mail_item** Index i klientens maildrop
- **storlek** Pekare till storlek på e-postmeddelande

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) e-postobjektet har hämtats
- **NX_POP3_INVALID_MAIL_ITEM** (0XB2) ogiltigt e-postobjekts index
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) av klient paketets nytto Last är för litet för POP3-begäran.
- **NX_POP3_SERVER_ERROR_STATUS** -Server (0xB4) svarar med fel status
- NX_POP3_CLIENT_INVALID_INDEX (0xB8) ogiltigt inmatade e-postindex
- NX_PTR_ERROR (0x07) ogiltig parameter för inmatad pekare

### <a name="allowed-from"></a>Tillåten från

Program kod

### <a name="example"></a>Exempel

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
