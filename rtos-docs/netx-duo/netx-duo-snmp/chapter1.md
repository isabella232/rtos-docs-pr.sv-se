---
title: Kapitel 1 – Introduktion till Azure RTOS NetX Duo SNMP
description: NetX Duo SNMP-implementeringen är en SNMP-agent. En agent ansvarar för att svara på SNMP-hanterarens kommandon och skicka händelsedrivna traps.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bf18efacc5ff7773e038a5140fc886e978ebd1ca59cc9b861139b3ce2d9ada6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797880"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>Kapitel 1 – Introduktion till Azure RTOS NetX Duo SNMP

SNMP (Simple Network Management Protocol) är ett protokoll som utformats för att hantera enheter på Internet. SNMP är ett protokoll som använder de anslutningslösa UDP-tjänsterna (User Datagram Protocol) för att utföra sin hanteringsfunktion. Den Azure RTOS NetX Duo SNMP-implementeringen är en SNMP-agent. En agent ansvarar för att svara på SNMP-hanterarens kommandon och skicka händelsedrivna traps. 

NetX Duo SNMP stöder både IPv4- och IPv6-kommunikation med SNMP Managers. NetX SNMP-program bör kompileras och köras i NetX Duo SNMP. Utvecklaren uppmanas dock att porta befintliga SNMP-program till att använda motsvarande "duo"-tjänster. När du till exempel skickar SNMP-trapmeddelanden bör följande "duo"-tjänster ersätta deras NetX-motsvarighet:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

Mer information finns i **Beskrivning av SNMP Agent Services någon** annanstans i den här användarhandboken.

## <a name="netx-duo-snmp-agent-requirements"></a>Krav för NetX Duo SNMP-agent

NetX Duo SNMP-paketet kräver att en IP-instans redan har skapats. Dessutom måste UDP vara aktiverat på samma IP-instans.

NetX Duo SNMP-agenten har flera ytterligare krav. För det första krävs åtkomst till port 161 för hantering av alla SNMP-hanterarbegäranden. Det kräver också åtkomst till port 162 för att skicka trap-meddelanden till chefen.

Om du vill använda NetX Duo SNMP Agent med över IPv6 och hämta IPv6-objekt måste IPv6 vara aktiverat i NetX Duo. Mer information ***om hur du aktiverar IP-instansen för*** IPv6-tjänster finns i användarhandboken för NetX Duo.

## <a name="netx-duo-snmp-constraints"></a>Begränsningar för NetX Duo SNMP

NetX Duo SNMP-protokollet implementerar SNMP version 1, 2 och 3. SNMPv3-implementeringen stöder MD5- och SHA-autentisering och DES-kryptering. Den här versionen av NetX Duo SNMP-agenten har följande begränsningar:

1. En SNMP-agent per NetX IP-instans
2. Inget stöd för RMON
3. SNMP v3 Inform-meddelanden stöds inte
4. OPAQUE- och NSAP-datatyper stöds inte
5. IPv6-adresser definieras som oktettsträngar och formatkontrollen lämnas till programmet.

## <a name="snmp-object-names"></a>SNMP-objektnamn

SNMP-protokollet är utformat för att hantera enheter på Internet. För att åstadkomma detta har varje SNMP-hanterad enhet en uppsättning objekt som definieras av SMI (Structure of Management Information) enligt definitionen i RFC 1155. Strukturen är en hierarkisk trädtyp av struktur som ser ut så här:

![Diagram över strukturen för hanteringsinformation.](media/image3.png)

Varje nod i trädet är ett objekt. "dod"-objektet i trädet identifieras av notationen 1.3.6, medan "Internet"-objektet i trädet identifieras av notationen 1.3.6.1. Alla SNMP-objektnamn börjar med notation 1.3.6.

En SNMP Manager använder den här objekt notationen för att ange vilket objekt på enheten som den vill hämta eller ange. NetX Duo SNMP-agenten tolkar sådana manager-begäranden och tillhandahåller mekanismer för att programmet ska kunna utföra den begärda åtgärden.

## <a name="snmp-manager-requests"></a>SNMP Manager-begäranden

SNMP har en enkel mekanism för att hantera enheter. Det finns en uppsättning standard-SNMP-kommandon som utfärdas av SNMP Manager till SNMP-enheten *på port 161.* Nedan visas några av de grundläggande SNMP Manager-kommandona:

| SNMP-kommando | Innebörd                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *Hämta det angivna objektet*                                       |
| GETNEXT      | *Hämta nästa logiska objekt efter det angivna objekt-ID:t*      |
| GETBULK      | *Hämta flera logiska objekt efter det angivna objekt-ID:t* |
| SET          | *Ange det angivna objektet*                                       |

Dessa kommandon kodas i ASN.1-formatet (Abstract Syntax Notation One) och finns i nyttolasten för UDP-paketet som skickas av SNMP Manager. NetX Duo SNMP Agent bearbetar begäran och anropar sedan motsvarande hanteringsrutin som anges i ***nx_snmp_agent_create anropet.***

## <a name="netx-duo-snmp-agent-traps"></a>NetX Duo SNMP Agent Traps

Med NetX Duo SNMP-agenten kan du även varna en SNMP-hanterare för händelser asynkront. Detta görs via ett SNMP-trapkommando. Det finns ett unikt API för varje version av SNMP för att skicka traps till en SNMP Manager. Som standard skickas traps till SNMP Manager på port 162.

NetX Duo SNMP Agent tillhandahåller separata säkerhetsnycklar för SNMPv3-trapmeddelanden. För att göra det måste SNMP-programmet skapa en separat uppsättning nycklar från de som tillämpas på svar på Manager-begäranden. Trap-säkerhet gör att SNMP-agenten kan använda samma eller olika lösenord för autentisering och sekretess. Mer information om hur du skapar säkerhetsnycklar finns **i NetX Duo SNMP-autentisering och -kryptering** i nästa avsnitt.

En lista över standard-SNMP-trapvariabler räknas upp överst *i nxd_snmp.h:*

| Variabler                                 | Värde  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

För att inkludera dessa variabler i trap-meddelandet anges trap_type-indataargumentet i *nx_snmp_agent_trapv2_send* (SNMPv2) eller *nx_snmp_agent_trapv3_send* (SNMPv3) till det uppräknade värdet för dessa variabler. Ett exempel visas nedan för SNMPv2 för att meddela SNMP Manager om en kallstartshändelse:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

Om du vill inkludera tillverkarspecifika variabler i trapmeddelandet är trap_type indataargumentet inställt på NX_SNMP_TRAP_CUSTOM och indataargumentet för traplistan innehåller upphovsrättsskyddade data. Observera att trapmeddelandet kommer att innehålla som systemets upptid (1.3.6.1.6.3.1.1.4.1.0). Ett exempel visas nedan för SNMPv2:

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a>NetX Duo SNMP-autentisering och -kryptering

Det finns två varianter av autentisering, *nämligen grundläggande* och *sammanfattande*. Grundläggande autentisering motsvarar en enkel autentisering med oformaterad text *för användarnamn* som finns i många protokoll. I grundläggande SNMP-autentisering verifierar användaren bara att det angivna användarnamnet är giltigt för att utföra SNMP-åtgärder. Grundläggande autentisering är det enda alternativet för SNMP version 1 och 2.

Den största nackdelen med grundläggande autentisering är att användarnamnet överförs i oformaterad text. Sammanfattad SNMPv3-autentisering åtgärdar det här problemet genom att aldrig överföra användarnamnet i oformaterad text. I stället används en algoritm för att härleda en 96-bitars "sammanfattning" från användarnamnet, kontextmotorn och annan information. NetX Duo SNMP Agent har stöd för både MD5- och SHA-sammanfattande algoritmer.

För att aktivera autentisering måste SNMP-agenten ange sitt kontextmotor-ID med hjälp *av nx_snmp_agent_context_engine_set tjänsten.* Kontextmotorns ID används när autentiseringsnyckeln skapas.

Kryptering av SNMPv3-data är tillgängligt med hjälp av DES-algoritmen. Kryptering kräver att autentisering är aktiverat (det går inte att kryptera data utan att ange autentiseringsparametrarna).

Följande API används för att skapa autentiserings- och sekretessnycklar:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

Därefter måste SNMP-agenten konfigureras för att använda dessa nycklar. Följande API används för att registrera en nyckel med SNMP-agenten:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

Separata nycklar kan skapas för trap-meddelanden. Följande API är tillgängligt för att tillämpa nycklar för trap-meddelanden:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

Om du vill inaktivera autentisering eller kryptering för svarsmeddelanden och skicka traps använder du dessa tjänster med nyckelpekarens indata inställt på NULL.

## <a name="netx-duo-snmp-community-strings"></a>NetX Duo SNMP Community-strängar

NetX Duo SNMP-agenten stöder både offentliga och privata community-strängar. Den offentliga strängen  anges med nx_snmp_agent _public_string_set tjänsten. NetX Duo SNMP-agentens privata sträng anges med hjälp *nx_snmp_agent_private_string_set* tjänsten.

## <a name="netx-duo-snmp-username-callback"></a>Motringning av NetX Duo SNMP-användarnamn

Med NetX Duo SNMP Agent-paketet kan  programmet (via nx_snmp_agent_create-anropet) ange ett motringning av användarnamn som anropas i början av hanteringen av varje SNMP-klientbegäran.

Motringningrutinen ger NetX Duo SNMP-agenten användarnamnet. Om det angivna användarnamnet är giltigt eller om det inte behövs någon användarnamnskontroll för att svara på begäran ska motringning av användarnamnet returnera värdet **för NX_SUCCESS**. Annars bör rutinen returnera en **NX_SNMP_ERROR att** ange att det angivna användarnamnet är ogiltigt.

Formatet för programmets motringning av användarnamn definieras nedan:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

Indataparametrarna definieras på följande sätt:

| Parameter | Innebörd                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | Pekare till att anropa SNMP-agenten                        |
| användarnamn  | Mål för pekaren till användarnamnet som krävs |

För SNMPv1- och SNMPv2/v2C-sessioner vill programmet undersöka community-strängen på en inkommande SNMP-begäran för att avgöra om SNMP-begäran har en giltig community-sträng. Det finns flera tjänster för SNMP-programmet för att göra detta.

SNMP-programmet kan fråga om den aktuella SNMP Manager-begäran är en GET-begäran (t.ex. GET, GETNEXT eller GETBULK) eller SET-typ av begäran med hjälp av den här tjänsten:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

Om begäran är en GET-typ vill programmet jämföra indata-community-strängen med SNMP-agentens offentliga sträng:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

På samma sätt, om begäran är en SET-typ, vill programmet jämföra indata-community-strängen med SNMP-agentens privata sträng:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

Värdena is_public och is_private returnerar anger respektive om indata-community-strängen är en giltig offentlig eller privat community-sträng.

Returvärdet för motringningrutinen för användarnamn anger om användarnamnet är giltigt. Värdet för **NX_SUCCESS** returneras om användarnamnet är giltigt eller **NX_SNMP_ERROR** om användarnamnet är ogiltigt.

## <a name="netx-duo-snmp-agent-get-callback"></a>Get Callback för NetX Duo SNMP-agent

Programmet måste ange en återanropsrutin för hantering av GET-objektbegäranden från SNMP Manager. Motringning hämtar värdet för det objekt som anges i begäran.

Programmet GET-återanropsrutin för begäran definieras nedan:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Indataparametrarna definieras på följande sätt:

| Parameter        | Innebörd |
|------------------|----------------------------------|
| *agent_ptr*        | Pekare till att anropa SNMP-agenten |
| object_requested | ASCII-sträng som representerar objekt-ID:t som GET-åtgärden gäller för. |
| object_data      | Datastruktur för att lagra värdet som hämtas av motringning. Detta kan anges med en serie NetX Duo SNMP-API:er som beskrivs nedan. |

> [!NOTE]
> *För oktettsträngar måste objektet tilldelas längden så att den interna funktionen vet hur lång längden är eftersom själva motringningen inte har något längdargument:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Eftersom typen av data inte är känd för GET-återanropet behöver du inte kontrollera datatypen. Längden påverkar inte numeriska typer eller strängar som är nullavgränsade.

Anropa sedan den interna funktionen:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Om återanropsfunktionen inte kan hitta det begärda **objektet NX_SNMP_ERROR_NOSUCHNAME** felkoden returneras. Om något annat fel upptäcks ska **NX_SNMP_ERROR** returneras.

## <a name="netx-duo-snmp-agent-getnext-callback"></a>GETNEXT-återanrop för NetX Duo SNMP-agent

Programmet måste också ange återanropsrutinen för GETNEXT-objektbegäranden från SNMP Manager. GETNEXT-återanropet hämtar värdet för nästa objekt som anges av begäran.

Programmets GETNEXT-rutin för återanrop av begäran definieras nedan:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

Indataparametrarna definieras på följande sätt:

| Parameter        | Innebörd |
|------------------|-------------------------------------------|
| *agent_ptr*        | Pekare till att anropa SNMP-agenten |
| object_requested | ASCII-sträng som representerar objekt-ID:t som GETNEXT-åtgärden gäller för. |
| object_data      | Datastruktur för att lagra värdet som hämtas av motringning. Detta kan anges med en serie NetX Duo SNMP-API:er som beskrivs nedan. |

Samma som gäller för GET-återanrop måste objekt med oktettsträngdata tilldelas längden så att den interna funktionen vet hur lång längden är eftersom själva motringningen inte har ett längdargument:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Eftersom typen av data inte är känd för GET-återanropet behöver du inte kontrollera datatypen. Längden påverkar inte numeriska typer eller strängar som är nullavgränsade.

Anropa sedan den interna funktionen:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Om återanropsfunktionen inte kan hitta det begärda **objektet NX_SNMP_ERROR_NOSUCHNAME** felkoden returneras. Om något annat fel upptäcks ska **NX_SNMP_ERROR** returneras.

## <a name="netx-duo-snmp-agent-set-callback"></a>NetX Duo SNMP Agent SET Callback

Programmet ska ange återanropsrutinen för hantering av SET-objektbegäranden från SNMP Manager. SET-motringning anger värdet för det objekt som anges av begäran.

Rutinerna för återanrop av begäran för programuppsättning definieras nedan:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Indataparametrarna definieras på följande sätt:

| Parameter        | Innebörd |
|------------------|-------- |
| *agent_ptr*      | Pekare till att anropa SNMP-agenten |
| object_requested | ASCII-sträng som representerar objekt-ID:t som SET-åtgärden gäller för. |
| object_data      | Datastruktur som innehåller det nya värdet för det angivna objektet. Den faktiska åtgärden kan utföras med hjälp av NetX Duo SNMP-API:et som beskrivs nedan. |

Observera att för oktettsträngar bör SET-återanropet uppdatera MIB-tabellen med längden på data eftersom SNMP-agenten har parsat data och känner till typ och längd:

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

Om återanropsfunktionen inte kan hitta det begärda **objektet NX_SNMP_ERROR_NOSUCHNAME** felkoden returneras.

Om NetX Duo SNMP-värden har skapat privata gruppsträngar och SNMP-avsändaren av SET-begäran inte har den matchande privata strängen kan det returnera **ett NX_SNMP_ERROR_NOACCESS-fel.** Om något annat fel upptäcks ska **NX_SNMP_ERROR** returneras.

> [!NOTE]
> *Även om NetX Duo SNMP Agent tillhandahåller en SNMP MIB-databas med distributionen är den främst avsedd för testning och utveckling. Utvecklaren kommer troligen att behöva en upphovsrättsskyddad MIB-databas för ett professionell SNMP-program.*

## <a name="changing-snmp-version-at-run-time"></a>Ändra SNMP-version vid körning

SNMP-agentvärden kan ändra SNMP-versionen för var och en av de tre versionerna vid körning med *hjälp av nx_snmp_agent_set_version tjänsten.* SNMP-agenten är som standard aktiverad för alla tre versionerna när SNMP-agenten skapas i *nx_snmp_agent_create*. Programmet kan dock begränsa det till en delmängd av alla versioner.

> [!NOTE]
> *Om konfigurationsalternativen för NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 och/eller NX_SNMP_DISABLE_V3 har definierats har den här funktionen ingen effekt på aktiveringen av de aktuella versionerna.*

SNMP-agenten kan hämta SNMP-versionen av det senaste SNMP-paketet som tagits emot *med hjälp av nx_snmp_agent_get_current_version tjänsten.*

## <a name="snmpv3-discovery"></a>SNMPv3-identifiering

SNMP-agenten svarar på identifieringsbegäranden från SNMP Manager om den är aktiverad för SNMPv3. En sådan begäran innehåller säkerhetsparameterdata med null-värden för auktoritativ motor-ID, användarnamn, startantal och starttid. Autentiseringsparametrar tillämpas inte på DISCOVERY-meddelandet. Variabelbindningslistan i begäran är tom (innehåller noll objekt). SNMP-agenten svarar med noll starttid och antal, och variabelbindningslistan som innehåller 1 objekt, *usmStatsUnknownEngineIDs*, vilket är antalet begäranden som tas emot med ett okänt (null) motor-ID. I den efterföljande GETNEXT-begäran från Browser/Manager fylls startdata och säkerhetsparametrar bara i om säkerhet har aktiverats. I så exempel skickas även en NotInTime-datauppdatering i PDU:en. Säkerhetsparametrarna, t.ex. autentisering, bevisar agentens identitet för chefen.

Mer detaljerad information om SNMPv3-autentisering finns i RFC 3414 "Användarbaserad säkerhetsmodell (USM) för version 3 av Simple Network Management Protocol (SNMPv3)".

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo SNMP RFCs

NetX Duo SNMP är kompatibel med RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 och relaterade RFC.
