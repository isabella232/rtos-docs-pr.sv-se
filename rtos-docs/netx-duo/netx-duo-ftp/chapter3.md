---
title: Kapitel 3 – Beskrivning av FTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX FTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825980"
---
# <a name="chapter-3---description-of-ftp-services"></a>Kapitel 3 – Beskrivning av FTP-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX FTP-tjänster (visas nedan) i alfabetisk ordning (förutom där IPv4-och IPv6-motsvarigheter till samma tjänst paras ihop).

> [!NOTE]
> I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Ansluta till en FTP-server via IPv4

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ansluter den tidigare skapade FTP-NetX till FTP-servern på den angivna IP-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **server_ip** IP-adressen för FTP-servern.
- **användar namn** Klientens användar namn för autentisering.
- **lösen ord** Klient lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på anslutning till FTP-klienten. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-anslutning.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) fick inget 22X-svar (OK)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) fick inget 23X-svar (OK)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) fick inget 33X-svar (OK)
- **NX_FTP_NOT_DISCONNECTED** (0xD4)-klienten är redan ansluten.
- NX_PTR_ERROR (0x07) ogiltig pekare inmatade.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.
- NX_IP_ADDRESS_ERROR (0x21) ogiltig IP-adress.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>Se även

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect

## <a name="nxd_ftp_client_connect"></a>nxd_ftp_client_connect

Ansluta till en FTP-server med IPv6-stöd

### <a name="prototype"></a>Prototyp

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ansluter den tidigare skapade NetX Duo FTP-serverinstansen till FTP-servern på den angivna IP-adressen. Både IPv4-och IPv6-nätverk stöds.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **server_ipduo** IP-adressen för FTP-servern.
- **användar namn** Klientens användar namn för autentisering.
- **lösen ord** Klient lösen ord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på anslutning till FTP-klienten. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-anslutning.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) fick inget 22X-svar (OK)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) fick inget 23X-svar (OK)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) fick inget 33X-svar (OK)
- **NX_FTP_NOT_DISCONNECTED** -klienten (0xD4) är redan ansluten
- NX_PTR_ERROR (0x07) ogiltigt nedpilens Inout.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.
- NX_IP_ADDRESS_ERROR (0x21) ogiltig IP-adress.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>Se även

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Skapa en instans av FTP-klienten

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en FTP-serverinstans.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **ftp_client_name** Namn på FTP-klient.
- **ip_ptr** Pekare till den tidigare skapade IP-instansen.
- **window_size** Annonserad fönster storlek för TCP-Sockets för den här FTP-klienten.
- **pool_ptr** Pekar på den här FTP-klientens standardpool för paket. Observera att den minsta paket nytto lasten måste vara tillräckligt stor för att rymma fullständig sökväg och fil-eller katalog namnet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-klient skapa.
- NX_PTR_ERROR (0x07) ogiltig pekare inmatade.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Ta bort en FTP-klient instans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en instans av FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-klient ta bort.
- **NX_FTP_NOT_DISCONNECTED** (0XD4) FTP-klienten är inte frånkopplad
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Skapa en katalog på en FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **directory_name** Namnet på den katalog som ska skapas.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-katalogen ska skapas. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-katalog skapa.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Ange standard katalog på FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger standard katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Den här standard katalogen gäller endast för den här klientens anslutning.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **directory_path** Namnet på den katalog Sök väg som ska anges.
- **wait_option** Definierar hur länge tjänsten ska vänta på katalog uppsättningen för FTP-katalogen. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP standard uppsättning.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Ta bort katalog på FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **directory_name** Namnet på den katalog som ska tas bort.
- **wait_option** Definierar hur länge tjänsten ska vänta på borttagning av FTP-katalogen. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) FTP-katalogen har tagits bort.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Hämta katalog lista från FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Den tillhandahållna paket pekaren innehåller en eller flera katalog poster. Varje post avgränsas med en \<cr/lf\> kombination. ***Nx_ftp_client_directory_listing_continue*** ska anropas för att slutföra hämtningen av katalogen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **directory_name** Namnet på den katalog som innehållet ska hämtas från.
- **packet_ptr** Pekare till pekare för mål paket. Om det lyckas kommer paketets nytto last att innehålla en eller flera katalog poster.
- **wait_option** Definierar hur länge tjänsten ska vänta på lista över FTP-kataloger. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) lista över slutförda FTP-kataloger.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- Tjänsten **NX_NOT_ENABLED** (0x14) (IPv6) är inte aktive rad
- **NX_FTP_EXPECTED_1XX_CODE** (0xD9) fick inget 1xx-svar (OK)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Fortsätt katalog listan från FTP-servern

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten fortsätter att hämta innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Det bör ha föregås av ett anrop till ***nx_ftp_client_directory_listing_get***. Om det lyckas kommer den tillhandahållna paket pekaren innehålla en eller flera katalog poster. Den här rutinen ska anropas tills en NX_FTP_END_OF_LISTING-status tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **packet_ptr** Pekare till pekare för mål paket. Om det lyckas innehåller paketets nytto Last en eller flera katalog poster, avgränsade med <CR/LF>.
- **wait_option** Definierar hur länge tjänsten ska vänta på lista över FTP-kataloger. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) lista över slutförda FTP-kataloger.
- **NX_FTP_END_OF_LISTING** (0XD8) inga fler poster i den här katalogen.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Koppla från FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar från en tidigare upprättad FTP-server-anslutning till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **wait_option** Definierar hur länge tjänsten ska vänta tills FTP-klienten kopplas från. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-anslutning.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Stäng klient filen

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger en tidigare öppnad fil på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientprogramvaran stängs. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-fil.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_NOT_OPEN (0xD5)** Filen är inte öppen; Det går inte att stänga den
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Ta bort fil på FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna filen på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **file_name** Namn på filen som ska tas bort.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klienttjänsten ska tas bort. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) FTP-filen har tagits bort.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Öppnar filen på FTP-servern

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten öppnar den angivna filen – för att läsa eller skriva – på FTP-servern som tidigare var ansluten till den angivna klient instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **file_name** Namnet på filen som ska öppnas.
- **open_type** Antingen **NX_FTP_OPEN_FOR_READ** eller **NX_FTP_OPEN_FOR_WRITE**.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klienttjänsten är öppen. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-fil öppen.
- **NX_OPTION_ERROR** (0X0a) ogiltig öppen typ.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_NOT_CLOSED** (0XD6) FTP-klienten har redan öppnats.
- **NX_NO_FREE_PORTS** (0x45) det finns inga tillgängliga TCP-portar att tilldela
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Läsa från fil

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser ett paket från en tidigare öppnad fil. Den bör anropas upprepade gånger tills en status för NX_FTP_END_OF_FILE tas emot.

Observera att anroparen inte allokerar ett paket för den här tjänsten.  Du behöver bara ange en pekare till en paket pekare. Den här tjänsten kommer att uppdatera paket pekaren så att den pekar på ett paket som hämtats från socket Receive-kön.  Om statusen lyckades returneras, innebär det att det fanns ett tillgängligt paket och att det är anroparens ansvar att frigöra paketet när det är klart.

Om en status som inte är noll (antingen en fel status eller NX_FTP_END_OF_FILE) returneras, frigörs inte paketet av anroparen. Annars genereras ett fel när paket pekaren är NULL.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **packet_ptr** Pekare till målet för data paket pekaren som ska lagras. Om det lyckas kan paketet vara en del av eller alla innehåller filen.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientdatorn läses. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en lyckad FTP-fil har lästs.
- **NX_FTP_NOT_OPEN** (0XD5) FTP-klienten är inte öppen.
- **NX_FTP_END_OF_FILE** (0xD7) fil villkoret är slut.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Byt namn på fil på FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten byter namn på en fil på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **filename** Aktuellt fil namn.
- **new_filename** Nytt namn på filen.
- **wait_option** Definierar hur länge tjänsten ska vänta på att byta namn på FTP-klienter. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) namn på slutförd FTP-fil.
- **NX_FTP_NOT_CONNECTED** (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_3XX_CODE** (0XDD) fick inte svar på 3xx (OK)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Skriv till fil

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skriver ett data paket till den tidigare öppnade filen på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **packet_ptr** Paket pekare som innehåller data som ska skrivas.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientdatorn skriver. Vänte alternativen definieras enligt följande:
  - **timeout-värde** (0X00000001 till 0xFFFFFFFE) om du väljer ett numeriskt värde (1-0xFFFFFFFE) anger det maximala antalet timer-Tick som ska förbli pausade vid väntan på FTP-serverns svar.
  - **TX_WAIT_FOREVER** (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden pausas under obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) lyckad FTP-fil skrivning.
- **NX_FTP_NOT_OPEN** (0XD5) FTP-klienten är inte öppen.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Aktivera eller inaktivera passivt överförings läge

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar passivt överförings läge om passive_mode_enabled indatatypen är inställd på NX_TRUE på en tidigare skapad FTP-serverinstans, så att efterföljande anrop till läsa eller skriva filer (RETR, lagr) eller hämtning av en katalog lista (NLST) görs i överförings läge. Om du vill inaktivera överföring i passivt läge och återgå till standard beteendet för aktivt överförings läge, anropar du den här funktionen med passive_mode_enabled indatamängden för att NX_FALSE.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till kontroll block för FTP-klient.
- **passive_mode_enabled** Om värdet är NX_TRUE aktive ras passivt läge.<br />Om värdet är NX_FALSE inaktive ras passivt läge.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) har angetts i passivt läge.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_INVALID_PARAMETERS (0x4D) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Skapa FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen. Observera att FTP-servern måste startas med ett anrop till ***nx_ftp_server_start*** för att det ska kunna starta åtgärden.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till kontroll block för FTP-server.
- **ftp_server_name** Namn på FTP-server.
- **ip_ptr** Pekare till den associerade NetX IP-instansen. Obs! det kan bara finnas en FTP-server för en IP-instans.
- **media_ptr** Pekare till den associerade FileX Media-instansen.
- **stack_ptr** Pekar på minne för den interna FTP-serverns stack-tråd.
- **stack_size** Storlek på det stack områden som anges av *stack_ptr*.
- **pool_ptr** Pekare till standard NetX. Observera nytto Last storleken för paket i poolen måste vara tillräckligt stor för att rymma största fil namn/sökväg.
- **ftp_login** Funktions pekare till programmets inloggnings funktion. Den här funktionen anges användar namn och lösen ord från klienten som begär en anslutning och klient adressen i data typen ULONG. Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.
- **ftp_logout** Funktions pekare till programmets utloggnings funktion. Den här funktionen anges användar namn och lösen ord från klienten som begär en från koppling och klient adressen i data typen ULONG. Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-server skapa.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a>nxd_ftp_server_create

Skapa FTP-server med stöd för IPv4 och IPv6

### <a name="prototype"></a>Prototyp

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen. Observera att FTP-servern fortfarande måste startas med ett anrop till ***nx_ftp_server_start*** för att den ska kunna påbörjas när servern har skapats.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till kontroll block för FTP-server.
- **ftp_server_name** Namn på FTP-server.
- **ip_ptr** Pekare till den associerade NetX IP-instansen. Obs! det kan bara finnas en FTP-server för en IP-instans.
- **media_ptr** Pekare till den associerade FileX Media-instansen.
- **stack_ptr** Pekar på minne för den interna FTP-serverns stack-tråd.
- **stack_size** Storlek på det stack områden som anges av *stack_ptr*.
- **pool_ptr** Pekare till standard NetX. Observera nytto Last storleken för paket i poolen måste vara tillräckligt stor för att rymma största fil namn/sökväg.
- **ftp_login_duo** Funktions pekare till programmets inloggnings funktion. Den här funktionen anges användar namn och lösen ord från klienten som begär en anslutning och en pekare till klient adressen i NXD_ADDRESS data typen. Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.
- **ftp_logout_duo** Funktions pekare till programmets utloggnings funktion. Den här funktionen anges användar namn och lösen ord från klienten som begär en från koppling, och en pekare till klient adressen i NXD_ADDRESS data typen. Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd FTP-server skapa.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Ta bort FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en instans av en tidigare skapad FTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till kontroll block för FTP-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) slutförd borttagning av FTP-server.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Starta FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en instans av en tidigare skapad FTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till kontroll block för FTP-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0X00) SLUTFÖRDE FTP-servern.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Stoppa FTP-Server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar en instans av en tidigare skapad och startad FTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till kontroll block för FTP-server.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS** (0x00) en slutförd FTP-server stoppades.
- NX_PTR_ERROR (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
