---
title: Kapitel 3 – Funktionsbeskrivning av Azure RTOS NetX LWM2M
description: Det här kapitlet innehåller en funktionell beskrivning av Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6424023a02aedf43c7433c9adc09231b8c146af13b9bddc15ebd1f2fc02e8c8a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784945"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Kapitel 3 – Funktionsbeskrivning av Azure RTOS NetX LWM2M

Det här kapitlet innehåller en funktionell beskrivning av Azure RTOS NetX LWM2M.

## <a name="lwm2m-client-initialization"></a>Initiering av LWM2M-klient

LWM2M-klienten initieras genom  att anropa nx_lwm2m_client_create tjänsten. LWM2M-klienten körs i en egen tråd och kan rapportera vissa händelser till programmet med hjälp av återanrop, eller genom att anropa metoder för de anpassade objekt som implementeras av programmet.

Dessutom måste LWM2M-klientsessioner skapas genom att ***anropa nx_lwm2m_client_session_create*** för att möjliggöra kommunikation med en eller flera servrar. En session kan kommunicera med två olika typer av servrar: en Bootstrap-server eller en LWM2M-server (Enhetshantering).

### <a name="bootstrap-server-session"></a>Bootstrap-serversession

En kommunikationssession med en Bootstrap-server används för att etablera viktig information i LWM2M-klienten så att LWM2M-klienten kan utföra åtgärden "Registrera" med en eller flera LWM2M-servrar. Den här typen av server används i lägena Klientinitierad och Serverinitierad bootstrap.

Programmet kan starta en Bootstrap-session genom att anropa ***nx_lwm2m_client_session_bootstrap** _ eller _*_nx_lwm2m_client_session_bootstrap_dtls_*_. Det måste ange serverns IP-adress och portnummer samt ett valfritt ID för instans-ID för säkerhetsobjekt. Funktionen _*_nx_lwm2m_client_session_bootstrap_*_ använder osäker kommunikation, medan _ nx_lwm2m_client_session_bootstrap_dtls **_upprättar_* en säker DTLS-anslutning till servern.

Om Bootstrap-åtgärden lyckas bör Bootstrap-servern ha skapat säkerhetsobjektinstanser för Bootstrap- och LWM2M-servrarna och serverobjektinstanserna för LWM2M-servrarna. Programmet måste använda den här informationen för att upprätta en session med LWM2M-servrarna.

Bootstrap-data ska sparas i beständigt minne av programmet för att konfigurera LWM2M-klienten vid nästa omstart av enheten.

### <a name="lwm2m-server-session"></a>LWM2M-serversession

En kommunikationssession med en LWM2M-server används för registrering, Enhetshantering och tjänstaktivering.

Programmet kan registrera LWM2M-klienten till en server genom att anropa ***nx_lwm2m_client_session_register** _ eller _*_nx_lwm2m_client_session_register_dtls_*_, måste det ange serverns IP-adress och portnummer samt det korta server-ID som motsvarar en befintlig serverobjektinstans. Funktionen _*_nx_lwm2m_client_session_register_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_register_dtls_** upprättar en säker DTLS-anslutning med servern.

Programmet kan avregistrera LWM2M-klienten genom att anropa ***nx_lwm2m_client_session_deregister** _, och be klienten att skicka ett uppdateringsmeddelande genom att anropa _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Återanrop av sessionstillstånd

Programmet registrerar ett återanrop när en session skapas som anropas när sessionens tillstånd uppdateras. Återanropsfunktionen i NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK har följande prototyp:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

Följande tillstånd definieras:

- **NX_LWM2M_CLIENT_SESSION_INIT:** Det ursprungliga tillståndet när sessionen har skapats.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING:** Klienten väntar på att timern "Håll av" eller ServerInitierad bootstrap ska förfalla.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:** Klienten har skickat ett meddelande om begäran till Bootstrap-servern (klientinitierad bootstrap).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:** Klienten tar emot data från Bootstrap-servern.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:** Bootstrap-servern har skickat meddelandet "Slutfört".

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:** Bootstrap-sessionen misslyckades.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING:** Klienten har skickat ett registermeddelande till LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED:** Klienten är registrerad på LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_UPDATING:** Klienten har skickat ett uppdateringsmeddelande till LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING:** Klienten har skickat meddelandet "Avregistrera" till LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED:** Klienten avregistreras från LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DISABLED:** LWM2M-servern är inaktiverad. Ett "Register" skickas efter att inaktiveringstiden har gått ut.

- **NX_LWM2M_CLIENT_SESSION_ERROR:** Registrerings- eller uppdateringsåtgärden för LWM2M-servern misslyckades.

- **NX_LWM2M_CLIENT_SESSION_DELETED:** Serverobjektinstansen som motsvarar LWM2M-servern har tagits bort. Om det uppstår fel kan programmet hämta orsaken till felet genom att anropa **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Lokal Enhetshantering

Programmet kan komma åt objekten i LWM2M-klienten med hjälp av de lokala enhetshanteringsfunktionerna. Följande funktioner tillhandahålls:

- ***nx_lwm2m_client_object_read:*** Läsa resurser från en objektinstans.

- ***nx_lwm2m_client_object_discover:*** Hämta listan över resurser för en objektinstans.

- ***nx_lwm2m_client_object_write:*** Skriva resurser till en objektinstans

- ***nx_lwm2m_client_object_execute:*** Utför åtgärden Kör på en resurs för en objektinstans.

- ***nx_lwm2m_client_object_create:*** Skapa en ny objektinstans.

- ***nx_lwm2m_client_object_delete:*** Ta bort en befintlig objektinstans.

- ***nx_lwm2m_client_object_get_next:*** Hämta nästa objekt-ID som implementeras av LWM2M-klienten.

- ***nx_lwm2m_client_object_instance_get_next:*** Hämta nästa instans av ett objekt.

## <a name="resource-information"></a>Resursinformation

När du läser från och skriver till objekt representeras en resurs av NX_LWM2M_RESOURCE struktur. Den här strukturen innehåller ID:t för resursen/instansen och dess värde. Kodningen av värdet beror på dess typ och dess ursprung (program eller nätverk).

Strukturen NX_LWM2M_RESOURCE har följande definition:

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id:** ID:t för resursen eller instansen.
- **nx_lwm2m_resource_type:** Typen av värde, se nedan.
- **nx_lwm2m_resource_value:** Värdet för resursen beror på typen av värde.

Följande typ av värden definieras:

- **NX_LWM2M_RESOURCE_NONE:** Tom resurs.

- **NX_LWM2M_RESOURCE_STRING:** Ett null-avslutat UTF-8-strängvärde som lagras *i nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32:** Ett 32-bitars heltalsvärde som lagras *i nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64:** Ett 64-bitars heltalsvärde som lagras *i nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32:** Ett 32-bitars flyttalsvärde som lagras *i nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64:** Ett 64-bitars flyttalsvärde som lagras *i nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN:** Ett booleskt värde som lagras *i nx_lwm2m_resource_booleandata*.

- **NX_LWM2M_RESOURCE_OPAQUE:** Ett Täckande värde som definieras av *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK:** Ett objektlänkvärde som lagras *i nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV:** Ett TLV-kodat värde som definieras *av nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT:** Ett Plain-Text kodat värde som definieras av *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_MULTIPLE:** En flera resurser som definieras av *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* är en pekare till en matris **NX_LWM2M_RESOURCE** strukturer som innehåller information om varje resursinstans.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV:** En flera resurser som definieras av *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* är en pekare till en TLV-kodad buffert.

Bekvämlighetsfunktioner tillhandahålls för att hämta värdet och kontrollera dess typ. Programmet bör aldrig direkt komma *åt nx_lwm2m_resource_value-fältet* när du hämtar ett värde NX_LWM2M_RESOURCE en NX_LWM2M_RESOURCE struktur. Följande funktioner definieras:

- ***nx_lwm2m_resource_get_:*** Hämta ett värde med den angivna typen.
- ***nx_lwm2m_resource_multiple_get_:*** Hämta ett värde med den angivna typen från en flera resurser.

Makron **NX_LWM2M_RESOURCE_IS_MULTIPLE**(typ) kan användas för att kontrollera om en resurstyp är en flera resurser.

## <a name="object-implementation"></a>Objektimplementering

LWM2M-klienten implementerar de obligatoriska OMA LWM2M-objekten: Säkerhet (0), Server (1), Access Control (2) och Enhet (3). Andra enhetsspecifika objekt måste implementeras av programmet.

Två datastrukturer används för att definiera ett objekt: NX_LWM2M_OBJECT-strukturen definierar objektimplementering, inklusive objekt-ID och objektmetoder, och NX_LWM2M_OBJECT_INSTANCE-strukturen innehåller data för en objektinstans.

Strukturen NX_LWM2M_OBJECT har följande definition:

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next:** Nästa objekt i listan.
- **nx_lwm2m_object_id:** Objekt-ID:t.
- **nx_lwm2m_object_read:** Metoden "Läsa" nedan.
- **nx_lwm2m_object_discover:** Metoden "Identifiera", se nedan.
- **nx_lwm2m_object_write:** Metoden "Write", se nedan.
- **nx_lwm2m_object_execute:** Metoden "Execute" (Kör) nedan.
- **nx_lwm2m_object_create:** Metoden "Skapa", se nedan.
- **nx_lwm2m_object_delete:** Metoden "Delete" (Ta bort) nedan.
- **nx_lwm2m_object_instances:** Den NULL-avslutade listan över objektinstanser.

Strukturen NX_LWM2M_OBJECT_INSTANCE har följande definition:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next:** Nästa instans i listan.
- **nx_lwm2m_object_instance_id:** Objektinstansens ID.

Objektet måste implementera metoder som motsvarar de åtgärder som definieras av LWM2M Enhetshantering Interface: "Read", "Discover", "Write", "Execute", "Create" och "Delete". Metoderna "Skapa" och "Ta bort" kan anges till NULL om objektet inte stöder dynamiskt skapande av instanser.

### <a name="the-read-method"></a>Read-metoden

Metoden "Läsa" används för att läsa resursvärden från en objektinstans. Funktionen har följande definition:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Indataparametrarna definieras på följande sätt:

- **object_ptr**: Pekare till objektimplementering.

- **instance_ptr:** Pekare till objektinstansen.

- **num_values:** Antalet resurser som ska läsas.

- **values_ptr:** Pekare till en matris NX_LWM2M_RESOURCE innehåller DE RESURSER som ska läsas. När matrisen returneras fylls den med motsvarande typer och värden.

### <a name="the-discover-method"></a>Identifieringsmetoden

Metoden "Identifiera" används för att hämta listan över alla resurser som implementeras av ett objekt. Funktionen har följande definition:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Indataparametrarna definieras på följande sätt:

- **object_ptr**: Pekare till objektimplementering.

- **instance_ptr:** Pekare till objektinstansen.

- **num_resources_ptr:** När du matar in storleken på målbufferten matar du ut antalet element som skrivits till bufferten.

- **resources_ptr:** Pekare till målbufferten.

Resursinformationen returneras i en NX_LWM2M_RESOURCE_INFO struktur som definieras på följande sätt:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id:** Resursens ID.

- **nx_lwm2m_resource_info_flags**: Se nedan.

- **nx_lwm2m_resource_info_dim:** Dimensionen för flera resurser om flaggan NX_LWM2M_RESOURCE_INFO_MULTIPLE har angetts.

Fältet *nx_lwm2m_resource_flags* kan ha följande värden:

- 0: Enkel läsbar resurs.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE:** Flera resurser *nx_lwm2m_resource_info_dim* måste definieras.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE:** Körbar eller icke-läsbar resurs.

### <a name="the-write-method"></a>Metoden "Write"

Metoden "Write" används för att uppdatera eller ersätta resurser i en objektinstans. Funktionen har följande definition:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Indataparametrarna definieras på följande sätt:

- **object_ptr**: Pekare till objektimplementering.
- **instance_ptr:** Pekare till objektinstansen.
- **num_values:** Antalet resurser som ska skrivas.
- **values_ptr:** Pekare till resursvärdena.
- **write_op:** Typen av skrivåtgärder.

Följande skrivåtgärder kan anges för den *write_op* parametern :

- 0 &mdash; Partiell uppdatering: lägger till eller uppdaterar resurser som anges i det nya värdet och lämnar andra befintliga resurser oförändrade,

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Ersätt instans: ersätter objektinstansen med de nya angivna resursvärdena.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Ersätt resurs: ersätter Resurser med de nya angivna resursvärdena (används för att ersätta flera resurser).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Skapa instans: initierar den nyligen skapade objektinstansen med de angivna resursvärdena (anropas *från nx_lwm2m_object_create-metoden).*

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: anropas under Bootstrap-sekvensen.

### <a name="the-execute-method"></a>Execute-metoden

Metoden "Execute" implementerar körningen av en objektresurs. Funktionen har följande definition:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Indataparametrarna definieras på följande sätt:

- **object_ptr:** Pekare till objektimplementering
- **instance_ptr:** Pekare till objektinstansen.
- **resource_id:** Resurs-ID.
- **arguments_ptr:** Pekare till argumenten för körningsåtgärden. Kan vara NULL om *arguments_length* är noll.
- **arguments_length:** Längden på argumenten.

Funktionen måste returnera NX_LWM2M_NOT_FOUND resurs-ID:t inte finns eller NX_LWM2M_METHOD_NOT_ALLOWED om det inte stöder körning.

### <a name="the-create-method"></a>Create-metoden

Metoden "Skapa" implementerar skapandet av en ny objektinstans. Funktionen har följande definition:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Indataparametrarna definieras på följande sätt:

- **object_ptr**: Pekare till objektimplementering.
- **instance_id:** ID:t för den nya instansen.
- **num_values:** Antalet resurser som ska initieras.
- **values_ptr:** Pekare till resursvärdena.
- **instance_ptr:** Pekare till målpekaren för den skapade instansen.
- **bootstrap:** Sant om det anropas från bootstrap-sekvensen.

Objektet måste allokera och initiera en ny objektinstans med hjälp av den angivna listan över resursvärden.

### <a name="the-delete-method"></a>Delete-metoden

Metoden "Delete" implementerar borttagningen av en objektinstans. Funktionen har följande definition:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Indataparametrarna definieras på följande sätt:

- **object_ptr**: Pekare till objektimplementering.
- **instance_ptr:** Pekare till objektinstansen.

Om det lyckas måste objektet frigöra objektinstansdata och alla andra resurser som allokerats av instansen.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Lägga till objektimplementering och instanser till LWM2M-klienten

Programmet kan lägga till ny objektimplementering till LWM2M-klienten genom att anropa ***nx_lwm2m_client_object_add tjänsten.***

Om objektet inte stöder dynamiskt skapande av instanser, till exempel om det är ett enda objekt, ska *nx_lwm2m_object_instances-fältet* i objektstrukturen peka på listan över statiska instansstrukturer.

Om objektet stöder skapande av dynamisk *instans nx_lwm2m_object_instances* anges till NULL och ***nx_lwm2m_client_object_create-tjänsten*** ska användas i stället för att anropa metoden "Skapa" för objektet.

## <a name="example-of-lwm2m-client-application"></a>Exempel på LWM2M-klientprogram

Följande kod är ett exempel på ett enkelt LWM2M-klientprogram som implementerar en anpassad enhet som består av en temperatursensor och en lampa.

Enheten gör att en server kan läsa värdet för temperatursensorn och det booleska tillståndet för ljusväxeln och ställa in reglaget på på/av.

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
