---
title: Kapitel 7 – Azure RTOS FileX-spårningshändelser
description: Det här kapitlet innehåller en beskrivning av Azure RTOS FileX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8668f0867e205afdeab112dfedd257998a5f5b7ff256f27298072dde3e9019b0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116803300"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>Kapitel 7 – Azure RTOS FileX-spårningshändelser

Det här kapitlet innehåller en beskrivning av Azure RTOS FileX-händelser. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

**Följande är en lista över FileX-händelser som visas av TraceX.**

Följande beskriver varje händelse:

| **Ikon**                         | **Innebörd**                               |
| -------------------------------- | ----------------------------------------- |
| ![Ikon för miss för cache för intern logisk sektor](./media/user-guide/fx-events/image1.png)    | Cachemiss för intern logisk sektor |
| ![Ikon för miss för intern katalogcache](./media/user-guide/fx-events/image2.png)    | Miss med intern katalogcache |
| ![Ikon för intern medie flush](./media/user-guide/fx-events/image3.png)    | Intern media flush |
| ![Ikon för intern katalogpostläsning](./media/user-guide/fx-events/image4.png)    | Intern katalogpost läses |
| ![Ikon för intern katalogpostskrivning](./media/user-guide/fx-events/image5.png)    | Intern katalogpostskrivning |
| ![Ikon för intern I/O-drivrutinsläsning](./media/user-guide/fx-events/image6.png)    | Läsa intern I/O-drivrutin |
| ![Ikon för intern I/O-drivrutinsskrivning](./media/user-guide/fx-events/image7.png)    | Intern I/O-drivrutinsskrivning |
| ![Ikon för intern I/O-drivrutins flush](./media/user-guide/fx-events/image8.png)    | Intern I/O-drivrutins flush |
| ![Ikonen Avbryt intern I/O-drivrutin](./media/user-guide/fx-events/image9.png)    | Intern I/O-drivrutins abort |
| ![Ikonen Initiera intern I/O-drivrutin](./media/user-guide/fx-events/image10.png)    | Initiera intern I/O-drivrutin |
| ![Startikon för intern I/O-drivrutin](./media/user-guide/fx-events/image11.png)    | Läsa intern I/O-drivrutinsstart |
| ![Ikon för interna I/O-drivrutinsutgåselsektorer](./media/user-guide/fx-events/image12.png)    | Interna sektorer för I/O-drivrutinsutgåsel |
| ![Startskrivningsikon för intern I/O-drivrutin](./media/user-guide/fx-events/image13.png)    | Intern startskrivning för I/O-drivrutin |
| ![Ikon för avitiering av intern I/O-drivrutin](./media/user-guide/fx-events/image14.png)    | Avitiering av intern I/O-drivrutin |
| ![Ikonen Läsa katalogattribut](./media/user-guide/fx-events/image15.png)    | **Läsa katalogattribut** (*fx_directory_attributes_read*) |
| ![Ikon för uppsättning av katalogattribut](./media/user-guide/fx-events/image16.png)    | **Katalogattributuppsättning** (*fx_directory_attributes_set*) |
| ![Ikonen Skapa katalog](./media/user-guide/fx-events/image17.png)    | **Katalog create** (*fx_directory_create*) |
| ![Ikonen Hämta för katalogstandard](./media/user-guide/fx-events/image18.png)    | **Directory Default Get** (*fx_directory_default_get*) |
| ![Ikon för standarduppsättning för katalog](./media/user-guide/fx-events/image19.png)    | **Standarduppsättning för katalog** (*fx_directory_default_set*) |
| ![Ikonen Ta bort katalog](./media/user-guide/fx-events/image20.png)    | **Ta bort katalog** (*fx_directory_delete*) |
| ![Ikonen Hitta första katalogpost](./media/user-guide/fx-events/image21.png)    | **Directory First Entry Find** (*fx_directory_first_entry_find*) |
| ![Ikonen Directory First Full Entry Find (Katalog första fullständiga post sök)](./media/user-guide/fx-events/image22.png)    | **Directory First Full Entry Find** (*fx_directory_first_full_entry_find*) |
| ![Ikonen Hämta kataloginformation](./media/user-guide/fx-events/image23.png)    | **Directory Information Get** (*fx_directory_information_get*) |
| ![Ikonen Rensa lokal katalogsökväg](./media/user-guide/fx-events/image24.png)    | **Directory Local Path Clear** (*fx_directory_local_path_clear*) |
| ![Ikonen Hämta lokal katalogsökväg](./media/user-guide/fx-events/image25.png)    | **Directory Local Path Get** (*fx_directory_local_path_get*) |
| ![Återställningsikon för lokal katalogsökväg](./media/user-guide/fx-events/image26.png)    | **Återställning av lokal katalogsökväg** (*fx_directory_local_path_restore*) |
| ![Ikon för kataloguppsättning för lokal sökväg](./media/user-guide/fx-events/image27.png)    | **Directory Local Path Set** (*fx_directory_local_path_set*) |
| ![Ikonen För långt namn för katalog](./media/user-guide/fx-events/image28.png)    | **Directory Long Name Get** (*fx_directory_long_name_get*) |
| ![Testikon för katalognamn](./media/user-guide/fx-events/image29.png)    | **Directory Name Test** (*fx_directory_name_test*) |
| ![Ikonen Hitta nästa katalogpost](./media/user-guide/fx-events/image30.png)    | **Hitta nästa katalogpost** (*fx_directory_next_entry_find*) |
| ![Ikonen Hitta nästa fullständiga post](./media/user-guide/fx-events/image31.png)    | **Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*) |
| ![Ikon för katalogbyte](./media/user-guide/fx-events/image32.png)    | **Directory Rename** (*fx_directory_rename*) |
| ![Kort namn på katalogikonen Hämta](./media/user-guide/fx-events/image33.png)    | **Kortnamn för katalog get** (*fx_directory_short_name_get*) |
| ![Ikonen Allokera fil](./media/user-guide/fx-events/image34.png)    | **File Allocate** (*fx_file_allocate*) |
| ![Ikonen Läsa filattribut](./media/user-guide/fx-events/image35.png)    | **Lästa filattribut** (*fx_file_attributes_read*) |
| ![Ikon för filattributuppsättning](./media/user-guide/fx-events/image36.png)    | **Filattributuppsättning** (*fx_file_attributes_set*) |
| ![Ikonen Allokera fil efter bästa försök](./media/user-guide/fx-events/image37.png)    | **Allokera bästa möjliga fil** (*fx_file_best_effort_allocate*) |
| ![Stäng filikon](./media/user-guide/fx-events/image38.png)    | **Stäng fil** (*fx_file_close*) |
| ![Ikonen Skapa fil](./media/user-guide/fx-events/image39.png)    | **Fil skapa** (*fx_file_create*) |
| ![Ikon för fildatum/tidsuppsättning](./media/user-guide/fx-events/image40.png)    | **Fildatum/tidsuppsättning** (*fx_file_date_time_set*) |
| ![Ikonen Ta bort fil](./media/user-guide/fx-events/image41.png)    | **Ta bort fil** (*fx_file_delete*) |
| ![Öppna filikon](./media/user-guide/fx-events/image42.png)    | **File Open** (*fx_file_open*) |
| ![Ikon för filläsning](./media/user-guide/fx-events/image43.png)    | **Filläsning** (*fx_file_read*) |
| ![Ikon för relativ filsökning](./media/user-guide/fx-events/image44.png)    | **Relativ filsökning** (*fx_file_relative_seek*) |
| ![Ikon för filbyte](./media/user-guide/fx-events/image45.png)    | **Byt namn** på *fil ( fx_file_rename*) |
| ![Ikon för filsökning](./media/user-guide/fx-events/image46.png)    | **Filsökning** (*fx_file_seek*) |
| ![Ikon för trunkering av fil](./media/user-guide/fx-events/image47.png)    | **Fil trunkera (** *fx_file_truncate*) |
| ![Ikon för fil trunkeringsutgås](./media/user-guide/fx-events/image48.png)    | **Fil trunkera version** (*fx_file_truncate_release*) |
| ![Ikon för filskrivning](./media/user-guide/fx-events/image49.png)    | **Filskrivning** (*fx_file_write*) |
| ![Ikon för medie abort](./media/user-guide/fx-events/image50.png)    | **Medie abort** (*fx_media_abort*) |
| ![Ikon för ogiltig mediacache](./media/user-guide/fx-events/image51.png)    | **Media Cache Invalidate** (*fx_media_cache_invalidate*) |
| ![Ikon för mediekontroll](./media/user-guide/fx-events/image52.png)    | **Mediekontroll** (*fx_media_check*) |
| ![*Ikonen Stäng media](./media/user-guide/fx-events/image53.png)    | **Media Close** (*fx_media_close*) |
| ![Ikonen Rensa media](./media/user-guide/fx-events/image54.png)    | **Media Flush** (*fx_media_flush*) |
| ![Ikon för medieformat](./media/user-guide/fx-events/image55.png)    | **Medieformat** (*fx_media_format*) |
| ![Media Open-ikon](./media/user-guide/fx-events/image56.png)    | **Media Open** (*fx_media_open*) |
| ![Ikon för medieläsning](./media/user-guide/fx-events/image57.png)    | **Medieläsning** (*fx_media_read*) |
| ![Ikon för tillgängligt medieutrymme](./media/user-guide/fx-events/image58.png)    | **Tillgängligt medieutrymme** (*fx_media_space_available*) |
| ![Ikonen Hämta medievolym](./media/user-guide/fx-events/image59.png)    | **Media Volume Get** (*fx_media_volume_get*) |
| ![Ikon för medievolymuppsättning](./media/user-guide/fx-events/image60.png)    | **Medievolymuppsättning** (*fx_media_volume_set*) |
| ![Ikon för medieskrivning](./media/user-guide/fx-events/image61.png)    | **Medieskrivning** (*fx_media_write*) |
| ![Ikonen Hämta systemdatum](./media/user-guide/fx-events/image62.png)    | **Systemdatum get** (*fx_system_date_get*) |
| ![Ikon för systemdatumuppsättning](./media/user-guide/fx-events/image63.png)    | **Systemdatumuppsättning** (*fx_system_date_set*) |
| ![Ikonen System initialize (System initialisering)](./media/user-guide/fx-events/image64.png)    | **System initialize** (*fx_system_initialize*) |
| ![Ikonen Hämta systemtid](./media/user-guide/fx-events/image65.png)    | **Systemtid get** (*fx_system_time_get*) |
| ![Ikon för systemtidsuppsättning](./media/user-guide/fx-events/image66.png)    | **Systemtidsuppsättning** (*fx_system_time_set*) |
| ![Ikonen Skapa i Unicode-katalog](./media/user-guide/fx-events/image67.png)    | **Unicode Directory Create** (*fx_unicode_directory_create*) |
| ![Ikon för unicode-katalogbyte](./media/user-guide/fx-events/image68.png)    | **Unicode Directory Rename** (*fx_unicode_directory_rename*) |
| ![Ikonen Skapa Unicode-fil](./media/user-guide/fx-events/image69.png)    | **Unicode File Create** (*fx_unicode_file_create*) |
| ![Ikon för Namnbyte för Unicode-fil](./media/user-guide/fx-events/image70.png)    | **Unicode-filbyte** (*fx_unicode_file_rename*) |
| ![Ikonen För att hämta Unicode-längd](./media/user-guide/fx-events/image71.png)    | **Unicode Lenght Get** (*fx_unicode_length_get*) |
| ![Ikonen Hämta Unicode-namn](./media/user-guide/fx-events/image72.png)    | **Unicode Name Get** (*fx_unicode_name_get*) |
| ![Kort namn på Unicode-ikonen Hämta](./media/user-guide/fx-events/image73.png)    | **Unicode Short Name Get** (*fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>Händelsebeskrivningar

Följande beskriver varje enskild händelse.

### <a name="internal-logical-sector-cache-miss"></a>Cachemiss för intern logisk sektor 

#### <a name="internal-logical-sector-cache-miss"></a>Cachemiss för intern logisk sektor

**Ikon** ![ Ikon för miss för intern logisk sektorcache](./media/user-guide/fx-events/image1.png)

**Beskrivning**

Den här händelsen representerar en intern cachemiss för logisk FileX-sektor.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Sektor.
- Informationsfält 3: Totalt antal missar.
- Informationsfält 4: Cachestorlek.

### <a name="internal-directory-cache-miss"></a>Miss för intern katalogcache

#### <a name="internal-directory-cache-miss"></a>Miss för intern katalogcache

**Ikon** ![ Ikon för miss för intern katalogcache](./media/user-guide/fx-events/image2.png)

**Beskrivning** 

Den här händelsen representerar en intern miss för FileX-katalogcache.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Totalt antal missar.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-media-flush"></a>Intern media flush 

#### <a name="internal-media-flush"></a>Intern media flush

**Ikon** ![ Ikonen För att tömma interna media](./media/user-guide/fx-events/image3.png)

**Beskrivning**

Den här händelsen representerar en intern FileX-media flush.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Antal dirty-sektorer.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.


### <a name="internal-directory-entry-read"></a>Intern katalogpostläsning 

#### <a name="internal-directory-entry-read"></a>Intern katalogpost läses

**Ikon** ![ Läsikon för intern katalogpost](./media/user-guide/fx-events/image4.png)

**Beskrivning**

Den här händelsen representerar en intern FileX-katalogpostläsningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-directory-entry-write"></a>Intern katalogpostskrivning

#### <a name="internal-directory-entry-write"></a>Intern katalogpostskrivning

**Ikon** ![ Skrivikon för intern katalogpost](./media/user-guide/fx-events/image5.png)

**Beskrivning**

Den här händelsen representerar en intern skrivningshändelse för FileX-katalogpost.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-read"></a>Läsa intern I/O-drivrutin 

#### <a name="internal-io-driver-read"></a>Intern I/O-drivrutinsläsning 

**Ikon** ![ Läsikon för intern I/O-drivrutin](./media/user-guide/fx-events/image6.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutinsläsningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Sektor.
- Informationsfält 3: Antal sektorer.
- Informationsfält 4: Buffertpekare.

### <a name="internal-io-driver-write"></a>Intern I/O-drivrutinsskrivning 

#### <a name="internal-io-driver-write"></a>Intern I/O-drivrutinsskrivning 

**Ikon** ![ Skrivikon för intern I/O-drivrutin](./media/user-guide/fx-events/image7.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutinsskrivningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Sektor.
- Informationsfält 3: Antal sektorer.
- Informationsfält 4: Buffertpekare.

### <a name="internal-io-driver-flush"></a>Intern I/O-drivrutins flush 

#### <a name="internal-io-driver-flush"></a>Intern I/O-drivrutins flush 

**Ikon** ![ Ikon för intern I/O-drivrutinsspolning](./media/user-guide/fx-events/image8.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutins flush-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-abort"></a>Intern I/O-drivrutins abort 

#### <a name="internal-io-dirver-abort"></a>Intern I/O-dirver avbryts

**Ikon** ![ Ikonen Avbryt intern I/O-drivrutin](./media/user-guide/fx-events/image9.png)

**Beskrivning**

Den här händelsen representerar en intern FileX I/O-drivrutinshändelse som avbryts.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-initialize"></a>Initiera intern I/O-drivrutin 

#### <a name="internal-io-driver-initialize"></a>Initiera intern I/O-drivrutin 

**Ikon** ![ Initieringsikon för intern I/O-drivrutin](./media/user-guide/fx-events/image10.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutin som initierar händelsen.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-boot-sector-read"></a>Läsa intern I/O-drivrutinsstartsektor 

#### <a name="internal-io-driver-boot-sector-read"></a>Läsa intern I/O-drivrutinsstartsektor 

**Ikon** ![ Läsikon för intern I/O-drivrutinsstartsektor](./media/user-guide/fx-events/image11.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutinsstartsektor för läshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Buffertpekare.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-release-sectors"></a>Interna sektorer för I/O-drivrutinsutgåsel 

#### <a name="internal-io-driver-release-sectors"></a>Interna sektorer för I/O-drivrutinsutgåsel 

**Ikon** ![ Ikon för interna I/O-drivrutinsutgåselsektorer](./media/user-guide/fx-events/image12.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutinsutgåselhändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Sektor.
- Informationsfält 3: Antal sektorer.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-boot-sector-write"></a>Intern skrivning i I/O-drivrutinsstartsektor

#### <a name="internal-io-driver-boot-sector-write"></a>Intern skrivning i I/O-drivrutinsstartsektor 

**Ikon** ![ Skrivikon för intern I/O-drivrutinsstartsektor](./media/user-guide/fx-events/image13.png)

**Beskrivning** 

Den här händelsen representerar en intern skrivningshändelse för FileX I/O-drivrutinssektor.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Buffertpekare.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="internal-io-driver-un-initialize"></a>Avitiera intern I/O-drivrutin 

#### <a name="internal-io-driver-un-initialize"></a>Avitiering av intern I/O-drivrutin 

**Ikon** ![ Ikon för avitiering av intern I/O-drivrutin](./media/user-guide/fx-events/image14.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutin som avitierar händelsen.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.
</blockquote></td>

### <a name="directory-attributes-read"></a>Läsa katalogattribut 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**Ikon** ![ Ikon för att läsa katalogattribut](./media/user-guide/fx-events/image15.png)

**Beskrivning** 

Den här händelsen representerar en läshändelse för katalogattribut.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Attributbitkarta:

  | Attribut                         | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | (0x01)  |
  |  Dold                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Volym                           | (0x08)  |
  |  Katalog                        | (0x10)  |
  |  Arkiv                          | (0x20)  |
- Informationsfält 4: Används inte.

### <a name="directory-attributes-set"></a>Katalogattributuppsättning 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**Ikon** ![ Ikon för attributuppsättning](./media/user-guide/fx-events/image16.png)

**Beskrivning** 

Den här händelsen representerar en katalog som en katalogattributuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Attributbitkarta:

  |  Attribut                        | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | (0x01)  |
  |  Dold                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Arkiv                          | (0x20)  |
- Informationsfält 4: Används inte.

### <a name="directory-create"></a>Katalog skapa 

#### <a name="fx_directory_create"></a>fx_directory_create

**Ikon** ![ Ikonen Skapa katalog](./media/user-guide/fx-events/image17.png)

**Beskrivning** 

Den här händelsen representerar en katalog skapa händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-default-get"></a>Standardvärde för katalog – Hämta 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**Ikon** ![ Ikonen Hämta för katalogstandard](./media/user-guide/fx-events/image18.png)

**Beskrivning** 

Den här händelsen representerar en standarduppsättningshändelse för katalogen.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare för att returnera sökvägens namn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-default-set"></a>Standarduppsättning för katalog 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**Ikon** ![ Ikon för katalogstandarduppsättning](./media/user-guide/fx-events/image19.png)

**Beskrivning** 

Den här händelsen representerar en standarduppsättningshändelse för katalogen.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till nytt standardsökvägnamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-delete"></a>Ta bort katalog 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**Ikon** ![ Ikonen Ta bort katalog](./media/user-guide/fx-events/image20.png)

**Beskrivning** 

Den här händelsen representerar en katalog borttagningshändelse.

**Informationsfält**
- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-first-entry-find"></a>Directory First Entry Find 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**Ikon** ![ Katalogikon för första posten](./media/user-guide/fx-events/image21.png)

**Beskrivning** 

Den här händelsen representerar en katalog första posten hitta händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-first-full-entry-find"></a>Directory First Full Entry Find 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**Ikon** ![ Katalogikonen för den första fullständiga posten](./media/user-guide/fx-events/image22.png)

**Beskrivning** 

Den här händelsen representerar en katalog första fullständiga posten hitta händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-information-get"></a>Kataloginformation Hämta 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**Ikon** ![ Ikonen Hämta kataloginformation](./media/user-guide/fx-events/image23.png)

**Beskrivning** 

Den här händelsen representerar en hämta händelse med kataloginformation.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-local-path-clear"></a>Rensa lokal katalogsökväg 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**Ikon** ![ Rensa ikon för lokal katalogsökväg](./media/user-guide/fx-events/image24.png)

**Beskrivning** 

Den här händelsen representerar en rensad katalogsökvägshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-local-path-get"></a>Directory Local Path Get 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**Ikon** ![ Hämta ikon för lokal katalogsökväg](./media/user-guide/fx-events/image25.png)

**Beskrivning** 

Den här händelsen representerar en lokal katalogsökväg för att hämta händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare för att returnera sökvägens namn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-local-path-restore"></a>Återställning av lokal katalogsökväg 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**Ikon** ![ Återställningsikon för lokal katalogsökväg](./media/user-guide/fx-events/image26.png)

**Beskrivning** 

Den här händelsen representerar en återställningshändelse för en lokal katalogsökväg.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till lokal sökvägsstruktur.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-local-path-set"></a>Ange lokal katalogsökväg 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**Ikon** ![ Ikon för katalog för lokal sökvägsuppsättning](./media/user-guide/fx-events/image27.png)

**Beskrivning** 

Den här händelsen representerar en lokal katalogsökvägsuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till lokal sökvägsstruktur.
- Informationsfält 3: Pekare till nytt sökvägsnamn.
- Informationsfält 4: Används inte.

### <a name="directory-long-name-get"></a>Långt katalognamn hämta 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**Ikon** ![ Ikonen Hämta katalog långt namn](./media/user-guide/fx-events/image28.png)

**Beskrivning** 

Den här händelsen representerar en katalog lång namn hämta händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till kort filnamn.
- Informationsfält 3: Pekare till långt filnamn.
- Informationsfält 4: Används inte.

### <a name="directory-name-test"></a>Katalognamnstest 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**Ikon** ![ Testikon för katalognamn](./media/user-guide/fx-events/image29.png)

**Beskrivning** 

Den här händelsen representerar en testhändelse för katalognamn.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-next-entry-find"></a>Hitta nästa katalogpost 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**Ikon** ![ Ikonen Hitta nästa katalogpost](./media/user-guide/fx-events/image30.png)

**Beskrivning** 

Den här händelsen representerar en nästa katalogpost för att hitta händelsen.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-next-full-entry-find"></a>Directory Next Full Entry Find 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**Ikon** ![ Katalogikon för nästa fullständiga post](./media/user-guide/fx-events/image31.png)

**Beskrivning**

Den här händelsen representerar en katalog nästa fullständiga post hitta händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till katalognamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="directory-rename"></a>Katalogbyte 

#### <a name="fx_directory_rename-event"></a>fx_directory_rename händelse

**Ikon** ![ Ikon för katalogbyte](./media/user-guide/fx-events/image32.png)

**Beskrivning**

Den här händelsen representerar en händelse för katalogbyte.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till gammalt katalognamn.
- Informationsfält 3: Pekare till nytt katalognamn.
- Informationsfält 4: Används inte.

### <a name="directory-short-name-get"></a>Kortnamn för katalog – hämta 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**Ikon** ![ Kort namn på katalogikonen hämta](./media/user-guide/fx-events/image33.png)

**Beskrivning**

Den här händelsen representerar en kort katalog med namnet get event.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till långt filnamn.
- Infofält 3: Pekare till kort filnamn.
- Informationsfält 4: Används inte.

### <a name="file-allocate"></a>Allokera fil 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**Ikon** ![ Ikon för fil allokera](./media/user-guide/fx-events/image34.png)

**Beskrivning**

Den här händelsen representerar en fil allokera händelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Begärd storlek.
- Informationsfält 3: Aktuell storlek.
- Informationsfält 4: Ny storlek.

### <a name="file-attributes-read"></a>Lästa filattribut 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**Ikon** ![ Ikon för att läsa filattribut](./media/user-guide/fx-events/image35.png)

**Beskrivning**

Den här händelsen representerar en läshändelse för filattribut.

**Informationsfält**

- Informationsfält 1: Pekare till mediet. 
- Informationsfält 2: Attribut bitmappning:

  |  Attribut                         | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | (0x01)  |
  |  Dold                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Volym                           | (0x08)  |
  |  Katalog                        | (0x10)  |
  |  Arkiv                          | (0x20)  |
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="file-attributes-set"></a>Filattributuppsättning 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**Ikon** ![ Ikon för filattributuppsättning](./media/user-guide/fx-events/image36.png)

**Beskrivning** 

Den här händelsen representerar en händelse för filattributuppsättning.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till filnamn. 
- Informationsfält 3: Attribut bitmappning:

  | Attribut                         | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | (0x01)  |
  |  Dold                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Arkiv                          | (0x20)  |
- Informationsfält 4: Används inte.

### <a name="file-best-effort-allocate"></a>Allokera bästa möjliga fil 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**Ikon** ![ Allokera ikon för bästa möjliga resultat](./media/user-guide/fx-events/image37.png)

**Beskrivning** 

Den här händelsen representerar en fils allokerade händelse efter bästa försök.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Begärd storlek.
- Informationsfält 3: Faktisk storlek allokerad.
- Informationsfält 4: Används inte.

### <a name="file-close"></a>Stäng fil 

#### <a name="fx_file_close"></a>fx_file_close

**Ikon** ![ Stäng filikon](./media/user-guide/fx-events/image38.png)

**Beskrivning** 

Den här händelsen representerar en fil stäng-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Filstorlek.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="file-create"></a>Skapa fil

#### <a name="fx_file_create"></a>fx_file_create

**Ikon** ![ Ikon för att skapa fil](./media/user-guide/fx-events/image39.png)

**Beskrivning**

Den här händelsen representerar en fil skapa händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till filnamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="file-date-time-set"></a>Fildatum/ tidsuppsättning 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**Ikon** ![ Ikon för tidsuppsättning för fildatum](./media/user-guide/fx-events/image40.png)

**Beskrivning**

Den här händelsen representerar en händelse för fildatum/tidsuppsättning.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till filnamn.
- Informationsfält 3: År.
- Informationsfält 4: Månad.

### <a name="file-delete"></a>Ta bort fil 

#### <a name="fx_file_delete"></a>fx_file_delete

**Ikon** ![ Ikonen Ta bort fil](./media/user-guide/fx-events/image41.png)

**Beskrivning**

Den här händelsen representerar en fil borttagningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till filnamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="file-open"></a>Öppna fil 

#### <a name="fx_file_open"></a>fx_file_open

**Ikon** ![ Ikonen Öppna fil](./media/user-guide/fx-events/image42.png)

**Beskrivning**

Den här händelsen representerar en öppen filhändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till filkontrollblocket.
- Informationsfält 3: Pekare till filnamn.
- Informationsfält 4: Öppen typ:

  |  Öppen typ                        | Värde        |
  |---------------------------------- | --------|
  |  Öppna för Läsning                    | (0x00)  |
  |  Öppna för skrivning                   | (0x01)  |
  |  Snabb öppning för läsning               | (0x02)  |

### <a name="file-read"></a>Filläsning 

#### <a name="fx_file_read"></a>fx_file_read

**Ikon** ![ Ikon för filläsning](./media/user-guide/fx-events/image43.png)

**Beskrivning**

Den här händelsen representerar en filläsningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Buffert pekare.
- Informationsfält 3: Begärandestorlek.
- Informationsfält 4: Faktisk storlek läst.

### <a name="file-relative-seek"></a>Relativ filsökning 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**Ikon** ![ Ikon för relativ filsökning](./media/user-guide/fx-events/image44.png)

**Beskrivning**

Den här händelsen representerar en relativ filsökningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Byteförskjutning.
- Informationsfält 3: Sök från:

  | Händelse                             | Värde        |
  |---------------------------------- | --------|
  |  Från början                   | (0x00)  |
  |  Från slutet                         | (0x01)  | 
  |  Vidarebefordra                          | (0x02)  |
  |  Bakåt                         | (0x03)  |
- Informationsfält 4: Föregående förskjutning.

### <a name="file-rename"></a>Byt namn på fil 

#### <a name="fx_file_rename"></a>fx_file_rename

**Ikon** ![ Ikon för filbyte](./media/user-guide/fx-events/image45.png)

**Beskrivning**

Den här händelsen representerar en filbyteshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till gammalt filnamn.
- Informationsfält 3: Pekare till nytt filnamn.
- Informationsfält 4: Används inte.

### <a name="file-seek"></a>Filsökning 

#### <a name="fx_file_seek"></a>fx_file_seek

**Ikon** ![ Ikon för filsökning](./media/user-guide/fx-events/image46.png)

**Beskrivning**

Den här händelsen representerar en filsökningshändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Byteförskjutning.
- Informationsfält 3: Föregående förskjutning.
- Informationsfält 4: Används inte.

### <a name="file-truncate"></a>Trunkering av fil 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**Ikon** ![ Ikon för trunkering av fil](./media/user-guide/fx-events/image47.png)

**Beskrivning**

Den här händelsen representerar en fil trunkeringshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Begärd storlek.
- Informationsfält 3: Föregående storlek.
- Informationsfält 4: Ny storlek.

### <a name="file-truncate-release"></a>Fil trunkera version 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**Ikon** ![ Ikon för fil trunkeringsutgås](./media/user-guide/fx-events/image48.png)

**Beskrivning**

Den här händelsen representerar en filtruncate release-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Begärd storlek.
- Informationsfält 3: Föregående storlek.
- Informationsfält 4: Ny storlek.

### <a name="file-write"></a>Filskrivning 

#### <a name="fx_file_write"></a>fx_file_write 

**Ikon** ![ Ikon för filskrivning](./media/user-guide/fx-events/image49.png)

**Beskrivning**

Den här händelsen representerar en filskrivningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till filen.
- Informationsfält 2: Buffertpekare.
- Informationsfält 3: Begärandestorlek.
- Informationsfält 4: Faktisk storlek skriven.

### <a name="media-abort"></a>Medie abort 

#### <a name="fx_media_abort"></a>fx_media_abort 

**Ikon** ![ Ikon för medie abort](./media/user-guide/fx-events/image50.png)

**Beskrivning**

Den här händelsen representerar en mediehändelse som avbryts.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="media-cache-invalidate"></a>Ogiltigförklara mediecache

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**Ikon** ![ Ikon för ogiltig mediacache](./media/user-guide/fx-events/image51.png)

**Beskrivning**

Den här händelsen representerar en ogiltig händelse för mediecache.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="media-check"></a>Mediekontroll 

#### <a name="fx_media_check"></a>fx_media_check

**Ikon** ![ Ikon för mediekontroll](./media/user-guide/fx-events/image52.png)

**Beskrivning**

Den här händelsen representerar en mediakontrollhändelse.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare för virtuellt minne.
- Informationsfält 3: Minnesstorlek för den sporade storleken.
- Informationsfält 4: Bitkarta för fel:

  | Feltyp                        | Värde        |
  |---------------------------------- | --------|
  |  FAT Chain-fel                  | (0x01)  |
  |  Katalogfel                  | (0x02)  |
  |  Fel med förlorat kluster               | (0x04)  |
  |  Filstorleksfel                  | (0x08)  |

### <a name="media-close"></a>Stäng media 

#### <a name="fx_media_close"></a>fx_media_close

**Ikon** ![ Ikonen Stäng media](./media/user-guide/fx-events/image53.png)

**Beskrivning**

Den här händelsen representerar en media close-händelse.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="media-flush"></a>Media Flush 

#### <a name="fx_media_flush"></a>fx_media_flush

**Ikon** ![ Ikon för medie flush](./media/user-guide/fx-events/image54.png)

**Beskrivning**

Den här händelsen representerar en media flush-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="media-format"></a>Medieformat 

#### <a name="fx_media_format"></a>fx_media_format

**Ikon** ![ Ikon för medieformat](./media/user-guide/fx-events/image55.png)

**Beskrivning**

Den här händelsen representerar en mediaformathändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Antal rotposter.
- Informationsfält 3: Sektorer.
- Informationsfält 4: Sektorer per kluster.

### <a name="media-open"></a>Media Open 

#### <a name="fx_media_open"></a>fx_media_open

**Ikon** ![ Ikonen Media öppen](./media/user-guide/fx-events/image56.png)

**Beskrivning**

Den här händelsen representerar en öppen mediahändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till posten mediadrivrutin.
- Informationsfält 3: Minnespekare.
- Informationsfält 4: Minnesstorlek.

### <a name="media-read-media-read"></a>Media Read Media Read 

#### <a name="fx_media_read"></a>fx_media_read

**Ikon** ![ Ikon för medieläsning](./media/user-guide/fx-events/image57.png)

**Beskrivning**

Den här händelsen representerar en medialäsningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Logisk sektor.
- Informationsfält 3: Buffert pekare.
- Informationsfält 4: Byte läses.

### <a name="media-space-available"></a>Tillgängligt medieutrymme 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**Ikon** ![ Ikon för tillgängligt medieutrymme](./media/user-guide/fx-events/image58.png)

**Beskrivning**

Den här händelsen representerar en mediaplats tillgänglig händelse.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Tillgänglig byte-pekare.
- Informationsfält 3: Antal kostnadsfria kluster.
- Informationsfält 4: Används inte.

### <a name="media-volume-get"></a>Hämta medievolym 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**Ikon** ![ Ikon för att hämta medievolym](./media/user-guide/fx-events/image59.png)

**Beskrivning**

Den här händelsen representerar en mediavolym för get-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till volymnamn.
- Informationsfält 3: Volymkälla.
- Informationsfält 4: Används inte.

### <a name="media-volume-set"></a>Medievolymuppsättning 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**Ikon** ![ Ikon för medievolymuppsättning](./media/user-guide/fx-events/image60.png)

**Beskrivning**

Den här händelsen representerar en mediavolymuppsättningshändelse.

**Informationsfält** 
- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Pekare till volymnamn.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="media-write"></a>Medieskrivning 

#### <a name="fx_media_write"></a>fx_media_write

**Ikon** ![ Ikon för medieskrivning](./media/user-guide/fx-events/image61.png)

**Beskrivning**

Den här händelsen representerar en medieskrivningshändelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Logisk sektor.
- Informationsfält 3: Buffert pekare.
- Informationsfält 4: Skrivna byte.

### <a name="system-date-get"></a>Systemdatum Get 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**Ikon** ![ Ikonen Hämta systemdatum](./media/user-guide/fx-events/image62.png)

**Beskrivning**

Den här händelsen representerar ett systemdatum för get-händelse.

**Informationsfält**

- Informationsfält 1: År.
- Informationsfält 2: Månad.
- Informationsfält 3: Dag.
- Informationsfält 4: Används inte.

### <a name="system-date-set"></a>Systemdatumuppsättning 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**Ikon** ![ Ikon för systemdatumuppsättning](./media/user-guide/fx-events/image63.png)

**Beskrivning**

Den här händelsen representerar en systemdatumuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: År.
- Informationsfält 2: Månad.
- Informationsfält 3: Dag.
- Informationsfält 4: Används inte.

### <a name="system-initialize"></a>Initiera systemet 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**Ikon** ![ Ikonen Systemitiering](./media/user-guide/fx-events/image64.png)

**Beskrivning**

Den här händelsen representerar en systemitieringshändelse.

**Informationsfält**

- Informationsfält 1: Används inte.
- Informationsfält 2: Används inte.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="system-time-get"></a>Systemtid get 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**Ikon** ![ Ikonen Hämta systemtid](./media/user-guide/fx-events/image65.png)

**Beskrivning**

Den här händelsen representerar en systemtid för att hämta händelse.

**Informationsfält** 

- Informationsfält 1: Timme.
- Informationsfält 2: Minut.
- Informationsfält 3: Sekund.
- Informationsfält 4: Används inte.

### <a name="system-time-set"></a>Systemtidsuppsättning 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**Ikon** ![ Ikon för systemtidsuppsättning](./media/user-guide/fx-events/image66.png)

**Beskrivning**

Den här händelsen representerar en systemtidsuppsättningshändelse.

**Informationsfält**

- Informationsfält 1: Timme.
- Informationsfält 2: Minut.
- Informationsfält 3: Sekund.
- Informationsfält 4: Används inte.

### <a name="unicode-directory-create"></a>Skapa Unicode-katalog 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**Ikon** ![ Ikon för att skapa Unicode-katalog](./media/user-guide/fx-events/image67.png)

**Beskrivning**

Den här händelsen representerar en Händelse för att skapa En Unicode-katalog.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Infofält 2: Pekare till Unicode-namn.
- Infofält 3: Storlek på Unicode-namn.
- Informationsfält 4: Pekare till kortnamn.

### <a name="unicode-directory-rename"></a>Namnbyte för Unicode-katalog 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**Ikon** ![ Ikon för namnbyte i Unicode-katalog](./media/user-guide/fx-events/image68.png)

**Beskrivning**

Den här händelsen representerar en namnbyteshändelse för En Unicode-katalog.

**Informationsfält** 

- Informationsfält 1: Pekare till mediet.
- Infofält 2: Pekare till Unicode-namn.
- Infofält 3: Storlek på Unicode-namn.
- Informationsfält 4: Pekare till kortnamn.

### <a name="unicode-file-create"></a>Skapa Unicode-fil 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**Ikon** ![ Ikon för att skapa Unicode-fil](./media/user-guide/fx-events/image69.png)

**Beskrivning**

Den här händelsen representerar en create-händelse för En Unicode-fil.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Infofält 2: Pekare till Unicode-namnet.
- Infofält 3: Storlek på Unicode-namn.
- Informationsfält 4: Pekare till kortnamn.

### <a name="unicode-file-rename"></a>Namnbyte för Unicode-fil 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**Ikon** ![ Ikon för namnbyte för Unicode-fil](./media/user-guide/fx-events/image70.png)

**Beskrivning**

Den här händelsen representerar en namnbyteshändelse för En Unicode-fil.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Infofält 2: Pekare till Unicode-namn.
- Infofält 3: Storlek på Unicode-namn.
- Informationsfält 4: Pekare till kortnamn.

### <a name="unicode-length-get"></a>Unicode Length Get 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**Ikon** ![ Get-ikon för Unicode-längd](./media/user-guide/fx-events/image71.png)

**Beskrivning**

Den här händelsen representerar en Get-händelse med Unicode-längd.

**Informationsfält**

- Infofält 1: Pekare till Unicode-namnet.
- Informationsfält 2: Längd.
- Informationsfält 3: Används inte.
- Informationsfält 4: Används inte.

### <a name="unicode-name-get"></a>Unicode Name Get 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**Ikon** ![ Ikon för att hämta Unicode-namn](./media/user-guide/fx-events/image72.png)

**Beskrivning**

Den här händelsen representerar ett Unicode-namn för get-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Informationsfält 2: Källans korta namn.
- Infofält 3: Unicode-målnamns pekare.
- Infofält 4: Unicode-målnamnslängd.

### <a name="unicode-short-name-get"></a>Kortnamn för Unicode Get 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**Ikon** ![ Kortnamn för Unicode get-ikon](./media/user-guide/fx-events/image73.png)

**Beskrivning**

Den här händelsen representerar ett kort Unicode-namn för get-händelse.

**Informationsfält**

- Informationsfält 1: Pekare till mediet.
- Infofält 2: Pekare till källans Unicode-namn.
- Infofält 3: Längden på Unicode-namn.
- Informationsfält 4: Pekare till kortnamn.