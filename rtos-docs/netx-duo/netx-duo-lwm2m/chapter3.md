---
title: Kapitel 3 – Funktionell beskrivning av LWM2M-klienten
description: Det här kapitlet innehåller en funktionell beskrivning av LWM2M-klienten.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be6d9d854ce89140ce749fbeb0364678077337bf19ddc1055d286d0f624e8bd5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783466"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Kapitel 3 Funktionell beskrivning av LWM2M-klienten

> Det här kapitlet innehåller en funktionell beskrivning av LWM2M-klienten.

## <a name="lwm2m-client-initialization"></a>LWM2M-klient initiering

LWM2M-klienten initieras genom  att anropa nx_lwm2m_client_create tjänsten. LWM2M-klienten körs i en egen tråd och kan rapportera vissa händelser till programmet med hjälp av återanrop, eller genom att anropa metoder för anpassade objekt som implementeras av programmet.

Dessutom måste LWM2M-klientsessioner skapas genom att ***anropa nx_lwm2m_client_session_create*** för att möjliggöra kommunikation med en eller flera servrar. En session kan kommunicera med två olika typer av servrar: en Bootstrap-server eller en LWM2M-server (Enhetshantering).

### <a name="bootstrap-server-session"></a>Bootstrap-serversession

En kommunikationssession med en Bootstrap-server används för att etablera viktig information i LWM2M-klienten så att LWM2M-klienten kan utföra åtgärden "Registrera" med en eller flera LWM2M-servrar. Den här typen av server används i lägena Klientinitierad och Serverinitierad bootstrap.

Programmet kan starta en Bootstrap-session genom att anropa ***nx_lwm2m_client_session_bootstrap** _ eller _*_nx_lwm2m_client_session_bootstrap_dtls_*_, den måste ange serverns IP-adress och portnummer samt ett valfritt ID för säkerhetsobjektinstans. Funktionen _*_nx_lwm2m_client_session_bootstrap_*_ använder osäker kommunikation, medan _ nx_lwm2m_client_session_bootstrap_dtls **_upprättar_* en säker DTLS-anslutning med servern.

Om bootstrap-åtgärden lyckas bör Bootstrap-servern ha skapat säkerhetsobjektinstanser för Bootstrap- och LWM2M-servrarna och serverobjektinstanserna för LWM2M-servrarna. Programmet kan anropa ***nx_lwm2m_client_session_register_info_get*** hämta information om LWM2M-servrar och använda den här informationen för att upprätta en session med LWM2M-servrarna.

Bootstrap-data ska sparas i beständigt minne av programmet för att konfigurera LWM2M-klienten vid nästa omstart av enheten.

### <a name="lwm2m-server-session"></a>LWM2M-serversession

En kommunikationssession med en LWM2M-server används för registrering, Enhetshantering och tjänstaktivering.

Programmet kan registrera LWM2M-klienten till en server genom att anropa ***nx_lwm2m_client_session_register** _ eller _*_nx_lwm2m_client_session_register_dtls_*_, den måste ange serverns IP-adress och portnummer samt det korta server-ID som motsvarar en befintlig serverobjektinstans. Funktionen _*_nx_lwm2m_client_session_register_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_register_dtls_** upprättar en säker DTLS-anslutning med servern.

Programmet kan avregistrera LWM2M-klienten genom att anropa ***nx_lwm2m_client_session_deregister** _, och be klienten att skicka ett uppdateringsmeddelande genom att anropa _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Återanrop av sessionstillstånd

Programmet registrerar ett återanrop när en session skapas som anropas när sessionens tillstånd uppdateras. Återanropsfunktionen har NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK **följande** prototyp.

typedef VOID ( \* NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \* session_ptr,UINT state);

Följande tillstånd definieras.

| &nbsp;Sessionstillstånd | Description |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | Det initiala tillståndet efter att sessionen har skapats. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | Klienten väntar på att timern "Håll av" eller ServerInitierad bootstrap ska förfalla. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | Klienten har skickat ett meddelande om begäran till Bootstrap-servern (klientinitierad bootstrap). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | Klienten tar emot data från Bootstrap-servern. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | Bootstrap-servern har skickat meddelandet "Finished". |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | Bootstrap-sessionen misslyckades. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | Klienten har skickat ett registermeddelande till LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | Klienten är registrerad på LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | Klienten har skickat ett uppdateringsmeddelande till LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | Klienten har skickat ett avregistrerat meddelande till LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | Klienten avregistreras från LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | LWM2M-servern är inaktiverad. Ett register skickas efter att inaktiveringstimern har gått ut. |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | Registreringen eller uppdateringen av LWM2M-servern misslyckades. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | Serverobjektinstansen som motsvarar LWM2M-servern har tagits bort. |

Om det uppstår fel kan programmet hämta orsaken till felet genom att anropa ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Lokala Enhetshantering

Programmet kan komma åt objekten för LWM2M-klienten med hjälp av de lokala enhetshanteringsfunktionerna. Följande funktioner tillhandahålls.

| &nbsp;Funktionsnamn | Description |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Läsa resurser från en objektinstans. |
| ***nx_lwm2m_client_object_discover*** | Hämta listan över resurserna för en objektinstans.
| ***nx_lwm2m_client_object_write*** | Skriva resurser till en objektinstans. |
| ***nx_lwm2m_client_object_execute*** | Utför åtgärden Kör på en resurs i en objektinstans. |
| ***nx_lwm2m_client_object_create*** | Skapa en ny objektinstans. |
| ***nx_lwm2m_client_object_delete*** | Ta bort en befintlig objektinstans. |
| ***nx_lwm2m_client_object_next_get*** | Hämta nästa objekt-ID av LWM2M-klienten. |
| ***nx_lwm2m_client_object_instance_next_get*** | Hämta nästa instans av ett objekt. |

## <a name="resource-information"></a>Resursinformation

När du läser från och skriver till objekt representeras en resurs av NX_LWM2M_CLIENT_RESOURCE struktur. Den här strukturen innehåller ID:t för resursen/instansen och dess värde.

Följande funktioner tillhandahålls för att ange resursinformation och värde.

| &nbsp;Funktionsnamn | Description |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Ange resursinformation: resurs-ID och åtgärd: LÄSA, SKRIVA, KÖRBAR FIL. |
| ***nx_lwm2m_client_resource_string_set*** | Ange resursvärdet som sträng. |
| ***nx_lwm2m_client_resource_integer32_set*** | Ange resursvärdet som 32-bitars heltal. |
| ***nx_lwm2m_client_resource_integer64_set*** | Ange resursvärdet som 64-bitars heltal. |
| ***nx_lwm2m_client_resource_float32_set*** | Ange resursvärdet som 32-bitars flyttal. |
| ***nx_lwm2m_client_resource_float64_set*** | Ange resursvärdet som 64-bitars flyttal. |
| ***nx_lwm2m_client_resource_boolean_set*** | Ange resursvärdet som booleskt. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Ange resursvärdet som objektlänk. |
| ***nx_lwm2m_client_resource_opaque_set*** | Ange resursvärdet som täckande. |
| ***nx_lwm2m_client_resource_instance_set*** | Ange resursvärdet som instans för flera resurser. |
| ***nx_lwm2m_client_resource_dim_set*** | Ange resursdimensionen för flera resurser för identifiering. |

Följande funktioner tillhandahålls för att hämta resursinformation och värde.

| &nbsp;Funktionsnamn | Description |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Hämta resursinformation: resurs-ID och åtgärd: LÄSA, SKRIVA, KÖRBAR FIL. |
| ***nx_lwm2m_client_resource_string_get*** | Hämta värdet för en strängresurs. |
| ***nx_lwm2m_client_resource_integer32_get*** | Hämta värdet för en 32-bitars heltalsresurs. |
| ***nx_lwm2m_client_resource_integer64_get*** | Hämta värdet för en b4-bitars heltalsresurs. |
| ***nx_lwm2m_client_resource_float32_get*** | Hämta värdet för en 32-bitars flyttalsresurs. |
| ***nx_lwm2m_client_resource_float64_get*** | Hämta värdet för en 64-bitars flyttalsresurs. |
| ***nx_lwm2m_client_resource_boolean_get*** | Hämta värdet för en boolesk resurs. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Hämta värdet för en objektlänkresurs. |
| ***nx_lwm2m_client_resource_opaque_get*** | Hämta värdet för en täckande resurs. |
| ***nx_lwm2m_client_resource_instance_get*** | Hämta resursinstansen för flera resurser. |
| ***nx_lwm2m_client_resource_dim_get*** | Hämta resursdimensionen för flera resurser. |

## <a name="object-implementation"></a>Objektimplementering

LWM2M-klienten implementerar de obligatoriska OMA LWM2M-objekten: Säkerhet (0), Server (1), Access Control (2) och Enhet (3). Andra enhetsspecifika objekt måste implementeras av programmet.

Två datastrukturer används för att definiera ett objekt: NX_LWM2M_CLIENT_OBJECT-strukturen definierar objektimplementering, inklusive objekt-ID och objektmetoder, och NX_LWM2M_CLIENT_OBJECT_INSTANCE-strukturen innehåller data för en objektinstans.

Följande funktioner tillhandahålls.

| &nbsp;Funktionsnamn | Description |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Lägg till objektimplementering till LwM2M-klienten. |
| ***nx_lwm2m_client_object_remove*** | Ta bort objektimplementering från LwM2M-klienten. |
| ***nx_lwm2m_client_object_instance_add*** | Lägg till objektinstansen i -objektet. |
| ***nx_lwm2m_client_object_instance_remove*** | Ta bort objektinstansen från -objektet. |

Återanropsfunktionen för objektmetoden har signaturen som visas nedan.

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>Read-metoden

Metoden "Läsa" används för att läsa resursvärden från en objektinstans. Parametrarna definieras på följande sätt.

| Parameter | Beskrivning |
| --- | --- |
| **Drift** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Pekare till objektimplementering. |
| **instance_ptr** | Pekare till objektinstansen. |
| **resource** | Pekare till en **matris NX_LWM2M_CLIENT_RESOURCE** som innehåller DE RESURSER som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekare till antalet resurser som ska läsas. |
| **args_ptr** | Oanvänd parameter för läsning. |
| **args_length** | Oanvänd parameter för läsning. |

### <a name="the-discover-method"></a>Identifieringsmetoden

Metoden "Identifiera" används för att hämta listan över alla resurser som implementeras av ett objekt. Parametrarna definieras på följande sätt.

| Parameter | Beskrivning |
| --- | --- |
| **Drift** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Pekare till objektimplementering. |
| **instance_ptr** | Pekare till objektinstansen. |
| **resource** | Pekare till en matris med NX_LWM2M_CLIENT_RESOURCE. När matrisen returneras fylls den med motsvarande resursinformation. |
| **resource_count** | Pekare till antalet resurser som ska upptäckas. Vid retur måste den här parametern uppdateras som det sanna värdet. |
| **args_ptr** | Oanvänd parameter för identifiering. |
| **args_length** | Oanvänd parameter för identifiering. |

### <a name="the-write-method"></a>Metoden "Write"

Metoden "Write" används för att uppdatera eller ersätta resurser för en objektinstans. Parametrarna definieras på följande sätt.

| Parameter  | Beskrivning |
| --- | --- |
| **Drift** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Pekare till objektimplementering. |
| **instance_ptr** | Pekare till objektinstansen. |
| **resource** | Pekare till en **matris NX_LWM2M_CLIENT_RESOURCE** som innehåller DE RESURSER som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekare till antalet resurser som ska upptäckas. |
| **args_ptr** | Skriv flaggor. |
| **args_length** | Längden på argumenten. |

Följande skrivåtgärder kan anges för *flaggparametern.*

| Åtgärd | Åtgärd | Beskrivning |
| --- | ---| --- |
| 0 | Partiell uppdatering | Lägger till eller uppdaterar resurser som anges i det nya värdet och lämnar andra befintliga resurser oförändrade.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Ersätt instans | Ersätter objektinstansen med de nya angivna resursvärdena.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Ersätt resurs | Ersätter resurserna med de nya angivna resursvärdena (används för att ersätta flera resurser). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Skapa instans | Initierar den nyligen skapade objektinstansen med de angivna resursvärdena (anropas **_från nx_lwm2m_object_create-metoden)._** |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Bootstrap-skrivning | Anropas under Bootstrap-sekvensen. |

### <a name="the-execute-method"></a>Execute-metoden

Metoden "Execute" implementerar körningen av en objektresurs.

Indataparametrarna definieras på följande sätt.

| Parameter  | Beskrivning |
| --- | --- |
| **Drift** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Pekare till objektimplementering. |
| **instance_ptr** | Pekare till objektinstansen. |
| **resource** | Pekare till en **matris NX_LWM2M_CLIENT_RESOURCE** som innehåller DE RESURSER som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekare till antalet resurser som ska upptäckas. |
| **args_ptr** | Pekare till argumenten. |
| **args_length** | Längden på argumenten.  |

Funktionen måste returnera **NX_LWM2M_CLIENT_NOT_FOUND** resurs-ID:t inte finns, eller **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** om det inte stöder körning.

### <a name="the-create-method"></a>Metoden "Skapa"

Metoden "Skapa" implementerar skapandet av en ny objektinstans.

Indataparametrarna definieras på följande sätt.

| Parameter  | Beskrivning |
| --- | --- |
| **Drift** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Pekare till objektimplementering. |
| **instance_ptr** | Oanvänd parameter. |
| **resource** | Pekare till en **matris NX_LWM2M_CLIENT_RESOURCE** som innehåller DE RESURSER som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekare till antalet resurser som ska upptäckas. |
| **args_ptr** | Objektinstans-ID. |
| **args_length** | Längden på argumenten. |

### <a name="the-delete-method"></a>Delete-metoden

Metoden "Ta bort" implementerar borttagningen av en objektinstans. Indataparametrarna definieras på följande sätt.

| Parameter  | Beskrivning |
| --- | --- |
| **Drift** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Pekare till objektimplementering. |
| **instance_ptr** | Pekare till objektinstansen. |
| **resource** | Oanvänd parameter. |
| **resource_count** | Oanvänd parameter. |
| **args_ptr** | Oanvänd parameter. |
| **args_length** | Oanvänd parameter. |

Om det lyckas måste objektet frigöra objektinstansdata och alla andra resurser som allokerats av instansen.

## <a name="example-of-lwm2m-client-application"></a>Exempel på LWM2M-klientprogram

Följande kod är ett exempel på ett enkelt LWM2M-klientprogram som implementerar en anpassad enhet som består av en temperatursensor och en lampa.

Enheten gör att en server kan läsa värdet för temperatursensorn och det booleska tillståndet för ljusväxeln och ställa in reglaget på på/av.

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```