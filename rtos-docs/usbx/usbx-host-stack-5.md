---
title: Kapitel 5 – API för USBX-värdklasser
description: Lär dig mer om API:et FÖR USBX-värdklasser.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 2e9e2e0286300b3f79f7f9e6ad2d7fab96ba7337
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115177753"
---
# <a name="chapter-5---usbx-host-classes-api"></a>Kapitel 5 – API för USBX-värdklasser

Det här kapitlet beskriver alla exponerade API:er för USBX-värdklasserna. Följande API:er för varje klass beskrivs i detalj.

- HID-klass
- CDC-ACM-klass
- CDC-ECM-klass
- Storage klass

## <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

Registrera en HID-klient till HID-klassen.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a>Description

Den här funktionen används för att registrera en HID-klient till HID-klassen. HID-klassen måste hitta en matchning mellan en HID-enhet och HID-klienten innan data begärs från den här enheten.

> [!NOTE]
> C-strängen för hid_client_name måste vara NULL-avslutad och längden på den (utan själva NULL-terminatorn) får inte vara **större än UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.

### <a name="parameters"></a>Parametrar

- **hid_client_name** Pekare till HID-klientnamnet.
- **hid_client_handler** Pekare till HID-klienthanteraren.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes
- **UX_MEMORY_INSUFFICIENT** (0x12) Minnesallokeringen för klienten misslyckades.
- **UX_MEMORY_ARRAY_FULL** (0x1a) Maximalt antal klienter som redan har registrerats.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Den här klassen finns redan

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a>ux_host_class_hid_report_callback_register

Registrera ett återanrop från HID-klassen.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a>Description

Den här funktionen används för att registrera ett återanrop från HID-klassen till HID-klienten när en rapport tas emot.

### <a name="parameters"></a>Parametrar

- **hid** Pekare till HID-klassinstansen
- **call_back** Pekare till call_back struktur

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Ogiltig HID-instans.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Fel i registreringen av återanrop i rapporten.

### <a name="example"></a>Exempel

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a>ux_host_class_hid_periodic_report_start

Starta den periodiska slutpunkten för en HID-klassinstans.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>Description

Den här funktionen används för att starta den periodiska slutpunkten (avbrott) för instansen av HID-klassen som är bunden till den här HID-klienten. HID-klassen kan inte starta den periodiska slutpunkten förrän HID-klienten har aktiverats och därför är det upp till HID-klienten att starta slutpunkten för att ta emot rapporter.

### <a name="input-parameter"></a>Indataparameter

- **hid** Pekare till HID-klassinstansen.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Periodisk rapportering har startats.
- **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Fel i den periodiska rapporten.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a>ux_host_class_hid_periodic_report_stop

Stoppa den periodiska slutpunkten för en HID-klassinstans.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>Description

Den här funktionen används för att stoppa den periodiska slutpunkten (avbrott) för instansen av HID-klassen som är bunden till den här HID-klienten. HID-klassen kan inte stoppa den periodiska slutpunkten förrän HID-klienten har inaktiverats, alla dess resurser frigörs och därför lämnas den till HID-klienten för att stoppa den här slutpunkten.

### <a name="input-parameter"></a>Indataparameter

- **hid** Pekare till HID-klassinstansen.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Periodisk rapportering har stoppats.
- **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Fel i den periodiska rapporten.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

Hämta en rapport från en HID-klassinstans.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>Description

Den här funktionen används för att ta emot en rapport direkt från enheten utan att förlita sig på den periodiska slutpunkten. Den här rapporten kommer från kontrollslutpunkten, men dess behandling är densamma som om den kom till den periodiska slutpunkten.

### <a name="parameters"></a>Parametrar

- **hid** Pekare till HID-klassinstansen.
- **client_report** Pekare till HID-klientrapporten.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Rapporten togs emot.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Antingen var klientrapporten ogiltig eller felaktig under överföringen.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.
- **UX_BUFFER_OVERFLOW** (0x5d) Den angivna bufferten är inte tillräckligt stor för att hantera den okomprimerade rapporten.

### <a name="example"></a>Exempel

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

Skicka en rapport

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>Description

Den här funktionen används för att skicka en rapport direkt till enheten.

### <a name="parameters"></a>Parametrar

- **hid** Pekare till HID-klassinstansen.
- **client_report** Pekare till HID-klientrapporten.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Rapporten har skickats.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Antingen var klientrapporten ogiltig eller felaktig under överföringen.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.
- **UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) Den angivna bufferten är inte tillräckligt stor för att hantera den okomprimerade rapporten.

### <a name="example"></a>Exempel

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a>ux_host_class_hid_mouse_buttons_get

Hämta musknappar.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a>Description

Den här funktionen används för att hämta musknapparna

### <a name="parameters"></a>Parametrar

- **mouse_instance** Pekare till HID-musinstansen.
- **mouse_buttons** Pekare till returknapparna.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Musknappen har hämtats.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.

### <a name="example"></a>Exempel

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a>ux_host_class_hid_mouse_position_get

Hämta musposition.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a>Description

Den här funktionen används för att hämta musens position i x & y-koordinater.

### <a name="parameters"></a>Parametrar

- **mouse_instance** Pekare till HID-musinstansen.
- **mouse_x_position** Pekare till x-koordinaten.
- **mouse_y_position** Pekare till y-koordinaten.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) X &amp; Y-koordinater har hämtats.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.

### <a name="example"></a>Exempel

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a>ux_host_class_hid_keyboard_key_get

Hämta tangentbordsnyckel och tillstånd.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a>Description

Den här funktionen används för att hämta tangentbordstangenten och tillståndet.

### <a name="parameters"></a>Parametrar

- **keyboard_instance** Pekare till HID-tangentbordsinstansen.
- **keyboard_key** Pekare till tangentbordsnyckelcontainer.
- **keyboard_state** Pekare till tangentbordstillståndscontainern.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Nyckel och tillstånd hämtades.
- **UX_ERROR** (0xff) Inget att rapportera.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.

Tangentbordstillståndet kan ha följande värden.

- **UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000
- **UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001
- **UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002
- **UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004
- **UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007
- **UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100
- **UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200
- **UX_HID_KEYBOARD_STATE_SHIFT** 0x0300
- **UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400
- **UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800
- **UX_HID_KEYBOARD_STATE_ALT** 0x0a00
- **UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000
- **UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000
- **UX_HID_KEYBOARD_STATE_CTRL** 0x3000
- **UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000
- **UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000
- **UX_HID_KEYBOARD_STATE_GUI** 0xa000

### <a name="example"></a>Exempel

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a>ux_host_class_hid_keyboard_ioctl

Utför en IOCTL-funktion på HID-tangentbordet.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen utför en specifik ioctl-funktion till HID-tangentbordet. Anropet blockerar och returnerar endast när det finns ett fel eller när kommandot har slutförts.

### <a name="parameters"></a>Parametrar

- **keyboard_instance** Pekare till HID-tangentbordsinstansen.
- **ioctl_function** ioctl-funktion som ska utföras. Se tabellen nedan för en av de tillåtna ioctl-funktionerna.
- **parameter** Pekare till en parameter som är specifik för ioctl.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Ioctl-funktionen har slutförts.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Okänd IOCTL-funktion

### <a name="ioctl-functions"></a>IOCTL-funktioner

- UX_HID_KEYBOARD_IOCTL_SET_LAYOUT
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE

### <a name="example--change-keyboard-layout"></a>Exempel – ändra tangentbordslayout

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a>Exempel – inaktivera avkodning av tangentbordstangenten

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a>ux_host_class_hid_remote_control_usage_get

Hämta fjärrstyrningsanvändning

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a>Description

Den här funktionen används för att hämta fjärrstyrningsanvändningar.

### <a name="parameters"></a>Parametrar

- **remote_control_instance** Pekare till HID-fjärrstyrningsinstansen.
- **användning** Pekare till användningen.
- **värde** Pekare till värdet för användningen.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_ERROR** (0xff) Inget att rapportera.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID-klassinstansen finns inte.

Listan över alla möjliga användningsområden är för lång för att få plats i den här användarhandboken. En fullständig beskrivning finns i ux_host_class_hid.h innehåller hela uppsättningen möjliga värden.

### <a name="example"></a>Exempel

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

Läs från cdc_acm gränssnittet.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a>Description

Den här funktionen läser från cdc_acm gränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar.

> [!Note]
> Den här funktionen läser massdata från enheten, så den väntar tills bufferten är full eller enheten avslutar överföringen med ett kort paket (inklusive nolllängdspaket). Mer information finns i Allmänna överväganden [**för massöverföring.**](usbx-device-stack-5.md#general-considerations-for-bulk-transfer)

### <a name="parameters"></a>Parametrar

- **cdc_acm** Pekare till cdc_acm-klassinstansen.
- **data_pointer** Pekare till buffertadressen för datanyttolasten.
- **requested_length** Den längd som ska tas emot.
- **actual_length** Den längd som faktiskt har tagits emot.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Instansen cdc_acm är ogiltig.
- **UX_TRANSFER_TIMEOUT** (0x5c) Tidsgräns för överföring, läsning ofullständig.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a>ux_host_class_cdc_acm_write

Skriva till cdc_acm gränssnittet

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a>Description

Den här funktionen skriver till cdc_acm gränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **cdc_acm** Pekare till cdc_acm-klassinstansen.
- **data_pointer** Pekare till buffertadressen för datanyttolasten.
- **requested_length** Längd som ska skickas.
- **actual_length** Längden skickades faktiskt.

### <a name="return-values"></a>Returvärden

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Instansen cdc_acm är ogiltig.
- **UX_TRANSFER_TIMEOUT** (0x5c) Tidsgräns för överföring, skriv ofullständig.

### <a name="example"></a>Exempel

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a>ux_host_class_cdc_acm_ioctl

Utför en IOCTL-funktion till cdc_acm gränssnittet.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a>Description

Den här funktionen utför en specifik ioctl-funktion till cdc_acm gränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när kommandot har slutförts.

### <a name="parameters"></a>Parametrar

- **cdc_acm** Pekare till cdc_acm-klassinstansen.
- **ioctl_function** ioctl-funktion som ska utföras. Se tabellen nedan för en av de tillåtna ioctl-funktionerna.
- **parameter** Pekare till en parameter som är specifik för ioctl

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_MEMORY_INSUFFICIENT** (0x12) Det finns inte tillräckligt med minne.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM-instansen är i ett ogiltigt tillstånd.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) Funktionen Okänd IOCTL.

### <a name="ioctl-functions"></a>IOCTL-funktioner:

- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

Påbörjar bakgrundsmottagande av data från enheten.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>Description

Den här funktionen gör att USBX kontinuerligt läser data från enheten i bakgrunden. När varje transaktion har slutförts anropas **återanropet som anges i cdc_acm_reception** så att programmet kan utföra ytterligare bearbetning av transaktionens data.

> [!NOTE]
> **ux_host_class_cdc_acm_read** får inte användas när bakgrundsmottagandet används.

### <a name="parameters"></a>Parametrar

- **cdc_acm** Pekare till cdc_acm-klassinstansen.
- **cdc_acm_reception** Pekare till parameter som innehåller värden som definierar beteendet för bakgrundsmottagande. Layouten för den här parametern följer:

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Bakgrundsmottagande har startats.
- **UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Fel klassinstans.

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

Stoppar bakgrundsmottagande av paket.

### <a name="prototype"></a>Prototyp

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>Description

Den här funktionen gör att USBX stoppar bakgrundsmottagandet som tidigare startats **av ux_host_class_cdc_acm_reception_start**.

### <a name="parameters"></a>Parametrar

- **cdc_acm** Pekare till cdc_acm-klassinstansen.
- **cdc_acm_reception** Pekare till samma parameter som användes för att starta bakgrundsmottagandet. Layouten för den här parametern följer:

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Bakgrundsmottagande har stoppats.
- **UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Fel klassinstans.

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
