---
title: Kapitel 4 – Beskrivning av Azure återställnings tider NetX krypto API
description: Beskrivning av Azure återställnings tider NetX-kryptografi-API
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826811"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Kapitel 4 – Beskrivning av Azure återställnings tider NetX krypto API

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Initierar NetX säkra bibliotek

### <a name="prototype"></a>Prototyp

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Beskrivning

Den här funktionen initierar modulen Azure återställnings tider NetX krypto-bibliotek. Innan du använder någon av de andra krypterings funktionerna måste programmet anropa den här funktionen för att utföra initiering och för att verifiera bibliotekets integritet. Om du inte anropar den här funktionen innan du använder andra NetX-krypto-tjänster leder det till att fel returneras.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) initiering av netx-kryptografi bibliotek lyckades. Biblioteks funktionerna är nu klara och kan användas.
- **NX_CRYPTO_INVALID_LIBRARY** (0X20001) Det gick inte att initiera kryptografi biblioteket eller också går det inte att utföra integritets kontrollen. Programmet kan inte använda det här biblioteket.

### <a name="example"></a>Exempel

ATT göra

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Hämta aktuell status för den FIPS-aktiverade modulen

### <a name="prototype"></a>Prototyp

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Beskrivning

Den här tjänsten är bara tillgänglig i FIPS build-biblioteket. Den returnerar statusen för det aktuella läget för NetX-krypto-biblioteket.

### <a name="parameters"></a>Parametrar

- **Ingen**

### <a name="return-values"></a>Retur värden

- **Status flagga:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **Alla andra värden är ogiltiga.**

### <a name="example"></a>Exempel

ATT göra

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Initierar kontroll block för AES-kryptografi

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar AES-kontroll-blocket med den aktuella nyckel strängen. När AES-Kontrollpanelen har initierats använder den efterföljande AES-åtgärden samma nyckel och nyckel storlek.

Programmet kan skapa flera AES-kontroll block, som representerar en session. En nyckel tilldelas ett kontroll block. Efterföljande krypterings-eller krypterings åtgärder kan referera till samma AES-kontroll block utan att behöva initiera AES-kontroll blocket igen. Om nyckeln för sessionen har ändrats måste programmet initiera om AES-kontrolls-blocket med den uppdaterade nyckeln.

Anrop _ *nx_crypto_method_aes_init ()* uppdaterar automatiskt en tidigare konfigurerad nyckel och nyckel storlek till den nya nyckeln.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för AES-krypto. Följande fördefinierade AES-krypterings metoder är tillgängliga:
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **nyckel** Pekar på en buffert som innehåller AES-nyckeln
- **key_size_in_bits** Nyckelns storlek i bitar. Giltiga värden är:
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **Alla andra värden är ogiltiga.**
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för AES-kontroll-blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För AES måste metadatans storlek vara *sizeof (NX_AES)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera AES-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size eller så är crypto_metadata inte 4 byte-justerad.
- Nyckel storleken för **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) är inte giltig för AES.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

Utföra en AES-åtgärd (kryptering eller dekryptering).

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

### <a name="description"></a>Beskrivning

Den här funktionen utför AES-kryptering eller dekrypteringsåtgärder. AES-kontroll blocket måste ha initierats med _ *nx_crypto_method_aes_init ()*. AES-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

Den angivna buffertstorleken måste vara en multipel av 16 byte. Storleken på dekrypterade data är samma storlek som storleken på indata. Om krypterade data har fyllts ut för att uppnå en jämnt multipel av AES-blocket, kommer utfyllnaden att inkluderas i utdatabufferten och måste hanteras av programmet.

Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckel materialet i AES-kontroll blocket.

När op är NX_CRYPTO_SET_ADDITIONAL_DATA och algoritm är AES-CCM8 är indata punkter till ytterligare data och input_length_in_byte längden på ytterligare data.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltiga kundgrupper är:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (endast AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (endast AES-CCM8)*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till giltig AES-kryptografi metod. Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_aes_init ().*
- **input_data** Pekar på en buffert som innehåller krypterade text data. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte. Storleken på indata måste vara en multipel av 16 byte.
- **iv_ptr** Pekar mot den inledande vektorn. Det finns inga begränsningar för IV-bufferten.
- **iv_size** Storlek på det inledande vektor blocket, i byte det här fältet måste vara 16.
- **output_buffer** Pekar på minnes området för AES för att lagra klartext-data. Programmet måste allokera utrymme för utdatabufferten. Utdatabufferten kan överlappa med indatabufferten. Utdatabufferten kan överlappa med indatabufferten om de delar samma start adress.
- **output_buffer_size** Storlek på utdatabufferten i byte. Storleken på utdatabufferten måste vara minst samma som storleken på indatabufferten och utdatabufferten måste vara en multipel av 16 byte.
- **crypto_metadata** Pekar på det AES-kontroll block som används i *_nx_crypto_method_aes_init () \* . \**
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För AES måste metadatans storlek *sizeof (NX_AES)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** – det här fältet används inte i program implementeringen för netx-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde AES-åtgärden.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig AES-algoritm har angetts * *.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Rensa AES-kontroll blocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa AES-kontroll blocket när den har bedömt att den här AES-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekar på det AES-kontroll block som används i *_nx_crypto_method_aes_init () \* . \**

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat AES-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Initiera 3DES-kontroll blocket.

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar kontroll blocket Triple DES (3DES) med de tre nyckel strängarna. Nyckel strängarna måste vara 8 byte. De tre DES-nycklarna måste sammanfogas i sammanhängande minne med 24 byte-buffert. För FIPS-kompatibla build-versioner måste de tre nycklarna vara olika från var och en av funktionerna, annars returneras NX_CRYPTO_INVALID_KEY fel. När 3DES-kontroll blocket initieras använder efterföljande 3DES-åtgärder samma nycklar.

Ett program kan skapa flera 3DES-kontroll block som representerar en session. En nyckel tilldelas ett kontroll block och efterföljande krypterings-eller dekrypterings åtgärder kan referera till samma kontroll block utan att behöva initieras på nytt. Om nyckeln för en session ändras måste programmet initiera kontroll blocket igen med den uppdaterade nyckeln.

Anrop _ *nx_crypto_method_3des_init ()* uppdaterar automatiskt en tidigare konfigurerad nyckel till de nya nycklarna.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för 3DES-kryptografisk metod. Följande fördefinierade metod för 3DES-kryptering är tillgänglig: ***crypto_method_3des***
- **nyckel** Pekar på en buffert som innehåller den tre (3) DES-nyckeln
- **key_size_in_bits** Måste vara 192 (3 nycklar, varje 64 bitar).
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen identifierar det 3DES-kontroll block som initieras. Efterföljande 3DES-åtgärder (kryptering, dekryptering och rensning) använder den här referensen för att få åtkomst till 3DES-kontroll blocket
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för 3DES-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För 3DES måste storleken på metadata vara *sizeof (NX_3DES)*

### <a name="return-value"></a>Returvärde

- **NX_CRYPTO_SUCCESS** (0X00) slutförde initieringen av 3DES-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size eller så är crypto_metadata inte 4 byte-justerad.
- Nyckel storleken för **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) är inte giltig för 3DES.

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

### <a name="description"></a>Beskrivning

Den här funktionen utför 3DES-kryptering eller dekrypteringsåtgärder. 3DES-kontroll blocket måste ha initierats med _ *nx_crypto_method_3des_init ()*. 3DES-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

Den angivna buffertstorleken måste vara en multipel av 8 byte. Storleken på dekrypterade data är samma storlek som storleken på indata. Om krypterade data har fyllts ut för att uppnå en jämn multipel av 3DES-blocket, inkluderas utfyllnaden i utdatabufferten och måste hanteras av programmet.

Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckel materialet i 3DES-kontroll blocket.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. Giltiga åtgärder är:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **Hantera** Referensen initierades av *_nx_crypto_method_3des_init ()*.
- **metod** Pekar på giltig 3DES-kryptografi metod. Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_3des_init ().*
- **input_data** Pekar på en buffert som innehåller krypterade text data.
Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte. Storleken på indata måste vara en multipel av 8 byte.
- **iv_ptr** Pekar mot den inledande vektorn. Det finns inga begränsningar för IV-bufferten.
- **iv_size** Storleken på det inledande vektor blocket, i byte det här fältet måste vara 8.
- **output_buffer** Pekar på minnes området för 3DES för att lagra rensade text data. Programmet måste allokera utrymme för utdatabufferten. Utdatabufferten kan överlappa med indatabufferten. Utdatabufferten kan överlappa med indatabufferten om de delar samma start adress.
- **output_buffer_size** Storlek på utdatabufferten i byte. Storleken på utdatabufferten måste vara minst samma som storleken på indatabufferten och utdatabufferten måste vara en multipel av 8 byte.
- **crypto_metadata** Pekare till det 3DES-kontroll block som används i *_nx_crypto_method_3des_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För 3DES måste storleken på metadata vara *sizeof (NX_3DES)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="description"></a>Beskrivning

Den här funktionen utför 3DES-kryptering. 3DES-kontroll blocket måste ha initierats med _ *nx_crypto_moethod_3des_init ()*. Den här åtgärden behåller inte tillståndsinformation och ändrar inte nyckel materialet i 3DES-kontroll blocket. Observera att utfyllnad inte läggs till av den här funktionen, så att anroparen måste hantera utfyllnad innan du anropar krypterings åtgärden.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) slutförde initieringen av 3DES-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR (0x07)** Ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Rensa 3DES-kontroll blocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa 3DES-kontroll blocket efter att den här 3DES-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **Hantera** Referensen initierades av *_nx_crypto_method_3des_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) rensade 3DES-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

Initierar kontroll block för DRBG-kryptografi

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar kontroll blocket DRBG med den aktuella nyckel strängen. När DRBG-kontroll blocket initieras, ska efterföljande DRBG-åtgärd använda samma kontroll block.

Programmet kan skapa flera DRBG-kontroll block, som var och en representerar en session. Initieringen av DRBG Control Block startar en ny session med hash-beräkning. Ominitieringen av kontroll blocket DRBG överger den aktuella sessionen och använder stjärnorna som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för DRBG-kryptografiska metoder. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_drbg*
- **nyckel** Det här fältet används inte för DRBG.
- **key_size_in_bits** Det här fältet används inte för DRBG.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för DRBG-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För DRBG måste storleken på metadata vara *sizeof (NX_CRYPTO_DRBG)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera DRBG-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Utför DRBG-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför DRBG-åtgärden. Kontroll blocket DRBG måste ha initierats med _ *nx_crypto_method_drbg_init ()*. DRBG-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket. Som standard används AES-128 för DRBG.

När åtgärden NX_CRYPTO_DRBG_OPTIONS_SETs pekar ingångarna till NX_CRYPTO_DRBG_OPTIONS-strukturen. När åtgärden är NX_CRYPTO_DRBG_INSTANTIATE, kommer nyckeln till nonce, ingångs punkter till anpassnings strängen. När åtgärden är NX_CRYPTO_DRBG_RESEED eller NX_CRYPTO_DRBG_GENERATE, så pekar ingångarna till ytterligare indatatyper.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga DRBG-kryptografi metoden. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_drbg_init ().*
- **nyckel** Pekar till nonce för initierings åtgärden. Det här fältet används inte för andra åtgärder.
- **key_size_in_bits** Storleken på nonce i bitar. Det här fältet används inte för andra åtgärder.
- **mata in** När op är NX_CRYPTO_DRBG_OPTIONS_SET pekar det här fältet på DRBG-alternativ. När op är NX_CRYPTO_DRBG_INSTANTIATE pekar detta fält på anpassnings sträng. När op är NX_CRYPTO_DRBG_RESEED eller NX_CRYPTO_DRBG_GENERATE, pekar det här fältet på ytterligare indata.
- **input_length_in_byte** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för DRBG.
- **utdata** När op är NX_CRYPTO_DRBG_GENERATE, pekar det här fältet på minnes området för den genererade DRBG. Annars används inte det här fältet.
- **output_length_in_byte** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekare till DRBG-kontroll blocket som används i *_nx_crypto_method_drbg_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För DRBG måste metadata *-storleken sizeof (NX_CRYPTO_DRBG)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig DRBG-algoritm anges.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Rensa kontroll blocket DRBG.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa DRBG-kontroll blocket när den har bedömt att den här DRBG-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till DRBG-kontroll blocket som används i *_nx_crypto_method_drbg_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat DRBG-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

Initierar kontroll block för ECDH-kryptografi

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar kontroll blocket ECDH med den aktuella nyckel strängen. När ECDH-kontroll blocket initieras, ska efterföljande ECDH-åtgärd använda samma kontroll block.

Programmet kan skapa flera ECDH-kontroll block, som var och en representerar en session. Initieringen av ECDH Control Block startar en ny session med hash-beräkning. Ominitieringen av kontroll blocket ECDH överger den aktuella sessionen och använder stjärnorna som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för ECDH-kryptografiska metoder. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_ecdh*
- **nyckel** Det här fältet används inte för ECDH.
- **key_size_in_bits** Det här fältet används inte för ECDH.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för ECDH-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För ECDH måste storleken på metadata vara *sizeof (NX_CRYPTO_ECDH)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera ECDH-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Utför ECDH-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför ECDH-åtgärden. Kontroll blocket ECDH måste ha initierats med _ *nx_crypto_method_ecdh_init ()*. ECDH-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

När åtgärden NX_CRYPTO_EC_CURVE_SETs, pekar ingångarna på Elliptic Curve-krypterings metod. När åtgärden är NX_CRYPTO_EC_KEY_PAIR_GENERATE kopieras utdata till NX_CRYPTO_EXTENDED_OUTPUT-strukturen och nyckel paret kopieras till nx_crypto_extended_output_data. När åtgärden NX_CRYPTO_DH_SETUP returneras den offentliga nyckeln till nx_crypto_extended_output_data. När åtgärden NX_CRYPTO_DH_KEY_PAIR_IMPORTs pekar ingångarna på offentlig nyckel och nyckel punkter till privat nyckel. När åtgärden NX_CRYPTO_DH_PRIVATE_KEY_EXPORT kopieras den privata nyckeln till nx_crypto_extended_output_data. När åtgärden är NX_CRYPTO_DH_CALCULATE kopieras ingångs punkterna till den offentliga fjärrnyckeln och den delade hemligheten till nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga ECDH-kryptografi metoden. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_ecdh_init ().*
- **nyckel** När op är NX_CRYPTO_DH_IMPORT_KEY_PAIR pekar detta fält på privat nyckel. Annars används inte det här fältet för ECDH.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **mata in** När op är NX_CRYPTO_EC_CURVE_SET pekar detta fält på kryptografi metoden för Elliptic-kurvan. När op är NX_CRYPTO_DH_SETUP används inte det här fältet. När op är NX_CRYPTO_DH_CALCULATE pekar det här fältet på en buffert som innehåller indata för text. När op är NX_CRYPTO_DH_IMPORT_KEY_PAIR, pekar detta fält på offentlig nyckel.
- **input_length_in_byte** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för ECDH.
- **utdata** När op är NX_CRYPTO_EC_CURVE_SET eller NX_CRYPTO_DH_IMPORT_KEY_PAIR används inte det här fältet. När op är NX_CRYPTO_DH_SETUP pekar det här fältet på minnes området för den genererade offentliga nyckeln ECDH. När op är NX_CRYPTO_DH_CALCULATE, pekar det här fältet på minnes området för den genererade ECDH delade hemligheten.
- **output_length_in_byte** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekare till ECDH-kontroll blocket som används i *_nx_crypto_method_ecdh_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För ECDH måste metadata *-storleken sizeof (NX_CRYPTO_ECDH)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig ECDH-algoritm anges.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Rensa kontroll blocket ECDH.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa ECDH-kontroll blocket när den har bedömt att den här ECDH-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till ECDH-kontroll blocket som används i *_nx_crypto_method_ecdh_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat ECDH-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

Initierar kontroll block för ECDSA-kryptografi

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar kontroll blocket ECDSA med den aktuella nyckel strängen. När ECDSA-kontroll blocket initieras, ska efterföljande ECDSA-åtgärd använda samma kontroll block.

Programmet kan skapa flera ECDSA-kontroll block, som var och en representerar en session. Initieringen av ECDSA Control Block startar en ny session med hash-beräkning. Ominitieringen av kontroll blocket ECDSA överger den aktuella sessionen och använder stjärnorna som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för ECDSA-kryptografiska metoder. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_ecdsa*
- **nyckel** Det här fältet används inte för ECDSA.
- **key_size_in_bits** Det här fältet används inte för ECDSA.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för ECDSA-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För ECDSA måste storleken på metadata vara *sizeof (NX_CRYPTO_ECDSA)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera ECDSA-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Utför ECDSA-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför ECDSA-åtgärden. Kontroll blocket ECDSA måste ha initierats med _ *nx_crypto_method_ecdsa_init ()*. ECDSA-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

När åtgärden NX_CRYPTO_EC_CURVE_SETs, pekar ingångarna på Elliptic Curve-krypterings metod. När åtgärden är NX_CRYPTO_EC_KEY_PAIR_GENERATE kopieras utdata till NX_CRYPTO_EXTENDED_OUTPUT-strukturen och nyckel paret kopieras till nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga ECDSA-kryptografi metoden. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_ecdsa_init ().*
- **nyckel** Pekar på nyckeln när op är NX_CRYPTO_VERIFY. Det finns inga begränsningar för nyckel-buffert. Det här fältet används inte för andra värden på op.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **mata in** När op är NX_CRYPTO_EC_CURVE_SET pekar detta fält på kryptografi metoden för Elliptic-kurvan. Annars pekar det här fältet på en buffert som innehåller indata för text.
- **input_length_in_byte** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för ECDSA.
- **utdata** När op är NX_CRYPTO_EC_CURVE_SET används inte det här fältet. När op är NX_CRYPTO_AUTHENTICATE, pekar det här fältet på minnes området för den genererade ECDSA-signaturen. När op är NX_CRYPTO_VERIFY, pekar det här fältet på minnes området för den verifierade ECDSA-signaturen.
- **output_length_in_byte** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekare till ECDSA-kontroll blocket som används i *_nx_crypto_method_ecdsa_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För ECDSA måste metadata *-storleken sizeof (NX_CRYPTO_ECDSA)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig ECDSA-algoritm anges.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Rensa kontroll blocket ECDSA.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa ECDSA-kontroll blocket när den har bedömt att den här ECDSA-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till ECDSA-kontroll blocket som används i *_nx_crypto_method_ecdsa_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat ECDSA-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Initierar kryptografi kontroll block för HMAC MD5

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

### <a name="description"></a>Beskrivning

Med den här funktionen initieras det HMAC MD5-kontroll blocket med den aktuella nyckel strängen. När HMAC MD5-kontroll blocket initieras, ska efterföljande HMAC MD5-åtgärd använda samma kontroll block.

Programmet kan skapa flera HMAC MD5-kontroll block, som representerar en session. Initiering av HMAC MD5-kontroll block startar en ny hash-beräknings session. Ominitieringen av HMAC MD5 Control Block överger den aktuella sessionen och använder stjärnor som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på en giltig kontroll block för HMAC MD5-kryptografi metoden.
Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_hmac_md5*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för det HMAC MD5-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För HMAC-MD5 måste storleken på metadata vara *sizeof (NX_CRYPTO_MD5_HMAC)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initieras av HMAC MD5-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Utför en HMAC MD5-hash-åtgärd.

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

### <a name="description"></a>Beskrivning

Den här funktionen utför HMAC MD5-hash-åtgärd. Kontroll blocket HMAC MD5 måste ha initierats med _ *nx_crypto_method_hmac_md5_init ()*. Den HMAC MD5-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 16 byte.

Den här åtgärden bevarar inte tillståndsinformation och ändrar inte nyckel materialet i HMAC MD5-kontroll blocket.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekar mot giltig krypterings metod för HMAC MD5. Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_hmac_md5_init ().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för HMAC MD5.
- **iv_size** Det här fältet används inte för HMAC MD5.
- **output_buffer** Pekar till minnes området för den genererade HMAC MD5-hashen.
- **output_buffer_size** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekar på det HMAC MD5-kontroll block som används i *_nx_crypto_method_hmac_md5_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För HMAC-MD5 måste storleken på *sizeof (NX_CRYPTO_MD5_HMAC)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde den HMAC MD5-åtgärden.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC MD5-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Initierar krypterings block för HMAC SHA1-kryptering

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar det HMAC SHA1-kontroll blocket med den aktuella nyckel strängen. När HMAC SHA1-kontroll block initieras, ska efterföljande HMAC SHA1-åtgärd använda samma kontroll block.

Programmet kan skapa flera HMAC-Control Block, som representerar en session. Initiering av HMAC SHA1-kontroll block startar en ny hash-beräknings session. Ominitieringen av HMAC SHA1 Control Block överger den aktuella sessionen och använder stjärnor som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på en giltig kontroll block för HMAC SHA1-kryptografisk metod. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_hmac_sha1*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för det HMAC SHA1-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. Metadata-storleken måste vara *sizeof (NX_CRYPTO_SHA1_HMAC)* för HMAC-SHA1.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) slutförde initieringen av HMAC SHA1control-blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Utför HMAC SHA1-hash-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför HMAC SHA1-hash-åtgärd. Kontroll blocket för HMAC SHA1 måste ha initierats med _ *nx_crypto_method_hmac_sha1_init ()*. Den HMAC SHA1-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 20 byte.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekar mot giltig krypterings metod för HMAC SHA1. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha1_init ().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för HMAC-SHA1.
- **iv_size** Det här fältet används inte för HMAC-SHA1.
- **output_buffer** Pekar till minnes området för den genererade HMAC SHA1-hashen.
- **output_buffer_size** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekar på HMAC SHA1-kontroll block som används i *_nx_crypto_method_hmac_sha1_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. Metadata-storleken för HMAC-SHA1 måste *sizeof (NX_CRYPTO_SHA1_HMAC)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde HMAC-SHA1-åtgärden.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC SHA1-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Rensa blockeringen av HMAC SHA1-kontroll.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa HMAC SHA1-kontroll blocket efter det att den anger att denna HMAC SHA1-session inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekar på HMAC SHA1-kontroll block som används i *_nx_crypto_method_hmac_sha1_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) rensade HMAC-SHA1-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Initierar SHA256 för kryptografisk kontroll av HMAC

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

### <a name="description"></a>Beskrivning

Med den här funktionen initieras kontroll blocket för HMAC-SHA256 med den aktuella nyckel strängen. När HMAC-SHA256 kontroll block initieras, ska efterföljande HMAC SHA256-åtgärd använda samma kontroll block.

Programmet kan skapa flera SHA256 för HMAC-kontroll, som representerar en session. Initierande av HMAC-SH256 kontroll block startar en ny hash-beräknings session. Ominitieringen av kontroll blocket för HMAC-SHA256 överger den aktuella sessionen och stjärnor en ny med en ny nyckel.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på en giltig kontroll block för HMAC SHA256-kryptografisk metod. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för kontroll blocket för HMAC-SHA256. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För HMAC-SHA256 måste storleken på metadata vara *sizeof (NX_CRYTPO_SHA256_HMAC)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initieras av HMAC-SHA256 kontroll block med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Utför hash-åtgärd för HMAC-SHA256

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

### <a name="description"></a>Beskrivning

Den här funktionen utför hash-åtgärden för HMAC-SHA256. Kontroll blocket för HMAC-SHA256 måste ha initierats med _ *nx_crypto_method_hmac_sha256_init ()*. Den HMAC SHA256-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 32 byte för SHA256, eller 28 byte för SHA224.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekar mot den giltiga kryptografi metoden för HMAC-SHA256. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha256_init ().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för HMAC-SHA256.
- **iv_size** Det här fältet används inte för HMAC-SHA256.
- **output_buffer** Pekar till minnes området för den genererade HMAC-SHA256 hash.
- **output_buffer_size** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekar på det HMAC-SHA256 kontroll block som används i *_nx_crypto_method_hmac_sha256_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För HMAC-SHA256 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA256_HMAC)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde åtgärden HMAC-SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC-SHA256-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Rensa bort HMAC-SHA256 kontroll block.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa HMAC-SHA256 kontroll block efter det att den anger att denna HMAC SHA256-session inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekar på det HMAC-SHA256 kontroll block som används i *_nx_crypto_method_hmac_sha256_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) rensade HMAC-SHA256-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Initierar SHA512 för kryptografisk kontroll av HMAC

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

### <a name="description"></a>Beskrivning

Med den här funktionen initieras kontroll blocket för HMAC-SHA512 med den aktuella nyckel strängen. När HMAC-SHA512 kontroll block initieras, ska efterföljande HMAC SHA512-åtgärd använda samma kontroll block.

Programmet kan skapa flera SHA512 för HMAC-kontroll, som representerar en session. Initierande av HMAC-SH512 kontroll block startar en ny hash-beräknings session. Ominitieringen av kontroll blocket för HMAC-SHA512 överger den aktuella sessionen och stjärnor en ny med en ny nyckel.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på en giltig kontroll block för HMAC SHA512-kryptografisk metod. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för kontroll blocket för HMAC-SHA512. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För HMAC-SHA512 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA512_HMAC)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initieras av HMAC-SHA512 kontroll block med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Utför hash-åtgärd för HMAC-SHA512

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

### <a name="description"></a>Beskrivning

Den här funktionen utför hash-åtgärden för HMAC-SHA512. Kontroll blocket för HMAC-SHA512 måste ha initierats med _ *nx_crypto_method_hmac_sha512_init ()*. Den HMAC SHA512-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 64 byte för SHA512, eller 48 byte för SHA384.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekar mot den giltiga kryptografi metoden för HMAC-SHA512. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_hmac_sha512_init ().*
- **nyckel** Pekar på nyckeln. Det finns inga begränsningar för nyckel-buffert.
- **key_size_in_bits** Nyckelns storlek i bitar.
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för HMAC-SHA512.
- **iv_size** Det här fältet används inte för HMAC-SHA512.
- **output_buffer** Pekar till minnes området för den genererade HMAC-SHA512 hash.
- **output_buffer_size** Storlek på utdatabufferten i byte.
- **crypto_metadata** Pekar på det HMAC-SHA512 kontroll block som används i *_nx_crypto_method_hmac_sha512_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För HMAC-SHA512 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA512_HMAC)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde åtgärden HMAC-SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig HMAC-SHA512-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Rensa bort HMAC-SHA512 kontroll block.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa HMAC-SHA512 kontroll block efter det att den anger att denna HMAC SHA512-session inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekar på det HMAC-SHA512 kontroll block som används i *_nx_crypto_method_hmac_sha512_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) rensade HMAC-SHA512-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

### <a name="example"></a>Exempel 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Initierar MD5-kontroll blocket

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar MD5-kontroll blocket med den aktuella nyckel strängen. När MD5-kontroll blocket initieras, använder den efterföljande MD5-åtgärden samma kontroll block.

Programmet kan skapa flera MD5-kontroll block, som representerar en session. Initiering av MD5 Control Block startar en ny session för hash-beräkning. Ominitieringen av MD5 Control Block överger den aktuella sessionen och stjärnor med en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på en giltig MD5-metod för kryptering av kryptografiska metoder. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_md5*
- **nyckel** Det här fältet används inte för MD5.
- **key_size_in_bits** Det här fältet används inte för MD5
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för MD5-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För MD5 måste metadatans storlek vara *sizeof (NX_CRYPTO_MD5)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera MD5-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

### <a name="example"></a>Exempel

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Utföra en MD5-hash-åtgärd.

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

### <a name="description"></a>Beskrivning

Den här funktionen utför MD5-hash-åtgärd. MD5-kontroll blocket måste ha initierats med _ *nx_crypto_method_md5_init ()*. MD5-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 16 byte.

Den här åtgärden bevarar inte tillståndsinformation och ändrar inte nyckel materialet i MD5-kontroll blocket.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga MD5-kryptografi metoden. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_md5_init ().*
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för MD5.
- **iv_size** Det här fältet används inte för MD5.
- **output_buffer** Pekar till minnes området för den genererade MD5-hashen.
- **output_buffer_size** Storlek på utdatabufferten i byte. För MD5 måste buffertstorleken vara 16 byte.
- **crypto_metadata** Pekar på MD5-kontroll block som används i *_nx_crypto_method_md5_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För MD5 måste metadatans storlek *sizeof (NX_CRYPTO_MD5)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde MD5-åtgärden.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- En ogiltig MD5-algoritm har angetts för **NX_CRYPTO_INVALID_ALGORITHM** (0x20004).
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Rensa MD5-kontroll blocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa MD5-kontroll blocket när den anger att den här MD5-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekar på MD5-kontroll block som används i *_nx_crypto_method_md5_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) rensade MD5-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

Initierar kontroll block för SHA1-krypto

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar SHA1-kontrolls blocket med den aktuella nyckel strängen. När SHA1-Control-blocket initieras, ska den efterföljande SHA1-åtgärden använda samma kontroll block.

Programmet kan skapa flera SHA1-kontroll block, som var och en representerar en session. Initiering av SHA1 Control Block startar en ny session för hash-beräkning. Om du initierar om SHA1 Control Block överges den aktuella sessionen och stjärnoren är en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar mot en giltig SHA1-kontroll block för krypterings metod. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_sha1*
- **nyckel** Det här fältet används inte för SHA1.
- **key_size_in_bits** Det här fältet används inte för SHA1
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för SHA1-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För SHA1 måste metadatans storlek vara *sizeof (NX_CRYPTO_SHA1)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera SHA1control-blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Utför SHA1-hash-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför SHA1-hash-åtgärd. SHA1-kontroll blocket måste ha initierats med _ *nx_crypto_method_sha1_init ()*. Den SHA1-algoritm som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutgiltiga *NX_CRYPTO_HASH_CALCULATE* -åtgärden måste storleken på utdatabufferten vara 20 byte.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till giltig SHA1-kryptografisk metod. Den krypterings metod som används här måste vara samma som används i *nx_crypto_method_sha1_init ().*
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för SHA1.
- **iv_size** Det här fältet används inte för SHA1.
- **output_buffer** Pekar till minnes området för den genererade SHA1-hashen.
- **output_buffer_size** Storlek på utdatabufferten i byte. Buffertstorleken måste vara 20 byte för SHA1.
- **crypto_metadata** Pekar på SHA1-kontroll block som används i *_nx_crypto_method_sha1_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För SHA1 måste metadatans storlek *sizeof (NX_CRYPTO_SHA1)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) körde SHA1-åtgärden.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig SHA1-algoritm har angetts.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

### <a name="example"></a>Exempel

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Rensa SHA1-kontroll blocket.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa SHA1-kontroll blocket när den har angett att den här SHA1-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekar på SHA1-kontroll block som används i *_nx_crypto_method_sha1_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat SHA1-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Initierar kontroll block för SHA256-kryptografi

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar kontroll blocket SHA256 med den aktuella nyckel strängen. När SHA256-kontroll blocket initieras, ska efterföljande SHA256-åtgärd använda samma kontroll block.

Programmet kan skapa flera SHA256-kontroll block, som var och en representerar en session. Initieringen av SHA256 Control Block startar en ny session med hash-beräkning. Ominitieringen av kontroll blocket SHA256 överger den aktuella sessionen och använder stjärnorna som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för SHA256-kryptografiska metoder. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **nyckel** Det här fältet används inte för SHA256.
- **key_size_in_bits** Det här fältet används inte för SHA256
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för SHA256-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För SHA256 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA256)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera SHA256-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Utför SHA256-hash-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför SHA256-hash-åtgärd. Kontroll blocket SHA256 måste ha initierats med _ ***nx_crypto_method_sha256_init ()***. SHA256-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 32 byte för SHA256, eller 28 byte för SHA224.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga SHA256-kryptografi metoden. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_sha256_init ().*
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för SHA256.
- **iv_size** Det här fältet används inte för SHA256.
- **output_buffer** Pekar till minnes området för den genererade SHA256-hashen.
- **output_buffer_size** Storlek på utdatabufferten i byte. För SHA256 måste buffertstorleken vara 32 byte. För SHA224 måste buffertstorleken vara 28 byte.
- **crypto_metadata** Pekare till SHA2-kontroll blocket som används i *_nx_crypto_method_sha2_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För SHA256 måste metadata *-storleken sizeof (NX_CRYPTO_SHA256)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig SHA256-algoritm anges.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Rensa kontroll blocket SHA256.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa SHA256-kontroll blocket när den har bedömt att den här SHA256-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till SHA256-kontroll blocket som används i *_nx_crypto_method_sha256_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat SHA256-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

Initierar kontroll block för SHA512-kryptografi

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

### <a name="description"></a>Beskrivning

Den här funktionen initierar kontroll blocket SHA512 med den aktuella nyckel strängen. När SHA512-kontroll blocket initieras, ska efterföljande SHA512-åtgärd använda samma kontroll block.

Programmet kan skapa flera SHA512-kontroll block, som var och en representerar en session. Initieringen av SHA512 Control Block startar en ny session med hash-beräkning. Ominitieringen av kontroll blocket SHA512 överger den aktuella sessionen och använder stjärnorna som en ny.

### <a name="parameters"></a>Parametrar

- **metod** Pekar på ett giltigt kontroll block för SHA512-kryptografiska metoder. Följande fördefinierade krypterings metoder är tillgängliga:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **nyckel** Det här fältet används inte för SHA512.
- **key_size_in_bits** Det här fältet används inte för SHA512
- **Hantera** Den här tjänsten returnerar en referens till anroparen. Referensen är implementerings beroende och används inte i den här implementeringen. Programmet ska skicka NULL för referensen.
- **crypto_metadata** Pekar på ett giltigt minnes utrymme för SHA512-kontroll blocket. Start adressen för minnes utrymmet måste vara 4-byte-justerad.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För SHA512 måste storleken på metadata vara *sizeof (NX_CRYPTO_SHA512)*

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) lyckades initiera SHA512-kontroll blocket med nyckel-och nyckel storleken.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig pekare till nyckeln eller ogiltig crypto_metadata eller crypto_metadata_size, eller så är crypto_metadata inte 4 byte-justerad.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Utför SHA512-hash-åtgärd

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

### <a name="description"></a>Beskrivning

Den här funktionen utför SHA512-hash-åtgärd. Kontroll blocket SHA512 måste ha initierats med _ *nx_crypto_method_sha512_init ()*. SHA512-algoritmen som ska utföras baseras på den algoritm som anges i *metod* kontroll blocket.

För den slutliga *NX_CRYPTO_HASH_CALCULATE* åtgärden måste buffertens storlek vara 64 byte för SHA512, eller 48 byte för SHA384.

### <a name="parameters"></a>Parametrar

- **op** Typ av åtgärd som ska utföras. En giltig åtgärd är:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Hantera** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **metod** Pekare till den giltiga SHA512-kryptografi metoden. Den krypterings metod som används här måste vara samma som används i _ *nx_crypto_method_sha512_init ().*
- **input_data** Pekar på en buffert som innehåller indata för text. Det finns inga begränsningar för indatabufferten.
- **input_data_size** Storlek på indata, i byte.
- **iv_ptr** Det här fältet används inte för SHA512.
- **iv_size** Det här fältet används inte för SHA512.
- **output_buffer** Pekar till minnes området för den genererade SHA512-hashen.
- **output_buffer_size** Storlek på utdatabufferten i byte. För SHA512 måste buffertstorleken vara 64 byte. För SHA384 måste buffertstorleken vara 48 byte.
- **crypto_metadata** Pekare till SHA512-kontroll blocket som används i *_nx_crypto_method_sha512_init ()*.
- **crypto_metadata_size** Storlek, i byte, för crypto_metadatas ytan. För SHA512 måste metadata *-storleken sizeof (NX_CRYPTO_SHA512)*
- **packet_ptr** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.
- **nx_crypto_hw_process_callback** Det här fältet används inte i program implementeringen för NetX-kryptografi bibliotek. Alla värden som skickas i ignoreras tyst.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0x00) genomförde åtgärden SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.
- **NX_PTR_ERROR** (0X07) ogiltig inmatad pekare eller ogiltig längd.
- **NX_CRYPTO_INVALID_ALGORITHM** (0X20004) ogiltig SHA512-algoritm anges.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) ogiltig storlek för utdatabuffert.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Rensa kontroll blocket SHA512.

### <a name="prototype"></a>Prototyp

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Beskrivning

Programmet anropar den här funktionen för att rensa SHA512-kontroll blocket när den har bedömt att den här SHA512-sessionen inte längre behövs.

### <a name="parameters"></a>Parametrar

- **crypto_metadata** Pekare till SHA512-kontroll blocket som används i *_nx_crypto_method_sha512_init ()*.

### <a name="return-values"></a>Retur värden

- **NX_CRYPTO_SUCCESS** (0X00) har rensat SHA512-sessionen.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) krypterings biblioteket är i ett ogiltigt tillstånd och kan inte användas.