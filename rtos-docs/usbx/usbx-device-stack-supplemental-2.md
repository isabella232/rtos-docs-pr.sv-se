---
title: Kapitel 2 – överväganden för enhets klass i USBX
description: USB-enhetens RNDIS-klass tillåter att ett USB-värdnamn kommunicerar med enheten som en Ethernet-enhet. Den här klassen baseras på Microsofts patentskyddade implementering och är specifika för Windows-plattformar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8104f00e192486f57fe9c22b2c83aa9a22954739
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828413"
---
# <a name="chapter-2---usbx-device-class-considerations"></a>Kapitel 2 – överväganden för enhets klass i USBX

## <a name="usb-device-rndis-class"></a>RNDIS-klass för USB-enhet

USB-enhetens RNDIS-klass tillåter att ett USB-värdnamn kommunicerar med enheten som en Ethernet-enhet. Den här klassen baseras på Microsofts patentskyddade implementering och är specifika för Windows-plattformar.

Ett RNDIS-kompatibelt enhets ramverk måste deklareras av enhets stacken. Ett exempel finns nedan.

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

RNDIS-klassen använder en mycket liknande enhets beskrivnings metod för CDC-ACM och CDC-ECM och kräver också en IAD-beskrivning. Se CDC-ACM-klassen för definition och krav för enhets beskrivningen.

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

För CDC-ECM kräver RNDIS-klassen 2 noder, en lokal och en fjärr anslutning, men det finns inget krav på att ha en sträng beskrivning som beskriver fjärrnoden.

Men på grund av Microsoft patentskyddad meddelande funktion krävs vissa extra parametrar. Först måste leverantörs-ID: t skickas. På samma sätt är driv rutins versionen av RNDIS. En leverantörs sträng måste också anges.

RNDIS-klassen har inbyggda API: er för överföring av data på båda sätt, men de är dolda för programmet när användar programmet kommer att kommunicera med USB-Ethernet-enheten via NetX.

USBX RNDIS-klassen är nära kopplad till Azure återställnings tider NetX-nätverks stacken. Ett program som använder både NetX-och USBX RNDIS-klassen kommer att aktivera NetX-nätverks stacken på vanligt sätt, men du måste också aktivera USB-protokollstacken på följande sätt.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

USB-protokollstacken behöver bara aktive ras en gång och är inte särskilt för RNDIS, men krävs av alla USB-klasser som kräver NetX-tjänster.

RNDIS-klassen känns inte igen av MAC OS-och Linux-värdar eftersom den är speciell för Microsofts operativ system. På Windows-plattformar måste en INF-fil finnas på den värd som matchar enhets beskrivningen. Microsoft tillhandahåller en mall för klassen RNDIS och finns i usbx_windows_host_files-katalogen. För senare versioner av Windows ska filen RNDIS_Template. inf användas. Den här filen måste ändras för att återspegla det PID/VID som används av enheten. PID/VID är specifika för den slutgiltiga kunden när företaget och produkten registreras med USB-IF. I INF-filen finns fälten som ska ändras här.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

I enhets ramverket för RNDIS-enheten lagras PID/VID i enhets beskrivningen (se den enhets beskrivning som anges ovan)

När ett USB-värdnamn identifierar USB-RNDIS enhet monteras ett nätverks gränssnitt och enheten kan användas med nätverks protokolls Tacken. Se värd operativ systemet för referens.

## <a name="usb-device-dfu-class"></a>DFU-klass för USB-enhet

USB-enhetens DFU-klass tillåter att ett USB-värdnamn uppdaterar enhetens inbyggda program vara baserat på ett värd program. Klassen DFU är en USB-IF-standardklass.

USBX DFU-klassen är relativt enkel. IT-enhetens Beskrivning kräver inte något annat än en kontroll slut punkt. I de flesta fall kommer den här klassen att bäddas in i en USB-sammansatt enhet. Enheten kan vara något som en lagrings enhet eller en kommunikations enhet och det tillagda DFU-gränssnittet kan informera värden om att enheten kan uppdatera sin inbyggda program vara i farten.

DFU-klassen fungerar i tre steg. Första enheten monteras som normal med den exporterade klassen. Ett program på värden (Windows eller Linux) kommer att utnyttja klassen DFU och skicka en begäran om att återställa enheten till DFU-läge. Enheten kommer att försvinna från bussen under en kort tid (tillräckligt för värden och enheten för att identifiera en återställnings ordning) och vid omstart är enheten exklusivt i DFU-läge, väntar på att värd programmet ska skicka en uppgradering av inbyggd program vara. När uppgraderingen av den inbyggda program varan har slutförts återställer värd programmet enheten och när den omräknas igen återgår enheten till sin normala drift med den nya inbyggda program varan.

En DFU Device Framework ser ut så här.

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

I det här exemplet är DFU-beskrivningen inte associerad med några andra klasser. Den har en enkel gränssnitts beskrivning och inga andra slut punkter är kopplade till den. Det finns en funktions beskrivning som beskriver de olika DFU-funktionerna på enheten.

Beskrivningen av DFU-funktionerna är följande.

| Name             | Offset  | Storlek | typ      | Beskrivning |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Bitars fält | Bit 3: enheten utför en buss-koppla bort sekvens när den får en DFU_DETACH begäran. Värden får inte utfärda en USB-återställning. (bitWillDetach) 0 = ingen 1 = Yes bit 2: enheten kan kommunicera via USB efter manifest fasen. (bitManifestationTolerant) 0 = Nej, måste se buss återställning 1 = Ja bit 1: uppladdnings funktion (bitCanUpload) 0 = ingen 1 = Yes bit 0: nedladdnings bar funktion (bitCanDnload) 0 = ingen 1 = Ja  |
| wDetachTimeOut  | 3      | 2  | antal    | Tid i millisekunder som enheten väntar efter att DFU_DETACH-begäran har mottagits. Om den här tiden går ut utan en USB-återställning avslutar enheten omkonfigurations fasen och återgår till normal drift. Detta motsvarar den längsta tid som enheten kan vänta (beroende på dess timers, osv.). USBX anger det här värdet till 1000 MS.  |
| wTransferSize  | 5      | 2  | antal    | Maximalt antal byte som enheten kan godkänna vid \- Skriv åtgärd per kontroll. USBX anger det här värdet till 64 byte. |

DFU-klassens deklaration är följande:

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

DFU-klassen måste fungera med en enhets program vara som är specifik för målet. Därför definierar den flera anrop tillbaka till Läs-och skriv block med inbyggd program vara och hämta status från uppdaterings programmet för den inbyggda program varan. Klassen DFU har också en funktion för att uppmana dig att meddela programmet när den inbyggda program varans start och slut har överförts.

Nedan visas en beskrivning av ett typiskt DFU-programflöde.

![DFU program flöde](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

Den största utmaningen i DFU-klassen får rätt program på värden för att utföra hämtningen av den inbyggda program varan. Det finns inget program från Microsoft eller USB-IF. Vissa shareware finns och de fungerar bra på Linux och i mindre utsträckning i Windows.

I Linux finns en DFU-utils som du kan hitta här: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) mycket information om DFU-utils finns också på den här länken: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

Linux-implementeringen av DFU utför korrekt återställnings ordningen mellan värden och enheten och därför behöver enheten inte göra det. Linux kan godkänna bmAttributes- *bitWillDetach* till 0. Windows på den andra sidan kräver att enheten utför återställningen.

I Windows måste USB-registret kunna associera USB-enheten med sitt PID/VID och USB-biblioteket som i sin tur används av DFU-programmet. Detta kan vara enkelt att göra med den kostnads fria Zadig som du hittar här: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .

När du kör Zadig för första gången visas den här skärmen:

![Kör Zadig för första gången](./media/usbx-device-stack-supplemental/zadig.png)

I enhets listan letar du reda på din enhet och associerar den med libusb Windows-drivrutinen. Detta binder enhets numret/VID enheten med Windows USB-biblioteket som används av DFU-verktygen.

Om du vill använda kommandot DFU packar du upp de zippade DFU-verktygen i en katalog och kontrollerar att libusb-DLL-filen också finns i samma katalog. DFU-verktygen måste köras från en DOS-ruta på kommando raden.

Börja med att skriva kommandot **DFU-util – l** för att avgöra om enheten visas i listan. Om inte kör du Zadig för att kontrol lera att enheten är listad och kopplad till USB-biblioteket. Du bör se en skärm på följande sätt:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

Nästa steg är att förbereda filen som ska laddas ned. USBX DFU-klassen utför ingen verifiering på den här filen och är oberoende av dess interna format. Den här inbyggda program varan är särskilt speciell för målet men inte att DFU eller USBX.

Sedan kan DFU-util instrueras att skicka filen genom att skriva följande kommando:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

DFU-util bör Visa fil hämtnings processen tills den inbyggda program varan har laddats ned helt.

## <a name="usb-device-pima-class-ptp-responder"></a>PIMA-klass (PTP-svarare) för USB-enhet

USB-enhetens PIMA-klass tillåter att ett USB-värdnamn (Initiator) ansluter till en

PIMA-enhet (Resonder) för överföring av mediafiler. USBX Pima-klassen överensstämmer med USB-IF PIMA 15740-klassen kallas även PTP-klass (för Picture Transfer Protocol).

USBX PIMA-klassen stöder följande åtgärder.

| Åtgärds kod                                    | Värde | Beskrivning                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Hämta de åtgärder och händelser som stöds av enheten                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Öppna en session mellan värden och enheten                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Stäng en session mellan värden och enheten                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Returnerar enhetens lagrings-ID. USBX PIMA använder bara ett lagrings-ID |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Returnera information om lagrings objekt såsom maximal kapacitet och ledigt utrymme                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Returnera antalet objekt som finns i lagrings enheten                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Returnera en matris med referenser för objekten på lagrings enheten                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Returnera information om ett objekt, till exempel namnet på objektet, dess skapelse datum, ändrings datum |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Returnera data som hör till ett angivet objekt                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | Skicka miniatyren om den är tillgänglig för ett objekt                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Ta bort ett objekt på mediet                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Skicka till enhets informationen om ett objekt för att skapa det på mediet                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Skicka data för ett objekt till enheten                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Rengör enhets mediet                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Återställa mål enheten                                                                                   |

| Åtgärds kod                                         | Värde | Beskrivning |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Avbryter den aktuella transaktionen                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Ett objekt har lagts till i enhets mediet och kan hämtas av host\. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Ett objekt har tagits bort från enhets mediet                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | Ett medium har lagts till i enheten                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Ett medium har tagits bort från enheten                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | Enhets egenskaperna har ändrats                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | En objekt information har ändrats                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | En enhet har ändrats                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | Enheten begär överföring av ett objekt från värden                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | Enheten rapporterar att mediet är fullt                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | Enhets rapporter som den återställdes                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | Lagrings information har ändrats på enheten                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | Avbildningen har slutförts                                                            |

Enhets klassen USBX PIMA använder en TX-tråd för att lyssna på PIMA-kommandon från värden.

Ett PIMA-kommando består av ett kommando block, ett data block och en status fas.

Funktionen ux_device_class_pima_thread publicerar en begäran till stacken för att ta emot ett PIMA-kommando från värd sidan. PIMA-kommandot avkodas och verifieras för innehåll. Om kommando blocket är giltigt är det grenat till lämplig kommando hanterare.

De flesta PIMA-kommandon kan bara utföras när en session har öppnats av värden. Det enda undantaget är kommandot **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**. Med USBX PIMA-implementeringen kan endast en session öppnas mellan en initierare och en svarare när som helst. Alla transaktioner i den enskilda sessionen blockeras och ingen ny transaktion kan börja innan den tidigare slutförts.

PIMA-transaktioner består av tre faser, en kommando fas, en valfri data fas och en svars fas. Om det finns en data fas kan den bara vara i en riktning.

Initieraren fastställer alltid flödet för PIMA-åtgärder, men den som svarar kan initiera händelser tillbaka till initieraren för att informera om status ändringar som har skett under en session.

Följande diagram visar överföringen av ett data objekt mellan värden och enhets klassen PIMA.

![PIMA transaktioner](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Initiering av enhets klassen PIMA

PIMA enhets klass behöver vissa parametrar som tillhandahålls av programmet under initieringen.

Följande parametrar beskriver enhets-och lagrings information.

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

PIMA-klassen kräver också registrering av motringning till programmet för att informera om tillämpningen av vissa händelser eller hämta/lagra data från/till det lokala mediet. Återanropen är följande.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

I följande exempel visas hur du initierar klient sidan av PIMA. I det här exemplet används PictBridge som en klient för PIMA.

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

Lägga till ett objekt och skicka händelsen till värden

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver lägga till ett objekt och informera värden.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot Pima-klass instansen
- **object_handle**: objektets handtag.

### <a name="example"></a>Exempel

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

Hämtar objekt numret från programmet

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver hämta antalet objekt i det lokala systemet och skicka tillbaka den till värden.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot Pima-klass instansen
- **object_number**: adressen för det antal objekt som ska returneras

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

Returnera objektets referens mat ris

### <a name="prototype"></a>Prototyp

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver hämta objektet hanterar matrisen i det lokala systemet och skicka tillbaka den till värden.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **object_handles_format_code**: format kod för handtagen
- **object_handles_association**: objekt kopplings kod
- **object_handle_array**: adress dit du vill lagra handtagen
- **object_handles_max_number**: högsta antal referenser i matrisen

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

Returnera objekt informationen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver hämta objektet hanterar matrisen i det lokala systemet och skicka tillbaka den till värden.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **object_handles**: referens för objektet
- **objekt**: objektets pekare adress

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

Returnera objekt data

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver hämta objekt data i det lokala systemet och skicka tillbaka den till värden.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot instans av Pima-klassen.
- **object_handle**: referens för objektet
- **object_buffer**: objektets bufferts adress
- **object_length_requested**: den objekt data längd som klienten har begärt till programmet
- **object_actual_length**: objekt data längden som returnerades av programmet

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

Värd skickar objekt informationen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver ta emot objekt informationen i det lokala systemet för framtida lagring.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot Pima-klass instansen
- **objekt**: pekar mot objektet
- **object_handle**: referens för objektet

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

Värden skickar objekt data

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver ta emot objekt data i det lokala systemet för lagring.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot Pima-klass instansen
- **object_handle**: referens för objektet
- **fas**: överförings fasen (aktiv eller fullständig)
- **object_buffer**: objektets bufferts adress
- **object_offset**: data adress
- **object_length**: objekt data längden har skickats av programmet

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas när PIMA-klassen behöver ta bort ett objekt i den lokala lagringen.

### <a name="parameters"></a>Parametrar

- **Pima**: pekar mot Pima-klass instansen
- **object_handle**: referens för objektet

### <a name="example"></a>Exempel

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Ljud klass för USB-enhet

Ljud klassen USB-enhet gör att ett USB-värdnamn kan kommunicera med enheten som en ljuden het. Den här klassen baseras på USB-standarden och USB Audio-klassen 1,0 eller 2,0 standard.

En USB-kompatibel enhets ramverk måste deklareras av enhets stacken. Ett exempel på en ljud 2,0-talare följer:

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

Klassen Audio använder ett sammansatt enhets ramverk för att gruppera gränssnitt (kontroll och strömning). Därför bör du vidta åtgärder när du definierar enhets beskrivningen. USBX förlitar sig på IAD-beskrivningen för att veta internt hur man binder gränssnitt. IAD-beskrivningen måste deklareras före gränssnitten (ett AudioControl-gränssnitt följt av ett eller flera AudioStreaming-gränssnitt) och innehålla det första gränssnittet i klassen Audio (AudioControl-gränssnittet) och hur många gränssnitt som är kopplade.

Hur klassen Audio fungerar beror på om enheten skickar eller tar emot ljud, men båda fallen använder en FIFO för att lagra ljud Rams buffertar: om enheten skickar ljud till värden, lägger programmet till ljud Rams buffertar till FIFO som senare skickas till värden av USBX; Om enheten tar emot ljud från värden lägger USBX till de ljud Rams buffertar som tas emot från värden till FIFO-enheten som senare läses av programmet. Varje ljud ström har en egen FIFO, och varje buffert för ljud ramar består av flera exempel.

Initieringen av klassen Audio förväntar sig följande delar.

1. Klassen Audio förväntar sig följande strömnings parametrar:

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

2. Klassen Audio förväntar sig följande funktions parametrar.

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
   status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   Den programdefinierade kontrollen begär motringning (***ux_device_class_audio_control_process***; som anges i föregående exempel) anropas när stacken tar emot en kontrollbegäran från värden. Om begäran godkänns och hanteras (bekräftas eller stoppas) måste återanropet returnera ett fel, annars ska felet returneras.

   Den klassbaserade kontrollen begär processen definieras som en programdefinierad motringning eftersom kontroll förfrågningarna är mycket olika mellan USB-ljudversioner och en stor del av processen för begäran relaterar till enhets ramverket. Programmet ska hantera begär Anden korrekt för att enheten ska fungera.

   Eftersom en ljuden het, volym, ljud av och samplings frekvens är vanliga kontroll begär Anden, är det enkelt att använda internt definierade återanrop för olika versioner av USB-ljud i senare avsnitt för program som ska användas. Se ***ux_device_class_audio10_control_process** _ och _ *_ux_device_class_audio_control_request_** för mer information.

I enhets ramverket för ljud enheten lagras PID/VID i enhets beskrivningen (se den enhets beskrivning som anges ovan).

När ett USB-värdnamn identifierar USB-ljudenheten och monterar klassen Audio, kan enheten användas med valfri ljuds pelare eller inspelning (beroende på ramverket). Se värd operativ systemet för referens.

Ljud klassens API: er definieras nedan.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Tråd inmatning för läsning av data för ljud funktionen.

### <a name="prototype"></a>Prototyp

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Beskrivning

Den här funktionen skickas till initierings parametern för ljud strömmen om du vill läsa ljud från värden. Internt skapas en tråd med den här funktionen som dess post funktion. själva tråden läser ljud data genom den isokrona slut punkten i ljud funktionen.

### <a name="parameters"></a>Parametrar

- **audio_stream**: pekar mot ljud Ströms instansen.

### <a name="example"></a>Exempel

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Tråd inmatning för att skriva data för ljud funktionen

### <a name="prototype"></a>Prototyp

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Beskrivning

Den här funktionen skickas till initierings parametern för ljud strömmen om du vill skriva ljud till värden. Internt skapas en tråd med den här funktionen som dess post funktion. själva tråden skriver ljud data via den isokrona slut punkten i ljud funktionen.

### <a name="parameters"></a>Parametrar

- **audio_stream**: pekar mot ljud Ströms instansen.

### <a name="example"></a>Exempel

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Hämta en speciell Stream-instans för ljud funktionen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Beskrivning

Den här funktionen används för att hämta en strömmande instans av klassen Audio.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot ljud instansen
- **stream_index**: Stream instance index baserat på 0
- **Stream**: pekare till buffer för att lagra pekaren för ljud strömmens instans

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Starta mottagning av ljud data för ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Beskrivning

Den här funktionen används för att starta läsning av ljud data i ljud strömmar.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är full.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Läs 8-bitars exempel från ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Beskrivning

Den här funktionen läser 8-bitars ljud exempel data från den angivna data strömmen.

Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten. När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **Buffer**: pekar mot bufferten för att spara exempel-byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Läsa 16-bitars exempel från ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Beskrivning

Den här funktionen läser 16-bitars ljud exempel data från den angivna data strömmen.

Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten. När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **Buffer**: pekare till bufferten för att spara 16-bitars exemplet.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Läs 24-bitars exempel från ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Beskrivning

Den här funktionen läser 24-bitars ljud exempel data från den angivna data strömmen.

Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten. När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **Buffer**: pekare till bufferten för att spara exemplet med tre byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Läs 32-bitars exempel från ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Beskrivning

Den här funktionen läser 32-bitars ljud exempel data från den angivna data strömmen.

Mer specifikt läser det exempel data från den aktuella bufferten för bild ramar i FIFO-enheten. När du läser det sista exemplet i en ljud ram frigörs ramen automatiskt så att den kan användas för att acceptera mer data från värden.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **Buffer**: pekar mot bufferten för att spara data för 4 byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

Få åtkomst till ljud ramen i ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Beskrivning

Den här funktionen returnerar den första ljud Rams bufferten och dess längd i den angivna data strömens FIFO. När programmet har behandlat data måste ux_device_class_audio_read_frame_free användas för att frigöra bildruteproportioner i FIFO.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **frame_data**: pekar på data pekare för att returnera data pekaren i.
- **frame_length**: pekare till buffer för att spara ram längden i antal byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Frigör en buffert i ljud fönstret i ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Beskrivning

Med den här funktionen frigörs ljud bildens buffert längst fram i den angivna data strömmens FIFO så att den kan ta emot data från värden.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Starta ljud data överföring för ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Beskrivning

Den här funktionen används för att börja skicka ljud data som skrivits till FIFO i klassen Audio.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är null.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Skriv en ljud bild ruta i ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Beskrivning

Den här funktionen skriver en ram till ljud strömmens FIFO. Ramdata kopieras till den tillgängliga bufferten i FIFO så att den kan skickas till värden.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **ram**: pekar mot ramdata.
- **frame_length** Ram längd i antal byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är full.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

Få åtkomst till ljud ramen i ljud strömmen

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Beskrivning

Den här funktionen hämtar adressen till den senaste ljud bildens buffert i FIFOn. den hämtar också längden på ljud Rams bufferten. När programmet har fyllt i ljud fönstrets buffert med önskade data, måste ***ux_device_class_audio_write_frame_commit*** användas för att lägga till/bekräfta RAMSIDAN till FIFO.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **frame_data**: pekar mot bildruta-datapekare för att returnera ramens data pekare i.
- **frame_length** Pekar på bufferten för att spara ram längden i antal byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är full.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

Bekräfta en buffert för ljud ramar i ljud strömmen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Beskrivning

Den här funktionen lägger till/aktiverar den senaste ljud bildens buffert till FIFO så att bufferten kan överföras till värden. Observera att den sista bufferten för ljud ramar borde ha fyllts i via ux_device_class_write_frame_get.

### <a name="parameters"></a>Parametrar

- **Stream**: pekar mot ljud Ströms instansen.
- **längd**: antal byte som är klara i bufferten.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) gränssnittet är nere.
- **UX_BUFFER_OVERFLOW** (0X5D) FIFO-bufferten är fssull.
- **UX_ERROR** (0Xff) fel från funktion

### <a name="example"></a>Exempel

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Bearbeta USB-ljud 1,0-kontroll begär Anden

### <a name="prototype"></a>Prototyp

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Beskrivning

Den här funktionen hanterar grundläggande förfrågningar som skickas av värden på kontrollens slut punkt med en USB-ljud1,0-typ.

Ljud 1,0 funktioner för volym-och ljud uppspelnings förfrågningar bearbetas i funktionen. När begär Anden bearbetas används fördefinierade data som skickas av den senaste parametern (grupp) för att besvara begär Anden och spara kontroll ändringar.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot ljud instansen.
- **överföring**: pekar mot överförings begär ande instansen.
- **grupp**: data grupp för process för begäran.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) fel från funktion

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

Bearbeta USB-ljud 1,0-kontroll begär Anden

### <a name="prototype"></a>Prototyp
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Beskrivning

Den här funktionen hanterar grundläggande förfrågningar som skickas av värden på kontrollens slut punkt med en USB-ljud2,0-typ.

Ljud 2,0 samplings frekvens (förmodad enkel fast frekvens), funktioner för volym och ljud av förfrågningar bearbetas i funktionen. När begär Anden bearbetas används fördefinierade data som skickas av den senaste parametern (grupp) för att besvara begär Anden och spara kontroll ändringar.

### <a name="parameters"></a>Parametrar

- **ljud**: pekar mot ljud instansen.
- **överföring**: pekar mot överförings begär ande instansen.
- **grupp**: data grupp för process för begäran.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) fel från funktion

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
