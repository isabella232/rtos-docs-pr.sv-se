---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo TFTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo TFTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825707"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX Duo TFTP-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo TFTP-tjänster (visas nedan) i alfabetisk ordning. Om inget annat anges stöder alla tjänster IPv6-och IPv4-kommunikation.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nxd_tftp_client_file_open**: *Öppna TFTP-klienttjänsten*

- **nxd_tftp_client_create**: *skapa en TFTP-klient instans*

- **nxd_tftp_client_delete**: *ta bort en TFTP-klient instans*

- **nxd_tftp_client_error_info_get**: *Hämta klient fel information*

- **nxd_tftp_client_file_close**: *Stäng klient filen*

- **nxd_tftp_client_file_open**: *Öppna klient filen*

- **nxd_tftp_client_file_read**: *läsa ett block från klient filen*

- **nxd_tftp_client_file_write**: *Skriv block till klient filen*

- **nxd_tftp_client_packet_allocate**: *allokera paket för skrivning av klient fil*

- **nxd_tftp_client_set_interface**: *Ange det fysiska gränssnittet för TFTP-begäranden*

- **nxd_tftp_server_create**: *skapa TFTP-server*

- **nxd_tftp_server_delete**: *ta bort TFTP-server*

- **nxd_tftp_server_start**: *Starta TFTP-server*

- **nxd_tftp_server_stop**: *stoppa TFTP-server*

> [!NOTE] 
> IPv4-motsvarigheterna till alla de tjänster som anges ovan är tillgängliga i NetX Duo TFTP-klienten och-servern, t. ex. *nx_tftp_server_create* och *nx_tftp_client_file_open*. Endast API-beskrivningarna Duo, t. ex. tjänster som börjar med *nxd_*, finns på följande sidor. När en NXD_ADDRESS \* -inmatare anges, anropar IPv4 motsvarande API för ulong-inmatade. Annars finns det ingen skillnad i att använda API: et.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Skapa en TFTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en TFTP-klient instans för den tidigare skapade IP-instansen.

> [!IMPORTANT]
> Programmet måste kontrol lera att den angivna IP-adresspoolen och Packet-poolen redan har skapats. Dessutom måste UDP vara aktiverat för IP-instansen innan den här tjänsten anropas.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till kontroll block för TFTP-klient.

- **tftp_client_name** Namnet på den här TFTP-klientcertifikatet

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

- **pool_ptr** Pekare till instansen för Packet-poolens TFTP.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**(0X00) korrekt TFTP-skapande.

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig eller IP-version som inte stöds

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0X08) ogiltig Server-IP-adress togs emot

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) Server ack har inte tagits emot

- NX_PTR_ERROR (0x16) ogiltig IP-, pool-eller TFTP-pekare.

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

Ta bort en TFTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad TFTP-klient instans.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till tidigare skapad TFTP-serverinstans.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad TFTP-klient borttagning.

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

Hämta information om klient fel

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar den senaste felkoden som togs emot och anger pekaren till klientens interna fel sträng. I fel tillstånd kan användaren se det senaste felet som skickats av servern. En null-felsträng anger att det inte finns något fel.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till tidigare skapad TFTP-serverinstans.

- **error_code** Pekare till mål arean för felkod

- **ERROR_STRING** Pekare till mål för fel sträng

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) Det gick inte att hämta TFTP-felinformation.  

- NX_PTR_ERROR (0x16) ogiltig TFTP-klient pekare.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

Stäng klient filen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger den tidigare öppnade filen av denna TFTP-klient instans. En TFTP-klientsession får bara ha en fil öppen åt gången.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till tidigare skapad TFTP-serverinstans.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) TFTP-filen stängs.

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Öppna TFTP-klienttjänsten

### <a name="prototype"></a>Prototyp

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker öppna den angivna filen på TFTP-servern på den angivna IP-adressen. Filen kommer att öppnas för läsning eller skrivning. 

> [!NOTE] 
> Detta är begränsat till endast IPv4-paket och är avsett för stöd för NetX TFTP-program. Utvecklare uppmuntras att hamna i sina program för att använda motsvarande "Duo"- *nxd_tftp_client_file_open.*

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-Control Block.

- **file_name** ASCII-filnamn, NULL-avslutad och med lämplig Sök vägs information.

- **server_ip_address** Server TFTP-adress.

- **open_type** Typ av öppen begäran, antingen:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (protokollnumret 0x02)

- **wait_option** Definierar hur länge tjänsten ska vänta på att TFTP-klienttjänsten är öppen. Vänte alternativen definieras enligt följande:

  **timeout-värde** (0X00000001 till 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills en TFTP-server svarar på begäran. 
  
  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på TFTP-serverns svar.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klient filen är öppen

- **NX_TFTP_NOT_CLOSED** -klienten (0xC3) har redan öppen fil

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0X08) ogiltig Server-IP togs emot

- **NX_TFTP_CODE_ERROR** (0X05) tog emot felkod

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_IP_ADDRESS_ERROR (0x21) ogiltig Server-IP-adress

- NX_OPTION_ERROR (0x0A) ogiltig öppen typ

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

Öppna TFTP-klienttjänsten

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten försöker öppna den angivna filen på TFTP-servern på den angivna IPv6-adressen. Filen kommer att öppnas för läsning eller skrivning.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-Control Block.

- **file_name** ASCII-filnamn, NULL-avslutad och med lämplig Sök vägs information.

- **server_ip_address** Server TFTP-adress.

- **open_type** Typ av öppen begäran, antingen:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (protokollnumret 0x02)

- **wait_option** Definierar hur länge tjänsten ska vänta på att TFTP-klienttjänsten är öppen. Vänte alternativen definieras enligt följande:

  **timeout-värde** (0X00000001 till 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills en TFTP-server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade vid väntan på TFTP-serverns svar.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) klient filen är öppen

- **NX_TFTP_NOT_CLOSED** -klienten (0xC3) har redan öppen fil

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig IP-version

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0X08) ogiltig Server-IP togs emot

- **NX_TFTP_CODE_ERROR** (0X05) tog emot felkod

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_IP_ADDRESS_ERROR (0x21) ogiltig Server-IP-adress

- NX_OPTION_ERROR (0x0A) ogiltig öppen typ

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

Läsa ett block från klient filen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser ett 512-byte-block från den tidigare öppnade TFTP-klientdatorn. Ett block som innehåller färre än 512 byte signalerar slutet av filen.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till kontroll block för TFTP-klient.

- **packet_ptr** Mål för paket som innehåller blocket läst från filen.

- **wait_option** Definierar hur länge tjänsten ska vänta på att läsningen ska slutföras. Vänte alternativen definieras enligt följande:

  **timeout-värde** (0X00000001 till 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills TFTP-servern svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det högsta antalet timer-Tick som ska vara pausat under väntan på att TFTP-servern ska skicka ett block av filen.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient block läsning

- **NX_TFTP_NOT_OPEN** (0xC3) den angivna klient filen är inte öppen för läsning

- **NX_NO_PACKET** (0X01) inget paket togs emot från servern.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern

- **NX_TFTP_END_OF_FILE** (0XC5) slutet av filen upptäcktes (inte ett fel).

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig IP-version

- **NX_TFTP_CODE_ERROR** (0X05) tog emot felkod

- **NX_TFTP_FAILED** (0XC2) Okänd TFTP-kod mottagen

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0X0a) ogiltigt block nummer togs emot

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

Skriv ett block till klient filen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skriver ett 512-byte-block till den tidigare öppnade TFTP-klientdatorn. Om du anger ett block som innehåller färre än 512 byte signalerar du slutet på filen.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till kontroll block för TFTP-klient.

- **packet_ptr** Paket som innehåller det block som ska skrivas till filen.

- **wait_option** Definierar hur länge tjänsten väntar på att skrivningen ska slutföras. Vänte alternativen definieras enligt följande:

  **timeout-värde** (0X00000001 till 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills TFTP-servern svarar på begäran.
 
  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på att TFTP-servern ska skicka en bekräftelse för skrivbegäran.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad klient block skrivning

- **NX_TFTP_NOT_OPEN** (0xC3) den angivna klient filen är inte öppen för skrivning

- **NX_TFTP_TIMEOUT** (0XC1) timeout vid väntan på Server ack

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) ingen bekräftelse togs emot från servern

- **NX_TFTP_INVALID_IP_VERSION** (0X0C) ogiltig IP-version

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0X08) ogiltig server adress togs emot

- **NX_TFTP_CODE_ERROR** (0X05) tog emot felkod

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

Allokera paket för skrivning av klient fil

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Beskrivning

Den här tjänsten allokerar ett UDP-paket från den angivna poolen och gör plats för TFTP-huvudet i 4 byte innan paketet returneras till anroparen. Anroparen kan sedan bygga en buffert för att skriva till en klient fil.

### <a name="input-parameters"></a>Indataparametrar

- **pool_ptr** Pekare till Packet bassäng.

- **packet_ptr** Mål för pekare till allokerat paket.

- **wait_option** Definierar hur länge tjänsten ska vänta på att paket tilldelningen ska slutföras. Vänte alternativen definieras enligt följande:

  **timeout-värde** (0X00000001 till 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om du väljer TX_WAIT_FOREVER stoppas den anropande tråden under obestämd tid tills tilldelningen har slutförts.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska pausas i väntan på paket tilldelningen.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) paket tilldelningen lyckades

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

Ange fysiskt gränssnitt för TFTP-begäranden

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>Beskrivning

Tjänsten använder gränssnitts indexet för att ange det fysiska gränssnittet för TFTP-klienten för att skicka och ta emot TFTP-paket. Standardvärdet är noll för det primära gränssnittet.

> [!NOTE]
> NetX Duo måste ha stöd för multihome-adressering (v 5.6 eller senare) för att kunna använda den här tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-klient instans

- **if_index** Index för det fysiska gränssnitt som ska användas

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) har inställt gränssnitt (0X0B) ogiltig gränssnitts information

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

- NX_TFTP_INVALID_INTERFACE (0x0B) ogiltig gränssnitts information

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

Skapa TFTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en TFTP-server som svarar på TFTP-klientbegäran på port 69. Servern måste startas av ett efterföljande anrop till *nxd_tftp_server_start*.

> [!IMPORTANT]
> Programmet måste kontrol lera att den angivna IP-instansen, mediepoolen och FileX-medie instansen redan har skapats. Dessutom måste UDP vara aktiverat för IP-instansen innan den här tjänsten anropas.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till kontroll block för TFTP-server.

- **tftp_server_name** Namnet på den här TFTP-serverinstansen

- **ip_ptr** Pekare till den tidigare skapade IP-instansen.

- **media_ptr** Pekare till FileX Media-instans.

- **stack_ptr** Pekare till TFTP-serverns stack-yta.

- **stack_size** Antal byte i TFTP-serverns stack.

- **pool_ptr** Pekare till TFTP-adresspool. 

> [!NOTE]
> Den angivna poolen måste ha paket nytto laster minst 580 byte stor. <sup>1</sup>

<sup>1</sup> data delen i ett paket är exakt 512 byte, men paketets nytto Last storlek måste vara minst 572 byte. Återstående byte används för rubrikerna UDP, IPv6 och Ethernet och eventuella efterföljande byte som krävs av driv rutinen för justering.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) servern har skapats

- **NX_TFTP_POOL_ERROR** (0XC6) paketets pool har en paket storlek på mindre än 560 byte

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

Ta bort TFTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en tidigare skapad TFTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till kontroll block för TFTP-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) Server borttagning har slutförts

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

Starta TFTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar den tidigare skapade TFTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till kontroll block för TFTP-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) Server start har slutförts

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.
 
### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

Stoppa TFTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar den tidigare skapade TFTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till kontroll block för TFTP-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) Server stopp har slutförts

- NX_PTR_ERROR (0x16) ogiltig pekare inmatade.

- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```