---
title: Kapitel 4 – Beskrivning av USBX-enhetstjänster
description: Läs mer om USBX-enhetstjänster.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9d88d9bd177a251a00fec6757fc1f1494b56bab9655a55f973481f273f0683ee
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797559"
---
# <a name="description-of-usbx-device-services"></a>Beskrivning av USBX-enhetstjänster

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Hämta aktuell alternativ inställning för ett gränssnittsvärde

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Description

Den här funktionen används av USB-värden för att hämta den aktuella alternativa inställningen för ett specifikt gränssnittsvärde. Den anropas av kontrollantdrivrutinen när en **GET_INTERFACE** tas emot.

### <a name="input-parameter"></a>Indataparameter

- **Interface_value** Gränssnittsvärde som den aktuella alternativa inställningen efterfrågas för

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_ERROR** (0xFF) Fel gränssnittsvärde.

### <a name="example"></a>Exempel

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Ange aktuell alternativ inställning för ett gränssnittsvärde

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Description

Den här funktionen används av USB-värden för att ange den aktuella alternativa inställningen för ett specifikt gränssnittsvärde. Den anropas av kontrollantdrivrutinen när en **SET_INTERFACE** tas emot. När **SET_INTERFACE** har slutförts tillämpas värdena för de alternativa inställningarna på klassen .

Enhetsstacken utfärdar en **UX_SLAVE_CLASS_COMMAND_CHANGE** den klass som äger det här gränssnittet för att återspegla ändringen av den alternativa inställningen.

### <a name="parameters"></a>Parametrar

- **interface_value:** Gränssnittsvärde som den aktuella alternativa inställningen har angetts för.
- **alternate_setting_value:** Det nya alternativa inställningsvärdet.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Inget gränssnitt kopplat.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Enheten har inte konfigurerats.
- **UX_ERROR** (0xFF) Fel gränssnittsvärde.

### <a name="example"></a>Exempel

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

Registrera en ny USB-enhetsklass

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen används av programmet för att registrera en ny USB-enhetsklass. Den här registreringen startar en klasscontainer och inte en instans av klassen . En klass ska ha en aktiv tråd och kopplas till ett specifikt gränssnitt.

Vissa klasser förväntar sig en parameter eller parameterlista. Enhetslagringsklassen förväntar sig till exempel geometrin för lagringsenheten som den försöker emulera. Parameterfältet är därför beroende av klasskravet och kan vara ett värde eller en pekare till en struktur som är fylld med klassvärdena.

> [!NOTE]
> C-strängen för class_name måste vara NULL-avslutad och längden på den (utan själva NULL-terminatorn) får inte vara **större än UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **class_name** Klassnamn
- **class_entry_function** Entry-funktionen för klassen .
- **configuration_number** Konfigurationsnumret som den här klassen är kopplad till.
- **interface_number** Gränssnittsnumret som den här klassen är kopplad till.
- **parameter** En pekare till en klassspecifik parameterlista.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Klassen registrerades
- **UX_MEMORY_INSUFFICIENT** (0x12) Inga poster kvar i klasstabellen.
- **UX_THREAD_ERROR** (0x16) Det går inte att skapa en klasstråd.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Avregistrera en USB-enhetsklass

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Description

Den här funktionen används av programmet för att avregistrera en USB-enhetsklass.

> [!NOTE]
> C-strängen för class_name måste vara NULL-avslutad och längden på den (utan själva NULL-terminatorn) får inte vara **större än UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **class_name**: Klassnamn
- **class_entry_function:** Postfunktionen i klassen .

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Klassen avregistrerades.
- **UX_NO_CLASS_MATCH** (0x57) Klassen är inte registrerad.

### <a name="example"></a>Exempel

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

Hämta den aktuella konfigurationen

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>Description

Den här funktionen används av värden för att hämta den aktuella konfigurationen som körs på enheten.

### <a name="input-parameter"></a>Indataparameter

Ingen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

Ange den aktuella konfigurationen

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Description

Den här funktionen används av värden för att ange den aktuella konfigurationen som körs på enheten. Vid mottagning av det här kommandot aktiverar USB-enhetsstacken den alternativa inställningen 0 för varje gränssnitt som är anslutet till den här konfigurationen.

### <a name="input-parameter"></a>Indataparameter

- **configuration_value** Konfigurationsvärdet som valts av värden.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Konfigurationen har angetts.

### <a name="example"></a>Exempel

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

Skicka en beskrivning till värden

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Description

Den här funktionen används av enheten för att returnera en beskrivning till värden. Den här beskrivningen kan vara en enhetsbeskrivning, en konfigurationsbeskrivning eller en strängbeskrivning.

### <a name="parameters"></a>Parametrar

- **descriptor_type:** Beskrivningens typ. Måste vara något av följande värden.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index:** Indexet för beskrivningen.
- **host_length:** Den längd som krävs av värden.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_ERROR** (0xFF) Överföringen slutfördes inte.

### <a name="example"></a>Exempel

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

Koppla från enhetsstack

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Description

VBUS-hanteraren anropar den här funktionen när enheten kopplas från. Enhetsstacken informerar alla klasser som är registrerade på den här enheten och kommer därefter att släppa alla enhetsresurser.

### <a name="input-parameter"></a>Indataparameter

Ingen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Enheten kopplades från.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Villkor för slutpunktsstopp för begäran

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Description

Den här funktionen anropas av USB-enhetsklassen när en slutpunkt ska returnera ett stoppvillkor till värden.

### <a name="input-parameter"></a>Indataparameter

- **slutpunkt** Slutpunkten där villkoret Stall begärs.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Enheten är i ett ogiltigt tillstånd.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Väck värden

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Description

Den här funktionen anropas när enheten vill väcka värden. Det här kommandot är endast giltigt när enheten är i pausläge. Det är upp till enhetsprogrammet att bestämma när det vill väcka USB-värden. Ett USB-modem kan till exempel väcka en värd när den identifierar en RING-signal på telefonlinjen.

### <a name="input-parameter"></a>Indataparameter

Ingen

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Anropet lyckades.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Anropet misslyckades (enheten var förmodligen inte i inaktiverat läge).

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Initiera USB-enhetsstack

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>Description

Den här funktionen anropas av programmet för att initiera USB-enhetsstacken. Inga klasser eller kontrollanter initieras. Detta bör göras med separata funktionsanrop. Det här anropet tillhandahåller huvudsakligen stacken med enhetsramverket för USB-funktionen. Den stöder både höga och fullständiga hastigheter med möjlighet att ha ett helt separat enhetsramverk för varje hastighet. Strängramverk och flera språk stöds.

### <a name="parameters"></a>Parametrar

- **device_framework_high_speed:** Pekare till ramverket för hög hastighet.
- **device_framework_length_high_speed:** Längden på ramverket för hög hastighet.
- **device_framework_full_speed:** Pekare till ramverket för full hastighet.
- **device_framework_length_full_speed:** Längden på ramverket för full hastighet.
- **string_framework**: Pekare till strängramverk.
- **string_framework_length:** Längden på strängramverket.
- **language_id_framework**: Pekare till ramverket för strängspråk.
- **language_id_framework_length:** Längden på ramverket för strängspråk.
- **ux_system_slave_change_function:** Funktionen anropas när enhetens tillstånd ändras.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_MEMORY_INSUFFICIENT** (0x12) Det finns inte tillräckligt med minne för att initiera stacken.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) Beskrivningen är ogiltig.

### <a name="example"></a>Exempel

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Programmet kan begära ett samtal tillbaka när kontrollanten ändrar sitt tillstånd. Kontrollantens två huvud tillstånd är:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Om programmet inte behöver pausa/återuppta-signaler skulle det tillhandahålla en UX_NULL funktion.

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

Ta bort ett stackgränssnitt

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett gränssnitt ska tas bort. Ett gränssnitt tas antingen bort när en enhet extraheras eller efter en bussåterställning, eller när det finns en ny alternativ inställning.

### <a name="input-parameter"></a>Indataparameter

- **interface**: Pekare till gränssnittet som ska tas bort.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Hämta det aktuella gränssnittsvärdet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Description

Den här funktionen anropas när värden frågar det aktuella gränssnittet. Enheten returnerar det aktuella gränssnittsvärdet.

> [!NOTE]
> Den här funktionen är inaktuell. Den är tillgänglig för äldre programvara, men ny programvara bör använda ***ux_device_stack_alternate_setting_get*** i stället.

### <a name="input-parameter"></a>Indataparameter

- **interface_value** Gränssnittsvärde som ska returneras.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Det finns inget gränssnitt.

### <a name="example"></a>Exempel

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Ändra den alternativa inställningen för gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Description

Den här funktionen anropas när värden begär en ändring av den alternativa inställningen för gränssnittet.

### <a name="parameters"></a>Parametrar

- **device_framework:** Adressen till enhetsramverket för det här gränssnittet.
- **device_framework_length:** Enhetens ramverks längd.
- **alternate_setting_value:** Alternativt inställningsvärde som ska användas av det här gränssnittet.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_ERROR** (0xFF) Det finns inget gränssnitt.

### <a name="example"></a>Exempel

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

Börja söka efter en klass för att äga en gränssnittsinstans

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett gränssnitt har valts av värden och enhetsstacken måste söka efter en enhetsklass för att äga den här gränssnittsinstansen.

### <a name="input-parameter"></a>Indataparameter

- **interface**: Pekare till det gränssnitt som skapats.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_NO_CLASS_MATCH** (0x57) Det finns ingen klass för det här gränssnittet.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

Begäran om att överföra data till värden

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Description

Den här funktionen anropas när en klass eller stack vill överföra data till värden. Värden avsöker alltid enheten, men enheten kan förbereda data i förväg.

### <a name="parameters"></a>Parametrar

- **transfer_request:** Pekare till överföringsbegäran.
- **slave_length:** Längden som enheten vill returnera.
- **host_length:** Längden som värden har begärt.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.
- **UX_TRANSFER_NOT_READY** (0x25) Enheten är i ett ogiltigt tillstånd. den måste vara **ANSLUTEN,** **KONFIGURERAD** eller **ADRESSERAD.**
- **UX_ERROR** (0xFF) Transportfel.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

Avbryta en överföringsbegäran

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver avbryta en överföringsbegäran eller när stacken behöver avbryta en överföringsbegäran som är associerad med en slutpunkt.

### <a name="parameters"></a>Parametrar

- **transfer_request:** Pekare till överföringsbegäran.
- **completion_code:** Felkod som ska returneras till klassen som väntar på att överföringsbegäran ska slutföras.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

Unitialize-stack

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Description

Den här funktionen anropas när ett program behöver unitialisera USBX-enhetsstacken – alla enhetsstackresurser frigörs. Detta bör anropas när alla klasser har avregistrerats via ux_device_stack_class_unregister.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-value"></a>Returvärde

**UX_SUCCESS** (0x00) Den här åtgärden lyckades.
