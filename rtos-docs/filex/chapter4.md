---
title: Kapitel 4 – Beskrivning av Azure återställnings tider FileX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider FileX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826544"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Kapitel 4 – Beskrivning av Azure återställnings tider FileX-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure återställnings tider FileX-tjänster i alfabetisk ordning. Tjänst namn är utformade så att alla liknande tjänster grupperas tillsammans.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

Läser katalogattribut

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten läser katalogens attribut från det angivna mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar mot namnet på den begärda katalogen (katalog Sök väg är valfritt).
- **attribut** _Ptr: pekar mot målet för katalogens attribut som ska placeras. Katalogattribut returneras i ett bit kart format med följande möjliga inställningar:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (protokollnumret 0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) attributen för lyckad katalog läsning
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta **FX-_NOT** (0x04) som angavs i mediet
- **FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_FILE_CORRUPT** 0X08-filen är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

Anger katalogattribut

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger katalogens attribut till dem som anges av anroparen.

> [!WARNING]
> *Det här programmet får bara ändra en delmängd av katalogens attribut med den här tjänsten. Alla försök att ange ytterligare attribut leder till ett fel.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar mot namnet på den begärda katalogen (katalog Sök väg är valfritt).
- **attribut**: de nya attributen för den här katalogen. Giltiga katalogattribut definieras enligt följande:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (protokollnumret 0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) konfigurerat katalog-Attribute
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04) i mediet
- **FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare
- **FX_INVALID_ATTR** (0X19) ogiltiga attribut har marker ATS.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

Skapar under Katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en under katalog i den aktuella standard katalogen eller i sökvägen som anges i katalog namnet. Till skillnad från rot katalogen har under kataloger ingen gräns för hur många filer de kan innehålla. Rot katalogen kan bara innehålla antalet poster som fastställs av start posten.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar på namnet på katalogen som ska skapas (katalog Sök väg är valfritt).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) katalogen har skapats.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04) i mediet
- **FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_FILE _CORRUPT** -filen (0x08) är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare
- **FX_INVALID_ATTR** (0X19) ogiltiga attribut har marker ATS.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

Hämtar senaste standard katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar pekaren till den sökväg som senast angavs av ***fx_directory_default_set***. Om standard katalogen inte har angetts eller om den aktuella standard katalogen är rot katalogen returneras ett värde för FX_NULL.

> [!IMPORTANT]
> *Standard storleken för den interna Sök vägs strängen är 256 tecken. Du kan ändra det genom att ändra **FX_MAXIMUM_PATH** i **fx_api. h** och återskapa hela FileX-biblioteket. Tecken Strängs Sök vägen upprätthålls för programmet och används inte internt av FileX.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **return_path_name**: pekar mot målet för den senaste standard katalog strängen. Värdet FX_NULL returneras om den aktuella inställningen för standard katalogen är roten. När mediet har öppnats är roten standardvärdet.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) standard katalog hämtning
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- **FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

Ställer in standard katalog

### <a name="prototype"></a>Prototyp

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger standard katalogen för mediet. Om värdet FX_NULL anges, anges standard katalogen till mediets rot Katalog. Alla efterföljande fil åtgärder som inte uttryckligen anger en sökväg kommer att använda den här katalogen som standard.

> [!IMPORTANT]
> *Standard storleken för den interna Sök vägs strängen är 256 tecken. Du kan ändra det genom att ändra **FX_MAXIMUM_PATH** i **fx_api. h** och återskapa hela FileX-biblioteket. Tecken Strängs Sök vägen upprätthålls för programmet och används inte internt av FileX.*

> [!IMPORTANT]
> *För namn som anges av programmet stöder FileX både omvänt snedstreck ( \\ ) och snedstreck (/) för att skilja kataloger, under kataloger och fil namn. FileX använder dock bara det omvända snedstrecket i sökvägar som returneras till programmet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **new_path_name**: pekar mot nytt standard katalog namn. Om värdet FX_NULL anges, är standard katalogen för mediet inställt på mediets rot Katalog.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) standard katalog uppsättning
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta **FX_INVALID_PATH** (0X0D) ny katalog
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

Tar bort under Katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna katalogen. Observera att katalogen måste vara tom för att den ska kunna tas bort.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar till namnet på katalogen som ska tas bort (katalog Sök väg är valfritt).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckad katalog borttagning
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04)
- Den angivna katalogen för **FX_DIR_NOT_EMPTY** (0x10) är inte tom
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen
- **FX_NOT_DIRECTORY** (0X0E) inte en katalog post
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

Hämtar första katalog posten

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det första post namnet i standard katalogen och kopierar den till det angivna målet.

> [!WARNING]
> *Det angivna målet måste vara tillräckligt stort för att rymma det maximala storleks FileX namnet, som definieras av **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *Om du använder en icke-lokal sökväg är det viktigt att förhindra (med en ThreadX semafor, mutex eller prioritets nivå ändring) andra program trådar från att ändra katalogen medan en katalogs traversr äger rum. Annars kan ogiltiga resultat erhållas.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **return_entry_name**: pekar mot mål för det första post namnet i standard katalogen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) den första katalog posten hittades
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

Hämtar den första katalog posten med fullständig information

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar mot målet som namn på en katalog post. Måste vara minst lika stor som FX_MAX_LONG_NAME_LEN.
- **attribut**: om det inte är null pekar pekaren på målet för postens attribut att placeras. Attributen returneras i formatet bit-Map med följande möjliga inställningar:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (protokollnumret 0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **storlek**: om den inte är null pekar markören mot målet för postens storlek i byte.
- **år**: om det inte är null pekar pekaren på målet för postens ändrings år.
- **månad**: om det inte är null pekar pekaren på målet för postens månads ändring.
- **dag**: om den inte är null pekar du på målet för postens dag.
- **timme**: om det inte är null pekar pekaren på målet för postens ändrings tid.
- **Minute**: om den inte är null pekar du på målet för postens minuters ändring.
- **sekund**: om det inte är null pekar pekaren på målet för postens andra ändring.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) den första katalog posten hittades
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat
- **FX_FILE _CORRUPT** -filen (0x08) är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

Hämtar information om katalog post

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar på katalog postens namn.
- **attribut**: pekar mot målet för attributen.
- **storlek**: pekar mot målets storlek.
- **år**: pekare till målet för året.
- **månad**: pekare till målet för månaden.
- **dag**: pekar mot målet för dagen.
- **timme**: pekare till målet för timmen.
- **minut**: pekar på målet för minuten.
- **sekund**: pekar mot målet för den andra.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) den första katalog posten hittades
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta den angivna katalogen för **FX_NOT_FOUND** (0x04) i mediet
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_FILE _CORRUPT** -filen (0x08) är skadad
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_PTR_ERROR** (0X18) ogiltig media-eller destinations pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

Rensar standard lokal sökväg

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten rensar den tidigare lokala Sök vägs inställningen för den anropande tråden.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar på ett tidigare öppnat medium.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) den lokala sökvägen är klar.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är för närvarande inte öppet
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

Hämtar den aktuella lokala Sök vägs strängen

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar den lokala Sök vägs pekaren för det angivna mediet. Om det inte finns någon lokal Sök vägs uppsättning returneras ett NULL-värde till anroparen.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **return_path_name**: pekar mot mål Strängs pekaren för den lokala Sök vägs strängen som ska lagras.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) lokal sökväg Hämta.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är för närvarande inte öppet
- **FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

Återställer tidigare lokal sökväg

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten återställer en tidigare angiven lokal sökväg. Sök positionen för katalogen som gjorts på den här lokala sökvägen återställs också, vilket gör den här rutinen användbar i rekursiva katalogs ökningar av programmet.

> [!IMPORTANT]
> *Varje lokal sökväg innehåller en lokal Sök vägs sträng med **FX_MAXIMUM_PATH** i storlek, som är som standard 256 tecken. Den här interna Sök vägs strängen används inte av FileX och tillhandahålls endast för programmets användning. Om **FX_LOCAL_PATH** ska deklareras som en lokal variabel bör användarna vara intakta i stacken som växer genom storleken på den här strukturen. Användarna är välkommen att minska storleken på **FX_MAXIMUM_PATH** och återskapa biblioteks källan för FileX.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **local_path_ptr**: pekar mot den tidigare angivna lokala sökvägen. Det är mycket viktigt att se till att den här pekaren faktiskt pekar på en lokal sökväg som används tidigare och fortfarande är intakt.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) återställning av lokal sökväg har slutförts.
- **FX_MEDIA_NOT_OPEN** (0X11) angivet medium är inte öppet för tillfället.
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller lokal Sök vägs pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

Konfigurerar en tråd bestämd lokal sökväg

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten konfigurerar en tråd specifik sökväg som anges av ***new_path_string** _. När den här rutinen har slutförts har den lokala Sök vägs informationen som lagras i _ *_local_path_ptr_** företräde framför den globala medie Sök vägen för alla fil-och katalog åtgärder som utförs av den här tråden. Detta kommer inte att påverka någon annan tråd i systemet 
> [!IMPORTANT]
> *Standard storleken för den lokala Sök vägs strängen är 256 tecken. Du kan ändra det genom att ändra **FX_MAXIMUM_PATH** i **fx_api. h** och återskapa hela FileX-biblioteket. Tecken Strängs Sök vägen upprätthålls för programmet och används inte internt av FileX.*

> [!IMPORTANT]
> *För namn som anges av programmet stöder FileX både omvänt snedstreck ( \\ ) och snedstreck (/) för att skilja kataloger, under kataloger och fil namn. FileX använder dock bara det omvända snedstrecket i sökvägar som returneras till programmet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot det tidigare öppnade mediet.
- **local_path_ptr**: målet för att hålla den trådbaserade lokala Sök vägs informationen. Adressen till den här strukturen kan anges i funktionen för återställning av lokal sökväg i framtiden.
- **new_path_name**: anger den lokala sökvägen till installations programmet.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) standard katalog uppsättningen har slutförts.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NOT_IMPLEMENTED** (0x22) * * FX_NO_LCOAL_PATH
- Det gick inte att hitta **FX_INVALID_PATH** (0X0D) ny katalog.
- **FX_NOT_IMPLEMENTED** (0x22)-* * FX_NO_LOCAL_PATH definieras.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller lokal Sök vägs pekare.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

Hämtar långt namn från kort namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det långa namnet (om det finns någon) som är associerad med det angivna korta (8,3-format) namnet. Det korta namnet kan vara antingen ett fil namn eller ett katalog namn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **short_name**: pekare till källans korta namn (8,3-format).
- **long_name**: pekar mot mål för långt namn. Om det inte finns något långt namn returneras det korta namnet. Observera att målet för det långa namnet måste vara tillräckligt stort för att rymma FX_MAX_LONG_NAME_LEN tecken.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) slutfört långt namn get
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) kort namn
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-post
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

Hämtar långt namn från kort namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det långa namnet (om det finns någon) som är associerad med det angivna korta (8,3-format) namnet. Det korta namnet kan vara antingen ett fil namn eller ett katalog namn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **short_name**: pekare till källans korta namn (8,3-format).
- **long_name**: pekar mot mål för långt namn. Om det inte finns något långt namn returneras det korta namnet. Obs: målet för det långa namnet måste vara tillräckligt stort för att rymma **FX_MAX_LONG_NAME_LEN** tecken.
- **long_file_name_buffer_length**: längden på den långa namn bufferten.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckat långt namn Hämta.
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) kort namn.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

Test för katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten testar om det angivna namnet är en katalog. I så fall returneras en FX_SUCCESS.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **directory_name**: pekar på katalog postens namn.

### <a name="return-values"></a>Retur värden

- Det angivna namnet för **FX_SUCCESS** (0x00) är en katalog.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) katalog posten.
- **FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

Hämtar nästa katalog post

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar nästa postnamn i den aktuella standard katalogen.

> [!WARNING]
> *Om du använder en icke-lokal sökväg är det också viktigt att förhindra (med en ThreadX semafor eller tråd prioritets nivå) andra program trådar från att ändra den här katalogen medan en katalog traversr äger rum. Annars kan ogiltiga resultat erhållas.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **return_entry_name**: pekare till målet för nästa postnamn i standard katalogen. Den buffert som pekaren pekar på måste vara tillräckligt stor för att rymma den maximala storleken på FileX namn, som definieras av **_FX_MAX_LONG_NAME_LEN_**.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) Nästa post hitta
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

Hämtar nästa katalog post med fullständig information

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar nästa postnamn i standard katalogen och kopierar den till det angivna målet. Den returnerar också fullständig information om posten som anges av de ytterligare indataparametrarna.

> [!WARNING]
> * Det angivna målet måste vara tillräckligt stort för att rymma det maximala storleks FileX namnet, som definieras av * * * FX_MAX_LONG_NAME_LEN * * * *

> [!WARNING]
> *Om du använder en icke-lokal sökväg är det viktigt att förhindra (med en ThreadX semafor, mutex eller prioritets nivå ändring) andra program trådar från att ändra katalogen medan en katalogs traversr äger rum. Annars kan ogiltiga resultat erhållas.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **directory_name**: pekar mot målet som namn på en katalog post. Måste vara minst lika stor som **FX_MAX_LONG_NAME_LEN**.
- **attribut**: om det inte är null pekar pekaren på målet för postens attribut att placeras. Attributen returneras i formatet bit-Map med följande möjliga inställningar:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (protokollnumret 0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **storlek**: om den inte är null pekar markören mot målet för postens storlek i byte.
- **månad**: om det inte är null pekar pekaren på målet för postens månads ändring.
- **år**: om det inte är null pekar pekaren på målet för postens ändrings år.
- **dag**: om den inte är null pekar du på målet för postens dag.
- **timme**: om det inte är null pekar pekaren på målet för postens ändrings tid.
- **Minute**: om den inte är null pekar du på målet för postens minuters ändring.
- **sekund**: om det inte är null pekar pekaren på målet för postens andra ändring.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckad katalog nästa post hitta.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_PTR_ERROR** (0X18) ogiltig Media pekare eller också är alla indataparametrar null.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

Byter namn på katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar katalog namnet till det angivna nya katalog namnet. Namnbytet görs också i förhållande till den angivna sökvägen eller standard Sök vägen. Om en sökväg anges i det nya katalog namnet flyttas den nya katalogen faktiskt till den angivna sökvägen. Om ingen sökväg anges placeras den omdöpta katalogen i den aktuella standard Sök vägen.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **old_directory_name**: pekar på aktuellt katalog namn.
- **new_directory_name**: pekar mot nytt katalog namn.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) katalog namns byte lyckades.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) katalog posten.
- **FX_NOT_DIRECTORY** -posten (0x0E) är inte en katalog.
- **FX_INVALID_NAME** (0X0C) nytt katalog namn är ogiltigt.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i den här katalogen.
- **FX_INVALID_PATH** (0X0D) ogiltig sökväg angavs med katalog namn.
- **FX_ALREADY_CREATED** (0x0B) den angivna katalogen har redan skapats.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

Hämtar kort namn från ett långt namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det korta (8,3-format) namn som är associerat med det angivna långa namnet. Det långa namnet kan vara antingen ett fil namn eller ett katalog namn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **long_name**: pekar mot källans långa namn.
- **short_name**: pekare till målets kort namn (8,3-format). Observera att målet för det korta namnet måste vara tillräckligt stort för att rymma 14 tecken.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) kort namn hämtades.
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) långt namn.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

Hämtar kort namn från ett långt namn

### <a name="prototype"></a>Prototyp

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det korta (8,3-format) namn som är associerat med det angivna långa namnet. Det långa namnet kan vara antingen ett fil namn eller ett katalog namn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **long_name**: pekar mot källans långa namn.
- **short_name**: pekare till målets kort namn (8,3-format). Obs: målet för det korta namnet måste vara tillräckligt stort för att rymma 14 tecken.
- **short_file_name_length**: längden på den korta bufferten.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) kort namn hämtades.
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) långt namn.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

Aktiverar tjänsten fel tolerans

### <a name="prototype"></a>Prototyp

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten aktiverar den feltoleranta modulen. Vid start identifierar den feltoleranta modulen om fil systemet är under FileX feltolerant skydd. Om den inte är det hittar tjänsten tillgängliga sektorer i fil systemet för att lagra loggar i fil system transaktioner. Om fil systemet är under FileX feltolerant skydd tillämpas loggarna på fil systemet för att upprätthålla dess integritet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **memory_ptr**: pekar på ett minnes block som används av feltolerant modul som virtuellt minne.
- **memory_size**: minnets storlek. För att feltolerant ska fungera korrekt, måste storleken på virtuellt minne vara minst 3072 byte, och måste vara flera av sektor storleken.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) har aktiverat fel tolerans.
- **FX_NOT_ENOUGH_MEMORY** (0x91) minnes storleken är för liten.
- Start sektor fel **FX_BOOT_ERROR** (0x01).
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_NO_MORE_ENTRIES** (0x0F) det finns inget ledigt kluster tillgängligt.
- **FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>Se även

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

Allokerar utrymme för en fil

### <a name="prototype"></a>Prototyp

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa hela kluster.

För att allokera utrymme utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_allocate*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **storlek**: antal byte som ska allokeras för filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) slutförde filallokering.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_NO_MORE_ENTRIES** (0x0F) det finns inget ledigt kluster tillgängligt.
- **FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>Se även

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close-fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open-fx_file_read
- fx_file_relative_seek
- fx_file_rename-fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

Läser filattribut

### <a name="prototype"></a>Prototyp

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten läser filens attribut från det angivna mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **file_name**: pekar mot namnet på den begärda filen (katalog Sök väg är valfritt).
- **attributes_ptr**: pekar mot målet för filens attribut som ska placeras. Filattributen returneras i ett bit kart format med följande möjliga inställningar:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (protokollnumret 0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Retur värden

- Det lästa attributet för **FX_SUCCESS** (0x00) har lästs.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen i mediet.
- **FX_NOT_A_FILE** (0x05) den angivna filen är en katalog.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltiga media-eller attribut pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close-fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

Ställer in filattribut

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger filens attribut till dem som anges av anroparen.

> [!WARNING]
> *Programmet får bara ändra en delmängd av filens attribut med den här tjänsten. Alla försök att ange ytterligare attribut leder till ett fel.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **file_name**: pekar på namnet på den begärda filen * * (katalog Sök väg är valfritt).
- **attribut**: de nya attributen för filen. Giltiga filattribut definieras på följande sätt:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (protokollnumret 0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Retur värden

- Den angivna attributet för **FX_SUCCESS** (0x00) har angetts.
- **FX_ACCESS_ERROR** -filen (0x06) är öppen och kan inte ha attributen inställd.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler poster i tabellen fat-eller exFAT-kluster.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen i mediet.
- **FX_NOT_A_FILE** (0x05) den angivna filen är en katalog.
- **FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_INVALID_ATTR** (0X19) ogiltiga attribut har marker ATS.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

Bästa förmåga att allokera utrymme för en fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa hela kluster. Om det inte finns tillräckligt många kluster som finns i följd i mediet länkar den här tjänsten det största tillgängliga blocket av flera kluster i följd till filen. Mängden utrymme som faktiskt allokeras till filen returneras till anroparen.

För att allokera utrymme utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_best_effort_allocate*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **storlek**: antal byte som ska allokeras för filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) bästa filallokering för bästa ansträngning.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare eller mål.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

Stänger filen

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten stänger den angivna filen. Om filen var öppen för skrivning och om den har ändrats, slutför den här tjänsten fil ändrings processen genom att uppdatera katalog posten med den nya storleken och den aktuella system tiden och det aktuella datumet.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) fil stängningen är klar.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltiga media-eller attribut pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

Skapar fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar den angivna filen i standard katalogen eller i den katalog Sök väg som anges med fil namnet.

> [!WARNING]
> *Den här tjänsten skapar en fil med längden noll, dvs. inga kluster allokeras. Allokeringen sker automatiskt vid efterföljande fil skrivningar eller kan göras i förväg med tjänsten fx_file_allocate eller fx_file_extended_allocate utrymme bortom 4 GB).*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **file_name**: pekar mot namnet på filen som ska skapas (katalog Sök väg är valfritt).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen har skapats.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) den angivna filen har redan skapats.
- **FX_NO_MORE_SPACE** (0x0A) det finns antingen inga fler poster i rot katalogen eller så finns det inga fler kluster tillgängliga.
- **FX_INVALID_PATH** (0X0D) ogiltig sökväg angavs med fil namn.
- **FX_INVALID_NAME** (0X0C) fil namnet är ogiltigt.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltigt medie-eller fil namns pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>Se även
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>Anger datum och tid för filen

Ange datum och tid för filen

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger datum och tid för den angivna filen.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **file_name**: pekaren till namnet på filen.
- **år**: värdet på året (1980-2107 inklusiv).
- **månad**: värde för månad (1-12 inklusiv).
- **dag**: värde på dag (1-31 inklusiv).
- **timme**: värde för timme (0-23 inklusiv).
- **Minute**: värdet för minut (0-59 inklusiv).
- **sekund**: värdet för sekund (0-59 inklusiv).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckad datum/tid-uppsättning.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta **FX_NOT_FOUND** -filen (0x04).
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.
- **FX_INVALID_YEAR** 0X12-året är ogiltigt.
- **FX_INVALID_MONTH** (0X13) månaden är ogiltig.
- **FX_INVALID_DAY** (0X14) dagen är ogiltig.
- **FX_INVALID_HOUR** (0X15) timmen är ogiltig.
- **FX_INVALID_MINUTE** (0X16) minut är ogiltig.
- Den andra **FX_INVALID_SECOND** (0x17) är ogiltig.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>Tar bort fil

Borttagning av fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tar bort den angivna filen.


### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **file_name**: pekar mot namnet på filen som ska tas bort (katalog Sök väg är valfritt).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) fil borttagning har slutförts.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta den angivna filen **FX_NOT_FOUND** (0x04).
- **FX_NOT_A_FILE** (0x05) det angivna fil namnet var en katalog eller volym.
- Den angivna filen för **FX_ACCESS_ERROR** (0x06) är öppen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

Allokerar utrymme för en fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa hela kluster.

Den här tjänsten är utformad för exFAT. *Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen förallokerar utrymme bortom intervallet 4 GB.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **storlek**: antal byte som ska allokeras för filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) slutförde filallokering.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

Bästa förmåga att allokera utrymme för en fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Beskrivning

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa hela kluster. Om det inte finns tillräckligt många kluster som finns i följd i mediet länkar den här tjänsten det största tillgängliga blocket av flera kluster i följd till filen. Mängden utrymme som faktiskt allokeras till filen returneras till anroparen.

Den här tjänsten är utformad för exFAT. *Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen förallokerar utrymme bortom intervallet 4 GB.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **storlek**: antal byte som ska allokeras för filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) slutförde filallokering.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_NO_MORE_SPACE** (0X0a) mediet som är kopplat till den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

Positioner till en relativ byte förskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven relativ byte förskjutning. Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.

Den här tjänsten är utformad för exFAT. Parametern *byte_offset* tar ett 64-bitars värde, vilket gör att anroparen kan placera Läs-och skriv Visa-pekaren utanför 4 GB-intervall.

> [!IMPORTANT]
> *Om Sök åtgärden försöker söka efter slutet av filen placeras filens Läs-och skriv pekare i slutet av filen. Om Sök åtgärden försöker placera förbi början av filen placeras filens Läs-och skriv visare i början av filen.*

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **byte_offset**: önskad relativ byte förskjutning i filen.
- **seek_from**: riktningen och platsen där den relativa sökningen ska utföras. Giltiga alternativ för sökning definieras på följande sätt:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (protokollnumret 0x02)
  - FX_SEEK_BACK (0x03) om FX_SEEK_BEGIN anges utförs Sök åtgärden från början av filen. Om FX_SEEK_END har angetts utförs Sök åtgärden bakåt från slutet av filen. Om FX_SEEK_FORWARD har angetts utförs söknings åtgärden framåt från den aktuella fil positionen. Om FX_SEEK_BACK har angetts utförs Sök åtgärden baklänges från den aktuella fil positionen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) fil relativ sökning har slutförts.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

Positioner till byte-förskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven byte förskjutning. Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.

Den här tjänsten är utformad för exFAT. Parametern *byte_offset* tar ett 64-bitars värde, vilket gör att anroparen kan placera Läs-och skriv Visa-pekaren utanför 4 GB-intervall.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **byte_offset**: önskad byte förskjutning i filen. Värdet noll placerar Läs-och skriv pekaren i början av filen, medan ett värde som är större än filens storlek kommer att placera Läs-och skriv pekaren i slutet av filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) Sök efter filer.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open-fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

Trunkerar fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten trunkerar filens storlek till den angivna storleken. Om den angivna storleken är större än den faktiska fil storleken gör inte den här tjänsten något. Inget av de medie kluster som är associerade med filen har släppts.

> [!WARNING]
> *Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*

Den här tjänsten är utformad för exFAT. *Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen kan använda fler än 4 GB.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **storlek**: ny fil storlek. Gamla byte den nya fil storleken ignoreras.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen trunkerades.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

Trunkerar filen och släpper kluster (er)

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten trunkerar filens storlek till den angivna storleken. Om den angivna storleken är större än den faktiska fil storleken gör inte tjänsten något. Till skillnad från den ***fx_file_extended_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.

> [!WARNING]
> *Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*

Den här tjänsten är utformad för exFAT. *Storleks* parametern tar ett 64-bitars heltals värde, vilket gör att anroparen kan använda fler än 4 GB.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **storlek**: ny fil storlek. Gamla byte den nya fil storleken ignoreras.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen trunkerades.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

Öppnar fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Beskrivning

Den här tjänsten öppnar den angivna filen för antingen läsning eller skrivning. En fil kan öppnas för läsning flera gånger, medan en fil bara kan öppnas för skrivning en gång tills skrivaren stänger filen.

> [!IMPORTANT]
> *Var försiktig om en fil öppnas samtidigt för läsning och skrivning. Fil skrivning som utförs när en fil öppnas samtidigt för läsning kanske inte visas av läsaren, om inte läsaren stänger och öppnar filen för läsning. På samma sätt bör filen Writer vara försiktig när du använder filtrunkering av tjänster. Om en fil trunkeras av skrivaren kan läsare av samma fil returnera ogiltiga data.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **file_ptr**: pekar mot fil kontroll blocket.
- **file_name**: pekar mot namnet på filen som ska öppnas (katalog Sök väg är valfritt).
- **open_type**: typ av fil öppen. Giltiga alternativ för öppen typ är:
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (protokollnumret 0x02)

Att öppna filer med FX_OPEN_FOR_READ och FX_OPEN_FOR_READ_FAST liknar följande:

- FX_OPEN_FOR_READ innehåller en verifiering av att den länkade listan över kluster som utgör filen är intakt och FX_OPEN_FOR_READ_FAST inte utför den här verifieringen, vilket gör det snabbare.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen är öppen.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta den angivna filen **FX_NOT_FOUND** (0x04).
- **FX_NOT_A_FILE** (0x05) det angivna fil namnet var en katalog eller volym.
- **FX_FILE_CORRUPT** (0x08) den angivna filen är skadad och det gick inte att öppna.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är redan öppen eller öppen typ är ogiltig.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) ogiltigt medium.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close-fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

Läser byte från fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>Beskrivning

Tjänsten läser byte från filen och lagrar dem i den angivna bufferten. När läsningen är klar är filens interna Läs pekare justerad så att den pekar på nästa byte i filen. Om det finns färre byte kvar i begäran lagras bara återstående byte i bufferten. I alla fall returneras det totala antalet byte som placeras i bufferten till anroparen.

> [!WARNING]
> *Programmet måste se till att den angivna bufferten kan lagra det angivna antalet begärda byte.*

> [!WARNING]
> *Snabbare prestanda uppnås om målcachen är på ett långt ord och den begärda storleken är jämnt delbar med sizeof (**ulong**).*

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **buffer_ptr**: pekar mot målcachen för läsning.
- **request_size**: högsta antal byte som ska läsas.
- **actual_size**: pekar mot variabeln som innehåller det faktiska antalet byte som läses in i den angivna bufferten.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen har lästs.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_FILE_CORRUPT** (0x08) den angivna filen är skadad och läsningen misslyckades.
- **FX_END_OF_FILE** (0X09) slutet av filen har nåtts.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig fil-eller buffert pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a>Se även

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

Positioner till en relativ byte förskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven relativ byte förskjutning. Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.

> [!IMPORTANT]
> *Om Sök åtgärden försöker söka efter slutet av filen placeras filens Läs-och skriv pekare i slutet av filen. Om Sök åtgärden försöker placera förbi början av filen placeras filens Läs-och skriv visare i början av filen.*

För att kunna söka med ett förskjutnings värde utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_relative_seek*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **byte_offset**: önskad relativ byte förskjutning i filen.
- **seek_from**: riktningen och platsen där den relativa sökningen ska utföras. Giltiga alternativ för sökning definieras på följande sätt:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (protokollnumret 0x02)
  - FX_SEEK_BACK (0x03)

Om FX_SEEK_BEGIN anges utförs Sök åtgärden från början av filen. Om FX_SEEK_END har angetts utförs Sök åtgärden bakåt från slutet av filen. Om FX_SEEK_FORWARD har angetts utförs söknings åtgärden framåt från den aktuella fil positionen. Om FX_SEEK_BACK har angetts utförs Sök åtgärden baklänges från den aktuella fil positionen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) fil relativ sökning har slutförts.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

Byter namn på filen

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar namnet på filen som anges av *old_file_name*. Namnbytet görs också i förhållande till den angivna sökvägen eller standard Sök vägen. Om en sökväg anges i det nya fil namnet flyttas filen med namnet som bytt namn till den angivna sökvägen. Om ingen sökväg anges placeras den omdöpta filen i den aktuella standard Sök vägen.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar mot ett medie kontroll block.
- **old_file_name**: pekar mot namnet på filen som ska byta namn (katalog Sök väg är valfritt).
- **new_file_name**: pekar mot det nya fil namnet. Katalog Sök vägen är inte tillåten.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen har bytt namn.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta den angivna filen **FX_NOT_FOUND** (0x04).
- **FX_NOT_A_FILE** (0x05) den angivna filen är en katalog.
- Den angivna filen för **FX_ACCESS_ERROR** (0x06) är redan öppen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_INVALID_NAME** (0X0C) angivet nytt fil namn är inte ett giltigt fil namn.
- Sökvägen till **FX_INVALID_PATH** (0x0D) är ogiltig.
- **FX_ALREADY_CREATED** (0X0B) det nya fil namnet används.
- **FX_MEDIA_INVALID** -mediet (protokollnumret 0x02) är ogiltigt.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

Positioner till byte-förskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Beskrivning

Den här tjänsten placerar den interna filen Läs/skriv-pekare till angiven byte förskjutning. Eventuella efterföljande fil läsnings-eller Skriv begär Anden kommer att börja på den här platsen i filen.

För att kunna söka med ett förskjutnings värde utöver 4 GB, ska programmet använda tjänsten *fx_file_extended_seek*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **byte_offset**: önskad byte förskjutning i filen. Värdet noll placerar Läs-och skriv pekaren i början av filen, medan ett värde som är större än filens storlek kommer att placera Läs-och skriv pekaren i slutet av filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) Sök efter filer.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

Trunkerar fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Beskrivning

Den här tjänsten trunkerar filens storlek till den angivna storleken. Om den angivna storleken är större än den faktiska fil storleken gör inte den här tjänsten något. Inget av de medie kluster som är associerade med filen har släppts.

> [!WARNING]
> *Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*

För att kunna arbeta mer än 4 GB använder programmet tjänsten *fx_file_extended_truncate*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **storlek**: ny fil storlek. Gamla byte den nya fil storleken ignoreras.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen trunkerades.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det saknas mer utrymme för att slutföra åtgärden
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

Trunkerar filen och släpper kluster (er)

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten trunkerar filens storlek till den angivna storleken. Om den angivna storleken är större än den faktiska fil storleken gör inte tjänsten något. Till skillnad från den ***fx_file_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.

> [!WARNING]
> *Använd varnings korta filer som också kan vara öppna för läsning samtidigt. Om du trunkerar en fil som också öppnas för läsning kan det leda till att ogiltiga data läses in.*

För att kunna arbeta mer än 4 GB använder programmet tjänsten *fx_file_extended_truncate_release*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot en tidigare öppnad fil.
- **storlek**: ny fil storlek. Gamla byte den nya fil storleken ignoreras.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen trunkerades.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- Den angivna filen för **FX_NOT_OPEN** (0x07) är inte öppen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0X23) underliggande media är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_NO_MORE_SPACE** (0x0A) det fanns inte mer utrymme för att slutföra åtgärden.
- **FX_PTR_ERROR** (0X18) ogiltig fil pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

Skriver byte till fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skriver byte från den angivna bufferten med början i filens aktuella position. När skrivningen är klar är filens interna Läs pekare justerad så att den pekar på nästa byte i filen.

> [!WARNING]
> *Snabbare prestanda uppnås om källhierarkin är på ett långt ord och den begärda storleken är jämnt delbar med sizeof (**ulong**).*

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **buffer_ptr**: pekar på käll bufferten för skrivning.
- **storlek**: antal byte som ska skrivas.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) fil skrivning.
- **FX_NOT_OPEN** (0x07) den angivna filen är inte öppen.
- **FX_ACCESS_ERROR** (0x06) den angivna filen är inte öppen för skrivning.
- **FX_NO_MORE_SPACE** (0X0a) det finns inget utrymme tillgängligt på mediet för att kunna utföra den här skrivningen.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0X0F) inga fler fett poster.
- **FX_PTR_ERROR** (0X18) ogiltig fil-eller buffert pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_read,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

Ställer in funktionen för fil skrivnings meddelande

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Beskrivning

Den här tjänsten installerar callback-funktionen som anropas efter en lyckad fil skrivnings åtgärd.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr**: pekar mot fil kontroll blocket.
- **file_write_notify**: funktionen Skriv motringning för fil som ska installeras. Om du anger funktionen motringning till NULL inaktive ras motringningsfunktionen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) har installerat motringningsfunktionen.
- **FX_PTR_ERROR** (0x18) FILE_PTR är null.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

Avbryter medie aktiviteter

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten avbryter alla aktuella aktiviteter som är associerade med mediet, inklusive stängning av alla öppna filer, sändning av en abort-begäran till den associerade driv rutinen och placering av mediet i avbrutet tillstånd. Den här tjänsten kallas vanligt vis när I/O-fel upptäcks.

> [!WARNING]
> *Mediet måste öppnas igen för att det ska kunna användas igen när en avbrotts åtgärd utförs.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) mediet har avbrutits.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

Ogiltig cachelagring av logisk sektor

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten tömmer alla skadade sektorer i cachen och upphäver sedan hela den logiska sektorens cacheminne.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) cachelagring av medie innehåll är ogiltig.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller Scratch-pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

Söker efter fel i mediet

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten kontrollerar det angivna mediet för grundläggande strukturella fel, inklusive fil/katalog över länkning, ogiltiga FAT-kedjor och förlorade kluster. Tjänsten ger också möjlighet att korrigera identifierade fel.

Den fx_media_check tjänsten kräver minne i minnet för den djupgående första analysen av kataloger och filer på mediet. Mer specifikt måste det virtuella minnet som tillhandahålls för medie kontroll tjänsten vara tillräckligt stort för att rymma flera katalog poster, en data struktur för att "stacka" den aktuella katalog inmatnings positionen innan du går in i under kataloger och slutligen den logiska FAT-bitars kartan. Det virtuella minnet måste vara minst 512-1024 byte plus minne för den logiska FAT-bitars kartan, vilket kräver så många bitar som det finns kluster i mediet. Till exempel skulle en enhet med 8000 kluster kräva 1000 byte för att representera och därför kräva en total arbets yta i ordningen på 2048 byte.

> [!WARNING]
> *Den här tjänsten ska endast anropas omedelbart efter fx_media_open och utan någon annan fil system aktivitet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **scratch_memory_ptr**: pekar mot start av virtuellt minne.
- **scratch_memory_size**: minnets storlek i byte.
- **error_correction_option**: fel korrigerings alternativ bitar när biten har angetts utförs fel korrigering. Bitarna med fel korrigerings alternativ definieras enligt följande:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (protokollnumret 0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) enkelt eller tillsammans de nödvändiga fel korrigerings alternativen. Om ingen fel korrigering krävs måste värdet 0 anges.
- **errors_detected_ptr**: målet för fel identifierings bitar enligt definitionen nedan:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (protokollnumret 0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Retur värden

- Media kontrollen **FX_SUCCESS** (0X00) lyckades, Visa fel identifierade destinationer för mer information.
- **FX_ACCESS_ERROR** (0X06) Det går inte att utföra kontrollen med öppna filer.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NO_MORE_SPACE** (0x0A) Det går inte att frigöra utrymme på mediet.
- **FX_NOT_ENOUGH_MEMORY** (0x91) som tillhandahöll det virtuella minnet är inte tillräckligt stort.
- **FX_ERROR_NOT_FIXED** (0X93) fel i FAT32-rot katalogen som inte kunde åtgärdas.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_SECTOR_INVALID** -sektorn (0x89) är ogiltig.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller Scratch-pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.


### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

Stänger mediet

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten stänger det angivna mediet. När mediet stängs stängs alla öppna filer och eventuella kvarvarande buffertar töms till det fysiska mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie stängningen lyckades.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

Ställer in meddelande funktionen för medie stängning

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger en funktion för att skicka ett meddelande om motringning som anropas när ett medium har stängts.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **media_close_notify**: medie stängning meddela återanrops funktion som ska installeras. Om du skickar NULL som callback-funktionen inaktive ras mediet Stäng motringning.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) har installerat motringningsfunktionen.
- **FX_PTR_ERROR** (0x18) MEDIA_PTR är null.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

Formaterar Media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a>Beskrivning

Den här tjänsten formaterar det angivna mediet på ett exFAT-kompatibelt sätt baserat på de angivna parametrarna. Den här tjänsten måste anropas innan mediet kan öppnas.

> [!WARNING]
> *Formatering av redan formaterade medier raderar effektivt alla filer och kataloger på mediet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block. Detta används endast för att ge lite grundläggande information som krävs för att driv rutinen ska fungera.
- **driv rutin**: pekar på i/O-drivrutinen för det här mediet. Detta är vanligt vis samma driv rutin som anges för efterföljande fx_media_open-anrop.
- **driver_info_ptr**: pekar mot valfri information som i/O-drivrutinen kan använda.
- **memory_ptr**: pekar på det aktiva minnet för mediet. memory_size anger storleken på arbets medie minnet. Storleken måste vara minst lika stor som mediets sektor storlek.
- **volume_name**: pekar på volym namn strängen, vilket är högst 11 tecken.
- **number_of_fats**: antalet fetter på mediet. Aktuell implementering stöder en FAT på mediet.
- **hidden_sectors**: antalet sektorer som är dolda innan mediets start sektor. Detta är vanligt när det finns flera partitioner.
- **total_sectors**: det totala antalet sektorer i mediet.
- **bytes_per_sector**: antal byte per sektor, vanligt vis 512. FileX kräver att detta är en multipel av 32.
- **sectors_per_cluster**: antalet sektorer i varje kluster. Klustret är den minsta allokeringsenheten i ett FAT-filsystem.
- **volumne_serial_number**: serie numret som ska användas för den här volymen.
- **boundary_unit**: justerings storlek för fysiskt data område i antal sektorer.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie formatet har slutförts.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig media, driv rutin eller minnes pekare.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

Returnerar tillgängligt medie utrymme

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar antalet byte som är tillgängliga i mediet.

Den här tjänsten är utformad för exFAT. Pekaren till *available_bytes* parameter tar ett 64-bitars heltals värde, vilket gör att anroparen kan arbeta med Media utanför 4 GB-intervallet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar på ett tidigare öppnat medium.
- **available_bytes_ptr**: tillgängliga byte kvar på mediet.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) har hämtat tillgängligt utrymme på mediet.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_PTR_ERROR** (0X18) ogiltig Media pekare eller tillgängliga byte pekare är null.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

Tömmer data till fysiska media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten tömmer alla cachelagrade sektorer och katalog poster för alla ändrade filer till det fysiska mediet.

> [!WARNING]
> *Den här rutinen kan anropas regelbundet av programmet för att minska risken för skadade filer och/eller data förlust i händelse av plötslig förlust av ström på målet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie tömning lyckades.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_FILE_CORRUPT**    -filen (0x08) är skadad.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

Formaterar Media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a>Beskrivning

Den här tjänsten formaterar det angivna mediet i ett FAT 12/16/32-kompatibelt sätt baserat på de angivna parametrarna. Den här tjänsten måste anropas innan mediet kan öppnas.

> [!WARNING]
> *Formatering av redan formaterade medier raderar effektivt alla filer och kataloger på mediet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block. Detta används endast för att ge lite grundläggande information som krävs för att driv rutinen ska fungera.
- **driv rutin**: pekar på i/O-drivrutinen för det här mediet. Detta är vanligt vis samma driv rutin som anges för efterföljande fx_media_open-anrop.
- **driver_info_ptr**: pekar mot valfri information som i/O-drivrutinen kan använda.
- **memory_ptr**: pekar på det aktiva minnet för mediet.
- **memory_size**: anger storleken på arbets medie minnet. Storleken måste vara minst lika stor som mediets sektor storlek.
- **volume_name**: pekar på volym namn strängen, vilket är högst 11 tecken.
- **number_of_fats**: antalet fetter på mediet. Det minimala värdet är 1 för primärt fett. Värden som är större än 1 leder till att ytterligare FAT-kopior bevaras vid körning.
- **directory_entries**: antalet katalog poster i rot katalogen.
- **hidden_sectors**: antalet sektorer som är dolda innan mediets start sektor. Detta är vanligt när det finns flera partitioner.
- **total_sectors**: det totala antalet sektorer i mediet.
- **bytes_per_sector**: antal byte per sektor, vanligt vis 512. FileX kräver att detta är en multipel av 32.
- **sectors_per_cluster**: antalet sektorer i varje kluster. Klustret är den minsta allokeringsenheten i ett FAT-filsystem.
- **huvuden**: antal fysiska huvuden.
- **sectors_per_track**: antalet sektorer per spår.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie formatet har slutförts.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig media, driv rutin eller minnes pekare.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

Öppnar mediet för fil åtkomst

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>Beskrivning

Den här tjänsten öppnar ett medium för fil åtkomst med hjälp av den angivna I/O-drivrutinen.

> [!WARNING]
> *Det minne som har angetts för den här tjänsten används för att implementera en intern logisk sektor, vilket innebär att det mer minne som tillhandahölls desto mer fysiskt I/O minskas. FileX kräver en cache på minst en logisk sektor (byte per sektor av mediet).*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **media_name**: pekar på mediets namn.
- **media_driver**: pekare till i/O-drivrutin för det här mediet. I/O-drivrutinen måste uppfylla kraven för FileX-drivrutin som definieras i kapitel 5.
- **driver_info_ptr**: pekar mot valfri information som den angivna i/O-drivrutinen kan använda.
- **memory_ptr**: pekar på det aktiva minnet för mediet.
- **memory_size**: anger storleken på arbets medie minnet. Storleken måste vara lika stor som mediets sektor storlek (vanligt vis 512 byte).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) media är öppna.
- **FX_BOOT_ERROR** (0x01) Det gick inte att läsa mediets start sektor.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) det angivna mediets start sektor är skadat eller ogiltigt. Dessutom används den här retur koden för att ange att antingen cache-storleken för den logiska sektorn eller FAT-poststorleken inte är en potens av 2.
- **FX_FAT_READ_ERROR** (0x03) Det gick inte att läsa mediet fat.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) en eller flera pekare är null.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

Anger funktionen för att öppna meddelanden i media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger en funktion för att skicka ett meddelande om motringning som anropas när ett medium har öppnats.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **media_open_notify**: mediet är öppet, så att callback-funktionen installeras. Om du skickar NULL som callback-funktionen inaktive ras mediet öppna motanrop.

### <a name="return-values"></a>Retur värden


- **FX_SUCCESS** (0x00) installerade återanrops funktionen.
- **FX_PTR_ERROR** (0x18) MEDIA_PTR är null.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

Läser logisk sektor från media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten läser en logisk sektor från mediet och placerar den i den angivna bufferten.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar på ett tidigare öppnat medium.
- **logical_sector**: logisk sektor som ska läsas.
- **buffer_ptr**: pekar mot målet för den logiska sektorn.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie läsning har lästs.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller buffert pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

Returnerar tillgängligt medie utrymme

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Beskrivning

Den här tjänsten returnerar antalet byte som är tillgängliga i mediet.

Om du vill arbeta med mediet som är större än 4 GB använder programmet tjänsten *fx_media_extended_space_available*.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar på ett tidigare öppnat medium.
- **available_bytes_ptr**: tillgängliga byte kvar på mediet.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) returnerade tillgängligt utrymme på mediet.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_PTR_ERROR** (0X18) ogiltig Media pekare eller tillgängliga byte pekare är null.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

Hämtar medie volymens namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar volym namnet för det tidigare öppnade mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **volume_name**: pekar mot mål för volym namn. Observera att målet måste vara minst tillräckligt stort för att rymma 12 tecken.
- **volume_source**: anger var du vill hämta namnet, antingen från start sektorn eller rot katalogen. Giltiga värden för den här parametern är:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie volym hämtades.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta **FX_NOT_FOUND** -volymen (0x04).
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller volym destinations pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

Hämtar medie volymens namn för tidigare öppnade medier

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar volym namnet för det tidigare öppnade mediet.

> [!IMPORTANT]
> Den här tjänsten är identisk med ***fx_media_volume_get () _,** förutom att anroparen skickar i storlek på den _ *volume_name** bufferten.

### <a name="input-parameters"></a>Indataparametrar


- **media_ptr**: pekare till Media Control Block.
- **volume_name**: pekar mot mål för volym namn. Observera att målet måste vara minst tillräckligt stort för att rymma 12 tecken.
- **volume_name_buffer_length**: volume_name buffertens storlek.
- **volume_source**: anger var du vill hämta namnet, antingen från start sektorn eller rot katalogen. Giltiga värden för den här parametern är:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) medie volym hämtades.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta **FX_NOT_FOUND** -volymen (0x04).
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) ogiltig media-eller volym destinations pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

Anger medie volymens namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten anger volym namnet för det tidigare öppnade mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **volume_name**: pekar mot volymens namn.

### <a name="return-values"></a>Retur värden

- Den **FX_SUCCESS** (0x00) medie volym uppsättningen har slutförts.
- **FX_INVALID_NAME** (0x0C) Volume_name är ogiltig.
- **FX_MEDIA_INVALID** (protokollnumret 0x02) Det gick inte att ange volym namn.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltigt medium eller volym namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

Skriver logisk sektor

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skriver den angivna bufferten till den angivna logiska sektorn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekar på ett tidigare öppnat medium.
- **logical_sector**: logisk sektor som ska skrivas.
- **buffer_ptr**: pekar mot källan för den logiska sektor skrivningen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) skrivning av media lyckades.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltig medie pekare.
- **FX_CALLER_ERROR**    (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a>Se även

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

Hämtar fil system datum

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Beskrivning

Den här tjänsten returnerar det aktuella system datumet.

### <a name="input-parameters"></a>Indataparametrar

- **år**: pekare till målet för år.
- **månad**: pekar mot mål i månaden.
- **dag**: pekare till mål för dag.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckad datum hämtning.
- **FX_PTR_ERROR** (0X18) en eller flera INDATAPARAMETRAR är null.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a>Se även

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

Anger system datum

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger det system datum som anges.

> [!WARNING]
> *Den här tjänsten ska ringas strax efter **fx_system_initialize** att ange det ursprungliga system datumet. Som standard är system datumet den senaste allmänna FileX-versionen.*

### <a name="input-parameters"></a>Indataparametrar

- **år**: nytt år. Det giltiga intervallet är från 1980 till och med året 2107.
- **månad**: ny månad. Det giltiga intervallet är mellan 1 och 12.
- **dag**: ny dag. Det giltiga intervallet är mellan 1 och 31, beroende på månad och år för skottår.

### <a name="return-values"></a>Retur värden

- Datum inställningen för **FX_SUCCESS** (0X00) lyckades.
- **FX_INVALID_YEAR** (0X12) ogiltigt år har angetts.
- **FX_INVALID_MONTH** (0X13) ogiltig månad har angetts.
- **FX_INVALID_DAY** (0X14) ogiltig dag har angetts.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>Se även

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

Initierar hela systemet

### <a name="prototype"></a>Prototyp

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>Beskrivning

Den här tjänsten initierar alla huvud data strukturer för FileX. Den ska anropas antingen i ***tx_application_define*** eller eventuellt från en initierings tråd och måste anropas innan någon annan FileX-tjänst används.

> [!WARNING]
> * När det här anropet har initierats bör programmet anropa ***fx_system_date_set** _ och _ *fx_system_time_set** för att börja med ett korrekt system datum och tid.*

### <a name="input-parameters"></a>Indataparametrar

Inget

### <a name="return-values"></a>Retur värden

Inga.

### <a name="allowed-from"></a>Tillåten från

Initiering, trådar

### <a name="example"></a>Exempel

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a>Se även

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

Hämtar aktuell system tid

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar den aktuella system tiden.

### <a name="input-parameters"></a>Indataparametrar

- **timme**: pekare till målet i timmen.
- **minut**: pekare till målet för minut.
- **sekund**: pekar mot målet för en sekund.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckad system tids hämtning.
- **FX_PTR_ERROR** (0X18) en eller flera indataparametrar

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a>Se även

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

Anger aktuell system tid

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Beskrivning

Den här tjänsten anger den aktuella system tiden som anges av indataparametrarna.

> [!WARNING]
> *Den här tjänsten ska ringas strax efter **fx_system_initialize** för att ställa in den första system tiden. System tiden är som standard 0:0:0.*

### <a name="input-parameters"></a>Indataparametrar

- **timme**: ny timme (0-23).
- **Minute**: ny minut (0-59).
- **sekund**: ny sekund (0-59).

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckad system tids hämtning.
- **FX_INVALID_HOUR**    (0X15) ny timme är ogiltig.
- **FX_INVALID_MINUTE** (0X16) ny minut är ogiltig.
- **FX_INVALID_SECOND** (0X17) ny sekund är ogiltig.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>Se även

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

Skapar en Unicode-katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Unicode-namngiven under katalog i den aktuella standard katalogen – ingen Sök vägs information tillåts i Unicode-källans namn parameter. Om det lyckas returneras det korta namnet (8,3-formatet) för den nyligen skapade Unicode-underkatalogen av tjänsten.

> [!WARNING]
> *Alla åtgärder i Unicode-underkatalogen (vilket gör den till standard Sök vägen, ta bort osv.) bör göras genom att ange det returnerade korta namnet (8,3-formatet) till standard katalog tjänsterna för FileX.*

> [!IMPORTANT]
> *Den här tjänsten stöds inte på exFAT media.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **source_unicode_name**: pekar mot Unicode-namnet för den nya under katalogen.
- **source_unicode_length**: längden på Unicode-namn.
- **short_name**: pekare till målet för kort namn (8,3-format) för den nya Unicode-underkatalogen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) Unicode-katalogen har skapats.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) som den angivna katalogen finns redan.
- **FX_NO_MORE_SPACE** (0X0a) inga fler kluster är tillgängliga i mediet för den nya katalog posten.
- Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.
- **FX_IO_ERROR (0x90)** Driv rutins-I/O-fel.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

Byter namn på katalogen med Unicode-sträng

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten ändrar en Unicode-namngiven under katalog till ett angivet nytt Unicode-namn i den aktuella arbets katalogen. Unicode-namnets parametrar får inte innehålla Sök vägs information.

> [!IMPORTANT]
> *Den här tjänsten stöds inte på exFAT media.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **old_unicode_name**: pekar mot Unicode-namnet för den aktuella filen.
- **old_unicode_name_length**: längden på det aktuella Unicode-namnet.
- **new_unicode_name**: pekar mot det nya Unicode-filnamn.
- **old_unicode_name_length**: längden på det nya Unicode-namnet.
- **new_short_name**: pekare till målet för kort namn (8,3-format) för den omdöpta Unicode-filen. Byt namn på katalogen med Unicode

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) media är öppna.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) det angivna katalog namnet finns redan.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) en eller flera pekare är null.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Se även

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

Skapar en Unicode-fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten skapar en Unicode-namngiven fil i den aktuella standard katalogen – ingen Sök vägs information tillåts i Unicode-källans namn parameter. Om det lyckas returneras det korta namnet (8,3-formatet) för den nyligen skapade Unicode-filen av tjänsten.

> [!WARNING]
> *Alla åtgärder på Unicode-filen (öppna, skriva, läsa, stänga osv.) bör utföras genom att tillhandahålla det returnerade korta namnet (8,3-formatet) till standard-FileX fil tjänster.*

### <a name="input-parameters"></a>Indataparametrar


- **media_ptr**: pekare till Media Control Block.
- **source_unicode_name**: pekar mot Unicode-namnet för den nya filen.
- **source_unicode_length**: längden på Unicode-namn.
- **short_name**: pekare till målet för kort namn (8,3-format) för den nya Unicode-filen.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) filen har skapats.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Den angivna filen för **FX_ALREADY_CREATED** (0x0B) finns redan.
- **FX_NO_MORE_SPACE** (0X0a) inga fler kluster är tillgängliga i mediet för den nya fil posten.
- Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

Byter namn på en fil med Unicode-sträng

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>Beskrivning

Den här tjänsten ändrar ett Unicode-namngivet fil namn till ett angivet nytt Unicode-namn i den aktuella standard katalogen. Unicode-namnets parametrar får inte innehålla Sök vägs information.

> [!IMPORTANT]
> *Den här tjänsten stöds inte på exFAT media.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **old_unicode_name**: pekar mot Unicode-namnet för den aktuella filen.
- **old_unicode_name_length**: längden på det aktuella Unicode-namnet.
- **new_unicode_name**: pekar mot det nya Unicode-filnamn.
- **new_unicode_name_length**: längden på det nya Unicode-namnet.
- **new_short_name**: pekare till målet för kort namn (8,3-format) för den omdöpta Unicode-filen.

### <a name="return-values"></a>Retur värden


- **FX_SUCCESS** (0x00) media är öppna.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) det angivna fil namnet finns redan.
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_PTR_ERROR** (0X18) en eller flera pekare är null.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.
- **FX_WRITE_PROTECT** (0x23) det angivna mediet är skrivskyddat.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

Hämtar längden på Unicode-namn

### <a name="prototype"></a>Prototyp

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>Beskrivning

Den här tjänsten fastställer längden på det angivna Unicode-namnet. Ett Unicode-tecken representeras av två byte. Ett Unicode-namn är en serie med två byte Unicode-tecken som avslut ATS av två NULL-byte (två byte 0-värde).

### <a name="input-parameters"></a>Indataparametrar

**unicode_name**: pekar mot Unicode-namn.

### <a name="return-values"></a>Retur värden

**längd**: längden på Unicode-namn (antal Unicode-tecken i namnet).

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

Hämtar längden på Unicode-namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar längden på det angivna Unicode-namnet. Ett Unicode-tecken representeras av två byte. Ett Unicode-namn är en serie twobyte Unicode-tecken som avslut ATS av två NULL-byte (två byte 0-värde).

> [!IMPORTANT]
> *Den här tjänsten är identisk med **fx_unicode_length_get ()** , förutom att anroparen skickar i storleken på den **unicode_name** bufferten, inklusive de två null-tecknen.*

### <a name="input-parameters"></a>Indataparametrar

- **unicode_name**: pekar mot Unicode-namn.
- **buffer_length**: storlek på Unicode-namnsuffix.

### <a name="return-values"></a>Retur värden

**längd**: längden på Unicode-namn (antal Unicode-tecken i namnet).

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

Hämtar Unicode-namn från kort namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det Unicode-namn som är associerat med det angivna korta namnet (8,3-formatet) i den aktuella standard katalogen – ingen Sök vägs information tillåts i den korta namn parametern. Om det lyckas returneras det Unicode-namn som är associerat med det korta namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten kan användas för att hämta Unicode-namn för både filer och under kataloger.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **short_name** Pekare till kort namn (8,3-format).
- **destination_unicode_name**: pekar mot målet för det Unicode-namn som är associerat med det angivna korta namnet.
- **destination_unicode_length**: pekare till returnerad Unicode-namn längd.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckades hämtning av Unicode-namn.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet eller så är storleken på Unicode-målet för liten.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

Hämtar Unicode-namn från kort namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det Unicode-namn som är associerat med det angivna korta namnet (8,3-formatet) i den aktuella standard katalogen – ingen Sök vägs information tillåts i den korta namn parametern. Om det lyckas returneras det Unicode-namn som är associerat med det korta namnet av tjänsten.

> [!IMPORTANT]
> * Den här tjänsten är identisk med ***fx_unicode_name_get**_, förutom att anroparen tillhandahåller storleken på målets Unicode-buffert som indatamängds argument. Detta gör att tjänsten kan garantera att den inte kommer att skriva över målets Unicode-buffert_

> [!IMPORTANT]
> *Den här tjänsten kan användas för att hämta Unicode-namn för både filer och under kataloger.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **short_name**: pekar mot kort namn (8,3-format).
- **destination_unicode_name**: pekar mot målet för det Unicode-namn som är associerat med det angivna korta namnet.
- **destination_unicode_length**: pekare till returnerad Unicode-namn längd.
- **unicode_name_buffer_length**: storleken på Unicode-databufferten. Obs! en NULL-begränsare krävs, vilket innebär en extra byte.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0X00) lyckades hämtning av Unicode-namn.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet eller så är storleken på Unicode-målet för liten.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

Hämtar kort namn från Unicode-namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

Den här tjänsten hämtar det korta namnet (8,3-formatet) som är associerat med Unicode-namnet i den aktuella standard katalogen, ingen Sök vägs information tillåts i Unicode-namn parametern. Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten kan användas för att hämta korta namn för både filer och under kataloger.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **source_unicode_name**: pekar mot Unicode-namn.
- **source_unicode_length**: längden på Unicode-namn.
- **destination_short_name**: pekare till målet för kort namnet (8,3-format). Det måste vara minst 13 byte stort.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) kort namn hämtning (0X00) lyckades.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) Unicode-namn.
- Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

Hämtar kort namn från Unicode-namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>Beskrivning

Den här tjänsten hämtar det korta namnet (8,3-formatet) som är associerat med Unicode-namnet i den aktuella standard katalogen, ingen Sök vägs information tillåts i Unicode-namn parametern. Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten är identisk med **fx_unicode_short_name_get ()**, förutom att anroparen tillhandahåller storleken på målcachen som ett indataargument. Detta gör att tjänsten garanterar det korta namnet inte överskrider målcachen.*

*Den här tjänsten kan användas för att hämta korta namn för både filer och under kataloger*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: pekare till Media Control Block.
- **source_unicode_name**: pekar mot Unicode-namn.
- **source_unicode_length**: längden på Unicode-namn.
- **destination_short_name**: pekare till målet för kort namnet (8,3-format). Det måste vara minst 13 byte stort.
- **short_name_buffer_length**: storleken på måldomänkontrollanten. Buffertstorleken måste vara minst 14 byte.

### <a name="return-values"></a>Retur värden

- **FX_SUCCESS** (0x00) kort namn hämtning (0X00) lyckades.
- **FX_FAT_READ_ERROR** (0X03) Det gick inte att läsa fat-tabellen.
- **FX_FILE_CORRUPT** -filen (0x08) är skadad
- **FX_IO_ERROR** (0X90) driv rutin I/O-fel.
- **FX_MEDIA_NOT_OPEN** (0x11) det angivna mediet är inte öppet.
- Det gick inte att hitta **FX_NOT_FOUND** (0X04) Unicode-namn.
- Tjänsten **FX_NOT_IMPLEMENTED** (0x22) har inte implementerats för fil systemet exFAT.
- **FX_SECTOR_INVALID** (0X89) ogiltig sektor.
- **FX_PTR_ERROR** (0X18) ogiltiga medie-eller namn pekare.
- **FX_CALLER_ERROR** (0X20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåten från

Konversation

### <a name="example"></a>Exempel

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Se även

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
