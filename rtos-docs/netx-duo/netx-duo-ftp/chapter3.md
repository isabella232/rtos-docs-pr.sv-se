---
title: Kapitel 3 – Beskrivning av FTP-tjänster
description: Det här kapitlet innehåller en beskrivning av alla NetX FTP-tjänster (visas nedan) i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d08d3c07f7be016ece68ff2f58b9ac5ba93ded780105bce362674ed36b5b885d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792374"
---
# <a name="chapter-3---description-of-ftp-services"></a>Kapitel 3 – Beskrivning av FTP-tjänster

Det här kapitlet innehåller en beskrivning av alla NetX FTP-tjänster (visas nedan) i alfabetisk ordning (förutom där IPv4- och IPv6-motsvarigheter till samma tjänst är sammankopplade).

> [!NOTE]
> I avsnittet "Returvärden" i följande API-beskrivningar påverkas inte värden i **FETSTIL** av **den NX_DISABLE_ERROR_CHECKING-definition** som används för att inaktivera API-felkontroll, medan värden som inte är fetstilta är helt inaktiverade.

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Anslut till en FTP-server via IPv4

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten ansluter den tidigare skapade NetX FTP-klientinstansen till FTP-servern på den angivna IP-adressen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **server_ip** IP-adress för FTP-server.
- **användarnamn** Klientens användarnamn för autentisering.
- **lösenord** Klientlösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på FTP-klientanslutningen. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-anslutning.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) Fick inget 22X-svar (ok)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) Fick inget 23X-svar (ok)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) Fick inget 33X-svar (ok)
- **NX_FTP_NOT_DISCONNECTED** (0xD4) Klienten är redan ansluten.
- NX_PTR_ERROR (0x07) Ogiltig pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.
- NX_IP_ADDRESS_ERROR (0x21) Ogiltig IP-adress.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anslut till en FTP-server med stöd för IPv6

### <a name="prototype"></a>Prototyp

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten ansluter den tidigare skapade NetX Duo FTP-klientinstansen till FTP-servern på den angivna IP-adressen. Både IPv4- och IPv6-nätverk stöds.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **server_ipduo** IP-adressen för FTP-servern.
- **användarnamn** Klientens användarnamn för autentisering.
- **lösenord** Klientlösenord för autentisering.
- **wait_option** Definierar hur länge tjänsten ska vänta på FTP-klientanslutningen. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-anslutning.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) Fick inget 22X-svar (ok)
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) Fick inget 23X-svar (ok)
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) Fick inget 33X-svar (ok)
- **NX_FTP_NOT_DISCONNECTED** (0xD4) Klienten är redan ansluten
- NX_PTR_ERROR (0x07) Ogiltig pekare inout.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.
- NX_IP_ADDRESS_ERROR (0x21) Ogiltig IP-adress.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapa en FTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Description

Den här tjänsten skapar en FTP-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **ftp_client_name** Namn på FTP-klient.
- **ip_ptr** Pekare till ip-instans som skapats tidigare.
- **window_size** Annonserad fönsterstorlek för TCP-socketar för den här FTP-klienten.
- **pool_ptr** Pekare till standardpaketpoolen för den här FTP-klienten. Observera att den minsta paketnyttolasten måste vara tillräckligt stor för att innehålla den fullständiga sökvägen och fil- eller katalognamnet.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-klient.
- NX_PTR_ERROR (0x07) Ogiltig pekare.

### <a name="allowed-from"></a>Tillåts från

Initiering och trådar

### <a name="example"></a>Exempel

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Ta bort en FTP-klientinstans

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en FTP-klientinstans.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad borttagning av FTP-klient.
- **FTP-NX_FTP_NOT_DISCONNECTED** (0xD4) inte frånkopplad
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Skapa en katalog på FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skapar den angivna katalogen på DEN FTP-server som är ansluten till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **directory_name** Namnet på katalogen som ska skapas.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-katalogen skapas. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-katalog skapas.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Ange standardkatalog på FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten anger standardkatalogen på DEN FTP-server som är ansluten till den angivna FTP-klienten. Den här standardkatalogen gäller endast för den här klientens anslutning.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **directory_path** Namnet på katalogsökvägen som ska anges.
- **wait_option** Definierar hur länge tjänsten ska vänta på FTP-standardkataloguppsättningen. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-standarduppsättning.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Ta bort katalog på FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **directory_name** Namnet på katalogen som ska tas bort.
- **wait_option** Definierar hur länge tjänsten ska vänta på borttagning av FTP-katalogen. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av FTP-katalog.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Hämta kataloglista från FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten hämtar innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Den angivna paket pekaren innehåller en eller flera katalogposter. Varje post avgränsas med en \<cr/lf\> kombination. Den ***nx_ftp_client_directory_listing_continue*** anropas för att slutföra åtgärden för katalog get.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **directory_name** Namnet på katalogen som innehållet ska hämtas från.
- **packet_ptr** Pekare till målpakets pekare. Om det lyckas innehåller paketnyttolasten en eller flera katalogposter.
- **wait_option** Definierar hur länge tjänsten ska vänta på FTP-kataloglistan. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-kataloglista.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_NOT_ENABLED** (0x14) Tjänst (IPv6) inte aktiverad
- **NX_FTP_EXPECTED_1XX_CODE** (0xD9) Fick inget 1XX-svar (ok)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Fortsätt kataloglistan från FTP-servern

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten fortsätter att hämta innehållet i den angivna katalogen på FTP-servern som är ansluten till den angivna FTP-klienten. Det bör ha föregås av ett anrop till ***nx_ftp_client_directory_listing_get***. Om det lyckas innehåller den angivna paket pekaren en eller flera katalogposter. Den här rutinen ska anropas tills en NX_FTP_END_OF_LISTING status tas emot.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **packet_ptr** Pekare till målpakets pekare. Om det lyckas innehåller paketnyttolasten en eller flera katalogposter, avgränsade med en <cr/lf>.
- **wait_option** Definierar hur länge tjänsten ska vänta på FTP-kataloglistan. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-kataloglista.
- **NX_FTP_END_OF_LISTING** (0xD8) Inga fler poster i den här katalogen.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Koppla från FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten kopplar från en tidigare upprättad FTP-serveranslutning med den angivna FTP-klienten.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klienten kopplas från. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ftp-frånkoppling.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Stäng klientfilen

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten stänger en fil som öppnats tidigare på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientfilen stängs. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-fil stäng.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_NOT_OPEN (0xD5)** Filen är inte öppen; kan inte stänga den
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Ta bort fil på FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna filen på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **file_name** Namnet på filen som ska tas bort.
- **wait_option** Definierar hur länge tjänsten ska vänta på borttagning av FTP-klientfilen. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad BORTTAGNING av FTP-fil.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten öppnar den angivna filen – för läsning eller skrivning – på den FTP-server som tidigare var ansluten till den angivna klientinstansen.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **file_name** Namnet på filen som ska öppnas.
- **open_type** Antingen **NX_FTP_OPEN_FOR_READ** eller **NX_FTP_OPEN_FOR_WRITE**.
- **wait_option** Definierar hur länge tjänsten ska vänta tills FTP-klientfilen är öppen. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-fil öppen.
- **NX_OPTION_ERROR** (0x0A) Ogiltig öppen typ.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **FTP NX_FTP_NOT_CLOSED klienten** (0xD6) har redan öppnats.
- **NX_NO_FREE_PORTS** (0x45) Inga TCP-portar som kan tilldelas
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten läser ett paket från en fil som öppnats tidigare. Det bör anropas upprepade tills statusen NX_FTP_END_OF_FILE tas emot.

Observera att anroparen inte allokerar något paket för den här tjänsten.  Den behöver bara ange en pekare till en paket pekare. Den här tjänsten uppdaterar paket pekaren så att den pekar på ett paket som hämtats från socket-mottagningskön.  Om en lyckad status returneras innebär det att det fanns ett tillgängligt paket och det är anroparens ansvar att släppa paketet när det är klart.

Om en status som inte är noll (antingen en felstatus eller NX_FTP_END_OF_FILE) returneras släpper inte anroparen paketet. Annars genereras ett fel när paket pekaren är NULL.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **packet_ptr** Pekare till mål för datapaketspekaren som ska lagras. Om det lyckas innehåller paketet en del eller alla filer i filen.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientfilen ska läsas. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-filläsning.
- **FTP NX_FTP_NOT_OPEN klienten** (0xD5) öppnas inte.
- **NX_FTP_END_OF_FILE** (0xD7) Slutet på filvillkoret.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Byt namn på fil på FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten byter namn på en fil på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **filnamn** Aktuellt namn på filen.
- **new_filename** Nytt namn för filen.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientfilen byter namn. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Namnbyte av FTP-fil.
- **NX_FTP_NOT_CONNECTED** (0xD3) FTP-klienten är inte ansluten.
- **NX_FTP_EXPECTED_3XX_CODE** (0XDD) Fick inget 3XX-svar (ok)
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) Fick inget 2XX-svar (ok)
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Skriva till fil

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Den här tjänsten skriver ett datapaket till den tidigare öppnade filen på FTP-servern.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **packet_ptr** Paket pekare som innehåller data som ska skrivas.
- **wait_option** Definierar hur länge tjänsten ska vänta på att FTP-klientfilen ska skrivas. Väntealternativen definieras på följande sätt:
  - **timeout-värde** (0x00000001 till 0xFFFFFFFE) Om du väljer ett numeriskt värde (1-0xFFFFFFFE) anges det maximala antalet timer tick som ska pausas medan du väntar på FTP-serversvaret.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) Om du TX_WAIT_FOREVER här alternativet pausas anropstråden på obestämd tid tills en FTP-server svarar på begäran.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-filskrivning.
- **FTP NX_FTP_NOT_OPEN klienten** (0xD5) öppnas inte.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Aktivera eller inaktivera passivt överföringsläge

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar passivt överföringsläge om passive_mode_enabled-indata har angetts till NX_TRUE på en ftp-klientinstans som skapats tidigare, så att efterföljande anrop till att läsa eller skriva filer (RETR, STOR) eller ladda ned en kataloglista (NLST) görs i överföringsläge. Om du vill inaktivera överföring i passivt läge och återgå till standardbeteendet för aktivt överföringsläge anropar du den här funktionen med passive_mode_enabled indata inställt på NX_FALSE.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_client_ptr** Pekare till KONTROLLblock för FTP-klient.
- **passive_mode_enabled** Om det är NX_TRUE läge är passivt läge aktiverat.<br />Om det är NX_FALSE läge inaktiveras passivt läge.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad passiv lägesuppsättning.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_INVALID_PARAMETERS (0x4D) Ogiltiga icke-pekarindata

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Skapa FTP-server

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

### <a name="description"></a>Description

Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen. Observera att FTP-servern måste startas med ett anrop till ***nx_ftp_server_start för*** att den ska starta åtgärden.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till KONTROLLblock för FTP-server.
- **ftp_server_name** Namn på FTP-server.
- **ip_ptr** Pekare till associerad NetX IP-instans. Observera att det bara kan finnas en FTP-server för en IP-instans.
- **media_ptr** Pekare till associerad FileX-medieinstans.
- **stack_ptr** Pekare till minnet för den interna FTP-servertrådens stackområde.
- **stack_size** Storleken på stackområdet som anges av *stack_ptr*.
- **pool_ptr** Pekare till netX-standardpaketpoolen. Observera att nyttolaststorleken för paket i poolen måste vara tillräckligt stor för att hantera det största filnamnet/sökvägen.
- **ftp_login** Funktionspekare till programmets inloggningsfunktion. Den här funktionen anges användarnamnet och lösenordet från klienten som begär en anslutning och klientadressen i ULONG-datatypen. Om detta är giltigt ska programmets inloggningsfunktion returnera NX_SUCCESS.
- **ftp_logout** Funktionspekare till programmets utloggningsfunktion. Den här funktionen anges användarnamnet och lösenordet från klienten som begär frånkoppling och klientadressen i ULONG-datatypen. Om detta är giltigt ska programmets inloggningsfunktion returnera NX_SUCCESS.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-server skapas.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten skapar en FTP-serverinstans på den angivna och tidigare skapade NetX IP-instansen. Observera att FTP-servern fortfarande måste startas med ett ***anrop till nx_ftp_server_start*** för att den ska kunna starta åtgärden när servern har skapats.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till FTP-serverkontrollblock.
- **ftp_server_name** Namn på FTP-server.
- **ip_ptr** Pekare till associerad NetX IP-instans. Observera att det bara kan finnas en FTP-server för en IP-instans.
- **media_ptr** Pekare till associerad FileX-medieinstans.
- **stack_ptr** Pekare till minnet för den interna FTP-servertrådens stackområde.
- **stack_size** Storleken på stackområdet som anges av *stack_ptr*.
- **pool_ptr** Pekare till netX-standardpaketpoolen. Observera att nyttolaststorleken för paket i poolen måste vara tillräckligt stor för att hantera det största filnamnet/sökvägen.
- **ftp_login_duo** Funktionspekare till programmets inloggningsfunktion. Den här funktionen anges användarnamnet och lösenordet från klienten som begär en anslutning och en pekare till klientadressen i NXD_ADDRESS datatypen. Om detta är giltigt ska programmets inloggningsfunktion returnera NX_SUCCESS.
- **ftp_logout_duo** Funktionspekare till programmets utloggningsfunktion. Den här funktionen anges användarnamnet och lösenordet från klienten som begär en frånkoppling och en pekare till klientadressen i NXD_ADDRESS datatypen. Om detta är giltigt ska programmets inloggningsfunktion returnera NX_SUCCESS.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-server skapas.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

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

Ta bort FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten tar bort en FTP-serverinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till FTP-serverkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Borttagning av FTP-server.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Starta FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten startar en FTP-serverinstans som skapats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till FTP-serverkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Lyckad FTP-serverstart.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Stoppa FTP-server

### <a name="prototype"></a>Prototyp

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Description

Den här tjänsten stoppar en FTP-serverinstans som skapats och startats tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **ftp_server_ptr** Pekare till FTP-serverkontrollblock.

### <a name="return-values"></a>Returvärden

- **NX_SUCCESS** (0x00) Ftp-servern stoppas.
- NX_PTR_ERROR (0x07) Ogiltig FTP-pekare.
- NX_CALLER_ERROR (0x11) Ogiltig anropare för den här tjänsten.

### <a name="allowed-from"></a>Tillåts från

Trådar

### <a name="example"></a>Exempel

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
