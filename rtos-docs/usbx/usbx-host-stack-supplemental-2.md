---
title: API för USBX-värdklasser
description: Det här kapitlet beskriver alla exponerade API:er för USBX-värdklasserna.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28e733e37b06da7053f238e23e2b8b8046df2dd9940e50cd0321ccf15c27ec47
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802115"
---
# <a name="chapter-2-usbx-host-classes-api"></a>Kapitel 2: API för USBX-värdklasser

Det här kapitlet beskriver alla exponerade API:er för USBX-värdklasserna. Följande API:er för varje klass beskrivs i detalj.

- Skrivarklass
- Ljudklass
- Asix-klass
- Pima/PTP-klass
- Prolific-klass
- Allmän serieklass

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Läs från skrivargränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Den här funktionen läser från skrivargränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar. Läsningar tillåts endast på dubbelriktade skrivare.

### <a name="parameters"></a>Parametrar

- **printer**: Pekare till skrivarklassinstansen.
- **data_pointer:** Pekare till buffertadressen för datanyttolasten.
- **requested_length:** Längd som ska tas emot.
- **actual_length:** Längden togs faktiskt emot.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen stöds inte eftersom skrivaren inte är dubbelriktad.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tidsgräns för överföring, läsning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Skriv till skrivargränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Den här funktionen skriver till skrivargränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **printer**: Pekare till skrivarklassinstansen.
- **data_pointer:** Pekare till buffertadressen för datanyttolasten.
- **requested_length:** Längd som ska skickas.
- **actual_length:** Längden skickas faktiskt.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Tidsgräns för överföring, skriv ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Utför en mjuk återställning till skrivaren.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Description

Den här funktionen utför en mjuk återställning till skrivaren.

### <a name="input-parameter"></a>Indataparameter

- **printer**: Pekare till skrivarklassinstansen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00)Återställningen slutfördes.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tidsgräns för överföring, återställning har inte slutförts.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Hämta skrivarstatus

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Description

Den här funktionen hämtar skrivarstatusen. Skrivarstatusen liknar LPT-statusen (1284 standard).

### <a name="parameters"></a>Parametrar

- **printer**: Pekare till skrivarklassinstansen.
- **printer_status:** Adressen till den status som ska returneras.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00): Återställningen slutfördes.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att utföra åtgärden.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tidsgräns för överföring, återställning har inte slutförts

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

Hämta skrivarenhetens ID.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Description

Den här funktionen hämtar skrivarens IEEE 1284-enhets-ID-sträng (inklusive längd i de första två bytena i big endian format).

### <a name="parameters"></a>Parametrar

- **printer**: Pekare till skrivarklassinstansen.
- **descriptor_buffer: Pekare** till en buffert för att fylla IEEE 1284-enhetens ID-sträng (inklusive längden i de första två byteen i BE-format) 
- **length**: Längden på bufferten i byte.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00): Åtgärden lyckades.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att utföra åtgärden.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tidsgräns för överföring, begäran slutfördes inte
- **UX_TRANSFER_NOT_READY**: (0x25) Enheten var i ett ogiltigt tillstånd – måste vara ANSLUTEN, ADRESSERad eller KONFIGURERAd.
- **UX_TRANSFER_STALL**: (0x21) Överföringen har stoppats.
- **TX_WAIT_ABORTED** (0x1A) Brytningen avbröts av en annan tråd, timer eller ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) Ogiltig inventerings-semaphore-pekare.
- **TX_WAIT_ERROR** (0x04) Ett annat väntealternativ än TX_NO_WAIT angavs för ett anrop från en icke-tråd.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Läs från ljudgränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Description

Den här funktionen läser från ljudgränssnittet. Anropet är icke-blockerande. Programmet måste se till att lämplig alternativ inställning har valts för ljudströmningsgränssnittet.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudklassinstansen.
- **audio_transfer_request:** Pekare till ljudöverföringsstrukturen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes
- **UX_FUNCTION_NOT_SUPPORTED**" (0x54) Funktionen stöds inte

### <a name="example"></a>Exempel

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

Skriv till ljudgränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Description

Den här funktionen skriver till ljudgränssnittet. Anropet är icke-blockerande. Programmet måste se till att lämplig alternativ inställning har valts för ljudströmningsgränssnittet.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudklassinstansen
- **audio_transfer_request:** Pekare till ljudöverföringsstrukturen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen stöds inte.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Felaktigt gränssnitt.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

Hämta en specifik kontroll från ljudkontrollgränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Description

Den här funktionen läser en specifik kontroll från ljudkontrollgränssnittet.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudklassinstansen
- **audio_control:** Pekare till ljudkontrollstrukturen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Felaktigt gränssnitt

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

Ange en specifik kontroll till ljudkontrollgränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

**Beskrivning **

Den här funktionen anger en specifik kontroll till ljudkontrollgränssnittet.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudklassinstansen
- **audio_control:** Pekare till ljudkontrollstrukturen

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Felaktigt gränssnitt

### <a name="example"></a>Exempel

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

Ange ett alternativt inställningsgränssnitt för ljudströmningsgränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Description

Den här funktionen anger lämpligt alternativt inställningsgränssnitt för ljudströmningsgränssnittet enligt en specifik samplingsstruktur.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudklassinstansen.
- **audio_sampling:** Pekare till ljudsamplingsstrukturen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Felaktigt gränssnitt
- **UX_NO_ALTERNATE_SETTING**: (0x5e) Ingen alternativ inställning för samplingsvärdena

### <a name="example"></a>Exempel

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

Hämta möjliga samplingsinställningar för ljudströmningsgränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Description

Den här funktionen hämtar alla möjliga samplingsinställningar som är tillgängliga i var och en av de alternativa inställningarna för ljudströmningsgränssnittet. Första gången funktionen används måste alla fält i pekaren för den anropande strukturen återställas. Funktionen returnerar en specifik uppsättning strömningsvärden vid retur såvida inte slutet av de alternativa inställningarna har uppnåtts. När den här funktionen återanvänds används de tidigare samplingsvärdena för att hitta nästa samplingsvärden.

### <a name="parameters"></a>Parametrar

- **audio**: Pekare till ljudklassinstansen.
- **audio_sampling:** Pekare till ljudsamplingsstrukturen.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen stöds inte
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Felaktigt gränssnitt
- **UX_NO_ALTERNATE_SETTING**: (0x5e) Ingen alternativ inställning för samplingsvärdena

### <a name="example"></a>Exempel

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Läs från asix-gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Den här funktionen läser från asix-gränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **asix:** Pekare till asix-klassinstansen.
- **data_pointer:** Pekare till buffertadressen för datanyttolasten.
- **requested_length:** Längd som ska tas emot.
- **actual_length:** Längden togs faktiskt emot.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tidsgräns för överföring, läsning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Skriv till asix-gränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Description

Den här funktionen skriver till asix-gränssnittet. Anropet är inte blockerande.

### <a name="parameters"></a>Parametrar

- **asix:** Pekare till asix-klassinstansen.
- **paket:** Netx-datapaket

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_ERROR**: (0xFF) Överföring kunde inte begäras.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Öppna en session mellan Initierare och Svarare.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Description

Den här funktionen öppnar en session mellan en PIMA-initierare och en PIMA-svarare. När en session har öppnats kan de flesta PIMA-kommandon köras.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_sessio:** Pekare till PIMA-<

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS:**(0x00) Sessionen har öppnats
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session har redan öppnats

### <a name="example"></a>Exempel

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Stäng en session mellan initieraren och svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Description

Den här funktionen stänger en session som tidigare öppnades mellan en PIMA-initierare och en PIMA-svarare. När en session har stängts kan de flesta PIMA-kommandon inte längre köras.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Sessionen stängdes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Session öppnas inte.

### <a name="example"></a>Exempel

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Hämta lagrings-ID-matrisen från svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Description

Den här funktionen hämtar lagrings-ID-matrisen från svararen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **storage_ids_array:** Matris där lagrings-ID:er returneras
- **storage_id_length:** Lagringsmatrisens längd

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Lagrings-ID-matrisen har fyllts i
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

Hämta lagringsinformationen från svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Description

Den här funktionen hämtar lagringsinformationen för en lagringscontainer med *värdet storage_id*.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **storage_id:** ID för lagringscontainern
- **storage**: Pekare till lagringsinformationscontainer

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Lagringsinformationen hämtades
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_MEMORY_INSUFFICIENT** (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

Hämta antalet objekt i en lagringscontainer från svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Description

Den här funktionen hämtar antalet objekt som lagras i en specifik lagringscontainer med storage_id som matchar en specifik formatkod. Antalet objekt returneras i fältet: ux_host_class_pima_session_nb_objects av pima_session struktur.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **storage_id:** ID för lagringscontainern
- **object_format_code:** Kodfilter för objektformat.

Objektformatkoderna kan ha något av följande värden.

| Objektformatkod               | Description   |     USBX-kod                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Odefinierat odefinierat objekt som inte är avbildningsobjekt | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Association Association (t.ex. mapp) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Skript för enhetsmodellspecifikt skript | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Körbar enhetsmodellspecifik binär körbar fil | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Texttextfil  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | HTML HyperText Markup Language-fil (text) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | DPOF Digital Print Order Format-fil (text) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | AIFF-ljudklipp  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | WAV-ljudklipp   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | MP3-ljudklipp   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | AVI-videoklipp   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | MPEG-videoklipp  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | ASF Microsoft Advanced Streaming Format (video) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Odefinierat okänt bildobjekt | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | EXIF/JPEG Exchangeable File Format, JEIDA standard | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | TIFF/EP Tag Image File Format for Electronic Photography | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | FlashPix Structured Storage-bildformat | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP Microsoft Windows Bitmapp-fil | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | Bildfilformat för CIFF Canon-kamera | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Odefinierad reserverad |  |
| 0x3807                           | GIF-Graphics Interchange Format | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | JFIF JPEG-filutbytesformat | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD PhotoCD Image Pac | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | PICT Quickdraw Image Format | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | PNG-Portable Network Graphics | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Odefinierad reserverad |   |
| 0x380D                           | TIFF-taggbildfilformat | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | TIFF/IT Tag Image File Format for Information Technology (grafisk grafik) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | JP2 JPEG2000-baslinjefilformat | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | JPX JPEG2000 utökat filformat | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Alla andra koder med MSN från 0011 | Odefinierad reserverad för framtida användning |                                    |
| Alla andra koder med MSN från 1011 | Alla leverantörsdefinierade leverantörsdefinierade typer: Avbildning |                                    |

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

Hämta objektreferenser från svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a>Description

Returnerar en matris med objektreferenser som finns i lagringscontainern som anges storage_id parametern. Om du vill ha en aggregerad lista över alla butiker ska värdet anges till 0xFFFFFFFF.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **object_handes_array:** Matris där referenser returneras
- **object_handles_length:** Matrisens längd
- **storage_id:** ID för lagringscontainern
- **object_format_code:** Formatera kod för objekt (se tabell för ux_host_class_pima_num_objects_get)
- **object_handle_association:** Valfritt objektassociationsvärde

Objekthandtagsassociationen kan vara ett av värdet i tabellen nedan:

| AssociationCode                        | AssociationType      | Tolkning       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Undefined (Odefinierad)            | Undefined (Odefinierad)            |
| 0x0001                                 | GenericFolder        | Oanvända               |
| 0x0002                                 | Album                | Reserverat             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | Oanvända               |
| 0x0005                                 | VerticalPanoramic    | Oanvända               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | Extradata        | Undefined (Odefinierad)            |
| Alla andra värden med bit 15 inställt på 0  | Reserverat             | Undefined (Odefinierad)            |
| Alla värden med bit 15 inställt på 1        | Leverantörsdefinierad       | Leverantörsdefinierad       |

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

Hämta objektinformationen från svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Den här funktionen hämtar objektinformationen för en objekthanterare.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **object_handle**: Referens för objektet
- **object**: Pekare till objektinformationscontainer

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

Skicka objektinformationen till svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Den här funktionen skickar lagringsinformation för en lagringscontainer med storage_id. Initieraren bör använda det här kommandot innan ett objekt skickas till svararen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session.
- **storage_id:** Mållagrings-ID.
- **parent_object_id:** Överordnad ObjectHandle på Svarare där objektet ska placeras.
- **object**: Pekare till objektinformationscontainern.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

Öppna ett objekt som lagras i svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Den här funktionen öppnar ett objekt på svararen innan du läser eller skriver.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session.
- **object_handle**: referens för objektet.
- **objec:** Pekare till objektinformationscontainer.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Objektet har redan öppnats.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

Hämta ett objekt som lagras i svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a>Description

Den här funktionen hämtar ett -objekt på svararen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **object_handle**: referens för objektet
- **object**: Pekare till objektinformationscontainer
- **object_buffer:** Adressen till objektdata
- **object_buffer_length:** Begärd längd på objekt
- **object_actual_length:** Längden på det objekt som returneras

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Objektet överfördes
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objektet har inte öppnats.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Åtkomst till objekt nekad
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) Överföringen är ofullständig
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.
- **UX_TRANSFER_ERROR:**(0x23) Överföringsfel vid läsning av objekt

### <a name="example"></a>Exempel

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

Skicka ett objekt som lagras i svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Description

Den här funktionen skickar ett -objekt till svararen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_sessio:** Pekare till PIMA-session
- **object_handle**: referens för objektet
- **object**: Pekare till objektinformationscontainer
- **object_buffer:** Adressen till objektdata
- **object_buffer_length:** Begärd längd på objekt

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sessionen är inte öppen
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objektet öppnas inte.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Åtkomst till objekt nekad
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) Överföringen är ofullständig
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.
- **UX_TRANSFER_ERROR:**(0x23) Överföringsfel vid skrivning av objekt

### <a name="example"></a>Exempel

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

Hämta ett tumobjekt som lagras i svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Description

Den här funktionen hämtar ett tumobjekt på svararen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session.
- **object_handle**: referens för objektet.
- **object**: Pekare till objektinformationscontainern.
- **thumb_buffer:** Adressen till tumobjektdata.
- **thumb_buffer_length:** Begärd längd på tumobjektet.
- **thumb_actual_length:** Längden på det tumobjekt som returneras.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Session öppnas inte.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objektet öppnas inte.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Åtkomst till objekt nekad.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) Överföringen är ofullständig.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.
- **UX_TRANSFER_ERROR:**(0x23) Överföringsfel vid läsning av objekt.

### <a name="example"></a>Exempel

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

Ta bort ett objekt som lagras i svararen.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Description

Den här funktionen tar bort ett objekt på svararen

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session
- **object_handle**: referens för objektet

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Objektet har tagits bort.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Session öppnas inte.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Det går inte att ta bort objektet.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Stäng ett objekt som lagras i svararen

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Description

Den här funktionen stänger ett objekt på svararen.

### <a name="parameters"></a>Parametrar

- **pima:** Pekare till pima-klassinstansen.
- **pima_session:** Pekare till PIMA-session.
- **object_handle**: Objektets referens.
- **object**: Pekare till objekt.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Objektet stängdes.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Session öppnas inte.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objektet öppnas inte.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne för att skapa PIMA-kommandot.

### <a name="example"></a>Exempel

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Läs från det allmänna seriegränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Den här funktionen läser från det allmänna seriegränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **gser:** Pekare till gser-klassinstansen.
- **interface_index:** Gränssnittsindex att läsa från.
- **data_pointer:** Pekare till buffertadressen för datanyttolasten.
- **requested_length:** Längd som ska tas emot.
- **actual_length:** Längden togs faktiskt emot.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Tidsgräns för överföring, läsning ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Skriv till det allmänna seriegränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Den här funktionen skriver till det allmänna seriegränssnittet. Anropet blockerar och returnerar bara när det finns ett fel eller när överföringen är klar.

### <a name="parameters"></a>Parametrar

- **gser:** Pekare till gser-klassinstansen.
- **interface_index:** Gränssnitt som du vill skriva till.
- **data_pointer:** Pekare till buffertadressen för datanyttolasten.
- **requested_length:** Längd som ska skickas.
- **actual_length:** Längden skickas faktiskt.

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_TRANSFER_TIMEOUT**: (0x5c) Tidsgräns för överföring, skriv ofullständig.

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

Utför en IOCTL-funktion i det generiska seriegränssnittet.

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Description

Den här funktionen utför en specifik ioctl-funktion för gser-gränssnittet. Anropet blockerar och returnerar endast när det finns ett fel eller när kommandot har slutförts.

### <a name="parameters"></a>Parametrar

- **gser:** Pekare till gser-klassinstansen.
- **ioctl_function:** ioctl-funktion som ska utföras. Se tabellen nedan för en av de tillåtna ioctl-funktionerna.
- **parameter**: Pekare till en parameter som är specifik för ioctl

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS**: (0x00) Dataöverföringen slutfördes.
- **UX_MEMORY_INSUFFICIENT**: (0x12) Det finns inte tillräckligt med minne.
- **UX_HOST_CLASS_UNKNOWN**: (0x59) Fel klassinstans
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) Funktionen Okänd IOCTL.

### <a name="ioctl-functions"></a>IOCTL-funktioner

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>Exempel

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

Starta mottagning på det allmänna seriegränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Description

Den här funktionen startar mottagningen i det generiska serieklassgränssnittet. Den här funktionen tillåter icke-blockerande mottagning. När en buffert tas emot anropas ett återanrop i programmet.

### <a name="parameters"></a>Parametrar

- **gser** Pekare till gser-klassinstansen.
- **gser_reception** Struktur som innehåller mottagningsparametrarna

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Fel klassinstans
- **UX_ERROR** (0x01)-fel

### <a name="example"></a>Exempel

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

Stoppa mottagning på det allmänna seriegränssnittet

### <a name="prototype"></a>Prototyp

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Description

Den här funktionen stoppar mottagningen i det generiska serieklassgränssnittet.

### <a name="parameters"></a>Parametrar

- **gser** Pekare till gser-klassinstansen.
- **gser_reception** Struktur som innehåller mottagningsparametrarna

### <a name="return-value"></a>Returvärde

- **UX_SUCCESS** (0x00) Dataöverföringen slutfördes.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Fel klassinstans
- **UX_ERROR** (0x01)-fel

### <a name="example"></a>Exempel

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
