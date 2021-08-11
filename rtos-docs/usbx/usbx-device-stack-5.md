---
title: Kapitel 5 – Överväganden för USBX-enhetsklass
description: Lär dig mer om USBX-enhetsklassöverväganden.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b8fcfa251df9140d23b50a99f13f2755d2bdfae0ca6b9529633f25e263c7edcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798748"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>Kapitel 5 – Överväganden för USBX-enhetsklass

## <a name="device-class-registration"></a>Registrering av enhetsklass

Varje enhetsklass följer samma registreringsprincip. En struktur som innehåller specifika klassparametrar skickas till funktionen class initialize.

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

Varje klass kan även registrera en återanropsfunktion när en instans av klassen aktiveras. Motringning anropas sedan av enhetsstacken för att informera programmet om att en instans har skapats.

Programmet skulle i sin brödtext ha de 2 funktionerna för aktivering och inaktivering, som du ser i följande exempel.

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

Vi rekommenderar inte att du gör något inom dessa funktioner, utan att memorera instansen av klassen och synkronisera med resten av programmet.

## <a name="general-considerations-for-bulk-transfer"></a>Allmänna överväganden för massöverföring

Enligt USB 2.0-specifikationen måste en slutpunkt alltid överföra datanyttolaster med ett datafält som är mindre än eller lika med slutpunktens rapporterade wMaxPacketSize-värde. Storleken på ett datapaket är begränsad till bMaxPacketSize. Överföringen kan slutföras med följande fall
1. Slutpunkten har överfört exakt den mängd data som förväntas
2. När en enhet eller värdslutpunkt tar emot ett paket med en storlek som är mindre än den maximala paketstorleken (wMaxPacketSize). Det här korta paketet anger att det inte finns några fler datapaket kvar och överföringen är klar eller när alla datapaket som ska överföras är lika med wMaxPacketSize kan överföringens slut inte fastställas. För att överföringen ska slutföras måste ett ZLP-paket (Zero Length Packet) skickas kortpaket och nolllängdspaket innebära slutet på en massöverföring av data. Ovanstående överväganden gäller för API:er för massöverföring av rådata, t.ex. ux_device_class_cdc_acm_read().

## <a name="usb-device-storage-class"></a>USB-enhetsklass Storage enhet

Usb-enhetens lagringsklass gör att en lagringsenhet som är inbäddad i systemet kan göras synlig för en USB-värd.

USB-enhetens lagringsklass tillhandahåller inte en lagringslösning på egen hand. Den accepterar och tolkar bara SCSI-begäranden som kommer från värden. När en av dessa begäranden är ett läs- eller skrivkommando anropas ett fördefinierat anrop tillbaka till en verklig lagringsenhetshanterare, till exempel en ATA-enhetsdrivrutin eller en Flash-enhetsdrivrutin.

När du initierar enhetslagringsklassen ges en pekarstruktur till klassen som innehåller all information som behövs. Ett exempel visas nedan.

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

I det här exemplet anpassas drivrutinslagringssträngarna genom att tilldela sträng pekare till motsvarande parameter. Om någon av sträng pekaren lämnas till UX_NULL används standardvärdet Azure RTOS strängen.

I det här exemplet anges enhetens sista blockadress eller LASTA samt storleken på den logiska sektorn. Lba är antalet sektorer som är tillgängliga på mediet –1. Blocklängden är inställd på 512 på vanliga lagringsmedier. Det kan anges till 2048 för optiska enheter.

Programmet måste skicka tre återanropsfunktionspekare så att lagringsklassen kan läsa, skriva och hämta status för mediet.

Prototyperna för läs- och skrivfunktionerna visas i exemplet nedan.

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

- *storage* är instansen av lagringsklassen.
- *lun* är det LUN som kommandot dirigeras till.
- *data_pointer* är adressen till bufferten som ska användas för läsning eller skrivning.
- *number_blocks* är antalet sektorer som ska läsas/skrivas.
- *lba* är sektoradressen att läsa.
- *media_status* ska fyllas i exakt som returvärdet för återanrop av mediestatus.

Returvärdet kan antingen ha värdet UX_SUCCESS eller UX_ERROR indikerar en lyckad eller misslyckad åtgärd. De här åtgärderna behöver inte returnera några andra felkoder. Om det finns ett fel i någon åtgärd anropar lagringsklassen funktionen för statusanrop tillbaka.

Den här funktionen har följande prototyp.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

Anropsparametern media_id inte används för närvarande och bör alltid vara 0. I framtiden kan den användas för att särskilja flera lagringsenheter eller lagringsenheter med flera SCSI LUN. Den här versionen av lagringsklassen stöder inte flera instanser av lagringsklassen eller lagringsenheter med flera SCSI LUN.

Returvärdet är en SCSI-felkod som kan ha följande format.

- **Bitar 0–7** Sense_key
- **Bitar 8–15** Ytterligare Sense Code
- **Bitar 16–23** Ytterligare Sense Code-kvalificerare

Följande tabell innehåller möjliga kombinationer av Sense/ASC/ASCQ.

| Sense Key | ASC | ASCQ | Description                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | NO SENSE                                          |
| 01        | 17  | 01   | ÅTERSTÄLLDA DATA MED ÅTERFÖRSÖK                       |
| 01        | 18  | 00   | ÅTERSTÄLLDA DATA MED ECC                           |
| 02        | 04  | 01   | LOGISK ENHET ÄR INTE KLAR – BLIR REDO          |
| 02        | 04  | 02   | LOGISK ENHET ÄR INTE KLAR – INITIERING KRÄVS |
| 02        | 04  | 04   | LOGISK ENHET ÄR INTE KLAR – FORMATET PÅGÅR       |
| 02        | 04  | Ff   | LOGISK ENHET INTE KLAR – ENHETEN ÄR UPPTAGEN          |
| 02        | 06  | 00   | INGEN REFERENSPOSITION HITTADES                       |
| 02        | 08  | 00   | KOMMUNIKATIONSFEL FÖR LOGISK ENHET                |
| 02        | 08  | 01   | TIME-OUT FÖR KOMMUNIKATION FÖR LOGISK ENHET               |
| 02        | 08  | 80   | KOMMUNIKATION MED LOGISK ENHET HAR ÖVERSKRIDITS                |
| 02        | 3A  | 00   | MEDEL INTE NÄRVARANDE                                |
| 02        | 54  | 00   | FEL MED USB-TILL-VÄRD-SYSTEMGRÄNSSNITTET              |
| 02        | 80  | 00   | OTILLRÄCKLIGA RESURSER                            |
| 02        | Ff  | Ff   | OKÄNT FEL                                     |
| 03        | 02  | 00   | INGEN SÖK HAR SLUTFÖRTS                                  |
| 03        | 03  | 00   | SKRIVFEL                                       |
| 03        | 10  | 00   | ID CRC-FEL                                      |
| 03        | 11  | 00   | OÅTERKALLELIGT LÄSFEL                            |
| 03        | 12  | 00   | ADRESSMARKERING HITTADES INTE FÖR ID-FÄLTET               |
| 03        | 13  | 00   | ADRESSMARKERING HITTADES INTE FÖR DATAFÄLT             |
| 03        | 14  | 00   | DET GÅR INTE ATT HITTA DEN REGISTRERADE ENTITETEN                         |
| 03        | 30  | 01   | DET GÅR INTE ATT LÄSA MEDEL – OKÄNT FORMAT               |
| 03        | 31  | 01   | FORMAT-KOMMANDOT MISSLYCKADES                             |
| 04        | 40  | Nn   | DIAGNOSTIKFEL PÅ KOMPONENT-NN (80 H-FFH)      |
| 05        | 1A  | 00   | LÄNGDFEL FÖR PARAMETERLISTA                       |
| 05        | 20  | 00   | OGILTIG KOMMANDOÅTGÄRDSKOD                    |
| 05        | 21  | 00   | LOGISK BLOCKADRESS UTANFÖR INTERVALLET                |
| 05        | 24  | 00   | OGILTIGT FÄLT I KOMMANDOPAKET                   |
| 05        | 25  | 00   | LOGISK ENHET STÖDS INTE                        |
| 05        | 26  | 00   | OGILTIGT FÄLT I PARAMETERLISTAN                   |
| 05        | 26  | 01   | PARAMETERN STÖDS INTE                           |
| 05        | 26  | 02   | PARAMETERVÄRDET ÄR OGILTIGT                           |
| 05        | 39  | 00   | DET FINNS INTE STÖD FÖR ATT SPARA PARAMETRAR                     |
| 06        | 28  | 00   | INTE REDO FÖR ÖVERGÅNG – MEDIET HAR ÄNDRATS     |
| 06        | 29  | 00   | ÅTERSTÄLLNING AV STRÖM ELLER ÅTERSTÄLLNING AV BUSSENHET INTRÄFFADE       |
| 06        | 2F  | 00   | KOMMANDON SOM RENSAS AV EN ANNAN INITIERARE             |
| 07        | 27  | 00   | SKRIVA SKYDDADE MEDIA                             |
| 0B        | 4E  | 00   | ÖVERLAPPANDE KOMMANDOFÖRSÖK                      |

Det finns ytterligare två valfria återanrop som programmet kan implementera. den ena är till för **att GET_STATUS_NOTIFICATION** ett kommando och den andra används för att svara **SYNCHRONIZE_CACHE** kommandot.

Om programmet vill hantera kommandot GET_STATUS_NOTIFICATION från värden bör det implementera ett återanrop med följande prototyp.

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

- *storage* är instansen av lagringsklassen.
- *media_id* används inte för närvarande. notification_class anger meddelandeklassen.
- *media_notification* ska anges av programmet till bufferten som innehåller svaret för meddelandet.
- *media_notification_length* ska anges av programmet så att det innehåller längden på svarsbufferten.

Returvärdet anger om kommandot lyckades – ska vara antingen **UX_SUCCESS** eller **UX_ERROR**.

Om programmet inte implementerar det här återanropet meddelar USBX värden **att kommandot inte har** implementerats när GET_STATUS_NOTIFICATION-kommandot tas emot.

Kommandot **SYNCHRONIZE_CACHE** ska hanteras om programmet använder ett cacheminne för skrivningar från värden. En värd kan skicka det här kommandot om den vet att lagringsenheten är på väg att kopplas från, till exempel i Windows. Om du högerklickar på en flash-enhetsikon i verktygsfältet och väljer "Mata ut lagringsenhetens namn" kommer Windows att utfärda SYNCHRONIZE_CACHE-kommandot till \[ \] enheten. 

Om programmet vill hantera kommandot **GET_STATUS_NOTIFICATION** från värden bör det implementera ett återanrop med följande prototyp.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Plats:

- *storage* är instansen av lagringsklassen.
- *lun-parametern* anger vilket LUN kommandot dirigeras till.
- *number_blocks* anger antalet block som ska synkroniseras.
- *lba* är sektoradressen för det första blocket som ska synkroniseras.
- *media_status* ska fyllas i exakt som returvärdet för återanrop av mediestatus.

Returvärdet anger om kommandot lyckades – ska vara antingen **UX_SUCCESS** eller **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>Flera SCSI LUN

USBX-enhetens lagringsklass stöder flera LUN. Det är därför möjligt att skapa en lagringsenhet som fungerar som en CD-ROM och en Flash-disk på samma gång. I så fall skulle initieringen vara något annorlunda. Här är ett exempel på en Flash-disk och CD-ROM:

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

## <a name="usb-device-cdc-acm-class"></a>USB-enhetens CDC-ACM-klass

USB-enhetens CDC-ACM-klass gör att ett USB-värdsystem kan kommunicera med enheten som en seriell enhet. Den här klassen baseras på USB-standarden och är en delmängd av CDC-standarden.

Ett CDC-ACM-kompatibelt enhetsramverk måste deklareras av enhetsstacken. Ett exempel finns här nedan.

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

CDC-ACM-klassen använder ett sammansatt enhetsramverk för att gruppera gränssnitt (kontroll och data). Därför bör du vara försiktig när du definierar enhetsbeskrivningen. USBX förlitar sig på IAD-beskrivningen för att veta internt hur gränssnitt ska bindas. IAD-beskrivningen ska deklareras före gränssnitten och innehålla det första gränssnittet i CDC-ACM-klassen och hur många gränssnitt som är anslutna.

CDC-ACM-klassen använder också en union funktionell beskrivning som utför samma funktion som den nyare IAD-beskrivningen. Även om en funktionell union-beskrivning måste deklareras av historiska skäl och kompatibilitet med värdsidan, används den inte av USBX.

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

De två parametrar som definieras är återanropspekare till de användarprogram som anropas när stacken aktiverar eller inaktiverar den här klassen.

Den tredje parametern som definieras är en återanrops pekare till användarprogrammet som anropas när det finns en radkodning eller om rad tillståndsparametern ändras. När det t.ex. finns en begäran från värden om att ändra DTR-tillståndet till **TRUE** anropas återanropet. I det kan användarprogrammet kontrollera radtillstånd via IOCTL-funktionen till host är redo för kommunikation.

CDC-ACM baseras på en USB-IF-standard och identifieras automatiskt av MACOs och Linux-operativsystem. På Windows-plattformar kräver den här klassen en .inf-fil för Windows tidigare än 10. Windows 10 kräver inga INF-filer. Vi tillhandahåller en mall för CDC-ACM-klassen och  den finns i usbx_windows_host_files katalogen. För den senaste versionen Windows filen CDC_ACM_Template_Win7_64bit.inf användas (utom Win10). Den här filen måste ändras så att den återspeglar den PID/VID som används av enheten. PID/VID är specifik för den slutliga kunden när företaget och produkten registreras med USB-IF. I inf-filen finns de fält som ska ändras här.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

I enhetsramverket för CDC-ACM-enheten lagras PID/VID i enhetsbeskrivningen (se enhetsbeskrivningen som deklareras ovan).

När ett USB-värdsystem identifierar USB CDC-ACM-enheten, monterar den en serieklass och enheten kan användas med alla seriella terminalprogram. Se värdens operativsystem som referens.

API-funktionerna i CDC-ACM-klassen definieras nedan.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Utföra IOCTL på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver utföra olika ioctl-anrop till cdc acm-gränssnittet

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** Ioctl-funktionen som ska utföras.
- **parameter**: Pekare till en parameter som är specifik för ioctl-anropet.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Ioctl-funktioner:

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

Utföra IOCTL Set Line Coding i CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver ange parametrarna för radkodning.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parameter**: Pekare till en radparameterstruktur:

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

**UX_SUCCESS** (0x00) Den här åtgärden lyckades.

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

Utför IOCTL Get Line Coding i CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver hämta parametrarna för radkodning.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parameter**: Pekare till en radparameterstruktur:

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

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.

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

Utför IOCTL Get Line State i CDC-ACM-gränssnittet

## <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver hämta radtillståndsparametrarna.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parameter**: Pekare till en radparameterstruktur:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.

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

Utför IOCTL Set Line State i CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver hämta radtillståndsparametrarna

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parameter**: Pekare till en radparameterstruktur:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Utför IOCTL ABORT PIPE på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver avbryta en pipe. Om du till exempel vill avbryta en pågående skrivning UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT skickas som parametern .

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parameter:** Rörriktningen:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Ogiltig rörriktning.

### <a name="example"></a>Exempel

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Starta IOCTL-överföring i CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program vill använda överföring med återanrop.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parameter**: Pekare till parameterstrukturen Starta överföring:

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

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Överföring har redan startats.
- **UX_MEMORY_INSUFFICIENT** (0x12) En minnesallokering misslyckades.

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

Utföra IOCTL-överföringsstopp på CDC-ACM-gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program vill sluta använda överföring med återanrop.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parameter:** Används inte

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Ingen pågående överföring.

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

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver läsa från OUT-datapipe pipe (UT från värden, IN från enheten). Den blockerar.

> [!Note]
> Den här funktionen läser massdata från värden, så den väntar tills bufferten är full eller värden avslutar överföringen med ett kort paket (inklusive nolllängdspaket). Mer information finns i avsnittet Allmänna överväganden [**för massöverföring.**](#general-considerations-for-bulk-transfer)

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **buffer**: Buffertadress där data ska lagras.
- **requested_length:** Den maximala längd som vi förväntar oss.
- **actual_length:** Längden som returneras till bufferten.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Enheten är inte längre i det konfigurerade tillståndet.
- **UX_TRANSFER_NO_ANSWER** (0x22) Inget svar från enheten. Enheten kopplades förmodligen från medan överföringen väntade.

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

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver skriva till IN-datapipe pipe (IN från värden, OUT från enheten). Den blockerar.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **buffer**: Buffertadress där data lagras.
- **requested_length:** Längden på bufferten som ska skrivas.
- **actual_length:** Längden som returneras till bufferten när skrivning har utförts.

### <a name="return-value"></a>Returvärde
- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Enheten är inte längre i det konfigurerade tillståndet.
- **UX_TRANSFER_NO_ANSWER** (0x22) Inget svar från enheten. Enheten kopplades förmodligen från medan överföringen väntade.

### <a name="example"></a>Exempel

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Skriva till en CDC-ACM-pipe med återanrop

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver skriva till IN-datapipe pipe (IN från värden, OUT från enheten). Den här funktionen är icke-blockerande och slutförandet görs via en motringning i UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Parametrar

- **cdc_acm:** Pekare till cdc-klassinstansen.
- **buffer**: Buffertadress där data lagras.
- **requested_length:** Längden på bufferten som ska skrivas.
- **actual_length:** Längden som returneras till bufferten efter att skrivning har utförts

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Enheten är inte längre i det konfigurerade tillståndet.
- **UX_TRANSFER_NO_ANSWER** (0x22) Inget svar från enheten. Enheten kopplades förmodligen från medan överföringen väntade.

### <a name="example"></a>Exempel

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>CDC-ECM-klass för USB-enhet

USB-enhetens CDC-ECM-klass gör att ett USB-värdsystem kan kommunicera med enheten som en Ethernet-enhet. Den här klassen baseras på USB-standarden och är en delmängd av CDC-standarden.

Ett CDC-ACM-kompatibelt enhetsramverk måste deklareras av enhetsstacken. Ett exempel finns här nedan.

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

CDC-ECM-klassen använder en liknande enhetsbeskrivningsmetod för CDC-ACM och kräver även en IAD-beskrivning. Mer information finns i CDC-ACM-klassen.

Förutom det vanliga enhetsramverket kräver CDC-ECM särskilda strängbeskrivningar. Ett exempel visas nedan.

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

MAC-adresssträngsbeskrivningen används av CDC-ECM-klassen för att svara på värdfrågorna om vilken MAC-adress enheten svarar på vid TCP/IP-protokollet. Det kan anges till enhetsvalet men måste definieras här.

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

Initieringen av den här klassen förväntar sig samma funktionsanrop för aktivering och inaktivering, men här är de inställda på NULL så att inga återanrop utförs.

Nästa parametrar är för definitionen av nod-ID:erna. 2 noder krävs för CDC-ECM, en lokal nod och en fjärrnod. Den lokala noden anger MAC-adressen för enheten, medan fjärrnoden anger MAC-adressen för värden. Fjärrnoden måste vara samma som den som deklareras i enhetsramverkets strängbeskrivning.

CDC-ECM-klassen har inbyggda API:er för att överföra data åt båda sätten, men de är dolda för programmet eftersom användarprogrammet kommer att kommunicera med USB Ethernet-enheten via NetX.

USBX CDC-ECM-klassen är nära knuten Azure RTOS NetX-nätverksstacken. Ett program som använder både NetX- och USBX CDC-ECM-klassen aktiverar NetX-nätverksstacken som vanligt men måste dessutom aktivera USB-nätverksstacken på följande sätt.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB-nätverksstacken måste bara aktiveras en gång och är inte specifik för CDCECM, men krävs av alla USB-klasser som kräver NetX-tjänster.

CDC-ECM-klassen identifieras av MAC OS- och Linux-värdar. Men det finns ingen drivrutin som tillhandahålls av Microsoft Windows att identifiera CDC-ECM inbyggt. Vissa kommersiella produkter finns för Windows och de tillhandahåller en egen .inf-fil. Den här filen måste ändras på samma sätt som CDC-ACM inf-mallen så att den matchar PID/VID för USB-nätverksenheten.

## <a name="usb-device-hid-class"></a>HID-klass för USB-enhet

MED USB-enhetens HID-klass kan ett USB-värdsystem ansluta till en HID-enhet med specifika HID-klientfunktioner.

USBX HID-enhetsklassen är relativt enkel jämfört med värdsidan. Den är nära kopplad till enhetens beteende och dess HID-beskrivning.

Alla HID-klienter måste först definiera ett HID-enhetsramverk enligt exemplet nedan.

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

HID-ramverket innehåller en gränssnittsbeskrivning som beskriver HID-klassen och HID-enhetens underklass. HID-gränssnittet kan vara en fristående klass eller en del av en sammansatt enhet.

FÖR närvarande stöder USBX HID-klassen inte flera rapport-ID:n, eftersom de flesta program bara kräver ett ID (ID noll). Om flera rapport-ID:er är en funktion som du är intresserad av kan du kontakta oss.

Initieringen av HID-klassen är som följer, med hjälp av ett USB-tangentbord som exempel.

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

Programmet måste skicka en HID-rapportbeskrivning till HID-klassen och dess längd. Rapportbeskrivningen är en samling objekt som beskriver enheten. Mer information om HID-grammatik finns i HID USB-klassspecifikationen.

Förutom rapportbeskrivningen skickar programmet ett återanrop när en HID-händelse inträffar.

USBX HID-klassen stöder följande HID-standardkommandon från värden.

| Kommandonamn                             | Värde | Beskrivning                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Hämta en rapport från enheten                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Hämta inaktivitetsfrekvensen för avbrottsslutpunkten |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Få igång protokollet på enheten           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Ange en rapport till enheten                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | Ange inaktivitetsfrekvensen för avbrottsslutpunkten |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Få igång protokollet på enheten           |

Rapporten Hämta och ange är de vanligaste kommandona av HID för att överföra data fram och tillbaka mellan värden och enheten. Värden skickar vanligtvis data på kontrollslutpunkten men kan ta emot data antingen på avbrottsslutpunkten eller genom att utfärda ett GET_REPORT-kommando för att hämta data på kontrollslutpunkten.

KLASSEN HID kan skicka tillbaka data till värden på avbrottsslutpunkten med hjälp av ux_device_class_hid_event_set funktionen.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Ange en händelse till HID-klassen

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver skicka tillbaka en HID-händelse till värden. Funktionen blockerar inte, utan placerar bara rapporten i en cirkelformad kö och återgår till programmet.

### <a name="parameters"></a>Parametrar

- **hid**: Pekare till hid-klassinstansen.
- **hid_event:** Pekare till strukturen för den dolde händelsen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Fel: Inget tillgängligt utrymme i cirkelformad kö.

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

Motringning som definierats vid initieringen av HID-klassen utför motsatsen till att skicka en händelse. Den får som indata den händelse som skickas av värden. Prototypen av återanropet är följande.

### <a name="hid_callback"></a>hid_callback

Hämta en händelse från HID-klassen

### <a name="prototype"></a>Prototyp

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Description

Den här funktionen anropas när värden skickar en HID-rapport till programmet.

### <a name="parameters"></a>Parametrar

- **hid**: Pekare till hid-klassinstansen.
- **hid_event:** Pekare till strukturen för den dolde händelsen.

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
