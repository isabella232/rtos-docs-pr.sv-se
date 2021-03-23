---
title: Kapitel 5-I/O-drivrutiner för Azure återställnings tider FileX
description: Det här kapitlet innehåller en beskrivning av I/O-drivrutiner för Azure återställnings tider FileX och är utformat för att hjälpa utvecklare att skriva programspecifika driv rutiner.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826538"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Kapitel 5-I/O-drivrutiner för Azure återställnings tider FileX

Det här kapitlet innehåller en beskrivning av I/O-drivrutiner för Azure återställnings tider FileX och är utformat för att hjälpa utvecklare att skriva programspecifika driv rutiner.

## <a name="io-driver-introduction"></a>Introduktion till I/O-drivrutin

FileX stöder flera medie enheter. FX_MEDIAs strukturen definierar allt som krävs för att hantera en Media enhet. Den här strukturen innehåller all medie information, inklusive den leverantörsspecifika I/O-drivrutinen och tillhör ande parametrar för att skicka information och status mellan driv rutins-och FileX. I de flesta system finns det en unik I/O-drivrutin för varje FileX medie instans.

## <a name="io-driver-entry"></a>Post för I/O-drivrutin

Varje FileX I/O-drivrutin har en enda post-funktion som definieras av ***fx_media_open*** tjänst anropet. Funktionen driv rutins post har följande format:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX anropar funktionen I/O-drivrutin för att begära all fysisk medie åtkomst, inklusive initiering och start sektor läsning. Begär Anden som görs till driv rutinen görs i tur och ordning. t. ex. FileX väntar på att den aktuella begäran ska slutföras innan en annan begäran skickas.

## <a name="io-driver-requests"></a>I/O-drivrutin begär Anden

Eftersom varje I/O-drivrutin har en enda post-funktion, gör FileX vissa förfrågningar via medie kontroll blocket. Mer specifikt används  **fx_media_driver_request** medlem i **FX_MEDIA** för att ange den exakta driv rutins förfrågan. I/O-drivrutinen meddelar att begäran lyckades eller misslyckades via **fx_media_driver_status** medlem i **FX_MEDIA**. Om begäran om driv rutin har lyckats placeras **FX_SUCCESS** i det här fältet innan driv rutinen returneras. Annars placeras FX_IO_ERROR i det här fältet om ett fel upptäcks.

### <a name="driver-initialization"></a>Driv rutins initiering

Även om den faktiska initieringen av driv rutinen är programspecifik, består det vanligt vis av data struktur initiering och eventuellt preliminär maskin varu initiering. Den här begäran är den första som görs av FileX och görs inifrån den fx_media_open tjänsten.

Om medie Skriv skyddet identifieras ska driv rutinen fx_media_driver_write_protect medlem i FX_MEDIA anges till FX_TRUE.

Följande FX_MEDIA-medlemmar används för begäran om att initiera I/O-drivrutinen:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX tillhandahåller en mekanism för att informera program driv rutinen när sektorer inte längre används. Detta är särskilt användbart för minnes hanterare i FLASH som måste hantera alla inaktuella logiska sektorer som är kopplade till FLASH.

Om det krävs ett sådant meddelande om kostnads fria sektorer, ställer program driv rutinen bara in *fx_media_driver_free_sector_update* fältet i den associerade **FX_MEDIAs** strukturen för att **FX_TRUE**. Efter den här inställningen gör FileX ett **_FX_DRIVER_RELEASE_SECTORS_** I/O-drivrutin som anger när en eller flera efterföljande sektorer blir kostnads fria.

### <a name="boot-sector-read"></a>Läsning av start sektor

I stället för att använda en vanlig Read-begäran, gör FileX en särskild begäran om att läsa mediets start sektor. Följande **FX_MEDIA** -medlemmar används för i/O-drivrutinens start sektor Read-begäran:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Mål adress för start sektor.|

### <a name="boot-sector-write"></a>Skriv start sektor

I stället för att använda en vanlig skrivbegäran, gör FileX en särskild begäran om att skriva mediets start sektor. Följande **FX_MEDIA** -medlemmar används för i/O-drivrutinens start sektor Skriv förfrågan:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Källans adress för start sektorn.|

### <a name="sector-read"></a>Läs sektor

FileX läser en eller flera sektorer i minnet genom att utfärda en Read-begäran till I/O-drivrutinen. Följande **FX_MEDIA** -medlemmar används för i/O-drivrutinen Read-begäran:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Logisk sektor att läsa|
|fx_media_driver_sectors|Antal sektorer att läsa|
|fx_media_driver_buffer|Destinations-buffert för sektor (er) Läs|
|fx_media_driver_data_sector_read|Ange till FX_TRUE om en fil data sektor begärs. I annat fall FX_FALSE om en system sektor (FAT eller katalog sektor) begärs.|
|fx_media_driver_sector_type|Definierar den explicita typ av sektor som begärs enligt följande:<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Sektor skrivning

FileX skriver en eller flera sektorer till de fysiska medierna genom att utfärda en skrivbegäran till I/O-drivrutinen. Följande FX_MEDIA-medlemmar används för i/O-drivrutinen Skriv förfrågan:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Logisk sektor att skriva|
|fx_media_driver_sectors|Antal sektorer att skriva|
|fx_media_driver_buffer|Source buffer för sektor (er) att skriva|
|fx_media_driver_system_write| Ange till FX_TRUE om en system sektor begärs (FAT eller katalog sektor). Annars FX_FALSE om en fil data sektor begärs.|
|fx_media_driver_sector_type|Definierar den explicita typ av sektor som begärs enligt följande:
FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4) |

### <a name="driver-flush"></a>Driv rutins tömning

FileX tömmer alla sektorer som för närvarande finns i driv Rutinens sektor-cache till det fysiska mediet genom att skicka en begäran om tömning till I/O-drivrutinen. Om driv rutinen inte cachelagrar sektorer behöver denna begäran naturligtvis ingen driv rutins bearbetning. Följande FX_MEDIA-medlemmar används för i/O-drivrutinen tömnings förfrågan:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Avbryt driv rutin

FileX informerar driv rutinen för att avbryta all ytterligare fysisk I/O-aktivitet med det fysiska mediet genom att utfärda en abort-begäran till I/O-drivrutinen. Driv rutinen ska inte utföra några I/O igen förrän den har startats om. Följande FX_MEDIA-medlemmar används för i/O-drivrutinens abort-begäran:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Versions sektorer

Om den tidigare valdes av driv rutinen under initieringen informerar FileX driv rutinen när en eller flera sektorer i följd blir kostnads fria. Om driv rutinen faktiskt är en FLASH Manager kan du använda den här informationen för att berätta för FLASH Manager att dessa sektorer inte längre behövs. Följande **FX_MEDIAs** medlemmar används för begäran om i/O-release-release-sektorn:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Början av den kostnads fria sektorn|
|fx_media_driver_sectors|Antal kostnads fria sektorer|

### <a name="driver-suspension"></a>Driv rutins SUS Pension

Eftersom I/O med fysiska media kan ta en stund, är det ofta önskvärt att pausa anrops tråden. Detta förutsätter att slut för ande av den underliggande i/O-åtgärden avbryts. I så fall, är det enkelt att göra en tråd upphängning med en ThreadX-semafor. När du har startat indata-eller utdata-åtgärden inaktive ras i/O-drivrutinen på den egna interna I/O-semaforen (skapas med det inledande antalet noll under driv rutins initieringen). Som en del av avbrotts processen i/O-slut för ande av driv rutinen anges samma I/O-semafor, vilket i sin tur aktiverar den pausade tråden.

### <a name="sector-translation"></a>Sektor Översättning

Eftersom FileX visar mediet som linjära logiska sektorer görs I/O-begäranden som görs till i/O-drivrutinen med logiska sektorer. Det är driv Rutinens ansvar att översätta mellan logiska sektorer och mediets fysiska geometri, som kan innehålla huvuden, spår och fysiska sektorer. För FLASH-och RAM-skivor mappar de logiska sektorerna vanligt vis katalog till fysiska sektorer. I så fall är det typiska formler för att utföra mappning av logiska till fysiska sektorer i i/O-drivrutinen:

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

Observera att fysiska sektorer börjar med en, medan logiska sektorer börjar på noll.

### <a name="hidden-sectors"></a>Dolda sektorer

Dolda sektorer fanns före start posten på mediet. Eftersom de verkligen ligger utanför omfånget för FAT-filsystemet måste de redovisas i varje logisk sektor åtgärd som driv rutinen gör.

### <a name="media-write-protect"></a>Skriv skydd för media

FileX-drivrutinen kan aktivera skriv skydd genom att ange fältet fx_media_driver_write_protect i medie kontroll blocket. Detta leder till att ett fel returneras om eventuella FileX-anrop görs i ett försök att skriva till mediet.

## <a name="sample-ram-driver"></a>Exempel på RAM-drivrutin

FileX demonstrations systemet levereras med en liten RAM-drivrutin, som definieras i filen fx_ram_driver. c. Driv rutinen förutsätter ett minnes utrymme på 32K och skapar en start post för 256 128 byte-sektorer. Den här filen ger ett användbart exempel på hur du implementerar programspecifika FileX I/O-drivrutiner.

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
