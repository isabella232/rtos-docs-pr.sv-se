---
title: Kapitel 7 – Azure återställnings tider FileX trace Events
description: Det här kapitlet innehåller en beskrivning av Azure återställnings tider FileX-händelser.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827492"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>Kapitel 7 – Azure återställnings tider FileX trace Events

Det här kapitlet innehåller en beskrivning av Azure återställnings tider FileX-händelser. 

## <a name="list-of-events-and-icons"></a>Lista över händelser och ikoner

**Följande är en lista över FileX-händelser som visas av TraceX.**

Följande beskriver varje händelse:

| **Ikon**                         | **Innebörd**                               |
| -------------------------------- | ----------------------------------------- |
| ![Intern logisk sektor cache missar ikon](./media/user-guide/fx-events/image1.png)    | Intern logisk sektor cache missar |
| ![Ikon för internt katalog-Cachemissar](./media/user-guide/fx-events/image2.png)    | Intern katalog-Cachemissar |
| ![Ikon för internt medie tömning](./media/user-guide/fx-events/image3.png)    | Intern medie tömning |
| ![Läs ikon för intern katalog post](./media/user-guide/fx-events/image4.png)    | Läsning av intern katalog post |
| ![Skriv ikon för intern katalog post](./media/user-guide/fx-events/image5.png)    | Skrivning av intern katalog post |
| ![Läs ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image6.png)    | Läst intern I/O-drivrutin |
| ![Skriv ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image7.png)    | Intern I/O-drivrutin skrivning |
| ![Intern I/O-drivrutin för driv Rutins tömning](./media/user-guide/fx-events/image8.png)    | Intern I/O-drivrutins tömning |
| ![Avbrotts ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image9.png)    | Intern I/O-drivrutin avbryts |
| ![Initiera ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image10.png)    | Intern I/O-drivrutin initieras |
| ![Intern I/O driv rutin start Läs ikon](./media/user-guide/fx-events/image11.png)    | Start läsning av intern I/O-drivrutin |
| ![Intern I/O driv Rutins ikon för versions sektorer](./media/user-guide/fx-events/image12.png)    | Interna I/O driv Rutins versions sektorer |
| ![Start Skriv ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image13.png)    | Intern I/O driv Rutins Start Skriv |
| ![Intern I/O driv rutin driv rutin driv rutin avinitiera ikon](./media/user-guide/fx-events/image14.png)    | Intern I/O driv rutin driv rutin avinitieras |
| ![Läs ikon för katalogattribut](./media/user-guide/fx-events/image15.png)    | **Lästa katalogattribut** (*fx_directory_attributes_read*) |
| ![Ikon för ange katalogattribut](./media/user-guide/fx-events/image16.png)    | **Katalog-attribut har angetts** (*fx_directory_attributes_set*) |
| ![Ikon för att skapa katalog](./media/user-guide/fx-events/image17.png)    | **Skapa katalog** (*fx_directory_create*) |
| ![Hämta ikon för katalog standard](./media/user-guide/fx-events/image18.png)    | **Hämta katalog standard** (*fx_directory_default_get*) |
| ![Ikon för katalog standard uppsättning](./media/user-guide/fx-events/image19.png)    | **Katalog standard uppsättning** (*fx_directory_default_set*) |
| ![Ikonen Ta bort katalog](./media/user-guide/fx-events/image20.png)    | **Ta bort katalog** (*fx_directory_delete*) |
| ![Hitta ikon för första katalog posten](./media/user-guide/fx-events/image21.png)    | **Sök efter katalog första posten** (*fx_directory_first_entry_find*) |
| ![Hitta ikon för första katalog start posten](./media/user-guide/fx-events/image22.png)    | **Katalog-första fullständiga post Sök** (*fx_directory_first_full_entry_find*) |
| ![Ikon för Hämta katalog information](./media/user-guide/fx-events/image23.png)    | **Hämta katalog information** (*fx_directory_information_get*) |
| ![Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image24.png)    | **Rensa katalogens lokala sökväg** (*fx_directory_local_path_clear*) |
| ![Hämta ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image25.png)    | **Lokal sökväg för katalog hämtning** (*fx_directory_local_path_get*) |
| ![Ikon för återställning av lokal sökväg för katalog](./media/user-guide/fx-events/image26.png)    | **Återställning av lokal sökväg för katalog** (*fx_directory_local_path_restore*) |
| ![Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image27.png)    | **Lokal sökväg till katalog** (*fx_directory_local_path_set*) |
| ![Hämta ikon för katalogens långa namn](./media/user-guide/fx-events/image28.png)    | **Katalogens långa namn get** (*fx_directory_long_name_get*) |
| ![Ikon för katalog namns test](./media/user-guide/fx-events/image29.png)    | **Katalog namns test** (*fx_directory_name_test*) |
| ![Sök ikon för katalog nästa post](./media/user-guide/fx-events/image30.png)    | **Sök i katalog nästa post** (*fx_directory_next_entry_find*) |
| ![Sök ikon för nästa fullständiga post-katalog](./media/user-guide/fx-events/image31.png)    | **Sök i katalog nästa fullständiga post** (*fx_directory_next_full_entry_find*) |
| ![Ikon för katalog namn](./media/user-guide/fx-events/image32.png)    | **Byt namn på katalog** (*fx_directory_rename*) |
| ![Katalog kort namn Hämta ikon](./media/user-guide/fx-events/image33.png)    | **Katalog kort namn Hämta** (*fx_directory_short_name_get*) |
| ![Fil tilldelnings ikon](./media/user-guide/fx-events/image34.png)    | **Fil tilldelning** (*fx_file_allocate*) |
| ![Läs ikon för filattribut](./media/user-guide/fx-events/image35.png)    | **Lästa filattribut** (*fx_file_attributes_read*) |
| ![Ikonen filattribut ange](./media/user-guide/fx-events/image36.png)    | **Angett filattribut** (*fx_file_attributes_set*) |
| ![Ikon för att allokera bästa ansträngning](./media/user-guide/fx-events/image37.png)    | **Bästa fördelar för fil** (*fx_file_best_effort_allocate*) |
| ![Fil stängnings ikon](./media/user-guide/fx-events/image38.png)    | **Stäng fil** (*fx_file_close*) |
| ![Ikon för fil skapande](./media/user-guide/fx-events/image39.png)    | **Skapa fil** (*fx_file_create*) |
| ![Ikon för datum/tid för fil uppsättning](./media/user-guide/fx-events/image40.png)    | **Datum tid för filen** (*fx_file_date_time_set*) |
| ![Fil borttagnings ikon](./media/user-guide/fx-events/image41.png)    | **Ta bort fil** (*fx_file_delete*) |
| ![Fil öppnings ikon](./media/user-guide/fx-events/image42.png)    | **Öppna fil** (*fx_file_open*) |
| ![Fil läsnings ikon](./media/user-guide/fx-events/image43.png)    | **Fil läsning** (*fx_file_read*) |
| ![Ikon för fil relativ sökning](./media/user-guide/fx-events/image44.png)    | **Relativ sökning av filer** (*fx_file_relative_seek*) |
| ![Ikon för fil namn](./media/user-guide/fx-events/image45.png)    | **Byt namn på fil** (*fx_file_rename*) |
| ![Fil Sök ikon](./media/user-guide/fx-events/image46.png)    | **Fil sökning** (*fx_file_seek*) |
| ![Ikon för fil trunkering](./media/user-guide/fx-events/image47.png)    | **Filen trunkeras** (*fx_file_truncate*) |
| ![Ikonen för att trunkera en fil](./media/user-guide/fx-events/image48.png)    | **Fil trunkerad version** (*fx_file_truncate_release*) |
| ![Fil skrivnings ikon](./media/user-guide/fx-events/image49.png)    | **Fil skrivning** (*fx_file_write*) |
| ![Ikon för medie avbrott](./media/user-guide/fx-events/image50.png)    | **Medie avbrott** (*fx_media_abort*) |
| ![Ikon för att verifiera medie cache](./media/user-guide/fx-events/image51.png)    | **Ogiltig cachelagring av media** (*fx_media_cache_invalidate*) |
| ![Ikon för medie kontroll](./media/user-guide/fx-events/image52.png)    | **Medie kontroll** (*fx_media_check*) |
| ![* Ikon för medie stängning](./media/user-guide/fx-events/image53.png)    | **Medie stängning** (*fx_media_close*) |
| ![Ikon för medie tömning](./media/user-guide/fx-events/image54.png)    | **Medie tömning** (*fx_media_flush*) |
| ![Ikon för medie format](./media/user-guide/fx-events/image55.png)    | **Medie format** (*fx_media_format*) |
| ![Medie öppnings ikon](./media/user-guide/fx-events/image56.png)    | **Öppna Media** (*fx_media_open*) |
| ![Medie läsnings ikon](./media/user-guide/fx-events/image57.png)    | **Läsning av media** (*fx_media_read*) |
| ![Ikon för tillgängligt medie utrymme](./media/user-guide/fx-events/image58.png)    | **Tillgängligt medie utrymme** (*fx_media_space_available*) |
| ![Ikon för Hämta medie volym](./media/user-guide/fx-events/image59.png)    | **Hämta medie volym** (*fx_media_volume_get*) |
| ![Ikon för medie volym uppsättning](./media/user-guide/fx-events/image60.png)    | **Medie volym uppsättning** (*fx_media_volume_set*) |
| ![Ikon för medie skrivning](./media/user-guide/fx-events/image61.png)    | **Medie skrivning** (*fx_media_write*) |
| ![Ikonen system datum get](./media/user-guide/fx-events/image62.png)    | **System datum get** (*fx_system_date_get*) |
| ![Ikon för system datum uppsättning](./media/user-guide/fx-events/image63.png)    | **System datum uppsättning** (*fx_system_date_set*) |
| ![Ikon för system initiering](./media/user-guide/fx-events/image64.png)    | **System initiering** (*fx_system_initialize*) |
| ![Ikonen system tid get](./media/user-guide/fx-events/image65.png)    | **System tid get** (*fx_system_time_get*) |
| ![Ikon för system tids uppsättning](./media/user-guide/fx-events/image66.png)    | **System tids uppsättning** (*fx_system_time_set*) |
| ![Ikon för att skapa Unicode-katalogen](./media/user-guide/fx-events/image67.png)    | **Skapa Unicode-katalog** (*fx_unicode_directory_create*) |
| ![Ikon för byte i Unicode-katalog](./media/user-guide/fx-events/image68.png)    | **Byt namn på Unicode-katalogen** (*fx_unicode_directory_rename*) |
| ![Ikon för att skapa Unicode-fil](./media/user-guide/fx-events/image69.png)    | **Skapa Unicode-fil** (*fx_unicode_file_create*) |
| ![Ikon för byte av Unicode-fil](./media/user-guide/fx-events/image70.png)    | **Byt namn på Unicode-filen** (*fx_unicode_file_rename*) |
| ![Hämta ikon för Unicode-längden](./media/user-guide/fx-events/image71.png)    | **Unicode-längden get** (*fx_unicode_length_get*) |
| ![Ikon för att hämta Unicode-namn](./media/user-guide/fx-events/image72.png)    | **Unicode-namn get** (*fx_unicode_name_get*) |
| ![Ikon för kort namn för Unicode-namn](./media/user-guide/fx-events/image73.png)    | **Unicode-kort namn Hämta** (*fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>Händelse beskrivningar

Följande beskriver varje enskild händelse.

### <a name="internal-logical-sector-cache-miss"></a>Intern logisk sektor cache missar 

#### <a name="internal-logical-sector-cache-miss"></a>Intern logisk sektor cache missar

**Ikonen** ![ Intern logisk sektor cache missar ikon](./media/user-guide/fx-events/image1.png)

**Beskrivning**

Den här händelsen representerar en intern FileX-cache för logisk sektor.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: sektor.
- Info-fält 3: totalt antal Cachemissar.
- Info fält 4: cachestorlek.

### <a name="internal-directory-cache-miss"></a>Intern katalog-Cachemissar

#### <a name="internal-directory-cache-miss"></a>Intern katalog-Cachemissar

**Ikonen** ![ Ikon för internt katalog-Cachemissar](./media/user-guide/fx-events/image2.png)

**Beskrivning** 

Den här händelsen representerar ett internt FileX Directory-Cachemissar.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: totalt antal Cachemissar.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-media-flush"></a>Intern medie tömning 

#### <a name="internal-media-flush"></a>Intern medie tömning

**Ikonen** ![ Ikon för internt medie tömning](./media/user-guide/fx-events/image3.png)

**Beskrivning**

Den här händelsen representerar en intern FileX medie tömning.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: antal skadade sektorer.
- Informations fält 3: används inte.
- Info fält 4: används inte.


### <a name="internal-directory-entry-read"></a>Läsning av intern katalog post 

#### <a name="internal-directory-entry-read"></a>Läsning av intern katalog post

**Ikonen** ![ Läs ikon för intern katalog post](./media/user-guide/fx-events/image4.png)

**Beskrivning**

Den här händelsen representerar en intern FileX-katalog post-händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-directory-entry-write"></a>Skrivning av intern katalog post

#### <a name="internal-directory-entry-write"></a>Skrivning av intern katalog post

**Ikonen** ![ Skriv ikon för intern katalog post](./media/user-guide/fx-events/image5.png)

**Beskrivning**

Den här händelsen representerar ett internt FileX för katalog poster.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-read"></a>Läst intern I/O-drivrutin 

#### <a name="internal-io-driver-read"></a>Läst intern I/O-drivrutin 

**Ikonen** ![ Läs ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image6.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutin.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: sektor.
- Informations fält 3: antal sektorer.
- Info fält 4: buffert pekare.

### <a name="internal-io-driver-write"></a>Intern I/O-drivrutin skrivning 

#### <a name="internal-io-driver-write"></a>Intern I/O-drivrutin skrivning 

**Ikonen** ![ Skriv ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image7.png)

**Beskrivning** 

Den här händelsen representerar en intern skrivnings händelse för FileX I/O-drivrutinen.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: sektor.
- Informations fält 3: antal sektorer.
- Info fält 4: buffert pekare.

### <a name="internal-io-driver-flush"></a>Intern I/O-drivrutins tömning 

#### <a name="internal-io-driver-flush"></a>Intern I/O-drivrutins tömning 

**Ikonen** ![ Intern I/O-drivrutin för driv rutins tömning](./media/user-guide/fx-events/image8.png)

**Beskrivning** 

Den här händelsen representerar en intern händelse av FileX I/O-drivrutinen.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-abort"></a>Intern I/O-drivrutin avbryts 

#### <a name="internal-io-dirver-abort"></a>Internt I/O-dirver Avbryt

**Ikonen** ![ Avbrotts ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image9.png)

**Beskrivning**

Den här händelsen representerar en intern FileX I/O-drivrutin.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-initialize"></a>Intern I/O-drivrutin initieras 

#### <a name="internal-io-driver-initialize"></a>Intern I/O-drivrutin initieras 

**Ikonen** ![ Initiera ikon för intern I/O-drivrutin](./media/user-guide/fx-events/image10.png)

**Beskrivning** 

Den här händelsen representerar en intern händelse för FileX I/O-drivrutinen.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-boot-sector-read"></a>Läs start sektor för intern I/O-drivrutin 

#### <a name="internal-io-driver-boot-sector-read"></a>Läs start sektor för intern I/O-drivrutin 

**Ikonen** ![ Läs ikon för intern I/O-drivrutinens start sektor](./media/user-guide/fx-events/image11.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O driv rutins start sektor.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: buffert pekare.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-release-sectors"></a>Interna I/O driv Rutins versions sektorer 

#### <a name="internal-io-driver-release-sectors"></a>Interna I/O driv rutins versions sektorer 

**Ikonen** ![ Intern I/O driv rutins ikon för versions sektorer](./media/user-guide/fx-events/image12.png)

**Beskrivning** 

Den här händelsen representerar en intern händelse för FileX I/O-drivrutiner.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: sektor.
- Informations fält 3: antal sektorer.
- Info fält 4: används inte.

### <a name="internal-io-driver-boot-sector-write"></a>Skriv åtgärd för intern I/O-drivrutins start sektor

#### <a name="internal-io-driver-boot-sector-write"></a>Skriv åtgärd för intern I/O-drivrutins start sektor 

**Ikonen** ![ Skriv ikon för intern I/O-drivrutinens start sektor](./media/user-guide/fx-events/image13.png)

**Beskrivning** 

Den här händelsen representerar en intern Skriv händelse för FileX I/O-drivrutin.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: buffert pekare.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="internal-io-driver-un-initialize"></a>Intern I/O-drivrutin avinitieras 

#### <a name="internal-io-driver-un-initialize"></a>Intern I/O-drivrutin avinitieras 

**Ikonen** ![ Ikon för intern I/O-drivrutin för avinitiering](./media/user-guide/fx-events/image14.png)

**Beskrivning** 

Den här händelsen representerar en intern FileX I/O-drivrutin som avinitieras.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.
</blockquote></td>

### <a name="directory-attributes-read"></a>Lästa katalogattribut 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**Ikonen** ![ Läs ikon för katalogattribut](./media/user-guide/fx-events/image15.png)

**Beskrivning** 

Den här händelsen representerar en Read-händelse för katalogattribut.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: bitmapp för attribut:

  | Attribut                         | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | 0x01  |
  |  Dold                           | protokollnumret 0x02  |
  |  System                           | (0x04)  |
  |  Volym                           | (0x08)  |
  |  Katalog                        | 0x10  |
  |  Arkiv                          | 0x20  |
- Info fält 4: används inte.

### <a name="directory-attributes-set"></a>Katalog-attribut har angetts 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**Ikonen** ![ Ikon för attribut uppsättning](./media/user-guide/fx-events/image16.png)

**Beskrivning** 

Den här händelsen representerar en katalog som anger ett katalog-attribut.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: bitmapp för attribut:

  |  Attribut                        | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | 0x01  |
  |  Dold                           | protokollnumret 0x02  |
  |  System                           | (0x04)  |
  |  Arkiv                          | 0x20  |
- Info fält 4: används inte.

### <a name="directory-create"></a>Skapa katalog 

#### <a name="fx_directory_create"></a>fx_directory_create

**Ikonen** ![ Ikon för att skapa katalog](./media/user-guide/fx-events/image17.png)

**Beskrivning** 

Den här händelsen representerar en händelse för katalog skapande.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-default-get"></a>Hämta katalog standard 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**Ikonen** ![ Hämta ikon för katalog standard](./media/user-guide/fx-events/image18.png)

**Beskrivning** 

Den här händelsen representerar en händelse för katalog standard uppsättning.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: en pekare till retur Sök vägs namnet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-default-set"></a>Katalog standard uppsättning 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**Ikonen** ![ Ikon för katalog standard uppsättning](./media/user-guide/fx-events/image19.png)

**Beskrivning** 

Den här händelsen representerar en händelse för katalog standard uppsättning.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot nytt standard Sök vägs namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-delete"></a>Ta bort katalog 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**Ikonen** ![ Ikonen Ta bort katalog](./media/user-guide/fx-events/image20.png)

**Beskrivning** 

Den här händelsen representerar en katalog borttagnings händelse.

**Informations fält**
- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-first-entry-find"></a>Hitta katalog första posten 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**Ikonen** ![ Hitta ikon för första katalog posten](./media/user-guide/fx-events/image21.png)

**Beskrivning** 

Den här händelsen representerar en händelse för katalog första posten.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-first-full-entry-find"></a>Katalog-första fullständiga post Sök 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**Ikonen** ![ Hitta ikon för första katalog start posten](./media/user-guide/fx-events/image22.png)

**Beskrivning** 

Den här händelsen representerar en katalog för första posten för att hitta en katalog.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-information-get"></a>Hämta katalog information 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**Ikonen** ![ Ikon för Hämta katalog information](./media/user-guide/fx-events/image23.png)

**Beskrivning** 

Den här händelsen representerar en händelse för att hämta katalog information.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-local-path-clear"></a>Rensa katalogens lokala sökväg 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**Ikonen** ![ Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image24.png)

**Beskrivning** 

Den här händelsen representerar en händelse av en lokal katalog Sök väg.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-local-path-get"></a>Hämta lokal sökväg för katalog 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**Ikonen** ![ Hämta ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image25.png)

**Beskrivning** 

Den här händelsen representerar en händelse för en lokal katalog Sök väg.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: en pekare till retur Sök vägs namnet.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-local-path-restore"></a>Återställning av lokal sökväg för katalog 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**Ikonen** ![ Ikon för återställning av lokal sökväg för katalog](./media/user-guide/fx-events/image26.png)

**Beskrivning** 

Den här händelsen representerar en händelse för återställning av lokal katalog Sök väg.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot lokal sökväg.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-local-path-set"></a>Lokal katalog Sök väg uppsättning 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**Ikonen** ![ Ikon för lokal sökväg för katalog](./media/user-guide/fx-events/image27.png)

**Beskrivning** 

Den här händelsen representerar en händelse för lokal katalog Sök väg.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot lokal sökväg.
- Info-fält 3: pekar mot nytt Sök vägs namn.
- Info fält 4: används inte.

### <a name="directory-long-name-get"></a>Katalogens långa namn Hämta 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**Ikonen** ![ Hämta ikon för katalogens långa namn](./media/user-guide/fx-events/image28.png)

**Beskrivning** 

Den här händelsen representerar en händelse för katalog långa namn get.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot kort fil namn.
- Info-fält 3: pekar på långt fil namn.
- Info fält 4: används inte.

### <a name="directory-name-test"></a>Katalog namns test 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**Ikonen** ![ Ikon för katalog namns test](./media/user-guide/fx-events/image29.png)

**Beskrivning** 

Den här händelsen representerar ett test händelse för katalog namn.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-next-entry-find"></a>Sök efter katalog nästa post 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**Ikonen** ![ Sök ikon för katalog nästa post](./media/user-guide/fx-events/image30.png)

**Beskrivning** 

Den här händelsen representerar en katalog nästa post hitta händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-next-full-entry-find"></a>Sök i katalog nästa fullständiga post 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**Ikonen** ![ Sök ikon för nästa fullständiga post-katalog](./media/user-guide/fx-events/image31.png)

**Beskrivning**

Den här händelsen representerar en katalog nästa post hitta händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till katalog namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="directory-rename"></a>Byt namn på katalog 

#### <a name="fx_directory_rename-event"></a>fx_directory_rename händelse

**Ikonen** ![ Ikon för katalog namn](./media/user-guide/fx-events/image32.png)

**Beskrivning**

Den här händelsen representerar en händelse för katalog namnbyte.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på gammalt katalog namn.
- Info-fält 3: pekar på nytt katalog namn.
- Info fält 4: används inte.

### <a name="directory-short-name-get"></a>Katalog kort namn Hämta 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**Ikonen** ![ Katalog kort namn Hämta ikon](./media/user-guide/fx-events/image33.png)

**Beskrivning**

Den här händelsen representerar en händelse för kort för katalog kort namn.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot långt fil namn.
- Info-fält 3: pekar mot kort fil namn.
- Info fält 4: används inte.

### <a name="file-allocate"></a>Fil tilldelning 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**Ikonen** ![ Fil tilldelnings ikon](./media/user-guide/fx-events/image34.png)

**Beskrivning**

Den här händelsen representerar en fil tilldelnings händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Informations fält 2: begärd storlek.
- Info-fält 3: aktuell storlek.
- Info fält 4: ny storlek.

### <a name="file-attributes-read"></a>Lästa filattribut 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**Ikonen** ![ Läs ikon för filattribut](./media/user-guide/fx-events/image35.png)

**Beskrivning**

Den här händelsen representerar filattributen Read event.

**Informations fält**

- Informations fält 1: pekar mot mediet. 
- Info fält 2: bitmapp för attribut:

  |  Behörighet                         | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | 0x01  |
  |  Dold                           | protokollnumret 0x02  |
  |  System                           | (0x04)  |
  |  Volym                           | (0x08)  |
  |  Katalog                        | 0x10  |
  |  Arkiv                          | 0x20  |
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="file-attributes-set"></a>Angivna filattribut 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**Ikonen** ![ Ikonen filattribut ange](./media/user-guide/fx-events/image36.png)

**Beskrivning** 

Den här händelsen representerar en händelse som anger filattribut.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på fil namn. 
- Informations fält 3: bitmapp för attribut:

  | Attribut                         | Värde        |
  |---------------------------------- | --------|
  |  Skrivskydd                        | 0x01  |
  |  Dold                           | protokollnumret 0x02  |
  |  System                           | (0x04)  |
  |  Arkiv                          | 0x20  |
- Info fält 4: används inte.

### <a name="file-best-effort-allocate"></a>Bästa fördelar med fil arbete 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**Ikonen** ![ Ikon för att allokera bästa ansträngning](./media/user-guide/fx-events/image37.png)

**Beskrivning** 

Den här händelsen representerar en metod för att allokera en fil.

**Informations fält**

- Info fält 1: pekar mot filen.
- Informations fält 2: begärd storlek.
- Info-fält 3: den faktiska storlek som har tilldelats.
- Info fält 4: används inte.

### <a name="file-close"></a>Stäng fil 

#### <a name="fx_file_close"></a>fx_file_close

**Ikonen** ![ Fil stängnings ikon](./media/user-guide/fx-events/image38.png)

**Beskrivning** 

Den här händelsen representerar en fil stängnings händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Info fält 2: fil storlek.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="file-create"></a>Skapa fil

#### <a name="fx_file_create"></a>fx_file_create

**Ikonen** ![ Ikon för fil skapande](./media/user-guide/fx-events/image39.png)

**Beskrivning**

Den här händelsen representerar en händelse för att skapa en fil.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på fil namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="file-date-time-set"></a>Datum och tid för filen 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**Ikonen** ![ Ikon för datum/tid för fil uppsättning](./media/user-guide/fx-events/image40.png)

**Beskrivning**

Den här händelsen representerar en händelse för fil datum/tids uppsättning.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på fil namn.
- Info-fält 3: år.
- Info fält 4: månad.

### <a name="file-delete"></a>Ta bort fil 

#### <a name="fx_file_delete"></a>fx_file_delete

**Ikonen** ![ Fil borttagnings ikon](./media/user-guide/fx-events/image41.png)

**Beskrivning**

Den här händelsen representerar en fil borttagnings händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på fil namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="file-open"></a>Öppna fil 

#### <a name="fx_file_open"></a>fx_file_open

**Ikonen** ![ Fil öppnings ikon](./media/user-guide/fx-events/image42.png)

**Beskrivning**

Den här händelsen representerar en fil öppnings händelse.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot fil kontroll blocket.
- Info fält 3: pekar på fil namn.
- Info-fält 4: öppen typ:

  |  Öppen typ                        | Värde        |
  |---------------------------------- | --------|
  |  Öppna för läsning                    | 0x00  |
  |  Öppna för skrivning                   | 0x01  |
  |  Snabb öppen för läsning               | protokollnumret 0x02  |

### <a name="file-read"></a>Fil läsning 

#### <a name="fx_file_read"></a>fx_file_read

**Ikonen** ![ Fil läsnings ikon](./media/user-guide/fx-events/image43.png)

**Beskrivning**

Den här händelsen representerar en fil läsnings händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Info fält 2: buffert pekare.
- Info-fält 3: begär ande storlek.
- Info fält 4: verklig storlek läst.

### <a name="file-relative-seek"></a>Fil relativ sökning 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**Ikonen** ![ Ikon för fil relativ sökning](./media/user-guide/fx-events/image44.png)

**Beskrivning**

Den här händelsen representerar en fil relativ sökning-händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Informations fält 2: byte förskjutning.
- Informations fält 3: Sök från:

  | Händelse                             | Värde        |
  |---------------------------------- | --------|
  |  Från början                   | 0x00  |
  |  Från slut                         | 0x01  | 
  |  Vidarebefordra                          | protokollnumret 0x02  |
  |  Bakåt                         | (0x03)  |
- Info fält 4: föregående offset.

### <a name="file-rename"></a>Byt namn på fil 

#### <a name="fx_file_rename"></a>fx_file_rename

**Ikonen** ![ Ikon för fil namn](./media/user-guide/fx-events/image45.png)

**Beskrivning**

Den här händelsen representerar en händelsen fil namn.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot gammalt fil namn.
- Info-fält 3: pekar på nytt fil namn.
- Info fält 4: används inte.

### <a name="file-seek"></a>Fil sökning 

#### <a name="fx_file_seek"></a>fx_file_seek

**Ikonen** ![ Fil Sök ikon](./media/user-guide/fx-events/image46.png)

**Beskrivning**

Den här händelsen representerar en fil söknings händelse.

**Informations fält** 

- Info fält 1: pekar mot filen.
- Informations fält 2: byte förskjutning.
- Info-fält 3: föregående offset.
- Info fält 4: används inte.

### <a name="file-truncate"></a>Filen trunkeras 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**Ikonen** ![ Ikon för fil trunkering](./media/user-guide/fx-events/image47.png)

**Beskrivning**

Den här händelsen representerar en fil trunkerar händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Informations fält 2: begärd storlek.
- Info-fält 3: föregående storlek.
- Info fält 4: ny storlek.

### <a name="file-truncate-release"></a>Frigör fil trunkerad 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**Ikonen** ![ Ikonen för att trunkera en fil](./media/user-guide/fx-events/image48.png)

**Beskrivning**

Den här händelsen representerar en fil trunkerar händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Informations fält 2: begärd storlek.
- Info-fält 3: föregående storlek.
- Info fält 4: ny storlek.

### <a name="file-write"></a>Fil skrivning 

#### <a name="fx_file_write"></a>fx_file_write 

**Ikonen** ![ Fil skrivnings ikon](./media/user-guide/fx-events/image49.png)

**Beskrivning**

Den här händelsen representerar en fil skrivnings händelse.

**Informations fält**

- Info fält 1: pekar mot filen.
- Info fält 2: buffert pekare.
- Info-fält 3: begär ande storlek.
- Info fält 4: den faktiska storlek som skrivits.

### <a name="media-abort"></a>Medie avbrott 

#### <a name="fx_media_abort"></a>fx_media_abort 

**Ikonen** ![ Ikon för medie avbrott](./media/user-guide/fx-events/image50.png)

**Beskrivning**

Den här händelsen representerar ett avbrotts händelse för media.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="media-cache-invalidate"></a>Ogiltig cachelagring av media

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**Ikonen** ![ Ikon för att verifiera medie cache](./media/user-guide/fx-events/image51.png)

**Beskrivning**

Den här händelsen representerar en händelse i medie cachen som är ogiltig.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="media-check"></a>Medie kontroll 

#### <a name="fx_media_check"></a>fx_media_check

**Ikonen** ![ Ikon för medie kontroll](./media/user-guide/fx-events/image52.png)

**Beskrivning**

Den här händelsen representerar en medie kontroll händelse.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Info fält 2: Scratch-minnes pekare.
- Info fält 3: minnes storlek för virtuellt minne.
- Informations fält 4: fel-bitars mappning:

  | Typ av fel                        | Värde        |
  |---------------------------------- | --------|
  |  Fel i FAT-kedja                  | 0x01  |
  |  Katalog fel                  | protokollnumret 0x02  |
  |  Fel i förlorad kluster               | (0x04)  |
  |  Fil storleks fel                  | (0x08)  |

### <a name="media-close"></a>Medie stängning 

#### <a name="fx_media_close"></a>fx_media_close

**Ikonen** ![ Ikon för medie stängning](./media/user-guide/fx-events/image53.png)

**Beskrivning**

Den här händelsen representerar en medie stängnings händelse.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="media-flush"></a>Medie tömning 

#### <a name="fx_media_flush"></a>fx_media_flush

**Ikonen** ![ Ikon för medie tömning](./media/user-guide/fx-events/image54.png)

**Beskrivning**

Den här händelsen representerar en händelse för medie tömning.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="media-format"></a>Medie format 

#### <a name="fx_media_format"></a>fx_media_format

**Ikonen** ![ Ikon för medie format](./media/user-guide/fx-events/image55.png)

**Beskrivning**

Den här händelsen representerar en medie format händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Informations fält 2: antal rot poster.
- Info-fält 3: sektorer.
- Info fält 4: sektorer per kluster.

### <a name="media-open"></a>Mediet är öppet 

#### <a name="fx_media_open"></a>fx_media_open

**Ikonen** ![ Medie öppnings ikon](./media/user-guide/fx-events/image56.png)

**Beskrivning**

Den här händelsen representerar en medie öppnings händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till medie driv rutins post.
- Informations fält 3: minnes pekare.
- Info fält 4: minnes storlek.

### <a name="media-read-media-read"></a>Läst Media läsning 

#### <a name="fx_media_read"></a>fx_media_read

**Ikonen** ![ Medie läsnings ikon](./media/user-guide/fx-events/image57.png)

**Beskrivning**

Den här händelsen representerar en medie läsnings händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: logisk sektor.
- Info-fält 3: buffert pekare.
- Info fält 4: lästa byte.

### <a name="media-space-available"></a>Tillgängligt medie utrymme 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**Ikonen** ![ Ikon för tillgängligt medie utrymme](./media/user-guide/fx-events/image58.png)

**Beskrivning**

Den här händelsen representerar en händelse för medie utrymme som är tillgänglig.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Informations fält 2: tillgängliga byte-pekare.
- Informations fält 3: antal lediga kluster.
- Info fält 4: används inte.

### <a name="media-volume-get"></a>Hämta medie volym 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**Ikonen** ![ Ikon för Hämta medie volym](./media/user-guide/fx-events/image59.png)

**Beskrivning**

Den här händelsen representerar en händelse för medie volym get.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på volym namn.
- Info-fält 3: volym källa.
- Info fält 4: används inte.

### <a name="media-volume-set"></a>Medie volym uppsättning 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**Ikonen** ![ Ikon för medie volym uppsättning](./media/user-guide/fx-events/image60.png)

**Beskrivning**

Den här händelsen representerar en händelse för en medie volym uppsättning.

**Informations fält** 
- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar på volym namn.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="media-write"></a>Medie skrivning 

#### <a name="fx_media_write"></a>fx_media_write

**Ikonen** ![ Ikon för medie skrivning](./media/user-guide/fx-events/image61.png)

**Beskrivning**

Den här händelsen representerar en medie Skriv händelse.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: logisk sektor.
- Info-fält 3: buffert pekare.
- Info fält 4: skrivna byte.

### <a name="system-date-get"></a>System datum get 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**Ikonen** ![ Ikonen system datum get](./media/user-guide/fx-events/image62.png)

**Beskrivning**

Den här händelsen representerar en händelse för system datum get.

**Informations fält**

- Informations fält 1: år.
- Info fält 2: månad.
- Info-fält 3: dag.
- Info fält 4: används inte.

### <a name="system-date-set"></a>System datum uppsättning 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**Ikonen** ![ Ikon för system datum uppsättning](./media/user-guide/fx-events/image63.png)

**Beskrivning**

Den här händelsen representerar en händelse för system datum uppsättning.

**Informations fält**

- Informations fält 1: år.
- Info fält 2: månad.
- Info-fält 3: dag.
- Info fält 4: används inte.

### <a name="system-initialize"></a>System initiering 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**Ikonen** ![ Ikon för system initiering](./media/user-guide/fx-events/image64.png)

**Beskrivning**

Den här händelsen representerar en händelse som startar om systemet.

**Informations fält**

- Informations fält 1: används inte.
- Informations fält 2: används inte.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="system-time-get"></a>Hämta system tid 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**Ikonen** ![ Ikonen system tid get](./media/user-guide/fx-events/image65.png)

**Beskrivning**

Den här händelsen representerar en händelse för system tid get.

**Informations fält** 

- Informations fält 1: timme.
- Info fält 2: minute.
- Info-fält 3: sekund.
- Info fält 4: används inte.

### <a name="system-time-set"></a>System tids uppsättning 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**Ikonen** ![ Ikon för system tids uppsättning](./media/user-guide/fx-events/image66.png)

**Beskrivning**

Den här händelsen representerar en händelse för system tids uppsättning.

**Informations fält**

- Informations fält 1: timme.
- Info fält 2: minute.
- Info-fält 3: sekund.
- Info fält 4: används inte.

### <a name="unicode-directory-create"></a>Skapa Unicode-katalog 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**Ikonen** ![ Ikon för att skapa Unicode-katalogen](./media/user-guide/fx-events/image67.png)

**Beskrivning**

Den här händelsen representerar en händelse för att skapa Unicode-katalogen.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot Unicode-namn.
- Informations fält 3: storlek på Unicode-namn.
- Info fält 4: pekar mot kort namn.

### <a name="unicode-directory-rename"></a>Byt namn på Unicode-katalog 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**Ikonen** ![ Ikon för byte i Unicode-katalog](./media/user-guide/fx-events/image68.png)

**Beskrivning**

Den här händelsen representerar en byte-händelse i Unicode-katalogen.

**Informations fält** 

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot Unicode-namn.
- Informations fält 3: storlek på Unicode-namn.
- Info fält 4: pekar mot kort namn.

### <a name="unicode-file-create"></a>Skapa Unicode-fil 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**Ikonen** ![ Ikon för att skapa Unicode-fil](./media/user-guide/fx-events/image69.png)

**Beskrivning**

Den här händelsen representerar en händelse för att skapa Unicode-filer.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot Unicode-namnet.
- Informations fält 3: storlek på Unicode-namn.
- Info fält 4: pekar mot kort namn.

### <a name="unicode-file-rename"></a>Byt namn på Unicode-fil 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**Ikonen** ![ Ikon för byte av Unicode-fil](./media/user-guide/fx-events/image70.png)

**Beskrivning**

Den här händelsen representerar en händelse för byte av Unicode-fil.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekar mot Unicode-namn.
- Informations fält 3: storlek på Unicode-namn.
- Info fält 4: pekar mot kort namn.

### <a name="unicode-length-get"></a>Unicode-längd Hämta 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**Ikonen** ![ Hämta ikon för Unicode-längd](./media/user-guide/fx-events/image71.png)

**Beskrivning**

Den här händelsen representerar en händelse med Unicode-längd.

**Informations fält**

- Informations fält 1: pekar mot Unicode-namnet.
- Informations fält 2: längd.
- Informations fält 3: används inte.
- Info fält 4: används inte.

### <a name="unicode-name-get"></a>Hämta Unicode-namn 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**Ikonen** ![ Ikon för att hämta Unicode-namn](./media/user-guide/fx-events/image72.png)

**Beskrivning**

Den här händelsen representerar en händelse av Unicode-namn.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info-fält 2: kort källans namn.
- Info-fält 3: målets Unicode-namn pekare.
- Info-fält 4: målets Unicode-namn längd.

### <a name="unicode-short-name-get"></a>Korta Unicode-namn Hämta 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**Ikonen** ![ Ikon för kort namn för Unicode-namn](./media/user-guide/fx-events/image73.png)

**Beskrivning**

Den här händelsen representerar en händelse för ett kort för att hämta Unicode-namn.

**Informations fält**

- Informations fält 1: pekar mot mediet.
- Info fält 2: pekare till käll-Unicode-namn.
- Informations fält 3: längd på Unicode-namn.
- Info fält 4: pekar mot kort namn.