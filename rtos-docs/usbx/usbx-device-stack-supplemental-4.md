---
title: Kapitel 4 – USBX PictBridge-implementering
description: UBSX stöder fullständig PictBridge-implementering både på värden och på enheten. PictBridge är ovanpå USBX PIMA-klassen på båda sidor.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2ef1809dac046d49b15aba000cabed6c9fd458a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828554"
---
# <a name="chapter-4---usbx-pictbridge-implementation"></a>Kapitel 4 – USBX PictBridge-implementering

UBSX stöder fullständig PictBridge-implementering både på värden och på enheten. PictBridge är ovanpå USBX PIMA-klassen på båda sidor.

PictBridge-standarden tillåter anslutning av en digital stillbilds kamera eller en smart telefon direkt till en skrivare utan en dator, vilket möjliggör direkt utskrift till vissa PictBridge-medvetna skrivare.

När en kamera eller telefon är ansluten till en skrivare är skrivaren USB-värden och kameran är USB-enheten. Men med PictBridge visas kameran som värd och kommandona drivs från kameran. Kameran är lagrings servern, skrivaren på lagrings klienten. Kameran är utskrifts klienten och skrivaren är naturligtvis utskrifts servern.

PictBridge använder USB som transport lager men förlitar sig på PTP (Picture Transfer Protocol) för kommunikations protokollet.

Följande är ett diagram över kommandon/svar mellan DPS-klienten och DPS-servern när ett utskrifts jobb inträffar:

![DPS-kommandon och-svar](./media/usbx-device-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>PictBridge-klient implementering

PictBridge på klienten kräver att USBX Device-stacken och PIMA-klassen körs först.

Ett Device Framework beskriver PIMA-klassen på följande sätt.

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
    0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,
    /* Configuration descriptor */
    0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

Pima-klassen använder ID-fältet 0x06 och har underklassen är 0x01 för stillbild och protokollet är 0x01 för PIMA 15740.

Tre slut punkter definieras i den här klassen. två mängder för att skicka/ta emot data och ett avbrott för händelser.

Till skillnad från andra USBX enhets implementeringar behöver inte PictBridge-programmet definiera en klass själva. I stället anropas funktionen ***ux_pictbridge_dpsclient_start***. Ett exempel är nedan.

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "ExpressLogic",13);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

De parametrar som skickas till PictBridge-klienten är följande.

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no
    : String of serial number
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

Nästa steg är för enheten och värden för att synkronisera och vara redo att utbyta information.

Detta görs genom att vänta på en händelse flagga på följande sätt.

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get(&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR,
    &actual_flags, UX_PICTBRIDGE_EVENT_TIMEOUT);
```

Om tillstånds datorn är i **DISCOVERY_COMPLETEs** tillstånd kommer kamera sidan (DPS-klienten) att samla in information om skrivaren och dess funktioner.

Om DPS-klienten är redo att acceptera ett utskrifts jobb anges dess status till **UX_PICTBRIDGE_NEW_JOB_TRUE**. Det kan kontrol leras nedan.

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)
/* We can print something … */
```

Efterföljande joib-beskrivningar måste fyllas på följande sätt:

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo -> ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo -> ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo -> ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo -> ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */
printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object -> ux_device_class_pima_object_compressed_size = IMAGE_LEN;
object -> ux_device_class_pima_object_offset = 0;
object -> ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object -> ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

PictBridge-klienten har nu ett utskrifts jobb för att göra och hämtar avbildnings blocken i taget från programmet via det motanrop som definierats i fältet

```C
jobinfo -> ux_pictbridge_jobinfo_object_data_read
```

Prototypen för den funktionen definieras som:

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

Kopiera ett data block från användar utrymmet för utskrift

### <a name="prototype"></a>Prototyp

```C
UINT ux_pictbridge_jobinfo_object_data_read( 
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,  
    ULONG object_offset,  
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när DPS-klienten behöver hämta ett data block för att skriva ut till mål PictBridge-skrivaren.

### <a name="parameters"></a>Parametrar

- **PictBridge**: pekare till klass instansen PictBridge.
- **object_buffer**: pekar mot objekt-buffert
- **object_offset**: där data blocket börjar läsas
- **object_length**: längden som ska returneras
- **actual_length**: den faktiska längden som returnerades

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0x01) programmet kunde inte hämta data.

### <a name="example"></a>Exempel

```C
/* Copy the object data. */
UINT ux_demo_object_data_copy(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);
    /* Update the actual length. */
    *actual_length = object_length;
    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a>PictBridge-värd implementering

Värd implementeringen av PictBridge skiljer sig från klienten.

Det första du gör i en PictBridge-värd miljö är att registrera klassen Pima som exemplet nedan visar:

```C
status = ux_host_stack_class_register(_ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

Den här klassen är det generiska PTP-lagret som sitter mellan USB-stacken och PictBridge-skiktet.

Nästa steg är att initiera PictBridge-standardvärden för utskrifts tjänster enligt följande:

| PictBridge-fält       | Värde                                  |
|------------------------|----------------------------------------|
| DpsVersion [0]          | 0x00010000                             |
| DpsVersion [1]          | 0x00010001                             |
| DpsVersion [2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| PrintServiceAvailable  | 0x30010000                             |
| Kvaliteter [0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Kvaliteter [1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Kvaliteter [2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Kvaliteter [3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| PaperSizes [0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| PaperSizes [1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| PaperSizes [2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| PaperSizes [3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| PaperSizes [4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| PaperTypes [0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| PaperTypes [1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| PaperTypes [2           | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| Filtypen [0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| Filtypen [1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| Filtypen [2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| Filfiltyp [3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DatePrints [0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DatePrints [1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DatePrints [2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints [0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints [1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints [2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimizes [0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimizes [1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimizes [2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Layouter [0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Layouter [1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Layouter [2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Layouter [3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| FixedSizes [0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| FixedSizes [1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| FixedSizes [2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| FixedSizes [3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| FixedSizes [4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| FixedSizes [5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| FixedSizes [6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Beskärningar [0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Beskärningar [1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Beskärningar [2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

Tillstånds datorn för DPS-värden ställs in på inaktiv och är redo att acceptera ett nytt utskrifts jobb.

Värd delen av PictBridge kan nu startas som exemplet nedan visar:

```C
/* Activate the pictbridge dpshost. */
status = ux_pictbridge_dpshost_start(&pictbridge, pima);

if (status != UX_SUCCESS)
    return;
```

Funktionen PictBridge Host kräver ett motanrop när data är klara att skrivas ut. Detta åstadkommer du genom att skicka en funktions pekare i den PictBridge värd strukturen enligt följande.

```C
/* Set a callback when an object is being received. */
pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

Den här funktionen har följande egenskaper.

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

Skriva ett data block för utskrift

### <a name="prototype"></a>Prototyp

```C
UINT ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge, 
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när DPS-servern behöver hämta ett data block från DPS-klienten för att skriva ut till den lokala skrivaren.

### <a name="parameters"></a>Parametrar

- **PictBridge**: pekare till klass instansen PictBridge.
- **object_buffer**: pekar mot objekt-buffert
- **object_offset**: där data blocket börjar läsas
- **total_length**: hela objekt längden
- **längd**: buffertens längd

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0x01) programmet kunde inte skriva ut data.

### <a name="example"></a>Exempel

```C
/* Copy the object data. */
UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;
    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
