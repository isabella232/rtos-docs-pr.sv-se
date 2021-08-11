---
title: Kapitel 3 – Beskrivning av Azure RTOS NetX Duo TFTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX Duo TFTP-tjänster (anges nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db7b7469bda02597db6428ecbf080b37a095413411eef2abefb1c4804d7bb1d3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799071"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Kapitel 3 – Beskrivning av Azure RTOS NetX Duo TFTP-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX Duo TFTP-tjänster (anges nedan) i alfabetisk ordning. Om inget annat anges stöder alla tjänster IPv6- och IPv4-kommunikation.

I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **BOLD** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är i fetstil är helt inaktiverade.

- **nxd_tftp_client_file_open:** *Öppna TFTP-klientfilen*

- **nxd_tftp_client_create:** Skapa *en TFTP-klientinstans*

- **nxd_tftp_client_delete:** Ta *bort en TFTP-klientinstans*

- **nxd_tftp_client_error_info_get:** *Hämta information om klientfel*

- **nxd_tftp_client_file_close:** Stäng *klientfilen*

- **nxd_tftp_client_file_open**: *Öppna klientfilen*

- **nxd_tftp_client_file_read:** *Läsa ett block från klientfilen*

- **nxd_tftp_client_file_write:** *Skrivblock till klientfil*

- **nxd_tftp_client_packet_allocate:** Allokera *paket för skrivning av klientfiler*

- **nxd_tftp_client_set_interface:** *Ange det fysiska gränssnittet för TFTP-begäranden*

- **nxd_tftp_server_create:** Skapa *TFTP-server*

- **nxd_tftp_server_delete:** Ta *bort TFTP-server*

- **nxd_tftp_server_start:** *Starta TFTP-server*

- **nxd_tftp_server_stop:** *Stoppa TFTP-server*

> [!NOTE] 
> IPv4-motsvarigheterna till alla tjänster som anges ovan är tillgängliga i NetX Duo TFTP Client och Server, t.ex. *nx_tftp_server_create* *och nx_tftp_client_file_open*. Endast "Duo"-API-beskrivningarna, t.ex. *tjänster som börjar nxd_*, finns på följande sidor. Om en NXD_ADDRESS \* indata anges anropar IPv4-motsvarande API för ULONG-indata. Annars finns det ingen skillnad i att använda API:et.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Skapa en TFTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skapar en TFTP-klientinstans för den tidigare skapade IP-instansen.

> [!IMPORTANT]
> Programmet måste se till att den angivna IP-adressen och paketpoolen redan har skapats. Dessutom måste UDP vara aktiverat för IP-instansen innan den här tjänsten anropas.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-klientens kontrollblock.

- **tftp_client_name** Namnet på den här TFTP-klientinstansen

- **ip_ptr** Pekare till ip-instans som skapats tidigare.

- **pool_ptr** Pekare till TFTP-klientinstansen för paketpoolen.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS**(0x00) Lyckad TFTP-skapa.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Ogiltig eller IP-version som inte stöds

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Ogiltig IP-adress för server tas emot

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK togs inte emot

- NX_PTR_ERROR (0x16) Ogiltig IP-adress, pool eller TFTP-pekare.

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

Ta bort en TFTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en TFTP-klientinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till tftp-klientinstans som skapats tidigare.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av TFTP-klient.

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

Hämta information om klientfel

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Description

Den här tjänsten returnerar den senaste mottagna felkoden och anger pekaren till klientens interna felsträng. I feltillstånd kan användaren se det senaste felet som skickats av servern. En null-felsträng anger att det inte finns något fel.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till tftp-klientinstans som skapats tidigare.

- **error_code** Pekare till målområdet för felkod

- **error_string** Pekare till mål för felsträng

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Information om lyckad TFTP-fel visas.  

- NX_PTR_ERROR (0x16) Ogiltig TFTP-klient pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

Stäng klientfilen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Description

Den här tjänsten stänger den tidigare öppnade filen av den här TFTP-klientinstansen. En TFTP-klientinstans får bara ha en fil öppen i taget.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till tftp-klientinstans som skapats tidigare.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad TFTP-fil stäng.

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Öppna TFTP-klientfilen

### <a name="prototype"></a>Prototyp

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten försöker öppna den angivna filen på TFTP-servern på den angivna IP-adressen. Filen öppnas för antingen läsning eller skrivning. 

> [!NOTE] 
> Detta är begränsat till endast IPv4-paket och är avsett att stödja NetX TFTP-program. Utvecklare uppmanas att porta sina program till motsvarande "duo"-tjänst *nxd_tftp_client_file_open.*

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-kontrollblock.

- **file_name** ASCII-filnamn, NULL-avslutat och med lämplig sökvägsinformation.

- **server_ip_address** Serverns TFTP-adress.

- **open_type** Typ av öppen begäran, antingen:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Definierar hur länge tjänsten ska vänta tills TFTP-klientfilen är öppen. Väntealternativen definieras på följande sätt:

  **timeout-värde** (0x00000001 via 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en TFTP-server svarar på begäran. 
  
  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på TFTP-serversvaret.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientfil öppen

- **NX_TFTP_NOT_CLOSED** -klienten (0xC3) har redan filen öppen

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Ogiltig serveradress mottagen

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Inget ACK togs emot från servern

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Ogiltig server-IP-adress togs emot

- **NX_TFTP_CODE_ERROR** (0x05) Mottagen felkod

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_IP_ADDRESS_ERROR (0x21) Ogiltig SERVER-IP-adress

- NX_OPTION_ERROR (0x0A) Ogiltig öppen typ

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Öppna TFTP-klientfilen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Description

Den här tjänsten försöker öppna den angivna filen på TFTP-servern på den angivna IPv6-adressen. Filen öppnas för antingen läsning eller skrivning.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-kontrollblock.

- **file_name** ASCII-filnamn, NULL-avslutat och med lämplig sökvägsinformation.

- **server_ip_address** Serverns TFTP-adress.

- **open_type** Typ av öppen begäran, antingen:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Definierar hur länge tjänsten ska vänta tills TFTP-klientfilen är öppen. Väntealternativen definieras på följande sätt:

  **timeout-värde** (0x00000001 via 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en TFTP-server svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på TFTP-serversvaret.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientfil öppen

- **NX_TFTP_NOT_CLOSED** -klienten (0xC3) har redan filen öppen

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Ogiltig serveradress mottagen

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Inget ACK togs emot från servern

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Ogiltig IP-version

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Ogiltig server-IP-adress togs emot

- **NX_TFTP_CODE_ERROR** (0x05) Mottagen felkod

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_IP_ADDRESS_ERROR (0x21) Ogiltig SERVER-IP-adress

- NX_OPTION_ERROR (0x0A) Ogiltig öppen typ

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Läsa ett block från klientfilen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Description

Den här tjänsten läser ett 512 byte-block från den tftp-klientfil som öppnades tidigare. Ett block som innehåller färre än 512 byte signalerar slutet av filen.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-klientens kontrollblock.

- **packet_ptr** Mål för paket som innehåller blocket som läses från filen.

- **wait_option** Definierar hur länge tjänsten ska vänta tills läsningen har slutförts. Väntealternativen definieras på följande sätt:

  **timeout-värde** (0x00000001 via 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills TFTP-servern svarar på begäran.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan TFTP-servern skickar ett block av filen.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad klientblockläsning

- **NX_TFTP_NOT_OPEN** (0xC3) angiven klientfil är inte öppen för läsning

- **NX_NO_PACKET** (0x01) Inget paket tas emot från servern.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Ogiltig serveradress mottagen

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Inget ACK togs emot från servern

- **NX_TFTP_END_OF_FILE** (0xC5) Slutet av filen har identifierats (inte ett fel).

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Ogiltig IP-version

- **NX_TFTP_CODE_ERROR** (0x05) Mottagen felkod

- **NX_TFTP_FAILED** (0xC2) Okänd TFTP-kod togs emot

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Ogiltigt blocknummer har tagits emot

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga indata som inte pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

Skriva ett block till klientfilen

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Description

Den här tjänsten skriver ett 512 byte-block till den TFTP-klientfil som öppnades tidigare. Om du anger ett block som innehåller färre än 512 byte signalerar det slutet på filen.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-klientens kontrollblock.

- **packet_ptr** Paket som innehåller blocket för att skriva till filen.

- **wait_option** Definierar hur länge tjänsten ska vänta på att skriven ska slutföras. Väntealternativen definieras på följande sätt:

  **timeout-värde** (0x00000001 via 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills TFTP-servern svarar på begäran.
 
  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan TFTP-servern skickar en ACK för skrivbegäran.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad blockskrivning för klient

- **NX_TFTP_NOT_OPEN** (0xC3) Angiven klientfil är inte öppen för skrivning

- **NX_TFTP_TIMEOUT** (0xC1) Tidsgräns väntar på Server ACK

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Ogiltig serveradress mottagen

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) Inget ACK togs emot från servern

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Ogiltig IP-version

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Ogiltig serveradress mottagen

- **NX_TFTP_CODE_ERROR** (0x05) Mottagen felkod

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga indata som inte pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

Allokera paket för klientfilskrivning

### <a name="prototype"></a>Prototyp

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Description

Den här tjänsten allokerar ett UDP-paket från den angivna paketpoolen och gör plats för TFTP-huvudet på 4 byte innan paketet returneras till anroparen. Anroparen kan sedan skapa en buffert för skrivning till en klientfil.

### <a name="input-parameters"></a>Indataparametrar

- **pool_ptr** Pekare till paketpool.

- **packet_ptr** Mål för pekare till allokerat paket.

- **wait_option** Definierar hur länge tjänsten ska vänta på att paketet allokeras för att slutföras. Väntealternativen definieras på följande sätt:

  **timeout-värde** (0x00000001 via 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Om TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills allokeringen har slutförts.

  Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på paketallokeringen.

- **ip_type** Ange vilket IP-protokoll som ska användas. Giltiga alternativ är IPv4 (4) eller IPv6 (6).

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Allokera ett lyckat paket

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_INVALID_PARAMETERS (0x4D) Ogiltiga indata som inte pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten använder indatagränssnittsindexet för att ange det fysiska gränssnittet för TFTP-klienten för att skicka och ta emot TFTP-paket. Standardvärdet är noll för det primära gränssnittet.

> [!NOTE]
> NetX Duo måste ha stöd för multihome-adressering (v5.6 eller senare) för att kunna använda den här tjänsten.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_client_ptr** Pekare till TFTP-klientinstans

- **if_index** Index för det fysiska gränssnitt som ska användas

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Felaktigt användargränssnitt (0x0B) Ogiltiga gränssnittsindata

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

- NX_TFTP_INVALID_INTERFACE (0x0B) Ogiltiga gränssnittsinmatningar

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar en TFTP-server som svarar på TFTP-klientbegäranden på port 69. Servern måste startas med ett efterföljande anrop till *nxd_tftp_server_start*.

> [!IMPORTANT]
> Programmet måste se till att den angivna IP-instansen, paketpoolen och FileX-medieinstansen redan har skapats. Dessutom måste UDP vara aktiverat för IP-instansen innan den här tjänsten anropas.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till TFTP-serverkontrollblocket.

- **tftp_server_name** Namnet på den här TFTP-serverinstansen

- **ip_ptr** Pekare till IP-instans som skapats tidigare.

- **media_ptr** Pekare till FileX-medieinstansen.

- **stack_ptr** Pekare till TFTP-serverstackområdet.

- **stack_size** Antal byte i TFTP-serverstacken.

- **pool_ptr** Pekare till TFTP-paketpool. 

> [!NOTE]
> Den angivna poolen måste ha paketnyttolaster som är minst 580 byte stora. <sup>1</sup>

<sup>1</sup> Datadelen i ett paket är exakt 512 byte, men paketets nyttolaststorlek måste vara minst 572 byte. Återstående byte används för UDP-, IPv6- och Ethernet-huvudena och eventuella avslutande byte som krävs av drivrutinen för justering.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad server create

- **NX_TFTP_POOL_ERROR** paketpoolen (0xC6) har en paketstorlek på mindre än 560 byte

- NX_PTR_ERROR (0x16) Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten tar bort en TFTP-server som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till TFTP-serverkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad server-borttagning

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten startar den TFTP-server som du skapade tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till TFTP-serverkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad serverstart

- NX_PTR_ERROR (0x16) Ogiltig pekare.
 
### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten stoppar den TFTP-server som skapades tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **tftp_server_ptr** Pekare till TFTP-serverkontrollblocket.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad serverstopp

- NX_PTR_ERROR (0x16) Ogiltig pekare.

- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```