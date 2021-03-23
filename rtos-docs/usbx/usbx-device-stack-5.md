---
title: Kapitel 5 – överväganden för enhets klass i USBX
description: Lär dig mer om USBX enhets klass överväganden.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826541"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>Kapitel 5 – överväganden för enhets klass i USBX

## <a name="device-class-registration"></a>Registrering av enhets klass

Varje enhets klass följer samma princip för registrering. En struktur som innehåller vissa klass parametrar skickas till klass initierings funktionen.

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

Varje klass kan registreras, om du vill, en callback-funktion när en instans av klassen aktive ras. Återanropet anropas sedan av enhets stacken för att informera programmet om att en instans har skapats.

Programmet skulle ha i sitt innehåll 2 funktioner för aktivering och inaktive ring, som du ser i följande exempel.

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

Vi rekommenderar inte att du gör något i dessa funktioner, men för att komma ihåg instansen av klassen och synkronisera med resten av programmet.

## <a name="usb-device-storage-class"></a>Lagrings klass för USB-enhet

Lagrings klassen USB-enhet gör det möjligt för en lagrings enhet som är inbäddad i systemet att göras synlig för en USB-värd.

USB-enhetens lagrings klass tillhandahåller inte någon lagrings lösning. Den accepterar bara och tolkar de SCSI-begäranden som kommer från värden. När en av dessa begär Anden är ett Läs-eller Skriv kommando, anropar den ett fördefinierat anrop till en riktig lagrings enhets hanterare, till exempel en ATA-drivrutin eller en driv rutin för Flash-enheter.

När enhetens lagrings klass initieras, tilldelas en pekare till den klass som innehåller all information som behövs. Ett exempel anges nedan.

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

I det här exemplet är driv Rutinens lagrings strängar anpassade genom att tilldela sträng pekare till motsvarande parameter. Om någon av sträng pekarna lämnas till UX_NULL används standard strängen för Azure-återställnings tider.

I det här exemplet anges enhetens senaste block adress eller LBA och storleken på den logiska sektorn. LBA är antalet sektorer som är tillgängliga i mediet – 1. Block längden anges till 512 i det vanliga lagrings mediet. Den kan ställas in på 2048 för optiska enheter.

Programmet måste klara tre återanrops funktions pekare för att tillåta lagrings klassen att läsa, skriva och hämta status för mediet.

Prototyperna för Läs-och skriv funktionerna visas i exemplet nedan.

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

Plats:

- *Storage* är instansen av lagrings klassen.
- *LUN* är den LUN som kommandot dirigeras till.
- *data_pointer* är adressen till den buffert som ska användas för att läsa eller skriva.
- *number_blocks* är antalet sektorer som ska läsas/skrivas.
- *LBA* är sektor adressen som ska läsas.
- *media_status* ska fyllas i exakt som retur värde för medie status.

Returvärdet kan antingen ha värdet UX_SUCCESS eller UX_ERROR som anger att åtgärden lyckades eller misslyckades. Dessa åtgärder behöver inte returnera andra felkoder. Om det uppstår ett fel i en åtgärd, kommer lagrings klassen att anropa funktionen för status anrops återställning.

Den här funktionen har följande prototyp.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

Den anropande parametern media_id används inte för närvarande och bör alltid vara 0. I framtiden kan det användas för att särskilja flera lagrings enheter eller lagrings enheter med flera SCSI-LUN. Den här versionen av lagrings klassen har inte stöd för flera instanser av lagrings klassen eller lagrings enheter med flera SCSI-LUN.

Returvärdet är en SCSI-felkod som kan ha följande format.

- **Bits 0-7** Sense_key
- **Bits 8-15** Ytterligare Sense-kod
- **Bits 16-23** Ytterligare Sense Code-kvalificerare

I följande tabell finns möjliga kombinationer för Sense/ASC/ASCQ.

| Sense-nyckel | ASC | ASCQ | Beskrivning                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | INGEN KÄNSLA                                          |
| 01        | 17  | 01   | ÅTERSTÄLLDA DATA MED ÅTERFÖRSÖK                       |
| 01        | 18  | 00   | ÅTERSTÄLLDA DATA MED ECC                           |
| 02        | 04  | 01   | DEN LOGISKA ENHETEN ÄR INTE KLAR – BLI KLAR          |
| 02        | 04  | 02   | DEN LOGISKA ENHETEN ÄR INTE KLAR-INITIERING KRÄVS |
| 02        | 04  | 04   | DEN LOGISKA ENHETEN ÄR INTE KLAR-FORMAT PÅGÅR       |
| 02        | 04  | FF   | DEN LOGISKA ENHETEN ÄR INTE KLAR-ENHETEN ÄR UPPTAGEN          |
| 02        | 06  | 00   | INGEN REFERENS POSITION HITTADES                       |
| 02        | 08  | 00   | KOMMUNIKATIONS PROBLEM MED LOGISK ENHET                |
| 02        | 08  | 01   | TIMEOUT FÖR KOMMUNIKATION AV LOGISK ENHET               |
| 02        | 08  | 80   | BUFFERTÖVERSKRIDNING VID KOMMUNIKATION MELLAN LOGISKA ENHETER                |
| 02        | Punkterna  | 00   | MEDIUM SAKNAS                                |
| 02        | 54  | 00   | USB TILL VÄRD FÖR SYSTEM GRÄNSSNITTS PROBLEM              |
| 02        | 80  | 00   | OTILLRÄCKLIGA RESURSER                            |
| 02        | FF  | FF   | OKÄNT FEL                                     |
| 03        | 02  | 00   | INGEN SÖKNING HAR SLUTFÖRTS                                  |
| 03        | 03  | 00   | SKRIV FEL                                       |
| 03        | 10  | 00   | ID-CRC-FEL                                      |
| 03        | 11  | 00   | LÄSFEL SOM INTE HAR ÅTERSTÄLLTS                            |
| 03        | 12  | 00   | ADRESS MARKERINGEN HITTADES INTE FÖR FÄLTET ID               |
| 03        | 13  | 00   | DET GICK INTE ATT HITTA ADRESS MARKERINGEN FÖR DATA FÄLTET             |
| 03        | 14  | 00   | DEN REGISTRERADE ENTITETEN HITTADES INTE                         |
| 03        | 30  | 01   | DET GÅR INTE ATT LÄSA MEDIUM-OKÄNT FORMAT               |
| 03        | 31  | 01   | FORMAT KOMMANDOT MISSLYCKADES                             |
| 04        | 40  | NN   | DIAGNOSTISKT FEL PÅ KOMPONENTEN NN (80H-FFH)      |
| 05        | 6.1  | 00   | PARAMETER LIST LÄNGD FEL                       |
| 05        | 20  | 00   | OGILTIG KOMMANDO ÅTGÄRDS KOD                    |
| 05        | 21  | 00   | LOGISK BLOCK ADRESS UTANFÖR INTERVALLET                |
| 05        | 24  | 00   | OGILTIGT FÄLT I KOMMANDO PAKET                   |
| 05        | 25  | 00   | LOGISK ENHET STÖDS INTE                        |
| 05        | 26  | 00   | OGILTIGT FÄLT I PARAMETER LISTAN                   |
| 05        | 26  | 01   | PARAMETERN STÖDS INTE                           |
| 05        | 26  | 02   | OGILTIGT PARAMETER VÄRDE                           |
| 05        | 39  | 00   | ATT SPARA PARAMETRAR STÖDS INTE                     |
| 06        | 28  | 00   | ÄR INTE REDO FÖR REDO ÖVER GÅNG – MEDIET HAR ÄNDRATS     |
| 06        | 29  | 00   | ÅTERSTÄLLNING AV STRÖM VID ÅTERSTÄLLNING ELLER BUSS ENHETS ÅTERSTÄLLNING UTFÖRDES       |
| 06        | 2F  | 00   | KOMMANDON SOM RENSATS AV EN ANNAN INITIERARE             |
| 07        | 27  | 00   | SKRIV SKYDDADE MEDIA                             |
| 0B        | 4E  | 00   | ÖVERLAPPANDE KOMMANDO FÖRSÖK                      |

Det finns två ytterligare, valfria återanrop som programmet kan implementera. ett för att svara på ett **GET_STATUS_NOTIFICATION** kommando och det andra är att svara på **SYNCHRONIZE_CACHE** kommandot.

Om programmet vill hantera GET_STATUS_NOTIFICATION kommandot från värden ska det implementera ett återanrop med följande prototyp.

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

Plats:

- *Storage* är instansen av lagrings klassen.
- *media_id* används inte för närvarande. notification_class anger klassen för meddelandet.
- *media_notification* ska anges av programmet till den buffert som innehåller svaret på aviseringen.
- *media_notification_length* ska anges av programmet som ska innehålla längden på svars bufferten.

Returvärdet anger om kommandot lyckades eller inte ska vara antingen **UX_SUCCESS** eller **UX_ERROR**.

Om programmet inte implementerar det här återanropet, kommer USBX att meddela värden att kommandot inte har implementerats när du tar emot kommandot **GET_STATUS_NOTIFICATION** .

Kommandot **SYNCHRONIZE_CACHE** bör hanteras om programmet använder ett cacheminne för skrivningar från värden. En värd kan skicka det här kommandot om det vet att lagrings enheten ska kopplas från, till exempel i Windows, om du högerklickar på en enhets ikon i verktygsfältet och väljer "Mata ut \[ lagrings enhets namn \] ", kommer Windows att utfärda **SYNCHRONIZE_CACHE** kommandot till den enheten.

Om programmet vill hantera **GET_STATUS_NOTIFICATION** kommandot från värden ska det implementera ett återanrop med följande prototyp.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Plats:

- *Storage* är instansen av lagrings klassen.
- *LUN* -parameter anger vilken LUN som kommandot dirigeras till.
- *number_blocks* anger antalet block som ska synkroniseras.
- *LBA* är sektor adressen för det första blocket som ska synkroniseras.
- *media_status* ska fyllas i exakt som retur värde för medie status.

Returvärdet anger om kommandot lyckades eller inte ska vara antingen **UX_SUCCESS** eller **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>Flera SCSI-LUN

Enhetens lagrings klass för USBX stöder flera LUN. Därför är det möjligt att skapa en lagrings enhet som fungerar som en CD-ROM-skiva och en flash-disk på samma tid. I sådana fall skulle initieringen skilja sig något. Här är ett exempel på en flash-disk och CD-ROM:

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a>USB-enhet CDC-ACM-klass

USB-enhetens CDC-ACM-klass gör att ett USB-värdnamn kan kommunicera med enheten som en seriell enhet. Den här klassen baseras på USB-standarden och är en delmängd av CDC-standarden.

Ett CDC-ACM-kompatibelt enhets ramverk måste deklareras av enhets stacken. Ett exempel finns här nedan.

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

Klassen CDC-ACM använder en sammansatt enhets ramverk för att gruppera gränssnitt (kontroll och data). Därför bör du vidta åtgärder när du definierar enhets beskrivningen. USBX förlitar sig på IAD-beskrivningen för att veta internt hur man binder gränssnitt. IAD-beskrivningen måste deklareras före gränssnitten och innehålla det första gränssnittet i CDC-ACM-klassen och hur många gränssnitt som är kopplade till dem.

Klassen CDC-ACM använder också en funktions beskrivning för union som utför samma funktion som den nyare IAD-beskrivningen. Även om en union funktions beskrivning måste deklareras för historiska orsaker och kompatibilitet med värd sidan, används den inte av USBX.

Initieringen av CDC-ACM-klassen förväntar sig följande parametrar.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

De två definierade parametrarna är callback-pekare i de användar program som anropas när stacken aktive ras eller inaktive ras i den här klassen.

Den tredje parametern som definierats är en callback-pekare till det användar program som kommer att anropas när det finns en parameter ändring i rad kod eller rad status. T. ex., om det finns en begäran från värden för att ändra DTR-tillståndet till **True**, anropas återanropet i det användar program som kan kontrol lera rad tillstånd genom IOCTL-funktionen för att Kow-värden är klar för kommunikation.

CDC-ACM baseras på en USB-IF-standard och identifieras automatiskt av MACOs och Linux-operativsystem. På Windows-plattformar kräver den här klassen en INF-fil för Windows-version före 10. Windows 10 kräver inte några INF-filer. Vi tillhandahåller en mall för CDC-ACM-klassen, som du hittar i ***usbx_windows_host_files*** -katalogen. För senare versioner av Windows ska filen CDC_ACM_Template_Win7_64bit. inf användas (förutom Win10). Den här filen måste ändras för att återspegla det PID/VID som används av enheten. PID/VID är specifika för den slutgiltiga kunden när företaget och produkten registreras med USB-IF. I INF-filen finns fälten som ska ändras här.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

I enhets ramverket för CDC-ACM-enheten lagras PID/VID i enhets beskrivningen (se den enhets beskrivning som anges ovan).

När ett USB-värdnamn identifierar USB CDC-ACM-enheten kommer den att montera en serie klass och enheten kan användas med alla seriella terminaler-program. Se värd operativ systemet för referens.

API-funktionerna för CDC-ACM-klass definieras nedan.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Utföra IOCTL på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver utföra olika IOCTL-anrop till CDC ACM-gränssnittet

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: IOCTL-funktion som ska utföras.
- **parameter**: pekar mot en parameter som är speciell för IOCTL-anropet.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>IOCTL-funktioner:

| Funktion                                        | Värde |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

Utför IOCTL-uppsättningens rad kodning i CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver ange rad kodnings parametrar.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parameter**: pekare till en linje parameter struktur:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Returvärde

**UX_SUCCESS** (0X00) den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

Utför IOCTL-kodning på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver hämta rad kodnings parametrarna.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parameter**: pekare till en linje parameter struktur:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

Utför IOCTL Hämta linje tillstånd på CDC-ACM-gränssnittet

## <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver hämta linje tillstånds parametrarna.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parameter**: pekare till en linje parameter struktur:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

Ange linje tillstånd för IOCTL-uppsättning på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver hämta parametrar för linje tillstånd

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parameter**: pekare till en linje parameter struktur:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Utföra IOCTL ABORT-PIPE på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program måste avbryta en pipe. Om du till exempel vill avbryta en pågående skrivning ska UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT skickas som parametern.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parameter**: riktningen för rör:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0X53) ogiltig rör riktning.

### <a name="example"></a>Exempel

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Starta IOCTL-överföring på gränssnittet CDC-ACM

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program vill använda överföring med motringning.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parameter**: pekare till den Start överförings parameter strukturen:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0xFF)-överföringen har redan startats.
- **UX_MEMORY_INSUFFICIENT** (0X12) en minnesallokering misslyckades.

### <a name="example"></a>Exempel

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

Stoppa IOCTL-överföringen på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program vill sluta använda överföring med motringning.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parameter**: används inte

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) ingen kontinuerlig överföring.

### <a name="example"></a>Exempel

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

Läsa från CDC-ACM-pipe

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver läsa från indata-pipen (ut från värden i från enheten). Den blockeras.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **Buffer**: buffertens adress där data ska lagras.
- **requested_length**: den maximala längden som vi förväntar dig.
- **actual_length**: längden som returnerades i bufferten.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** -enheten (0x51) är inte längre i det konfigurerade läget.
- **UX_TRANSFER_NO_ANSWER** (0X22) inget svar från enheten. Enheten var förmodligen frånkopplad medan överföringen väntade.

### <a name="example"></a>Exempel

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

Skriva till en CDC-ACM-pipe

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver skriva till i data-pipe (från värden från-enheten). Den blockeras.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **Buffer**: buffertens adress där data lagras.
- **requested_length**: längden på bufferten som ska skrivas.
- **actual_length**: längden som returnerades till bufferten efter skrivning utförs.

### <a name="return-value"></a>Returvärde
- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** -enheten (0x51) är inte längre i det konfigurerade läget.
- **UX_TRANSFER_NO_ANSWER** (0X22) inget svar från enheten. Enheten var förmodligen frånkopplad medan överföringen väntade.

### <a name="example"></a>Exempel

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Skriver till en CDC-ACM-pipe med motringning

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver skriva till i data-pipe (från värden från-enheten). Den här funktionen är inte blockerad och slut för ande görs via en motringning som anges i UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Parametrar

- **cdc_acm**: pekar mot CDC-klassens instans.
- **Buffer**: buffertens adress där data lagras.
- **requested_length**: längden på bufferten som ska skrivas.
- **actual_length**: längden som returnerades till bufferten efter skrivning utförs

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** -enheten (0x51) är inte längre i det konfigurerade läget.
- **UX_TRANSFER_NO_ANSWER** (0X22) inget svar från enheten. Enheten var förmodligen frånkopplad medan överföringen väntade.

### <a name="example"></a>Exempel

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>USB-enhet CDC-ECM-klass

USB-enhet CDC-ECM-klassen gör att ett USB-värdnamn kan kommunicera med enheten som en Ethernet-enhet. Den här klassen baseras på USB-standarden och är en delmängd av CDC-standarden.

Ett CDC-ACM-kompatibelt enhets ramverk måste deklareras av enhets stacken. Ett exempel finns här nedan.

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

CDC-ECM-klassen använder en mycket liknande enhets beskrivnings metod för CDC-ACM och kräver även en IAD-beskrivning. Se CDC-ACM-klassen för definition.

Förutom det vanliga enhets ramverket kräver CDC-ECM särskilda sträng beskrivningar. Ett exempel anges nedan.

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

Beskrivningen av MAC-adress strängen används av CDC-ECM-klassen för att svara på värd frågor som den MAC-adress som enheten svarar på på TCP/IP-protokollet. Den kan ställas in på enhets valet men måste definieras här.

Initieringen av CDC-ECM-klassen är följande.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

Initieringen av den här klassen förväntar sig samma funktions återanrop för aktivering och inaktive ring, även om den är inställd på NULL så att ingen motringning utförs.

Nästa parametrar är för definitionen av nod-ID: n. 2 noder krävs för CDC-ECM, en lokal nod och en fjärrnod. Den lokala noden anger enhetens MAC-adress, medan fjärrnoden anger värdens MAC-adress. Fjärrnoden måste vara samma som den som har deklarerats i enhets ramverkets sträng beskrivning.

CDC-ECM-klassen har inbyggda API: er för överföring av data på båda sätt, men de är dolda för programmet när användar programmet kommer att kommunicera med USB Ethernet-enheten via NetX.

USBX CDC-ECM-klassen är nära kopplad till Azure återställnings tider NetX Network stack. Ett program som använder både NetX och USBX CDC-ECM-klass kommer att aktivera NetX-nätverks stacken på vanligt sätt, men du måste också aktivera USB-protokollstacken på följande sätt.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB-protokollstacken behöver bara aktive ras en gång och är inte särskilt för CDCECM, men krävs av alla USB-klasser som kräver NetX-tjänster.

CDC-ECM-klassen kommer att identifieras av MAC OS-och Linux-värdar. Men det finns ingen driv rutin som tillhandahålls av Microsoft Windows för att identifiera CDC-ECM internt. Vissa kommersiella produkter finns för Windows-plattformar och de tillhandahåller sin egen. inf-fil. Den här filen måste ändras på samma sätt som inf-mallen för CDC-ACM för att matcha PID/VID-USB-enheten.

## <a name="usb-device-hid-class"></a>HID-klass för USB-enhet

Med HID-klassen USB-enhet kan ett USB-värdnamn ansluta till en HID-enhet med vissa funktioner för HID-klienter.

USBX HID-enhets klass är relativt enkel jämfört med värd sidan. Den är nära knuten till enhetens funktions sätt och dess HID-beskrivning.

Alla HID-klienter måste först definiera ett HID Device Framework som i exemplet nedan.

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

HID-ramverket innehåller en gränssnitts beskrivning som beskriver klassen HID och underklassen HID-enhet. HID-gränssnittet kan vara en fristående klass eller en del av en sammansatt enhet.

För närvarande stöder USBX HID-klassen inte flera rapport-ID: n eftersom de flesta program bara kräver ett ID (ID noll). Kontakta oss om flera rapport-ID: n är en funktion som du är intresse rad av.

Initieringen av HID-klassen är som följer med ett USB-tangentbord som exempel.

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

Programmet måste skicka till HID-klassen en rapport beskrivning med en HID-rapport och dess längd. Rapport beskrivningen är en samling objekt som beskriver enheten. Mer information om HID-grammatiken hittar du i specifikationen HID USB-klass.

Förutom rapport beskrivningen skickar programmet ett anrop tillbaka när en HID-händelse inträffar.

USBX HID-klassen stöder följande HID-standardkommandon från värden.

| Kommando namn                             | Värde | Beskrivning                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Hämta en rapport från enheten                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Hämta vilo läges frekvensen för avbrotts slut punkten |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Hämta protokollet som körs på enheten           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Ställ in en rapport på enheten                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0A  | Ange inaktivitet för avbrotts slut punkten |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Hämta protokollet som körs på enheten           |

Rapporten hämta och ange är de vanligaste kommandona av HID för att överföra data fram och tillbaka mellan värden och enheten. Oftast skickar värden data på kontroll slut punkten, men kan ta emot data antingen på avbrotts slut punkten eller genom att utfärda ett GET_REPORT-kommando för att hämta data på kontroll slut punkten.

Klassen HID kan skicka data tillbaka till värden på avbrotts slut punkten med hjälp av funktionen ux_device_class_hid_event_set.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Ställa in en händelse på HID-klassen

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver skicka en HID-händelse tillbaka till värden. Funktionen blockeras inte, den placerar bara rapporten i en cirkulär kö och återgår till programmet.

### <a name="parameters"></a>Parametrar

- **HID**: pekar mot klass instansen HID.
- **hid_event**: pekaren till strukturen för HID-händelsen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) fel ledigt utrymme i cirkulär kö.

### <a name="example"></a>Exempel

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

Återanropet som definieras vid initieringen av HID-klassen utför motsatsen till att skicka en händelse. Den tar emot den händelse som skickas av värden. Prototypen för återanropet är följande.

### <a name="hid_callback"></a>hid_callback

Hämta en händelse från HID-klassen

### <a name="prototype"></a>Prototyp

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när värden skickar en HID-rapport till programmet.

### <a name="parameters"></a>Parametrar

- **HID**: pekar mot klass instansen HID.
- **hid_event**: pekaren till strukturen för HID-händelsen.

### <a name="example"></a>Exempel

I följande exempel visas hur du tolkar en händelse för ett HID-tangentbord:

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
