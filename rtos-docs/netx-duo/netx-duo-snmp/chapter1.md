---
title: Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SNMP
description: NetX Duo SNMP-implementeringen är en SNMP-agent. En agent ansvarar för att svara på SNMP-hanterarens kommandon och skicka händelse drivna traps.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825782"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>Kapitel 1 – Introduktion till Azure återställnings tider NetX Duo SNMP

Simple Network Management Protocol (SNMP) är ett protokoll som har utformats för att hantera enheter på Internet. SNMP är ett protokoll som använder tjänsterna för anslutnings lös UDP (User Datagram Protocol) för att utföra sin hanterings funktion. Azure återställnings tider NetX Duo SNMP-implementeringen är en SNMP-agent. En agent ansvarar för att svara på SNMP-hanterarens kommandon och skicka händelse drivna traps. 

NetX Duo SNMP stöder både IPv4-och IPv6-kommunikation med SNMP-hanterare. NetX SNMP-program bör kompilera och köra i NetX Duo SNMP. Utvecklare uppmanas dock att Porta befintliga SNMP-program för att använda motsvarande "Duo"-tjänster. Om du till exempel skickar SNMP trap-meddelanden ska följande Duo-tjänster ersätta deras NetX-motsvarighet:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

Mer information finns i **Beskrivning av SNMP agent-tjänster** någon annan stans i användar handboken för mer information.

## <a name="netx-duo-snmp-agent-requirements"></a>Krav för NetX Duo SNMP-agenten

NetX Duo SNMP-paketet kräver att en IP-instans redan har skapats. Dessutom måste UDP vara aktiverat på samma IP-instans.

NetX Duo SNMP-agenten har flera ytterligare krav. Först måste den ha åtkomst till port 161 för hantering av alla SNMP Manager-begäranden. Det kräver också åtkomst till port 162 för att skicka trap-meddelanden till chefen.

Om du vill använda NetX Duo SNMP-agenten med över IPv6 och för att hämta IPv6-objekt måste IPv6 vara aktiverat i NetX Duo. I ***användar handboken för netx Duo*** finns mer information om hur du aktiverar IP-instansen för IPv6-tjänster.

## <a name="netx-duo-snmp-constraints"></a>NetX Duo SNMP-begränsningar

NetX Duo SNMP-protokollet implementerar SNMP version 1, 2 och 3. SNMPv3-implementeringen stöder MD5-och SHA-autentisering och DES-kryptering. Den här versionen av NetX Duo SNMP-agenten har följande begränsningar:

1. En SNMP-agent per NetX IP-instans
2. Inget stöd för RMON
3. SNMP v3-informerar meddelanden stöds inte
4. TÄCKANDE och NSAP-datatyper stöds inte
5. IPv6-adresser definieras som oktett-strängar och format kontroll lämnas till programmet.

## <a name="snmp-object-names"></a>Namn på SNMP-objekt

SNMP-protokollet är utformat för att hantera enheter på Internet. För att åstadkomma detta har varje SNMP-hanterad enhet en uppsättning objekt som definieras av strukturen för hanterings information (SMI) enligt definitionen i RFC 1155. Strukturen är en hierarkisk träd struktur typ som ser ut ungefär så här:

![Diagram över hanterings informationens struktur.](media/image3.png)

Varje nod i trädet är ett objekt. "DoD"-objektet i trädet identifieras av Notations-1.3.6, medan "Internet"-objektet i trädet identifieras av notation-1.3.6.1. Alla namn på SNMP-objekt börjar med notationen 1.3.6.

En SNMP-hanterare använder den här objekt notationen för att ange vilket objekt i enheten som den vill hämta eller ange. NetX Duo SNMP-agenten tolkar sådana Manager-begäranden och tillhandahåller mekanismer för att utföra den begärda åtgärden.

## <a name="snmp-manager-requests"></a>SNMP Manager-begäranden

SNMP har en enkel mekanism för att hantera enheter. Det finns en uppsättning vanliga SNMP-kommandon som utfärdas av SNMP-hanteraren till SNMP-enheten på *port 161*. Nedan visas några av de grundläggande SNMP Manager-kommandona:

| SNMP-kommando | Innebörd                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *Hämta det angivna objektet*                                       |
| GETNEXT      | *Hämta nästa logiska objekt efter angivet objekt-ID*      |
| GETBULK      | *Hämta flera logiska objekt efter angivet objekt-ID* |
| SET          | *Ange det angivna objektet*                                       |

De här kommandona är kodade i formatet för abstrakt syntax notation One (ASN. 1) och finns i nytto lasten för UDP-paketet som skickas av SNMP-hanteraren. NetX Duo SNMP-agenten bearbetar begäran och anropar sedan motsvarande hanterings rutin som anges i ***nx_snmp_agent_create*** -anropet.

## <a name="netx-duo-snmp-agent-traps"></a>NetX Duo SNMP-agentens traps

NetX Duo SNMP-agenten ger möjlighet att även varna en SNMP-hanterare av händelser asynkront. Detta görs via ett SNMP-trap-kommando. Det finns ett unikt API för varje version av SNMP för att skicka traps till en SNMP-hanterare. Som standard skickas traps till SNMP-hanteraren på port 162.

NetX Duo SNMP-agenten innehåller separata säkerhets nycklar för meddelanden om SNMPv3-trap. För att göra det måste SNMP-programmet skapa en separat uppsättning nycklar från de som tillämpas på svar till Manager-begäranden. Med trap-säkerhet kan SNMP-agenten använda samma eller olika lösen ord för autentisering och sekretess. Mer information om hur du skapar säkerhets nycklar finns i **netx Duo SNMP-autentisering och kryptering** i nästa avsnitt.

En lista med variabler för standard-SNMP-trap räknas upp överst i *nxd_snmp. h:*

| Variabler                                 | Värde  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

Om du vill inkludera dessa variabler i trap-meddelandet, trap_type indataargumentet i *nx_snmp_agent_trapv2_send* (SNMPv2) eller *nx_snmp_agent_trapv3_send* (SNMPv3) anges till det uppräknade värdet för dessa variabler. Ett exempel visas nedan för SNMPv2 för att meddela SNMP-hanteraren om en kall start händelse:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

Om du vill inkludera tillverkarspecifika variabler i trap-meddelandet anges argumentet trap_type indataargumentet till NX_SNMP_TRAP_CUSTOM och indataargumentet för trap-listan innehåller de tillverkarspecifika data. Observera att trap-meddelandet kommer att innehålla som system tid (1.3.6.1.6.3.1.1.4.1.0). Ett exempel visas nedan för SNMPv2:

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

## <a name="netx-duo-snmp-authentication-and-encryption"></a>NetX Duo SNMP-autentisering och kryptering

Det finns två varianter-autentisering, nämligen *Basic* och *Digest*. Grundläggande autentisering motsvarar en enkel autentisering med oformaterad text- *username* i många protokoll. I grundläggande SNMP-autentisering verifierar användaren bara att det angivna användar namnet är giltigt för att utföra SNMP-åtgärder. Grundläggande autentisering är det enda alternativet för SNMP version 1 och 2.

Den största nack delen med grundläggande autentisering är att användar namnet överförs som oformaterad text. SNMPv3 Digest-autentiseringen åtgärdar det här problemet genom att aldrig överföra användar namnet som oformaterad text. I stället används en algoritm för att härleda en 96-bitars sammandrag från användar namnet, kontext motorn och annan information. NetX Duo SNMP-agenten har stöd för både MD5-och SHA-algoritmer.

Om du vill aktivera autentisering måste SNMP-agenten ange sitt kontext motor-ID med hjälp av *nx_snmp_agent_context_engine_set* tjänsten. Kontext motorns ID används i skapandet av autentiseringsnyckel.

Kryptering av SNMPv3-data är tillgängligt med DES-algoritmen. Kryptering kräver att autentisering är aktiverat (en kan inte kryptera data utan att ange autentiseringsinställningarna).

Följande API används för att skapa autentiserings-och sekretess nycklar:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

Därefter måste SNMP-agenten konfigureras att använda dessa nycklar. Följande API används för att registrera en nyckel med SNMP-agenten:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

Du kan skapa separata nycklar för trap-meddelanden. Följande API är tillgängliga om du vill använda nycklar för trap-meddelanden:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

Om du vill inaktivera autentisering eller kryptering för svarsmeddelanden och skicka traps, använder du dessa tjänster med indatamängden för nyckel pekare till NULL.

## <a name="netx-duo-snmp-community-strings"></a>NetX Duo SNMP community-strängar

NetX Duo SNMP-agenten stöder både offentliga och privata grupp strängar. Den offentliga strängen anges med tjänsten *nx_snmp_agent _public_string_set* . Den privata strängen för NetX Duo SNMP-agenten anges med hjälp av tjänsten *nx_snmp_agent_private_string_set* .

## <a name="netx-duo-snmp-username-callback"></a>NetX Duo SNMP username-motanrop

NetX Duo SNMP agent-paketet gör att programmet kan ange (via ***nx_snmp_agent_create*** -anrop) ett användar namn för motringning som anropas i början av hantering av varje SNMP-klientbegäran.

Återanrops rutinen ger NetX Duo SNMP-agenten med användar namnet. Om det angivna användar namnet är giltigt eller om ingen användar namns kontroll krävs för att svara på begäran, ska återanropet av användar namnet returnera värdet för **NX_SUCCESS**. Annars bör rutinen returnera **NX_SNMP_ERROR** för att indikera att det angivna användar namnet är ogiltigt.

Formatet på rutinen för motringning av program användar namn definieras nedan:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

Indataparametrarna definieras enligt följande:

| Parameter | Innebörd                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | Pekare för att anropa SNMP-agenten                        |
| användarnamn  | Mål för pekaren till det begärda användar namnet |

För SNMPv1-och SNMPv2/v2C-sessioner ska programmet undersöka grupp strängen i en inkommande SNMP-begäran för att avgöra om SNMP-begäran har en giltig grupp sträng. Det finns flera tjänster för SNMP-programmet att göra detta.

SNMP-programmet kan fråga om den aktuella SNMP Manager-begäran är GET (t. ex. GET, GETNEXT eller GETBULK) eller ange typ av begäran som använder den här tjänsten:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

Om begäran är en GET-typ, vill programmet jämföra ingångs grupp strängen med SNMP-agentens offentliga sträng:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

Om begäran är en UPPSÄTTNINGs typ vill programmet jämföra ingångs gruppens sträng till SNMP-agentens privata sträng:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

Värdena för is_public och is_private anger om gruppens ingångs sträng är en giltig offentlig eller privat grupp sträng.

Returvärdet för återanrops rutinen för användar namn anger om användar namnet är giltigt. Värdet **NX_SUCCESS** returneras om användar namnet är giltigt eller **NX_SNMP_ERROR** om användar namnet är ogiltigt.

## <a name="netx-duo-snmp-agent-get-callback"></a>NetX Duo SNMP-agent Hämta motringning

Programmet måste ange en callback-rutin för att hantera GET-objekt-begär Anden från SNMP-hanteraren. Återanropet hämtar värdet för det objekt som anges i begäran.

Rutinen för att hämta återanrops förfrågan anges nedan:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Indataparametrarna definieras enligt följande:

| Parameter        | Innebörd |
|------------------|----------------------------------|
| *agent_ptr*        | Pekare för att anropa SNMP-agenten |
| object_requested | ASCII-sträng som representerar det objekt-ID som åtgärden GET är för. |
| object_data      | Data struktur som ska innehålla värdet som hämtas av återanropet. Detta kan anges med en serie med NetX Duo SNMP API: er som beskrivs nedan. |

> [!NOTE]
> *För oktett-strängar måste objektet tilldelas längden så att den interna funktionen vet hur lång tid det tar eftersom motringningen inte har något längd argument:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Eftersom data typen inte är känd för att hämta motringning, behöver du inte kontrol lera data typen. Längden får inte påverka numeriska typer eller strängar som är null-avgränsade.

Anropa sedan den interna funktionen:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Om funktionen motringning inte kan hitta det begärda objektet, ska **NX_SNMP_ERROR_NOSUCHNAME** fel koden returneras. Om något annat fel upptäcks, ska **NX_SNMP_ERROR** returneras.

## <a name="netx-duo-snmp-agent-getnext-callback"></a>NetX Duo SNMP-agent GETNEXT motringning

Programmet måste också ange callback-rutinen för GETNEXT-objekt begär Anden från SNMP-hanteraren. GETNEXT-återanropet hämtar värdet för nästa objekt som anges av begäran.

Rutinen för begäran om program GETNEXT anges nedan:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

Indataparametrarna definieras enligt följande:

| Parameter        | Innebörd |
|------------------|-------------------------------------------|
| *agent_ptr*        | Pekare för att anropa SNMP-agenten |
| object_requested | ASCII-sträng som representerar det objekt-ID som GETNEXT-åtgärden avser. |
| object_data      | Data struktur som ska innehålla värdet som hämtas av återanropet. Detta kan anges med en serie med NetX Duo SNMP API: er som beskrivs nedan. |

Samma som sant för GET-återanrop måste objekt med oktett-strängar tilldelas längden så att den interna funktionen vet hur lång tid det tar eftersom motringningen inte har ett längd argument:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Eftersom data typen inte är känd för att hämta motringning, behöver du inte kontrol lera data typen. Längden får inte påverka numeriska typer eller strängar som är null-avgränsade.

Anropa sedan den interna funktionen:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Om funktionen motringning inte kan hitta det begärda objektet, ska **NX_SNMP_ERROR_NOSUCHNAME** fel koden returneras. Om något annat fel upptäcks, ska **NX_SNMP_ERROR** returneras.

## <a name="netx-duo-snmp-agent-set-callback"></a>NetX Duo SNMP-agent ange motringning

Programmet ska ange callback-rutinen för hantering av objekt begär Anden från SNMP-hanteraren. SET motringning anger värdet för det objekt som anges av begäran.

Rutinen för motringning av program uppsättning definieras nedan:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Indataparametrarna definieras enligt följande:

| Parameter        | Innebörd |
|------------------|-------- |
| *agent_ptr*      | Pekare för att anropa SNMP-agenten |
| object_requested | ASCII-sträng som representerar det objekt-ID som åtgärden ställs in för. |
| object_data      | Data struktur som innehåller det nya värdet för det angivna objektet. Den faktiska åtgärden kan utföras med hjälp av NetX Duo SNMP API: erna som beskrivs nedan. |

Observera att om du skapar en oktett-sträng ska MIB-tabellen uppdatera MIB-tabellen med data längden eftersom SNMP-agenten har parsat data och känner till typ och längd:

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

Om funktionen motringning inte kan hitta det begärda objektet, ska **NX_SNMP_ERROR_NOSUCHNAME** fel koden returneras.

Om NetX Duo SNMP-värden har skapat privata grupp strängar och SNMP-avsändaren för SET-begäran inte har den matchande privata strängen, kan den returnera ett **NX_SNMP_ERROR_NOACCESS** fel. Om något annat fel upptäcks, ska **NX_SNMP_ERROR** returneras.

> [!NOTE]
> *Även om NetX Duo SNMP-agenten tillhandahåller en SNMP MIB-databas med distributionen, är det främst för testning och utveckling. Utvecklare kräver förmodligen en patentskyddad MIB-databas för ett professionellt SNMP-program.*

## <a name="changing-snmp-version-at-run-time"></a>Ändra SNMP-version vid körning

SNMP-agentens värd kan ändra SNMP-version för var och en av de tre versionerna vid körning med hjälp av tjänsten *nx_snmp_agent_set_version* . SNMP-agenten aktive ras som standard för alla tre versioner när SNMP-agenten skapas i *nx_snmp_agent_create*. Programmet kan dock begränsas till en delmängd av alla versioner.

> [!NOTE]
> *Om konfigurations alternativen NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 och/eller NX_SNMP_DISABLE_V3 har definierats, har den här funktionen ingen inverkan som gör det möjligt att använda de versioner som påverkas.*

SNMP-agenten kan hämta SNMP-versionen av det senaste SNMP-paketet som togs emot med hjälp av tjänsten *nx_snmp_agent_get_current_version* .

## <a name="snmpv3-discovery"></a>SNMPv3-identifiering

SNMP-agenten, om den är aktive rad för SNMPv3, kommer att svara på identifierings begär Anden från SNMP-hanteraren. En sådan begäran innehåller säkerhets parameter data med null-värden för auktoritativt motor-ID, användar namn, start antal och start tid. Autentiseringsinställningarna används inte för IDENTIFIERINGs meddelandet. Variabel bindnings listan i begäran är tom (innehåller noll objekt). SNMP-agenten svarar med noll start tid och antal, och variabel bindnings listan som innehåller 1 objekt, *usmStatsUnknownEngineIDs*, vilket är antalet förfrågningar som tagits emot med ett okänt motor-ID (null). På den efterföljande GETNEXT-begäran från webbläsaren/hanteraren fylls start data och säkerhets parametrar bara i om säkerhet är aktiverat. Om så är fallet skickas även en NotInTime-datauppdatering i PDU. Säkerhets parametrarna, t. ex. autentisering, visar identiteten för agenten för chefen.

Mer detaljerad information om SNMPv3-autentisering finns i RFC 3414 "User-based Security Model (USM POLICYEGENSKAPER) för version 3 av Simple Network Management Protocol (SNMPv3)".

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo SNMP-RFC

NetX Duo SNMP är kompatibelt med RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 och relaterade RFC: er.
