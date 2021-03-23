---
title: Kapitel 3 – funktions Beskrivning av LWM2M-klienten
description: Det här kapitlet innehåller en funktions Beskrivning av LWM2M-klienten.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825938"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Kapitel 3 funktions Beskrivning av LWM2M-klienten

> Det här kapitlet innehåller en funktions Beskrivning av LWM2M-klienten.

## <a name="lwm2m-client-initialization"></a>LWM2M klient initiering

LWM2M-klienten initieras genom att anropa ***nx_lwm2m_client_creates*** tjänsten. LWM2M-klienten körs i sin egen tråd och kan rapportera vissa händelser till programmet genom att använda återanrop eller genom att anropa metoder för de anpassade objekt som implementeras av programmet.

Dessutom måste LWM2M-klientsessioner skapas genom att anropa ***nx_lwm2m_client_session_create*** för att aktivera kommunikation med en eller flera servrar. En session kan kommunicera med två olika typer av servrar: en Start Server eller en LWM2M-Server (enhets hantering).

### <a name="bootstrap-server-session"></a>Bootstrap-Server-session

En kommunikations-session med en Start Server används för att tillhandahålla viktig information till LWM2M-klienten så att LWM2M-klienten kan utföra åtgärden "Registrera" med en eller flera LWM2M-servrar. Den här typen av Server används vid start läge för klienten som initierats och initierats av servern.

Programmet kan starta en bootstrap-session genom att anropa ***nx_lwm2m_client_session_bootstrap** _ eller _*_nx_lwm2m_client_session_bootstrap_dtls_*_, den måste ange IP-adressen och port numret för-servern och ett valfritt säkerhets objekts instans-ID. Funktionen _*_nx_lwm2m_client_session_bootstrap_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_bootstrap_dtls_** upprättar en säker DTLS-anslutning till servern.

Om bootstrap-åtgärden lyckas ska start servern ha skapat säkerhets objekts instanser för start-och LWM2M-servrarna och Server objekt instanser för LWM2M-servrarna. Programmet kan anropa ***nx_lwm2m_client_session_register_info_get*** för att hämta information om Lwm2m-servrar och använda den här informationen för att upprätta en session med Lwm2m-servrarna.

Bootstrap-data ska sparas till beständigt minne av programmet för att konfigurera LWM2M-klienten vid nästa omstart av enheten.

### <a name="lwm2m-server-session"></a>LWM2M Server-session

En kommunikations-session med en LWM2M-Server används för registrering, enhets hantering och tjänst aktivering.

Programmet kan registrera LWM2M-klienten på en server genom att anropa ***nx_lwm2m_client_session_register** _ eller _*_nx_lwm2m_client_session_register_dtls_*_, den måste ange IP-adressen och port numret för-servern och det korta Server-ID som motsvarar en befintlig server objekt instans. Funktionen _*_nx_lwm2m_client_session_register_*_ använder osäker kommunikation, medan _ *_nx_lwm2m_client_session_register_dtls_** upprättar en säker DTLS-anslutning till servern.

Programmet kan avregistrera LWM2M-klienten genom att anropa ***nx_lwm2m_client_session_deregister** _ och be klienten att skicka ett uppdaterings meddelande genom att anropa _ *_nx_lwm2m_client_session_update_* *.

### <a name="session-state-callback"></a>Motanrop för sessionstillstånd

Programmet registrerar ett återanrop vid skapandet av en session som anropas när sessionens status uppdateras. motringningsfunktionen **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** har följande prototyp.

TypeDef VOID ( \* NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK) (NX_LWM2M_CLIENT_SESSION \* SESSION_PTR, uint-tillstånd);

Följande tillstånd definieras.

| Sessionstillstånd &nbsp; | Beskrivning |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | Initialt tillstånd efter att sessionen skapats. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | Klienten väntar på att start av timer eller initierad Server ska startas. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | Klienten har skickat ett "Request"-meddelande till bootstrap-servern (klienten initierade start). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | Klienten tar emot data från start servern. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | Start servern har skickat ett meddelande om att det har skickats. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | Det gick inte att starta bootstrap-sessionen. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | Klienten har skickat ett "Registrera"-meddelande till LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | Klienten är registrerad på LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | Klienten har skickat ett uppdaterings meddelande till LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | Klienten har skickat meddelandet "avregistrera" till LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | Klienten är avregistrerad från LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | LWM2M-servern är inaktive rad. En "Registrera" skickas när den inaktiverade timern upphör att gälla. |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | Det gick inte att utföra registreringen eller uppdateringen på LWM2M-servern. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | Server objekts instansen som motsvarar LWM2M-servern har tagits bort. |

Om ett fel uppstår kan programmet Hämta orsaken till felet genom att anropa ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Hantering av lokala enheter

Programmet kan komma åt objekten i LWM2M-klienten med hjälp av funktionerna för lokal enhets hantering. Följande funktioner finns.

| Funktions &nbsp; namn | Beskrivning |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Läsa resurser från en objekt instans. |
| ***nx_lwm2m_client_object_discover*** | Hämta listan över resurser för en objekt instans.
| ***nx_lwm2m_client_object_write*** | Skriv resurser till en objekt instans. |
| ***nx_lwm2m_client_object_execute*** | Utför åtgärden kör på en resurs av en objekt instans. |
| ***nx_lwm2m_client_object_create*** | Skapa en ny objekt instans. |
| ***nx_lwm2m_client_object_delete*** | Ta bort en befintlig objekt instans. |
| ***nx_lwm2m_client_object_next_get*** | Hämta nästa objekt-ID av LWM2M-klienten. |
| ***nx_lwm2m_client_object_instance_next_get*** | Hämta nästa instans av ett objekt. |

## <a name="resource-information"></a>Resursinformation

Vid läsning från och skrivning till objekt representeras en resurs av NX_LWM2M_CLIENT_RESOURCE-strukturen. Den här strukturen innehåller ID: t för resursen/instansen och dess värde.

Följande funktioner finns för att ange resursinformation och-värde.

| Funktions &nbsp; namn | Beskrivning |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Ange resursinformation: resurs-ID och åtgärd: läsa, skriva, KÖRBAR fil. |
| ***nx_lwm2m_client_resource_string_set*** | Ange resurs värde som sträng. |
| ***nx_lwm2m_client_resource_integer32_set*** | Ange resurs värde som 32-bitars heltal. |
| ***nx_lwm2m_client_resource_integer64_set*** | Ange resurs värde som 64-bitars heltal. |
| ***nx_lwm2m_client_resource_float32_set*** | Ange resurs värde som 32-bitars flyttal. |
| ***nx_lwm2m_client_resource_float64_set*** | Ange resurs värde som 64-bitars flyttal. |
| ***nx_lwm2m_client_resource_boolean_set*** | Ange resurs värde som Boolean. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Ange resurs värde som objekt länk. |
| ***nx_lwm2m_client_resource_opaque_set*** | Ange resurs värde som ogenomskinligt. |
| ***nx_lwm2m_client_resource_instance_set*** | Ange resurs värde som instansen för flera resurser. |
| ***nx_lwm2m_client_resource_dim_set*** | Ange resurs dimensionen för flera resurser för identifiering. |

Följande funktioner är tillgängliga för att hämta resurs information och-värde.

| Funktions &nbsp; namn | Beskrivning |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Hämta resurs information: resurs-ID och åtgärd: läsa, skriva, KÖRBAR fil. |
| ***nx_lwm2m_client_resource_string_get*** | Hämta värdet för en sträng resurs. |
| ***nx_lwm2m_client_resource_integer32_get*** | Hämta värdet för en 32-bitars heltals resurs. |
| ***nx_lwm2m_client_resource_integer64_get*** | Hämta värdet för en B4-bitars heltals resurs. |
| ***nx_lwm2m_client_resource_float32_get*** | Hämta värdet för en 32-bitars float-resurs. |
| ***nx_lwm2m_client_resource_float64_get*** | Hämta värdet för en 64-bitars float-resurs. |
| ***nx_lwm2m_client_resource_boolean_get*** | Hämta värdet för en boolesk resurs. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Hämta värdet för en objekt länk resurs. |
| ***nx_lwm2m_client_resource_opaque_get*** | Hämta värdet för en ogenomskinlig resurs. |
| ***nx_lwm2m_client_resource_instance_get*** | Hämta resurs instansen för flera resurser. |
| ***nx_lwm2m_client_resource_dim_get*** | Hämta resurs dimensionen för flera resurser. |

## <a name="object-implementation"></a>Objekt implementering

LWM2M-klienten implementerar de obligatoriska OMA LWM2M-objekten: säkerhet (0), Server (1), Access Control (2) och enhet (3). Andra enhets specifika objekt måste implementeras av programmet.

Två data strukturer används för att definiera ett objekt: NX_LWM2M_CLIENT_OBJECTs strukturen definierar objekt implementeringen, inklusive objekt-ID och objekt metoder, och NX_LWM2M_CLIENT_OBJECT_INSTANCE strukturen innehåller data för en objekt instans.

Följande funktioner finns.

| Funktions &nbsp; namn | Beskrivning |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Lägg till objekt implementering i LwM2M-klienten. |
| ***nx_lwm2m_client_object_remove*** | Ta bort objekt implementering från LwM2M-klienten. |
| ***nx_lwm2m_client_object_instance_add*** | Lägg till objekt instans i objektet. |
| ***nx_lwm2m_client_object_instance_remove*** | Ta bort objekt instansen från objektet. |

Funktionen callback för objekt metod innehåller en signatur som visas nedan.

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

### <a name="the-read-method"></a>Metoden Read

Metoden Read används för att läsa resurs värden från en objekt instans. Parametrarna definieras enligt följande.

| Parameter | Beskrivning |
| --- | --- |
| **reparation** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Pekare till objekt implementeringen. |
| **instance_ptr** | Pekare till objekt instansen. |
| **klusterresursen** | Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekar på antalet resurser som ska läsas. |
| **args_ptr** | Oanvänd parameter för läsning. |
| **args_length** | Oanvänd parameter för läsning. |

### <a name="the-discover-method"></a>Identifiera-metoden

Identifiera-metoden används för att hämta en lista över alla resurser som implementerats av ett objekt. Parametrarna definieras enligt följande.

| Parameter | Beskrivning |
| --- | --- |
| **reparation** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Pekare till objekt implementeringen. |
| **instance_ptr** | Pekare till objekt instansen. |
| **klusterresursen** | Pekare till en matris med NX_LWM2M_CLIENT_RESOURCE. Vid retur fylls matrisen med motsvarande resursinformation. |
| **resource_count** | Pekar på antalet resurser som ska identifieras. Vid retur måste den här parametern uppdateras som det sanna värdet. |
| **args_ptr** | Oanvänd parameter för identifiering. |
| **args_length** | Oanvänd parameter för identifiering. |

### <a name="the-write-method"></a>Write-metoden

Metoden Write används för att uppdatera eller ersätta resurser för en objekt instans. Parametrarna definieras enligt följande.

| Parameter  | Beskrivning |
| --- | --- |
| **reparation** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Pekare till objekt implementeringen. |
| **instance_ptr** | Pekare till objekt instansen. |
| **klusterresursen** | Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekar på antalet resurser som ska identifieras. |
| **args_ptr** | Skriv flaggor. |
| **args_length** | Argumentens längd. |

Följande Skriv åtgärder kan anges för *flagg* parametern.

| Åtgärd | Åtgärd | Beskrivning |
| --- | ---| --- |
| 0 | Partiell uppdatering | Lägger till eller uppdaterar resurser som finns i det nya värdet och lämnar andra befintliga resurser oförändrade.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Ersätt instans | Ersätter objekt instansen med de nya angivna resurs värdena.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Ersätt resurs | Ersätter resurserna med de nya angivna resurs värdena (används för att ersätta flera resurser). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Skapa instans | Initierar den nyligen skapade objekt instansen med de tillhandahållna resurs värdena (anropas från metoden **_nx_lwm2m_object_create_** ). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Bootstrap-skrivning | Anropas under bootstrap-sekvens. |

### <a name="the-execute-method"></a>Metoden Execute

Metoden Execute implementerar körningen av en objekt resurs.

Indataparametrarna definieras enligt följande.

| Parameter  | Beskrivning |
| --- | --- |
| **reparation** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Pekare till objekt implementeringen. |
| **instance_ptr** | Pekare till objekt instansen. |
| **klusterresursen** | Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekar på antalet resurser som ska identifieras. |
| **args_ptr** | Pekar mot argumenten. |
| **args_length** | Argumentens längd.  |

Funktionen måste returnera **NX_LWM2M_CLIENT_NOT_FOUND** om resurs-ID: t inte finns eller **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** om det inte stöder körning.

### <a name="the-create-method"></a>Metoden Create

Metoden Create implementerar skapandet av en ny objekt instans.

Indataparametrarna definieras enligt följande.

| Parameter  | Beskrivning |
| --- | --- |
| **reparation** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Pekare till objekt implementeringen. |
| **instance_ptr** | Oanvänd parameter. |
| **klusterresursen** | Pekar till en matris med **NX_LWM2M_CLIENT_RESOURCE** som innehåller ID: n för de resurser som ska läsas. Vid retur fylls matrisen med motsvarande typer och värden. |
| **resource_count** | Pekar på antalet resurser som ska identifieras. |
| **args_ptr** | Objekt instans-ID. |
| **args_length** | Argumentens längd. |

### <a name="the-delete-method"></a>Metoden Delete

Metoden Delete implementerar borttagningen av en objekt instans, indataparametrarna definieras enligt följande.

| Parameter  | Beskrivning |
| --- | --- |
| **reparation** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Pekare till objekt implementeringen. |
| **instance_ptr** | Pekare till objekt instansen. |
| **klusterresursen** | Oanvänd parameter. |
| **resource_count** | Oanvänd parameter. |
| **args_ptr** | Oanvänd parameter. |
| **args_length** | Oanvänd parameter. |

Vid lyckad måste objektet frisläppa objekt instans data och andra resurser som allokerats av instansen.

## <a name="example-of-lwm2m-client-application"></a>Exempel på LWM2M-klientprogram

Följande kod är ett exempel på ett enkelt LWM2M klient program som implementerar en anpassad enhet som består av en temperatur sensor och en ljus växel.

Enheten gör att en server kan läsa värdet för temperatur sensorn och den booleska statusen för ljus växeln och för att ställa in ljus växeln på/av.

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