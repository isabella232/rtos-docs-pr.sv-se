---
title: Kapitel 4 – Beskrivning av Azure RTOS FileX-tjänster
description: Det här kapitlet innehåller en beskrivning av alla Azure RTOS FileX-tjänster i alfabetisk ordning.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 948adff65a080649db0870e35bc75ee774775cb7
ms.sourcegitcommit: 4cbe92b337e82124bb5a86d319b787eb05b4ea76
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/27/2021
ms.locfileid: "108067020"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Kapitel 4 – Beskrivning av Azure RTOS FileX-tjänster

Det här kapitlet innehåller en beskrivning av alla Azure RTOS FileX-tjänster i alfabetisk ordning. Tjänstnamn är utformade så att alla liknande tjänster grupperas tillsammans.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

Läser katalogattribut

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Description

Den här tjänsten läser katalogens attribut från det angivna mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name:** Pekare till namnet på den begärda katalogen (katalogsökvägen är valfri).
- **attribut** _ptr: Pekare till målet för katalogens attribut som ska placeras. Katalogattributen returneras i ett bit-map-format med följande möjliga inställningar:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckade katalogattribut lästa
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX _NOT FOUND** (0x04) Den angivna katalogen hittades inte på mediet
- **FX_NOT_DIRECTORY post** (0x0E) är inte en katalog
- **FX_IO_ERROR** (0x90) I/O-drivrutin
- **FX_FILE_CORRUPT** 0x08) Filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten anger katalogens attribut till de som anges av anroparen.

> [!WARNING]
> *Det här programmet kan bara ändra en delmängd av katalogens attribut med den här tjänsten. Om du försöker ange ytterligare attribut resulterar det i ett fel.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name:** Pekare till namnet på den begärda katalogen (katalogsökvägen är valfri).
- **attribut:** De nya attributen i den här katalogen. Giltiga katalogattribut definieras på följande sätt:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad katalogattributuppsättning
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet
- **FX_NOT_DIRECTORY post** (0x0E) är inte en katalog
- **FX_IO_ERROR** (0x90) I/O-drivrutin
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare
- **FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Skapar underkatalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Description

Den här tjänsten skapar en underkatalog i den aktuella standardkatalogen eller i den sökväg som anges i katalognamnet. Till skillnad från rotkatalogen har underkatalogerna ingen gräns för hur många filer de kan innehålla. Rotkatalogen kan bara innehålla det antal poster som bestäms av startposten.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name:** Pekare till namnet på katalogen som ska skapas (katalogsökvägen är valfri).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad katalog create.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet
- **FX_NOT_DIRECTORY post** (0x0E) är inte en katalog
- **FX_IO_ERROR** (0x90) I/O-drivrutin
- **FX_FILE _CORRUPT** (0x08) filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltig media
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare
- **FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar den senaste standardkatalogen

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Description

Den här tjänsten returnerar pekaren till sökvägen som senast angetts ***av fx_directory_default_set***. Om standardkatalogen inte har angetts eller om den aktuella standardkatalogen är rotkatalogen returneras värdet FX_NULL.

> [!IMPORTANT]
> *Standardstorleken för den interna sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **return_path_name:** Pekare till målet för den senaste standardkatalogsträngen. Värdet för FX_NULL returneras om den aktuella inställningen för standardkatalogen är roten. När mediet öppnas är roten standard.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad standardkatalog hämta
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger standardkatalog

### <a name="prototype"></a>Prototyp

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Description

Den här tjänsten anger standardkatalogen för mediet. Om ett värde FX_NULL anges anges standardkatalogen till mediets rotkatalog. Alla efterföljande filåtgärder som inte uttryckligen anger en sökväg kommer som standard att använda den här katalogen.

> [!IMPORTANT]
> *Standardstorleken för den interna sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*

> [!IMPORTANT]
> *För namn som anges av programmet har FileX stöd för både omsnedstreck ( ) och snedstreck (/) tecken för att avgränsa \\ kataloger, underkataloger och filnamn. FileX använder dock bara omsnedstreckstecknet i sökvägar som returneras till programmet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **new_path_name:** Pekare till nytt standardkatalognamn. Om ett värde FX_NULL anges anges standardkatalogen för mediet till mediets rotkatalog.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad standardkataloguppsättning
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_INVALID_PATH** (0x0D) Det gick inte att hitta den nya katalogen
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Tar bort underkatalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Description

Den här tjänsten tar bort den angivna katalogen. Observera att katalogen måste vara tom för att ta bort den.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name: Pekare** till namnet på katalogen som ska tas bort (katalogsökvägen är valfri).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad katalog borttagning
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna katalogen
- **FX_DIR_NOT_EMPTY** (0x10) Den angivna katalogen är inte tom
- **FX_IO_ERROR** (0x90) I/O-drivrutin
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen
- **FX_NOT_DIRECTORY** (0x0E) Inte en katalogpost
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar den första katalogposten

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det första postnamnet i standardkatalogen och kopierar det till det angivna målet.

> [!WARNING]
> *Det angivna målet måste vara tillräckligt stort för att innehålla det maximala FileX-namnet, enligt definitionen i **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *Om du använder en icke-lokal sökväg är det viktigt att förhindra andra programtrådar från att ändra den här katalogen medan en katalog-traverserning äger rum (med en ThreadX-semaphore, mutex eller prioritetsnivåändring). Annars kan ogiltiga resultat erhållas.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **return_entry_name:** Pekare till mål för det första postnamnet i standardkatalogen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad första katalogpost
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen
- **FX_IO_ERROR** (0x90) I/O-drivrutin
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare
- **FX_CALLER_ERROR** (0x20) Anroparen är inte en tråd

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar den första katalogposten med fullständig information

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

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name:** Pekare till målet för namnet på en katalogpost. Måste vara minst lika stor som FX_MAX_LONG_NAME_LEN.
- **attribut:** Om det inte är null pekar du mot målet för postens attribut som ska placeras. Attributen returneras i bitkartformat med följande möjliga inställningar:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: Om det inte är null pekar du till målet för postens storlek i byte.
- **year**: Om det inte är null pekar du till målet för postens ändringsår.
- **month**: Om det inte är null pekar du till målet för postens ändringsmånad.
- **day**: Om det inte är null pekar du mot målet för postens ändringsdag.
- **hour**: Om det inte är null pekar du mot målet för postens ändringstimmar.
- **minute**: Om det inte är null pekar du mot målet för postens ändringsminut.
- **second**: Om det inte är null pekar du till målet för postens andra ändring.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad första katalogposts find
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen
- **FX_IO_ERROR** (0x90) Drivrutins-I/O
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade
- **FX_FILE _CORRUPT** (0x08) filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltig media
- **FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar information om katalogpost

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

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name:** Pekare till namnet på katalogposten.
- **attribut:** Pekare till målet för attributen.
- **storlek:** Pekare till målet för storleken.
- **year**: Pekare till årets mål.
- **month**: Pekare till målet för månaden.
- **day**: Pekare till dagens mål.
- **hour**: Pekare till målet för timmen.
- **minute**: Pekare till målet för minuten.
- **second**: Pekare till målet för den andra.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad första katalogposts find
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NOT_FOUND** (0x04) Den angivna katalogen hittades inte på mediet
- **FX_IO_ERROR** (0x90) Drivrutins-I/O
- **FX_MEDIA_INVALID** (0x02) Ogiltig media
- **FX_FILE _CORRUPT** (0x08) filen är skadad
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_PTR_ERROR** (0x18) Ogiltig media eller mål pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Rensar den lokala standardsökvägen

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar den tidigare lokala sökvägen som har ställts in för anropstråden.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: Pekare till ett media som öppnats tidigare.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad lokal sökväg rensas.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH har definierats
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar den aktuella lokala sökvägssträngen

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Description

Den här tjänsten returnerar pekaren för den lokala sökvägen för det angivna mediet. Om det inte finns någon lokal sökväg returneras null till anroparen.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **return_path_name:** Pekare till målsträngens pekare för den lokala sökvägssträng som ska lagras.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad lokal sökväg hämta.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande
- **FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare


### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten återställer en tidigare inställd lokal sökväg. Katalogsökpositionen som görs på den här lokala sökvägen återställs också, vilket gör den här rutinen användbar i rekursiva katalogtratter av programmet.

> [!IMPORTANT]
> *Varje lokal sökväg innehåller en lokal sökvägssträng **med FX_MAXIMUM_PATH** storlek, som som standard är 256 tecken. Den här interna sökvägssträngen används inte av FileX och tillhandahålls endast för programmets användning. Om **FX_LOCAL_PATH** ska deklareras som en lokal variabel bör användarna vara försiktig med stacken som växer med storleken på den här strukturen. Användare är välkommen att minska storleken på FX_MAXIMUM_PATH **och** återskapa FileX-bibliotekskällan.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **local_path_ptr:** Pekare till den tidigare inställt lokala sökvägen. Det är mycket viktigt att se till att pekaren verkligen pekar på en tidigare använd och fortfarande intakt lokal sökväg.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad återställning av lokal sökväg.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet för närvarande.
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH definieras.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller lokal sökvägs pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Uppsättningar en trådspecifik lokal sökväg

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Description

Den här tjänsten uppsättningar en trådspecifik sökväg som anges av ***new_path_string** _. När den här rutinen har slutförts har den lokala sökvägsinformationen som lagras i _ *_local_path_ptr_** företräde framför den globala mediesökvägen för alla fil- och katalogåtgärder som utförs av den här tråden. Detta påverkar inte någon annan tråd i systemet 
> [!IMPORTANT]
> *Standardstorleken för den lokala sökvägssträngen är 256 tecken. Det kan ändras genom att ändra **FX_MAXIMUM_PATH** i **fx_api.h** och återskapa hela FileX-biblioteket. Teckensträngens sökväg underhålls för programmet och används inte internt av FileX.*

> [!IMPORTANT]
> *För namn som anges av programmet har FileX stöd för både omsnedstreck ( ) och snedstreck (/) tecken för att avgränsa \\ kataloger, underkataloger och filnamn. FileX använder dock bara omsnedstreckstecknet i sökvägar som returneras till programmet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till tidigare öppnade media.
- **local_path_ptr:** Mål för att lagra den trådspecifika lokala sökvägsinformationen. Adressen för den här strukturen kan anges för den lokala funktionen för sökvägsåterställning i framtiden.
- **new_path_name:** Anger den lokala sökvägen till konfigurationen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad standardkataloguppsättning.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_IMPLEMENTED** (0x22) **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH** (0x0D) Det gick inte att hitta den nya katalogen.
- **FX_NOT_IMPLEMENTED** (0x22)- **FX_NO_LOCAL_PATH har definierats.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller lokal sökvägs pekare.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten hämtar det långa namnet (om det finns) som är associerat med det angivna korta (8,3-format) namnet. Det korta namnet kan vara antingen ett filnamn eller ett katalognamn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **short_name**: Pekare till källans korta namn (8.3-format).
- **long_name:** Pekare till målet för det långa namnet. Om det inte finns något långt namn returneras det korta namnet. Observera att målet för det långa namnet måste vara tillräckligt stort för att innehålla FX_MAX_LONG_NAME_LEN tecken.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Successful long name get
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet
- **FX_IO_ERROR** (0x90) I/O-drivrutin
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare
- **FX_CALLER_ERROR** (0x20) Anroparen är inte en tråd

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten hämtar det långa namnet (om det finns) som är associerat med det angivna korta (8,3-format) namnet. Det korta namnet kan vara antingen ett filnamn eller ett katalognamn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **short_name**: Pekare till källans korta namn (8.3-format).
- **long_name:** Pekare till målet för det långa namnet. Om det inte finns något långt namn returneras det korta namnet. Obs! Målet för det långa namnet måste vara tillräckligt stort för att innehålla **FX_MAX_LONG_NAME_LEN** tecken.
- **long_file_name_buffer_length:** Längden på den långa namnbufferten.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Successful long name get.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta det korta namnet.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Tester för katalog

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Description

Den här tjänsten testar om det angivna namnet är en katalog. I så fall returneras FX_SUCCESS en ny.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **directory_name:** Pekare till namnet på katalogposten.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Det angivna namnet är en katalog.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta katalogposten.
- **FX_NOT_DIRECTORY post** (0x0E) är inte en katalog
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar nästa katalogpost

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Description

Den här tjänsten returnerar nästa postnamn i den aktuella standardkatalogen.

> [!WARNING]
> *Om du använder en icke-lokal sökväg är det också viktigt att förhindra (med en ThreadX-semaphore eller trådprioritetsnivå) andra programtrådar från att ändra den här katalogen medan en katalog-traverserning sker. Annars kan ogiltiga resultat erhållas.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **return_entry_name:** Pekare till mål för nästa postnamn i standardkatalogen. Bufferten som pekar på den här pekaren måste vara tillräckligt stor för att innehålla den maximala storleken för FileX-namn, som definieras **_av FX_MAX_LONG_NAME_LEN_**.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad nästa post
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar nästa katalogpost med fullständig information

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

### <a name="description"></a>Description

Den här tjänsten hämtar nästa postnamn i standardkatalogen och kopierar det till det angivna målet. Den returnerar också fullständig information om posten som anges av de ytterligare indataparametrarna.

> [!WARNING]
> *Det angivna målet måste vara tillräckligt stort för att innehålla det maximala FileX-namnet, enligt definitionen i FX_MAX_LONG_NAME_LEN*...

> [!WARNING]
> *Om du använder en icke-lokal sökväg är det viktigt att förhindra andra programtrådar från att ändra den här katalogen medan en katalog-traverserning äger rum (med en ThreadX-semaphore, mutex eller prioritetsnivåändring). Annars kan ogiltiga resultat erhållas.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **directory_name:** Pekare till målet för namnet på en katalogpost. Måste vara minst lika stor som **FX_MAX_LONG_NAME_LEN**.
- **attribut:** Om det inte är null pekar du mot målet för postens attribut som ska placeras. Attributen returneras i bitkartformat med följande möjliga inställningar:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **storlek:** Om det inte är null pekar du till målet för postens storlek i byte.
- **month**: Om det inte är null pekar du mot målet för postens ändringsmånad.
- **year**: Om det inte är null pekar du mot målet för postens ändringsår.
- **day**: Om det inte är null pekar du mot målet för postens ändringsdag.
- **hour**: Om det inte är null pekar du mot målet för postens ändringstimmar.
- **minute**: Om det inte är null pekar du mot målet för postens ändringsminut.
- **second**: Om det inte är null pekar du till målet för postens andra ändring.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Nästa katalogpost söks.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare eller alla indataparametrar är NULL.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Byter namn på katalogen

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Description

Den här tjänsten ändrar katalognamnet till det angivna nya katalognamnet. Namnbyte görs också i förhållande till den angivna sökvägen eller standardsökvägen. Om en sökväg anges i det nya katalognamnet flyttas den omdöpta katalogen effektivt till den angivna sökvägen. Om ingen sökväg anges placeras den omdöpta katalogen i den aktuella standardsökvägen.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **old_directory_name**: Pekare till aktuellt katalognamn.
- **new_directory_name**: Pekare till nytt katalognamn.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad katalogbyte.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta katalogposten.
- **FX_NOT_DIRECTORY** (0x0E) Posten är inte en katalog.
- **FX_INVALID_NAME** (0x0C) Nytt katalognamn är ogiltigt.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i den här katalogen.
- **FX_INVALID_PATH** (0x0D) Ogiltig sökväg med katalognamnet.
- **FX_ALREADY_CREATED** (0x0B) Angiven katalog har redan skapats.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar ett kort namn från ett långt namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det korta (8.3-format) namnet som är associerat med det angivna långa namnet. Det långa namnet kan vara antingen ett filnamn eller ett katalognamn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **long_name:** Pekare till källans långa namn.
- **short_name**: Pekare till målets kortnamn (8.3-format). Observera att målet för det korta namnet måste vara tillräckligt stort för att innehålla 14 tecken.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Ett lyckat kortnamn get.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta det långa namnet.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar ett kort namn från ett långt namn

### <a name="prototype"></a>Prototyp

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Description

Den här tjänsten hämtar det korta (8.3-format) namnet som är associerat med det angivna långa namnet. Det långa namnet kan vara antingen ett filnamn eller ett katalognamn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **long_name:** Pekare till källans långa namn.
- **short_name**: Pekare till målets kortnamn (8.3-format). Obs! Målet för det korta namnet måste vara tillräckligt stort för att innehålla 14 tecken.
- **short_file_name_length:** Längden på den korta namnbufferten.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Ett lyckat kortnamn get.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta det långa namnet.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Aktiverar den feltoleranta tjänsten

### <a name="prototype"></a>Prototyp

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Description

Den här tjänsten aktiverar den feltoleranta modulen. Vid start identifierar den feltoleranta modulen huruvida filsystemet är under FileX-feltolerant skydd eller inte. Om den inte är det hittar tjänsten tillgängliga sektorer i filsystemet för att lagra loggar på filsystemtransaktioner. Om filsystemet är under FileX-feltolerant skydd tillämpar det loggarna på filsystemet för att upprätthålla dess integritet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **memory_ptr:** Pekare till ett minnesblock som används av den feltoleranta modulen som ett minne som är försnåe.
- **memory_size:** Storleken på det scratch-minnet. För att feltoleranta ska fungera korrekt ska den scratch-minnesstorleken vara minst 3072 byte, och den måste vara flera av sektorstorleken.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Feltolerans har aktiverats.
- **FX_NOT_ENOUGH_MEMORY** (0x91) för liten.
- **FX_BOOT_ERROR** (0x01) Startsektorfel.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_NO_MORE_ENTRIES** (0x0F) Inget mer ledigt kluster tillgängligt.
- **FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_SECTOR_INVALID** (0x89) sektor är ogiltig
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

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
### <a name="description"></a>Description

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX fastställer antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa helt kluster.

Om du vill allokera mer än 4 GB utrymme ska programmet använda *tjänsten fx_file_extended_allocate*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **size**: Antal byte som ska allokeras för filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filallokering.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_FAT_READ_ERROR** (0x03) Det gick inte att läsa FAT-posten.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_NO_MORE_ENTRIES** (0x0F) Inget mer ledigt kluster tillgängligt.
- **FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_SECTOR_INVALID** (0x89) sektor är ogiltig
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0x18) Ogiltig filpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
- fx_file_close– fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open– fx_file_read
- fx_file_relative_seek
- fx_file_rename– fx_file_seek
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
### <a name="description"></a>Description

Den här tjänsten läser filens attribut från det angivna mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **file_name:** Pekare till namnet på den begärda filen (katalogsökvägen är valfri).
- **attributes_ptr:** Pekare till målet för filens attribut som ska placeras. Filattributen returneras i ett bitkartformat med följande möjliga inställningar:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad attributläsning.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Den angivna filen hittades inte på mediet.
- **FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller attribut pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
- fx_file_close– fx_file_create
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

Anger filattribut

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Description

Den här tjänsten anger filens attribut till de som anges av anroparen.

> [!WARNING]
> *Programmet kan bara ändra en delmängd av filens attribut med den här tjänsten. Om du försöker ange ytterligare attribut resulterar det i ett fel.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **file_name:** Pekare till namnet på den begärda filen** (katalogsökvägen är valfri).
- **attribut:** De nya attributen för filen. De giltiga filattributen definieras på följande sätt:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad attributuppsättning.
- **FX_ACCESS_ERROR** (0x06) Filen är öppen och kan inte ha sina attribut inställda.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler poster i FAT-tabellen eller exFAT-klusterkartan.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_NOT_FOUND** (0x04) Den angivna filen hittades inte på mediet.
- **FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.
- **FX_SECTOR_INVALID** (0x89) sektor är ogiltig
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_INVALID_ATTR** (0x19) Ogiltiga attribut har valts.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Bästa möjliga resultat för att allokera utrymme för en fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Description

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa helt kluster. Om det inte finns tillräckligt många kluster i följd tillgängliga på mediet länkar den här tjänsten det största tillgängliga blocket med kluster i följd till filen. Mängden utrymme som faktiskt allokerats till filen returneras till anroparen.

Om du vill allokera mer än 4 GB utrymme ska programmet använda tjänsten *fx_file_extended_best_effort_allocate*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **size**: Antal byte som ska allokeras för filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filallokering med bästa resultat.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt många tillgängliga kluster.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare eller mål.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten stänger den angivna filen. Om filen var öppen för skrivning och om den ändrades slutför den här tjänsten filändringsprocessen genom att uppdatera dess katalogpost med den nya storleken och systemets aktuella tid och datum.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckades.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller attribut pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten skapar den angivna filen i standardkatalogen eller i den katalogsökväg som medföljer filnamnet.

> [!WARNING]
> *Den här tjänsten skapar en fil med ingen längd, dvs. inga kluster allokerade. Allokering sker automatiskt vid efterföljande fil skrivningar eller kan göras i förväg med tjänsten fx_file_allocate eller fx_file_extended_allocate utrymme över 4 GB).*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **file_name:** Pekare till namnet på filen som ska skapas (katalogsökvägen är valfri).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckades fil skapas.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) Den angivna filen har redan skapats.
- **FX_NO_MORE_SPACE** (0x0A) Det finns antingen inga fler poster i rotkatalogen eller så finns det inga fler kluster tillgängliga.
- **FX_INVALID_PATH** (0x0D) Ogiltig sökväg medföljer filnamnet.
- **FX_INVALID_NAME** (0x0C) är ogiltigt.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_MEDIA_INVALID** (0x02)Ogiltigt medium.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.
- **FX_PTR_ERROR** (0x18) Ogiltig media- eller filnamnspekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="sets-file-date-and-time"></a>Anger filens datum och tid

Ange fildatum och -tid

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
### <a name="description"></a>Description

Den här tjänsten anger datum och tid för den angivna filen.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **file_name**: Pekare till namnet på filen.
- **year**: Värdet för året (inklusive 1980–2107).
- **month**: Värdet för månad (inklusive 1–12).
- **day**: Värdet för dagen (inklusive 1–31).
- **hour**: Timvärde (inklusive 0–23).
- **minute**: Minutvärdet (inklusive 0–59).
- **second**: Värdet för sekund (inklusive 0–59).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Datum/tid har angetts.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Hittades inte.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller namn pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.
- **FX_INVALID_YEAR** (0x12) År är ogiltigt.
- **FX_INVALID_MONTH** (0x13) Månad är ogiltig.
- **FX_INVALID_DAY** (0x14) Day är ogiltig.
- **FX_INVALID_HOUR** (0x15) Timme är ogiltig.
- **FX_INVALID_MINUTE** (0x16) Minut är ogiltig.
- **FX_INVALID_SECOND** (0x17) Sekund är ogiltigt.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Filborttagning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Description

Den här tjänsten tar bort den angivna filen.


### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **file_name:** Pekare till namnet på filen som ska tas bort (katalogsökvägen är valfri).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Borttagningen lyckades.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.
- **FX_NOT_A_FILE** (0x05) Det angivna filnamnet var en katalog eller volym.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är öppen för tillfället.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX fastställer antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa helt kluster.

Den här tjänsten är utformad för exFAT. Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan allokera utrymme i förväg över 4 GB. 

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **size**: Antal byte som ska allokeras för filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filallokering.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Bästa möjliga tid för att allokera utrymme för en fil

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Description

Den här tjänsten allokerar och länkar ett eller flera sammanhängande kluster till slutet av den angivna filen. FileX avgör antalet kluster som krävs genom att dividera den begärda storleken med antalet byte per kluster. Resultatet avrundas sedan uppåt till nästa helt kluster. Om det inte finns tillräckligt många kluster i följd tillgängliga på mediet länkar den här tjänsten det största tillgängliga blocket med kluster i följd till filen. Mängden utrymme som faktiskt allokeras till filen returneras till anroparen.

Den här tjänsten är utformad för exFAT. Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan allokera utrymme i förväg över 4 GB. 

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **storlek:** Antal byte som ska allokeras för filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filallokering.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_NO_MORE_SPACE** (0x0A) Media som är associerade med den här filen har inte tillräckligt med tillgängliga kluster.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Positioner till en relativ byteförskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Description

Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna relativa byteförskjutningen. Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.

Den här tjänsten är utformad för exFAT. Parametern *byte_offset* tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan flytta läs-/skrivpekaren över 4 GB.

> [!IMPORTANT]
> *Om sökåtgärden försöker att söka förbi slutet av filen placeras filens läs-/skriv pekare i slutet av filen. Om sökåtgärden försöker placera sig förbi början av filen placeras däremot filens läs-/skriv pekare i början av filen.*

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **byte_offset:** Önskad relativ byteförskjutning i filen.
- **seek_from:** Riktningen och platsen för var du ska utföra det relativa söket. Giltiga sökalternativ definieras på följande sätt:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03) FX_SEEK_BEGIN har angetts utförs sökåtgärden från början av filen. Om FX_SEEK_END har angetts utförs sökåtgärden bakåt från slutet av filen. Om FX_SEEK_FORWARD har angetts utförs sökåtgärden framåt från den aktuella filpositionen. Om FX_SEEK_BACK har angetts utförs sökåtgärden bakåt från den aktuella filpositionen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad relativ filsökning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig filpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Positioner för byteförskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Description

Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna byteförskjutningen. Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.

Den här tjänsten är utformad för exFAT. Parametern *byte_offset* ett 64-bitars heltalsvärde, vilket gör att anroparen kan flytta läs-/skriv pekaren över 4 GB.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **byte_offset:** Önskad byteförskjutning i filen. Värdet noll placerar pekaren för läsning/skrivning i början av filen, medan ett värde som är större än filens storlek placerar pekaren för läsning/skrivning i slutet av filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filsökning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
- fx_file_open– fx_file_read
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

Trunkerar filen

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Description

Den här tjänsten trunkerar storleken på filen till den angivna storleken. Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting. Inget av de mediekluster som är associerade med filen släpps.

> [!WARNING]
> *Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Att trunkera en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*

Den här tjänsten är utformad för exFAT. Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta längre än 4 GB. 

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **size**: Ny filstorlek. Byte som har gått förbi den nya filstorleken tas bort.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad fil trunkering.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddad.
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Trunkerar fil- och versionskluster

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Description

Den här tjänsten trunkerar storleken på filen till den angivna storleken. Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting. Till skillnad ***fx_file_extended_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.

> [!WARNING]
> *Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*

Den här tjänsten är utformad för exFAT. Storleksparametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta utanför 4 GB intervall. 

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **storlek:** Ny filstorlek. Byte som har gått förbi den nya filstorleken tas bort.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad fil trunkering.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_PTR_ERROR** (0x18) Ogiltig filpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Öppnar filen

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Description

Den här tjänsten öppnar den angivna filen för läsning eller skrivning. En fil kan öppnas för läsning flera gånger, medan en fil bara kan öppnas för skrivning en gång tills skrivaren stänger filen.

> [!IMPORTANT]
> *Var försiktig om en fil är öppen samtidigt för läsning och skrivning. Filskrivning som utförs när en fil öppnas samtidigt för läsning kanske inte kan ses av läsaren, såvida inte läsaren stänger och öppnar filen igen för läsning. På samma sätt bör filskrivaren vara försiktig när du använder tjänster för trunkering av filer. Om en fil trunkeras av skrivaren kan läsare av samma fil returnera ogiltiga data.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **file_ptr:** Pekare till filkontrollblocket.
- **file_name:** Pekare till namnet på filen som ska öppnas (katalogsökvägen är valfri).
- **open_type:** Typ av fil som är öppen. Giltiga alternativ för öppen typ är:
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

Att öppna filer med FX_OPEN_FOR_READ och FX_OPEN_FOR_READ_FAST liknar följande:

- FX_OPEN_FOR_READ verifiering att den länkade listan över kluster som utgör filen är intakt och FX_OPEN_FOR_READ_FAST utför inte den här verifieringen, vilket gör den snabbare.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Filen lyckades öppen.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.
- **FX_NOT_A_FILE** (0x05) Det angivna filnamnet var en katalog eller volym.
- **FX_FILE_CORRUPT** (0x08) Angiven fil är skadad och det gick inte att öppna filen.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är redan öppen eller öppen typ är ogiltig.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_MEDIA_INVALID** (0x02) Ogiltigt medium.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddat.
- **FX_PTR_ERROR** (0x18) Ogiltig media- eller fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
- fx_file_close– fx_file_create
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
### <a name="description"></a>Description

Den här tjänsten läser byte från filen och lagrar dem i den angivna bufferten. När läsningen är klar justeras filens interna läs pekare så att den pekar på nästa byte i filen. Om det finns färre byte kvar i begäran lagras bara återstående byte i bufferten. I vilket fall som helst returneras det totala antalet byte som placerats i bufferten till anroparen.

> [!WARNING]
> *Programmet måste se till att den angivna bufferten kan lagra det angivna antalet begärda byte.*

> [!WARNING]
> *Snabbare prestanda uppnås om målbufferten ligger på en lång ordgräns och den begärda storleken är jämnt delbar efter sizeof(**ULONG).***

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **buffer_ptr:** Pekare till målbufferten för läsningen.
- **request_size:** Maximalt antal byte som ska läsas.
- **actual_size:** Pekare till variabeln för det faktiska antalet byte som lästs in i den angivna bufferten.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filläsning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_FILE_CORRUPT** (0x08) Angiven fil är skadad och läsningen misslyckades.
- **FX_END_OF_FILE** (0x09) Slutet av filen har nåtts.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_PTR_ERROR** (0x18) Ogiltig fil- eller buffertpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Positioner till en relativ byteförskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Description

Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna relativa byteförskjutningen. Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.

> [!IMPORTANT]
> *Om sökåtgärden försöker att söka förbi slutet av filen placeras filens läs-/skriv pekare i slutet av filen. Om sökåtgärden försöker placera sig förbi början av filen placeras däremot filens läs-/skriv pekare i början av filen.*

Om du vill söka med ett förskjutningsvärde över 4 GB ska programmet använda tjänsten *fx_file_extended_relative_seek*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **byte_offset:** Önskad relativ byteförskjutning i filen.
- **seek_from:** Riktningen och platsen för var du ska utföra det relativa söket. Giltiga sökalternativ definieras på följande sätt:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

Om FX_SEEK_BEGIN har angetts utförs sökåtgärden från början av filen. Om FX_SEEK_END har angetts utförs sökåtgärden bakåt från slutet av filen. Om FX_SEEK_FORWARD har angetts utförs sökåtgärden framåt från den aktuella filpositionen. Om FX_SEEK_BACK har angetts utförs sökåtgärden bakåt från den aktuella filpositionen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad relativ filsökning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_PTR_ERROR** (0x18) Ogiltig filpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten ändrar namnet på filen som anges av *old_file_name*. Namnbyte görs också i förhållande till den angivna sökvägen eller standardsökvägen. Om en sökväg anges i det nya filnamnet flyttas den omdöpta filen effektivt till den angivna sökvägen. Om ingen sökväg anges placeras den omdöpta filen i den aktuella standardsökvägen.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett mediakontrollblock.
- **old_file_name:** Pekare till namnet på filen som du vill byta namn på (katalogsökvägen är valfri).
- **new_file_name**: Pekare till det nya filnamnet. Katalogsökvägen tillåts inte.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Namnbyte av fil.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Det gick inte att hitta den angivna filen.
- **FX_NOT_A_FILE** (0x05) Angiven fil är en katalog.
- **FX_ACCESS_ERROR** (0x06) Den angivna filen är redan öppen.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_INVALID_NAME** (0x0C) Angivet nytt filnamn är inte ett giltigt filnamn.
- **FX_INVALID_PATH** (0x0D) Sökvägen är ogiltig.
- **FX_ALREADY_CREATED** (0x0B) Det nya filnamnet används.
- **FX_MEDIA_INVALID** (0x02) Media är ogiltigt.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Positioner för byteförskjutning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Description

Den här tjänsten placerar den interna filläsnings-/skriv pekaren mot den angivna byteförskjutningen. Alla efterföljande filläsnings- eller skrivbegäran börjar på den här platsen i filen.

Om du vill söka med ett förskjutningsvärde över 4 GB ska programmet använda *tjänsten fx_file_extended_seek*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **byte_offset:** Önskad byteförskjutning i filen. Värdet noll placerar pekaren för läsning/skrivning i början av filen, medan ett värde som är större än filens storlek placerar pekaren för läsning/skrivning i slutet av filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filsökning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Trunkerar filen

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Description

Den här tjänsten trunkerar storleken på filen till den angivna storleken. Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting. Inget av de mediekluster som är associerade med filen släpps.

> [!WARNING]
> *Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*

För att kunna arbeta mer än 4 GB ska programmet använda tjänsten *fx_file_extended_truncate*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **storlek:** Ny filstorlek. Byte som har gått förbi den nya filstorleken tas bort.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad fil trunkering.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden
- **FX_PTR_ERROR** (0x18) Ogiltig fil pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Trunkerar fil- och versionskluster

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Description

Den här tjänsten trunkerar storleken på filen till den angivna storleken. Om den angivna storleken är större än den faktiska filstorleken gör den här tjänsten ingenting. Till skillnad ***fx_file_truncate*** tjänsten släpper den här tjänsten eventuella oanvända kluster.

> [!WARNING]
> *Var försiktig när du trunkerar filer som också kan vara öppna samtidigt för läsning. Trunkering av en fil som också öppnas för läsning kan resultera i läsning av ogiltiga data.*

För att kunna arbeta mer än 4 GB ska programmet använda tjänsten *fx_file_extended_truncate_release*.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till en fil som öppnats tidigare.
- **storlek:** Ny filstorlek. Byte som har gått förbi den nya filstorleken tas bort.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad fil trunkering.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen för närvarande.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Underliggande media är skrivskyddat.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme för att slutföra åtgärden.
- **FX_PTR_ERROR** (0x18) Ogiltig filpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten skriver byte från den angivna bufferten med början vid filens aktuella position. När skriven är klar justeras filens interna läs pekare så att den pekar på nästa byte i filen.

> [!WARNING]
> *Snabbare prestanda uppnås om källbufferten finns på en lång ordgräns och den begärda storleken är jämnt delbar efter sizeof(**ULONG).***

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **buffer_ptr:** Pekare till källbufferten för skrivning.
- **size**: Antal byte som ska skrivas.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad filskrivning.
- **FX_NOT_OPEN** (0x07) Angiven fil är inte öppen.
- **FX_ACCESS_ERROR** (0x06) Angiven fil är inte öppen för skrivning.
- **FX_NO_MORE_SPACE** (0x0A) Det finns inte mer utrymme tillgängligt på mediet för att utföra den här skriven.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_WRITE_PROTECT** (0x23) Det angivna mediet är skrivskyddat.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-posten.
- **FX_NO_MORE_ENTRIES** (0x0F) Inga fler FAT-poster.
- **FX_PTR_ERROR** (0x18) Ogiltig fil eller buffertpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger funktionen för att meddela om filskrivning

### <a name="prototype"></a>Prototyp

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Description

Den här tjänsten installerar återanropsfunktionen som anropas efter en lyckad filskrivningsåtgärd.

### <a name="input-parameters"></a>Indataparametrar

- **file_ptr:** Pekare till filkontrollblocket.
- **file_write_notify:** Återanropsfunktionen för filskrivning som ska installeras. Om du ställer in återanropsfunktionen på NULL inaktiveras återanropsfunktionen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Återanropsfunktionen har installerats.
- **FX_PTR_ERROR** (0x18) file_ptr är NULL.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Avbryter medieaktiviteter

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

Den här tjänsten avbryter alla aktuella aktiviteter som är associerade med mediet, inklusive att stänga alla öppna filer, skicka en begäran om avbrott till den associerade drivrutinen och placera mediet i ett avbrutna tillstånd. Den här tjänsten anropas vanligtvis när I/O-fel identifieras.

> [!WARNING]
> *Mediet måste öppnas igen för att det ska kunna användas igen när en avbrottsåtgärd har utförts.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medie abort.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Ogiltigförklarar cache för logisk sektor

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Description

Den här tjänsten rensar alla felaktiga sektorer i cacheminnet och ogiltigförklarar sedan hela cacheminnet för den logiska sektorn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad mediecache ogiltigförklaras.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller scratch pointer.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Söker efter fel i media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Description

Den här tjänsten söker efter grundläggande strukturella fel på de angivna mediet, inklusive fil-/kataloglänkning, ogiltiga FAT-kedjor och förlorade kluster. Den här tjänsten ger också möjlighet att korrigera identifierade fel.

Tjänsten fx_media_check minne för djupanalys av kataloger och filer på mediet. Mer specifikt måste det scratch-minne som tillhandahålls till mediakontrolltjänsten vara tillräckligt stort för att rymma flera katalogposter, en datastruktur för att "stapla" den aktuella katalogpostpositionen innan du anger i underkataloger och slutligen den logiska FAT-bitmappningen. Det scratch-minnet ska vara minst 512–1 024 byte plus minne för den logiska FAT-bitkartan, vilket kräver lika många bitar som det finns kluster på mediet. Till exempel skulle en enhet med 8 000 kluster kräva 1 000 byte för att representera och därmed kräva en total scratch area på en beställning på 2 048 byte.

> [!WARNING]
> *Den här tjänsten bör bara anropas omedelbart efter fx_media_open och utan någon annan filsystemaktivitet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **scratch_memory_ptr:** Pekare till början av det scratch-minnet.
- **scratch_memory_size:** Storleken på det scratch-minnet i byte.
- **error_correction_option:** Bitar för felkorrigeringsalternativ när biten har angetts utförs felkorrigering. Bitarna för felkorrigeringsalternativet definieras på följande sätt:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) Helt enkelt ELLER ihop de alternativ för felkorrigering som krävs. Om ingen felkorrigering krävs ska värdet 0 anges.
- **errors_detected_ptr:** Mål för felidentifierings bitar enligt definitionen nedan:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad mediekontroll visar du de fel som identifierats för mer information.
- **FX_ACCESS_ERROR** (0x06) Det går inte att kontrollera med öppna filer.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NO_MORE_SPACE** (0x0A) Inget mer utrymme på mediet.
- **FX_NOT_ENOUGH_MEMORY** (0x91) Det angivna minnet är inte tillräckligt stort.
- **FX_ERROR_NOT_FIXED** (0x93) Fel i FAT32-rotkatalogen som inte kunde åtgärdas.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_SECTOR_INVALID** (0x89) Sektor är ogiltig.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller scratch pointer.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.


### <a name="allowed-from"></a>Tillåts från

Trådar

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

Stänger media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

Den här tjänsten stänger det angivna mediet. När mediet stängs stängs alla öppna filer och eventuella återstående buffertar rensas till det fysiska mediet.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad media stäng.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig mediepekare.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger funktionen media close notify

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Description

Den här tjänsten anger en avanropsfunktion som anropas när ett medium har stängts.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **media_close_notify: Media** close notify callback function to be installed. Genom att skicka NULL som återanropsfunktion inaktiveras återanropet av media close.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Återanropsfunktionen har installerats.
- **FX_PTR_ERROR** (0x18) media_ptr är NULL.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Formaterar media

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
### <a name="description"></a>Description

Den här tjänsten formaterar det angivna mediet på ett exFAT-kompatibelt sätt baserat på de angivna parametrarna. Den här tjänsten måste anropas innan mediet öppnas.

> [!WARNING]
> *Om du formaterar ett redan formaterat medium raderas effektivt alla filer och kataloger på mediet.*

> [!IMPORTANT]
> *ExFAT-volymstorleken ska matcha storleken på partitionen (om det finns en MBR- eller GPT-layout) eller storleken på hela enheten om det inte finns någon partitionslayout (ingen MBR eller GPT). Det finns en begränsning för Windows som exFAT Disk inte kommer att recoginzed om formateras med vissa värden för totala sektorer som är mindre än medelvärden sektorer*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock. Detta används endast för att tillhandahålla viss grundläggande information som krävs för att drivrutinen ska fungera.
- **driver**: Pekare till I/O-drivrutinen för det här mediet. Detta är vanligtvis samma drivrutin som angavs för efterföljande fx_media_open anropet.
- **driver_info_ptr:** Pekare till valfri information som I/O-drivrutinen kan använda.
- **memory_ptr:** Pekare till arbetsminnet för mediet. memory_size Anger storleken på arbetsmediaminnet. Storleken måste vara minst lika stor som mediets sektorstorlek.
- **volume_name:** Pekare till volymnamnssträngen, som är högst 11 tecken.
- **number_of_fats:** Antal vanliga frågor och svar på mediet. Den aktuella implementeringen stöder en FAT på mediet.
- **hidden_sectors:** Antalet sektorer som är dolda före det här mediets startsektor. Detta är vanligt när det finns flera partitioner.
- **total_sectors:** Totalt antal sektorer i mediet.
- **bytes_per_sector:** Antal byte per sektor, vilket vanligtvis är 512. FileX kräver att detta är en multipel av 32.
- **sectors_per_cluster:** Antalet sektorer i varje kluster. Klustret är den minsta allokeringsenheten i ett FAT-filsystem.
- **volumne_serial_number:** Serienummer som ska användas för den här volymen.
- **boundary_unit:** Justeringsstorlek för fysiskt dataområde i antal sektorer.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Medieformatet lyckades.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig media, drivrutin eller minnespekare.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Returnerar tillgängligt medieutrymme

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Description

Den här tjänsten returnerar antalet tillgängliga byte på mediet.

Den här tjänsten är utformad för exFAT. Pekaren till *available_bytes* parametern tar ett 64-bitars heltalsvärde, vilket gör att anroparen kan arbeta med medier utanför 4 GB intervall.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: Pekare till ett media som öppnats tidigare.
- **available_bytes_ptr:** Tillgängliga byte kvar på mediet.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Tillgängligt utrymme på mediet har hämtats.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare eller tillgänglig byte-pekare är NULL.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Rensar data till fysiska media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Description

Den här tjänsten rensar alla cachelagrade sektorer och katalogposter för ändrade filer till det fysiska mediet.

> [!WARNING]
> *Den här rutinen kan anropas regelbundet av programmet för att minska risken för skadade filer och/eller dataförlust i händelse av plötslig strömförlust på målet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medieström.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_FILE_CORRUPT**    (0x08) Filen är skadad.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Formaterar media

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
### <a name="description"></a>Description

Den här tjänsten formaterar det angivna mediet på ett FAT 12/16/32-kompatibelt sätt baserat på de angivna parametrarna. Den här tjänsten måste anropas innan mediet öppnas.

> [!WARNING]
> *Om du formaterar ett redan formaterat medium raderas effektivt alla filer och kataloger på mediet.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock. Detta används endast för att tillhandahålla viss grundläggande information som krävs för att drivrutinen ska fungera.
- **driver**: Pekare till I/O-drivrutinen för det här mediet. Detta är vanligtvis samma drivrutin som tillhandahålls till efterföljande fx_media_open anrop.
- **driver_info_ptr:** Pekare till valfri information som I/O-drivrutinen kan använda.
- **memory_ptr:** Pekare till arbetsminnet för mediet.
- **memory_size:** Anger storleken på arbetsmediaminnet. Storleken måste vara minst lika stor som mediets sektorstorlek.
- **volume_name:** Pekare till volymnamnssträngen, som är högst 11 tecken.
- **number_of_fats:** Antal vanliga frågor och svar i mediet. Det minimala värdet är 1 för primärt FAT. Värden som är större än 1 resulterar i att ytterligare FAT-kopior underhålls vid körning.
- **directory_entries:** Antal katalogposter i rotkatalogen.
- **hidden_sectors:** Antalet sektorer som är dolda före det här mediets startsektor. Detta är vanligt när det finns flera partitioner.
- **total_sectors:** Totalt antal sektorer i mediet.
- **bytes_per_sector:** Antal byte per sektor, vilket vanligtvis är 512. FileX kräver att detta är en multipel av 32.
- **sectors_per_cluster:** Antalet sektorer i varje kluster. Klustret är den minsta allokeringsenheten i ett FAT-filsystem.
- **krona:** Antal fysiska huvuden.
- **sectors_per_track:** Antal sektorer per spår.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Medieformatet lyckades.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_PTR_ERROR** (0x18) Ogiltig media-, drivrutins- eller minnespekare.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Öppnar media för filåtkomst

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
### <a name="description"></a>Description

Den här tjänsten öppnar ett medium för filåtkomst med hjälp av den angivna I/O-drivrutinen.

> [!WARNING]
> *Det minne som tillhandahålls till den här tjänsten används för att implementera en intern logisk sektorcache, och ju mer minne som tillhandahålls desto mer fysisk I/O minskas. FileX kräver en cache med minst en logisk sektor (byte per sektor av mediet).*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **media_name:** Pekare till mediets namn.
- **media_driver:** Pekare till I/O-drivrutin för det här mediet. I/O-drivrutinen måste uppfylla kraven för FileX-drivrutinen som definieras i kapitel 5.
- **driver_info_ptr:** Pekare till valfri information som den angivna I/O-drivrutinen kan använda.
- **memory_ptr:** Pekare till arbetsminnet för mediet.
- **memory_size:** Anger storleken på arbetsmediaminnet. Storleken måste vara lika stor som mediets sektorstorlek (vanligtvis 512 byte).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad media är öppen.
- **FX_BOOT_ERROR** (0x01) Fel vid läsning av mediets startsektor.
- **FX_MEDIA_INVALID** (0x02) Det angivna mediets startsektor är skadad eller ogiltig. Dessutom används den här returkoden för att ange att antingen cachestorleken för den logiska sektorn eller FAT-poststorleken inte är 2.
- **FX_FAT_READ_ERROR** (0x03) Fel vid läsning av mediet FAT.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger media open notify-funktionen

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Description

Den här tjänsten anger en avanropsfunktion som anropas när ett medium har öppnats.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **media_open_notify:** Funktionen Media open notify callback som ska installeras. Om null-värdet används som återanropsfunktion inaktiveras återanropet från mediet.

### <a name="return-values"></a>Returvärden


- **FX_SUCCESS** (0x00) Successfuly installerade återanropsfunktionen.
- **FX_PTR_ERROR** (0x18) media_ptr är NULL.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten läser en logisk sektor från mediet och placerar den i den angivna bufferten.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett media som öppnats tidigare.
- **logical_sector:** Logisk sektor att läsa.
- **buffer_ptr:** Pekare till målet för den logiska sektorn läsa.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medieläsning.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_PTR_ERROR** (0x18) Ogiltig media eller buffert pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Returnerar tillgängligt medieutrymme

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Description

Den här tjänsten returnerar antalet tillgängliga byte på mediet.

Om du vill arbeta med media som är större än 4 GB ska programmet använda tjänsten *fx_media_extended_space_available*.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till ett media som öppnats tidigare.
- **available_bytes_ptr:** Tillgängliga byte kvar på mediet.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Tillgängligt utrymme på mediet har returnerats.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare eller tillgänglig byte-pekare är NULL.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar medievolymens namn

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Description

Den här tjänsten hämtar volymnamnet för det media som öppnades tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **volume_name:** Pekare till mål för volymnamn. Observera att målet måste vara minst tillräckligt stort för att innehålla 12 tecken.
- **volume_source:** Anger var namnet ska hämtas, antingen från startsektorn eller rotkatalogen. Giltiga värden för den här parametern är:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medievolym get.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04)-volymen hittades inte.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig media- eller volymmål pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar medievolymens namn på tidigare öppnade media

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Description

Den här tjänsten hämtar volymnamnet för det media som öppnades tidigare.

> [!IMPORTANT]
> Den här tjänsten är identisk med ***fx_media_volume_get()** _ förutom att anroparen skickar storleken på *bufferten* _ volume_name * .

### <a name="input-parameters"></a>Indataparametrar


- **media_ptr:** Pekare till mediakontrollblock.
- **volume_name:** Pekare till mål för volymnamn. Observera att målet måste vara minst tillräckligt stort för att innehålla 12 tecken.
- **volume_name_buffer_length:** Storleken på volume_name bufferten.
- **volume_source:** Anger var namnet ska hämtas, antingen från startsektorn eller rotkatalogen. Giltiga värden för den här parametern är:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medievolym get.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04)-volymen hittades inte.
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_PTR_ERROR** (0x18) Ogiltig media- eller volymmål pekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger medievolymnamn

### <a name="prototype"></a>Prototyp

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Description

Den här tjänsten anger volymnamnet för det media som öppnades tidigare.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **volume_name:** Pekare till volymnamnet.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medievolymuppsättning.
- **FX_INVALID_NAME** (0x0C) Volume_name är ogiltig.
- **FX_MEDIA_INVALID** (0x02) Det går inte att ange volymnamnet.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltig media- eller volymnamnspekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten skriver den angivna bufferten till den angivna logiska sektorn.

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr**: Pekare till ett media som öppnats tidigare.
- **logical_sector:** Logisk sektor att skriva.
- **buffer_ptr:** Pekare till källan för den logiska sektorskrivningen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad medieskrivning.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltig medie pekare.
- **FX_CALLER_ERROR**    (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar filsystemdatum

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Description

Den här tjänsten returnerar det aktuella systemdatumet.

### <a name="input-parameters"></a>Indataparametrar

- **year**: Pekare till mål för år.
- **month**: Pekare till mål för månad.
- **day**: Pekare till mål för dagen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad datumhämtning.
- **FX_PTR_ERROR** (0x18) En eller flera av indataparametrarna är NULL.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger systemdatum

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Description

Den här tjänsten anger systemdatumet som angivet.

> [!WARNING]
> *Den här tjänsten ska anropas strax efter **fx_system_initialize för** att ange det första systemdatumet. Som standard är systemdatumet den senaste allmänna FileX-versionen.*

### <a name="input-parameters"></a>Indataparametrar

- **year**: Nytt år. Det giltiga intervallet är från 1980 till och med år 2107.
- **month**: Ny månad. Det giltiga intervallet är mellan 1 och 12.
- **day**: Ny dag. Det giltiga intervallet är mellan 1 och 31, beroende på månad och skottår.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Inställningen Lyckades.
- **FX_INVALID_YEAR** (0x12) Ogiltigt år angivet.
- **FX_INVALID_MONTH** (0x13) Ogiltig månad har angetts.
- **FX_INVALID_DAY** (0x14) Ogiltig dag har angetts.

### <a name="allowed-from"></a>Tillåts från

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

### <a name="description"></a>Description

Den här tjänsten initierar alla större FileX-datastrukturer. Det bör anropas antingen ***i tx_application_define*** eller möjligen från en initieringstråd och måste anropas innan du använder någon annan FileX-tjänst.

> [!WARNING]
> *När det här anropet initieras bör programmet anropa fx_system_date_set _ och _ fx_system_time_set * för att börja med ett *korrekt systemdatum och en korrekt tid.*

### <a name="input-parameters"></a>Indataparametrar

Inget

### <a name="return-values"></a>Returvärden

Inga.

### <a name="allowed-from"></a>Tillåts från

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

Hämtar aktuell systemtid

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Description

Den här tjänsten hämtar den aktuella systemtiden.

### <a name="input-parameters"></a>Indataparametrar

- **hour**: Pekare till mål för timme.
- **minute**: Pekare till mål för minut.
- **second**: Pekare till mål för andra.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad systemtidshämtning.
- **FX_PTR_ERROR** (0x18) En eller flera av indataparametrarna

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Anger aktuell systemtid

### <a name="prototype"></a>Prototyp

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Description

Den här tjänsten anger den aktuella systemtiden till den som anges av indataparametrarna.

> [!WARNING]
> *Den här tjänsten ska anropas strax efter **fx_system_initialize för** att ange den första systemtiden. Som standard är systemtiden 0:0:0.*

### <a name="input-parameters"></a>Indataparametrar

- **hour**: Ny timme (0–23).
- **minute**: Ny minut (0–59).
- **second**: Ny sekund (0–59).

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad systemtidshämtning.
- **FX_INVALID_HOUR**    (0x15) Ny timme är ogiltig.
- **FX_INVALID_MINUTE** (0x16) Ny minut är ogiltig.
- **FX_INVALID_SECOND** (0x17) Ny sekund är ogiltig.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten skapar en Unicode-namngiven underkatalog i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i parametern Unicode-källnamn. Om det lyckas returneras det korta namnet (8.3-format) för den nyligen skapade Unicode-underkatalogen av tjänsten.

> [!WARNING]
> *Alla åtgärder i Unicode-underkatalogen (vilket gör den till standardsökväg, borttagning osv.) ska göras genom att ange det returnerade korta namnet (8.3-format) till standardfilX-katalogtjänsterna.*

> [!IMPORTANT]
> *Den här tjänsten stöds inte på exFAT-media.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **source_unicode_name:** Pekare till Unicode-namnet för den nya underkatalogen.
- **source_unicode_length:** Längden på Unicode-namnet.
- **short_name:** Pekare till mål för kortnamn (8.3-format) för den nya Unicode-underkatalogen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad Unicode-katalog skapas.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) Angiven katalog finns redan.
- **FX_NO_MORE_SPACE** (0x0A) Inga fler kluster tillgängliga på mediet för den nya katalogposten.
- **FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.
- **FX_IO_ERROR (0x90)** Drivrutins-I/O-fel.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten ändrar en Unicode-namngiven underkatalog till angivet nytt Unicode-namn i den aktuella arbetskatalogen. Unicode-namnparametrarna får inte innehålla sökvägsinformation.

> [!IMPORTANT]
> *Den här tjänsten stöds inte på exFAT-media.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **old_unicode_name:** Pekare till Unicode-namnet för den aktuella filen.
- **old_unicode_name_length:** Längden på det aktuella Unicode-namnet.
- **new_unicode_name**: Pekare till det nya Unicode-filnamnet.
- **old_unicode_name_length:** Längden på det nya Unicode-namnet.
- **new_short_name:** Pekare till mål för kortnamn (8.3-format) för den omdöpta Unicode-filen. Byt namn på katalog med Unicode

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad media är öppen.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) Angivet katalognamn finns redan.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten skapar en Unicode-namngiven fil i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i parametern Unicode-källnamn. Om det lyckas returneras det korta namnet (8.3-format) för den nyligen skapade Unicode-filen av tjänsten.

> [!WARNING]
> *Alla åtgärder på Unicode-filen (öppna, skriva, läsa, stänga osv.) ska göras genom att ange det returnerade korta namnet (formatet 8.3) till standardfiltjänsterna för FileX.*

### <a name="input-parameters"></a>Indataparametrar


- **media_ptr:** Pekare till mediakontrollblock.
- **source_unicode_name:** Pekare till Unicode-namnet för den nya filen.
- **source_unicode_length:** Längden på Unicode-namnet.
- **short_name**: Pekare till mål för kortnamn (8.3-format) för den nya Unicode-filen.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckades fil skapas.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) Angiven fil finns redan.
- **FX_NO_MORE_SPACE** (0x0A) Inga fler kluster tillgängliga på mediet för den nya filposten.
- **FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.
- **FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten ändrar ett Unicode-namn till angivet nytt Unicode-namn i den aktuella standardkatalogen. Unicode-namnparametrarna får inte ha sökvägsinformation.

> [!IMPORTANT]
> *Den här tjänsten stöds inte på exFAT-media.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **old_unicode_name:** Pekare till Unicode-namnet för den aktuella filen.
- **old_unicode_name_length:** Längden på det aktuella Unicode-namnet.
- **new_unicode_name**: Pekare till det nya Unicode-filnamnet.
- **new_unicode_name_length:** Längden på det nya Unicode-namnet.
- **new_short_name:** Pekare till mål för kortnamn (8.3-format) för den omdöpta Unicode-filen.

### <a name="return-values"></a>Returvärden


- **FX_SUCCESS** (0x00) Lyckad media är öppen.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_ALREADY_CREATED** (0x0B) Det angivna filnamnet finns redan.
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_PTR_ERROR** (0x18) En eller flera pekare är NULL.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.
- **FX_WRITE_PROTECT** (0x23) Angivna medier är skrivskyddade.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten avgör längden på det angivna Unicode-namnet. Ett Unicode-tecken representeras av två byte. Ett Unicode-namn är en serie med Unicode-tecken med två byte som avslutas med två NULL-byte (två byte med 0 värde).

### <a name="input-parameters"></a>Indataparametrar

**unicode_name**: Pekare till Unicode-namn.

### <a name="return-values"></a>Returvärden

**length**: Längden på Unicode-namnet (antalet Unicode-tecken i namnet).

### <a name="allowed-from"></a>Tillåts från

Trådar

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
### <a name="description"></a>Description

Den här tjänsten hämtar längden på det angivna Unicode-namnet. Ett Unicode-tecken representeras av två byte. Ett Unicode-namn är en serie med Unicode-tecken på tvåbyte som avslutas med två NULL-byte (två byte med ett värde på 0).

> [!IMPORTANT]
> *Den här tjänsten är **identisk med fx_unicode_length_get()** förutom att anroparen skickar storleken på unicode_name bufferten, inklusive de två NULL-tecknen.*

### <a name="input-parameters"></a>Indataparametrar

- **unicode_name**: Pekare till Unicode-namn.
- **buffer_length:** Storlek på Unicode-namnbuffert.

### <a name="return-values"></a>Returvärden

**length**: Längden på Unicode-namnet (antalet Unicode-tecken i namnet).

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar Unicode-namn från kortnamn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Description

Den här tjänsten hämtar Unicode-namnet som är associerat med det angivna kortnamnet (formatet 8.3) i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i den korta namnparametern. Om det lyckas returneras Unicode-namnet som är associerat med det korta namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten kan användas för att hämta Unicode-namn för både filer och underkataloger.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **short_name** Pekare till kortnamn (8.3-format).
- **destination_unicode_name:** Pekare till målet för Unicode-namnet som är associerat med det angivna korta namnet.
- destination_unicode_length : **Pekare** till returnerad Unicode-namnlängd.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad hämtning av Unicode-namn.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Kortnamnet hittades inte eller så är Unicode-målstorleken för liten.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Hämtar Unicode-namn från kortnamn

### <a name="prototype"></a>Prototyp

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Description

Den här tjänsten hämtar Unicode-namnet som är associerat med det angivna kortnamnet (formatet 8.3) i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i den korta namnparametern. Om det lyckas returneras Unicode-namnet som är associerat med det korta namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten är identisk med ***fx_unicode_name_get**, förutom att anroparen tillhandahåller storleken på _Unicode-målbufferten som ett indataargument. På så sätt kan tjänsten garantera att den inte skriver över Unicode-målbufferten_

> [!IMPORTANT]
> *Den här tjänsten kan användas för att hämta Unicode-namn för både filer och underkataloger.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **short_name**: Pekare till kortnamn (8.3-format).
- **destination_unicode_name: Pekare** till målet för Unicode-namnet som är associerat med det angivna kortnamnet.
- **destination_unicode_length: Pekare** till returnerad Unicode-namnlängd.
- **unicode_name_buffer_length:** Storlek på Unicode-namnbufferten. Obs! En NULL-avslutning krävs, vilket gör en extra byte.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad hämtning av Unicode-namn.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Kortnamnet hittades inte eller så är Unicode-målstorleken för liten.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_PTR_ERROR** (0x18) Ogiltiga medie- eller namnpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

Den här tjänsten hämtar det korta namnet (8.3-format) som är associerat med Unicode-namnet i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i Unicode-namnparametern. Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten kan användas för att hämta korta namn för både filer och underkataloger.*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **source_unicode_name**: Pekare till Unicode-namn.
- **source_unicode_length:** Längden på Unicode-namn.
- **destination_short_name:** Pekare till mål för kortnamnet (8.3-format). Detta måste vara minst 13 byte stort.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Kortnamnhämtningen lyckades.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_IO_ERROR** (0x90) I/O-drivrutin.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Unicode-namn hittades inte.
- **FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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

### <a name="description"></a>Description

Den här tjänsten hämtar det korta namnet (8.3-format) som är associerat med Unicode-namnet i den aktuella standardkatalogen – ingen sökvägsinformation tillåts i Unicode-namnparametern. Om det lyckas returneras det korta namnet som är associerat med Unicode-namnet av tjänsten.

> [!IMPORTANT]
> *Den här tjänsten är identisk **med fx_unicode_short_name_get()**, förutom att anroparen tillhandahåller storleken på målbufferten som ett indataargument. Detta gör att tjänsten kan garantera att det korta namnet inte överskrider målbufferten.*

*Den här tjänsten kan användas för att hämta korta namn för både filer och underkataloger*

### <a name="input-parameters"></a>Indataparametrar

- **media_ptr:** Pekare till mediakontrollblock.
- **source_unicode_name**: Pekare till Unicode-namn.
- **source_unicode_length:** Längden på Unicode-namnet.
- **destination_short_name:** Pekare till mål för kortnamnet (formatet 8.3). Det måste vara minst 13 byte.
- **short_name_buffer_length:** Storleken på målbufferten. Buffertstorleken måste vara minst 14 byte.

### <a name="return-values"></a>Returvärden

- **FX_SUCCESS** (0x00) Lyckad kort namnhämtning.
- **FX_FAT_READ_ERROR** (0x03) Det går inte att läsa FAT-tabellen.
- **FX_FILE_CORRUPT** (0x08) Filen är skadad
- **FX_IO_ERROR** (0x90) Drivrutins-I/O.
- **FX_MEDIA_NOT_OPEN** (0x11) Det angivna mediet är inte öppet.
- **FX_NOT_FOUND** (0x04) Unicode-namn hittades inte.
- **FX_NOT_IMPLEMENTED** (0x22) Tjänsten har inte implementerats för exFAT-filsystemet.
- **FX_SECTOR_INVALID** (0x89) Ogiltig sektor.
- **FX_PTR_ERROR** (0x18) Ogiltiga media- eller namnpekare.
- **FX_CALLER_ERROR** (0x20) anroparen är inte en tråd.

### <a name="allowed-from"></a>Tillåts från

Trådar

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
