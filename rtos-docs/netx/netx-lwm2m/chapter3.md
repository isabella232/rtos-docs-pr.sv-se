---
title: Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-LWM2M
description: Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX-LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826679"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Kapitel 3 – funktionell beskrivning av Azure återställnings tider NetX-LWM2M

Det här kapitlet innehåller en funktions Beskrivning av Azure återställnings tider NetX-LWM2M.

## <a name="lwm2m-client-initialization"></a>LWM2M klient initiering

LWM2M-klienten initieras genom att anropa ***nx_lwm2m_client_creates*** tjänsten. LWM2M-klienten körs i sin egen tråd och kan rapportera vissa händelser till programmet genom att använda återanrop eller genom att anropa metoder för de anpassade objekt som implementeras av programmet.

Dessutom måste LWM2M-klientsessioner skapas genom att anropa ***nx_lwm2m_client_session_create*** för att aktivera kommunikation med en eller flera servrar. En session kan kommunicera med två olika typer av servrar: en Start Server eller en LWM2M-Server (enhets hantering).

### <a name="bootstrap-server-session"></a>Bootstrap-Server-session

En kommunikations-session med en Start Server används för att tillhandahålla viktig information till LWM2M-klienten så att LWM2M-klienten kan utföra åtgärden "Registrera" med en eller flera LWM2M-servrar. Den här typen av Server används vid start läge för klienten som initierats och initierats av servern.

Programmet kan starta en bootstrap-session genom att anropa ***nx_lwm2m_client_session_bootstrap** _ eller _*_nx_lwm2m_client_session_bootstrap_dtls_*_, den måste ange IP-adressen och port numret för-servern och ett valfritt säkerhets objekts instans-ID. Funktionen _*_nx_lwm2m_client_session_bootstrap_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_bootstrap_dtls_** upprättar en säker DTLS-anslutning till servern.

Om bootstrap-åtgärden lyckas ska start servern ha skapat säkerhets objekts instanser för start-och LWM2M-servrarna och Server objekt instanser för LWM2M-servrarna. Programmet måste använda den här informationen för att upprätta en session med LWM2M-servrar.

Bootstrap-data ska sparas till beständigt minne av programmet för att konfigurera LWM2M-klienten vid nästa omstart av enheten.

### <a name="lwm2m-server-session"></a>LWM2M Server-session

En kommunikations-session med en LWM2M-Server används för registrering, enhets hantering och tjänst aktivering.

Programmet kan registrera LWM2M-klienten på en server genom att anropa ***nx_lwm2m_client_session_register** _ eller _*_nx_lwm2m_client_session_register_dtls_*_, den måste ange IP-adressen och port numret för-servern och det korta Server-ID som motsvarar en befintlig server objekt instans. Funktionen _*_nx_lwm2m_client_session_register_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_register_dtls_** upprättar en säker DTLS-anslutning till servern.

Programmet kan avregistrera LWM2M-klienten genom att anropa ***nx_lwm2m_client_session_deregister** _ och be klienten att skicka ett uppdaterings meddelande genom att anropa _ *_nx_lwm2m_client_session_update_* *.

### <a name="session-state-callback"></a>Motanrop för sessionstillstånd

Programmet registrerar ett återanrop vid skapandet av en session som anropas när sessionens tillstånd uppdateras, motringningsfunktionen NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK har följande prototyp:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

Följande tillstånd definieras:

- **NX_LWM2M_CLIENT_SESSION_INIT**: initialt tillstånd efter att sessionen skapats.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: klienten väntar på att den väntande vänte tiden eller servern har initierats.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: klienten har skickat ett "Request"-meddelande till bootstrap-servern (klienten initierade start).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: klienten tar emot data från start servern.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: bootstrap-servern har skickat ett meddelande om att det har skickats.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: bootstrap-sessionen misslyckades.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: klienten har skickat ett "Registrera"-meddelande till LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: klienten är registrerad på LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: klienten har skickat ett uppdaterings meddelande till LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: klienten har skickat meddelandet "avregistrera" till LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: klienten AVREGISTRERAS från LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: LWM2M-servern är inaktive rad. En "Registrera" skickas när den inaktiverade timern upphör att gälla.

- **NX_LWM2M_CLIENT_SESSION_ERROR**: det gick inte att utföra registreringen eller uppdateringen på LWM2M-servern.

- **NX_LWM2M_CLIENT_SESSION_DELETED**: den server objekt instans som motsvarar LWM2M-servern har tagits bort. Om ett fel uppstår kan programmet Hämta orsaken till felet genom att anropa **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Hantering av lokala enheter

Programmet kan komma åt objekten i LWM2M-klienten med hjälp av funktionerna för lokal enhets hantering. Följande funktioner är tillgängliga:

- ***nx_lwm2m_client_object_read***: läsa resurser från en objekt instans.

- ***nx_lwm2m_client_object_discover***: Hämta en lista över resurser för en objekt instans.

- ***nx_lwm2m_client_object_write***: skriva resurser till en objekt instans

- ***nx_lwm2m_client_object_execute***: utför åtgärden kör på en resurs av en objekt instans.

- ***nx_lwm2m_client_object_create***: skapa en ny objekt instans.

- ***nx_lwm2m_client_object_delete***: ta bort en befintlig objekt instans.

- ***nx_lwm2m_client_object_get_next***: Hämta nästa objekt-ID som implementeras av Lwm2m-klienten.

- ***nx_lwm2m_client_object_instance_get_next***: Hämta nästa instans av ett objekt.

## <a name="resource-information"></a>Resursinformation

Vid läsning från och skrivning till objekt representeras en resurs av NX_LWM2M_RESOURCE-strukturen. Den här strukturen innehåller ID: t för resursen/instansen och dess värde. Kodningen för värdet beror på dess typ och ursprung (program eller nätverk).

NX_LWM2M_RESOURCEs strukturen har följande definition:

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

- **nx_lwm2m_resource_id**: ID för resursen eller instansen.
- **nx_lwm2m_resource_type**: värdets typ, se nedan.
- **nx_lwm2m_resource_value**: resursens värde beror på typen av värde.

Följande typ av värden definieras:

- **NX_LWM2M_RESOURCE_NONE**: Tom resurs.

- **NX_LWM2M_RESOURCE_STRING**: ett null-avslutat UTF-8-sträng värde lagrat i *nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32**: ett 32-bitars heltals värde lagrat i *nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64**: ett 64-bitars heltals värde lagrat i *nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32**: ett 32-bitars flytt ALS värde som lagras i *nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64**: ett 64-bitars flytt ALS värde som lagras i *nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN**: ett booleskt värde lagrat i *nx_lwm2m_resource_booleandata*.

- **NX_LWM2M_RESOURCE_OPAQUE**: ett ogenomskinligt värde som definieras av *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK**: ett objekt länk värde lagrat i *nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV**: ett TLV-kodat värde som definieras av *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT**: ett Plain-Text-kodat värde som definieras av *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_MULTIPLE**: en flera resurs som definieras av *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* är en pekare till en matris med **NX_LWM2M_RESOURCE** strukturer som innehåller information om varje resurs instans.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: en flera resurs som definieras av *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* är en pekare till en TLV-kodad buffert.

Bekvämlighets funktioner används för att hämta värdet och kontrol lera dess typ. programmet ska aldrig direkt komma åt *nx_lwm2m_resource_value* fältet när du hämtar ett värde från en NX_LWM2M_RESOURCE-struktur. Följande funktioner definieras:

- ***nx_lwm2m_resource_get_***: Hämta ett värde med den aktuella typen.
- ***nx_lwm2m_resource_multiple_get_***: Hämta ett värde med en specifik typ från en flera resurser.

Makro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(typ) kan användas för att kontrol lera om en resurs typ är en flera resurser.

## <a name="object-implementation"></a>Objekt implementering

LWM2M-klienten implementerar de obligatoriska OMA LWM2M-objekten: säkerhet (0), Server (1), Access Control (2) och enhet (3). Andra enhets specifika objekt måste implementeras av programmet.

Två data strukturer används för att definiera ett objekt: NX_LWM2M_OBJECTs strukturen definierar objekt implementeringen, inklusive objekt-ID och objekt metoder, och NX_LWM2M_OBJECT_INSTANCE strukturen innehåller data för en objekt instans.

NX_LWM2M_OBJECTs strukturen har följande definition:

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

- **nx_lwm2m_object_next**: Nästa objekt i listan.
- **nx_lwm2m_object_id**: objekt-ID.
- **nx_lwm2m_object_read**: metoden Read, se nedan.
- **nx_lwm2m_object_discover**: ' Discover '-metoden finns nedan.
- **nx_lwm2m_object_write**: metoden Write, se nedan.
- **nx_lwm2m_object_execute**: metoden Execute, se nedan.
- **nx_lwm2m_object_create**: metoden ' create ', se nedan.
- **nx_lwm2m_object_delete**: metoden Delete, se nedan.
- **nx_lwm2m_object_instances**: listan över null-terminerade objekt instanser.

NX_LWM2M_OBJECT_INSTANCEs strukturen har följande definition:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next**: nästa instans i listan.
- **nx_lwm2m_object_instance_id**: ID för objekt instans.

Objektet måste implementera de metoder som motsvarar de åtgärder som definierats av LWM2M enhets hanterings gränssnitt: Read, Discovery, Write, EXECUTE, Create och Delete. Metoderna Create och Delete kan anges till NULL om objektet inte stöder dynamisk generering av instanser.

### <a name="the-read-method"></a>Metoden Read

Metoden Read används för att läsa resurs värden från en objekt instans, funktionen har följande definition:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Indataparametrarna definieras enligt följande:

- **object_ptr**: pekar mot objekt implementeringen.

- **instance_ptr**: pekar mot objekt instansen.

- **num_values**: antalet resurser som ska läsas.

- **values_ptr**: pekar mot en matris med NX_LWM2M_RESOURCE som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden.

### <a name="the-discover-method"></a>Identifiera-metoden

Identifiera-metoden används för att hämta en lista över alla resurser som implementerats av ett objekt, funktionen har följande definition:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Indataparametrarna definieras enligt följande:

- **object_ptr**: pekar mot objekt implementeringen.

- **instance_ptr**: pekar mot objekt instansen.

- **num_resources_ptr**: om du vill ange storleken på måldomänkontrollanten vid utdata anger du antalet element som skrivs till bufferten.

- **resources_ptr**: pekar mot målcachen.

Resursinformationen returneras i en NX_LWM2M_RESOURCE_INFO-struktur som definieras enligt följande:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id**: resursens ID.

- **nx_lwm2m_resource_info_flags**: se nedan.

- **nx_lwm2m_resource_info_dim**: dimensionen för flera resurser om flaggan NX_LWM2M_RESOURCE_INFO_MULTIPLE har angetts.

Fältet *nx_lwm2m_resource_flags* kan ha följande värden:

- 0: en läsbar resurs.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE**: flera resurser måste *nx_lwm2m_resource_info_dim* definieras.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: körbar eller icke läsbar resurs.

### <a name="the-write-method"></a>Write-metoden

Metoden Write används för att uppdatera eller ersätta resurser för en objekt instans, funktionen har följande definition:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Indataparametrarna definieras enligt följande:

- **object_ptr**: pekar mot objekt implementeringen.
- **instance_ptr**: pekar mot objekt instansen.
- **num_values**: antalet resurser som ska skrivas.
- **values_ptr**: pekar mot resurs värden.
- **write_op**: typ av Skriv åtgärder.

Följande Skriv åtgärder kan anges för parametern *write_op* :

- 0 &mdash; del uppdatering: lägger till eller uppdaterar resurser som finns i det nya värdet och låter andra befintliga resurser ändras,

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Ersätt instans: ersätter objekt instansen med de nya angivna resurs värdena.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Ersätt resurs: ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Skapa instans: initierar den nyligen skapade objekt instansen med de tillhandahållna resurs värdena (anropades från metoden *nx_lwm2m_object_create* ).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap-skrivning: anropas under bootstrap-sekvens.

### <a name="the-execute-method"></a>Metoden Execute

Metoden Execute implementerar körningen av en objekt resurs, funktionen har följande definition:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Indataparametrarna definieras enligt följande:

- **object_ptr**: pekar mot objekt implementeringen
- **instance_ptr**: pekar mot objekt instansen.
- **resource_id**: resurs-ID.
- **arguments_ptr**: pekar mot argumenten för körnings åtgärden. Kan vara NULL om *arguments_length* är noll.
- **arguments_length**: argumentens längd.

Funktionen måste returnera NX_LWM2M_NOT_FOUND om resurs-ID: t inte finns eller NX_LWM2M_METHOD_NOT_ALLOWED om det inte stöder körning.

### <a name="the-create-method"></a>Metoden Create

Metoden Create implementerar skapandet av en ny objekt instans, funktionen har följande definition:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Indataparametrarna definieras enligt följande:

- **object_ptr**: pekar mot objekt implementeringen.
- **instance_id**: ID för den nya instansen.
- **num_values**: antalet resurser som ska initieras.
- **values_ptr**: pekar mot resurs värden.
- **instance_ptr**: pekar mot destinations pekaren för den skapade instansen.
- **bootstrap**: true om den anropas från bootstrap-sekvens.

Objektet måste allokera och initialiaze en ny objekt instans med hjälp av den angivna listan med resurs värden.

### <a name="the-delete-method"></a>Metoden Delete

Metoden Delete implementerar borttagningen av en objekt instans, funktionen har följande definition:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Indataparametrarna definieras enligt följande:

- **object_ptr**: pekar mot objekt implementeringen.
- **instance_ptr**: pekar mot objekt instansen.

Vid lyckad måste objektet frisläppa objekt instans data och andra resurser som allokerats av instansen.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Lägga till objekt implementeringar och instanser i LWM2M-klienten

Programmet kan lägga till ny objekt implementering i LWM2M-klienten genom att anropa tjänsten ***nx_lwm2m_client_object_add*** .

Om objektet inte stöder dynamisk skapande av instanser, till exempel om det är ett enda instans objekt, ska *nx_lwm2m_object_instances* fältet i objekt strukturen peka på listan över de statiska instans strukturerna.

Om objektet har stöd för att skapa dynamiska instanser måste *nx_lwm2m_object_instances* vara inställt på NULL och ***nx_lwm2m_client_object_creates*** tjänsten ska användas i stället för att anropa "Create"-metoden för objektet.

## <a name="example-of-lwm2m-client-application"></a>Exempel på LWM2M-klientprogram

Följande kod är ett exempel på ett enkelt LWM2M klient program som implementerar en anpassad enhet som består av en temperatur sensor och en ljus växel.

Enheten gör att en server kan läsa värdet för temperatur sensorn och den booleska statusen för ljus växeln och för att ställa in ljus växeln på/av.

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
