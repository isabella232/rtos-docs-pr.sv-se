---
title: Kapitel 3 – Beskrivning av Azure återställnings tider NetX FTP Services
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX FTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826721"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a>Kapitel 3 – Beskrivning av Azure återställnings tider NetX FTP Services

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider NetX FTP-tjänster (visas nedan) i alfabetisk ordning.

I avsnittet "retur värden" i följande API-beskrivningar påverkas inte värden i **fetstil** av **NX_DISABLE_ERROR_CHECKING** definiera som används för att inaktivera API-felkontroll, medan icke-Fetstilade värden är helt inaktiverade.

- **nx_ftp_client_connect**: *Anslut till FTP-server*
- **nx_ftp_client_create**: *skapa en instans av FTP-klienten*
- **nx_ftp_client_delete**: *ta bort en instans av FTP-klienten*
- **nx_ftp_client_directory_create**: *skapa en katalog på servern*
- **nx_ftp_client_directory_default_set**: *Ange standard katalog på servern*
- **nx_ftp_client_directory_delete**: *ta bort en katalog på servern*
- **nx_ftp_client_directory_listing_get**: *Hämta katalog lista från Server*
- **nx_ftp_client_directory_listing_continue**: *Fortsätt katalog listan från servern*
- **nx_ftp_client_disconnect**: *Koppla från FTP-server*
- **nx_ftp_client_file_close**: *Stäng klient filen*
- **nx_ftp_client_file_delete**: *ta bort filen på servern*
- **nx_ftp_client_file_open**: *Öppna klient filen*
- **nx_ftp_client_file_read**: *läsa från fil*
- **nx_ftp_client_file_rename**: *Byt namn på filen på servern*
- **nx_ftp_client_file_write**: *Skriv till fil*
- **nx_ftp_server_create**: *Skapa FTP-server*
- **nx_ftp_server_delete**: *ta bort FTP-server*
- **nx_ftp_server_start**: *starta FTP-server*
- **nx_ftp_server_stop**: *Stoppa FTP-server*

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Ansluta till en FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ansluter den tidigare skapade FTP-klienttjänsten till FTP-servern på den angivna IP-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **server_ip**: IP-adressen för FTP-servern.
- **username**: klientens användar namn för autentisering.
- **lösen ord**: klient lösen ord för autentisering.
- **wait_option**: anger hur länge tjänsten ska vänta på anslutning till FTP-klienten. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutförd FTP-anslutning.
- **NX_TFTP_EXPECTED_22X_CODE**: (0xDB) fick inget 22X-svar (OK)
- **NX_FTP_EXPECTED_23X_CODE**: (0xDC) fick inget 23X-svar (OK)
- **NX_FTP_EXPECTED_33X_CODE**: (0xDE) fick inget 33X-svar (OK)
- **NX_FTP_NOT_DISCONNECTED**: (0xD4)-klienten är redan ansluten.
- NX_PTR_ERROR: (0x07) ogiltig pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.
- NX_IP_ADDRESS_ERROR: (0x21) ogiltig IP-adress.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Skapa en instans av FTP-klienten

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en FTP-serverinstans.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **ftp_client_name**: namnet på FTP-klienten.
- **ip_ptr**: pekare till den tidigare skapade IP-instansen.
- **window_size**: annonserad fönster storlek för TCP-socket för denna FTP-klient.
- **pool_ptr**: pekar mot standardpoolen för den här FTP-klienten. Observera att den minsta paket nytto lasten måste vara tillräckligt stor för att rymma fullständig sökväg och fil-eller katalog namnet.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-klient skapa.
- NX_PTR_ERROR: (0x16) ogiltig FTP, IP-pekare eller adresspool. lösen ords pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Ta bort en FTP-klient instans

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en instans av FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutförd FTP-klient ta bort.
- **NX_FTP_NOT_DISCONNECTED**: (0XD4) FTP-klient ta bort fel.
- NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Skapa en katalog på en FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **directory_name**: namnet på den katalog som ska skapas.
- **wait_option**: anger hur länge tjänsten ska vänta på att FTP-katalogen ska skapas. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-katalog skapa.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK) 
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare. 
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Ange standard katalog på FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger standard katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Den här standard katalogen gäller endast för den här klientens anslutning.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **directory_path**: namnet på den katalog Sök väg som ska anges.
- **wait_option**: definierar hur länge tjänsten ska vänta på katalog uppsättningen för FTP-katalogen. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP standard uppsättning.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK) 
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare. 
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Ta bort katalog på FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **directory_name**: namnet på den katalog som ska tas bort.
- **wait_option**: anger hur länge tjänsten ska vänta på borttagning av FTP-katalogen. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutförd borttagning av FTP-katalogen.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK) 
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare. 
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Hämta katalog lista från FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Den tillhandahållna paket pekaren innehåller en eller flera katalog poster. Varje post skiljs åt av en &lt; CR/LF \-kombination. ***Nx_ftp_client_directory_listing_continue***: ska anropas för att slutföra hämtningen av katalogen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **directory_name**: namnet på den katalog som innehållet ska hämtas från.
- **packet_ptr**: pekar mot mål paket pekare. Om det lyckas kommer paketets nytto last att innehålla en eller flera katalog poster.
- **wait_option**: definierar hur länge tjänsten ska vänta på listan över FTP-kataloger. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) lista över lyckade FTP-kataloger.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_NOT_ENABLED**: (0X14) service (IPv6) är inte aktive rad
- **NX_FTP_EXPECTED_1XX_CODE**: (0xD9) fick inget 1xx-svar (OK)
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Fortsätt katalog listan från FTP-servern

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten fortsätter att hämta innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Det bör ha föregås av ett anrop till ***nx_ftp_client_directory_listing_get***. Om det lyckas kommer den tillhandahållna paket pekaren innehålla en eller flera katalog poster. Den här rutinen ska anropas tills en NX_FTP_END_OF_LISTING-status tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **packet_ptr**: pekar mot mål paket pekare. Om det lyckas innehåller paketets nytto Last en eller flera katalog poster, avgränsade med &lt; CR/LF &gt; .
- **wait_option**: definierar hur länge tjänsten ska vänta på listan över FTP-kataloger. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) lista över lyckade FTP-kataloger.
- **NX_FTP_END_OF_LISTING**: (0XD8) inga fler poster i den här katalogen.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Koppla från FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten kopplar från en tidigare upprättad FTP-server-anslutning till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **wait_option**: anger hur länge tjänsten ska vänta tills FTP-klienten kopplas från. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-från koppling.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Stäng klient filen

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stänger en tidigare öppnad fil på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **wait_option**: anger hur länge tjänsten ska vänta på att FTP-klientprogramvaran stängs. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-fil stängs.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_NOT_OPEN (0xD5)**: filen är inte öppen. Det går inte att stänga den
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Ta bort fil på FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna filen på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **file_name**: namnet på filen som ska tas bort.
- **wait_option**: anger hur länge tjänsten ska vänta på att ta bort FTP-klienten. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-fil borttagning.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Öppnar filen på FTP-servern

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten öppnar den angivna filen – för att läsa eller skriva – på FTP-servern som tidigare var ansluten till den angivna klient instansen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **file_name**: namnet på filen som ska öppnas.
- **open_type**: antingen **NX_FTP_OPEN_FOR_READ** eller **NX_FTP_OPEN_FOR_WRITE**.
- **wait_option**: anger hur länge tjänsten ska vänta på att FTP-klienttjänsten är öppen. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-fil öppen.
- **NX_OPTION_ERROR**: (0X0a) ogiltig öppen typ.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_NOT_CLOSED**: (0XD6) FTP-klienten har redan öppnats.
- **NX_NO_FREE_PORTS**: (0x45) det finns inga tillgängliga TCP-portar att tilldela
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Läsa från fil

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser ett paket från en tidigare öppnad fil. Den bör anropas upprepade gånger tills en status för NX_FTP_END_OF_FILE tas emot.

Observera att anroparen inte allokerar ett paket för den här tjänsten.  Du behöver bara ange en pekare till en paket pekare. Den här tjänsten kommer att uppdatera paket pekaren så att den pekar på ett paket som hämtats från socket Receive-kön.  Om statusen lyckades returneras, innebär det att det fanns ett tillgängligt paket och att det är anroparens ansvar att frigöra paketet när det är klart.

Om en status som inte är noll (antingen en fel status eller NX_FTP_END_OF_FILE) returneras, frigörs inte paketet av anroparen. Annars genereras ett fel när paket pekaren är NULL.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **packet_ptr**: pekare till målet för data paket pekaren som hämtades från kön. Om det lyckas innehåller paket data en del av eller hela filen.
- **wait_option**: anger hur länge tjänsten ska vänta på att FTP-klientdatorn läses. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-fil har lästs.
- **NX_FTP_NOT_OPEN**: (0XD5) FTP-klienten är inte öppen.
- **NX_FTP_END_OF_FILE**: (0xD7) fil villkoret är slut.
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

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

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Byt namn på fil på FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten byter namn på en fil på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **filename**: aktuellt fil namn.
- **new_filename**: nytt namn på filen.
- **wait_option**: anger hur länge tjänsten ska vänta på att byta namn på FTP-klienten. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades FTP-filens namn.
- **NX_FTP_NOT_CONNECTED**: (0XD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_3XX_CODE**: (0XDD) fick inte svar på 3xx (OK)
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) fick inget 2xx-svar (OK)
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Skriv till fil

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skriver ett data paket till den tidigare öppnade filen på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **packet_ptr**: paket pekare som innehåller data som ska skrivas.
- **wait_option**: anger hur länge tjänsten ska vänta på att FTP-klientdatorn skriver. Vänte alternativen definieras enligt följande:
  - **timeout-värde**: (0X00000001 till 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0Xffffffff) väljer TX_WAIT_FOREVER gör att anrops tråden inaktive ras under obestämd tid tills en FTP-server svarar på begäran. Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer-Tick som ska förbli pausade i väntan på FTP-serverns svar.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-fil skrivning.
- **NX_FTP_NOT_OPEN**: (0XD5) FTP-klienten är inte öppen.
- NX_PTR_ERROR: (0x07) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Aktivera eller inaktivera passivt överförings läge

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar passivt överförings läge om passive_mode_enabled indatatypen är inställd på NX_TRUE på en tidigare skapad FTP-serverinstans, så att efterföljande anrop till läsa eller skriva filer (RETR, lagr) eller hämtning av en katalog lista (NLST) görs i överförings läge. Om du vill inaktivera överföring i passivt läge och återgå till standard beteendet för aktivt överförings läge, anropar du den här funktionen med passive_mode_enabled indatamängden för att NX_FALSE.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr**: pekar mot FTP-klientens kontroll block.
- **passive_mode_enabled**:
  - Om värdet är NX_TRUE aktive ras passivt läge.
  - Om värdet är NX_FALSE inaktive ras passivt läge.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckades passivt läge.
- NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.
- NX_INVALID_PARAMETERS: (0x4D) ogiltig inmatad icke-pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Skapa FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen. Observera att FTP-servern måste startas med ett anrop till ***nx_ftp_server_start*** för att det ska kunna starta åtgärden.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr**: pekare till FTP Server Control Block.
- **ftp_server_name**: namnet på FTP-servern.
- **ip_ptr**: pekar mot associerad netx IP-instans. Obs! det kan bara finnas en FTP-server för en IP-instans.
- **media_ptr**: pekar mot associerad FileX Media-instans.
- **stack_ptr**: pekar på minne för den interna FTP-serverns stack-tråd.
- **stack_size**: storleken på det stack områden som anges av *stack_ptr*.
- **pool_ptr**: pekar mot standard netx. Observera nytto Last storleken för paket i poolen måste vara tillräckligt stor för att rymma största fil namn/sökväg.
- **ftp_login**: funktions pekare till programmets inloggnings funktion. Den här funktionen anges användar namn och lösen ord från klienten som begär en anslutning. Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.
- **ftp_logout**: funktions pekare till programmets utloggnings funktion. Den här funktionen anges användar namn och lösen ord från klienten som begär en från koppling. Om detta är giltigt ska programmets inloggnings funktion returnera NX_SUCCESS.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-server skapa.
- NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Ta bort FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort en instans av en tidigare skapad FTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr**: pekare till FTP Server Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) slutförd borttagning av FTP-server.
- NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Starta FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten startar en instans av en tidigare skapad FTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr**: pekare till FTP Server Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0X00) lyckad FTP-server startar.
- NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.

### <a name="allowed-from"></a>Tillåten från

Initiering och trådar

### <a name="example"></a>Exempel

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Stoppa FTP-Server

### <a name="prototype"></a>Prototyp

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten stoppar en instans av en tidigare skapad och startad FTP-server.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr**: pekare till FTP Server Control Block.

### <a name="return-values"></a>Retur värden

- **NX_SUCCESS**: (0x00) en slutförd FTP-server stoppas.
- NX_PTR_ERROR: (0x16) ogiltig FTP-pekare.
- NX_CALLER_ERROR: (0x11) ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
