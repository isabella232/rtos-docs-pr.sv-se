---
title: Kapitel 4 – Azure RTOS beskrivning av NetX Crypto API
description: Azure RTOS beskrivning av NetX Crypto API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5bd4cdae28a293ec9ef259bbd29fdb8f8d6dc43f964cbc184290b82ee8f590a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788815"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Kapitel 4 – Azure RTOS beskrivning av NetX Crypto API

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Initierar NetX Secure Library

### <a name="prototype"></a>Prototyp

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Description

Den här funktionen initierar Azure RTOS NetX Crypto-biblioteksmodulen. Innan du använder någon av de andra kryptografiska funktionerna måste programmet anropa den här funktionen för att utföra initiering och för att verifiera bibliotekets integritet. Om du inte anropar den här funktionen innan du använder andra NetX Crypto-tjänster returneras fel.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Ett lyckat initierat NetX Crypto-bibliotek. Biblioteksfunktionerna är nu klara och kan användas.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket kan inte initieras eller integritetskontrollen misslyckas. Programmet kan inte använda det här biblioteket.

### <a name="example"></a>Exempel

Todo

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Hämta aktuell status för den FIPS-aktiverade modulen

### <a name="prototype"></a>Prototyp

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Description

Den här tjänsten är endast tillgänglig i FIPS-byggbiblioteket. Den returnerar tillståndet för det aktuella tillståndet för NetX Crypto-biblioteket.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Returvärden

- **Statusflagga:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **Alla andra värden är ogiltiga.**

### <a name="example"></a>Exempel

Todo

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Initierar AES-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar AES-kontrollblocket med den angivna nyckelsträngen. När AES-kontrollblocket har initierats använder efterföljande AES-åtgärd samma nyckel- och nyckelstorlek.

Programmet kan skapa flera AES-kontrollblock, var och en representerar en session. En nyckel tilldelas till ett kontrollblock. Efterföljande krypterings- eller dekrypteringsåtgärd kan referera till samma AES-kontrollblock utan att behöva initiera om AES-kontrollblocket. Om nyckeln för sessionen ändras måste programmet initiera om AES-kontrollblocket med den uppdaterade nyckeln.

När _ *nx_crypto_method_aes_init() anropas* uppdateras automatiskt en tidigare konfigurerad nyckel och nyckelstorlek till den nya nyckeln.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för AES-kryptografimetoden. Följande fördefinierade AES-kryptografimetoder är tillgängliga:
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **nyckel** Pekar på en buffert som innehåller AES-nyckeln
- **key_size_in_bits** Nyckelns storlek, i bitar. Giltiga värden är:
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **Alla andra värden är ogiltiga.**
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för AES-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För AES måste metadatastorleken vara *sizeof(NX_AES)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av AES-kontrollblocket med nyckel- och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltigt crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Nyckelstorleken är inte giltig för AES.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

Utför en AES-åtgärd (kryptering eller dekryptering).

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>Description

Den här funktionen utför AES-krypterings- eller dekrypteringsåtgärden. AES-kontrollblocket måste ha initierats med _ *nx_crypto_method_aes_init()*. AES-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

Indatabuffertens storlek måste vara en multipel på 16 byte. Storleken på de dekrypterade data har samma storlek som storleken på indata. Om krypterade data har utfyllnad för att uppnå en jämn multipel av AES-blockstorleken inkluderas utfyllnaden i utdatabufferten och måste hanteras av programmet.

Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckelmaterial i AES-kontrollblocket.

När op är NX_CRYPTO_SET_ADDITIONAL_DATA och algoritmen är AES-CCM8, pekar indata på ytterligare data input_length_in_byte är längden på ytterligare data.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltiga opertioner är:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (endast AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (endast AES-CCM8)*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga AES-kryptografimetoden. Kryptometoden som används här måste vara samma som används i *nx_crypto_method_aes_init().*
- **input_data** Pekar på en buffert som innehåller krypterade textdata. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte. Storleken på indata måste vara en multipel på 16 byte.
- **iv_ptr** Pekare till den inledande vektorn. Det finns inga begränsningar för IV-bufferten.
- **iv_size** Storleken på det inledande vektorblocket i byte Det här fältet måste vara 16.
- **output_buffer** Pekare till minnesområdet för AES för att lagra klartextdata. Programmet måste allokera utrymme för utdatabufferten. Utdatabufferten kan överlappa indatabufferten. Utdatabufferten kan överlappa indatabufferten om de delar samma startadress.
- **output_buffer_size** Storleken på utdatabufferten i byte. Utdatabuffertens storlek måste vara minst samma som indatabuffertens storlek och utdatabuffertens storlek måste vara en multipel på 16 byte.
- **crypto_metadata** Pekare till AES-kontrollblocket som används *i _nx_crypto_method_aes_init() \* . \**
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För AES måste metadatastorleken *vara sizeof(NX_AES)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** – Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) AES-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig AES-algoritm anges**.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Rensa AES-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa AES-kontrollblocket när den här AES-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till AES-kontrollblocket som används *i _nx_crypto_method_aes_init() \* . \**

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Har rensat AES-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Initiera 3DES-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar kontrollblocket Triple DES (3DES) med de tre nyckelsträngarna. Nyckelsträngarna måste vara 8 byte vardera. De tre DES-nycklarna måste sammanfogas i sammanhängande minne av 24 byte-buffert. För FIPS-kompatibelt bygge måste de tre nycklarna vara olika från var och en, annars returnerar funktionen NX_CRYPTO_INVALID_KEY fel. När 3DES-kontrollblocket har initierats använder efterföljande 3DES-åtgärder samma nycklar.

Ett program kan skapa flera 3DES-kontrollblock, som var och en representerar en session. En nyckel tilldelas till ett kontrollblock och efterföljande krypterings- eller dekrypteringsåtgärder kan referera till samma kontrollblock utan att behöva initiera om. Om nyckeln för en session ändras måste programmet initiera om kontrollblocket med den uppdaterade nyckeln.

Anropa _ *nx_crypto_method_3des_init() uppdaterar* automatiskt en tidigare konfigurerad nyckel till de nya nycklarna.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för 3DES-kryptografimetod. Följande fördefinierade 3DES-kryptografimetod är tillgänglig: ***crypto_method_3des***
- **nyckel** Pekar på en buffert som innehåller den tre (3) DES-nyckeln
- **key_size_in_bits** Måste vara 192 (3 nycklar, var och en 64 bitar).
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen identifierar det 3DES-kontrollblock som initieras. Efterföljande 3DES-åtgärder (kryptering, dekryptering och rensning) använder den här referensen för att komma åt 3DES-kontrollblocket
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för 3DES-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För 3DES måste metadatastorleken vara *sizeof(NX_3DES)*

### <a name="return-value"></a>Returvärde

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av 3DES-kontrollblocket med nyckeln och nyckelstorleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltigt crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Nyckelstorleken är inte giltig för 3DES.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

Kryptera eller dekryptera med 3DES.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför 3DES-krypterings- eller dekrypteringsåtgärd. 3DES-kontrollblocket måste ha initierats med _ *nx_crypto_method_3des_init()*. 3DES-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

Indatabuffertens storlek måste vara flera på 8 byte. Storleken på de dekrypterade data har samma storlek som storleken på indata. Om krypterade data har utfyllnad för att uppnå en jämn multipel av blockstorleken 3DES inkluderas utfyllnaden i utdatabufferten och måste hanteras av programmet.

Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckelmaterial i 3DES-kontrollblocket.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltiga åtgärder är:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **handle** Referensen initieras av *_nx_crypto_method_3des_init()*.
- **metod** Pekare till den giltiga 3DES-kryptografimetoden. Kryptometoden som används här måste vara samma som används i *nx_crypto_method_3des_init().*
- **input_data** Pekar på en buffert som innehåller krypterade textdata.
Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte. Storleken på indata måste vara en multipel på 8 byte.
- **iv_ptr** Pekare till den inledande vektorn. Det finns inga begränsningar för IV-bufferten.
- **iv_size** Storleken på blocket Initial vektor i byte Det här fältet måste vara 8.
- **output_buffer** Pekare till minnesområdet för 3DES för att lagra klartextdata. Programmet måste allokera utrymme för utdatabufferten. Utdatabufferten kan överlappa indatabufferten. Utdatabufferten kan överlappa indatabufferten om de delar samma startadress.
- **output_buffer_size** Storleken på utdatabufferten i byte. Utdatabuffertens storlek måste vara minst samma som indatabuffertens storlek och utdatabuffertens storlek måste vara en multipel på 8 byte.
- **crypto_metadata** Pekare till 3DES-kontrollblocket som används *i _nx_crypto_method_3des_init()*.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För 3DES måste metadatastorleken vara *sizeof(NX_3DES)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="description"></a>Description

Den här funktionen utför 3DES-kryptering. 3DES-kontrollblocket måste ha initierats med _ *nx_crypto_moethod_3des_init()*. Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckelmaterial i 3DES-kontrollblocket. Observera att utfyllnad inte läggs till av den här funktionen, så anroparen måste hantera utfyllnad innan krypteringsåtgärden anropas.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av 3DES-kontrollblocket med nyckeln och nyckelstorleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltigt crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Rensa 3DES-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa 3DES-kontrollblocket när den här 3DES-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **handle** Referensen initieras av *_nx_crypto_method_3des_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Rensat 3DES-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

Initierar KRYPTO-kontrollblocket för DRBG

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar DRBG-kontrollblocket med den angivna nyckelsträngen. När DRBG-kontrollblocket har initierats ska efterföljande DRBG-åtgärd använda samma kontrollblock.

Programmet kan skapa flera DRBG-kontrollblock, var och en representerar en session. Initiering av DRBG-kontrollblocket startar en ny hash-beräkningssession. Om du initierar om DRBG-kontrollblocket överger den aktuella sessionen och spelar in en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för DRBG-kryptometoden. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_drbg*
- **nyckel** Det här fältet används inte för DRBG.
- **key_size_in_bits** Det här fältet används inte för DRBG.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för DRBG-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För DRBG måste metadatastorleken vara *sizeof(NX_CRYPTO_DRBG)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av DRBG-kontrollblocket med nyckeln och nyckelstorleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Utföra DRBG-åtgärd

### <a name="prototype"></a>Prototyp

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför DRBG-åtgärden. DRBG-kontrollblocket måste ha initierats med _ *nx_crypto_method_drbg_init()*. DRBG-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.* Som standard används AES-128 för DRBG.

När åtgärden är NX_CRYPTO_DRBG_OPTIONS_SET pekar indata till NX_CRYPTO_DRBG_OPTIONS struktur. När åtgärden är NX_CRYPTO_DRBG_INSTANTIATE pekar nyckeln på nonce, indata pekar på anpassningssträngen. När åtgärden är NX_CRYPTO_DRBG_RESEED eller NX_CRYPTO_DRBG_GENERATE pekar indata på ytterligare indata.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga DRBG-kryptografimetoden. Kryptometoden som används här måste vara samma som används i _ *nx_crypto_method_drbg_init().*
- **nyckel** Pekare till nonce för instansiera åtgärden. Det här fältet används inte för andra åtgärder.
- **key_size_in_bits** Nonce-storleken, i bitar. Det här fältet används inte för andra åtgärder.
- **indata** När op är NX_CRYPTO_DRBG_OPTIONS_SET pekar det här fältet på DRBG-alternativ. När op är NX_CRYPTO_DRBG_INSTANTIATE pekar det här fältet på anpassningssträngen. När op är NX_CRYPTO_DRBG_RESEED eller NX_CRYPTO_DRBG_GENERATE pekar det här fältet på ytterligare indata.
- **input_length_in_byte** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för DRBG.
- **utdata** När op NX_CRYPTO_DRBG_GENERATE pekar det här fältet på minnesområdet för den genererade DRBG:en. Annars används inte det här fältet.
- **output_length_in_byte** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till DRBG-kontrollblocket som används *i _nx_crypto_method_drbg_init()*.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För DRBG måste metadatastorleken *vara sizeof(NX_CRYPTO_DRBG)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) DRBG-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig DRBG-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Rensa DRBG-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa DRBG-kontrollblocket när den här DRBG-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till DRBG-kontrollblocket som används *i _nx_crypto_method_drbg_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HAR rensat DRBG-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

Initierar ECDH-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar ECDH-kontrollblocket med den angivna nyckelsträngen. När ECDH-kontrollblocket har initierats ska efterföljande ECDH-åtgärd använda samma kontrollblock.

Programmet kan skapa flera ECDH-kontrollblock, var och en representerar en session. När ECDH-kontrollblocket initieras startar en ny hash-beräkningssession. När ECDH-kontrollblocket initieras på nytt överger den aktuella sessionen och en ny initieras.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt ecdh-kryptografimetodkontrollblock. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_ecdh*
- **nyckel** Det här fältet används inte för ECDH.
- **key_size_in_bits** Det här fältet används inte för ECDH.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för ECDH-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För ECDH måste metadatastorleken vara *sizeof(NX_CRYPTO_ECDH)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av ECDH-kontrollblocket med nyckel- och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Utföra ECDH-åtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför ECDH-åtgärden. ECDH-kontrollblocket måste ha initierats med _ *nx_crypto_method_ecdh_init()*. ECDH-algoritmen som ska utföras baseras på algoritmen som anges i *metodkontrollblocket.*

När åtgärden har NX_CRYPTO_EC_CURVE_SET pekar indata på kryptografimetoden Elliptic Curve. När åtgärden är NX_CRYPTO_EC_KEY_PAIR_GENERATE pekar utdata på NX_CRYPTO_EXTENDED_OUTPUT struktur och nyckelparet kopieras till nx_crypto_extended_output_data. När åtgärden har NX_CRYPTO_DH_SETUP returneras den offentliga nyckeln till nx_crypto_extended_output_data. När åtgärden har NX_CRYPTO_DH_KEY_PAIR_IMPORT pekar indata på den offentliga nyckeln och nyckelpunkterna på den privata nyckeln. När åtgärden har NX_CRYPTO_DH_PRIVATE_KEY_EXPORT kopieras den privata nyckeln till nx_crypto_extended_output_data. När åtgärden har NX_CRYPTO_DH_CALCULATE kopieras indatapunkterna till den offentliga fjärrnyckeln och den delade hemligheten kopieras till nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga ECDH-kryptografimetoden. Kryptografimetoden som används här måste vara samma som används i *_nx_crypto_method_ecdh_init().*
- **nyckel** När op NX_CRYPTO_DH_IMPORT_KEY_PAIR pekar det här fältet på privat nyckel. Annars används inte det här fältet för ECDH.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **indata** När op NX_CRYPTO_EC_CURVE_SET pekar det här fältet på kryptografimetoden Elliptic Curve. När op NX_CRYPTO_DH_SETUP används inte det här fältet. När op NX_CRYPTO_DH_CALCULATE pekar det här fältet på en buffert som innehåller indatatext. När op NX_CRYPTO_DH_IMPORT_KEY_PAIR pekar det här fältet på offentlig nyckel.
- **input_length_in_byte** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för ECDH.
- **utdata** När op NX_CRYPTO_EC_CURVE_SET eller NX_CRYPTO_DH_IMPORT_KEY_PAIR används inte det här fältet. När op NX_CRYPTO_DH_SETUP pekar det här fältet på minnesområdet för den genererade offentliga ECDH-nyckeln. När op NX_CRYPTO_DH_CALCULATE pekar det här fältet på minnesområdet för den genererade delade ECDH-hemligheten.
- **output_length_in_byte** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till ECDH-kontrollblocket som används *i _nx_crypto_method_ecdh_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För ECDH måste metadatastorleken *vara sizeof(NX_CRYPTO_ECDH)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) ECDH-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig ECDH-algoritm anges.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Rensa ECDH-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa ECDH-kontrollblocket när den här ECDH-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till ECDH-kontrollblocket som används *i _nx_crypto_method_ecdh_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) ECDH-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

Initierar ECDSA-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar ECDSA-kontrollblocket med den angivna nyckelsträngen. När ECDSA-kontrollblocket har initierats ska efterföljande ECDSA-åtgärd använda samma kontrollblock.

Programmet kan skapa flera ECDSA-kontrollblock, som var och en representerar en session. Initiering av ECDSA-kontrollblocket startar en ny hash-beräkningssession. När ECDSA-kontrollblocket initieras på nytt överger den aktuella sessionen en ny session.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt ecdsa kryptografimetodkontrollblock. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_ecdsa*
- **nyckel** Det här fältet används inte för ECDSA.
- **key_size_in_bits** Det här fältet används inte för ECDSA.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för ECDSA-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För ECDSA måste metadatastorleken vara *sizeof(NX_CRYPTO_ECDSA)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av ECDSA-kontrollblocket med nyckel- och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Utföra ECDSA-åtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför ECDSA-åtgärden. ECDSA-kontrollblocket måste ha initierats med _ *nx_crypto_method_ecdsa_init()*. ECDSA-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

När åtgärden har NX_CRYPTO_EC_CURVE_SET pekar indata på kryptografimetoden Elliptic Curve. När åtgärden är NX_CRYPTO_EC_KEY_PAIR_GENERATE pekar utdata på NX_CRYPTO_EXTENDED_OUTPUT struktur och nyckelparet kopieras till nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga ECDSA-kryptografimetoden. Kryptografimetoden som används här måste vara samma som används i *_nx_crypto_method_ecdsa_init().*
- **nyckel** Pekar på nyckeln när op NX_CRYPTO_VERIFY. Det finns inga begränsningar för nyckelbufferten. Det här fältet används inte för andra op-värden.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **indata** När op NX_CRYPTO_EC_CURVE_SET pekar det här fältet på kryptografimetoden Elliptic Curve. Annars pekar det här fältet på en buffert som innehåller indatatext.
- **input_length_in_byte** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för ECDSA.
- **utdata** När op NX_CRYPTO_EC_CURVE_SET används inte det här fältet. När op NX_CRYPTO_AUTHENTICATE pekar det här fältet på minnesområdet för den genererade ECDSA-signaturen. När op NX_CRYPTO_VERIFY pekar det här fältet på minnesområdet för den verifierade ECDSA-signaturen.
- **output_length_in_byte** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till ECDSA-kontrollblocket som används *i _nx_crypto_method_ecdsa_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För ECDSA måste metadatastorleken *vara sizeof(NX_CRYPTO_ECDSA)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) ECDSA-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig ECDSA-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Rensa ECDSA-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa ECDSA-kontrollblocket när den här ECDSA-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till ECDSA-kontrollblocket som används *i _nx_crypto_method_ecdsa_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) ECDSA-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Initierar HMAC MD5-kontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar HMAC MD5-kontrollblocket med den angivna nyckelsträngen. När HMAC MD5-kontrollblocket har initierats ska efterföljande HMAC MD5-åtgärd använda samma kontrollblock.

Programmet kan skapa flera HMAC MD5-kontrollblock, som var och en representerar en session. Initiera HMAC MD5-kontrollblocket startar en ny hash-beräkningssession. Genom att initiera om HMAC MD5-kontrollblocket överger den aktuella sessionen och en ny initieras.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för HMAC MD5-kryptografimetod.
Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_hmac_md5*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för HMAC MD5-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För HMAC MD5 måste metadatastorleken vara *sizeof(NX_CRYPTO_MD5_HMAC)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av HMAC MD5-kontrollblocket med nyckel och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Utför en HMAC MD5-hashåtgärd.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför HMAC MD5-hashåtgärden. Kontrollblocket HMAC MD5 måste ha initierats med _ *nx_crypto_method_hmac_md5_init()*. HMAC MD5-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

För den sista *NX_CRYPTO_HASH_CALCULATE* måste utdatabuffertens storlek vara 16 byte.

Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckelmaterial i HMAC MD5-kontrollblocket.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga kryptografimetoden HMAC MD5. Kryptometoden som används här måste vara samma som används i *nx_crypto_method_hmac_md5_init().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **input_data** Pekar på en buffert som innehåller indata. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för HMAC MD5.
- **iv_size** Det här fältet används inte för HMAC MD5.
- **output_buffer** Pekare till minnesområdet för den genererade HMAC MD5-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till HMAC MD5-kontrollblocket som används *i _nx_crypto_method_hmac_md5_init()*.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För HMAC MD5 måste metadatastorleken *vara sizeof(NX_CRYPTO_MD5_HMAC)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC MD5-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig HMAC MD5-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Initierar kryptografikontrollblocket HMAC SHA1

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar HMAC SHA1-kontrollblocket med den angivna nyckelsträngen. När HMAC SHA1-kontrollblocket har initierats ska efterföljande HMAC SHA1-åtgärd använda samma kontrollblock.

Programmet kan skapa flera HMAC SHA1-kontrollblock, var och en representerar en session. Initiera HMAC SHA1-kontrollblocket startar en ny hash-beräkningssession. Om du initierar om HMAC SHA1-kontrollblocket överger den aktuella sessionen och spelar in en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för kryptografimetoden HMAC SHA1. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_hmac_sha1*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för HMAC SHA1-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För HMAC SHA1 måste metadatastorleken vara *sizeof(NX_CRYPTO_SHA1_HMAC)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av HMAC SHA1-kontrollblocket med nyckel- och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Utföra hashåtgärden HMAC SHA1

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför hash-åtgärden HMAC SHA1. Kontrollblocket HMAC SHA1 måste ha initierats med _ *nx_crypto_method_hmac_sha1_init()*. HMAC SHA1-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

För den sista *NX_CRYPTO_HASH_CALCULATE* måste utdatabuffertens storlek vara 20 byte.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga kryptografimetoden HMAC SHA1. Kryptometoden som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha1_init().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **input_data** Pekar på en buffert som innehåller indata. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för HMAC SHA1.
- **iv_size** Det här fältet används inte för HMAC SHA1.
- **output_buffer** Pekare till minnesområdet för den genererade HMAC SHA1-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till HMAC SHA1-kontrollblocket som används *i _nx_crypto_method_hmac_sha1_init()*.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För HMAC SHA1 måste metadatastorleken *vara sizeof(NX_CRYPTO_SHA1_HMAC)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig HMAC SHA1-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Rensa kontrollblocket HMAC SHA1.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa HMAC SHA1-kontrollblocket när den här HMAC SHA1-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till HMAC SHA1-kontrollblocket som används *i _nx_crypto_method_hmac_sha1_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Initierar HMAC SHA256-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar HMAC SHA256-kontrollblocket med den angivna nyckelsträngen. När HMAC SHA256-kontrollblocket har initierats ska efterföljande HMAC SHA256-åtgärder använda samma kontrollblock.

Programmet kan skapa flera HMAC SHA256-kontrollblock, var och en representerar en session. Initiera HMAC SH256-kontrollblocket startar en ny hash-beräkningssession. Om du initierar om HMAC SHA256-kontrollblocket överger den aktuella sessionen och spelar en ny med en ny nyckel.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt HMAC SHA256-kryptografimetodkontrollblock. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för HMAC SHA256-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För HMAC SHA256 måste metadatastorleken vara *sizeof(NX_CRYTPO_SHA256_HMAC)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av HMAC SHA256-kontrollblocket med nyckel och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Utföra HMAC SHA256-hashåtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför HMAC SHA256-hashåtgärden. HMAC SHA256-kontrollblocket måste ha initierats med _ *nx_crypto_method_hmac_sha256_init()*. HMAC SHA256-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

För den *sista NX_CRYPTO_HASH_CALCULATE* måste utdatabuffertstorleken vara 32 byte för SHA256 eller 28 byte för SHA224.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga kryptografimetoden HMAC SHA256. Kryptografimetoden som används här måste vara samma som används i *_nx_crypto_method_hmac_sha256_init().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **input_data** Pekar på en buffert som innehåller indatatext. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för HMAC SHA256.
- **iv_size** Det här fältet används inte för HMAC SHA256.
- **output_buffer** Pekare till minnesområdet för den genererade HMAC SHA256-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till HMAC SHA256-kontrollblocket som används *i _nx_crypto_method_hmac_sha256_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För HMAC SHA256 måste metadatastorleken *vara sizeof(NX_CRYPTO_SHA256_HMAC)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig HMAC SHA256-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Rensa HMAC SHA256-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa HMAC SHA256-kontrollblocket när den här HMAC SHA256-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till HMAC SHA256-kontrollblocket som används *i _nx_crypto_method_hmac_sha256_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Initierar HMAC SHA512 kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar HMAC SHA512-kontrollblocket med den angivna nyckelsträngen. När HMAC SHA512-kontrollblocket har initierats ska efterföljande HMAC SHA512-åtgärd använda samma kontrollblock.

Programmet kan skapa flera HMAC SHA512-kontrollblock, var och en representerar en session. Initiera HMAC SH512-kontrollblocket startar en ny hash-beräkningssession. Om du initierar om HMAC SHA512-kontrollblocket överger den aktuella sessionen och spelar in en ny med en ny nyckel.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för kryptografimetoden HMAC SHA512. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för HMAC SHA512-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För HMAC SHA512 måste metadatastorleken vara *sizeof(NX_CRYPTO_SHA512_HMAC)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av HMAC SHA512-kontrollblocket med nyckel- och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size, eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Utföra HMAC SHA512-hashåtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför HMAC SHA512-hashåtgärden. Kontrollblocket HMAC SHA512 måste ha initierats med _ *nx_crypto_method_hmac_sha512_init()*. HMAC SHA512-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

För den *NX_CRYPTO_HASH_CALCULATE* åtgärden måste utdatabuffertens storlek vara 64 byte för SHA512 eller 48 byte för SHA384.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga kryptografimetoden HMAC SHA512. Kryptometoden som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha512_init().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckelbufferten.
- **key_size_in_bits** Nyckelns storlek, i bitar.
- **input_data** Pekar på en buffert som innehåller indata. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för HMAC SHA512.
- **iv_size** Det här fältet används inte för HMAC SHA512.
- **output_buffer** Pekare till minnesområdet för den genererade HMAC SHA512-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte.
- **crypto_metadata** Pekare till HMAC SHA512-kontrollblocket som används *i _nx_crypto_method_hmac_sha512_init()*.
- **crypto_metadata_size** Storleken, i byte, crypto_metadata området. För HMAC SHA512 måste metadatastorleken *vara sizeof(NX_CRYPTO_SHA512_HMAC)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig HMAC SHA512-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Rensa HMAC SHA512-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa HMAC SHA512-kontrollblocket när den här HMAC SHA512-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till HMAC SHA512-kontrollblocket som används *i _nx_crypto_method_hmac_sha512_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptobiblioteket är i ett ogiltigt tillstånd och kan inte användas.

### <a name="example"></a>Exempel 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Initierar MD5-kontrollblocket för kryptografi

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar MD5-kontrollblocket med den angivna nyckelsträngen. När MD5-kontrollblocket har initierats ska efterföljande MD5-åtgärd använda samma kontrollblock.

Programmet kan skapa flera MD5-kontrollblock, var och en representerar en session. Initiera MD5-kontrollblocket startar en ny hash-beräkningssession. Om du initierar om MD5-kontrollblocket överger den aktuella sessionen och spelar in en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt kontrollblock för MD5-kryptometoden. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_md5*
- **nyckel** Det här fältet används inte för MD5.
- **key_size_in_bits** Det här fältet används inte för MD5
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för MD5-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För MD5 måste metadatastorleken vara *sizeof(NX_CRYPTO_MD5)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av MD5-kontrollblocket med nyckel och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

### <a name="example"></a>Exempel

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Utför en MD5-hashåtgärd.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför MD5-hashåtgärden. MD5-kontrollblocket måste ha initierats med _ *nx_crypto_method_md5_init()*. MD5-algoritmen som ska utföras baseras på algoritmen som anges i *metodkontrollblocket.*

För den  sista NX_CRYPTO_HASH_CALCULATE åtgärden måste utdatabuffertens storlek vara 16 byte.

Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckelmaterialet i MD5-kontrollblocket.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga MD5-kryptografimetoden. Kryptografimetoden som används här måste vara samma som används i *_nx_crypto_method_md5_init().*
- **input_data** Pekar på en buffert som innehåller indatatext. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för MD5.
- **iv_size** Det här fältet används inte för MD5.
- **output_buffer** Pekare till minnesområdet för den genererade MD5-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte. För MD5 måste buffertstorleken vara 16 byte.
- **crypto_metadata** Pekare till MD5-kontrollblocket som används *i _nx_crypto_method_md5_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För MD5 måste metadatastorleken *vara sizeof(NX_CRYPTO_MD5)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) MD5-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig MD5-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Rensa MD5-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa MD5-kontrollblocket när den här MD5-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till MD5-kontrollblocket som används *i _nx_crypto_method_md5_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) MD5-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

Initierar SHA1-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar SHA1-kontrollblocket med den angivna nyckelsträngen. När SHA1-kontrollblocket har initierats ska efterföljande SHA1-åtgärd använda samma kontrollblock.

Programmet kan skapa flera SHA1-kontrollblock, var och en representerar en session. Initiera SHA1-kontrollblocket startar en ny hash-beräkningssession. När sha1-kontrollblocket initieras på nytt överger den aktuella sessionen och en ny initieras.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt SHA1-kontrollblock för kryptografimetod. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_sha1*
- **nyckel** Det här fältet används inte för SHA1.
- **key_size_in_bits** Det här fältet används inte för SHA1
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för SHA1-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För SHA1 måste metadatastorleken vara *sizeof(NX_CRYPTO_SHA1)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av SHA1-kontrollblocket med nyckel- och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Utföra SHA1-hashåtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför SHA1-hashåtgärden. SHA1-kontrollblocket måste ha initierats med _ *nx_crypto_method_sha1_init()*. SHA1-algoritmen som ska utföras baseras på algoritmen som anges i *metodkontrollblocket.*

För den sista *NX_CRYPTO_HASH_CALCULATE* måste utdatabuffertens storlek vara 20 byte.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekar på den giltiga SHA1-kryptografimetoden. Kryptografimetoden som används här måste vara samma som används i *nx_crypto_method_sha1_init().*
- **input_data** Pekar på en buffert som innehåller indatatext. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för SHA1.
- **iv_size** Det här fältet används inte för SHA1.
- **output_buffer** Pekare till minnesområdet för den genererade SHA1-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte. För SHA1 måste buffertstorleken vara 20 byte.
- **crypto_metadata** Pekare till SHA1-kontrollblocket som används *i _nx_crypto_method_sha1_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För SHA1 måste metadatastorleken *vara sizeof(NX_CRYPTO_SHA1)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) SHA1-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig SHA1-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

### <a name="example"></a>Exempel

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Rensa SHA1-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa SHA1-kontrollblocket när den här SHA1-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till SHA1-kontrollblocket som används *i _nx_crypto_method_sha1_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) SHA1-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Initierar SHA256-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>Description

Den här funktionen initierar SHA256-kontrollblocket med den angivna nyckelsträngen. När SHA256-kontrollblocket har initierats ska efterföljande SHA256-åtgärd använda samma kontrollblock.

Programmet kan skapa flera SHA256-kontrollblock, var och en representerar en session. När sha256-kontrollblocket initieras startas en ny hash-beräkningssession. När sha256-kontrollblocket initieras på nytt överger den aktuella sessionen och en ny initieras.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt SHA256 crypto-metodkontrollblock. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **nyckel** Det här fältet används inte för SHA256.
- **key_size_in_bits** Det här fältet används inte för SHA256
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för SHA256-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För SHA256 måste metadatastorleken vara *sizeof(NX_CRYPTO_SHA256)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av SHA256-kontrollblocket med nyckel och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Utföra SHA256-hashåtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a>Description

Den här funktionen utför SHA256-hashåtgärden. SHA256-kontrollblocket måste ha initierats med _ ***nx_crypto_method_sha256_init()***. SHA256-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

För den *sista NX_CRYPTO_HASH_CALCULATE* måste utdatabuffertstorleken vara 32 byte för SHA256 eller 28 byte för SHA224.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga SHA256-kryptografimetoden. Kryptografimetoden som används här måste vara samma som används i _ *nx_crypto_method_sha256_init().*
- **input_data** Pekar på en buffert som innehåller indatatext. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för SHA256.
- **iv_size** Det här fältet används inte för SHA256.
- **output_buffer** Pekare till minnesområdet för den genererade SHA256-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte. För SHA256 måste buffertstorleken vara 32 byte. För SHA224 måste buffertstorleken vara 28 byte.
- **crypto_metadata** Pekare till SHA2-kontrollblocket som används *i _nx_crypto_method_sha2_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För SHA256 måste metadatastorleken *vara sizeof(NX_CRYPTO_SHA256)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) SHA256-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig SHA256-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Rensa SHA256-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa SHA256-kontrollblocket när den här SHA256-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till SHA256-kontrollblocket som används *i _nx_crypto_method_sha256_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) SHA256-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

Initierar SHA512-kryptografikontrollblocket

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Description

Den här funktionen initierar SHA512-kontrollblocket med den angivna nyckelsträngen. När SHA512-kontrollblocket har initierats ska efterföljande SHA512-åtgärder använda samma kontrollblock.

Programmet kan skapa flera SHA512-kontrollblock, var och en representerar en session. När du initierar SHA512-kontrollblocket startas en ny hash-beräkningssession. När sha512-kontrollblocket initieras om överger den aktuella sessionen och en ny initieras.

### <a name="parameters"></a>Parametrar

- **metod** Pekare till ett giltigt SHA512 crypto-metodkontrollblock. Följande fördefinierade kryptografimetoder är tillgängliga:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **nyckel** Det här fältet används inte för SHA512.
- **key_size_in_bits** Det här fältet används inte för SHA512
- **handle** Den här tjänsten returnerar en referens till anroparen. Referensen är implementeringsberoende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekare till ett giltigt minnesutrymme för SHA512-kontrollblocket. Startadressen för minnesutrymmet måste vara justerad med 4 byte.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För SHA512 måste metadatastorleken vara *sizeof(NX_CRYPTO_SHA512)*

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) Lyckad initiering av SHA512-kontrollblocket med nyckel och nyckelstorlek.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig pekare till nyckeln, ogiltig crypto_metadata eller crypto_metadata_size eller crypto_metadata är inte justerad med 4 byte.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Utföra SHA512-hashåtgärd

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a>Description

Den här funktionen utför SHA512-hashåtgärden. SHA512-kontrollblocket måste ha initierats med _ *nx_crypto_method_sha512_init()*. SHA512-algoritmen som ska utföras baseras på den algoritm som anges i *metodkontrollblocket.*

För den *sista NX_CRYPTO_HASH_CALCULATE åtgärden* måste utdatabuffertstorleken vara 64 byte för SHA512 eller 48 byte för SHA384.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **handle** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga SHA512-kryptografimetoden. Kryptografimetoden som används här måste vara samma som används i _ *nx_crypto_method_sha512_init().*
- **input_data** Pekar på en buffert som innehåller indatatext. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storleken på indata i byte.
- **iv_ptr** Det här fältet används inte för SHA512.
- **iv_size** Det här fältet används inte för SHA512.
- **output_buffer** Pekare till minnesområdet för den genererade SHA512-hashen.
- **output_buffer_size** Storleken på utdatabufferten i byte. För SHA512 måste buffertstorleken vara 64 byte. För SHA384 måste buffertstorleken vara 48 byte.
- **crypto_metadata** Pekare till SHA512-kontrollblocket som används *i _nx_crypto_method_sha512_init()*.
- **crypto_metadata_size** Storlek, i byte, crypto_metadata området. För SHA512 måste metadatastorleken *vara sizeof(NX_CRYPTO_SHA512)*
- **packet_ptr** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i programvaruimplementering av NetX Crypto-biblioteket. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) SHA512-åtgärden har körts.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0x07) Ogiltig indatapekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Ogiltig SHA512-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Ogiltig utdatabuffertstorlek.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Rensa SHA512-kontrollblocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Description

Programmet anropar den här funktionen för att rensa SHA512-kontrollblocket när den här SHA512-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till SHA512-kontrollblocket som används *i _nx_crypto_method_sha512_init()*.

### <a name="return-values"></a>Returvärden

- **NX_CRYPTO_SUCCESS** (0x00) SHA512-sessionen har rensats.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Kryptografibiblioteket är i ett ogiltigt tillstånd och kan inte användas.