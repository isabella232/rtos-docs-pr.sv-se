---
title: Kapitel 4 – Beskrivning av USBX Device Services
description: Läs mer om USBX Device Services.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828137"
---
# <a name="description-of-usbx-device-services"></a>Beskrivning av USBX Device Services

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Hämta aktuell alternativ inställning för ett gränssnitts värde

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Beskrivning

Den här funktionen används av USB-värden för att hämta den aktuella alternativa inställningen för ett angivet gränssnitts värde. Den anropas av styrenhetens driv rutin när en **GET_INTERFACE** -begäran tas emot.

### <a name="input-parameter"></a>Indataparameter

- **Interface_value** Gränssnitts värde som den aktuella alternativa inställningen efterfrågar

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) data överföringen har slutförts.
- **UX_ERROR** (0Xff) felaktigt gränssnitts värde.

### <a name="example"></a>Exempel

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Ange den aktuella alternativa inställningen för ett gränssnitts värde

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Beskrivning

Den här funktionen används av USB-värden för att ange den aktuella alternativa inställningen för ett angivet gränssnitts värde. Den anropas av styrenhetens driv rutin när en **SET_INTERFACE** -begäran tas emot. När **SET_INTERFACE** har slutförts används värdena för de alternativa inställningarna i klassen.

Enhets stacken utfärdar en **UX_SLAVE_CLASS_COMMAND_CHANGE** till den klass som äger det här gränssnittet för att återspegla ändringen av en alternativ inställning.

### <a name="parameters"></a>Parametrar

- **interface_value**: gränssnitts värde som den aktuella alternativa inställningen har angetts för.
- **alternate_setting_value**: det nya värdet för alternativ inställning.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) data överföringen har slutförts.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0X52) inget gränssnitt har bifogats.
- **UX_FUNCTION_NOT_SUPPORTED** -enheten (0x54) har inte kon figurer ATS.
- **UX_ERROR** (0Xff) felaktigt gränssnitts värde.

### <a name="example"></a>Exempel

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

Registrera en ny USB-enhets klass

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Beskrivning

Den här funktionen används av programmet för att registrera en ny USB-enhets klass. Den här registreringen startar en klass behållare och inte en instans av klassen. En klass måste ha en aktiv tråd och vara kopplad till ett särskilt gränssnitt.

Vissa klasser förväntar sig en parameter-eller parameter lista. Enhets lagrings klassen förväntar sig till exempel geometrin för lagrings enheten som den försöker emulera. Parameter fältet är därför beroende av klass kravet och kan vara ett värde eller en pekare till en struktur som är ifylld med klass värden.

> [!NOTE]
> C-strängen för class_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **class_name** Klass namn
- **class_entry_function** Funktionen post i klassen.
- **configuration_number** Konfigurations numret som den här klassen är kopplad till.
- **interface_number** Gränssnitts numret som den här klassen är kopplad till.
- **parameter** En pekare till en lista med landsspecifika parametrar.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) klassen har registrerats
- **UX_MEMORY_INSUFFICIENT** (0X12) inga poster kvar i klass tabellen.
- **UX_THREAD_ERROR** (0X16) kan inte skapa en klass tråd.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Avregistrera en USB-enhets klass

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Beskrivning

Den här funktionen används av programmet för att avregistrera en USB-enhets klass.

> [!NOTE]
> C-strängen för class_name måste vara NULL-terminerad och längden på den (utan själva NULL-begränsaren) får inte vara större än **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **class_name**: klass namn
- **class_entry_function**: post funktionen i klassen.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) klassen har avregistrerats.
- **UX_NO_CLASS_MATCH** (0x57) klassen är inte registrerad.

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

### <a name="description"></a>Beskrivning

Den här funktionen används av värden för att hämta den aktuella konfigurationen som körs i enheten.

### <a name="input-parameter"></a>Indataparameter

Inget

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) data överföringen har slutförts.

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

### <a name="description"></a>Beskrivning

Den här funktionen används av värden för att ange den aktuella konfigurationen som körs i enheten. Vid mottagande av det här kommandot aktiverar USB-enheten den alternativa inställningen 0 för varje gränssnitt som är anslutet till den här konfigurationen.

### <a name="input-parameter"></a>Indataparameter

- **configuration_value** Konfiguration svärdet som valts av värden.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) konfigurationen har angetts.

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

### <a name="description"></a>Beskrivning

Den här funktionen används av enhets sidan för att returnera en beskrivning till värden. Den här beskrivningen kan vara en enhets beskrivning, en konfigurations beskrivning eller en sträng beskrivning.

### <a name="parameters"></a>Parametrar

- **descriptor_type**: typ av beskrivning. Måste vara något av följande värden.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index**: indexet för beskrivningen.
- **host_length**: längden som krävs av värden.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0x00) data överföringen har slutförts.
- **UX_ERROR** (0xFF) överföringen slutfördes inte.

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

Koppla bort enhets stack

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Beskrivning

VBUS Manager anropar den här funktionen när det finns en enhets anslutning. Enhets stacken meddelar alla klasser som är registrerade för enheten och släpper därefter alla enhets resurser.

### <a name="input-parameter"></a>Indataparameter

Inget

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) enheten kopplades från.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Villkor för begär slut punkts ficka

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas av USB-enhetens klass när en slut punkt ska returnera ett ficka-villkor till värden.

### <a name="input-parameter"></a>Indataparameter

- **slut punkt** Den slut punkt där parkerings villkoret har begärts.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0xFF) enheten är i ett ogiltigt tillstånd.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Väcka värden

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när enheten vill aktivera värden. Det här kommandot är endast giltigt när enheten är i paus läge. Det är upp till enhets programmet som avgör när du vill aktivera USB-värden. Ett USB-modem kan till exempel aktivera en värd när den identifierar en RING signal på telefon linjen.

### <a name="input-parameter"></a>Indataparameter

Inget

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) anropet lyckades.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) anropet misslyckades (enheten var förmodligen inte i paus läge).

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Initiera USB-enhets stack

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas av programmet för att initiera USB-enhetens stack. De initierar inga klasser eller styrenheter. Detta bör göras med separata funktions anrop. Det här anropet tillhandahåller huvudsakligen stacken med enhets ramverket för USB-funktionen. Det stöder både hög och fullständig hastighet med möjligheten att ha helt separata enhets ramverk för varje hastighet. Sträng ramverk och flera språk stöds.

### <a name="parameters"></a>Parametrar

- **device_framework_high_speed**: pekar mot ramverket med hög hastighet.
- **device_framework_length_high_speed**: längden på ramverket med hög hastighet.
- **device_framework_full_speed**: pekar mot ramverket med full hastighet.
- **device_framework_length_full_speed**: längden på ramverket med full hastighet.
- **string_framework**: pekar mot sträng ramverk.
- **string_framework_length**: sträng ramverkets längd.
- **language_id_framework**: pekar mot sträng språks ramverk.
- **language_id_framework_length**: längden på sträng språk ramverket.
- **ux_system_slave_change_function**: funktion som ska anropas när enhetens tillstånd ändras.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_MEMORY_INSUFFICIENT** (0x12) det finns inte tillräckligt med minne för att initiera stacken.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) beskrivningen är ogiltig.

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

Programmet kan begära ett anrop igen när styrenheten ändrar sitt tillstånd. De två huvud tillstånden för kontrollanten är:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Om programmet inte behöver pausa/återuppta signaler, skulle det tillhandahålla en UX_NULL-funktion.

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

Ta bort ett stack gränssnitt

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett gränssnitt ska tas bort. Ett gränssnitt tas bort när en enhet extraheras eller följer en återställning av bussen eller när det finns en ny alternativ inställning.

### <a name="input-parameter"></a>Indataparameter

- **gränssnitt**: pekar på det gränssnitt som ska tas bort.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Hämta det aktuella gränssnitt svärdet

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när värden frågar det aktuella gränssnittet. Enheten returnerar det aktuella gränssnitt svärdet.

> [!NOTE]
> Den här funktionen är föråldrad. Den är tillgänglig för äldre program vara, men den nya program varan bör använda funktionen ***ux_device_stack_alternate_setting_get*** i stället.

### <a name="input-parameter"></a>Indataparameter

- **interface_value** Gränssnitts värde att returnera.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) inget gränssnitt finns.

### <a name="example"></a>Exempel

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Ändra gränssnittets alternativa inställning

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när värden begär en ändring av den alternativa inställningen för gränssnittet.

### <a name="parameters"></a>Parametrar

- **device_framework**: adressen för det här gränssnittets enhets ramverk.
- **device_framework_length**: enhets ramverkets längd.
- **alternate_setting_value**: alternativ inställnings värde som ska användas av det här gränssnittet.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_ERROR** (0Xff) inget gränssnitt finns.

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

Starta sökning efter en klass för att äga en gränssnitts instans

### <a name="prototype"></a>Prototyp

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett gränssnitt har valts av värden och enhets stacken måste söka efter en enhets klass för att äga den här gränssnitts instansen.

### <a name="input-parameter"></a>Indataparameter

- **gränssnitt**: pekar mot gränssnittet som skapats.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_NO_CLASS_MATCH** (0x57) det finns ingen klass för det här gränssnittet.

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas när en klass eller stacken vill överföra data till värden. Värden avsöker alltid enheten men enheten kan förbereda data i förväg.

### <a name="parameters"></a>Parametrar

- **transfer_request**: pekar mot överförings förfrågan.
- **slave_length**: den längd som enheten vill returnera.
- **host_length**: längden på värden har begärts.

### <a name="return-values"></a>Retur värden

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.
- **UX_TRANSFER_NOT_READY** (0x25) enheten är i ett ogiltigt tillstånd. den måste vara **ansluten**, **konfigurerad** eller **adresserad**.
- **UX_ERROR** (0Xff) transport fel.

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program måste avbryta en överförings förfrågan eller när stacken måste avbryta en överföringsbegäran som är associerad med en slut punkt.

### <a name="parameters"></a>Parametrar

- **transfer_request**: pekar mot överförings förfrågan.
- **completion_code**: den felkod som ska returneras till klassen som väntar på att denna överföringsbegäran ska slutföras.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0X00) den här åtgärden lyckades.

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

### <a name="description"></a>Beskrivning

Den här funktionen anropas när ett program behöver unitialize USBX Device-stacken – alla enhets stack resurser frigörs. Detta ska anropas när alla klasser har avregistrerats via ux_device_stack_class_unregister.

### <a name="parameters"></a>Parametrar

Ingen

### <a name="return-value"></a>Returvärde

**UX_SUCCESS** (0X00) den här åtgärden lyckades.
