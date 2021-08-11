---
title: Kapitel 5 – I/O-drivrutiner för Azure RTOS FileX
description: Det här kapitlet innehåller en beskrivning av I/O-drivrutiner för Azure RTOS FileX och är utformat för att hjälpa utvecklare att skriva programspecifika drivrutiner.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 163893119837a46479b3f346c2bd47d200de2af75232f91a23bbc3f64e20ea50
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782922"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Kapitel 5 – I/O-drivrutiner för Azure RTOS FileX

Det här kapitlet innehåller en beskrivning av I/O-drivrutiner för Azure RTOS FileX och är utformat för att hjälpa utvecklare att skriva programspecifika drivrutiner.

## <a name="io-driver-introduction"></a>Introduktion till I/O-drivrutin

FileX stöder flera medieenheter. Strukturen FX_MEDIA definierar allt som krävs för att hantera en medieenhet. Den här strukturen innehåller all medieinformation, inklusive mediespecifik I/O-drivrutin och associerade parametrar för att skicka information och status mellan drivrutinen och FileX. I de flesta system finns det en unik I/O-drivrutin för varje FileX-medieinstans.

## <a name="io-driver-entry"></a>I/O-drivrutinspost

Varje FileX I/O-drivrutin har en enda postfunktion som definieras av fx_media_open tjänstanropet.  Drivrutinspostfunktionen har följande format:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX anropar I/O-drivrutinspostfunktionen för att begära all fysisk mediaåtkomst, inklusive initiering och läsning av startsektor. Begäranden som görs till drivrutinen görs sekventiellt. FileX väntar alltså på att den aktuella begäran ska slutföras innan en annan begäran skickas.

## <a name="io-driver-requests"></a>I/O-drivrutinsbegäranden

Eftersom varje I/O-drivrutin har en enda postfunktion gör FileX specifika begäranden via mediakontrollblocket. Mer specifikt  **fx_media_driver_request** medlem **i FX_MEDIA** för att ange den exakta drivrutinsbegäran. I/O-drivrutinen kommunicerar om begäran lyckades eller misslyckades via **fx_media_driver_status** medlem **i FX_MEDIA**. Om drivrutinsbegäran lyckades placeras **FX_SUCCESS** i det här fältet innan drivrutinen returneras. Annars, om ett fel upptäcks, FX_IO_ERROR placeras i det här fältet.

### <a name="driver-initialization"></a>Drivrutinsinitiering

Även om den faktiska initieringsbearbetningen av drivrutiner är programspecifik består den vanligtvis av initiering av datastrukturer och eventuellt viss preliminär maskinvaru initiering. Den här begäran är den första som görs av FileX och görs inifrån fx_media_open tjänsten.

Om medieskrivningsskydd identifieras ska drivrutinsmedlemmen fx_media_driver_write_protect i FX_MEDIA vara inställd på FX_TRUE.

Följande medlemmar FX_MEDIA för I/O-drivrutinsinitieringsbegäran:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX tillhandahåller en mekanism för att informera programdrivrutinen när sektorer inte längre används. Detta är särskilt användbart för FLASH-minneshanterare som måste hantera alla logiska sektorer som används och som är mappade till FLASH.

Om sådana meddelanden om kostnadsfria sektorer krävs anger programdrivrutinen bara *fx_media_driver_free_sector_update* i den associerade **FX_MEDIA** strukturen till **FX_TRUE**. Efter uppsättningen gör FileX ett **_FX_DRIVER_RELEASE_SECTORS_** I/O-drivrutinsanrop som anger när en eller flera efterföljande sektorer blir lediga.

### <a name="boot-sector-read"></a>Läsa startsektor

I stället för att använda en standardläsningsbegäran, gör FileX en specifik begäran om att läsa mediets startsektor. Följande **FX_MEDIA** används för läsbegäran för I/O-drivrutinsstartsektor:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Måladress för startsektor.|

### <a name="boot-sector-write"></a>Skrivning av startsektor

I stället för att använda en standardskrivningsbegäran, gör FileX en specifik begäran om att skriva mediets startsektor. Följande **FX_MEDIA** används för skrivbegäran för I/O-drivrutinsstartsektor:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Källadress för startsektor.|

### <a name="sector-read"></a>Sektorläsning

FileX läser en eller flera sektorer i minnet genom att utfärda en läsbegäran till I/O-drivrutinen. Följande **FX_MEDIA** används för läsbegäran för I/O-drivrutinen:

|FX_MEDIA medlem|Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Logisk sektor att läsa|
|fx_media_driver_sectors|Antal sektorer som ska läsas|
|fx_media_driver_buffer|Målbuffert för sektorläsning|
|fx_media_driver_data_sector_read|Ange till FX_TRUE om en fildatasektor begärs. Annars FX_FALSE om en systemsektor (FAT eller katalogsektor) begärs.|
|fx_media_driver_sector_type|Definierar den explicita typen av sektor som begärs enligt följande:<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Sektorskrivning

FileX skriver en eller flera sektorer till det fysiska mediet genom att utfärda en skrivbegäran till I/O-drivrutinen. Följande FX_MEDIA används för skrivbegäran för I/O-drivrutinen:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Logisk sektor att skriva|
|fx_media_driver_sectors|Antal sektorer som ska skrivas|
|fx_media_driver_buffer|Källbuffert för sektorer som ska skrivas|
|fx_media_driver_system_write| Ange till FX_TRUE om en systemsektor begärs (FAT eller katalogsektor). Annars FX_FALSE om en fildatasektor begärs.|
|fx_media_driver_sector_type|Definierar den explicita typen av sektor som begärs enligt följande:<br> <br>FX_FAT_SECTOR (2) <br> FX_DIRECTORY_SECTOR (3) <br>FX_DATA_SECTOR (4).|

### <a name="driver-flush"></a>Drivrutins flush

FileX rensar alla sektorer som för närvarande finns i drivrutinens sektorcache till det fysiska mediet genom att skicka en flush-begäran till I/O-drivrutinen. Om drivrutinen inte cachelagrar sektorer kräver den här begäran naturligtvis ingen drivrutinsbearbetning. Följande FX_MEDIA används för I/O-drivrutins flush-begäran:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Drivrutinsförsening

FileX informerar drivrutinen om att avbryta all ytterligare fysisk I/O-aktivitet med det fysiska mediet genom att skicka en begäran om avbrott till I/O-drivrutinen. Drivrutinen bör inte utföra några I/O igen förrän den har initierats på nytt. Följande FX_MEDIA för I/O-drivrutinens avbrottsbegäran:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Lanseringssektorer

Om fileX tidigare valdes av drivrutinen under initieringen informerar det drivrutinen när en eller flera efterföljande sektorer blir lediga. Om drivrutinen faktiskt är en FLASH-hanterare kan den här informationen användas för att meddela FLASH-hanteraren att dessa sektorer inte längre behövs. Följande **FX_MEDIA** används för begäran om I/O-publiceringssektorer:

|FX_MEDIA medlem| Innebörd|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Start av den kostnadsfria sektorn|
|fx_media_driver_sectors|Antal lediga sektorer|

### <a name="driver-suspension"></a>Drivrutinsavstängning

Eftersom I/O med fysiska medier kan ta lite tid är det ofta önskvärt att pausa anropstråden. Naturligtvis förutsätter detta att slutförandet av den underliggande I/O-åtgärden är avbrottsdriven. I så fall kan trådavstängning enkelt implementeras med en ThreadX-semaphore. När du har initierat indata- eller utdataåtgärden pausar I/O-drivrutinen sin egen interna I/O-semaphore (skapas med det första antalet noll under drivrutinsinitieringen). Som en del av bearbetningen av I/O-slutförande av drivrutinen anges samma I/O-semaphore, som i sin tur aktiverar den pausade tråden.

### <a name="sector-translation"></a>Sektoröversättning

Eftersom FileX ser mediet som linjära logiska sektorer görs I/O-begäranden som görs till I/O-drivrutinen med logiska sektorer. Det är drivrutinens ansvar att översätta mellan logiska sektorer och den fysiska geometrin för mediet, som kan innehålla krona, spår och fysiska sektorer. För FLASH- och RAM-diskmedier mappar de logiska sektorerna vanligtvis katalogen till fysiska sektorer. I vilket fall som helst är här de vanliga formlerna för att utföra mappningen mellan logiska och fysiska sektorer i I/O-drivrutinen:

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

Observera att fysiska sektorer börjar på en, medan logiska sektorer börjar på noll.

### <a name="hidden-sectors"></a>Dolda sektorer

Dolda sektorer finns före startposten på mediet. Eftersom de verkligen ligger utanför FAT-filsystemets layout måste de redovisas i varje logisk sektoråtgärd som drivrutinen gör.

### <a name="media-write-protect"></a>Media Write Protect

FileX-drivrutinen kan aktivera skrivskydd genom att ange fx_media_driver_write_protect i mediakontrollblocket. Detta leder till att ett fel returneras om några FileX-anrop görs i ett försök att skriva till mediet.

## <a name="sample-ram-driver"></a>Exempel på RAM-drivrutin

FileX-demonstrationssystemet levereras med en liten RAM-diskdrivrutin, som definieras i filen fx_ram_driver.c. Drivrutinen förutsätter ett 32 000 minnesutrymme och skapar en startpost för 256 128 byte-sektorer. Den här filen är ett bra exempel på hur du implementerar programspecifika FileX I/O-drivrutiner.

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
