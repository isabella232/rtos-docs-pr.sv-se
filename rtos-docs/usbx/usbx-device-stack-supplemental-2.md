---
title: Kapitel 2 – Överväganden för USBX-enhetsklass
description: Usb-enhetens RNDIS-klass gör att ett USB-värdsystem kan kommunicera med enheten som en Ethernet-enhet. Den här klassen baseras på Microsofts egenutvecklade implementering och är specifik för Windows plattformar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a28196c8f0e29ad94ef9f2d65b143459bf0214f48c345e6bb0d4ea71d520dfd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802639"
---
# <a name="chapter-2---usbx-device-class-considerations"></a>Kapitel 2 – Överväganden för USBX-enhetsklass

## <a name="usb-device-rndis-class"></a>USB-enhetens RNDIS-klass

Usb-enhetens RNDIS-klass gör att ett USB-värdsystem kan kommunicera med enheten som en Ethernet-enhet. Den här klassen baseras på Microsofts egenutvecklade implementering och är specifik för Windows plattformar.

Ett RNDIS-kompatibelt enhetsramverk måste deklareras av enhetsstacken. Ett exempel finns nedan.

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

RNDIS-klassen använder en liknande enhetsbeskrivningsmetod som CDC-ACM och CDC-ECM och kräver även en IAD-beskrivning. Se CDC-ACM-klassen för definition och krav för enhetsbeskrivningen.

Aktiveringen av RNDIS-klassen är följande.

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

För CDC-ECM kräver RNDIS-klassen 2 noder, en lokal och en fjärrnod, men det finns inget krav på att ha en strängbeskrivning som beskriver fjärrnoden.

På grund av Microsofts egna meddelandemekanism krävs dock vissa extra parametrar. Först måste leverantörs-ID:t skickas. På samma sätt gäller drivrutinsversionen för RNDIS. En leverantörssträng måste också anges.

RNDIS-klassen har inbyggda API:er för överföring av data på båda sätten, men de är dolda för programmet eftersom användarprogrammet kommer att kommunicera med USB Ethernet-enheten via NetX.

USBX RNDIS-klassen är nära knuten Azure RTOS NetX-nätverksstacken. Ett program som använder både NetX- och USBX RNDIS-klassen aktiverar NetX-nätverksstacken på vanligt sätt, men måste dessutom aktivera USB-nätverksstacken på följande sätt.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB-nätverksstacken måste bara aktiveras en gång och är inte specifik för RNDIS, men krävs av alla USB-klasser som kräver NetX-tjänster.

RNDIS-klassen identifieras inte av MAC OS- och Linux-värdar eftersom den är specifik för Microsofts operativsystem. På Windows-plattformar måste en .inf-fil finnas på den värd som matchar enhetsbeskrivningen. Microsoft tillhandahåller en mall för RNDIS-klassen och den finns i usbx_windows_host_files katalogen. För den senaste versionen Windows filen RNDIS_Template.inf användas. Den här filen måste ändras så att den återspeglar den PID/VID som används av enheten. PID/VID är specifik för den slutliga kunden när företaget och produkten registreras med USB-IF. I inf-filen finns de fält som ska ändras här.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

I enhetsramverket för RNDIS-enheten lagras PID/VID i enhetsbeskrivningen (se enhetsbeskrivningen som deklareras ovan)

När ett USB-värdsystem identifierar USB RNDIS-enheten monterar det ett nätverksgränssnitt och enheten kan användas med nätverksprotokollstacken. Se värdens operativsystem som referens.

## <a name="usb-device-dfu-class"></a>USB-enhetens DFU-klass

Usb-enhetens DFU-klass gör att ett USB-värdsystem kan uppdatera enhetens inbyggda programvara baserat på ett värdprogram. DFU-klassen är en USB-IF-standardklass.

USBX DFU-klassen är relativt enkel. Enhetsbeskrivningen kräver inte något annat än en kontrollslutpunkt. I de flesta fall bäddas den här klassen in i en USB-sammansatt enhet. Enheten kan vara vad som helst, till exempel en lagringsenhet eller en kommunikationsenhet, och det tillagda DFU-gränssnittet kan informera värden om att enhetens inbyggda programvara kan uppdateras direkt.

DFU-klassen fungerar i 3 steg. Först monterar enheten som vanligt med hjälp av den exporterade klassen. Ett program på värden (Windows eller Linux) använder DFU-klassen och skickar en begäran om att återställa enheten till DFU-läge. Enheten försvinner från buss under en kort tid (tillräckligt för att värden och enheten ska kunna identifiera en RESET-sekvens) och vid omstart är enheten uteslutande i DFU-läge och väntar på att värdprogrammet ska skicka en uppgradering av den inbyggda programvaran. När uppgraderingen av den inbyggda programvaran har slutförts återställer värdprogrammet enheten och vid omräkning återgår enheten till normal drift med den nya inbyggda programvaran.

Ett DFU-enhetsramverk kommer att se ut så här.

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

I det här exemplet är DFU-beskrivningen inte associerad med några andra klasser. Den har en enkel gränssnittsbeskrivning och inga andra slutpunkter kopplade till den. Det finns en funktionell beskrivning som beskriver enhetens DFU-funktioner.

Beskrivningen av DFU-funktionerna är följande.

| Name             | Offset  | Storlek | typ      | Description |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Bitfält | Bit 3: Enheten utför en från koppla från-koppla-busssekvens när den tar emot en DFU_DETACH begäran. Värden får inte utfärda en USB-återställning. (bitWillDetach) 0 = nej 1 = ja Bit 2: enheten kan kommunicera via USB efter Fasen Fördr. (bitManifestationTolerant) 0 = nej, måste se bussåterställning 1 = ja Bit 1: uppladdnings kompatibel (bitCanUpload) 0 = nej 1 = ja Bit 0: hämtnings kompatibel (bitCanDnload) 0 = nej 1 = ja  |
| wDetachTimeOut  | 3      | 2  | antal    | Tid, i millisekunder, som enheten väntar efter att ha fått DFU_DETACH begäran. Om den här tiden går utan EN USB-återställning avslutar enheten omkonfigurationsfasen och återgår till normal drift. Detta representerar den maximala tid som enheten kan vänta (beroende på timers osv.). USBX anger det här värdet till 1 000 ms.  |
| wTransferSize  | 5      | 2  | antal    | Maximalt antal byte som enheten kan acceptera per kontroll för \- skrivåtgärd. USBX anger det här värdet till 64 byte. |

Deklarationen för DFU-klassen är följande:

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

DFU-klassen måste fungera med ett program för enhetens inbyggda programvara som är specifik för målet. Därför definierar den flera åter anrop till läs- och skrivblock för inbyggd programvara och för att hämta status från programmet för uppdatering av inbyggd programvara. DFU-klassen har också en återanropsfunktion för att meddela programmet när en överföring av den inbyggda programvaran påbörjas och avslutas.

Nedan visas en beskrivning av ett typiskt DFU-programflöde.

![DFU-programflöde](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

Den största utmaningen med DFU-klassen är att få rätt program på värden för att utföra nedladdningen av den inbyggda programvaran. Det finns inget program som tillhandahålls av Microsoft eller USB-IF. Det finns vissa shareware-program som fungerar någorlunda bra i Linux och i mindre utsträckning Windows.

På Linux kan du använda dfu-utils för att hitta här: Mycket information om [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) dfu utils finns också på den här länken: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

Linux-implementeringen av DFU utför korrekt återställningssekvensen mellan värden och enheten och därför behöver enheten inte göra det. Linux kan acceptera att bmAttributes *bitWillDetach* är 0. Windows på den andra sidan kräver att enheten utför återställningen.

På Windows måste USB-registret kunna associera USB-enheten med dess PID/VID och USB-biblioteket som i sin tur kommer att användas av DFU-programmet. Detta kan enkelt göras med det kostnadsfria verktyget Zadig som finns här: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .

Om du kör Zadig för första gången visas den här skärmen:

![Köra Zadig för första gången](./media/usbx-device-stack-supplemental/zadig.png)

I enhetslistan hittar du enheten och associerar den med biblioteksdrivrutinen för Windows. Detta binder ENHETENs PID/VID till den Windows USB-biblioteket som används av DFU-verktygen.

Om du vill köra DFU-kommandot packar du bara upp de komprimerade dfu-verktygen i en katalog och kontrollerar att libusb dll också finns i samma katalog. DFU-verktygen måste köras från en DOS-ruta på kommandoraden.

Skriv först kommandot **dfu-util –l för** att avgöra om enheten visas. Om inte kör du Zadig för att kontrollera att enheten visas och är associerad med USB-biblioteket. Du bör se en skärm på följande sätt:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

Nästa steg är att förbereda filen som ska laddas ned. USBX DFU-klassen utför ingen verifiering av den här filen och är oberoende av dess interna format. Den här filen för inbyggd programvara är mycket specifik för målet, men inte för DFU eller USBX.

Sedan kan dfu-util instrueras att skicka filen genom att skriva följande kommando:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

Dfu-util bör visa filnedladdningsprocessen tills den inbyggda programvaran har laddats ned helt.

## <a name="usb-device-pima-class-ptp-responder"></a>PIMA-klass för USB-enhet (PTP-svarare)

USB-enhetens PIMA-klass gör att ett USB-värdsystem (initierare) kan ansluta till en

PIMA-enhet (Resonder) för att överföra mediefiler. USBX Pima-klassen överensstämmer med USB-IF PIMA 15740-klassen, som även kallas PTP-klass (för Picture Transfer Protocol).

PIMA-klassen på USBX-enhetssidan stöder följande åtgärder.

| Åtgärdskod                                    | Värde | Beskrivning                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Hämta åtgärder och händelser som stöds av enheten                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Öppna en session mellan värden och enheten                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Stäng en session mellan värden och enheten                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Returnerar enhetens lagrings-ID. USBX PIMA använder endast ett lagrings-ID |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Returnera information om lagringsobjektet, till exempel maximal kapacitet och ledigt utrymme                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Returnera antalet objekt som finns på lagringsenheten                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Returnera en matris med referenser till objekten på lagringsenheten                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Returnera information om ett objekt, till exempel namnet på objektet, dess skapandedatum, ändringsdatum |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Returnera data som hör till ett specifikt objekt                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | Skicka miniatyrbilden om den är tillgänglig för ett objekt                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Ta bort ett objekt på mediet                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Skicka information om ett objekt till enheten för att det ska kunna skapas på mediet                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Skicka data för ett objekt till enheten                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Rensa enhetens media                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Återställa målenheten                                                                                   |

| Åtgärdskod                                         | Värde | Beskrivning |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Avbryter den aktuella transaktionen                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Ett objekt har lagts till i enhetsmediet och kan hämtas av värden\. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Ett objekt har tagits bort från enhetens media                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | Ett medium har lagts till på enheten                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Ett medium har tagits bort från enheten                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | Enhetsegenskaperna har ändrats                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | Objektinformationen har ändrats                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | En enhet har ändrats                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | Enheten begär överföring av ett objekt från värden                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | Enheten rapporterar att mediet är fullt                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | Enhetsrapporter som återställdes                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | Storage information har ändrats på enheten                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | Avskiljning har slutförts                                                            |

USBX PIMA-enhetsklassen använder en TX-tråd för att lyssna på PIMA-kommandon från värden.

Ett PIMA-kommando består av ett kommandoblock, ett datablock och en statusfas.

Funktionen ux_device_class_pima_thread en begäran till stacken om att ta emot ett PIMA-kommando från värdsidan. PIMA-kommandot avkodas och verifieras för innehåll. Om kommandoblocket är giltigt förgrenar det till lämplig kommandohanterare.

De flesta PIMA-kommandon kan bara köras när en session har öppnats av värden. Det enda undantaget är kommandot **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**. Med USBX PIMA-implementering kan endast en session öppnas mellan en initierare och svarare när som helst. Alla transaktioner i den enda sessionen blockeras och ingen ny transaktion kan påbörjas innan den föregående slutfördes.

PIMA-transaktioner består av tre faser, en kommandofas, en valfri datafas och en svarsfas. Om det finns en datafas kan den bara vara i en riktning.

Initieraren bestämmer alltid flödet för PIMA-åtgärderna, men svararen kan initiera händelser tillbaka till initieraren för att informera om statusändringar som inträffade under en session.

Följande diagram visar överföringen av ett dataobjekt mellan värden och PIMA-enhetsklassen.

![PIMA-transaktioner](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Initiering av PIMA-enhetsklassen

PIMA-enhetsklassen behöver vissa parametrar som tillhandahålls av programmet under initieringen.

Följande parametrar beskriver enheten och lagringsinformationen.

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

PIMA-klassen kräver också registrering av återanrop i programmet för att informera tillämpningen av vissa händelser eller hämta/lagra data från/till det lokala mediet. Återanropen är följande.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

I följande exempel visas hur du initierar klientsidan av PIMA. I det här exemplet används Pictbridge som klient för PIMA.

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

Lägga till ett -objekt och skicka händelsen till värden

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver lägga till ett -objekt och informera värden.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen
- **object_handle**: Referens för objektet.

### <a name="example"></a>Exempel

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

Hämta objektnumret från programmet

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver hämta antalet objekt i det lokala systemet och skicka tillbaka det till värden.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen
- **object_number:** Adress för antalet objekt som ska returneras

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a>ux_device_class_pima_object_handles_get

Returnera objekthandtagsmatrisen

### <a name="prototype"></a>Prototyp

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver hämta objektet hanterar matrisen i det lokala systemet och skicka tillbaka den till värden.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **object_handles_format_code:** Formatera kod för handtagen
- **object_handles_association:** Objektassociationskod
- **object_handle_array:** Adress där handtagen ska lagras
- **object_handles_max_number:** Maximalt antal referenser i matrisen

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a>ux_device_class_pima_object_info_get

Returnera objektinformationen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver hämta objektet hanterar matrisen i det lokala systemet och skicka tillbaka den till värden.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **object_handles**: Referens för objektet
- **objekt:** Objekt pekaradress

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

Returnera objektdata

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver hämta objektdata i det lokala systemet och skicka tillbaka dem till värden.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **object_handle**: Referens för objektet
- **object_buffer:** Objektbuffertadress
- **object_length_requested:** Objektdatalängd som begärs av klienten till programmet
- **object_actual_length:** Objektdatalängd som returneras av programmet

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

Värden skickar objektinformationen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver ta emot objektinformationen i det lokala systemet för framtida lagring.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen
- **object**: Pekare till objektet
- **object_handle**: Referens för objektet

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

Värden skickar objektdata

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver ta emot objektdata i det lokala systemet för lagring.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen
- **object_handle**: Referens för objektet
- **fas**: överföringsfasen (aktiv eller klar)
- **object_buffer:** Objektbuffertadress
- **object_offset:** Dataadress
- **object_length:** Objektdatalängd som skickas av programmet

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

Ta bort ett lokalt objekt

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a>Description

Den här funktionen anropas när PIMA-klassen behöver ta bort ett objekt på den lokala lagringen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen
- **object_handle**: Referens för objektet

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Ljudklass för USB-enhet

Usb-enhetens ljudklass gör att ett USB-värdsystem kan kommunicera med enheten som en ljudenhet. Den här klassen baseras på USB-standarden och USB-ljudklass 1.0 eller 2.0-standarden.

Ett USB-ljud kompatibelt enhetsramverk måste deklareras av enhetsstacken. Ett exempel på en Audio 2.0-talare följer:

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

Klassen Audio använder ett sammansatt enhetsramverk för att gruppera gränssnitt (kontroll och strömning). Därför bör du vara försiktig när du definierar enhetsbeskrivningen. USBX förlitar sig på IAD-beskrivningen för att veta internt hur gränssnitt ska bindas. IAD-beskrivningen ska deklareras före gränssnitten (ett AudioControl-gränssnitt följt av ett eller flera AudioStreaming-gränssnitt) och innehålla det första gränssnittet i klassen Audio (AudioControl-gränssnittet) och hur många gränssnitt som är anslutna.

Hur ljudklassen fungerar beror på om enheten skickar eller tar emot ljud, men båda fallen använder en FIFO för att lagra ljudrambuffertar: om enheten skickar ljud till värden lägger programmet till ljudrambuffertar till FIFO:n som senare skickas till värden via USBX. Om enheten tar emot ljud från värden lägger USBX till de ljudrambuffertar som tas emot från värden till FIFO:n som läses senare av programmet. Varje ljudström har sin egen FIFO, och varje ljudrambuffert består av flera exempel.

Initieringen av klassen Audio förväntar sig följande delar.

1. Ljudklassen förväntar sig följande strömningsparametrar:

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. Ljudklassen förväntar sig följande funktionsparametrar.

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   Det programdefinierade återanropet av kontrollbegäran (***ux_device_class_audio_control_process***; som anges i föregående exempel) anropas när stacken tar emot en kontrollbegäran från värden. Om begäran godkänns och hanteras (bekräftad eller avstannad) måste återanropet returnera lyckat, annars ska felet returneras.

   Den klassspecifika processen för kontrollbegäran definieras som ett programdefinierat återanrop eftersom kontrollbegäranden skiljer sig mycket åt mellan USB-ljudversioner och en stor del av begärandeprocessen relaterar till enhetsramverket. Programmet ska hantera begäranden korrekt för att enheten ska fungera.

   Eftersom volym, mute och samplingsfrekvens för en ljudenhet är vanliga kontrollbegäranden introduceras enkla, internt definierade återanrop för olika USB-ljudversioner i senare avsnitt så att program kan använda dem. Mer information **finns i * ux_device_class_audio10_control_process** _ och _ *_ux_device_class_audio_control_request_** .

I enhetsramverket för ljudenheten lagras PID/VID i enhetsbeskrivningen (se enhetsbeskrivningen som deklarerades ovan).

När ett USB-värdsystem identifierar USB-ljudenheten och monterar ljudklassen kan enheten användas med valfri ljudspelare eller inspelare (beroende på ramverk). Se värdoperativsystemet som referens.

Ljudklass-API:erna definieras nedan.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Trådpost för läsning av data för funktionen Audio.

### <a name="prototype"></a>Prototyp

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Description

Den här funktionen skickas till initieringsparametern för ljudströmmar om du vill läsa ljud från värden. Internt skapas en tråd med den här funktionen som postfunktion. tråden läser ljuddata via den isokrona OUT-slutpunkten i funktionen Audio.

### <a name="parameters"></a>Parametrar

- **audio_stream:** Pekare till ljudströminstansen.

### <a name="example"></a>Exempel

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Trådpost för att skriva data för ljudfunktionen

### <a name="prototype"></a>Prototyp

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Description

Den här funktionen skickas till initieringsparametern för ljudströmmar om du vill skriva ljud till värden. Internt skapas en tråd med den här funktionen som postfunktion. själva tråden skriver ljuddata via den isokrona IN-slutpunkten i funktionen Audio.

### <a name="parameters"></a>Parametrar

- **audio_stream:** Pekare till ljudströminstansen.

### <a name="example"></a>Exempel

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Hämta en specifik ströminstans för ljudfunktionen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Description

Den här funktionen används för att hämta en ströminstans av ljudklassen.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudinstansen
- **stream_index:** Stream-instansindex baserat på 0
- **stream**: Pekare till buffert för att lagra pekaren för ljudströminstansen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Starta mottagning av ljuddata för ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Description

Den här funktionen används för att starta ljuddataläsning i ljudströmmar.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är full.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Läsa 8-bitarsexempel från ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Description

Den här funktionen läser 8-bitars ljudexempeldata från den angivna strömmen.

Mer specifikt läser den exempeldata från den aktuella ljudrambufferten i FIFO:n. När du läser det sista exemplet i en ljudram frigörs ramen automatiskt så att den kan användas för att ta emot mer data från värden.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **buffer**: Pekare till bufferten för att spara exempelbyte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Läsa 16-bitarsexempel från ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Description

Den här funktionen läser 16-bitars ljudexempeldata från den angivna strömmen.

Mer specifikt läser den exempeldata från den aktuella ljudrambufferten i FIFO:n. När du läser det sista exemplet i en ljudram frigörs ramen automatiskt så att den kan användas för att ta emot mer data från värden.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **buffer**: Pekare till bufferten för att spara 16-bitarsprovet.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Läsa 24-bitarsexempel från ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Description

Den här funktionen läser 24-bitars ljudexempeldata från den angivna strömmen.

Mer specifikt läser den exempeldata från den aktuella ljudrambufferten i FIFO. När du läser det sista exemplet i en ljudram frigörs ramen automatiskt så att den kan användas för att ta emot mer data från värden.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **buffer**: Pekare till bufferten för att spara 3 byte-exemplet.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Läsa 32-bitarsexempel från ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Description

Den här funktionen läser 32-bitars ljudexempeldata från den angivna dataströmmen.

Mer specifikt läser den exempeldata från den aktuella ljudrambufferten i FIFO. När du läser det sista exemplet i en ljudram frigörs ramen automatiskt så att den kan användas för att ta emot mer data från värden.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **buffer**: Pekare till bufferten för att spara 4 byte-data.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

Få åtkomst till ljudramen i ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Description

Den här funktionen returnerar den första ljudrambufferten och dess längd i den angivna strömmens FIFO. När programmet har bearbetat data måste ux_device_class_audio_read_frame_free användas för att frigöra rambufferten i FIFO:n.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **frame_data:** Pekare till data pekare för att returnera data pekaren i.
- **frame_length:** Pekare till buffert för att spara ramlängden i antal byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Frigör en ljudramsbuffert i ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Description

Den här funktionen frigör ljudrambufferten framför den angivna strömmens FIFO så att den kan ta emot data från värden.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Starta överföring av ljuddata för ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Description

Den här funktionen används för att börja skicka ljuddata som skrivits till FIFO i ljudklassen.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är null.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Skriva en ljudram till ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Description

Den här funktionen skriver en bildruta till ljudströmmens FIFO. Ramdata kopieras till den tillgängliga bufferten i FIFO:n så att de kan skickas till värden.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **frame**: Pekare för att rama in data.
- **frame_length** Ramlängd i antal byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är full.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

Få åtkomst till ljudramen i ljudströmmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Description

Den här funktionen hämtar adressen till den sista ljudrambufferten för FIFO: Den hämtar även längden på ljudrambufferten. När programmet har fyllt ljudrambufferten med önskade data ***ux_device_class_audio_write_frame_commit*** användas för att lägga till/spara bildrutebufferten till FIFO:n.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **frame_data: Pekare** för att rama in datapekaren för att returnera pekaren för ramdata.
- **frame_length** Pekare till bufferten för att spara ramlängden i antal byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är full.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

Spara en ljudramsbuffert i ljudströmmen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Description

Den här funktionen lägger till/genomför den sista ljudrambufferten till FIFO:n så att bufferten är redo att överföras till värden. Observera att den senaste ljudrambufferten bör ha fyllts i via ux_device_class_write_frame_get.

### <a name="parameters"></a>Parametrar

- **stream**: Pekare till ljudströminstansen.
- **length**: Antal byte som är redo i bufferten.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO-bufferten är fssull.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Bearbeta USB Audio 1.0-kontrollbegäranden

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Description

Den här funktionen hanterar grundläggande begäranden som skickas av värden på kontrollslutpunkten med en USB Audio 1.0-specifik typ.

Audio 1.0-funktioner för volym- och mute-begäranden bearbetas i funktionen. Vid bearbetning av begäranden används fördefinierade data som skickas av den sista parametern (grupp) för att besvara begäranden och lagra kontrolländringar.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudinstansen.
- **transfer**: Pekare till instansen för överföringsbegäran.
- **group**: Datagrupp för begärandeprocess.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a>ux_device_class_audio20_control_process

Bearbeta USB Audio 1.0-kontrollbegäranden

### <a name="prototype"></a>Prototyp
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Description

Den här funktionen hanterar grundläggande begäranden som skickas av värden på kontrollslutpunkten med en USB Audio 2.0-specifik typ.

Samplingsfrekvensen för Audio 2.0 (antas vara en fast frekvens), funktioner för volym- och mute-begäranden bearbetas i funktionen. Vid bearbetning av begäranden används fördefinierade data som skickas av den sista parametern (grupp) för att besvara begäranden och lagra kontrolländringar.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudinstansen.
- **transfer**: Pekare till instansen för överföringsbegäran.
- **group**: Datagrupp för begärandeprocess.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Fel från funktion

### <a name="example"></a>Exempel

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
